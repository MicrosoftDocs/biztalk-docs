---
title: "Defining Data in BAM | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggregations [BAM], dimensions"
  - "monitoring business activities [BAM], BAM Activity Wizard"
  - "monitoring business activities [BAM], time intervals"
  - "aggregations [BAM], measurements"
  - "monitoring business activities [BAM], views"
  - "monitoring business activities [BAM], aggregations"
  - "Excel add-in [BAM], collecting data"
  - "aggregations [BAM], scheduling"
  - "monitoring business activities [BAM], milestone groups"
  - "aggregations [BAM], real-time data"
ms.assetid: 501a1c08-3979-4a99-94d9-0d1b5ec4266b
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defining Data in BAM
You use the BAM Excel Add-in to define the data you want BAM to collect, and define the way in which the data will be shared. You use BAM activities to define the data, and you use BAM views to define the data that other users can see.  
  
## Activities  
 You create a BAM activity to define information about a business process that you want to monitor with BAM. A BAM activity represents a specific business process in the business, such as handling purchase orders or shipping a product. A business process has a defined set of milestones and business data. For example, a purchase order process might have milestones such as Approved, Denied, and Delivered along with business data like Customer Name and Product.  
  
 The intention of a BAM activity is to show the history (milestones) and data about a process to information workers. BAM activities are high-level abstractions that are independent of the actual implementation of BizTalk Server. For a conceptual overview of BAM, see the topic "Business Activity Monitoring" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
 You use the BAM Activity Wizard to define BAM activities that contain at least one activity item. You group related activity items in an activity, and you use activity items to describe the type of data you want to make available from a business process.  
  
 The following table describes the types of activity items BAM provides.  
  
|Item type|Description|  
|---------------|-----------------|  
|Business Milestone|A date/time value. For example, an approval date for a purchase order.|  
|Business Data - Text|A string containing any alphanumeric characters. For example, Ship to: City, State/Province and Zip/Postal code.|  
|Business Data - Integer|A whole number value. For example, the total number of purchases.|  
|Business Data - Float|A decimal value. For example the total dollar amount of the PO.|  
  
 For example, in a purchase order activity, you might create the activity items in the following table.  
  
|Activity item|Item type|  
|-------------------|---------------|  
|Product|Business Data — Text|  
|City|Business Data — Text|  
|State|Business Data — Text|  
|Amount|Business Data — Float|  
|Quantity|Business Data — Integer|  
|Approved|Business Milestone|  
|Delivered|Business Milestone|  
|Denied|Business Milestone|  
|Received|Business Milestone|  
  
 Note that Amount is a float because it may be a decimal value. Quantity is an integer because it will always be a whole number in this example. Approved, Delivered, Denied, and Received are all milestones in the purchase order process.  
  
## Views  
 You create views to expose data from an activity to users. When you create a view based on the purchase order activity, you define the data behind the activity items. You define view data in BAM as dimensions, measures, durations, milestone groups, and progress dimensions.  
  
 A view contains one or more view items. You can create the following types of view items:  
  
-   Durations  
  
-   Milestone groups  
  
-   Aggregations  
  
### Durations  
 Durations are time intervals. Durations are described in terms of the milestones that define the start and end of time intervals. The following table shows the durations you can make from the milestones listed in the previous table.  
  
|Duration|Start milestone|End milestone|  
|--------------|---------------------|-------------------|  
|1|Received|Approved|  
|2|Received|Delivered|  
|3|Received|Denied|  
|4|Approved|Delivered|  
  
 In this table, you can see that the first duration (Duration 1) is the time interval that starts when a purchase order is received by BizTalk Server, and ends when the purchase order is approved.  
  
### Milestone groups  
 You create milestone groups to treat a set of milestones as a single entity, for example, the beginning and ending milestones for a process, which creates a single milestone to represent the entire length of the process.  
  
### Aggregations  
 You use aggregations to improve the response time for refreshing data from the database. Excel defines aggregations as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked. For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer. However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.  
  
 The following figure displays an example of pre-calculated aggregation data.  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
  
 The figure summarizes the numbers of each product shipped to specific locations over a two-month time period. Excel typically defines this data as measure. The data used for filtering and categorization, Excel defines as dimension.  
  
 You can define two types of aggregations in the BAM workbook:  
  
-   Real-time aggregations  
  
-   Scheduled aggregations  
  
### Real-time aggregations  
 Real-time aggregations (RTA) allow you to see the current state of the business process and to easily identify process bottlenecks.  
  
 BAM data is displayed in a pivot table. You can define a BAM pivot table as an RTA or a scheduled aggregation. An RTA gives you an up-to-the-minute view of your data, for example, where a particular PO is in the shipping process. You can refresh your screen to update the view of the data throughout the day.  
  
 In some cases, specific slices of the multidimensional aggregations are so time-sensitive that you want them to be available in real time. For example, your business is selling perishable products and you want the aggregation of product quantity in different stages of delivery to be available in real time. At the same time, you want other aggregations such as the age of your typical customers, but only at the end of the month for business intelligence analysis.  
  
