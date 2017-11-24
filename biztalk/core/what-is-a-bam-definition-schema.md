---
title: "What Is a BAM Definition Schema? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definitions [BAM], schemas"
  - "schemas, definitions [BAM]"
  - "code samples, definition schemas [BAM]"
  - "definitions [BAM], code samples"
ms.assetid: 2eefe513-6593-409f-936f-7760e924f605
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is a BAM Definition Schema?
The BAM definition schema defines the structure of the observation model created by the business analyst.  
  
 The schema defines the structure of the BAM definition XML document including the document's elements and subelements. For example, the root element is the BAM definition, and inside the BAM definition there are the following elements:  
  
-   Activities  
  
-   Views  
  
-   Cubes  
  
-   Alerts  
  
> [!NOTE]
>  If the BAM definition XML contains two views and the user only has permission for one of the views, on making a call to **GetViewDefinition**, the user gets back the definition of both views.  
  
 The schema defines the document constraints. The constraints dictate, for example, that some elements can only reference certain other elements.  
  
 You can create an XML file containing the BAM definitions (instances of this schema) with any text editor or by using BAM Add-in for Excel to create a worksheet that can be exported into an XML file by using the BAM add-in export to XML feature .  
  
 Once you define the BAM activities and views, you do not have to manually export the XML file, since the BAM Management utility (bm.exe) can read this spreadsheet and get the XML from it to deploy your infrastructure automatically. The result is another copy of the spreadsheet named \<your workbook name\>_Livedata.xls. You can use this new spreadsheet to connect to your live data source and view the aggregations in PivotTable reports.  
  
> [!NOTE]
>  If you manually export your XML file through the BAM menu item at the top of the spreadsheet and use the BAM Management utility to deploy the exported XML file and not the Microsoft Excel file, then you cannot view your live data using the Office tools.  
  
> [!NOTE]
>  When you export a BAM definition as XML, you cannot export the BAM definition to localhost. For example, trying to export the BAM definition to `\\localhost\C$\definition1.xml` would result in an error.  
>   
>  Similarly, you cannot import a BAM definition from localhost.  
  
