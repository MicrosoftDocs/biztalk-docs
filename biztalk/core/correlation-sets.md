---
description: "Learn more about: Correlation Sets"
title: "Correlation Sets"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Correlation Sets
You can achieve this sort of correlation of messages with orchestration instances by defining correlation sets. A correlation set is a set of properties *with specific values*. This is different from a correlation type, which is simply a list of properties. If an incoming message does not have all of these properties, with matching values for each, correlation will fail and the message will not be received by the orchestration instance.  
  
 Correlation types define a set of properties on which you will be correlating messages. These can be any properties which were previously defined in a property schema and deployed with some BizTalk Project including "system" properties deployed with the GlobalPropertySchemas which is installed as part of the base BizTalk install. A correlation set defines a set of properties and values for these properties that a message must contain to be processed by a particular orchestration.  
  
 For example, a correlation type could consist of the following properties:  
  
|Correlation Type Property|Possible XML Representation|  
|-------------------------------|---------------------------------|  
|Social Security number|\<SSN\>\</SSN\>|  
|Date of Birth|\<DOB\>\</DOB\>|  
|Gender|\<Gender\>\</Gender\>|  
  
 While a correlation set derived from this correlation type could consist of the following properties and values:  
  
|Correlation Set Property/Value|Possible XML representation|  
|-------------------------------------|---------------------------------|  
|Social Security number = 222112222|\<SSN\>222112222\</SSN\>|  
|Date of Birth = “1/1/1995”|\<DOB\>”1/1/1995”\</DOB\>|  
|Gender = Male|\<Gender\>M\</Gender\>|  
  
> [!NOTE]
>  Each correlation set supports a maximum of three parameters.  
  
## Initializing Correlation Sets  
  
-   **Correlation Sets initialized on a Receive action**  
  
     Correlation sets initialized on a Receive action define the exact set of properties that must exist in a published message in order for it to be processed by the corresponding receive action(s) in an orchestration. An initializing correlation set will create a correlation set from a correlation type based on the corresponding values in a document.  
  
-   **Correlation Sets initialized on a Send action**  
  
     Correlation sets initialized on a Send action are created from a correlation type based upon the corresponding values in a document and promote the correlation properties in the outbound document.  
  
## Following Correlation Sets  
 Following correlation sets can only be bound to a non-activating receive action or to a send action. Following correlation sets are specified in tandem with previously initialized correlation sets.  
  
-   **Following Correlation Sets bound to a Receive action**  
  
     Following correlation sets bound to a receive action define the set of properties and values that the document must contain to be received.  Receive actions with following correlation sets accept documents that contain properties from a previously initialized correlation set.  
  
-   **Following Correlation Sets bound to a Send action**  
  
     Following correlation sets bound to a send action dictate that the set of properties in the correlation set are promoted in the outbound document.  
  
## Inspecting Correlation Sets  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the ability to inspect correlation sets. You can inspect a correlation set in an Expression Shape using code similar to the following:  
  
```  
MsgLen = Correlation_1(BTS.MessageLength);  
```  
  
 The example above assumes that you have created a variable named **MsgLen** of type **System.Int16** and that your orchestration contains a correlation set named **Correlation_1**. The ability to inspect correlation sets may be useful if you need to inspect the value of a correlation that was passed to an orchestration by another orchestration.  
  
## Passing Correlation Sets as Parameters to Orchestrations  
 You can pass correlations as *in* parameters to other orchestrations.
