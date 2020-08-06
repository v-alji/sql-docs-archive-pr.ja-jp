---
title: 制御フローのデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- breakpoints [Integration Services]
- debugging [Integration Services], control flow
- control flow [Integration Services], debugging
- color-coded progress reporting [Integration Services]
- Set Breakpoints dialog box
ms.assetid: 54a458cc-9f4f-4b48-8cf2-db2e0fa7756c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f2e2feff6723a510cb773131cb6452bdc7a77cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718446"
---
# <a name="debugging-control-flow"></a><span data-ttu-id="281e9-102">制御フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="281e9-102">Debugging Control Flow</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="281e9-103">と [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージの制御フローのトラブルシューティングに使用できる、機能とツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="281e9-103">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include features and tools that you can use to troubleshoot the control flow in an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package.</span></span>

-   [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="281e9-104">では、コンテナーおよびタスク上のブレークポイントがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="281e9-104">supports breakpoints on containers and tasks.</span></span>

-   [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="281e9-105">デザイナーでは、実行時の進行状況レポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="281e9-105">Designer provides progress reporting at run time.</span></span>

-   [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="281e9-106">では、デバッグ ウィンドウが用意されています。</span><span class="sxs-lookup"><span data-stu-id="281e9-106">provides debug windows.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="281e9-107">ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="281e9-107">Breakpoints</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="281e9-108">デザイナーには、 **[ブレークポイントの設定]** ダイアログ ボックスが用意されています。このダイアログ ボックスから、ブレークの条件を有効にし、パッケージの実行が中断するまでのブレークポイントの到達回数を指定することにより、ブレークポイントを設定できます。</span><span class="sxs-lookup"><span data-stu-id="281e9-108">Designer provides the **Set Breakpoints** dialog box, in which you can set breakpoints by enabling break conditions and specifying the number of times a breakpoint can occur before the execution of the package is suspended.</span></span> <span data-ttu-id="281e9-109">ブレークポイントは、パッケージ レベル、または個別のコンポーネントのレベルで有効にできます。</span><span class="sxs-lookup"><span data-stu-id="281e9-109">Breakpoints can be enabled at the package level, or at the level of the individual component.</span></span> <span data-ttu-id="281e9-110">タスクまたはコンテナー レベルでブレークの条件を有効にすると、 **[制御フロー]** タブのデザイン画面上にあるタスクまたはコンテナーの隣に、ブレークポイントのアイコンが表示されます。パッケージ レベルでブレークの条件を有効にすると、 **[制御フロー]** タブのラベル上にブレークポイントのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-110">If break conditions are enabled at the task or container level, the breakpoint icon appears next to the task or container on the design surface of the **Control Flow** tab. If the break conditions are enabled on the package, the breakpoint icon appears on the label of the **Control Flow** tab.</span></span>

 <span data-ttu-id="281e9-111">ブレークポイントにヒットすると、ブレークポイントのアイコンが変化し、ブレークポイントの発生元を識別できます。</span><span class="sxs-lookup"><span data-stu-id="281e9-111">When a breakpoint is hit, the breakpoint icon changes to help you identify the source of the breakpoint.</span></span> <span data-ttu-id="281e9-112">ブレークポイントは、パッケージの実行時に追加、削除、および変更できます。</span><span class="sxs-lookup"><span data-stu-id="281e9-112">You can add, delete, and change breakpoints when the package is running.</span></span>

 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="281e9-113">ではブレークの条件が 10 件用意されており、すべてのタスクとコンテナーで有効にできます。</span><span class="sxs-lookup"><span data-stu-id="281e9-113">provides ten break conditions that you can enable on all tasks and containers.</span></span> <span data-ttu-id="281e9-114">**[ブレークポイントの設定]** ダイアログ ボックスでは、次の条件に基づいてブレークポイントを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="281e9-114">In the **Set Breakpoints** dialog box, you can enable breakpoints on the following conditions:</span></span>

|<span data-ttu-id="281e9-115">ブレークの条件</span><span class="sxs-lookup"><span data-stu-id="281e9-115">Break condition</span></span>|<span data-ttu-id="281e9-116">説明</span><span class="sxs-lookup"><span data-stu-id="281e9-116">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="281e9-117">タスクまたはコンテナーが `OnPreExecute` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-117">When the task or container receives the `OnPreExecute` event.</span></span>|<span data-ttu-id="281e9-118">タスクが実行される直前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-118">Called when a task is about to execute.</span></span> <span data-ttu-id="281e9-119">このイベントは、タスクまたはコンテナーが実行される直前に、タスクまたはコンテナーから発生します。</span><span class="sxs-lookup"><span data-stu-id="281e9-119">This event is raised by a task or a container immediately before it runs.</span></span>|
|<span data-ttu-id="281e9-120">タスクまたはコンテナーが `OnPostExecute` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-120">When the task or container receives the `OnPostExecute` event.</span></span>|<span data-ttu-id="281e9-121">タスクの実行ロジックが完了した直後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-121">Called immediately after the execution logic of the task finishes.</span></span> <span data-ttu-id="281e9-122">このイベントは、タスクまたはコンテナーが実行された直後に、タスクまたはコンテナーから発生します。</span><span class="sxs-lookup"><span data-stu-id="281e9-122">This event is raised by a task or container immediately after it runs.</span></span>|
|<span data-ttu-id="281e9-123">タスクまたはコンテナーが `OnError` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-123">When the task or container receives the `OnError` event.</span></span>|<span data-ttu-id="281e9-124">エラーが発生すると、タスクまたはコンテナーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-124">Called by a task or container when an error occurs.</span></span>|
|<span data-ttu-id="281e9-125">タスクまたはコンテナーが `OnWarning` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-125">When the task or container receives the `OnWarning` event.</span></span>|<span data-ttu-id="281e9-126">タスクでエラーは発生していないが、警告が確認された状態にあるときに、呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-126">Called when the task is in a state that does not justify an error, but does warrant a warning.</span></span>|
|<span data-ttu-id="281e9-127">タスクまたはコンテナーが `OnInformation` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-127">When the task or container receives the `OnInformation` event.</span></span>|<span data-ttu-id="281e9-128">タスクから情報が提供される必要があるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-128">Called when the task is required to provide information.</span></span>|
|<span data-ttu-id="281e9-129">タスクまたはコンテナーが `OnTaskFailed` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-129">When the task or container receives the `OnTaskFailed` event.</span></span>|<span data-ttu-id="281e9-130">タスク ホストが失敗したとき、タスク ホストによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-130">Called by the task host when it fails.</span></span>|
|<span data-ttu-id="281e9-131">タスクまたはコンテナーが `OnProgress` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-131">When the task or container receives the `OnProgress` event.</span></span>|<span data-ttu-id="281e9-132">タスクの実行の進行状況を更新するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-132">Called to update progress about task execution.</span></span>|
|<span data-ttu-id="281e9-133">タスクまたはコンテナーが `OnQueryCancel` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-133">When the task or container receives the `OnQueryCancel` event.</span></span>|<span data-ttu-id="281e9-134">タスク処理の実行をキャンセルできる場合、任意のタイミングで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-134">Called at any time in task processing when you can cancel execution.</span></span>|
|<span data-ttu-id="281e9-135">タスクまたはコンテナーが `OnVariableValueChanged` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-135">When the task or container receives the `OnVariableValueChanged` event.</span></span>|<span data-ttu-id="281e9-136">変数の値が変更されたとき、 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイムによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-136">Called by the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime when the value of a variable changes.</span></span> <span data-ttu-id="281e9-137">このイベントを発生させるには、変数の RaiseChangeEvent をに設定する必要があり `true` ます。</span><span class="sxs-lookup"><span data-stu-id="281e9-137">The RaiseChangeEvent of the variable must be set to `true` to raise this event.</span></span><br /><br /> <span data-ttu-id="281e9-138">**&#42;&#42; 警告 &#42;&#42;** このブレークポイントに関連付けられている変数は、**コンテナー** スコープで定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="281e9-138">**&#42;&#42; Warning &#42;&#42;** The variable associated with this breakpoint must be defined at the **container** scope.</span></span> <span data-ttu-id="281e9-139">この変数がパッケージ スコープで定義されると、ブレークポイントにヒットしません。</span><span class="sxs-lookup"><span data-stu-id="281e9-139">If the variable is defined at the package scope, the breakpoint does not get hit.</span></span>|
|<span data-ttu-id="281e9-140">タスクまたはコンテナーが `OnCustomEvent` イベントを受け取ったとき</span><span class="sxs-lookup"><span data-stu-id="281e9-140">When the task or container receives the `OnCustomEvent` event.</span></span>|<span data-ttu-id="281e9-141">タスクによって定義されたカスタム イベントを起動するため、タスクによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-141">Called by tasks to raise custom task-defined events.</span></span>|

 <span data-ttu-id="281e9-142">一部のタスクとコンテナーには、すべてのタスクとコンテナーで使用できるブレークの条件以外に、ブレークポイントを設定するための特殊なブレーク条件が含まれています。</span><span class="sxs-lookup"><span data-stu-id="281e9-142">In addition to the break conditions available to all tasks and containers, some tasks and containers include special break conditions for setting breakpoints.</span></span> <span data-ttu-id="281e9-143">たとえば、For ループ コンテナーでは、ループの各反復処理の開始点で実行を中断するブレークポイントを設定するための、ブレークの条件を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="281e9-143">For example, you can enable a break condition on the For Loop container that sets a breakpoint that suspends execution at the start of each iteration of the loop.</span></span>

 <span data-ttu-id="281e9-144">ブレークポイントをさらに柔軟に使用し、機能を強化するには、次のオプションを指定してブレークポイントの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="281e9-144">To add flexibility and power to a breakpoint, you can modify the behavior of a breakpoint by specifying the following options:</span></span>

-   <span data-ttu-id="281e9-145">ヒット カウント。実行が中断するまでにブレーク条件に到達する最大回数です。</span><span class="sxs-lookup"><span data-stu-id="281e9-145">The hit count, or the maximum number of times that a break condition occurs before the execution is suspended.</span></span>

-   <span data-ttu-id="281e9-146">ヒット カウントの種類。ブレーク条件によってブレークポイントがトリガーされるタイミングを指定するルールです。</span><span class="sxs-lookup"><span data-stu-id="281e9-146">The hit count type, or the rule that specifies when the break condition triggers the breakpoint.</span></span>

 <span data-ttu-id="281e9-147">[常に行う] 以外のヒット カウントの種類では、そのヒット カウントによってさらに限定されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-147">The hit count types, except for the Always type, are further qualified by the hit count.</span></span> <span data-ttu-id="281e9-148">たとえば、種類が [ヒット カウント (等しい)] でヒット カウントが 5 の場合、ブレーク条件が 6 回発生した時点で実行は中断されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-148">For example, if the type is "Hit count equals" and the hit count is 5, execution is suspended on the sixth occurrence of the break condition.</span></span>

 <span data-ttu-id="281e9-149">次の表では、ヒット カウントの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="281e9-149">The following table describes the hit count types.</span></span>

|<span data-ttu-id="281e9-150">ヒット カウントの種類</span><span class="sxs-lookup"><span data-stu-id="281e9-150">Hit count type</span></span>|<span data-ttu-id="281e9-151">説明</span><span class="sxs-lookup"><span data-stu-id="281e9-151">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="281e9-152">Always (常に)</span><span class="sxs-lookup"><span data-stu-id="281e9-152">Always</span></span>|<span data-ttu-id="281e9-153">ブレークポイントにヒットすると、常に実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-153">Execution is always suspended when the breakpoint is hit.</span></span>|
|<span data-ttu-id="281e9-154">ヒット カウント (等しい)</span><span class="sxs-lookup"><span data-stu-id="281e9-154">Hit count equals</span></span>|<span data-ttu-id="281e9-155">ブレークポイントの発生回数がヒット カウントと等しくなると実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-155">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|
|<span data-ttu-id="281e9-156">ヒット カウント (より大きいまたは等しい)</span><span class="sxs-lookup"><span data-stu-id="281e9-156">Hit count greater than or equal to</span></span>|<span data-ttu-id="281e9-157">ブレークポイントの発生回数がヒット カウント以上になると実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-157">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|
|<span data-ttu-id="281e9-158">ヒット カウント (倍数)</span><span class="sxs-lookup"><span data-stu-id="281e9-158">Hit count multiple</span></span>|<span data-ttu-id="281e9-159">ヒット カウントの倍数だけブレークポイントが発生すると実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-159">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="281e9-160">たとえば、このオプションを 5 に設定すると、実行は 5 回ごとに中断されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-160">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|

#### <a name="to-set-breakpoints"></a><span data-ttu-id="281e9-161">ブレークポイントを設定するには</span><span class="sxs-lookup"><span data-stu-id="281e9-161">To set breakpoints</span></span>

-   [<span data-ttu-id="281e9-162">タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする</span><span class="sxs-lookup"><span data-stu-id="281e9-162">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>](../debug-a-package-by-setting-breakpoints-on-a-task-or-a-container.md)

## <a name="progress-reporting"></a><span data-ttu-id="281e9-163">進行状況レポート</span><span class="sxs-lookup"><span data-stu-id="281e9-163">Progress Reporting</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="281e9-164">デザイナーには、2 種類の進行状況レポート機能が含まれています。1 つは **[制御フロー]** タブのデザイン画面上の色分けで、もう 1 つは **[進行状況]** タブ上の進行状況メッセージです。</span><span class="sxs-lookup"><span data-stu-id="281e9-164">Designer includes two types of progress reporting: color-coding on the design surface of the **Control Flow** tab, and progress messages on the **Progress** tab.</span></span>

 <span data-ttu-id="281e9-165">パッケージを実行すると、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでは、各タスクまたはコンテナーが実行状態を示す色で表示され、進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="281e9-165">When you run a package, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer depicts execution progress by displaying each task or container using a color that indicates execution status.</span></span> <span data-ttu-id="281e9-166">この色により、要素が実行の待機中か、現在実行中か、正常に完了したか、または正しく終了しなかったか、などがわかります。</span><span class="sxs-lookup"><span data-stu-id="281e9-166">You can tell by its color whether the element is waiting to run, currently running, has completed successfully, or has ended unsuccessfully.</span></span> <span data-ttu-id="281e9-167">パッケージの実行を停止すると、表示は色分けされなくなります。</span><span class="sxs-lookup"><span data-stu-id="281e9-167">After you stop package execution, the color-coding disappears.</span></span>

 <span data-ttu-id="281e9-168">次の表では、実行状態を示す色について説明します。</span><span class="sxs-lookup"><span data-stu-id="281e9-168">The following table describes the colors that are used to depict execution status.</span></span>

|<span data-ttu-id="281e9-169">Color</span><span class="sxs-lookup"><span data-stu-id="281e9-169">Color</span></span>|<span data-ttu-id="281e9-170">実行状態</span><span class="sxs-lookup"><span data-stu-id="281e9-170">Execution status</span></span>|
|-----------|----------------------|
|<span data-ttu-id="281e9-171">グレー</span><span class="sxs-lookup"><span data-stu-id="281e9-171">Gray</span></span>|<span data-ttu-id="281e9-172">実行の待機中です。</span><span class="sxs-lookup"><span data-stu-id="281e9-172">Waiting to run</span></span>|
|<span data-ttu-id="281e9-173">黄</span><span class="sxs-lookup"><span data-stu-id="281e9-173">Yellow</span></span>|<span data-ttu-id="281e9-174">実行中</span><span class="sxs-lookup"><span data-stu-id="281e9-174">Running</span></span>|
|<span data-ttu-id="281e9-175">[緑]</span><span class="sxs-lookup"><span data-stu-id="281e9-175">Green</span></span>|<span data-ttu-id="281e9-176">正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="281e9-176">Ran successfully</span></span>|
|<span data-ttu-id="281e9-177">強調表示</span><span class="sxs-lookup"><span data-stu-id="281e9-177">highlighted</span></span>|<span data-ttu-id="281e9-178">実行されましたがエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="281e9-178">Ran with errors</span></span>|

 <span data-ttu-id="281e9-179">**[進行状況]** タブには、タスクとコンテナーが実行順に一覧表示され、それらの開始時刻と終了時刻、警告、およびエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-179">The **Progress** tab lists tasks and containers in execution order and includes the start and finish times, warnings, and error messages.</span></span> <span data-ttu-id="281e9-180">パッケージの実行を停止すると、 **[その実行結果]** タブに進行に関する情報が表示され、そのまま使用できます。</span><span class="sxs-lookup"><span data-stu-id="281e9-180">After you stop package execution, the progress information remains available on the **Execution Results** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="281e9-181">**[進行状況]** タブでのメッセージの表示を有効または無効にするには、 **[SSIS]** メニューの **[進行状況レポートのデバッグ]** オプションを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="281e9-181">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

 <span data-ttu-id="281e9-182">次の図は、 **[進行状況]** タブを示しています。</span><span class="sxs-lookup"><span data-stu-id="281e9-182">The following diagram shows the **Progress** tab.</span></span>

 <span data-ttu-id="281e9-183">![SSIS デザイナーの [進行状況] タブ](../media/mw-dtsflow04.gif "SSIS デザイナーの [進行状況] タブ")</span><span class="sxs-lookup"><span data-stu-id="281e9-183">![Progress tab of SSIS Designer](../media/mw-dtsflow04.gif "Progress tab of SSIS Designer")</span></span>

## <a name="debug-windows"></a><span data-ttu-id="281e9-184">デバッグ ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="281e9-184">Debug Windows</span></span>
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="281e9-185">には、ブレークポイントの処理、およびブレークポイントが含まれるパッケージのデバッグに使用できる多数のウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="281e9-185">includes many windows that you can use to work with breakpoints, and to debug packages that contain breakpoints.</span></span> <span data-ttu-id="281e9-186">各ウィンドウの詳細については、ウィンドウを開いて F1 キーを押し、目的のウィンドウのヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="281e9-186">To learn more about each window, open the window, and then press F1 to display Help for the window.</span></span>

 <span data-ttu-id="281e9-187">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でこれらのウィンドウを開くには、 **[デバッグ]** メニューをクリックし、 **[ウィンドウ]** をポイントします。次に、 **[ブレークポイント]** 、 **[出力]** 、または **[イミディエイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281e9-187">To open these windows in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], click the **Debug** menu, point to **Windows**, and then click **Breakpoints**, **Output**, or **Immediate**.</span></span>

 <span data-ttu-id="281e9-188">次の表は、各ウィンドウについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="281e9-188">The following table describes the windows.</span></span>

|<span data-ttu-id="281e9-189">ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="281e9-189">Window</span></span>|<span data-ttu-id="281e9-190">説明</span><span class="sxs-lookup"><span data-stu-id="281e9-190">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="281e9-191">ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="281e9-191">Breakpoints</span></span>|<span data-ttu-id="281e9-192">パッケージ内のブレークポイントを一覧表示し、ブレークポイントの有効化および削除のオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="281e9-192">Lists the breakpoints in a package and provides options to enable and delete breakpoints.</span></span>|
|<span data-ttu-id="281e9-193">出力</span><span class="sxs-lookup"><span data-stu-id="281e9-193">Output</span></span>|<span data-ttu-id="281e9-194">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]の機能に関する状態メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="281e9-194">Displays status messages for features in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>|
|<span data-ttu-id="281e9-195">即時</span><span class="sxs-lookup"><span data-stu-id="281e9-195">Immediate</span></span>|<span data-ttu-id="281e9-196">式をデバッグして評価し、変数の値を出力するのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="281e9-196">Used to debug and evaluate expressions and print variable values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="281e9-197">参照</span><span class="sxs-lookup"><span data-stu-id="281e9-197">See Also</span></span>
 [<span data-ttu-id="281e9-198">パッケージ開発のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="281e9-198">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)


