---
title: "Invoking a Policy from Another Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5bf658a-02a1-426a-abe5-8c9de673cf0d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoking a Policy from Another Policy
You can invoke a policy (child) from another policy (parent) by using one of the following methods:  
  
- Calling the **Policy.Execute** method directly from the parent policy  
  
- Calling a method of a helper .NET component that wraps the **Policy.Execute** method from the parent policy  
  
  The advantage of using the second method is that you can add pre-processing and post-processing code to the **Policy.Execute** method. For example, you can create any facts required from the child policy in this wrapper method. The following sections provide an example for each method.  
  
## Invoking the Policy.Execute Method Directly from the Parent Policy  
 This section presents the high-level steps to invoke the child policy from the parent policy by using the **Policy.Execute** method directly.  
  
### Adding the Policy.Execute Action to the Parent Policy  
 The following procedure has steps to add the **Policy.Execute** method as an action to the parent policy that passes an XML document as a fact to the child policy.  
  
##### To add the Policy.Execute method as an action to a policy  
  
1.  In the Facts Explorer window, click the **.NET Classes** tab.  
  
2.  Right-click **.NET Assemblies**, and then click **Browse**.  
  
3.  Select **Microsoft.RuleEngine** from the **.NET Assemblies** list, and then click **OK**.  
  
4.  Expand **Policy**.  
  
5.  Drag **Execute(Object facts)** or **Execute(Object facts, IRuleSetTrackingInterceptor trackingInterceptor)** to the THEN pane.  
  
6.  Click the **XML Schemas** node.  
  
    > [!NOTE]
    >  In this sample scenario, an XML document that is submitted as a fact to the parent policy is passed as a fact to the child policy. Instead, you can invoke a .NET method that creates the facts for the child policy.  
  
7.  Right-click **Schemas**, and then click **Browse**.  
  
8.  Select the schema for the XML document you want to pass as a fact, and then click **Open**.  
  
9. Drag *\<Schema name\>*.xsd to the first argument of the **Policy.Execute** method to pass the XML document that is passed to the parent policy as a fact to the child policy.  
  
10. If you use the **Execute** method that does not take the **IRuleSetTrackingInterceptor** as the second argument, skip the following steps.  
  
11. Click the **.NET Classes** tab.  
  
12. Drag **DebugTrackingInterceptor** in **Microsoft.RuleEngine** to the second argument of the **Policy.Execute** method.  
  
    > [!NOTE]
    >  If you perform this action, the client must pass an instance of the **DebugTrackingInterceptor** class as a fact to the parent policy, which in turn passes the instance as a fact to the child policy. Instead you could drag the constructor of the **DebugTrackingInterceptor** class so that the instance is automatically created for you.  
  
### Modifying the Client Application that Invokes the Parent Policy  
 The client that invokes the parent policy creates an instance of the **Policy** class with the child policy name as a parameter and passes it as a fact to the parent policy along with other facts. The following sample code illustrates this action:  
  
```  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
Policy policy = new Policy("ParentPolicy");  
object[] facts = new object[3];  
facts[0] = txd;  
facts[1] = new Policy("ChildPolicy");  
facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
 If the client is a BizTalk orchestration, you may need to place the code to create facts in an **Expression** shape, and then pass the facts as parameters to the **Call Rules** shape.  
  
## Invoking a .NET Wrapper Method from the Parent Policy  
 This section presents the high-level steps to invoke a .NET method that wraps the call to the **Policy.Execute** method from the parent policy.  
  
### Creating the Utility .NET Class  
  
##### To create the utility class  
  
1.  Create a .NET class library project, and then add a class to the project.  
  
2.  Add a static method that calls the **Policy.Execute** method to invoke the policy whose name is passed as a parameter, as shown in the following sample code:  
  
    ```  
    public static void Execute(string policyName, TypedXmlDocument txd)  
    {  
        DebugTrackingInterceptor dti = new   DebugTrackingInterceptor("PolicyTracking.txt");  
        Policy policy = new Policy("ParentPolicy");  
        object[] facts = new object[3];  
        facts[0] = txd;  
        facts[1] = new Policy("ChildPolicy");  
        facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
        policy.Execute(facts, dti);  
        policy.Dispose();  
    }   
    ```  
  
3.  Make sure that the **StaticSupport** registry key is set to 1 or 2. For more information about the registry key, see [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).  
  
    > [!NOTE]
    >  You can use an instance method instead of a static method. Remember that, if you use an instance method, the client must pass an instance of the helper .NET class as a fact to the parent policy.  
  
### Modifying the Client Application  
 The client invokes the parent policy, and the parent policy invokes the helper method that invokes the child policy. The sample code for the client is as follows:  
  
```  
facts[0] = txd;  
facts[1] = new PolicyExecutor(txd);  
//call the first or parent policy  
Policy policy = new Policy(policyName);  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
> [!NOTE]
>  If the method is an instance method, the client must create an instance of the helper .NET class, and pass it as a fact to the parent policy.  
  
> [!NOTE]
>  If the client is a BizTalk orchestration, you may need to place the code to create facts in an **Expression** shape, and then pass the facts as parameters to the **Call Rules** shape.