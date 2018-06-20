---
title: "Planning for your solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Greenfield project"
  - "security, BTAHL7"
  - "BTAHL7, security"
  - "installing, planning"
  - "installing, installation types"
  - "HL7, security"
  - "security, HL7"
  - "Embedded installation"
  - "Migration project"
  - "Coexistence installation"
ms.assetid: a108c6d0-dd51-4bf9-85a0-103f60fae971
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for your solution
This section provides information about what you should consider when planning for your [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] solution.  
  
 You can implement BTAHL7 in the following ways:  
  
- **Greenfield project**. This scenario is a new installation of BTAHL7.  
  
- **Migration project**. This scenario occurs when the health-care organization is phasing out an existing integration broker. The organization migrates to BTAHL7.  
  
- **Coexistence**. This scenario involves an installation of BTAHL7 side-by-side with another integration engine.  
  
- **Embedded**. This scenario involves integrating BTAHL7 within a line-of-business application. You use BTAHL7 to add HL7 messaging capabilities to that application.  
  
  People tend to underestimate the amount of effort it takes to manage applications over time compared to the work it takes to create them in the first place. This is especially true when looking at large distributed institutions that need to carry out a complex array of data processing and management tasks. A hospitals or integrated health delivery organizations are excellent examples of such institutions. Such institutions face the need to provide software to support a myriad of functions, to enable information to be passed from application to application to avoid the need for duplicate and faulty data entry, to provide training for users and maintainers of the software, and to provide for the replacement of obsolete or outdated applications by improved ones. This replacement process has its own requirements for testing and education.  
  
  It would be impossible (prohibitively expensive) for such institutions to manage all their functions with a single integrated application. In the first place, the institutions are not going to want to tie their fortunes to a single vendor, and will not find all the function they need through a single vendor. In the second place, the simple operational needs of institutional processing make it impossible for institutions to be satisfied with a single integrated application. Therefore, institutions will support their needs with multiple applications. In order for these applications to interoperate, the applications need interfaces to exchange information. The number of applications and interfaces involved are often quite large. Given this distributed application architecture, the interface engine is a key instrument for managing the data processing for the institutions over time. The key issues are migration, mapping, and education. The job of BTAHL7 is to make addressing these issues as easy and efficient as possible:  
  
- **Mapping**. The biggest job in interface implementation is creating the mapping between application/database structures and the data structures used in the interface. Anything the tool does to make this easy and natural is good. In addition, since the mapping document will become a spec used by interface and application developers, it is important to be able to easily generate documentation of it. You use the BTAHL7 Configuration Explorer, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and BizTalk Server tools to develop and implement these maps.  
  
- **Migration**. You must maintain application interoperability over time as applications change. If you consider the issues related to replacing a single application, the need is to update the data source mappings to the applicable interfaces. With an interface engine there should be just one of these. You should consider where interfaces have been installed and if the interface standards changed over time. You will find that over time interface standards change and need to be migrated to the prevalent standards. It is recommended that your migration plan take into account any future interface changes. You need to map between standards, and between the different versions of the standard. Moreover, within the confines of a single standard—especially a flexible one such as HL7 V2—you have to deal with (across many applications) multiple implementations of the same standard. The interface engine should deal with this complexity in such a way that it is easy to manage.  
  
   A key migration task is that of migrating a body of interfaces from one standard to another. Here the task is to migrate all the mappings that use the old version to the new one—taking in account interface specific localization and extensions, which can be a complicated process. The tool should provide assistance with this migration.  
  
   You use the BTAHL7 Configuration Explorer Validation tab to specify the namespace of an any additional message type schemas.  
  
- **Education**. The people involved with managing and supporting applications will change over time. In addition, since the interfaces are central to the interoperability features of the collection of applications, their documentation will be come key tools in managing the overall enterprise. For both these reasons, it is valuable to provide easy to use, and easy to maintain documentation of a) the interface specifications, b) the application and introversion mappings, and c) the rationale for customization and localization activities.  
  
## See Also  
[Learn the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)