---
title: sp_who (TRANSACT-SQL) |Microsoft 文档
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
- sp_who_TSQL
- sp_who
dev_langs:
- TSQL
helpviewer_keywords:
- sp_who
ms.assetid: 132dfb08-fa79-422e-97d4-b2c4579c6ac5
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f21ac270ac0f448291b5e6eb8874182598e933ef
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="spwho-transact-sql"></a>sp_who (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  提供有关当前用户、 会话和实例中的进程信息[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。 可以筛选信息以便只返回那些属于特定用户或特定会话的非空闲进程。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_who [ [ @loginame = ] 'login' | session ID | 'ACTIVE' ]  
```  
  
## <a name="arguments"></a>参数  
 [  **@loginame =** ] *****登录***** | *会话 ID* | **'ACTIVE'**  
 用于筛选结果集。  
  
 *登录名*是**sysname**标识属于特定的登录名的进程。  
  
 *会话 ID*是属于会话标识号[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。 *会话 ID*是**smallint**。  
  
 **ACTIVE**排除正在等待下一个命令从用户的会话。  
  
 如果没有提供任何值，则过程报告属于实例的所有会话。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 **sp_who**返回的结果集包含以下信息。  
  
|列|数据类型|Description|  
|------------|---------------|-----------------|  
|**spid**|**int**|会话 ID。|  
|**ecid**|**int**|与特定会话 ID 相关联的给定线程的执行上下文 ID。<br /><br /> ECID = {0、 1、 2、 3，…*n*}，其中 0 始终表示主或父线程和 {1，2，3，…*n*} 表示子线程。|  
|**status**|**nchar(30)**|进程状态。 可能的值有：<br /><br /> **休眠**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在重置会话。<br /><br /> **运行**。 会话正在运行一个或多个批。 多个活动的结果集 (MARS) 启用后，会话可以运行多个批。 有关详细信息，请参阅[使用多个活动结果集 & #40;MARS & #41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **后台**。 会话正在运行一个后台任务，例如死锁检测。<br /><br /> **回滚**。 会话具有正在处理的事务回滚。<br /><br /> **挂起**。 会话正在等待工作线程变为可用。<br /><br /> **可运行**。 会话的任务在等待获取时间量程时位于计划程序的可运行队列中。<br /><br /> **spinloop**。 会话的任务正在等待调节锁变为可用。<br /><br /> **挂起**。 会话正在等待事件（如 I/O）完成。|  
|**loginame**|**nchar(128)**|与特定进程相关联的登录名。|  
|**主机名**|**nchar(128)**|每个进程的主机或计算机名。|  
|**blk**|**char(5)**|如果存在阻塞进程，则是该阻塞进程的会话 ID。 否则该列为零。<br /><br /> 当与指定会话 ID 相关联的事务受到孤立分布式事务的阻塞时，该列将对阻塞孤立事务返回“-2”。|  
|**dbname**|**nchar(128)**|进程使用的数据库。|  
|**Cmd**|**nchar(16)**|为该进程执行的[!INCLUDE[ssDE](../../includes/ssde-md.md)]命令（[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、[!INCLUDE[ssDE](../../includes/ssde-md.md)]进程等等）。|  
|**request_id**|**int**|特定会话中运行的请求的 ID。|  
  
 如果是并行处理，则会为特定的会话 ID 创建子线程。 主线程则以 `spid = <xxx>` 和 `ecid =0` 表示。 具有相同的其他子线程`spid = <xxx>`，但与**ecid** > 0。  
  
## <a name="remarks"></a>注释  
 阻塞进程（可能含有排他锁）是控制其他进程所需要的资源的进程。  
  
 所有孤立的分布式事务的会话 ID 都被赋予值“-2”。 孤立的分布式事务是不与任何会话 ID 关联的分布式事务。 有关详细信息，请参阅 [使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)。  
  
 查询**is_user_process** sys.dm_exec_sessions 将系统进程从用户进程中分隔列。  
  
## <a name="permissions"></a>权限  
 要求对服务器拥有 VIEW SERVER STATE 权限才能查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上所有正在执行的会话。 否则，用户只能查看当前会话。  
  
## <a name="examples"></a>示例  
  
### <a name="a-listing-all-current-processes"></a>A. 列出全部当前进程  
 以下示例使用没有参数的 `sp_who` 来报告所有当前用户。  
  
```  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
### <a name="b-listing-a-specific-users-process"></a>B. 列出特定用户的进程  
 以下示例显示如何通过登录名查看有关单个当前用户的信息。  
  
```  
USE master;  
GO  
EXEC sp_who 'janetl';  
GO  
```  
  
### <a name="c-displaying-all-active-processes"></a>C. 显示所有活动进程  
  
```  
USE master;  
GO  
EXEC sp_who 'active';  
GO  
```  
  
### <a name="d-displaying-a-specific-process-identified-by-a-session-id"></a>D. 显示会话 ID 标识的特定进程  
  
```  
USE master;  
GO  
EXEC sp_who '10' --specifies the process_id;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [sp_lock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sys.sysprocesses &#40;Transact SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
