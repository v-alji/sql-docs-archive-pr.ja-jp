---
title: ミラー化されたデータベースの状態の確認 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc691e8b746a816ab88448e3399aebad6d8844e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639637"
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a><span data-ttu-id="cbe8b-102">ミラー化されたデータベースの状態の確認 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cbe8b-102">View the State of a Mirrored Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="cbe8b-103">データベース ミラーリング セッション中に、 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-103">During a database mirroring session, you can view the status on the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a><span data-ttu-id="cbe8b-104">データベース ミラーリング セッションの状態を確認するには</span><span class="sxs-lookup"><span data-stu-id="cbe8b-104">To view the status of a database mirroring session</span></span>  
  
1.  <span data-ttu-id="cbe8b-105">プリンシパル サーバー インスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-105">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="cbe8b-106">**[データベース]** を展開し、ミラー化するデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-106">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="cbe8b-107">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-107">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="cbe8b-108">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-108">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="cbe8b-109">ミラー化開始後は、 **[ミラーリング]** ページを選択した時点または **[最新の情報に更新]** ボタンをクリックした時点のデータベース ミラーリング セッションの状態が **[状態]** パネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-109">After mirroring begins, the **Status** panel displays the status of the database mirroring session as of when you selected the **Mirroring** page or clicked the **Refresh** button.</span></span> <span data-ttu-id="cbe8b-110">表示される状態は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-110">The possible states are as follows:</span></span>  
  
    |<span data-ttu-id="cbe8b-111">状態</span><span class="sxs-lookup"><span data-stu-id="cbe8b-111">States</span></span>|<span data-ttu-id="cbe8b-112">説明</span><span class="sxs-lookup"><span data-stu-id="cbe8b-112">Explanation</span></span>|  
    |------------|-----------------|  
    |\<blank>|<span data-ttu-id="cbe8b-113">データベース ミラーリング セッションが存在せず、 **[ミラーリング]** ページに表示する動作情報がありません。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-113">No database mirroring session exists and there is no activity to report on the **Mirroring** page.</span></span>|  
    |<span data-ttu-id="cbe8b-114">一時停止</span><span class="sxs-lookup"><span data-stu-id="cbe8b-114">Paused</span></span>|<span data-ttu-id="cbe8b-115">プリンシパル データベースは実行中ですが、ミラー サーバーにログを送信していません。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-115">The principal database is running but is not sending any logs to the mirror server.</span></span> <span data-ttu-id="cbe8b-116">データベースのミラー コピーは使用できない状態です。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-116">The mirror copy of the database is not available.</span></span>|  
    |<span data-ttu-id="cbe8b-117">[接続なし]</span><span class="sxs-lookup"><span data-stu-id="cbe8b-117">No connection</span></span>|<span data-ttu-id="cbe8b-118">プリンシパル サーバー インスタンスから、パートナーまたはミラーリング監視サーバー インスタンス (ある場合) に接続できません。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-118">The principal server instance cannot connect to its partner or to the witness server instance (if any)</span></span>|  
    |<span data-ttu-id="cbe8b-119">[同期中]</span><span class="sxs-lookup"><span data-stu-id="cbe8b-119">Synchronizing</span></span>|<span data-ttu-id="cbe8b-120">ミラー データベースの内容が、プリンシパル データベースの内容に遅れています。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-120">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="cbe8b-121">プリンシパル サーバー インスタンスからミラー サーバー インスタンスにログ レコードを送信して、ミラー データベースを更新するための変更を適用しています。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-121">The principal server instance is sending log records to the mirror server instance, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="cbe8b-122">データベース ミラーリング セッションの開始時点では、ミラー データベースとプリンシパル データベースが同期中の状態です。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-122">At the start of a database mirroring session, the mirror and principal databases are in the synchronizing state.</span></span>|  
    |<span data-ttu-id="cbe8b-123">[フェールオーバー]</span><span class="sxs-lookup"><span data-stu-id="cbe8b-123">Failover</span></span>|<span data-ttu-id="cbe8b-124">プリンシパル サーバー インスタンスで手動フェールオーバー (役割の交代) を開始しましたが、まだミラーが受け入れていません。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-124">On the principal server instance, a manual failover (role swap) has begun but has not yet accepted by the mirror.</span></span>|  
    |<span data-ttu-id="cbe8b-125">同期済み</span><span class="sxs-lookup"><span data-stu-id="cbe8b-125">Synchronized</span></span>|<span data-ttu-id="cbe8b-126">ミラー データベースとプリンシパル データベースには、同一のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-126">The mirror database contains the same data as the principal database.</span></span> <span data-ttu-id="cbe8b-127">同期完了の状態のとき *だけ* 、手動および自動フェールオーバーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cbe8b-127">Manual and automatic failover are possible *only* in the synchronized state.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbe8b-128">参照</span><span class="sxs-lookup"><span data-stu-id="cbe8b-128">See Also</span></span>  
 [<span data-ttu-id="cbe8b-129">ミラーリング状態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cbe8b-129">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  
