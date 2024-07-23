# Module 7 - Lab 1 - Exercise 7 - Create Detections

### Task 1: Attack 1 Detection with Defender for Endpoint

In this task, you will create a detection for **Attack 1** on the host with the Microsoft Defender for Endpoint configured.

1. Log in to the WIN1 virtual machine with the password as provided in the Environment tab. 

2. In the Microsoft Sentinel portal, Select **Logs** from the General section.

3. First, you need to see where the data is stored. Since you just performed the attacks set the log **Time Range: Last 24 hours**.

4. Run the following KQL Statement:

    ```KQL
    search "temp\\startup.bat"
    ```
   
   ![Screenshot](../Media/plx1.png)

   > **Note**: If you don't see any output of the command, please follow the next step. because sometimes this query may take more time to get proper output.

5. The table *SecurityEvent* looks to have the data already normalized and is easy for us to query. Expand the row to see all the columns related to the record.

6. From the results, we now know that the Threat Actor is using reg.exe to add keys to the Registry key and the program is located in C:\temp. **Run** the following statement to replace the *search* operator with the *where* operator in our query:

    ```KQL
    SecurityEvent 
    | where Activity startswith "4624" 
    ```

    ![Lab overview.](../Media/plx2.png)

  >**Important:** If you do not see the *DeviceRegistryEvents* table in the results, an alternative for the following two queries is to use the *DeviceProcessEvents* table as a replacement. That said, use one of the two provided examples below, depending on the table you see in the previous query.

1. It is important to help the Security Operations Center Analyst by providing as much context about the alert as you can. This includes projecting Entities for use in the investigation graph. **Run** the following query:

    ```KQL
    SecurityEvent 
    | where Activity startswith "4624" 
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = SubjectUserName
    ```

1. Now that you have a good detection rule, in the Logs window, select the **+ New alert rule** in the command bar and then select **Create Microsoft Sentinel alert**. This will create a new Scheduled rule.
**Hint:** You might need to select the ellipsis (...) button in the command bar.

1. This starts the "Analytics rule wizard". For the *General* tab type:

    |Setting|Value|
    |---|---|
    |Name|Startup RegKey|
    |Description|Startup RegKey in c:\temp|
    |Severity|High|
    |MITRE ATT&CK|Persistence|
    
1. Select **Next: Set rule logic >** button.

   ![Lab overview.](../Media/plx3.png)

1. On the *Set rule logic* tab, the *Rule query* should be populated already with your KQL query, as well as the entities under *Alert enrichment - Entity mapping*.

    |Entity|Identifier|Data Field|
    |:----|:----|:----|
    |Account|FullName|AccountCustomEntity|
    |Host|Hostname|HostCustomEntity|

1. If **Hostname** isn't selected for *Host* Entity, select it from the drop-down list.

1. For *Query scheduling* set the following:

    |Setting|Value|
    |---|---|
    |Run Query every|5 minutes|
    |Lookup data from the last|1 Days|

    >**Note:** We are purposely generating many incidents for the same data. This enables the Lab to use these alerts.

1. Leave the rest of the options with the defaults. Select **Next: Incident settings>** button.

1. For the *Incident settings* tab, leave the default values and select **Next: Automated response >** button.

1. On the *Automated response* tab under *Automation rules*, select **Add new**.

1. Use the settings in the table to configure the automation rule.

    |Setting|Value|
    |:----|:----|
    |Automation rule name|Startup RegKey|
    |Trigger|When incident is created|
    |Actions |Run playbook|
   
1. A second drop-down menu appears with an *Information (i)* message regarding playbook permissions and a **Manage playbook permissions link**

    >**Note:** The playbooks will appear grayed out in the drop-down list until permissions are configured.

1. Select the **Manage playbook permissions link**

1. On the *Manage Permissions* page, select the **threat-xdr** resource group, and select **Apply**.

1. From the drop-down menu, select the playbook **PostMessageTeams-OnIncident**, if required refresh the page.

1. Select **Apply**

    ![Lab overview.](../Media/plx4.png)

1. Select the **Next: Review + Create >** button.
  
