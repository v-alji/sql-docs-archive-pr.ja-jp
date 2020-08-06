---
title: '[サイトの設定] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75805a4e30293195b23cd5b75f1de3a01a1e76d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715074"
---
# <a name="site-settings-page-report-manager"></a><span data-ttu-id="7f861-102">[サイトの設定] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="7f861-102">Site Settings Page (Report Manager)</span></span>
  <span data-ttu-id="7f861-103">[サイトの設定] ページでは、アプリケーションのタイトルの変更、レポート履歴の制限やレポート処理タイムアウトに関するサーバー全体の既定値の設定、システム レベルのロールの割り当ての管理、および共有スケジュールの管理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="7f861-103">Use the Site Settings page to change the application title, set server-wide defaults for report history limits and report processing timeout values, manage system-level role assignments, and manage shared schedules.</span></span> <span data-ttu-id="7f861-104">このページを表示するには、コンテンツ マネージャーとシステム管理者の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7f861-104">You must have Content Manager and System Administrator permissions to view this page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f861-105">レポート履歴、レポート実行、および共有スケジュール機能は、すべてのエディションの SQL Server で使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7f861-105">The following features are not available in every edition of SQL Server: report history, report execution, and shared schedules.</span></span> <span data-ttu-id="7f861-106">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f861-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="7f861-107">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="7f861-107">Navigation</span></span>  
 <span data-ttu-id="7f861-108">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7f861-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-site-settings-page"></a><span data-ttu-id="7f861-109">[サイトの設定] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="7f861-109">To open the Site Settings page</span></span>  
  
