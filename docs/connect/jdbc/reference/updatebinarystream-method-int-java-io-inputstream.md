---
title: updateBinaryStream 方法 （int、 java.io.InputStream） |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3682c8418ff107eb7ef7a7c91797a9d859a5f1d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="updatebinarystream-method-int-javaioinputstream"></a>updateBinaryStream 方法 (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用二进制流值更新指定列。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Parameters  
 columnIndex  
  
 指示列索引的 int。  
  
 *x*  
  
 一个 InputStream 对象中。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>注释  
 由 java.sql.ResultSet 接口中的 updateBinaryStream 方法指定此 updateBinaryStream 方法。  
  
 使用此方法对于**映像**，**文本**，和**ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]数据类型可能会影响性能。  
  
 此方法将从 InputStream 对象选择传递字节[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]如二进制、 varbinary、 varbinary （max）、 图像、 xml 和 udt 的二进制列。 此方法不支持更新字符列。 若要更新使用 InputStream 字符列，请使用[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [updateBinaryStream 方法&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
