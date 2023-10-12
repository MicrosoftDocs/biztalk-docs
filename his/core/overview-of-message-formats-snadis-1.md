---
description: "Learn more about: Overview of Message Formats (SNADIS)"
title: "Overview of Message Formats (SNADIS)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Overview of Message Formats (SNADIS)
A message always contains fixed-format header information such as a message type and addressing information. It can also contain other header information specific to a particular message type (such as the message subtype) and an indefinite amount of extra data.  
  
 Messages are saved in buffers that consist of one header and zero or more elements:  
  
- The header contains the fixed-format information and a pointer to an element. (This pointer will be NULL if there are no elements associated with the message.)  
  
- An element contains any extra data for a message and a pointer to another element if the data continues into another element.  
  
  Buffer headers and elements are regarded as contiguous (8-bit) byte sequences. Messages of any length can be built up by chaining sufficient elements to a header.  
  
  The following figure shows a typical message with two elements.  
  
  ![Image that shows a typical message with two elements.](../core/media/his-dev1d.gif "his_dev1d")  
  Typical message with two elements
