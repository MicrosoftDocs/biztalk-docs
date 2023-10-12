---
description: "Learn more about: Creating a Partitioned View in the Archiving Database"
title: "Creating a Partitioned View in the Archiving Database"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating a Partitioned View in the Archiving Database

When you run the BAM data maintenance package (BAM_DM_`<activity name>`) BAM copies each partition in the BAM Primary Import database to a separate table in the BAM Archive database. If you detach the archive database and reattach it for querying, it will be difficult to locate the data for your query.

You can create partitioned views in the BAM Archive database to facilitate locating the data. BAM supports up to 253 partitions. For each activity, BAM generates one BAM data maintenance DTS package, which copies the activity data to the BAM Archive database and then removes it from the BAM Primary Import database. If the archive database fails after the data is copied but before the next backup, data is lost.

The solution to prevent lost data is to have a single archiving package, which first copies the old data from all activities, then backs up the BAM Archive database, and finally drops the partitions that were copied from the BAM Primary Import database.

## Prerequisites

You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.

## Create a partitioned view in the BAM Archive database (SQL Server 2008 SP1 or SQL Server 2008 R2)

1. Open SQL Server Management Studio.

2. Select the BAM Archive database, and then click **New Query**.

3. On the **Query** menu, point to **Results To** and then click **Results to Text**.

4. Copy the following SQL script into the query pane. Replace \<activity name\> with your activity name, and replace `<view type>` with either **Instances** for instance view or **Relationships** for relationship view.

    ```sql
    set nocount on

    declare @activityName as nvarchar(128)
    declare @viewType as nvarchar(50)
    set @activityName = N'<activity name>'-- Substitute your activity name here
    set @viewType = N'<view type>'-- Substitute the view type here, either "Instances" or "Relationships"

    declare @tableName nvarchar(128)
    declare @viewName nvarchar(128)
    declare @isFirstTable bit
    declare @scriptLine nvarchar(300)

    set @viewName = N'bam_' + @activityName + '_' + @viewType + 'View'
    select N'SELECT Name FROM sysobjects where name = N''' + @viewName + ''' and type = ''V'''
     + char(13) + char(10) + 'IF @@ROWCOUNT > 0 DROP VIEW ' + @viewName
     + char(13) + char(10) + 'GO'

    select 'CREATE VIEW ' +  @viewName + ' AS ' + char(13) + char(10)

    declare instance_cursor cursor local for
    select name from sysobjects
    where name like N'bam_' + @activityName + '_' + @viewType + '_%' and type = 'U'

    SET @isFirstTable = 1
    OPEN instance_cursor
    FETCH NEXT FROM instance_cursor INTO @tableName

    WHILE @@fetch_status = 0
    BEGIN

    if @isFirstTable = 1
    BEGIN
    SET @scriptLine = N'SELECT * FROM [' + @tableName + ']'
    SET @isFirstTable = 0
    END
    ELSE
    SET @scriptLine = N'UNION ALL SELECT * FROM [' + @tableName + ']'

    SELECT @scriptLine

    FETCH NEXT FROM instance_cursor INTO @tableName
    END
    CLOSE instance_cursor
    DEALLOCATE instance_cursor

    select 'GO'
    set nocount off
    ```

5. Execute the query.

## See Also

- [BAM DTS Packages](../core/bam-dts-packages.md)
- [How to Back Up the BAM Analysis and Tracking Analysis Server Databases](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)
