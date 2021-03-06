---
title: sp_help_jobs_in_schedule (Transact SQL) |Microsoft 文档
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
- sp_help_jobs_in_schedule_TSQL
- sp_help_jobs_in_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobs_in_schedule
ms.assetid: 1168aa2c-136b-4ba3-b18e-9070d95a26fa
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78bffc1432bb650d5c1a7f37c0a712c34236dca1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobsinschedule-transact-sql"></a>sp_help_jobs_in_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回有关附加了特定计划的作业的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help_jobs_in_schedule   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>参数  
 [ **@schedule_id =** ] *schedule_id*  
 将列出其信息的计划的标识符。 *schedule_id*是**int**，无默认值。 任一*schedule_id*或*schedule_name*可指定。  
  
 [ **@schedule_name =** ] **'***schedule_name***'**  
 将列出其信息的计划的名称。 *schedule_name*是**sysname**，无默认值。 任一*schedule_id*或*schedule_name*可指定。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
 返回以下结果集：  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|作业的唯一 ID。|  
|**originating_server**|**nvarchar(30)**|作业来自的服务器的名称。|  
|**名称**|**sysname**|作业的名称。|  
|**enabled**|**tinyint**|指示是否启用要执行的作业。|  
|**说明**|**nvarchar(512)**|对作业的说明。|  
|**start_step_id**|**int**|执行作业的起始步骤的 ID。|  
|**category**|**sysname**|作业类别。|  
|**所有者**|**sysname**|作业所有者。|  
|**notify_level_eventlog**|**int**|位掩码，它表示在何种情况下通知事件应记录到 Microsoft Windows 应用程序日志中。 可以是下列值之一：<br /><br /> **0** = 从不<br /><br /> **1** = 当作业成功<br /><br /> **2** = 当作业失败时<br /><br /> **3** = 当作业完成 （不考虑作业结果中） 时|  
|**notify_level_email**|**int**|位掩码，它指示当作业完成时，在什么情况下应该发送一个通知电子邮件。 可能的值为相同**notify_level_eventlog**。|  
|**notify_level_netsend**|**int**|位掩码，它表示当作业完成时，在什么情况下应该发送一个网络消息。 可能的值为相同**notify_level_eventlog**。|  
|**notify_level_page**|**int**|位掩码，它表示当作业完成时，在什么情况下应该发送一个呼叫。 可能的值为相同**notify_level_eventlog**。|  
|**notify_email_operator**|**sysname**|被通知的操作员的电子邮件名称。|  
|**notify_netsend_operator**|**sysname**|在发送网络消息时所使用的计算机或用户的名称。|  
|**notify_page_operator**|**sysname**|在发送寻呼时所使用的计算机或用户的名称。|  
|**delete_level**|**int**|位掩码，它表示当作业完成时，在什么情况下应该删除作业。 可能的值为相同**notify_level_eventlog**。|  
|**date_created**|**datetime**|作业的创建日期。|  
|**date_modified**|**datetime**|上次修改作业的日期。|  
|**version_number**|**int**|作业的版本（每次修改作业时都自动对其进行更新）。|  
|**last_run_date**|**int**|作业上一次开始执行的日期。|  
|**last_run_time**|**int**|作业上一次开始执行的时间。|  
|**last_run_outcome**|**int**|作业上一次运行时所得到的结果：<br /><br /> **0** = 失败<br /><br /> **1** = 成功<br /><br /> **3** = 取消<br /><br /> **5** = 未知|  
|**next_run_date**|**int**|计划作业下一次运行的日期。|  
|**next_run_time**|**int**|计划作业下一次运行的时间。|  
|**next_run_schedule_id**|**int**|下一个运行的计划的标识号。|  
|**current_execution_status**|**int**|当前执行状态。|  
|**current_execution_step**|**sysname**|作业中当前的执行步骤。|  
|**current_retry_attempt**|**int**|如果作业正在运行，并且已经重试过该步骤，那么这就是当前的重试尝试。|  
|**has_step**|**int**|作业具有的作业步骤数。|  
|**has_schedule**|**int**|作业具有的作业计划数。|  
|**has_target**|**int**|作业具有的目标服务器数。|  
|**类型**|**int**|作业类型：<br /><br /> **1** = 本地作业。<br /><br /> **2** = 多服务器作业。<br /><br /> **0** = 作业具有任何目标服务器。|  
  
## <a name="remarks"></a>注释  
 此过程列出有关附加到指定计划的作业的信息。  
  
## <a name="permissions"></a>权限  
 默认情况下，只有 **sysadmin** 固定服务器角色的成员才可以执行此存储过程。 其他用户必须被授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **数据库中下列** 代理固定数据库角色的权限之一：  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 有关这些角色的权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)。  
  
 成员**SQLAgentUserRole**可以仅查看他们所拥有的作业的状态。  
  
## <a name="examples"></a>示例  
 以下示例列出附加到 `NightlyJobs` 计划的作业。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobs_in_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server 代理存储过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule 将&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
