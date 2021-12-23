# Module 7 - Lab 1 - Exercise 2 - Create a Playbook

### Task 1: Create a Security Operations Center Team in Microsoft Teams.

In this task, you will create a Microsoft Teams team for use in the lab.

1. Log in to WIN1 virtual machine with the password as provided in the Environment tab.  

1. In the Edge browser, open a new tan and navigate to the Microsoft Teams portal at (https://teams.microsoft.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. Close any Teams pop-ups that may appear.

1. If not already selected, select **Teams** on the left menu, then at the bottom, select **Join or create a team**.

1. Select the **Create Team** button in the main window.

1. Select the **From scratch** button.

1. Select the **Private** button.

1. Give the team the name: **SOC** and select the **Create** button.

1. In the Add members to SOC screen, select the **Skip** button. 

1. Select the **...** next to the newly created SOC team and select **Add channel**.

1. Enter a channel name of *New Alerts* then select the **Add** button.


### Task 2: Create a Playbook in Microsoft Sentinel.

In this task, you will create a Logic App that will be used as a Playbook in Microsoft Sentinel.

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created earlier.

1. Select the **Community** page in the *Content management* area on the left side of the page.

1. Select the **Onboard community content** link on the right pane. This will open a new tab in the Edge Browser for Microsoft Sentinel GitHub content.

1. Select the **Playbooks** folder.

1. Select the **Post-Message-Teams** folder.

1. In the readme.md box, go below the second *Quick Deployment* option **Deploy with alert trigger** and select **Deploy to Azure** button.  

    **VERY IMPORTANT**: Be aware that they are two different Microsoft Sentinel triggers to use, Incident and Alert. Make sure you are selecting the Alert (second) one.

1. Make sure your Azure Subscription is selected.

1. For Resource Group, select **Create New** and enter *RG-Playbooks* and select **OK**.

1. For region, select the appropriate region for your situation. The default region will likely be optimal.

1. Make sure the *Playbook Name* is "PostMessageTeams-OnAlert" and select **Review + create**.

1. Now select **create**.

    **Note:** Wait for the deployment to finish before proceeding to the next task. It may take a couple minutes to deploy.


### Task 3: Update a Playbook in Microsoft Sentinel.

In this task, you will update the new playbook you created with the proper connection information.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. Select the **Automation** from the Configuration area and then select the **Active Playbooks** tab.

1. Select the **PostMessageTeams-OnAlert** playbook.

1. On the Logic App page for *PostMessageTeams-OnAlert*, in the center menu, select **Edit**.

1. Select the *first* block **When a response to an Microsoft Sentinel alert is triggered**.

1. Select the **Change connection** link.

1. Select **Add new** and select **Sign in**. In the new window, select your Azure subscription admin credentials when prompted.

1. Now select the *second* block **Alert - Get incident**.

1. Select the **Change connection** link.

1. Select the connection that has your Azure subscription admin credentials under *Display Name*. **Hint:** ODL_USER_ID@ZZZZZZ.onmicrosoft.com.

1. Now select the *third* block **Connections**.

1. Select **Add new** and select your Azure subscription admin credentials when prompted.

1. Now in the **Post a message (V3)** block, at the end of the Team box, select the **X** to clear the contents. The edit box will be changed to a dropdown with a listing of the available teams from Microsoft Teams.  Select **SOC**.

1. Do the same for the Channel, select the **X** at the end of the edit box to clear the contents. The edit box will be changed to a dropdown with a listing of the Channels. Select **New Alerts**.

1. Select **Save** on the command bar.

The Logic App will be used in a future lab.

## Proceed to Exercise 3
