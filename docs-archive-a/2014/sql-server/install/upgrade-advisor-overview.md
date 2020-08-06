---
title: Upgrade Advisor の概要 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- SQL Server Upgrade Advisor, components
- tools [Upgrade Advisor]
- Upgrade Advisor [SQL Server], components
- components [Upgrade Advisor]
- Upgrade Advisor Analysis Wizard
- limitations [Upgrade Advisor]
- analyzing system [Upgrade Advisor]
- analyzing system [Upgrade Advisor], about analysis
ms.assetid: f5c56f63-4478-40af-abb9-642f58a0026c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d787f41eba97314986ec77df4cfcff580ae9915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640379"
---
# <a name="upgrade-advisor-overview"></a><span data-ttu-id="3809f-102">アップグレード アドバイザーの概要</span><span class="sxs-lookup"><span data-stu-id="3809f-102">Upgrade Advisor Overview</span></span>
  <span data-ttu-id="3809f-103">アップグレード アドバイザーには、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、および [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のコンポーネントを分析し、分析結果に関する情報が記載されたレポートを表示するための中央コンソールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3809f-103">Upgrade Advisor provides a central console to analyze [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] components, and to view reports that contain information about the results of the analysis.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="3809f-104">アップグレード アドバイザーの機能</span><span class="sxs-lookup"><span data-stu-id="3809f-104">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="3809f-105">アップグレード アドバイザーを実行すると、アップグレード アドバイザーの開始ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-105">When you run Upgrade Advisor, the Upgrade Advisor start page appears.</span></span> <span data-ttu-id="3809f-106">アップグレード アドバイザーの開始ページからは、以下を起動できます。</span><span class="sxs-lookup"><span data-stu-id="3809f-106">The Upgrade Advisor start page is the launching point for the following:</span></span>  
  
-   <span data-ttu-id="3809f-107">アップグレード アドバイザー分析ウィザード</span><span class="sxs-lookup"><span data-stu-id="3809f-107">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="3809f-108">アップグレード アドバイザー レポート ビューアー</span><span class="sxs-lookup"><span data-stu-id="3809f-108">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="3809f-109">アップグレード アドバイザーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="3809f-109">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="3809f-110">アップグレード アドバイザーを初めて使用するときは、アップグレード アドバイザー分析ウィザードを実行してサーバーを分析します。</span><span class="sxs-lookup"><span data-stu-id="3809f-110">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze a server.</span></span> <span data-ttu-id="3809f-111">ウィザードで分析が完了したら、ウィザードの [**レポートの起動**] をクリックするか、アップグレードアドバイザーの開始ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3809f-111">When the wizard completes the analysis, click **Launch Report** from the wizard or return to the Upgrade Advisor start page.</span></span> <span data-ttu-id="3809f-112">そこから、アップグレード アドバイザー レポート ビューアーを実行してレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="3809f-112">From there, run the Upgrade Advisor Report Viewer to view the report.</span></span> <span data-ttu-id="3809f-113">レポートには、既知の問題の解決に役立つ情報へのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3809f-113">The report provides links to information that will help you resolve known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis-wizard"></a><span data-ttu-id="3809f-114">アップグレード アドバイザー分析ウィザード</span><span class="sxs-lookup"><span data-stu-id="3809f-114">Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="3809f-115">分析を実行するには、アップグレードアドバイザーの開始ページで [**アップグレードアドバイザー分析ウィザードの起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3809f-115">To perform an analysis, click **Launch Upgrade Advisor Analysis Wizard** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="3809f-116">アップグレード アドバイザー分析ウィザードによって、分析するコンピューター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント、およびトレース ファイルに関する情報が収集されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-116">The Upgrade Advisor Analysis Wizard gathers information about the computer, instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, and trace files that you want to analyze.</span></span> <span data-ttu-id="3809f-117">すべての情報の収集と確認が完了した後、アップグレード アドバイザー分析ウィザードによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントが分析されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-117">After all the information has been gathered and confirmed, the Upgrade Advisor Analysis Wizard analyzes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3809f-118">アップグレード アドバイザー分析ウィザードを実行するたびに個別のレポートが生成され、選択したコンポーネントに関する既存のレポートは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="3809f-118">Each time you run the Upgrade Advisor Analysis Wizard, a separate report is generated, and existing reports for the selected components are not overwritten.</span></span> <span data-ttu-id="3809f-119">ただし、レポート ビューアーで表示されるのは、最近 5 件のレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="3809f-119">However, the report viewer displays only the five latest reports.</span></span>  
  
 <span data-ttu-id="3809f-120">アップグレード アドバイザー分析ウィザードによる分析が完了すると、分析対象として選択したコンポーネントごとに XML ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-120">When the Upgrade Advisor Analysis Wizard finishes its analysis, it creates an XML file for each component that you have included in the analysis.</span></span> <span data-ttu-id="3809f-121">これらの XML ファイルには、各コンポーネントの検出されたアイテムと問題が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3809f-121">The XML files contain the items and issues discovered in each component.</span></span>  
  
### <a name="what-upgrade-advisor-analyzes"></a><span data-ttu-id="3809f-122">アップグレード アドバイザーの分析対象</span><span class="sxs-lookup"><span data-stu-id="3809f-122">What Upgrade Advisor Analyzes</span></span>  
 <span data-ttu-id="3809f-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントごとに、アップグレード アドバイザーのコンテキスト内で専用のアナライザーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-123">A dedicated analyzer runs in the context of Upgrade Advisor for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span> <span data-ttu-id="3809f-124">各アナライザーは、コンポーネントに関する XML レポートを出力します。</span><span class="sxs-lookup"><span data-stu-id="3809f-124">The output of each analyzer is an XML report for that component.</span></span>  
  
 <span data-ttu-id="3809f-125">アップグレード アドバイザーでは、次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントが照会されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-125">Upgrade Advisor queries the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="3809f-126">レプリケーション、[!INCLUDE[ssDE](../../includes/ssde-md.md)] エージェント、フルテキスト検索、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を含むデータベース サーバー ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とも呼ばれます)</span><span class="sxs-lookup"><span data-stu-id="3809f-126">Database Server (also referred to as the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online), which includes Replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Full-Text Search, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="3809f-127">分析時に、各アナライザーによってログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-127">During analysis, each analyzer creates a log file.</span></span> <span data-ttu-id="3809f-128">ログ ファイルを使用して、分析のトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3809f-128">You can use these log files to troubleshoot the analysis.</span></span> <span data-ttu-id="3809f-129">たとえば、アップグレード アドバイザーの実行速度が遅い場合、ログ ファイルを表示して遅延の原因を突き止めることができます。</span><span class="sxs-lookup"><span data-stu-id="3809f-129">For example, if Upgrade Advisor is running slowly, you can view the log files to determine the cause of the delay.</span></span>  
  
### <a name="upgrade-advisor-limitations"></a><span data-ttu-id="3809f-130">アップグレード アドバイザーの制限事項</span><span class="sxs-lookup"><span data-stu-id="3809f-130">Upgrade Advisor Limitations</span></span>  
 <span data-ttu-id="3809f-131">アップグレード アドバイザーではアップグレードに影響するすべての問題を検出することはできません。</span><span class="sxs-lookup"><span data-stu-id="3809f-131">Upgrade Advisor cannot detect every issue that might affect an upgrade.</span></span> <span data-ttu-id="3809f-132">たとえば、エンド ユーザーのデスクトップで実行するクライアント アプリケーションに SQL コードを埋め込んだ場合は、アップグレード アドバイザーでそのアプリケーションを分析できません。</span><span class="sxs-lookup"><span data-stu-id="3809f-132">For example, if you have embedded SQL code in a client application that runs on end-user desktops, it will not be possible for Upgrade Advisor to analyze the applications.</span></span> <span data-ttu-id="3809f-133">このようなアイテムに対しては、問題を検討し、インストールに必要な情報をアップグレード、移行、または修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3809f-133">For these items, you still must consider the issues and upgrade, migrate, or modify the information as required in your installation.</span></span>  
  
 <span data-ttu-id="3809f-134">アップグレード アドバイザーで、暗号化されたストアド プロシージャ、拡張ストアド プロシージャのコード、および [!INCLUDE[tsql](../../includes/tsql-md.md)] 以外の言語によるソース コードの分析は行われません。</span><span class="sxs-lookup"><span data-stu-id="3809f-134">Upgrade Advisor does not analyze encrypted stored procedures, code in extended stored procedures, and source code in languages other than [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="upgrade-advisor-report-viewer"></a><span data-ttu-id="3809f-135">アップグレード アドバイザー レポート ビューアー</span><span class="sxs-lookup"><span data-stu-id="3809f-135">Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="3809f-136">アップグレードアドバイザーレポートを表示するには、アップグレードアドバイザーの開始ページで [**アップグレードアドバイザーレポートビューアーの起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3809f-136">To view an Upgrade Advisor report, click **Launch Upgrade Advisor Report Viewer** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="3809f-137">アップグレード アドバイザー レポート ビューアーが起動し、既定ディレクトリのレポートが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3809f-137">When the Upgrade Advisor Report Viewer starts, the reports in the default directory are loaded.</span></span> <span data-ttu-id="3809f-138">アップグレードアドバイザーのレポートビューアーで既定のディレクトリにレポートが検出されない場合、レポートは表示されません。</span><span class="sxs-lookup"><span data-stu-id="3809f-138">Reports are not displayed if the Upgrade Advisor Report Viewer does not find any reports in the default directory.</span></span> <span data-ttu-id="3809f-139">既定ディレクトリにレポートがない場合は、アップグレード アドバイザー分析ウィザードを実行してレポートを作成するか、別のサーバーまたはサブディレクトリから既存のレポートを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3809f-139">If there are no reports in the default directory, you can either run the Upgrade Advisor Analysis Wizard to create a report or load an existing report from another server or from a subdirectory.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="3809f-140">アップグレード アドバイザーで、既存のレポートは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="3809f-140">Upgrade Advisor does not overwrite existing reports.</span></span> <span data-ttu-id="3809f-141">ただし、レポート ビューアーで表示されるのは、最近 5 件のレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="3809f-141">However, the report viewer displays only the five latest reports.</span></span> <span data-ttu-id="3809f-142">以前のレポートを表示するには、[**レポート**] ボックスの一覧からレポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="3809f-142">To view an earlier report, select the report from the **Report** drop-down list box.</span></span> <span data-ttu-id="3809f-143">タイムスタンプにより、レポートが生成された日時が示されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-143">The timestamp indicates the date and time the report was generated.</span></span>  
  
 <span data-ttu-id="3809f-144">XML ファイルがアップグレード アドバイザー分析ウィザードからアップグレード アドバイザー レポート ビューアーに読み込まれると、各コンポーネントのレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-144">When XML files from the Upgrade Advisor Analysis Wizard are loaded into the Upgrade Advisor Report Viewer, a report for each component is displayed.</span></span> <span data-ttu-id="3809f-145">レポートには、対処が必要な既知の問題が検出できるできないに限らず、すべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="3809f-145">The report contains all the known issues, both detectable and undetectable, that you need to address.</span></span> <span data-ttu-id="3809f-146">各問題には、重要度を示すアイコン、問題の修正が必要な時期を示すラベル、および簡単な説明が付けられています。</span><span class="sxs-lookup"><span data-stu-id="3809f-146">For each issue there is an icon indicating importance, a label informing you when the issue must be fixed, and a short description.</span></span> <span data-ttu-id="3809f-147">問題を展開すると、より詳しい説明、問題の詳細へのリンク、およびヘルプ ファイルへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3809f-147">When you expand an issue, you will see a longer description, a link to issue details, and a link to the Help file.</span></span> <span data-ttu-id="3809f-148">各問題の情報は、問題を修正するために十分な情報を提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3809f-148">The information for each issue is designed to provide enough information for you to fix the issue.</span></span>  
  
 <span data-ttu-id="3809f-149">ほとんどのコンポーネントには、検出できない問題があります。</span><span class="sxs-lookup"><span data-stu-id="3809f-149">Most components have issues that cannot be detected.</span></span> <span data-ttu-id="3809f-150">これらの問題を表示するには、コンポーネントの [**その他のアップグレードの問題**] 項目を展開し、リンクをクリックして、ドキュメントの問題に関する追加情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="3809f-150">To view these issues, expand the **Other Upgrade Issues** item for the component, and then click the link to view additional information about the issues in the documentation.</span></span> <span data-ttu-id="3809f-151">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の下位互換性の問題の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3809f-151">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backward compatibility issues, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3809f-152">参照</span><span class="sxs-lookup"><span data-stu-id="3809f-152">See Also</span></span>  
 [<span data-ttu-id="3809f-153">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="3809f-153">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
