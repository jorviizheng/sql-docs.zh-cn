---
title: SQLServerXAResource 类 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46281eca1f326f39a0e8aff7e167214152a839e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverxaresource-class"></a>SQLServerXAResource 类
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  表示为 XA XAResource 分布式事务管理。  
  
 **包：** com.microsoft.sqlserver.jdbc  
  
 **扩展：** java.lang.Object  
  
 **实现：** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>语法  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>注释  
 在中实现 XA 事务[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]使用[!INCLUDE[msCoName](../../../includes/msconame_md.md)]分布式事务管理器 (DTC)。 SQLServerXAResource 类，使调用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]扩展名为 sqljdbc_xa.dll，与 DTC 交互的 dll。 XA 调用所接收的 SQLServerXAResource （XA_START、 XA_END、 XA_PREPARE，等） 将映射到对 DTC 函数对应的调用。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerXAResource 成员](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [JDBC 驱动程序 API 参考](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
