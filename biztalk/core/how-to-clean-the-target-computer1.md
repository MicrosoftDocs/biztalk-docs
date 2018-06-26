---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 


# How to Clean the Target Computer
Deployment overwrites the receive location configuration. When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  
  
### To clean the target computer  
  
- Remove send ports and receive locations bound to the orchestration.  
  
   If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:  
  
  - [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
  - [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
     For example, at a command prompt, run:  
  
     **cscript RemoveSendPort.vbs \<Send port name\>**  
  
