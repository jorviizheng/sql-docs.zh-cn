---
title: sys.dm_pdw_wait_stats (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b0998939599ba5f793eeb8a4784246a75b68198a
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwwaitstats-transact-sql"></a>sys.dm_pdw_wait_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  包含与相关的信息[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]OS 状态相关的不同节点上运行的实例。 等待类型和及其说明的列表，请参阅[sys.dm_os_wait_stats](http://msdn.microsoft.com/en-us/library/ms179984\(v=sql.120\).aspx)。  
  
|列名|数据类型|Description|范围|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|此项引用的节点 ID。||  
|**wait_name**|**nvarchar(255)**|等待类型的名称。||  
|**max_wait_time**|**bigint**|该等待类型的最长等待时间。||  
|**request_count**|**bigint**|等待类型未完成的此等待数。||  
|**signal_time**|**bigint**|正在等待的线程从收到信号通知到其开始运行之间的时差。||  
|**completed_count**|**bigint**|重新启动的等待完成，因为最后一个服务器此类型的总数。||  
|**wait_time**|**bigint**|该等待类型的 millisecons 的总等待时间。 Signal_time 的非独占时间。||  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_waits &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
