---
title: "Message Repair and New Submission Service Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "repairing messages, MrsrRepair orchestration"
  - "orchestrations, MrsrRepair orchestration"
  - "InfoPath forms, valid forms"
  - "messages, BAS"
  - "unparsed messages"
  - "repairing messages, unparsed messages"
  - "messages, unparsed messages"
  - "messages, InfoPath forms"
  - "Business Rule Engine"
  - "MrsrRepair orchestration"
  - "InfoPath forms, messages"
  - "BAS, messages"
ms.assetid: fe2ee009-bf63-4bc0-b231-ad8a2633719f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Repair and New Submission Service Processing
The MrsrRepair orchestration handles all Message Repair and New Submission operations, including processing the following:  

-   Messages requiring repair  

-   Unparsed messages  

-   New messages created in MRSR site  

## Processing Messages Requiring Repair  
 If a message needs to be repaired, the orchestration is alerted that the incoming message is coming from the disassembler. It only processes messages from the disassembler if the role capability is set to Create or Repair. The MrsrRepair orchestration subscribes to messages from the MessageBox that have the following properties:  

```  
A4SWIFT_Failed==true AND  
BTS_Operation=="A4SWIFT_DasmMarkedAsFailed" AND  
A4SWIFT_SwiftBound==true  
```  

 The inbound port of the MrsrRepair orchestration used for Message Repair and New Submission is bound to the Sts.Outbox.Location receive location. The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup program installs this receive location by default. When users submit messages back to the MRSR site, this receive location picks up the messages and routes them to the MrsrRepair orchestration.  

 The following table lists the valid [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms:  


| [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] Forms |       |       |              |              |       |
|-------------------------------------------------------------------------------|-------|-------|--------------|--------------|-------|
|                                     MT010                                     | MT011 | MT012 |    MT015     |    MT019     | MT020 |
|                                     MT021                                     | MT022 | MT023 |    MT028     |    MT029     | MT030 |
|                                     MT031                                     | MT032 | MT035 |    MT036     |    MT037     | MT039 |
|                                     MT041                                     | MT042 | MT043 |    MT044     |    MT045     | MT046 |
|                                     MT047                                     | MT048 | MT049 |    MT050     |    MT051     | MT052 |
|                                     MT055                                     | MT056 | MT057 |    MT059     |    MT061     | MT062 |
|                                     MT063                                     | MT064 | MT065 |    MT066     |    MT067     | MT068 |
|                                     MT069                                     | MT072 | MT073 |    MT074     |    MT075     | MT076 |
|                                     MT077                                     | MT081 | MT082 |    MT083     |    MT085     | MT087 |
|                                     MT090                                     | MT092 | MT094 |    MT102     |  MT102PLUS   | MT103 |
|                                   MT103Plus                                   | MT104 | MT105 |    MT106     |    MT107     | MT110 |
|                                     MT111                                     | MT112 | MT121 |    MT190     |    MT191     | MT192 |
|                                     MT195                                     | MT196 | MT198 |    MT199     |    MT200     | MT201 |
|                                     MT202                                     | MT203 | MT204 |    MT205     |    MT206     | MT207 |
|                                     MT210                                     | MT256 | MT290 |    MT291     |    MT292     | MT295 |
|                                     MT296                                     | MT298 | MT299 |    MT300     |    MT303     | MT304 |
|                                     MT305                                     | MT306 | MT307 |    MT308     |    MT320     | MT321 |
|                                     MT330                                     | MT340 | MT341 |    MT350     |    MT360     | MT361 |
|                                     MT362                                     | MT364 | MT365 |    MT380     |    MT381     | MT390 |
|                                     MT391                                     | MT392 | MT395 |    MT396     |    MT398     | MT399 |
|                                     MT400                                     | MT405 | MT410 |    MT412     |    MT416     | MT420 |
|                                     MT422                                     | MT430 | MT450 |    MT4555    |    MT456     | MT490 |
|                                     MT491                                     | MT492 | MT495 |    MT496     |    MT498     | MT499 |
|                                     MT500                                     | MT501 | MT502 |    MT503     |    MT504     | MT505 |
|                                     MT506                                     | MT507 | MT508 |    MT509     |    MT510     | MT513 |
|                                     MT514                                     | MT515 | MT516 |    MT517     |    MT518     | MT519 |
|                                     MT524                                     | MT526 | MT527 |    MT528     |    MT529     | MT535 |
|                                     MT536                                     | MT537 | MT538 |    MT540     |    MT541     | MT542 |
|                                     MT543                                     | MT544 | MT545 |    MT546     |    MT547     | MT548 |
|                                     MT549                                     | MT558 | MT559 |    MT564     |    MT565     | MT566 |
|                                     MT567                                     | MT568 | MT569 | MT574_IRSLST | MT574_W8BENO | MT575 |
|                                     MT576                                     | MT577 | MT578 |    MT579     |    MT581     | MT582 |
|                                     MT584                                     | MT586 | MT587 |    MT588     |    MT589     | MT590 |
|                                     MT591                                     | MT592 | MT595 |    MT596     |    MT598     | MT599 |
|                                     MT600                                     | MT601 | MT604 |    MT605     |    MT606     | MT607 |
|                                     MT643                                     | MT644 | MT645 |    MT646     |    MT649     | MT690 |
|                                     MT691                                     | MT692 | MT695 |    MT696     |    MT698     | MT699 |
|                                     MT700                                     | MT701 | MT705 |    MT707     |    MT710     | MT711 |
|                                     MT720                                     | MT721 | MT730 |    MT732     |    MT734     | MT740 |
|                                     MT742                                     | MT747 | MT750 |    MT752     |    MT754     | MT756 |
|                                     MT760                                     | MT767 | MT768 |    MT769     |    MT790     | MT791 |
|                                     MT792                                     | MT795 | MT796 |    MT798     |    MT799     |       |
|                                     MT800                                     | MT801 | MT802 |    MT810     |    MT812     | MT813 |
|                                     MT820                                     | MT821 | MT822 |    MT823     |    MT824     | MT890 |
|                                     MT891                                     | MT892 | MT895 |    MT896     |    MT898     | MT899 |
|                                     MT900                                     | MT910 | MT920 |    MT935     |    MT940     | MT941 |
|                                     MT942                                     | MT950 | MT960 |    MT961     |    MT962     | MT963 |
|                                     MT964                                     | MT965 | MT966 |    MT967     |    MT970     | MT971 |
|                                     MT972                                     | MT973 | MT985 |    Mt986     |    MT990     | MT991 |
|                                     MT992                                     | MT995 | MT996 |    MT998     |    MT999     |       |

## Processing Unparsed Messages  
 If the MrsrRepair orchestration determines that a message could not be parsed, it sets the appropriate flags, and then sends the message to the MRSR site Inbox for repair in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for unparsed messages. When the orchestration receives the message after repair, it sets the BTS.Operation property to "[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRCompleted" and the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed property to False, and then routes the message to the MessageBox. These properties ensure that the repaired unparsed message does not enter the message repair process again.  

 The unparsed repair form is called **Unparsed Message**.  

## Processing New Messages Created in MRSR  
 If the message received by the MrsrRepair orchestration was created in MRSR site, the orchestration is alerted that the incoming message is coming from [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] (not the disassembler), and that the message has been signed.  

## Common Operations  
 The MrsrRepair orchestration performs a series of common operations on all messages, whether they need repair, could not be parsed, or are new messages. The orchestration executes a loop that performs the common operations for each step of the workflow, including rekey verification, create, repair, and approve. This orchestration is used no matter what the department and role are.  

 These common steps include the following:  

1. Put the message in an envelope form.  

2. Send the message to MRSR site.  

3. Receive the message (after the user actions) from MRSR site through the Sts.Outbox.Location receive location. If a time-out occurs, the orchestration handles the time-out. If the time-out occurs while a user is repairing, verifying, or approving a message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] returns the message to the Repair inbox, resetting the workflow to the Repair stage.  

   > [!NOTE]
   >  The inbound port of the MrsrRepair orchestration used for Message Repair and New Submission is bound to the Sts.Outbox.Location receive location. This receive location must be running in a BizTalk host that is bound to servers that have MRSR site installed on them. That host is typically BizTalkServerApplication, but it can be a different host. If it is a different host, you must verify that the servers to which the host is bound have MRSR site installed on them.  

