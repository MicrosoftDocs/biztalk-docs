---
redirect_url: /biztalk/core/architecture-of-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# PeopleSoft Enterprise Requirements

## Send Handler requirements  
 Microsoft BizTalk Adapter for PeopleSoft Enterprise contains a custom component interface (CI) and provides access to it through a Java API. A custom CI object, `GET_CI_INFO`, is deployed in the PeopleSoft system using PeopleSoft Tools to provide metadata information that is required by BizTalk Adapter for PeopleSoft Enterprise. For more information, see [Install Enterprise Applications adapters](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md).  
  
 Uploading the custom component interface is a one-time occurrence. This file, `GET_CI_INFO.pc`, installs with the product and must be installed before you can use the adapter to browse CIs. You must have access to the PeopleSoft Application Designer. The Application Designer application does not have to be on the BizTalk Server computer. You use the Application Designer to upload the custom CI onto the PeopleSoft computer that you browse.  
  
 You must have access to the PeopleSoft computer because you must set the environment variable CLASSPATH (or set the information in the **Transport Properties** screen) to point to PeopleSoft's `PSJOA/psjoa.jar` file.  
  
## See Also  
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 