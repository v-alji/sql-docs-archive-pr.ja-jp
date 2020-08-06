---
title: Managed Instance の詳細 (SQL Server ユーティリティ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 6e51b7bb-a733-4852-8c33-7f4dbdf931c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f895f9978511ab7b2b40b3f161185a68a497b2eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738689"
---
# <a name="managed-instance-details-sql-server-utility"></a><span data-ttu-id="e143a-102">マネージド インスタンスの詳細 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="e143a-102">Managed Instance Details (SQL Server Utility)</span></span>
  <span data-ttu-id="e143a-103">ユーティリティ エクスプローラーの [マネージド インスタンス] ビューでは、個々の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスの使用率に関するデータ、CPU 使用率の履歴、ファイル レベルでの記憶域使用率の詳細を参照できます。ポリシーしきい値の表示と更新も可能です。</span><span class="sxs-lookup"><span data-stu-id="e143a-103">Information in the Managed Instances view of Utility Explorer provides utilization data for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="e143a-104">ポリシーのしきい値は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス レベルでコンピューター、データベース ファイル、およびログ ファイルを対象に制御するか、記憶域ボリュームのレベルで制御することができます。</span><span class="sxs-lookup"><span data-stu-id="e143a-104">Policy thresholds can be controlled at the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance level, for a computer, for database files and log files, and at the level of storage volumes.</span></span> <span data-ttu-id="e143a-105">特定の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]マネージド インスタンスのプロパティ詳細を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="e143a-105">You can also view property details for individual managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="e143a-106">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="e143a-106">UI element list</span></span>  
 <span data-ttu-id="e143a-107">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="e143a-107">List view</span></span>  
 <span data-ttu-id="e143a-108">上部のペインには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の個々のインスタンス (ComputerName\InstanceName) とそのデータがリスト表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-108">The list view in the top pane displays data about individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listed in rows by ComputerName\InstanceName.</span></span>  
  
 <span data-ttu-id="e143a-109">正常性状態アイコンにより、各 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの状態が使用率カテゴリごとに示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-109">Health state icons provide summary status for each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by utilization category:</span></span>  
  
