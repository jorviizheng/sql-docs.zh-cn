---
title: getWorkstationID 方法 (SQLServerDataSource) |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4466d3bfe0a088f4694eb01bef74e8ac34c4f8b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>getWorkstationID 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回用于连接数据源的客户端计算机名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>返回值  
 A**字符串**，其中包含客户端计算机名称。  
  
## <a name="remarks"></a>注释  
 workstationID 是客户端计算机或工作站的名称。 如果未设置 workstationID 属性，默认值是通过调用 InetAddress.getLocalHost().getHostName() 方法构造的。 如果 getHostName 返回空白值，调用 getHostAddress().toString() 方法。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
