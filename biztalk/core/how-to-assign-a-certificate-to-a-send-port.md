---
description: "Learn more about: How to Assign a Certificate to a Send Port"
title: "How to Assign a Certificate to a Send Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Assign a Certificate to a Send Port
This topic describes how to use the BizTalk Server Administration console to assign a security certificate to a send port. The certificate must exist in the Other People certificate store on the computer running BizTalk Server, or messages associated with this send port will not be processed, and errors will be logged.  
  
> [!NOTE]
>  The application developer can assign a security certificate to a send port during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To assign a certificate to a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to assign a certificate to a send port.  
  
3. Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Certificate**.  
  
4. If the certificate exists on the local computer, click **Browse**, browse to the certificate that you want to assign to this send port, and then click **OK**. Otherwise, skip this step.  
  
   > [!NOTE]
   >  Even if the certificate exists on the local computer, it must also exist on the computer running BizTalk Server, if different, before the send port will be able to process messages.  
  
5. If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)
