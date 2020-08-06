---
title: レポートの使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f52afcfdaa7de33d83d64a049f9a350f0463b4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742757"
---
# <a name="using-reports"></a><span data-ttu-id="ecc77-102">レポートの使用</span><span class="sxs-lookup"><span data-stu-id="ecc77-102">Using Reports</span></span>
  <span data-ttu-id="ecc77-103">アップグレード アドバイザー分析ウィザードによってサーバー上で分析されたコンポーネントごとまたはインスタンスごとに、個別のレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-103">A separate report is generated for each component, and, where necessary, each instance, that the Upgrade Advisor Analysis Wizard analyzes on a server.</span></span> <span data-ttu-id="ecc77-104">レポートでは、アップグレードに影響する既知の問題の詳細を参照できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-104">The report provides details about known issues that affect an upgrade.</span></span> <span data-ttu-id="ecc77-105">また、特定された問題に対処するための情報と推奨される操作へのリンクも示します。</span><span class="sxs-lookup"><span data-stu-id="ecc77-105">It also provides links to information and suggested actions for addressing the identified issues.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecc77-106">アップグレードアドバイザーのレポートビューアーで、既定のレポートディレクトリにレポートが見つからない場合、[**レポートを開く**] リンクを使用して別のディレクトリからレポートを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-106">If the Upgrade Advisor Report Viewer does not find any reports in the default reports directory, you can load a report from a different directory by using the **Open Report** link.</span></span>  
  
## <a name="viewing-reports"></a><span data-ttu-id="ecc77-107">レポートの表示</span><span class="sxs-lookup"><span data-stu-id="ecc77-107">Viewing Reports</span></span>  
 <span data-ttu-id="ecc77-108">アップグレード アドバイザー レポート ビューアーを使用して、アップグレード アドバイザー レポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecc77-108">You use the Upgrade Advisor Report Viewer to view Upgrade Advisor reports.</span></span> <span data-ttu-id="ecc77-109">レポートを表示するには、アップグレードアドバイザーの開始ページで、[**アップグレードアドバイザーレポートビューアーの起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecc77-109">To view reports, on the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
 <span data-ttu-id="ecc77-110">サーバーのレポートを読み込んだ後、アップグレード問題を確認するコンポーネントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-110">After you load a report for a server, you can select a component for which you want to see upgrade issues.</span></span> <span data-ttu-id="ecc77-111">[**フィルター** ] ボックスからフィルターを適用すると、次のことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-111">You can apply a filter from the **Filter By** box to see the following:</span></span>  
  
-   <span data-ttu-id="ecc77-112">すべての問題</span><span class="sxs-lookup"><span data-stu-id="ecc77-112">All issues</span></span>  
  
-   <span data-ttu-id="ecc77-113">アップグレードに関するすべての問題</span><span class="sxs-lookup"><span data-stu-id="ecc77-113">All upgrade issues</span></span>  
  
-   <span data-ttu-id="ecc77-114">アップグレード前の問題</span><span class="sxs-lookup"><span data-stu-id="ecc77-114">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="ecc77-115">移行に関するすべての問題</span><span class="sxs-lookup"><span data-stu-id="ecc77-115">All migration issues</span></span>  
  
-   <span data-ttu-id="ecc77-116">解決した問題</span><span class="sxs-lookup"><span data-stu-id="ecc77-116">Resolved issues</span></span>  
  
-   <span data-ttu-id="ecc77-117">未解決の問題</span><span class="sxs-lookup"><span data-stu-id="ecc77-117">Unresolved issues</span></span>  
  
 <span data-ttu-id="ecc77-118">レポートに20件を超える問題がある場合は、問題の一覧の上部または下部にある **[次の 20** ] または [**前の 20** ] をクリックして、問題の次のグループまたは前のグループに移動できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-118">If your report has more than 20 issues, you can move to the next or previous group of issues by clicking **Next 20** or **Previous 20** at the top or bottom of the issues list.</span></span>  
  
 <span data-ttu-id="ecc77-119">[**レポート**] ボックスの一覧からレポートを選択すると、最大5つのレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-119">You can view up to five saved reports by selecting the reports from the **Report** drop-down list box.</span></span> <span data-ttu-id="ecc77-120">レポートは、生成日時を示すタイムスタンプ順に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-120">The reports are listed by the timestamp from when they were generated.</span></span>  
  
