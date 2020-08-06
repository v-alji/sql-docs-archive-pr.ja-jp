---
title: SQL Server セットアップ ログ ファイルの表示と読み取り | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 70f9bbb9a8ed72503dc6fe90077232748b2c4ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714565"
---
# <a name="view-and-read-sql-server-setup-log-files"></a><span data-ttu-id="ddcc3-102">SQL Server セットアップ ログ ファイルの表示と読み取り</span><span class="sxs-lookup"><span data-stu-id="ddcc3-102">View and Read SQL Server Setup Log Files</span></span>
  <span data-ttu-id="ddcc3-103">セットアップを実行するたびにログファイルが、新しいタイムスタンプを持つログフォルダーと共に% programfiles% \120\Setup Bootstrap\Log に作成され \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-103">Each execution of Setup creates log files are created with a new timestamped log folder at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span> <span data-ttu-id="ddcc3-104">タイムスタンプ付きのログ フォルダーの名前形式は YYYYMMDD_hhmmss です。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-104">The time-stamped log folder name format is YYYYMMDD_hhmmss.</span></span> <span data-ttu-id="ddcc3-105">セットアップを自動モードで実行した場合は、% temp%\sqlsetup\*.log にログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-105">When Setup is run in an unattended mode, the logs are created at % temp%\sqlsetup\*.log.</span></span> <span data-ttu-id="ddcc3-106">ログ フォルダー内のログ ファイルはすべて、それぞれのログ フォルダー内で Log\*.cab ファイルにアーカイブされます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-106">All files in the logs folder are archived into the Log\*.cab file in their respective log folder.</span></span>  
  
 <span data-ttu-id="ddcc3-107">一般的なセットアップの要求では、次の 3 つの実行フェーズを経由します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-107">A typical Setup request goes through three execution phases:</span></span>  
  
1.  <span data-ttu-id="ddcc3-108">グローバル ルールのテキスト</span><span class="sxs-lookup"><span data-stu-id="ddcc3-108">Global rules text</span></span>  
  
2.  <span data-ttu-id="ddcc3-109">コンポーネントの更新</span><span class="sxs-lookup"><span data-stu-id="ddcc3-109">Component update</span></span>  
  
3.  <span data-ttu-id="ddcc3-110">ユーザーが要求した操作</span><span class="sxs-lookup"><span data-stu-id="ddcc3-110">User-requested action</span></span>  
  
 <span data-ttu-id="ddcc3-111">各フェーズでは、セットアップが詳細ログと概要ログを生成するほか、必要に応じて追加のログ ファイルも生成されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-111">In each phase, Setup generates detail and summary logs with additional logs created as appropriate.</span></span> <span data-ttu-id="ddcc3-112">セットアップは、ユーザーが要求したセットアップ操作ごとに最低 3 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-112">Setup is called at least three times per user-requested Setup action.</span></span>  
  
 <span data-ttu-id="ddcc3-113">データストア ファイルにはセットアップ処理で記録されるすべての構成オブジェクトの状態を示すスナップショットが含まれており、構成エラーのトラブルシューティングに便利です。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-113">Datastore files contain a snapshot of the state of all configuration objects being tracked by the Setup process, and are useful for troubleshooting configuration errors.</span></span> <span data-ttu-id="ddcc3-114">実行フェーズごとに、データストア オブジェクトに対して XML ファイル ダンプが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-114">XML file dumps are created for datastore objects for each execution phase.</span></span> <span data-ttu-id="ddcc3-115">これらの XML ファイル ダンプは、次に示すタイムスタンプ付きのログ フォルダー内にある独自のログ サブフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-115">They are saved in their own log subfolder under the time-stamped log folder, as follows:</span></span>  
  
-   <span data-ttu-id="ddcc3-116">Datastore_GlobalRules</span><span class="sxs-lookup"><span data-stu-id="ddcc3-116">Datastore_GlobalRules</span></span>  
  
-   <span data-ttu-id="ddcc3-117">Datastore_ComponentUpdated</span><span class="sxs-lookup"><span data-stu-id="ddcc3-117">Datastore_ComponentUpdated</span></span>  
  
