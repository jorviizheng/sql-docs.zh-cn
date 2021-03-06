---
title: 管理策略类别 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 088f033dcc51fd3cccb2342c8932ddfe911a4af3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="manage-policy-categories"></a>管理策略类别
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 将某类别的任意或所有可用策略应用到整个 [!INCLUDE[tsql](../../includes/tsql-md.md)]实例。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [Security](#Security)  
  
-   **将类别策略应用到 SQL Server 实例，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
  
-   使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时，如果未选中 **“托管数据库订阅”** 复选框，则必须将策略类别分别应用于服务器的每个相关部分，例如，一个或多个数据库或表。  
  
-   如果您指定的策略类别不存在，将创建新的策略类别，并且在您执行存储过程时对于所有数据库都将托管订阅。 如果你为新的类别清除托管的订阅，则该订阅将只适用于你指定为 *target_object* 的数据库。 有关如何更改托管的订阅设置的详细信息，请参阅 [sp_syspolicy_update_policy_category (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 此存储过程在其当前所有者的上下文中运行。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>将类别策略应用到 SQL Server 实例  
  
1.  在 **“对象资源管理器”**中，单击加号以展开您将应用类别策略的服务器。  
  
2.  单击加号以便展开 **“管理”** 文件夹。  
  
3.  右键单击“策略管理”，然后选择“管理类别”。  
  
     在 **“管理策略类别”** 对话框中提供以下信息：  
  
     **名称**  
     策略类别的名称。  
  
     **“托管数据库订阅”**  
     强制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的所有数据库实施策略类别中的策略。  
  
4.  选中或清除 **“托管数据库订阅”** 下的任意或所有复选框，以将该策略类别应用到 SQL Server 实例。  
  
5.  完成后，单击 **“确定”**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>将类别策略应用到 SQL Server 实例  
  
1.  在 **“对象资源管理器”**中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 有关详细信息，请参阅 [sp_syspolicy_add_policy_category_subscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql.md)。  
  
  
