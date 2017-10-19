---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 
# How to Create Send Ports for JD Edwards EnterpriseOne
Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a send port.  
  
### To create a send port  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.  
  
3.  Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.  
  
4.  In the **Send Port Properties** dialog box, do the following:  
  
    -   In the **Name** box, type a send port name (for example, `SendToJDE`).  
  
    -   From the **Type** drop-down list, select **JDEdwards**.  
  
    -   From the **Send handler** drop-down list, select the send handler address.  
  
5.  Click **OK**.  
  
