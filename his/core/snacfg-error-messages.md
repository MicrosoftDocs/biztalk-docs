---
title: "Snacfg Error Messages2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2cb780c-5e74-4421-b97b-b36557516c6f
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Snacfg Error Messages
This section lists the error codes and their corresponding messages used by Snacfg commands.  
  
|Error Code|Message|  
|----------------|-------------|  
|3841|Insufficient privilege to run the SNA Manager program in this domain.|  
|3842|The activation value is invalid.|  
|3843|The link service is invalid.|  
|3844|The allocation timeout is invalid.|  
|3845|The audit level is invalid.|  
|3846|The Control Point Name is invalid. The name can be from one through eight alphanumeric characters long.|  
|3847|The Switched Connection Establishment Timeout is invalid. The range is from 10 through 500 seconds; the default is 300.|  
|3848|The Contact Retry Limit is invalid. The range is from 1 through 20; the default is 10.|  
|3849|The Contact Timeout is invalid. The range is from 5 (five-tenths of a second) through 300 (30 seconds). The default is 300 (30 seconds).|  
|3850|The Partner Min Contention Winner Limit is invalid. The range is from 0 through the parallel session limit; the default is 0.|  
|3851|The Minimum Contention Winner Limit is invalid. The range is from 0 through the parallel session limit; the default is 0.|  
|3852|The default connection for the display verb is invalid.|  
|3853|The DLC type is invalid.|  
|3854|The domain name is invalid.|  
|3855|The duplex value is invalid.|  
|3856|Internal : Bad existing record.|  
|3857|Facility Data is invalid. Facility Data can include as many as 126 hexadecimal digits.|  
|3858|The configuration file is corrupt or does not have correct structure.|  
|3859|The configuration file name is invalid. Verify that a primary or backup server is running in the domain you are trying to administer.|  
|3860|Internal : Bad File Handle.|  
|3861|The Idle Retry Limit is invalid. The range is from 1 through 255; the default is 10.|  
|3862|The Idle Timeout is invalid. The range is from 1 (one-tenth of a second) through 300 (30 seconds). The default is 300 (30 seconds).|  
|3863|The Automatic Activation Limit is invalid. The range is from 0 through the Minimum Contention Winner Limit.|  
|3864|The Security Key Type is invalid.|  
|3865|The Line Type is invalid.|  
|3866|The LU Name is invalid. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. Names for APPC LUs must be different from one another, and names for non-APPC LUs must be different from one another.|  
|3867|The LU Number is invalid. The range is from 1 through 255. The LU Number cannot be the same as that for any other LU using the connection, including local APPC LUs paired with remote APPC LUs that use the connection.|  
|3869|The Mode Name is invalid. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase.|  
|3870|The Display Model is invalid.|  
|3871|The Name or Alias is invalid.|  
|3872|The LU Name is invalid. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. Names for APPC LUs must be different from one another.|  
|3873|The NetView connection is invalid.|  
|3874|The Network Name is invalid. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase.|  
|3875|The Network Name is invalid. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase.|  
|3876|The value for 'Model can be overridden' is invalid.|  
|3877|The Packet Size is invalid. The possible values are 64, 128, 256, and 512. The default is 128.|  
|3878|The LU Partner is invalid.|  
|3879|The password is invalid. A password can contain from one through 10 characters.|  
|3880|The Poll Address is invalid. The address is a two-digit hexadecimal number; the address cannot be the reserved values 00 or FF.|  
|3881|The Poll Rate is invalid. The range is from 1 through 50 polls per second; the default is 5.|  
|3882|The Poll Retry Limit is invalid. The range is from 1 through 255; the default is 10.|  
|3883|The Poll Timeout is invalid. The range is from 1 (one-tenth of a second) through 300 (30 seconds). The default is 10 (1 second).|  
|3884|The Port is invalid.|  
|3885|Internal : Invalid record.|  
|3886|The Remote X.25 Address is invalid. The address usually consists of 12 hexadecimal digits, but can contain up to 15 hexadecimal digits.|  
|3887|The Role Type is invalid.|  
|3888|The RTM Timers Run Until value is invalid.|  
|3889|The first three digits of the Remote Node ID are invalid. These digits, also called the Block Number, can be any three hexadecimal digits except 000 or FFF, which are reserved.|  
|3890|The last five digits of the Remote Node ID are invalid. These digits, also called the Node Number, can be any five hexadecimal digits.|  
|3891|The Max Receive RU Size is invalid. The range is from 256 through 16384; the default is 1024.|  
|3892|The Pacing Receive Count is invalid. The range is from 0 through 63; the default is 4.|  
|3893|The Remote SAP Address is invalid. The address can be a 2-digit hexadecimal number that is a multiple of 04, between 04 and EC. The default is 04.|  
|3894|The Security Key is invalid. For a Security Key in Hex, type a 16-digit hexadecimal number. For a Security Key in Characters, type an eight-character string consisting of alphanumeric characters and/or $, @, #, and the period (.).|  
|3895|The server name is invalid.|  
|3896|The Parallel Session Limit is invalid. Legal values are between 1 and 10000 inclusive.|  
|3897|The Parallel Session Limit is invalid. Legal values are between 1 and 10000 inclusive.|  
|3898|The Timeout for Starting TPs is invalid. The range is from 1 through 3600 seconds; the default is 60 seconds.|  
|3899|The Timeout for Starting TPs is invalid. The range is from 1 through 3600 seconds; the default is 60 seconds.|  
|3900|The Maximum BTU Length is invalid. The range is from 265 through 16393; the defaults are: Token Ring:\t1929Ethernet:\t1493Channel:\t4105SLDC:\t\t265X25:\t\t1033.|  
|3901|The Remote Network Address is invalid. The address is a 12-digit hexadecimal value.|  
|3902|The Retry Limit is invalid. The range is from 0 through 255; the default is 10. A value of zero means the system uses its internal default retry limit.|  
|3903|The Receive ACK Threshold is invalid. The range is from 1 through 127; the default is 2.|  
|3904|The Unacknowledged Send Limit is invalid. The range is from 1 through 127; the default is 8.|  
|3905|The XID Retries value is invalid. The range is from 0 through 30; the default is 3.|  
|3906|The first three digits of the Local Node ID are invalid. These digits, also called the Block Number, can be any three hexadecimal digits except 000 or FFF, which are reserved.|  
|3907|The last five digits of the Local Node ID are invalid. These digits, also called the Node Number, can be any five hexadecimal digits except 00000, which is reserved.|  
|3908|The Max Send RU Size is invalid. The range is from 256 through 16384; the default is 1024.|  
|3909|Minimum Send RU is invalid.|  
|3910|The Pacing Send Count is invalid. The range is from 0 through 63; the default is 4.|  
|3911|User Data is invalid. User Data consists of an even number of hexadecimal charters, up to the maximum of 32 characters. The default is C3; this specifies the Qualified Logical Link Control (QLLC) protocol.|  
|3912|The User ID is invalid. The User ID can contain from one through 10 characters.|  
|3913|The PVC Alias is invalid. The range is from 1 through the number of configured PVC channels; the default is 1.|  
|3914|The configuration file has been created by newer version of [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)]. The Admin program only supports newer versions in read only mode.|  
|3915|The Window Size is invalid.|  
|3917|The connection cannot be modified when there are downstream LUs associated with it.|  
|3918|There is already a 3270 LU with this name.|  
|3919|There is already a 3270 Pool with this name.|  
|3920|There is already a Link Service with this name.|  
|3921|Multiple implicit partners or modes are not allowed for a local LU.|  
|3922|There is already an LU with this LU Number.|  
|3923|There is already an LUA LU with this name.|  
|3924|There is already an LUA Pool with this name.|  
|3925|The name or alias has already been used.|  
|3926|There is already a Host Integration Server with this name.|  
|3927|There is already a Downstream LU with this name.|  
|3928|There is already an Downstream LU Pool with this name.|  
|3929|The LU-LU pair already exists, or the adapter assignment already exists for the connection.|  
|3930|There is already a user with this name.|  
|3931|Unable to read the file.|  
|3932|Unable to write the file.|  
|3933|Field conflict. Unable to change.|  
|3934|Writing to active file is not allowed.|  
|3935|Configuration file was not found.|  
|3936|Limit reached on objects associated with this item.|  
|3937|Internal: Configuration is invalid.|  
|3938|Session Limit conflicts with contention settings.|  
|3939|Line Types do not match.|  
|3940|Unable to write to active configuration file.|  
|3941|Lost contact with remote domain.|  
|3942|Unable to allocate memory.|  
|3943|Internal: Memory corruption has occurred. Please reload configuration file.|  
|3944|The number of LUs or connections for this Host Integration Server has been exceeded. Each Host Integration Server is capable of supporting 250 connections and 15000 dependent LUs.|  
|3945|Internal: LUs are on different servers.|  
|3946|Implicit partner or mode is not implicit.|  
|3947|Internal: The item to be deleted is already absent from this grouping.|  
|3948|Internal: Record has already been added to the configuration.|  
|3949|A connection must have an associated link service.|  
|3950|The Initially Active value must be zero for Local/Local Partners.|  
|3951|The diagnostics record could not be found in the configuration file.|  
|3952|Parallel Sessions are not supported on this LU.|  
|3953|When a link service is to be used by multiple connections, and the connections accept incoming calls, the NRZ/NRZI settings for all the connections must match.|  
|3954|The configuration file is an older config file.|  
|3955|Internal: Target record already has an owner.|  
|3956|The internal control record for the configuration file has exceeded its maximum size.|  
|3957|During the conversion of an old Comm Server configuration file, COM.SEC was found to be corrupt, or of the wrong version type.|  
|3958|Insufficient privilege or the configuration file is locked for read\\\write access.|  
|3959|Limit reached on number of objects in a configuration file.|  
|3960|Limit reached on number of objects of this type.|  
|3961|Internal: Invalid record type.|  
|3962|Unable to change this record.|  
|3963|The connection cannot be modified when there are LUs associated with it.|  
|3964|The Session Limit is invalid.|  
|3965|One of the DLC timeout values is invalid.|  
|3966|This Return code is not used.|  
|3967|The LU Alias has already been used. The LU Alias cannot be the same as any other APPC LU on its server.|  
|3968|Unable to configure domain because the primary Host Integration Server for the domain is not active.|  
|3969|The same Remote Network Address and SAP have already been specified for this link service in connection %s. To create more than one connection to the same remote machine, add one or more 802.2/DLC link services via [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] Setup over the same adapter with different local SAP addresses. This will automatically create additional connections in SNA Manager. Alternatively, if further SAPs are available at the remote machine, choose a different Remote SAP for this connection.|  
|3970|No users or groups have been defined with Full Control Administration Access privileges. At least one user or group must be configured with permissions to alter the configuration.|  
|3971|The Fully Qualified LU Name has already been used. The combination of the Net Name and LU Name cannot be the same as any other APPC LU on the server.|  
|3972|Another Incoming Connection for this Link Service is already configured for XID 0. Multiple Incoming connections for one Link Service can only be configured if the connections use XID 3.|  
|3973|Another incoming connection for this link service is configured for a different NRZ/NRZI setting. Multiple incoming connections for one link service must use the same NRZ/NRZI setting.|  
|3974|Another Incoming Connection for this Link Service is configured for a different Poll Address. Multiple Incoming connections for one Link Service must use the same Poll Address.|  
|3975|Another Primary Multidrop Connection for this Link Service is configured for this Poll Address. Primary Multidrop connections for the same Link Service must use different Poll Addresses.|  
|3976|Another Primary Multidrop Connection for this Link Service is configured for a different NRZ/NRZI setting. Primary Multidrop connections for the same Link Service must use the same NRZ/NRZI setting.|  
|3977|Another Primary Multidrop Connection for this Link Service is configured for a different Maximum BTU Length. Primary Multidrop connections for the same Link Service must use the same Maximum BTU Length.|  
|3984|Another Primary Multidrop Connection for this Link Service is configured for a different XID Type. Primary Multidrop connections for the same Link Service must use the same XID Type.|  
|3985|Another Primary Multidrop Connection for this Link Service is configured for a different Duplex setting. Primary Multidrop connections for the same Link Service must use the same Duplex setting.|  
|3986|Another Primary Multidrop Connection for this Link Service is configured for a different Data Rate. Primary Multidrop connections for the same Link Service must use the same Data Rate.|  
|3987|Another Primary Multidrop Connection for this Link Service is configured for a different Data Rate. Primary Multidrop connections for the same Link Service must use the same Data Rate.|  
|3988|Another Primary Multidrop Connection for this Link Service is configured for a different Poll Timeout. Primary Multidrop connections for the same Link Service must use the same Poll Timeout.|  
|3989|Another Primary Multidrop Connection for this Link Service is configured for a different Poll Retry Limit. Primary Multidrop connections for the same Link Service must use the same Poll Retry Limit.|  
|3990|Another Primary Multidrop Connection for this Link Service is configured for a different Contact Timeout. Primary Multidrop connections for the same Link Service must use the same Contact Timeout.|  
|3991|Another Primary Multidrop Connection for this Link Service is configured for a different Contact Retry Limit. Primary Multidrop connections for the same Link Service must use the same Contact Retry Limit.|  
|3992|Leased SDLC connections cannot support Incoming Calls. Leased connections do not require either end to initiate the connection, therefore both ends treat the connection as Outgoing Calls only.|  
|3993|The Partner LU specified for the CPI-C Symbolic Destination Name does not exist.|  
|4000|The Mean time between broadcasts is invalid. The range is from 45 through 65535 seconds; the default is 60.|  
|4001|No protocols have been defined to send Server Broadcasts. At least one protocol must be configured to send Server Broadcasts.|  
|4002|The Channel Address is invalid.|  
|4003|Could not perform the necessary privilege lookup to enable the required privileges in your process.|  
|4004|Could not perform the necessary operations on the process token to enable the required privileges.|  
|4005|You do not have the privileges required to set system ACLs on files.|  
|4006|Unable to get or set security information on the config file.|  
|4007|All connections on this SDLC Link Service must have their multidrop primary flag set the same way.|  
|4008|Unable to obtain a write lock on the config file.|  
|4009|The config file has become out of date and you must reload it.|  
|4010|Bad parameter to function.|  
|4011|The LU Alias has already been used. The LU alias cannot be the same as any other APPC LU on its server.|  
|4012|You do not have the privileges necessary to lock the config file.|  
|4013|Only a primary 3.0 or later computer can write a pre-3.0 configuration file.|  
|4014|This configuration contains un-partnered dependent Local LU(s). These LU(s) have been discarded.|  
|4015|The primary configuration file could not be located. The primary Host Integration Server may be unavailable. No configuration changes may be made at this time.|  
|4016|This LU is already assigned to this user.|  
|4017|There is already a dependent Local APPC LU with this LU number.|  
|4018|There is already a 3270 LU with this LU number.|  
|4019|Insufficient privilege to modify the config file.|  
|4020|A 3270 LU name must be provided.|  
|4021|The AS/400 device name must be provided.|  
|4022|The Local LU Alias must be provide|  
|4023|The Remote LU Alias or Fully Qualified Name must be provided.|  
|4024|The mode must be provided.|  
|4025|A Workstation with the same ID exists. Please use a different ID.|  
|4026|The page width must be between 40 and 512.|  
|4027|This LU is already assigned to this workstation.|  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference.md)