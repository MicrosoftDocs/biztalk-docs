---
title: "Considerations when using the Siebel adapter with SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea7da079-3250-4ecc-bf01-6b5495c7f380
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations when using the Siebel adapter with SharePoint
This topic contains information about the issues you might encounter while using the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] with Microsoft Office SharePoint Server, along with resolutions. The issues are divided into two categories:  
  
-   General issues  
  
-   Issues involving custom Web Parts  
  
## General Issues  
 This section contains issues that either have no resolution or requires you to modify the application definition file for the resolution.  
  
### Issue 1: The simple type data returned by the WCF service is not displayed  
 **Explanation**: Microsoft Office SharePoint Server expects the data returned by the WCF service to be of DataSet or Collection type only. If the data returned by the WCF service is of simple type, Microsoft Office SharePoint Server does not display the data.  
  
 **Resolution**: No resolution. It is a known limitation with Microsoft Office SharePoint Server.  
  
### Issue 2: An error message is displayed if the data returned by the WCF service is NULL  
 **Explanation**: If the data returned by the WCF service is a NULL value, Microsoft Office SharePoint Server displays an error message. For example, suppose you are using the Business Data List Web Part for the **Finder** method instance, and are searching for customers in the Siebel system based on a search expression. The search expression that you specified fetches a NULL value. In this case, Microsoft Office SharePoint Server will display an error message.  
  
 **Resolution**: No resolution. It is a known limitation with Microsoft Office SharePoint Server.  
  
### Issue 3: An array of simple type returned by the WCF service is not displayed  
 **Explanation**: If the data returned by the WCF service is an array of simple type, Microsoft Office SharePoint Server does not display the data. Moreover, when you execute a method instance in Business Data Catalog Definition Editor that returns an array of simple type, the following error message is displayed: “Backend system adapter returned a structure incompatible with the corresponding metadata (MethodInstance, Parameter or TypeDescriptor).”  
  
 **Resolution**: No resolution. It is a known limitation with Microsoft Office SharePoint Server and Business Data Catalog Definition Editor.  
  
### Issue 4: Cannot import an application definition file that contains a complex type parameter having more than 300 fields  
 **Explanation**: Microsoft Office SharePoint Server cannot import an application definition file that has more than 300 fields in the complex type parameter returned by the WCF service, and displays an error message if you try to do so. This is due to the limitation of Microsoft Office SharePoint Server of not being able to display more than 300 fields of a complex type parameter.  
  
 **Resolution**: Use the Business Data Catalog Definition Editor to limit the number of fields of the complex type parameter to less than or equal to 300. Depending on your requirement, you can delete the fields of the complex type parameter in the Business Data Catalog Definition Editor that you do not require to be displayed in Microsoft Office SharePoint Server.  Alternatively, you can also export the application definition file from Business Data Catalog Definition Editor with all the fields, and then modify the application definition file in a notepad or any XML authoring application to delete the fields that are not required in order to limit the number of fields to 300.  
  
##  <a name="Custom_Web_Part"></a> Issues Involving Custom Web Parts  
 This section contains issues that require the use of custom Web Parts for resolution. For detailed information about using a custom Web Part to resolve issues that might come up while working with [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and Microsoft Office SharePoint Server, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).  
  
### Issue 1: Index of an enumerator is displayed instead of the value for the enum data type  
 **Explanation**: If a Business Data List or Business Data Item Web Part in Microsoft Office SharePoint Server contains data of enum type (a distinct type consisting of a set of named constants called the enumerators), the index of the enumerator is displayed instead of its value in Microsoft Office SharePoint Server. This is because the Business Data List and Business Data Item Web Parts incorrectly print the values of the enum type data to the SharePoint portal.  
  
 **Resolution**: Use a custom Web Part to print the value of the enumerator instead of the index. For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md). For example, you can use the following code sample in your Web part to print the correct values of enum type data on Microsoft Office SharePoint Server.  
  
