---
description: "Learn more about: Syntax for an EXEC Statement in Siebel"
title: "Syntax for an EXEC Statement in Siebel"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Syntax for an EXEC Statement in Siebel
Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients can also perform an EXEC operation on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. The syntax for the EXEC statement is:  
  
```  
EXEC  
<Business Service name>.<Business Service method>  
<value 1..n>,  
@parameter 1..n [OUTPUT],  
@parameter 1..n = <value>  
  
```  
  
 In the preceding syntax, `\<value 1..n\>` represents a set of unnamed parameters. These are hard-coded values. They usually represent IN parameters.  They can also represent INOUT parameters. However, if a hard-coded value is used for an INOUT parameter, the output value associated with that parameter cannot be retrieved after the EXEC statement is executed.  
  
 The `@parameter 1..n` syntax represents a set of named parameters, which can be IN, INOUT, or OUT parameters. The output parameters must be followed by the **OUTPUT** keyword.  
  
> [!NOTE]
>  The **OUTPUT** keyword must only be used with OUT parameters and not with INOUT parameters.  
  
 To specify parameter values inline, use the `@parameter 1..n = <value>` syntax.  
  
 All parameters must be comma-separated.  
  
 The following are examples of EXEC statements:  
  
```  
EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo 'InputValue', @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo @InOut, @Out OUTPUT, @In='InputValue'  
  
EXEC ExtractDataService.Echo 'InputValue', @Out OUTPUT, @InOut='InputValue'  
  
```  
  
> [!NOTE]
>  Every parameter name (like `@In` in the preceding example) must match the corresponding argument name in the Siebel Business Service method.  
  
## See Also  
 [Use the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)
