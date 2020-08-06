---
title: レポート履歴のスナップショットの作成、変更および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ee091ad3361280c4da258eb86c83492ade8b3bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642547"
---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a><span data-ttu-id="e04e5-102">レポート履歴のスナップショットの作成、変更および削除</span><span class="sxs-lookup"><span data-stu-id="e04e5-102">Create, Modify, and Delete Snapshots in Report History</span></span>
  <span data-ttu-id="e04e5-103">レポート履歴は、一連のレポート スナップショットです。</span><span class="sxs-lookup"><span data-stu-id="e04e5-103">Report history is a collection of report snapshots.</span></span> <span data-ttu-id="e04e5-104">スナップショットの追加と削除、またはレポート履歴の記憶域に影響するプロパティの変更を行うことで、レポート履歴を管理できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-104">You can maintain report history by adding and deleting snapshots, or by modifying properties that affect report history storage.</span></span> <span data-ttu-id="e04e5-105">レポート履歴は手動で、またはスケジュールに従って作成できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-105">You can create report history manually or on a schedule.</span></span>  
  
 <span data-ttu-id="e04e5-106">レポート履歴を作成するには、ロールの割り当てに "レポート履歴の管理" タスクが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e04e5-106">To create report history, your role assignment must include the "Manage report history" task.</span></span> <span data-ttu-id="e04e5-107">レポート履歴を表示するには、ロールの割り当てに "レポートの表示" タスクが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e04e5-107">To view report history, your role assignment must include the "View reports" task.</span></span> <span data-ttu-id="e04e5-108">レポート履歴は、レポートにアクセスできるすべてのユーザーが利用できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-108">Report history is available to all users who have access to the report.</span></span> <span data-ttu-id="e04e5-109">一部のユーザーを対象に、レポート履歴の有効化または無効化を選択的に行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="e04e5-109">You cannot selectively enable or disable report history for a subset of users.</span></span>  
  
 <span data-ttu-id="e04e5-110">レポート履歴のスナップショットは、スナップショットの作成日時で識別されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-110">Snapshots in report history are identified by the date and time that they were created.</span></span> <span data-ttu-id="e04e5-111">その日時は、クエリが実行された日時に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e04e5-111">The date and time is based on when the query executed.</span></span>  
  
