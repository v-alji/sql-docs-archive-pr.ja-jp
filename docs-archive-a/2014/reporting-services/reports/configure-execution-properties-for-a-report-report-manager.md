---
title: レポートの実行プロパティを構成する (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51cd7b5db225b39f5a061ed750b2ef5cdd265b9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646017"
---
# <a name="configure-execution-properties-for-a-report--report-manager"></a><span data-ttu-id="cd118-102">レポートの実行プロパティを構成する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="cd118-102">Configure Execution Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="cd118-103">レポートの処理オプションでは、レポート データが取得されるタイミングを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd118-103">You can set report processing options to specify when data is retrieved for a report.</span></span> <span data-ttu-id="cd118-104">レポート データ処理のスケジュールを設定することは、外部データ ソースが特定の時刻に更新される場合 (日次または週次で更新されるデータ ウェアハウスなど) や、レポート要求のたびに同じデータが取得されるオーバーヘッドを回避したい場合などに効果的です。</span><span class="sxs-lookup"><span data-stu-id="cd118-104">It is useful to schedule data processing for a report if the external data source is refreshed at specific times (for example, a data warehouse that is refreshed daily or weekly) and you want to avoid the overhead of retrieving the same data each time a report is requested.</span></span> <span data-ttu-id="cd118-105">また、外部のデータベース サーバーにかかる処理負荷を制御する場合や、まったく同じ一連のデータを扱う複数のユーザーに一貫性した結果を提供する場合に役立てることもできます。</span><span class="sxs-lookup"><span data-stu-id="cd118-105">Scheduling data processing is also useful if you want to control the processing load on the external database server or when you want to provide consistent results for multiple users who must work with identical sets of data.</span></span> <span data-ttu-id="cd118-106">変化しやすいデータを使用した場合、レポートを要求するたびに異なる結果が生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd118-106">With volatile data, an on-demand report can produce different results from one minute to the next.</span></span> <span data-ttu-id="cd118-107">一方、レポート スナップショットでは、同時点のデータを含む他のレポートや分析ツールとの有効な比較が可能になります。</span><span class="sxs-lookup"><span data-stu-id="cd118-107">A report snapshot, by contrast, allows you to make valid comparisons against other reports or analytical tools that contain data from the same point in time.</span></span>  
  
 <span data-ttu-id="cd118-108">レポート スナップショットは、特定の時点で取得されたレイアウト指定およびクエリ結果を含むレポートです。</span><span class="sxs-lookup"><span data-stu-id="cd118-108">A report snapshot is a report that contains layout instructions and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="cd118-109">レポートを選択したときに最新のクエリ結果を取得する要求時レポートとは異なり、レポート スナップショットはスケジュールに従って処理され、その後、レポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="cd118-109">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="cd118-110">表示するレポート スナップショットを選択すると、レポート サーバーによってレポート サーバー データベースに格納されたレポートが取得され、スナップショット作成時点のレポートで最新だったデータとレイアウトを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd118-110">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
 <span data-ttu-id="cd118-111">レポート スナップショットは、特定の表示形式では保存されません。</span><span class="sxs-lookup"><span data-stu-id="cd118-111">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="cd118-112">その代わりに、レポート スナップショットは、ユーザーまたはアプリケーションが要求したときのみ、最終的な表示形式 (HTML など) で表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd118-112">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="cd118-113">遅延表示により、スナップショットの移植性が実現します。</span><span class="sxs-lookup"><span data-stu-id="cd118-113">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="cd118-114">レポートは、要求元のデバイスまたは Web ブラウザーの適切な形式で表示できます。</span><span class="sxs-lookup"><span data-stu-id="cd118-114">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
### <a name="to-configure-report-processing-options"></a><span data-ttu-id="cd118-115">レポート処理オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="cd118-115">To configure report processing options</span></span>  
  
1.  <span data-ttu-id="cd118-116">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="cd118-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="cd118-117">処理オプションを設定するレポートに移動し、そのレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="cd118-117">Navigate to and open the report for which you want to set processing options.</span></span>  
  
 <span data-ttu-id="cd118-118">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd118-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
1.  <span data-ttu-id="cd118-119">ドロップダウン メニューで、 **[管理]** をクリックし、 **[処理オプション]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd118-119">In the drop-down menu, click **Manage** and then select the **Processing Options** tab.</span></span>  
  
2.  <span data-ttu-id="cd118-120">**[このレポートを実行スナップショットから表示する]** をクリックしてから、次のオプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd118-120">Click **Render this report from an execution snapshot, and then select one of the following options:**</span></span>  
  
    -   <span data-ttu-id="cd118-121">スナップショットを作成する場合は、 **[次のスケジュールを使用して、レポート実行スナップショットを作成する]** を選択し、レポート固有のスケジュールを定義するか、または **[共有スケジュール]** 一覧からスケジュールを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd118-121">If you want to create a snapshot, select **Use the following schedule to create report execution snapshots**, and then either define a report-specific schedule or select from the **Shared schedule** list.</span></span>  
  
    -   <span data-ttu-id="cd118-122">スナップショットをすぐに作成する場合は、 **[このページの [適用] ボタンをクリックしたときに、レポート スナップショットを作成します]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd118-122">If you want to create a snapshot immediately, select **Create a report snapshot when you click the Apply button on this page**.</span></span>  
  
3.  <span data-ttu-id="cd118-123">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd118-123">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd118-124">参照</span><span class="sxs-lookup"><span data-stu-id="cd118-124">See Also</span></span>  
 <span data-ttu-id="cd118-125">[レポート処理プロパティの設定](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="cd118-125">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="cd118-126">[レポート &#40;レポートマネージャーを開いて閉じる&#41;](../reports/open-and-close-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="cd118-126">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) </span></span>  
 <span data-ttu-id="cd118-127">[[コンテンツ] ページ (レポート マネージャー)](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="cd118-127">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="cd118-128">[レポート サーバー コンテンツの管理 &#40;SSRS ネイティブ モード&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="cd118-128">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="cd118-129">[[処理オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../processing-options-properties-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="cd118-129">[Processing Options Properties Page &#40;Report Manager&#41;](../processing-options-properties-page-report-manager.md)</span></span>  
  
  
