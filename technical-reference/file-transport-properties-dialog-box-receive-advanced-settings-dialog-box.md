---
title: File Transport Properties Dialog Box, Receive, Advanced Settings Dialog Box
TOCTitle: File Transport Properties Dialog Box, Receive, Advanced Settings Dialog Box
ms:assetid: 2f67a63c-57f2-4ba9-af7c-151817c32c97
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559438(v=BTS.80)
ms:contentKeyID: 51527082
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.file.transport.receive.advanced
---

# File Transport Properties Dialog Box, Receive, Advanced Settings Dialog Box

 

Use the **File Transport Properties** dialog box to configure the receive location for the File adapter.

**Rename files while reading**  
Specify whether to rename files before picking them up for processing. For more information about using this option, see the appropriate topics in See Also.

Default Value: False

Type: Boolean

**Polling interval (ms)**  
Specify the interval in milliseconds that the File adapter will poll the specified location for new files.

Default Value: 60,000

Type: Int

Minimum value: 1,000 (set to 1 to disable polling)

Maximum value: 3,600,000

**Retry count**  
Specify the number of times that the File adapter will attempt to delete a file that it has read and submitted to BizTalk Server.

Default Value: 5

Type: Int

Minimum value: 0

Maximum value: 100

**Retry interval (ms)**  
Specify the initial interval in milliseconds that the File adapter waits before attempting to delete a file that it has read and submitted to BizTalk Server. This interval will double after each retry interval up to the specified maximum retry interval value.

Default Value: 10

Type: Int

Minimum value: 1

Maximum value: 1,000

**Maximum retry interval (ms)**  
Specify the maximum retry interval time in milliseconds that the File adapter waits before attempting to delete a file that it has read and submitted to BizTalk Server.

Default Value: 300,000

Type: Int

Minimum value: 1,000

Maximum value: 900,000

## See Also

[How to Configure a File Receive Location](https://msdn.microsoft.com/library/aa547108\(v=bts.80\))  
[Restrictions on the File Mask and File Name Properties](https://msdn.microsoft.com/library/aa578688\(v=bts.80\))  
[File Adapter](https://msdn.microsoft.com/library/aa561615\(v=bts.80\))