## <a name="report-format"></a><span data-ttu-id="ecc77-121">レポート形式</span><span class="sxs-lookup"><span data-stu-id="ecc77-121">Report Format</span></span>  
 <span data-ttu-id="ecc77-122">レポート ビューアーには、レポート内の問題が 3 列で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-122">The report viewer displays report issues in three columns.</span></span> <span data-ttu-id="ecc77-123">それぞれの問題を折りたたむと、説明が非表示になり、重要な情報だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-123">Each issue is collapsible so that you can hide the description and view only the key information.</span></span>  
  
 <span data-ttu-id="ecc77-124">最初の列は、[**重要度**列です。</span><span class="sxs-lookup"><span data-stu-id="ecc77-124">The first column is the **Importance** column.</span></span> <span data-ttu-id="ecc77-125">アイコンは各問題の重要度を示します。移行がブロックされる問題や重要な問題の場合は、赤い円の中に X マークが表示されます。警告および情報を表す場合は、黄色い三角形の中に感嘆符が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-125">Icons indicate the importance for each issue by displaying either a red circle with an X for blocking or important issues or a yellow triangle with an exclamation mark for Warning and Information issues.</span></span> <span data-ttu-id="ecc77-126">2番目の列 (**修正する場合**) は、問題を解決する必要がある時期を示します。</span><span class="sxs-lookup"><span data-stu-id="ecc77-126">The second column, **When to fix**, indicates when you must resolve the issue.</span></span> <span data-ttu-id="ecc77-127">レポートは、[**重要度**] 列または [**修正するタイミング**] 列で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-127">You can sort the report on either the **Importance** or **When to fix** column.</span></span> <span data-ttu-id="ecc77-128">3番目の [**説明**] 列には、問題のタイトルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-128">The third column, **Description**, lists the title of the issue.</span></span>  
  
 <span data-ttu-id="ecc77-129">問題を展開して、追加情報、問題の解決に関する詳細情報のリンク、および問題の詳細を示すリンクを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-129">You can expand an issue to display additional information, a link to detailed information about resolving the issue, and a link to show issue details.</span></span> <span data-ttu-id="ecc77-130">問題の詳細情報を入手できるリンクをクリックすると、問題に関する情報および問題を解決するための指示を含むヘルプ トピックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-130">When you click the link to get detailed information for the issue, a Help topic with information about the issue and instructions for addressing the issue is displayed.</span></span> <span data-ttu-id="ecc77-131">問題を修正した後、またはアクション項目を管理するには、[**この問題は解決され**ました] チェックボックスをオンにして、問題を完了としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-131">After you have fixed an issue, or to manage your action items, you can mark issues as complete by selecting the **This issue has been resolved** check box.</span></span> <span data-ttu-id="ecc77-132">解決済みの問題をアップグレードの問題の一覧から削除する場合は、[最新の状態に**更新**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecc77-132">If you want to remove the resolved issues from the list of upgrade issues, click **Refresh**.</span></span> <span data-ttu-id="ecc77-133">同じコンポーネントに対してアップグレードアドバイザー分析ウィザードを実行するか、[**フィルター条件**] オプションから**解決済みの問題**フィルターを適用するまで、この問題は再び表示されません。</span><span class="sxs-lookup"><span data-stu-id="ecc77-133">The issue is not displayed again until you either run the Upgrade Advisor Analysis Wizard against the same component or apply the **Resolved Issues** filter from the **Filter By** option.</span></span>  
  
## <a name="report-files"></a><span data-ttu-id="ecc77-134">レポート ファイル</span><span class="sxs-lookup"><span data-stu-id="ecc77-134">Report Files</span></span>  
 <span data-ttu-id="ecc77-135">Upgrade Advisor 分析ウィザードでは、My Documents upgrade Advisor\110\Reports ディレクトリにレポートが作成され、 \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分析するサーバーごとにサブディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-135">The Upgrade Advisor Analysis Wizard creates reports in the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports directory and creates a subdirectory for each server that you analyze.</span></span> <span data-ttu-id="ecc77-136">レポート ファイルは、特定の名前付け規則に従った XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="ecc77-136">The report files are XML files that follow a specific naming convention.</span></span> <span data-ttu-id="ecc77-137">アップグレード アドバイザー レポート ビューアーを起動すると、既定のディレクトリにあるレポート ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-137">When you launch the Upgrade Advisor Report Viewer, the report files in the default directory are displayed.</span></span> <span data-ttu-id="ecc77-138">レポート ファイルをこのフォルダーにコピーする場合、名前付け規則に従う必要があります。名前付け規則に従わないと、レポート ビューアーでレポート ファイルが自動的に表示されません。</span><span class="sxs-lookup"><span data-stu-id="ecc77-138">If you copy report files into this folder, they must adhere to the naming convention or the report viewer will not display them automatically.</span></span>  
  
 <span data-ttu-id="ecc77-139">他のユーザーと情報を共有するには、XML レポートを他のユーザーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-139">If you want to share the information with other people, you can send them the XML report.</span></span> <span data-ttu-id="ecc77-140">また、レポートをコンマ区切り形式のファイルにエクスポートすれば、スプレッドシート、テキスト ファイル、電子メール メッセージなどを別のアプリケーションで作成できます。</span><span class="sxs-lookup"><span data-stu-id="ecc77-140">Or, if you want to use another application, you can export the report into a comma-separated value file that you can use to create a spreadsheet, text file, or e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc77-141">参照</span><span class="sxs-lookup"><span data-stu-id="ecc77-141">See Also</span></span>  
 <span data-ttu-id="ecc77-142">[アップグレードアドバイザーレポートを表示する方法](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span><span class="sxs-lookup"><span data-stu-id="ecc77-142">[How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span></span>  
 <span data-ttu-id="ecc77-143">[レポートをエクスポートする方法](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ecc77-143">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="ecc77-144">[方法: レポートをフィルター処理する](../../../2014/sql-server/install/how-to-filter-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ecc77-144">[How to: Filter Reports](../../../2014/sql-server/install/how-to-filter-reports.md) </span></span>  
 <span data-ttu-id="ecc77-145">[アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ecc77-145">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ecc77-146">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="ecc77-146">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
