---
title: "Common Schema Collections for the Host File System1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3721784-6aa7-464d-b3c8-488c29ba3abe
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Common Schema Collections for the Host File System
The common schema collection is the schema collection that is implemented by the Managed Provider for Host Files. You can query the managed provider to determine the list of supported schema collections by calling the `GetSchema` method with no arguments, or with the schema collection name "MetaDataCollections". This returns a `DataTable` object with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.  

 The following tables describe the common schema collections for the Host File System.  

 **Columns**  

|Column Name|Data Type|Description|  
|-----------------|---------------|-----------------|  
|table_catalog|String|Catalog of the table.|  
|table_schema|String|Schema that contains the table.|  
|table_name|String|Table name.|  
|column_name|String|Column name.|  
|ordinal_position|Int16|Column identification number.|  
|column_default|String|Default value of the column|  
|is_nullable|String|Nullability of the column. If this column allows NULL, this column returns YES. Otherwise, No is returned.|  
|data_type|String|System-supplied data type.|  
|character_maximum_length|Int32 – Sql8, Int16 – Sql7|Maximum length, in characters, for binary data, character data, or text and image data. Otherwise, NULL is returned.|  
|character_octet_length|Int32 – SQL8, Int16 – Sql7|Maximum length, in bytes, for binary data, character data, or text and image data. Otherwise, NULL is returned.|  
|numeric_precision|Unsigned Byte|Precision of approximate numeric data, exact numeric data, integer data, or monetary data. Otherwise, NULL is returned.|  
|numeric_precision_radix|Int16|Precision radix of approximate numeric data, exact numeric data, integer data, or monetary data. Otherwise, NULL is returned.|  
|numeric_scale|Int32|Scale of approximate numeric data, exact numeric data, integer data, or monetary data. Otherwise, NULL is returned.|  
|datetime_precision|Int16|Subtype code for datetime and SQL-92 interval data types. For other data types, NULL is returned.|  
|character_set_catalog|String|Returns master, indicating the database in which the character set is located, if the column is character data or text data type. Otherwise, NULL is returned.|  
|character_set_schema|String|Always returns NULL.|  
|character_set_name|String|Returns the unique name for the character set if this column is character data or text data type. Otherwise, NULL is returned.|  
|collation_catalog|String|Returns master, indicating the database in which the collation is defined, if the column is character data or text data type. Otherwise, this column is NULL.|  

 **DataSourceInformation**  