-   <span data-ttu-id="ddcc3-118">データストア</span><span class="sxs-lookup"><span data-stu-id="ddcc3-118">Datastore</span></span>  
  
 <span data-ttu-id="ddcc3-119">次のセクションでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップのログ ファイルを説明します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-119">The following sections describe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup log files.</span></span>  
  
## <a name="summary-text"></a><span data-ttu-id="ddcc3-120">概要テキスト</span><span class="sxs-lookup"><span data-stu-id="ddcc3-120">Summary Text</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-121">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-121">Overview</span></span>  
 <span data-ttu-id="ddcc3-122">このファイルは、セットアップ時に検出された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント、オペレーティング システム環境、指定されているコマンド ライン パラメーター値、および実行された各 MSI/MSP の全体的な状態を示します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-122">This file shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components that were detected during Setup, the operating system environment, command-line parameter values if they are specified, and the overall status of each MSI/MSP that was executed.</span></span>  
  
 <span data-ttu-id="ddcc3-123">ログは次の各セクションに整理されています。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-123">The log is organized into the following sections:</span></span>  
  
-   <span data-ttu-id="ddcc3-124">実行全体の要約</span><span class="sxs-lookup"><span data-stu-id="ddcc3-124">An overall summary of the execution</span></span>  
  
-   <span data-ttu-id="ddcc3-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが実行されたコンピューターのプロパティと構成</span><span class="sxs-lookup"><span data-stu-id="ddcc3-125">Properties and the configuration of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup was run</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddcc3-126">そのコンピューターに以前にインストールされていた製品の機能</span><span class="sxs-lookup"><span data-stu-id="ddcc3-126">product features previously installed on the computer</span></span>  
  
-   <span data-ttu-id="ddcc3-127">インストールされたバージョンとインストール パッケージのプロパティ</span><span class="sxs-lookup"><span data-stu-id="ddcc3-127">Description of the installation version and installation package properties</span></span>  
  
-   <span data-ttu-id="ddcc3-128">インストール時に提供されたランタイム入力設定</span><span class="sxs-lookup"><span data-stu-id="ddcc3-128">Runtime input settings that are provided during install</span></span>  
  
-   <span data-ttu-id="ddcc3-129">構成ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-129">Location of the configuration file</span></span>  
  
-   <span data-ttu-id="ddcc3-130">実行結果の詳細</span><span class="sxs-lookup"><span data-stu-id="ddcc3-130">Details of the execution results</span></span>  
  
-   <span data-ttu-id="ddcc3-131">グローバル ルール</span><span class="sxs-lookup"><span data-stu-id="ddcc3-131">Global rules</span></span>  
  
-   <span data-ttu-id="ddcc3-132">そのインストール シナリオ独自のルール</span><span class="sxs-lookup"><span data-stu-id="ddcc3-132">Rules specific to the installation scenario</span></span>  
  
-   <span data-ttu-id="ddcc3-133">失敗したルール</span><span class="sxs-lookup"><span data-stu-id="ddcc3-133">Failed rules</span></span>  
  
