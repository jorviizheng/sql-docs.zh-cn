---
title: 除非 (MDX) |Microsoft 文档
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
- EXCEPT
dev_langs:
- kbMDX
helpviewer_keywords:
- Except function
ms.assetid: 5d832c82-1e6d-4308-9c26-7edb8afe11dd
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a918ebbed1b43dae8ad8e8aacb634f3b37781163
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="except-mdx-function"></a>除非 (MDX) 函数
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  计算两个集并删除第一个集中与第二个集中的元组重复的元组，也可以选择保留重复项。  
  
## <a name="syntax"></a>语法  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression1*  
 返回集的有效多维表达式 (MDX)。  
  
 *Set_Expression2*  
 返回集的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>注释  
 如果**所有**是指定的函数将保留在第一组中找到重复项; 第二组中的重复项仍将被删除。 成员的返回顺序与它们在第一个集中出现的顺序相同。  
  
## <a name="examples"></a>示例  
 以下示例说明了此函数的用法。  
  
```  
   //This query shows the quantity of orders for all products,  
   //with the exception of Components, which are not  
   //sold.  
SELECT   
   [Date].[Month of Year].Children  ON COLUMNS,  
   Except  
      ([Product].[Product Categories].[All].Children ,  
         {[Product].[Product Categories].[Components]}  
      ) ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   ([Measures].[Order Quantity])  
```  
  
## <a name="see-also"></a>另请参阅  
 [-&#40;除&#41; &#40;MDX&#41;](../mdx/except-mdx-operator.md)   
 [MDX 函数引用 & #40;MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
