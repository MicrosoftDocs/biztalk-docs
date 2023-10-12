---
description: "Learn more about: Issuing and Redeeming a Single Sign-On Ticket"
title: "Issuing and Redeeming a Single Sign-On Ticket"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)
