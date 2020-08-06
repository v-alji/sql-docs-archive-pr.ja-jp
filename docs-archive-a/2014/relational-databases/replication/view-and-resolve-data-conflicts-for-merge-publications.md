---
title: マージパブリケーションのデータの競合の表示および解決 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77aa9ece0073149c017f6eca35a756b22751a74b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639436"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications-sql-server-management-studio"></a><span data-ttu-id="19cb5-102">マージ パブリケーションでのデータの競合の表示および解決 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="19cb5-102">View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="19cb5-103">マージ レプリケーションの競合は、各アーティクルに対して指定された競合回避モジュールに基づいて解決されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-103">Conflicts in merge replication are resolved based on the resolver specified for each article.</span></span> <span data-ttu-id="19cb5-104">既定では、競合はユーザーの介入を必要とせずに解決されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-104">By default, conflicts are resolved without the need for user intervention.</span></span> <span data-ttu-id="19cb5-105">ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] レプリケーション競合表示モジュールで競合を表示したり、解決の結果を変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-105">But conflicts can be viewed, and the outcome of the resolution can be changed, in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span>  
  
 <span data-ttu-id="19cb5-106">競合データは、競合の保有期間に指定した期間内 (既定では 14 日間) はレプリケーション競合表示モジュールで利用できます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-106">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period (with a default of 14 days).</span></span> <span data-ttu-id="19cb5-107">競合の保有期間を設定するには、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-107">To set the conflict retention period, either:</span></span>  
  
