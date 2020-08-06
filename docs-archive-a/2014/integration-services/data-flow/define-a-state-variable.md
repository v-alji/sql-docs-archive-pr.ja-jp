---
title: 状態変数の定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45d66152-883a-49a7-a877-2e8ab45f8f79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5214b3512ea0113d1abace61a76033e5531ac99f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742461"
---
# <a name="define-a-state-variable"></a><span data-ttu-id="e3150-102">状態変数の定義</span><span class="sxs-lookup"><span data-stu-id="e3150-102">Define a State Variable</span></span>
  <span data-ttu-id="e3150-103">この手順では、CDC 状態が格納されるパッケージ変数を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3150-103">This procedure describes how to define a package variable where the CDC state is stored.</span></span>  
  
 <span data-ttu-id="e3150-104">CDC 状態変数は CDC 制御タスクによって読み込まれ、初期化され、更新されます。また、CDC ソース データ フロー コンポーネントによって使用され、変更レコードの現在の処理範囲が決まります。</span><span class="sxs-lookup"><span data-stu-id="e3150-104">The CDC state variable is loaded, initialized, and updated by the CDC Control task and is used by the CDC Source data flow component to determine the current processing range for change records.</span></span> <span data-ttu-id="e3150-105">CDC 状態変数は、CDC 制御タスクおよび CDC ソースに共通のコンテナーで定義できます。</span><span class="sxs-lookup"><span data-stu-id="e3150-105">The CDC state variable can be defined on any container common to the CDC Control task and the CDC source.</span></span> <span data-ttu-id="e3150-106">これはパッケージ レベルですが、ループ コンテナーのような他のコンテナーに対しても設定できます。</span><span class="sxs-lookup"><span data-stu-id="e3150-106">This may be at the package level but may also be on other containers such as a loop container.</span></span>  
  
 <span data-ttu-id="e3150-107">CDC 状態変数の値を手動で変更することは推奨されませんが、その内容を理解しておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="e3150-107">Manually modifying the CDC state variable value is not recommended, however it can be useful to understand its contents.</span></span>  
  
 <span data-ttu-id="e3150-108">次の表に、CDC 状態変数値の各要素の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-108">The following table provides a high-level description of the components of the CDC state variable value.</span></span>  
  
|<span data-ttu-id="e3150-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e3150-109">Component</span></span>|<span data-ttu-id="e3150-110">説明</span><span class="sxs-lookup"><span data-stu-id="e3150-110">Description</span></span>|  
|---------------|-----------------|  
|`<state-name>`|<span data-ttu-id="e3150-111">現在の CDC 状態の名前です。</span><span class="sxs-lookup"><span data-stu-id="e3150-111">This is the name of the current CDC state.</span></span>|  
|`CS`|<span data-ttu-id="e3150-112">現在の処理範囲の始点 (Current Start) を示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-112">This marks the current processing range start point (Current Start).</span></span>|  
|`<cs-lsn>`|<span data-ttu-id="e3150-113">前回の CDC 実行で処理された最後のログ シーケンス番号 (LSN) です。</span><span class="sxs-lookup"><span data-stu-id="e3150-113">This is the last (Log Sequence Number) LSN processed in the previous CDC run.</span></span>|  
|`CE`|<span data-ttu-id="e3150-114">現在の処理範囲の終点 (Current End) を示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-114">This marks the current processing range end point (Current End).</span></span> <span data-ttu-id="e3150-115">CDC 状態に CE 要素が存在するかどうかにより、CDC パッケージが現在処理中であるか、または CDC 処理範囲が完全に処理される前に CDC パッケージが失敗したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="e3150-115">The presence of the CE component in the CDC state is an indication that either a CDC package is currently processing or that a CDC package failed before fully processing its CDC processing range.</span></span>|  
|`<ce-lsn>`|<span data-ttu-id="e3150-116">現在の CDC 実行で処理される最後の LSN です。</span><span class="sxs-lookup"><span data-stu-id="e3150-116">This is the last LSN to be processed in the current CDC Run.</span></span> <span data-ttu-id="e3150-117">処理対象の最後のシーケンス番号は最大値 (0xFFF...) であることが常に想定されます。</span><span class="sxs-lookup"><span data-stu-id="e3150-117">It is always assumed that the last sequence number to be processed is the maximum (0xFFF...).</span></span>|  
|`IR`|<span data-ttu-id="e3150-118">初期処理範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-118">This marks the initial processing range.</span></span>|  
|`<ir-start>`|<span data-ttu-id="e3150-119">初期読み込みが開始した直前の変更の LSN です。</span><span class="sxs-lookup"><span data-stu-id="e3150-119">This is an LSN of a change just before the initial load began.</span></span>|  
|`<ir-end>`|<span data-ttu-id="e3150-120">初期読み込みが終了した直後の変更の LSN です。</span><span class="sxs-lookup"><span data-stu-id="e3150-120">This is an LSN of a change just after the initial load ended.</span></span>|  
|`TS`|<span data-ttu-id="e3150-121">CDC 状態の最後の更新のタイムスタンプを示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-121">This marks the timestamp for the last CDC state update.</span></span>|  
|**\<timestamp>**|<span data-ttu-id="e3150-122">64 ビットの System.DateTime.UtcNow プロパティの 10 進数表記です。</span><span class="sxs-lookup"><span data-stu-id="e3150-122">This is a decimal representation of the 64-bit, System.DateTime.UtcNow property.</span></span>|  
|`ER`|<span data-ttu-id="e3150-123">直前の操作が失敗した場合に表示され、エラーの原因の簡単な説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e3150-123">This appears when the last operation failed and includes a short description of the cause of the error.</span></span> <span data-ttu-id="e3150-124">この要素が存在する場合は、常に最後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3150-124">If this component is present, it will always appear last.</span></span>|  
|`<short-error-text>`|<span data-ttu-id="e3150-125">エラーの簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="e3150-125">This is the short error description.</span></span>|  
  
 <span data-ttu-id="e3150-126">LSN とシーケンス番号はそれぞれ、Binary(10) の LSN 値を表す最大 20 桁の 16 進数文字列としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="e3150-126">The LSNs and sequence numbers are each encoded as a hexadecimal string of up to 20 digits representing the LSN value of Binary(10).</span></span>  
  
 <span data-ttu-id="e3150-127">次の表に、使用可能な CDC 状態値を示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-127">The following table describes the possible CDC state values.</span></span>  
  
