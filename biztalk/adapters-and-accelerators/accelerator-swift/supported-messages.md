---
title: "Supported Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SWIFT messages, supported message types"
ms.assetid: 9e059f86-05b1-4c6b-afa8-0ca969874a97
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Supported Messages
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides a list of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] and SWIFT messages. The messages fall into several financial categories which are listed below.  
  
 This section contains:  
  
-   [SWIFT Messages - Microsoft](#fsa_intro_xtkj)  
  
-   [Category 0: FIN System Messages](#fsa_intro_xcpk)  
  
-   [Category 1: Customer Payments and Checks](#fsa_intro_lxnf)  
  
-   [Category 2: Financial Institution Transfers](#fsa_intro_fywg)  
  
-   [Category 3: Treasury Markets Foreign Exchange, Money Markets and Derivatives](#fsa_intro_qipa)  
  
-   [Category 4: Collections and Cash Letters](#fsa_intro_ruuc)  
  
-   [Category 5: Securities Markets](#fsa_intro_iitn)  
  
-   [Category 6: Treasury Markets Precious Metals](#fsa_intro_bjez)  
  
-   [Category 7: Documentary Credits and Guarantees](#fsa_intro_vhkw)  
  
-   [Category 8: Travellers Cheques](#fsa_intro_qlwo)  
  
-   [Category 9: Cash Management and Customer Status](#fsa_intro_sptj)  
  
##  <a name="fsa_intro_xtkj"></a> SWIFT Messages - Microsoft  
 The following table describes the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SWIFT messages for service types GPA and FIN Control.  
  
|Message type|Description|  
|------------------|-----------------|  
|**02**|Login Request Message|  
|**03**|Select Command|  
|**05**|Quit Command|  
|**06**|Logout Command|  
|**12**|System Remove AP Request|  
|**13**|System Abort AP Confirmation|  
|**14**|System Request to Remove LT|  
|**15**|System Confirmation of User-initiated LT Abort|  
|**21**|Acknowledgement of a GPA Message Sent by an LT (ACK/NAK)|  
|**21**|Acknowledgement of a GPA Message Received by an LT (ACK/NAK)|  
|**21**|Acknowledgement of a FIN Message Sent by an LT (ACK/NAK)|  
|**21**|Acknowledgement of a FIN Message Received by an LT (UAK/UNK)|  
|**22**|Login Positive Acknowledgement (LAK)|  
|**23**|Acknowledgement of a Select Request (SAK)|  
|**25**|Quit Acknowledgement|  
|**26**|Logout Acknowledgement|  
|**33**|User Abort AP Request|  
|**35**|User Request to Abort LT (ABORT LT)|  
|**42**|Login Negative Acknowledgement (LNK)|  
|**43**|Select Negative Acknowledgement (SNK)|  
  
##  <a name="fsa_intro_xcpk"></a> Category 0: FIN System Messages  
 The following table describes messages form Category 0: Financial System Messages, including User to SWIFT and SWIFT to User.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 008**|System Request to Quit|  
|**MT 009**|System Request to Logout|  
|**MT 010**|Non-Delivery Warning|  
|**MT 011**|Delivery Notification|  
|**MT 012**|Sender Notification|  
|**MT 015**|Delayed NAK|  
|**MT 019**|Abort Notification|  
|**MT 020**|Retrieval Request (Text and History)|  
|**MT 021**|Retrieved Message (Text and History)|  
|**MT 022**|Retrieval Request (History)|  
|**MT 023**|Retrieved Message (History)|  
|**MT 028**|FIN Copy Message Status Request|  
|**MT 029**|FIN Copy Message Status Report|  
|**MT 031**|Session History Request|  
|**MT 032**|Delivery Subset Status Request|  
|**MT 035**|Delivery Instruction Request|  
|**MT 036**|LT History Request|  
|**MT 037**|Time Zone Status Request|  
|**MT 041**|Select Status Request for FIN|  
|**MT 042**|Cut-off Times List Request|  
|**MT 043**|Non-Banking Days List Request|  
|**MT 044**|Undelivered Report Rules Redefinition|  
|**MT 045**|Daily Check Time Change Request|  
|**MT 046**|Undelivered Message Report Request|  
|**MT 047**|Delivery Instructions Redefinition Request|  
|**MT 048**|Undelivered Report Rules Request|  
|**MT 049**|Daily Check Report Time Query|  
|**MT 051**|Session History Report|  
|**MT 052**|Delivery Subset Status Report|  
|**MT 055**|Delivery Instructions Report|  
|**MT 056**|LT History Report|  
|**MT 057**|Time Zone Status Report|  
|**MT 061**|Select Status Report for FIN|  
|**MT 062**|Cut-off Time List Report|  
|**MT 063**|Non-Banking Days List Report|  
|**MT 064**|Undelivered Report Rules Change Report|  
|**MT 065**|Time Change Report for Daily Check Report|  
|**MT 066**|Solicited Undelivered Message Report|  
|**MT 067**|Delivery Instructions Redefinition Report|  
|**MT 068**|Undelivered Report Rules|  
|**MT 069**|Daily Check Report Time Status|  
|**MT 072**|Test Mode Selection|  
|**MT 073**|Message Sample Request|  
|**MT 074**|Broadcast Request|  
|**MT 075**|Certification Request|  
|**MT 076**|Certification Error|  
|**MT 077**|Additional Selection Criteria for FIN|  
|**MT 081**|Daily Check Report|  
|**MT 082**|Undelivered Message Report at a Fixed Hour|  
|**MT 083**|Undelivered Message Report at Cut-off Time|  
|**MT 085**|ICC Delivery Information|  
|**MT 087**|Certification Response|  
|**MT 090**|User-to-SWIFT Message|  
|**MT 092**|SWIFT-to-User Message|  
|**MT 094**|Broadcast|  
|**MT 096**|FIN Copy to Central Institution Message|  
|**MT 097**|FIN Copy Message Authorization/Refusal Notification|  
  
##  <a name="fsa_intro_lxnf"></a> Category 1: Customer Payments and Checks  
 The following table describes messages from Category 1: Payments and Checks.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 101**|Request for Transfer|  
|**MT 102**|Multiple Customer Transfer|  
|**MT 102+**|Multiple Customer Transfer (STP)|  
|**MT 103**|Single Customer Credit Transfer|  
|**MT 103+**|Single Customer Credit Transfer (STP)|  
|**MT 104**|Direct Debit and Request for Debit Transfer Message|  
|**MT 105**|EDIFACT Envelope|  
|**MT 106**|EDIFACT Envelope|  
|**MT 107**|General Direct Debit Message|  
|**MT 110**|Advice of Cheque(s)|  
|**MT 111**|Request for Stop Payment of a Cheque|  
|**MT 112**|Status of a Request for Stop Payment of a Cheque|  
|**MT 121**|Multiple Interbank Funds Transfer (EDIFACT FINPAY)|  
|**MT 190**|Advice of Charges, Interest and Other Adjustments|  
|**MT 191**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 192**|Request for Cancellation|  
|**MT 195**|Queries|  
|**MT 196**|Answers|  
|**MT 198**|Proprietary Message|  
|**MT 199**|Free Format Message|  
  
##  <a name="fsa_intro_fywg"></a> Category 2: Financial Institution Transfers  
 The following table describes messages from Category 2: Financial Institution Transfers.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 200**|Financial Institution Transfer for its Own Account|  
|**MT 201**|Multiple Financial Institution Transfer for its Own Account|  
|**MT 202**|General Financial Institution Transfer|  
|**MT 203**|Multiple General Financial Institution Transfer|  
|**MT 204**|Financial Markets Direct Debit Message|  
|**MT 205**|Financial Institution Transfer Execution|  
|**MT 206**|Cheque Truncation Message|  
|**MT 207**|Request for Financial Institution Transfer|  
|**MT 210**|Notice to Receive|  
|**MT 256**|Advice of Non-Payment of Cheques|  
|**MT 290**|Advice of Charges, Interest and Other Adjustments|  
|**MT 291**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 292**|Request for Cancellation|  
|**MT 293**|Information Service Message|  
|**MT 295**|Queries|  
|**MT 296**|Answers|  
|**MT 298**|Proprietary Message|  
|**MT 299**|Free Format Message|  
  
##  <a name="fsa_intro_qipa"></a> Category 3: Treasury Markets Foreign Exchange, Money Markets and Derivatives  
 The following table describes messages from Category 3: Treasury Markets Foreign Exchange, Money Markets, and Derivatives.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 300**|Foreign Exchange Confirmation|  
|**MT 303**|Forex/Currency Option Allocation Instruction|  
|**MT 304**|Advice/Instruction of a Third Party Deal|  
|**MT 305**|Foreign Currency Option Confirmation|  
|**MT 306**|Foreign Currency Option Confirmation|  
|**MT 307**|Advice/Instruction of a Third Party FX Deal|  
|**MT 308**|Instruction for Gross/Net Settlement of Third Party FX Deals|  
|**MT 320**|Fixed Loan/Deposit Confirmation|  
|**MT 321**|Instruction to Settle a Third Party Loan/Deposit|  
|**MT 330**|Call/Notice Loan/Deposit Confirmation|  
|**MT 340**|Forward Rate Agreement Confirmation|  
|**MT 341**|Forward Rate Agreement Settlement Confirmation|  
|**MT 350**|Advice of Loan/Deposit Interest Payment|  
|**MT 360**|Single Currency Interest Rate Derivative Confirmation|  
|**MT 361**|Cross Currency Interest Rate Swap Confirmation|  
|**MT 362**|Interest Rate Reset/Advice of Payment|  
|**MT 364**|Single Currency Interest Rate Swap Termination/Recouponing Confirmation|  
|**MT 365**|Cross Currency Interest Rate Swap Termination/Recouponing Confirmation|  
|**MT 380**|Foreign Exchange Order|  
|**MT 381**|Foreign Exchange Order Confirmation|  
|**MT 390**|Advice of Charges, Interest and Other Adjustments|  
|**MT 391**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 392**|Request for Cancellation|  
|**MT 395**|Queries|  
|**MT 396**|Answers|  
|**MT 398**|Proprietary Message|  
|**MT 399**|Free Format Message|  
  
##  <a name="fsa_intro_ruuc"></a> Category 4: Collections and Cash Letters  
 The following table describes messages from Category 4: Collections and Cash Letters.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 400**|Advice of Payment|  
|**MT 405**|Clean Collection|  
|**MT 410**|Acknowledgement|  
|**MT 412**|Advice of Acceptance|  
|**MT 416**|Advice of Non-Payment/Non-Acceptance|  
|**MT 420**|Tracer|  
|**MT 422**|Advice of Fate and Request for Instructions|  
|**MT 430**|Amendment of Instructions|  
|**MT 450**|Cash Letter Credit Advice|  
|**MT 455**|Cash Letter Credit Adjustment Advice|  
|**MT 456**|Advice of Dishonour|  
|**MT 490**|Advice of Charges, Interest and Other Adjustments|  
|**MT 491**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 492**|Request for Cancellation|  
|**MT 495**|Queries|  
|**MT 496**|Answers|  
|**MT 498**|Proprietary Message|  
|**MT 499**|Free Format Message|  
  
##  <a name="fsa_intro_iitn"></a> Category 5: Securities Markets  
 The following table describes messages from Category 5: Securities Markets.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 500**|Instruction to Register|  
|**MT 501**|Confirmation of Registration or Modification|  
|**MT 502**|Order to Buy or Sell|  
|**MT 503**|Collateral Claim|  
|**MT 504**|Collateral Proposal|  
|**MT 505**|Collateral Substitution|  
|**MT 506**|Collateral and Exposure Statement|  
|**MT 507**|Collateral Status and Processing Advice|  
|**MT 508**|Intra-Position Advice|  
|**MT 509**|Trade Status Message|  
|**MT 510**|Registration Status and Processing Advice|  
|**MT 513**|Client Advice Of Execution|  
|**MT 514**|Trade Allocation Instruction|  
|**MT 515**|Client Confirmation of Purchase or Sale|  
|**MT 516**|Securities Loan Confirmation|  
|**MT 517**|Trade Confirmation Affirmation|  
|**MT 518**|Market-Side Securities Trade Confirmation|  
|**MT 519**|Modification of Client Details|  
|**MT 524**|Intra-Position Instruction|  
|**MT 526**|General Securities Lending/Borrowing Message|  
|**MT 527**|Tri-party Collateral Instruction|  
|**MT 528**|ETC Client-Side Settlement Instruction|  
|**MT 529**|ETC Market-Side Settlement Instruction|  
|**MT 530**|Transaction Processing Command|  
|**MT 535**|Statement of Holdings|  
|**MT 536**|Statement of Transactions|  
|**MT 537**|Statement of Pending Transactions|  
|**MT 538**|Statement of Intra-Position Advices|  
|**MT 540**|Receive Free|  
|**MT 541**|Receive Against Payment|  
|**MT 542**|Deliver Free|  
|**MT 543**|Deliver Against Payment|  
|**MT 544**|Receive Free Confirmation|  
|**MT 545**|Receive Against Payment Confirmation|  
|**MT 546**|Deliver Free Confirmation|  
|**MT 547**|Deliver Against Payment Confirmation|  
|**MT 548**|Settlement Status and Processing Advice|  
|**MT 549**|Request for Statement/Processing Advice|  
|**MT 558**|Tri-party Collateral Status and Processing Advice|  
|**MT 559**|Paying Agents Claim|  
|**MT 564**|Corporate Action Notification|  
|**MT 565**|Corporate Action Instruction|  
|**MT 566**|Corporate Action Confirmation|  
|**MT 567**|Corporate Action Status and Processing Advice|  
|**MT 568**|Corporate Action Narrative|  
|**MT 569**|Tri-party Collateral and Exposure Statement|  
|**MT 574**|(IRSLST) IRS 1441 NRA|  
|**MT 574**|(W8BENO) IRS 1441 NRA|  
|**MT 575**|Report of Combined Activity|  
|**MT 576**|Statement of Open Orders|  
|**MT 577**|Statement of Numbers|  
|**MT 578**|Settlement Allegement|  
|**MT 579**|Certificate Numbers|  
|**MT 581**|Collateral Adjustment Message|  
|**MT 582**|Reimbursement Claim Or Advice|  
|**MT 584**|Statement of ETC Pending Trades|  
|**MT 586**|Statement of Settlement Allegements|  
|**MT 587**|Depositary Receipt Instruction|  
|**MT 588**|Depositary Receipt Confirmation|  
|**MT 589**|Depositary Receipt Status and Processing Advice|  
|**MT 590**|Advice of Charges, Interest and Other Adjustments|  
|**MT 591**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 592**|SWIFT-to-User Message|  
|**MT 595**|Questions|  
|**MT 596**|Answers|  
|**MT 598**|Proprietary Message|  
|**MT 599**|Free Format Message|  
  
##  <a name="fsa_intro_bjez"></a> Category 6: Treasury Markets Precious Metals  
 The following table describes messages from Category 6: Treasury Markets Precious Metals, Treasure Markets Syndications, and Treasury Markets Common Messages.  
  
|Message type|Description|  
|------------------|-----------------|  
||**Treasury Markets Precious Metals**|  
|**MT 600**|Metal Trade Confirmation|  
|**MT 601**|Precious Metal Option Confirmation|  
|**MT 604**|Precious Metal Transfer/Delivery Order|  
|**MT 605**|Precious Metal Notice to Receive|  
|**MT 606**|Precious Metal Debit Advice|  
|**MT 607**|Precious Metal Credit Advice|  
|**MT 608**|Statement of a Metal Account|  
|**MT 609**|Statement of Metal Contracts|  
|**MT 620**|Metal Fixed Loan/Deposit Confirmation|  
||**Treasury Markets Syndications**|  
|**MT 643**|Notice of Drawdown/Renewal|  
|**MT 644**|Advice of Rate and Amount Fixing|  
|**MT 645**|Notice of Fee Due|  
|**MT 646**|Payment of Principal and/or of Interest|  
|**MT 649**|General Syndicated Facility Message|  
||**Treasury Markets - Common Messages**|  
|**MT 690**|Advice of Charges, Interest and Other Adjustments|  
|**MT 691**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 692**|Request for Cancellation|  
|**MT 695**|Queries|  
|**MT 696**|Answers|  
|**MT 698**|Proprietary Message|  
|**MT 699**|Free Format Message|  
  
##  <a name="fsa_intro_vhkw"></a> Category 7: Documentary Credits and Guarantees  
 The following table describes messages from Category 7: Documentary Credits and Guarantees.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 700**|Issue of a Documentary Credit|  
|**MT 701**|Issue of a Documentary Credit|  
|**MT 705**|Pre-Advice of a Documentary Credit|  
|**MT 707**|Amendment to a Documentary Credit|  
|**MT 710**|Advice of a Third Banks Documentary Credit|  
|**MT 711**|Advice of a Third Banks Documentary Credit|  
|**MT 720**|Transfer of a Documentary Credit|  
|**MT 721**|Transfer of a Documentary Credit|  
|**MT 730**|Acknowledgement|  
|**MT 732**|Advice of Discharge|  
|**MT 734**|Advice of a Refusal|  
|**MT 740**|Authorization to Reimburse|  
|**MT 742**|Reimbursement Claim|  
|**MT 747**|Amendment to an Authorisation to Reimburse|  
|**MT 750**|Advice of Discrepancy|  
|**MT 752**|Authorisation to Pay, Accept or Negotiate|  
|**MT 754**|Advice of Payment/Acceptance/Negotiation|  
|**MT 756**|Advice of Reimbursement or Payment|  
|**MT 760**|Guarantee|  
|**MT 767**|Guarantee Amendment|  
|**MT 768**|Acknowledgement of a Guarantee Message|  
|**MT 769**|Advice of Reduction or Release|  
|**MT 790**|Advice of Charges, Interest and Other Adjustments|  
|**MT 791**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 792**|Request for Cancellation|  
|**MT 795**|Queries|  
|**MT 796**|Answers|  
|**MT 798**|Proprietary Message|  
|**MT 799**|Free Format Message|  
  
##  <a name="fsa_intro_qlwo"></a> Category 8: Travellers Cheques  
 The following table describes messages from Category 8: Travellers Cheques.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 800**|MT 800 T/C Sales and Settlement Advice [Single]|  
|**MT 801**|MT 801 T/C Multiple Sales Advice|  
|**MT 802**|MT 802 T/C Settlement Advice|  
|**MT 810**|MT 810 T/C Refund Request|  
|**MT 812**|MT 812 T/C Refund Authorisation|  
|**MT 813**|MT 813 T/C Refund Confirmation|  
|**MT 820**|MT 820 Request for T/C Stock|  
|**MT 821**|MT 821 T/C Inventory Addition|  
|**MT 822**|MT 822 Trust Receipt Acknowledgement|  
|**MT 823**|MT 823 T/C Inventory Transfer|  
|**MT 824**|MT 824 T/C Inventory Destruction/Cancellation Notice|  
|**MT 890**|MT 890 Advice of Charges, Interest and Other Adjustments|  
|**MT 891**|MT 891 Request for Payment of Charges, Interest and Other Expenses|  
|**MT 892**|MT 892 Request for Cancellation|  
|**MT 895**|MT 895 Queries|  
|**MT 896**|MT 896 Answers|  
|**MT 898**|MT 898 Proprietary Message|  
|**MT 899**|MT 899 Free Format Message|  
  
##  <a name="fsa_intro_sptj"></a> Category 9: Cash Management and Customer Status  
 The following table describes messages from Category 9: Cash Management and Customer Status.  
  
|Message type|Description|  
|------------------|-----------------|  
|**MT 900**|Confirmation of Debit|  
|**MT 910**|Confirmation of Credit|  
|**MT 920**|Request Message|  
|**MT 935**|Rate Change Advice|  
|**MT 940**|Customer Statement Message|  
|**MT 941**|Balance Report|  
|**MT 942**|Interim Transaction Report|  
|**MT 950**|Statement Message|  
|**MT 960**|Request for Service Initiation Message|  
|**MT 961**|Initiation Response Message|  
|**MT 962**|Key Service Message|  
|**MT 963**|Key Acknowledgement Message|  
|**MT 964**|Error Message|  
|**MT 965**|Error in Key Service Message|  
|**MT 966**|Discontinue Service Message|  
|**MT 967**|Discontinuation Acknowledgement Message|  
|**MT 970**|Netting Statement|  
|**MT 971**|Netting Balance Report|  
|**MT 972**|Netting Interim Statement|  
|**MT 973**|Netting Request Message|  
|**MT 985**|Status Enquiry|  
|**MT 986**|Status Report|  
|**MT 990**|Advice of Charges, Interest and Other Adjustments|  
|**MT 991**|Request for Payment of Charges, Interest and Other Expenses|  
|**MT 992**|Request for Cancellation|  
|**MT 995**|Queries|  
|**MT 996**|Answers|  
|**MT 998**|Proprietary Message|  
|**MT 999**|Free Format Message|  
  
 All messages follow the *SWIFT Standards Release Guide 2008* specifications. For more information about the *SWIFT Standards Release Guide*, see the SWIFT Web site at [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).  
  
## See Also  
 [SWIFT Messages](../../adapters-and-accelerators/accelerator-swift/swift-messages.md)