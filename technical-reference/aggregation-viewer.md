---
title: Aggregation Viewer
TOCTitle: Aggregation Viewer
ms:assetid: d39664b8-0d2a-4ad7-a718-b4cbbe35a21b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578579(v=BTS.80)
ms:contentKeyID: 51531577
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts06.bam.portal.aggregationviewer
---

# Aggregation Viewer

 

Aggregations are tables of precalculated data you can use for analytical processing with an OLAP cube. Aggregations facilitate the efficient querying of multidimensional databases. When you create and deploy your observation model (the high-level definition of your business data) using the BAM Add-In for Excel, you create aggregations that you can use to quickly evaluate collections of data relating your Key Performance Indicators (KPIs).

Aggregations can be either scheduled or real-time. Scheduled aggregations are OLAP cubes, which represent a snapshot of your business data at a time you specify. Real-time aggregations allow a view of your business data based on trigger points that you specify, allowing the BAM system to notify you through an alert as soon as a KPI has been reached.

## PivotTable view

The PivotTable View area displays the PivotTable report you design using the BAM Add-In for Excel. The Office Web Components allow you to manipulate the PivotTable report to present the view of the data that best fits your needs. For more information about using PivotTable reports, see "Layout and Format" in Office Online Help at [http://go.microsoft.com/fwlink/?LinkId=194314](http://go.microsoft.com/fwlink/?linkid=194314).

When viewing the PivotTable report it is possible that some rows could contain null data in both real-time aggregations (RTAs) and precalculated aggregations (an OLAP implementation) if the milestones in the activity have been reached but are not used in the progress dimension. It is also possible to encounter rows with null data if the time dimension is used in the context of a progress dimension and is anchored to a milestone such as "acknowledged" instead of "received." In this case an activity instance is received and triggers the received milestone, but the activity has not yet triggered the acknowledge milestone and a zero will appear in the time dimension row. To avoid this situation, link the time dimension to the received milestone.

There are several points to keep in mind when using the Office Web Components in the BAM portal:

  - PivotTable reports in Excel include a Page field where you can put a time slice dimension. The Office Web Components used by the BAM Portal do not include a Page field. If your Excel PivotTable report uses the Page field for any dimensions, the data for this field is not displayed in your PivotTable report in the BAM portal.

  - The Office Web Components display data in the content frame of the BAM portal. Because of the space limitations of this frame, adding dimensions from the field list to the columns area can cause the display of the PivotTable report to move dimension names partly or wholly out of view.

For more information about PivotTable reports, see "PivotTable terminology demystified" at [http://go.microsoft.com/fwlink/?LinkId=194317](http://go.microsoft.com/fwlink/?linkid=194317).

## Chart view

The Chart View area displays the aggregation in a graphical manner. The Office Web Components allow you to manipulate the details of the aggregation through the chart view to adjust the reported data as needed. When you adjust the aggregation by dragging and dropping data items from the Chart Field list, the PivotTable report for the aggregation is automatically updated to reflect your changes. You can drill through the PivotTable report to create an alert on the new aggregation view.

#### To modify an aggregation

1.  From the PivotTable Field List window, drag the fields with data that you want to display in rows and drop them onto the left column of the grid to add row fields. If you do not see the field list, click within the outlines of the PivotTable drop areas to make sure the Show Field List appears. To see what levels of detail are available in fields that have levels, click the plus sign (+) next to the field.

2.  Drag fields with data that you want to display across columns to the drop area labeled **Drop Column Fields Here**. Only fields that are designated as counts or progress fields can be dragged to this area.

3.  If you add more than one data field, arrange these fields in the order you want: right-click a data field, point to **Order** on the shortcut menu, and use the commands on the **Order** menu to move the field.

4.  To rearrange fields, drag them from one area to another. To remove a field, drag it out of the PivotTable report onto the navigation frame.

5.  From the totals column in the PivotTable report, right-click the cell containing the total on which you are going to set an alert. Select **Create Alert** to open the Alert Management page.

## See Also

[Alert Manager](alert-manager.md)

