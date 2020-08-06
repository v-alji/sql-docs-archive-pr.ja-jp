---
title: サーバーのパフォーマンスと利用状況の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0fa7902d68c587a7733f07ceb8daccd3a6a98fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645569"
---
# <a name="server-performance-and-activity-monitoring"></a><span data-ttu-id="17854-102">サーバーのパフォーマンスと利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="17854-102">Server Performance and Activity Monitoring</span></span>
  <span data-ttu-id="17854-103">データベースを監視する目的は、サーバーのパフォーマンスを評価することです。</span><span class="sxs-lookup"><span data-stu-id="17854-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="17854-104">適切な監視には、現在のパフォーマンスのスナップショットを定期的にキャプチャして問題の原因となっているプロセスを特定したり、長期にわたって継続的にデータを採取してパフォーマンスの傾向を追跡する作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="17854-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="17854-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows オペレーティング システムでは、データベースの現在の状態を参照したり、状態の変化に伴うパフォーマンスを追跡するためのユーティリティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="17854-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system provide utilities that let you view the current condition of the database and to track performance as conditions change.</span></span>  
  
 <span data-ttu-id="17854-106">次のセクションには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Windows のパフォーマンスと利用状況の監視ツールの使用方法を説明するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="17854-106">The following section contains topics that describe how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span> <span data-ttu-id="17854-107">ここで説明する内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="17854-107">It contains the following topics:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17854-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="17854-108">In This Section</span></span>  
 <span data-ttu-id="17854-109">**Windows ツールで監視タスクを実行するには**</span><span class="sxs-lookup"><span data-stu-id="17854-109">**To perform monitoring tasks with Windows tools**</span></span>  
  
