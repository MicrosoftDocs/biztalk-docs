---
title: "Configure the JSON template for automatic deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.prod: biztalk-server
ms.topic: "article"
ms.assetid: 0b7755a6-5a5a-4a6b-8f99-ac12a5fbf3d4
caps.latest.revision: 4
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Configure the JSON template for automatic deployment


When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – (.btaproj). This new project holds all the BizTalk applications that you build using VSTS. 

Your project includes the `BizTalkServerInventory.json` file. In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and set a deployment sequence. 

This topic shows you how to update the json file. 

## Add assemblies, binding files, and deployment sequence

1. Open the `BizTalkServerInventory.json` file in your **BizTalk Server Application** project (.btaproj).

2. The template includes the following sections: 

    | | |
	|---|---|
	|BizTalkAssemblies | The assemblies used in your applications |
	|BindingFiles | The binding files you are referencing|
	| DeploymentSequence | The sequence for the elements to be installed|
	
	Sample template: 
	
	![FP1 Json template image 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
	> Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.

3. In `BizTalkAssemblies`, add the assemblies used by your BizTalk applications: 

	```
	"BizTalkAssemblies": [
		{
			"Name": "AssemblyName"
			"Path": "PathToAssembly
		}
	]
	```

4. In `BindingsFiles`, add the binding files for your BizTalk applications: 

	```
	"BindingsFiles": [
		{
			"Name": "Binding File Name"
			"Path": "PathToBindingFile
		}
	]
	```

5. In `DeploymentSequence`, add the application names in the order you want them deployed and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]: 

	```
	"DeploymentSequence": [
		{
			"NameOfFirst", "NameOfSecond", "NameOfThird"
		}
	]
	```
	
6. **Save** your changes. 

Once completed, the Visual Studio Team Service deployment task honors the required files and the install sequence. 

## Next step
[Configure tokens and variables](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md) in your binding file to deploy the same BizTalk application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s.

 