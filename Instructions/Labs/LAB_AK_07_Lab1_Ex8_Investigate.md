# Module 7 - Lab 1 - Exercise 8 - Investigate Incidents

### Task 1: Investigate an incident.

In this task, you will investigate an incident.

1. Log in to WIN1 virtual machine with the password as provided in the Environment tab.  

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created earlier.

1. Select the **Incidents** tab from Threat management area.

1. Review the list of Incidents

    **Note:** The analytical rules are generating alerts and incidents on the same specific log entry.  This is done to generate more alerts and incidents to be utilized in the lab.
    
1. Select one of the *MDE Startup RegKey* incidents.

1. Review the incident details on the right blade that opened. Scroll down and select the **View full details** button.

1. On the left blade of the incident, change the Status to **Active** and then select **Apply**.

1. Scroll down to the *Tags* area, select **+** and type **RegKey** and select **OK**.

1. On the middle pane, select the tab **Comments** tab.

1. Type in the comments box: *I will research this* and select the **Comment** button to submit the new comment.

1. Select the **Alerts** tab. For the *MDE Startup RegKey* alert, slide right using the bar and notice the **View playbooks** link. This allows manual execution of a playbook from the alert, rather than triggering it from the *Automated response* tab within an Analytics rule.

1. From the left pane, scroll down and select the **Investigate** button. **Hint:** If the icons are too small for your screen, select **(+)** to magnify them.

1. Hover the **ODL_user_xxx@mocholxxxx.onmicrosoft.com** entity icon and wait for new *exploration queries* to be shown. It looks that *Related Alerts* has more data on it. Select the name of the exploration query **Related Alerts** to bring them to the investigation graph or select **Events >** to investigate them with a KQL query.

1.	When you select an entity, a window on the right opens for more detailed information. Review the **Info** page.

1. Select **Timeline** button. Hover the first two incidents and see which things on the graph occurred at what point in time.

1. Select **Entities** button and review the *Entities* and *Alerts* related to *ODL_user_xxx@mocholxxxx.onmicrosoft.com*.

1. Close the investigation graph by selecting the **X** in the top right of the page.

  
## Proceed to Exercise 9
