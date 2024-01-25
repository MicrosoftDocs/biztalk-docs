---
description: "Learn more about: Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved"
title: "Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved
If you are moving the Tracking database but not the MessageBox database, when you edit the SampleUpdateInfo.xml file, make sure that you include an entry for the MessageBox database as well, even though the MessageBox database is not being moved. This must be done to ensure that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent job TrackedMessages_Copy_BizTalkMsgBoxDb is updated with the location of the new Tracking database.  
  
 For example, in the following SampleUpdateInfo.xml file, only the Tracking database is being moved from OldServer to NewServer. The MessageBox database is staying on OldServer:  
  
```  
<UpdateConfiguration>  
     <MessageBoxDB oldDBName="BizTalkMgmtDb" oldDBServer="OldServer" newDBName="BizTalkMgmtDb" newDBServer="OldServer" IsMaster="1"/>  
     <TrackingDB oldDBName="BizTalkDTADB" oldDBServer="OldServer" newDBName="BizTalkDTADB" newDBServer="NewServer"/>  
     <OtherDatabases>  
     </OtherDatabases>  
</UpdateConfiguration>  
```  
  
## See Also  
 [Moving Databases](../technical-guides/moving-databases.md)
