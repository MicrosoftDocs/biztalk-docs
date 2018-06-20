---
title: "Composed Message Processor (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, examples"
  - "messages, processing"
  - "messages, aggregated"
  - "examples, pipelines"
ms.assetid: a0f87f98-6f5f-4edb-8f65-49d22df5de97
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Composed Message Processor (BizTalk Server Sample)
The purpose of this sample is to build a composed message processor application that processes individual line items from aggregated messages.  
  
 Specifically we will build an orchestration schedule that:  
  
1. Receives a batched interchange message consisting of multiple purchase orders.  
  
2. Disassembles the interchange message into individual purchase order documents.  
  
3. Processes each document – converts each purchase order into an invoice message.  
  
4. Assembles all the invoice messages into a batched interchange.  
  
   Step #3 is simplified for the sample purposes. For example, in more complex applications, an orchestration may send disassembled purchase orders to different back-end inventory systems and then after collecting all the responses, aggregate them into one batched invoice message.  
  
   For more information on the composed message processor pattern refer to [1].  
  
## What This Sample Does  
 There are two projects within the sample solution, both of which are described in detail in the following sections.  
  
### Pipelines and Schemas  
 Pipelines and schemas project contains:  
  
-   Flat file schemas for input purchase order interchange and for output invoice interchange.  
  
-   Map to transform purchase order document into an invoice document.  
  
-   Receive and send pipelines.  
  
#### Flat File Schemas For Input and Output Interchanges  
 Our sample application will be working with the interchanges in the flat file format. Below are the examples of the purchase order interchange and invoice interchange:  
  
 Purchase order interchange (CMPInput.txt):  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
PO1999-10-21  
US    John Dow       123 Elm Street      Mill Valley    CA 90952  
US    July Dow       8 Pine Avenue       Old Town       PA 95819  
Please ship it urgent!  
ITEMS,ITEM398-BB|Tire|4|324.99|Wrap them up nicely,ITEM201-BB|Engine Oil|1|12.99|SAE10W30|1999-05-22  
PO1999-10-23  
US    John Connor    123 Cedar Street    Mill Valley    CA 90952  
US    Sarah Connor   8 Grass Avenue      Old Town       PA 95819  
Use cheapest shipping method.  
ITEMS,ITEM101-TT|Plastic flowers|10|4.99|Fragile handle with care,ITEM202-RR|Fertilizer|1|10.99|Lawn fertilizer,ITEM453-XS|Weed killer|1|5.99|Lawn weed killer|1999-05-25  
```  
  
 The interchange, or purchase order document, has a header that identifies what type of the documents it contains:  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
```  
  
 This interchange consist of three purchase order documents. One instance consists of the information shown below. As you can see, it contains such information as address for billing and shipping as well as the list of items that were ordered.  
  
```  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
```  
  
 The invoice interchange we want to generate for this should look like the following:  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
INVOICE1999-10-21  
BILLTO,US,John Dow,123 Elm Street,Mill Valley,CA,90952  
398-BB    Tire              4    324.99    Wrap them up nicely  
201-BB    Engine Oil        1    12.99     SAE10W30  
INVOICE1999-10-20  
BILLTO,US,John Connor,123 Cedar Street,Mill Valley,CA,90952  
101-TT    Plastic flowers   10   4.99      Fragile handle with care  
202-RR    Fertilizer        1    10.99     Lawn fertilizer  
453-XS    Weed killer       1    5.99      Lawn weed killer  
```  
  
 This interchange contains a subset of information that was in purchase order interchange and also the format of the interchange as well as format of the header are different.  
  
 The header is as follows:  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
```  
  
 And the document instance includes the following:  
  
```  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
```  
  
 First thing we need to create flat file schemas for:  
  
- Purchase order document (PO.xsd)  
  
- Invoice document (Invoice.xsd)  
  
- Purchase order header (POHeader.xsd)  
  
- Invoice header (InvoiceHeader.xsd)  
  
  For this sample, we are not going to explain the process of creating flat file schemas. To learn how to create flat file schemas from document instances, refer to the "Creating flat file schemas from document instance" documentation section.  
  
#### Map to Transform Purchase Order Document Into Invoice Document  
 The map (PO2Invoice.btm) transforms an instance of the purchase order into an invoice document.  
  
#### Receive and Send Pipelines  
 The receive pipeline (FFReceivePipeline.btp) contains a flat file disassembler component that is used to process a purchase order interchange. In particular, for the interchange in file CMPInput.txt, it removes the interchange header and produces three XML documents corresponding to three purchase orders.  
  
 The flat file disassembler in the receive pipeline is configured as shown:  
  
- **Document schema:** PipelinesAndSchemas.PO  
  
- **Header schema:** PipelinesAndSchemas.POHeader  
  
