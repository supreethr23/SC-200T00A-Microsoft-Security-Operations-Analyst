# Module 8 - Lab 1 - Exercise 1 - Connect data to Microsoft Sentinel using data connectors

## Lab scenario

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must learn how to connect log data from the many data sources in your organization. The organization has data from Microsoft 365, Microsoft 365 Defender, Azure resources, non-azure virtual machines, etc. You start connecting the Microsoft sources first.

>**Important:** The lab exercises for Learning Path #8 are in a *standalone* environment. If you exit the lab before completing it, you will be required to re-run the configurations again.

## Lab objectives
 In this lab, you will perform the following:
- Task 1: Access the Microsoft Sentinel Workspace
- Task 2: Connect the Microsoft Defender for Cloud data connector
- Task 3: Connect the Azure Activity data connector

### Estimated timing: 20 minutes

## Architecture Diagram

  ![Picture 1](../Media/mod8arch.png)

### Task 1: Access the Microsoft Sentinel Workspace

In this task, you will access your Microsoft Sentinel workspace.

1. In the Search bar of the Azure portal, type **Log Analytics**, then select **Log Analytics workspaces**.

   ![](../Media/l8e132.png)

1. Select **+Create** from the command bar.

   ![](../Media/l8e133.png)

1. Select Resource Group **RG-Defender**  from the drop down.

1. For the Name, enter **uniquenameDefender**.

1. Select **Review + Create**.

   ![](../Media/l8e134.png)

1. Once the workspace validation has passed, select **Create**. Wait for the new workspace to be provisioned, this may take a few minutes.

    ![](../Media/l8e135.png)
 
1. In the Search bar of the Azure portal, type **microsoft sentinel**, then select **Microsoft Sentinel**.

   ![](../Media/l8e129.png)

1. Select **+Create** from the command bar.

 1. Select the newly created workspace and click on **Add**.
  
    ![](../Media/l8e131.png)

1. Select your Microsoft Sentinel Workspace that you created in the previous lab.

### Task 2: Connect the Microsoft Defender for Cloud data connector

In this task, you will connect the Microsoft Defender for Cloud data connector.

1. In the Microsoft Sentinel left menus, scroll down to the **Content management** section and select **Content Hub**.

1. In the *Content hub*, search for the **Microsoft Defender for Cloud** solution and select it from the list.

1. On the *Microsoft Defender for Cloud* solution details page select **Install**.

   ![](../Media/l8e136.png)

1. When the installation completes,  search for the **Microsoft Defender for Cloud** solution and select it.

1. On the *Microsoft Defender for Cloud* solution details page select **Manage**.

    ![](../Media/l8e137.png)

    >**Note:** The *Microsoft Defender for Cloud* solution installs the *Subscription-based Microsoft Defender for Cloud (Legacy)* Data connector, the *Tenant-based Microsoft Defender for Cloud (Preview)* Data connector, and an Analytics rule. The *Tenant-based Microsoft Defender for Cloud (Preview)* Data connector is used when a tenant has multiple subscriptions.

1. Select the *Subscription-based Microsoft Defender for Cloud (Legacy)* Data connector check-box, and select **Open connector page**.

   ![](../Media/l8e138.png)

1. In the *Configuration* section, under the *Instructions* tab, **select** the checkbox for your subscription and slide the **Status** option to the right.

    ![](../Media/l8e139.png)

    >**Note:** If it switches back to disconnected, please review the Learning Path 3, Exercise 1, Task 1 to assign the proper permissions to your account.

1. The *Status* should be now **Connected** and "Bi-directional sync" should be *Enabled*.

    ![](../Media/l8e140.png)

    <!--- 1. Scroll down and under the *Create incidents - Recommended!* area, verify that *Create incidents automatically from all alerts generated in this connected service* is **Enabled**. --->

### Task 3: Connect the Azure Activity data connector

In this task, you will connect the *Azure Activity* data connector.

1. In the Microsoft Sentinel left menus, scroll down to the *Content management* section and select **Content Hub**.

1. In the *Content hub*, search for the **Azure Activity** solution and select it from the list.

1. On the *Azure Activity* solution page select **Install**.

   ![](../Media/l8e141.png)

1. When the installation completes select **Manage**

    >**Note:** The *Azure Activity* solution installs the *Azure Activity* Data connector, 12 Analytic rules, 14 Hunting queries and 1 Workbook.

1. Select the *Azure Activity* Data connector and select **Open connector page**.

    ![](../Media/l8e143.png)

1. In the *Configuration* area under the *Instructions* tab, scroll down to "2. Connect your subscriptions...", and select **Launch Azure Policy Assignment Wizard>**.

    ![](../Media/l8e142.png)

1. In the **Basics** tab, select the ellipsis button (...) under **Scope** and select your subscription from the drop-down list and click **Select**.

    ![](../Media/l8e144.png)

1. Select the **Parameters** tab, choose your *uniquenameDefender* workspace from the **Primary Log Analytics workspace** drop-down list. This action will apply the subscription configuration to send the information to the Log Analytics workspace.

    ![](../Media/l8e145.png)

1. Select the **Remediation** tab and select the **Create a remediation task** checkbox. This action will apply the policy to existing Azure resources.

1. Select the **Review + Create** button to review the configuration.

1. Select **Create** to finish.

## Review
In this lab, you have completed the following:
- Accessed the Microsoft Sentinel Workspace
- Connected the Microsoft Defender for Cloud data connector
- Connected the Azure Activity data connector

## Select **Next** to continue to Lab 2.
