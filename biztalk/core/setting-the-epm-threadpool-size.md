---
description: "Learn more about: Setting the EPM Threadpool Size"
title: "Setting the EPM Threadpool Size"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Setting the EPM Threadpool Size
This topic explains how to set the threadpool size for the End Point Manager (EPM).  
  
 On the **Advanced** tab in the **Host Properties** dialog box, there is a property called **Maximum number of messaging engine threads per CPU**. For instructions about accessing this dialog box, see [How to Create a New Host](../core/how-to-create-a-new-host.md). Use this property to control the size of the pool of process threads that the messaging engine uses to process messages. The default value for this property is 20, meaning that the messaging engine will use no more than 20 threads for each CPU on the server.  
  
 Since batches of messages are processed by each thread in the pool, adjusting the value of **Maximum number of messaging engine threads per CPU** can affect performance by changing the dynamics of resource utilization on the server. For more information about how the threadpool works, see [Using the BizTalk Messaging Engine](../core/using-the-biztalk-messaging-engine.md).  
  
 Testing has shown that in cases where the CPU or the SQL Server is over utilized, decreasing the value of **Maximum number of messaging engine threads per CPU** can result in a net gain in throughput. For example, in cases where the MessageBox database server exhibits CPU utilization above 90% or the SQL lock wait times are elevated above 500-1000 milliseconds, reducing the number of threads in the pool will reduce the overall number connections being made to SQL Server, which results in more efficient message processing. In some cases, setting the maximum thread pool size to a value as low as 2 can result in measurable throughput gain.  
  
## Recommendation  
 When optimizing a BizTalk Server installation, it is recommended that you fine tune the value you set for **Maximum number of messaging engine threads per CPU**.  When you try to reduce the utilization of the MessageBox database server, consider reducing the value of this property.  
  
 When the BizTalk server or the MessageBox database server is not highly utilized, and applying additional load does not result in additional throughput, try increasing the value of **Maximum number of messaging engine threads per CPU** to take advantage of underutilized resources.  
  
## See Also  
 [How to Create a New Host](../core/how-to-create-a-new-host.md)   
 [Using the BizTalk Messaging Engine](../core/using-the-biztalk-messaging-engine.md)
