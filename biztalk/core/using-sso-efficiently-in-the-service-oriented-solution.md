---
title: "Using SSO Efficiently in the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, service solutions"
  - "service solution tutorial, SSO"
  - "SSO, using from code"
ms.assetid: 809e0ad3-cc7f-4095-87d1-63031675a47f
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using SSO Efficiently in the Service Oriented Solution
The service oriented solution uses Enterprise Single Sign-On (SSO) both to store configuration values and to handle credentials for the back-end systems. To reduce latency, the solution uses a local cache for the configuration values. The solution refreshes the cache every five minutes.  
  
 In many applications, the adapters handle the SSO operations—including getting an SSO ticket, redeeming the ticket, and using the credentials to gain access to the affiliate application. However, the inline version of the service oriented solution does not use adapters. It must use SSO from code.  
  
 This topic describes the caching mechanism used by the solution, as well as how the inline version of the solution uses SSO from code.  
  
## Local Caching of Configuration Values  
 The service oriented solution uses two objects, **ConfigPropertyBag** and **ConfigParameters**, to handle the configuration values. The **ConfigPropertyBag** class holds the values and is used only by the **ConfigParameters** class. The **ConfigParameters** class is used by the other parts of the solution to retrieve the configuration parameters. Both classes are in the **Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper** namespace.  
  
> [!NOTE]
>  The Service Oriented solution fixes the cache refresh interval at 300 seconds (5 minutes). You may, instead, want to make the cache refresh interval itself  a configurable property in this solution. This is done in the Business Process Management solution. For more information about how that solution handles SSO, see [Using SSO Efficiently in the Business Process Management Solution](../core/using-sso-efficiently-in-the-business-process-management-solution.md). Notice that, in such a case, a change in the refresh interval does not take effect until the cache is refreshed at the end of the old interval time.  
  
 The **ConfigPropertyBag** has the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|Read|Retrieves a value for a given property.|  
|Write|Assigns a value to a property.|  
  
 The class uses an instance of a .NET **NameValueCollection** to hold the values. The two access methods implement the **IPropertyBag** interface from the **Microsoft.BizTalk.SSOClient.Interop** namespace. The **ConfigPropertyBag** class is an internal class and used only by the **ConfigParameters** class.  
  
> [!NOTE]
>  Key names in the property bag are case insensitive. The underlying **NameValueCollection** uses case-insensitive hashing and case-insensitive comparisons.  
  
 The application uses the **ConfigParameters** class to handle the SSO configuration values. The class has the following public methods and attributes:  
  
|Method or Attribute|Description|  
|-------------------------|-----------------|  
|SSOConfigParameter|An enumeration for specifying configuration parameters.|  
|GetConfigParameters|A method used to retrieve a value for a given parameter. Uses the SSOConfigParameter to indicate the parameter.|  
  
 The **ConfigParameters** class uses the .NET Timer class and a delegate function to set up the refresh of the **ConfigPropertyBag**:  
  
```  
private static Timer cacheRefreshTimer;  
private static ISSOConfigStore ssoConfigStore;  
private static ReaderWriterLock syncLock;  
  
// Cache refresh interval in milliseconds  
private const int CacheRefreshInterval = 5 * 60 * 1000;  
private static ConfigPropertyBag ssoPropBag;  
  
static ConfigParameters()  
{  
    ssoConfigStore = new ISSOConfigStore();  
    ssoPropBag = new ConfigPropertyBag();  
    syncLock = new ReaderWriterLock();  
  
    ssoConfigStore.GetConfigInfo(SSO_CONFIG_APP,  
         SSO_IDENTIFIER_NAME, SSOFlag.SSO_FLAG_RUNTIME,  
         ssoPropBag);  
  
    cacheRefreshTimer = new Timer(  
        new TimerCallback(ConfigParameters.cacheRefreshCallback),  
        null, CacheRefreshInterval, CacheRefreshInterval);  
}  
```  
  
 Notice that the static constructor initializes the static member variables thus enabling the use of class methods without creating an instance of the class. The constructor creates instances of the SSO configuration store (**ISSOConfigStore**), the configuration property bag (**ConfigPropertyBag**), and a synchronization lock (**ReaderWriterLock**) used to control access to the **ConfigurationPropertyBag** during updates and reads. The constructor then uses **GetConfigInfo** to retrieve the SSO configuration values and to put them in the property bag. Finally, the constructor creates a **Timer** object that, after the specified interval, calls the delegate function, **cacheRefreshCallback**.  
  
 The **Timer** delegate function is relatively straightforward:  
  
