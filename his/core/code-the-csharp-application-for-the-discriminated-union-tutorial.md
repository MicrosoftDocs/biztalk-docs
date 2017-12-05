---
title: "Code the C# Application for the Discriminated Union Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1449560-daec-4b7a-ba01-b8932bc6e7c6
caps.latest.revision: 3
---
# Code the C# Application for the Discriminated Union Tutorial
After you create the C# project to contain your code (in [Create a Visual C# Project for the Discriminated Union Tutorial](../core/create-a-visual-csharp-project-for-the-discriminated-union-tutorial.md)), you can write code for the C# application that uses the deployed interface to access the remote mainframe.  
  
 Follow these steps to write code for the application in [Tutorial 2: A Step-by-Step Guide to Creating a Simple Discriminated Union Application](../core/4f12d9eb-7eff-45c2-94fd-425b87a6134d.md).  
  
## Procedure  
  
#### To code the C# application for the discriminated union tutorial  
  
1.  In Solution Explorer, expand the ConsoleApplication1 node.  
  
2.  Right-click **References**, and then click **Add Reference**.  
  
3.  In the **Add Reference** dialog box, select the **Browse** tab, and locate the DiscrUnionTutorial folder.  
  
     For this tutorial, the DiscrUnionTutorial folder is located at \<*Installation Directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\AppInt\DiscrUnionTutorial\DiscrUnionTutorial.  
  
4.  Click Banking.DLL, and then click **OK**.  
  
5.  Add the following code to your Program.cs file:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Banking;  
  
    namespace ConsoleApplication1  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                Banking.Accounts MyBankObj = new Banking.Accounts();  
                Banking.ACCT_ARRAY[] accountInfoArray = new Banking.ACCT_ARRAY[2];  
                Banking.SAVINGS MySavInfo = new Banking.SAVINGS();  
                Banking.CHECKING MyChkInfo = new Banking.CHECKING();  
  
                accountInfoArray[0].ACCT_NUM = "SAV1234567";  
                accountInfoArray[0].ACCT_TYPE = "S";  
                accountInfoArray[0].UNION1 = MySavInfo;  
  
                accountInfoArray[1].ACCT_NUM = "CHK4566112";  
                accountInfoArray[1].ACCT_TYPE = "C";  
                accountInfoArray[1].UNION1 = MyChkInfo;  
  
                MyBankObj.GetAInfo("11223333", ref accountInfoArray);  
  
                foreach (ACCT_ARRAY aa in accountInfoArray)  
                {  
                    switch (aa.ACCT_TYPE)  
                    {  
                        case "C":  
                            Banking.CHECKING ChkInfo = (Banking.CHECKING)aa.UNION1;  
                            break;  
                        case "S":  
                            Banking.SAVINGS SavInfo = (Banking.SAVINGS)aa.UNION1;  
                            break;  
                    }  
                }  
  
            }  
        }  
    }  
    ```  
  
6.  On the **File** menu, click **Save All**.  
  
7.  Click **Build**, and then click **Build ConsoleApplication1**.  
  
8.  Click **Debug**, and then click **Start**.  
  
## See Also  
 [Tutorial 2: A Step-by-Step Guide to Creating a Simple Discriminated Union Application](../core/4f12d9eb-7eff-45c2-94fd-425b87a6134d.md)