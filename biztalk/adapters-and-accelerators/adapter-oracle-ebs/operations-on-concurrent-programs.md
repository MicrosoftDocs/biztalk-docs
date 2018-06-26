---
title: "Operations on Concurrent Programs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbc40e4c-d5a1-4763-9683-09a744e5b656
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Concurrent Programs
Concurrent programs in Oracle E-Business Suite are surfaced as operations in [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  Along with the concurrent programs specific to an Oracle application, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] also surfaces the following three standard operations: Get_Status, Wait_For_Request, and Submit_Request. This implies that if an Oracle application has two concurrent programs, five operations will be exposed: one for each concurrent program, and three for the standard operations.  
  
 For information about:  
  
- Browsing and searching concurrent programs, see [Browse, Search, and Get Metadata for Oracle E-Business Operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
- How to invoke concurrent programs in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Invoke Concurrent Programs in Oracle E-Business Suite Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md).  
  
> [!IMPORTANT]
>  You must set the applications context for concurrent programs in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] before you can perform any operations on concurrent programs. This is because setting applications context facilitates secure transactions in Oracle E-Business Suite by setting user preferences (such as responsibility, organization, and language settings) and access control for an artifact. For information about applications context, and how to set it, see Set Application Context[Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 The following sections provide information about the operations exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] for concurrent programs.  
  
##  <a name="Concurrent"></a> <Concurrent_Program_Name> Operation  
 As mentioned earlier, there will be as many <Concurrent_Program_Name> operations as the number of concurrent programs in an Oracle Aapplication. The <Concurrent_Program_Name> operation takes five standard parameters:  three of complex type and two of simple type.  
  
> [!NOTE]
>  For the concurrent programs that do not expose their metadata, the Oracle E-Business adapter exposes 100 optional parameters for each of these concurrent programs. To invoke these concurrent programs successfully, the user must consult the Oracle E-Business Suite documentation to figure out the parameters for a concurrent program that require a value, and then specify them. An example of such a concurrent program is **Journal Import** (actual name: **GLLEZL**) in the **General Ledger** application.  
  
 **Complex type parameters**  
  
- **SetOptions**: Enables you to set options for the concurrent program before submitting the request. SetOptions takes the following options as parameters:  
  
  -   **Implicit**: Indicates whether to display the concurrent request in the user’s Concurrent Requests form in Oracle E-Business Suite. You can specify any of the following four values: **No**, **Yes**, **Error** or **Warning**. Specifying **No**causes the requests to be displayed in the user’s Concurrent Requests form in Oracle E-Business Suite. Specifying **Yes** implies that the request may be viewed only from the system administrator's privileged Concurrent Requests form. Specifying **Error** causes the request to be displayed in the user’s Concurrent Requests form only if it fails. Specifying **Warning** causes the request to display in the user’s  Concurrent Requests form only if it there is a warning or an error.  
  
  -   **Protected**: Indicates whether the concurrent request is protected against updates made using the Concurrent Requests form in Oracle E-Business Suite. You can specify **Yes** (protected) or **No** (not protected).  
  
  -   **Language**: Indicates the National Language Support (NLS) language. If no value is specified, it defaults to the current language.  
  
  -   **Territory**: Indicates the language territory. If no value is specified, it defaults to the current language territory.  
  
  -   **ContinueOnFail**: Indicates whether the concurrent request submission should continue or throw an exception in case **SetOptions** fails. You can specify **True** (continue) or **False** (throw an exception).  
  
