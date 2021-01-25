---
description: "Learn more about: Search"
title: Search
TOCTitle: Search
ms:assetid: 34c39cf2-4684-4a76-833d-427dd9aead11
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559540(v=BTS.80)
ms:contentKeyID: 51527231
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts06.bam.portal.default
---

# Search

 

An activity search allows you to perform searches against BAM data to find activities that match criteria you specify, based on tracked values and items available in a BAM view, and to display the activities so that you can edit them or create alerts based on them.

Queries can be saved and reused. You can also use them as the basis for an alert, for example, "Notify me any time a purchase order arrives from the specified customer." You use the buttons at the top of the content page to save, open, and run queries, as well as to set alerts.

The Activity Search page is divided into three main sections inside the Content frame:

  - **Query**: This section allows users to search for activities by building search clauses based on specific tracked data items. The user can add and remove clauses as required.

  - **Column Chooser**: This section allows users to specify which items of data, from those available in that view, to return if any records match the search criteria.

  - **Results**: Results of the query display in this section. Clicking a row in the returned results opens the Activity Status page.

### To open a query

1.  On Computers running Windows; click **Start**, point to **All Programs**, right-click **Internet Explorer**, and then click **Run as administrator**. In the **User Account Control** dialog box, click **Continue**. In the Internet Explorer address bar, type `http://<server>/BAM`, where *\<server\>* is the name of the computer that is running the BAM portal.
    
    \-- or --
    
    Click **Start**, click **All Programs**, point to **Microsoft BizTalk Server 20xx**, and then click **BAM Portal Web Site**.

2.  In the **My Views** frame of the portal, click an existing view to expand the menus available to that view.

3.  Click **Activity Search** to expand the list of activities available for the view.

4.  Click an activity from the list. This will load the Activity Search page for the selected activity.

5.  In the content frame, at the top of the page, click the **Browse** button to open the **Choose File** dialog box.

6.  Browse to the folder where you have previously saved queries.

7.  Click a saved query.

8.  Click the **Open** button. This will load the path to the query in the text box to the left of the **Browse** button. You can also type the path to the query directly into the text box.

9.  Click the **Open Query** button to the right of the **Browse** button.

### To construct a query

1.  On Computers running Windows; click **Start**, point to **All Programs**, right-click **Internet Explorer**, and then click **Run as administrator**. In the **User Account Control** dialog box, click **Continue**. In the Internet Explorer address bar, type `http://<server>/BAM`, where *\<server\>* is the name of the computer that is running the BAM portal.
    
    \-- or --
    
    Click **Start**, click **All Programs**, point to **Microsoft BizTalk Server 20xx**, and then click **BAM Portal Web Site**.

2.  In the **My Views** frame of the portal there is a list of currently configured views. Under each view there are three tasks that can be performed for that view. If the view is currently collapsed, click the existing view to expand the list of tasks.

3.  Click **Activity Search** to expand the list of activities available for the view.

4.  Click an activity from the list. This will load the **Activity Search** page for the selected activity.

5.  In the content frame, in the **Query** box, choose a field from the **Business Data** drop-down list to use for a comparison in the query.

6.  From the **Operator** drop-down list, select the comparison operator to use.

7.  In the **Value** box, enter the value to compare against. You will only be able to enter a value appropriate to the field to which you are comparing. (If the business data item is a date field, then the comparison data is a date or date time formatted as appropriate for your culture settings.)

8.  If you have more clauses to add to the query, click the **Add** button to the right of the query box. This will add a new line for the next clause. You can select whether the clauses are joined by using AND or OR.
    

    > [!NOTE]
    > <P>You cannot group clauses to form more complex queries. A query is a simple set of clauses joined by an AND or an OR operator.</P>

    

    > [!NOTE]
    > <P>If you click the back button during these procedures and receive a message ("warning: page has expired"), you can press F5 to get your original contents back. You may have to press F5 several times.</P>



9.  In the Column Chooser, select the data or milestones from the **Available Data and Milestones** list box for the query to return as data. You can select multiple items by holding down the SHIFT key and clicking the first and last items in the group you want to return. You can also select multiple items from the list by holding down the CTRL key and selecting the items to return.

10. Use the **\>\>** button to move the selected items to the **Items to show** list box. You can remove items from this list by selecting them and using the **\<\<** button to move them back to the data and milestones list box.

11. Once you have selected all the items that the query will return, you can rearrange the results to determine in what order the columns are shown. To move a column to the first position in the returned data set, select it by clicking it and clicking the **Move Up** button until it is at the top of the list of items. Similarly, to move an item to a later position in the returned data set, select the item by clicking it and then clicking the **Move Down** button until it is in the position in which you want it to display.

### To save a query

1.  In the content frame, at the top of the page, click the **Save Query** button to open the **Save File** dialog box.

2.  On the **File Download** dialog box, click the **Save** button.

3.  Browse to the location where you want to save the query.

4.  You can accept the default name provided for the query or you can enter a new name in the **File Name** text box.

5.  Click the **Save** button.

### To execute a query

1.  On Computers running Windows; click **Start**, point to **All Programs**, right-click **Internet Explorer**, and then click **Run as administrator**. In the **User Account Control** dialog box, click **Continue**. In the Internet Explorer address bar, type `http://<server>/BAM`, where *\<server\>* is the name of the computer that is running the BAM portal.
    
    \-- or --
    
    Click **Start**, click **All Programs**, point to **Microsoft BizTalk Server 20xx**, and then click **BAM Portal Web Site**.

2.  In the **My Views** frame of the portal, click an existing view to expand the menus available to that view.

3.  Click **Activity Search** to expand the list of activities available for the view.

4.  Click an activity from the list. This will load the Activity Search page for the selected activity.

5.  Either open an existing query or build a new query.

6.  In the content frame of the portal, click the **Execute Query** button.

## See Also

[Alert Manager](alert-manager.md)

