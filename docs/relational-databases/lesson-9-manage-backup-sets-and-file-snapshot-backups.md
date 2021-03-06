---
title: 第 9 课：管理备份集和文件快照备份 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: 766a0846-db15-4346-b814-4049039bcbfc
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32a5bad72add276eae015433f697cad01b8158c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-9-manage-backup-sets-and-file-snapshot-backups"></a>第 9 课：管理备份集和文件快照备份
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
本课程中，将使用 [sp_delete_backup (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md) 系统存储过程删除备份集。 此系统存储过程会删除每个与此备份集关联的数据库文件中的备份文件和文件快照。  
  
> [!NOTE]  
> 如果试图通过仅从 Azure blob 容器中删除备份文件来删除备份集，将只删除备份文件本身，而保留相关的文件快照。 如果发现自己处于这种情况下，请使用 [sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md) 系统函数来标识孤立文件快照的 URL，并使用 [sp_delete_backup_file_snapshot (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) 系统存储过程来删除每个孤立文件快照。 有关详细信息，请参阅  [Azure 中数据库文件的文件快照备份](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)。  
  
若要删除文件快照备份集，请执行下列步骤：  
  
1.  连接到 SQL Server Management Studio。  
  
2.  打开一个新查询窗口并连接到 Azure 虚拟机中数据库引擎的 SQL Server 2016 实例（或连接到任何在此容器上具有读写权限的 SQL Server 2016 实例）。  
  
3.  复制以下 Transact-SQL 脚本，然后将其粘贴到查询窗口中。 选择想要将其及其关联的文件快照删除的日志备份。 针对第 1 课中指定的存储帐户名称和容器适当修改 URL，提供日志备份文件名称，然后执行此脚本。  
  
    ```  
  
    sys.sp_delete_backup 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-9164-20150726012420.bak';  
  
    ```  
  
4.  在对象资源管理器中，连接到 Azure 存储。  
  
5.  展开“容器”，展开第 1 课中创建的容器，并验证在步骤 3 中使用的备份文件不再出现在此容器中（如有必要，请刷新该节点）。  
  
    ![显示删除的日志备份 blob 的 Azure 容器](../relational-databases/media/c0070b08-4667-4db5-aaff-987a404ec934.JPG "显示删除的日志备份 blob 的 Azure 容器")  
  
6.  复制下列 Transact-SQL 脚本，将其粘贴到查询窗口中并执行，验证是否已删除这两个文件快照。  
  
    ```  
  
    -- verify that two file snapshots have been removed  
    SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![显示删除的 2 个文件快照的结果窗格](../relational-databases/media/f3891361-dfb6-4f4d-a090-ebfeb977981e.JPG "显示删除的 2 个文件快照的结果窗格")  
  
**教程结束**  
  
## <a name="see-also"></a>另请参阅  
[Azure 中数据库文件的文件快照备份](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sp_delete_backup (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
[sp_delete_backup_file_snapshot (Transact-SQL)](../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
  