-   [<span data-ttu-id="17854-110">システム モニターの起動 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-110">Start System Monitor &#40;Windows&#41;</span></span>](start-system-monitor-windows.md)  
  
-   [<span data-ttu-id="17854-111">Windows アプリケーション ログの表示 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-111">View the Windows Application Log &#40;Windows&#41;</span></span>](view-the-windows-application-log-windows-10.md)  
  
 <span data-ttu-id="17854-112">**Windows ツールで SQL Server データベースの警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="17854-112">**To create SQL Server database alerts with Windows tools**</span></span>  
  
-   [<span data-ttu-id="17854-113">SQL Server データベースの警告のセットアップ &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-113">Set Up a SQL Server Database Alert &#40;Windows&#41;</span></span>](set-up-a-sql-server-database-alert-windows.md)  
  
 <span data-ttu-id="17854-114">**SQL Server Management Studio で監視タスクを実行するには**</span><span class="sxs-lookup"><span data-stu-id="17854-114">**To perform monitoring tasks with SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="17854-115">SQL Server エラー ログの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-115">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="17854-116">利用状況モニターを開く方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-116">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)  
  
 <span data-ttu-id="17854-117">**Transact-SQL ストアド プロシージャを使用して SQL トレースで監視タスクを実行するには**</span><span class="sxs-lookup"><span data-stu-id="17854-117">**To perform monitoring tasks with SQL Trace by using Transact-SQL stored procedures**</span></span>  
  
-   [<span data-ttu-id="17854-118">トレースの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-118">Create a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
-   [<span data-ttu-id="17854-119">トレース フィルターの設定 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-119">Set a Trace Filter &#40;Transact-SQL&#41;</span></span>](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
-   [<span data-ttu-id="17854-120">既存のトレースの変更 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-120">Modify an Existing Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [<span data-ttu-id="17854-121">保存されているトレースの表示 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-121">View a Saved Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [<span data-ttu-id="17854-122">フィルター情報の表示 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-122">View Filter Information &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-filter-information-transact-sql.md)  
  
-   [<span data-ttu-id="17854-123">トレースの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-123">Delete a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/delete-a-trace-transact-sql.md)  
  
 <span data-ttu-id="17854-124">**SQL Server Profiler を使用してトレースを作成および変更するには**</span><span class="sxs-lookup"><span data-stu-id="17854-124">**To create and modify traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="17854-125">トレースの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-125">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-126">グローバル トレース オプションの設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-126">Set Global Trace Options &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-127">トレース ファイルに含めるイベントとデータ列の指定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-127">Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-128">トレースを実行するための Transact-SQL スクリプトの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-128">Create a Transact-SQL Script for Running a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-129">トレース結果のファイルへの保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-129">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-130">トレース ファイルの最大ファイル サイズの設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-130">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-131">トレース結果のテーブルへの保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-131">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-132">トレース テーブルの最大テーブル サイズの設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-132">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-133">トレース内のイベントへのフィルターの適用 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-133">Filter Events in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-134">フィルター情報の表示 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-134">View Filter Information &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-135">フィルターの変更 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-135">Modify a Filter &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-136">イベントの開始時刻に基づいたイベントのフィルター選択 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-136">Filter Events Based on the Event Start Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-137">イベントの終了時刻に基づいたフィルターでのイベントの選択 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-137">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-138">トレースでのサーバー プロセス ID &#40;SPIDs&#41; のフィルター選択 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-138">Filter Server Process IDs &#40;SPIDs&#41; in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-139">トレースに表示される列の構成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-139">Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="17854-140">**SQL Server Profiler を使用してトレースを開始、一時停止、および停止するには**</span><span class="sxs-lookup"><span data-stu-id="17854-140">**To start, pause, and stop traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="17854-141">サーバーへの接続後の自動的なトレースの開始 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-141">Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-142">トレースの一時停止 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-142">Pause a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-143">トレースの停止 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-143">Stop a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-144">一時停止または停止したトレースの再開 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-144">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
 <span data-ttu-id="17854-145">**SQL Server Profiler を使用してトレースを開き、トレースの表示方法を構成するには**</span><span class="sxs-lookup"><span data-stu-id="17854-145">**To open traces and configure how traces are displayed by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="17854-146">トレース ファイルを開く &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-146">Open a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-147">トレース テーブルを開く &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-147">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-148">トレース ウィンドウの消去 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-148">Clear a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-149">トレース ウィンドウを閉じる &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-149">Close a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-150">トレース定義の既定値の設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-150">Set Trace Definition Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-151">トレース表示の既定値の設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-151">Set Trace Display Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="17854-152">**SQL Server Profiler を使用してトレースを再生するには**</span><span class="sxs-lookup"><span data-stu-id="17854-152">**To replay traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="17854-153">トレース ファイルを再生する &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-153">Replay a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-154">トレース テーブルを再生する &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-154">Replay a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-155">一度に単一のイベントの再生 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-155">Replay a Single Event at a Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-156">ブレークポイントまでの再生 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-156">Replay to a Breakpoint &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-157">カーソルまでの再生 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-157">Replay to a Cursor &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-158">Transact-SQL スクリプトの再生 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-158">Replay a Transact-SQL Script &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
 <span data-ttu-id="17854-159">**SQL Server Profiler を使用してトレース テンプレートを作成、変更、および使用するには**</span><span class="sxs-lookup"><span data-stu-id="17854-159">**To create, modify, and use trace templates by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="17854-160">トレース テンプレートの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-160">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-161">トレース テンプレートの変更 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-161">Modify a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-162">実行中のトレースからのテンプレートの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-162">Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-163">トレース ファイルまたはトレース テーブルからのテンプレートの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-163">Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-164">トレース テンプレートのエクスポート &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-164">Export a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-165">トレース テンプレートのインポート &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-165">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="17854-166">**SQL Server Profiler トレースを使用してサーバーのパフォーマンスを収集および監視するには**</span><span class="sxs-lookup"><span data-stu-id="17854-166">**To use SQL Server Profiler traces to collect and monitor server performance**</span></span>  
  
-   [<span data-ttu-id="17854-167">トレース中の値列またはデータ列の検索 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-167">Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-168">Deadlock Graph の保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-168">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-169">Showplan XML イベントを個別に保存する方法 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-169">Save Showplan XML Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-170">Showplan XML Statistics Profile イベントを個別に保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-170">Save Showplan XML Statistics Profile Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-171">トレースからのスクリプトの抽出 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-171">Extract a Script from a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="17854-172">トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17854-172">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
