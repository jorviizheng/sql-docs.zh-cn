---
title: sp_grantlogin (TRANSACT-SQL) |Microsoft 文档
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
- sp_grantlogin_TSQL
- sp_grantlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantlogin
ms.assetid: 0c873d99-c3bf-4eb1-948b-a46cb235ccd4
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c0e5454e94024bf0cebe6d9b0b2702e1bcf989f6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="spgrantlogin-transact-sql"></a>sp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)相反。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_grantlogin [@loginame=] 'login'  
```  
  
## <a name="arguments"></a>参数  
 [ **@loginame =** ] **'***login***'**  
 是 Windows 用户或组的名称。 Windows 用户或组必须用在窗体中的 Windows 域名称进行限定*域*\\*用户*; 例如， **London\Joeb**。 *登录名*是**sysname**，无默认值。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>注释  
 **sp_grantlogin**调用 CREATE LOGIN、 支持其他选项。 有关创建 SQL Server 登录名的信息，请参阅[CREATE LOGIN &#40;Transact SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)  
  
 **sp_grantlogin**不能在用户定义的事务内执行。  
  
## <a name="permissions"></a>权限  
 要求对服务器拥有 ALTER ANY LOGIN 权限。  
  
## <a name="examples"></a>示例  
 下面的示例使用`CREATE LOGIN`创建[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 Windows 用户登录`Corporate\BobJ.`这是首选的方法。  
  
```  
CREATE LOGIN [Corporate\BobJ] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [安全存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
