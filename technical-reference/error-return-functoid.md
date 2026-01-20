---
description: "Learn more about: Error Return Functoid"
title: Error Return Functoid
TOCTitle: Error Return Functoid
ms:assetid: 2bcd968b-fb40-419b-be16-09293f1f9f96
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559365(v=BTS.80)
ms:contentKeyID: 51526975
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Error Return Functoid

 

Use the **Error Return** functoid ( ![Icon that represents the Error Return functoid.](images/Aa559365.7a3b89f4-0550-47f4-8cfa-6ff1b295005e(BTS.80).jpeg)) to capture error information, such as database connection failures, that occur during run time.

## Input

**Parameter 1:** A link from a **Database Lookup** functoid.

## Output

**Output 1:** The error string, if any, returned by Open Database Connectivity (ODBC) when using the functoid.

## Remarks

Use this functoid in conjunction with the [Database Lookup](database-lookup-functoid.md) and [Value Extractor](value-extractor-functoid.md) functoids to capture and map error information. Some of the scenarios this might be useful include:

  - When your map has a **Database Lookup** or **Value Extractor** functoid that is not behaving as expected. To see the error message, temporarily map the functoid to a field in the output schema.

  - If your application expects different message content when database operations fail. You can use the **Error Return** functoid to detect an error and map the error message to an alternate structure so that downstream applications can react in a controlled manner.

To avoid errors that are only detected at run time, make sure that the parameter 1 to the **Error Return** functoid is the output of a **Database Lookup** functoid and not the output of any other functoid in the **Database** category.

## Sample

In the following mapping, a **Database Lookup** functoid is used to retrieve the last name of a person based on their first name. If no error is encountered and a last name exists, the **Value Extractor** functoid copies it to the destination schema. Any error thrown by the **Database Lookup** functoid during the query will be caught by the **Error Return** functoid and copied to the error message field in the destination schema.

![Map illustrating error return functoid](images/Aa559365.f2b110a5-c1e8-4430-b1bb-370e3be45967(BTS.80).jpeg "Map illustrating error return functoid")  
Error Return Sample Map

To test, configure the Database Lookup functoid with an invalid table as shown below.

![DB Lookup functoid with invalid table name](images/Aa559365.87160772-ea93-4411-8fe4-529a9db36240(BTS.80).jpeg "DB Lookup functoid with invalid table name")  
Invalid Table Name for Database Lookup Functoid

The value for Input\[1\] is “Provider=SQLNCLI10;Server=localhost;Database=Contoso; Trusted\_Connection=yes;

If the lookup table name is incorrect, the output message would be similar to the one below. If “authors” is an invalid table name, an error message is encountered which is stored in the “ErrorMessage” node.

```C#
<ns0:SampleSource xmlns:ns0="http://Sample">  
    <Person>  
        <FirstName>FirstName_0</FirstName>  
        <LastName />  
        <ErrorMessage>Invalid object name 'authors'.</ErrorMessage>  
    </Person>  
</ns0:SampleSource>  
```

This is one example of an error message. There are many different types of possible error messages including connection failures, stored procedure problems, environment issues, SQL exceptions, etc. Downstream processes could monitor the ErrorMessage field and process or route the message appropriately.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

