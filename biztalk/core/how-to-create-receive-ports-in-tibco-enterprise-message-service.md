---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-receive-handlers/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# How to Create Receive Ports in TIBCO Enterprise Message Service
Follow these steps to create a receive port.  
  
### To create a receive port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.  
  
3.  In the **Receive Port Properties** window, on the **General** page, do the following:  
  
    1.  In the **Name** field, type `ReceiveFromTIBCOEMS`.  
  
    2.  In the **Authentication** group box, specify how messages are handled when using authentication.  
  
    3.  Select the **Enable routing for failed messages** checkbox.  
  
4.  On the **Receive Locations** page, do the following:  
  
    1.  Click **New**.  
  
    2.  In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.  
  
    3.  From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.  
  
    4.  From the **Receive pipeline** drop-down list, select the receive pipeline.  
  
    5.  On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.  
  
    6.  Select the **Enable service window** checkbox.  
  
    7.  Click **OK**.  
  
5.  On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.  
  
6.  On the **Tracking** page, select the desired tracking message bodies and tracking message properties.  
  
7.  Click **OK**.  
  
