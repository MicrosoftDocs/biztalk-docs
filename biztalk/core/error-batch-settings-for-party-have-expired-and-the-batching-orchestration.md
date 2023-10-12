---
description: "Learn more about: The batch settings for party have expired and the batching orchestration is being terminated"
title: "The batch settings for party have expired and the batching orchestration is being terminated"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The batch settings for party have expired and the batching orchestration is being terminated
## Details  
  
|     Field            |      Error Details                                                                                                                                                                            |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                   |
| Product Version |                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                               |
|    Event ID     |                                                                                           -                                                                                           |
|  Event Source   |                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                 |
|    Component    |                                                                                    Batching Engine                                                                                    |
|  Symbolic Name  |                                                                                 BatchSettingsExpired                                                                                  |
|  Message Text   | The batch settings for party {0} have expired and the batching orchestration is being terminated. Further batches will not be generated till the batching is activated for this party |
  
## Explanation  
 This Warning indicates that the batching orchestration instance has been deactivated because the end of the activation range has been reached.  
  
## User Action  
 To resolve this error, restart the batching process by doing the following:  
  
1.  Open the BizTalk Server Administration Console, and move to the Interchange Batch Creation Settings Page of the EDI Properties dialog box.  
  
2.  Reset the end criteria, and then restart the orchestration by clicking **Start**.  
  
3.  If the Start datetime is prior to the time when you clicked **Start**, click **Yes** to update the Start datetime to the current datetime.
