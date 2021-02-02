---
description: "Learn more about: Error"
title: Error
TOCTitle: Error
ms:assetid: f1807ac8-cfb2-49eb-bf9d-876066294071
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561874(v=BTS.80)
ms:contentKeyID: 51533362
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts06.bam.portal.error
---

# Error

 

Following is a list of the most commonly encountered errors on the BAM portal.

## Incorrect link or PivotView name

### Error message

  - The link used to navigate to the portal is outdated or incorrect.

  - The Pivot View Name does not exist or is incorrect.

### Description

These errors can occur if the administrator has removed or renamed a view, an activity, or a PivotView report. Links to the BAM portal contain the View Name and Activity Name and can contain the PivotView name.

## Alert not found

### Error message

  - This alert could not be found. It may have been deleted or marked as private by another user.

### Description

The alert you are trying to access does not exist. If you are trying to access the alert through a link, the link is either outdated or it was deleted by another user.

## Could not open query

### Error message

  - Could not open the query: the document does not appear to be a valid search query.

### Description

When opening a saved query, you can receive this error if the BAM portal is not able to determine the type of document it received. The most likely causes of this error are opening an invalid query or a document that is not a BAM Portal query.

## Server not configured for alerting

### Error message

  - The current action cannot be completed because the server is not configured for alerting. Ask your System Administrator to enable alerting on the server and try again.

### Description

  - This error occurs when you attempt to use alerting-related features on a server that is not configured for alerting.

## Alert is private or you are not the owner of the alert

### Error message

  - This operation cannot be completed because you are not owner of this alert.

  - This operation cannot be completed because this alert is private.

### Description

Private alerts can be modified only by their owners.

## Cannot perform the requested action

### Error message

  - The Business Activity Monitoring Portal encountered a critical error and cannot perform the requested action. The server requires System Administrator's attention. Contact your System Administrator.

### Description

The BAM portal encountered a critical error that can only be corrected by your system administrator. When you receive this error, details of the error have been logged for your System Administrator.

## Unspecified error

### Error message

  - An unspecified error has occurred.

### Description

The BAM portal encountered an error when processing your request. This usually means that the BAM portal requires the attention of a system administrator. The exact source of the error was logged and is accessible by the administrator.

