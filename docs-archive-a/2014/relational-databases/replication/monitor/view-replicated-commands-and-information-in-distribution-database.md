---
title: ディストリビューションデータベースにレプリケートされたコマンドおよびその他の情報を表示する (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb5850277d685f2ecf6471fa4bf9814579b2843e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741806"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a><span data-ttu-id="278d4-102">レプリケートされたコマンドなどディストリビューション データベースに格納されている情報を表示する (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="278d4-102">View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="278d4-103">トランザクション レプリケーションでは、トランザクション コマンドが、ディストリビューション エージェントによってすべてのサブスクライバーに反映されるか、サブスクライバーのディストリビューション エージェントによって変更が抽出されるまで、ディストリビューション データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="278d4-103">When using transactional replication, transaction commands are stored in the distribution database until the Distribution Agent propagates them to all Subscribers or a Distribution Agent at the Subscriber pulls the changes.</span></span> <span data-ttu-id="278d4-104">ディストリビューション データベース内で保留状態のコマンドは、レプリケーションのストアド プロシージャを使用してプログラムから表示できます。</span><span class="sxs-lookup"><span data-stu-id="278d4-104">These pending commands in the distribution database can be viewed programmatically using replication stored procedures.</span></span> <span data-ttu-id="278d4-105">詳細については、「[Replication Stored Procedures &#40;Transact-SQL&#41; (レプリケーションのストアド プロシージャ &#40;Transact-SQL&#41;)](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="278d4-105">For more information, see [Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).</span></span>  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a><span data-ttu-id="278d4-106">すべてのトランザクション パブリケーションからディストリビューション データベース内のレプリケートされたコマンドを表示するには</span><span class="sxs-lookup"><span data-stu-id="278d4-106">To view replicated commands from all transactional publications in the distribution database</span></span>  
  
1.  <span data-ttu-id="278d4-107">ディストリビューターのディストリビューション データベースで [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="278d4-107">At the Distributor on the distribution database, execute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).</span></span>  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a><span data-ttu-id="278d4-108">トランザクション レプリケーションを使用してパブリッシュされた特定のアーティクルまたは特定のデータベースから、ディストリビューション データベース内のレプリケートされたコマンドを表示するには</span><span class="sxs-lookup"><span data-stu-id="278d4-108">To view replicated commands in the distribution database from a specific article or from a specific database published using transactional replication</span></span>  
  
1.  <span data-ttu-id="278d4-109">(省略可) パブリッシャーのパブリケーション データベースで [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="278d4-109">(Optional) At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="278d4-110">\*\* \@ パブリケーション**と** \@ アーティクル\*\*を指定します。</span><span class="sxs-lookup"><span data-stu-id="278d4-110">Specify **\@publication** and **\@article**.</span></span> <span data-ttu-id="278d4-111">結果セットの **article id** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="278d4-111">Note the value of **article id** in the result set.</span></span>  
  
2.  <span data-ttu-id="278d4-112">ディストリビューターのディストリビューション データベースで [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="278d4-112">At the Distributor on the distribution database, execute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).</span></span> <span data-ttu-id="278d4-113">Optional手順 2. のアーティクル ID を\*\* \@ article_id\*\*に指定します。</span><span class="sxs-lookup"><span data-stu-id="278d4-113">(Optional) Specify the article ID from step 2 for **\@article_id**.</span></span> <span data-ttu-id="278d4-114">Optional\*\* \@ Publisher_database_id**のパブリケーションデータベースの ID を指定します。この ID は、[データベース](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)カタログビューの**database_id\*\*列から取得できます。</span><span class="sxs-lookup"><span data-stu-id="278d4-114">(Optional) Specify the ID of the publication database for **\@publisher_database_id**, which can be obtained from the **database_id** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="278d4-115">参照</span><span class="sxs-lookup"><span data-stu-id="278d4-115">See Also</span></span>  
 [<span data-ttu-id="278d4-116">プログラムによるレプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="278d4-116">Programmatically Monitor Replication</span></span>](../monitoring-replication.md)  
  
  
