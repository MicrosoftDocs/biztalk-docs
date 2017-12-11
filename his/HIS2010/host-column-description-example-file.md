---
title: "Host Column Description Example File | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a91eafb-a066-4bdd-ada1-ee00005264d2
caps.latest.revision: 3
---
# Host Column Description Example File
The following is an example for a host column description (HCD) file containing two sample database file descriptions—SAMPLE/ACCOUNTS and PUBS/AUTHORS. The first sample file (SAMPLE/ACCOUNTS) has four columns of data while the second example (PUBS/AUTHORS) has nine columns that must be described.  
  
```  
[files]  
SAMPLE/ACCOUNTS=1  
PUBS/AUTHORS=1  
  
[SAMPLE/ACCOUNTS]  
numcol=4  
col1=0;CUST_NO;CUST_NO;8;0;0;ZONED;LONG;N;37;;  
col2=0;CUST_NAME;CUST_NAME;0;0;40;CHAR;CHAR;N;37;;  
col3=0;BALANCE;BALANCE;10;2;0;ZONED;FLOAT;N;37;;  
col4=0;LAST_ACC;LAST_ACC;0;0;26;TIMESTAMP;TIMESTAMP;N;37;;  
  
[PUBS/AUTHORS]  
NumCol=9  
Col1=0;AU_ID;AU_ID;11;0;11;CHAR;CHAR;N;37;;  
Col2=0;AU_LNAME;AU_LNAME;0;0;40;VARCHAR;CHAR;N;37;;  
Col3=0;AU_FNAME;AU_FNAME;0;0;20;VARCHAR;CHAR;N;37;;  
Col4=0;PHONE;PHONE;0;0;12;CHAR;CHAR;N;37;;  
Col5=0;ADDRESS;ADDRESS;0;0;40;VARCHAR;CHAR;N;37;;  
Col6=0;CITY;CITY;0;0;20;VARCHAR;CHAR;N;37;;  
Col7=0;STATE;STATE;2;0;2;CHAR;CHAR;N;37;;  
Col8=0;ZIP;ZIP;0;0;5;CHAR;SHORT;N;37;;  
Col9=0;CONTRACT;CONTRACT;0;0;9;BINARY;BINARY;N;37;;  
```