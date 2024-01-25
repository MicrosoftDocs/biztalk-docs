---
description: "Learn more about: Configuring Service for DRDA"
title: "Configuring Service for DRDA"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Service for DRDA
IT professionals can specify the basic required DRDA Service configuration settings by running the interactive or unattended installation program. The installation and configuration process registers the MsDrdaService.exe as a service.  
  
### Service Credentials  
 Using Windows Services Microsoft Management Console (MMC) snap-in, you can change the account name and password in which context to run the DRDA Service (C:\Program Files\Microsoft Host Integration Server 2020\system\MsDrdaService.exe). The configuration is stored in the Windows registry.  
  
1.  On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and click **Computer Management**.  
  
2.  In the **Computer Management (local)** settings pane, navigate to **Services** under **Services and Applications**.  
  
3.  In the Service pane, double click **Microsoft Service for DRDA**.  
  
4.  In the **Microsoft Service for DRDA Properties (local)** dialog, click **Log On**.  
  
5.  In the **Log On** dialog, click **This account**. Type a computer_name\user_name or domain_name\user_name. Optionally, click **Browse** to select a local or domain account.  
  
    > [!NOTE]
    >  When ESSO to map foreign credentials to AD credentials, this log on service account must be a member of the **SSO Affiliate Administrators** group.  
  
6.  Type a corresponding password in the **Password** and **Confirm password** edit boxes. Click **OK** to continue.  
  
    > [!NOTE]
    >  You must stop and re-start the service in order for the new credentials to utilize the newly-entered log service credentials.  
  
### Service Security Policy Rights  
 Using the Windows Policy Editor Microsoft Management Console (MMC) snap-in, you can change policy objects associated with the MsDrdaService and credentials. The MsDrdaService requires the **Log on as a service** policy rights.  
  
 This security setting allows a security principal to log on as a service. Services can be configured to run under the Local System, Local Service, or Network Service accounts, which have a built in right to log on as a service. Any service that runs under a separate user account must be assigned the right.  
  
### Application Configuration File  
 The DRDA Service configuration is stored in the MsDrdaService.exe.config application configuration (app config) file, and associated XML files (error message mapping and data type mapping). At runtime, the DRDA Service will monitor the MsDrdaService.exe.config file for changes. When detected, the DRDA Service will read and utilize the changed configuration information when processing new in-bound connections.  
  
 Post-installation, IT professionals can customize the DRDA Service configuration by editing the MsDrdaService.exe.config application configuration (app config) file using an XML editor and the associated C:\Program Files\Microsoft Host Integration Server 2020\system\Schemas\HostIntegrationDrdaServiceConfiguration.xsd file.