## <a name="creating-snapshots-in-report-history"></a><span data-ttu-id="e04e5-112">レポート履歴でのスナップショットの作成</span><span class="sxs-lookup"><span data-stu-id="e04e5-112">Creating Snapshots in Report History</span></span>  
 <span data-ttu-id="e04e5-113">スナップショットは、自動的に実行できる任意のレポートに、手動で、またはスケジュールされた間隔で、作成できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-113">Snapshots can be created manually or at scheduled intervals for any report that can run unattended.</span></span> <span data-ttu-id="e04e5-114">レポートを自動的に実行するには、保存されている資格情報を使用するか、資格情報を使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e04e5-114">To run unattended, the report must use stored credentials or no credentials at all.</span></span> <span data-ttu-id="e04e5-115">また、レポートでパラメーターを使用する場合、レポートの実行時に使用する既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e04e5-115">Furthermore, if the report uses parameters, you must specify default values to use when the report runs.</span></span> <span data-ttu-id="e04e5-116">レポートのプロパティ ページで、格納された資格情報とパラメーター値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-116">You can specify stored credentials and parameter values in the property pages for the report.</span></span> <span data-ttu-id="e04e5-117">詳細については、「[[パラメーター] プロパティ ページ &#40;レポート マネージャー&#41;](../parameters-properties-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e04e5-117">For more information, see [Parameters Properties Page &#40;Report Manager&#41;](../parameters-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="e04e5-118">レポート スナップショットを作成すると、レポート スナップショットと共に、以下の要素がレポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-118">When you create a report snapshot, the following elements are stored along with the report snapshot in the report server database:</span></span>  
  
-   <span data-ttu-id="e04e5-119">結果セット (レポートの [データ ソース] プロパティ ページで指定した資格情報によって取得される、レポート内のデータ)。</span><span class="sxs-lookup"><span data-stu-id="e04e5-119">The result set (that is, the data in the report, retrieved through the credentials specified in the Data Sources properties page of the report).</span></span>  
  
-   <span data-ttu-id="e04e5-120">基になるレポート定義。これは、スナップショットを作成した時点で存在するものです。</span><span class="sxs-lookup"><span data-stu-id="e04e5-120">The underlying report definition, as it exists at the time the snapshot was created.</span></span> <span data-ttu-id="e04e5-121">スナップショットを生成した後にレポート定義を変更する場合、これらの変更はスナップショットに反映されません。</span><span class="sxs-lookup"><span data-stu-id="e04e5-121">If the report definition is subsequently modified after the snapshot is generated, those changes are not reflected in the snapshot.</span></span>  
  
-   <span data-ttu-id="e04e5-122">結果セットの取得またはフィルター処理に使用するパラメーター値。</span><span class="sxs-lookup"><span data-stu-id="e04e5-122">Parameter values that are used to obtain or filter the result set.</span></span>  
  
-   <span data-ttu-id="e04e5-123">画像などの埋め込みリソース。</span><span class="sxs-lookup"><span data-stu-id="e04e5-123">Embedded resources, such as images.</span></span> <span data-ttu-id="e04e5-124">レポートにリンクされている外部リソースは、レポート スナップショットと共には格納されません。</span><span class="sxs-lookup"><span data-stu-id="e04e5-124">External resources that are linked to a report are not stored with the report snapshot.</span></span>  
  
 <span data-ttu-id="e04e5-125">レポート履歴を作成する方法、および格納できるレポート スナップショット数は、設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e04e5-125">The ways in which report history can be created and the number of report snapshots that can be stored are determined by settings.</span></span>  
  
 <span data-ttu-id="e04e5-126">レポートでエラーが発生した場合、スナップショットは作成されません。</span><span class="sxs-lookup"><span data-stu-id="e04e5-126">If a report produces an error, a snapshot is not created.</span></span> <span data-ttu-id="e04e5-127">警告が発生してもそのまま動作するレポートは、スナップショットの生成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-127">Reports that produce warnings, yet still run, can be used to generate snapshots.</span></span>  
  
## <a name="modifying-properties-and-deleting-report-history"></a><span data-ttu-id="e04e5-128">プロパティの変更およびレポート履歴の削除</span><span class="sxs-lookup"><span data-stu-id="e04e5-128">Modifying Properties and Deleting Report History</span></span>  
 <span data-ttu-id="e04e5-129">レポート スナップショットを作成した後に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="e04e5-129">Once a report snapshot exists, you cannot modify it.</span></span> <span data-ttu-id="e04e5-130">ただし、プロパティを変更することはできます。この場合、レポート履歴は削除されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-130">However, you can modify properties in a way that deletes report history.</span></span>  
  
 <span data-ttu-id="e04e5-131">レポート履歴は、以下の方法で削除できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-131">Report history can be deleted in the following ways:</span></span>  
  
-   <span data-ttu-id="e04e5-132">1 つずつ、またはまとめて、スナップショットを手動で削除します。</span><span class="sxs-lookup"><span data-stu-id="e04e5-132">Manually delete snapshots singly or in groups.</span></span>  
  
     <span data-ttu-id="e04e5-133">レポート マネージャーで、[履歴] ページからスナップショットを削除できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-133">You can delete snapshots from the History page in Report Manager.</span></span> <span data-ttu-id="e04e5-134">レポートに移動して [履歴] をクリックし、削除するスナップショットの隣にあるチェック ボックスをオンにして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e04e5-134">Navigate to the report, click History, select the check box next to the snapshots that you want to delete, and then click **Delete**.</span></span>  
  
-   <span data-ttu-id="e04e5-135">レポート履歴の制限を低くして、格納されているスナップショット数を減らします。</span><span class="sxs-lookup"><span data-stu-id="e04e5-135">Lower the report history limit to reduce the number of snapshots that are stored.</span></span> <span data-ttu-id="e04e5-136">レポート履歴の制限は、レポート サーバーに対して、または特定のレポートに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-136">The report history limit can be set for the report server or for specific reports.</span></span> <span data-ttu-id="e04e5-137">制限値を下げた場合、最も古いスナップショットが履歴から削除されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-137">When the limit is lowered, the oldest snapshots are deleted from history.</span></span>  
  
 <span data-ttu-id="e04e5-138">レポート サーバーに格納されているすべてのレポート履歴を、一括操作で削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="e04e5-138">You cannot delete all report history stored on a report server in a bulk operation.</span></span>  
  
 <span data-ttu-id="e04e5-139">また、レポートを削除するとレポート履歴も削除されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-139">Report history is also deleted when you delete a report.</span></span> <span data-ttu-id="e04e5-140">たとえば、月間の売上レポートを新しい売上レポートに置き換えるために削除する場合、そのレポートに関連付けられたすべてのレポート履歴も削除されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-140">For example, if you delete a monthly sales report because you are replacing it with a newer version, all report history that is associated with the report is also deleted.</span></span> <span data-ttu-id="e04e5-141">ただし、レポートを移動する場合、すべてのレポート履歴がそのレポートと共に移動されます。</span><span class="sxs-lookup"><span data-stu-id="e04e5-141">However, if you move a report, all report history moves with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e04e5-142">参照</span><span class="sxs-lookup"><span data-stu-id="e04e5-142">See Also</span></span>  
 <span data-ttu-id="e04e5-143">[レポート履歴の作成 (Reporting Services の SharePoint 統合モード)](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e04e5-143">[Create Report History &#40;Reporting Services in SharePoint Integrated Mode&#41;](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="e04e5-144">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e04e5-144">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e04e5-145">[レポート サーバー コンテンツの管理 &#40;SSRS ネイティブ モード&#41;](report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e04e5-145">[Report Server Content Management &#40;SSRS Native Mode&#41;](report-server-content-management-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e04e5-146">[レポート履歴へのスナップショットの追加 &#40;レポート マネージャー&#41;](add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e04e5-146">[Add a Snapshot to Report History &#40;Report Manager&#41;](add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="e04e5-147">レポート履歴を制限する &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="e04e5-147">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)  
  
  
