---
title: "Audit Management Operations  | Microsoft Docs"
description: How to Audit management Operations.
author: "Pravakar Garnayak"
ms.author: "pravagar"
manager: "dougeby"
ms.date: "01/10/2020"
ms.topic: conceptual
ms.prod: biztalk-server

# optional metadata

#ROBOTS:

ms.reviewer: 
ms.suite:
ms.tgt_pltfrm:
ms.assetid: 
ms.custom: "biztalk-2020"

---


# How to Audit Management Operations

## Overview

**Applicable starting BizTalk Server 2020**, administrators can configure BizTalk to generate audit trail for management operation on application artifacts like send port, receive port, receive locations, orchestrations and resources. Auditing of suspend/resume/terminate operation on service instances is also possible.

## Configure auditing

Auditing is not enabled by default. To enable auditing:

 1. Open **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.

 2. Check **Audit management operations**.

 3. Set **Maximum number of audit entries** to desired number. By default BizTalk stores **10000** most recent entries.

 4. Select **OK** to save your changes.

 5. Refresh **BizTalk Server Administration**, if you wish to do more management operation in same session.

   ![bts2020audit_configure](../core/media/configure-audit.png)

## Viewing audit logs

1. Make sure BizTalk operational data service is configured.
2. In your browser type  http://localhost/BizTalkOperationalDataService/AuditLogs .
3. To retrieve audit log entries between a date range use http://localhost/BizTalkOperationalDataService/AuditLogs?fromDate=2019-12-25T01:00:00&toDate=2020-01-10 . Supported date formats are : *yyyy-MM-dd* or *yyyy-MM-ddThh:mm:ss* .

## Audit Log Structure

An audit log has following information:

- **Id**: Id of type Guid, unique per entry.
- **BatchId**: Same for all audited operations performed in a single SQL transaction. Insightful in correlating user operations with lower level details
- **UserPrincipal**: User who performed the operation, for example, `jeffsmith@Fabricom.com`.
- **Machine**: Machine name from which operation was performed, for example, `machine1@contoso.com`.
- **ArtifactId**: Unique id of the artifact.
- **ParentArtifactId**: If an artifact is child of another artifact, then this field will have artifact id of the parent.
- **ArtifactType**: Type of artifact on which operation was performed, for example `SendPort, ReceivePort, Application etc`.
- **ArtifactName**: User configured name of the artifact, for example, `FTP send port`.
- **OperationName**: Action performed on the artifact, for example `Create`.

  Following table summarizes possible operations name on different artifacts:

   | Artifact type | Operation name|
   | --- | --- |
   | Ports | Create/Update/Delete |
   | Service Instances | Suspend/Resume/Terminate |
   | Application resources | Add/Update/Remove |
   | Binding file | Import|

- **Payload**: Contains information about what is changed in JSON structure, for example, `{"Description":"New description"}`.
- **CreatedDate**: Timestamp when the operation was performed.

When an artifact is created/updated, one or more audit entries are logged. For example, when a send port is created, 3 audit entries are logged. One each for send port, primary transport and secondary transport respectively. All these entries will have same **BatchId**. Audit log entries for primary and secondary transport can be correlated with send port using **ArtifactId** and **ParentArtifactId** values.
