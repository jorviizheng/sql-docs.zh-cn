---
title: getConnection 方法 （java.lang.String，java.lang.String） |Microsoft 文档
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
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb33640c75d98fa065c6388458aaffc3067c3126
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="getconnection-method-javalangstring-javalangstring"></a>getConnection 方法 (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  尝试建立连接的数据源此[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)对象表示通过使用指定的用户名和密码。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parameters  
 *username*  
  
 A**字符串**包含的用户名称。  
  
 *password*  
  
 A**字符串**包含的密码。  
  
## <a name="return-value"></a>返回值  
 A [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)对象。  
  
## <a name="exceptions"></a>异常  
 java.sql.SQLException  
  
## <a name="remarks"></a>注释  
 由 javax.sql.DataSource 接口中的 getConnection 方法指定此 getConnection 方法。  
  
 调用 getConnection 使用非 null 用户名或密码的方法将替换 SQLServerDataSource 类时初始化 SQLServerConnection 对象设置的用户名称和密码属性。 例如，如果调用方已调用[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)和[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)上对数据源，然后调用 getConnection 和提供非 null 用户名称或非空密码，用户名和密码设置setUser 和 setPassword 将被替换的用户名和密码传递到 getConnection。  
  
> [!NOTE]  
>  用户名和密码在 URL 内使用设置的调用[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)方法将不会在这种情况下更改。  
  
## <a name="see-also"></a>另请参阅  
 [getConnection 方法&#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
