---
title: "BizTalk Adapter for Host Files Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6122beab-32af-4f48-b214-53cfdcda86fd
caps.latest.revision: 2
ms.author: "paulettm"
author: MandiOhlinger
manager: anneta
---
# BizTalk Adapter for Host Files Troubleshooting
**Send Port Updategram**  
  
 When using the BizTalk Adapter for Host File Send Port, the adapter will generate an error if the Updategram XML document does not contain the correct host file alias or fully-qualified host file name.  
  
 The adapter failed to transmit message going to send port "Send_HF2" with URL "HostFiles://MVS1DFM.HB01.PA62TKNU/HISDEMO/31fa3aba-606e-4b23-9814-baa4f10c1d2f". It will be retransmitted after the retry interval specified for this Send Port. Details:"HISEHFC0048 An error occurred while opening the cursor for file HostFileDefinition1.AREAS_RECORDS_0 with error code MW_DDM_ACCMTHRM. Check if the filename is correct.".  
  
 The BizTalk Designer will generate an XSD that does not contain the correct host file alias or fully-qualified host file name. The developer must generate an XML document instance that contains the correct reference to the host file, by updating the example of BizTalk Designer-generated XML document instance, where the name of the file is incorrectly specified as “HostFileDefinition1.AREAS_RECORDS_0”.  
  
```  
<ns0:HFRDREN xmlns:ns0="HFDTN">  
  <sync>  
    <after>  
      <HostFileDefinition1.AREAS_RECORDS AREAID="99999" AREADESC="AREA99999" REGIONID="999">HostFileDefinition1.AREAS_RECORDS_0</HostFileDefinition1.AREAS_RECORDS>  
    </after>  
  </sync>  
</ns0:HFRDREN>  
```  
  
 Example of BizTalk Designer-generated XML document instance, where the name of the file is correctly specified as the fully qualified dataset name “HISDEMO.NWIND.AREAS”.  
  
```  
<ns0:HFRDREN xmlns:ns0="HFDTN">  
  <sync>  
    <after>  
      <HostFileDefinition1.AREAS_RECORDS AREAID="99999" AREADESC="AREA99999" REGIONID="999">HISDEMO.NWIND.AREAS</HostFileDefinition1.AREAS_RECORDS>  
    </after>  
  </sync>  
</ns0:HFRDREN>  
  
```