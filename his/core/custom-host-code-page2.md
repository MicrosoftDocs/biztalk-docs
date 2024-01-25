---
description: "Learn more about: Custom Host Code Page"
title: "Custom Host Code Page2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Custom Host Code Page
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] allows a custom host code page to be used for a printer session. The host code page is used for the translation between ASCII and EBCDIC. By default, a printer session will use the standard language code page provided by Windows Server. As an alternative, a custom code page can be specified to allow a different translation. For example, using the default code page, the EBCDIC letter "A" ('0xC1') would be translated to an ASCII letter "A" ('0x41'). With a custom code page, it would be possible to have the EBCDIC "A" translated to any value. The custom code pages are text files that can be modified with a hex editor. The code page file contains 512 bytes. The first 256 bytes represent what the EBCDIC characters are translated to. The second 256 bytes are what the ASCII characters are translated to. Logically each section is a 16-column by 16-row block.  
  
 Bytes 0-255: Data from Host  
  
```  
  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F  
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
c0| 7b 41 42 43 44 45 46 47 48 49 ad f4 f6 f2 f3 f5  
d0| 7d 4a 4b 4c 4d 4e 4f 50 51 52 b9 fb fc f9 fa ff  
e0| 5c f7 53 54 55 56 57 58 59 5a b2 d4 d6 d2 d3 d5  
f0| 30 31 32 33 34 35 36 37 38 39 b3 db dc d9 da 00  
  
```  
  
 Bytes 256-511: Data to Host  
  
```  
  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F  
00| 00 01 02 03 37 2d 2e 2f 16 05 25 0b 0c 0d 0e 0f  
10| 10 14 24 04 b6 15 32 26 18 19 00 27 1c 1d 1e 1f  
20| 40 5a 7f 7b 5b 6c 50 7d 4d 5d 5c 4e 6b 60 4b 61  
30| f0 f1 f2 f3 f4 f5 f6 f7 f8 f9 7a 5e 4c 7e 6e 6f  
40| 7c c1 c2 c3 c4 c5 c6 c7 c8 c9 d1 d2 d3 d4 d5 d6  
50| d7 d8 d9 e2 e3 e4 e5 e6 e7 e8 e9 ba e0 bb b0 6d  
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
  
 The value being translated is matched to its new value using the first number in the hex value as the row and the second as the column. For example, to find what the EBCDIC character "Z" ('0xE9') is translated to in the sample code page count down to row E and over to column 9. This position has the value '0x5A', which is the ASCII value for a "Z".  
  
## Sample Host Code Page (as seen in a Hex editor)  
  
```  
20 20 20 20 20 20 20 20-20 20 20 20 20 20 20 20  
20 20 20 20 20 20 20 20-20 20 20 20 20 20 20 20  
20 20 20 20 20 20 20 20-20 20 20 20 20 20 20 20  
20 20 20 20 20 20 20 20-20 20 20 20 20 20 20 20  
20 A0 E2 E4 E0 E1 E3 E5-E7 F1 A2 2E 3C 28 2B 7C  
26 E9 EA EB E8 ED EE EF-EC DF 21 24 2A 29 3B AC  
2D 2F C2 C4 C0 C1 C3 C5-C7 D1 A6 2C 25 5F 3E 3F  
F8 C9 CA CB C8 CD CE CF-CC 60 3A 23 40 27 3D 22  
D8 61 62 63 64 65 66 67-68 69 AB BB F0 FD DE B1  
B0 6A 6B 6C 6D 6E 6F 70-71 72 AA BA E6 B8 C6 A4  
B5 7E 73 74 75 76 77 78-79 7A A1 BF D0 DD FE AE  
5E A3 A5 B7 A9 A7 B6 BC-BD BE 5B 5D AF A8 B4 D7  
7B 41 42 43 44 45 46 47-48 49 AD F4 F6 F2 F3 F5  
7D 4A 4B 4C 4D 4E 4F 50-51 52 B9 FB FC F9 FA FF  
5C F7 53 54 55 56 57 58-59 5A B2 D4 D6 D2 D3 D5  
30 31 32 33 34 35 36 37-38 39 B3 DB DC D9 DA 00  
00 01 02 03 37 2D 2E 2F-16 05 25 0B 0C 0D 0E 0F  
10 14 24 04 B6 15 32 26-18 19 00 27 1C 1D 1E 1F  
40 5A 7F 7B 5B 6C 50 7D-4D 5D 5C 4E 6B 60 4B 61  
F0 F1 F2 F3 F4 F5 F6 F7-F8 F9 7A 5E 4C 7E 6E 6F  
7C C1 C2 C3 C4 C5 C6 C7-C8 C9 D1 D2 D3 D4 D5 D6  
D7 D8 D9 E2 E3 E4 E5 E6-E7 E8 E9 BA E0 BB B0 6D  
79 81 82 83 84 85 86 87-88 89 91 92 93 94 95 96  
97 98 99 A2 A3 A4 A5 A6-A7 A8 A9 C0 4F D0 A1 00  
00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  
00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  
41 AA 4A B1 9F B2 6A B5-BD B4 9A 8A 5F CA AF BC  
90 8F EA FA BE A0 B6 B3-9D DA 9B 8B B7 B8 B9 AB  
64 65 62 66 63 67 9E 68-74 71 72 73 78 75 76 77  
AC 69 ED EE EB EF EC BF-80 FD FE FB FC AD 8E 59  
44 45 42 46 43 47 9C 48-54 51 52 53 58 55 56 57  
8C 49 CD CE CB CF CC E1-70 DD DE DB DC 8D AE DF  
  
```  
  
## See Also  
 [IBM i (APPC) Printing](../core/as-400-appc-printing1.md)
