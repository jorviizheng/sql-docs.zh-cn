---
title: 架构行集支持 (OLE DB) |Microsoft 文档
description: 架构行集支持 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- OLE DB Driver for SQL Server, schema rowsets
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d5b8bc20c380494560a5e7b605ff68dded99a928
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="schema-rowset-support-ole-db"></a>架构行集支持 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server 的 OLE DB 驱动程序还支持从链接服务器返回的架构信息时处理[!INCLUDE[tsql](../../../includes/tsql-md.md)]分布式查询。  
  
> [!NOTE]  
>  尽管[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]支持用于同义词不由返回 OLE DB 驱动程序适用于 SQL Server 的同义词，元数据。  
  
 下表列出架构行集和适用于 SQL Server 的 OLE DB 驱动程序支持的限制列。  
  
|架构行集|限制列|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> 以下附加列专用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]：<br /><br /> COLUMN_LCID，这是排序规则的区域设置 ID。 COLUMN_LCID 是与 Windows LCID 相同的值。<br /><br /> COLUMN_COMPFLAGS 定义对于排序规则支持哪些比较。 数据格式与 DBPROB_FINDCOMPAREOPS 相同。<br /><br /> COLUMN_SORTID，即[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]排序排序规则的样式。<br /><br /> COLUMN_TDSCOLLATION，这是用于列的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 排序规则。<br /><br /> IS_COMPUTED，如果列为计算列，则为 VARIANT_TRUE；否则为 VARIANT_FALSE。|  
|DBSCHEMA_FOREIGN_KEYS|支持所有限制。<br /><br /> PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|DBSCHEMA_INDEXES|支持限制 1、2、3 和 5。<br /><br /> TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURE_PARAMETERS|支持所有限制。<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROCEDURES|支持限制 1、2 和 3。<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME<br /><br /> DBSCHEMA_PROCEDURES 只返回可由当前用户执行的过程，或返回已向当前用户授予 VIEW DEFINITION 权限的过程。|  
|DBSCHEMA_PROVIDER_TYPES|支持所有限制。<br /><br /> DATA_TYPE BEST_MATCH|  
|DBSCHEMA_SCHEMATA|支持所有限制。<br /><br /> CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|DBSCHEMA_STATISTICS|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_TABLE_CONSTRAINTS|支持所有限制。<br /><br /> CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|DBSCHEMA_TABLE_PRIVILEGES|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|DBSCHEMA_TABLES|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|DBSCHEMA_TABLES_INFO|支持所有限制。<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
## <a name="in-this-section"></a>本節內容  
 [分布式查询中架构行集的支持](../../oledb/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [LINKEDSERVERS 行集&#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>另请参阅  
 [用于 SQL Server 编程的 OLE DB 驱动程序](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [使用用户定义的类型](../../oledb/features/using-user-defined-types.md)  
  
  
