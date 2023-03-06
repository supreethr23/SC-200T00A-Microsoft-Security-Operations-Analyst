# Module 7 - Lab 1 - Exercise 1 - Activate a Microsoft Security rule

## Lab scenario

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must learn how to detect and mitigate threats using Microsoft Sentinel.  You need to enable alerts from other Microsoft 365 and Azure services.  


### Task 1: Create a Log Analytics Workspace

In this task, you will create a Log Analytics workspace for use with Microsoft Defender for Cloud.

1. Log in to WIN1 virtual machine with the password as provided in the Environment tab. 

1. In the Edge browser, navigate to the Azure portal at (https://portal.azure.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type **Log Analytics**, then select **Log Analytics workspaces**.

1. Select **+Create** from the command bar.

1. Select **RG-Defender** from the drop down.

1. For the Name, enter something unique like **uniquenameDefender**.

1. Select **Review + Create**.

1. Once the workspace validation has passed, select **Create**. Wait for the new workspace to be provisioned, this may take a few minutes.

### Task 2: Initialize the Microsoft Sentinel Workspace.

In this task, you will create a Microsoft Sentinel workspace.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select **+ Create**.

1. Next, In Add Microsoft Sentinel to a workspace page.

1. Select your existing workspace that was created in the previous lab, then select **Add**. This could take a few minutes.

1. Navigate around the newly created Microsoft Sentinel workspace to become familiar with the user interface options.

### Task 3: Connect the Microsoft Defender for Cloud connector.

In this task, you will connect the Microsoft Defender for Cloud connector.

1. In the Configuration area select **Data connectors**.  In the Data Connectors page, search for the **Azure Active Directory** connector and select it from the list.

1. From the Data Connectors tab, search for the **Microsoft Defender for Cloud** connector and select it from the list.

1. Select the **Open connector page** on the connector information blade.

1. In the **Configuration** area, under Subscription, select the checkbox for the "Azure Pass - Sponsorship" subscription and slide the **Status** option to the right to indicate **Connected**.

1. The "Status" should be now *Connected* and "Bi-directional sync" should be *Enabled*.

1. Scroll down and under the "Create incidents - Recommended!" area, select **Enable**. This option creates an Analytics rule automatically for this service. You can manually add it later if not enabled here or change its configuration within the *Analytics* blade.

### Task 4: Activate a Microsoft Security Rule

In this task, you will activate a Microsoft Security rule.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created in the previous labs.

1. Select **Analytics** from the Configuration area. By default, you will see the *Active rules*.

1. Select the **Create incidents based on Microsoft Defender for Cloud**.

1. On the right blade, select the **Edit** button.

1. Scroll down the page and under "Analytics rule logic - Filter by Severity", select the *Custom* drop-down list.

1. Unselect **Low** for the severity level and go back to the rule.

1. Select the **Next: Automated response** button and then select **Next: Review** button.

1. Review the changes made and select the **Save** button. The Analytics rule will be saved.

## Proceed to Exercise 2
