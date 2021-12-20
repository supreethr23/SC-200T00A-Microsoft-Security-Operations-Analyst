# Module 2 - Lab 1 - Exercise 1 - Deploy Microsoft Defender for Endpoint

## Lab scenario

You are a Security Operations Analyst working at a company that is implementing Microsoft Defender for Endpoint. Your manager plans to onboard a few devices to provide insight into required changes to the Security Operations (SecOps) team response procedures.

You start by initializing the Defender for Endpoint environment. Next, you onboard the initial devices for your deployment by running the onboarding script on the devices. You configure security for the environment. Lastly, you create Device groups and assign the appropriate devices.

>**Important:**  The lab Virtual Machines are used through different modules. SAVE your virtual machines. If you exit the lab without saving, you will be required to re-run some configurations again.


### Task 1: Initialize Microsoft Defender for Endpoint.

In this task, you will perform the initialization of the Microsoft Defender for Endpoint portal.

1. On WIN1 Virtual machine, If you are not already at the Microsoft 365 Defender portal, start the Microsoft Edge browser.

1. In the Edge browser, go to the Microsoft 365 Defender portal at (https://security.microsoft.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. On the **Microsoft 365 Defender** portal, from the navigation menu, select **Settings** from the left.

1. On the **Settings** page select **Microsoft 365 Defender**.  Select **Preview features** and make sure preview features are turned on. Return to the **Settings** menu.

1. On the **Settings** page select **Device discovery**.  In Discovery setup make sure **Standard discovery** is selected.  Return to the **Settings** menu. **Note**: If you don't see the **Device discovery** option under **Settings**, logout by selecting the top-right circle with your account initials and select **Sign out**. Login again with the **Tenant Email** credentials.

	**Note:** The Defender for Endpoint setup should be performed automatically by your Microsoft 365 E5 tenant.  You can view the other settings if you like.  You will onboard Devices in the next task.  


### Task 2: Onboard a Device.

In this task, you will onboard a device to Microsoft Defender for Endpoint using an onboarding script.

1. If you are not already at the Microsoft 365 Defender portal in your browser, start the Microsoft Edge browser and go to (https://security.microsoft.com) and login with the **Tenant Email** credentials.

1. Select **Settings** from the left menu bar, then from the Settings page select **Endpoints**.

1. Select **Onboarding** in the Device management section.

1. In the "1. Onboard a device" area make sure "Local Script (for up to 10 devices)" is displayed in the Deployment method drop-down and select the **Download onboarding package** button. Highlight the "WindowsDefenderATPOnboardingPackage.zip" file with your mouse and select the folder icon **Show in folder**.

1. Right-click the downloaded zip file and select **Extract All...**, make sure that *Show extracted files when complete* is checked and select **Extract**.

1. Right-click on the extracted file "WindowsDefenderATPLocalOnboardingScript.cmd" and choose **Run as Administrator**.  If you encounter the Windows SmartScreen, select on **More info** and choose **Run anyway**. **Hint:** By default, the file should be in the c:\users\admin\downloads directory.
    
1. When the "User Account Control" windows is shown, select **Yes** to allow the script to run and answer **Y** to questions presented by the script and press **Enter**. When complete you should see a message in the command screen that says something like "Successfully onboarded machine to Microsoft Defender for Endpoint". Press any key to close the window.

1. From the Onboarding page in the portal under the "2. Run a detection test" area, copy the detection test script by selecting the **Copy** button.  In the windows search bar type **CMD** and choose to **Run as Administrator** on the right pane. When the "User Account Control" windows is shown, select **Yes** to allow the app to run. Paste the script by right-clicking in the **Administrator: Command Prompt** windows and press **Enter** to run it. The window closes automatically after running the script.

1. In the Microsoft 365 Defender portal, in the left-hand menu, in the Endpoints area, select **Device inventory**. You should now see your device in the list.

	![](../Media/s6.png)


	**Note:** It can take up to 5 minutes for the device to be displayed in the portal. If the device is not shown, complete the next task and come back to check it back later.


### Task 3: Configure Role

In this task, you will configure roles for use with device groups.

1. In the Microsoft 365 Defender portal select **Settings** from the left menu bar, then select **Endpoints**. 

1. Select **Roles** in the permissions area.

1. Select the **Turn on roles** button.

1. Select **+ Add item**.

1. In the Add role dialog enter the following:

    |General setting|Value|
    |---|---|
    |Role name|**Tier 1 Support**|
    |Permissions|select **Live Response capabilities** and click on **Advanced**|

1. Select the **Assigned user groups** tab. Select **sg-IT** and then select **Add selected groups**. Make sure it appears under *Azure AD user groups with this role*.

1. Select **Save**.


### Task 4: Configure Device Groups

In this task, you will configure device groups that allow for access control and automation configuration.

1. In the Microsoft 365 Defender portal select **Settings** from the left menu bar, then select **Endpoints**. 

1. In the permissions area select **Device groups**.

1. Select **+ Add device group**.

1. Enter the following information on the General tab:

    |General setting|Value|
    |---|---|
    |Device group name|**Regular**|
    |Automation level|Full - remediate threats automatically|

1. Select **Next**.

1. On the Devices tab for the OS condition select **Windows 10** and select **Next**.

1. On the Preview devices tab you may select **Show preview** and see the WIN1 virtual machine.  Select **Next**.

1. For the User access tab, select **sg-IT** and then select **Add selected groups** button. Make sure it appears under *Azure AD user groups with access to this device group*.

1. Select **Done**.

1. Device group configuration has changed. Select **Apply changes** to check matches and recalculate groupings.

## Proceed to Exercise 2
