---
title: 检查 ODBC SQL Server 驱动程序版本 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c7e602687a8f677af5a3160a7e3e1c5b0c2f900d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>检查 ODBC SQL Server 驱动程序版本 (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  您的计算机可能包含来自 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 和其他公司的多种 ODBC 驱动程序。 本主题介绍如何使用 Windows **“ODBC 数据源管理器”** 来查看已安装的 ODBC 驱动程序的版本。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>检查 ODBC SQL Server 驱动程序版本（32 位 ODBC）  
  
-   在 **“ODBC 数据源管理器”**中，单击 **“驱动程序”** 选项卡。  
  
     有关 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 项的信息显示在 **“版本”** 列中。  


> [!NOTE]  
>  对于与 SQL 数据库的 Azure Active Directory 身份验证的连接，请安装最新的驱动程序，如 [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)。   

  
## <a name="see-also"></a>另请参阅  
 [打开 ODBC 数据源管理器](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
