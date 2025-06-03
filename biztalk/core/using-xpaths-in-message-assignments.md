---
description: "Learn more about: Using XPaths in Message Assignments"
title: "Using XPaths in Message Assignments"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Using XPaths in Message Assignments
You can use the **xpath** function to assign an XPath value to a message part, or to assign a value to an XPath that refers to a message part. For more information on assigning to messages and message parts, see [Constructing Messages](../core/constructing-messages.md).  
  
> [!NOTE]
>  For more information on the xpath function, see third-party documentation on the XML Path Language (XPath).  
  
> [!NOTE]
>  The use of the **xpath** function is not limited to message assignment. You can also use it in any expression, for example:  
  
```  
If ((System.Double) xpath(_RequestMessage.part, "number(//book[last()]/price)") == 75.00 && (System.Boolean) xpath(msgBoolean, "string(//boolean)") == false)...  
```  
  
> [!NOTE]
>  If you want to assign a value to a string, use the XPath string() function. For example:  
  
```  
myString = xpath(msg, "string(/*/book[1]/title)");  
```  
  
> [!NOTE]
>  The engine is not schema-aware, so you can only read values from or write values to a node that exists in the containing message (the complete path must exist), or the engine will raise an exception. This is true even if you supply a default value.  
  
## Assigning to an XPath in a message part  
 Consider the following schema:  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="catalog">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="book">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="title" type="xs:string" />  
              <xs:element name="author">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element name="FirstName" type="xs:string" />  
                    <xs:element name="LastName" type="xs:string" />  
                  </xs:sequence>  
                </xs:complexType>  
              </xs:element>  
              <xs:element name="price" type="xs:string" />  
            </xs:sequence>  
            <xs:attribute name="country" type="xs:string" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 You can use the  function as follows to set values on a document instance of that schema type:  
  
```  
//assumes that a message named _ResponseMessage is already constructed  
_ResponseMessage.part = _RequestMessage.part;  
xpath(_ResponseMessage.part, "/*/book[1]/@country") = "USA";  
xpath(_ResponseMessage.part, "/*/book[1]/title") = "Legends";  
xpath(_ResponseMessage.part, "/*/book[1]/author/FirstName") = "A";  
xpath(_ResponseMessage.part, "/*/book[1]/author/LastName") = "B";  
xpath(_ResponseMessage.part, "/*/book[1]/price") = 50;  
```  
  
## Assigning to a message part from an XPath  
  
```  
//assumes that a message named objMessage is already constructed  
objMessage.BooleanPart = xpath("false()");  
objMessage.IntPart = xpath("100");  
objMessage.StringPart = xpath("'Hello'");  
objMessage.StringPart2 = xpath("'World'");  
```  
  
## Using XPath to assign from nodes and node sets  
 You can also use XPath to assign XML nodes and node sets to an XML element, a class, or a schema-based or class-based message.  
  
 Suppose you have an XML-serializable class called Book, and consider the following examples:  
  
```  
[Serializable]  
Class Book {...}  
```  
  
 Example One — select the fourth book element from the catalog, and assign it to an XML element variable:  
  
```  
myXmlElement = xpath(myMsg, "/catalog/book[3]");  
```  
  
 Example Two — select the fourth book element from the catalog, and convert it using XML deserialization into a Book class instance:  
  
```  
myBook = xpath(myMsg, "/catalog/book[3]");  
```  
  
 Example Three — select the fourth book element from the catalog, and convert it a message of type Book:  
  
```  
myBookMsg = xpath(myMsg, "/catalog/book[3]");  
```  
  
 Example Four — select all book elements in the catalog, where MyMethod takes an XmlNodeSet as a parameter:  
  
```  
MyMethod(xpath(myMsg, "/catalog/book"));  
```  
  
 Example Five — add a book element to the "BookOfTheMonth" container:  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BookOfTheMonth") = myBook;  
```  
  
 Example Six — add all books that are priced at twenty or less to a set of recommended books:  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BestPriceBooks") = xpath(MyMsg, "/catalog/book[@price <= 20]");  
```  
  
 Example Seven — call user code that returns an XML element:  
  
```  
xpath(MyMsg2, "/RecommendedBooks/AdvertisedByPartner") = GetPartnerAdvertisedBook();  
```  
  
 Before applying examples five and seven:  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth/>  
       <BestPriceBooks/>  
       <AdvertisedByPartner/>  
</RecommendedBooks>  
```  
  
 After applying examples five and seven:  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth>  
              <Book country="USA">  
                     <title>McSharry</title>  
                     <author>  
                            <FirstName>Nancy</FirstName>  
                            <LastName>Jensen</LastName>  
                     </author>  
              </Book>  
       </BookOfTheMonth>  
       <BestPriceBooks/>  
       <AdvertisedByPartner>  
              <Book country="USA">  
                     <title>The Rooster</title>  
                     <author>  
                            <FirstName>Mindy</FirstName>  
                            <LastName>Martin</LastName>  
                     </author>  
              </Book>  
       </AdvertisedByPartner>  
</RecommendedBooks>  
```
