# Module 7 - Lab 1 - Exercise 7 - Investigate Incidents

### Task 1: Investigate an incident.

In this task, you will investigate an incident.

1. Log in to WIN1 virtual machine with the password as provided in the Environment tab.  

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created earlier.

1. Select the **Incidents** page.

1. Review the list of Incidents

    **Note:** The analytical rules are generating alerts and incidents on the same specific log entry.  This is done to generate more alerts and incidents to be utilized in the lab.
  
1. Select a *Sysmon Startup RegKey* incident.

1. Select **View full details** button.

1. On the left side of the page, change the Status to **Active** and then select **Apply**.

1. In the Tag area, select **+** and add a tag named **RegKey** and select **Ok**.

1. On the middle of the page, select the tab **Comments** tab.

1. Enter in the Comments: *I will research this. *

1. Select the **Comment** button to submit the new comment.

1. Select the **Entities** tab and review.

1. Select the **Alerts** tab.

    **Note:** For the alert shown, notice to the far right there is an option for **View playbooks**.  This allows for the manual execution of a playbook.

1. Select the **Investigate** button.

1. Select the **Sysmon Startup RegKey Alert** graphic.

1.	Select **Timeline** button and review.

1. Select **Info** button and review.

1.	Select **Entities** button and review.

1.	Select the *WIN2* Host graphic (your Windows device name may vary depending on how it was deployed by your lab hoster).

1.	Select **Insights** button and review.

1.	Select **Timeline** button and review.

1.	Select **Info** button and review.

1.	Select **Entities** button and review.

1.	Select **Insights** button and review.

1.	Hover *WIN2* Host in the graph. A menu should appear around the icon.  Select **Related alerts**.

1. Explore the Related Alerts graphs.

## Proceed to Exercise 8
