---
title: Importing COBOL Host Definitions
description: Learn how to import COBOL host definitions for CICS, IMS, and host files.
ms.prod: host-integration-server
ms.topic: how-to
ms.date: 10/17/2023
---

# Importing COBOL Host Definitions

The original Host Integration Server TI Designer feature was introduced with the full capabilities for designing metadata artifacts from scratch with the assistance from a mainframe programmer. Later, the capability to import host definitions in COBOL or RPG copybook format was added to support scenarios for automating design and reducing involvement from mainframe programmers. Over the years, this capability became the principal option to create metadata artifacts.

## Prerequisites

- Obtain the host definitions (copybooks) that you want to import into HIS Designer for Logic Apps. This designer supports COBOL and RPG copybooks.
 - Understanding how the programming model works for the technology that you want to integrate against, which is CICS or IMS. Both platforms have different requirements and ways to pass and receive information. Make sure that you learn about the appropriate [programming model](choosing-the-appropriate-programming-model1.md) before you import the host definitions.

## Preparing a COBOL Copybook

- COBOL copybooks should follow the basic COBOL coding rules. The HIS Designer for Logic Apps enforces many of those rules. The following table lists the main rules:

   |Columns  |Type  |Observation  |
   |---------|---------|---------|
   | 1–6 | Sequence number | Don't enter anything in these positions. |
   | 7 | Indicator | Use to code a comment (*). A slash (/) is also accepted. |
   | 8-11 | A Margin (Area A) | 77 level numbers and 01 level numbers |
   | 12-72 | B Margin (Area B) | Reserved for 02 levels and higher |
   | 73-80 | Identification | No definitions are allowed here. |

- Verify that the COBOL or RPG copybook meets the requirement of the selected [programming model](choosing-the-appropriate-programming-model1.md).
- Verify the dots at the end of every line. Although with the COBOL latest versions this is not required, be prepared.
- If there are REDEFINES in your copybook, talk to the Mainframe programmer to verify the definition that you will use if there is no discriminant available.
- Remove any character other than the ones stated in the earlier table. Make sure that you have the correct number of characters.

## Importing a COBOL Host Definition (CICS)

The following steps show how to import a COBOL copybook into the HIS Designer for Logic Apps. This COBOL program follows the CICS ELM Link [programming model](choosing-the-appropriate-programming-model1.md).

1. In the left pane, open the component node's shortcut menu, and select **Import** > **Host Definition**.

    In the following example, the component node is named **NetCInt1**.

   :::image type="content" source="media/la-newproject-import-hostdef1.png" alt-text="Importing CICS Host Definitions in Visual Studio":::

1. In the **Import System z COBOL Source File** box, select **Browse**.

   :::image type="content" source="media/la-newproject-import-hostdef2.png" alt-text="Selecting Host Definitions in Visual Studio (CICS)":::

