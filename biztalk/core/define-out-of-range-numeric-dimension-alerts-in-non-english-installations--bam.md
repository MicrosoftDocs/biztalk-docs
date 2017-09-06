---
title: "How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f1e0373-eadf-4c6d-9a38-a34d847f310f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations
When setting alerts that include a condition for a value that is outside the defined numeric range dimension on non-English installations, you must manually modify the BAM definition with the localized version of the string **out of range**.  
  
 The following table lists examples of localized out-of-range values.  
  
|Language code|Localized string|  
|-------------------|----------------------|  
|CN|超出范围|  
|DE|Außerhalb des gültigen Bereichs|  
|ES|Fuera de rango|  
|FR|hors limites|  
|IT|Fuori intervallo|  
|JA|範囲外|  
|KO|범위를 벗어남|  
|TW|超過範圍|  
  
### To define out-of-range alerts in non-English installations  
  
1.  Navigate to the folder containing your BAM definition xml file.  
  
2.  Using a text editor or an XML editor, open the BAM definition file.  
  
3.  Locate the slicer dimension for the numeric dimension. For example, if your slicer dimension is named **Alerts_NumDim**, you would locate the following node:  
  
    ```  
    <SlicerDimension Name="Alerts_NumDim">  
    <Level Name="(Out of Range)" />  
    </SlicerDimension>  
    ```  
  
4.  Change the **Out of Range** string value to the appropriate localized string.  
  
5.  Save the file and deploy the definition.  
  
## See Also  
 [What Is a BAM Definition Schema?](../core/what-is-a-bam-definition-schema.md)   
 [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md)