1. On the *Review and create* tab, select the **Save** button to create the new Scheduled Analytics rule.

### Task 2: Privilege Elevation Attack Detection

In this task, you will create a detection for the second attack of the previous exercise.

1. In the Microsoft Sentinel portal, select **Logs** from the General section in case you navigated away from this page.

1. **Run** the following KQL Statement to identify any entry that refers to administrators:

    ```KQL
    search "administrators" 
    | summarize count() by $table
    ```

    ![](../Media/plx5.png)

1. The result might show events from different tables, but in our case, we want to investigate the SecurityEvent table. The EventID and Event that we are looking at is "4732 - A member was added to a security-enabled local group". With this, we will identify adding a member to a privileged group. **Run** the following KQL query to confirm:

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    ```

   ![](../Media/plx6.png)

1. Expand the row to see all the columns related to the record. The username of the account added as Administrator does not show. The issue is that instead of storing the username, we have the Security IDentifier (SID). **Run** the following KQL to match the SID to the username that was added to the Administrators group:

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    | extend Acct = MemberSid, MachId = SourceComputerId  
    | join kind=leftouter (
        SecurityEvent 
        | summarize count() by TargetSid, SourceComputerId, TargetUserName 
        | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1
    ```

    ![](../Media/plx7.png)

1. Extend the row to show the resulting columns, in the last one, we see the name of the added user under the *UserName1* column we *project* within the KQL query. It is important to help the Security Operations Analyst by providing as much context about the alert as you can. This includes projecting Entities for use in the investigation graph. **Run** the following query:

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    | extend Acct = MemberSid, MachId = SourceComputerId  
    | join kind=leftouter (
        SecurityEvent 
        | summarize count() by TargetSid, SourceComputerId, TargetUserName 
        | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = UserName1
    ```

   ![](../Media/plx8.png)

1. Now that you have a good detection rule, in the Logs window, select **+ New alert rule** in the command bar and then select **Create Microsoft Sentinel alert**. **Hint:** You might need to select the ellipsis (...) button in the command bar.

1. This starts the "Analytics rule wizard". For the *General* tab type:

    |Setting|Value|
    |---|---|
    |Name|**SecurityEvent Local Administrators User Add**|
    |Description|**User added to Local Administrators group**|
    |Severity|**High**|
    |MITRE ATT&CK|**Privilege Escalation**|
  
1. Select **Next: Set rule logic >** button. 

   ![](../Media/plx9.png)


1. On the *Set rule logic* tab, the *Rule query* should be populated already with your KQL query, and add the details for entities under *Alert enrichment - Entity mapping*.

    |Entity|Identifier|Data Field|
    |:----|:----|:----|
    |Account|FullName|AccountCustomEntity|
    |Host|Hostname|HostCustomEntity|

1. For *Query scheduling* set the following:

    |Setting|Value|
    |---|---|
    |Run Query every| **5 minutes (1)** |
    |Lookup data from the last| **1 Days (2)**|

    >**Note:** We are purposely generating many incidents for the same data. This enables the Lab to use these alerts.

1. Leave the rest of the options with the defaults. Select **Next: Incident settings> (3)** button.

   ![](../Media/plx10.png)

1. For the *Incident settings* tab, leave the default values and select **Next: Automated response >** button.

1. On the *Automated response* tab under *Automation rules*, select **Add new (1)** and Use the settings in the table to configure the automation rule Select **Apply (6)**.

   |Setting|Value|
   |:----|:----|
   |Automation rule name|**SecurityEvent Local Administrators User Add (1)**|
   |Trigger|**When incident is created (2)**|
   |Actions |**Run playbook (3)**|
   |playbook |**PostMessageTeams-OnIncident (4)**|

   >**Note:** You have already assigned permissions to the playbook, so it must be available if not click on manage permissions and select it manually and it will be available by now

   ![](../Media/plx11.png)

1. Select the **Next: Review and create >** button.
  
1. On the *Review and create* tab, select the **Save** button to create the new Scheduled Analytics rule.

## Proceed to Exercise 8
