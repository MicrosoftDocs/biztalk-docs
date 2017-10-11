---
title: BizTalk adapters included with Host Integration Server | Microsoft Docs
description: Overview of BizTalk adapters for Host Applications, host files, DB2, and WebSphere MQ included with HIS
author: "MandiOhlinger"
manager: "anneta"

ms.date: "10/10/2017"
ms.prod: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.author: "mandia"
---

# BizTalk adapters for host systems


## BizTalk Adapter for Host Applications

The Microsoft BizTalk Adapter for Host Applications is designed for BizTalk Server. It is based on technology in Microsoft Transaction Integrator (TI) for Windows-Initiated Processing, which enables efficient client access to existing IBM mainframe zSeries (CICS and IMS) or midrange iSeries (RPG) server programs. 

The TI design tools are integrated with Visual Studio and BizTalk Server solutions, enabling IT developers to be highly productive when defining the client proxy and creating the XSD schema. For BizTalk Server administrators, the existing TI Manager, Microsoft Management Console (MMC) snap-in, has been enhanced to improve supportability and support the required remote BizTalk Server solution deployment scenarios.

See [BizTalk Adapter for Host Applications](https://msdn.microsoft.com/library/dn148497(BTS.80).aspx). 

## BizTalk Adapter for Host Files
The Microsoft BizTalk Adapter for Host Files is an advanced data adapter that enables IT organizations to access and integrate information stored in host file systems, including mainframe zSeries VSAM datasets and midrange iSeries physical files. 

Visual Studio design tools are used within a BizTalk Server solution to define a metadata map of the host program-described files, which is then exported as XSD for use with the BizTalk adapter. The configuration wizards are integrated into the BizTalk Server administration tools, allowing IT professionals to define dynamic send ports and static and solicit response receive ports, based on a simplified set of SQL commands (SELECT, INSERT, UPDATE, DELETE). 

This BizTalk adapter is based on the Microsoft .NET Framework Data Provider for Host Files that maps SQL to non-relational host datasets and members. This makes it easier for non-programmers to read and write host file data sources.

See [BizTalk Adapter for Host Files](https://msdn.microsoft.com/library/dn150042(BTS.80).aspx).

## BizTalk Adapter for DB2
The Microsoft BizTalk Adapter for DB2 is a relational database adapter that enables IT professionals to access vital data stored in IBM DB2 database servers on remote host computing platforms, IBM mainframe zSeries and midrange iSeries (DB2/400), and also IBM DB2 Universal Database (UDB) on open platforms. 

Using standard SQL commands and a configuration wizard built into BizTalk Server administration tools, IT professionals can create solutions that read and write to DB2 without any need for database programming. The DB2 adapter, which is based on the Microsoft .NET Framework Data Provider for DB2, supports a broad range of functions, including dynamic send ports, and static and solicit response receive ports.

See [BizTalk Adapter for DB2](https://msdn.microsoft.com/library/dn150160(BTS.80).aspx).

## BizTalk Adapter for WebSphere MQ
The Microsoft BizTalk Adapter for WebSphere MQ (Client-Based) uses IBM WebSphere MQ Client (Base-Client) and IBM WebSphere MQ Extended Transactional Client (Extended-Client) APIs to communicate with remote MQSeries Queue Managers. The adapter enables BizTalk Server to communicate directly with MQSeries Queue Managers deployed on non-Windows operating systems, without needing to deploy and manage WebSphere MQ Server for Windows, to efficiently exchange messages with line-of-business applications across the enterprise. 

When used with the Base-Client, the adapter provides non-transactional message processing, guaranteeing only the delivery of messages. It is the responsibility of the application on the receiving end to handle any duplicate messages. When used with the Extended-Client, the adapter provides transactional message processing to guarantee once-and-only-once delivery of messages.

See [BizTalk Adapter for WebSphere MQ](https://msdn.microsoft.com/library/dn191830(BTS.80).aspx).