1. Find and select the copybook to import, and then select **Open**.

   :::image type="content" source="media/la-newproject-import-hostdef3.png" alt-text="Selecting the Host Definitions from their directory (CICS)":::

   The following example shows the COBOL program to import:

   ```  
      *****************************************************************
      ** THIS PROGRAM IS A SAMPLE CICS SERVER THAT DEMONSTRATES A      *
      ** SIMPLE BANKING APPLICATION WHICH FORMATS AND RETURNS AN      *
      ** ARRAY OF ACCOUNT RECORDS THAT WILL CONTAIN EITHER CHECKING OR*
      ** SAVINGS INFORMATION.                                         *
      *****************************************************************
       IDENTIFICATION DIVISION.
       PROGRAM-ID. GETAINFO.
       ENVIRONMENT DIVISION.

       DATA DIVISION.

      *****************************************************************
      ** VARIABLES FOR INTERACTING WITH THE TERMINAL SESSION          *
      *****************************************************************
       WORKING-STORAGE SECTION.

       LINKAGE SECTION.

       01 DFHCOMMAREA.
          05 SSN                          PIC X(9).
          05 ACCT-ARRAY OCCURS 2 TIMES.
             10 ACCT-NUM                  PIC X(10).
             10 ACCT-TYPE                 PIC X.
             10 ACCT-INFO                 PIC X(39).
             10 CHECKING REDEFINES ACCT-INFO.
                15 CHK-OD-CHG             PIC S9(3)V99   COMP-3.
                15 CHK-OD-LIMIT           PIC S9(5)V99   COMP-3.
                15 CHK-OD-LINK-ACCT       PIC X(10).
                15 CHK-LAST-STMT          PIC X(10).
                15 CHK-DETAIL-ITEMS       PIC S9(7)      COMP-3.
                15 CHK-BAL                PIC S9(13)V99  COMP-3.
             10 SAVINGS  REDEFINES ACCT-INFO.
                15 SAV-INT-RATE           PIC S9(1)V99   COMP-3.
                15 SAV-SVC-CHRG           PIC S9(3)V99   COMP-3.
                15 SAV-LAST-STMT          PIC X(10).
                15 SAV-DETAIL-ITEMS       PIC S9(7)      COMP-3.
                15 SAV-BAL                PIC S9(13)V99  COMP-3.
                15 FILLER                 PIC X(12).

       PROCEDURE DIVISION.
           IF SSN = '111223333' THEN
      **********************************************************
      *   SSN = 111223333 IS AN INDICATION TO RETURN A
      *   DISCRIMINATED UNION OF CHECKING AND SAVINGS ACCOUNTS
      **********************************************************
              MOVE 'CHK4566112' TO ACCT-NUM         OF ACCT-ARRAY(1)
              MOVE 'C'          TO ACCT-TYPE        OF ACCT-ARRAY(1)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(1)

              MOVE 25.00        TO CHK-OD-CHG       OF ACCT-ARRAY(1)
              MOVE 2000.00      TO CHK-OD-LIMIT     OF ACCT-ARRAY(1)
              MOVE 'SAV1234567' TO CHK-OD-LINK-ACCT OF ACCT-ARRAY(1)
              MOVE '10/31/2005' TO CHK-LAST-STMT    OF ACCT-ARRAY(1)
              MOVE 1            TO CHK-DETAIL-ITEMS OF ACCT-ARRAY(1)
              MOVE 41852.16     TO CHK-BAL          OF ACCT-ARRAY(1)

              MOVE 'SAV1234567' TO ACCT-NUM         OF ACCT-ARRAY(2)
              MOVE 'S'          TO ACCT-TYPE        OF ACCT-ARRAY(2)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(2)
              MOVE 4.50         TO SAV-INT-RATE     OF ACCT-ARRAY(2)
              MOVE 5.00         TO SAV-SVC-CHRG     OF ACCT-ARRAY(2)

              MOVE '10/15/2005' TO SAV-LAST-STMT    OF ACCT-ARRAY(2)
              MOVE 1            TO SAV-DETAIL-ITEMS OF ACCT-ARRAY(2)
              MOVE 146229.83    TO SAV-BAL          OF ACCT-ARRAY(2)
           ELSE
      **********************************************************
      *   SSN = 333221111 IS AN INDICATION TO RETURN A
      *   SIMPLE REDEFINITION OF CHECKING ACCOUNTS ONLY
      **********************************************************
              MOVE 'CHK4566112' TO ACCT-NUM         OF ACCT-ARRAY(1)
              MOVE 'C'          TO ACCT-TYPE        OF ACCT-ARRAY(1)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(1)

              MOVE 25.00        TO CHK-OD-CHG       OF ACCT-ARRAY(1)
              MOVE 2000.00      TO CHK-OD-LIMIT     OF ACCT-ARRAY(1)
              MOVE 'SAV1234567' TO CHK-OD-LINK-ACCT OF ACCT-ARRAY(1)
              MOVE '10/31/2005' TO CHK-LAST-STMT    OF ACCT-ARRAY(1)
              MOVE 1            TO CHK-DETAIL-ITEMS OF ACCT-ARRAY(1)
              MOVE 41852.16     TO CHK-BAL          OF ACCT-ARRAY(1)

              MOVE 'CHK7896112' TO ACCT-NUM         OF ACCT-ARRAY(2)
              MOVE 'C'          TO ACCT-TYPE        OF ACCT-ARRAY(2)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(2)

              MOVE 25.00        TO CHK-OD-CHG       OF ACCT-ARRAY(2)
              MOVE 2000.00      TO CHK-OD-LIMIT     OF ACCT-ARRAY(2)
              MOVE 'SAV7891234' TO CHK-OD-LINK-ACCT OF ACCT-ARRAY(2)
              MOVE '10/31/2005' TO CHK-LAST-STMT    OF ACCT-ARRAY(2)
              MOVE 1            TO CHK-DETAIL-ITEMS OF ACCT-ARRAY(2)
              MOVE 41852.16     TO CHK-BAL          OF ACCT-ARRAY(2)
           END-IF.

           EXEC CICS RETURN END-EXEC.

   ```  

