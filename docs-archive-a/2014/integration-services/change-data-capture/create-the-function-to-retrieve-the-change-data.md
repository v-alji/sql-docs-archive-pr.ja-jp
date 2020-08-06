---
title: 変更データを取得する関数を作成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],creating function
ms.assetid: 55dd0946-bd67-4490-9971-12dfb5b9de94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc1d5af0a64225aca4ff54570ad6504d25d62812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740231"
---
# <a name="create-the-function-to-retrieve-the-change-data"></a><span data-ttu-id="b3764-102">変更データを取得する関数を作成する</span><span class="sxs-lookup"><span data-stu-id="b3764-102">Create the Function to Retrieve the Change Data</span></span>
  <span data-ttu-id="b3764-103">変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローが完了したので、次の作業では、変更データを取得するテーブル値関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b3764-103">After completing the control flow for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the next task is to create a table-valued function that retrieves the change data.</span></span> <span data-ttu-id="b3764-104">この関数は、最初の増分読み込みの前に一度作成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="b3764-104">You only have to create this function one time before the first incremental load.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3764-105">変更データを取得する関数の作成は、変更データの増分読み込みを実行するパッケージを作成するプロセスにおける 2 番目の手順です。</span><span class="sxs-lookup"><span data-stu-id="b3764-105">The creation of a function to retrieve the change data is the second step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="b3764-106">このパッケージを作成するプロセス全体の説明については、「[Change Data Capture (SSIS)](change-data-capture-ssis.md)」 (変更データ キャプチャ (SSIS)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3764-106">For a description of the overall process for creating this package, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations-for-change-data-capture-functions"></a><span data-ttu-id="b3764-107">変更データ キャプチャの関数の設計に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="b3764-107">Design Considerations for Change Data Capture Functions</span></span>  
 <span data-ttu-id="b3764-108">変更データを取得するには、パッケージのデータ フローの変換元コンポーネントで、次のいずれかの変更データ キャプチャのクエリ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b3764-108">To retrieve change data, a source component in the data flow of the package calls one of the following change data capture query functions:</span></span>  
  
-   <span data-ttu-id="b3764-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** このクエリでは、更新ごとに返される単一行に、変更された各行の最終的な状態が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** For this query, the single row returned for each update contains the final state of each changed row.</span></span> <span data-ttu-id="b3764-110">ほとんどの場合、差分変更のクエリによって返されるデータのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3764-110">In most cases, you only need the data returned by a query for net changes.</span></span> <span data-ttu-id="b3764-111">詳細については、「[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3764-111">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
-   <span data-ttu-id="b3764-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** このクエリでは、キャプチャ間隔中に各行で行われたすべての変更が返されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** This query returns all the changes that have occurred in each row during the capture interval.</span></span> <span data-ttu-id="b3764-113">詳細については、「[cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3764-113">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="b3764-114">その後、関数によって返された結果を変換元コンポーネントが受け取って下流にある変換や変換先に渡し、その変換によって変更データが最終的な変換先に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-114">The source component then takes the results returned by the function and passes them to downstream transformations and destinations, which apply the change data to the final destination.</span></span>  
  
 <span data-ttu-id="b3764-115">ただし、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントは、これらの変更データ キャプチャの関数を直接呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="b3764-115">However, an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component cannot call these change data capture functions directly.</span></span> <span data-ttu-id="b3764-116">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントには、クエリから返される列に関するメタデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3764-116">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component requires metadata about the columns that the query returns.</span></span> <span data-ttu-id="b3764-117">変更データ キャプチャの関数では、その出力テーブルの列は定義されません。</span><span class="sxs-lookup"><span data-stu-id="b3764-117">The change data capture functions do not define the columns of their output table.</span></span> <span data-ttu-id="b3764-118">したがって、この関数では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントに十分なメタデータが返されません。</span><span class="sxs-lookup"><span data-stu-id="b3764-118">Thus, these functions do not return sufficient metadata for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
 <span data-ttu-id="b3764-119">代わりに、テーブル値ラッパー関数を使用します。この種の関数では RETURNS 句にその出力テーブルの列が明示的に定義されるためです。</span><span class="sxs-lookup"><span data-stu-id="b3764-119">Instead, you use a table-valued wrapper function because this kind of function explicitly defines the columns of its output table in its RETURNS clause.</span></span> <span data-ttu-id="b3764-120">この列の明示的な定義によって、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントに必要なメタデータを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="b3764-120">This explicit definition of columns provides the metadata that an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component needs.</span></span> <span data-ttu-id="b3764-121">この関数は、変更データを取得するテーブルごとに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3764-121">You have to create this function for each table for which you want to retrieve change data.</span></span>  
  
 <span data-ttu-id="b3764-122">変更データ キャプチャのクエリ関数を呼び出すテーブル値ラッパー関数を作成するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="b3764-122">You have two options for creating the table-valued wrapper function that calls the change data capture query function:</span></span>  
  
-   <span data-ttu-id="b3764-123">**sys.sp_cdc_generate_wrapper_function** システム ストアド プロシージャを呼び出して、テーブル値関数を自動的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b3764-123">You can call the **sys.sp_cdc_generate_wrapper_function** system stored procedure to create the table-valued functions for you.</span></span>  
  
-   <span data-ttu-id="b3764-124">このトピックで解説するガイドラインと例を使用して、独自のテーブル値関数を記述できます。</span><span class="sxs-lookup"><span data-stu-id="b3764-124">You can write your own table-valued function by using the guidelines and the example in this topic.</span></span>  
  
## <a name="calling-a-stored-procedure-to-create-the-table-valued-function"></a><span data-ttu-id="b3764-125">テーブル値関数を作成するストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="b3764-125">Calling a Stored Procedure to Create the Table-valued Function</span></span>  
 <span data-ttu-id="b3764-126">必要なテーブル値関数を最も短時間で簡単に作成する方法は、 **sys.sp_cdc_generate_wrapper_function** システム ストアド プロシージャを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="b3764-126">The quickest and easiest way to create the table-valued functions that you need is to call the **sys.sp_cdc_generate_wrapper_function** system stored procedure.</span></span> <span data-ttu-id="b3764-127">このストアド プロシージャでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントの要件を厳密に満たすラッパー関数を作成するスクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-127">This stored procedure generates scripts to create wrapper functions that are designed specifically to meet the needs of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b3764-128">**sys.sp_cdc_generate_wrapper_function** システム ストアド プロシージャによって、直接、ラッパー関数が作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b3764-128">The **sys.sp_cdc_generate_wrapper_function** system stored procedure does not directly create the wrapper functions.</span></span> <span data-ttu-id="b3764-129">このストアド プロシージャでは、ラッパー関数の CREATE スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-129">Instead, the stored procedure generates the CREATE scripts for the wrapper functions.</span></span> <span data-ttu-id="b3764-130">開発者は、増分読み込みパッケージでラッパー関数が呼び出される前に、ストアド プロシージャによって生成された CREATE スクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3764-130">The developer must run the CREATE scripts that the stored procedure generates before an incremental load package can call the wrapper functions.</span></span>  
  
 <span data-ttu-id="b3764-131">このシステム ストアド プロシージャの使用方法を理解するには、プロシージャの実行内容、プロシージャによって生成されるスクリプト、およびスクリプトによって作成されるラッパー関数を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3764-131">To understand how to use this system stored procedure, you should understand what the procedure does, what scripts the procedure generates, and what wrapper functions the scripts create.</span></span>  
  
### <a name="understanding-and-using-the-stored-procedure"></a><span data-ttu-id="b3764-132">ストアド プロシージャの概要と使用方法</span><span class="sxs-lookup"><span data-stu-id="b3764-132">Understanding and Using the Stored Procedure</span></span>  
 <span data-ttu-id="b3764-133">**sys.sp_cdc_generate_wrapper_function** システム ストアド プロシージャでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで使用するためのラッパー関数を作成するスクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-133">The **sys.sp_cdc_generate_wrapper_function** system stored procedure generates scripts to create wrapper functions for use by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="b3764-134">次に、ストアド プロシージャの定義に含まれる最初の数行を示します。</span><span class="sxs-lookup"><span data-stu-id="b3764-134">Here are the first few lines of the definition of the stored procedure:</span></span>  
  
 `CREATE PROCEDURE sys.sp_cdc_generate_wrapper_function`  
  
 `(`  
  
 `@capture_instance sysname = null`  
  
 `@closed_high_end_point bit = 1,`  
  
 `@column_list = null,`  
  
 `@update_flag_list = null`  
  
 `)`  
  
 <span data-ttu-id="b3764-135">ストアド プロシージャのパラメーターはすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b3764-135">All the parameters for the stored procedure are optional.</span></span> <span data-ttu-id="b3764-136">どのパラメーターにも値を指定せずにストアド プロシージャを呼び出すと、ストアド プロシージャでは、アクセス権が与えられているすべてのキャプチャ インスタンスに対してラッパー関数が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-136">If you call the stored procedure without supplying values for any of the parameters, the stored procedure creates wrapper functions for all the capture instances to which you have access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3764-137">このストアド プロシージャの構文とそのパラメーターの詳細については、「[sys.sp_cdc_generate_wrapper_function (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3764-137">For more information about the syntax of this stored procedure and its parameters, see [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql).</span></span>  
  
 <span data-ttu-id="b3764-138">ストアド プロシージャでは、常に、各キャプチャ インスタンスからすべての変更を返すラッパー関数が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-138">The stored procedure always generates a wrapper function to return all changes from each capture instance.</span></span> <span data-ttu-id="b3764-139">*@supports_net_changes*キャプチャインスタンスの作成時にパラメーターが設定された場合、ストアドプロシージャは、該当する各キャプチャインスタンスから差分変更を返すラッパー関数も生成します。</span><span class="sxs-lookup"><span data-stu-id="b3764-139">If the *@supports_net_changes* parameter was set when the capture instance was created, the stored procedure also generates a wrapper function to return net changes from each applicable capture instance.</span></span>  
  
 <span data-ttu-id="b3764-140">このストアド プロシージャによって返される結果セットには、次の 2 つの列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b3764-140">The stored procedure returns a result set with two columns:</span></span>  
  
-   <span data-ttu-id="b3764-141">ストアド プロシージャによって生成されたラッパー関数の名前。</span><span class="sxs-lookup"><span data-stu-id="b3764-141">The name of the wrapper function that the stored procedure has generated.</span></span> <span data-ttu-id="b3764-142">このストアド プロシージャでは、キャプチャ インスタンス名から関数名を取得します</span><span class="sxs-lookup"><span data-stu-id="b3764-142">This stored procedure derives the function name from the name of the capture instance name.</span></span> <span data-ttu-id="b3764-143">(関数名は、'fn_all_changes_' の後にキャプチャ インスタンス名が続きます。</span><span class="sxs-lookup"><span data-stu-id="b3764-143">(The function name is 'fn_all_changes_' followed by the capture instance name.</span></span> <span data-ttu-id="b3764-144">差分変更追跡の関数が生成された場合、その関数に使用されるプレフィックスは 'fn_net_changes_' です)。</span><span class="sxs-lookup"><span data-stu-id="b3764-144">The prefix used for the net changes function, if it is created, is 'fn_net_changes_'.)</span></span>  
  
-   <span data-ttu-id="b3764-145">ラッパー関数の CREATE ステートメント。</span><span class="sxs-lookup"><span data-stu-id="b3764-145">The CREATE statement for the wrapper function.</span></span>  
  
### <a name="understanding-and-using-the-scripts-created-by-the-stored-procedure"></a><span data-ttu-id="b3764-146">ストアド プロシージャによって作成されるスクリプトの概要と使用方法</span><span class="sxs-lookup"><span data-stu-id="b3764-146">Understanding and Using the Scripts Created by the Stored Procedure</span></span>  
 <span data-ttu-id="b3764-147">通常、開発者は、INSERT...EXEC ステートメントを使用して **sys.sp_cdc_generate_wrapper_function** ストアド プロシージャを呼び出し、ストアド プロシージャによって作成されるスクリプトを一時テーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="b3764-147">Typically, a developer would use an INSERT...EXEC statement to call the **sys.sp_cdc_generate_wrapper_function** stored procedure and save the scripts that the stored procedure creates to a temporary table.</span></span> <span data-ttu-id="b3764-148">その後、各スクリプトを個別に選択して実行し、対応するラッパー関数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b3764-148">Each script could then be individually selected and run to create the corresponding wrapper function.</span></span> <span data-ttu-id="b3764-149">ただし、次のサンプル コードに示すように、開発者は、一連の SQL コマンドを使用して、すべての CREATE スクリプトを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3764-149">However, a developer could also use one set of SQL commands to run all the CREATE scripts, as shown in the following sample code:</span></span>  
  
```  
create table #wrapper_functions  
      (function_name sysname, create_stmt nvarchar(max))  
insert into #wrapper_functions  
exec sys.sp_cdc_generate_wrapper_function  
  
declare @stmt nvarchar(max)  
declare #hfunctions cursor local fast_forward for   
      select create_stmt from #wrapper_functions  
open #hfunctions  
fetch #hfunctions into @stmt  
while (@@fetch_status <> -1)  
begin  
      exec sp_executesql @stmt  
      fetch #hfunctions into @stmt  
end  
close #hfunctions  
deallocate #hfunctions  
```  
  
### <a name="understanding-and-using-the-functions-created-by-the-stored-procedure"></a><span data-ttu-id="b3764-150">ストアド プロシージャによって作成される関数の概要と使用方法</span><span class="sxs-lookup"><span data-stu-id="b3764-150">Understanding and Using the Functions Created by the Stored Procedure</span></span>  
 <span data-ttu-id="b3764-151">キャプチャした変更データのタイムラインを体系的に進めるために、生成されるラッパー関数は、 *@end_time* 1 つの間隔のパラメーターが後続の期間のパラメーターになることを想定して *@start_time* います。</span><span class="sxs-lookup"><span data-stu-id="b3764-151">To systematically walk the timeline of captured change data, the generated wrapper functions expect that the *@end_time* parameter for one interval will be the *@start_time* parameter for the subsequent interval.</span></span> <span data-ttu-id="b3764-152">この規則に従うと、生成されたラッパー関数では次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b3764-152">When this convention is followed, the generated wrapper functions can do the following tasks:</span></span>  
  
-   <span data-ttu-id="b3764-153">内部で使用される LSN 値に日付/時刻値をマップします。</span><span class="sxs-lookup"><span data-stu-id="b3764-153">Map the date/time values to the LSN values that are used internally.</span></span>  
  
-   <span data-ttu-id="b3764-154">データの欠落や重複を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="b3764-154">Ensure that no data is lost or repeated.</span></span>  
  
 <span data-ttu-id="b3764-155">変更テーブルのすべての行に対するクエリの実行を簡略化するために、生成されたラッパー関数では、次の規則もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b3764-155">To make querying for all rows of a change table simpler, the generated wrapper functions also support the following conventions:</span></span>  
  
-   <span data-ttu-id="b3764-156">@start_time パラメーターが NULL の場合、ラッパー関数では、キャプチャ インスタンスの最小 LSN 値がクエリの下限として使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-156">If the @start_time parameter is null, the wrapper functions use the lowest LSN value in the capture instance as the lower bound of the query.</span></span>  
  
-   <span data-ttu-id="b3764-157">@end_time パラメーターが NULL の場合、ラッパー関数では、キャプチャ インスタンスの最大 LSN 値がクエリの上限として使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-157">If the @end_time parameter is null, the wrapper functions use the highest LSN value in the capture instance as the upper bound of the query.</span></span>  
  
 <span data-ttu-id="b3764-158">ほとんどのユーザーは、 **sys.sp_cdc_generate_wrapper_function** システム ストアド プロシージャによって作成されたラッパー関数を、変更することなく使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3764-158">Most users should be able to use the wrapper functions that the **sys.sp_cdc_generate_wrapper_function** system stored procedure creates without modification.</span></span> <span data-ttu-id="b3764-159">ただし、ラッパー関数をカスタマイズするには、CREATE スクリプトを実行する前にカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3764-159">However, to customize the wrapper functions, you have to customize the CREATE scripts before you run the scripts.</span></span>  
  
 <span data-ttu-id="b3764-160">パッケージでは、ラッパー関数を呼び出すときに、3 つのパラメーターの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3764-160">When your package calls the wrapper functions, the package must supply values for three parameters.</span></span> <span data-ttu-id="b3764-161">この 3 つのパラメーターは、変更データ キャプチャ関数で使用される 3 つのパラメーターに似ています。</span><span class="sxs-lookup"><span data-stu-id="b3764-161">These three parameters are like the three parameters that the change data capture functions use.</span></span> <span data-ttu-id="b3764-162">この 3 つのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b3764-162">These three parameters are as follows:</span></span>  
  
-   <span data-ttu-id="b3764-163">期間の開始日時の値と終了日時の値。</span><span class="sxs-lookup"><span data-stu-id="b3764-163">The starting date/time value and the ending date/time value for the interval.</span></span> <span data-ttu-id="b3764-164">ラッパー関数では、クエリ範囲のエンドポイントとして日付/時刻値が使用されますが、変更データ キャプチャ関数では、エンドポイントとして 2 つの LSN 値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-164">While the wrapper functions use date/time values as the end points for the query interval, the change data capture functions use two LSN values as the end points.</span></span>  
  
-   <span data-ttu-id="b3764-165">行フィルター。</span><span class="sxs-lookup"><span data-stu-id="b3764-165">The row filter.</span></span> <span data-ttu-id="b3764-166">ラッパー関数と変更データキャプチャ関数の両方について、 *@row_filter_option* パラメーターは同じです。</span><span class="sxs-lookup"><span data-stu-id="b3764-166">For both the wrapper functions and the change data capture functions, the *@row_filter_option* parameter is the same.</span></span> <span data-ttu-id="b3764-167">詳細については、「[cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62; (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)」および「[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3764-167">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) and [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="b3764-168">ラッパー関数から返される結果セットには、次のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b3764-168">The result set returned by the wrapper functions includesthe following data:</span></span>  
  
-   <span data-ttu-id="b3764-169">変更データの要求されたすべての列。</span><span class="sxs-lookup"><span data-stu-id="b3764-169">All of the requested columns of change data.</span></span>  
  
-   <span data-ttu-id="b3764-170">行に関連付けられている操作を示すために 1 文字または 2 文字のフィールドを使用する、__CDC_OPERATION という名前の列。</span><span class="sxs-lookup"><span data-stu-id="b3764-170">A column named __CDC_OPERATION that uses a one- or two-character field to identify the operation that is associated with the row.</span></span> <span data-ttu-id="b3764-171">このフィールドに有効な値は、'I' (挿入)、'D' (削除)、'UO' (古い値の更新)、'UN' (新しい値の更新) です。</span><span class="sxs-lookup"><span data-stu-id="b3764-171">The valid values for this field are as follows: 'I' for insert, 'D' for delete, 'UO' for update old values, and 'UN' for update new values.</span></span>  
  
-   <span data-ttu-id="b3764-172">更新フラグを要求した場合は、操作コードの後にビット列として表示され、パラメーターに指定された順序で表示され *@update_flag_list* ます。</span><span class="sxs-lookup"><span data-stu-id="b3764-172">Update flags, when you request them, that appear as bit columns after the operation code and in the order that is specified in the *@update_flag_list* parameter.</span></span> <span data-ttu-id="b3764-173">これらの列には、関連する列名に '_uflag' が追加された名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="b3764-173">These columns are named by appending '_uflag' to the associated column name.</span></span>  
  
 <span data-ttu-id="b3764-174">パッケージで、すべての変更に対してクエリを実行するラッパー関数を呼び出すと、そのラッパー関数は __CDC_STARTLSN 列と \__CDC_SEQVAL 列も返します。</span><span class="sxs-lookup"><span data-stu-id="b3764-174">If your package calls a wrapper function that queries for all changes, the wrapper function also returns the columns, __CDC_STARTLSN and \__CDC_SEQVAL.</span></span> <span data-ttu-id="b3764-175">この 2 つの列はそれぞれ、結果セットの 1 番目の列と 2 番目の列になります。</span><span class="sxs-lookup"><span data-stu-id="b3764-175">These two columns become the first and second columns, respectively, of the result set.</span></span> <span data-ttu-id="b3764-176">また、ラッパー関数は、この 2 つの列に基づいて結果セットを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="b3764-176">The wrapper function also sorts the result set based on these two columns.</span></span>  
  
## <a name="writing-your-own-table-value-function"></a><span data-ttu-id="b3764-177">独自のテーブル値関数の作成</span><span class="sxs-lookup"><span data-stu-id="b3764-177">Writing Your Own Table-Value Function</span></span>  
 <span data-ttu-id="b3764-178">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用すると、変更データ キャプチャのクエリ関数を呼び出す独自のテーブル値ラッパー関数を作成して、そのテーブル値ラッパー関数を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3764-178">You can also use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to write your own table-valued wrapper function that calls the change data capture query function, and store the table-valued wrapper function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b3764-179">Transact-SQL 関数の作成方法の詳細については、「[CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3764-179">For more information about how to create a Transact-SQL function, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
 <span data-ttu-id="b3764-180">次の例では、指定した変更間隔の Customer テーブルから変更を取得するテーブル値関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3764-180">The following example defines a table-valued function that retrieves changes from a Customer table for the specified change interval.</span></span> <span data-ttu-id="b3764-181">この関数では、変更データ キャプチャの関数を使用して、変更テーブルで内部的に使用されるバイナリ ログ シーケンス番号 (LSN) の値に `datetime` 値をマップします。</span><span class="sxs-lookup"><span data-stu-id="b3764-181">This function uses change data capture functions to map the `datetime` values to the binary log sequence number (LSN) values that the change tables use internally.</span></span> <span data-ttu-id="b3764-182">また、この関数では、次の特殊な条件も処理されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-182">This function also handles several special conditions:</span></span>  
  
-   <span data-ttu-id="b3764-183">開始時刻に NULL 値が渡されると、この関数では、使用可能な最も早い時刻値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-183">When a null value is passed for the starting time, this function uses the earliest available value.</span></span>  
  
-   <span data-ttu-id="b3764-184">終了時刻に NULL 値が渡されると、この関数では、使用可能な最も遅い時刻値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-184">When a null value is passed for the ending time, this function uses the latest available value.</span></span>  
  
-   <span data-ttu-id="b3764-185">開始 LSN が最終 LSN と同じ場合、この関数は終了します (これは通常、選択した間隔にレコードが存在しないことを示します)。</span><span class="sxs-lookup"><span data-stu-id="b3764-185">When the starting LSN is equal to the ending LSN, which usually indicates that there are no records for the selected interval, this function exits.</span></span>  
  
### <a name="example-of-a-table-value-function-that-queries-for-change-data"></a><span data-ttu-id="b3764-186">変更データをクエリで取得するテーブル値関数の例</span><span class="sxs-lookup"><span data-stu-id="b3764-186">Example of a Table-Value Function that Queries for Change Data</span></span>  
  
```  
CREATE function CDCSample.uf_Customer (  
     @start_time datetime  
    ,@end_time datetime  
)  
returns @Customer table (  
     CustomerID int  
    ,TerritoryID int  
    ,CustomerType nchar(1)  
    ,rowguid uniqueidentifier  
    ,ModifiedDate datetime  
    ,CDC_OPERATION varchar(1)  
) as  
begin  
    declare @from_lsn binary(10), @to_lsn binary(10)  
  
    if (@start_time is null)  
        select @from_lsn = sys.fn_cdc_get_min_lsn('Customer')  
    else  
        select @from_lsn = sys.fn_cdc_increment_lsn(sys.fn_cdc_map_time_to_lsn('largest less than or equal',@start_time))  
  
    if (@end_time is null)  
        select @to_lsn = sys.fn_cdc_get_max_lsn()  
    else  
        select @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal',@end_time)  
  
    if (@from_lsn = sys.fn_cdc_increment_lsn(@to_lsn))  
        return  
  
    -- Query for change data  
    insert into @Customer  
    select   
        CustomerID,      
        TerritoryID,   
        CustomerType,   
        rowguid,   
        ModifiedDate,   
        case __$operation  
                when 1 then 'D'  
                when 2 then 'I'  
                when 4 then 'U'  
                else null  
         end as CDC_OPERATION  
    from   
        cdc.fn_cdc_get_net_changes_Customer(@from_lsn, @to_lsn, 'all')  
  
    return  
end   
go  
  
```  
  
### <a name="retrieving-additional-metadata-with-the-change-data"></a><span data-ttu-id="b3764-187">変更データを含む追加のメタデータの取得</span><span class="sxs-lookup"><span data-stu-id="b3764-187">Retrieving Additional Metadata with the Change Data</span></span>  
 <span data-ttu-id="b3764-188">前述のユーザーが作成したテーブル値関数では **__$operation** 列のみが使用されていますが、**cdc.fn_cdc_get_net_changes_<capture_instance>** 関数では、各変更行の 4 つのメタデータ列を返します。</span><span class="sxs-lookup"><span data-stu-id="b3764-188">Although the user-created table-valued function shown earlier uses only the **__$operation** column, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns four columns of metadata for each change row.</span></span> <span data-ttu-id="b3764-189">これらの値をデータ フローで使用する場合は、テーブル値ラッパー関数から追加の列として値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b3764-189">If you want to use these values in your data flow, you can return them as additional columns from the table-valued wrapper function.</span></span>  
  
|<span data-ttu-id="b3764-190">列名</span><span class="sxs-lookup"><span data-stu-id="b3764-190">Column name</span></span>|<span data-ttu-id="b3764-191">データ型</span><span class="sxs-lookup"><span data-stu-id="b3764-191">Data type</span></span>|<span data-ttu-id="b3764-192">説明</span><span class="sxs-lookup"><span data-stu-id="b3764-192">Description</span></span>|  
|-----------------|---------------|-----------------|  
|<span data-ttu-id="b3764-193">**__$start_lsn**</span><span class="sxs-lookup"><span data-stu-id="b3764-193">**__$start_lsn**</span></span>|`binary(10)`|<span data-ttu-id="b3764-194">変更のコミット トランザクションに関連付けられた LSN。</span><span class="sxs-lookup"><span data-stu-id="b3764-194">LSN associated with the commit transaction for the change.</span></span><br /><br /> <span data-ttu-id="b3764-195">同じトランザクションでコミットされたすべての変更は、同じコミット LSN を共有します。</span><span class="sxs-lookup"><span data-stu-id="b3764-195">All changes committed in the same transaction share the same commit LSN.</span></span> <span data-ttu-id="b3764-196">たとえば、ソース テーブルの更新操作によって 2 つの異なる行が変更された場合、変更テーブルには、すべて同じ **__$start_lsn** 値を持った 4 つの行 (古い値を含む 2 行と新しい値を含む 2 行) が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-196">For example, if an update operation on the source table modifies two different rows, the change table will contain four rows (two with the old values and two with the new values), each with the same **__$start_lsn** value.</span></span>|  
|<span data-ttu-id="b3764-197">**__$seqval**</span><span class="sxs-lookup"><span data-stu-id="b3764-197">**__$seqval**</span></span>|`binary(10)`|<span data-ttu-id="b3764-198">特定のトランザクションに含まれる行の変更を並べ替えるためのシーケンス値です。</span><span class="sxs-lookup"><span data-stu-id="b3764-198">Sequence value that is used to order the row changes in a transaction.</span></span>|  
|<span data-ttu-id="b3764-199">**__$operation**</span><span class="sxs-lookup"><span data-stu-id="b3764-199">**__$operation**</span></span>|`int`|<span data-ttu-id="b3764-200">変更に関連付けられているデータ操作言語 (DML) 操作。</span><span class="sxs-lookup"><span data-stu-id="b3764-200">The data manipulation language (DML) operation associated with the change.</span></span> <span data-ttu-id="b3764-201">以下のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b3764-201">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="b3764-202">1 = 削除</span><span class="sxs-lookup"><span data-stu-id="b3764-202">1 = delete</span></span><br /><br /> <span data-ttu-id="b3764-203">2 = 挿入</span><span class="sxs-lookup"><span data-stu-id="b3764-203">2 = insert</span></span><br /><br /> <span data-ttu-id="b3764-204">3 = 更新 (更新操作前の値)</span><span class="sxs-lookup"><span data-stu-id="b3764-204">3 = update (Values before the update operation.)</span></span><br /><br /> <span data-ttu-id="b3764-205">4 = 更新 (更新操作後の値)</span><span class="sxs-lookup"><span data-stu-id="b3764-205">4 = update (Values after the update operation.)</span></span>|  
|<span data-ttu-id="b3764-206">**__$update_mask**</span><span class="sxs-lookup"><span data-stu-id="b3764-206">**__$update_mask**</span></span>|`varbinary(128)`|<span data-ttu-id="b3764-207">変更された列を識別する、変更テーブルの列序数に基づくビットマスク。</span><span class="sxs-lookup"><span data-stu-id="b3764-207">A bitmask that is based on the column ordinals of the change table identifying those columns that changed.</span></span> <span data-ttu-id="b3764-208">変更された列を特定する必要がある場合にこの値を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="b3764-208">You could examine this value if you had to determine which columns have changed.</span></span>|  
|**\<captured source table columns>**|<span data-ttu-id="b3764-209">多様</span><span class="sxs-lookup"><span data-stu-id="b3764-209">varies</span></span>|<span data-ttu-id="b3764-210">この関数によって返されるその他の列は、ソース テーブルの列のうち、キャプチャ インスタンスの作成時にキャプチャ対象として指定された列です。</span><span class="sxs-lookup"><span data-stu-id="b3764-210">The remaining columns returned by the function are the columns from the source table that were identified as captured columns when the capture instance was created.</span></span> <span data-ttu-id="b3764-211">キャプチャ対象列リストで列が最初に指定されなかった場合、ソース テーブルのすべての列が返されます。</span><span class="sxs-lookup"><span data-stu-id="b3764-211">If no columns were originally specified in the captured column list, all columns in the source table are returned.</span></span>|  
  
 <span data-ttu-id="b3764-212">詳細については、「[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3764-212">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b3764-213">次の手順</span><span class="sxs-lookup"><span data-stu-id="b3764-213">Next Step</span></span>  
 <span data-ttu-id="b3764-214">変更データをクエリで取得するテーブル値関数を作成したら、次の手順で、パッケージのデータ フローのデザインを開始します。</span><span class="sxs-lookup"><span data-stu-id="b3764-214">After you have created the table-valued function that queries for change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="b3764-215">**次のトピック:** [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="b3764-215">**Next topic:** [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>  
  
  
