# Module 7 - Lab 1 - Exercise 8 - Create workbooks

## Lab scenario

You're a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You must design workbooks with advanced visualizations.


### Task 1: Explore Workbooks.

In this task, you will explore the configuration of a workbook.

1. Login to WIN1 virtual machine with the password as provided in the Environment Tab.  

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. Select **Workbooks** in the **Portal** menu.

1. Select **Identity & Access**, then select the **View template** button.

1. Review the Identity & Access workbook.

1. Close the workbook by selecting the 'x' in the top-right corner. You should be in the **Microsoft Sentinel - Workbooks - Templates** tab.

1. In the *Templates* tab search for and select **Azure AD Audit logs**, then select the **Save** button from the right pane. 

1. Select the location that is appropriate for your location and select **OK**. The appropriate location usually defaults.

1. Select the **View saved workbook** button.

1. Select **Edit** in command bar.

1. In the *User activities* area, take a look at the colors in the graph for "Operations count" and "Trend". Then select **Edit** below the grid.

#### To format columns, the Column setting panel provides customization options, do the following:

1. Select the **Column Settings** button in the right of the Query Command bar.

    **Note:** This button only appears if there is data in the report.

1. In the *Edit column settings* blade select the column **Operations Count (Heatmap + Formatted)**.

1. Review the settings, specially the options for *Column renderer*. For *Color palette*, select **32-color categorical**.

1. Select the column **Trend (Spark line + Formatted)**.

1. Review the settings, For *Column renderer* select **Spark area** and select the color of your choosing in *Color palette*.

1. Select **Save and Close**.

#### To have one tile/grid control filter the results in another tile/grid do the following:

1. Select the **Advanced Settings** button in the *Editing query item: query - 2*.

1. Review the *When items are selected, export parameters* setting. Notice the *UserInfo* field is selected.

1. Select **Done Editing** at the bottom of the query (not the top menu).

1. Select **Edit** below the *Top active users* grid on the right side of the screen.  

1. In the query, locate *UserInfo*. The query is using the parameter exported from the other query to filter results.

1. Select **Done Editing** at the bottom of the query (not the top menu).

1. Select **Done Editing** at the top menu for the workbook and select the **Save** icon. Close the workbook by selecting the 'x' in the top-right corner.


### Task 2: Create a Workbook.

In this task, you will create a new workbook with advanced visualizations.

1. Go back to the **Workbooks** area of the Microsoft Sentinel portal.

1. Select **+ Add workbook**

1. Select **Edit**

#### Edit Header text:

4. Select **Edit** below the title of the workbook to change *## New workbook* to *## My workbook*.

5. Select **Done Editing** on the bottom menu, for the Header text.

6. Select **Edit** below the only visible graph.

7. Review the KQL statement that provides a union of counts across multiple tables.

8. Select the **Done Editing** on the bottom menu, for the Graph.

9. Select **...** next to the graph area, then select **+ Add**, then select **Add query**.

10. Enter *SecurityEvent* into the query box, then select the **Run Query** button.

11. Change the *Time Range* to **Last 3 days**.

12. Change the *Visualization* to **Bar chart** and see the results.

13. Change the *Visualization* to **Time chart** and see the results.

14. Select **Style** from the Query tab.

15. Select the **Make this item a custom width** box.

16. Set the Percent width to **75** and Maximum width to **75**.

17. Select **Advanced Settings** from the Query tab.

18. Select **Show refresh icon when not editing** box. 

19. Select **Done Editing** on the bottom menu, for the new Graph.

20. At the bottom of the Workbook select **Add**, then **Add query**.

Enter the following KQL command for the query:

```KQL
SecurityEvent
```

21. For Time Range, select **Last 4 hours**.

22. Change the Visualization to **Grid**.

23. Select the **Style** tab.

24. Select **Make this item a custom width**.

25. Change percentage width to **25** and maximum width to **25**. 

26. Select **Done Editing** on the bottom menu, for the new Query.

27. Select **Done Editing** for the Workbook.

28. Select the **Save** icon, change the *Title* to *My Workbook* and select **Save** again.

29. Close the workbook by selecting the 'x' at the top-right or select **Workbooks** in the Microsoft Sentinel portal.

30. Select the **My workbooks** tab if needed.

31. Select the workbook you just created.

32. Select **View saved workbook**.

## You have completed the lab.
