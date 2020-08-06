---
title: 変更データの準備ができているかどうかを判断する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],determining readiness
ms.assetid: 04935f35-96cc-4d70-a250-0fd326f8daff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e672440938e366e53ba150f65d7bcd6aed8a58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740213"
---
# <a name="determine-whether-the-change-data-is-ready"></a><span data-ttu-id="dc1ea-102">データの変更の準備ができているかどうかを判断する</span><span class="sxs-lookup"><span data-stu-id="dc1ea-102">Determine Whether the Change Data Is Ready</span></span>
  <span data-ttu-id="dc1ea-103">変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローにおいて、2 番目のタスクは、選択した間隔の変更データが準備できていることを確認することです。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the second task is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="dc1ea-104">選択したエンドポイントまでの変更が非同期キャプチャ プロセスでまだ一部処理されていない可能性があるため、この手順が必要となります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-104">This step is necessary because the asynchronous capture process might not yet have processed all the changes up to the selected endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc1ea-105">制御フローの最初のタスクは、変更間隔のエンドポイントを計算することです。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-105">The first task for the control flow is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="dc1ea-106">このタスクに関する詳細については、「 [変更データの間隔を指定する](specify-an-interval-of-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-106">For more information about this task, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span> <span data-ttu-id="dc1ea-107">制御フローをデザインするプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-107">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="understanding-the-components-of-the-solution"></a><span data-ttu-id="dc1ea-108">ソリューションのコンポーネントについて</span><span class="sxs-lookup"><span data-stu-id="dc1ea-108">Understanding the Components of the Solution</span></span>  
 <span data-ttu-id="dc1ea-109">このトピックで説明するソリューションでは、次の 4 つの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-109">The solution described in this topic uses 4 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="dc1ea-110">SQL 実行タスクの出力を繰り返し評価する For ループ コンテナー。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-110">A For Loop container that repeatedly evaluates the output of an Execute SQL Task.</span></span>  
  
-   <span data-ttu-id="dc1ea-111">変更データ キャプチャ プロセスによって保持されている特殊なテーブルに対してクエリを実行し、この情報を使用してデータが準備できているかどうかを判断する SQL 実行タスク。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-111">An Execute SQL task that queries special tables that the change data capture process maintains and then uses this information to determine whether data is ready.</span></span>  
  
-   <span data-ttu-id="dc1ea-112">データが準備できていない場合に処理の遅延を実装するコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-112">A component that implements a delay in processing when the data is not ready.</span></span> <span data-ttu-id="dc1ea-113">このコンポーネントは、スクリプト タスクまたは SQL 実行タスクのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-113">This can be either a Script task or an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="dc1ea-114">(省略可) SQL 実行タスクによってエラーまたはタイムアウト状態を示す値が返されたときにエラーまたはタイムアウトを報告するコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-114">Optionally, a component that reports an error or a timeout when the Execute SQL task returns a value that indicates an error or a timeout condition.</span></span>  
  
 <span data-ttu-id="dc1ea-115">これらのコンポーネントによって、いくつかのパッケージ変数の値が設定されるか読み取られ、ループ内およびパッケージの後続の実行フローが制御されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-115">These components set or read the values of several package variables to control the flow of execution inside the loop and later in the package.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="dc1ea-116">パッケージ変数を設定するには</span><span class="sxs-lookup"><span data-stu-id="dc1ea-116">To set up package variables</span></span>  
  
