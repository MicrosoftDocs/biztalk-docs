---
title: "Date and Time Parameters1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0add6a2-2a71-4e60-86b7-0a2a15b8b20a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Date and Time Parameters
Transaction Integrator (TI) converts and formats the **Date** and **Time** parameters exchanged with the host differently, depending on the programming language and the host platform.  

 You can use TI Project to set or change the properties of the **Date** parameter. The following table shows the formatting and valid separators for each **Host Data Type** in situations where the **Data Type** property of the parameter is set to **Date**.  

### Data Type Formats and Separators  

|Host Data Type|Format (default separator)|Valid separators|Length|Notes|  
|--------------------|----------------------------------|----------------------|------------|-----------|  
|DATE and TIME|yyyydddhhmmsss (two packed decimal fields)|None|8|None|  
|DATE only (COBOL only)|yyyyddd (packed decimal)|None|4|(1) (2)|  
|DATE only (RPG only *MDY)|mm/dd/yy|/-.,&|8|(5)|  
|DATE only (RPG only *DMY)|dd/mm/yy|/-.,&|8|(5)|  
|DATE only (RPG only *YMD)|yy/mm/dd|/-.,&|8|(5)|  
|DATE only (RPG only *JUL)|yy/ddd|/-.,&|6|(5)|  
|DATE only (RPG only *LONGJUL)|yyyy/ddd|None|8|None|  
|TIME only (COBOL only)|hhmmsss (packed decimal)|None|4|(3) (4)|  
IME only (RPG only *HMS)|hh:mm:ss|:.,&|8|None|  
|ISO DATE and TIME|yyyy-mm-dd hh.mm.ss|space|19|None|  
|ISO DATE only|yyyy-mm-dd|-|10|None|  
|ISO TIME only|hh.mm.ss|.|8|None|  
|USA DATE and TIME|mm/dd/yyyy hh:mm AM (or PM)|space|19|None|  
|USA DATE only|mm/dd/yyyy|/|10|None|  
|USA TIME only|hh:mm AM or<br /><br /> hh:mm PM|:|8|None|  
|JIS DATE and TIME|yyyy-mm-dd hh:mm:ss|space|19|None|  
|JIS DATE only|yyyy-mm-dd|-|10|None|  
|JIS TIME only|hh:mm:ss|:|8|None|  
|EUR DATE and TIME|dd.mm.yyyy hh.mm.ss|space|19|None|  
|EUR DATE only|dd.mm.yyyy|.|10|None|  
|EUR TIME only|hh.mm.ss|.|8|None|  
|TIMESTAMP|yyyy-mm-dd-hh.mm.ss.mmmm (length 26).|0001-01-01-00.00.00.000000|0001-01-01-00.00.00.000000|None|  

 Where:  

 ISO = International Standards Organization  

 USA = IBM USA Standard  

 EUR = IBM European Standard  

 JIS = Japanese Industrial Standard Christian Era  

> [!NOTE]
>  When a date is sent to the host, the host populates a seven-digit COMP-3 data type only with the Julian Date YYYYDDD and no other format.  

> [!NOTE]
>  When a date is received from the host, the **Date** parameter must be packed as a valid Julian Date within a seven-digit COMP-3 data type.  

> [!NOTE]
>  When a time is sent to the host, the host populates a seven-digit COMP-3 data type as HHMMSSS up to 100th of a second. For example, sending 01:12:03 AM populates the COMP-3 data type on the host with 0112030; sending 01:12:003 AM populates the COMP-3 data type on the host with 0112003.  

> [!NOTE]
>  When a time is received from the host, the **Time** parameter must be packed within a seven-digit COMP-3 data type packed as HHMMSSS; data passed under any other format might not return the expected results.  

> [!NOTE]
>  A two-digit year (yy) returned from the host is mapped to a four-digit year (yyyy) as follows:  

 00 to 39 is mapped as 20xx.  

 40 to 99 is mapped as 19xx.  

 Rounding occurs when TI receives the parameter from the host:  

- The hour value of time rounds up the day of date.  

- The minutes of time rounds up the hour of time.  

- The first two digits of seconds influences the value of minutes.  

- The third digit of second, or the one 1\100 value of seconds, does not influence the value of minutes. It would just be passed forward to the workstation and displayed.  

  For example:  

- Assigning 1997001 to the host date field and 3701000 to the time field causes the workstation to display 01/02/1997 11:01:00 PM.  

- Assigning 1197001 to the host date field and 0101610 to the time field causes the workstation to display 01/01/1997 01:02:01.  

- Assigning 1197001 to the host date field and 0101619 to the time field, causes the workstation to display 01/01/1997 01:02:019.
