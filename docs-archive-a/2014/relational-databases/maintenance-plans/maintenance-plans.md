---
title: メンテナンス プラン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- SQL12.AG.MAINTPLAN.LEGACY.F1
helpviewer_keywords:
- maintenance plans [SQL Server], about database maintenance plans
- maintenance plans [SQL Server], database compatibility level displayed in designer
- maintenance plans [SQL Server]
ms.assetid: 5982ca65-74fe-44e3-aef9-00a65a0db169
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2f614e2cfad78cb1efddc49cc897ca57087fec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631011"
---
# <a name="maintenance-plans"></a><span data-ttu-id="906b8-102">メンテナンス プラン</span><span class="sxs-lookup"><span data-stu-id="906b8-102">Maintenance Plans</span></span>
  <span data-ttu-id="906b8-103">メンテナンス プランでは、データベースを最適化したり、データベースを定期的にバックアップしたり、データベースの不整合をなくしたりするために必要なタスクのワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="906b8-103">Maintenance plans create a workflow of the tasks required to make sure that your database is optimized, regularly backed up, and free of inconsistencies.</span></span> <span data-ttu-id="906b8-104">メンテナンス プラン ウィザードでも主要なメンテナンス プランを作成できますが、プランを手動で作成するとより柔軟性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="906b8-104">The Maintenance Plan Wizard also creates core maintenance plans, but creating plans manually gives you much more flexibility.</span></span>  
  
## <a name="benefits-of-maintenance-plans"></a><span data-ttu-id="906b8-105">メンテナンス プランの利点</span><span class="sxs-lookup"><span data-stu-id="906b8-105">Benefits of Maintenance Plans</span></span>  
 <span data-ttu-id="906b8-106">[!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)]では、メンテナンス プランによって、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エージェント ジョブが実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="906b8-106">In [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)], maintenance plans create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, which is run by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="906b8-107">メンテナンス プランは、手動で実行することも、定期的に自動実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="906b8-107">Maintenance plans can be run manually or automatically at scheduled intervals.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="906b8-108">メンテナンス プランには、次の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="906b8-108">maintenance plans provide the following features:</span></span>  
  
