---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Importing Binding Files
This topic provides some information concerning the import process when you deploy BizTalk Adapter for JD Edwards EnterpriseOne. When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.  
  
### To clean the target computer  
  
- Remove Send ports and Receive locations bound to the orchestration.  
  
   If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:  
  
   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
   Remove Send Port\VBScript\RemoveSendPort.vbs  
  
   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
   Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
   For example, from a command prompt run:  
  
   **cscript RemoveSendPort.vbs \<Send port name\>**  
  
## See Also  
 [Import the JD Edwards EnterpriseOne app](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)