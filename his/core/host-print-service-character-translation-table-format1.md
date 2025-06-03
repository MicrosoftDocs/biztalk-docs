---
description: "Learn more about: Host Print Service Character Translation Table Format"
title: "Host Print Service Character Translation Table Format1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Host Print Service Character Translation Table Format
The character translation table that can be used by the custom code page option of Host Print service is a 512-byte file, split into two 256-byte regions. Bytes 0255 are the mapping bytes for data from the host; bytes 256511 map data to the host.  
  
 For example, the following illustrates standard translation tables for the 037 EBCDIC code page:  
  
```  
  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F  
---------------------------------------------------  
00| 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20  
10| 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20  
20| 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20  
30| 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20  
40| 20 a0 e2 e4 e0 e1 e3 e5 e7 f1 a2 2e 3c 28 2b 7c  
50| 26 e9 ea eb e8 ed ee ef ec df 21 24 2a 29 3b ac  
60| 2d 2f c2 c4 c0 c1 c3 c5 c7 d1 a6 2c 25 5f 3e 3f  
70| f8 c9 ca cb c8 cd ce cf cc 60 3a 23 40 27 3d 22  
80| d8 61 62 63 64 65 66 67 68 69 ab bb f0 fd de b1  
90| b0 6a 6b 6c 6d 6e 6f 70 71 72 aa ba e6 b8 c6 a4  
a0| b5 7e 73 74 75 76 77 78 79 7a a1 bf d0 dd fe ae  
b0| 5e a3 a5 b7 a9 a7 b6 bc bd be 5b 5d af a8 b4 d7  
c0| 7b  42 43 44 45 46 47 48 49 ad f4 f6 f2 f3 f5  
d0| 7d 4a 4b 4c 4d 4e 4f 50 51 52 b9 fb fc f9 fa ff  
e0| 5c f7 53 54 55 56 57 58 59 5a b2 d4 d6 d2 d3 d5  
f0| 30 31 32 33 34 35 36 37 38 39 b3 db dc d9 da 00  
  
```  
  
## Bytes 0-255: Data from Host  
 Each byte that is received represents a location, that is, a byte offset, in the appropriate table. For example, if the value 0xC1 (the EBCDIC value for the letter A) is received from the host, it is converted to the value in position 0xC1 in the first table; that is, to 0x41 (the ASCII value for the letter A). This is shown in bold in the preceding table.  
  
 Similarly, if the letter *Z* (ASCII value 0x5A) is to be transmitted to the host, it is first converted to the value located in position 0x5A in the second table, which is 0xE9 (the EBCDIC value for Z). This is shown in bold in the table below:  
  
```  
  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F  
00| 00 01 02 03 37 2d 2e 2f 16 05 25 0b 0c 0d 0e 0f  
10| 10 14 24 04 b6 15 32 26 18 19 00 27 1c 1d 1e 1f  
20| 40 5a 7f 7b 5b 6c 50 7d 4d 5d 5c 4e 6b 60 4b 61  
30| f0 f1 f2 f3 f4 f5 f6 f7 f8 f9 7a 5e 4c 7e 6e 6f  
40| 7c c1 c2 c3 c4 c5 c6 c7 c8 c9 d1 d2 d3 d4 d5 d6  
50| d7 d8 d9 e2 e3 e4 e5 e6 e7 e8  ba e0 bb b0 6d  
60| 79 81 82 83 84 85 86 87 88 89 91 92 93 94 95 96  
70| 97 98 99 a2 a3 a4 a5 a6 a7 a8 a9 c0 4f d0 a1 00  
80| 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
90| 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
a0| 41 aa 4a b1 9f b2 6a b5 bd b4 9a 8a 5f ca af bc  
b0| 90 8f ea fa be a0 b6 b3 9d da 9b 8b b7 b8 b9 ab  
c0| 64 65 62 66 63 67 9e 68 74 71 72 73 78 75 76 77  
d0| ac 69 ed ee eb ef ec bf 80 fd fe fb fc ad 8e 59  
e0| 44 45 42 46 43 47 9c 48 54 51 52 53 58 55 56 57  
f0| 8c 49 cd ce cb cf cc e1 70 dd de db dc 8d ae df  
```  
  
## Bytes 256511: Data to Host  
 Currently, only the first table (bytes 0255) is used by Host Print service. However, the file must be exactly 512 bytes in length, so the final 256 bytes must be present, even if they are set to zero.  
  
## See Also  
 [Character Tables](./character-tables2.md)
