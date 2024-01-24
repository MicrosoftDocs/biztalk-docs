---
description: "Learn more about: Transparency"
title: "Transparency2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transparency
**Transparency** sets a flag that indicates that transparent data from the host is in ASCII and needs no translation from EBCDIC to ASCII. Selecting **Transparency is ASCII** causes the Windows Host Print service not to put the received data through an EBCDIC to ASCII translation table before printing.  
  
 Check **Transparency Custom Byte** to send the data stream in transparent mode. **Transparency Custom Byte** indicates the character designated to start a sequence of transparent data (the transparent data may or may not be ASCII). The IBM standard is 0x35, but if the host print job uses another value (for example, 0x36), this should be specified.  
  
### To select Transparency  
  
1.  In SNA Manager, expand the server, right-click **Print Service**, and then click **Properties**.  
  
2.  Click the **Advanced** tab, click **Transparency Custom Byte**,enter the byte data, and then click **OK**.  
  
## See Also  
 [Formatting Print Jobs](../core/formatting-print-jobs1.md)
