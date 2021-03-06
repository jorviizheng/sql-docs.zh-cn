---
title: sys.dm_db_uncontained_entities (TRANSACT-SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_uncontained_entities
- dm_db_uncontained_entities_TSQL
- sys.dm_db_uncontained_entities_TSQL
- dm_db_uncontained_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_uncontained_entities dynamic management view
ms.assetid: f417efd4-8c71-4f81-bc9c-af13bb4b88ad
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18f89d3a275a36d32d72524a1c2e650a9e2dc663
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmdbuncontainedentities-transact-sql"></a>sys.dm_db_uncontained_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  显示数据库中使用的任何非包含对象。 非包含对象是跨包含数据库中的数据库边界的对象。 此视图可同时从包含数据库和非包含数据库进行访问。 如果 sys.dm_db_uncontained_entities 为空，则你的数据库不使用任何非包含的实体。  
  
 如果某个模块多次跨越数据库边界，则只报告发现的第一个跨越。  
  
||||  
|-|-|-|  
|**列名**|**类型**|**Description**|  
|class|**int**|1 = 对象或列（包括模块、XP、视图、同义词和表）。<br /><br /> 4 = 数据库主体<br /><br /> 5 = 程序集<br /><br /> 6 = 类型<br /><br /> 7 = 索引（全文索引）<br /><br /> 12 = 数据库 DDL 触发器<br /><br /> 19 = 路由<br /><br /> 30 = 审核规范|  
|*class_desc*|**nvarchar(120)**|对实体的类的说明。 下列其中一项以匹配的类：<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **DATABASE_PRINCIPAL**<br /><br /> **ASSEMBLY**<br /><br /> **TYPE**<br /><br /> **INDEX**<br /><br /> **DATABASE_DDL_TRIGGER**<br /><br /> **ROUTE**<br /><br /> **AUDIT_SPECIFICATION**|  
|*major_id*|**int**|实体的 ID。<br /><br /> 如果*类*= 1，则 object_id<br /><br /> 如果*类*= 4，则 sys.database_principals.principal_id。<br /><br /> 如果*类*= 5，则 sys.assemblies.assembly_id。<br /><br /> 如果*类*= 6，则 sys.types.user_type_id。<br /><br /> 如果*类*= 7，则 sys.indexes.index_id。<br /><br /> 如果*类*= 12，则 sys.triggers.object_id。<br /><br /> 如果*类*= 19，则 sys.routes.route_id。<br /><br /> 如果*类*= 30，则 sys。 database_audit_specifications.databse_specification_id.|  
|*statement_line_number*|**int**|如果此类是一个模块，则返回找到非包含使用所在的行号。  否则，值为 Null。|  
|*statement_ offset_begin*|**int**|如果此类是一个模块，则指示非包含使用开始的起始位置（以字节表示，从 0 开始）。 否则，返回值为 Null。|  
|*statement_ offset_end*|**int**|如果此类是一个模块，则指示非包含使用的结束位置（以字节表示，从 0 开始）。 值为 -1 指示模块的结尾。 否则，返回值为 Null。|  
|*statement_type*|**nvarchar(512)**|语句的类型。|  
|*功能名称*|**nvarchar(256)**|返回对象的外部名称。|  
|*feature_type_name*|**nvarchar(256)**|返回功能的类型。|  
  
## <a name="remarks"></a>注释  
 sys.dm_db_uncontained_entities 显示这些实体，这可能跨越数据库边界。 它将返回可能使用数据库之外的对象的任何用户实体。  
  
 将报告下面的功能类型。  
  
-   未知的包含行为（动态 SQL 或延迟的名称解析）  
  
-   DBCC 命令  
  
-   系统存储过程  
  
-   系统标量函数  
  
-   系统表值函数  
  
-   系统内置函数  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>权限  
 sys.dm_db_uncontained_entities 只返回对其用户具有某种类型的权限对象。 若要完全评估高特权用户例如的成员时应使用此函数的数据库的包含关系**sysadmin**固定的服务器角色或**db_owner**角色。  
  
## <a name="examples"></a>示例  
 
              `sys.dm_db_uncontained_entities`下面的示例创建一个名为 P1 的过程，然后查询 。 
              **
              ** 此查询报告 P1 使用数据库之外的 sys.endpoints。  
  
```sql  
CREATE DATABASE Test;  
GO  
  
USE Test;  
GO  
CREATE PROC P1  
AS   
SELECT * FROM sys.endpoints ;  
GO  
SELECT SO.name, UE.* FROM sys.dm_db_uncontained_entities AS UE  
LEFT JOIN sys.objects AS SO  
    ON UE.major_id = SO.object_id;  
```  
  
## <a name="see-also"></a>另请参阅  
 [包含的数据库](../../relational-databases/databases/contained-databases.md)  
  
  
