---
title: "IBTDTCCommitConfirm.DTCCommitConfirm Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e4edc24-f3e0-4c31-aec7-abb8ab929f53
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTDTCCommitConfirm.DTCCommitConfirm Method (COM)
Notifies the BizTalk Server Messaging Engine of the outcome of a DTC transaction that the adapter committed.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTDTCCommitConfirm::DTCCommitConfirm(  
        IUnknown*  
        pTransaction,  
BOOLbCommitSuccessful);  
```  
  
```vb  
  
        Sub DTCCommitConfirm(  
        pTransaction  
         As IUnknown,  
bCommitSuccessful As Boolean)  
```  
  
## Remarks  
 **Parameters**  
  
 *pTransaction*  
 [in] Pointer to the **IUnknown** interface that contains the transaction that was committed.  
  
 *pTransaction*  
 **IUnknown** that contains the transaction that was committed.  
  
 *bCommitSuccessful*  
 [in] Boolean that contains the commit successful. **true** to indicate that the commit was successful; otherwise, **false**.  
  
 *bCommitSuccessful*  
 **Boolean** that contains the commit successful. **true** to indicate that the commit was successful; otherwise, **false**.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTDTCCommitConfirm Interface (COM)](../core/ibtdtccommitconfirm-interface-com.md)   
 [IBTDTCCommitConfirm Members (COM)](../core/ibtdtccommitconfirm-members-com.md)