|                                     |                        |                                                                                                                                                                                                                                                        |
|-------------------------------------|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CompositeIdentifierSeparatorPattern |         string         |                                                 The regular expression to match the composite separators in a composite identifier. For example, “\\.” (for SQL Server) or “@&#124;\\.” (for Oracle).                                                  |
|                                     |                        |                                                            A composite identifier is typically what is used for a database object name, for example: pubs.dbo.authors or pubs@dbo.authors.                                                             |
|                                     |                        |                                                                                 For SQL Server, use the regular expression “\\.”. For OracleClient, use “@&#124;\\.”.                                                                                  |
|                                     |                        |                                                                                                                                                                                                                                                        |
|                                     |                        |                                                                                       For OLE DB use DBLITERAL_CATALOG_SEPARATOR or DBLITERAL_SCHEMA_SEPARATOR.                                                                                        |
|        DataSourceProductName        |         string         |                                                                                   The name of the product accessed by the provider, such as "Oracle" or "SQLServer".                                                                                   |
|      DataSourceProductVersion       |         string         |                                                                  The version of the product accessed by the provider, in the data sources native format and not in Microsoft format.                                                                   |
|                                     |                        |                In some cases DataSourceProductVersion and DataSourceProductVersionNormalized are the same value. With OLE DB, these are always the same because they are mapped to the same function call in the underlying native API.                |
| DataSourceProductVersionNormalized  |         string         |         A normalized version for the data source, such that it can be compared with `String.Compare()`. The format of this is consistent for all versions of the provider to prevent version 10 from sorting between version 1 and version 2.          |
|                                     |                        |              For example, the Oracle provider uses a format of “nn.nn.nn.nn.nn” for its normalized version, which causes an Oracle 8i data source to return “08.01.07.04.01”. SQL Server uses the typical Microsoft “nn.nn.nnnn” format.               |
|                                     |                        |         In some cases, DataSourceProductVersion and DataSourceProductVersionNormalized will be the same value. In the case of OLE DB, these will always be the same as they are mapped to the same function call in the underlying native API.         |
|           GroupByBehavior           |    GroupByBehavior     |                                                                 Specifies the relationship between the columns in a GROUP BY clause and the non-aggregated columns in the select list.                                                                 |
|          IdentifierPattern          |         String         |                                                                 A regular expression that matches an identifier and has a match value of the identifier. For example “[A-Za-z0-9_#$]”.                                                                 |
|           IdentifierCase            |     IdentifierCase     |                                                                                        Indicates whether non-quoted identifiers are treated as case sensitive.                                                                                         |
|       OrderByColumnsInSelect        |          bool          |         Specifies whether columns in an ORDER BY clause must be in the select list. A value of true indicates that they are required to be in the select list, a value of false indicates that they are not required to be in the select list.         |
|        ParameterMarkerFormat        |         string         |                                                                                               A format string that represents how to format a parameter.                                                                                               |
|                                     |                        |                                                   If named parameters are supported by the data source, the first placeholder in this string should be where the parameter name should be formatted.                                                   |
|                                     |                        |                            For example, if the data source expects parameters to be named and prefixed with an ‘:’ this would be “:{0}”. When formatting this with a parameter name of “p1” the resulting string is “:p1”.                             |
|                                     |                        |                         If the data source expects parameters to be prefixed with the ‘@’, but the names already include them, this would be ‘{0}’, and the result of formatting a parameter named “@p1” would just be “@p1”.                          |
|                                     |                        |                     For data sources that do not expect named parameters and expect the use of the ‘?’ character, the format string can be specified as just ‘?’, which would ignore the parameter name. For OLE DB we return ‘?’.                     |
|       ParameterMarkerPattern        |         string         |                                                                       A regular expression that matches a parameter marker. It has a match value of the parameter name, if any.                                                                        |
|                                     |                        |                                            For example, if named parameters are supported with an ‘@’ lead-in character that will be included in the parameter name, this would be: “(@[A-Za-z0-9_$#]\*)”.                                             |
|                                     |                        |                                             However, if named parameters are supported with a ‘:’ as the lead-in character and it is not part of the parameter name, this would be: “:([A-Za-z0-9_$#]\*)”.                                             |
|                                     |                        |                                                                                Of course, if the data source does not support named parameters, this would just be “?”.                                                                                |
|       ParameterNameMaxLength        |          int           |                                     The maximum length of a parameter name in characters. Visual Studio expects that if parameter names are supported, the minimum value for the maximum length is 30 characters.                                      |
|                                     |                        |                                                                                   If the data source does not support named parameters, this property returns zero.                                                                                    |
|        ParameterNamePattern         |         string         |                                        A regular expression that matches the valid parameter names. Different data sources have different rules regarding the characters that may be used for parameter names.                                         |
|                                     |                        |                        Visual Studio expects that if parameter names are supported, the characters "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" are the minimum supported set of characters that are valid for parameter names.                        |
|       QuotedIdentifierPattern       |         string         | A regular expression that matches a quoted identifier and has a match value of the identifier itself without the quotes. For example, if the data source uses double-quotes to identify quoted identifiers, this would be: "(([^\\"]&#124;\\"\\")\*)". |
|        QuotedIdentifierCase         |     IdentifierCase     |                                                                                          Indicates whether quoted identifiers are treated as case sensitive.                                                                                           |
|      StatementSeparatorPattern      |         string         |                                                                                               A regular expression that matches the statement separator.                                                                                               |
|        StringLiteralPattern         |         string         |                     A regular expression that matches a string literal and has a match value of the literal itself. For example, if the data source used single-quotes to identify strings, this would be: "('([^']&#124;'')\*')"'                     |
|       SupportedJoinOperators        | SupportedJoinOperators |                                                                                     Specifies what types of SQL join statements are supported by the data source.                                                                                      |

 **DataTypes**  

|Column Name|Data Type|Description|  
|-----------------|---------------|-----------------|  
|TypeName|string|The provider-specific data type name.|  
|ProviderDbType|int|The provider-specific type value that should be used when specifying a parameter’s type. For example, `SqlDbType.Money` or `OracleType.Blob`.|  
|ColumnSize|long|The length of a non-numeric column or parameter refers to either the maximum or the length defined for this type by the provider.|  
|||For character data, this is the maximum or defined length in units, defined by the data source. Oracle has the concept of specifying a length and then specifying the actual storage size for some character data types. This defines only the length in units for Oracle.|  
|||For date-time data types, this is the length of the string representation (assuming the maximum allowed precision of the fractional seconds component).|  
|||If the data type is numeric, this is the upper bound on the maximum precision of the data type.|  
|CreateFormat|string|Format string that represents how to add this column to a data definition statement, such as CREATE TABLE. Each element in the `CreateParameter` array should be represented by a “parameter marker” in the format string.|  
|||For example, the SQL data type DECIMAL needs a precision and a scale. In this case, the format string would be “DECIMAL({0},{1})”.|  
|CreateParameters|string|The creation parameters that must be specified when creating a column of this data type. Each creation parameter is listed in the string, separated by a comma in the order they are to be supplied.|  
|||For example, the SQL data type DECIMAL needs a precision and a scale. In this case, the creation parameters should contain the string “precision, scale”.|  
|||In a text command to create a DECIMAL column with a precision of 10 and a scale of 2, the value of the CreateFormat column might be DECIMAL({0},{1})” and the complete type specification would be DECIMAL(10,2).|  
|DataType|string|The name of the .NET Framework type of the data type.|  
|IsAutoincrementable|bool|`true`—Values of this data type may be auto-incrementing.|  
|||`false`—Values of this data type may not be auto-incrementing.|  
|||Note that this merely indicates whether a column of this data type may be auto-incrementing, not that all columns of this type are auto-incrementing.|  
|IsBestMatch|Bool|`true`—The data type is the best match between all data types in the data store and the .NET Framework data type indicated by the value in the DataType column.|  
|||`false`—The data type is not the best match.|  
|||For each set of rows in which the value of the DataType column is the same, the IsBestMatch column is set to true in only one row.|  
|IsCaseSensitive|bool|`true`—The data type is a character type and is case sensitive.<br /><br /> `false`—The data type is not a character type or is not case sensitive.|  
|IsFixedLength|bool|`true`—Columns of this data type created by the data definition language (DDL) are of fixed length.<br /><br /> `false`—Columns of this data type created by the DDL are of variable length.<br /><br /> `DBNull.Value`—It is not known whether the provider will map this field with a fixed-length or variable-length column.|  
|IsFixedPrecisionScale|bool|`true`—The data type has a fixed precision and scale.<br /><br /> `false`—The data type does not have a fixed precision and scale.|  
|IsLong|bool|`true`—The data type contains very long data; the definition of very long data is provider-specific.<br /><br /> `false`—The data type does not contain very long data.|  
|IsNullable|bool|`true`—The data type is nullable.<br /><br /> `false`—The data type is not nullable.<br /><br /> `DBNull.Value`—It is not known whether the data type is nullable.|  
|IsSearchable|bool|`true`—The data type can be used in a WHERE clause with any operator except the LIKE predicate.<br /><br /> `false`—The data type cannot be used in a WHERE clause with any operator except the LIKE predicate.|  
|IsSearchableWithLike|bool|`true`—The data type can be used with the LIKE predicate.<br /><br /> `false`—The data type cannot be used with the LIKE predicate.|  
|IsUnsigned|bool|`true`—The data type is unsigned.<br /><br /> `false`—The data type is signed.<br /><br /> `DBNull.Value`—Not applicable to data type.|  
|MaximumScale|short|If the type indicator is a numeric type, this is the maximum number of digits allowed to the right of the decimal point. Otherwise, this is `DBNull.Value`.|  
|MinimumScale|short|If the type indicator is a numeric type, this is the minimum number of digits allowed to the right of the decimal point. Otherwise, this is `DBNull.Value`.|  
|IsConcurrencyType|bool|`true`–The data type is updated by the database every time the row is changed and the value of the column is different from all previous values<br /><br /> `false`–The data type is note updated by the database every time the row is changed<br /><br /> `DBNull.Value`–The database does not support this data type.|  
|IsLiteralsSupported|bool|`true`–The data type can be expressed as a literal.<br /><br /> `false`–The data type cannot be expressed as a literal.|  
|LiteralPrefix|string|The prefix applied to a given literal.|  
|LitteralSuffix|string|The suffix applied to a given literal.|  
|NativeDataType|String|An OLE DB-specific column for exposing the OLE DB type of the data type .|  

 **MetaDataCollections**  

|Column Name|Data Type|Description|  
|-----------------|---------------|-----------------|  
|CollectionName|string|The name of the collection to pass to the `GetSchema` method to return the collection.|  
|NumberOfRestriction|int|The number of restrictions that can be specified for the collection.|  
|NumberOfIdentifierParts|int|The number of parts in the composite identifier/database object name. For example, in SQL Server, this would be 3 for tables and 4 for columns. In Oracle, it would be 2 for tables and 3 for columns.|  


 **Restrictions**  

|Column Name|Data Type|Description|  
|-----------------|---------------|-----------------|  
|CollectionName|string|The name of the collection that these restrictions apply to.|  
|RestrictionName|string|The name of the restriction in the collection.|  
|RestrictionDefault|string|Ignored.|  
|RestrictionNumber|int|The actual location in the collections restrictions that this particular restriction falls in.|  

 **Tables**  

|Column Name|Data Type|Description|  
|-----------------|---------------|-----------------|  
|table_catalog|String|Catalog of the table.|  
|table_schema|String|Schema that contains the table.|  
|table_name|String|Table name.|  
|table_type|String|Type of table. Can be VIEW or BASE TABLE.|  

## Example  

## See Also  
 [Obtaining Schema Information from the Host File System](../core/obtaining-schema-information-from-the-host-file-system1.md)   
 [BizTalk Adapter for Host Files Configuration](./biztalk-adapter-for-host-files-configuration1.md)