|<span data-ttu-id="e3150-128">State</span><span class="sxs-lookup"><span data-stu-id="e3150-128">State</span></span>|<span data-ttu-id="e3150-129">説明</span><span class="sxs-lookup"><span data-stu-id="e3150-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3150-130">(INITIAL)</span><span class="sxs-lookup"><span data-stu-id="e3150-130">(INITIAL)</span></span>|<span data-ttu-id="e3150-131">現在の CDC グループでパッケージが実行される前の初期状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-131">This is the initial state before the any package was run on the current CDC group.</span></span> <span data-ttu-id="e3150-132">CDC 状態が空のときの状態でもあります。</span><span class="sxs-lookup"><span data-stu-id="e3150-132">This is also the state when the CDC state is empty.</span></span>|  
|<span data-ttu-id="e3150-133">ILSTART (Initial Load Started)</span><span class="sxs-lookup"><span data-stu-id="e3150-133">ILSTART (Initial Load Started)</span></span>|<span data-ttu-id="e3150-134">CDC 制御タスクに対する `MarkInitialLoadStart` 操作の呼び出し後、初期読み込みパッケージが開始したときの状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-134">This is the state when the initial load package starts, after the `MarkInitialLoadStart` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="e3150-135">ILEND (Initial Load Ended)</span><span class="sxs-lookup"><span data-stu-id="e3150-135">ILEND (Initial Load Ended)</span></span>|<span data-ttu-id="e3150-136">CDC 制御タスクに対する `MarkInitialLoadEnd` 操作の呼び出し後、初期読み込みパッケージが正常に終了したときの状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-136">This is the state when the initial load package ends successfully, after the `MarkInitialLoadEnd` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="e3150-137">ILUPDATE (Initial Load Update)</span><span class="sxs-lookup"><span data-stu-id="e3150-137">ILUPDATE (Initial Load Update)</span></span>|<span data-ttu-id="e3150-138">初期読み込みの後にトリクル フィード更新パッケージが実行され、まだ初期処理範囲を処理しているときの状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-138">This is the state on the runs of the trickle feed update package following the initial load, while still processing the initial processing range.</span></span> <span data-ttu-id="e3150-139">CDC 制御タスクに対する `GetProcessingRange` 操作の呼び出し後に、この状態になります。</span><span class="sxs-lookup"><span data-stu-id="e3150-139">This is after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="e3150-140">__$reprocessing 列を使用している場合は、既にターゲットに存在する行をパッケージが再処理している可能性があることを示す 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e3150-140">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="e3150-141">TFEND (Trickle-Feed Update Ended)</span><span class="sxs-lookup"><span data-stu-id="e3150-141">TFEND (Trickle-Feed Update Ended)</span></span>|<span data-ttu-id="e3150-142">定期的な CDC の実行で期待される状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-142">This is the state expected for regular CDC runs.</span></span> <span data-ttu-id="e3150-143">前の実行が正常に完了していることと、新しい実行を新しい処理範囲で開始できることを表します。</span><span class="sxs-lookup"><span data-stu-id="e3150-143">It indicates that the previous run completed successfully and that a new run with a new processing range can be started.</span></span>|  
|<span data-ttu-id="e3150-144">TFSTART</span><span class="sxs-lookup"><span data-stu-id="e3150-144">TFSTART</span></span>|<span data-ttu-id="e3150-145">CDC 制御タスクに対する `GetProcessingRange` 操作の呼び出し後、トリクル フィード更新パッケージの後続実行を行ったときの状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-145">This is the state on a non-initial run of the trickle feed update package, after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="e3150-146">定期的な CDC の実行を開始したものの、まだ完了していないことを表します (`MarkProcessedRange`)。</span><span class="sxs-lookup"><span data-stu-id="e3150-146">This indicates that a regular CDC run is started but has not finished or has not yet finished, cleanly (`MarkProcessedRange`).</span></span>|  
|<span data-ttu-id="e3150-147">TFREDO (Reprocessing Trickle-Feed Updates)</span><span class="sxs-lookup"><span data-stu-id="e3150-147">TFREDO (Reprocessing Trickle-Feed Updates)</span></span>|<span data-ttu-id="e3150-148">TFSTART の後に `GetProcessingRange` が行われたときの状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-148">This is the state on a `GetProcessingRange` that occurs after TFSTART.</span></span> <span data-ttu-id="e3150-149">前の実行が正常に完了しなかったことを表します。</span><span class="sxs-lookup"><span data-stu-id="e3150-149">This indicates that the previous run did not complete successfully.</span></span><br /><br /> <span data-ttu-id="e3150-150">__$reprocessing 列を使用している場合は、既にターゲットに存在する行をパッケージが再処理している可能性があることを示す 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e3150-150">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="e3150-151">ERROR</span><span class="sxs-lookup"><span data-stu-id="e3150-151">ERROR</span></span>|<span data-ttu-id="e3150-152">CDC グループはエラー状態です。</span><span class="sxs-lookup"><span data-stu-id="e3150-152">The CDC group is in an ERROR state.</span></span>|  
  
 <span data-ttu-id="e3150-153">次に、CDC 状態変数値の例を示します。</span><span class="sxs-lookup"><span data-stu-id="e3150-153">The following are examples of CDC state variable values.</span></span>  
  
