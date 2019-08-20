---
title: "Issuing and Redeeming a Single Sign-On Ticket | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a979e2dd-54ad-4387-b58f-b3f02fc4f5f9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Issuing and Redeeming a Single Sign-On Ticket
After you link a user and an affiliate application, you can issue tickets to help ensure security while maintaining communications. Single Sign-On ticketing works just like other ticketing technologies: before sending the message off, you append the Single Sign-On ticket to the message as a string. The server receives your message, decodes the ticket, and uses the information as appropriate.  
  
### To issue a Single Sign-On ticket  
  
1.  Create a new ticket object with a call to I`SSOTicket`.  
  
2.  Issue the ticket with a call to I`SSOTicket.IssueTicket`.  
  
### To redeem a Single Sign-On ticket  
  
1.  Create a new ticket object with a call to I`SSOTicket`.  
  
2.  Redeem the ticket with a call to I`SSOTicket.RedeemTicket`.  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)