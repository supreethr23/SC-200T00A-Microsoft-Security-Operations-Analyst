# Module 3 - Lab 1 - Exercise 1 - Enable Microsoft Defender for Cloud

## Lab scenario

You're a Security Operations Analyst working at a company that is implementing cloud workload protection with Microsoft Defender for Cloud.  In this lab you will enable Microsoft Defender for Cloud.


### Task 1: Access the Azure portal and set up a Subscription.

In this task, you will set up an Azure Subscription required to complete this lab and future labs.

1. On WIN1 Virtual machine, Open the Microsoft Edge browser or open a new tab if already open.

1. In the Edge browser, navigate to the Azure portal at (https://portal.azure.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Subscription*, then select **Subscriptions**. 

1. If the **"Azure HOL xxxx"** subscription is shown (or equivalent name in your selected language), proceed to Task #2. Otherwise, ask your instructor on how to create the Azure subscription with your tenant admin user credentials. **Note:** The subscription creation process could take up to 10 minutes. 

    **Important:** These labs have been designed to use less than USD $10 of Azure services during the class.


### Task 2: Create a Log Analytics Workspace.

In this task, you will create a Log Analytics workspace for use with Microsoft Defender for Cloud.

1. In the Search bar of the Azure portal, type *Log Analytics*, then select **Log Analytics workspaces**.

1. Select **+Create** from the command bar.

1. Select **Create new** for the Resource group.

1. Enter *RG-Defender* and select **Ok**.

1. For the Name, enter something unique like: *uniquenameDefender*.

1. Select **Review + Create**.

1. Once the workspace validation has passed, select **Create**. Wait for the new workspace to be provisioned, this may take a few minutes.


### Task 3: Enable Microsoft Defender for Cloud.

In this task, you will enable and configure Microsoft Defender for Cloud.

1. In the Search bar of the Azure portal, type *Defender*, then select **Microsoft Defender for Cloud**.

1. On the **Getting started** page, go to the **Upgrade** section and make sure your subscription is selected, and then select **Upgrade** button at the bottom of the page.

1. The next page shows the option to install the agent on virtual machines already in the subscription. Do nothing here.

1. Select **Environment settings** from the Management area of the portal menu.

1. expand it and note that your "Defender coverage" includes at least 11 plans. If you don't see it, wait for the *Trial started* notification to appear. After that, select **Refresh** and select your Subscription. 

1. click on the subscription and Review the different Azure resources and fees under the *Microsoft Defender for* and *Pricing* columns.

1. Select **Auto provisioning** from the Settings area in Defender plans.

1. Review the Auto provisioning - Extensions. Confirm that **Log Analytics agent for Azure VMs** is **Off**.

1. Close the settings page by selecting the 'x' on the upper right of the page to go back to the **Environment settings** again and select the '>' on the left of your subscription.

1. Select the Log analytics workspace you created earlier *uniquenameDefender* to review the available options and pricing. Select **Enable all Microsoft Defender for Cloud plans** and select **Save**.


### Task 4: Install Azure Arc on an On-Premises Server. (Read-Only)

To make onboarding of your on-premises server easier.  Install Azure Arc, which will then enable Azure to manage the on-premises server.

In this task, you will install Azure Arc on an on-premises server.

1. Log in to WINServer virtual machine as Administrator with the password: **Passw0rd!**.  

1. Open the Microsoft Edge browser and navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy, and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Arc*, then select **Azure Arc**.

1. In the navigation pane under **Infrastructure** select **Servers**

1. Select **+ Add**.

1. Select **Generate script** in the "Add a single server" section.

1. Select **Next** to get to the Resource details tab.

1. Select the Resource group you created earlier. Hint: *RG-Defender*

    **Note:** If you haven't already created a resource group, open another tab and create the resource group and start over.

1. Review the *Server details* and *Network connectivity* options. Select **Next** to get to the Tags tab.

1. Select **Next** to get to the Download and run script tab.

1. Select **Register**.

    **Note:** Wait at least three (3) minutes for processing.

1. Scroll down and select the **Download** button. Hint: if your browser blocks the download take action in the browser to allow it. In Edge Browser, select the 3 dots "..." and then select **Keep**. 

1. Right-click the Windows Start button and select **Windows PowerShell (Admin)**.

1. Enter Administrator for the Username if prompted.

1. Enter Passw0rd! for the password if prompted.

1. Enter: cd C:\Users\Administrator\Downloads

1. Type *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* and press enter.

1. Enter **A** for Yes to All and press enter.

1. Type *.\OnboardingScript.ps1* and press enter.

1. Enter **R** to Run once and press enter (this may take a couple minutes).

1. Follow the instructions on the last line of the output in PowerShell, to complete the device registration.  This will include authentication of the device through a browser.  Copy the url (https://microsoft.com/devicelogin) and enter it in a new Edge browser tab. Go back to the Windows PowerShell window, copy the code to authenticate and paste it in the previously open tab and select **Next**. Select your tenant admin account and select **Continue** in the *Are you trying to sign in to Azure Connected Machine Agent?* window. 

1. After the message *"Successfully Onboarded Resource to Azure"* appears in the Windows PowerShell window, go to the Azure portal page where you downloaded the script and select **Close**. Close the **Add servers with Azure Arc** to go back to the Azure Arc **Servers** page.

1. Select **Refresh** until WINServer server name appears.

    **Note:** This could take a few minutes.


### Task 5: Protect an On-Premises Server.

In this task, you will manually install the required agent on the Windows Server.

1. On WIN1 Virtual machine, Go to **Microsoft Defender for Cloud** and select the **Getting Started** page.

1. Select the **Get Started** tab.

1. Scroll down and select **Configure** under the *Add non-Azure servers* section.

1. Select **Upgrade** next to the workspace you created earlier.  This might take a few minutes, wait until you see the notification *"Defender plans for workspace were saved successfully"*.

1. Select **+ Add Servers** next to the workspace you created earlier.

1. Select **Download Windows Agent (64 bit)**.

1. Run the downloaded file.

1. Select **Next** until the wizard page for **Agent Setup Options** appears, Select **Connect the Agent to Azure Log Analytics (OMS)**, then select **Next**.

1. Copy and paste the **Workspace ID** and **Primary Key** from the Azure portal into the wizard page fields as appropriate and select **Next**.

1. Continue with the Install. Select **Finish** when complete.

1. Go to the "Microsoft Defender for Cloud" portal and select **Inventory**.

1. The Server should appear in the list.  You may have to select **Refresh** to see the update and it will take a few minutes.

1. You can move on to the next lab and return later to the **Microsoft Defender for Cloud**. Your server will appear in the **Inventory** section. 

# Proceed to Exercise 2
