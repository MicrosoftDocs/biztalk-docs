---
description: "Learn more about: Send Pipeline"
title: "Send Pipeline"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Send Pipeline
This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] send pipeline that you can customize for your application.  
  
## Demonstrates  
 This sample demonstrates how to process an outgoing XML message into the equivalent RNIF message using the BTARN send pipeline (PipelineSend.btp). PipelineSend.btp is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines. It includes the following stages:  
  
-   XML Assembler  
  
-   MIME Encoder  
  
-   Send message Non-repudiate  
  
> [!NOTE]
>  If you select one of the above components of the BTARN send pipeline in the Pipeline Designer in Visual Studio, the properties for that component will not be displayed in the Properties pane. To display the properties of the component, you must add the component to the Toolbox by using the **Choose Toolbox Items** command in the Tools menu; delete the existing component from the send pipeline; and then add the component from the Toolbox into the appropriate stage in the Pipeline Designer. If you then select the component, its properties will be displayed in the Properties pane.  
  
 For more information about the components of this pipeline, and the message flow within this pipeline, see [BTARN Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md).  
  
## See Also  
 [Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md)   
 [BTARN Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)
