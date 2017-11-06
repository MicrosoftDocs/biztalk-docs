---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# TIBCO Rendezvous Limitations
In TIBCO Rendezvous, field name uniqueness is not guaranteed. If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.  
  
 Other limitations include the following:  
  
-   Field ordering/sorting is not provided.  
  
-   According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used. BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.  
  
-   Secure connection to daemons is not supported.  
  
-   Custom data types are not supported.  
  
-   Certified Messaging is not supported on the transmit side.  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)