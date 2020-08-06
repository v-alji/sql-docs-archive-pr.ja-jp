---
title: アップグレードアドバイザーレポートを表示する方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e6df35b869186a601458889c348153093ccbce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644796"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a><span data-ttu-id="0fbb5-102">アップグレード アドバイザーのレポートを表示する方法</span><span class="sxs-lookup"><span data-stu-id="0fbb5-102">How to: View an Upgrade Advisor Report</span></span>
  <span data-ttu-id="0fbb5-103">アップグレード アドバイザーでは、分析対象として選択したコンポーネントごとにレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-103">Upgrade Advisor creates reports for each component that you select to analyze.</span></span> <span data-ttu-id="0fbb5-104">このトピックでは、アップグレード アドバイザーの開始ページからアップグレード アドバイザーのレポートを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-104">This topic describes how to view an Upgrade Advisor report from the Upgrade Advisor start page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0fbb5-105">レポート ビューアーは、標準のファイル名に基づいてファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-105">The report viewer loads files based on standard file names.</span></span> <span data-ttu-id="0fbb5-106">ファイル名が変更されると、そのファイルは読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-106">If the files have been renamed, the report viewer will not load them.</span></span>  
  
### <a name="to-view-a-report"></a><span data-ttu-id="0fbb5-107">レポートを表示するには</span><span class="sxs-lookup"><span data-stu-id="0fbb5-107">To view a report</span></span>  
  
1.  <span data-ttu-id="0fbb5-108">[**スタート**]、[**すべてのプログラム**]、[]、[ **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] アップグレードアドバイザー\*\*] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-108">Click **Start**, click **All Programs**, click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
2.  <span data-ttu-id="0fbb5-109">アップグレードアドバイザーの開始ページで、[**アップグレードアドバイザーレポートビューアーの起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
3.  <span data-ttu-id="0fbb5-110">コンピューターの既定の場所にあるレポートを選択するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-110">To select a report in the default location on your computer:</span></span>  
  
    1.  <span data-ttu-id="0fbb5-111">[**サーバー** ] ボックスの一覧で、サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-111">In the **Server** list, select a server.</span></span>  
  
    2.  <span data-ttu-id="0fbb5-112">[**インスタンス] また**は [コンポーネント] の一覧で、コンポーネントまたはコンポーネント/インスタンスの組み合わせを選択します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-112">In the **Instance or component** list, select a component or component/instance combination.</span></span>  
  
     <span data-ttu-id="0fbb5-113">別の場所でレポートを選択するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-113">To select a report at another location:</span></span>  
  
    1.  <span data-ttu-id="0fbb5-114">[**レポートを開く**] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-114">Click the **Open Report** link.</span></span>  
  
    2.  <span data-ttu-id="0fbb5-115">レポートの場所を参照し、XML ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-115">Browse to the report location and then double-click the XML file.</span></span>  
  
     <span data-ttu-id="0fbb5-116">アップグレード アドバイザーでは、以前に行った分析の履歴として最大 5 件のレポートが保持されます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-116">Upgrade Advisor stores up to five reports from previous analysis as history.</span></span> <span data-ttu-id="0fbb5-117">これらのレポートを表示するには、[**レポート**] ドロップダウンリストボックスをクリックし、レポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-117">To view these reports, click the **Report** drop-down list box, and select a report.</span></span> <span data-ttu-id="0fbb5-118">レポートは、生成日時を示すタイムスタンプ順に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-118">The reports are listed by the timestamp from when they were generated.</span></span>  
  
     <span data-ttu-id="0fbb5-119">レポートには、検出されたすべての問題に対して次の詳細が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-119">The report contains the following details for all detected issues:</span></span>  
  
    -   <span data-ttu-id="0fbb5-120">[**重要度**]: 問題を解決するための重要度を示します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-120">**Importance**, which indicates how important it is to fix the issue.</span></span>  
  
    -   <span data-ttu-id="0fbb5-121">**修正する**場合は、アプリケーションまたはデータを移行する前または後に、またはいつでもアップグレードする前または後に、問題を修正する必要があるかどうかを示します [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-121">**When to fix**, which indicates if you should (or must) fix the issue before or after upgrading to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], before or after migrating the application or data, or anytime.</span></span>  
  
    -   <span data-ttu-id="0fbb5-122">問題の簡潔な説明。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-122">A brief description of the issue.</span></span>  
  
4.  <span data-ttu-id="0fbb5-123">レポートに含まれている項目が 20 項目を超える場合、レポートの上部または下部にある緑色の次へ進む矢印をクリックし、次の項目セットを表示します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-123">If the report contains more than 20 items, click the green forward arrow at the top or bottom of the report to view the next set of items.</span></span> <span data-ttu-id="0fbb5-124">前の 20 項目を表示するには、緑色の "戻る" ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-124">Click the green back button to view the previous 20 items.</span></span>  
  
5.  <span data-ttu-id="0fbb5-125">レポートを並べ替えるには、列見出しをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-125">To sort the report, click a column heading.</span></span>  
  
6.  <span data-ttu-id="0fbb5-126">特定の項目の詳細を表示するには、その項目をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-126">To view details for a specific item, click the item.</span></span> <span data-ttu-id="0fbb5-127">問題の説明が追加のオプションと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-127">A description of the issue appears, along with additional options:</span></span>  
  
    -   <span data-ttu-id="0fbb5-128">この問題が検出されたオブジェクトを表示するには、[**影響を受けるオブジェクトの表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-128">To view the objects where this issue was found, click **Show affected objects**.</span></span>  
  
    -   <span data-ttu-id="0fbb5-129">問題のヘルプを表示するには、[**この問題とその解決方法について詳しく**教えてください] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-129">To view help for the issue, click **Tell me more about this issue and how to resolve it**.</span></span>  
  
    -   <span data-ttu-id="0fbb5-130">問題を解決済みとしてマークするには、レポートを再度表示したときに問題が表示されないようにするには、[**この問題は解決されまし**た] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-130">To mark the issue as resolved, which hides the issue when you view the report again, select **This issue has been resolved**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fbb5-131">レポートには、検出不可能な問題に対する項目が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-131">The report may contain an item for undetectable issues.</span></span> <span data-ttu-id="0fbb5-132">これらは、検出できない問題か、または誤って検出された結果が大量に生成される問題です。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-132">These are issues that cannot be detected or that would generate too many false-positive results.</span></span> <span data-ttu-id="0fbb5-133">[**この問題の詳細**を確認してください] リンクをクリックすると、コンポーネントの検出できない問題の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fbb5-133">Click the **Tell me more about this issue and how to resolve it** link to see a list of undetectable issues for the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fbb5-134">参照</span><span class="sxs-lookup"><span data-stu-id="0fbb5-134">See Also</span></span>  
 <span data-ttu-id="0fbb5-135">[レポートをエクスポートする方法](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="0fbb5-135">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="0fbb5-136">[アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0fbb5-136">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="0fbb5-137">[アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0fbb5-137">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="0fbb5-138">[アップグレードアドバイザーの操作方法に関するトピック](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="0fbb5-138">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="0fbb5-139">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="0fbb5-139">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
