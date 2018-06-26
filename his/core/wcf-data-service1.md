---
title: "WCF Data Service1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8d6320c-a682-495b-b1cf-c7b84a57104d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# WCF Data Service
WCF Data Services enables you to create and consume Open Data Protocol (OData) services in your application. OData exposes your data as resources that are addressable by URIs, allowing you to access and change data by using the semantics of representational state transfer (REST), specifically the standard HTTP verbs of GET, PUT, POST, and DELETE. For more information, see [ASP.NET Dynamic Data Content Map](http://go.microsoft.com/fwlink/?LinkId=199029) (http://go.microsoft.com/fwlink/?LinkId=199029), [WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199030) (http://go.microsoft.com/fwlink/?LinkId=199030), and [A Developer's Guide to the WCF REST Starter Kit](http://go.microsoft.com/fwlink/?LinkId=199031) (http://go.microsoft.com/fwlink/?LinkId=199031).  
  
 This topic contains the following sections:  
  
-   [Adding the WCF Data Service](../core/wcf-data-service1.md#add)  
  
-   [Configuring the WCF Data Service](../core/wcf-data-service1.md#config)  
  
-   [Configure Internet Explorer for use with WCF Data Service](../core/wcf-data-service1.md#conf)  
  
-   [Testing the WCF Data Service](../core/wcf-data-service1.md#test)  
  
##  <a name="add"></a> Adding the WCF Data Service  
 This walkthrough builds on the Dynamic Data Web walkthrough in Dynamic Data Web. Follow these steps to create the WCF Data Service using a Visual Studio template.  
  
1.  From the **Solution Explorer**, right-click on the project name **DynamicData**. The Add New Item dialog box is displayed.  
  
2.  Under **Installed Templates**, in the left pane, select **Visual C#**.  
  
3.  In the center pane, select **WCF Data Service**.  
  
4.  In the **Name** box, enter a name for the data service. For example, enter the name **WcfDataServiceDB2.svc** and click **Add**.  
  
> [!IMPORTANT]
>  You must explicitly enable access to resources before you can access resources or associations. To enable read and write access to all resources in the Entity Data Model associated with the service, locate the InitializeService method and ensure it matches what is shown in the example.  
  
##  <a name="config"></a> Configuring the WCF Data Service  
  
1.  In the **WcfDataServiceDB2.cs** file, replace the code comments `/* TODO: put your data source class name here */` with `SAMPLEModel.SAMPLEEntities`.  
  
    ```  
    public class WcfDataServiceDB2 : DataService<SAMPLEModel.SAMPLEEntities>  
    ```  
  
     The next step is to allow access to the entities exposed by the Data Service. By default, access is not allowed to all entity sets. Access must be allowed for each entity set.  
  
2.  In the **WcfDataServiceDB2.cs** file, uncomment the code containing the **config.SetEntitySetAccessRule**. Replace **MyEntitySet** with an asterisk (\*), replace **AllRead** with **All**.  
  
    ```  
    using System;  
    using System.Data.Services;  
    using System.Data.Services.Common;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.ServiceModel.Web;  
  
    public class WcfDataServiceDB2 : DataService<SAMPLEModel.SAMPLEEntities>  
    {  
        // This method is called only once to initialize service-wide policies.  
        public static void InitializeService(DataServiceConfiguration config)  
        {  
            // TODO: set rules to indicate which entity sets and service operations are visible, updatable, etc.  
            // Examples:  
            config.SetEntitySetAccessRule("*", EntitySetRights.All);  
            // config.SetServiceOperationAccessRule("MyServiceOperation", ServiceOperationRights.All);  
            config.DataServiceBehavior.MaxProtocolVersion = DataServiceProtocolVersion.V2;  
        }  
    }  
  
    ```  
  
3.  In the **File** menu, click **Save WcfDataServiceDB2.cs**.  
  
4.  In Solution Explorer, right-click **WcfDataServiceDB2.svc**, and select **Set As Start Page**.  
  
##  <a name="conf"></a> Configure Internet Explorer for use with WCF Data Service  
 Follow these steps to configure Internet Explorer to view the WCF Data Service as an RSS feed.  
  
1.  In the **Tools** menu, click Internet **Options**, and then click **Content**.  
  
2.  The **Content** pane of the **Internet Options** dialog box is displayed.  
  
3.  Click **Settings** for **Feeds and Web Slices**. De-select the **Turn on feed reading view** check box, and then click **OK**.  
  
##  <a name="test"></a> Testing the WCF Data Service  
 Follow these steps to test the WCF Data Service that you have created.  
  
1. In the **Debug** menu, click **Start Debugging**. If prompted t enable debugging, click **OK**. Internet Explorer displays the WCF Data Service.  
  
    OData exposes data as resources that are addressable by URIs. The resource paths are constructed based on the entity-relationship conventions of the Entity Data Model. In this model, entities represent operational units of data in an application domain, such as DEPARTMENTs and EMPLOYEEs.  
  
2. In Internet Explorer, enter a URI to return all of the records from a DB2 table through the data service.  
  
    In OData, you address entity resources as an entity set that contains instances of entity types. For example, the URI http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders returns all of the orders from the Northwind data service that are related to the customer with a CustomerID value of ALFKI.  
  
   ```  
   http://localhost:36651/DynamicData/WcfDataServiceDB2.svc/DEPARTMENTs  
   ```  
  
3. Close the browser when you have finished viewing the database records.  
  
## See Also  
 [Dynamic Data Web](../core/dynamic-data-web1.md)   
 [Entity Framework](../core/entity-framework2.md)