-   <span data-ttu-id="e143a-110">緑のチェック - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - リソース使用率のポリシーに違反していない、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="e143a-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span> <span data-ttu-id="e143a-111">リソースは適正使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="e143a-112">緑の下向き矢印 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - リソースは過小使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="e143a-113">赤の上向き矢印 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - リソースは過大使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="e143a-114">リスト ビュー内で列を左右にドラッグすると、列の順番を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e143a-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="e143a-115">リスト ビューに列を追加したり、リスト ビューから列を削除したりするには、列見出しを右クリックして、目的の列を選択または選択解除します。</span><span class="sxs-lookup"><span data-stu-id="e143a-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="e143a-116">右クリック メニューには、並べ替えオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="e143a-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="e143a-117">並べ替えは、列名の上部をクリックして有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e143a-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="e143a-118">ユーティリティのリスト ビューのフィルター オプションにアクセスするには、ユーティリティ エクスプローラーのナビゲーション ペインで **[マネージド インスタンス]** ノードを右クリックし、 **[フィルター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e143a-118">To access filter options for the Utility list view, right-click on the **Managed Instances** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="e143a-119">フィルターを設定すると、ユーティリティ エクスプローラーの **[マネージド インスタンス]** ノードが **[マネージド インスタンス (フィルター選択)]** という名前になります。</span><span class="sxs-lookup"><span data-stu-id="e143a-119">After filter settings have been implemented, the **Managed Instances** node in Utility Explorer will be labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="e143a-120">詳細については、「[[フィルターの設定] &#40;オブジェクト エクスプローラーおよびユーティリティ エクスプローラー&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="e143a-121">既定では、次の列に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の各マネージド インスタンスに関する正常性状態の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-121">By default, the following columns display health state information about each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e143a-122">[インスタンスの CPU] - この [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスに割り当てられたプロセッサ使用率の正常性状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-122">Instance CPU - Displays the health state of processor utilization allocated to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e143a-123">このパラメーターの正常性状態は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス用に設定された CPU 使用率ポリシーと、変動の多いリソースの評価ポリシーの構成設定に従って決定されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-123">The health state for this parameter is determined according to CPU utilization policy set for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="e143a-124">詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-124">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="e143a-125">この [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスのプロセッサ使用率の履歴を表示するか、またはポリシーの制限を表示または変更するには、 **[CPU 使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-125">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="e143a-126">[コンピューターの CPU] - コンピューターのプロセッサ使用率の正常性状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-126">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="e143a-127">このパラメーターの正常性状態は、コンピューター用に設定された CPU 使用率ポリシーと、変動の多いリソースの評価ポリシーの構成設定に従って決定されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-127">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="e143a-128">詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-128">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="e143a-129">この [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスのプロセッサ使用率の履歴を表示するか、またはポリシーの制限を表示または変更するには、 **[CPU 使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-129">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="e143a-130">[ファイル領域] - 選択した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスに属するすべてのデータベースについて、ファイル領域使用率の正常性状態の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-130">File Space - Displays a summary of health states of file space utilization for all databases that belong to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e143a-131">いずれかのデータベースの正常性状態が過大使用になっている場合、そのファイル領域の正常性状態は過大使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-131">If the health state of any database is overutilized, then the file space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="e143a-132">いずれかのデータベースの正常性状態が過小使用になっており、かつ、いずれのデータベースも過大使用でない場合、そのファイル領域の正常性状態は過小使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-132">If the health state of any database is underutilized, and no database is overutilized, then the file space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="e143a-133">それ以外の場合、ファイル領域の正常性状態は適正使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-133">Otherwise, the file space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="e143a-134">ポリシーの制限を表示または変更するには、 **[ストレージの使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-134">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="e143a-135">[ボリューム領域] - 選択した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスに属するデータベースを含むすべてのボリュームについて、ボリューム領域使用率の正常性状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-135">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e143a-136">いずれかのボリュームの正常性状態が過大使用になっている場合、ボリューム領域の正常性状態は過大使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-136">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="e143a-137">いずれかのボリュームの正常性状態が過小使用になっており、かつ、いずれのボリュームも過大使用になっていない場合、ボリューム領域の正常性状態は過小使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-137">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="e143a-138">それ以外の場合、ボリューム領域の正常性状態は適正使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-138">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="e143a-139">ポリシーの制限を表示または変更するには、 **[ストレージの使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-139">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="e143a-140">[ポリシーの種類] - [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンスに対して、"グローバル" 既定ポリシーまたは "オーバーライド" カスタム ポリシーのいずれを有効にするかを示します。</span><span class="sxs-lookup"><span data-stu-id="e143a-140">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e143a-141">リスト ビューの列見出し領域で右クリック メニューを使用すると、次に示すその他の列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e143a-141">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="e143a-142">[プロセッサ名]</span><span class="sxs-lookup"><span data-stu-id="e143a-142">Processor Name:</span></span>  
  
-   <span data-ttu-id="e143a-143">[プロセッサの速度 (MHz)]</span><span class="sxs-lookup"><span data-stu-id="e143a-143">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="e143a-144">[プロセッサ数]</span><span class="sxs-lookup"><span data-stu-id="e143a-144">Processor Count:</span></span>  
  
-   <span data-ttu-id="e143a-145">[物理メモリ (MB)]</span><span class="sxs-lookup"><span data-stu-id="e143a-145">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="e143a-146">[オペレーティング システムのバージョン]</span><span class="sxs-lookup"><span data-stu-id="e143a-146">Operating System Version:</span></span>  
  
-   <span data-ttu-id="e143a-147">[SQL Server のバージョン]</span><span class="sxs-lookup"><span data-stu-id="e143a-147">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="e143a-148">[SQL Server のエディション]</span><span class="sxs-lookup"><span data-stu-id="e143a-148">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="e143a-149">[クラスター化] (True または False)</span><span class="sxs-lookup"><span data-stu-id="e143a-149">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="e143a-150">[バックアップ ディレクトリ]</span><span class="sxs-lookup"><span data-stu-id="e143a-150">Backup Directory:</span></span>  
  
-   <span data-ttu-id="e143a-151">[照合順序]</span><span class="sxs-lookup"><span data-stu-id="e143a-151">Collation:</span></span>  
  
-   <span data-ttu-id="e143a-152">[大文字と小文字を区別する] (True または False)</span><span class="sxs-lookup"><span data-stu-id="e143a-152">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="e143a-153">[言語]</span><span class="sxs-lookup"><span data-stu-id="e143a-153">Language:</span></span>  
  
-   <span data-ttu-id="e143a-154">[最終報告日時] この列には、UCP のローカル日時が datetime データ型を使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-154">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="e143a-155">詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-155">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="e143a-156">ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-156">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="e143a-157">詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-157">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e143a-158">[CPU 使用率] タブ</span><span class="sxs-lookup"><span data-stu-id="e143a-158">CPU Utilization tab</span></span>  
 <span data-ttu-id="e143a-159">[CPU 使用率] タブには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとコンピューターの CPU 使用率を示す履歴データのグラフが並んで表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-159">The CPU utilization tab shows side-by-side graphs of historical data for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="e143a-160">表示領域の右側にあるオプション ボタンで対象期間を指定すると、その期間におけるプロセッサ使用率の履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-160">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="e143a-161">表示間隔を変更してデータセットを更新するには、一覧にあるオプション ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e143a-161">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="e143a-162">間隔のオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e143a-162">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="e143a-163">[1 日] : 15 分間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-163">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="e143a-164">[1 週間] : 1 日間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-164">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="e143a-165">[1 か月] : 1 週間間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-165">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="e143a-166">[1 年] : 1 か月間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-166">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="e143a-167">[ストレージの使用率] タブ</span><span class="sxs-lookup"><span data-stu-id="e143a-167">Storage Utilization tab</span></span>  
 <span data-ttu-id="e143a-168">[ストレージの使用率] タブには、記憶域使用率の詳細が表示されるツリー ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="e143a-168">The Storage Utilization tab has a tree view that displays storage utilization details.</span></span> <span data-ttu-id="e143a-169">時間データとして、UCP のローカル日時が datetime データ型で表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-169">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="e143a-170">詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-170">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="e143a-171">ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-171">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="e143a-172">詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-172">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e143a-173">表示内容は、データベースまたはボリュームごとにグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="e143a-173">Display can be grouped by database or by volume.</span></span> <span data-ttu-id="e143a-174">データベース ツリー ビューを使用するには、 **[ファイルのグループ化]** の選択項目で **[データベース]** オプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-174">To use the database tree view, select the **Database** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="e143a-175">個々のデータベース ファイルの記憶域使用率の状態を表示するには、ツリー ビューでデータベース名の横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-175">To view storage utilization status for individual database files, click on the plus sign next to a database name in the tree view.</span></span> <span data-ttu-id="e143a-176">一覧表示されるデータベース ファイルには、リスト ビューで選択した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスに属する、すべてのシステム データベースとユーザー データベースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e143a-176">The database files listed include all system and user databases that belong to the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] you selected in the list view.</span></span>  
  
 <span data-ttu-id="e143a-177">ツリー構造は、記憶域の階層に対応しています。</span><span class="sxs-lookup"><span data-stu-id="e143a-177">The tree structure corresponds to the storage hierarchy.</span></span> <span data-ttu-id="e143a-178">ツリー ビューのルート ノードはデータベースです。</span><span class="sxs-lookup"><span data-stu-id="e143a-178">The root node in the tree view is the database.</span></span> <span data-ttu-id="e143a-179">ツリー ビューの次のレベルには、データベースに属する 1 つ以上のファイル グループ ノードと、データベースに属するログのログ ファイル ノードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e143a-179">The next level of the tree view contains a filegroup node or nodes that belong to the database, and a log file node for the logs that belong to the database.</span></span> <span data-ttu-id="e143a-180">次のレベルには、ファイル グループに属するデータ ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e143a-180">The next level contains the data files that belong to the filegroup.</span></span>  
  
 <span data-ttu-id="e143a-181">記憶域使用率の履歴のグラフに表示されるデータは、ツリー ビューで選択したノードに応じて変化します。</span><span class="sxs-lookup"><span data-stu-id="e143a-181">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="e143a-182">ファイル グループ ノードを選択すると、選択したファイル グループに属するすべてのデータ ファイルによって使用されているファイル領域のグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-182">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="e143a-183">ログ ファイル ノードを選択すると、選択したデータベースに属するすべてのログ ファイルによって使用されているファイル領域のグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-183">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="e143a-184">データベース ノードを選択すると、選択したデータベースに属するすべてのデータ ファイルとすべてのログ ファイルによって使用されているファイル領域を合計したグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-184">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="e143a-185">正常性状態のアイコンにより、データベース ファイル、ファイル グループ、およびログ ファイルの状態がひとめでわかります。</span><span class="sxs-lookup"><span data-stu-id="e143a-185">Health state icons provide at-a-glance status for database files, filegroups, and log files:</span></span>  
  
 <span data-ttu-id="e143a-186">データベースの場合 :</span><span class="sxs-lookup"><span data-stu-id="e143a-186">For databases:</span></span>  
  
