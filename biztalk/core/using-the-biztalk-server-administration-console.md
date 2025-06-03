---
description: "Learn more about: Using the BizTalk Server Administration Console"
title: "Using the BizTalk Server Administration Console"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Using the BizTalk Server Administration Console
The BizTalk Server Administration Console is a Microsoft Management Console (MMC) that you can use to manage and monitor BizTalk Server, and that you can use to deploy and manage your BizTalk Server applications.  
  
 The left side of the BizTalk Server Administration Console, the console tree, consists of folders and subfolders that represent different types of artifacts that you can manage.  
  
 When you select a node in the console tree, the details pane on the right side of the Administration Console displays information about the items.  
  
 Selecting the BizTalk Server Administration node in the console tree displays the start page, which contains actions you can perform, such as connecting to an existing BizTalk Server group. In addition, the start page includes links to the BizTalk Server documentation and online community Web sites.  
  
 For information about using the keyboard shortcuts for the Administration console, see [Administration Console Keyboard Shortcuts](../core/administration-console-keyboard-shortcuts.md).  
  
## BizTalk Server artifacts  
 You can manage the following artifacts using the BizTalk Server Administration console:  
  
-   **BizTalk Group**. The BizTalk Group node in the console tree contains additional nodes that represent the artifacts (applications, parties, and platform settings) for that BizTalk group. BizTalk groups are units of organization that usually represent enterprises, departments, hubs, or other business units that require a contained BizTalk Server implementation. A BizTalk group has a one-to-one relationship with a BizTalk Management database. For more information, see [Managing Groups](../core/managing-groups.md).  
  
     When you select the BizTalk Group node in the BizTalk Server Administration console, the BizTalk Server Group Hub page is displayed in the details pane. The BizTalk Server Group Hub page provides an overall view of the health of your BizTalk Server system. For more information, see [Using the Group Hub Page](../core/using-the-group-hub-page.md).  
  
-   **Orchestration**. An orchestration is designed by using Orchestration Designer and is deployed to the BizTalk group under which it appears in the Administration console. For more information, see [Managing Orchestrations](../core/managing-orchestrations.md).  
  
-   **Role Links**. A role link defines the relationship between roles by defined by the message and port types used in the interactions in both directions. For more information, see [Managing Role Links](../core/managing-role-links.md).  
  
-   **Send port groups**. A send port group is a named collection of send ports that you can use to send the same message to multiple destinations in a single configuration. For more information, see [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md).  
  
-   **Send ports**. A send port is a BizTalk object that sends messages. For more information, see [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md).  
  
-   **Receive ports**. A receive port is a logical grouping of similar receive locations. For more information, see [Managing Receive Ports](../core/managing-receive-ports.md).  
  
-   **Receive locations**. A receive location is defined as a specific address at which inbound documents arrive combined with a BizTalk Server pipeline that processes the messages received at that address. For more information, see [Managing Receive Locations](../core/managing-receive-locations.md).  
  
-   **Policies**. A policy is a versioned collection of business rules. For more information, see [Managing Policies](../core/managing-policies.md).  
  
-   **Schemas**. A schema is the structure for a message. A schema can contain multiple subschemas. For more information, see [Managing Schemas](../core/managing-schemas.md).  
  
-   **Maps**. A map is an XML file that defines the correspondence between the records and fields in one specification and the records and fields in another specification. A map contains an Extensible Stylesheet Language (XSL) stylesheet that is used by BizTalk Server to perform the transformation described in the map. For more information, see [Managing Maps](../core/managing-maps.md).  
  
-   **Pipelines**. A pipeline is a software infrastructure that defines and links one or more processing stages, running them in prescribed order to complete a specific task. Pipelines divide processing into stages, abstractions that describe a category of work. They also determine the sequence in which each category of work is performed. For more information, see [Managing Pipelines](../core/managing-pipelines.md).  
  
-   **Resources**. A resource is a script, deployed assembly, or other file associated with an application. For more information, see [Managing Resources](../core/managing-resources.md).  
  
-   **Parties**. A party is an entity outside of BizTalk Server that interacts with an orchestration. All of the partners your organization deals with are considered parties, and your organization may have several thousand partners. For more information, see [Managing Parties](../core/managing-parties.md).  
  
