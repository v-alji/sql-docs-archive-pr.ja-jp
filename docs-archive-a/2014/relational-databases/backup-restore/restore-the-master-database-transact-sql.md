---
title: master データベースの復元 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c9cb078b7af60fc5e060bcb144fc9cbaee8ecf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643419"
---
# <a name="restore-the-master-database-transact-sql"></a><span data-ttu-id="54d2a-102">master データベースの復元 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="54d2a-102">Restore the master Database (Transact-SQL)</span></span>
  <span data-ttu-id="54d2a-103">このトピックでは、データベースの完全バックアップから **master** データベースを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-103">This topic explains how to restore the **master** database from a full database backup.</span></span>  
  
### <a name="to-restore-the-master-database"></a><span data-ttu-id="54d2a-104">master データベースを復元するには</span><span class="sxs-lookup"><span data-stu-id="54d2a-104">To restore the master database</span></span>  
  
1.  <span data-ttu-id="54d2a-105">サーバー インスタンスをシングル ユーザー モードで起動します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-105">Start the server instance in single-user mode.</span></span>  
  
     <span data-ttu-id="54d2a-106">シングル ユーザー スタートアップ パラメーター ( **-m**) の指定方法の詳細については、「[サーバーのスタートアップ オプションの構成 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54d2a-106">For information about how to specify the single-user startup parameter (**-m**), see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
2.  <span data-ttu-id="54d2a-107">**master**データベースの完全バックアップを復元するには、次の [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します:</span><span class="sxs-lookup"><span data-stu-id="54d2a-107">To restore a full database backup of **master**, use the following [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="54d2a-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span><span class="sxs-lookup"><span data-stu-id="54d2a-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span></span>  
  
     <span data-ttu-id="54d2a-109">REPLACE オプションは、指定したデータベースと同じ名前のデータベースが既に存在していても、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でデータベースを復元することを指定します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-109">The REPLACE option instructs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to restore the specified database even when a database of the same name already exists.</span></span> <span data-ttu-id="54d2a-110">既存のデータベースがある場合は削除されます。</span><span class="sxs-lookup"><span data-stu-id="54d2a-110">The existing database, if any, is deleted.</span></span> <span data-ttu-id="54d2a-111">シングル ユーザー モードでは、 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)で RESTORE DATABASE ステートメントを入力することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="54d2a-111">In single-user mode, we recommend that you enter the RESTORE DATABASE statement in the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="54d2a-112">詳細については、「 [sqlcmd Utility の使用](../scripting/sqlcmd-use-the-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54d2a-112">For more information, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="54d2a-113">**master** の復元後、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスがシャットダウンされ、 **sqlcmd** プロセスが終了します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-113">After **master** is restored, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] shuts down and terminates the **sqlcmd** process.</span></span> <span data-ttu-id="54d2a-114">サーバー インスタンスを再起動する前に、シングル ユーザーの起動時のパラメーターを削除してください。</span><span class="sxs-lookup"><span data-stu-id="54d2a-114">Before you restart the server instance, remove the single-user startup parameter.</span></span> <span data-ttu-id="54d2a-115">詳細については、「[サーバーのスタートアップ オプションの構成 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54d2a-115">For more information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
3.  <span data-ttu-id="54d2a-116">サーバー インスタンスを再起動し、他のデータベースの復元、データベースのインポート、ユーザーの不一致の修正など、残りの復旧手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-116">Restart the server instance and continue other recovery steps such as restoring other databases, attaching databases, and correcting user mismatches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54d2a-117">例</span><span class="sxs-lookup"><span data-stu-id="54d2a-117">Example</span></span>  
 <span data-ttu-id="54d2a-118">次の例では、既定のサーバー インスタンスで `master` データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-118">The following example restores the `master` database on the default server instance.</span></span> <span data-ttu-id="54d2a-119">この例では、サーバー インスタンスが既にシングル ユーザー モードで実行されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="54d2a-119">The example assumes that the server instance is already running in single-user mode.</span></span> <span data-ttu-id="54d2a-120">この例は、 `sqlcmd` を起動し、ディスク デバイス `RESTORE DATABASE` から `master` データベースの完全バックアップを復元する `Z:\SQLServerBackups\master.bak`ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="54d2a-120">The example starts `sqlcmd` and executes a `RESTORE DATABASE` statement that restores a full database backup of `master` from a disk device: `Z:\SQLServerBackups\master.bak`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54d2a-121">名前付きインスタンスの場合は、**sqlcmd** コマンドで、 **-S** _\<ComputerName>_ \\ *\<InstanceName>* オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54d2a-121">For a named instance, the **sqlcmd** command must specify the **-S**_\<ComputerName>_\\*\<InstanceName>* option.</span></span>  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="54d2a-122">参照</span><span class="sxs-lookup"><span data-stu-id="54d2a-122">See Also</span></span>  
 <span data-ttu-id="54d2a-123">[データベースの全体復元 &#40;単純復旧モデル&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-123">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="54d2a-124">[データベースの全体復元 &#40;完全復旧モデル&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-124">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="54d2a-125">[孤立ユーザーのトラブルシューティング &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-125">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 <span data-ttu-id="54d2a-126">[データベースのデタッチとアタッチ &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-126">[Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="54d2a-127">[システム データベースの再構築](../databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-127">[Rebuild System Databases](../databases/system-databases.md) </span></span>  
 <span data-ttu-id="54d2a-128">[データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-128">[Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span></span>  
 <span data-ttu-id="54d2a-129">[SQL Server 構成マネージャー](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-129">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="54d2a-130">[システム データベースのバックアップと復元 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="54d2a-130">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="54d2a-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54d2a-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="54d2a-132">シングル ユーザー モードでの SQL Server の起動</span><span class="sxs-lookup"><span data-stu-id="54d2a-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
