---
title: 変更データの間隔を指定する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],specifying interval
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 70b9c14d609f2db69ee5751eca18acb5262a07a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634584"
---
# <a name="specify-an-interval-of-change-data"></a><span data-ttu-id="e13a0-102">変更データの間隔を指定する</span><span class="sxs-lookup"><span data-stu-id="e13a0-102">Specify an Interval of Change Data</span></span>
  <span data-ttu-id="e13a0-103">変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローにおいて、最初のタスクは、変更間隔のエンドポイントを計算することです。</span><span class="sxs-lookup"><span data-stu-id="e13a0-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="e13a0-104">このエンドポイントは `datetime` 値で、パッケージで後から使用するためにパッケージ変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-104">These endpoints are `datetime` values and will be stored in package variables for use later in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e13a0-105">制御フローをデザインするプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e13a0-105">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="set-up-package-variables-for-the-endpoints"></a><span data-ttu-id="e13a0-106">エンドポイントのパッケージ変数の設定</span><span class="sxs-lookup"><span data-stu-id="e13a0-106">Set Up Package Variables for the Endpoints</span></span>  
 <span data-ttu-id="e13a0-107">エンドポイントを計算するように SQL 実行タスクを構成する前に、エンドポイントを格納するパッケージ変数を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e13a0-107">Before configuring the Execute SQL task to calculate the endpoints, the package variables that will store the endpoints have to be defined.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="e13a0-108">パッケージ変数を設定するには</span><span class="sxs-lookup"><span data-stu-id="e13a0-108">To set up package variables</span></span>  
  
1.  <span data-ttu-id="e13a0-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="e13a0-110">**[変数]** ウィンドウで、次の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-110">In the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="e13a0-111">間隔の開始時点を格納する `datetime` データ型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-111">Create a variable with the `datetime` data type to hold the starting point for the interval.</span></span>  
  
         <span data-ttu-id="e13a0-112">この例では、ExtractStartTime という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-112">This example uses the variable name, ExtractStartTime.</span></span>  
  
    2.  <span data-ttu-id="e13a0-113">間隔の終了時点を格納する `datetime` データ型の別の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-113">Create another variable with the `datetime` data type to hold the ending point for the interval.</span></span>  
  
         <span data-ttu-id="e13a0-114">この例では、ExtractEndTime という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-114">This example uses the variable name, ExtractEndTime.</span></span>  
  
 <span data-ttu-id="e13a0-115">複数の子パッケージを実行するマスター パッケージのエンドポイントを計算する場合は、親パッケージ変数の構成を使用してその変数の値を各子パッケージに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-115">If you calculate the endpoints in a master package that executes multiple child packages, you can use Parent Package Variable configurations to pass the values of these variables to each child package.</span></span> <span data-ttu-id="e13a0-116">詳細については、「 [パッケージ実行タスク](../control-flow/execute-package-task.md) 」および「 [子パッケージでの変数およびパラメーターの値の使用](../use-the-values-of-variables-and-parameters-in-a-child-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e13a0-116">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
