---
description: "Learn more about: Why Write Code For BAM?"
title: "Why Write Code For BAM?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Why Write Code For BAM?
In most circumstances you can use the BAM tools without writing your own code to perform your tracking functions. These tools are the BAM Add-in for Excel, the BAM Management utility, and the Tracking Profile Editor (TPE). BAM in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides interceptors for BizTalk orchestrations and messaging components (pipelines and ports). An interceptor is software that instruments an application so that it can collect data in a generic way based on a configuration file. You can instrument your application to use these interceptors by using the Tracking Profile Editor. For more information about the Tracking Profile Editor, see [Tracking Profile Editor](../core/tracking-profile-editor.md).  
  
 There are two primary scenarios, however, in which you will find it advantageous to instrument your application using the BAM APIs:  
  
- There is no BAM interceptor for the host you intend to monitor.  
  
- The built-in interceptor does not allow for the complexity of your application.  
  
  When there is no built-in interceptor, you can use the BAM **EventStream** APIs to capture the events of interest.  
  
> [!NOTE]
>  You can combine **EventStream** classes with the **BAMInterceptor** class to create your own interceptor. The BAM API SDK sample illustrates a simple generic interceptor that you can extend. By constructing your own interceptor you can instrument a number of similar processes without writing new code for each application. To view the BAM API SDK sample, see [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md).  
  
## See Also  
 [Implementing BAM Solutions](../core/implementing-bam-solutions.md)
