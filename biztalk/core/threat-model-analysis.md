---
title: "Threat Model Analysis | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TMA, about TMA"
  - "TMA"
  - "TMA, procedure steps"
ms.assetid: dfbf46aa-0a35-4925-8718-df8591efc279
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Threat Model Analysis
A threat model analysis (TMA) is an analysis that helps determine the security risks posed to a product, application, network, or environment, and how attacks can show up. The goal is to determine which threats require mitigation and how to mitigate them.  
  
 This section provides high-level information about the TMA process. For more information, see Chapter 4 of *Writing Secure Code, Second edition*, by Michael Howard and David LeBlanc.  
  
 Some of the benefits of a TMA are:  
  
- Provides a better understanding of your application  
  
- Helps you find bugs  
  
- Can help new team members understand the application in detail  
  
- Contains important information for other teams that build on your application  
  
- Useful for testers  
  
  The high-level steps to perform a TMA are:  
  
- Step 1. Collect Background Information  
  
- Step 2. Create and Analyze the Threat Model  
  
- Step 3. Review Threats  
  
- Step 4. Identify Mitigation Techniques and Technologies  
  
- Step 5. Document Security Model and Deployment Considerations  
  
- Step 6. Implement and Test Mitigations  
  
- Step 7. Keep the Threat Model in Sync with Design  
  
## Step 1. Collect Background Information  
 To prepare for a successful TMA, you have to collect some background information. It is useful to analyze your target environment (an application, program, or the whole infrastructure) as follows:  
  
-   Identify use-case scenarios. For each use-case scenario for your target environment, identify how you expect your company to use the target environment, and any limitations or restrictions on the target environment. This information helps define the scope of the threat model discussion, and provides pointers to assets (anything of value to your company, such as data and computers) and entry points.  
  
-   Create a data flow diagram (DFD) for each scenario. Make sure that you go deep enough to understand your threats.  
  
-   Determine the boundaries and scope of the target environment.  
  
-   Understand the boundaries between trusted and untrusted components.  
  
-   Understand the configuration and administration model for each component.  
  
-   Create a list of external dependencies.  
  
-   Create a list of assumptions about other components on which each component depends. This helps validate cross-component assumptions, action items, and follow-up items with other teams.  
  
## Step 2. Create and Analyze the Threat Model  
 After you collect the background information, you should have a threat model meeting or meetings. Make sure that at least one member of each development discipline (for example, program managers, developers, and testers) is at the meeting. Make sure that you remind the attendees that the goal of the meeting is to find threats, not to fix them. During the threat model meeting, do the following:  
  
-   Examine the DFD for each use case. For each use case identify:  
  
    -   Entry points  
  
    -   Trust boundaries  
  
    -   Flow of data from entry point to final resting location (and back)  
  
-   Note the assets involved.  
  
-   Discuss each DFD, and look for threats in the following categories for all entries in the DFD: **S**poofing identify, **T**ampering with data, **R**epudiation, **I**nformation disclosure, **D**enial of service, and **E**levation of privileges.  
  
-   Create a list of the identified threats. We recommend that this list include the following: title, brief description (including threat trees), asset (asset), impact(s), risk, mitigation techniques, mitigation status, and a bug number.  
  
    > [!NOTE]
    >  You can add risk, mitigation techniques, and mitigation status as you review the threats. Do not spend too much time in these areas during the threat model meeting.  
  
## Step 3. Review Threats  
 After you have identified the threats to your environment, you must rank the risk of each threat and determine how you want to respond to each threat. You can do this with additional team meetings or through e-mail. You can use the following effect categories to calculate risk exposure: **D**amage potential, **R**eproducibility, **E**xploitability, **A**ffected users, and **D**iscoverability.  
  
 After you have a list of the threats to your target environment prioritized by risk, you must determine how you will respond to each threat. Your response can be to do nothing (rarely a good choice), warn users about the potential problem, remove the problem, or fix the problem.  
  
## Step 4. Identify Mitigation Techniques and Technologies  
 After you identify which threats you will fix, you must determine the available mitigation techniques for each threat, and the most appropriate technology to reduce the effect of each threat.  
  
 For example, depending on the details of your target environment, you can reduce the effect of data-tamper threats by using authorization techniques. You then have to determine the appropriate authorization technology to use (for example, discretionary access control lists (DACLs), permissions, or IP restrictions).  
  
> [!IMPORTANT]
>  When you evaluate mitigation techniques and technologies to use, you must consider what makes business sense for your company, and any policies your company has that might affect the mitigation technique to choose.  
  
 After you complete the TMA, do the following:  
  
-   Document the security model and deployment considerations  
  
-   Implement and test mitigations  
  
-   Keep the threat model synchronized with design  
  
## Step 5. Document Security Model and Deployment Considerations  
 It is valuable to document what you discover during the TMA and how you decide to reduce the effect of the threats to your target environment. This documentation can be useful to quality assurance (QA), test, support, and operations personnel. Include information about other applications that interact or interface with your target environment, and the firewall and topology recommendations and requirements.  
  
## Step 6. Implement and Test Mitigations  
 When your team is ready to fix threats identified during the TMA, make sure you use development and deployment checklists to follow secure code and deployment standards that will help minimize the introduction of new threats.  
  
 After you implement a mitigation, make sure you test it to make sure it provides the level of protection that you want for the threat.  
  
## Step 7. Keep the Threat Model in Sync with Design  
 As you add new applications, servers, and other elements to your environment, make sure that you revisit the findings of the threat model analysis and do TMAs for any new functionality.  
  
## See Also  
[Security Case Studies for Small to Medium-Sized Companies](../core/security-case-studies-for-small-to-medium-sized-companies.md)   
 [Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md)