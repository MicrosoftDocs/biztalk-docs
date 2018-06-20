---
title: "Step 1 (For Azure): Create the EDI Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d353129-04f0-456b-b371-b346959f5155
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1 (For Azure): Create the EDI Project
In this section, Contoso creates an EDI project using the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] April 2012 release. As part of the project, Contoso adds the following:  
  
- An internal sales order schema (**ECommerceSalesOrder.xsd**) to which the X12 840 EDI sales order schema will be transformed. Contoso uses the internal schema to process the message after it is received into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- A transform (**EDI840TOSALESORDER.TRFM**) to convert the X12 840 sales order schema to the **ECommerceSalesOrder** schema.  
  
  Contoso uses these artifacts while creating an agreement in the Azure BizTalk portal in [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].  
  
### To create EDI project  
  
1.  Open Visual Studio, from the **File** menu point to **New**, and then click **Project**.  
  
2.  In the **New Project** dialog box, from the **Installed Templates**, select **Service Bus**. Specify a project name and a location for the project, and then click **OK**.  
  
##  <a name="BKMK_CreateSchema"></a> To create a schema within the EDI project  
  
1.  From the Solution Explorer, right-click the project name you just created, point to **Add**, and then click **New Item**.  
  
2.  In the **Add New Item** dialog box, from the **Installed Templates**, select **Schema**, specify the name of the schema as **ECommerceSalesOrder.xsd**, and then click **Add**.  
  
3.  Edit and build the schema to resemble the following:  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns="http://ECommerceSalesOrder.Inbound" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://ECommerceSalesOrder.Inbound" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="SalesOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="CompanyCode" type="xs:string" />  
            <xs:element name="PartID" type="xs:int" />  
            <xs:element name="Quantity" type="xs:int" />  
            <xs:element name="AskPrice" type="xs:decimal" />  
            <xs:element name="RequestShipmentDate" type="xs:date" />  
            <xs:element name="Address">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Line1" type="xs:string" />  
                  <xs:element name="Line2" type="xs:string" />  
                  <xs:element name="City" type="xs:string" />  
                  <xs:element name="State" type="xs:string" />  
                  <xs:element name="Country" type="xs:string" />  
                  <xs:element name="Zipcode" type="xs:int" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Contact">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Firstname" type="xs:string" />  
                  <xs:element name="Lastname" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Comments" type="xs:string" />  
            <xs:element name="DateNow" type="xs:date" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
     You can use the Schema Editor to build this schema. For more information, see [Using BizTalk Editor](../core/using-biztalk-editor.md).  
  
4.  Save the schema.  
  
##  <a name="BKMK_CreateTrfm"></a> To create a transform within the EDI project  
  
1.  From the Solution Explorer, right-click the project name you just created, point to **Add**, and then click **New Item**.  
  
2.  In the **Add New Item** dialog box, from the **Installed Templates**, select **Map**, specify the name of the schema as **Edi840ToSalesOrder.trfm**, and then click **Add**.  
  
3.  In the map, for the source schema select **X12_00401_840.xsd**. This is the standard X12 schema for an EDI sales order. You must have already added this schema to the EDI project you created. You can download this, and other X12 schemas from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057). The X12 schemas are part of the **MicrosoftEdiXSDTemplates.zip** package available from the download location.  
  
4.  For the destination schema, select **ECommerceSalesOrder.xsd**. You created this schema earlier in this topic.  
  
5.  Create the map by connecting the relevant nodes in the source and target schemas.  
  
6.  Save the map.  
  
## See Also  
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)