1.  <span data-ttu-id="7f861-110">レポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7f861-110">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="7f861-111">ページの上部にある **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7f861-111">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="7f861-112">この操作により、サイトの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="7f861-112">This opens the General Properties page of the site.</span></span>  
  
     <span data-ttu-id="7f861-113">**注:** メニューに [**サイトの設定**] オプションが表示されない場合は、必要なアクセス許可がありません。詳細については、「[ローカル管理用のネイティブモードのレポートサーバーの構成 &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」の「サイトの設定」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f861-113">**Note:** If you do not see the **Site Settings** option in the menu, you do not have the required permissions, For more information see the "site settings" section of [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f861-114">Options</span><span class="sxs-lookup"><span data-stu-id="7f861-114">Options</span></span>  
 <span data-ttu-id="7f861-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="7f861-115">**Name**</span></span>  
 <span data-ttu-id="7f861-116">この [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート マネージャーのインスタンスに使用するタイトルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f861-116">Specify the title to use for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="7f861-117">既定では、タイトルは " [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] " です。</span><span class="sxs-lookup"><span data-stu-id="7f861-117">By default, the title is "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]".</span></span>  
  
 <span data-ttu-id="7f861-118">**[レポート履歴の既定の設定を選択します]**</span><span class="sxs-lookup"><span data-stu-id="7f861-118">**Select the default settings for report history**</span></span>  
 <span data-ttu-id="7f861-119">レポート履歴で保持されるコピー数の既定値を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f861-119">Select a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="7f861-120">既定値には、レポート履歴の制限を規定する初期設定が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7f861-120">The default value provides an initial setting that establishes report history limits.</span></span> <span data-ttu-id="7f861-121">これらの設定は、レポート レベルで異なります。</span><span class="sxs-lookup"><span data-stu-id="7f861-121">You can vary these settings at the report level.</span></span> <span data-ttu-id="7f861-122">詳細については、「[[スナップショット オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f861-122">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="7f861-123">これから指定するレポート履歴の制限を超えてから、既存のレポート履歴を制限した場合、既存のレポート履歴が新しい制限値まで削減されます。</span><span class="sxs-lookup"><span data-stu-id="7f861-123">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="7f861-124">最初に、最も古いレポート スナップショットが削除されます。</span><span class="sxs-lookup"><span data-stu-id="7f861-124">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="7f861-125">レポート履歴が空であるか、制限を超えていない場合は、新しいレポート スナップショットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="7f861-125">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="7f861-126">制限に達すると、新しいレポート スナップショットが追加されたときに最も古いスナップショットが削除されます。</span><span class="sxs-lookup"><span data-stu-id="7f861-126">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
 <span data-ttu-id="7f861-127">**[レポート実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="7f861-127">**Report Execution Timeout**</span></span>  
 <span data-ttu-id="7f861-128">特定の秒数が経過した後、レポート処理をタイムアウトさせるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f861-128">Specify whether report processing times out after a certain number of seconds.</span></span>  
  
 <span data-ttu-id="7f861-129">この値は、レポート サーバーでのレポート処理に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f861-129">This value applies to report processing on a report server.</span></span> <span data-ttu-id="7f861-130">レポートにデータを提供するデータベース サーバーで処理されるデータには影響しません。</span><span class="sxs-lookup"><span data-stu-id="7f861-130">It does not affect data processing on the database server that provides the data for your report.</span></span>  
  
 <span data-ttu-id="7f861-131">レポート処理時間の時計は、レポートを選択したときに開始され、レポートを開くと終了します。</span><span class="sxs-lookup"><span data-stu-id="7f861-131">The report processing timer clock begins when the report is selected and ends when the report opens.</span></span> <span data-ttu-id="7f861-132">この値を設定する際、データ処理とレポート処理の両方を十分に完了できる時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f861-132">When you set this value, specify enough time to complete both data processing and report processing.</span></span>  
  
 <span data-ttu-id="7f861-133">**[カスタムのレポート ビルダーの起動 URL]**</span><span class="sxs-lookup"><span data-stu-id="7f861-133">**Custom Report Builder launch URL**</span></span>  
 <span data-ttu-id="7f861-134">レポート サーバーで既定のレポート ビルダー URL を使用しない場合に、カスタムの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f861-134">Specify a custom URL when the report server does not use the default Report Builder URL.</span></span> <span data-ttu-id="7f861-135">この設定はオプションです。</span><span class="sxs-lookup"><span data-stu-id="7f861-135">This setting is optional.</span></span> <span data-ttu-id="7f861-136">この値が指定されなかった場合は、レポート ビルダーを ClickOnce アプリケーションとして起動する既定の URL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f861-136">If you do not specify a value, the default URL will be used, which launches Report Builder as a ClickOnce application.</span></span> <span data-ttu-id="7f861-137">既定の URL は、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="7f861-137">The default URL is one of the following:</span></span>  
  
 <span data-ttu-id="7f861-138">**ネイティブモードのレポートサーバー:** ネイティブモードのインストールでは、既定の URL は http:///Reportserver/reportbuilder/ReportBuilder_3_0_0_0 の形式になります。 \<*computername*></span><span class="sxs-lookup"><span data-stu-id="7f861-138">**Native mode report server:** In a native mode installation, the default URL will take the form of http://\<*computername*>/reportserver/ReportBuilder/ReportBuilder_3_0_0_0.application.</span></span>  
  
 <span data-ttu-id="7f861-139">SharePoint 統合モード: 既定の URL は、http:// \<*SharePoint_site*> /_vti_bin/reportbuilder/ReportBuilder_3_0_0_0 の形式になります。</span><span class="sxs-lookup"><span data-stu-id="7f861-139">SharePoint integrated mode: The default URL will take the form of http://\<*SharePoint_site*>/_vti_bin/ReportBuilder/ReportBuilder_3_0_0_0.application."</span></span>  
  
 <span data-ttu-id="7f861-140">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="7f861-140">**Apply**</span></span>  
 <span data-ttu-id="7f861-141">レポート サーバーに変更を保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7f861-141">Click to save your changes to the report server.</span></span>  
  
 <span data-ttu-id="7f861-142">**Security**</span><span class="sxs-lookup"><span data-stu-id="7f861-142">**Security**</span></span>  
 <span data-ttu-id="7f861-143">このリンクをクリックすると、[システム ロールの割り当て] ページが開きます。このページでは、ユーザー アカウントおよびグループ アカウントを定義済みのシステム ロールに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7f861-143">Click this link to open the System Role Assignments page, on which you can assign user and group accounts to predefined system roles.</span></span>  
  
 <span data-ttu-id="7f861-144">**スケジュール**</span><span class="sxs-lookup"><span data-stu-id="7f861-144">**Schedules**</span></span>  
 <span data-ttu-id="7f861-145">このリンクをクリックすると、[スケジュール] ページが開きます。このページでは、ユーザーがレポートおよびサブスクリプションに対して選択できる共有スケジュールを事前に定義できます。</span><span class="sxs-lookup"><span data-stu-id="7f861-145">Click this link to open the Schedules page, on which you can predefine shared schedules that users can select for their reports and subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f861-146">参照</span><span class="sxs-lookup"><span data-stu-id="7f861-146">See Also</span></span>  
 <span data-ttu-id="7f861-147">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="7f861-147">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="7f861-148">[ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="7f861-148">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="7f861-149">[定義済みロール](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="7f861-149">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="7f861-150">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="7f861-150">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
