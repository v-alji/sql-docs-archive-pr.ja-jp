---
title: グローバルトレースオプションの設定 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- global trace options [SQL Server]
ms.assetid: 2854608a-c3c7-4eb8-b567-034bfec4b1a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f0809ae11776e1bddf42c189b86f48689ff4859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632237"
---
# <a name="set-global-trace-options-sql-server-profiler"></a><span data-ttu-id="099fc-102">グローバル トレース オプションの設定 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="099fc-102">Set Global Trace Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="099fc-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の特定のインスタンスで作成したすべてのトレースに適用するオプションの設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="099fc-103">This topic describes how to set options that apply to all traces that are created with a specific instance of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-global-trace-options"></a><span data-ttu-id="099fc-104">グローバル トレース オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="099fc-104">To set global trace options</span></span>  
  
1.  <span data-ttu-id="099fc-105">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="099fc-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="099fc-106">**[全般オプション]** ダイアログ ボックスで、 **[フォントの選択]** をクリックして表示オプションを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="099fc-106">In the **General Options**dialog box, click **Choose Font**to modify the display options, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="099fc-107">必要に応じて、 **[接続の確立直後にトレースを開始する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="099fc-107">Optionally, select **Start tracing immediately after making connection**.</span></span>  
  
4.  <span data-ttu-id="099fc-108">必要に応じて、 **[プロバイダーのバージョンが変更されたときに、トレース定義を更新する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="099fc-108">Optionally, select **Update trace definition when provider version changes**.</span></span> <span data-ttu-id="099fc-109">このオプションの使用をお勧めします。既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="099fc-109">This option is recommended and is selected by default.</span></span> <span data-ttu-id="099fc-110">このオプションを選択した場合、トレース定義はトレースを実行するサーバーの現在のバージョンに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="099fc-110">When this option is selected, the trace definition is automatically updated to the current version of the server where tracing is performed.</span></span>  
  
5.  <span data-ttu-id="099fc-111">必要に応じて、サーバーでロールオーバー ファイルを管理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="099fc-111">Optionally, specify how the server should manage rollover files:</span></span>  
  
    -   <span data-ttu-id="099fc-112">再生時にロールオーバー ファイルを自動的に読み込むには、 **[確認せずにすべてのロールオーバー ファイルを順に読み込む]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="099fc-112">Select **Load all rollover files in sequence without prompting** to automatically load rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="099fc-113">再生時にロールオーバー ファイルを制御するには、 **[ロールオーバー ファイルを読み込む前に確認する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="099fc-113">Select **Prompt before loading rollover files** to control rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="099fc-114">一度に 1 つのファイルのみを再生するには、 **[後続のロールオーバー ファイルを読み込まない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="099fc-114">Select **Never load subsequent rollover files** to replay only one file at a time.</span></span>  
  
6.  <span data-ttu-id="099fc-115">必要に応じて、再生オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="099fc-115">Optionally, set replay options:</span></span>  
  
    -   <span data-ttu-id="099fc-116">**[再生スレッドの既定の数]** では、再生時に使用するプロセッサ スレッドの数を制御します。</span><span class="sxs-lookup"><span data-stu-id="099fc-116">**Default number of replay threads** controls the number of processor threads to use during replay.</span></span> <span data-ttu-id="099fc-117">スレッド数を多くすると、再生は早く完了しますが、再生時にサーバーのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="099fc-117">A higher number of threads causes replay to complete faster, but causes server performance to degrade during replay.</span></span> <span data-ttu-id="099fc-118">推奨設定値は **4**です。</span><span class="sxs-lookup"><span data-stu-id="099fc-118">The recommended setting is **4**.</span></span> <span data-ttu-id="099fc-119">次の表は、使用可能な値の一覧です。</span><span class="sxs-lookup"><span data-stu-id="099fc-119">The following table lists the available options:</span></span>  
  
        |<span data-ttu-id="099fc-120">値</span><span class="sxs-lookup"><span data-stu-id="099fc-120">Value</span></span>|<span data-ttu-id="099fc-121">説明</span><span class="sxs-lookup"><span data-stu-id="099fc-121">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="099fc-122">**2**</span><span class="sxs-lookup"><span data-stu-id="099fc-122">**2**</span></span>|<span data-ttu-id="099fc-123">最小値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-123">Minimum value.</span></span> <span data-ttu-id="099fc-124">2 つのスレッドを使用して再生します。</span><span class="sxs-lookup"><span data-stu-id="099fc-124">Use two threads to replay.</span></span>|  
        |<span data-ttu-id="099fc-125">**4**</span><span class="sxs-lookup"><span data-stu-id="099fc-125">**4**</span></span>|<span data-ttu-id="099fc-126">既定値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-126">Default value.</span></span>|  
        |<span data-ttu-id="099fc-127">**255**</span><span class="sxs-lookup"><span data-stu-id="099fc-127">**255**</span></span>|<span data-ttu-id="099fc-128">最大値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-128">Maximum value.</span></span> <span data-ttu-id="099fc-129">最大値を設定すると、他のプロセスのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="099fc-129">Setting a maximum value will impede performance for other processes.</span></span>|  
  
    -   <span data-ttu-id="099fc-130">**[ヘルス モニターの既定の待機間隔 (秒)]** では、再生スレッドが他のプロセスをブロックできる最長時間を秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="099fc-130">**Default health monitor wait interval (sec)** sets the maximum amount of time that a replay thread can block another process in seconds.</span></span> <span data-ttu-id="099fc-131">次の表は、その値を示しています。</span><span class="sxs-lookup"><span data-stu-id="099fc-131">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="099fc-132">値</span><span class="sxs-lookup"><span data-stu-id="099fc-132">Value</span></span>|<span data-ttu-id="099fc-133">説明</span><span class="sxs-lookup"><span data-stu-id="099fc-133">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="099fc-134">**0**</span><span class="sxs-lookup"><span data-stu-id="099fc-134">**0**</span></span>|<span data-ttu-id="099fc-135">最小値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-135">Minimum value.</span></span> <span data-ttu-id="099fc-136">**0** に設定すると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によってブロック プロセスが停止されません。</span><span class="sxs-lookup"><span data-stu-id="099fc-136">A setting of **0** means that [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will never stop a blocking process.</span></span>|  
        |<span data-ttu-id="099fc-137">**3600**</span><span class="sxs-lookup"><span data-stu-id="099fc-137">**3600**</span></span>|<span data-ttu-id="099fc-138">既定値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-138">Default value.</span></span> <span data-ttu-id="099fc-139">**3600** 秒 (1 時間) を超えないブロック プロセスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="099fc-139">Allow blocking processes that do not exceed **3600** seconds, or one hour.</span></span>|  
        |<span data-ttu-id="099fc-140">**86400**</span><span class="sxs-lookup"><span data-stu-id="099fc-140">**86400**</span></span>|<span data-ttu-id="099fc-141">最大値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-141">Maximum value.</span></span> <span data-ttu-id="099fc-142">**86400** 秒 (1 日) を超えないブロック プロセスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="099fc-142">Allow blocking processes that do not exceed **86400** seconds, or one day.</span></span>|  
  
    -   <span data-ttu-id="099fc-143">**[ヘルス モニターの既定のポーリング間隔 (秒)]** では、ブロック プロセスの再生スレッドを呼び出す頻度を設定します。</span><span class="sxs-lookup"><span data-stu-id="099fc-143">**Default health monitor poll interval (sec)** sets the frequency to poll replay threads for blocking processes.</span></span> <span data-ttu-id="099fc-144">次の表は、その値を示しています。</span><span class="sxs-lookup"><span data-stu-id="099fc-144">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="099fc-145">値</span><span class="sxs-lookup"><span data-stu-id="099fc-145">Value</span></span>|<span data-ttu-id="099fc-146">説明</span><span class="sxs-lookup"><span data-stu-id="099fc-146">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="099fc-147">**1**</span><span class="sxs-lookup"><span data-stu-id="099fc-147">**1**</span></span>|<span data-ttu-id="099fc-148">最小値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-148">Minimum value.</span></span> <span data-ttu-id="099fc-149">**1** に設定すると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によって毎秒 1 回ブロック プロセスが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="099fc-149">A setting of **1** means [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will poll for blocking processes once per second.</span></span>|  
        |<span data-ttu-id="099fc-150">**60**</span><span class="sxs-lookup"><span data-stu-id="099fc-150">**60**</span></span>|<span data-ttu-id="099fc-151">既定値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-151">Default value.</span></span> <span data-ttu-id="099fc-152">毎分 1 回ブロック プロセスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="099fc-152">Poll for blocking processes once per minute.</span></span>|  
        |<span data-ttu-id="099fc-153">**86400**</span><span class="sxs-lookup"><span data-stu-id="099fc-153">**86400**</span></span>|<span data-ttu-id="099fc-154">最大値です。</span><span class="sxs-lookup"><span data-stu-id="099fc-154">Maximum value.</span></span> <span data-ttu-id="099fc-155">**86400** 秒 (1 日) に 1 回ブロック プロセスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="099fc-155">Poll for blocking processes once per **86400** seconds, or one day.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="099fc-156">参照</span><span class="sxs-lookup"><span data-stu-id="099fc-156">See Also</span></span>  
 <span data-ttu-id="099fc-157">[トレース表示の既定値の設定 &#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="099fc-157">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="099fc-158">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="099fc-158">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
