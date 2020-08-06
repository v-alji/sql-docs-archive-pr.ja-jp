---
title: レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736258"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a><span data-ttu-id="60188-102">レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="60188-102">Run Replication Maintenance Jobs (SQL Server Management Studio)</span></span>
  <span data-ttu-id="60188-103">レプリケーションでは以下のメンテナンス ジョブを使用します。</span><span class="sxs-lookup"><span data-stu-id="60188-103">Replication uses the following maintenance jobs:</span></span>  
  
-   <span data-ttu-id="60188-104">**データ検証で問題が見つかったサブスクリプションの再初期化**</span><span class="sxs-lookup"><span data-stu-id="60188-104">**Reinitialize subscriptions having data validation failures**</span></span>
-   <span data-ttu-id="60188-105">**エージェント履歴のクリーンアップ: ディストリビューション**</span><span class="sxs-lookup"><span data-stu-id="60188-105">**Agent history clean up: distribution**</span></span>
-   <span data-ttu-id="60188-106">**ディストリビューションのレプリケーション モニターの状態更新機能**</span><span class="sxs-lookup"><span data-stu-id="60188-106">**Replication monitoring refresher for distribution.**</span></span>
-   <span data-ttu-id="60188-107">**レプリケーション エージェントの検査**</span><span class="sxs-lookup"><span data-stu-id="60188-107">**Replication agents checkup**</span></span>
-   <span data-ttu-id="60188-108">**ディストリビューションのクリーンアップ: ディストリビューション**</span><span class="sxs-lookup"><span data-stu-id="60188-108">**Distribution clean up: distribution**</span></span>
-   <span data-ttu-id="60188-109">**有効期限が切れたサブスクリプションのクリーンアップ**</span><span class="sxs-lookup"><span data-stu-id="60188-109">**Expired subscription clean up**</span></span>  
  
 <span data-ttu-id="60188-110">上記のジョブの開始および停止は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の **[ジョブ]** フォルダー、およびレプリケーション モニターの **[エージェント]** タブから行います。</span><span class="sxs-lookup"><span data-stu-id="60188-110">Start and stop these jobs from the **Jobs** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="60188-111">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60188-111">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="60188-112">各ジョブのプロパティの表示および変更は、同じフォルダーおよびタブからアクセスできる **[ジョブのプロパティ - \<Job>]** ダイアログ ボックスで行います。</span><span class="sxs-lookup"><span data-stu-id="60188-112">View and modify properties for each job in the **Job Properties - \<Job>** dialog box, which is available from the same folder and tab.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="60188-113">Management Studio でレプリケーション メンテナンス ジョブを開始または停止するには</span><span class="sxs-lookup"><span data-stu-id="60188-113">To start or stop a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="60188-114">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="60188-114">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="60188-115">**[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="60188-115">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="60188-116">ジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-116">Right-click a job, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="60188-117">レプリケーション モニターでレプリケーション メンテナンス ジョブを開始または停止するには</span><span class="sxs-lookup"><span data-stu-id="60188-117">To start or stop a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="60188-118">レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="60188-118">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="60188-119">**[エージェント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-119">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="60188-120">グリッド内のジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-120">Right-click a job in the grid, and then click **Start Job** or **Stop Job**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a><span data-ttu-id="60188-121">Management Studio でレプリケーション メンテナンス ジョブのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="60188-121">To view and modify properties for a replication maintenance job in Management Studio</span></span>  
  
1.  <span data-ttu-id="60188-122">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="60188-122">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="60188-123">**[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="60188-123">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="60188-124">ジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-124">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="60188-125">**[ジョブのプロパティ - \<Job>]** ダイアログ ボックスで、必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-125">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a><span data-ttu-id="60188-126">レプリケーション モニターでレプリケーション メンテナンス ジョブのプロパティを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="60188-126">To view and modify properties for a replication maintenance job in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="60188-127">レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="60188-127">Expand a Publisher group in Replication Monitor, and then select a Publisher.</span></span>  
  
2.  <span data-ttu-id="60188-128">**[エージェント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-128">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="60188-129">グリッド内のジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-129">Right-click a job in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="60188-130">**[ジョブのプロパティ - \<Job>]** ダイアログ ボックスで、必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60188-130">In the **Job Properties - \<Job>** dialog box, modify any properties if necessary, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60188-131">参照</span><span class="sxs-lookup"><span data-stu-id="60188-131">See Also</span></span>  
 <span data-ttu-id="60188-132">[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="60188-132">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="60188-133">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="60188-133">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="60188-134">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="60188-134">Replication Agent Administration</span></span>](../agents/replication-agent-administration.md)  
  
  