-   **Platform Settings**. The Platform Settings node contains subnodes for hosts, host instances, MessageBox databases, and adapters. For more information, see [Managing Platform Settings](../core/managing-platform-settings.md).  
  
    -   **Hosts**. The Hosts node contains all of the in-process and isolated hosts in the BizTalk Server environment. A BizTalk Host is a logical container for items such as adapter handlers, receive locations (including pipelines), and orchestrations. For more information, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).  
  
    -   **Host Instances**. The Host Instances node contains all of the host instances in the current BizTalk Server group. Host instances are processes of the BizTalk Server runtime that execute your application components.  
  
         Using the Host Instances node, you can create new host instances and refresh host instance information. For more information, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).  
  
    -   **Servers**. The Servers node lists all servers that are joined to the BizTalk Server group. These are the computers where BizTalk Server is installed and configured, and where host instances are running. Host instances are created by associating a server with a particular host. For more information, see [Managing Servers](../core/managing-servers.md).  
  
    -   **Message Boxes**. The Message Boxes node contains all MessageBox databases used by the current BizTalk Server group. Using the Message Boxes node, you can create new MessageBox databases and refresh MessageBox database information. The MessageBox database is the basis for work item load balancing across servers that do cooperative processing. A work item can pass through a MessageBox database more than once during its processing life. The name of the MessageBox database cannot exceed 100 characters. For more information, see [Managing MessageBox Databases](../core/managing-messagebox-databases.md).  
  
    -   **Adapters**. The Adapters node contains subnodes for all of the send and receive adapters configured for the BizTalk Server group and the associated adapter handlers. Adapters are the messaging middleware used to send and receive messages between endpoints. For more information, see [Using Adapters](../core/using-adapters.md).  

## Tips and tricks

#### Update settings for multiple hosts and host instances simultaneously
Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can select multiple hosts and host instances, and update some of the settings in **Settings Dashboard**.

**Steps**:

1. In BizTalk Administration, expand **BizTalk group**, and expand **Platform Settings**.
2. Select **Hosts**. In the hosts list, use the CTRL or SHIFT keys to select multiple hosts simultaneously.
3. Right-click the hosts you selected, and select **Settings**. Or, select **Settings** in the Actions pane.
4. In Settings Dashboard, the general and throttling settings can be set, and applied to the multiple hosts you selected. 
5. Next, select **Host Instances**. In the host instances list, use the CTRL or SHIFT keys to select multiple host instances simultaneously. In **Settings**, the .NET CLR and orchestration throttling settings can be applied to the multiple host instances you selected. 

> [!NOTE]
> You can select multiple host and host instances that are the same Host Type. If the host type is different, the **Settings** option is grayed out. For example, if you multi-select an in-process host and an isolated host, then **Settings** is grayed out.

#### Filter artifacts in your application
Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can search for artifacts in your application. For example, you can search for a specific schema or an orchestration in an application. 

**Steps**:

1. In BizTalk Administration, expand **BizTalk group**, expand **Applications**, and expand one of your applications that has artifacts. For example, expand the **BizTalk EDI Application**. 
2. Select **Schemas**. In the schemas list, use the **Search** box to search for a schema, or filter the schemas displayed. For example, type in **x12** in the Search box, and hit Enter. All the schemas with X12 in the name are displayed. Clear your search. 

    Next, type in **batch** in the Search box, and hit Enter. The batch schemas are displayed. 
    
You can use this Search to find or filter any artifacts with your application, including send ports, resources, maps, and so on. 

#### Save multiple suspended messages simultaneously to a file within Group Hub 
Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can save multiple suspended messages simultaneously to a file.

**Steps**:

1. In BizTalk Administration, select **BizTalk group**
2. Select **New Query**, and in the query, **Seach for**

    Filed Name: Search For  
    Operator: Equals  
    Value: Messages
3. Select **Run Query**. In the query results, use the CTRL or SHIFT keys to select multiple suspended instances simultaneously. Right-click, and select **Safe to File**. 
4. Choose your folder to save the files. When saved, an XML file is created for every message.

## Next steps
  
-   [Open the BizTalk Server Administration Console](../core/how-to-open-the-biztalk-server-administration-console.md)  
  
-   [Using the Group Hub Page](../core/using-the-group-hub-page.md)