1.  <span data-ttu-id="dc1ea-117">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[変数]** ウィンドウで、次の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-118">SQL 実行タスクによって返される状態値を格納する整数データ型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-118">Create a variable with an integer data type to hold the status value returned by the Execute SQL task.</span></span>  
  
         <span data-ttu-id="dc1ea-119">この例では、初期値が 0 である DataReady という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-119">This example uses the variable name, DataReady, with an initial value of 0.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-120">データが準備できていない場合の遅延時間を格納する変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-120">Create a variable to hold the period of time to delay when data is not ready.</span></span> <span data-ttu-id="dc1ea-121">スクリプト タスクを使用して遅延を実装する場合、変数には整数データ型が格納されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-121">If you plan to use a Script task to implement the delay, the variable should have an integer data type integer.</span></span> <span data-ttu-id="dc1ea-122">WAITFOR ステートメントを実行する SQL 実行タスクを使用する場合、変数には文字列データ型が格納され、"00:00:10" などの値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-122">If you plan to use an Execute SQL task with a WAITFOR statement, the variable should have a string data type to accept values such as "00:00:10".</span></span>  
  
         <span data-ttu-id="dc1ea-123">この例では、初期値が 10 である DelaySeconds という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-123">This example uses the variable name, DelaySeconds, with an initial value of 10.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-124">ループの現在の反復を格納する整数データ型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-124">Create a variable with an integer data type to hold the current iteration of the loop.</span></span>  
  
         <span data-ttu-id="dc1ea-125">この例では、初期値が 0 である TimeoutCount という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-125">This example uses the variable name, TimeoutCount, with an initial value of 0.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-126">タイムアウト状態を報告する前にループでデータをテストする回数を指定する整数データ型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-126">Create a variable with an integer data type to specify the number of times that the loop should test for data before reporting a timeout condition.</span></span>  
  
         <span data-ttu-id="dc1ea-127">この例では、初期値が 20 である TimeoutCeiling という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-127">This example uses the variable name, TimeoutCeiling, with an initial value of 20.</span></span>  
  
    5.  <span data-ttu-id="dc1ea-128">(省略可) 変更データの最初の読み込みを示すために使用できる整数データ型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-128">(Optional) Create a variable with an integer data type that you can use to indicate the first load of change data.</span></span>  
  
         <span data-ttu-id="dc1ea-129">この例では、IntervalID という名前の変数を使用し、値が最初の読み込みを示す 0 であることだけをチェックします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-129">This example uses the variable name, IntervalID, and checks only for a value of 0 to indicate the initial load.</span></span>  
  
## <a name="configuring-a-for-loop-container"></a><span data-ttu-id="dc1ea-130">For ループ コンテナーの構成</span><span class="sxs-lookup"><span data-stu-id="dc1ea-130">Configuring a For Loop Container</span></span>  
 <span data-ttu-id="dc1ea-131">変数を設定したら、まず For ループ コンテナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-131">With the variables set, the For Loop container is the first component to be added.</span></span>  
  
#### <a name="to-configure-a-for-loop-container-to-wait-until-change-data-is-ready"></a><span data-ttu-id="dc1ea-132">変更データが準備できるまで待機するように For ループ コンテナーを構成するには</span><span class="sxs-lookup"><span data-stu-id="dc1ea-132">To configure a For Loop container to wait until change data is ready</span></span>  
  
