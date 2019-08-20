---
title: "Enhanced Listener CICS Administration2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70852e7a-8b0d-45d8-9aa9-d90852d3aaac
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Enhanced Listener CICS Administration
The following code defines a CICS Enhanced Listener. There are several new keywords available for use with the Enhanced Listener. The parameter definitions describe how these new Listener configuration values are used for support the TI Enhanced Listener feature.  
  
```  
EZACICD TYPE=LISTENER,  Listener record definition               X  
       FORMAT=ENHANCED,  Enhanced Listener                       X  
       APPLID=XYZ12345,  Application ID of CICS region           X  
       TRANID=CSKM,      Transaction name for Listener           X  
       PORT=1234,        Port number for Listener                X  
       IMMED=YES,        Listener starts up at initialization?   X  
       NUMSOCK=50,       Number of sockets supported by Listener X  
       ACCTIME=30,       Timeout value for Accept                X  
       GIVTIME=30,       Timeout value for Givesocket            X  
       REATIME=30,       Timeout value for Read                  X  
       CSTRAN=MSCS,      Name of child server transaction        X  
       CSSTTYPE=KC,       Child server startup type              X  
       CSDELAY=000000,   Child server delay interval             X  
       MSGLEN=35,        Length of input message                 X  
       PEEKDATA=NO,       Peek option                            X  
       MSGFORM=EBCDIC,   Output message format                   X  
  
```  
  
 *CSTRANID*  
 This parameter is specific to the enhanced version of the Listener and specifies the default child server transaction that the Listener starts.  
  
 For enhanced listener message (ELM) Link support, this value should be set to MSCS to conform to the samples that Microsoft delivers with the product. The MSCS transaction code should be associated with the mscmtics.cbl program that supports the Standard and Enhanced Listener protocols. Otherwise, this parameter is the transaction ID that will be executed for each request made to the designated port.  
  
 *CSSTTYPE*  
 This parameter is specific to the enhanced version of the Listener and specifies the default start method for the child server task. This parameter can be overridden by the security/transaction exit. Possible values are IC, KC, and TD.  
  
 *IC*  
 Indicates that the child server task is started using EXEC CICS START with the value specified by CSDLYINT (or an overriding value from the security/transaction exit) as the delay interval.  
  
 *KC*  
 Indicates that the child server task is started using EXEC CICS START with no delay interval.  
  
 *TD*  
 Indicates that the child server task is started using the EXEC CICS WRITEQ TD command, which uses transient data to trigger the child server task.  
  
 *CSDLYINT*  
 This parameter is specific to the enhanced version of the Listener and is applicable only if CSSTTYPE is IC. It specifies the delay interval to be used on the EXEC CICS START command, in the form hhmmss (hours/minutes/seconds).  
  
 *MSGFORM*  
 This parameter is specific to the enhanced version of the Listener and indicates whether an error message returned to the client should be in ASCII or Extended Binary Coded Decimal Interchange Code (EBCDIC) format. ASCII is the default. MSGFORM is displayed as MSGFORMat on the IBM-supplied CICS Transaction screens.  
  
 For TI Enhanced Listener support, this value must be set to EBCDIC.  
  
 *MSGLEN*  
 This parameter is specific to the enhanced version of the Listener and specifies the length of the data to be received from the client by the Listener. The valid range is from 0 through 999. If the value is 0, the Listener does not read in any data from the client.  
  
 For TI Enhanced Listener support, this value must be the size of the ELM that is delivered. The size of the ELM is 35.  
  
 *PEEKDATA*  
 This parameter is specific to the enhanced version of the Listener and applies only if MSGLEN is not 0.  
  
 A value of NO indicates that the Listener performs a normal read of the client data. The child server application accesses this data in the data area-2 portion of the transaction initiation message (TIM).  
  
 A value of YES indicates that the Listener reads the data using the Peek option. The data remains queued in TCP/IP and the child server applications read it in rather than accessing it through the TIM.  
  
 For TI Enhanced Listener support, this value must be set to NO. Setting this value to NO instructs the Enhanced Listener to read the ELM (35 bytes) and place it in the TIM in the data area-2 field.  
  
 The mscmtics.cbl Concurrent Server uses the information in this area to determine what server program to link to.  
  
 For more information about the format of the ELM, see the ELM definition file at \<drive>:\Program Files\Microsoft Host Integration Server\System\TIM\MicrosoftELMDefs.tim. Use Visual Studio to view the file.  
  
## See Also  
 [ELM Format for the TCP ELM Link Programming Model](../core/elm-format-for-the-tcp-elm-link-programming-model1.md)   
 [ELM Format for the TCP ELM User Data Programming Model](../core/elm-format-for-the-tcp-elm-user-data-programming-model2.md)