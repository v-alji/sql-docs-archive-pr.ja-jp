---
title: トランザクションレプリケーションの連携バックアップを有効にする (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77405cd968fa917c3ccc799eb7d168782443eee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741885"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a><span data-ttu-id="96858-102">トランザクション レプリケーションの連携バックアップの有効化 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="96858-102">Enable Coordinated Backups for Transactional Replication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="96858-103">データベースでトランザクション レプリケーションを有効にする場合、ディストリビューション データベースに配布する前にすべてのトランザクションをバックアップするように指定できます。</span><span class="sxs-lookup"><span data-stu-id="96858-103">When enabling a database for transactional replication, you can specify that all transactions must be backed up before being delivered to the distribution database.</span></span> <span data-ttu-id="96858-104">また、ディストリビューション データベースの連携バックアップを有効にして、ディストリビューターに反映されたトランザクションがバックアップされるまで、パブリケーション データベースのトランザクション ログが切り捨てられないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="96858-104">You can also enable coordinated backup on the distribution database so that the transaction log for the publication database is not truncated until transactions that have been propagated to the Distributor have been backed up.</span></span> <span data-ttu-id="96858-105">詳細については、「 [スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96858-105">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a><span data-ttu-id="96858-106">トランザクション レプリケーションでパブリッシュされたデータベースの連携バックアップを有効にするには</span><span class="sxs-lookup"><span data-stu-id="96858-106">To enable coordinated backups for a database published with transactional replication</span></span>  
  
1.  <span data-ttu-id="96858-107">パブリッシャーで、[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 関数を使用すると、パブリケーション データベースの **IsSyncWithBackup** プロパティが返されます。</span><span class="sxs-lookup"><span data-stu-id="96858-107">At the Publisher, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the publication database.</span></span> <span data-ttu-id="96858-108">この関数が **1**を返した場合、連携バックアップはパブリッシュされたデータベースに対して既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="96858-108">If the function returns **1**, coordinated backups are already enabled for the published database.</span></span>  
  
2.  <span data-ttu-id="96858-109">手順 1. の関数が **0** を返した場合、パブリッシャー側のパブリケーション データベースに対して [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="96858-109">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="96858-110">\*\* \@ Optname**に**sync with backup**を指定し、 \*\* \@ 値**に**true**を指定します。</span><span class="sxs-lookup"><span data-stu-id="96858-110">Specify a value of **sync with backup** for **\@optname**, and **true** for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96858-111">**sync with backup** オプションを **false**に変更すると、ログ リーダー エージェントが実行された後で、または一定の間隔で (ログ リーダー エージェントが継続的に実行されている場合)、パブリケーション データベースの切り捨てのポイントが更新されます。</span><span class="sxs-lookup"><span data-stu-id="96858-111">If you change the **sync with backup** option to **false**, the truncation point of the publication database will be updated after the Log Reader Agent runs, or after an interval if the Log Reader Agent is running continuously.</span></span> <span data-ttu-id="96858-112">最長間隔は、**-MessageInterval** エージェント パラメーター (既定値は 30 秒) によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="96858-112">The maximum interval is controlled by the **-MessageInterval** agent parameter (which has a default of 30 seconds).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a><span data-ttu-id="96858-113">ディストリビューション データベースの連携バックアップを有効にするには</span><span class="sxs-lookup"><span data-stu-id="96858-113">To enable coordinated backups for a distribution database</span></span>  
  
1.  <span data-ttu-id="96858-114">ディストリビューターで、[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 関数を使用すると、ディストリビューション データベースの **IsSyncWithBackup** プロパティが返されます。</span><span class="sxs-lookup"><span data-stu-id="96858-114">At the Distributor, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the distribution database.</span></span> <span data-ttu-id="96858-115">この関数が **1**を返した場合、ディストリビューション データベースの連携バックアップは既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="96858-115">If the function returns **1**, coordinated backups are already enabled for the distribution database.</span></span>  
  
2.  <span data-ttu-id="96858-116">手順 1. の関数が **0** を返した場合、ディストリビューター側のディストリビューション データベースに対して [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="96858-116">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="96858-117">\*\* \@ Optname**に**sync with backup**を指定し、 \*\* \@ 値**に**true**を指定します。</span><span class="sxs-lookup"><span data-stu-id="96858-117">Specify a value of **sync with backup** for **\@optname** and **true** for **\@value**.</span></span>  
  
### <a name="to-disable-coordinated-backups"></a><span data-ttu-id="96858-118">連携バックアップを無効にするには</span><span class="sxs-lookup"><span data-stu-id="96858-118">To disable coordinated backups</span></span>  
  
1.  <span data-ttu-id="96858-119">パブリッシャーのパブリケーション データベースで、またはディストリビューターのディストリビューション データベースで、[sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="96858-119">At either the Publisher on the publication database or at the Distributor on the distribution database, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span> <span data-ttu-id="96858-120">\*\* \@ Optname**に**sync with backup**を指定し、 \*\* \@ 値**に**false**を指定します。</span><span class="sxs-lookup"><span data-stu-id="96858-120">Specify a value of **sync with backup** for **\@optname** and **false** for **\@value**.</span></span>  
  
  