> [!NOTE]
>  If you change the activities or views, you need to remove and then redeploy the BAM definition.  
  
 The following file is the BAM definition schema itself:  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM"  
    xmlns:bam="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM"  
    targetNamespace="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM"  
    elementFormDefault="qualified" attributeFormDefault="unqualified">  
  
    <xs:element name="BAMDefinition" type="BAMDefinition">  
        <xs:key name="ActivityName_Key">  
            <xs:selector xpath="bam:Activity" />  
            <xs:field xpath="@Name" />  
        </xs:key>  
        <xs:key name="ViewName_Key">  
            <xs:selector xpath="bam:View" />  
            <xs:field xpath="@Name" />  
        </xs:key>  
        <xs:key name="CubeName_Key">  
            <xs:selector xpath="bam:Cube" />  
            <xs:field xpath="@Name" />  
        </xs:key>  
        <xs:key name="ActivityID_Key">  
            <xs:selector xpath="bam:Activity" />  
            <xs:field xpath="@ID" />  
        </xs:key>  
        <xs:keyref name="ActivityView_ref_ActivityID" refer="ActivityID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView" />  
            <xs:field xpath="@ActivityRef" />  
        </xs:keyref>  
        <xs:key name="ActivityViewID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView" />  
            <xs:field xpath="@ID" />  
        </xs:key>  
        <xs:keyref name="Cube_ref_ActivityViewID" refer="ActivityViewID_Key">  
            <xs:selector xpath="bam:Cube" />  
            <xs:field xpath="@ActivityViewRef" />  
        </xs:keyref>  
        <xs:key name="CheckpointID_Key">  
            <xs:selector xpath="bam:Activity/bam:Checkpoint" />  
            <xs:field xpath="@ID" />  
        </xs:key>  
        <xs:keyref name="CheckpointRef_ref_CheckpointID" refer="CheckpointID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView/bam:Alias/bam:CheckpointRef" />  
            <xs:field xpath="." />  
        </xs:keyref>  
        <xs:key name="AliasID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView/bam:Alias" />  
            <xs:field xpath="@ID" />  
        </xs:key>  
        <xs:keyref name="FromAliasRef_ref_AliasID" refer="AliasID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView/bam:Duration/bam:FromAliasRef" />  
            <xs:field xpath="." />  
        </xs:keyref>  
        <xs:keyref name="ToAliasRef_ref_AliasID" refer="AliasID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView/bam:Duration/bam:ToAliasRef" />  
            <xs:field xpath="." />  
        </xs:keyref>  
        <xs:key name="AliasOrDurationID_Key">  
            <xs:selector xpath="bam:View/bam:ActivityView/bam:Alias|bam:View/bam:ActivityView/bam:Duration" />  
            <xs:field xpath="@ID" />  
        </xs:key>  
        <xs:keyref name="Measure_ref_AliasOrDurationID" refer="AliasOrDurationID_Key">  
            <xs:selector xpath="bam:Cube/bam:Measure" />  
            <xs:field xpath="@AliasRef" />  
        </xs:keyref>  
        <xs:keyref name="DataDimension_ref_AliasOrDurationID" refer="AliasOrDurationID_Key">  
            <xs:selector xpath="bam:Cube/bam:DataDimension/bam:LevelAliasRef" />  
            <xs:field xpath="." />  
        </xs:keyref>  
        <xs:keyref name="TimeDimension_ref_AliasOrDurationID" refer="AliasOrDurationID_Key">  
            <xs:selector xpath="bam:Cube/bam:TimeDimension" />  
            <xs:field xpath="@TimeStampAliasRef" />  
        </xs:keyref>  
        <xs:keyref name="NumericRangeDimension_ref_AliasOrDurationID" refer="AliasOrDurationID_Key">  
            <xs:selector xpath="bam:Cube/bam:NumericRangeDimension" />  
            <xs:field xpath="@NumericAliasRef" />  
        </xs:keyref>  
        <xs:keyref name="ProgressStage_ref_AliasOrDurationID" refer="AliasOrDurationID_Key">  
            <xs:selector xpath=".//bam:ProgressStage" />  
            <xs:field xpath="@TimeStampAliasRef" />  
        </xs:keyref>  
    </xs:element>  
  
    <xs:complexType name="BAMDefinition">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="Activity" type="Activity">  
                <xs:key name="CheckpointName_Key">  
                    <xs:selector xpath="bam:Checkpoint" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
                <xs:key name="IndexName_Key">  
                    <xs:selector xpath="bam:Index" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
                <xs:key name="LocalCheckpointID_Key">  
                    <xs:selector xpath="bam:Checkpoint" />  
                    <xs:field xpath="@ID" />  
                </xs:key>  
                <xs:keyref name="IndexCheckpointRef_ref_localCheckpointID" refer="LocalCheckpointID_Key">  
                    <xs:selector xpath="bam:Index/bam:CheckpointRef" />  
                    <xs:field xpath="." />  
                </xs:keyref>  
            </xs:element>  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="View" type="View">  
                <xs:key name="ActivityViewName_Key">  
                    <xs:selector xpath="bam:ActivityView" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
            </xs:element>  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="Cube" type="Cube">  
                <xs:key name="MeasureName_Key">  
                    <xs:selector xpath="bam:Measure" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
                <xs:key name="DimensionNames_Key">  
                    <xs:selector xpath="bam:DataDimension|bam:TimeDimension|bam:NumericRangeDimension|bam:ProgressDimension" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
                <xs:key name="RangeDimensionName_Key">  
                    <xs:selector xpath="bam:Cube/bam:NumericRangeDimension/bam:Range" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
                <xs:key name="MeasureID_Key">  
                    <xs:selector xpath="bam:Measure" />  
                    <xs:field xpath="@ID" />  
                </xs:key>  
                <xs:keyref name="RTAMeasure_ref_MeasureID" refer="MeasureID_Key">  
                    <xs:selector xpath="bam:RealTimeAggregation/bam:MeasureRef" />  
                    <xs:field xpath="." />  
                </xs:keyref>  
                <xs:key name="DimensionID_Key">  
                    <xs:selector xpath="bam:DataDimension|bam:TimeDimension|bam:NumericRangeDimension|bam:ProgressDimension" />  
                    <xs:field xpath="@ID" />  
                </xs:key>  
                <xs:keyref name="RTADimension_Ref_DimensionID" refer="DimensionID_Key">  
                    <xs:selector xpath="bam:RealTimeAggregation/bam:DimensionRef" />  
                    <xs:field xpath="." />  
                </xs:keyref>  
                <xs:key name="DataDimensionLevel_Key">  
                    <xs:selector xpath="bam:Cube/bam:DataDimension/bam:LevelAliasRef" />  
                    <xs:field xpath="." />  
                </xs:key>  
                <xs:key name="TimeDimensionLevel_Key">  
                    <xs:selector xpath="bam:Cube/bam:TimeDimension/bam:TimeLevel" />  
                    <xs:field xpath="." />  
                </xs:key>  
            </xs:element>  
            <xs:element minOccurs="0" maxOccurs="1" name="Alerts" type="Alerts">  
            </xs:element>  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="Extension" type="Extension">  
            </xs:element>  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="Activity">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1000" name="Checkpoint" type="Checkpoint" />  
            <xs:element minOccurs="0" maxOccurs="245" name="Index" type="Index">  
                <xs:key name="IndexCheckpointRef_Key">  
                    <xs:selector xpath="bam:CheckpointRef" />  
                    <xs:field xpath="." />  
                </xs:key>  
            </xs:element>  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMActivityViewAndRtaName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="Checkpoint">  
        <xs:attribute name="Name" type="BAMSqlObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="DataType" type="CheckpointDataType" use="required" />  
        <xs:attribute name="DataLength" type="xs:positiveInteger" use="optional" />  
    </xs:complexType>  
  
    <xs:complexType name="Index">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="16" name="CheckpointRef" type="xs:NCName" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMSqlObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="View">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="ActivityView" type="ActivityView">  
                <xs:key name="AliasAndDurationName_Key">  
                    <xs:selector xpath="bam:Alias|bam:Duration" />  
                    <xs:field xpath="@Name" />  
                </xs:key>  
            </xs:element>  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMActivityViewAndRtaName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="ActivityView">  
        <xs:choice minOccurs="1" maxOccurs="1000">  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="Alias" type="Alias" />  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="Duration" type="Duration" />  
        </xs:choice>  
        <xs:attribute name="Name" type="BAMActViewName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="ActivityRef" type="xs:NCName" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="Alias">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="CheckpointRef" type="xs:NCName" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAliasName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="Duration">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1" name="FromAliasRef" type="xs:NCName" />  
            <xs:element minOccurs="1" maxOccurs="1" name="ToAliasRef" type="xs:NCName" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMSqlObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="TimeResolution" type="DurationTimeResolution" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="Cube">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="Measure" type="Measure" />  
            <xs:choice minOccurs="1" maxOccurs="unbounded">  
                <xs:element name="DataDimension" type="DataDimension">  
                    <xs:key name="DataDimLevelKey">  
                        <xs:selector xpath="bam:LevelAliasRef" />  
                        <xs:field xpath="." />  
                    </xs:key>  
                </xs:element>  
                <xs:element name="TimeDimension" type="TimeDimension" />  
                <xs:element name="NumericRangeDimension" type="NumericRangeDimension" />  
                <xs:element name="ProgressDimension" type="ProgressDimension">  
                    <xs:key name="ProgressStageName_Key">  
                        <xs:selector xpath=".//bam:ProgressStage" />  
                        <xs:field xpath="@Name" />  
                    </xs:key>  
                </xs:element>  
            </xs:choice>  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="RealTimeAggregation" type="RealTimeAggregation" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="ActivityViewRef" type="xs:NCName" use="required" />  
        <xs:attribute default="true" name="CreateOlapCube" type="xs:boolean" use="optional" />  
    </xs:complexType>  
  
    <xs:complexType name="Alerts">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="ViewAlert" type="ViewAlert" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="Extension">  
        <xs:sequence>  
            <xs:any processContents="skip"/>  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="ViewAlert">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1" name="ViewRef" type="xs:NCName" />  
            <xs:element minOccurs="0" maxOccurs="1" name="ActivityViewRef" type="xs:NCName" />  
            <xs:element minOccurs="0" maxOccurs="1" name="CubeRef" type="xs:NCName" />  
            <xs:element minOccurs="0" maxOccurs="1" name="RtaRef" type="xs:NCName" />  
            <xs:element minOccurs="0" maxOccurs="1" name="PollingInterval" type="TimeDuration" />  
            <xs:element minOccurs="0" maxOccurs="1" name="MaxAlertsPerTimeUnit" type="MaxAlertsPerTimeUnit" />  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="AlertInstance" type="AlertInstance" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="MaxAlertsPerTimeUnit">  
        <xs:simpleContent>  
            <xs:extension base="xs:positiveInteger">  
                <xs:attribute name="TimeUnit" type="TimePartSimple" use="required" />  
            </xs:extension>  
        </xs:simpleContent>  
    </xs:complexType>  
  
    <xs:complexType name="AlertInstance">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1" name="Message" type="BAMAlertMessage" />  
            <xs:choice>  
                <xs:element minOccurs="1" maxOccurs="1" name="AggregationQuery" type="AggregationQuery" />  
                <xs:element minOccurs="1" maxOccurs="1" name="InstanceQuery" type="InstanceQuery" />  
            </xs:choice>  
            <xs:element minOccurs="1" maxOccurs="1" name="Owners" type="Owners" />  
            <xs:element minOccurs="0" maxOccurs="1" name="Subscriptions" type="Subscriptions" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMSqlObjectName" use="required" />  
        <xs:attribute name="Priority" type="AlertPriority" use="required" />  
        <xs:attribute name="Enabled" type="xs:boolean" use="required" />  
        <xs:attribute name="Security" type="xs:NCName" use="required" />  
        <xs:attribute name="CreatedBy" type="xs:token" use="optional" />  
        <xs:attribute name="CreationDate" type="xs:dateTime" use="optional" />  
        <xs:attribute name="LastModifiedDate" type="xs:dateTime" use="optional" />  
        <xs:attribute name="ExtensionRef" type="xs:NCName" use="optional" />  
    </xs:complexType>  
  
    <xs:complexType name="InstanceQuery">  
        <xs:sequence>  
            <xs:element name="SelectClauses" type="SelectClauses" minOccurs="1" maxOccurs="1" />  
            <xs:element name="WhereClauses" type="WhereClauses" minOccurs="1" maxOccurs="1" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="SelectClauses">  
        <xs:sequence>  
            <xs:element name="Column" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="WhereClauses">  
        <xs:sequence>  
            <xs:element name="Filter" minOccurs="0" maxOccurs="unbounded">  
                <xs:complexType>  
                    <xs:attribute name="Field" use="required" type="xs:string" />  
                    <xs:attribute name="Condition" use="required" type="xs:string" />  
                    <xs:attribute name="Value" type="xs:string" use="optional" />  
                    <xs:attribute name="Logic" use="required" type="xs:string" />  
                    <xs:attribute name="TimeUnit" use="optional" type="DurationTimeResolution" />  
                </xs:complexType>  
            </xs:element>  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="AggregationQuery">  
        <xs:sequence>  
            <xs:element name="Threshold" type="Threshold" minOccurs="1" maxOccurs="1" nillable="false" />  
            <xs:element name="SlicerDimensions" type="SlicerDimensions" minOccurs="1" maxOccurs="1" />  
            <xs:element name="TimeWindow" type="TimeWindow" minOccurs="0" maxOccurs="1" nillable="false" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="SlicerDimensions">  
        <xs:sequence>  
            <xs:element name="SlicerDimension" type="SlicerDimension" minOccurs="0" maxOccurs="unbounded" nillable="false" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="SlicerDimension">  
        <xs:sequence>  
            <xs:element name="Level" type="Level" minOccurs="0" maxOccurs="unbounded" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="Level">  
        <xs:simpleContent>  
            <xs:extension base="xs:string">  
                <xs:attribute name="Name" type="SlicerDimLevelName" use="optional" />  
            </xs:extension>  
        </xs:simpleContent>  
    </xs:complexType>  
  
    <xs:complexType name="Threshold">  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="Condition" type="xs:string" use="required" />  
        <xs:attribute name="Value" type="xs:double" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="TimeWindow">  
        <xs:sequence>  
            <xs:element name="TimeWindowDuration" type="TimeDurationSimple" minOccurs="1" maxOccurs="1" nillable="false" />  
            <xs:element name="Increment" type="TimeDurationNoQuarter" minOccurs="1" maxOccurs="1" nillable="false" />  
        </xs:sequence>  
        <xs:attribute name="Enabled" type="xs:boolean" use="required" />  
        <xs:attribute name="TimeDimension" type="xs:string" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="Owners">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="Owner" type="xs:token" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="Subscriptions">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="Subscription" type="Subscription" />  
        </xs:sequence>  
    </xs:complexType>  
  
    <xs:complexType name="Subscription">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1" name="UserName" type="xs:token" />  
            <xs:element minOccurs="0" maxOccurs="1" name="Address" type="xs:string" />  
        </xs:sequence>  
        <xs:attribute name="Type" type="SubscriptionType" use="required" />  
        <xs:attribute name="ID" type="xs:string" use="optional" />  
    </xs:complexType>  
  
    <xs:complexType name="Measure">  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="AliasRef" type="xs:NCName" use="required" />  
        <xs:attribute name="AggregationFunction" type="AggregationFunctionType" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="DataDimension">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="LevelAliasRef" type="xs:NCName" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="TimeDimension">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="TimeLevel" type="TimeLevel" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="TimeStampAliasRef" type="xs:NCName" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="TimeLevel">  
        <xs:simpleContent>  
            <xs:extension base="TimePart">  
                <xs:attribute name="Name" type="BAMToken" use="optional" />  
            </xs:extension>  
        </xs:simpleContent>  
    </xs:complexType>  
  
    <xs:complexType name="NumericRangeDimension">  
        <xs:sequence>  
            <xs:element minOccurs="2" maxOccurs="unbounded" name="Range" type="RangeType" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="NumericAliasRef" type="xs:NCName" use="required" />  
    </xs:complexType>  
    <xs:complexType name="RangeType">  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="From" type="xs:double" />  
        <xs:attribute name="To" type="xs:double" />  
    </xs:complexType>  
  
    <xs:complexType name="ProgressDimension">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="1" name="ProgressStage" type="ProgressStage" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="ProgressStage">  
        <xs:sequence>  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="ProgressStage" type="ProgressStage" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMAnalysisObjectName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
        <xs:attribute name="TimeStampAliasRef" type="xs:NCName" use="required" />  
    </xs:complexType>  
  
    <xs:complexType name="RealTimeAggregation">  
        <xs:sequence>  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="MeasureRef" type="xs:NCName" />  
            <xs:element minOccurs="1" maxOccurs="unbounded" name="DimensionRef" type="xs:NCName" />  
        </xs:sequence>  
        <xs:attribute name="Name" type="BAMActivityViewAndRtaName" use="required" />  
        <xs:attribute name="ID" type="xs:ID" use="required" />  
    </xs:complexType>  
  
    <xs:simpleType name="CheckpointDataType">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="NVARCHAR" />  
            <xs:enumeration value="DATETIME" />  
            <xs:enumeration value="INT" />  
            <xs:enumeration value="FLOAT" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="AggregationFunctionType">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="Sum" />  
            <xs:enumeration value="Count" />  
            <xs:enumeration value="Avg" />  
            <xs:enumeration value="Min" />  
            <xs:enumeration value="Max" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="AlertPriority">  
        <xs:restriction base="xs:positiveInteger">  
            <xs:minInclusive value="1"/>  
            <xs:maxInclusive value="3"/>  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="DurationTimeResolution">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="Day" />  
            <xs:enumeration value="Hour" />  
            <xs:enumeration value="Minute" />  
            <xs:enumeration value="Second" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="TimePart">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="Year" />  
            <xs:enumeration value="Quarter" />  
            <xs:enumeration value="Month" />  
            <xs:enumeration value="Week" />  
            <xs:enumeration value="Day" />  
            <xs:enumeration value="Hour" />  
            <xs:enumeration value="Minute" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="TimePartNoQuarter">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="Year" />  
            <xs:enumeration value="Month" />  
            <xs:enumeration value="Week" />  
            <xs:enumeration value="Day" />  
            <xs:enumeration value="Hour" />  
            <xs:enumeration value="Minute" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="TimePartSimple">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="Week" />  
            <xs:enumeration value="Day" />  
            <xs:enumeration value="Hour" />  
            <xs:enumeration value="Minute" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:complexType name="TimeDuration">  
        <xs:simpleContent>  
            <xs:extension base="xs:integer">  
                <xs:attribute name="Unit" type="TimePart" use="required" />  
            </xs:extension>  
        </xs:simpleContent>  
    </xs:complexType>  
  
    <xs:complexType name="TimeDurationNoQuarter">  
        <xs:simpleContent>  
            <xs:extension base="xs:integer">  
                <xs:attribute name="Unit" type="TimePartNoQuarter" use="required" />  
            </xs:extension>  
        </xs:simpleContent>  
    </xs:complexType>  
  
    <xs:complexType name="TimeDurationSimple">  
        <xs:simpleContent>  
            <xs:extension base="xs:integer">  
                <xs:attribute name="Unit" type="TimePartSimple" use="required" />  
            </xs:extension>  
        </xs:simpleContent>  
    </xs:complexType>  
  
    <xs:simpleType name="BAMSqlObjectName">  
        <xs:restriction base="BAMToken">  
            <xs:minLength value="1" />  
            <xs:maxLength value="100" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="BAMAliasName">  
        <xs:restriction base="BAMToken">  
            <xs:minLength value="1" />  
            <xs:maxLength value="50" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="BAMAnalysisObjectName">  
        <xs:restriction base="BAMToken">  
            <xs:minLength value="1" />  
            <xs:maxLength value="20" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="BAMActivityViewAndRtaName">  
        <xs:restriction base="BAMToken">  
            <xs:minLength value="1" />  
            <xs:maxLength value="48" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="BAMActViewName">  
        <xs:restriction base="BAMToken">  
            <xs:minLength value="1" />  
            <xs:maxLength value="52" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="SubscriptionType">  
        <xs:restriction base="BAMToken">  
            <xs:enumeration value="email" />  
            <xs:enumeration value="file" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="BAMAlertMessage">  
        <xs:restriction base="xs:string">  
            <xs:minLength value="0" />  
            <xs:maxLength value="1024" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="SlicerDimLevelName">  
        <xs:restriction base="xs:string">  
            <xs:pattern value="\(?(\p{Ll}|\p{Lu}|\p{Lo}|\p{Lt}|\p{Nl}|_)([ ]?(_|\p{L}|\p{Nl}|\p{Nd})+)*\)?" />  
            <xs:whiteSpace value="preserve" />  
        </xs:restriction>  
    </xs:simpleType>  
  
    <xs:simpleType name="BAMToken">  
        <xs:restriction base="xs:string">  
            <xs:pattern value="(\p{Ll}|\p{Lu}|\p{Lo}|\p{Lt}|\p{Nl}|_)([ ]?(_|\p{L}|\p{Nl}|\p{Nd})+)*" />  
            <xs:whiteSpace value="preserve" />  
        </xs:restriction>  
    </xs:simpleType>  
  
