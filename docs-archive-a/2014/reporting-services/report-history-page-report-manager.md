---
title: '[レポート履歴] ページ (レポートマネージャー) |Microsoft Docs'
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 4070be8c1d6b0633131e96c665d4551c1b676a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640607"
---
# <a name="report-history-page-report-manager"></a><span data-ttu-id="2ce17-102">[レポート履歴] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="2ce17-102">Report History Page (Report Manager)</span></span>

<span data-ttu-id="2ce17-103">[レポート履歴] ページには、一定期間に生成および保存したレポート スナップショットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-103">Use the Report History page to view report snapshots that are generated and stored over time.</span></span> <span data-ttu-id="2ce17-104">レポート サーバーで設定されているオプションによっては、新しいスナップショットのみがレポート ヒストリに保存されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-104">Depending on options that are set on the report server, report history may contain only the more recent snapshots.</span></span>  
  

<span data-ttu-id="2ce17-105">レポート ヒストリは、常に元のレポートのコンテキスト内で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-105">Report history is always viewed within the context of the report from which it originates.</span></span> <span data-ttu-id="2ce17-106">すべてのレポートのヒストリをレポート サーバーの 1 か所に表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="2ce17-106">You cannot view the history of all reports on a report server in one place.</span></span>  
  
<span data-ttu-id="2ce17-107">レポート ヒストリを生成するには、レポートが自動的に実行されるようにする必要があります (つまり、保存されている資格情報を使用する必要があります。また、パラメーター化されたレポートには、すべてのパラメーターのパラメーター値を含める必要があります)。</span><span class="sxs-lookup"><span data-stu-id="2ce17-107">To generate report history, the report must be able to run unattended (that is, it must use stored credentials; parameterized reports must contain default parameter values for all parameters).</span></span> <span data-ttu-id="2ce17-108">レポート ヒストリの生成は、手動またはスケジュールに設定した操作によって行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-108">Report history can be generated manually or as a scheduled operation.</span></span> <span data-ttu-id="2ce17-109">レポート ヒストリの作成方法は、レポートのヒストリ プロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="2ce17-109">History properties on the report determine the ways in which report history can be created.</span></span>  
  
<span data-ttu-id="2ce17-110">レポート ヒストリ スナップショットをクリックすると、そのスナップショットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-110">You can click a report history snapshot to view it.</span></span> <span data-ttu-id="2ce17-111">レポート ヒストリに表示されるスナップショットは、作成日時だけで識別されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-111">Snapshots that appear in report history are distinguished only by the date and time at which they were created.</span></span> <span data-ttu-id="2ce17-112">スナップショットがスケジュールの設定を受けて生成されたのか、手動で生成されたのかを識別する表示はありません。</span><span class="sxs-lookup"><span data-stu-id="2ce17-112">There is no visual indication to distinguish whether a snapshot was generated in response to a schedule or a manual operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ce17-113">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2ce17-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2ce17-114">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ce17-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="2ce17-115">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2ce17-115">Navigation</span></span>  
 <span data-ttu-id="2ce17-116">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2ce17-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-report-history-page"></a><span data-ttu-id="2ce17-117">[レポート履歴] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="2ce17-117">To open the Report History page</span></span>  
  
1.  <span data-ttu-id="2ce17-118">レポート マネージャーを開き、レポート スナップショットを表示するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="2ce17-118">Open Report Manager, and locate the report for which you want to view report snapshots.</span></span>  
  
2.  <span data-ttu-id="2ce17-119">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce17-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="2ce17-120">ドロップダウン メニューの **[レポート履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce17-120">In the drop-down menu, click **View Report History**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2ce17-121">Options</span><span class="sxs-lookup"><span data-stu-id="2ce17-121">Options</span></span>  
 <span data-ttu-id="2ce17-122">**削除**</span><span class="sxs-lookup"><span data-stu-id="2ce17-122">**Delete**</span></span>  
 <span data-ttu-id="2ce17-123">1 つ以上のスナップショットを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce17-123">Click to delete one or more snapshots.</span></span> <span data-ttu-id="2ce17-124">削除するスナップショットの横のチェック ボックスをオンにしてから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce17-124">Before clicking **Delete**, select the check box next to the snapshot that you want to delete.</span></span>  
  
 <span data-ttu-id="2ce17-125">**新しいスナップショット**</span><span class="sxs-lookup"><span data-stu-id="2ce17-125">**New Snapshot**</span></span>  
 <span data-ttu-id="2ce17-126">レポート履歴にスナップショットを追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce17-126">Click to add a snapshot to report history.</span></span> <span data-ttu-id="2ce17-127">レポートの [レポート履歴] プロパティ ページの **[レポート履歴の手動作成を許可する]** をオンにしたときに、このボタンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="2ce17-127">This button is available when you choose the option **Allow history to be created manually** on the History properties page of the report.</span></span>  
  
 <span data-ttu-id="2ce17-128">**[最終実行]**</span><span class="sxs-lookup"><span data-stu-id="2ce17-128">**Last Run**</span></span>  
 <span data-ttu-id="2ce17-129">スナップショットが作成された日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-129">Displays the date and time at which the snapshot was created.</span></span> <span data-ttu-id="2ce17-130">説明をクリックすると、特定のスナップショットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-130">Click a description to view a particular snapshot.</span></span>  
  
 <span data-ttu-id="2ce17-131">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="2ce17-131">**Size**</span></span>  
 <span data-ttu-id="2ce17-132">レポートのレポート定義とデータを合わせたサイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-132">Displays the size of the report definition plus the data in the report.</span></span> <span data-ttu-id="2ce17-133">この値は、レポート定義とデータがレポート サーバー データベースの領域をどのくらい使用しているのかを示します。</span><span class="sxs-lookup"><span data-stu-id="2ce17-133">This value indicates how much space in the report server database is used by the report definition and data.</span></span> <span data-ttu-id="2ce17-134">書式を含めた表示レポートの実際のサイズは、この値より大きくなります。</span><span class="sxs-lookup"><span data-stu-id="2ce17-134">The size of the rendered report, which includes formatting, is actually larger.</span></span> <span data-ttu-id="2ce17-135">現在のレポートのレポート履歴に保存されているすべてのスナップショットの合計サイズは、かっこ内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce17-135">The total size, indicated in parentheses, sums the sizes of all snapshots in the report history for the current report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce17-136">参照</span><span class="sxs-lookup"><span data-stu-id="2ce17-136">See Also</span></span>  
 <span data-ttu-id="2ce17-137">[レポート履歴 &#40;レポートマネージャーの表示または削除&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2ce17-137">[View or Delete Report History &#40;Report Manager&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="2ce17-138">[レポート履歴へのスナップショットの追加 &#40;レポートマネージャー&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2ce17-138">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="2ce17-139">[[全般] プロパティページ、レポート &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2ce17-139">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="2ce17-140">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="2ce17-140">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="2ce17-141">[[スナップショットオプション] プロパティページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="2ce17-141">[Snapshot Options Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)</span></span>