-   <span data-ttu-id="e143a-187">緑のチェック - すべてのファイル グループおよびログ ファイルの正常性状態が過大使用でも過小使用でもありません。</span><span class="sxs-lookup"><span data-stu-id="e143a-187">Green check - Health states of all filegroups and log files a neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="e143a-188">緑の下向き矢印 - 少なくとも 1 つのファイル グループまたはログ ファイルの正常性状態が過小使用であり、かつ、いずれの正常性状態も過大使用ではありません。</span><span class="sxs-lookup"><span data-stu-id="e143a-188">Green down arrow - Health states of at least one filegroup or log file is underutilized, and no health states are overutilized.</span></span>  
  
-   <span data-ttu-id="e143a-189">赤の上向き矢印 - 少なくとも 1 つのファイル グループまたはログ ファイルの正常性状態が過大使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-189">Red up arrow - The health state of at least one filegroup or log file is overutilized.</span></span>  
  
 <span data-ttu-id="e143a-190">ファイル グループおよびログ ファイルの場合 :</span><span class="sxs-lookup"><span data-stu-id="e143a-190">For filegroups and log files:</span></span>  
  
-   <span data-ttu-id="e143a-191">緑のチェック - ファイル グループにあるすべてのファイルのファイル領域使用率が過大使用でも過小使用でもありません。</span><span class="sxs-lookup"><span data-stu-id="e143a-191">Green check - File space utilization for all files in the filegroup are neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="e143a-192">緑の下向き矢印 - ファイル グループにある少なくとも 1 つのファイルのファイル領域使用率が過小使用であり、かつ、ファイル グループにあるいずれのファイルも過大使用ではありません。</span><span class="sxs-lookup"><span data-stu-id="e143a-192">Green down arrow - File space utilization for at least one file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="e143a-193">赤の上向き矢印 - ファイル グループにあるすべてのデータ ファイルのファイル領域使用率が過大使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-193">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span>  
  
 <span data-ttu-id="e143a-194">ボリュームごとにファイルを表示するには、 **[ファイルのグループ化]** の選択項目で **[ボリューム]** オプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-194">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="e143a-195">記憶域使用率の履歴のグラフに、記憶域ボリューム上ですべてのデータ ファイルとすべてのログ ファイルによって使用されているファイル領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-195">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="e143a-196">ツリーを展開すると、個々のデータベース データ ファイルとログ ファイルの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e143a-196">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="e143a-197">各ボリュームの状態は、状態アイコンによって示されます。</span><span class="sxs-lookup"><span data-stu-id="e143a-197">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="e143a-198">緑のチェック - リソースは適正使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-198">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="e143a-199">緑の下向き矢印 - リソースは過小使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-199">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="e143a-200">赤の上向き矢印 - リソースは過大使用です。</span><span class="sxs-lookup"><span data-stu-id="e143a-200">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="e143a-201">[ストレージの使用率] タブ上の各ファイル名の横にあるゲージは、ファイルによって使用されている領域のサイズを、ファイルの有効容量と比較して表します。</span><span class="sxs-lookup"><span data-stu-id="e143a-201">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="e143a-202">ゲージの横に表示されるパーセントの値は、ファイルによって使用されている領域のサイズとファイルの有効容量の比率です。</span><span class="sxs-lookup"><span data-stu-id="e143a-202">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="e143a-203">ツールヒントでは、各ボリュームおよび各ファイルと有効容量の比較によるパーセント計算に使用されたデータを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e143a-203">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="e143a-204">ファイルが自動拡張するように構成されていない場合は、ファイルに割り当てられている領域のサイズが有効容量になります。</span><span class="sxs-lookup"><span data-stu-id="e143a-204">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="e143a-205">ファイルが自動拡張するように構成されている場合は、現在ファイルに割り当てられている領域のサイズと、現在ボリューム上で利用できる空き領域のサイズの合計が有効容量になります。</span><span class="sxs-lookup"><span data-stu-id="e143a-205">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="e143a-206">データ ファイル用およびログ ファイル用に、記憶域使用率のポリシーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="e143a-206">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="e143a-207">ファイルの記憶域使用率ポリシーのしきい値を表示または変更するには、[ストレージの使用率] ペインの下部にある **[ファイル ポリシー]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-207">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="e143a-208">記憶域ボリュームの記憶域使用率ポリシーのしきい値を表示または変更するには、[ストレージの使用率] ペインの下部にある **[ボリューム ポリシー]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-208">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="e143a-209">既定のポリシーのしきい値をオーバーライドするには、 **[既定のポリシーをオーバーライド]** のオプション ボタンをクリックして上限と下限の値を指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e143a-209">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="e143a-210">ポリシー違反の許容範囲変更の詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e143a-210">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="e143a-211">[プロパティの詳細] タブ</span><span class="sxs-lookup"><span data-stu-id="e143a-211">Property Details tab</span></span>  
 <span data-ttu-id="e143a-212">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで一覧表示されるプロパティの詳細には、次のカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="e143a-212">Property details listed for instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] include the following categories:</span></span>  
  
