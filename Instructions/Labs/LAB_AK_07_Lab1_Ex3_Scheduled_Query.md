# Module 7 - Lab 1 - Exercise 3 - Create a Scheduled Query from a template

   ![Picture 1](../Media/sc3.png)

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must learn how to detect and mitigate threats using Microsoft Sentinel. After connecting your data sources to Microsoft Sentinel, you create custom analytics rules to help discover threats and anomalous behaviors in your environment.

Analytics rules search for specific events or sets of events across your environment, alert you when certain event thresholds or conditions are reached, generate incidents for your SOC to triage and investigate, and respond to threats with automated tracking and reMediation processes.

>**Note:** An **[interactive lab simulation](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20a%20scheduled%20query)** is available that allows you to click through this lab at your own pace. You may find slight differences between the interactive simulation and the hosted lab, but the core concepts and ideas being demonstrated are the same. 

## Objectives

After you complete this Exercise, you will be able to:

-  Task 1: Connect the Azure Activity connector.
-  Task 2: Create a Scheduled Query
-  Task 3: Test your new rule
   
### Task 1: Connect the Azure Activity connector.

In this task, you will connect the Azure Activity connector.

1. Log in to WIN1 virtual machine as Admin with the password: Pa55w.rd.

   >**Note:** WIN1 virtual machine is the same one that your using in Excercise 2. only need to login if your logged out otherwise no need to login again.

   >**Note:** If prompted to sign in, In the **Sign in** dialog box, copy and paste the **Username** and **Password** from the Environment tab and select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

    ![Picture 1](../Media/sc-200-19.png)

1. Select the Microsoft Sentinel Workspace you created in the previous labs.

    ![Picture 1](../Media/xx2.png)

1. Select **Content hub** under the Content management from the left pane.

    ![Picture 1](../Media/sc-200-36.png)

1. Search for **Azure Activity (1)** then select it and Click on **Install (2)** from the right pane.

    ![Picture 1](../Media/sc-200-37.png)

1. From the Data Connectors Tab under Configuration, search for the **Azure Activity** connector If doesn't appear just click refresh and select it from the list.

    ![Picture 1](../Media/sc-200-38.png)

1. Select the **Open connector page** on the connector information blade.

    ![Picture 1](../Media/sc-200-39.png)

1. In the Configuration area, scroll down and under ***2. Connect your subscriptions...*** select **Launch Azure Policy Assignment Wizard>**.

    ![Picture 1](../Media/sc-200-40.png)

1. In the **Basics** tab, select the button with the **three dots(...)** under **Scope** to select your subscription from the drop-down list and click **Select**.

1. Select the **Parameters** tab, choose your Microsoft Sentinel workspace from the **Primary Log Analytics workspace** drop-down list.

    ![Picture 1](../Media/sc-200-41.png)

1. Select the **Remediation** tab and mark the **Create a remediation task** checkbox.

    ![Picture 1](../Media/sc-200-42.png)

1. Select the **Review + Create** button to review the configuration.

1. Select **Create** to finish.

    >**Note:** The Azure Activity Connector Sometimes takes moretime than expected to show as connected in data connector tab after creating the azure policy assignment.

### Task 2: Create a Scheduled Query

In this task, you create a scheduled query and connect it to the Teams channel you created in the previous exercise.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

    ![Picture 1](../Media/sc-200-19.png)

1. Select the Microsoft Sentinel Workspace you created in the previous labs.

    ![Picture 1](../Media/xx2.png)

1. Select **Analytics** from the Configuration area.

1. Make sure that you are in the **Rule templates** tab in the command bar and search for the **New CloudShell User** rule.

   ![Picture 1](../Media/sc-200-43.png)

1. From the rule summary blade, make sure you're receiving data by reviewing the under *Data sources: Azure Activity*.

1. Click on the three dots **(...) (1)** then select **Create rule (2)** to continue.

   ![Picture 1](../Media/sc-200-44.png)

1. In the Analytics rule wizard, on the *General* tab, change the *Severity* to **Medium (1)** then click **Next: Set rule logic > (2)** button:

   ![Picture 1](../Media/sc-200-45.png)

1. For the rule query, select **View query results**. You shouldn't receive any results or any errors.

   ![Picture 1](../Media/sc-200-46.png)

