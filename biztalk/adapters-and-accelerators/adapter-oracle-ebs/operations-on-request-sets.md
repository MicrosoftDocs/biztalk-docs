---
title: "Operations on Request Sets | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0537354d-821e-4cf9-a4d1-f4e7d1643df9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Request Sets
A request set in Oracle E-Business Suite is a set of reports and concurrent programs that are organized into various stages. You can use a single request set to run a set of reports and concurrent programs. Request sets are divided into one or more stages, and each stage contains a set of reports and concurrent programs. These stages are linked with each other, and the order of the execution of each stage is defined. For more Oracle-specific information about request sets, go to [http://go.microsoft.com/fwlink/p/?LinkId=129539](http://go.microsoft.com/fwlink/p/?LinkId=129539).  
  
 [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] enables you to execute request sets in Oracle E-Business Suite. The request sets are exposed as operations in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Since a request set contains a set of concurrent programs, those concurrent programs are the input parameters for a request set operation. Along with the concurrent programs, the request set operation takes four complex type parameters and a simple type parameter as input.  
  
> [!IMPORTANT]
>  You must set the applications context for request sets in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] before you can perform any operations on request sets. This is because setting applications context facilitates secure transactions in Oracle E-Business Suite by setting user preferences (such as responsibility, organization, and language settings) and access control for an artifact. For information about applications context, and how to set it, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## Complex type parameters
  
-   **SetRelClassOptions**: Enables you to set scheduling options for the request set. If both SetRelClassOptions and SetRepeatOptions are set then SetRelClassOptions will take precedence. SetRelClassOptions takes the following options as parameters:  
  
    -   **Application**: Indicates the short name of the application associated with the request set.  
  
    -   **ClassName**: Indicates the name of the class associated with the request set.  
  
    -   **CanceOrHold**: Indicates the Cancel or Hold flag.  
  
    -   **StaleDate**: Indicates the date on or after which this request set will be canceled if the request set has not yet run.  
  
    -   **ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetRelClassOptions fails. You can specify “True” (continue) or “False” (throw an exception).  
  
-   **SetPrintOptions**: Enables you to set the print options for the request set. SetPrintOptions takes the following options as parameters:  
  
    -   **Printer**: Indicates the printer name where the request set output should be sent.  
  
    -   **Style**: Indicates the print style used to print the request set output. For example, you can specify the orientation (“Landscape” or “Portrait”).  
  
    -   **Copies**: Indicates the number of copies to be printed of the request set output.  
  
    -   **SaveOutput**: Indicates whether or not to save the output file. You can specify “True” or “False”.  
  
    -   **PrintTogether**: Applicable only for sub-requests. Indicates how the output of sub-requests is printed. If you specify “Y”, the output of sub-requests is printed only after all the sub-requests are complete. If you specify “N”, the output of each sub-request is printed as it completes.  
  
    -   **ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetPrintOptions fails. You can specify “True” (continue) or “False” (throw an exception).  
  
-   **SetRepeatOptions**: Enables you to set the repeat options for the request set. SetRepeatOptions takes the following options as parameters:  
  
    -   **RepeatTime**: Indicates the time of day to repeat the request set.  
  
    -   **RepeatInterval**: This parameter is applicable only when **RepeatTime** is NULL. Indicates the interval between resubmissions of the request. Use this option along with **RepeatUnit** to specify the time between resubmissions.  
  
    -   **RepeatUnit**: This parameter is applicable only when **RepeatTime** is NULL. The unit of time used along with **RepeatInterval** to specify the time between resubmissions of the request. You can specify “Minutes”, “Hours”, “Days” or “Months”.  
  
    -   **RepeatType**: This parameter is applicable only when **RepeatTime** is NULL. Indicates whether the repeat interval is applied after the “start” of a previous request set execution or after the “end” of a previous request set execution.  
  
    -   **RepeatEndTime**: Indicates the date and time to stop resubmitting the request set.  
  
    -   **ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetRepeatOptions fails. You can specify “True” (continue) or “False” (throw an exception).  
  
-   **SetNlsOptions**: Enables you to set the NLS options for the request set. SetNlsOptions takes the following options as parameters:  
  
    -   **Language**: Indicates the NLS language.  
  
    -   **Language**: Indicates the language territory.  
  
    -   **ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetNlsOptions fails. You can specify “True” (continue) or “False” (throw an exception).  
  
## Simple type parameter
  
 **StartTime**: Indicates the time at which the request set should start running.  
  
 If the request set completes successfully, a concurrent request ID is returned. Otherwise, “0” is returned.  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)