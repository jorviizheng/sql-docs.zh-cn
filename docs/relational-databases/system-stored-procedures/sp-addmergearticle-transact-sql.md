---
title: sp_addmergearticle (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addmergearticle
- sp_addmergearticle_TSQL
helpviewer_keywords:
- sp_addmergearticle
ms.assetid: 0df654ea-24e2-4c61-a75a-ecaa7a140a6c
caps.latest.revision: 69
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d60ceb96dfaf5f690a8485c74648707da0ae59ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="spaddmergearticle-transact-sql"></a>sp_addmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在现有合并发布中添加项目。 在发布服务器的发布数据库上执行此存储的过程。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_addmergearticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @source_object = ] 'source_object'   
    [ , [ @type = ] 'type' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @column_tracking = ] 'column_tracking' ]   
    [ , [ @status = ] 'status' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @subset_filterclause = ] 'subset_filterclause' ]   
    [ , [ @article_resolver = ] 'article_resolver' ]   
    [ , [ @resolver_info = ] 'resolver_info' ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @verify_resolver_signature = ] verify_resolver_signature ]   
    [ , [ @destination_object = ] 'destination_object' ]   
    [ , [ @allow_interactive_resolver = ] 'allow_interactive_resolver' ]   
    [ , [ @fast_multicol_updateproc = ] 'fast_multicol_updateproc' ]   
    [ , [ @check_permissions = ] check_permissions ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @published_in_tran_pub = ] 'published_in_tran_pub' ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection' ]  
    [ , [ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution' ]  
    [ , [ @partition_options = ] partition_options ]  
    [ , [ @processing_order = ] processing_order ]  
    [ , [ @subscriber_upload_options = ] subscriber_upload_options ]  
    [ , [ @identityrangemanagementoption = ] 'identityrangemanagementoption' ]  
    [ , [ @delete_tracking = ] delete_tracking ]  
    [ , [ @compensate_for_errors = ] 'compensate_for_errors' ]   
    [ , [ @stream_blob_columns = ] 'stream_blob_columns' ]  
```  
  
## <a name="arguments"></a>参数  
 [  **@publication=** ] *****发布*****  
 包含项目的发布的名称。 *发布*是**sysname**，无默认值。  
  
 [  **@article=** ] *****文章*****  
 项目的名称。 该名称在发布中必须唯一。 *文章*是**sysname**，无默认值。 *文章*必须运行的本地计算机上[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，并且必须符合标识符的规则。  
  
 [  **@source_object=** ] *****source_object*****  
 要发布的数据库对象。 *source_object*是**sysname**，无默认值。 有关可以使用合并复制发布的对象的类型的详细信息，请参阅[发布数据和数据库对象](../../relational-databases/replication/publish/publish-data-and-database-objects.md)。  
  
 [ **@type=** ] **'***type***'**  
 项目的类型。 *类型*是**sysname**，默认值为**表**，和可以是以下值之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|**表**（默认值）|具有架构和数据的表。 复制会监视该表以确定要复制的数据。|  
|**仅限 func 架构**|仅具有架构的函数。|  
|**索引视图****仅限架构**|仅具有架构的索引视图。|  
|**仅限 proc 架构**|仅具有架构的存储过程。|  
|**仅限同义词架构**|仅具有架构的同义词。|  
|**仅限视图架构**|仅具有架构的视图。|  
  
 [  **@description=** ] *****说明*****  
 是文章的描述。 *说明*是**nvarchar （255)**，默认值为 NULL。  
  
 [  **@column_tracking=** ] *****column_tracking*****  
 列级跟踪的设置。 *column_tracking*是**nvarchar(10)**，默认值为 FALSE。 **true**开启列跟踪。 **false**关闭列跟踪，并保留在行级冲突检测。 如果已经在其他合并发布中发布过该表，则使用的列跟踪值必须与基于此表的现有项目所用的值相同。 此参数只适用于表项目。  
  
> [!NOTE]  
>  如果行跟踪用于冲突检测（默认值），则基表最多可包含 1,024 列，但是必须从项目中筛选列，以便最多发布 246 列。 如果使用列跟踪，则基表最多可包含 246 列。  
  
 [  **@status=** ] *****状态*****  
 项目的状态。 *状态*是**nvarchar(10)**，默认值为**unsynced**。 如果**active**，运行要发布的表的初始处理脚本。 如果**unsynced**，在下次运行快照代理运行要发布的表的初始处理脚本。  
  
 [  **@pre_creation_cmd=** ] *****pre_creation_cmd*****  
 指定应用快照时，如果订阅服务器上存在该表，系统将采取的操作。 *pre_creation_cmd*是**nvarchar(10)**，和可以是以下值之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|**无**|如果订阅服务器上已存在该表，则不执行任何操作。|  
|**删除**|根据子集筛选器中的 WHERE 子句发出 delete 命令。|  
|**删除**（默认值）|删除该表，然后重新创建一个表。 需要该项以支持[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssEW](../../includes/ssew-md.md)]订阅服务器。|  
|**truncate**|截断目标表。|  
  
 [  **@creation_script=** ] *****creation_script*****  
 用于创建订阅数据库中项目的可选项目架构脚本的路径和名称。 *creation_script*是**nvarchar （255)**，默认值为 NULL。  
  
> [!NOTE]  
>  创建脚本不在 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 订阅服务器上运行。  
  
 [  **@schema_option=** ] *schema_option*  
 给定项目的架构生成选项的位图。 *schema_option*是**binary （8)**，并且可以[|（位或）](../../t-sql/language-elements/bitwise-or-transact-sql.md)产品的一个或多个这些值。  
  
|“值”|Description|  
|-----------|-----------------|  
|**0x00**|禁用脚本由快照代理，并使用提供的架构预创建脚本中定义*creation_script*。|  
|**0x01**|生成对象创建（CREATE TABLE、CREATE PROCEDURE 等）。 这是存储过程项目的默认值。|  
|**0x10**|生成对应的聚集索引。 即使不设置此选项，但如果已在已发布的表中定义与主键相关的索引以及 UNIQUE 约束，那么也会生成它们。|  
|**0x20**|在订阅服务器中将用户定义数据类型 (UDT) 转换为基本数据类型。 如果 UDT 列是主键的一部分或者计算列引用 UDT 列，则当 UDT 列上具有 CHECK 或 DEFAULT 约束时，此选项无法使用。|  
|**0x40**|生成相应的非聚集索引。 即使不设置此选项，但如果已在已发布的表中定义与主键相关的索引以及 UNIQUE 约束，那么也会生成它们。|  
|**0x80**|复制 PRIMARY KEY 约束。 也会复制任何相关的约束的索引，即使选项**0x10**和**0x40**未启用。|  
|**0x100**|如果已定义，则复制表项目的用户触发器。|  
|**0x200**|复制 FOREIGN KEY 约束。 如果被引用的表不是发布的一部分，则不会复制已发布表的任何 FOREIGN KEY 约束。|  
|**0x400**|将复制 CHECK 约束。|  
|**0x800**|复制默认值。|  
|**0x1000**|复制列级排序规则。|  
|**0x2000**|复制与已发布项目源对象关联的扩展属性。|  
|**0x4000**|复制 UNIQUE 约束。 也会复制任何相关的约束的索引，即使选项**0x10**和**0x40**未启用。|  
|**0x8000**|此选项对运行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本的发布服务器无效。|  
|**0x10000**|以 NOT FOR REPLICATION 方式复制 CHECK 约束，以便在同步期间不强制执行约束。|  
|**0x20000**|以 NOT FOR REPLICATION 方式复制 FOREIGN KEY 约束，以便在同步期间不强制执行约束。|  
|**而 0x40000 可**|复制与已分区表或已分区索引相关联的文件组。|  
|**0x80000**|复制已分区表的分区方案。|  
|**0x100000**|复制已分区索引的分区方案。|  
|**0x200000**|复制表统计信息。|  
|**0x400000**|复制默认绑定。|  
|**0x800000**|复制规则绑定。|  
|**0x1000000**|将复制的全文索引。|  
|**0x2000000**|XML 架构集合绑定到**xml**列不会复制。|  
|**0x4000000**|在复制索引**xml**列。|  
|**0x8000000**|创建订阅服务器没有的任何架构。|  
|**0x10000000**|将转换**xml**列**ntext**订阅服务器上。|  
|**0x20000000**|将大型对象数据类型 (**nvarchar (max)**， **varchar （max)**，和**varbinary （max)**) 中引入[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]上支持的数据类型[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|复制权限。|  
|**0x80000000**|尝试删除不属于发布的任何对象的依赖关系。|  
|**0x100000000**|使用此选项用于复制 FILESTREAM 属性，如果在指定**varbinary （max)** 列。 如果要将表复制到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 订阅服务器，请勿指定此选项。 包含 FILESTREAM 列的表复制[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]不支持订阅服务器，而不考虑如何设置此架构选项。 请参阅相关的选项**0x800000000**。|  
|**0x200000000**|将日期和时间数据类型转换 (**日期**，**时间**， **datetimeoffset**，和**datetime2**) 中引入[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]到数据在早期版本的支持的类型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|**0x400000000**|复制数据和索引的压缩选项。 有关详细信息，请参阅 [Data Compression](../../relational-databases/data-compression/data-compression.md)。|  
|**0x800000000**|设置此选项可将 FILESTREAM 数据存储到订阅服务器上其自身的文件组中。 如果不设置此选项，FILESTREAM 数据将存储在默认文件组中。 由于复制操作不创建文件组，因此如果您设置此选项，您必须先创建文件组，然后在订阅服务器上应用快照。 有关如何在应用快照之前创建对象的详细信息，请参阅[将脚本执行之前和之后应用快照](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)。<br /><br /> 请参阅相关的选项**0x100000000**。|  
|**0x1000000000**|将公共语言运行时 (CLR) 用户定义类型 (Udt) 转换为**varbinary （max)** 以便类型 UDT 的列可以复制到订阅服务器运行[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。|  
|**0x2000000000**|将转换**hierarchyid**数据类型设置为**varbinary （max)** 以便类型的列**hierarchyid**可以复制到订阅服务器运行[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。 有关如何使用**hierarchyid**列中复制的表，请参阅[hierarchyid &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)。|  
|**0x4000000000**|复制表的任何筛选的索引。 有关筛选的索引的详细信息，请参阅[Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)。|  
|**0x8000000000**|将转换**geography**和**几何图形**数据类型到**varbinary （max)** ，以便这些类型的列可以复制到订阅服务器运行[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|复制类型的列的索引**geography**和**几何图形**。|  
  
 如果此值为 NULL，则系统将自动为项目生成一个有效的架构选项。 **默认架构选项**备注部分中的表显示选择基于该项目类型的值。 此外，并非所有*schema_option*值也适用于每种类型的复制和项目的类型。 **有效架构选项**备注中给定的表显示可以为指定的项目类型中指定的选项。  
  
> [!NOTE]  
>  *Schema_option*参数仅影响对初始快照的复制选项。 发布架构更改复制到订阅服务器生成的快照代理并应用到订阅服务器的初始架构后，会根据架构更改复制规则和*replicate_ddl*中指定的参数设置[sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)。 有关详细信息，请参阅[对发布数据库进行架构更改](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)。  
  
 [  **@subset_filterclause=** ] *****subset_filterclause*****  
 WHERE 子句，用于指定表项目的水平筛选，但不含单词 WHERE。 *subset_filterclause*的**nvarchar(1000)**，默认值为空字符串。  
  
> [!IMPORTANT]  
>  为提高性能，建议您不要在参数化行筛选子句中对列名应用函数，如 `LEFT([MyColumn]) = SUSER_SNAME()`。 如果你使用[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)在筛选器子句和替代 HOST_NAME 值中，你可能需要将数据类型转换使用[转换](../../t-sql/functions/cast-and-convert-transact-sql.md)。 有关这种情况下的最佳实践的详细信息，请参阅"重写 host_name （） 值"一节中[参数化行筛选器](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)。  
  
 [  **@article_resolver=** ] *****article_resolver*****  
 基于 COM 的冲突解决程序，用于解决表项目中的冲突或解决调用来对表项目执行自定义业务逻辑的 .NET Framework 程序集中的冲突。 *article_resolver*是**varchar(255)**，默认值为 NULL。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 自定义冲突解决程序中列出了此参数的可用值。 如果提供的值并不属于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 冲突解决程序，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将使用指定的冲突解决程序代替系统提供的冲突解决程序。 使用**sp_enumcustomresolvers**枚举可用的自定义冲突解决程序的列表。 有关详细信息，请参阅[执行合并同步期间业务逻辑](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)和[高级合并复制冲突检测和解决](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)。  
  
 [  **@resolver_info=** ] *****resolver_info*****  
 用于指定自定义冲突解决程序所需的其他信息。 某些 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 冲突解决程序需要提供列作为冲突解决程序的输入。 *resolver_info*是**nvarchar （255)**，默认值为 NULL。 有关详细信息，请参阅 [Microsoft 基于 COM 的冲突解决程序](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)。  
  
 [  **@source_owner=** ] *****source_owner*****  
 是的所有者的名称*source_object*。 *source_owner*是**sysname**，默认值为 NULL。 如果值为 NULL，则假定当前用户为所有者。  
  
 [  **@destination_owner=** ] *****destination_owner*****  
 订阅数据库中对象的所有者（如果不是“dbo”）。 *destination_owner*是**sysname**，默认值为 NULL。 如果值为 NULL，则假定‘dbo’为所有者。  
  
 [  **@vertical_partition=** ] *****column_filter*****  
 启用和禁用对表项目的列筛选。 *vertical_partition*是**nvarchar(5)** 默认值为 FALSE。  
  
 **false**指示没有垂直筛选并发布所有列。  
  
 **true**清除除声明主键外的所有列和 ROWGUID 列。 列通过使用添加**sp_mergearticlecolumn**。  
  
 [  **@auto_identity_range=** ] *****automatic_identity_range*****  
 在创建表项目时允许或禁止在发布中对此表项目执行自动标识范围处理。 *auto_identity_range*是**nvarchar(5)**，默认值为 FALSE。 **true**启用自动标识范围处理，而**false**禁用它。  
  
> [!NOTE]  
>  *auto_identity_range*已弃用，为了向后兼容性。 应使用*identityrangemanagementoption*用于指定标识范围管理选项。 有关详细信息，请参阅[复制标识列](../../relational-databases/replication/publish/replicate-identity-columns.md)。  
  
 [  **@pub_identity_range=** ] *pub_identity_range*  
 使用自动标识范围管理时，控制分配给包含服务器订阅的订阅服务器的标识范围大小。 此标识范围是为重新发布订阅服务器保留的，用于分配给其自身的订阅服务器。 *pub_identity_range*是**bigint**，默认值为 NULL。 如果必须指定此参数*identityrangemanagementoption*是**自动**或如果*auto_identity_range*是**true**。  
  
 [  **@identity_range=** ] *identity_range*  
 使用自动标识范围管理时，控制分配给发布服务器和订阅服务器的标识范围大小。 *identity_range*是**bigint**，默认值为 NULL。 如果必须指定此参数*identityrangemanagementoption*是**自动**或如果*auto_identity_range*是**true**。  
  
> [!NOTE]  
>  *identity_range*控制在重新发布订阅服务器使用的早期版本的标识范围大小[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 [  **@threshold=** ]*阈值*  
 百分比值，用于控制合并代理分配新标识范围的条件。 如果在中指定值的百分比*阈值*是使用，合并代理创建的新标识范围。 *阈值*是**int**，默认值为 NULL。 如果必须指定此参数*identityrangemanagementoption*是**自动**或如果*auto_identity_range*是**true**。  
  
 [  **@verify_resolver_signature=** ] *verify_resolver_signature*  
 指定在合并复制中使用冲突解决程序之前是否验证数字签名。 *verify_resolver_signature*是**int**，默认值为 1。  
  
 **0**指定签名不进行验证。  
  
 **1**指定将验证的签名以查看它是否来自可靠来源。  
  
 [  **@destination_object=** ] *****destination_object*****  
 订阅数据库中的对象的名称。 *destination_object*是**sysname**，使用默认值中的新增功能**@source_object**。 仅当项目为仅架构项目（如存储过程、视图和 UDF 等）时，才能指定此参数。 如果指定的文章是表项目中的值*@source_object*重写中的值*destination_object*。  
  
 [  **@allow_interactive_resolver=** ] *****allow_interactive_resolver*****  
 启用或禁用对项目使用交互式冲突解决程序。 *allow_interactive_resolver*是**nvarchar(5)**，默认值为 FALSE。 **true**启用在文章; 交互式冲突解决程序的使用**false**禁用它。  
  
> [!NOTE]  
>  [!INCLUDE[ssEW](../../includes/ssew-md.md)] 订阅服务器不支持交互式冲突解决程序。  
  
 [  **@fast_multicol_updateproc=** ] *****fast_multicol_updateproc*****  
 不推荐使用此参数，保留它是为了让脚本能够向后兼容。  
  
 [  **@check_permissions=** ] *check_permissions*  
 表级权限的位图，合并代理将更改应用于发布服务器时将验证该权限。 如果合并进程使用的发布服务器登录名/用户帐户没有正确的表权限，则无效更改将被记录为冲突。 *check_permissions*是**int**，并且可以[|（位或）](../../t-sql/language-elements/bitwise-or-transact-sql.md)产品的一个或多个以下的值。  
  
|“值”|Description|  
|-----------|-----------------|  
|**0x00** （默认值）|不检查权限。|  
|**0x10**|检查了发布服务器上的权限后，才能上载订阅服务器上的插入操作。|  
|**0x20**|检查了发布服务器上的权限后，才能上载订阅服务器上的更新操作。|  
|**0x40**|检查了发布服务器上的权限后，才能上载订阅服务器上的删除操作。|  
  
 [  **@force_invalidate_snapshot=** ] *force_invalidate_snapshot*  
 确认此存储过程所执行的操作是否会使现有快照失效。 *force_invalidate_snapshot*是**位**，默认值为 0。  
  
 **0**指定将项目添加不会导致快照无效。 如果该存储过程检测到更改确实需要新的快照，则会发生错误，并且不进行任何更改。  
  
 **1**指定添加项目可能会导致快照无效，并且需要一次新快照的现有订阅是否可以为现有的快照将被标记为过时和新的快照生成授予的权限。 *force_invalidate_snapshot*设置为**1**与现有的快照发布添加项目时。  
  
 [  **@published_in_tran_pub=** ] *****published_in_tran_pub*****  
 指示合并发布中的项目也将在事务发布中发布。 *published_in_tran_pub*是**nvarchar(5)**，默认值为 FALSE。 **true**指定文章也在事务发布中发布。  
  
 [  **@force_reinit_subscription=** ] *force_reinit_subscription*  
 确认此存储过程执行的操作可能需要重新初始化现有订阅。 *force_reinit_subscription*是**位**，默认值为 0。  
  
 **0**指定将项目添加不会导致要重新初始化的订阅。 如果该存储过程检测到更改将需要重新初始化现有订阅，则会发生错误，并且不进行任何更改。  
  
 **1**更改为合并项目的方式导致现有订阅重新初始化订阅，可以授予权限，重新初始化订阅发生。 *force_reinit_subscription*设置为**1**时*subset_filterclause*指定参数化的行筛选器。  
  
 [  **@logical_record_level_conflict_detection=** ] *****logical_record_level_conflict_detection*****  
 指定作为逻辑记录成员的项目的冲突检测级别。 *logical_record_level_conflict_detection*是**nvarchar(5)**，默认值为 FALSE。  
  
 **true**指定是否逻辑记录中任意位置进行更改，将检测冲突。  
  
 **false**指定使用默认冲突检测所指定的*column_tracking*。 有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)。  
  
> [!NOTE]  
>  因为不支持逻辑记录[!INCLUDE[ssEW](../../includes/ssew-md.md)]订阅服务器，你必须指定的值**false**为*logical_record_level_conflict_detection*以支持这些订阅服务器。  
  
 [  **@logical_record_level_conflict_resolution=** ] *****logical_record_level_conflict_resolution*****  
 为作为逻辑记录成员的项目指定冲突解决级别。 *logical_record_level_conflict_resolution*是**nvarchar(5)**，默认值为 FALSE。  
  
 **true**指定整个入选逻辑记录覆盖落选的逻辑记录。  
  
 **false**指定入选行并不限于逻辑记录。 如果*logical_record_level_conflict_detection*是**true**，然后*logical_record_level_conflict_resolution*还必须设置为**true**. 有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)。  
  
> [!NOTE]  
>  因为不支持逻辑记录[!INCLUDE[ssEW](../../includes/ssew-md.md)]订阅服务器，你必须指定的值**false**为*logical_record_level_conflict_resolution*以支持这些订阅服务器。  
  
 [  **@partition_options=** ] *partition_options*  
 定义项目数据的分区方式，当所有行只属于一个分区或只属于一个订阅时，这将可以实现性能优化。 *partition_options*是**tinyint**，和可以是以下值之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|**0** （默认值）|项目的筛选是静态的，或者不会为每个分区生成一个唯一数据子集（即“重叠”分区）。|  
|**1**|分区是重叠的，订阅服务器中执行的数据操作语言 (DML) 更新不能更改行所属的分区。|  
|**2**|对项目的筛选将生成不重叠分区，但多个订阅服务器可以接收到相同的分区。|  
|**3**|对项目的筛选将为每个订阅生成唯一的不重叠分区。|  
  
> [!NOTE]  
>  如果在另一个发布，则的值已发布文章的源表*partition_options*必须是相同的这两篇文章。  
  
 [  **@processing_order=** ] *processing_order*  
 指示合并发布中项目的处理顺序。 *processing_order*是**int**，默认值为 0。 **0**指定文章无序，以及任何其他值表示这篇文章的处理顺序的序号值。 项目按值的由低到高顺序进行处理。 如果两个项目具有相同的值，处理顺序由顺序中的文章昵称[sysmergearticles](../../relational-databases/system-tables/sysmergearticles-transact-sql.md)系统表。 有关详细信息，请参阅[指定合并项目的处理顺序](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)。  
  
 [  **@subscriber_upload_options=** ] *subscriber_upload_options*  
 定义在包含客户端订阅的订阅服务器上进行更新的限制。 有关详细信息，请参阅[使用仅下载项目优化合并复制性能](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)。 *subscriber_upload_options*是**tinyint**，和可以是以下值之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|**0** （默认值）|无限制。 将订阅服务器上所做的更改上载到发布服务器。|  
|**1**|允许在订阅服务器上进行更改，但不将更改上载到发布服务器。|  
|**2**|不允许在订阅服务器上进行更改。|  
  
 更改*subscriber_upload_options*需要订阅，以便可通过调用[sp_reinitmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md)。  
  
> [!NOTE]  
>  如果在另一个发布的值中已发布文章的源表*subscriber_upload_options*必须是相同的这两篇文章。  
  
 [  **@identityrangemanagementoption=** ] *identityrangemanagementoption*  
 指定如何处理项目的标识范围管理。 *identityrangemanagementoption*是**nvarchar(10)**，和可以是以下值之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|**无**|禁用标识范围管理。|  
|**手动**|使用 NOT FOR REPLICATION 标记标识列，以启用手动标识范围处理。|  
|**自动**|指定自动管理标识范围。|  
|NULL（默认值）|默认为**无**时的值*auto_identity_range*不**true**。|  
  
 为了向后兼容时的值*identityrangemanagementoption*为 NULL，则这的*auto_identity_range*已选中。 但是，当的值*identityrangemanagementoption*不为 NULL，则值*auto_identity_range*将被忽略。 有关详细信息，请参阅[复制标识列](../../relational-databases/replication/publish/replicate-identity-columns.md)。  
  
 [  **@delete_tracking=** ] *****delete_tracking*****  
 指示是否复制删除操作。 *delete_tracking*是**nvarchar(5)**，默认值为 TRUE。 **false**指示，不会复制删除，和**true**指示删除已被复制，这将是为合并复制的常用行为。 当*delete_tracking*设置为**false**、 必须在发布服务器，手动删除订阅服务器上删除的行和删除发布服务器上的行都必须在订阅服务器上手动删除。  
  
> [!IMPORTANT]  
>  设置*delete_tracking*到**false**导致非收敛。 如果在另一个发布，则的值已发布文章的源表*delete_tracking*必须是相同的这两篇文章。  
  
> [!NOTE]  
>  *delete_tracking*选项不能通过设置**新建发布向导**或**发布属性**对话框。  
  
 [  **@compensate_for_errors=** ] *****compensate_for_errors*****  
 指示在同步期间遇到错误时是否采取补救措施。 *是 compensate_for_errors 我*s **nvarchar(5)**，默认值为 FALSE。 当设置为**true**，更改，无法在订阅服务器上应用或发布服务器始终同步过程会导致补偿操作要撤销此更改; 但是，其中一个不正确地配置订阅服务器生成错误可以导致要撤消其他订阅服务器和发布服务器上的更改。 **false**禁用这些补偿操作，但是，错误仍然会记录如补偿和后续合并将继续尝试应用所做的更改，直到成功为止。  
  
> [!IMPORTANT]  
>  尽管受影响行中的数据可能会无法收敛，但是只要解决了发生的错误，就可应用更改，并且数据也会收敛。 如果在另一个发布，则的值已发布文章的源表*compensate_for_errors*必须是相同的这两篇文章。  
  
 [  **@stream_blob_columns=** ] *****stream_blob_columns*****  
 指定在复制二进制大型对象列时使用数据流优化。 *stream_blob_columns*是**nvarchar(5)**，默认值为 FALSE。 **true**意味着将尝试优化。 *stream_blob_columns*设置为 true 时启用 FILESTREAM。 这使复制 FILESTREAM 数据的性能达到最佳并减少内存使用率。 若要强制 FILESTREAM 项目不使用 blob 流，请使用**sp_changemergearticle**设置*stream_blob_columns*为 false。  
  
> [!IMPORTANT]  
>  启用此内存优化可能会降低在同步期间合并代理的性能。 仅当复制包含数兆字节数据的列时，才应使用此选项。  
  
> [!NOTE]  
>  某些合并复制功能，例如逻辑记录，仍可以防止复制即使使用的二进制大型对象时所使用的流优化*stream_blob_columns*设置为**true**.  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>注释  
 **sp_addmergearticle**合并复制中使用。  
  
 发布对象时，对象的定义会复制到订阅服务器。 如果要发布的数据库对象依赖于一个或多个其他对象，则必须发布所有被引用对象。 例如，如果要发布的视图依赖于一个表，则也必须发布该表。  
  
 如果指定的值**3**为*partition_options*，可以仅单个订阅的每个分区这篇文章中的数据。 如果创建了另一个订阅，而这个新订阅的筛选条件解析到的分区与现有订阅的分区相同，则会删除现有订阅。  
  
 指定为 3 的值时*partition_options*，元数据是已清理的每次时运行合并代理和分区的快照过期得更快。 使用此选项时，应考虑启用订阅服务器请求的分区快照。 有关详细信息，请参阅 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)。  
  
 使用静态的水平筛选器添加项目、 使用*subset_filterclause*到现有发布具有参数化筛选器的项目要求重新初始化订阅。  
  
 指定时*processing_order*，我们建议文章顺序值之间留出间隙这使得更轻松地在将来设置新值。 例如，如果你有三个项目 Article1、 Article2 和 Article3，设置*processing_order*到 10、 20，和 30，而不是 1、 2 和 3。 有关详细信息，请参阅[指定合并项目的处理顺序](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)。  
  
## <a name="default-schema-option-table"></a>默认架构选项表  
 下表介绍的默认值所设置的存储过程中，如果为指定 NULL 值*schema_option*，取决于项目类型。  
  
|项目类型|架构选项值|  
|------------------|-------------------------|  
|**仅限 func 架构**|**0x01**|  
|**仅限索引的视图架构**|**0x01**|  
|**仅限 proc 架构**|**0x01**|  
|**table**|**0x0C034FD1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]和更高版本兼容发布使用本机模式快照。<br /><br /> **0x08034FF1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]和更高版本兼容发布提供字符模式快照。|  
|**仅限视图架构**|**0x01**|  
  
> [!NOTE]  
>  如果发布支持早期版本的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的默认架构选项**表**是**0x30034FF1**。  
  
## <a name="valid-schema-option-table"></a>有效架构选项表  
 下表描述了允许的值*schema_option*具体取决于项目类型。  
  
|项目类型|架构选项值|  
|------------------|--------------------------|  
|**仅限 func 架构**|**0x01**和**0x2000**|  
|**仅限索引的视图架构**|**0x01**， **0x040**， **0x0100**， **0x2000**，**而 0x40000 可**， **0x1000000**，和**0x200000**|  
|**仅限 proc 架构**|**0x01**和**0x2000**|  
|**table**|所有选项。|  
|**仅限视图架构**|**0x01**， **0x040**， **0x0100**， **0x2000**，**而 0x40000 可**， **0x1000000**，和**0x200000**|  
  
## <a name="example"></a>示例  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-addmergearticle-trans_1.sql)]  
  
## <a name="permissions"></a>权限  
 要求具有 **sysadmin** 固定服务器角色或 **db_owner** 固定数据库角色的成员身份。  
  
## <a name="see-also"></a>另请参阅  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [发布数据和数据库对象](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [复制标识列](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [复制存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