- **Preserve header:** False  
  
- **Recoverable interchange:** False  
  
- **Trailer schema:** (None)  
  
- **Validate document structure:** False  
  
  The send pipeline (FFSendPipeline.btp) contains a flat file assembler component that is used to create aggregated invoice interchange.  
  
  The flat file assembler in send pipeline is configured as shown:  
  
- **Document schema:** PipelinesandSchemas.Invoice  
  
- **Header schema:** PipelinesAndSchemas.InvoiceHeader  
  
- **Preserve byte order mark:** False  
  
- **Target charset:** (None)  
  
- **Trailer schema:** (None)  
  
### Orchestration Schedule  
 Orchestration schedule (CMP.odx) is where all the main processing happens. Specifically the following actions are performed:  
  
-   Receive pipeline is executed to disassemble purchase order interchange  
  
-   Every output message of receive pipeline is transformed  
  
-   Send pipeline is executed to assemble an invoice interchange  
  
#### Creating Orchestration Schedule and Defining Global Variables  
 Our orchestration will receive a flat file interchange as an input and will send a flat file interchange as an output. Because of that, we need to define input and output messages (called InputInterchange and OutputInterchange respectively) as type agnostic (i.e. having type of System.Xml.XmlDocument).  
  
 Also, we need to define an atomic scope where we will process messages. This is required because the receive pipeline can be executed within atomic scope.  
  
#### Executing Receive Pipeline  
 As a next step, we will add logic to execute a receive pipeline for the message that was received in orchestration. To do this, first we declare a variable (called RcvPipeOutput) of type Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages within the scope. This variable is an enumerator that allows us to cycle through the receive pipeline output messages. Note that in order to access this type, as well as all the other types for execution of pipelines from orchestration, you need to add references to the following assemblies:  
  
- Microsoft.XLANGs.Pipeline.dll  
  
- Microsoft.BizTalk.Pipeline.dll  
  
  There is no guarantee that the receive pipeline will always execute successfully. Sometimes messages may be malformed, which would cause the pipeline processing to fail. When a pipeline fails execution in the orchestration, there is an exception thrown that can be caught and the error handling logic can be performed. In order for us to catch the exception thrown by pipeline, we need to execute the pipeline within a non-atomic scope with an exception handling. The actual code to execute pipeline is invoked from an expression shape within that scope.  
  
  In the ExecuteRcvPipe expression shape, write the following line of code to execute the receive pipeline:  
  
```  
RcvPipeOutput = Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteReceivePipeline(typeof(PipelinesAndSchemas.FFReceivePipeline), InputInterchange);  
```  
  
 Let's analyze this line of code in more detail. As you can see, we call a static method ExecuteReceivePipeline that takes as a parameter a type of receive pipeline to execute and an input message. As a result, it produces an enumerator object with the set of output messages. The result is assigned to a variable of type ReceivePipelineOutputMessages that was defined in this scope before.  
  
 We have also included an exception handling block for the pipeline execution scope. This block catches the exception of type XLANGPipelineManagerException and then for simplicity reasons just terminates an orchestration instance with customized error message.  
  
 In more complex scenarios, additional error handling can be performed here, such as generation or the error notification message and sending it to a business user or administrator using email.  
  
#### Transforming Pipeline Output Messages  
 After the pipeline has been executed and the set of disassembled messages has been produced, we need to transform each output message into a different format.  
  
 To use transformation in orchestration we need to define two messages – transformation input and output. We will define those messages within the atomic scope. The transformation input message called TmpMessageIn will be of type PipelinesAndSchemas.PO. The transformation output message called TmpMessageOut will be of type PipeliensAndSchemas.Invoice. We will apply the map PO2Invoice.btm that is defined in project PipelinesAndSchemas.  
  
 As we want to map each pipeline output message we need to perform transformation in the loop. We will use a loop shape with the condition for exiting as below:  
  
```  
RcvPipeOutput.MoveNext()  
```  
  
 MoveNext() method is a standard method of IEnumerator .NET interface that allows to move within the collection of pipeline output messages. When it reaches the end of collection it returns false.  
  
 The first construct shape is used to construct an orchestration message TmpMessageIn out of the pipeline output message.  
  
 The code in the construct shape:  
  
```  
TmpMessageIn = null;  
RcvPipeOutput.GetCurrent(TmpMessageIn);  
```  
  
 In this code we first initialize orchestration message to null and then set it to the current message from the pipeline output messages collection.  
  
 In second construct shape the actual transformation of the TmpMessageIn is performed and the TmpMessageOut of type PipelinesAndSchemas.Invoice is constructed.  
  
