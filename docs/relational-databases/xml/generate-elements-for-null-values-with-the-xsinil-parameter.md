---
title: 使用 XSINIL 参数生成 NULL 值对应的元素 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6cce3b58cd219a35aac830c41d5151a76146bd99
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>使用 XSINIL 参数生成 NULL 值对应的元素
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  **ELEMENTS** 指令将构造 XML，其中每个列值映射到 XML 中的一个元素。 如果列值为 NULL，则不添加元素。 通过对 ELEMENTS 指令指定可选的 **XSINIL** 参数，可以请求创建 NULL 值对应的元素。 在这种情况下，将为每个 NULL 列值返回一个元素，其 **xsi:nil** 属性被设置为 TRUE。  
  
## <a name="see-also"></a>另请参阅  
 [将 RAW 模式与 FOR XML 一起使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