```  
namespace CustomWebpart  
{  
    public class CustomWebPart : WebPart  
    {  
        private string displayText = "Hello World!";  
  
        [WebBrowsable(true), Personalizable(true)]  
        public string DisplayText  
        {  
            get { return displayText; }  
            set { displayText = value; }  
        }  
        protected override void Render(System.Web.UI.HtmlTextWriter writer)  
        {  
            string SearchExpr = "[Address Name] LIKE \"*\"";  
            object ElementType = null;  
  
/***Step 1: Get the required entity and method.***/  
  
            LobSystem newSystem = ApplicationRegistry.GetLobSystems()["WebServiceLobSystem"]; // Name specified in application definition file  
            LobSystemInstance newSystemInstance = newSystem.GetLobSystemInstances()["Siebel_Instance"]; // Name specified in application definition file  
            Entity CategoryEntity = newSystem.GetEntities()["Siebel_Method_Name"]; // Name specified in application definition file  
            Method newMethod = CategoryEntity.GetMethods()["Query"]; // Name specified in application definition file  
            MethodInstance methodInstance = newMethod.GetMethodInstances()["MethodInstance0"]; // Name specified in application definition file  
  
/***Step 2: Get the list of input parameters.***/  
            Object[] args = methodInstance.GetMethod().CreateDefaultParameterInstances(methodInstance); // Get default value of the input parameter  
            Object[] ArgsInput = new Object[args.Length];  
  
/***Step 3: Assign them required values.***/  
  
           //Assigning values to a complex type parameter. Index of this parameter is 3rd in args array.   
           /*** Complex Type Parameter is defined as follows:  
           <Parameter Direction="In" Name="BusinessAddressQueryInputRecord">  
           <TypeDescriptor TypeName="BDC.BusinessAddressQueryInputRecord,WebServiceLobSystem" Name="BusinessAddressQueryInputRecord">  
              <TypeDescriptors>  
                 <TypeDescriptor TypeName="System.String, ...." Name="SearchExpr"></TypeDescriptor>  
                 <TypeDescriptor TypeName="System.String, ...." Name="SortSpec"></TypeDescriptor>  
                 <TypeDescriptor TypeName="System.String[], ...." IsCollection="true" Name="QueryFields"></TypeDescriptor>  
              </TypeDescriptors>  
           </TypeDescriptor>  
           </Parameter>  
            * We are assigning value to Parameter SearchExpr. ***/  
  
            Assembly asm = Assembly.GetAssembly(args[2].GetType());  
            Type t = asm.GetType(args[2].GetType().ToString()); // Get type of the parameter  
  
            FieldInfo[] FI = t.GetFields();  
            ElementType = Activator.CreateInstance(t);  
            ElementType.GetType().GetFields()[0].SetValue(ElementType, (Object)SearchExpr);  
  
            ArgsInput[2] = ElementType; // ArgsInput is fed as input while executing Method Instance.  
  
/***Step 4: Execute the particular method instance using the required value.***/              
  
            IEntityInstanceEnumerator prodEntityInstanceEnumerator = (IEntityInstanceEnumerator)CategoryEntity.Execute(methodInstance, newSystemInstance, ref ArgsInput); //Method instance of type Finder is being used here.  
  
/***Step 5: Display the output on the custom Web Part in Microsoft Office SharePoint Server.***/  
  
            writer.Write("<table>");  
            while (prodEntityInstanceEnumerator.MoveNext())  
            {  
                IEntityInstance IE = prodEntityInstanceEnumerator.Current;  
  
                writer.Write("<tr>");  
                foreach (Field f in CategoryEntity.GetFinderView().Fields)  
                {  
  
                    writer.Write("<td>");  
                    writer.Write(IE[f]);  
                    writer.Write("</td>");  
                }  
                writer.Write("</tr>");  
            }  
            writer.Write("</table>");  
  
        }  
    }  
}  
  
```  
  
### Issue 2: Cannot specify values to array elements  
 **Explanation**: If the input parameter of the WCF service is an array, you cannot specify values to the array elements using filters that are defined in the application definition file created using the Business Data Catalog Definition Editor. It implies that you cannot use the Business Data List or Business Data Item Web Part in Microsoft Office SharePoint Server to specify values for these input parameters (elements of array) to the WCF service. This is because of the way arrays are defined in the application definition file.  
  
 **Resolution**: Use a custom Web Part to assign values to array elements. For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md). For example, you can use the following code sample in step 3 in “Issue 1: Index of an enumerator is displayed instead of the value for the enum data type” to assign values to array elements.  
  
```  
/***Assign required values to parameters of type array.***/   
/***Assumption is that the ith parameter of Method is of type Array and all the simple type elements in the array are of type string***/  
  
            Type t = asm.GetType(args[i].GetType().ToString()); // Get type of the parameter  
            Type TElement = t.GetElementType(); // Getting type of element of array  
            int index = 5; //Size of Array  
            Array ElementArray = Array.CreateInstance(TElement, index); //Creating an array of length: index  
  
            for (int ind = 0; ind < index; ind++)  
            {  
                //Creating an instance of an element of array  
                object ElementType = Activator.CreateInstance(TElement);  
                FieldInfo[] FI = ElementType.GetType().GetFields();  
                for (int f = 0; f \< FI.Length; f++)  
                {  
                    ElementType.GetType().GetFields()[f].SetValue(ElementType, (Object)"ElementValue");  
                }  
                ElementArray.SetValue(ElementType, ind);  
            }  
  
            ArgsInput[i] = (object)ElementArray; // As shown in sample, ArgsInput is fed as input while executing Method Instance  
  
```  
  
### Issue 3: Limitation with specifying NULL values to complex type parameters  
 **Explanation**: If you do not specify any value for a complex type parameter from a Web Part in Microsoft Office SharePoint Server, NULL should be passed on as the value for the complex type parameter to the WCF service. However, a non-NULL value is passed for the complex type parameter, and NULL is passed for its children elements (of simple type). This causes a mismatch between the expected message schema and the message schema that is passed on to the WCF service. As a result, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] might display an error message.  
  
> [!NOTE]
>  To find out the default value of a complex type parameter when no value is passed from a Web Part in Microsoft Office SharePoint Server, use step 2 in the code sample mentioned in “Issue 1: Index of an enumerator is displayed instead of the value for the enum data type.”  
  
 **Resolution**: Use a custom Web Part to assign a NULL value to the complex type parameter when no value is specified from a Web Part in Microsoft Office SharePoint Server. For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).  
  
###  <a name="Issue1"></a> Issue 4: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values  
 **Explanation**: If you want to display a single record in Microsoft Office SharePoint Server based on multiple values (input parameters) from a Siebel system, you cannot use any of the three Web Parts (Business Data List, Business Data Item, and Business Data Related List) specified in [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) in [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
 **Resolution**: You must use a custom Web Part to do this. For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md). For example, in step 3 in “Issue 1: Index of an enumerator is displayed instead of the value for the enum data type” you can modify the code to provide values for more than one parameter instead of providing input to a single business component parameter.  
  
## See Also  
 [Use the Siebel Adapter with SharePoint](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)