</xs:schema>  
```  
  
 **Example XML**  
  
 The following example is an XML file that conforms to the BAM definition schema.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<BAM:BAMDefinition xmlns:BAM='urn:schemas-microsoft.com:BAM' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance'>  
   <Activity Name="PurchaseOrder" ID="PurchaseOrder">  
      <Checkpoint Name="POReceived" ID="POReceived" DataType="DATETIME" />  
      <Checkpoint Name="POApproved" ID="POApproved" DataType="DATETIME" />  
      <Checkpoint Name="PODenied" ID="PODenied" DataType="DATETIME" />  
      <Checkpoint Name="POShipped" ID="POShipped" DataType="DATETIME" />  
      <Checkpoint Name="POAmount" ID="POAmount" DataType="FLOAT" />  
      <Checkpoint Name="OrderChannel" ID="OrderChannel" DataType="NVARCHAR" DataLength="30" />  
      <Checkpoint Name="CustomerName" ID="CustomerName" DataType="NVARCHAR" DataLength="50" />  
      <Checkpoint Name="CustomerState" ID="CustomerState" DataType="NVARCHAR" DataLength="20" />  
      <Checkpoint Name="CustomerCity" ID="CustomerCity" DataType="NVARCHAR" DataLength="30" />  
      <Checkpoint Name="ProductName" ID="ProductName" DataType="NVARCHAR" DataLength="50" />  
      <Checkpoint Name="ProductCategory" ID="ProductCategory" DataType="NVARCHAR" DataLength="20" />  
      <Index Name="LocationIndex" ID="LocationIndex">  
         <CheckpointRef>CustomerState</CheckpointRef>  
         <CheckpointRef>CustomerCity</CheckpointRef>  
      </Index>  
      <Index Name="CategoryIndex" ID="CategoryIndex">  
         <CheckpointRef>ProductCategory</CheckpointRef>  
      </Index>  
   </Activity>  
   <View Name="SalesManagerView" ID="SalesManagerView">  
      <ActivityView Name="PurchaseOrderView" ID="PurchaseOrderView" ActivityRef="PurchaseOrder">  
         <Alias Name="POReceivedTime" ID="POReceivedTime">  
            <CheckpointRef>POReceived</CheckpointRef>  
         </Alias>  
         <Alias Name="PODecisionTime" ID="PODecisionTime">  
            <CheckpointRef>POApproved</CheckpointRef>  
            <CheckpointRef>PODenied</CheckpointRef>  
         </Alias>  
         <Alias Name="PODeniedTime" ID="PODeniedTime">  
            <CheckpointRef>PODenied</CheckpointRef>  
         </Alias>  
         <Alias Name="POApprovedTime" ID="POApprovedTime">  
            <CheckpointRef>POApproved</CheckpointRef>  
         </Alias>  
         <Alias Name="POShippedTime" ID="POShippedTime">  
            <CheckpointRef>POShipped</CheckpointRef>  
         </Alias>  
         <Alias Name="POEndedTime" ID="POEndedTime">  
            <CheckpointRef>PODenied</CheckpointRef>  
            <CheckpointRef>POShipped</CheckpointRef>  
         </Alias>  
         <Alias Name="Amount" ID="Amount">  
            <CheckpointRef>POAmount</CheckpointRef>  
         </Alias>  
         <Alias Name="CustomerName" ID="CustomerNameAlias">  
            <CheckpointRef>CustomerName</CheckpointRef>  
         </Alias>  
         <Alias Name="State" ID="State">  
            <CheckpointRef>CustomerState</CheckpointRef>  
         </Alias>  
         <Alias Name="City" ID="City">  
            <CheckpointRef>CustomerCity</CheckpointRef>  
         </Alias>  
         <Alias Name="ProductCategory" ID="Category">  
            <CheckpointRef>ProductCategory</CheckpointRef>  
         </Alias>  
         <Alias Name="ProductName" ID="ProductNameAlias">  
            <CheckpointRef>ProductName</CheckpointRef>  
         </Alias>  
         <Duration Name="POProgressDuration" ID="PODuration" TimeResolution="Hour">  
            <FromAliasRef>POReceivedTime</FromAliasRef>  
            <ToAliasRef>POEndedTime</ToAliasRef>  
         </Duration>  
         <Duration Name="POEvaluationDuration" ID="EvalDuration" TimeResolution="Hour">  
            <FromAliasRef>POReceivedTime</FromAliasRef>  
            <ToAliasRef>PODecisionTime</ToAliasRef>  
         </Duration>  
         <Duration Name="POFulfillmentDuration" ID="FulfillDuration" TimeResolution="Hour">  
            <FromAliasRef>POApprovedTime</FromAliasRef>  
            <ToAliasRef>POShippedTime</ToAliasRef>  
         </Duration>  
      </ActivityView>  
   </View>  
   <Cube Name="POCube" DisplayName="PO Cube" ID="POCube" ActivityViewRef="PurchaseOrderView">  
      <Measure Name="POCount" ID="POCount" AliasRef="Category" AggregationFunction="Count" />  
      <Measure Name="PurchaseAmountTotal" ID="SumPurchaseAmount" AliasRef="Amount" AggregationFunction="Sum" />  
      <Measure Name="PurchaseAmountMax" ID="MaxPurchaseAmount" AliasRef="Amount" AggregationFunction="Max" />  
      <Measure Name="PurchaseAmountMin" ID="MinPurchaseAmount" AliasRef="Amount" AggregationFunction="Min" />  
      <Measure Name="AvgPurchaseAmount" ID="AvgPurchaseAmount" AliasRef="Amount" AggregationFunction="Avg" />  
      <Measure Name="EvalDurationTotal" ID="SumEvalDuration" AliasRef="EvalDuration" AggregationFunction="Sum" />  
      <Measure Name="EvalDurationMin" ID="MinEvalDuration" AliasRef="EvalDuration" AggregationFunction="Min" />  
      <Measure Name="FulfillDurationTotal" ID="SumFulfillDuration" AliasRef="FulfillDuration" AggregationFunction="Sum" />  
      <DataDimension Name="Location" ID="Location">  
         <LevelAliasRef>State</LevelAliasRef>  
         <LevelAliasRef>City</LevelAliasRef>  
      </DataDimension>  
      <DataDimension Name="Product" ID="Product">  
         <LevelAliasRef>Category</LevelAliasRef>  
         <LevelAliasRef>ProductNameAlias</LevelAliasRef>  
      </DataDimension>  
      <TimeDimension Name="POReceivedTime" ID="POStartTimeDim" TimeStampAliasRef="POReceivedTime">  
         <TimeLevel>Year</TimeLevel>  
         <TimeLevel>Month</TimeLevel>  
         <TimeLevel>Day</TimeLevel>  
      </TimeDimension>  
      <NumericRangeDimension Name="POAmountRange" ID="POAmountRange" NumericAliasRef="Amount">  
         <Range Name="SmallPO" ID="range1" To="1000"/>  
         <Range Name="MediumPO" ID="range2" From="1000" To="100000"/>  
         <Range Name="LargePO" ID="range3" From="100000"/>  
      </NumericRangeDimension>  
      <ProgressDimension Name="POState" ID="POState">  
         <ProgressStage Name="POReceived" ID="POReceivedState" TimeStampAliasRef="POReceivedTime">  
            <ProgressStage Name="Evaluating" ID="Evaluating" TimeStampAliasRef="POReceivedTime"/>  
            <ProgressStage Name="Approved" ID="ApprovedState" TimeStampAliasRef="POApprovedTime">  
               <ProgressStage Name="Fulfilllment" ID="FulfillmentState" TimeStampAliasRef="POApprovedTime"/>  
               <ProgressStage Name="Shipped" ID="ShippedState" TimeStampAliasRef="POShippedTime"/>  
            </ProgressStage>  
            <ProgressStage Name="Denied" ID="Denied" TimeStampAliasRef="PODeniedTime"/>  
         </ProgressStage>  
      </ProgressDimension>  
      <RealTimeAggregation Name="POByLocation" ID="POAmountByLocation">  
         <MeasureRef>SumPurchaseAmount</MeasureRef>  
         <MeasureRef>SumEvalDuration</MeasureRef>  
         <MeasureRef>AvgPurchaseAmount</MeasureRef>  
         <MeasureRef>POCount</MeasureRef>  
         <DimensionRef>Location</DimensionRef>  
         <DimensionRef>Product</DimensionRef>  
         <DimensionRef>POStartTimeDim</DimensionRef>  
         <DimensionRef>POAmountRange</DimensionRef>  
         <DimensionRef>POState</DimensionRef>  
      </RealTimeAggregation>  
   </Cube>  
  
    <Alerts>  
        <ViewAlert>  
            <ViewRef>SalesManagerView</ViewRef>           
            <CubeRef>POCube</CubeRef>  
            <PollingInterval Unit="Minute">1</PollingInterval>  
            <MaxAlertsPerTimeUnit TimeUnit="Hour">1</MaxAlertsPerTimeUnit>  
            <AlertInstance Name="PoCountAlert" Priority="1" Enabled="true" Security="public" CreatedBy="" CreationDate="2002-10-10T12:00:00Z" LastModifiedDate="2002-10-10T12:00:00Z" ExtensionRef="PurchaseOrderCube">  
                <Message>Order from Microsoft (WA) has arrived.</Message>  
                <AggregationQuery>  
                    <Threshold Name="POCount" Condition="<" Value="10" />  
                    <SlicerDimensions>  
                        <SlicerDimension Name="Location">  
                            <Level Name="State">WA</Level>  
                            <Level Name="City">Redmond</Level>  
                        </SlicerDimension>   
                        <SlicerDimension Name="Product">  
                            <Level Name="Category">CategoryName</Level>  
                            <Level Name="ProductNameAlias">ProductName</Level>  
                        </SlicerDimension>   
                        <SlicerDimension Name="POAmountRange">  
                            <Level Name="MediumPO"/>  
                        </SlicerDimension>   
                        <SlicerDimension Name="POState">  
                            <Level Name="POReceived"></Level>  
                            <Level Name="Approved"></Level>  
                            <Level Name="Shipped"></Level>  
                        </SlicerDimension>   
                    </SlicerDimensions>  
                    <TimeWindow Enabled="true" TimeDimension="POReceivedTime">  
                        <TimeWindowDuration Unit="Day">1</TimeWindowDuration>  
                        <Increment Unit="Day">1</Increment>  
                    </TimeWindow>  
                </AggregationQuery>  
                <Owners>  
                    <Owner>REDMOND\btslabs</Owner>  
                    <Owner>redmond\owner1</Owner>  
                </Owners>  
                  <Subscriptions>  
                    <Subscription Type="email" ID="">  
                        <UserName>redmond\osubscriber`</UserName>  
                        <Address>email address</Address>  
                    </Subscription>  
                    <Subscription Type="file" ID="">  
                        <UserName>redmond\subscriber2</UserName>  
                    </Subscription>  
                </Subscriptions>  
            </AlertInstance>  
        </ViewAlert>  
        <ViewAlert>  
            <ViewRef>SalesManagerView</ViewRef>   
            <ActivityViewRef>PurchaseOrderView</ActivityViewRef>   
            <PollingInterval Unit="Minute">1</PollingInterval>  
            <MaxAlertsPerTimeUnit TimeUnit="Hour">1</MaxAlertsPerTimeUnit>  
            <AlertInstance Name="alert2" Priority="1" Enabled="true" Security="public" CreatedBy="" CreationDate="2002-10-10T12:00:00Z" LastModifiedDate="2002-10-10T12:00:00Z">  
                <Message>Order from Microsoft (WA) has arrived.</Message>  
                 <InstanceQuery>  
                    <SelectClauses>  
                        <Column>Amount</Column>  
                        <Column>POState</Column>  
                    </SelectClauses>  
                    <WhereClauses>  
                        <Filter Field="Amount" Condition=">" Value="100" Logic="AND" />   
                        <Filter Field="State" Condition="=" Value="WA" Logic="AND"/>   
                    </WhereClauses>  
                <Owners>  
                    <Owner>REDMOND\btslabs</Owner>  
                    <Owner>redmond\owener1</Owner>  
                </Owners>  
                <Subscriptions>  
                    <Subscription Type="email" ID="">  
                        <UserName>redmond\subscriber2</UserName>  
                        <Address>email address</Address>  
                    </Subscription>  
                    <Subscription Type="file" ID="">  
                        <UserName>redmond\subscriber3</UserName>  
                    </Subscription>  
                </Subscriptions>  
            </AlertInstance>  
        <AlertInstance Name="Alert3" Priority="1" Enabled="true" Security="public" CreatedBy="" CreationDate="2002-10-10T12:00:00Z" LastModifiedDate="2002-10-10T12:00:00Z">  
            <Message>Order from Microsoft (WA) has arrived.</Message>  
            <InstanceQuery>  
                <SelectClauses>  
                    <Column>Amount</Column>  
                    <Column>POState</Column>  
                </SelectClauses>  
                <WhereClauses>  
                    <Filter Field="Amount" Condition=">" Value="100" Logic="AND" />   
                    <Filter Field="State" Condition="=" Value="WA" Logic="AND"/>   
                </WhereClauses>  
            </InstanceQuery>  
            <Owners>  
                <Owner>REDMOND\owner2</Owner>  
            </Owners>  
            <Subscriptions>  
                <Subscription Type="email" ID="">  
                    <UserName>redmond\subscriber1</UserName>  
                    <Address>email address</Address>  
                </Subscription>  
                <Subscription Type="file" ID="">  
                    <UserName>redmond\subscriber2</UserName>  
                </Subscription>  
            </Subscriptions>  
        </AlertInstance>  
        </ViewAlert>  
    </Alerts>  
</BAM:BAMDefinition>  
```  
  
## See Also  
 [BAM Configuration Schema](../core/bam-configuration-schema.md)   
 [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md)