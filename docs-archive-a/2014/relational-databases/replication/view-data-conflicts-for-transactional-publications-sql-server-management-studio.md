---
title: トランザクションパブリケーションのデータの競合の表示 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
- viewing conflict information
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 228753c113bcf43ed276d989a3996e9bf23bfc16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643773"
---
# <a name="view-data-conflicts-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="e29d8-102">トランザクション パブリケーションのデータの競合の表示 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e29d8-102">View Data Conflicts for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e29d8-103">ピア ツー ピア トランザクション レプリケーション、およびキュー更新サブスクリプションを使用するトランザクション レプリケーションでの競合を、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] レプリケーション競合表示モジュールで表示できます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-103">You can view conflicts for peer-to-peer transactional replication and transactional replication with queued updating subscriptions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span> <span data-ttu-id="e29d8-104">競合の検出と解決方法については、「[ピア ツー ピア レプリケーションにおける競合検出](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」と「[キュー更新の競合解決オプションの設定 &#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e29d8-104">For information about how conflicts are detected and resolved, see [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) and [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md).</span></span>  
  
 <span data-ttu-id="e29d8-105">競合データを表示できるかどうかは、レプリケーションの種類および競合の保有期間によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e29d8-105">The availability of conflict data depends on the type of replication and the conflict retention period:</span></span>  
  
-   <span data-ttu-id="e29d8-106">ピア ツー ピア レプリケーションの場合、ディストリビューション エージェントは、競合を検出すると既定で停止します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-106">For peer-to-peer replication, by default, the Distribution Agent fails when it detects a conflict.</span></span> <span data-ttu-id="e29d8-107">競合エラーはエラー ログに記録されますが、競合データは競合テーブルに記録されないため、競合データを表示できません。</span><span class="sxs-lookup"><span data-stu-id="e29d8-107">A conflict error is logged into the error log, but no conflict data is logged into the conflict table; therefore it is not available for viewing.</span></span> <span data-ttu-id="e29d8-108">ディストリビューション エージェントが実行の継続を許可されている場合は、競合が検出された各ノードで、競合がローカルでログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-108">If the Distribution Agent is allowed to continue, a conflict is logged locally on each node where it was detected.</span></span> <span data-ttu-id="e29d8-109">詳細については、「 [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e29d8-109">For more information, see "Handling Conflicts" in [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
-   <span data-ttu-id="e29d8-110">キュー更新サブスクリプションの場合は、すべての競合のデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-110">For queued updating subscriptions, data is available for every conflict.</span></span> <span data-ttu-id="e29d8-111">競合データは、競合の保有期間に指定した期間 (既定では 14 日間)、レプリケーション競合表示モジュールで表示できます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-111">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period, with a default of 14 days.</span></span> <span data-ttu-id="e29d8-112">競合の保有期間を設定するには、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-112">To set the conflict retention period, perform either of the following:</span></span>  
  
    -   <span data-ttu-id="e29d8-113">[sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) の @conflict_retention パラメーターに保有期間の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-113">Specify a retention value for the @conflict_retention parameter of [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="e29d8-114">パラメーターに値を指定し、 `'conflict_retention'` @property sp_changepublication のパラメーターに保有期間の値を指定し @value ます。 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="e29d8-114">Specify a value of `'conflict_retention'` for the @property parameter and a retention value for the @value parameter of [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span>  
  
### <a name="to-view-conflicts"></a><span data-ttu-id="e29d8-115">競合を表示するには</span><span class="sxs-lookup"><span data-stu-id="e29d8-115">To view conflicts</span></span>  
  
1.  <span data-ttu-id="e29d8-116">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で適切なサーバーに接続し、そのサーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-116">Connect to the appropriate server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="e29d8-117">ピア ツー ピア レプリケーションの場合は、競合の発生したノードがこれに当たります。</span><span class="sxs-lookup"><span data-stu-id="e29d8-117">For peer-to-peer replication, this is the node at which the conflict occurred.</span></span>  
  
    -   <span data-ttu-id="e29d8-118">キュー更新サブスクリプションの場合は、パブリッシャーがこれに当たります。</span><span class="sxs-lookup"><span data-stu-id="e29d8-118">For queued updating subscriptions, this is the Publisher.</span></span>  
  
2.  <span data-ttu-id="e29d8-119">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-119">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e29d8-120">競合を表示するパブリケーションを右クリックしてから、 **[競合の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e29d8-120">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
4.  <span data-ttu-id="e29d8-121">**[競合テーブルの選択]** ダイアログ ボックスで、競合を表示するデータベース、パブリケーション、およびテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-121">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="e29d8-122">レプリケーション競合表示モジュールでは、以下を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-122">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="e29d8-123">上のグリッドの右側のボタンで行をフィルター選択する。</span><span class="sxs-lookup"><span data-stu-id="e29d8-123">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="e29d8-124">上のグリッドで行を選択して、下のグリッドにその行の情報を表示する。</span><span class="sxs-lookup"><span data-stu-id="e29d8-124">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="e29d8-125">上のグリッドで複数の行を選択し、 **[削除]** をクリックして、競合メタデータ テーブルから行を削除する。</span><span class="sxs-lookup"><span data-stu-id="e29d8-125">Select one or more rows in the upper grid, and then click **Remove**, which removes the row from the conflicts metadata table.</span></span>  
  
    -   <span data-ttu-id="e29d8-126">プロパティボタン ([.**..**]) をクリックして、競合に関係する列の詳細情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-126">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="e29d8-127">**[この競合の詳細をログに記録する]** を選択して、競合のデータをログ ファイルに記録する。</span><span class="sxs-lookup"><span data-stu-id="e29d8-127">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="e29d8-128">ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e29d8-128">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="e29d8-129">値を入力するか、または参照ボタン (**[...]**) をクリックして適切なファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="e29d8-129">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="e29d8-130">**[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-130">Click **OK** to close the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="e29d8-131">レプリケーション競合表示モジュールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e29d8-131">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e29d8-132">参照</span><span class="sxs-lookup"><span data-stu-id="e29d8-132">See Also</span></span>  
 <span data-ttu-id="e29d8-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e29d8-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span></span>  
 [<span data-ttu-id="e29d8-134">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="e29d8-134">Queued Updating Conflict Detection and Resolution</span></span>](transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