-   <span data-ttu-id="ddcc3-134">ルール レポート ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-134">Location of the rules report file</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-135">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-135">Location</span></span>  
 <span data-ttu-id="ddcc3-136">% Programfiles% \120\Setup Bootstrap\Log にあり \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-136">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span>  
  
 <span data-ttu-id="ddcc3-137">概要テキスト ファイル内でエラーを見つけるには、"エラー" や "失敗" をキーワードにして検索できます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-137">To find errors in the summary text file, search the file by using the "error" or "failed" keywords.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmsstxt"></a><span data-ttu-id="ddcc3-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span><span class="sxs-lookup"><span data-stu-id="ddcc3-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-139">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-139">Overview</span></span>  
 <span data-ttu-id="ddcc3-140">summary_engine の基本的なファイルは概要ファイルに似ていますが、メイン ワークフロー内で生成されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-140">The summary_engine base file is similar to the summary file and is generated during the main workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-141">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-141">Location</span></span>  
 <span data-ttu-id="ddcc3-142">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-142">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmss_componentupdatetxt"></a><span data-ttu-id="ddcc3-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="ddcc3-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-144">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-144">Overview</span></span>  
 <span data-ttu-id="ddcc3-145">コンポーネントの更新概要ファイルは概要ファイルに似ていますが、コンポーネント更新ワークフロー内で生成されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-145">The component update summary log file is similar to the summary file and is generated during the component update workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-146">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-146">Location</span></span>  
 <span data-ttu-id="ddcc3-147">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-147">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_versionnumbermmdd_hhmmss_globalrulestxt"></a><span data-ttu-id="ddcc3-148">Summary_engine-base_ \<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="ddcc3-148">Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-149">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-149">Overview</span></span>  
 <span data-ttu-id="ddcc3-150">グローバル ルール概要ファイルは概要ファイルに似ていますが、グローバル ルール ワークフロー内で生成されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-150">The global rules summary log file is similar to the summary file generated during the global rules workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-151">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-151">Location</span></span>  
 <span data-ttu-id="ddcc3-152">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-152">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detailtxt"></a><span data-ttu-id="ddcc3-153">Detail.txt</span><span class="sxs-lookup"><span data-stu-id="ddcc3-153">Detail.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-154">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-154">Overview</span></span>  
 <span data-ttu-id="ddcc3-155">Detail.txt はインストールやアップグレードなど、メイン ワークフロー内で生成され、実行の詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-155">Detail.txt is generated for the main workflow such as install or upgrade, and provides the details of the execution.</span></span> <span data-ttu-id="ddcc3-156">このファイル内のログは、インストールで各アクションが呼び出された時刻に基づいて生成され、アクションが実行された順序とその依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-156">The logs in the file are generated based on the time when each action for the installation was invoked, and show the order in which the actions were executed, and their dependencies.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-157">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-157">Location</span></span>  
 <span data-ttu-id="ddcc3-158">% Programfiles% \120\Setup にあります。 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcc3-158">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup</span></span>  
  
 <span data-ttu-id="ddcc3-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.</span><span class="sxs-lookup"><span data-stu-id="ddcc3-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.</span></span>  
  
 <span data-ttu-id="ddcc3-160">セットアップ過程でエラーが発生すると、実行やエラーはこのファイルの終わりに記録されます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-160">If an error occurs during the Setup process, the exception or error are logged at the end of this file.</span></span> <span data-ttu-id="ddcc3-161">このファイル内でエラーを見つけるには、まずファイルの終わりを調べてから、「エラー」や「例外」をキーワードにして検索します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-161">To find the errors in this file, first examine the end of the file followed by a search of the file for the "error" or "exception" keywords.</span></span>  
  
## <a name="detail_componentupdatetxt"></a><span data-ttu-id="ddcc3-162">Detail_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="ddcc3-162">Detail_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-163">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-163">Overview</span></span>  
 <span data-ttu-id="ddcc3-164">Detail_ComponentUpdate.txt ファイルはコンポーネント更新ワークフローに対して生成され、Detail.txt に似ています。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-164">The Detail_ComponentUpdate.txt file is generated for the component update workflow and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-165">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-165">Location</span></span>  
 <span data-ttu-id="ddcc3-166">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-166">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detail_globalrulestxt"></a><span data-ttu-id="ddcc3-167">Detail_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="ddcc3-167">Detail_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-168">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-168">Overview</span></span>  
 <span data-ttu-id="ddcc3-169">Detail_GlobalRules.txt ファイルはグローバル ルール実行のために生成され、Detail.txt ファイルに似ています。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-169">Detail_GlobalRules.txt is generated for the global rules execution and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-170">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-170">Location</span></span>  
 <span data-ttu-id="ddcc3-171">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-171">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="msi-log-files"></a><span data-ttu-id="ddcc3-172">MSI ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="ddcc3-172">MSI log files</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-173">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-173">Overview</span></span>  
 <span data-ttu-id="ddcc3-174">MSI ログ ファイルはパッケージ インストール過程の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-174">The MSI log files provide details of the installation package process.</span></span> <span data-ttu-id="ddcc3-175">各パッケージのインストール時に、MSIEXEC によって生成されるログ ファイルです。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-175">They are generated by the MSIEXEC during the installation of the specified package.</span></span>  
  
 <span data-ttu-id="ddcc3-176">MSI ログ ファイルの種類</span><span class="sxs-lookup"><span data-stu-id="ddcc3-176">Types of MSI log files:</span></span>  
  
