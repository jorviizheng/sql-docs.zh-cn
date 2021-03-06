---
title: 查看订阅代理的信息和执行其任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: fbb59d31-2424-4552-9195-0da8d83e755f
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f98dd86491561fb67197a02e228ec1b151e6e3ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="view-information-and-perform-tasks-for-subscription-agents"></a>查看订阅代理的信息和执行其任务
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  复制监视器提供了两个选项卡，可用于访问与订阅相关联的代理的相关信息：  
  
-   **所有订阅**  
  
     此选项卡显示有关所选发布的所有订阅的信息。  
  
-   **订阅监视列表**  
  
     此选项卡用于显示所选发布服务器上所有可用发布的订阅的信息：有错误、出现警告或性能最差。 对于运行 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]以前版本的分发服务器，不显示此选项卡。  
  
 有关每个选项卡上各选项的详细信息，请在右窗格中单击相应选项卡，然后在菜单栏上单击 **“帮助”** 。 有关启动复制监视器的信息，请参阅[启动复制监视器](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)。  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-all-subscriptions-tab"></a>查看信息并执行与订阅相关联的代理任务（“所有订阅”选项卡）  
  
1.  在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。  
  
2.  单击 **“所有订阅”** 选项卡以查看有关订阅的信息。 您还可以通过此选项卡访问更详细的信息并执行任务：  
  
    -   若要查看与订阅相关联的代理的详细信息，请右键单击该订阅，再单击 **“查看详细信息”**。 详细信息包括：代理历史记录和错误消息；事务复制的性能统计信息；合并复制的项目级同步统计信息。  
  
         启动的详细信息窗口上显示的选项卡取决于订阅的类型：对于快照订阅，显示的选项卡是 **“分发服务器到订阅服务器的历史记录”**；对于事务订阅，显示的选项卡有 **“发布服务器到分发服务器的历史记录”**、 **“发布服务器到订阅服务器的历史记录”**和 **“未分发的命令”**；对于合并订阅，显示的选项卡是 **“同步历史记录”**。  
  
    -   若要同步推送订阅，请右键单击该订阅，然后单击 **“开始同步”**。  
  
    -   若要重新初始化订阅，请右键单击该订阅，然后单击 **“重新初始化订阅”**。  
  
    -   若要验证单个合并订阅，请右键单击该订阅，再单击 **“验证单个订阅”**。 若要验证合并发布的所有订阅，请右键单击该发布，再单击 **“验证所有订阅”**；若要验证事务发布的所有订阅，请右键单击该发布，再单击 **“验证多个订阅”**。  
  
    -   若要管理代理的配置文件，请右键单击代理，然后单击 **“代理配置文件”**。 有关详细信息，请参阅[处理复制代理配置文件](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)。  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-subscription-watch-list-tab"></a>查看信息并执行与订阅相关联的代理任务（“订阅监视列表”选项卡）  
  
1.  在左窗格中，展开发布服务器组，然后单击一个发布服务器。  
  
2.  单击 **“订阅监视列表”** 选项卡以查看有关订阅的信息。 您还可以通过此选项卡访问更详细的信息并执行任务：  
  
    -   若要查看与订阅相关联的代理的详细信息，请右键单击该订阅，再单击 **“查看详细信息”**。 详细信息包括：代理历史记录和错误消息；事务复制的性能统计信息；合并复制的项目级同步统计信息。  
  
         启动的详细信息窗口上显示的选项卡取决于订阅的类型：对于快照订阅，显示的选项卡是 **“分发服务器到订阅服务器的历史记录”**；对于事务订阅，显示的选项卡是 **“发布服务器到分发服务器的历史记录”**、 **“发布服务器到订阅服务器的历史记录”**和 **“未分发的命令”**；对于合并订阅，显示的选项卡是 **“同步历史记录”**。  
  
    -   若要同步推送订阅，请右键单击该订阅，然后单击 **“开始同步”**。  
  
    -   若要重新初始化订阅，请右键单击该订阅，然后单击 **“重新初始化订阅”**。  
  
    -   若要验证单个合并订阅，请右键单击该订阅，再单击 **“验证单个订阅”**。 若要验证合并发布的所有订阅，请右键单击该发布，再单击 **“验证所有订阅”**；若要验证事务发布的所有订阅，请右键单击该发布，再单击 **“验证多个订阅”**。  
  
    -   若要管理代理的配置文件，请右键单击代理，然后单击 **“代理配置文件”**。 有关详细信息，请参阅[处理复制代理配置文件](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)。  
  
## <a name="see-also"></a>另请参阅  
 [查看订阅的信息和执行其任务（复制监视器）](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [监视复制](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
