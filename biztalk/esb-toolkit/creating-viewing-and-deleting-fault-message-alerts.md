---
description: "Learn more about: Creating, Viewing, and Deleting Fault Message Alerts"
title: "Creating, Viewing, and Deleting Fault Message Alerts"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating, Viewing, and Deleting Fault Message Alerts
The ESB Management Portal can generate alerts when fault messages arrive at the portal, based on a comparison of values in the message with criteria specified for the alert. The portal can also maintain a list of notifications linked to individual alerts and users, and it will notify these users when it proactively raises alerts.  
  
### To create and configure a new alert  
  
1.  Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.  
  
2.  Click the **Create Alert** link to open the [Add Alert Page](../esb-toolkit/add-alert-page.md).  
  
3.  In the **Enter Alert Name** text box, type a name for the new alert.  
  
4.  In the **Conditions** section of the Add Alert page, select a field (such as **Application**, **Error Type**, or **Fault Severity**) in the **Criteria** drop-down list; select a comparison type (such as +, =, !=, >=, <=, or **like**) in the **Operator** drop-down list; and type or select a value from the third list or text box (named **Value**). As you select a **Criteria** value, the page changes to display either a text box or a drop-down list for the matching value. All conditions are combined using the **AND** operator.  
  
5.  Click the **Add** link to add this condition to the list, and then repeat the previous step to add more conditions if required.  
  
6.  Click the **Save** button to create a new alert with the specified name and conditions.  
  
### To view details of an existing alert or delete an existing alert  
  
1.  Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md).  
  
2.  To delete an alert, click the **Delete Alert** icon in the Action column of an existing alert.  
  
    > [!NOTE]
    >  Non-administrative users can delete only alerts for which they are an owner, and for which there are currently no subscribers. You must log on to the portal as an administrator to delete other alerts.  
  
3.  To view details of an alert, click the **View** icon in the Action column of an existing alert. This opens the Alert Viewer page.  
  
4.  Click **Export To Excel** to download the complete list of alerts in a format that you can view in Microsoft Excel.
