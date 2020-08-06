---
title: Reporting Services ツール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43e181e52cd40c961423b4e5f8b60d5528145005
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721027"
---
# <a name="reporting-services-tools"></a><span data-ttu-id="32a0c-102">Reporting Services ツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-102">Reporting Services Tools</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="32a0c-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、管理環境での機能豊富なレポートの開発と使用をサポートするグラフィカル ツールとスクリプト ツールのセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="32a0c-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] contains a set of graphical and scripting tools that support the development and use of rich reports in a managed environment.</span></span> <span data-ttu-id="32a0c-104">このツール セットには、開発ツール、構成と管理ツール、およびレポート表示ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="32a0c-104">The tool set includes development tools, configuration and administration tools, and report viewing tools.</span></span> <span data-ttu-id="32a0c-105">ここでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の各ツール、およびツールへのアクセス方法について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-105">This topic gives a brief overview of each tool in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and how it can be accessed.</span></span>  
  
 <span data-ttu-id="32a0c-106">ツールを簡単に見つける方法については、「[チュートリアル : Reporting Services ツールを検索および開始する方法 (SSRS)](tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-106">To find a tool right away, see [Tutorial: How to Locate and Start Reporting Services Tools &#40;SSRS&#41;](tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md).</span></span>  
  
## <a name="tools-for-report-authoring"></a><span data-ttu-id="32a0c-107">レポートの作成ツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-107">Tools for Report Authoring</span></span>  
 <span data-ttu-id="32a0c-108">次の表に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でのレポートの作成に使用できるツールの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-108">The following table lists the available tools for report authoring in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="32a0c-109">ツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-109">Tool</span></span>|<span data-ttu-id="32a0c-110">説明</span><span class="sxs-lookup"><span data-stu-id="32a0c-110">Description</span></span>|<span data-ttu-id="32a0c-111">アクセス方法</span><span class="sxs-lookup"><span data-stu-id="32a0c-111">How to access</span></span>|  
|----------|-----------------|-------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|<span data-ttu-id="32a0c-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表形式モデルに基づいてレポートを作成し、対話できるようにデザインされた、対話型データの探索およびビジュアル化が可能です。</span><span class="sxs-lookup"><span data-stu-id="32a0c-112">An interactive data exploration and visual presentation experience designed to let you create and interact with reports based on [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular models.</span></span><br /><br /> <span data-ttu-id="32a0c-113">注: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードではが必要です。</span><span class="sxs-lookup"><span data-stu-id="32a0c-113">Note: Requires [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>|<span data-ttu-id="32a0c-114">Silverlight がインストールされているブラウザー</span><span class="sxs-lookup"><span data-stu-id="32a0c-114">Browser with Silverlight.</span></span>|  
|<span data-ttu-id="32a0c-115">レポート デザイナー</span><span class="sxs-lookup"><span data-stu-id="32a0c-115">Report Designer</span></span>|<span data-ttu-id="32a0c-116">レポートをデザインし、ネイティブ モードまたは SharePoint モードのレポート サーバーに配置するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-116">Use this tool to design reports and deploy to a native mode or SharePoint mode report server.</span></span><br /><br /> <span data-ttu-id="32a0c-117">でホストされる [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a0c-117">Hosted in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span></span><br /><br /> <span data-ttu-id="32a0c-118">レポートで使用されるデータを編成するためのレポート データ ペイン</span><span class="sxs-lookup"><span data-stu-id="32a0c-118">Report Data pane to organize data used in your report</span></span><br /><br /> <span data-ttu-id="32a0c-119">対話型のレポート デザインのデザインおよびプレビューに使用するタブ付きビュー</span><span class="sxs-lookup"><span data-stu-id="32a0c-119">Tabbed views for Design and Preview for interactive report design</span></span><br /><br /> <span data-ttu-id="32a0c-120">データ ソースから取得するデータを指定できるクエリ デザイナー、および [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)内のデータ ソースの種類に関連付けられているクエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="32a0c-120">Query designers to help specify which data to retrieve from data sources and that are associated with data source types in the [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)</span></span><br /><br /> <span data-ttu-id="32a0c-121">レポートのコンテンツと外観をカスタマイズする [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 式を作成するための IntelliSense 対応の式エディター</span><span class="sxs-lookup"><span data-stu-id="32a0c-121">Expression editor with IntelliSense to build [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] expressions that customize report content and appearance</span></span><br /><br /> <span data-ttu-id="32a0c-122">カスタム レポート アイテムとカスタム クエリ デザイナーをサポート</span><span class="sxs-lookup"><span data-stu-id="32a0c-122">Supports custom report items and custom query designers</span></span><br /><br /> <br /><br /> <span data-ttu-id="32a0c-123">詳細については、「[SQL Server データ ツールの Reporting Services (SSDT)](reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-123">For more information, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).</span></span>|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|<span data-ttu-id="32a0c-124">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="32a0c-124">Report Builder</span></span>|<span data-ttu-id="32a0c-125">レポートをデザインし、ネイティブ モードまたは SharePoint モードのレポート サーバーに配置するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-125">Use this tool to design reports and deploy to a native mode or SharePoint mode report server.</span></span><br /><br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="32a0c-126">Office と同様の作成環境</span><span class="sxs-lookup"><span data-stu-id="32a0c-126">Office-like authoring environment</span></span><br /><br /> <span data-ttu-id="32a0c-127">レポート アイテムをレポート パーツとして保存する機能</span><span class="sxs-lookup"><span data-stu-id="32a0c-127">Ability to save report items as report parts</span></span><br /><br /> <span data-ttu-id="32a0c-128">マップを作成するウィザード</span><span class="sxs-lookup"><span data-stu-id="32a0c-128">A wizard for creating maps</span></span><br /><br /> <span data-ttu-id="32a0c-129">集計の集計</span><span class="sxs-lookup"><span data-stu-id="32a0c-129">Aggregates of aggregates</span></span><br /><br /> <span data-ttu-id="32a0c-130">式のサポート強化</span><span class="sxs-lookup"><span data-stu-id="32a0c-130">Enhanced support for expressions</span></span><br /><br /> <span data-ttu-id="32a0c-131">選択した組み込みのデータ ソースの種類から取得するデータを指定できるクエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="32a0c-131">Query designers to help specify which data to retrieve from a selection of built-in data sources types</span></span><br /><br /> <br /><br /> <span data-ttu-id="32a0c-132">詳細については、「[レポートビルダー &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-132">For more information, see [Report Builder &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md).</span></span>|<span data-ttu-id="32a0c-133">MSI をダウンロードするか、レポート マネージャーまたは SharePoint から開く</span><span class="sxs-lookup"><span data-stu-id="32a0c-133">Download MSI or open from Report Manager/SharePoint</span></span>|  
  
## <a name="tools-for-report-server-administration"></a><span data-ttu-id="32a0c-134">レポート サーバー管理用のツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-134">Tools for Report Server Administration</span></span>  
 <span data-ttu-id="32a0c-135">のレポートサーバーを管理するためのグラフィカルツールとスクリプトツールのセットが用意されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="32a0c-135">A set of graphical and scripting tools are available for administering the report server in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="32a0c-136">使用するツールは、レポート サーバーの配置モードによって異なります。</span><span class="sxs-lookup"><span data-stu-id="32a0c-136">The tools that you use depend on the deployment mode of your report server.</span></span>  
  
### <a name="native-mode"></a><span data-ttu-id="32a0c-137">ネイティブ モード</span><span class="sxs-lookup"><span data-stu-id="32a0c-137">Native Mode</span></span>  
 <span data-ttu-id="32a0c-138">次の表に、ネイティブ モードで配置されているレポート サーバーの管理に使用できるツールの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-138">The following table lists the available tools for administering the report server that is deployed in native mode.</span></span>  
  
|<span data-ttu-id="32a0c-139">ツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-139">Tool</span></span>|<span data-ttu-id="32a0c-140">説明</span><span class="sxs-lookup"><span data-stu-id="32a0c-140">Description</span></span>|<span data-ttu-id="32a0c-141">アクセス方法</span><span class="sxs-lookup"><span data-stu-id="32a0c-141">How to access</span></span>|  
|----------|-----------------|-------------------|  
|<span data-ttu-id="32a0c-142">Reporting Services 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="32a0c-142">Reporting Services Configuration Manager</span></span>|<span data-ttu-id="32a0c-143">Reporting Services のインストールを構成するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-143">Use this tool to configure a Reporting Services installation.</span></span> <span data-ttu-id="32a0c-144">Reporting Services Configuration Manager は、レポートサーバーのコンテンツの管理、追加機能の有効化、またはサーバーへのアクセス権の付与には役立ちません。</span><span class="sxs-lookup"><span data-stu-id="32a0c-144">Note that the Reporting Services Configuration Manager does not help you manage report server content, enable additional features, or grant access to the server.</span></span> <span data-ttu-id="32a0c-145">実行できるタスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="32a0c-145">Available tasks include:</span></span><br /><br /> <span data-ttu-id="32a0c-146">ローカルとリモートの両方のレポート サーバー インスタンスの構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-146">Configuring both local and remote report server instances</span></span><br /><br /> <span data-ttu-id="32a0c-147">レポート サーバー サービス アカウントの構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-147">Configuring the Report Server service account.</span></span><br /><br /> <span data-ttu-id="32a0c-148">1 つ以上の Web サービス URL の作成および構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-148">Creating and configuring one or more Web service URL.</span></span><br /><br /> <span data-ttu-id="32a0c-149">レポート マネージャー URL の構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-149">Configuring the Report Manager URL</span></span><br /><br /> <span data-ttu-id="32a0c-150">レポート サーバー データベースの作成および構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-150">Creating and configuring the report server database.</span></span><br /><br /> <span data-ttu-id="32a0c-151">スケールアウト配置の構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-151">Configuring a scale-out deployment.</span></span><br /><br /> <span data-ttu-id="32a0c-152">保存されている接続文字列や資格情報を暗号化する対称キーのバックアップ、復元、または置き換え</span><span class="sxs-lookup"><span data-stu-id="32a0c-152">Backup, restoring, or replacing the symmetric key that is used to encrypt stored connection strings and credentials.</span></span><br /><br /> <span data-ttu-id="32a0c-153">自動実行アカウントの構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-153">Configuring the unattended execution account.</span></span><br /><br /> <span data-ttu-id="32a0c-154">電子メール配信用の SMTP サーバーの構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-154">Configuring an SMTP server for e-mail delivery.</span></span><br /><br /> <br /><br /> <span data-ttu-id="32a0c-155">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-155">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>|<span data-ttu-id="32a0c-156">スタート メニュー</span><span class="sxs-lookup"><span data-stu-id="32a0c-156">Start menu</span></span>|  
|<span data-ttu-id="32a0c-157">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="32a0c-157">SQL Server Management Studio</span></span>|<span data-ttu-id="32a0c-158">次のように、単一の環境で 1 つ以上のレポート サーバー インスタンスを管理するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-158">Use this tool to manage one or more report server instances in a single environment, including:</span></span><br /><br /> <span data-ttu-id="32a0c-159">ローカルとリモートの両方のレポート サーバー インスタンスの管理</span><span class="sxs-lookup"><span data-stu-id="32a0c-159">Managing both local and remote report server instances</span></span><br /><br /> <span data-ttu-id="32a0c-160">レポート サーバーのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="32a0c-160">Setting report server properties</span></span><br /><br /> <span data-ttu-id="32a0c-161">ロールの定義の変更</span><span class="sxs-lookup"><span data-stu-id="32a0c-161">Modifying role definitions</span></span><br /><br /> <span data-ttu-id="32a0c-162">使用していないレポート サーバー機能の無効化</span><span class="sxs-lookup"><span data-stu-id="32a0c-162">Turning off report server features you are not using</span></span><br /><br /> <span data-ttu-id="32a0c-163">ジョブの管理</span><span class="sxs-lookup"><span data-stu-id="32a0c-163">Managing jobs</span></span><br /><br /> <span data-ttu-id="32a0c-164">共有スケジュールの管理</span><span class="sxs-lookup"><span data-stu-id="32a0c-164">Managing shared schedules</span></span>|<span data-ttu-id="32a0c-165">スタート メニュー</span><span class="sxs-lookup"><span data-stu-id="32a0c-165">Start menu</span></span>|  
|<span data-ttu-id="32a0c-166">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="32a0c-166">SQL Server Configuration Manager</span></span>|<span data-ttu-id="32a0c-167">このツールは次の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-167">Use this tool to:</span></span><br /><br /> <span data-ttu-id="32a0c-168">Reporting Services の Windows サービスの開始と停止</span><span class="sxs-lookup"><span data-stu-id="32a0c-168">Start and stop the Reporting Services Windows services</span></span><br /><br /> <span data-ttu-id="32a0c-169">カスタマー フィードバック レポート、ダンプ ディレクトリの場所、およびエラー報告の構成</span><span class="sxs-lookup"><span data-stu-id="32a0c-169">Configure Customer Feedback Reporting, the dump directory location, and error reporting</span></span><br /><br /> <br /><br /> <span data-ttu-id="32a0c-170">警告このツールを使用してサービスアカウントを構成することはできません。 \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="32a0c-170">**\*\* Warning \*\*** Do not use this tool to configure service account.</span></span> <span data-ttu-id="32a0c-171">代わりに Reporting Services 構成ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-171">Use the Reporting Services Configuration tool instead.</span></span><br /><br /> <span data-ttu-id="32a0c-172">詳細については、「 [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-172">For more information, see [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md).</span></span>|<span data-ttu-id="32a0c-173">スタート メニュー</span><span class="sxs-lookup"><span data-stu-id="32a0c-173">Start menu</span></span>|  
|<span data-ttu-id="32a0c-174">Rsconfig ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="32a0c-174">Rsconfig Utility</span></span>|<span data-ttu-id="32a0c-175">レポート サーバー データベースへのレポート サーバー接続を構成および管理するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-175">Use this tool to configure and manage a report server connection to the report server database.</span></span> <span data-ttu-id="32a0c-176">これを使用して、自動レポート処理に使用するユーザー アカウントを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="32a0c-176">You can also use it to specify a user account to use for unattended report processing.</span></span><br /><br /> <span data-ttu-id="32a0c-177">詳細については、「[レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)](report-server-command-prompt-utilities-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-177">For more information, see [Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).</span></span>|<span data-ttu-id="32a0c-178">コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="32a0c-178">Command prompt</span></span>|  
|<span data-ttu-id="32a0c-179">Rskeymgmt ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="32a0c-179">Rskeymgmt Utility</span></span>|<span data-ttu-id="32a0c-180">このツールは次の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-180">Use this tool to:</span></span><br /><br /> <span data-ttu-id="32a0c-181">レポート サーバー データの暗号化に使用する対称キーの抽出、復元、作成、および削除</span><span class="sxs-lookup"><span data-stu-id="32a0c-181">Extract, restore, create, and delete the symmetric key used to encrypt report server data</span></span><br /><br /> <span data-ttu-id="32a0c-182">スケールアウト配置へのレポート サーバー インスタンスの追加</span><span class="sxs-lookup"><span data-stu-id="32a0c-182">Join report server instances in a scale-out deployment</span></span><br /><br /> <br /><br /> <span data-ttu-id="32a0c-183">詳細については、「[レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)](report-server-command-prompt-utilities-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-183">For more information, see [Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).</span></span>|<span data-ttu-id="32a0c-184">コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="32a0c-184">Command prompt</span></span>|  
|<span data-ttu-id="32a0c-185">Windows Management Instrumentation (WMI) クラス</span><span class="sxs-lookup"><span data-stu-id="32a0c-185">Windows Management Instrumentation (WMI) Classes</span></span>|<span data-ttu-id="32a0c-186">グラフィカル ユーザー インターフェイスを使用せずに、Reporting Services 構成マネージャーの構成タスクを自動化するには、これらのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-186">Use these classes to automate the configuration tasks in Reporting Services Configuration Manager without the need to use the graphical user interface.</span></span><br /><br /> <span data-ttu-id="32a0c-187">詳細については、「 [Accessing the WMI Provider Programmatically](../accessing-the-wmi-provider-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-187">For more information, see [Accessing the WMI Provider Programmatically](../accessing-the-wmi-provider-programmatically.md).</span></span>|<span data-ttu-id="32a0c-188">Visual Basic スクリプト</span><span class="sxs-lookup"><span data-stu-id="32a0c-188">Visual Basic script</span></span>|  
  
### <a name="sharepoint-integrated-mode"></a><span data-ttu-id="32a0c-189">SharePoint 統合モード</span><span class="sxs-lookup"><span data-stu-id="32a0c-189">SharePoint Integrated Mode</span></span>  
 <span data-ttu-id="32a0c-190">SharePoint モードでは、Reporting Services は SharePoint アーキテクチャのサービス アプリケーションであり、SharePoint によって直接管理されます。</span><span class="sxs-lookup"><span data-stu-id="32a0c-190">In SharePoint mode, the Reporting Services is a service application in the SharePoint architecture, and is administered directly through SharePoint</span></span>  
  
|<span data-ttu-id="32a0c-191">ツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-191">Tool</span></span>|<span data-ttu-id="32a0c-192">説明</span><span class="sxs-lookup"><span data-stu-id="32a0c-192">Description</span></span>|<span data-ttu-id="32a0c-193">アクセス方法</span><span class="sxs-lookup"><span data-stu-id="32a0c-193">How to access</span></span>|  
|----------|-----------------|-------------------|  
|<span data-ttu-id="32a0c-194">SharePoint サーバーの全体管理</span><span class="sxs-lookup"><span data-stu-id="32a0c-194">SharePoint Central Administration</span></span>|<span data-ttu-id="32a0c-195">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の共有サービス アプリケーションを作成、クエリ、および管理するには、SharePoint サーバーの全体管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-195">Use SharePoint Central Administration to create, query, and manage the shared service applications for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="32a0c-196">詳細については、「[レポート サーバーの構成と管理 (Reporting Services SharePoint モード)](../configure-administer-report-server-reporting-services-sharepoint-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-196">For more information, see [Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md).</span></span>|<span data-ttu-id="32a0c-197">サーバーの全体管理の SharePoint サイト URL に接続するブラウザー</span><span class="sxs-lookup"><span data-stu-id="32a0c-197">Browser to the SharePoint site URL for Central Administration</span></span>|  
|<span data-ttu-id="32a0c-198">PowerShell コマンドレット</span><span class="sxs-lookup"><span data-stu-id="32a0c-198">PowerShell Cmdlets</span></span>|<span data-ttu-id="32a0c-199">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の共有サービス アプリケーションを作成、クエリ、および管理するには、PowerShell コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-199">Use PowerShell cmdlets to create, query, and manage the shared service applications for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="32a0c-200">詳細については、「 [Reporting Services SharePoint モード用の PowerShell コマンドレット](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-200">For more information, see [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>|<span data-ttu-id="32a0c-201">SharePoint 2010 管理シェル</span><span class="sxs-lookup"><span data-stu-id="32a0c-201">SharePoint 2010 Management Shell</span></span>|  
  
## <a name="tools-for-report-content-management"></a><span data-ttu-id="32a0c-202">レポート コンテンツ管理用のツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-202">Tools for Report Content Management</span></span>  
 <span data-ttu-id="32a0c-203">のコンテンツを管理するためのグラフィカルツールとスクリプトツールのセットが用意されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="32a0c-203">A set of graphical and scripting tools are available for managing content in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="32a0c-204">使用するツールは、レポート サーバーの配置モードによって異なります。</span><span class="sxs-lookup"><span data-stu-id="32a0c-204">The tools that you use depend on the deployment mode of your report server.</span></span>  
  
|<span data-ttu-id="32a0c-205">ツール</span><span class="sxs-lookup"><span data-stu-id="32a0c-205">Tool</span></span>|<span data-ttu-id="32a0c-206">説明</span><span class="sxs-lookup"><span data-stu-id="32a0c-206">Description</span></span>|<span data-ttu-id="32a0c-207">アクセス方法</span><span class="sxs-lookup"><span data-stu-id="32a0c-207">How to access</span></span>|  
|----------|-----------------|-------------------|  
|<span data-ttu-id="32a0c-208">レポート サーバー Web サービスの URL</span><span class="sxs-lookup"><span data-stu-id="32a0c-208">Report Server Web service URL</span></span>|<span data-ttu-id="32a0c-209">汎用アイテム ナビゲーション ページのレポート カタログのコンテンツを参照するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-209">Use this tool to browse content in the report catalog in a generic item navigation page.</span></span><br /><br /> <span data-ttu-id="32a0c-210">詳細については、「 [Report Server Web Service](../report-server-web-service/report-server-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-210">For more information, see [Report Server Web Service](../report-server-web-service/report-server-web-service.md).</span></span>|<span data-ttu-id="32a0c-211">Browser</span><span class="sxs-lookup"><span data-stu-id="32a0c-211">Browser</span></span>|  
|<span data-ttu-id="32a0c-212">レポート マネージャー</span><span class="sxs-lookup"><span data-stu-id="32a0c-212">Report Manager</span></span>|<span data-ttu-id="32a0c-213">**(ネイティブ モードのみ)** HTTP 接続を経由してリモートの場所から 1 つのレポート サーバー インスタンスを管理するには、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-213">**(Native mode only)** Use this tool to administer a single report server instance from a remote location over an HTTP connection.</span></span> <span data-ttu-id="32a0c-214">次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="32a0c-214">You can do the following:</span></span><br /><br /> <span data-ttu-id="32a0c-215">レポートの表示、検索、印刷、およびサブスクライブ。</span><span class="sxs-lookup"><span data-stu-id="32a0c-215">View, search, print, and subscribe to reports.</span></span><br /><br /> <span data-ttu-id="32a0c-216">サーバー上のアイテムを整理するフォルダー階層の作成、セキュリティ保護、および保守。</span><span class="sxs-lookup"><span data-stu-id="32a0c-216">Create, secure, and maintain the folder hierarchy to organize items on the server.</span></span><br /><br /> <span data-ttu-id="32a0c-217">アイテムおよび操作に対するアクセスを決定するロールベースのセキュリティの構成。</span><span class="sxs-lookup"><span data-stu-id="32a0c-217">Configure role-based security that determines access to items and operations.</span></span><br /><br /> <span data-ttu-id="32a0c-218">レポート実行プロパティ、レポート履歴、およびレポート パラメーターの構成。</span><span class="sxs-lookup"><span data-stu-id="32a0c-218">Configure report execution properties, report history, and report parameters.</span></span><br /><br /> <span data-ttu-id="32a0c-219">Microsoft SQL Server Analysis Services データ ソースまたは SQL Server リレーショナル データ ソースに接続してデータを取得するレポート モデルの作成。</span><span class="sxs-lookup"><span data-stu-id="32a0c-219">Create report models that connect to and retrieve data from a Microsoft SQL Server Analysis Services data source or from a SQL Server relational data source.</span></span><br /><br /> <span data-ttu-id="32a0c-220">モデル内の特定のエンティティへのアクセスを許可するモデル アイテム セキュリティの設定、または事前に作成した定義済みのクリックスルー レポートへのエンティティのマップ。</span><span class="sxs-lookup"><span data-stu-id="32a0c-220">Set model item security to allow access to specific entities in the model, or map entities to predefined clickthrough reports that you create in advance.</span></span><br /><br /> <span data-ttu-id="32a0c-221">スケジュールおよびデータ ソース接続をさらに管理しやすくする共有スケジュールおよび共有データ ソースの作成。</span><span class="sxs-lookup"><span data-stu-id="32a0c-221">Create shared schedules and shared data sources to make schedules and data source connections more manageable.</span></span><br /><br /> <span data-ttu-id="32a0c-222">大きい受信者一覧にレポートをロール アウトするデータ ドリブン サブスクリプションの作成。</span><span class="sxs-lookup"><span data-stu-id="32a0c-222">Create data-driven subscriptions that roll out reports to a large recipient list.</span></span><br /><br /> <span data-ttu-id="32a0c-223">既存レポートの再利用や目的変更を行うための、リンク レポートの作成。</span><span class="sxs-lookup"><span data-stu-id="32a0c-223">Create linked reports to reuse and repurpose an existing report in different ways.</span></span><br /><br /> <span data-ttu-id="32a0c-224">レポートを作成するレポート ビルダーの起動。作成したレポートは、レポート サーバーで保存および実行できます。</span><span class="sxs-lookup"><span data-stu-id="32a0c-224">Launch Report Builder to create reports that you can save and run on the report server.</span></span><br /><br /> <br /><br /> <span data-ttu-id="32a0c-225">詳細については、「[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-225">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>||  
|<span data-ttu-id="32a0c-226">RS ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="32a0c-226">RS Utility</span></span>|<span data-ttu-id="32a0c-227">このツールは、スクリプト操作の実行に使用できるスクリプト ホストです。</span><span class="sxs-lookup"><span data-stu-id="32a0c-227">This tool is a script host that you can use to perform scripted operations.</span></span> <span data-ttu-id="32a0c-228">このツールを使用して、レポート サーバー データベース間でのデータのコピー、レポートのパブリッシュ、レポート サーバー データベースでのアイテムの作成などを行う [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="32a0c-228">Use this tool to run [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] scripts that copy data between report server databases, publish reports, create items in a report server database, and more.</span></span><br /><br /> <span data-ttu-id="32a0c-229">詳細については、「[レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)](report-server-command-prompt-utilities-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32a0c-229">For more information, see [Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).</span></span>|<span data-ttu-id="32a0c-230">コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="32a0c-230">Command prompt</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32a0c-231">参照</span><span class="sxs-lookup"><span data-stu-id="32a0c-231">See Also</span></span>  
 <span data-ttu-id="32a0c-232">[レポートサーバーの Reporting Services](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="32a0c-232">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="32a0c-233">[SSRS&#41;&#40;の Reporting Services の概念](../reporting-services-concepts-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32a0c-233">[Reporting Services Concepts &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) </span></span>  
 [<span data-ttu-id="32a0c-234">Reporting Services &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32a0c-234">Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  