#### Executing Send Pipeline  
 Last processing step in orchestration is to execute flat file send pipeline to assemble all the transformed xml messages into one flat file interchange.  
  
 In order to execute a send pipeline we need to use a variable of type Microsoft.XLANGs.Pipeline.SendPipelineInputMessages called SendPipeInput that will hold a collection of orchestration messages that need to be processed in a send pipeline.  
  
 In the last expression of the loop where we performed transformation we will write a code that will add each transformed message to a message collection for send pipeline:  
  
```  
SendPipeInput.Add(TmpMessageOut);  
```  
  
 Similar to the part where we execute receive pipeline the code for execution of send pipeline is placed within a non-atomic scope with exception handling block. The send pipeline execution code is located in the message assignment shape of the construct block.  
  
```  
OutputInterchange = null;  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(typeof(PipelinesAndSchemas.FFSendPipeline), SendPipeInput, OutputInterchange);  
```  
  
 The construct block is used to construct type agnostic (i.e. System.Xml.XmlDocument) pipeline output message OutputInterchange. Then in the message assignment shape the newly constructed message is initialized to null. After that the static method ExecuteSendPipeline is invoked to execute a send pipeline. This method takes as a parameter a type of the send pipeline to execute, the input message and the reference to output message where the pipeline output will be stored.  
  
 As with the execution of the receive pipeline, here we also have an exception handling block for the pipeline execution scope. This block catches the exception of type XLANGPipelineManagerException and then for simplicity reasons just terminates an orchestration instance with customized error message.  
  
## Where to Find This Sample  
 The following table lists the files for this sample.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache (GAC).<br /><br /> Removes send and receive ports.<br /><br /> Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|ComposedMessageProcessor.sln|Visual Studio solution file for the sample.|  
|ComposedMessageProcessorBinding.xml|Binding file for the sample.|  
|Setup.bat|Used to build and initialize this sample.|  
|In Orchestration folder:<br /><br /> CMP.odx|Orchestration that runs the receive pipeline to disassembler message, transforms each disassembled message and then runs send pipeline to assemble messages into an interchange.|  
|In Orchestration folder:<br /><br /> Orchestration.btproj|BizTalk project for orchestration.|  
|In Orchestration folder:<br /><br /> SuspendMessage.odx|Orchestration used for suspending messages that fail pipeline processing.|  
|In PipelinesAndSchemas folder:<br /><br /> CMPInput.xml, CMPOutput.xml|Input and output document instances for the sample.|  
|In PipelinesAndSchemas folder:<br /><br /> FFReceivePipeline.btp, FFSendPipeline.btp|Receive and send pipelines with flat file components. These pipelines are run within orchestration.|  
|In PipelinesAndSchemas folder:<br /><br /> Invoice.xsd, InvoiceHeader.xsd|Flat file schemas for the output document and header.|  
|In PipelinesAndSchemas folder:<br /><br /> PO.xsd, POHeader.xsd|Flat file schemas for the input document and header.|  
|In PipelinesAndSchemas folder:<br /><br /> PropertySchema.xsd|Property schema for the sample.|  
  
## Building and Initializing the Sample  
 Use the following procedure to build and initialize the Compose sample.  
  
#### To build and initialize the Compose sample  
  
1.  In a command window, navigate to the following folder:  
  
     \<Samples Path\>\Pipelines\ComposedMessageProcessor  
  
2.  Run the file Setup.bat, which performs the following actions:  
  
    -   Creates the input (In) and output (Out) folders for this sample in the folder:  
  
         \<Samples Path\>\Pipelines\ComposedMessageProcessor  
  
    -   Compiles the Visual Studio projects for this sample.  
  
    -   Creates a new application called "CMP Sample" and deploys the sample assemblies into it.  
  
    -   Creates and binds the BizTalk Server receive location, and the send and receive ports.  
  
    -   Enlists and starts orchestration, enables the receive location, and starts the send port.  
  
         If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair is used to sign the resulting assemblies.  
  
3.  Before attempting to run this sample, confirm that BizTalk Server did not report any errors during the build and initialization process.  
  
     To undo changes made by Setup.bat, you must do the following:  
  
    1.  Stop and restart the host instance from the BizTalk Server Administration console.  
  
    2.  Run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running the sample  
 Use the following procedure to run the ComposedMessageProcessor sample.  
  
#### To run the ComposedMessageProcessor sample  
  
1.  Copy the text file CMPInput.txt located in the PipelinesAndSchemas folder. Paste the file into the folder In.  
  
2.  Observe the text file created in the folder Out. This file contains the same records as the CMPInput.txt, but the format of data in the file is different.  
  
     As the message passes through the BizTalk Server, the following happens:  
  
    1.  The message gets disassembled and converted into XML messages. Each message is mapped to a different format.  
  
    2.  All mapped messages are assembled together and converted into the flat file format.  
  
## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)