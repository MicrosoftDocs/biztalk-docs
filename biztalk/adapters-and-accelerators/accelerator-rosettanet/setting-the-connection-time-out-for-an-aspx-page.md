---
description: "Learn more about: Setting the Connection Time-Out for an ASPX Page"
title: "Setting the Connection Time-Out for an ASPX Page"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Setting the Connection Time-Out for an ASPX Page
When you use an ASPX page for synchronous messages, you must increase the connection time-out for the ASPX page so that it can wait for the expected message.  
  
 Increasing the connection time-out for the ASPX page can have unintended consequences. First, it increases the risk of a denial-of-service attack and the threat of exhausting the thread pool. Second, if there are too many synchronous connections on the ASPX page, the system can lock up. Therefore, while you must increase the connection time-out, be careful not to increase it too much.  
  
 Set the connection time-out to the minimum allowed by the RosettaNet organization. For more information about the timing parameters for a Partner Interface Process (PIP), see Table 4-3: Message Exchange Controls, in the RosettaNet PIP Specification.  
  
### To set the connection time-out for the ASPX page  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In IIS Manager, expand the node for the local computer, and then expand **Web Sites**.  
  
3.  Right-click **Default Web Site**, and then click **Properties**.  
  
4.  In the Default Web Site Properties dialog box, on the **Web Site** tab, in the **Connection Timeout** box, type an appropriate value, and then click **OK**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)
