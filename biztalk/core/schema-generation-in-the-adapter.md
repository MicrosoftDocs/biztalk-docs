---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Schema Generation in the Adapter
A TIBCO Rendezvous system does not include a message types repository. All the message construction and parsing is buried at the Rendezvous application level. Because of this limitation, Microsoft BizTalk Adapter for TIBCO Rendezvous cannot provide schema-generation capabilities.  
  
## Writing Schemas  
 You must write a schema and use **Add Existing Item** in Visual Studio to import it for use in orchestrations. Schemas are very important for BizTalk Server development tools and for integration in Visual Studio. BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.  
  
## See Also  
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)