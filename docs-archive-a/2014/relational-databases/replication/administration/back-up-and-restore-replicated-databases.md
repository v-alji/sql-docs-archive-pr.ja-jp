---
title: レプリケートされたデータベースのバックアップと復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- backups [SQL Server replication]
- administering replication, restoring
- backing up replicated databases
- backups [SQL Server replication], about backups
- restoring replicated databases [SQL Server replication]
- recovery [SQL Server replication], about recovery
- restoring databases [SQL Server], replicated databases
- backing up databases [SQL Server], replicated databases
- restoring [SQL Server replication], about restoring
- recovery [SQL Server replication]
- replication [SQL Server], administering
- distribution databases [SQL Server replication], backing up
- restoring [SQL Server replication]
- administering replication, backing up
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e91505bacf67f7f4628bd1b3f6b2cc78a6bc4c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641623"
---
# <a name="back-up-and-restore-replicated-databases"></a><span data-ttu-id="f92ef-102">レプリケートされたデータベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="f92ef-102">Back Up and Restore Replicated Databases</span></span>
  <span data-ttu-id="f92ef-103">レプリケートされたデータベースでは、データのバックアップと復元に対する特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="f92ef-103">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="f92ef-104">このトピックでは、それぞれの種類のレプリケーションのバックアップと復元の方法に関する概要、および詳細情報へのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="f92ef-104">This topic provides introductory information and links to further information on backup and restore strategies for each type of replication.</span></span>  
  
 <span data-ttu-id="f92ef-105">レプリケーションでは、レプリケートされたデータベースをバックアップ作成元のサーバーおよびデータベースに復元する操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f92ef-105">Replication supports restoring replicated databases to the same server and database from which the backup was created.</span></span> <span data-ttu-id="f92ef-106">レプリケートされたデータベースのバックアップを別のサーバーまたはデータベースに復元する場合は、レプリケーションの設定は保存できません。</span><span class="sxs-lookup"><span data-stu-id="f92ef-106">If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved.</span></span> <span data-ttu-id="f92ef-107">この場合、バックアップが復元された後で、すべてのパブリケーションとサブスクリプションを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-107">In this case, you must recreate all publications and subscriptions after backups are restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f92ef-108">ログ配布が使用されている場合は、レプリケートされたデータベースをスタンバイ サーバーに復元できます。</span><span class="sxs-lookup"><span data-stu-id="f92ef-108">It is possible to restore a replicated database to a standby server if log shipping is being used.</span></span> <span data-ttu-id="f92ef-109">詳細については、[ログ配布とレプリケーション &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f92ef-109">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="f92ef-110">レプリケートされたデータベースと関連付けられているシステム データベースは、定期的にバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-110">Replicated databases and their associated system databases should be backed up regularly.</span></span> <span data-ttu-id="f92ef-111">次のデータベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="f92ef-111">Back up the following databases:</span></span>  
  
-   <span data-ttu-id="f92ef-112">パブリッシャーにあるパブリケーション データベース</span><span class="sxs-lookup"><span data-stu-id="f92ef-112">The publication database at the Publisher</span></span>  
  
-   <span data-ttu-id="f92ef-113">ディストリビューターにあるディストリビューション データベース</span><span class="sxs-lookup"><span data-stu-id="f92ef-113">The distribution database at the Distributor</span></span>  
  
-   <span data-ttu-id="f92ef-114">各サブスクライバーにあるサブスクリプション データベース</span><span class="sxs-lookup"><span data-stu-id="f92ef-114">The subscription database at each Subscriber</span></span>  
  
