---
title: "IBTBatchCallBack.BatchComplete Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75fa8e05-38f8-460b-bd1f-2213f1672bff
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTBatchCallBack.BatchComplete Method (COM)
Notifies the adapter the outcome of the batch of work.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTBatchCallBack::BatchComplete(  
        HRESULT  
        hrStatus,  
shortnOpCount,  
BTBatchOperationStatus*pOperationStatus,  
VARIANTvCallbackCookie);  
```  
  
```vb  
  
        Sub BatchComplete(  
        hrStatus  
         As HRESULT,  
nOpCount As short,  
pOperationStatus As BTBatchOperationStatus,  
vCallbackCookie As Variant)  
```  
  
#### Parameters  
 *hrStatus*  
 [in] **HRESULT** that contains the top level status of the batch. If this parameter is set to **S_OK**, then there is no need to drill down into the details of the status. If this parameter is set to **S_FALSE** and the batch contained messages to be submitted, then one or more messages failed in the pipeline and these messages were successfully suspended.  
  
 *hrStatus*  
 **HRESULT** that contains the top level status of the batch. If this parameter is set to **S_OK**, then there is no need to drill down into the details of the status. If this parameter is set to **S_FALSE** and the batch contained messages to be submitted, then one or more messages failed in the pipeline and these messages were successfully suspended.  
  
 *nOpCount*  
 [in] **Short** that contains the number of operations that were processed in this batch.  
  
 *nOpCount*  
 Short that contains the number of operations that were processed in this batch.  
  
 *pOperationStatus*  
 [in,size_is(nOpCount)] An array of operation statuses, one entry will be present for each type of operation that the batch contained.  
  
 *pOperationStatus*  
 An array of operation statuses, one entry will be present for each type of operation that the batch contained.  
  
 *vCallbackCookie*  
 [in] Variant that contains the cookie that was passed in by the adapter when it got the batch.  
  
 *vCallbackCookie*  
 **Variant** that contains the cookie that was passed in by the adapter when it got the batch.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
## Remarks  
 This method is called by the BizTalk Server Messaging Engine when it has completed processing a batch of work.  
  
 The adapter should release any resources that it was holding during this callback because the batch is atomic. If an error occurred in the batch, none of the work will be complete and the adapter, therefore, needs to handle failures correctly in order to avoid data loss. The nature of how those resources should be released is dependent upon the outcome of the batch.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTBatchCallBack Interface (COM)](../core/ibtbatchcallback-interface-com.md)   
 [IBTBatchCallBack Members (COM)](../core/ibtbatchcallback-members-com.md)