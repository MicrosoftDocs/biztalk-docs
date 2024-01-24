---
description: "Learn more about: Deploying and Starting a New Version of an Orchestration Programmatically"
title: "Deploying and Starting a New Version of an Orchestration Programmatically"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Deploying and Starting a New Version of an Orchestration Programmatically
The code in this topic illustrates how to quickly deploy and start a new version of the orchestration. Because manual operations can take a few seconds to perform, manually unenlisting an orchestration and then starting a new version of it can result in suspended or duplicate messages. The programmatic method illustrated in this topic allows you to perform these operations much more quickly – reducing the likelihood of suspended and duplicate messages – and as a single transaction, so that if one operation fails, both orchestrations are left in the same state as they were at the beginning.  
  
> [!NOTE]
>  In rare cases, when the orchestration you are updating with a new version is operating under high load, some messages can become suspended even when you unenlist and enlist the orchestrations programmatically.  We recommend that after performing these operations, you check your suspended message queue and resume any suspended messages.  
  
 The following code sample illustrates how to use the Explorer OM API to unenlist an existing orchestration and start the new version of the orchestration.  
  
```  
using System;  
using Microsoft.BizTalk.ExplorerOM;  
#endregion  
namespace OrchestrationBinding  
{  
class OrchestrationBinding  
{  
static void Main(string[] args)  
{  
            UpdateOrchestration();  
}  
        static public void UpdateOrchestration()  
        {  
            // Create the root object and set the connection string  
            BtsCatalogExplorer catalog = new BtsCatalogExplorer();  
            catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI";  
            string orchestrationAssemblyV1 = "HelloWorld, Version=1.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationAssemblyV2 = "HelloWorld, Version=2.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationName = "Microsoft.Samples.BizTalk.HelloWorld.HelloSchedule";  
            try  
            {  
                BtsAssembly assemblyV1 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV1);  
                BtsAssembly assemblyV2 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV2);  
                BtsOrchestration orchestrationV1 = assemblyV1.Orchestrations[orchestrationName];  
                BtsOrchestration orchestrationV2 = assemblyV2.Orchestrations[orchestrationName];  
                orchestrationV1.Status = OrchestrationStatus.Unenlisted;  
                orchestrationV2.Status = OrchestrationStatus.Started;  
                // Commit the accumulated changes transactionally  
                catalog.SaveChanges();  
            }  
            catch (Exception e)  
            {  
                catalog.DiscardChanges();  
                throw;  
            }  
        }  
        static BtsAssembly FindAssemblyByFullName(BtsAssemblyCollection assemblies, string fullName)  
        {  
            foreach (BtsAssembly assembly in assemblies)  
            {  
                if (assembly.DisplayName == fullName)  
                    return assembly;  
            }  
            return null;  
        }  
}  
}  
```  
  
## See Also  
 [Updating BizTalk Applications](../core/updating-biztalk-applications.md)   
 [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md)   
 [How to Unenlist an Orchestration](../core/how-to-unenlist-an-orchestration.md)
