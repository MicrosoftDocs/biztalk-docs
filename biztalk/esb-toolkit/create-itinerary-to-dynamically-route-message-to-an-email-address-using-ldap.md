---
title: "How to: Create an Itinerary to Dynamically Route a Message to an Email Address Using an LDAP Query | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d9929dd-5e45-4b0d-90df-52a35e68b0ba
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to: Create an Itinerary to Dynamically Route a Message to an Email Address Using an LDAP Query
## Goal  
 This section demonstrates how to create an itinerary that queries an e-mail address through LDAP (Lightweight Directory Access Protocol) and then sends an e-mail message to the resolved endpoint using the BizTalk Server SMTP adapter.  
  
 In this How-to topic, you will complete the following steps:  
  
-   Create an itinerary routing slip to dynamically route a message using an LDAP query.  
  
-   Test the itinerary using the Itinerary Test Client sample application.  
  
## Prerequisites  
 The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
 The computer on which you will complete this section must have Microsoft Active Directory directory service configured and running (it is not required that the computer is the domain controller, but it must be connected to the domain). Also, an SMTP server must be configured and running; in order to test the outcome of this How-to topic, you must have a client with which to check the e-mail sent by the ESB.  
  
 The instructions in this section assume an organization named Global Bank, with a domain of globalbank.com, with an Active Directory Organizational Unit named Employees that contains a user named John Evans with a valid e-mail address in his profile (such as johne@globalbank.com). It is not necessary to replicate these environmental factors; however, for purposes of recreating this implementation in your environment, please account for these factors and make substitutions as necessary.  
  
## Steps  
  
#### To create an ESB itinerary domain-specific language (DSL) model  
  
1.  In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.  
  
2.  In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.  
  
3.  In the **Add New Item** dialog box, type **LdapResolution** in the **Name** box, and then click **Add**.  
  
#### To configure the properties of the itinerary  
  
1.  In Visual Studio, click the design surface of **LdapResolution.itinerary**. In the **LdapResolution** Properties window, configure the following properties:  
  
    1.  In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.  
  
    2.  Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).  
  
    3.  In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\LdapResolution** in the **File name** box, and then click **Save**.  
  
        > [!NOTE]
        >  This step enables you to export the itinerary as XML to a local file location. By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application. You will complete this process later in this How-to topic.  
  
#### To define the structure of the itinerary  
  
1. From the Toolbox, drag an **On-Ramp** model element to the design surface. In the **OnRamp1** Properties window, configure the following properties:  
  
   1.  Click the **Name** property, and then type **ReceiveNAOrder**.  
  
   2.  In the **Extender** drop-down list, click **On-Ramp ESB Extender**.  
  
   3.  In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.  
  
   4.  In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.  
  
2. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
   1.  Click the **Name** property, and then type **RouteMessageEmail**.  
  
   2.  In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.  
  
       > [!NOTE]
       >  This property defines that the process will take place in a pipeline (messaging). Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.  
  
   3.  In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.  
  
   4.  In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.  
  
3. Right-click the **Resolver** collection of the **RouteMessageEmail** model element, and then click **Add new Resolver**. In the **Resolver1** Properties window, configure the following properties:  
  
   1.  Click the **Name** property, and then type **LdapResolver**.  
  
   2.  In the **Resolver Implementation** drop-down list, click **LDAP Resolver Extension**.  
  
   3.  In the **Transport Name** drop-down list, click **SMTP**.  
  
   4.  Click the **Transport Location** property, and then type **{mail}**  
  
   5.  Click the **SearchRoot** property, and then type **ou=Employees,dc=globalbank,dc=com**  
  
       > [!NOTE]
       >  If you have not set up your environment according to the specifications in the "Prerequisites" section, replace the values in the preceding property with ones that are appropriate for your environment.  
  
   6.  Click the **Filter** property, and then change the value to **(&(objectClass=User)(&#124;(givenName=john)))**  
  
       > [!NOTE]
       >  Type the preceding value to replace the existing text.  
  
   7.  In the **ThrowErrorIfNotFound** drop-down list, click **True**.  
  
4. In the Properties window, click the **Endpoint Configuration** property, and then click the ellipsis button (...).  
  
   1. In the **Endpoint Configuration** dialog box, click the **EmailBodyText** property, and then type **Order is ready to be processed**.  
  
   2. Click the **From** property, and then type <strong>orders@globalbank.com</strong>.  
  
   3. Click the **MessagePartsAttachment** property, and then type **2**.  
  
   4. Click the **Subject** property, and then type **Order for {givenName}**.  
  
   5. Configure the **SMTPAuthentication, SMTPHost, UserName,** and **Password** properties using the connection information for your local environment.  
  
   6. Click **OK** to close the **Endpoint Configuration** dialog box.  
  
5. Right-click the **LdapResolver** resolver, and then click **Test Resolver Configuration**.  
  
6. In the Output window, verify the subject in the resolved **Endpoint Configuration** value is **Order for John**, and then verify that the resolved **Transport Location** is the e-mail address associated with the user's account in Active Directory (for example, johne@globalbank.com).  
  
7. In the Toolbox, click **Connector**. Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessageEmail** model element.  
  
8. From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteMessageEmail** model element. In the **OffRamp1** Properties window, configure the following properties:  
  
   1.  Click the **Name** property, and then type **EmailNAOrderDoc**.  
  
   2.  In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.  
  
   3.  In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.  
  
   4.  In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.  
  
9. From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteMessageEmail** model element and the **EmailNAOrderDoc** model element. In the **ItineraryService1** Properties window, configure the following properties:  
  
    1.  Click the **Name** property, and then type **SendPortFilter**.  
  
    2.  In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.  
  
    3.  In the **Off-Ramp** drop-down list, expand **EmailNAOrderDoc**, and then click **Send Handlers**.  
  
10. In the Toolbox, click **Connector**. Drag a connection from the **RouteMessageEmail** model element to the **SendPortFilter** model element.  
  
11. In the Toolbox, click **Connector**. Drag a connection from the **SendPortFilter** model element to the **EmailNAOrderDoc** model element.  
  
#### To export the model for use with the Itinerary Test Client  
  
1.  In Visual Studio, right-click the design surface of the **LdapResolution** itinerary, and then click **Export Model**.  
  
    > [!NOTE]
    >  The XML version of the itinerary opens in Visual Studio.  
  
2.  Save all project artifacts.  
  
3.  In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (LdapResolution.xml).  
  
#### To test the itinerary  
  
1.  Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).  
  
2.  In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.  
  
3.  In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries. Select **LdapResolution.xml**, and then click **Open** to load the itinerary.  
  
4.  Click **OK** to clear the **Itinerary Loaded Successfully** message.  
  
5.  In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.  
  
6.  In the **Select XML Document to load** dialog box, browse to C:\HowTos. Select **NAOrderDoc.xml**, and then click **Open** to load the test message.  
  
7.  Click the **Submit Request** button. When the test completes, click **OK** to dismiss the confirmation that appears.  
  
8.  Open Microsoft Outlook Express (or the mail client of your choice) and verify delivery of the message to the e-mail of John Evans.  
  
## Additional Resources  
 For more information, see the following related topics:  
  
-   [Development Activities](../esb-toolkit/development-activities.md)  
  
-   [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md)