> [!IMPORTANT]
>  Do not define multiple RTAs that use the same BAM activity. If you do so, the RTA data will be incorrect when you archive the BAM data.  
  
 For information about browsing multidimensional data, see the PivotTable topic in Excel Help.  
  
### Scheduled aggregations  
 All BAM aggregations are scheduled aggregations by default. A scheduled aggregation represents a snapshot of the business at a specific time, for example, a summary of this morning's shipments. Ask your database administrator when your aggregations are processed, and then you can look at the historical data.  
  
### Dimensions and Measures  
 You use dimensions and measures to create data aggregations:  
  
- Dimensions describe a fact.  
  
- Measures are fact values.  
  
  For example, a fact could be “3 red cars” in inventory. The description of the product: "car" and "red" are dimensions. The value of the fact "3" is a measure. If the price of each car is included in the fact, the car price is a dimension, but the average price of cars in inventory is a measure. Microsoft SQL Server Books Online describes a measure as "the central values that are aggregated and analyzed." In other words, if you can count it, average it, or otherwise perform mathematical functions to get it, it is a measure.  
  
  You can create the following types of dimensions:  
  
- Progress dimension  
  
- Data dimension  
  
- Time dimension  
  
- Numeric range dimension  
  
## Progress dimensions  
 BAM introduces a new type of dimension: the progress dimension. You create progress dimensions to create aggregations that relate to the progress of activities still in process.  
  
 For example, consider a purchasing business process where you receive 1,000 purchase orders. You can use the progress dimension on rows to create the following table.  
  
|OrderProgress_Level1|Count|  
|---------------------------|-----------|  
|Received|1000|  
  
 You can then open the Received process to view further details about the progress of the activities, such as:  
  
|||Count|  
|------|------|-----------|  
|Received|Evaluating|300|  
||Approved|500|  
||Denied|200|  
  
 This means that from the 1000 purchase orders you received, 500 were approved, 200 were denied, and 300 are currently being evaluated.  
  
 Received, Approved, and Denied represent milestones. The corresponding numbers in the Count column show how many orders have passed through these milestones. Evaluating is a stage that the orders pass through between the Received and Approved or Denied milestones.  
  
 You can use progress dimensions in combination with any other dimensions. For example, by using the progress dimension Order Progress on rows and the data dimension Product on columns, the following results occur:  
  
|||Tennis Racquets|Soccer Balls|  
|------|------|---------------------|------------------|  
|Received|Evaluating|250|50|  
||Approved|200|300|  
||Denied|150|50|  
  
 Progress dimensions provide especially useful information for charts based on real-time aggregations (RTA). RTAs allow you to see the current state of the business process and to easily identify process bottlenecks.  
  
 The milestones in a purchase order progress dimension can be sequential: the first step is completed before the next step is started. Or milestones can be completed in tandem. Sequential steps are child steps, and tandem steps are sibling steps. In the purchase order process, verification begins as soon as the purchase order is received. It is a transitory step that occurs at the same time as the received milestone, and is therefore a sibling to the receive milestone. A purchase order is approved only after it is received — approved is a child of received.  
  
## Data dimension  
 You define a data dimension to use the value of some text items in the BAM activity on rows or columns. For example, a data dimension named Product can be used to create the following table:  
  
|Product|Count|  
|-------------|-----------|  
|Tennis racquets|100|  
|Soccer balls|200|  
  
 Also, you can define more than one data dimension in the BAM View Wizard. For example, defining a data dimension named Location with levels for State and City can be used to create the following table:  
  
|Product|Los Angeles|San Francisco|Seattle|  
|-------------|-----------------|-------------------|-------------|  
|Tennis racquets|50|20|30|  
|Soccer balls|130|50|20|  
  
 In this table, the Product dimension was used as the rows, and the Location dimension was used as the columns.  
  
## Time dimension  
 You create a time dimension to create aggregations with respect to time. For example, a time dimension can be used to create the following table:  
  
|Year|Month|Count|  
|----------|-----------|-----------|  
|2003|January|120|  
||February|230|  
||March|350|  
||April|280|  
  
 You can combine the time dimension with any other dimension. For example, you can use the time dimension on rows and the data dimension on columns to create the following table:  
  
|Month|Tennis racquets|Soccer balls|  
|-----------|---------------------|------------------|  
|January|50|70|  
|February|120|110|  
|March|300|50|  
|April|220|60|  
  
## Numeric range dimension  
 You use numeric range dimensions to create aggregations that categorize ranges of numbers by friendly names. For example, a business analyst can define a numeric range dimension named PO Size with the following ranges:  
  
 Small, for purchase orders between 0 and $100  
  
 Medium, for purchase orders between $100 and $1,000  
  
 Large, for purchase orders exceeding $1,000  
  
> [!NOTE]
>  If a purchase order amount is not in the defined ranges, for example, a purchase order amount is less than 0, then an "Out of range" row will be automatically created by BAM to accommodate the out-of-range data.  
  
|PO Size|Count|  
|-------------|-----------|  
|Small|500|  
|Medium|350|  
|Large|225|  
  
> [!NOTE]
>  You cannot create two numeric range dimensions that reference the same data alias.