-   <span data-ttu-id="f92ef-115">パブリッシャー、ディストリビューター、およびすべてのサブスクライバーにある **master** および **msdb** システム データベース。</span><span class="sxs-lookup"><span data-stu-id="f92ef-115">The **master** and **msdb** system databases at the Publisher, Distributor and all Subscribers.</span></span> <span data-ttu-id="f92ef-116">これらのデータベースは、相互に関連するレプリケーション データベースとして、同時にバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-116">These databases should be backed up at the same time as each other and the relevant replication database.</span></span> <span data-ttu-id="f92ef-117">たとえば、パブリッシャーでパブリケーション データベースをバックアップするときに、 **master** および **msdb** データベースも同時にバックアップします。</span><span class="sxs-lookup"><span data-stu-id="f92ef-117">For example, back up the **master** and **msdb** databases at the Publisher at the same time you back up the publication database.</span></span> <span data-ttu-id="f92ef-118">パブリケーション データベースを復元するときは、 **master** および **msdb** データベースのレプリケーションの構成と設定が、パブリケーション データベースと一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f92ef-118">If the publication database is restored, ensure that the **master** and **msdb** database are consistent with the publication database in terms of replication configuration and settings.</span></span>  
  
 <span data-ttu-id="f92ef-119">定期的なログ バックアップを実行する場合は、レプリケーション関連の変更をログ バックアップでキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-119">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="f92ef-120">ログ バックアップを実行しない場合は、レプリケーションに関連する設定を変更するたびに、バックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-120">If you do not perform log backups, a backup should be performed whenever a setting relevant to replication is changed.</span></span> <span data-ttu-id="f92ef-121">詳細については、「 [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f92ef-121">For more information, see [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md).</span></span>  
  
## <a name="backup-and-restore-strategies"></a><span data-ttu-id="f92ef-122">バックアップと復元の方法</span><span class="sxs-lookup"><span data-stu-id="f92ef-122">Backup and Restore Strategies</span></span>  
 <span data-ttu-id="f92ef-123">レプリケーション トポロジの各ノードのバックアップと復元の方法は、使用されるレプリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-123">The strategies for backing up and restoring each node in a replication topology differ according to the type of replication used.</span></span> <span data-ttu-id="f92ef-124">それぞれの種類のレプリケーションのバックアップと復元の方法の詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f92ef-124">For information on backup and restore strategies for each type of replication, see the following topics:</span></span>  
  
-   [<span data-ttu-id="f92ef-125">スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式</span><span class="sxs-lookup"><span data-stu-id="f92ef-125">Strategies for Backing Up and Restoring Snapshot and Transactional Replication</span></span>](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [<span data-ttu-id="f92ef-126">マージ レプリケーションのバックアップと復元の方式</span><span class="sxs-lookup"><span data-stu-id="f92ef-126">Strategies for Backing Up and Restoring Merge Replication</span></span>](strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 <span data-ttu-id="f92ef-127">どの方法で復元を行う場合でも、必ずレプリケーションの設定の現在のスクリプトを安全な場所に保管しておいてください。</span><span class="sxs-lookup"><span data-stu-id="f92ef-127">As part of any recovery strategy, always keep a current script of your replication settings in a safe location.</span></span> <span data-ttu-id="f92ef-128">サーバーで障害が発生した場合やテスト環境をセットアップする必要がある場合は、サーバー名の参照を変更してスクリプトを修正し、そのスクリプトをレプリケーションの設定の再作成に利用することができます。</span><span class="sxs-lookup"><span data-stu-id="f92ef-128">In the event of server failure or the need to set up a test environment, you can modify the script by changing server name references, and it can be used to help recreate your replication settings.</span></span> <span data-ttu-id="f92ef-129">現在のレプリケーションの設定用のスクリプトの他に、レプリケーションを有効にするスクリプトと無効にするスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f92ef-129">In addition to scripting your current replication settings, you should script the enabling and disabling of replication.</span></span> <span data-ttu-id="f92ef-130">レプリケーション オブジェクトのスクリプトの作成方法の詳細については、「 [Scripting Replication](../scripting-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f92ef-130">For information about scripting replication objects, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f92ef-131">参照</span><span class="sxs-lookup"><span data-stu-id="f92ef-131">See Also</span></span>  
 <span data-ttu-id="f92ef-132">[SQL Server データベースのバックアップと復元](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f92ef-132">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="f92ef-133">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="f92ef-133">Best Practices for Replication Administration</span></span>](best-practices-for-replication-administration.md)  
  
  