## <a name="calculate-a-starting-point-and-an-ending-point-for-change-data"></a><span data-ttu-id="e13a0-117">変更データの開始時点と終了時点の計算</span><span class="sxs-lookup"><span data-stu-id="e13a0-117">Calculate a Starting Point and an Ending Point for Change Data</span></span>  
 <span data-ttu-id="e13a0-118">間隔のエンドポイントのパッケージ変数を設定したら、そのエンドポイントの実際の値を計算し、対応するパッケージ変数にマップできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e13a0-118">After you set up the package variables for the interval endpoints, you can calculate the actual values for those endpoints and map those values to the corresponding package variables.</span></span> <span data-ttu-id="e13a0-119">このエンドポイントは `datetime` 値なので、`datetime` 値を計算または操作できる関数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e13a0-119">Because those endpoints are `datetime` values, you will have to use functions that can calculate or work with `datetime` values.</span></span> <span data-ttu-id="e13a0-120">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式言語と Transact-SQL の両方に、`datetime` 値を操作する関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e13a0-120">Both the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language and Transact-SQL have functions that work with `datetime` values:</span></span>  
  
 <span data-ttu-id="e13a0-121">`datetime` 値を操作する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式言語の関数</span><span class="sxs-lookup"><span data-stu-id="e13a0-121">Functions in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language that work with `datetime` values</span></span>  
 -   [<span data-ttu-id="e13a0-122">DATEADD (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-122">DATEADD &#40;SSIS Expression&#41;</span></span>](../expressions/dateadd-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-123">DATEDIFF (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-123">DATEDIFF &#40;SSIS Expression&#41;</span></span>](../expressions/datediff-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-124">DATEPART (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-124">DATEPART &#40;SSIS Expression&#41;</span></span>](../expressions/datepart-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-125">DAY (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-125">DAY &#40;SSIS Expression&#41;</span></span>](../expressions/day-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-126">GETDATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-126">GETDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getdate-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-127">GETUTCDATE (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-127">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getutcdate-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-128">MONTH (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-128">MONTH &#40;SSIS Expression&#41;</span></span>](../expressions/month-ssis-expression.md)  
  
-   [<span data-ttu-id="e13a0-129">YEAR (SSIS 式)</span><span class="sxs-lookup"><span data-stu-id="e13a0-129">YEAR &#40;SSIS Expression&#41;</span></span>](../expressions/year-ssis-expression.md)  
  
 <span data-ttu-id="e13a0-130">`datetime` 値を操作する Transact-SQL の関数</span><span class="sxs-lookup"><span data-stu-id="e13a0-130">Functions in Transact-SQL that work with `datetime` values</span></span>  
 <span data-ttu-id="e13a0-131">[日付と時刻のデータ型および関数 (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e13a0-131">[Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
 <span data-ttu-id="e13a0-132">これらの `datetime` 関数のいずれかを使用してエンドポイントを計算する前に、間隔が一定で定期的かどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e13a0-132">Before you use any one of these `datetime` functions to calculate the endpoints, you have to determine whether the interval is fixed and occurs on a regular schedule.</span></span> <span data-ttu-id="e13a0-133">通常、ソース テーブルで行われた変更は、定期的に変換先テーブルに適用します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-133">Typically, you want to apply changes that have occurred in source tables to destination tables on a regular schedule.</span></span> <span data-ttu-id="e13a0-134">たとえば、このような変更は、1 時間ごと、毎日、または毎週適用します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-134">For example, you might want to apply those changes on an hourly, daily, or weekly basis.</span></span>  
  
 <span data-ttu-id="e13a0-135">変更間隔が一定かランダムかを把握したら、エンドポイントを計算できます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-135">After you understand whether your change interval is fixed or is more random, you can calculate the endpoints:</span></span>  
  
-   <span data-ttu-id="e13a0-136">**開始日時の計算**。</span><span class="sxs-lookup"><span data-stu-id="e13a0-136">**Calculating the starting date and time**.</span></span> <span data-ttu-id="e13a0-137">前の読み込みの終了日時を現在の開始日時として使用します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-137">You use the ending date and time from the previous load as the current starting date and time.</span></span> <span data-ttu-id="e13a0-138">増分読み込みの間隔が一定である場合は、Transact-SQL または [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式言語の `datetime` 関数を使用してこの値を計算できます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-138">If you use a fixed interval for incremental loads, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span> <span data-ttu-id="e13a0-139">一定でない場合は、実行のたびにエンドポイントを保存し、SQL 実行タスクまたはスクリプト タスクを使用して前のエンドポイントを読み込むことが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e13a0-139">Otherwise, you might have to persist the endpoints between executions, and use an Execute SQL task or a Script task to load the previous endpoint.</span></span>  
  
-   <span data-ttu-id="e13a0-140">**終了日時の計算**。</span><span class="sxs-lookup"><span data-stu-id="e13a0-140">**Calculating the ending date and time**.</span></span> <span data-ttu-id="e13a0-141">増分読み込みの間隔が一定である場合は、現在の終了日時を開始日時からのオフセットとして計算します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-141">If you use a fixed interval for incremental loads, calculate the current ending date and time as an offset from the starting date and time.</span></span> <span data-ttu-id="e13a0-142">ここでも、 `datetime` transact-sql または式言語の関数を使用して、この値を計算でき [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-142">Again, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span>  
  
 <span data-ttu-id="e13a0-143">次の手順では、変更間隔が一定で、増分読み込みパッケージが例外なく毎日実行されることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e13a0-143">In the following procedure, the change interval uses a fixed interval and assumes that the incremental load package is run daily without exception.</span></span> <span data-ttu-id="e13a0-144">それ以外の場合、対象外の間隔の変更データは失われます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-144">Otherwise, change data for missed intervals would be lost.</span></span> <span data-ttu-id="e13a0-145">間隔の開始時点は一昨日の午前 0 時 (24 ～ 48 時間前) です。</span><span class="sxs-lookup"><span data-stu-id="e13a0-145">The starting point for the interval is midnight the day before yesterday, that is, between 24 and 48 hours ago.</span></span> <span data-ttu-id="e13a0-146">間隔の終了時点は昨日の午前 0 時 (0 ～ 24 時間前の昨晩) です。</span><span class="sxs-lookup"><span data-stu-id="e13a0-146">The ending point for the interval is midnight yesterday, that is, the previous night, between 0 and 24 hours ago.</span></span>  
  
#### <a name="to-calculate-the-starting-point-and-ending-point-for-the-capture-interval"></a><span data-ttu-id="e13a0-147">キャプチャ間隔の開始時点と終了時点を計算するには</span><span class="sxs-lookup"><span data-stu-id="e13a0-147">To calculate the starting point and ending point for the capture interval</span></span>  
  
1.  <span data-ttu-id="e13a0-148">**デザイナーの** [制御フロー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブで、SQL 実行タスクをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-148">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add an Execute SQL Task to the package.</span></span>  
  
2.  <span data-ttu-id="e13a0-149">**[SQL 実行タスク エディター]** を開いて、エディターの **[全般]** ページで次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-149">Open the **Execute SQL Task Editor**, and on the **General** page of the editor, select the following options:</span></span>  
  
    1.  <span data-ttu-id="e13a0-150">**[ResultSet]** で **[単一行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-150">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="e13a0-151">ソース データベースへの有効な接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-151">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="e13a0-152">**[SQLSourceType]** で **[直接入力]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-152">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="e13a0-153">**[SQLStatement]** に、次の SQL ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-153">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  <span data-ttu-id="e13a0-154">**[SQL 実行タスク エディター]** の **[結果セット]** ページで、ExtractStartTime の結果を ExtractStartTime パッケージ変数に、ExtractEndTime の結果を ExtractEndTime パッケージ変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="e13a0-154">On the **Result Set** page of the **Execute SQL Task Editor**, map the ExtractStartTime result to the ExtractStartTime package variable, and map the ExtractEndTime result to the ExtractEndTime package variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e13a0-155">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変数の値を設定する式を使用する場合は、変数の値にアクセスするたびに式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="e13a0-155">When you use an expression to set the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, the expression is evaluated every time that the value of the variable is accessed.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e13a0-156">次の手順</span><span class="sxs-lookup"><span data-stu-id="e13a0-156">Next Step</span></span>  
 <span data-ttu-id="e13a0-157">変更の範囲の開始時点と終了時点を計算したら、次の手順で、変更データが準備できているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e13a0-157">After you calculate the starting point and ending point for a range of changes, the next step is to determine whether the change data is ready.</span></span>  
  
 <span data-ttu-id="e13a0-158">**次のトピック:** [変更データの準備ができているかどうかを判断する](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="e13a0-158">**Next topic:** [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13a0-159">参照</span><span class="sxs-lookup"><span data-stu-id="e13a0-159">See Also</span></span>  
 <span data-ttu-id="e13a0-160">[パッケージで変数を使用する](../use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e13a0-160">[Use Variables in Packages](../use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="e13a0-161">[Integration Services &#40;SSIS&#41; 式](../expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="e13a0-161">[Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="e13a0-162">[SQL 実行タスク](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="e13a0-162">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="e13a0-163">スクリプト タスク</span><span class="sxs-lookup"><span data-stu-id="e13a0-163">Script Task</span></span>](../control-flow/script-task.md)  
  
  
