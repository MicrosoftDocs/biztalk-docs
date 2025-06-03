---
description: "Learn more about: How to Modify or Update an Instance"
title: "How to Modify or Update an Instance1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Modify or Update an Instance
After you have retrieved an instance, you can modify your local copy and update your changes to the server.  
  
#### To modify or update an instance  
  
1.  Retrieve a local copy of the object with a call to **GetObject**.  
  
2.  If necessary, view the properties of the object with a call to the **Properties_** method.  
  
     Although not required, you may want to know the value of the property before you change it.  
  
3.  Make any changes to the object properties with a call to the **SWbemProperty.Value** method.  
  
     The **Value** method changes only the local copy. To save your changes to WMI, you must put the complete copy back in the WMI repository.  
  
4.  Put the object back in the WMI repository with a call to the **SWbemObject.Put_** or **SWbemObject.PutAsync_** methods.  
  
     As the names imply, **Put_** updates synchronously while **PutAsync_** updates asynchronously. Either method copies over the original instance with your modified instance. However, to take advantage of asynchronous processing, you must create a **SWbemSink** object.  
  
     The following example shows how to update an instance:  
  
    ```  
        Set ObjClass  = Namespace.Get("MsSna_LinkService_IpDlc")     
    ' Create new link service instance  
        Set NewInst   = ObjClass.SpawnInstance_  
        ' Set instance properties  
        NewInst.NetworkName = Left(strComputerName, 8)  
        NewInst.CPName = "IPDLCLS"  
        NewInst.NodeID = "05D.FFFFF"  
        NewInst.AddressType = 2  
        NewInst.LocalAddress = Trim(strLocalAddress)  
        NewInst.LENNode = strLenNode  
        NewInst.PrimaryNNS = strPrimaryNNS  
        if (strBackupNNS <> Empty) then  
            NewInst.BackupNNS = strBackupNNS  
        end if  
        ' Commit the instance  
        NewInst.Put_  
  
    ```
