---
title: XOR (MDX) |Microsoft 文档
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- XOR
dev_langs:
- kbMDX
helpviewer_keywords:
- XOR operator
ms.assetid: 17280f36-df0e-477e-9342-e8129ed5cc3c
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17bebf33ae3cc5d08f51fe61ac7adbe0de875751
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="xor-mdx"></a>XOR (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  对两个数值表达式执行逻辑异运算。  
  
## <a name="syntax"></a>语法  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>Parameters  
 *Expression1*  
 返回数值的有效多维表达式 (MDX) 表达式。  
  
 *Expression2*  
 返回数值的有效 MDX 表达式。  
  
## <a name="return-value"></a>返回值  
 返回一个布尔值**true**如果一个且仅有一个自变量的计算结果为**true**; 否则为**false**。  
  
## <a name="remarks"></a>注释  
 **XOR**运算符将两个参数视为布尔值 (0，0，作为**false**; 否则为**true**) 执行逻辑异或运算符之前。 下表说明了如何**XOR**执行逻辑异或运算符。  
  
|*Expression1*|*Expression2*|返回值|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>另请参阅  
 [MDX 运算符参考&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
