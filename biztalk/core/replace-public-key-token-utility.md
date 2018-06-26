---
title: "Replace Public Key Token Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Replace Public Key Token Utility"
  - "utilities, Replace Public Key Token Utility"
  - "public key token"
ms.assetid: ed8673b9-af06-4bd7-b8b7-7371e4dd0fed
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Replace Public Key Token Utility
This utility can be used to replace either a public key token or variable in a file with a public key token derived from a strong name assembly key (.snk) file.  
  
 This utility might be useful when a developer is writing a script that uses the [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) to deploy an assembly. For the deployment to succeed, the fully qualified name of the assembly must be provided, which includes its public key token. The public key token for an assembly is extracted from an .snk file and assigned to the assembly when it is built. Before the assembly is deployed into a new environment, however, it is often rebuilt using a different public key token. As a result, the developer may not know what public key token will be used for the assembly when the deployment script is run.  
  
 There are two ways that you can use the Replace Public Key Token utility to address this situation:  
  
-   **Scenario 1.** In the deployment script, the developer can use either a public key token or a placeholder representing the public key token. Before running the script, a user can run the Replace Public Key Token utility to substitute the public key token or placeholder in the script file with the public key token extracted from the .snk file that was used to build the assembly for the destination environment.  
  
-   **Scenario 2.** The developer can configure the script to automatically substitute the new public key token, as follows: At the start of the script, invoke the Replace Public Key Token utility and point it to a .snk file that contains the public key token. Within the script, use the environment variable %NEWTOKEN% to represent the public key token. When the script runs, the utility extracts the value of the public key token from the .snk file and sets it into an environment variable %NEWTOKEN%. When the script runs, each instance of %NEWTOKEN% will be with substituted with the public key token from the specified .snk file. For example:  
  
    ```  
    ReplacePKT.bat key.snk  
    ...  
    ...  
    gacutil /u Assembly, ... PublicKey=%NEWTOKEN% ...  
    ```  
  
## Location in SDK  
 The Replace Public Key Token utility is located in:  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\ReplacePublicKeyToken\\.  
  
 The Replace Public Key Token utility comprises three files:  
  
-   ReplacePKT.bat  
  
-   ReplacePKT.vbs  
  
-   ReplacePKT.wsf  
  
## Procedures  
 Use the following procedure to replace all instances of a public key token or a placeholder in a file with a public key token extracted from an .snk file, as described in Scenario 1.  
  
#### To replace instances of a public key token or a placeholder in a file  
  
1. Make sure that the three Replace Public Key Token utility files (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf), the script file, and the .snk file are all available from the local computer.  
  
2. In a command window, change the directory to the folder containing the Replace Public Key utility files.  
  
3. From a command prompt, run the following command:  
  
4. **ReplacePKT \<** *.snk file* **\> \<** *old public key token* **\> \<** *file to replace* **\>**  
  
   |Option|Description|  
   |------------|-----------------|  
   |**\<** *.snk file* **\>**|Full path of the .snk file containing the public key token that you want substitute for the existing public key token or placeholder.|  
   |**\<** *old public key token* **\>**|Public key token or placeholder that you want to replace.|  
   |**\<** *file to replace* **\>**|Full path of the file in which you want to replace the public key token or placeholder.|  
  
    Example:  
  
    **ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**  
  
   Use the following procedure to automatically set an environment variable in a script that uses a public key token derived from an .snk file, as described in Scenario 2.  
  
#### To set an environment variable that uses a public key token  
  
1.  At the beginning of your script file, add the following line of code:  
  
    ```  
    ReplacePKT <filename>.snk  
    ```  
  
     Where \<*filename*\> is the name of the .snk file from which to derive the public key token.  
  
    ```  
    Example: ReplacePKT.bat MyToken.snk  
    ```  
  
2.  In your script file, use `%NEWTOKEN%` to represent the public key token.  
  
     Example:  
  
    ```  
    PublicKey=%NEWTOKEN%  
    ```  
  
3.  When you deliver your script file to your users, include the three files that comprise the Replace Public Key Token utility (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf). Make sure that users of your script copy all of the files to the same folder on the file system before running your script.  
  
## See Also  
 [Utilities in the SDK](../core/utilities-in-the-sdk.md)