1.  <span data-ttu-id="dc1ea-133">**デザイナーの** [制御フロー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブで、For ループ コンテナーを制御フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-133">On the **Control Flow** tab of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a For Loop container to the control flow.</span></span>  
  
2.  <span data-ttu-id="dc1ea-134">間隔のエンドポイントを計算する SQL 実行タスクを For ループ コンテナーに連結します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-134">Connect the Execute SQL Task that calculates the endpoints of the interval to the For Loop container.</span></span>  
  
3.  <span data-ttu-id="dc1ea-135">**[For ループ エディター]** で、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-135">In the **For Loop Editor**, select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-136">**[InitExpression]** に「 `@DataReady = 0`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-136">For **InitExpression**, enter `@DataReady = 0`.</span></span>  
  
         <span data-ttu-id="dc1ea-137">この式によって、ループ変数の初期値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-137">This expression sets the initial value of the loop variable.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-138">**[EvalExpression]** に「 `@DataReady == 0`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-138">For **EvalExpression**m, enter `@DataReady == 0`.</span></span>  
  
         <span data-ttu-id="dc1ea-139">この式が **False**と評価されると、実行がループの外に移り、増分読み込みが開始されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-139">When this expression evaluates to **False**, execution passes out of the loop and the incremental load starts.</span></span>  
  
## <a name="configuring-the-execute-sql-task-that-queries-for-change-data"></a><span data-ttu-id="dc1ea-140">変更データのクエリを実行する SQL 実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="dc1ea-140">Configuring the Execute SQL Task That Queries for Change Data</span></span>  
 <span data-ttu-id="dc1ea-141">For ループ コンテナー内に SQL 実行タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-141">Inside the For Loop container, you add an Execute SQL task.</span></span> <span data-ttu-id="dc1ea-142">このタスクでは、変更データ キャプチャ プロセスがデータベースに保持しているテーブルに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-142">This task queries the tables that the change data capture process maintains in the database.</span></span> <span data-ttu-id="dc1ea-143">このクエリの結果は、変更データが準備できているかどうかを示す状態値です。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-143">The result of this query is a status value that indicates whether the change data is ready.</span></span>  
  
 <span data-ttu-id="dc1ea-144">次の表の 1 列目は、サンプルの Transact-SQL クエリによって SQL 実行タスクから返される値を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-144">In the following table, the first column shows the values returned from the Execute SQL task by the sample Transact-SQL query.</span></span> <span data-ttu-id="dc1ea-145">2 列目は、その他のコンポーネントがこれらの値に応答する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-145">The second column shows how the other components respond to these values.</span></span>  
  
|<span data-ttu-id="dc1ea-146">戻り値</span><span class="sxs-lookup"><span data-stu-id="dc1ea-146">Return Value</span></span>|<span data-ttu-id="dc1ea-147">意味</span><span class="sxs-lookup"><span data-stu-id="dc1ea-147">Meaning</span></span>|<span data-ttu-id="dc1ea-148">Response</span><span class="sxs-lookup"><span data-stu-id="dc1ea-148">Response</span></span>|  
|------------------|-------------|--------------|  
|<span data-ttu-id="dc1ea-149">0</span><span class="sxs-lookup"><span data-stu-id="dc1ea-149">0</span></span>|<span data-ttu-id="dc1ea-150">変更データが準備できていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-150">Indicates that the change data is not ready.</span></span><br /><br /> <span data-ttu-id="dc1ea-151">選択した間隔の終了時点より後に変更データ キャプチャ レコードがありません。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-151">There are no change data capture records later than the ending point of the selected interval.</span></span>|<span data-ttu-id="dc1ea-152">遅延を実装するコンポーネントから実行が継続されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-152">Execution continues with the component that implements a delay.</span></span> <span data-ttu-id="dc1ea-153">その後、制御が For ループ コンテナーに戻り、返される値が 0 である限り引き続きコンテナーによって SQL 実行タスクがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-153">Then control returns to the For Loop container, which continues to check the Execute SQL task as long as the value returned is 0.</span></span>|  
|<span data-ttu-id="dc1ea-154">1</span><span class="sxs-lookup"><span data-stu-id="dc1ea-154">1</span></span>|<span data-ttu-id="dc1ea-155">間隔全体にわたって変更データがキャプチャされていないか、変更データが削除されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-155">Might indicate that the change data has not been captured for the complete interval, or that it has been deleted.</span></span> <span data-ttu-id="dc1ea-156">これは、エラー状態として扱われます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-156">This is treated as an error condition.</span></span><br /><br /> <span data-ttu-id="dc1ea-157">選択した間隔の開始時点より前に変更データ キャプチャ レコードがありません。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-157">There are no change data capture records earlier than the starting point of the selected interval</span></span>|<span data-ttu-id="dc1ea-158">エラーをログに記録するオプションのコンポーネントから実行が継続されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-158">Execution continues with the optional component that logs the error.</span></span>|  
|<span data-ttu-id="dc1ea-159">2</span><span class="sxs-lookup"><span data-stu-id="dc1ea-159">2</span></span>|<span data-ttu-id="dc1ea-160">データが準備できていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-160">Indicates that data is ready.</span></span><br /><br /> <span data-ttu-id="dc1ea-161">選択した間隔の開始時点より前にも終了時点より後にも変更データ キャプチャ レコードがあります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-161">There are change data capture records that are both earlier than the starting point and later than the ending point of the selected interval.</span></span>|<span data-ttu-id="dc1ea-162">実行が For ループ コンテナーの外に移り、増分読み込みが開始されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-162">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="dc1ea-163">3</span><span class="sxs-lookup"><span data-stu-id="dc1ea-163">3</span></span>|<span data-ttu-id="dc1ea-164">使用可能なすべての変更データの最初の読み込みを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-164">Indicates the initial load of all available change data.</span></span><br /><br /> <span data-ttu-id="dc1ea-165">この値は、このためだけに使用される特殊なパッケージ変数から条件ロジックによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-165">The conditional logic obtains this value from a special package variable that is used only for this purpose.</span></span>|<span data-ttu-id="dc1ea-166">実行が For ループ コンテナーの外に移り、増分読み込みが開始されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-166">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="dc1ea-167">5</span><span class="sxs-lookup"><span data-stu-id="dc1ea-167">5</span></span>|<span data-ttu-id="dc1ea-168">TimeoutCeiling に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-168">Indicates that the TimeoutCeiling has been reached.</span></span><br /><br /> <span data-ttu-id="dc1ea-169">指定された回数だけループでデータがテストされましたが、データはまだ使用できません。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-169">The loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="dc1ea-170">このテストまたは同様のテストを実行しないと、パッケージが無期限に実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-170">Without this test or a similar test, the package might run indefinitely.</span></span>|<span data-ttu-id="dc1ea-171">タイムアウトをログに記録するオプションのコンポーネントから実行が継続されます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-171">Execution continues with the optional component that logs the timeout.</span></span>|  
  
#### <a name="to-configure-an-execute-sql-task-to-query-whether-change-data-is-ready"></a><span data-ttu-id="dc1ea-172">変更データが準備できているかどうかをクエリするように SQL 実行タスクを構成するには</span><span class="sxs-lookup"><span data-stu-id="dc1ea-172">To configure an Execute SQL task to query whether change data is ready</span></span>  
  
1.  <span data-ttu-id="dc1ea-173">For ループ コンテナー内に SQL 実行タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-173">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="dc1ea-174">**[SQL 実行タスク エディター]** の **[全般]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-174">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-175">**[ResultSet]** で **[単一行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-175">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-176">ソース データベースへの有効な接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-176">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-177">**[SQLSourceType]** で **[直接入力]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-177">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-178">**[SQLStatement]** に、次の SQL ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-178">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @DataReady int, @TimeoutCount int  
  
        if not exists (select tran_end_time from cdc.lsn_time_mapping  
                where tran_end_time > ?  )  
            select @DataReady = 0  
        else  
            if ? = 0  
                select @DataReady = 3   
        else  
            if not exists (select tran_end_time from cdc.lsn_time_mapping  
                    where tran_end_time <= ? )  
                select @DataReady = 1   
        else  
            select @DataReady = 2  
  
        select @TimeoutCount = ?  
        if (@DataReady = 0)  
            select @TimeoutCount = @TimeoutCount + 1  
        else  
            select @TimeoutCount = 0  
  
        if (@TimeoutCount > ?)  
            select @DataReady = 5  
  
        select @DataReady as DataReady, @TimeoutCount as TimeoutCount  
  
        ```  
  
3.  <span data-ttu-id="dc1ea-179">**[SQL 実行タスク エディター]** の **[パラメーター マッピング]** ページで、次のマッピングを行います。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-179">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, make the following mappings:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-180">ExtractEndTime 変数をパラメーター 0 にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-180">Map the ExtractEndTime variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-181">IntervalID 変数をパラメーター 1 にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-181">Map the IntervalID variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-182">ExtractStartTime 変数をパラメーター 2 にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-182">Map the ExtractStartTime variable to parameter 2.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-183">TimeoutCount 変数をパラメーター 3 にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-183">Map the TimeoutCount variable to parameter 3.</span></span>  
  
    5.  <span data-ttu-id="dc1ea-184">TimeoutCeiling 変数をパラメーター 4 にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-184">Map the TimeoutCeiling variable to parameter 4.</span></span>  
  
4.  <span data-ttu-id="dc1ea-185">**[SQL 実行タスク エディター]** の **[結果セット]** ページで、DataReady の結果を DataReady 変数に、TimeoutCount の結果を TimeoutCount 変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-185">On the **Result Set** page of the **Execute SQL Task Editor**, map the DataReady result to the DataReady variable, and the TimeoutCount result to the TimeoutCount variable.</span></span>  
  
## <a name="waiting-until-the-change-data-is-ready"></a><span data-ttu-id="dc1ea-186">変更データが準備できるまでの待機</span><span class="sxs-lookup"><span data-stu-id="dc1ea-186">Waiting Until the Change Data Is Ready</span></span>  
 <span data-ttu-id="dc1ea-187">いくつかある方法のうちいずれかを使用して、変更データが準備できていない場合に遅延を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-187">You can use one of several methods to implement a delay when the change data is not ready.</span></span> <span data-ttu-id="dc1ea-188">次の 2 つの手順は、スクリプト タスクまたは SQL 実行タスクを使用して遅延を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-188">The following two procedures illustrate how to use a Script task or an Execute SQL task to implement the delay.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc1ea-189">発生するオーバーヘッドは、SQL 実行タスクよりも事前コンパイルしたスクリプトの方が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-189">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-a-script-task"></a><span data-ttu-id="dc1ea-190">スクリプト タスクを使用して遅延を実装するには</span><span class="sxs-lookup"><span data-stu-id="dc1ea-190">To implement a delay by using a Script task</span></span>  
  
1.  <span data-ttu-id="dc1ea-191">For ループ コンテナー内にスクリプト タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-191">Inside the For Loop container, add a Script task.</span></span>  
  
2.  <span data-ttu-id="dc1ea-192">変更データが準備できているかどうかを判断するためにクエリを実行する SQL 実行タスクを新しいスクリプト タスクに連結します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-192">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
3.  <span data-ttu-id="dc1ea-193">SQL 実行タスクをスクリプト タスクに連結する優先順位制約のために、 **[優先順位制約エディター]** を開いて次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-193">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-194">**[評価操作]** で **[式と制約]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-194">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-195">**[値]** で **[成功]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-195">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="dc1ea-196">制約値 **[成功]** は、前のタスクの成功を表します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-196">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="dc1ea-197">この場合は、SQL 実行タスクの成功を表します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-197">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-198">**[式]** に「 `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-198">For **Expression**, enter `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-199">**[論理 AND (すべての制約が True と評価される必要があります)** ] が選択されていない場合は、選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-199">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
4.  <span data-ttu-id="dc1ea-200">**[スクリプト タスク エディター]** の **[スクリプト]** ページの **[ReadOnlyVariables]** で、 **[User::DelaySeconds]** 整数変数を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-200">In the **Script Task Editor**, on the **Script** page, for **ReadOnlyVariables**, select the **User::DelaySeconds** integer variable from the list.</span></span>  
  
5.  <span data-ttu-id="dc1ea-201">**[スクリプト タスク エディター]** の **[スクリプト]** ページで、 **[スクリプトの編集]** をクリックしてスクリプト開発環境を開きます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-201">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="dc1ea-202">Main プロシージャに、次のいずれかのコード行を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-202">In the Main procedure, enter one of the following lines of code:</span></span>  
  
    -   <span data-ttu-id="dc1ea-203">C# でプログラミングしている場合は、次のコード行を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-203">If you are programming in C#, enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep((int)Dts.Variables["DelaySeconds"].Value * 1000);  
        ```  
  
         <span data-ttu-id="dc1ea-204">\- - または -</span><span class="sxs-lookup"><span data-stu-id="dc1ea-204">\- or -</span></span>  
  
    -   <span data-ttu-id="dc1ea-205">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]でプログラミングしている場合は、次のコード行を入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-205">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep(Ctype(Dts.Variables("DelaySeconds").Value, Integer) * 1000)  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="dc1ea-206">`Thread.Sleep` メソッドは、ミリ秒単位で指定される引数を想定しています。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-206">The `Thread.Sleep` method expects an argument that is specified in milliseconds.</span></span>  
  
7.  <span data-ttu-id="dc1ea-207">スクリプトの実行から `DtsExecResult.Success` を返す既定のコード行はそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-207">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
8.  <span data-ttu-id="dc1ea-208">スクリプト開発環境と **[スクリプト タスク エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-208">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-an-execute-sql-task"></a><span data-ttu-id="dc1ea-209">SQL 実行タスクを使用して遅延を実装するには</span><span class="sxs-lookup"><span data-stu-id="dc1ea-209">To implement a delay by using an Execute SQL task</span></span>  
  
1.  <span data-ttu-id="dc1ea-210">For ループ コンテナー内に SQL 実行タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-210">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="dc1ea-211">変更データが準備できているかどうかを判断するためにクエリを実行する SQL 実行タスクを新しい SQL 実行タスクに連結します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-211">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Execute SQL task.</span></span>  
  
3.  <span data-ttu-id="dc1ea-212">2 つの SQL 実行タスクを連結する優先順位制約のために、 **[優先順位制約エディター]** を開いて次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-212">For the precedence constraint that connects the two Execute SQL tasks, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-213">**[評価操作]** で **[式と制約]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-213">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-214">**[値]** で **[成功]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-214">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="dc1ea-215">制約値 **[成功]** は、前の SQL 実行タスクの成功を表します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-215">The constraint value of **Success** refers to the success of the previous Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-216">**[式]** に「 `@DataReady == 0`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-216">For **Expression**, enter `@DataReady == 0`.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-217">**[論理 AND (すべての制約が True と評価される必要があります)** ] が選択されていない場合は、選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-217">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="dc1ea-218">この選択により、制約と式の両方の条件が True であることが必要になります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-218">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
4.  <span data-ttu-id="dc1ea-219">**[SQL 実行タスク エディター]** の **[全般]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-219">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-220">**[ResultSet]** で **[単一行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-220">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-221">ソース データベースへの有効な接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-221">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-222">**[SQLSourceType]** で **[直接入力]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-222">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-223">**[SQLStatement]** に、次の SQL ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-223">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        WAITFOR DELAY ?  
  
        ```  
  
5.  <span data-ttu-id="dc1ea-224">エディターの **[パラメーター マッピング]** ページで、DelaySeconds 文字列変数をパラメーター 0 にマップします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-224">On the **Parameter Mapping** page of the editor, map the DelaySeconds string variable to parameter 0.</span></span>  
  
## <a name="handling-an-error-condition"></a><span data-ttu-id="dc1ea-225">エラー状態の処理</span><span class="sxs-lookup"><span data-stu-id="dc1ea-225">Handling an Error Condition</span></span>  
 <span data-ttu-id="dc1ea-226">必要に応じて、エラーまたはタイムアウト状態をログに記録するようにループ内に追加のコンポーネントを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-226">You can optionally configure an additional component inside the loop to log an error or a timeout condition:</span></span>  
  
-   <span data-ttu-id="dc1ea-227">このコンポーネントでは、DataReady 変数の値が 1 の場合にエラー状態をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-227">This component can log an error condition when the value of the DataReady variable = 1.</span></span> <span data-ttu-id="dc1ea-228">この値は、選択した間隔の開始前に使用可能な変更データがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-228">This value indicates that there is no available change data before the start of the selected interval.</span></span>  
  
-   <span data-ttu-id="dc1ea-229">このコンポーネントでは、TimeoutCeiling 変数の値に達した場合にタイムアウト状態をログに記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-229">This component can also log a timeout condition when the value of the TimeoutCeiling variable is reached.</span></span> <span data-ttu-id="dc1ea-230">この値は、指定された回数だけループでデータがテストされたが、データがまだ使用できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-230">This value indicates the loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="dc1ea-231">このテストまたは同様のテストを実行しないと、パッケージが無期限に実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-231">Without this test or a similar test, the package might run indefinitely.</span></span>  
  
#### <a name="to-configure-an-optional-script-task-to-log-an-error-condition"></a><span data-ttu-id="dc1ea-232">エラー状態をログに記録するようにオプションのスクリプト タスクを構成するには</span><span class="sxs-lookup"><span data-stu-id="dc1ea-232">To configure an optional Script task to log an error condition</span></span>  
  
1.  <span data-ttu-id="dc1ea-233">メッセージをログに書き込んでエラーまたはタイムアウトを報告する場合は、パッケージのログ記録を構成します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-233">If you want to report the error or timeout by writing a message to the log, configure logging for the package.</span></span> <span data-ttu-id="dc1ea-234">詳細については、「 [SQL Server Data Tools でパッケージのログ記録を有効にする](../enable-package-logging-in-sql-server-data-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-234">For more information, see [Enable Package Logging in SQL Server Data Tools](../enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
2.  <span data-ttu-id="dc1ea-235">For ループ コンテナー内にスクリプト タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-235">Inside the For Loop container, add a Script task.</span></span>  
  
3.  <span data-ttu-id="dc1ea-236">変更データが準備できているかどうかを判断するためにクエリを実行する SQL 実行タスクを新しいスクリプト タスクに連結します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-236">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
4.  <span data-ttu-id="dc1ea-237">SQL 実行タスクをスクリプト タスクに連結する優先順位制約のために、 **[優先順位制約エディター]** を開いて次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-237">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc1ea-238">**[評価操作]** で **[式と制約]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-238">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="dc1ea-239">**[値]** で **[成功]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-239">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="dc1ea-240">制約値 **[成功]** は、前のタスクの成功を表します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-240">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="dc1ea-241">この場合は、SQL 実行タスクの成功を表します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-241">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="dc1ea-242">**[式]** に「 `@DataReady == 1 || @DataReady == 5`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-242">For **Expression**, enter `@DataReady == 1 || @DataReady == 5`.</span></span>  
  
    4.  <span data-ttu-id="dc1ea-243">**[論理 AND (すべての制約が True と評価される必要があります)** ] が選択されていない場合は、選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-243">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="dc1ea-244">この選択により、制約と式の両方の条件が True であることが必要になります。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-244">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
5.  <span data-ttu-id="dc1ea-245">**[スクリプト タスク エディター]** の **[スクリプト]** ページの **[ReadOnlyVariables]** で、 **[User::DataReady]** および **[User::ExtractStartTime]** を一覧から選択し、それらの値をスクリプトに使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-245">In the **Script Task Editor**, on the **Script** page of the editor, for **ReadOnlyVariables**, select **User::DataReady** and **User::ExtractStartTime** from the list to make their values available to the script.</span></span>  
  
     <span data-ttu-id="dc1ea-246">特定のシステム変数 (System::PackageName など) の情報をログに書き込む情報に含める場合は、それらの変数も選択します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-246">If you want to include information from certain system variables (for example, System::PackageName) in the information that you write to the log, select those variables also.</span></span>  
  
6.  <span data-ttu-id="dc1ea-247">**[スクリプト タスク エディター]** の **[スクリプト]** ページで、 **[スクリプトの編集]** をクリックしてスクリプト開発環境を開きます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-247">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
7.  <span data-ttu-id="dc1ea-248">Main プロシージャに、`Dts.Log` メソッドを呼び出してエラーをログに記録するコードか、`Dts.Events` インターフェイスのいずれかのメソッドを呼び出してイベントを発生させるコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-248">In the Main procedure, enter code to log an error by calling the `Dts.Log` method, or to raise an event by calling one of the methods of the `Dts.Events` interface.</span></span> <span data-ttu-id="dc1ea-249">`Dts.TaskResult = Dts.Results.Failure`を返すことによってエラーをパッケージに通知します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-249">Inform the package of the error by returning `Dts.TaskResult = Dts.Results.Failure`.</span></span>  
  
     <span data-ttu-id="dc1ea-250">次の例は、メッセージをログに書き込む方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-250">The following sample shows how to write a message to the log.</span></span> <span data-ttu-id="dc1ea-251">詳細については、「 [スクリプト タスクでのログ記録](../extending-packages-scripting/task/logging-in-the-script-task.md)」、「 [スクリプト タスクでのイベントの発生](../extending-packages-scripting/task/raising-events-in-the-script-task.md)」、「 [スクリプト タスクから結果を返す](../extending-packages-scripting/task/returning-results-from-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-251">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md), [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md), and [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>  
  
    ```  
    ' User variables.  
    Dim dataReady As Integer = _  
      CType(Dts.Variables("DataReady").Value, Integer)  
    Dim extractStartTime As Date = _  
      CType(Dts.Variables("ExtractStartTime").Value, DateTime)  
  
    ' System variables.  
    Dim packageName As String = _  
      Dts.Variables("PackageName").Value.ToString()  
    Dim executionStartTime As Date = _  
      CType(Dts.Variables("StartTime").Value, DateTime)  
  
    Dim eventMessage As New System.Text.StringBuilder()  
  
    If dataReady = 1 OrElse dataReady = 5 Then  
  
      If dataReady = 1 Then  
        eventMessage.AppendLine("Start Time Error")  
      Else  
        eventMessage.AppendLine("Timeout Error")  
      End If  
  
      With eventMessage  
        .Append("The package ")  
        .Append(packageName)  
        .Append(" started at ")  
        .Append(executionStartTime.ToString())  
        .Append(" and ended at ")  
        .AppendLine(DateTime.Now().ToString())  
        If dataReady = 1 Then  
          .Append("The specified ExtractStartTime was ")  
          .AppendLine(extractStartTime.ToString())  
        End If  
      End With  
  
      System.Windows.Forms.MessageBox.Show(eventMessage.ToString())  
  
      Dts.Log(eventMessage.ToString(), 0, Nothing)  
  
      Dts.TaskResult = Dts.Results.Failure  
  
    Else  
  
      Dts.TaskResult = Dts.Results.Success  
  
    End If  
  
    ```  
  
8.  <span data-ttu-id="dc1ea-252">スクリプト開発環境と **[スクリプト タスク エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-252">Close the script development environment and the **Script Task Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="dc1ea-253">次の手順</span><span class="sxs-lookup"><span data-stu-id="dc1ea-253">Next Step</span></span>  
 <span data-ttu-id="dc1ea-254">変更データが準備できていると判断したら、次に変更データのクエリを準備します。</span><span class="sxs-lookup"><span data-stu-id="dc1ea-254">After you determine that change data is ready, the next step is to prepare to query for the change data.</span></span>  
  
 <span data-ttu-id="dc1ea-255">**次のトピック:** [変更データのクエリを準備する](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="dc1ea-255">**Next topic:** [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>  
  
  