-   <span data-ttu-id="906b8-109">さまざまな一般的なメンテナンス タスクを使用するワークフローの作成。</span><span class="sxs-lookup"><span data-stu-id="906b8-109">Workflow creation using a variety of typical maintenance tasks.</span></span> <span data-ttu-id="906b8-110">カスタム [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを独自に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="906b8-110">You can also create your own custom [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span>  
  
-   <span data-ttu-id="906b8-111">概念的な階層。</span><span class="sxs-lookup"><span data-stu-id="906b8-111">Conceptual hierarchies.</span></span> <span data-ttu-id="906b8-112">各プランでは、ワークフローの作成や編集を行えます。</span><span class="sxs-lookup"><span data-stu-id="906b8-112">Each plan lets you create or edit task workflows.</span></span> <span data-ttu-id="906b8-113">各プランのタスクはサブプランにグループ化できます。サブプランは、異なるタイミングで実行されるようにスケジュールを設定できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-113">Tasks in each plan can be grouped into subplans, which can be scheduled to run at different times.</span></span>  
  
-   <span data-ttu-id="906b8-114">マスター サーバーやターゲット サーバーの環境で使用できるマルチサーバーのプランのサポート。</span><span class="sxs-lookup"><span data-stu-id="906b8-114">Support for multiserver plans that can be used in master server/target server environments.</span></span>  
  
-   <span data-ttu-id="906b8-115">プランの履歴をリモート サーバーのログに記録する際のサポート。</span><span class="sxs-lookup"><span data-stu-id="906b8-115">Support for logging plan history to remote servers.</span></span>  
  
-   <span data-ttu-id="906b8-116">Windows 認証と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のサポート。</span><span class="sxs-lookup"><span data-stu-id="906b8-116">Support for Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="maintenace-plan-functionality"></a><span data-ttu-id="906b8-117">メンテナンス プラン機能</span><span class="sxs-lookup"><span data-stu-id="906b8-117">Maintenace Plan Functionality</span></span>  
 <span data-ttu-id="906b8-118">メンテナンス プランは、次のタスクを実行するように作成できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-118">Maintenance plans can be created to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="906b8-119">新しい FILL FACTOR を使用してインデックスを再構築し、データ ページとインデックス ページのデータを再編成します。</span><span class="sxs-lookup"><span data-stu-id="906b8-119">Reorganize the data on the data and index pages by rebuilding indexes with a new fill factor.</span></span> <span data-ttu-id="906b8-120">この再構築によって、データ量と空き領域がすべてのデータベース ページに均等に分配されます。</span><span class="sxs-lookup"><span data-stu-id="906b8-120">Rebuilding indexes with a new fill factor makes sure that database pages contain an equally distributed amount of data and free space.</span></span> <span data-ttu-id="906b8-121">また、その後の拡張を高速化できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-121">It also enables faster growth in the future.</span></span> <span data-ttu-id="906b8-122">詳細については、「 [インデックスの FILL FACTOR の指定](../indexes/specify-fill-factor-for-an-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="906b8-122">For more information, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
-   <span data-ttu-id="906b8-123">空のデータベース ページを削除してデータ ファイルを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="906b8-123">Compress data files by removing empty database pages.</span></span>  
  
-   <span data-ttu-id="906b8-124">インデックス統計を更新して、クエリ オプティマイザーで保持されているテーブル内のデータ値の分布に関する情報を常に最新の状態に保ちます。</span><span class="sxs-lookup"><span data-stu-id="906b8-124">Update index statistics to make sure the query optimizer has current information about the distribution of data values in the tables.</span></span> <span data-ttu-id="906b8-125">その結果、データベース内のデータに関してクエリ オプティマイザーが使用できる情報が多くなるため、データにアクセスする最適な方法がクエリ オプティマイザーによってより適切に判断されます。</span><span class="sxs-lookup"><span data-stu-id="906b8-125">This enables the query optimizer to make better judgments about the best way to access data, because it has more information about the data stored in the database.</span></span> <span data-ttu-id="906b8-126">インデックス統計は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって定期的に自動更新されますが、このオプションを使用すると、インデックス統計をすぐに更新できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-126">Although index statistics are automatically updated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically, this option can force the statistics to update immediately.</span></span>  
  
-   <span data-ttu-id="906b8-127">データベース内のデータとデータ ページの内部一貫性チェックを実行して、システムまたはソフトウェアの問題が原因でデータが壊れていないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="906b8-127">Perform internal consistency checks of the data and data pages within the database to make sure that a system or software problem has not damaged data.</span></span>  
  
-   <span data-ttu-id="906b8-128">データベースとトランザクション ログ ファイルをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="906b8-128">Back up the database and transaction log files.</span></span> <span data-ttu-id="906b8-129">データベースとログのバックアップは、指定した期間、保管できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-129">Database and log backups can be retained for a specified period.</span></span> <span data-ttu-id="906b8-130">これにより、バックアップの履歴を作成して、最後にデータベースをバックアップした時点より前の時点への復元が必要になった場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-130">This lets you create a history of backups to be used if you have to restore the database to a time earlier than the last database backup.</span></span> <span data-ttu-id="906b8-131">また、差分バックアップも行えます。</span><span class="sxs-lookup"><span data-stu-id="906b8-131">You can also perform differential backups.</span></span>  
  
-   <span data-ttu-id="906b8-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="906b8-132">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="906b8-133">これにより、さまざまなアクションを実行するジョブと、それらのジョブを実行するメンテナンス プランを作成できます。</span><span class="sxs-lookup"><span data-stu-id="906b8-133">This can be used to create jobs that perform a variety of actions and the maintenance plans to run those jobs.</span></span>  
  
 <span data-ttu-id="906b8-134">メンテナンス タスクで生成される結果は、レポートとしてテキスト ファイルに書き込むことや、`sysmaintplan_log` 内のメンテナンス プラン用のテーブルである `sysmaintplan_logdetail` や `msdb` に書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="906b8-134">The results generated by the maintenance tasks can be written as a report to a text file or to the maintenance plan tables (`sysmaintplan_log` and `sysmaintplan_logdetail`) in `msdb`.</span></span> <span data-ttu-id="906b8-135">ログ ファイル ビューアーで結果を参照するには、 **[メンテナンス プラン]** を右クリックし、 **[履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="906b8-135">To view the results in the log file viewer, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="906b8-136">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="906b8-136">Related Tasks</span></span>  
 <span data-ttu-id="906b8-137">メンテナンス プランの基礎知識については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="906b8-137">Use the following topics to get started with maintenance plans.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="906b8-138">**説明**</span><span class="sxs-lookup"><span data-stu-id="906b8-138">**Description**</span></span>|<span data-ttu-id="906b8-139">**トピック**</span><span class="sxs-lookup"><span data-stu-id="906b8-139">**Topic**</span></span>|  
|<span data-ttu-id="906b8-140">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してメンテナンス プランを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="906b8-140">Describes how to create a maintenance plan by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|[<span data-ttu-id="906b8-141">メンテナンス プランの作成</span><span class="sxs-lookup"><span data-stu-id="906b8-141">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)|  
|<span data-ttu-id="906b8-142">メンテナンス プラン デザイン画面を使用してメンテナンス プランを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="906b8-142">Describes how to create a maintenance plan by using the Maintenance Plan Design Surface.</span></span>|[<span data-ttu-id="906b8-143">メンテナンス プランの作成 &#40;メンテナンス プラン デザイン画面&#41;</span><span class="sxs-lookup"><span data-stu-id="906b8-143">Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;</span></span>](create-a-maintenance-plan-maintenance-plan-design-surface.md)|  
|<span data-ttu-id="906b8-144">オブジェクト エクスプローラーで利用できるメンテナンス プランの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="906b8-144">Documents maintenance plan functionality available in Object Explorer.</span></span>|<span data-ttu-id="906b8-145">[[メンテナンス プラン] ノード &#40;オブジェクト エクスプローラー&#41;](../../ssms/object/object-explorer.md)</span><span class="sxs-lookup"><span data-stu-id="906b8-145">[Maintenance Plans Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md)</span></span>|  
  
  