-   <span data-ttu-id="ddcc3-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="ddcc3-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="ddcc3-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="ddcc3-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="ddcc3-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span><span class="sxs-lookup"><span data-stu-id="ddcc3-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-180">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-180">Location</span></span>  
 <span data-ttu-id="ddcc3-181">MSI ログファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\<名 \> .log にあります。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-181">The MSI log files are located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\<Name\>.log.</span></span>  
  
 <span data-ttu-id="ddcc3-182">ファイルの終わりに実行の概要があり、成功したかどうかとプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-182">At the end of the file is a summary of the execution which includes the success or failure status and properties.</span></span> <span data-ttu-id="ddcc3-183">MSI ファイル内でエラーを見つけるには、"value 3" を検索します。通常、エラーはその文字列の近くで見つかります。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-183">To find the error in the MSI file, search for "value 3" and usually the errors can be found close to the string.</span></span>  
  
## <a name="configurationfileini"></a><span data-ttu-id="ddcc3-184">ConfigurationFile.ini</span><span class="sxs-lookup"><span data-stu-id="ddcc3-184">ConfigurationFile.ini</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-185">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-185">Overview</span></span>  
 <span data-ttu-id="ddcc3-186">構成ファイルにはインストール時に使用される入力の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-186">The configuration file contains the input settings that are provided during installation.</span></span> <span data-ttu-id="ddcc3-187">手動で設定を入力しなくてもインストールを再起動できるようにするときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-187">It can be used to restart the installation without having to enter the settings manually.</span></span> <span data-ttu-id="ddcc3-188">ただし、パスワード、PID、およびパラメーターの一部は構成ファイルには保存されません。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-188">However, passwords for the accounts, PID, and some parameters are not saved in the configuration file.</span></span> <span data-ttu-id="ddcc3-189">設定はファイルに追加できますが、コマンドラインまたはセットアップのインターフェイスを使って供給することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-189">The settings can be either added to the file or provided by using the command line or the Setup user interface.</span></span> <span data-ttu-id="ddcc3-190">詳細については、「[構成ファイルを使用した SQL Server 2014 のインストール](install-sql-server-using-a-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-190">For more information, see [Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md).</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-191">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-191">Location</span></span>  
 <span data-ttu-id="ddcc3-192">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-192">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="systemconfigurationcheck_reporthtm"></a><span data-ttu-id="ddcc3-193">SystemConfigurationCheck_Report.htm</span><span class="sxs-lookup"><span data-stu-id="ddcc3-193">SystemConfigurationCheck_Report.htm</span></span>  
  
### <a name="overview"></a><span data-ttu-id="ddcc3-194">概要</span><span class="sxs-lookup"><span data-stu-id="ddcc3-194">Overview</span></span>  
 <span data-ttu-id="ddcc3-195">システム構成チェッカーのレポートには、実行された各ルールの簡単な記述と、実行ステータスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-195">The system configuration check report contains a short description for each executed rule, and the execution status.</span></span>  
  
### <a name="location"></a><span data-ttu-id="ddcc3-196">場所</span><span class="sxs-lookup"><span data-stu-id="ddcc3-196">Location</span></span>  
 <span data-ttu-id="ddcc3-197">このファイルは、% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>にあり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="ddcc3-197">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcc3-198">参照</span><span class="sxs-lookup"><span data-stu-id="ddcc3-198">See Also</span></span>  
 <span data-ttu-id="ddcc3-199">[インストール方法に関するトピック](../../sql-server/install/installation-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="ddcc3-199">[Installation How-to Topics](../../sql-server/install/installation-how-to-topics.md) </span></span>  
 [<span data-ttu-id="ddcc3-200">SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="ddcc3-200">Install SQL Server 2014</span></span>](install-sql-server.md)  
  
  