-   <span data-ttu-id="e3150-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="e3150-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="e3150-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="e3150-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="e3150-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span><span class="sxs-lookup"><span data-stu-id="e3150-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span></span>  
  
-   <span data-ttu-id="e3150-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span><span class="sxs-lookup"><span data-stu-id="e3150-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span></span>  
  
-   <span data-ttu-id="e3150-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span><span class="sxs-lookup"><span data-stu-id="e3150-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span></span>  
  
### <a name="to-define-a-cdc-state-variable"></a><span data-ttu-id="e3150-159">CDC 状態変数を定義するには</span><span class="sxs-lookup"><span data-stu-id="e3150-159">To define a CDC state variable</span></span>  
  
1.  <span data-ttu-id="e3150-160">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、変数を定義する必要がある CDC フローを含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="e3150-160">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package that has the CDC flow where you need to define the variable.</span></span>  
  
2.  <span data-ttu-id="e3150-161">**[パッケージ エクスプ ローラー]** タブをクリックして、新しい変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="e3150-161">Click the **Package Explorer** tab, and add a new variable.</span></span>  
  
3.  <span data-ttu-id="e3150-162">変数に、状態変数として識別できる名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e3150-162">Give the variable a name that you can recognize as your state variable.</span></span>  
  
4.  <span data-ttu-id="e3150-163">変数を **String** データ型に設定します。</span><span class="sxs-lookup"><span data-stu-id="e3150-163">Give the variable a **String** data type.</span></span>  
  
 <span data-ttu-id="e3150-164">定義するときに、変数に値を設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="e3150-164">Do not give the variable a value as part of its definition.</span></span> <span data-ttu-id="e3150-165">値は、CDC 制御タスクで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3150-165">The value must be set by the CDC Control task.</span></span>  
  
 <span data-ttu-id="e3150-166">**[状態の自動保持]** を指定して CDC 制御タスクを使用する予定の場合、CDC 状態変数は指定するデータベース状態テーブルから読み取られ、値の変更時に同じテーブルの値が更新されます。</span><span class="sxs-lookup"><span data-stu-id="e3150-166">If you plan to use the CDC Control task with **Automatic State Persistence**, the CDC State variable will be read from the database state table you specify and will be updated back to that same table when its value changes.</span></span> <span data-ttu-id="e3150-167">状態テーブルの詳細については、「 [CDC Control Task](../control-flow/cdc-control-task.md)」および「 [CDC Control Task Editor](../cdc-control-task-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3150-167">For more information about the State table, see [CDC Control Task](../control-flow/cdc-control-task.md)and [CDC Control Task Editor](../cdc-control-task-editor.md).</span></span>  
  
 <span data-ttu-id="e3150-168">[状態の自動保持] を指定して CDC 制御タスクを使用しない場合は、パッケージが最後に実行されたときに変数の値が保存された永続ストレージからその値を読み込み、現在の処理範囲の処理が終了したときに永続ストレージにその値を書き戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3150-168">If you are not using the CDC Control task with Automatic State Persistence then you must load the variable value from persistent storage where its value was saved the last time the package ran and to write it back to the persistent storage when the processing of the current processing range was completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3150-169">参照</span><span class="sxs-lookup"><span data-stu-id="e3150-169">See Also</span></span>  
 <span data-ttu-id="e3150-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span><span class="sxs-lookup"><span data-stu-id="e3150-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span></span>  
 [<span data-ttu-id="e3150-171">CDC 制御タスク エディター</span><span class="sxs-lookup"><span data-stu-id="e3150-171">CDC Control Task Editor</span></span>](../cdc-control-task-editor.md)  
  
  
