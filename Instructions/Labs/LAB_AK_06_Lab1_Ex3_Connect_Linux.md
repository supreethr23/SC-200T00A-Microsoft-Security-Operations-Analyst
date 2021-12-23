# Module 6 - Lab 1 - Exercise 3 - Connect Linux hosts to Microsoft Sentinel using data connectors

### Task 1: Access the Microsoft Sentinel Workspace.

In this task, you will access your Microsoft Sentinel workspace.

1. Log in to WIN1 virtual machine with the password as provided in the Environment tab.  

1. Start the Microsoft Edge browser.

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created in a previous lab.


### Task 2: Connect a Linux Host using the Common Event Format connector.

In this task, you will connect a Linux host to Microsoft Sentinel with the Common Event Format (CEF) connector.

1. Select **Data connectors** from the Configuration area in Microsoft Sentinel.  From the Data Connectors tab, search for the **Common Event Format (CEF)** connector and select it from the list.

1. Select **Open connector page** on the connector information blade.

1. Copy to the clipboard the command shown in *1.2 Install the CEF collector on the Linux machine*.

1. Back to the Azure portal, In the Search bar of the Azure portal, type **virtual machine**, then select **Virtual machine**.

1. Open LIN1 Linux virtual machine and copy the Public ip address of LIN1.

1. launch Windows PowerShell as Administrator by right-clicking the Start menu icon and select **Windows PowerShell (Admin)**. Select **Yes** to allow the app to run in the User Account Control window that appears.

1. Enter the following PowerShell command, adjusting for your specific Linux server information, and press enter:

```PowerShell
ssh <insert your linux IP address here> -l <insert linux user name here>
```
   **Note**: Replace `<insert your linux IP address here>` with Copied Public iP address and `<insert linux user name here>` with Admin Username provided under Resource group: LIN1 in the Environment tab

1. Enter *yes* to confirm the connection and then type the user's password and press enter. Your screen should look something like this:

   ![linux login](../Media/PSconnectLinux.png)

1. You are now ready to paste in the *1.2 Install the CEF collector on the Linux machine* from the earlier step. Make sure that script from Azure is in the clipboard. In PowerShell right-click the top bar and choose **Edit** and then **Paste**. Once pasted add a **3** to the word *python* as shown below:

   ![ConnectorScript](../Media/ConnectorScript.png)


1. Once the script is pasted in and adjusted press enter. The script will run against your Linux server remotely. When the script processes properly it should look similar to this screen:

   ![ConnectorScript](../Media/LinuxConnected.png)


### Task 3: Connect a Linux host using the Syslog connector.

In this task, you will connect a Linux host to Microsoft Sentinel with the Syslog connector.

1. Connect to WIN1, which should already be in the Microsoft Sentinel portal for your workspace.  

1. From the Data Connectors tab, search for the **Syslog** connector and select it from the list.

1. Select **Open connector page** on the connector information blade.

1. Open the **Install agent on a non-Azure Linux Machine** section.

1. Select the link for **Download & install agent for non-Azure Linux machine**. 

1. Select the tab for **Linux servers**.
   
1. Open LIN2 Linux virtual machine and copy the Public ip address of LIN2.

1. Copy the command in the *Download and onboard agent for Linux* area to the clipboard.

1. Go back to the WIN1 virtual machine and launch a NEW Windows PowerShell as Administrator by right-clicking the Start menu icon and select **Windows PowerShell (Admin)**. Select **Yes** to allow the app to run in the User Account Control window that appears.

   >**Note:** You can reuse the Windows PowerShell window if the *Installation completed* for the last task by entering *exit* to close the connection to LIN1.

1. Enter the following PowerShell command, adjusting for your specific Linux server information, and press enter:

```PowerShell
ssh <insert your linux IP address here> -l <insert linux user name here>
```

   **Note**: Replace `<insert your linux IP address here>` with Copied Public iP address and `<insert linux user name here>` with Admin Username provided under Resource group: LIN2 in the Environment tab
   
1. Enter *yes* to confirm the connection and then type the user's password and press enter. Your screen should look something like this:

   ![linux login](../Media/PSconnectLinux.png)

1. You are now ready to paste in the *Download and onboard agent for Linux* from the earlier step. Make sure that script from Azure is in the clipboard. In PowerShell right-click the top bar and choose **Edit** and then **Paste**.

1. Once the script is pasted in press enter. The script will run against your Linux server remotely. You have completed the task. No further labs in this course rely on this connection.


### Task 4: Configure the facilities you want to collect and their severities for the Syslog connector.

In this task, you will configure the Syslog collection facilities.

1. Connect to WIN1 virtual machine.

1. In Microsoft Sentinel portal, select **Settings** and then **Workspace settings** from the settings blade.

1. Select **Agents configuration** from the **Settings** area.

1. Select the **Syslog** tab.

1. Select the **+ Add facility** button.

1. Select **auth** from the drop-down menu for *Facility name*.

1. Select the **+ Add facility** button again.

1. Select **authpriv** from the drop-down menu for *Facility name*.

1. Select **Apply**.  You have completed this task.

## Proceed to Exercise 4