1. Close the *Logs* window by selecting the upper right **X** and select **OK** to discard to save changes to go back to the wizard.

1. Scroll down and under *Query scheduling* set the following:

    |Setting|Value|
    |---|---|
    |Run Query every|5 minutes **(1)**|  
    |Lookup data from the last|1 Days **(2)**| 

    >**Note:** We are purposely generating many incidents for the same data. This enables the Lab to use these alerts.

1. Under the *Alert threshold* area, leave the value unchanged since we want the alert to register every event.

1. Under the *Event grouping* area, leave the **Group all events into a single alert (3)** as the selected option since we want to generate a single alert every time it runs, as long as the query returns more results than the specified alert threshold above then click on **Next: Incident settings > (4)** button. 

   ![Picture 1](../Media/sc-200-47.png)

1. On the *Incident settings* tab, review the default options.

1. Select the **Next: Automated response >** button.

1. On the *Automated response* tab under *Automation rules*, select **Add new**.

1. For the *Automation rule name*, enter **Tier 2 (1)**.

1. For the *Actions*, select **Assign owner (2)**.

1. Then select **<inject key="AzureAdUserEmail"></inject> (3)**. Then select **+ Add action (4)**.

   ![Picture 1](../Media/sc-200-48.png)

1. Use the *And then* drop-down menus to select **Run playbook (1)**.

1. A second drop-down menu appears with an *Information (i)* message regarding playbook permissions and a **Manage playbook permissions link**.

    >**Note:** The playbooks will appear grayed out in the drop-down list until permissions are configured.

1. Select the **Manage playbook permissions link**

1. On the *Manage Permissions* page, select the **RG-Playbooks** resource group you created in the previous lab, and select **Apply**.

1. From the drop-down menu, select the playbook **PostMessageTeams-OnIncident (2)** you created in the previous exercise then click on **Apply (3).**

   ![Picture 1](../Media/sc-200-49.png)

1. Select the **Next: Review and create >** button.
  
1. Select **Save**.

### Task 3: Test your new rule

In this task, you test your new scheduled query rule.

1. In the top bar of the Azure portal, Select the icon **>_** that corresponds to the Cloud Shell. You might need to select the ellipsis icon first **(...)** if your display resolution is too low.

   ![Picture 1](../Media/xs5.png)

1. In the *Welcome to Azure Cloud Shell* window, select **Powershell**.

1. On the *Getting started* page, select **Mount storage account**, and then select your **Subscription** from the *storage account subscription* drop-down menu item and select the **Apply** button.

   ![Picture 1](../Media/xs6.png)

   >**Important:** Do not select the *No storage account required* radio button option. This will cause the incident creation to fail.

1. On the *Mount storage account* page, select **We will create a storage account for you**, and then select **Next**.

1. Wait until the Cloud Shell is provisioned, then close the Azure Cloud Shell window.

1. In the Search bar of the Azure portal, type *Activity* and then select **Activity Log**.

   ![Picture 1](../Media/sc-200-50.png)

1. Make sure the following *Operation name* items appear: **List Storage Account Keys** and **Update Storage Account Create**. These are the operations that the KQL query you reviewed earlier will match to generate the alert. **Hint:** You might need to select **Refresh** to update the list.

   ![Picture 1](../Media/sc-200-51.png)

    >**Note:** You might not see the output of the logs at the Activity log, this might take sometime 30 mins or longer.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. Select the **Incidents** menu option under *Threat management*.

1. Select the **Auto-refresh incidents** toggle.

   ![Picture 1](../Media/xs7.png)

1. You should see the newly created Incident.

    >**Note:** The event that triggers the incident may take time to process. Continue with the next exercise, you will come back to this view later.

1. Select the Incident and review the information in the right blade.

1. Go back to Microsoft Teams by selecting the tab in your Microsoft Edge browser. If you closed it, just open a new tab and type https://teams.microsoft.com. Go to the *SOC* Teams, select the *New Alerts* channel and see the message post about the incident.

    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   - If you receive a success message, you can proceed to the next task.
   - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
 
   <validation step="d771d20d-c2d8-410c-8b53-a1ccd733741e" />

## Review

 In this exercise, you enhanced security monitoring by first connecting the Azure Activity connector to gather activity logs. Then, you created a scheduled query for automated log analysis and finally tested the new rule to ensure it functions as expected

## Proceed to Exercise 4
