# Module 3 - Lab 1 - Exercise 1 - Enable Microsoft Defender for Cloud

## Lab scenario

You're a Security Operations Analyst working at a company that is implementing cloud workload protection with Microsoft Defender for Cloud.  In this lab, you will enable Microsoft Defender for Cloud.

## Lab objectives

In this lab, you will perform the following:

- Task 1: Access the Azure portal and set up a Subscription

- Task 2: Create a Log Analytics Workspace

- Task 3: Enable Microsoft Defender for Cloud

- Task 4: Install Azure Arc on an On-Premises Server

- Task 5: Protect an On-Premises Server

## Estimated timing: 40 minutes

## Architecture Diagram

  ![Picture 1](../Media/SC200-Lab_Diagrams_Mod3_L1_Ex1.png)
  
### Task 1: Access the Azure portal and set up a Subscription

In this task, you will set up an Azure Subscription required to complete this lab and future labs.

1. On the lab Virtual machine, Open the Microsoft Edge browser or open a new tab if already open.

1. In the Edge browser, navigate to the Azure portal at (https://portal.azure.com).

1. In the **Sign in** dialog box, copy and paste Email/Username: <inject key="AzureAdUserEmail"></inject> and then select Next.

1. In the **Enter password** dialog box, copy and paste Password: <inject key="AzureAdUserPassword"></inject> and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Subscription*, then select **Subscriptions**. 

1. Make sure the **"MOC HOL xxxx"** subscription is shown.

### Task 2: Create a Log Analytics Workspace

In this task, you will create a Log Analytics workspace for use with Microsoft Defender for Cloud.

1. In the Search bar of the Azure portal, type **Log Analytics**, then select **Log Analytics workspaces**.

1. Select **+ Create** from the command bar.

1. Select Resource Group **rg-defender** from the drop down.

1. For the Name, enter something unique like **uniquenameDefender**.

1. Select the default Region 

1. Select **Review + Create**.

1. Once the workspace validation has passed, select **Create**. Wait for the new workspace to be provisioned, this may take a few minutes.

### Task 3: Enable Microsoft Defender for Cloud

In this task, you'll enable and configure Microsoft Defender for Cloud.

1. In the Search bar of the Azure portal, type *Defender*, then select **Microsoft Defender for Cloud**.

1. On the **Getting Started** page, under the **Upgrade** tab, make sure your subscription is selected, and then select the **Upgrade** button at the bottom of the page. Wait for the *Trial started* notification to appear, it takes about 2 minutes.

    >**Hint:** You can click the bell button on the top bar to review your Azure portal notifications.

    >**Note:** If you see the error *"Could not start Azure Defender trial on the subscription"*, continue with the next steps to enable all the Defender plans in Step 5.

1. In the left menu for Microsoft Defender for Cloud, under Management, select **Environment settings**.

1. Select the **"MOC HOL xxxx"** subscription.

1. Review the Azure resources that are now protected with the Defender for Cloud plans.

    >**Important:** If all Defender plans are *Off*, select **Enable all plans**. Select the *$200/month Microsoft Defender for APIs Plan 1* and then select **Save**. Select **Save** at the top of the page and wait for the *"Defender plans (for your) subscription were saved successfully!"* notifications to appear.

1. Select the **Settings & monitoring** tab from the Settings area (next to Save).

1. Review the monitoring extensions. It includes configurations for Virtual Machines, Containers and Storage Accounts. Close the "Settings & monitoring" page by selecting the 'X' on the upper right of the page.

1. Close the settings page by selecting the 'X' on the upper right of the page to go back to the **Environment settings** and select the '>' to the left of your subscription.

1. Select the Log Analytics workspace you created earlier *uniquenameDefender* to review the available options and pricing.

1. Close the Defender plans page by selecting the 'X' on the upper right of the page to go back to the **Environment settings**

### Task 4: Install Azure Arc on an On-Premises Server

In this task, you will install Azure Arc on an on-premises server to make onboarding easier.

>**Important:** The next steps are done on a different machine than the one you were previously working on. Look for the Virtual Machine name references.

1. Click on the Start button, search for **Hyper-V** from the bottom windows search bar, and select to open.

1. Click on WIN1-XXXXX    

1. Select and right-click on the **WINServer** virtual machine from the virtual machine section in the middle and select start, then again right-click on the **WINServer** virtual machine and select **connect**.

   >**Note:** To enable the clipboard Right-click on WIN1-xxxx and select Hyper-V Settings click on **enhanced session mode** and check the **use enhanced mode** click on apply Then restart your virtual machine, once vm starts you will get a configuration pop-up click on show more options and select local resources and make sure the clipboard is selected

1. It asks you to press ctrl+alt+dlt, Go-to **actions** in the top of VM toolbar and click on **ctrl+alt+dlt** (**Skip if not asked**)

1. Select connect and enter the **Password** as `Password.1!!` when prompted.

1. Open the Microsoft Edge browser and navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy, and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Arc*, then select **Azure Arc**.

1. In the navigation pane under **Azure Arc resources** select **Machines**

1. Select **+ Add/Create**, then select **Add a machine**.

1. Select **Generate script** from the "Add a single server" section.

    <!--- 1. Read through the *Prerequisites* tab and then select **Next** to continue.--->

1. In the *Add a server with Azure Arc* page, select the Resource group you created earlier under *Project details*. **Hint:** *rg-defender*

    >**Note:** If you haven't already created a resource group, open another tab and create the resource group and start over.

1. For *Region*, select **(US) East Us** from the drop-down list.

1. Review the *Server details* and *Connectivity method* options. Keep the default values and select **Next** to get to the Tags tab.

1. Review the default available tags. Select **Next** to get to the Download and Run Script tab.

1. Scroll down and select the **Download** button. **Hint:** If your browser blocks the download, take action in the browser to allow it. In Edge Browser, select the ellipsis button (...) if needed and then select **Keep**.

1. Right-click the Windows Start button and select **Windows PowerShell (Admin)**.

1. Enter: cd C:\Users\Administrator\Downloads

    >**Important:** If you do not have this directory, it most likely means that you are on the wrong machine. Go back to the beginning of Task 4 change to WINServer and start over.

1. Type *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* and press enter.

1. Enter **A** for Yes to All and press enter.

1. Type *.\OnboardingScript.ps1* and press enter.  

    >**Important:** If you get the error *"The term .\OnboardingScript.ps1 is not recognized..."*, make sure you are doing the steps for Task 4 in the WINServer virtual machine. Other issues might be that the name of the file changed due to multiple downloads, search for *".\OnboardingScript (1).ps1"* or other file numbers in the running directory.

1. Enter **R** to Run once and press enter (this may take a couple of minutes).

1. The setup process will open a new Edge browser tab to authenticate the Azure Arc agent. Select your admin account, wait for the message "Authentication complete" and then go back to the Windows PowerShell window.

1. When the installation finishes, go back to the Azure portal page where you downloaded the script and select **Close**. Close the **Add servers with Azure Arc** to go back to the Azure Arc **Machines** page.

1. Select **Refresh** until WINServer server name appears and the Status is *Connected*.

    >**Note:** This could take a couple of minutes.

    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
    > - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
    > - Hit the Validate button for the corresponding task. You can proceed to the next task if you receive a success message.
    > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
    > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

      <validation step="0c6dee81-f921-4af0-b0aa-c090d4d61db8" />

### Task 5: Protect an On-Premises Server

In this task, you will manually install the required agent on the Windows Server.

1. On the Lab Virtual machine, navigate to **Microsoft Defender for Cloud** in Azure Portal.

1. Select the **Inventory** from the leftpane.

1. Select **+ Add non-Azure servers** section.

1. Select **Upgrade** next to the workspace you created earlier.  This might take a few minutes, wait until you see the notification *"Defender plans for workspace were saved successfully"*.

1. Select **+ Add Servers** next to the workspace you created earlier.

1. Select **Data Collection Rules**.

1. Select **+ Create**.

1. Enter **WINServer** for Rule Name.

1. Select your *MOC HOL xxxx* subscription and select a Resource Group. **Hint:** *rg-defender*

1. You can keep the default *East US* region or select another preferable location.

1. Select the **Windows** radio button for *Platform Type* and select **Next:Resources**.

1. In the **Resources** tab, **+ Add resources**.

1. In the **Select a scope** page, expand the *Scope* column for **rg-defender** (or the Resource Group you created), then select **WINServer** and select **Apply**.

    >**Note:** You may need to set the column filter for *Resource type* to *Server-Azure Arc* if **WINServer** is not displayed.

1. Select **Next: Collect and deliver**

1. In the **Collect and deliver** tab, select **+ Add data source**

1. In the **Add a data source** page, select **Performance Counters** from *Data source type*.

    >**Note:** For the purposes of this lab you could select *Windows Event Logs*. These selections can be revised later.

1. Click the **Destination** tab

1. Select **Azure Monitor Logs** in the **Destination Type** dropdown

1. Select your *Azure Pass - Sponsorship* subscription from the **Subscription** dropdown

1. Select your workspace name **Hint:** *RG-Defender* from the **Account or namespace** dropdown

1.  Select **Add data source** and select **Review + create**

1. Select **Create** after *Validation passed* is displayed.

1. The **Data Collection Rule** creation initiates the installation of the *AzureMonitorWindowsAgent* extension on **WINServer**.

1. When the *Data Collection Rule* creation completes, enter **WINServer** in the *Search resources, services and docs* search bar, and select **WINServer** from *Resources*.

1. On **WINServer** scroll down through the left menu to *Settings* and *Extensions*.

1. The **AzureMonitorWindowsAgent** should be listed with a *Status* of **Succeeded**.

1. You can move on to the next lab and return later to review the **Inventory** section of **Microsoft Defender for Cloud** to verify that **WINServer** is included.

### Review

In this lab, you have completed the following:

- Able to access the Azure portal and set up a Subscription.
- Created a Log Analytics Workspace
- Enabled Microsoft Defender for Cloud
- Installed Azure Arc on an On-Premises Server.
- Protected an On-Premises Server

## Proceed to Exercise 2
