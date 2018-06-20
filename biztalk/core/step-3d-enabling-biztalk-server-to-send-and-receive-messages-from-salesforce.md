---
title: "Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 470c4a72-1e97-4493-8958-33a13f793ffd
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce
We must authenticate with Salesforce while sending messages using the REST interface. The authentication methods for REST calls supported by Salesforce are not available out of the box with the WCF-WebHttp adapter, which we’ll use to invoke Salesforce’s REST interface. So, we’ll create a custom WCF endpoint behavior and then attach it to WCF-WebHttp send adapter that we’ll configure to invoke the Salesforce REST interface.  
  
 Similarly, the XML response received from Salesforce will not contain any namespace. For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process the response message against the response schema, the response message must include the target namespace. So, we’ll create a custom pipeline using the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to add a namespace to the response message. We’ll then use this custom pipeline as the receive pipeline for request-response WCF-WebHttp send port.  
  
## Add a Custom WCF Behavior for Salesforce Authentication  
 Salesforce provides different options for client applications to authenticate with Salesforce. We’ll use what Salesforce terms as the [Username-password](http://go.microsoft.com/fwlink/?LinkId=287082) flow. On the client side, WCF enables you to create [Message Inspectors](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx) to alter messages before they are sent or after they are received. A message inspector is an extension to the client runtime and is configured as a behavior. A behavior, in turn, is added to a behavior extension element. This behavior extension element is registered in the machine.config with an element name, which makes it available to be configured as a custom behavior on a WCF port. For more information, see [Extending WCF with Custom Behaviors](http://msdn.microsoft.com/magazine/cc163302.aspx). We are going to use this approach to incorporate the username-authentication flow for authenticating with Salesforce. The broad steps that we’ll follow are:  
  
-   Create a message inspector that makes an HTTP POST call to the Salesforce authentication endpoint and receives an access token. The message inspector then adds the authentication token as the value of the Authorization header of the query message being sent to Salesforce. The message inspector also adds the Accept header to the request message so that the response received is in an XML format. Otherwise, Salesforce sends the message in the default JSON format.  
  
-   Create an endpoint behavior to apply the message inspector to the client endpoint.  
  
-   Create a behavior extension element to enable configuration of the endpoint behavior.  
  
#### To create a message inspector  
  
1. As part of the **BtsSalesforceIntegration** solution in Visual Studio, create a C# Class Library. Name it `Microsoft.BizTalk.Adapter.Behaviors` and add the following namespaces:  
  
   ```  
   using System.ServiceModel.Description;  
   using System.ServiceModel.Dispatcher;  
   using System.ServiceModel.Channels;  
   using System.Xml;  
   using System.Net;  
   using System.IO;  
   using System.ServiceModel.Configuration;  
   using System.Configuration;  
   using System.Web.Script.Serialization;  
   ```  
  
2. From the Solution Explorer, add references to `System.ServiceModel`, `System.Web.Extensions`, and `System.Configuration`.  
  
3. Add a class `SalesforceOAuthToken` with the following properties. This class represents the authorization token that is received from Salesforce.  
  
   ```  
   public class SalesforceOAuthToken  
   {  
       public string id { get; set; }  
       public string issued_at { get; set; }  
       public string refresh_token { get; set; }  
       public string instance_url { get; set; }  
       public string signature { get; set; }  
       public string access_token { get; set; }  
   }  
   ```  
  
4. Add a class `SalesforceRESTSecurityBehavior` that implements the `IClientMessageInspector` and the `IEndpointBehavior`. This class includes the `HttpPost()` and `FetchOAuthToken()` methods that make an HTTP POST call to the Salesforce authentication endpoint to retrieve the authorization token.  
  
    Because the `SalesforceRESTSecurityBehavior` class implements the `IClientMessageInspector` interface, it must implement the two methods, `AfterReceiveReply()` and `BeforeSendRequest()`. For this scenario we do not need to do anything as part of the `AfterReceiverReply()` method. However, the `BeforeSendRequest()` method invokes the `FetchOAuthToken()` method, which in turn calls the `HttpPost()` method. The `BeforeSendRequest()` method then adds the authorization token as part of the message header. It also adds the **Accept** header to ensure that that the response received from Salesforce is in an XML format.  
  
    The `IEndpointBehavior` implementation simply adds the message inspector class to the client endpoint behavior.  
  
   ```  
   public class SalesforceRESTSecurityBehavior : IClientMessageInspector, IEndpointBehavior  
   {  
       // Some constants  
       private static string SalesforceAuthEndpoint = "https://login.salesforce.com/services/oauth2/token";  
  
       // Configuration Properties  
       private string username_;  
       private string password_;  
       private string consumerKey_;  
       private string consumerSecret_;  
       private int sessionTimeout_;  
  
       // Private Properties  
       private SalesforceOAuthToken token_;  
       private DateTime tokenExpiryTime_;  
  
       public SalesforceRESTSecurityBehavior(  
           string username,  
           string password,  
           string consumerKey,  
           string consumerSecret,  
           int sessionTimeout)  
       {  
           this.username_ = username;  
           this.password_ = password;  
           this.consumerKey_ = consumerKey;  
           this.consumerSecret_ = consumerSecret;  
           this.sessionTimeout_ = sessionTimeout;  
       }  
  
       private void FetchOAuthToken()  
       {  
           if ((tokenExpiryTime_ == null) || (tokenExpiryTime_.CompareTo(DateTime.Now) <= 0))  
           {  
               StringBuilder body = new StringBuilder();  
               body.Append("grant_type=password&")  
                   .Append("client_id=" + consumerKey_ + "&")  
                   .Append("client_secret=" + consumerSecret_ + "&")  
                   .Append("username=" + username_ + "&")  
                   .Append("password=" + password_);  
  
               string result;  
  
               try  
               {  
                   result = HttpPost(SalesforceAuthEndpoint, body.ToString());  
               }  
               catch (WebException)  
               {  
                   // do something  
                   return;  
               }  
  
               // Convert the JSON response into a token object  
               JavaScriptSerializer ser = new JavaScriptSerializer();  
               this.token_ = ser.Deserialize<SalesforceOAuthToken>(result);  
               this.tokenExpiryTime_ = DateTime.Now.AddSeconds(this.sessionTimeout_);  
           }  
       }  
  
       public string HttpPost(string URI, string Parameters)  
       {  
           WebRequest req = WebRequest.Create(URI);  
           req.ContentType = "application/x-www-form-urlencoded";  
           req.Method = "POST";  
  
           // Add parameters to post  
           byte[] data = Encoding.ASCII.GetBytes(Parameters);  
           req.ContentLength = data.Length;  
           System.IO.Stream os = req.GetRequestStream();  
           os.Write(data, 0, data.Length);  
           os.Close();  
  
           // Do the post and get the response.  
           System.Net.WebResponse resp = null;  
           resp = req.GetResponse();  
  
           StreamReader sr = new StreamReader(resp.GetResponseStream());  
           return sr.ReadToEnd().Trim();  
       }  
       #region IClientMessageInspector  
  
       public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
       {  
           // do nothing  
       }  
       public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
       {  
           // We are going to send a request to Salesforce  
           // Overview:  
           // This behavior will do the following:  
           // (1) Fetch Token from Salesforce, if required  
           // (2) Add the token to the message  
           // (3) Insert an Http Accept header so we get XML data in response, instead of JSON, which is default  
           // Reference: http://www.salesforce.com/us/developer/docs/api_rest/index.htm  
           //  
           // (1) Authentication with Salesforce  
           // (2) The token is added to the HTTP Authorization Header   
           // (3) Add the Accept Header  
           //  
  
           HttpRequestMessageProperty httpRequest = null;  
  
           if (request.Properties.ContainsKey(HttpRequestMessageProperty.Name))  
           {  
               httpRequest = request.Properties[HttpRequestMessageProperty.Name] as HttpRequestMessageProperty;  
           }  
  
           if (httpRequest == null)  
           {  
               // NOTE: Ideally, we shouldn’t get here for WebHttp  
               httpRequest = new HttpRequestMessageProperty()  
               {  
                   Method = "GET",  
                   SuppressEntityBody = true  
               };  
               request.Properties.Add(HttpRequestMessageProperty.Name, httpRequest);  
           }  
  
           WebHeaderCollection headers = httpRequest.Headers;  
           FetchOAuthToken();  
  
           headers.Add(HttpRequestHeader.Authorization, "OAuth " + this.token_.access_token);  
           headers.Add(HttpRequestHeader.Accept, "application/xml");  
  
           return null;  
       }  
  
       #endregion IClientMessageInspector  
  
       #region IEndpointBehavior  
  
       public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
       {  
           // do nothing  
       }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
       {  
           clientRuntime.MessageInspectors.Add(this);  
       }  
  
       public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
       {  
           // do nothing  
       }  
  
       public void Validate(ServiceEndpoint endpoint)  
       {  
           // do nothing  
       }  
  
       #endregion IEndpointBehavior  
   }  
   ```  
  
5. In the previous step we created a behavior class that applies the message inspector to the client endpoint. We now need to make this behavior available to the configuration experience for the WCF-WebHttp adapter that will send the request message to Salesforce. To make this behavior available for configuration we need to do two things:  
  
   - Create a class that derives from the `BehaviorExtensionElement`  
  
   - Register your BehavaiorExtensionElement in the \<extensions\>\\<behaviorExtensions\> element in the machine.config using an element name.  
  
     We’ll also add configuration properties to this class so that they are available from the WCF-WebHttp adapter configuration UI.  
  
   ```  
   public class SalesforceRESTBehaviorElement : BehaviorExtensionElement  
   {  
       public override Type BehaviorType  
       {  
           get { return typeof(SalesforceRESTSecurityBehavior); }  
       }  
  
       protected override object CreateBehavior()  
       {  
           return new SalesforceRESTSecurityBehavior(Username, Password, ConsumerKey, ConsumerSecret, SessionTimeout);  
       }  
  
       [ConfigurationProperty("username", IsRequired = true)]  
       public string Username  
       {  
           get { return (string)this["username"]; }  
           set { this["username"] = value; }  
       }  
  
       [ConfigurationProperty("password", IsRequired = true)]  
       public string Password  
       {  
           get { return (string)this["password"]; }  
           set { this["password"] = value; }  
       }  
  
       [ConfigurationProperty("consumerKey", IsRequired = true)]  
       public string ConsumerKey  
       {  
           get { return (string)this["consumerKey"]; }  
           set { this["consumerKey"] = value; }  
       }  
  
       [ConfigurationProperty("consumerSecret", IsRequired = true)]  
       public string ConsumerSecret  
       {  
           get { return (string)this["consumerSecret"]; }  
           set { this["consumerSecret"] = value; }  
       }  
  
       [ConfigurationProperty("sessionTimeout", IsRequired = false, DefaultValue = 300)]  
       public int SessionTimeout  
       {  
           get { return (int)this["sessionTimeout"]; }  
           set { this["sessionTimeout"] = value; }  
       }  
   }  
   ```  
  
6. Add a strong name key file to the project and build the project. Once the project builds successfully, add the assembly `Microsoft.BizTalk.Adapter.Behaviors` to the GAC.  
  
7. Add the following entry in the machine.config under System.ServiceModel\Extensions\BehaviorExtensions.  
  
   ```  
   <add name="Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce" type="Microsoft.BizTalk.Adapter.Behaviors.SalesforceRESTBehaviorElement, Microsoft.BizTalk.Adapter.Behaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=45bd7fe67ef032db"/>  
   ```  
  
    You can retrieve the public key token for the assembly from the GAC. Also, if you are creating this application on a 64-bit computer, you must add this entry to both 32-bit and 64-bit versions of the machine.config.  
  
## Add a Custom Pipeline to Add Namespace to the Salesforce Response  
 The response received from Salesforce does not include a namespace. However, to process the response message against the response schema (QueryResult.xsd) we must include the namespace in the Salesforce response. In this section, we create a custom pipeline and use a custom pipeline component shipped with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to add a namespace to the response message. This custom pipeline is deployed with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application and will be used as the receive pipeline while configuring the WCF-WebHttp adapter.  
  
 Before performing the steps in this procedure, ensure that [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is installed and configured on the computer where you are creating this application.  
  
#### To add a custom pipeline  
  
1. Within the **BtsSalesforceIntegration** solution, create a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project. Name the project `CustomPipeline`.  
  
2. Within the **CustomPipeline** project, add a new receive pipeline. Name the pipeline as `AddNamespace.btp`.  
  
3. Within the **Decode** stage of the pipeline, from the toolbox, drag and drop the **ESB Add Namespace** pipeline component. Within the **Disassemble** stage, drag and drop the **XML disassembler** pipeline component.  
  
   > [!NOTE]
   >  If the **ESB Add Namespace** pipeline component is not listed in the toolbox, you can add it. Right-click the **BizTalk Pipeline Components** tab, and then click **Choose Items**. In the **Choose Toolbox Items** dialog box, click the **BizTalk Pipeline Components** tab, select the check box for **ESB Add Namespace** component, and then click **OK**.  
  
4. Add a strong name key file to the project and save the project.  
  
5. Right-click the **CustomPipeline** project and select **Properties**. In the **Deployment** tab, for **Application Name**, enter `SalesforceIntegration`.  
  
6. Save changes to the project.  
  
   In this topic, added a custom behavior to authenticate with Salesforce and a custom pipeline to add a namespace to the Salesforce response. We’ll use these custom components while configuring the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## See Also  
 [Step 3: Create the BizTalk Server Solution in Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)