```  
private static void cacheRefreshCallback(object state)  
{  
    // Disable the timer until we are done loading the cache.  
    cacheRefreshTimer.Change(Timeout.Infinite, CacheRefreshInterval);  
  
    // Put the data from SSO in a new property bag so that  
    // we don't have to lock the property bag and block it from being  
    // used. The SSO call is a remote call and may take a while.  
    ConfigPropertyBag propBag2 = new ConfigPropertyBag();  
    ssoConfigStore.GetConfigInfo(SSO_CONFIG_APP,   
        SSO_IDENTIFIER_NAME, SSOFlag.SSO_FLAG_RUNTIME, propBag2);  
  
    // Get a writer lock before updating the cached values.  
    syncLock.AcquireWriterLock(Timeout.Infinite);  
  
    try  
    {  
        ssoPropBag = propBag2;  
    }  
    finally   
    {  
        syncLock.ReleaseWriterLock();  
    }  
    // Enable the timer.  
    cacheRefreshTimer.Change(CacheRefreshInterval,   
        CacheRefreshInterval);  
}  
```  
  
 Notice that the cache refresh callback method disables the timer so that the method can run all the way through. Also notice the use of the locks to control access to the property bag. The **ReaderWriterLock** is the best choice here—it is designed for cases where there are more reads than writes. Notice also that the lock, **syncLock**, is static and declared at the class level that all threads share the same, single instance of it.  
  
## Using SSO from Code  
 When using single sign-on from code, the code must take on the role of the adapter: that is,retrieve the SSO ticket from the message, redeem the ticket to get the user name and password for the back-end system, and, finally, use the back-end system. The service-oriented solution does this through the **GetPendingTransactionsResponse** method of the **PendingTransactionsCaller** object.  
  
 The method appears as follows:  
  
```  
public static PendingTransactionsResponse GetPendingTransactionsResponse(XLANGMessage requestMsg)  
{  
    try  
    {  
        // Get config parameter values.  
        int ptTimeout = Convert.ToInt32(  
            ConfigParameters.GetConfigParameter(  
                ConfigParameters.  
                    SSOConfigParameter.  
                        PENDING_TRANSACTIONS_INLINE_TIMEOUT  
            )  
        );  
  
        string ptURL = ConfigParameters.GetConfigParameter(  
            ConfigParameters.  
                SSOConfigParameter.  
                    PENDING_TRANSACTIONS_URL  
        );  
        string ssoAffliateApp = ConfigParameters.  
            GetConfigParameter(ConfigParameters.  
                SSOConfigParameter.  
                    PENDING_TRANSACTIONS_SSO_AFFILIATE_APP  
            );  
  
        // Redeem the SSO ticket and get the userid/password to   
        // use to interact with Pending Transaction System.  
  
        // Extract the ticket…  
        string msgTicket = (string)requestMsg.  
            GetPropertyValue(typeof(BTS.SSOTicket));  
  
        // and the user name of the originating user.  
        string originatorSID = (string)requestMsg.  
            GetPropertyValue(  
                typeof(  
                    Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID  
                )  
            );  
  
        string pendTransUserName;  
        // Now, redeem the ticket.  
        string[] pendTransCredential =   
            ssoTicket.RedeemTicket(  
                ssoAffliateApp,  
                originatorSID,  
                msgTicket,  
                SSOFlag.SSO_FLAG_NONE,  
                out pendTransUserName  
            );   
  
        PendingTransactionsRequest req =   
            (PendingTransactionsRequest)requestMsg[0].  
                RetrieveAs(  
                    typeof(PendingTransactionsRequest)  
                );  
        PendingTransactionsResponse resp;  
  
        using (PendingTransactionsWebService  
            svc = new PendingTransactionsWebService())  
        {  
            svc.Url = ptURL;  
            svc.Timeout = ptTimeout;  
  
            // The web service uses basic authentication, so we  
            //need to send the user id and password in the request.  
            CredentialCache credCache = new CredentialCache();  
            NetworkCredential credentialToUse =  
                new NetworkCredential(  
                    pendTransUserName, pendTransCredential[0]  
                );  
            credCache.Add(new Uri(svc.Url), "Basic", credentialToUse);  
            svc.Credentials = credCache;  
  
            resp = svc.GetPendingTransactions(req);  
        }  
        return resp;                  
    }  
    catch (System.Net.WebException webEx)  
    {  
        if (webEx.Status == WebExceptionStatus.Timeout)  
        {  
            throw new PendingTransactionsTimeoutException();  
        }  
        else  
        {  
            Trace.WriteLine("Other Net.WebException: "  
                + webEx.ToString()   
                + (null == webEx.InnerException ? "" :  
                     ("Inner Exception: "   
                        + webEx.InnerException.ToString())  
                )  
            );  
            throw;  
        }  
    }  
    catch(System.Exception ex)  
    {  
        Trace.WriteLine("Other Exception: "  
            + ex.ToString()   
            + (null == ex.InnerException ? "" :   
                 ("Inner Exception: "  
                    + ex.InnerException.ToString())  
                  )  
            );  
        throw;  
    }  
}  
```  
  
 The method begins by retrieving configuration information, including the URL, for the back-end system and the name of the backend (affiliate) application.  
  
 To redeem the ticket, the method must extract the ticket and original requesting user name from the message. The message contains the ticket as one of the message context properties, **BTS.SSOTicket**. For more information, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. The method also extracts the **OriginatorSID** from the message context properties. With the ticket and the originator's name in hand, the method calls the RedeemTicket method on the ticket to retrieve the credentials.  
  
 The remainder of the code creates a .NET NetworkCredential cache for the credentials and calls the back-end Web service.  
  
> [!NOTE]
>  Because the user name and password come back from SSO in clear text, you want to minimize the lifetime of variables holding that information. Notice that the code declares the credential variables within a **try** block. Here, the variables expire upon exit from the **try** block.  
  
## See Also  
 [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md)