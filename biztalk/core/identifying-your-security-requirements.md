---
description: "Learn more about: Identifying Your Security Requirements"
title: "Identifying Your Security Requirements"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Identifying Your Security Requirements
The answers to the following questions help you plan the best way to deploy BizTalk Server in your environment.

|Question|Recommendation|
|--------------|--------------------|
|What is the recommended way to deploy BizTalk Server in a secure environment?|The answer to this question really depends on the specific needs of your environments, the assets of your company, how vulnerable to potential threats these assets are, and how you want to protect them. It is important to do a Threat Model Analysis to understand what the main assets you want to protect are.<br /><br /> [Large Distributed Architecture](../core/large-distributed-architecture.md) provides recommendations for securing your BizTalk Server environment. After you do the Threat Modeling, use the information in this section to design your own secure deployment of BizTalk Server.|
|Are you planning to use Business Activity Monitoring (BAM)?|BAM requires that business users in the corporate network access BizTalk Server resources. If you use this feature, there are additional security recommendations to keep in mind when you design your BizTalk Server deployment. For more information, see [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md).|
|What is the best way to secure the BizTalk Server features you plan to use?|For general recommendations on how to help secure a BizTalk Server environment, see [Security Recommendations for a BizTalk Server Deployment](../core/security-recommendations-for-a-biztalk-server-deployment.md).<br /><br /> For recommendations on how to help secure the different BizTalk Server features, see the appropriate security topic for that feature.|
|What are the potential threats a BizTalk environment is exposed to?|For more information, see [Identifying Potential Threats](../core/identifying-potential-threats.md).|
|What are the potential threats for your implementation of BizTalk Server, and how can you mitigate them?|To identify the potential threats to your environment, and how to mitigate them, you should do a Threat Model Analysis. |
|How can you protect your environment from Denial of Service attacks?|Denial of Service attacks are one of the hardest threats to mitigate. While you cannot completely protect your environment from these attacks, there are some actions you can take to mitigate their impact in your environment. For more information, see [Mitigating Denial of Service Attacks](../core/mitigating-denial-of-service-attacks.md).|
|What ports should you open on the firewalls for the BizTalk services?|For more information, see [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md).|
|What accounts should you use for a distributed BizTalk Server deployment?|While the specific accounts you use in your environment depend on what services you use, it is recommended that you use different groups and accounts for different services. For more information, see [Windows Accounts for a Secure Distributed BizTalk Server Deployment](../core/windows-accounts-for-a-secure-distributed-biztalk-server-deployment.md).|

## See Also
 [Planning for Security](../core/planning-for-security.md)
 [Security Recommendations for a BizTalk Server Deployment](../core/security-recommendations-for-a-biztalk-server-deployment.md)
 [Identifying Potential Threats](../core/identifying-potential-threats.md)
 [Mitigating Denial of Service Attacks](../core/mitigating-denial-of-service-attacks.md)
