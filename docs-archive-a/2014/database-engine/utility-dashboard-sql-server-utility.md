---
title: ユーティリティダッシュボード (SQL Server ユーティリティ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 999eb741-4a60-43f6-ab37-2df7dce845c1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1e6f59eca0aaaee0d0fc79f267a781b650fb3d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715665"
---
# <a name="utility-dashboard-sql-server-utility"></a><span data-ttu-id="54474-102">ユーティリティ ダッシュボード (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="54474-102">Utility Dashboard (SQL Server Utility)</span></span>
  <span data-ttu-id="54474-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティ ダッシュボードにデータを表示するには、ユーティリティ エクスプローラーのツリーで最上位ノード "Utility<UCP 名>\\(ComputerName\UCP)" を選択します。</span><span class="sxs-lookup"><span data-stu-id="54474-103">To see data in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard, select the top node in the Utility Explorer tree - labeled "Utility<UCP_Name>\\(ComputerName\UCP)."</span></span> <span data-ttu-id="54474-104">ダッシュボードには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のすべてのマネージド インスタンス、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのすべてのデータ層アプリケーションに関する概要データと詳細データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-104">The dashboard includes summary and detail data from all managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and all data-tier applications in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="54474-105">ダッシュボードのデータを更新するには、ユーティリティ エクスプローラーのツリーで最上位ノードを右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54474-105">To refresh data in the dashboard, right-click the top node in the Utility Explorer tree, and select **Refresh**.</span></span>  
  
 <span data-ttu-id="54474-106">ユーティリティ コントロール ポイントの作成方法については、「 [SQL Server ユーティリティ コントロール ポイントの作成 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54474-106">For more information about how to create a utility control point, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span> <span data-ttu-id="54474-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティに追加する方法については、「[Enroll an Instance of SQL Server &#40;SQL Server Utility&#41; (SQL Server のインスタンスの登録 &#40;SQL Server ユーティリティ&#41;)](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54474-107">For more information about how to add an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="54474-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="54474-108">UI element list</span></span>  
 <span data-ttu-id="54474-109">マネージド インスタンスの正常性</span><span class="sxs-lookup"><span data-stu-id="54474-109">Managed Instance Health</span></span>  
 <span data-ttu-id="54474-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスの正常性状態は、ユーティリティ エクスプローラーのコンテンツ ペインの左側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-110">Health status for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is displayed on the left side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="54474-111">マネージド インスタンスの正常性パラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54474-111">Managed Instance Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="54474-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスの CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="54474-112">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="54474-113">データベース ファイルの使用率</span><span class="sxs-lookup"><span data-stu-id="54474-113">Database file utilization.</span></span>  
  
-   <span data-ttu-id="54474-114">記憶域ボリュームの領域使用率</span><span class="sxs-lookup"><span data-stu-id="54474-114">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="54474-115">コンピューターの CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="54474-115">CPU utilization for the computer.</span></span>  
  
-   <span data-ttu-id="54474-116">各パラメーターの状態は、次の 3 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="54474-116">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="54474-117">適正使用 - リソース使用率のポリシーに違反していない、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスの数</span><span class="sxs-lookup"><span data-stu-id="54474-117">Well-utilized - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="54474-118">過小使用 - リソースの過小使用ポリシーに違反しているマネージド リソースの数</span><span class="sxs-lookup"><span data-stu-id="54474-118">Underutilized - Number of managed resources which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="54474-119">過大使用 - リソースの過大使用ポリシーに違反しているマネージド リソースの数</span><span class="sxs-lookup"><span data-stu-id="54474-119">Overutilized - Number of managed resources which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="54474-120">利用可能データなし - SQL Server のマネージド インスタンスによって利用できるデータがありません。SQL Server のインスタンスが登録された直後であるため最初のデータ収集操作が完了していないか、またはデータの収集と UCP へのアップロードの際に SQL Server のマネージド インスタンスで問題が発生したことが原因です。</span><span class="sxs-lookup"><span data-stu-id="54474-120">No Data Available - Data is not available for managed instances of SQL Server either because the instance of SQL Server has just been enrolled and the first data collection operation has not completed, or because there is a problem with the managed instance of SQL Server collecting and uploading data to the UCP.</span></span>  
  
 <span data-ttu-id="54474-121">各正常性パラメーターの詳細な状態は、スライド式インジケーターに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-121">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="54474-122">スライド式インジケーターの右側にある部分は、何個のマネージド インスタンスが各状態カテゴリに存在するかを示します。</span><span class="sxs-lookup"><span data-stu-id="54474-122">The fraction to the right of the sliding indicators shows how many managed instances are in each status category.</span></span>  
  
 <span data-ttu-id="54474-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスまたはデータ層アプリケーションについてフィルターを適用したビューを作成するには、ユーティリティ ダッシュボードのスライド式インジケーターの横にある使用率カテゴリのリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54474-123">To create a filtered view of a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or a data-tier application, click on the link for a utilization category next to its sliding indicator in the Utility dashboard.</span></span> <span data-ttu-id="54474-124">たとえば、 **ユーティリティ エクスプローラーのコンテンツ** ペインで **[使用率が高いインスタンス CPU]** をクリックすると、SSMS では、現在のポリシー設定に基づいてフィルターが適用され、CPU 使用率の高い [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスについてのリスト ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="54474-124">For example, if you click on **Overutilized Instance CPU** in the **Utility Explorer Content** pane, SSMS creates a filtered list view of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that have overutilized CPU based on current policy settings.</span></span>  
  
 <span data-ttu-id="54474-125">使用率カテゴリのリンクをクリックすると、ユーティリティ エクスプローラー ナビゲーション ウィンドウの対応するノードに **(フィルター選択)** と表示されます。つまり、 **[マネージド インスタンス]** のラベルが **[マネージド インスタンス (フィルター選択)]** になります。</span><span class="sxs-lookup"><span data-stu-id="54474-125">Notice that when you click on a link for a utilization category, the corresponding node in the Utility Explorer navigation pane is appended with **(filtered)** - that is, **Managed Instances** is labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="54474-126">フィルターの設定を表示するには、ナビゲーション ウィンドウでノードを右クリックし、 **[フィルター]** 、 **[フィルターの設定]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="54474-126">To view filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Filter Settings**.</span></span> <span data-ttu-id="54474-127">フィルターの設定をクリアするには、ナビゲーション ウィンドウでノードを右クリックし、 **[フィルター]** 、 **[フィルターの削除]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="54474-127">To clear filter settings, right-click on the node in the navigation pane and select **Filter**, then click on **Remove Filter**.</span></span>  
  
 <span data-ttu-id="54474-128">個々の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの正常性状態の表示と、ポリシー構成設定の表示または変更の詳細については、「[マネージド インスタンスの詳細 &#40;SQL Server ユーティリティ &#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54474-128">For more information about viewing health status for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change policy configuration settings, see [Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="54474-129">ユーティリティの概要</span><span class="sxs-lookup"><span data-stu-id="54474-129">Utility Summary</span></span>  
 <span data-ttu-id="54474-130">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスの数と、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティによって管理されるデータ層アプリケーションの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="54474-130">Displays the number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the number of data-tier applications managed by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="54474-131">データ層アプリケーションの正常性</span><span class="sxs-lookup"><span data-stu-id="54474-131">Data-tier Application Health</span></span>  
 <span data-ttu-id="54474-132">データ層アプリケーションの正常性状態は、ユーティリティ エクスプローラーのコンテンツ ペインの右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-132">Health status for data-tier applications is displayed on the right side of the Utility Explorer content pane.</span></span>  
  
 <span data-ttu-id="54474-133">データ層アプリケーションの正常性パラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54474-133">Data-tier Application Health parameters are as follows:</span></span>  
  
-   <span data-ttu-id="54474-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスの CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="54474-134">CPU utilization for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="54474-135">データベース ファイルの使用率</span><span class="sxs-lookup"><span data-stu-id="54474-135">Database file utilization.</span></span>  
  
-   <span data-ttu-id="54474-136">記憶域ボリュームの領域使用率</span><span class="sxs-lookup"><span data-stu-id="54474-136">Storage volume space utilization.</span></span>  
  
-   <span data-ttu-id="54474-137">コンピューターの CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="54474-137">CPU utilization for the computer.</span></span>  
  
 <span data-ttu-id="54474-138">各パラメーターの状態は、次の 3 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="54474-138">Status for each parameter is divided into three categories:</span></span>  
  
-   <span data-ttu-id="54474-139">適正使用 - リソース使用率のポリシーに違反していないデータ層アプリケーションの数</span><span class="sxs-lookup"><span data-stu-id="54474-139">Well-utilized - Number of data-tier applications which are not violating resource utilization policies.</span></span>  
  
-   <span data-ttu-id="54474-140">過大使用 - リソースの過大使用ポリシーに違反しているデータ層アプリケーションの数</span><span class="sxs-lookup"><span data-stu-id="54474-140">Overutilized - Number of data-tier applications which are violating resource overutilization policies.</span></span>  
  
-   <span data-ttu-id="54474-141">過小使用 - リソースの過小使用ポリシーに違反しているデータ層アプリケーションの数</span><span class="sxs-lookup"><span data-stu-id="54474-141">Underutilized - Number of data-tier applications which are violating resource underutilization policies.</span></span>  
  
-   <span data-ttu-id="54474-142">利用可能データなし - データ層アプリケーションによって利用できるデータがありません。データ層アプリケーションを含む SQL Server のマネージド インスタンスがデータを報告していないことが原因です。</span><span class="sxs-lookup"><span data-stu-id="54474-142">No Data Available - Data is not available for data-tier applications because the managed instance of SQL Server that contains the data-tier application is not reporting data.</span></span>  
  
 <span data-ttu-id="54474-143">各正常性パラメーターの詳細な状態は、スライド式インジケーターに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-143">Detailed status for each health parameter is listed in sliding indicators.</span></span> <span data-ttu-id="54474-144">スライド式インジケーターの右側にある部分は、何個のデータ層アプリケーションが各状態カテゴリに存在するかを示します。</span><span class="sxs-lookup"><span data-stu-id="54474-144">The fraction to the right of the sliding indicators shows how many data-tier applications are in each status category.</span></span> <span data-ttu-id="54474-145">個々のデータ層アプリケーションの正常性状態の表示と、ポリシー構成設定の表示または変更の詳細については、「[配置済みのデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54474-145">For more information about viewing health status for individual data-tier applications, or to view or change policy configuration settings, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="54474-146">ユーティリティの記憶域使用率の履歴</span><span class="sxs-lookup"><span data-stu-id="54474-146">Utility Storage Utilization History</span></span>  
 <span data-ttu-id="54474-147">使用率の履歴は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティ ダッシュボードの下部にある時間グラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-147">Utilization history is shown in a time graph at the bottom of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility dashboard.</span></span> <span data-ttu-id="54474-148">時間データとして、UCP のローカル日時が datetime データ型で表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="54474-148">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="54474-149">詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54474-149">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="54474-150">ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="54474-150">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="54474-151">詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54474-151">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="54474-152">表示領域の左側にあるオプション ボタンを使用して、グラフ表示の対象期間を変更できます。</span><span class="sxs-lookup"><span data-stu-id="54474-152">Use the radio buttons to the left of the display area to change the reporting period for the graph.</span></span>  
  
 <span data-ttu-id="54474-153">対象期間のオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54474-153">Options for the reporting interval are:</span></span>  
  
-   <span data-ttu-id="54474-154">[1 日] : 15 分間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-154">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="54474-155">[1 週間] : 1 日間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-155">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="54474-156">[1 か月] : 1 週間間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-156">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="54474-157">[1 年] : 1 か月間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="54474-157">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="54474-158">レポート間隔を変更すると、データが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="54474-158">After you make a change to the reporting interval, the data refreshes automatically.</span></span>  
  
 <span data-ttu-id="54474-159">ユーティリティの記憶域使用率</span><span class="sxs-lookup"><span data-stu-id="54474-159">Utility Storage Utilization</span></span>  
 <span data-ttu-id="54474-160">ダッシュボードの右下には、記憶域の使用率を示す円グラフが表示されます。このグラフでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスを含むコンピューターにあるボリュームについて、使用済み領域と空き領域の比率を確認できます。</span><span class="sxs-lookup"><span data-stu-id="54474-160">In the bottom right of the dashboard, the storage utilization pie chart displays the ratio of used space to free space on volumes residing on computers that contain managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54474-161">ここに表示されるデータは、15 分ごとに更新されます。</span><span class="sxs-lookup"><span data-stu-id="54474-161">Data for this display are refreshed every 15 minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54474-162">参照</span><span class="sxs-lookup"><span data-stu-id="54474-162">See Also</span></span>  
 <span data-ttu-id="54474-163">[ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="54474-163">[Use Utility Explorer to Manage the SQL Server Utility](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="54474-164">[SQL Server &#40;SQL Server ユーティリティのインスタンスを登録する&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="54474-164">[Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="54474-165">リソース正常性ポリシーの定義の変更 &#40;SQL Server Utility&#41;</span><span class="sxs-lookup"><span data-stu-id="54474-165">Modify a Resource Health Policy Definition &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)  
  
  
