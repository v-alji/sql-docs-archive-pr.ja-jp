---
title: レポート履歴の作成 (Reporting Services の SharePoint 統合モード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 996202580bbacc24080460c2c43218db27294d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642543"
---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="8115e-102">レポート履歴の作成 (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="8115e-102">Create Report History (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="8115e-103">レポート履歴とは、時間の経過と共に作成されるレポート スナップショットの集まりです。</span><span class="sxs-lookup"><span data-stu-id="8115e-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="8115e-104">各スナップショットは、レポート作成時の状態でのレポートのコピーであり、</span><span class="sxs-lookup"><span data-stu-id="8115e-104">Each snapshot is a copy of the report as it existed when it was created.</span></span> <span data-ttu-id="8115e-105">スナップショット作成時点のレポートのレイアウトとデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8115e-105">It includes the layout and data that was current for the report when the snapshot was created.</span></span> <span data-ttu-id="8115e-106">レンダリング情報はスナップショットに保存されません。</span><span class="sxs-lookup"><span data-stu-id="8115e-106">Rendering information is not stored with the snapshot.</span></span> <span data-ttu-id="8115e-107">レポート履歴のスナップショットを開くと、スナップショットはレポート ビューアー Web パーツに HTML 形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="8115e-107">When you open a snapshot in report history, it opens in HTML in the Report Viewer Web Part.</span></span> <span data-ttu-id="8115e-108">表示されたスナップショットは、別のアプリケーション形式にエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="8115e-108">After it is rendered, you can export it to other application formats.</span></span>  
  
 <span data-ttu-id="8115e-109">レポート履歴を作成するには、レポートの自動実行が可能な状態である必要があります (つまり、レポート サーバー側で、ユーザーの操作を必要とせずにレポートを実行できる必要があります)。</span><span class="sxs-lookup"><span data-stu-id="8115e-109">To create report history, the report must be able to run unattended (that is, the report server must be able to run the report without user interaction).</span></span> <span data-ttu-id="8115e-110">レポートを含むライブラリに対する、"アイテムの編集" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8115e-110">You must have Edit Items permission on the library that contains the report.</span></span> <span data-ttu-id="8115e-111">レポート履歴を表示または削除するには、"バージョンの表示" 権限または "バージョンの削除" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8115e-111">To view or delete report history, you must have View Versions or Delete Versions permissions.</span></span>  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a><span data-ttu-id="8115e-112">スナップショットまたはレポート履歴を必要に応じて作成するには</span><span class="sxs-lookup"><span data-stu-id="8115e-112">To create a snapshot or report history on demand</span></span>  
  
1.  <span data-ttu-id="8115e-113">レポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="8115e-113">Point to the report.</span></span>  
  
2.  <span data-ttu-id="8115e-114">クリックして下矢印を表示し、 **[レポート履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8115e-114">Click to display the down arrow, and then select **View Report History**.</span></span>  
  
3.  <span data-ttu-id="8115e-115">**[新しいスナップショット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8115e-115">Click **New Snapshot**.</span></span> <span data-ttu-id="8115e-116">レポート履歴にスナップショットを作成する権限がない場合、このボタンは表示されません。</span><span class="sxs-lookup"><span data-stu-id="8115e-116">If the button is not visible, it is because you do not have permission to create snapshots in report history.</span></span>  
  
4.  <span data-ttu-id="8115e-117">作成したスナップショットを表示するには、一覧から作成したスナップショットを選択します。</span><span class="sxs-lookup"><span data-stu-id="8115e-117">To view the snapshot you just created, select it from the list.</span></span> <span data-ttu-id="8115e-118">各スナップショットは、スナップショットの作成日時を示すタイムスタンプで識別できます。</span><span class="sxs-lookup"><span data-stu-id="8115e-118">Each snapshot is identified by a timestamp that shows when the snapshot was created.</span></span> <span data-ttu-id="8115e-119">スナップショットは、名前を変更したり、別の場所に移動したり、内容を変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8115e-119">You cannot rename the snapshot, move it to another location, or modify it.</span></span>  
  
### <a name="to-schedule-report-history"></a><span data-ttu-id="8115e-120">レポート履歴をスケジュールするには</span><span class="sxs-lookup"><span data-stu-id="8115e-120">To schedule report history</span></span>  
  
1.  <span data-ttu-id="8115e-121">レポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="8115e-121">Point to the report.</span></span>  
  
2.  <span data-ttu-id="8115e-122">クリックして下矢印を表示し、 **[処理オプションの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8115e-122">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="8115e-123">**[履歴スナップショットのオプション]** の **[スケジュールに従ってレポート履歴スナップショットを作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8115e-123">In **History Snapshot Options**, click **Create report history snapshots on a schedule**.</span></span>  
  
4.  <span data-ttu-id="8115e-124">使用するスケジュール情報が含まれている共有スケジュールがある場合は、 **[次の共有スケジュールで実行する]** をクリックし、使用するスケジュールを選択します。</span><span class="sxs-lookup"><span data-stu-id="8115e-124">If you have a shared schedule that contains the schedule information you want to use, click **On a shared schedule** and select the schedule you want to use.</span></span> <span data-ttu-id="8115e-125">それ以外の場合は、 **[カスタム スケジュールで実行する]** をクリックし、 **[構成]** をクリックして、定期的にレポート履歴を作成するためのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="8115e-125">Otherwise, click **On a custom schedule**, and then click **Configure** to specify options to create report history on a recurring schedule.</span></span>  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a><span data-ttu-id="8115e-126">レポートのデータが更新されたときにレポート履歴を作成するには</span><span class="sxs-lookup"><span data-stu-id="8115e-126">To create report history when data is refreshed in a report</span></span>  
  
1.  <span data-ttu-id="8115e-127">レポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="8115e-127">Point to the report.</span></span>  
  
2.  <span data-ttu-id="8115e-128">クリックして下矢印を表示し、 **[処理オプションの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8115e-128">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="8115e-129">**[履歴スナップショットのオプション]** の **[すべてのレポート データ スナップショットをレポート履歴に保存します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8115e-129">In **History Snapshot Options**, click **Store all report data snapshots in report history**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8115e-130">参照</span><span class="sxs-lookup"><span data-stu-id="8115e-130">See Also</span></span>  
 [<span data-ttu-id="8115e-131">処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8115e-131">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  