- **SetPrintOptions**: Enables you to set the print options for the concurrent program before submitting the request. SetPrintOptions takes the following options as parameters:  
  
  -   **Printer**: Indicates the printer name where the concurrent request output should be sent. You cannot override this print option if it is already set in the Concurrent Programs form in Oracle E-Business Suite.  
  
  -   **Style**: Indicates the print style used to print the concurrent request output. For example, you can specify the orientation (**Landscape** or **Portrait**). If the print style is already set in the Concurrent Programs form in Oracle E-Business Suite, and the **Style Required** check box is selected, you cannot override this print option.  
  
  -   **Copies**: Indicates the number of copies to be printed of the concurrent request output.  
  
  -   **SaveOutput**: Indicates whether or not to save the output file. You can specify **Yes** or **No**.  
  
  -   **PrintTogether**: Applicable only for those requests that contain sub-requests. Indicates how the output of sub-requests is printed. If you specify **Y**, the output of sub-requests is printed only after all the sub-requests are complete. If you specify **N**, the output of each sub-request is printed as it completes.  
  
  -   **ContinueOnFail**: Indicates whether the concurrent request submission should continue or throw an exception in case **SetPrintOptions** fails. You can specify **True** (continue) or **False** (throw an exception).  
  
- **SetRepeatOptions**: Enables you to set the repeat options for the concurrent program before submitting the request. **SetRepeatOptions** takes the following options as parameters:  
  
  -   **RepeatTime**: Indicates the time of day to repeat the concurrent request.  
  
  -   **RepeatInterval**: This parameter is applicable only when **RepeatTime** is NULL. Indicates the interval between resubmissions of the request. Use this option along with **RepeatUnit** to specify the time between resubmissions.  
  
  -   **RepeatUnit**: This parameter is applicable only when **RepeatTime** is NULL. The unit of time used along with **RepeatInterval** to specify the time between resubmissions of the request. You can specify **Minutes**, **Hours**, **Days** or **Months**.  
  
  -   **RepeatType**: This parameter is applicable only when **RepeatTime** is NULL. Indicates whether the repeat interval is applied after the “start” of a concurrent request execution or after the “end” of a concurrent request execution.  
  
  -   **RepeatEndTime**: Indicates the date and time to stop resubmitting the concurrent request.  
  
  -   **ContinueOnFail**: Indicates whether the concurrent request submission should continue or throw an exception in case **SetRepeatOptions**. You can specify **True** (continue) or **False** (throw an exception).  
  
  **Simple Type Parameters**  
  
- **Description**: Description of the concurrent request.  
  
- **StartTime**: Indicates the time at which the concurrent request should start running.  
  
## Get_Status operation  
 The standard operation, Get_Status, returns the request phase/status and the completion message of a concurrent program. This operation takes the request ID of a concurrent program (**RequestID**) as an input, and then returns the following information:  
  
-   **Phase**: The user-friendly request phase from FND_LOOKUPS.  
  
-   **Status**: The user-friendly request status from FND_LOOKUPS.  
  
-   **DevPhase**: The request phase as a string that can be used for program logic comparisons.  
  
-   **DevStatus**: The request status as a string that can be used for program logic comparisons.  
  
-   **Message**: The completion message if the request has completed.  
  
## Wait_For_Request operation  
 The standard operation, Wait_For_Request, waits for request completion, and then returns the request phase/status and the completion message. This operation takes the request ID of a concurrent program (**RequestID**), the number of seconds to wait between checks (**Interval**), and the maximum time in seconds to wait for the request's completion (**MaxWait**) as input parameters, and then returns the same information as in the Get_Status operation.  
  
## Submit_Request operation  
 The standard operation, Submit_Request, submits a concurrent request for processing by a concurrent manager. If the request completes successfully, this operation returns the concurrent request ID. Otherwise, it returns “0”.  
  
 The Submit_Request operation takes six standard parameters:  three each of complex type simple type. Apart from these parameters, it also takes the arguments of the concurrent program as an array of string.  
  
 **Complex type parameters**  
  
 The Submit_Request operation takes **SetOptions**, **SetPrintOptions**, and **SetRepeatOptions** as input parameters. For information about these parameters, see [&lt;Concurrent_Program_Name&gt; Operation](#Concurrent) earlier in this section.  
  
 **Simple type parameters**  
  
-   **Program**: Short name of the concurrent program for which the request should be submitted.  
  
-   **Description**: Description of the concurrent request.  
  
-   **StartTime**: The time at which the concurrent request should start running.  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)