1. Review the copybook to import. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef4.png" alt-text="Dialog with pre-loaded Host Definition in Visual Studio":::

1. After the **Item Options** box opens and populates with the artifact name and the **Link-to-Program name** value, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef5.png" alt-text="Dialog to select options for Item such as Methods, Data Tables, Structures or Unions":::

   The designer presents the metadata artifact that's generated from the COBOL copybook.

   :::image type="content" source="media/la-newproject-import-hostdef6.png" alt-text="Metadata artifact view in HIS Designer for Logic Apps":::

   The designer also generates a host definition for the copybook. This host definition doesn't include the entire provided copybook, but only the fields and datatypes needed for the artifact to interact with the mainframe program. Although the previously provided sample is an entire program, the HIS Designer extracts only the information required based on the selected [programming model](choosing-the-appropriate-programming-model1.md).

   :::image type="content" source="media/la-newproject-import-hostdef7.png" alt-text="Host Definition parsed by HIS Designer for Logic Apps view":::

1. To generate the HIDX, select **Save All**.

## Importing a COBOL Host Definition (IMS)

Both CICS and IMS host mission-critical programs, but each have different requirements. The following steps show how to import a COBOL copybook into the HIS Designer for Logic Apps. This COBOL program follows the IMS Connect programming model.

1.  In the left pane, open the component node's shortcut menu, and select **Import** > **Host Definition**.

     In the following example, the component node is named **NetCInt1**.

   :::image type="content" source="media/la-newproject-import-hostdef1.png" alt-text="Importing IMS Host Definitions in Visual Studio":::

1. In the **Import System z COBOL Source File** box, select **Browse**.

   :::image type="content" source="media/la-newproject-import-hostdef2.png" alt-text="Visual Studio configuration for Logic Apps and HIS":::

