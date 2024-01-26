---
title: Creating logical units (LUs)
description: Learn about creating logical units (LUs)
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017
---

# Creating logical units (LUs)

After you configure the connection, you can create the 3270 LUs. The LUs can be display (terminal emulation) LUs, printer LUs, application LUs (LUAs), or downstream LUs.  

You can create LUs one at a time or in a consecutively numbered range. When you create a range of LUs, all the LUs are given the same properties. You can modify individual LUs after creating them.  

3270 LUs typically need an LU number, which identifies the LU on its connection. Make sure that this number matches the LU definition's **LOCADDR=** parameter in the Virtual Telecommunications Access Method (VTAM) or in the Network Control Program (NCP) GEN. You can configure up to 254 LUs for each connection, and you can consecutively configure them as a range of LUs.
  
## In This Section  

[Create a 3270 Display LU](how-to-create-a-3270-display-lu1.md)
[Create a 3270 Printer LU](how-to-create-a-3270-printer-lu1.md)
[Create a 3270 Application LU (LUA)](how-to-create-a-3270-application-lu-lua-2.md)
[Create a 3270 Downstream LU](how-to-create-a-3270-downstream-lu2.md)
[Create a Local APPC LU](how-to-create-a-local-appc-lu1.md)
[Create a Remote APPC LU](how-to-create-a-remote-appc-lu2.md)
  
## See also

[Step 3 (LU) Creating and Configuring 3270 LUs](step-3-lu-creating-and-configuring-3270-lus1.md)
