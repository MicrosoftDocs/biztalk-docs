---
description: "Learn more about: Importing an XSD-based PIP"
title: "Importing an XSD-based PIP"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Importing an XSD-based PIP
While the majority of PIPS provided by RosettaNet.org are DTD-based, newer PIPS are XSD-based. The following procedure describes how to import XSD-based PIPS.

### To import an XSD-based PIP

1. Download the XSD-based PIP .zip file from [GS1 RosettaNet website](https://www.gs1us.org/resources/rosettanet) or the [CIDX website](https://oagi.org/pages/chem-estandards). 

1. Extract the files from the .zip file. The files that you need are in the subfolders of the XML folder.

2.  Open Visual Studio. Create a new BizTalk project.

3.  Open Windows Explorer, and move to the XML folder extracted in step 1. Select the first folder under the XML folder, drag it to Solutions Explorer in Visual Studio, and drop it into your project. Repeat for each of the subfolders in the XML folder, creating the same folder structure in your project.

    > [!NOTE]
    >  For a PIP7c7 PIP these folders would include the Domain, Interchange, System, and Universal folders. For this PIP, your project should contain Domain, Interchange, System, and Universal folders and their contents.

4.  If there is an .xsd file in the System folder, select it in Solution Explorer and change the namespace listed in the property page so that it does not contain the string ".System". For example, for PIP7c7 PIP, you could change the namespace to be "PIP7c7._System". Repeat for each .xsd file in the System folder. If you do not change the namespace, you will receive the following or a similar error:

    ```
    The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'PIP7C7.System'.
    ```

5.  Review all .xsd files to ensure that the \<schema\> TypeName and root node TypeName are not identical. For example, for a PIP7C7 PIP the PartnerIdentification.xsd in the Universal folder has the TypeName of 'PartnerIdentification' for both the \<schema\> (when PartnerIdentification.xsd is selected in Solution Explorer) and also the PartnerIdentification root node. To correct this, select PartnerIdentification.xsd in Solution Explorer, and then in the property page change the TypeName property so that it does not contain the same TypeName as the PartnerIdentification root node. For example, change the TypeName to be "_PartnerIdentification". If you do not take this step, you will receive the following error when you try to build the project:

    ```
    Node "<Schema>" - This schema file has a TypeName that collides with the RootNode TypeName of one of its root Nodes. Make sure that they are different.
    ```

    > [!NOTE]
    >  The File column in the error list will indicate which files have this problem.

6.  Build and then deploy the project.