1. Find and select the copybook to import, and then select **Open**.

   :::image type="content" source="media/la-newproject-import-hostdef8.png" alt-text="Selecting Host Definitions in Visual Studio (IMS)":::

   The following example shows the COBOL program to import:

      ```
       IDENTIFICATION DIVISION.
       PROGRAM-ID. GETBAL.
       ENVIRONMENT DIVISION.
   
       DATA DIVISION.
   
       WORKING-STORAGE SECTION.
      **************************************************************
      * USER DATA DEFINITIONS.                                     *
      **************************************************************
   
       01  INPUT-AREA.
           05  LLI                      PIC S9(4) COMP VALUE ZERO.
           05  ZZI                      PIC S9(4) COMP VALUE ZERO.
           05  TRAN                     PIC X(7) VALUE SPACES.
           05  NAME                     PIC X(30).
           05  ACCNUM                   PIC X(6).
   
       01  OUTPUT-AREA.
           05  LLO                      PIC S9(4) COMP VALUE ZERO.
           05  ZZO                      PIC S9(4) COMP VALUE ZERO.
           05  ACCBAL                   PIC S9(7)V9(2) COMP-3.
   
       01  IMS-VALUES.
           02  END-OF-MSG               PIC X(2)       VALUE 'QD'.
           02  QUEUE-EMPTY              PIC X(2)       VALUE 'QC'.
           02  GU                       PIC X(4)       VALUE 'GU  '.
           02  ISRT                     PIC X(4)       VALUE 'ISRT'.
           02  CHNG                     PIC X(4)       VALUE 'CHNG'.
   
       LINKAGE SECTION.
       01  IOTP-PCB.
           05  IOTP-LTERM                           PIC X(8).
           05  FILLER                               PIC X(2).
           05  IOTP-STATUS                          PIC X(2).
           05  IOTP-PREFIX.
               10  IOTP-DATE                        PIC S9(7) COMP-3.
               10  IOTP-TIME                        PIC S9(7) COMP-3.
               10  IOTP-MSG-NUMBER                  PIC S9(4) COMP.
               10  FILLER                           PIC X(2).
           05  IOTP-MOD-NAME                        PIC X(8).
           05  IOTP-USER-ID                         PIC X(8).
   
       PROCEDURE DIVISION.
           ENTRY 'DLITCBL' USING IOTP-PCB.
           CALL 'CBLTDLI' USING GU IOTP-PCB INPUT-AREA.
   
              IF IOTP-STATUS = END-OF-MSG
                 DISPLAY 'IOTP-STATUS = END-OF-MSG'
              END-IF.
              IF IOTP-STATUS = QUEUE-EMPTY
                 DISPLAY 'IOTP-STATUS = QUEUE-EMPTY'
              END-IF.
              IF IOTP-STATUS NOT = ' '
                 DISPLAY 'CALL FAILED IOTP-STATUS = ' IOTP-STATUS
              END-IF.
   
           MOVE 777.12               TO ACCBAL OF OUTPUT-AREA.
   
           MOVE LENGTH OF OUTPUT-AREA TO LLO.
           CALL 'CBLTDLI' USING ISRT IOTP-PCB OUTPUT-AREA.
              IF IOTP-STATUS NOT = ' '
                 DISPLAY 'SEND FAILED IOTP-STATUS = ' IOTP-STATUS
              END-IF.
   
           GOBACK.

   ```

1. Review the copybook to import. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef9.png" alt-text="Dialog with pre-loaded Host Definition in Visual Studio (IMS)":::

1. After the **Item Options** box opens and populates with the artifact name and the **Transaction ID** value, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef10.png" alt-text="Dialog to select options for Item such as Methods, Data Tables, Structures or Unions (IMS)":::

1. After the **Input Area** box opens, review the information in the **Input area** section. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef11.png" alt-text="IMS Host transaction input area":::

1. After the **Output Area** box opens, review information in the **Output area** section. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef12.png" alt-text="IMS Host transaction output area":::

1. After the **Return Value** box opens, review the information in the **Return value** section. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef13.png" alt-text="Return value dialog for host transaction":::

1. After the **Data Tables, Structures and Unions** box opens, review the groups to use for the data tables and structures in your application. When you're ready, select **Next**.

   For this sample application, the following example doesn't require this setting.

   :::image type="content" source="media/la-newproject-import-hostdef14.png" alt-text="Data Tables and Structures dialog":::

1. After the **LL Fields Area** box opens, review the LL fields that must be excluded from the transaction. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef15.png" alt-text="LL Fields Area dialog":::

1. After the **ZZ Fields Area** box opens, review the ZZ fields that must be excluded from the transaction. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef16.png" alt-text="ZZ Fields Area dialog":::

