---
description: "Learn more about: Maintaining the Non-Repudiation Database Tables"
title: "Maintaining the Non-Repudiation Database Tables"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Maintaining the Non-Repudiation Database Tables
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores messages for non-repudiation purposes in the MessageStorageIn and MessageStorageOut tables of the BTARNArchive database. Many messages in these tables can affect system performance. You may want to maintain these non-repudiation database tables by periodically purging and archiving messages from these tables, as appropriate.  
  
## Routine Database Maintenance  
 When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receives a message, it always saves the message in the MessageStorageIn table and initially sets the **ToBePurged** field to "1", which indicates that the message does not require non-repudiation. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] then decrypts and decodes the message to determine what the agreement is. After decrypting and decoding, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] examines the agreement to see whether it must save the message for non-repudiation purposes. If so, it sets the **ToBePurged** field to "0" and fills in the other fields of the message. If not, it leaves the **ToBePurged** field as "1" and does not fill in the other fields of the message.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not automatically delete messages with the **ToBePurged** field set to "1". In addition, it does not archive messages saved for non-repudiation to other tables. These two sets of messages can build up in the MessageStorageIn table and affect performance. As part of routine maintenance on the database, you may want to do the following:  
  
-   Run a stored procedure containing the following SQL statement to delete all messages in the MessageStorageIn table whose **ToBePurged** field is not equal to "0":  
  
    ```  
    delete MessageStorageIn where ToBePurged <> 0  
    ```  
  
-   After an appropriate period (which company policy may dictate), run a stored procedure to archive non-repudiation messages to an offline database that will not affect performance. You can determine this period by using the **TimeCreated** field in the MessageStorageIn table. After the non-repudiation period for a message has expired, you can delete the message from the archive database by using the following SQL statement (which deletes messages that are older than seven days):  
  
    ```  
    delete <archive table name> where datediff(d, TimeCreated, GetUTCDATA())>7  
    ```  
  
> [!NOTE]
>  The **TimeCreated** field in the MessageStorageIn table is in UTC.  
  
> [!NOTE]
>  You should not delete an incoming message that is less than one hour old.  
  
 When [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends an outgoing message, it has access to the non-repudiation agreement. If the agreement requires non-repudiation, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves the message in the MessageStorageOut table. If not, it does not save the message in the table. This means that there is no need for a **ToBePurged** field in this table. The only maintenance required for the MessageStorageOut table is to archive non-repudiation messages to an offline database after an appropriate period, and to delete each message after its non-repudiation period has expired. You can do so with the following SQL statement (which deletes messages that are older than seven days):  
  
```  
delete MessageStorageOut where datediff(d, TimeCreated, GetUTCDATA())>7  
```  
  
## See Also  
 [RNIF Message Processing](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md)   
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)
