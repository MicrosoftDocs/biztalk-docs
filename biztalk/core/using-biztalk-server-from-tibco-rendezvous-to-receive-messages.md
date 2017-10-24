---
redirect_url: /biztalk/core/using-tibco-rendezvous-receive-ports-from-biztalk-server/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Using BizTalk Server from TIBCO Rendezvous to Receive Messages
Microsoft BizTalk Adapter for TIBCO Rendezvous dispatches events from a queue on multiple threads. A BizTalk Server receive location is associated with one TIBCO Rendezvous event queue and its pool of dispatcher threads.  
  
## Memory Use and Errors  
 While processing events, the adapter keeps an eye on used resources. If memory use goes above the high-watermark, the adapter stops dispatching events until it reaches the low-watermark memory consumption. Note that this might result in TIBCO Rendezvous messages being missed for non certified messages (a TIBCO RV consumer has 60 seconds to remove messages from a queue). This data loss is reported as an error. If the adapter receives a TIBCO Rendezvous system advisory NO_MEMORY message, messages have already been lost.  
  
 BizTalk Adapter for TIBCO Rendezvous maintains a state, and it executes tasks differently based on that state. If the BizTalk Message Engine reports an error, and the adapter is configured to be a certified listener, it reports the error to TIBCO Rendezvous so that it can resubmit the message.  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Creating TIBCO Rendezvous Receive Handlers](../core/creating-tibco-rendezvous-receive-handlers.md)