1. After the **TRANCODE Fields Area** box opens, review the TRANCODE fields that must be excluded from your application. When you're ready, select **Finish**.

   :::image type="content" source="media/la-newproject-import-hostdef17.png" alt-text="TRANCODE Fields Area dialog":::

   - The Designer will present the metadata artifact generated from the COBOL copybook.
   
   :::image type="content" source="media/la-newproject-import-hostdef18.png" alt-text="IMS generated metadata view":::
   
   The Designer will also generate a Host Definition for the Copybook. This Host Definition will not include the entire provided copybook but only the fields and datatypes needed for the artifact to interact with the Mainframe Program. In other words, while the sample provided above is an entire program, the HIS Designer will extract only the information needed depending on the selected [Programming Model](choosing-the-appropriate-programming-model1.md).
   
   :::image type="content" source="media/la-newproject-import-hostdef19.png" alt-text="Host Definition generated by HIS Designer for Logic Apps":::

1. Select **Save All** to generate the HIDX.

## Importing a COBOL Host File Definition

There are multiple types of IBM Host Files. Host files can exist in Mainframes or Midranges and have their own types and characteristics. With an increasing demand on modernizing or migrating Mainframe or midranges applications that use Host File data such as VSAM files to Azure, it is becoming more common to access this files and integrate them into Modern solutions.

The following steps will allow importing a COBOL copybook into the HIS Designer for Logic Apps. This COBOL copybook represents a simple VSAM file. The Import wizard will create structures and unions. Once the copybook was imported, you will be able to create Tables  and assign them the right schemas.

1. Select on the **Component** node and then **Import** and **Host Definition**.

   :::image type="content" source="media/la-newproject-import-hostdefhf1.png" alt-text="Importing Host Files Definitions in Visual Studio":::

1. In the Import System z COBOL source file dialog, Select **Browse**

   :::image type="content" source="media/la-newproject-import-hostdefhf2.png" alt-text="Selecting Host Definitions in Visual Studio (Host Files)":::

1. Select the Copybook to be imported

   :::image type="content" source="media/la-newproject-import-hostdefhf3.png" alt-text="Selecting the Host Definitions from their directory (Host Files)":::

1. The following is the COBOL program to be imported:

   ```
         ******************************************************************        
         *HIS TRANSACTION DESIGNER EXPORT, 9.0
         *DATA DECLARATION GENERATED ON 9/23/2013 5:21:51 PM
         ******************************************************************        
         *LIBRARY NAME.............CustomerDatabaseZOS.HIDX
         *DESCRIPTION..............NONE AVAILABLE
         ******************************************************************        
          01  CUSTOMER-RECORD.
              05 CUSTOMER-NAME               PIC X(30).
              05 CUSTOMER-SSN                PIC X(9).
              05 CUSTOMER-ADDRESS.
                 10 CUSTOMER-STREET          PIC X(20).
                 10 CUSTOMER-CITY            PIC X(10).
                 10 CUSTOMER-STATE           PIC X(4).
                 10 CUSTOMER-ZIP             PIC 9(5).
              05 CUSTOMER-PHONE              PIC X(13).
              05 CUSTOMER-ACCESS-PIN         PIC X(4).
   ```  
 
1. Preview the Copybook to be imported and review the options for REDEFINEs, use of Importer defaults and/or Generate structure on host definition indents. Select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdefhf4.png" alt-text="Dialog with pre-loaded Host Definition in Visual Studio (Host Files)":::

   - The Designer will present the metadata artifact generated from the COBOL copybook. Remember this artifact is incomplete. You will need to create a Table or Tables that will reflect the Host Files.

   :::image type="content" source="media/la-newproject-import-hostdefhf6.png" alt-text="Metadata artifact view in HIS Designer for Logic Apps (Host Files)":::

1. Select the Tables directory and right Select **Add table**.

   :::image type="content" source="media/la-newproject-import-hostdefhf7.png" alt-text="Addint a Table to the Host File Definition":::

   - You will need to rename the Table, assign the previously imported Schema and enter the Mainframe or Midrange name of the Host File as follows.

   :::image type="content" source="media/la-newproject-import-hostdefhf8.png" alt-text="Entering Alias, Host File Name and Schema of the Host File":::

1. Select **Save All** to generate the HIDX. file. The following is the final view of the Host Files Metadata artifact.

   :::image type="content" source="media/la-newproject-import-hostdefhf9.png" alt-text="Generating HIDX file by saving the metadata artifact":::
