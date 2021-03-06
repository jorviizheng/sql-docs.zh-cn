---
title: Reporting Services 网站集功能 | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 100ec0e739dc397b8173259abcfaf7c8e6cdfd9e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="reporting-services-site-collection-features"></a>Reporting Services 网站集功能

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Reporting Services SharePoint 模式提供了三个 SharePoint 网站集功能。 这些功能支持一般的 Reporting Services SharePoint 模式报告环境、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]（SQL Server 2016 Reporting Services 加载项的一个功能）以及 SharePoint 管理中心的 Reporting Services 的管理操作。

> [!NOTE]
> 自 SQL Server 2016 之后，不再提供 Reporting Services 与 SharePoint 的集成这一功能。
  
## <a name="site-collection-features"></a>网站集功能

 下表对 Reporting Services 网站集功能进行了说明。  
  
|功能|Description|  
|-------------|-----------------|  
|**报表服务器管理中心功能**|启用用于管理与 Reporting Services 报表服务器的集成的功能。 此功能仅安装和用于 SharePoint 管理中心网站集中。<br /><br /> 在安装了用于 SharePoint 产品的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 外接程序之后，报表服务器集成功能将自动在 SharePoint 管理中心网站集中激活。 在某些情况下，你需要手动激活此功能。 若要激活报表服务器功能，请在 SharePoint 管理中心的“站点设置”页中使用 Reporting Services 页。<br /><br /> 用于 SharePoint 产品的外接程序的 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Reporting Services 版本和更高版本将在安装外接程序时为所有现有的网站集激活报表服务器集成功能。 此外，对于新的网站集，此功能将自动激活。|  
|**报表服务器集成功能**|使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Reporting Services 启用多功能报告<br /><br /> 默认情况下此功能处于活动状态。|  
|**Power View 集成功能**|对 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工作簿和 Analysis Services 表格数据库启用交互式数据浏览和直观的展示。<br /><br /> 该功能可通过下列数据源的上下文菜单访问：<br /><br /> **.rdlx**<br /><br /> **.rsds**<br /><br /> **.bism** 连接文件<br /><br /> <br /><br /> 如果 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 未出现在上下文菜单中，请确认 **“Power View 集成功能”** 已激活。<br /><br /> 默认情况下此功能是被停用的。|  

## <a name="next-steps"></a>后续步骤

[在 SharePoint 中激活报表服务器和 Power View 集成功能](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Reporting Services 网站设置和网站功能（SharePoint 模式）](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[在 SharePoint 管理中心中激活报表服务器文件同步功能](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

更多疑问？ [请访问 Reporting Services 论坛](http://go.microsoft.com/fwlink/?LinkId=620231)
