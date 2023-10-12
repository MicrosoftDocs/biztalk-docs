---
description: "Learn more about: Related Activities"
title: "Related Activities"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Related Activities
The Related Activities area contains a list of activities that are related to the activity on which the query is based. An example of a related activity for a Purchase Order activity would be multiple Shipment activities, since items on a single purchase order can be delivered in multiple shipments.  
  
## Creating related activities  
 The list of related activities is generated in one of two ways:  
  
- You define two activities and then create a single view that includes both of them. Your developer makes a correlation connection between the two by implementing the key, field, and value relationships between the activities.  
  
- You define two activities. Your developer makes a correlation connection in your custom application by calling AddRelationship() and defining the key, field, and value relationships between the activities.  
  
  Defining the activity relationships in either of these ways adds a row in the \<activityname\>_Relationships table.  
  
> [!NOTE]
>  Only the first method of defining relationships results in the related activities having live links to each other. The second method does not define a spanning view and therefore the portal cannot know about the relationship between the two activities.  
  
## See Also  
 [How to View the Results of an Activity Search](../core/how-to-view-the-results-of-an-activity-search.md)
