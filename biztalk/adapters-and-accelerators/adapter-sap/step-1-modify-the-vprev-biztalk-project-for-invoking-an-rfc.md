---
title: "Step 1: Modify the vPrev BizTalk Project for Invoking an RFC | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migration, modifying previous version of BizTalk project for invoking an RFC"
  - "migration"
ms.assetid: 2d4a6cd7-d216-4e0f-8f82-41e044cd325b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Modify the vPrev BizTalk Project for Invoking an RFC
![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Time to complete:** 10 minutes  
  
 **Objective:** In this step, you make the following changes to the existing vPrev BizTalk project:  
  
- Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- Map the request message for invoking the RFC using the vPrev SAP adapter to a request message for invoking the RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- Map the response message received using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the response message for the vPrev SAP adapter.  
  
## Prerequisite  
  
-   You must have a vPrev BizTalk project to invoke the SD_RFC_CUSTOMER_GET RFC in the SAP system.  
  
### To modify the vPrev BizTalk project  
  
1. Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. You can use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata.  
  
    For instructions on how to generate metadata for RFCs, see [Browse, search and get metadata for RFC operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md). After the schema is generated, a file with the name similar to *SapBindingSchema.xsd* is added to the BizTalk project. This file contains the schema for invoking the SD_RFC_CUSTOMER_GET using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
2. Generating the metadata for the SD_RFC_CUSTOMER_GET RFC also creates a port binding file. In the next step, this binding file will be used to create a WCF-Custom send port to send messages to the SAP system. The SOAP action for the operation is also set to the operation for which you generated metadata. For example, if you generate metadata for the SD_RFC_CUSTOMER_GET RFC, the operation name in the SOAP action on the send port will be “SD_RFC_CUSTOMER_GET”. However, the operation name on the logical send port that you create as part of the orchestration could be different, for example, “Operation_1”. As a result, when you send messages to the SAP system using the send port, you get an error. To prevent this, make sure the operation name on the logical send port in your orchestration is the same as the operation name for which you generated metadata.  
  
    So, in the case of this tutorial, because you generate metadata for the SD_RFC_CUSTOMER_GET RFC, change the name of the logical send port operation to “SD_RFC_CUSTOMER_GET”.  
  
3. For the request message, map the schema generated using vPrev SAP adapter to the schema generated using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
   1. Add a BizTalk mapper to the BizTalk project. Right-click the BizTalk project, point to **Add**, and then click **New Item**.  
  
       In the **Add New Item** dialog box, from the left pane, select **Map Files**. From the right pane, select **Map**. Specify a name for the map, such as **RequestMap.btm**. Click **Add**.  
  
   2. From the Source Schema pane, click **Open Source Schema**.  
  
   3. In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the vPrev SAP adapter. For this tutorial, select *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*,and then click **OK**.  
  
   4. In the **Root Node for Source Schema** dialog box, select *SD_RFC_CUSTOMER_GET_Request*, and then click **OK**.  
  
   5. From the Destination Schema pane, click **Open Destination Schema**.  
  
   6. In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the request message for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For this tutorial, select *SAP_Migration.SapBindingSchema*, and then click OK.  
  
   7. In the **Root Node for Target Schema** dialog box, select *SD_RFC_CUSTOMER_GET*, and then click **OK**.  
  
       Map the respective elements in both the schemas as illustrated in the following figure. Map the CUSTOMER_T element using a String Left Trim functoid. To do so, from the **Toolbox**, drag the **String Left Trim** functoid and drop it on the mapper grid. Connect the **CUSTOMER_T** element in the source schema to the functoid. Similarly, connect the **CUSTOMER_T** element in the destination schema to the functoid. The following figure illustrates how the two elements are mapped via the functoid.  
  
       ![Map the request messages between adapter versions](../../adapters-and-accelerators/adapter-sap/media/f12f280d-766f-4647-bced-435354206fb9.gif "f12f280d-766f-4647-bced-435354206fb9")  
  
      > [!NOTE]
      >  For more information about the String Left Trim functoid, see "String Left Trim Functoid" at [http://go.microsoft.com/fwlink/?LinkId=105774](http://go.microsoft.com/fwlink/?LinkId=105774).  
  
   8. Save the map.  
  
4. For the response message, map the schema generated using vPrev SAP adapter to the schema generated using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
   1. Add a BizTalk mapper to the BizTalk project. Right-click the BizTalk project, point to **Add**, and click **New Item**.  
  
       In the **Add New Item** dialog box, from the left pane, select **Map Files**. From the right pane, select **Map**. Specify a name for the map, such as **ResponseMap.btm**. Click **Add**.  
  
   2. From the Source Schema pane, click **Open Source Schema**.  
  
   3. In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For this tutorial, select *SAP_Migration.SapBindingSchema*, and then click **OK**.  
  
   4. In the **Root Node for Source Schema** dialog box, select *SD_RFC_CUSTOMER_GETResponse*, and then click **OK**.  
  
   5. From the Destination Schema pane, click **Open Destination Schema**.  
  
   6. In the **BizTalk Type Picker** dialog box, expand the project name, expand **Schemas**, and select the schema for the response message for the vPrev SAP adapter. For this tutorial, select *SAP_Migration.SD_RFC_CUSTOMER_GET__x32003*, and then click **OK**.  
  
   7. In the **Root Node for Target Schema** dialog box, select *SD_RFC_CUSTOMER_GET_Response*, and then click **OK**.  
  
   8. Map the respective elements in both the schemas as illustrated in the following figure.  
  
       ![Map the response messages between adapter versions](../../adapters-and-accelerators/adapter-sap/media/d8dddaba-d978-4159-bcc6-6a6bfee36564.gif "d8dddaba-d978-4159-bcc6-6a6bfee36564")  
  
   9. Save the map.  
  
5. Save and build the BizTalk solution. Right-click the solution, and then click **Build Solution**.  
  
6. Deploy the solution. Right-click the solution, and then click **Deploy Solution**.  
  
## Next Steps  
 Create a WCF-Custom send port, and configure it to use the maps you created in this step, as described in [Step 2: Configure the Orchestration in BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md).  
  
## See Also  
 [Tutorial 2: Migrating an SAP RFC BizTalk Project](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)