---
description: "Learn more about: Creating and Deploying Policies for New Message Types"
title: "Creating and Deploying Policies for New Message Types"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating and Deploying Policies for New Message Types
To create and deploy policies for new message types:  
  
1.  Create a folder with the name of the message type inside MX Messages folder. For example, in this case the name of the folder would be setr.004.001.02.  
  
    ```csharp  
    (<xs:complexType name="Document">  
        <xs:sequence>  
            <xs:element name="setr.004.001.02" type="setr.004.001.02"/>  
        </xs:sequence>  
    </xs:complexType>)  
    ```  
  
2.  Place the schema file (*.xsd) along with the resulting master / validation policy file for this message type in this folder.  
  
3.  Update the MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools) with a keyword name. This name must be the first four letters of the message folder name. For example,  
  
    ```csharp  
    (<Keyword name ="setr" />)  
    ```  
  
4.  To create specific master / validation policies, take a copy of the master / validation policy files of the existing message and place it in the new message folder.  
  
5.  Change all of the references to message types in the master / validation policy to reflect the new message types.  
  
## Message Naming Conventions  
 Follow these conventions for message names:  
  
-   **Replacing the message name**: If the new message name is swift.if.ia.setr.004.001.02 and the old message whose policy files have been used is pacs.002.001.02, then replace all of the occurrences of pacs.002.001.02 with swift.if.ia.setr.004.001.02 within the policy files.  
  
    > [!NOTE]
    >  Message name is the name of the schema file which has been downloaded and message type is the name of the document type in the message.  
  
-   Keep the name of the policy files the same as the message schema itself. For example, swift.if.ia.setr.004.001.02.xsd will have following policies swift.if.ia.setr.004.001.02 _Master_Policy.xml and swift.if.ia.setr.004.001.02 _Validation_Policy.xml.  
  
-   **Special characters**: If the message name has any special characters in it, then creating a policy file requires a slightly different convention. If the message name is, for example, swift.if.ia$setr.004.001.02, then you must change the name of the policy file to the message name with the special characters being replaced by “.” For example, if the name of the message schema file is swift.if.ia$setr.004.001.02.xsd, then the resulting master policy would be swift.if.ia.setr.004.001.02_Master_Policy.xml.  
  
     The master policy file also needs to be changed to reflect the new name in the following tags:  
  
    -   \<ruleset name="swift.if.ia.setr.004.001.02_Master_Policy"\>  
  
    -   <rule name="swift.if.ia.setr.004.001.02_Policy_List"
