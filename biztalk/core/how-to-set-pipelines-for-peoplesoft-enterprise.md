---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 
# How to Set Pipelines for PeopleSoft Enterprise
Microsoft BizTalk Adapter for PeopleSoft Enterprise requires that you select an appropriate pipeline.  
  
## Setting Pipelines  
  
#### To set pipelines  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SSOSendToPeopleSoft`.  
  
    2.  From the **Type** drop-down list, select **PeopleSoft**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
4.  Click **OK**.  
  
## See Also  
 [Creating PeopleSoft Send Handlers](../core/creating-peoplesoft-send-handlers.md)