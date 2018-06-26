---
title: "Runtime Validation for the Orchestration Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "validating, assemblies"
  - "orchestrations, validating"
  - "validating, orchestration engine"
  - "schemas, validating"
  - "correlations, validating"
  - "validating, schemas"
  - "orchestration engine, runtime validation"
  - "assemblies, validating"
  - "validating, correlations"
  - "validating, orchestrations"
  - "validating"
ms.assetid: f6085889-05d6-4eba-a528-9d034c4e4225
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Runtime Validation for the Orchestration Engine
You can configure the orchestration engine to perform various runtime validations that can help you test your orchestration and diagnose configuration or data errors that might arise.  
  
 You can set flags in BTSNTSvc.exe.config, a configuration file that you can create or edit in the same directory as BTSNTSvc.exe (normally in the BizTalk deployment directory). You can set the following flags in the BTSNTSvc.exe.config file:  
  
- If you set the **ValidateAssemblies** flag to `True`, the engine tries to load all assemblies referenced by immediate dependent assemblies of an orchestration and upon failure throws Microsoft.XLANGs.Core.AssemblyValidationException.  
  
- If you set the **ValidateSchemas** flag to `True`, the engine uses System.Xml.XmlValidatingReader to validate every schema representing a message part type and upon failure throws System.Xml.XmlException.  
  
- If you set the **ValidateCorrelations** flag to `True`, the engine verifies that in a parallel convoy all messages that match one of the convoy receives have the same correlation property values and upon failure throws Microsoft.XLANGs.Core.CorrelationValidationException.  
  
- If you set the **ExtendedLogging** flag to `True`, the engine displays the promoted properties in the information for Microsoft.XLANGs.BaseTypes.PublishMessageException for the message that failed to publish.  
  
  If you want to disable a validation, remove the flag entirely from the configuration file. When all validations are on, the engine will validate assemblies, schemas, and correlation. For more information and examples of BTSNTSvc.exe.config, see [Orchestration Engine Configuration](../core/orchestration-engine-configuration.md).  
  
## Validate Assemblies  
 The orchestration engine will verify that any assemblies referenced by the orchestration are available. For the validation to succeed, all referenced assemblies must be in the Global Assembly Cache (GAC) when the first instance of the orchestration is activated. If the validation fails, an error will be logged to the application log and the orchestration will be suspended.  
  
## Validate Schemas  
 Any time an XSD part is assigned, the orchestration engine will validate the part's data against its schema. If the validation fails, the error will be logged to the application log and an exception will be thrown.  
  
## Validate Correlation  
 The orchestration engine will confirm that the property values that are specified for correlation with a given instance of an orchestration are reflected in any messages that are sent from that orchestration instance. If **validateCorrelation** is not set, the engine will assume that the sent message contains the correct correlation values, and no check will be performed.  
  
 If any correlation validation fails, the engine will log an error to the application log and throw an exception of type **CorrelationValidationException**.  
  
 By default, **validateCorrelation** is not set.  
  
## See Also  
 [Debugging Orchestrations](../core/debugging-orchestrations.md)   
 [Orchestration Engine Configuration](../core/orchestration-engine-configuration.md)