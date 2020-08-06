---
title: 配置されたデータ層アプリケーションの詳細 (SQL Server ユーティリティ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58d0933dcb7682210dde24c3c6d3a9a539d02b1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634021"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a><span data-ttu-id="36b1a-102">配置済みのデータ層アプリケーションの詳細 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="36b1a-102">Deployed Data-tier Application Details (SQL Server Utility)</span></span>
  <span data-ttu-id="36b1a-103">ユーティリティ エクスプローラーの [配置済みのデータ層アプリケーション] ビュー内の情報では、個々のデータ層アプリケーションの使用率に関するデータ、CPU 使用率の履歴、ファイル レベルでの記憶域使用率の詳細を確認できるほか、ポリシーのしきい値を表示および更新できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-103">Information in the Deployed Data-tier Applications view of Utility Explorer provides utilization data for individual data-tier applications, CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="36b1a-104">ポリシーのしきい値は、データ層アプリケーション レベルで CPU 使用率やデータベース データ ファイルおよびログ ファイルを対象に制御できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-104">Policy thresholds can be controlled at the data-tier application level for CPU utilization and for database data files and log files.</span></span> <span data-ttu-id="36b1a-105">個々のデータ層アプリケーションについて、プロパティの詳細を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-105">You can also view property details for individual data-tier applications.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="36b1a-106">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="36b1a-106">UI element list</span></span>  
 <span data-ttu-id="36b1a-107">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="36b1a-107">List view</span></span>  
 <span data-ttu-id="36b1a-108">上部ペインのリスト ビューには、個々のデータ層アプリケーションに関するデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-108">The list view in the top pane displays data about individual data-tier applications.</span></span> <span data-ttu-id="36b1a-109">正常性状態アイコンにより、各データ層アプリケーションの状態が使用率カテゴリごとに示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-109">Health state icons provide summary status for each data-tier application by utilization category:</span></span>  
  
-   <span data-ttu-id="36b1a-110">緑のチェック - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - リソース使用率のポリシーに違反していないデータ層アプリケーションの数。</span><span class="sxs-lookup"><span data-stu-id="36b1a-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of data-tier application which are not violating resource utilization policies.</span></span> <span data-ttu-id="36b1a-111">リソースは適正使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="36b1a-112">緑の下向き矢印 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - リソースは過小使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="36b1a-113">赤の上向き矢印 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - リソースは過大使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="36b1a-114">リスト ビュー内で列を左右にドラッグすると、列の順番を変更できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="36b1a-115">リスト ビューに列を追加したり、リスト ビューから列を削除したりするには、列見出しを右クリックして、目的の列を選択または選択解除します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="36b1a-116">右クリック メニューには、並べ替えオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="36b1a-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="36b1a-117">並べ替えは、列名の上部をクリックして有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="36b1a-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのリスト ビューのフィルター オプションにアクセスするには、ユーティリティ エクスプローラーのナビゲーション ペインで **[配置済みのデータ層アプリケーション]** ノードを右クリックし、 **[フィルター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-118">To access filter options for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility list view, right-click on the **Deployed Data-tier applications** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="36b1a-119">フィルターの設定が実装されると、ユーティリティ エクスプローラーの **[配置済みのデータ層アプリケーション]** ノードに **[配置済みのデータ層アプリケーション (フィルター選択)]** というラベルが付けられます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-119">After filter settings have been implemented, the **Deployed Data-tier Applications** node in Utility Explorer will be labeled **Deployed Data-tier Applications (filtered)**.</span></span> <span data-ttu-id="36b1a-120">詳細については、「[[フィルターの設定] &#40;オブジェクト エクスプローラーおよびユーティリティ エクスプローラー&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="36b1a-121">既定では、次の列に各データ層アプリケーションに関する正常性状態の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-121">By default, the following columns display health state information about each data-tier application.</span></span>  
  
-   <span data-ttu-id="36b1a-122">[名前] - データ層アプリケーション名。</span><span class="sxs-lookup"><span data-stu-id="36b1a-122">Name - the data-tier application name.</span></span>  
  
-   <span data-ttu-id="36b1a-123">[アプリケーションの CPU] - このデータ層アプリケーションのプロセッサ使用率の正常性状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-123">Application CPU - Displays the health state of processor utilization for this data-tier application.</span></span> <span data-ttu-id="36b1a-124">このパラメーターの正常性状態は、データ層アプリケーション用に設定された CPU 使用率ポリシーと、変動の多いリソースの評価ポリシーの構成設定に従って決定されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-124">The health state for this parameter is determined according to CPU utilization policy set for the data-tier application and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="36b1a-125">詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-125">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="36b1a-126">このデータ層アプリケーションのプロセッサ使用率の履歴を表示するか、またはポリシーの制限を表示または変更するには、 **[CPU 使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-126">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="36b1a-127">[コンピューターの CPU] - コンピューターのプロセッサ使用率の正常性状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-127">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="36b1a-128">このパラメーターの正常性状態は、コンピューター用に設定された CPU 使用率ポリシーと、変動の多いリソースの評価ポリシーの構成設定に従って決定されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-128">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="36b1a-129">詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-129">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="36b1a-130">このデータ層アプリケーションのプロセッサ使用率の履歴を表示するか、またはポリシーの制限を表示または変更するには、 **[CPU 使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-130">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="36b1a-131">[ファイル領域] - 各データ層アプリケーションに関するファイル領域使用率の正常性状態の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-131">File Space - Displays a summary of health states of file space utilization for each data-tier application.</span></span>  
  
    -   <span data-ttu-id="36b1a-132">緑のチェック - すべてのファイル グループおよびログ ファイル グループの正常性状態が過大使用でも過小使用でもありません。</span><span class="sxs-lookup"><span data-stu-id="36b1a-132">Green check - The health states for all filegroups and the log file group are neither overutilized or underutilized.</span></span>  
  
    -   <span data-ttu-id="36b1a-133">緑の下向き矢印 - 少なくとも 1 つのファイル グループまたはログ ファイル グループの正常性状態が過小使用であり、かつ、いずれのファイル グループまたはログ ファイル グループも過大使用ではありません。</span><span class="sxs-lookup"><span data-stu-id="36b1a-133">Green down arrow - The health state for at least one filegroup or log file group is underutilized, and no filegroup or log file group is overutilized.</span></span>  
  
    -   <span data-ttu-id="36b1a-134">赤の上向き矢印 - 少なくとも 1 つのファイル グループまたはログ ファイル グループの正常性状態が過大使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-134">Red up arrow - The health state for at least one filegroup or the log file group is overutilized.</span></span> <span data-ttu-id="36b1a-135">データベースが "緊急" 状態になっている場合、正常性状態は過大使用になっているログ ファイル領域を示します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-135">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
     <span data-ttu-id="36b1a-136">ファイル領域ポリシーの制限を表示または変更するには、 **[ストレージの使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-136">To view or change the file space policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="36b1a-137">[ボリューム領域] - 選択したデータ層アプリケーションに属するデータベースを含むすべてのボリュームに関するボリューム領域使用率の正常性状態の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-137">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected data-tier application.</span></span> <span data-ttu-id="36b1a-138">いずれかのボリュームの正常性状態が過大使用になっている場合、ボリューム領域の正常性状態は過大使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-138">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="36b1a-139">いずれかのボリュームの正常性状態が過小使用になっており、かつ、いずれのボリュームも過大使用になっていない場合、ボリューム領域の正常性状態は過小使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-139">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="36b1a-140">それ以外の場合、ボリューム領域の正常性状態は適正使用としてリスト ビューに報告されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-140">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="36b1a-141">ポリシーの制限を表示または変更するには、 **[ストレージの使用率]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-141">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="36b1a-142">[ポリシーの種類] - データ層アプリケーションに対して "グローバル" 既定ポリシーまたは "オーバーライド" カスタム ポリシーのいずれを有効にするかを示します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-142">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the data-tier application.</span></span>  
  
-   <span data-ttu-id="36b1a-143">[インスタンス名] - データ層アプリケーションをホストする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-143">Instance Name - Displays the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that hosts the data-tier application.</span></span>  
  
 <span data-ttu-id="36b1a-144">リスト ビューの列見出し領域で右クリック メニューを使用すると、次に示すその他の列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-144">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="36b1a-145">データベース名</span><span class="sxs-lookup"><span data-stu-id="36b1a-145">Database Name</span></span>  
  
-   <span data-ttu-id="36b1a-146">[配置日]</span><span class="sxs-lookup"><span data-stu-id="36b1a-146">Deployed Date</span></span>  
  
-   <span data-ttu-id="36b1a-147">信頼可能: (True または False)</span><span class="sxs-lookup"><span data-stu-id="36b1a-147">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="36b1a-148">照合順序</span><span class="sxs-lookup"><span data-stu-id="36b1a-148">Collation</span></span>  
  
-   <span data-ttu-id="36b1a-149">[互換性レベル]\([Version100] など)</span><span class="sxs-lookup"><span data-stu-id="36b1a-149">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="36b1a-150">暗号化有効: (True または False)</span><span class="sxs-lookup"><span data-stu-id="36b1a-150">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="36b1a-151">復旧モデル: (単純、完全、または一括ログ)</span><span class="sxs-lookup"><span data-stu-id="36b1a-151">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="36b1a-152">[最終報告日時] この列には、UCP のローカル日時が datetime データ型を使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-152">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="36b1a-153">詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-153">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="36b1a-154">ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-154">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="36b1a-155">詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-155">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="36b1a-156">[CPU 使用率] タブ</span><span class="sxs-lookup"><span data-stu-id="36b1a-156">CPU Utilization tab</span></span>  
 <span data-ttu-id="36b1a-157">[CPU 使用率] タブには、データ層アプリケーションとコンピューターの CPU 使用率を示す履歴データのグラフが並んで表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-157">The CPU utilization tab shows side-by-side graphs of historical data for data-tier application and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="36b1a-158">表示領域の右側にあるオプション ボタンで対象期間を指定すると、その期間におけるプロセッサ使用率の履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-158">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="36b1a-159">表示間隔を変更してデータセットを更新するには、一覧にあるオプション ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-159">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="36b1a-160">間隔のオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36b1a-160">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="36b1a-161">[1 日] : 15 分間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-161">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="36b1a-162">[1 週間] : 1 日間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-162">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="36b1a-163">[1 か月] : 1 週間間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-163">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="36b1a-164">[1 年] : 1 か月間隔で表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-164">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="36b1a-165">[ストレージの使用率] タブ</span><span class="sxs-lookup"><span data-stu-id="36b1a-165">Storage Utilization tab</span></span>  
 <span data-ttu-id="36b1a-166">[ストレージの使用率] タブには、リスト ビューで選択したデータ層アプリケーションに属するデータベース ファイルとログ ファイルに関する記憶域使用率の詳細が表示されるツリー ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="36b1a-166">The Storage Utilization tab has a tree view that displays storage utilization details for database files and log files that belong to the data-tier application selected in the list view.</span></span> <span data-ttu-id="36b1a-167">時間データとして、UCP のローカル日時が datetime データ型で表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-167">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="36b1a-168">詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-168">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="36b1a-169">ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-169">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="36b1a-170">詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-170">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="36b1a-171">表示内容は、ファイル グループまたはボリュームごとにグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-171">Display can be grouped by filegroup or by volume.</span></span> <span data-ttu-id="36b1a-172">ファイル グループ ツリー ビューを使用するには、 **[ファイルのグループ化]** の選択項目で **[ファイル グループ]** オプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-172">To use the filegroup tree view, select the **Filegroup** radio button in the **Group files by:** selection.</span></span>  
  
 <span data-ttu-id="36b1a-173">記憶域使用率の履歴のグラフに表示されるデータは、ツリー ビューで選択したノードに応じて変化します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-173">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="36b1a-174">ファイル グループ ノードを選択すると、選択したファイル グループに属するすべてのデータ ファイルによって使用されているファイル領域のグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-174">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="36b1a-175">ログ ファイル ノードを選択すると、選択したデータベースに属するすべてのログ ファイルによって使用されているファイル領域のグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-175">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="36b1a-176">データベース ノードを選択すると、選択したデータベースに属するすべてのデータ ファイルとすべてのログ ファイルによって使用されているファイル領域を合計したグラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-176">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="36b1a-177">個々のファイルの記憶域使用率の状態を表示するには、ツリー ビューでファイル名の横にあるプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-177">To view storage utilization status for individual files, click on the plus sign next to a file name in the tree view.</span></span>  
  
 <span data-ttu-id="36b1a-178">正常性状態のアイコンにより、ポリシーのしきい値と比較した各ファイル グループの状態がひとめでわかります。</span><span class="sxs-lookup"><span data-stu-id="36b1a-178">Health state icons provide at-a-glance status for each filegroup compared to policy thresholds:</span></span>  
  
-   <span data-ttu-id="36b1a-179">緑のチェック - ファイル グループにある少なくとも 1 つのデータ ファイルのファイル領域使用率が過大使用でも過小使用でもありません。</span><span class="sxs-lookup"><span data-stu-id="36b1a-179">Green check - File space utilization for at least one data file in the filegroup is neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="36b1a-180">緑の下向き矢印 - ファイル グループにある少なくとも 1 つのデータ ファイルのファイル領域使用率が過小使用であり、かつ、ファイル グループにあるいずれのファイルも過大使用ではありません。</span><span class="sxs-lookup"><span data-stu-id="36b1a-180">Green down arrow - File space utilization for at least one data file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="36b1a-181">赤の上向き矢印 - ファイル グループにあるすべてのデータ ファイルのファイル領域使用率が過大使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-181">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span> <span data-ttu-id="36b1a-182">データベースが "緊急" 状態になっている場合、正常性状態は過大使用になっているログ ファイル領域を示します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-182">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="36b1a-183">ボリュームごとにファイルを表示するには、 **[ファイルのグループ化]** の選択項目で **[ボリューム]** オプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-183">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="36b1a-184">記憶域使用率の履歴のグラフに、記憶域ボリューム上ですべてのデータ ファイルとすべてのログ ファイルによって使用されているファイル領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-184">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="36b1a-185">ツリーを展開すると、個々のデータベース データ ファイルとログ ファイルの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-185">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="36b1a-186">各ボリュームの状態は、状態アイコンによって示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-186">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="36b1a-187">緑のチェック - リソースは適正使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-187">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="36b1a-188">緑の下向き矢印 - リソースは過小使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-188">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="36b1a-189">赤の上向き矢印 - リソースは過大使用です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-189">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="36b1a-190">[ストレージの使用率] タブ上の各ファイル名の横にあるゲージは、ファイルによって使用されている領域のサイズを、ファイルの有効容量と比較して表します。</span><span class="sxs-lookup"><span data-stu-id="36b1a-190">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="36b1a-191">ゲージの横に表示されるパーセントの値は、ファイルによって使用されている領域のサイズとファイルの有効容量の比率です。</span><span class="sxs-lookup"><span data-stu-id="36b1a-191">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="36b1a-192">ツールヒントでは、各ボリュームおよび各ファイルと有効容量の比較によるパーセント計算に使用されたデータを確認できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-192">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="36b1a-193">ファイルが自動拡張するように構成されていない場合は、ファイルに割り当てられている領域のサイズが有効容量になります。</span><span class="sxs-lookup"><span data-stu-id="36b1a-193">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="36b1a-194">ファイルが自動拡張するように構成されている場合は、現在ファイルに割り当てられている領域のサイズと、現在ボリューム上で利用できる空き領域のサイズの合計が有効容量になります。</span><span class="sxs-lookup"><span data-stu-id="36b1a-194">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="36b1a-195">データ ファイル用およびログ ファイル用に、記憶域使用率のポリシーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-195">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="36b1a-196">ファイルの記憶域使用率ポリシーのしきい値を表示または変更するには、[ストレージの使用率] ペインの下部にある **[ファイル ポリシー]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-196">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="36b1a-197">記憶域ボリュームの記憶域使用率ポリシーのしきい値を表示または変更するには、[ストレージの使用率] ペインの下部にある **[ボリューム ポリシー]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-197">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="36b1a-198">既定のポリシーのしきい値をオーバーライドするには、 **[既定のポリシーをオーバーライド]** のオプション ボタンをクリックして上限と下限の値を指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36b1a-198">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="36b1a-199">ポリシー違反の許容範囲変更の詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-199">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="36b1a-200">[プロパティの詳細] タブ</span><span class="sxs-lookup"><span data-stu-id="36b1a-200">Property Details tab</span></span>  
 <span data-ttu-id="36b1a-201">データ層アプリケーションで一覧表示されるプロパティの詳細には、次のカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="36b1a-201">Property details listed for data-tier applications include the following categories:</span></span>  
  
-   <span data-ttu-id="36b1a-202">データベース名</span><span class="sxs-lookup"><span data-stu-id="36b1a-202">Database Name</span></span>  
  
-   <span data-ttu-id="36b1a-203">[配置日]</span><span class="sxs-lookup"><span data-stu-id="36b1a-203">Deployed Date</span></span>  
  
-   <span data-ttu-id="36b1a-204">信頼可能: (True または False)</span><span class="sxs-lookup"><span data-stu-id="36b1a-204">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="36b1a-205">照合順序</span><span class="sxs-lookup"><span data-stu-id="36b1a-205">Collation</span></span>  
  
-   <span data-ttu-id="36b1a-206">[互換性レベル]\([Version100] など)</span><span class="sxs-lookup"><span data-stu-id="36b1a-206">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="36b1a-207">暗号化有効: (True または False)</span><span class="sxs-lookup"><span data-stu-id="36b1a-207">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="36b1a-208">復旧モデル: (単純、完全、または一括ログ)</span><span class="sxs-lookup"><span data-stu-id="36b1a-208">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="36b1a-209">[最終報告日時] この列には、UCP のローカル日時が datetime データ型を使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="36b1a-209">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="36b1a-210">詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-210">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="36b1a-211">ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-211">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="36b1a-212">詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36b1a-212">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b1a-213">参照</span><span class="sxs-lookup"><span data-stu-id="36b1a-213">See Also</span></span>  
 <span data-ttu-id="36b1a-214">[Managed Instance の詳細 &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="36b1a-214">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="36b1a-215">[ユーティリティダッシュボード &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="36b1a-215">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="36b1a-216">[SQL Server ユーティリティでの SQL Server のインスタンスの監視](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="36b1a-216">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="36b1a-217">SQL Server ユーティリティの機能とタスク</span><span class="sxs-lookup"><span data-stu-id="36b1a-217">SQL Server Utility Features and Tasks</span></span>](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
