# Module 7 - Lab 1 - Exercise 6 - Create Detections


### Task 1: Attack 1 Detection with Defender for Endpoint

In this task, you will create a detection for **Attack 1** on the host with the Microsoft Defender for Endpoint configured.

1. Login to WIN1 virtual machine with the password as provided in the environment tab.

2. In the Microsoft Sentinel portal, Select **Logs** from the General section.

3. First, you need to see where the data is stored. Since you just performed the attacks set the log **Time Range: Last 24 hours**.

4. Run the following KQL Statement:

```KQL
search "temp\\startup.bat"
```

5. This detection will focus on data from Defender for Endpoint.  Run the following KQL Statement:

```KQL
search in (Device*) "temp\\startup.bat"
```

  >**Important:** If you do not see the *DeviceRegistryEvents* table in the results, an alternative for the following two queries is to use the *DeviceProcessEvents* table as replacement. Being that said, use one of the two provided examples below, depending on the table you see in the previous query.

6. The table - DeviceRegistryEvents looks to have the data already normalized and easy for us to query.  Expand the rows to see all the columns related to the record.

7. From the results, we now know that the Threat Actor is using reg.exe to add keys to the Registry key and the program is located in C:\temp. **Run** the following statement to replace the *search* operator with the *where* operator in our query:

    ```KQL
    DeviceRegistryEvents | where ActionType == "RegistryValueSet"
    | where InitiatingProcessFileName == "reg.exe"
    | where RegistryValueData startswith "c:\\temp"
    ```

    Alternatively, you can **Run** the following KQL query using the *DeviceProcessEvents* table:

    ```KQL
    DeviceProcessEvents | where ActionType == "ProcessCreated"
    | where FileName == "reg.exe"
    | where ProcessCommandLine contains "c:\\temp"
    ```

8. It is important to help the Security Operations Center Analyst by providing as much context about the alert as you can. This includes projecting Entities for use in the investigation graph. Run the following query:

    ```KQL
    DeviceRegistryEvents
    | where ActionType == "RegistryValueSet"
    | where InitiatingProcessFileName == "reg.exe"
    | where RegistryValueData startswith "c:\\temp"
    | extend timestamp = TimeGenerated, HostCustomEntity = DeviceName, AccountCustomEntity = InitiatingProcessAccountName
    ```

   ![Screenshot](../Media/SC200_sysmon_query2.png)
   
   Alternatively, you can **Run** the following KQL query using the *DeviceProcessEvents* table:

    ```KQL
    DeviceProcessEvents | where ActionType == "ProcessCreated"
    | where FileName == "reg.exe"
    | where ProcessCommandLine contains "c:\\temp"
    | extend timestamp = TimeGenerated, HostCustomEntity = DeviceName, AccountCustomEntity = InitiatingProcessAccountName
    ```

9.  Now that you have a good detection rule, in the Log window with the query, select the **+ New alert rule** in the Command Bar(**...**).  Then select **Create Azure Sentinel alert**.

10. This starts our Analytics rule wizard. For the General Tab, enter:

    |Setting|Value|
    |---|---|
    |Name|**MDE Startup RegKey**|
    |Description|**MDE Startup Regkey in c:\temp**|
    |Tactics and techniques|**Persistence**|
    |Severity|**High**|

11. Select **Next : Set rule logic >** button.

12. On the Set rule logic tab, the **Rule query** should already be populated.

13. For Query scheduling set the following:

    |Setting|Value|
    |---|---|
    |Run Query every|5 minutes|
    |Look data from the last|1 Day|

    >**Note:** We are purposely generating many incidents for the same data.  This enables the Lab to use these alerts.

14. Leave the rest of the options to the defaults.  Select **Next : Incident settings >**:

15. For the *Incident settings* set the following: 

    |Setting|Value|
    |---|---|
    |Incident settings|Enabled|
    |Alert grouping|Disabled|

16. For the Automated response tab select the **PostMessageTeams-OnAlert** under Alert automation (classic) and then select Next: Review button.

17. On the Review tab, select the Create button to create the new Scheduled Analytics rule.


### Task 2: Attack 2 Detection with SecurityEvent

In this task, you will create a detection for *Attack 2* on the host with the Security Events connector and Sysmon installed.

1. Select **Logs** from the General section of the Microsoft Sentinel portal.

2. First, you need to see where the data is stored. Since you just performed the attacks.  

    Set the Log Time Range to Last 24 hours.

3. Run the following KQL Statement:

```KQL
search "administrators"
```

4. The results show the following tables:
    - Event
    - SecurityEvent

5. Our first data source is SecurityEvent. Time to research what event ID Windows uses to identify adding a member to a privileged group. copy the EventID and replace in all the bewlow queries. **Kindly check the Event Id before run the script** and replace. Run the following script to confirm:

```KQL
SecurityEvent
| where EventID == "4732"
| where TargetAccount == "Builtin\\Administrators"
```

6. Expand the rows to see all the columns related to the record.  The username we are looking for doesn't show.  The issue is that instead of storing the username, the security identifier (SID) is stored.  The following KQL will try to match the SID to populate the TargetUserName that was added to the Administrators group.

```KQL
SecurityEvent
| where EventID == "4732"
| where TargetAccount == "Builtin\\Administrators"
| extend Acct = MemberSid, MachId = SourceComputerId 
| join kind=leftouter (
     SecurityEvent 
     | summarize count() by TargetSid, SourceComputerId, TargetUserName
     | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName
) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1 
```

   ![Screenshot](../Media/SC200_sysmon_attack3.png)

>**Note:** This KQL might not return the expected results because of the small dataset used in the lab.

7. It is important to help the Security Operations Analyst by providing as much context about the alert as you can. This includes projecting Entities for use in the investigation graph.  Run the following query:

```KQL
SecurityEvent
| where EventID == "4732"
| where TargetAccount == "Builtin\\Administrators"
| extend Acct = MemberSid, MachId = SourceComputerId 
| join kind=leftouter (
     SecurityEvent 
     | summarize count() by TargetSid, SourceComputerId, TargetUserName
     | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName
) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1 
| extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = UserName1
```

8. Now that you have a good detection rule, in the Log window with the query, select **+ New alert rule** in the Command Bar(by selecting **...**), then select **Create Azure Sentinel alert**.

9. This starts our Analytics rule wizard. For the General Tab, enter:

    |Setting|Value|
    |---|---|
    |Name|**SecurityEvents Local Administrators User Add**|
    |Description|**User added to Local Administrators group**|
    |Tactics and techniques|**Privilege Escalation**|
    |Severity|**High**|

10. Select **Next : Set rule logic >** button. On the Set rule logic tab, the Rule query and Map entities should already be populated.

11. For Query scheduling set the following:

    |Setting|Value|
    |---|---|
    |Run Query every|5 minutes|
    |Look data from the last|1 Day|

    >**Note:** We are purposely generating many incidents for the same data.  This enables the Lab to use these alerts.

12. Leave the rest of the options to the defaults.  Select **Next : Incident settings >**:

13. For the *Incident settings (Preview)* set the following:

    |Setting|Value|
    |---|---|
    |Incident settings|Enabled|
    |Alert grouping|Disabled|

14. Select **Next: Automated response >**. For the "Automated response" tab select the *PostMessageTeams-OnAlert* under *Alert automation* and then select **Next : Review** button.

15. On the Review tab, select **Create**.

## Proceed to Exercise 7
