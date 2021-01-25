---
description: "Learn more about: Importing Data for the Cross Referencing Functoids"
title: Importing Data for the Cross Referencing Functoids
TOCTitle: Importing Data for the Cross Referencing Functoids
ms:assetid: 9eb847a6-bc9c-4459-8c8b-c7286c69c642
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577624(v=BTS.80)
ms:contentKeyID: 51530019
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Importing Data for the Cross Referencing Functoids

 

The cross referencing database functoids use data from tables stored in the **BizTalkMgmtDb** SQL Server database. The Configuration Wizard creates the necessary tables in the database during installation. The tables are, however, initially empty.

The BizTalk Server Cross Reference Import tool (btsxrefimport.exe) reads data from a group of nine XML documents and stores the data in the appropriate tables.


> [!NOTE]
> <P>You must populate the tables in order to use the cross referencing functoids (<STRONG>Format Message</STRONG>, <STRONG>Get Application ID</STRONG>, <STRONG>Get Application Value</STRONG>, <STRONG>Get Common ID</STRONG>, <STRONG>Get Common Value</STRONG>, <STRONG>Remove Application ID</STRONG>, and <STRONG>Set Common Value</STRONG>).</P>



This section describes how to the use the tool, and the format of each of the required XML documents.

## In This Section

  - [BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)](biztalk-server-cross-reference-import-tool-btsxrefimport-exe.md)

  - [SetUp-Files Document](setup-files-document.md)

  - [listOfAppType Document](listofapptype-document.md)

  - [listOfAppInstance Document](listofappinstance-document.md)

  - [listOfIDXRef Document](listofidxref-document.md)

  - [listOfIDXRefData Document](listofidxrefdata-document.md)

  - [listOfValueXRef Document](listofvaluexref-document.md)

  - [listOfValueXRefData Document](listofvaluexrefdata-document.md)

  - [listOfMessageDef Document](listofmessagedef-document.md)

  - [listOfMessageText Document](listofmessagetext-document.md)

