---
description: "Learn more about: Business Rules Framework Security"
title: "Business Rules Framework Security"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Business Rules Framework Security
The Business Rule Engine operates in the security context of the hosting application. The identity of the rule engine instance during execution is that of the thread context that invokes the **Policy.Execute** method.  
  
## Default security configuration  
 When you install Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], two Microsoft Windows groups are created by default, one for administrators and one for users: "BizTalk Server Administrators" and "BizTalk Application Users." These two Windows groups are members of BTS_ADMIN_USERS and BTS_HOST_USERS SQL Roles which are members of RE_ADMIN_USERS and RE_HOST_USERS SQL Roles respectively.  
  
 The default SQL roles are created whenever a rule store is created: BTS_ADMIN_USERS, BTS_HOST_USERS, RE_ADMIN_USERS and RE_HOST_USERS.  
  
|Default Windows groups|SQL roles|  
|----------------------------|---------------|  
|BizTalk Server Administrators|RE_ADMIN_USERS|  
|BizTalk Application Users|RE_HOST_USERS|  
  
 Only users in the RE_ADMIN_USERS role can execute the stored procedures that update the deployment and entity access protection configuration tables. This means that the deployment, undeployment, and protection configuration are all done only by rule engine administrators. Users in the RE_HOST_USERS role can execute the other stored procedures in the SQL rule store.  
  
 Regardless of the order of installation of the rule engine, the rule engine configuration process grants the Rule Engine Update Service account membership to the RE_HOST_USERS SQL role, if it does not already have database access. However, if the rule engine is installed after the initial BizTalk installation the BizTalk, host-specific users group is not added to the BTS_HOST_USERS SQL role in the Rule Engine database because host creation has already been completed. You need to perform this step manually.  
  
## Artifact level security  
 In addition to the default security configuration, the Business Rule Engine can also provide security at the artifact—policy and vocabulary level.  
  
 Each policy or vocabulary version has one or more authorization groups associated with it. An Authorization group is a named list of Microsoft Windows users, SQL users, SQL roles, and Windows groups, with a particular access level on each type.  
  
 When a new policy or vocabulary is created in the rule store, only the user who created it and the rule engine administrator have both read/execute and modify/delete access by default. The rule engine administrator can configure which users (processes operate under user credentials) have the access level, or rights, to perform different operations—read/execute, modify/delete, full permission, or no permission.  
  
 Artifact specific security is not enabled by default. Setting artifact level security is not currently available through the user interface. However, it can be set programmatically with the Business Rule Engine administrator credential. The following code fragment shows how to create a new authorization and associate the group to a rule set.  
  
```  
RuleSet rs;  
string RSName;     
  
// Create new user  
AuthorizationGroupEntry newuser = new AuthorizationGroupEntry(UserName, UID);  
AuthorizationGroupEntryCollection AGEC = new AuthorizationGroupEntryCollection();  
AGEC.Add(newuser);  
  
// Define new authorization group collection  
AuthorizationGroupCollection AGC = new AuthorizationGroupCollection();  
  
// Create new authorization group  
AuthorizationGroup AG = new AuthorizationGroup(GroupName, AccessPermit, AGEC);  
  
//add the authorization group to the authorization group collection  
AGC.Add(AG);  
  
//saving the authorization group collection to the rule store  
m_sqlRS.SaveAuthorizationGroups(AGC);  
  
rs = m_sqlRS.GetRuleSet(rsInfo[0]);                 
RSName = rs.Name;  
  
// Associate authorization group to the ruleset  
m_sqlRS.SetRuleSetAuthorizations(RSName, AGC);  
  
// Get ruleset by name from SQL rule store  
RuleSetInfoCollection rsInfo = m_sqlRS.GetRuleSets("myRuleSet", RuleStore.Filter.All);  
```  
  
> [!NOTE]
>  The use of artifact level l security can diminish performance, because the policy will have to do a database lookup on each execution to evaluate the application's access level before returning an instance of the rule engine.  
  
## See Also  
 [Important Security Notes for the Business Rule Engine](../core/important-security-notes-for-the-business-rule-engine.md)
