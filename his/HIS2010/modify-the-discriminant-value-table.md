---
title: "Modify the Discriminant Value Table | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20d98b41-521a-4af7-b498-3758f3dc0b13
caps.latest.revision: 3
---
# Modify the Discriminant Value Table
After you import the host definition file (in [Import the Host Definition File](../HIS2010/import-the-host-definition-file.md)), you can modify the logic of the associated discriminant value table.  
  
 Follow these steps to modify the discriminant value table for [Tutorial 2: A Step-by-Step Guide to Creating a Simple Discriminated Union Application](../HIS2010/4f12d9eb-7eff-45c2-94fd-425b87a6134d.md).  
  
## Procedures  
  
#### To modify the discriminant value table  
  
1.  On the Banking.dll tab, expand the **Banking** .dll node, expand the **Accounts interface** node, expand the **GetAInfo method** node, and then expand the **ACCT_ARRAY parameter** node.  
  
2.  Right-click the **UNION1** node, and then click **Properties**.  
  
3.  In the **Properties** window, in the **Discriminant** field, click the drop-down button, and then click the ACCT_ARRAY.ACCT_TYPE value.  
  
4.  Click the **DVT** field, and then click the **ellipsis (…)** button.  
  
5.  In the **Discriminant Value Table** dialog box, click the drop-down button under the **Union Member** field, and then click **Checking**.  
  
6.  Double-click the field in the **Condition** column, and type **C**.  
  
7.  In the **Union Member** column, click the drop-down button under the **Checking** field, and then click Savings.  
  
8.  Double-click the **Condition** field under the **C**, and then type **S**.  
  
9. Click **OK**.  
  
## See Also  
 [Save and Deploy the GetAInfo Interface](../HIS2010/save-and-deploy-the-getainfo-interface.md)