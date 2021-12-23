# Module 7 - Lab 1 - Exercise 1 - Activate a Microsoft Security rule

## Lab scenario

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must learn how to detect and mitigate threats using Microsoft Sentinel.  You need to enable alerts from other Microsoft 365 and Azure services.  


### Task 1: Activate a Microsoft Security Rule

In this task, you will activate a Microsoft Security rule.

1. Log in to WIN1 virtual machine with the password as provided in the Environment tab. 

1. In the Edge browser, navigate to the Azure portal at (https://portal.azure.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created in the previous labs.

1. Select **Analytics** from the Configuration area, then select the **Rule templates** tab.

1. In the search box on the Rule templates tab, enter *defender*.

1. In the result set, select **Create incidents based on Microsoft Defender for Endpoint alerts**. 

1. On the right blade, select **Create rule** button.

1. Change *Filter by Severity* to **Custom**.

1. Select **High** for the severity level.

1. Select the **Next : Automated response >** button and then select **Next: Review >** button.

1. Review the changes made and select the **Create** button.  The Analytics rule will be saved.

# Proceed to Exercise 2
