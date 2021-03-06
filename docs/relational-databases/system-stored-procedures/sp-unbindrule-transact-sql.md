---
title: sp_unbindrule (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_unbindrule_TSQL
- sp_unbindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindrule
ms.assetid: f54ee155-c3c9-4f1a-952e-632a8339f0cc
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: be14a4885cea481edda6ba7465ac2c5aa969ec1b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="spunbindrule-transact-sql"></a>sp_unbindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在当前数据库中取消列或别名数据类型的规则绑定。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] 我们建议你通过中的默认关键字创建默认定义[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)或[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)语句相反。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_unbindrule [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>参数  
 [ **@objname=** ] **'***object_name***'**  
 要取消规则绑定的表和列或别名数据类型的名称。 *object_name*是**nvarchar(776)**，无默认值。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 尝试先将两部分标识符解析为列名，再解析为别名数据类型。 在取消别名数据类型的规则绑定时，也同时取消数据类型相同并具有相同规则的任何列的绑定。 属于该数据类型并且规则直接绑定的列将不受影响。  
  
> [!NOTE]  
>  *object_name*可以包含括号 **[]** 作为分隔标识符字符。 有关详细信息，请参阅 [Database Identifiers](../../relational-databases/databases/database-identifiers.md)。  
  
 [ **@futureonly=** ] **'***futureonly_flag***'**  
 仅在取消别名数据类型的规则绑定时使用。 *futureonly_flag*是**varchar(15)**，默认值为 NULL。 当*futureonly_flag*是**futureonly**，该数据类型的现有列不会丢失指定的规则。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>注释  
 若要显示某条规则的文本，请以该规则的名称作为参数来执行 sp_helptext。  
  
 未绑定规则时，从删除绑定有关的信息**sys.columns**表如果规则已绑定到列，并从**sys.types**表如果规则绑定到别名数据类型。  
  
 当取消别名数据类型的规则绑定时，任何具有该别名数据类型的列也同时取消该规则绑定。 该规则可能仍然会绑定到 ALTER TABLE 语句的 ALTER COLUMN 子句之后已更改其数据类型的列，具体而言，则必须取消这些列中的规则绑定使用**sp_unbindrule**并指定列名称。  
  
## <a name="permissions"></a>权限  
 若要取消表列的规则绑定，需要对表具有 ALTER 权限。 若要取消别名数据类型的规则绑定，需要对该类型具有 CONTROL 权限或对该类型所属的架构具有 ALTER 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-unbinding-a-rule-from-a-column"></a>A. 取消列的规则绑定  
 以下示例取消 `startdate` 表的 `employees` 列的规则绑定。  
  
```  
EXEC sp_unbindrule 'employees.startdate';  
```  
  
### <a name="b-unbinding-a-rule-from-an-alias-data-type"></a>B. 取消别名数据类型的规则绑定  
 以下示例取消别名数据类型 `ssn` 的规则绑定。 这将从属于该数据类型的现有列和将来的列取消规则绑定。  
  
```  
EXEC sp_unbindrule ssn;  
```  
  
### <a name="c-using-futureonlyflag"></a>C. Using futureonly_flag  
 以下示例取消别名数据类型 `ssn` 的规则绑定，而不影响现有 `ssn` 列。  
  
```  
EXEC sp_unbindrule 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. 使用分隔的标识符  
 下面的示例演示使用中的分隔的标识符*object_name*参数。  
  
```  
CREATE TABLE [t.4] (c1 int); -- Notice the period as part of the table   
-- name.  
GO  
CREATE RULE rule2 AS @value > 100;  
GO  
EXEC sp_bindrule rule2, '[t.4].c1' -- The object contains two   
-- periods; the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
GO  
EXEC sp_unbindrule '[t.4].c1';  
```  
  
## <a name="see-also"></a>另请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [数据库引擎存储过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [DROP RULE (Transact-SQL)](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_bindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
