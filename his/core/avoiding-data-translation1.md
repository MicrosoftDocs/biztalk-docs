---
title: "Avoiding Data Translation1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 419b2582-3f70-4c67-8ccd-695f351afb22
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Avoiding Data Translation
In some circumstances, you may want the Transaction Integrator runtime to pass untranslated data to or from the mainframe. To do this, set up an array of PIC X Untranslated bytes.  
  
 TI supports many data types, however, you may not always want TI to translate or interpret the data.  
  
### To configure a byte array of PIC X Untranslated bytes, follow these steps:  
  
1. Open the COMTI Component Builder.  
  
2. Unlock the COMTI component.  
  
3. Select the properties for the parameter that you want to change.  
  
4. On the Automation tab, set the data type to Byte.  
  
5. On the COBOL Definition tab, set the COBOL Definition to PIC X Untranslated.  
  
6. On the Arrays tab, set the array to be a Single Dimension Array, and set the maximum size of the array equal to the expected number of bytes.  
  
7. Lock the component.  
  
   After the last step is complete, TI will pass the bytes in the array to the calling program as untranslated binary data.  
  
   Because MTI passes the bytes as untranslated binary data, the interface program must take into account the newly modified parameter.  You can use this procedure if, for example, the characters coming from or going to the host are outside the range of the translation table. By following the steps earlier in this section, you can implement a custom translation table in code that handles the data.  
  
   If a variable-sized array is to be transferred, follow these steps:  
  
8. Set the array size to the maximum number of characters ever to be exchanged.  
  
9. On the Advanced tab of the method properties, set the Data buffer options as follows:  
  
   1.  Final field from host is Bounded.  
  
   2.  Final field to host is Bounded.