# Module 7 - Lab 1 - Exercise 8 - Create workbooks

## Lab scenario

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. Once you have connected your data sources to Microsoft Sentinel, you can visualize and monitor the data using the Microsoft Sentinel adoption of Azure Monitor Workbooks, which provides versatility in creating custom dashboards. 

Microsoft Sentinel allows you to create custom workbooks across your data and also comes with built-in workbook templates to allow you to quickly gain insights across your data as soon as you connect a data source.

## Objectives

After you complete this Exercise, you will be able to:

-   Task 1: Explore workbook templates
-   Task 2: Save and modify a workbook template
-   Task 3: Create a Workbook

### Task 1: Explore workbook templates

In this task, you will explore the Microsoft Sentinel workbook templates.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

    ![Picture 1](../Media/sc-200-19.png)

1. Select the Microsoft Sentinel Workspace you created in the previous labs.

    ![Picture 1](../Media/xx2.png)

1. Select **Workbooks (1)** under the *Threat Management* left blade. Navigate to *Templates* tab.

1. Search for and select the **Azure Activity (2)** template workbook. In the right pane, scroll down and select the **View template (3)** button.

    ![linux login](../Media/sc-200-69.png)   

1. Review the contents of the workbook. It shows insights into your Azure subscription operations by collecting and analyzing the data from the Activity Log.

    ![linux login](../Media/m3.png)  

1. Close the workbook by selecting the **X** in the top-right corner.

### Task 2: Save and modify a workbook template

In this task, you will save a workbook template and modify it.

1. You should be back in the **Microsoft Sentinel - Workbooks - Templates** tab. Scroll down again and select the **Save** button for the *Azure Activity* workbook. 

1. Leave **East US** as the default value for *Region* and select **yes**.

1. Select the **View saved workbook** button.

1. Select **Edit** in the command bar to enable changes in the workbook.

1. Scroll down to the *Caller activities over time* area, and look at the color of the *Activities* column since we are going to format those columns. Select the **Edit** button below the grid.

   ![linux login](../Media/m4.png)  

1. Select the **Column Settings** button, it is located to the right of the *Run Query* command bar. **Hint:** This button only appears if there is data from the KQL query.

   ![linux login](../Media/m5.png)  

1. In the *Edit column settings* blade that appears, within *Columns* select **Activities**.

1. Change the value for *Column renderer* to **Heatmap**. For *Color palette*, scroll down to select **32-color categorical**.

1. Select **Save and Close**. Notice the change in the *Activities* column.

   ![linux login](../Media/m6.png)  

1. Select **Done Editing** at the bottom of the query (not the top menu).

1. Now select **Done Editing** at the top menu and select the **Save** icon. 

1. Close the workbook by selecting the **X** in the top-right corner and observe the change.

   >**Note:** If you don't find the results it might take some to populate. Please proceed with the next task.
  
### Task 3: Create a Workbook

In this task, you will create a new workbook with advanced visualizations.

1. You should be back at the **Workbooks (1)** area of the Microsoft Sentinel portal then  select **+ Add workbook (2)** to create a new workbook from scratch. 

    ![Picture 1](../Media/sc-200-8-1.png)

     >**Note:** Although it is a new workbook, a startup template is used.

1. To edit the workbook, select **Edit**.

1. Select the **Edit** button below the first paragraph of the workbook.

    ![Picture 1](../Media/sc-200-8-2.png)

1. Type *# My workbook* in a new line on top of **## New workbook (1).**

1. Select **Done Editing (2)** on the bottom of this section, *Editing text item: text - 2*. Notice that your header increased in size and name changed.

    ![Picture 1](../Media/sc-200-8-3.png)

1. Select **Edit** below the only visible bar chart graph.

    ![Picture 1](../Media/sc-200-8-4.png)

1. Review the KQL statement that provides a *union* statement of counts across all tables. **(1)**

1. Scroll down and select the **Done Editing (2)** on the bottom menu, for the *Editing query item: query - 2*.

    ![Picture 1](../Media/sc-200-8-6.png)

1. Select the ellipsis **... (1)** next to the *Edit* button of the barchart graph, then select **+ Add (2)**, then select **Add query (3)**.

    ![Picture 1](../Media/sc-200-8-7.png)

1. Type **SecurityEvent (1)** into the query box.

1. Change the *Time Range* to **Last hour (2)**.

1. Change the *Visualization* to **Time chart (3)**.

    ![Picture 1](../Media/sc-200-8-8.png)
   
1. Select the **Style (1)** tab from the query's command bar then select the **Make this item a custom width (2)** box then set the *Percent width* to ***25*** **(3)** and *Maximum width* to ***25*** **(4)**.

    ![Picture 1](../Media/sc-200-8-9.png)

1. Now select the **Advanced Settings (1)** tab from the query's command bar.

1. Select **Show refresh icon when not editing (2)** box. 

1. Scroll down and select **Done Editing (3)** on the bottom menu, for the new *Editing query item: query - 2*.

    ![Picture 1](../Media/sc-200-8-10.png)

1. Scroll down and at the bottom of the workbook select **+ Add (1)** drop-down, then **Add query (2)**.

    ![Picture 1](../Media/sc-200-8-11.png)

1. Type **SecurityEvent (1)** into the query box.

1. Change the *Time Range* to **Last hour (2)**.

1. Change the *Visualization* to **Grid (3)**.

    ![Picture 1](../Media/sc-200-8-12.png)

1. Select **Style (1)** from the query's command bar then select **Make this item a custom width (2)** box then set the *Percent width* to ***75*** **(3)** and *Maximum width* to ***75*** **(4)** and then scroll down and select **Done Editing (5)** on the bottom menu, for the new *Editing query item: query - 3*.

    ![Picture 1](../Media/sc-200-8-13.png)

1. Select **Done Editing** in Workbook's top command bar.

    ![Picture 1](../Media/sc-200-8-14.png)

1. Select the **Save** icon.

    ![Picture 1](../Media/sc-200-8-15.png)

1. On the **Save As** page, change the *Title* to **My Workbook (1)** then select the **RG-Defender (2)** resource group if needed and leave other values as default and then click on **Save As (3)** to commit the changes. 

    ![Picture 1](../Media/sc-200-8-16.png)

1. Close the workbook by selecting the **X** at the top-right or select **Workbooks** in the Microsoft Sentinel portal.

1. Back in the *Workbooks* page, select the **My Workbooks (1)** tab and then select the workbook you just created, **My Workbook (2)**.

    ![Picture 1](../Media/sc-200-8-17.png)

1. On the right pane, select **View saved workbook** to review your workbook.

    ![Picture 1](../Media/sc-200-8-18.png)

## Review

In this exercise, you explored workbook templates to familiarize yourself with pre-built visualizations, then saved and modified a template to suit your needs. Finally, you created a custom workbook to analyze and display security data in a tailored format.

## Proceed to Exercise 9