-   <span data-ttu-id="e143a-213">[プロセッサ名]</span><span class="sxs-lookup"><span data-stu-id="e143a-213">Processor Name:</span></span>  
  
-   <span data-ttu-id="e143a-214">[プロセッサの速度 (MHz)]</span><span class="sxs-lookup"><span data-stu-id="e143a-214">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="e143a-215">[プロセッサ数]</span><span class="sxs-lookup"><span data-stu-id="e143a-215">Processor Count:</span></span>  
  
-   <span data-ttu-id="e143a-216">[物理メモリ (MB)]</span><span class="sxs-lookup"><span data-stu-id="e143a-216">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="e143a-217">[オペレーティング システムのバージョン]</span><span class="sxs-lookup"><span data-stu-id="e143a-217">Operating System Version:</span></span>  
  
-   <span data-ttu-id="e143a-218">[SQL Server のバージョン]</span><span class="sxs-lookup"><span data-stu-id="e143a-218">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="e143a-219">[SQL Server のエディション]</span><span class="sxs-lookup"><span data-stu-id="e143a-219">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="e143a-220">[クラスター化] (True または False)</span><span class="sxs-lookup"><span data-stu-id="e143a-220">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="e143a-221">[バックアップ ディレクトリ]</span><span class="sxs-lookup"><span data-stu-id="e143a-221">Backup Directory:</span></span>  
  
-   <span data-ttu-id="e143a-222">[照合順序]</span><span class="sxs-lookup"><span data-stu-id="e143a-222">Collation:</span></span>  
  
-   <span data-ttu-id="e143a-223">[大文字と小文字を区別する] (True または False)</span><span class="sxs-lookup"><span data-stu-id="e143a-223">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="e143a-224">[言語]</span><span class="sxs-lookup"><span data-stu-id="e143a-224">Language:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e143a-225">参照</span><span class="sxs-lookup"><span data-stu-id="e143a-225">See Also</span></span>  
 <span data-ttu-id="e143a-226">[配置されたデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e143a-226">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="e143a-227">[ユーティリティダッシュボード &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e143a-227">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="e143a-228">[SQL Server ユーティリティでの SQL Server のインスタンスの監視](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e143a-228">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="e143a-229">[SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="e143a-229">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="e143a-230">SQL Server ユーティリティのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e143a-230">Troubleshoot the SQL Server Utility</span></span>](../../2014/database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
