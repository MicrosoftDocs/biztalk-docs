---
title: "User Trailers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "trailers [SWIFT]"
  - "SWIFT, trailers"
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# User Trailers
User trailers, except for the CHK trailer, are optional and when present, occur in the following order:  
  
|Trailer code|Name|  
|------------------|----------|  
|MAC|Message Authentication Code|  
|PAC|Proprietary Authentication Code|  
|CHK|Checksum|  
|TNG|Training|  
|PDE|Possible Duplicate Emission|  
  
- **Message Authentication Code (MAC) Trailer.** Allows authentication by the receiving user. The MAC trailer is followed by an authentication result. This trailer is mandatory for most user-to-user message categories within the FIN application.  
  
   When the FIN Copy Service is used, a PAC trailer (if present) follows the MAC trailer. The following code is an example of a MAC trailer:  
  
  ```  
  {MAC:<authentication-result>}  
  where <authentication-result> = 8!h  
  ```  
  
- **Proprietary Authentication Code (PAC) Trailer.** The PAC trailer is used within the FIN Copy service only when using the double authentication option. Block 5 of FIN user-to-user messages include the PAC trailer immediately after the MAC trailer, if present. This result is calculated on the extracted fields of Block 4 of the message, the value of field 115, if present, and the \<authentication-result\> of the MAC trailer for Copy Services with double authentication.  
  
   As a result, the end-of-block indicator (CrLf-) is included in the PAC calculation and the fields are defined as follows:  
  
  - The first four characters are CrLf:  
  
  - The field and the delimiter are present, that is, 32A:, 20:, and so on.  
  
  - All subfields and their delimiters are present.  
  
    The following code is an example of the PAC trailer format:  
  
  ```  
  {PAC:[<authentication-result>]}  
  where <authentication-result> is mandatory on input messages only and  
  <authentication-result> = 8!h  
  ```  
  
- **CHK (Checksum) Trailer (mandatory for all FIN messages)**  
  
   The CHK trailer is mandatory for all FIN messages and is computed based upon the receiver's address (12 characters with the ninth character replaced by *X* plus the text block). This trailer allows the system and the CBT to check that messages are not corrupted due to a system malfunction or an undetected transmission error.  
  
   The following code is an example of the CHK trailer format:  
  
  ```  
  {CHK:<checksum-result>}  
  where <checksum-result> = 12!h  
  ```  
  
## See Also  
 [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)