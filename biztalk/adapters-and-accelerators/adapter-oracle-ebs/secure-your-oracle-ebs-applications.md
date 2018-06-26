---
title: "Secure your Oracle EBS applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76147120-57a8-4959-a0ff-77d04dee06a6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Secure your Oracle EBS applications
Oracle E-Business applications deal with sensitive business information such as customer account details. Applications that use the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission. Data protection and security are usually thought of in the following terms:  
  
- *Authorization* controls access to a resource based on the identity of the requester.  
  
- *Authentication* provides mechanisms for verifying the identity of a requester.  
  
- *Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.  
  
- *Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.  
  
  Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. The adapter uses these credentials to open connections to the Oracle database. These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.  
  
  The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