4. Verify that the signature entered by the user is proper for the role, and store that signature to verify role restrictions.  

5. If the content of the message was stored by a previous step, compare the content received from MRSR site with the stored message. The orchestration fails the message if there is not a match.  

6. Fail the message if the user rejected the changes.  

7. Perform XSD and BRE validation on the message if the user accepted the changes.  

8. If applicable, move to the next step.  

## Customizing the Repair Orchestration  
 You can customize the MrsrRepair orchestration by adding preprocessing or postprocessing functionality. For example, you could add an orchestration to the preprocessing steps, or add an orchestration shape prior to the existing send shape to promote a property. However, you cannot create or change the agreements or profiles associated with Message Repair and New Submission, because the MrsrRepair orchestration would not be aware of them. You cannot add new role definitions beyond repairer, creator, verifier, or approver. You also cannot change the structure, or add functionality to the core, of the orchestration.  

## Business Rules Policies  
 For the repair process, the repair orchestration calls the BizTalk Business Rule Engine (BRE) to load the master policy for the message type, for instance, MT103_Master_Policy.xml. The orchestration passes the BRE the message type and body. The message master policy contains a list of all other policies that pertain to that message type. The BRE loads all the policies for the message type. These policies include SWIFT_Reference_Policy, SWIFT_PartyIdentifier_Policy, network rule policies, and the validation policy specific to the message type. The BRE executes all of the policies listed in the master policy, regardless of errors, and returns all errors.