---
title: MDDataSet 数据类型 (XMLA) |Microsoft 文档
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b5f42140d8987cb36ea95c4c4314798a1ee7633
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="mddataset-data-type-xmla"></a>MDDataSet 数据类型 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  定义一个派生的数据类型，表示返回的多维数据[执行](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法。  
  
 **Namespace** urn： 架构-microsoft-com:xml-分析： mddataset  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>数据类型特征  
  
|特征|说明|  
|--------------------|-----------------|  
|基本数据类型|[结果集](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|派生数据类型|无|  
  
## <a name="data-type-relationships"></a>数据类型关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|无|  
|子元素|[轴](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md)， [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md)， [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|派生元素|無|  
  
## <a name="remarks"></a>注释  
 **MDDataSet**数据类型提供的 OLAP 面向行集 （或数据集） 以表示在 XML 中的 OLAP 数据要求。 值而异的下一个行集合的内容**内容**和**格式**属性中提供[属性](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)集合**执行**方法。 有关详细信息**内容**和**格式**属性，请参阅[支持 XMLA 属性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)。  
  
 有关 OLE DB for OLAP 数据集结构的基本信息，请参考 XML for Analysis 1.1 规范中的“MDDataSet 数据类型到 OLE DB 的映射”。 有关的完整 XML 架构定义语言 (XSD) 示例**MDDataSet**数据类型，请参阅"附录 d: MDDataSet"的 XML 示例分析 1.1 规范。  
  
## <a name="see-also"></a>另请参阅  
 [XML 数据类型&#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