-   <span data-ttu-id="19cb5-108">**@conflict_retention** [Sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)のパラメーターの保有期間の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-108">Specify a retention value for the **@conflict_retention** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
-   <span data-ttu-id="19cb5-109">パラメーターに**conflict_retention**の値を指定 **@property** し、 **@value** [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)のパラメーターに保有期間の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-109">Specify a value of **conflict_retention** for the **@property** parameter and a retention value for the **@value** parameter of [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="19cb5-110">競合情報の既定の保存先は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19cb5-110">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="19cb5-111">パブリケーションの互換性レベルが 90 RTM 以上の場合は、パブリッシャーおよびサブスクライバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-111">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="19cb5-112">パブリケーションの互換性レベルが 80 RTM 未満の場合は、パブリッシャーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-112">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="19cb5-113">サブスクライバーが [!INCLUDE[ssEW](../../includes/ssew-md.md)]を実行している場合は、パブリッシャーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-113">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="19cb5-114">競合データを [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーに保存することはできません。</span><span class="sxs-lookup"><span data-stu-id="19cb5-114">Conflict data cannot be stored on [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="19cb5-115">競合情報を格納する領域は、 **conflict_logging** パブリケーション プロパティによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-115">Storage of conflict information is controlled by the **conflict_logging** publication property.</span></span> <span data-ttu-id="19cb5-116">詳細については、「[sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)」と「[sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="19cb5-116">For more information, see [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) and [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="19cb5-117">競合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインタラクティブ競合回避モジュールを使用して、同期実行時に対話的に解決することもできます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-117">Conflicts can also be resolved interactively during synchronization using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Interactive Resolver.</span></span> <span data-ttu-id="19cb5-118">インタラクティブ競合回避モジュールは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーで利用できます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-118">The Interactive Resolver is available through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="19cb5-119">詳細については、「[Windows 同期マネージャーを使用したサブスクリプションの同期 &#40;Windows 同期マネージャー&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="19cb5-119">For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a><span data-ttu-id="19cb5-120">マージ パブリケーションで競合を表示および解決するには</span><span class="sxs-lookup"><span data-stu-id="19cb5-120">To view and resolve conflicts for merge publications</span></span>  
  
1.  <span data-ttu-id="19cb5-121">でパブリッシャー (または必要に応じてサブスクライバー) に接続 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] し、サーバーノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-121">Connect to the Publisher (or Subscriber if appropriate) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="19cb5-122">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-122">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="19cb5-123">競合を表示するパブリケーションを右クリックしてから、 **[競合の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19cb5-123">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19cb5-124">**conflict_logging** プロパティの値として **'subscriber'** を指定した場合は、 **[競合の表示]** メニュー オプションを利用できません。</span><span class="sxs-lookup"><span data-stu-id="19cb5-124">If you specified a value of **'subscriber'** for the **conflict_logging** property, the **View Conflicts** menu option is not available.</span></span> <span data-ttu-id="19cb5-125">競合を表示するには、コマンド プロンプトで ConflictViewer.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-125">To view conflicts, start ConflictViewer.exe from the command prompt.</span></span> <span data-ttu-id="19cb5-126">既定では、ConflictViewer.exe が格納されているディレクトリは、Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE です。</span><span class="sxs-lookup"><span data-stu-id="19cb5-126">By default, ConflictViewer.exe is located in the following directory: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.</span></span> <span data-ttu-id="19cb5-127">有効な起動時のパラメーターの一覧を表示するには、ConflictViewer.exe -? を実行します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-127">For a list of valid startup parameters, run ConflictViewer.exe -?.</span></span>  
  
4.  <span data-ttu-id="19cb5-128">**[競合テーブルの選択]** ダイアログ ボックスで、競合を表示するデータベース、パブリケーション、およびテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-128">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="19cb5-129">レプリケーション競合表示モジュールでは、以下を実行できます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-129">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="19cb5-130">上のグリッドの右側のボタンで行をフィルター選択する。</span><span class="sxs-lookup"><span data-stu-id="19cb5-130">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="19cb5-131">上のグリッドで行を選択して、下のグリッドにその行の情報を表示する。</span><span class="sxs-lookup"><span data-stu-id="19cb5-131">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="19cb5-132">上のグリッドで 1 つ以上の行を選択し、 **[削除]** をクリックする。これは、データに変更を加えずに **[優先されたデータの送信]** をクリックするのと同じです。</span><span class="sxs-lookup"><span data-stu-id="19cb5-132">Select one or more rows in the upper grid, and then click **Remove**, which is equivalent to clicking the **Submit Winner** button (without making any changes to the data).</span></span>  
  
    -   <span data-ttu-id="19cb5-133">プロパティボタン ([.**..**]) をクリックして、競合に関係する列の詳細情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-133">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="19cb5-134">データを送信する前に、 **[競合で優先されたデータ]** 列または **[競合で優先されなかったデータ]** 列でデータを編集する (列が灰色の場合、データは読み取り専用です)。</span><span class="sxs-lookup"><span data-stu-id="19cb5-134">Edit data in the **Conflict winner** or **Conflict loser** column before submitting the data (data is read-only if the column is gray).</span></span>  
  
    -   <span data-ttu-id="19cb5-135">**[優先されたデータの送信]** をクリックし、競合で優先するデータとして指定された行を受け入れる。</span><span class="sxs-lookup"><span data-stu-id="19cb5-135">Click **Submit Winner** to accept the row designated as the winner of the conflict.</span></span>  
  
    -   <span data-ttu-id="19cb5-136">**[優先されなかったデータの送信]** をクリックして解決をオーバーライドし、競合で優先されないデータとして指定された値をトポロジのすべてのノードに反映する。</span><span class="sxs-lookup"><span data-stu-id="19cb5-136">Click **Submit Loser** to override the resolution and to propagate the value designated as the loser of the conflict to all nodes in the topology.</span></span>  
  
    -   <span data-ttu-id="19cb5-137">**[この競合の詳細をログに記録する]** を選択して、競合のデータをログ ファイルに記録する。</span><span class="sxs-lookup"><span data-stu-id="19cb5-137">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="19cb5-138">ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19cb5-138">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="19cb5-139">値を入力するか、または参照ボタン (**[...]**) をクリックして適切なファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-139">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="19cb5-140">**[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-140">Click **OK** to exit the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="19cb5-141">レプリケーション競合表示モジュールを閉じます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-141">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cb5-142">参照</span><span class="sxs-lookup"><span data-stu-id="19cb5-142">See Also</span></span>  
 <span data-ttu-id="19cb5-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="19cb5-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="19cb5-144">マージ アーティクル競合回避モジュールの指定</span><span class="sxs-lookup"><span data-stu-id="19cb5-144">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)  
  
  
