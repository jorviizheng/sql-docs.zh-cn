---
title: 一些同步副本不同步 | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0edbc7e52b279dc7b14b550526dd3c1b14b29c27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>一些同步副本不同步
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>简介  
  
|||  
|-|-|  
|**策略名称**|同步副本数据同步状态|  
|**问题**|一些同步副本不同步。|  
|**类别**|**警告**|  
|**方面**|可用性组 (availability group)|  
  
## <a name="description"></a>Description  
 此策略将汇总所有可用性副本的数据同步状态，并且检查是否存在未处于预期同步状态的任何可用性副本。 在任何异步副本未处于 SYNCHRONIZING 状态以及任何同步副本未处于 SYNCHRONIZED 状态时，该策略处于不正常状态。 否则，策略状态为正常。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [某些同步副本未同步](http://go.microsoft.com/fwlink/p/?LinkId=220853) 中。  
  
## <a name="possible-causes"></a>可能的原因  
 在该可用性组中，至少一个同步副本当前未同步。 副本同步状态可以是 SYNCHONIZING 或 SYNCHRONIZING。  
  
## <a name="possible-solution"></a>可能的解决方法  
 使用可用性副本策略状态可以找到具有错误同步状态的可用性副本，然后解决该可用性副本上的问题。  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
