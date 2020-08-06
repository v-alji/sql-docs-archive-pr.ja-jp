---
title: 変更データのクエリを準備する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],preparing query
ms.assetid: 9ea2db7a-3dca-4bbf-9903-cccd2d494b5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ab732389d5a747c596472f14f5229361dd46275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632043"
---
# <a name="prepare-to-query-for-the-change-data"></a><span data-ttu-id="442de-102">変更データのクエリを準備する</span><span class="sxs-lookup"><span data-stu-id="442de-102">Prepare to Query for the Change Data</span></span>
  <span data-ttu-id="442de-103">変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローにおいて、3 番目に行う最後のタスクは、変更データのクエリを準備してデータ フロー タスクを追加することです。</span><span class="sxs-lookup"><span data-stu-id="442de-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to prepare to query for the change data and add a Data Flow task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="442de-104">制御フローの 2 番目のタスクは、選択した間隔の変更データが準備できていることを確認することです。</span><span class="sxs-lookup"><span data-stu-id="442de-104">The second task for the control flow is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="442de-105">このタスクの詳細については、「 [データの変更の準備ができているかどうかを判断する](determine-whether-the-change-data-is-ready.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442de-105">For more information about this task, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span> <span data-ttu-id="442de-106">制御フローをデザインするプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442de-106">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations"></a><span data-ttu-id="442de-107">デザインに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="442de-107">Design Considerations</span></span>  
 <span data-ttu-id="442de-108">変更データを取得するには、間隔のエンドポイントを入力パラメーターとして受け取り、指定した間隔の変更データを返す Transact-SQL テーブル値関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="442de-108">To retrieve the change data, you will call a Transact-SQL table-valued function that accepts the endpoints of the interval as input parameters and returns change data for the specified interval.</span></span> <span data-ttu-id="442de-109">この関数は、データ フローの変換元コンポーネントによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="442de-109">A source component in the data flow calls this function.</span></span> <span data-ttu-id="442de-110">この変換元コンポーネントに関する詳細については、「 [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442de-110">For information about this source component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
 <span data-ttu-id="442de-111">OLE DB ソース、ADO ソース、ADO NET ソースなどの最もよく使用される [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントでは、テーブル値関数のパラメーター情報を取得できません。</span><span class="sxs-lookup"><span data-stu-id="442de-111">The most frequently used [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source components, including the OLE DB source, the ADO source, and the ADO NET source, cannot derive parameter information for a table-valued function.</span></span> <span data-ttu-id="442de-112">したがって、ほとんどの変換元では、パラメーター化された関数を直接呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="442de-112">Therefore, most sources cannot call a parameterized function directly.</span></span>  
  
 <span data-ttu-id="442de-113">入力パラメーターを関数に渡すには、次の 2 つのデザイン方法があります。</span><span class="sxs-lookup"><span data-stu-id="442de-113">You have two design options for passing the input parameters to the function:</span></span>  
  
-   <span data-ttu-id="442de-114">**パラメーター化クエリを文字列として作成します**。</span><span class="sxs-lookup"><span data-stu-id="442de-114">**Assemble the parameterized query as a string**.</span></span> <span data-ttu-id="442de-115">スクリプト タスクまたは SQL 実行タスクを使用して、文字列にハードコーディングされたパラメーター値で動的 SQL 文字列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="442de-115">You can use a Script task or an Execute SQL task to assemble a dynamic SQL string with parameter values hard-coded into the string.</span></span> <span data-ttu-id="442de-116">その後、この文字列をパッケージ変数に格納したものを使用して、変換元コンポーネントの SqlCommand プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="442de-116">Then, you can store this string in a package variable and use it to set the SqlCommand property of a source component.</span></span> <span data-ttu-id="442de-117">変換元コンポーネントでパラメーター情報が不要になるので、この方法は有効です。</span><span class="sxs-lookup"><span data-stu-id="442de-117">This approach succeeds because the source component no longer requires parameter information.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="442de-118">発生するオーバーヘッドは、SQL 実行タスクよりも事前コンパイルしたスクリプトの方が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="442de-118">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="442de-119">**パラメーター化されたラッパーを使用します**。</span><span class="sxs-lookup"><span data-stu-id="442de-119">**Use a parameterized wrapper**.</span></span> <span data-ttu-id="442de-120">パラメーター化されたテーブル値関数を呼び出すラッパーとして、パラメーター化されたストアド プロシージャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="442de-120">Alternatively, you can create a parameterized stored procedure as a wrapper that calls the parameterized table-valued function.</span></span> <span data-ttu-id="442de-121">変換元コンポーネントでストアド プロシージャのパラメーター情報を正常に取得できるので、この方法は有効です。</span><span class="sxs-lookup"><span data-stu-id="442de-121">This approach succeeds because a source component can successfully derive parameter information for a stored procedure.</span></span>  
  
 <span data-ttu-id="442de-122">ここでは最初のデザイン方法を使用し、パラメーター化クエリを文字列として作成します。</span><span class="sxs-lookup"><span data-stu-id="442de-122">This topic uses the first design option and assembles a parameterized query as a string.</span></span>  
  
## <a name="preparing-the-query"></a><span data-ttu-id="442de-123">クエリの準備</span><span class="sxs-lookup"><span data-stu-id="442de-123">Preparing the Query</span></span>  
 <span data-ttu-id="442de-124">入力パラメーターの値を 1 つのクエリ文字列に連結する前に、クエリで必要なパッケージ変数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="442de-124">Before you can concatenate the values of the input parameters into a single query string, you have to set up the package variables that the query needs.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="442de-125">パッケージ変数を設定するには</span><span class="sxs-lookup"><span data-stu-id="442de-125">To set up package variables</span></span>  
  
-   <span data-ttu-id="442de-126">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[変数]** ウィンドウで、SQL 実行タスクによって返されるクエリ文字列を格納する文字列データ型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="442de-126">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create a variable with a string data type to hold the query string returned by the Execute SQL Task.</span></span>  
  
     <span data-ttu-id="442de-127">この例では、SqlDataQuery という名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="442de-127">This example uses the variable name, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="442de-128">パッケージ変数を作成したら、スクリプト タスクまたは SQL 実行タスクを使用して入力パラメーターの値を連結できます。</span><span class="sxs-lookup"><span data-stu-id="442de-128">With the package variable created, you can use either a Script task or Execute SQL task to concatenate the values of the input parameters.</span></span> <span data-ttu-id="442de-129">次の 2 つの手順では、このコンポーネントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="442de-129">The following two procedures describe how to configure these components.</span></span>  
  
#### <a name="to-use-a-script-task-to-concatenate-the-query-string"></a><span data-ttu-id="442de-130">スクリプト タスクを使用してクエリ文字列を連結するには</span><span class="sxs-lookup"><span data-stu-id="442de-130">To use a Script task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="442de-131">**[制御フロー]** タブで、スクリプト タスクをパッケージの For ループ コンテナーの後に追加し、For ループ コンテナーをこのタスクに連結します。</span><span class="sxs-lookup"><span data-stu-id="442de-131">On the **Control Flow** tab, add a Script task to the package after the For Loop container and connect the For Loop container to the task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="442de-132">この手順では、パッケージによって 1 つのテーブルから増分読み込みが実行されることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="442de-132">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="442de-133">複数のテーブルから読み込みが実行され、パッケージに親パッケージと複数の子パッケージが存在する場合、このタスクは最初のコンポーネントとして各子パッケージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="442de-133">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="442de-134">詳細については、「 [複数のテーブルの増分読み込みを実行する](perform-an-incremental-load-of-multiple-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442de-134">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="442de-135">**[スクリプト タスク エディター]** の **[スクリプト]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="442de-135">In the **Script Task Editor**, on the **Script** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="442de-136">**[ReadOnlyVariables]** で **[User::DataReady]** 、 **[User::ExtractStartTime]** 、および **[User::ExtractEndTime]** を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="442de-136">For **ReadOnlyVariables**, select **User::DataReady**, **User::ExtractStartTime**, and **User::ExtractEndTime** from the.</span></span>  
  
    2.  <span data-ttu-id="442de-137">**[ReadWriteVariables]** で [User::SqlDataQuery] を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="442de-137">For **ReadWriteVariables**, select User::SqlDataQuery from the list.</span></span>  
  
3.  <span data-ttu-id="442de-138">**[スクリプト タスク エディター]** の **[スクリプト]** ページで、 **[スクリプトの編集]** をクリックしてスクリプト開発環境を開きます。</span><span class="sxs-lookup"><span data-stu-id="442de-138">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
4.  <span data-ttu-id="442de-139">Main プロシージャに、次のいずれかのコード セグメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="442de-139">In the Main procedure, enter one of the following code segments:</span></span>  
  
    -   <span data-ttu-id="442de-140">C# でプログラミングしている場合は、次のコード行を入力します。</span><span class="sxs-lookup"><span data-stu-id="442de-140">If you are programming in C#, enter the following lines of code:</span></span>  
  
        ```  
        int dataReady;  
        System.DateTime extractStartTime;  
        System.DateTime extractEndTime;  
        string sqlDataQuery;  
  
        dataReady = (int)Dts.Variables["DataReady"].Value;  
        extractStartTime = (System.DateTime)Dts.Variables["ExtractStartTime"].Value;  
        extractEndTime = (System.DateTime)Dts.Variables["ExtractEndTime"].Value;  
  
        if (dataReady == 2)  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) + "', '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
        else  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" + ", '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
  
        Dts.Variables["SqlDataQuery"].Value = sqlDataQuery;  
        ```  
  
         <span data-ttu-id="442de-141">\- - または -</span><span class="sxs-lookup"><span data-stu-id="442de-141">\- or -</span></span>  
  
    -   <span data-ttu-id="442de-142">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]でプログラミングしている場合は、次のコード行を入力します。</span><span class="sxs-lookup"><span data-stu-id="442de-142">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following lines of code:</span></span>  
  
        ```  
        Dim dataReady As Integer  
        Dim extractStartTime As Date  
        Dim extractEndTime As Date  
        Dim sqlDataQuery As String  
  
        dataReady = CType(Dts.Variables("DataReady").Value, Integer)  
        extractStartTime = CType(Dts.Variables("ExtractStartTime").Value, Date)  
        extractEndTime = CType(Dts.Variables("ExtractEndTime").Value, Date)  
  
        If dataReady = 2 Then  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) & _  
              "', '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        Else  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" & _  
              ", '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        End If  
  
        Dts.Variables("SqlDataQuery").Value = sqlDataQuery  
  
        ```  
  
5.  <span data-ttu-id="442de-143">スクリプトの実行から `DtsExecResult.Success` を返す既定のコード行はそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="442de-143">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
6.  <span data-ttu-id="442de-144">スクリプト開発環境と **[スクリプト タスク エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="442de-144">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-use-an-execute-sql-task-to-concatenate-the-query-string"></a><span data-ttu-id="442de-145">SQL 実行タスクを使用してクエリ文字列を連結するには</span><span class="sxs-lookup"><span data-stu-id="442de-145">To use an Execute SQL task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="442de-146">**[制御フロー]** タブで、SQL 実行タスクをパッケージの For ループ コンテナーの後に追加し、For ループ コンテナーをこのタスクに連結します。</span><span class="sxs-lookup"><span data-stu-id="442de-146">On the **Control Flow** tab, add an Execute SQL task to the package after the For Loop container and connect the For Loop container to this task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="442de-147">この手順では、パッケージによって 1 つのテーブルから増分読み込みが実行されることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="442de-147">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="442de-148">複数のテーブルから読み込みが実行され、パッケージに親パッケージと複数の子パッケージが存在する場合、このタスクは最初のコンポーネントとして各子パッケージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="442de-148">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="442de-149">詳細については、「 [複数のテーブルの増分読み込みを実行する](perform-an-incremental-load-of-multiple-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="442de-149">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="442de-150">**[SQL 実行タスク エディター]** の **[全般]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="442de-150">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="442de-151">**[ResultSet]** で **[単一行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="442de-151">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="442de-152">ソース データベースへの有効な接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="442de-152">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="442de-153">**[SQLSourceType]** で **[直接入力]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="442de-153">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="442de-154">**[SQLStatement]** に、次の SQL ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="442de-154">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @ExtractStartTime datetime,  
        @ExtractEndTime datetime,   
        @DataReady int  
  
        select @DataReady = ?,   
        @ExtractStartTime = ?,   
        @ExtractEndTime = ?  
  
        if @DataReady = 2  
        select N'select * from CDCSample.uf_Customer'  
        + N'('''+ convert(nvarchar(30),@ExtractStartTime,120)  
        + ''', '''  
        + convert(nvarchar(30),@ExtractEndTime,120) + ''') '   
        as SqlDataQuery  
        else  
        select N'select * from CDCSample.uf_Customer'  
        + N'(null, '''  
        + convert(nvarchar(30),@ExtractEndTime,120)  
        + ''') '  
        as SqlDataQuery  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="442de-155">このサンプルの `else` 句では、開始日時として NULL 値を渡すことによって変更データの最初の読み込みのクエリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="442de-155">The `else` clause in this sample generates a query for the initial load of change data by passing a null value for the starting date and time.</span></span> <span data-ttu-id="442de-156">このサンプルは、変更データ キャプチャを有効にする前に行われた変更もデータ ウェアハウスにアップロードする必要があるシナリオには対応していません。</span><span class="sxs-lookup"><span data-stu-id="442de-156">This sample does not address the scenario in which changes that were made before change data capture was enabled also have to be uploaded to the data warehouse.</span></span>  
  
3.  <span data-ttu-id="442de-157">**[SQL 実行タスク エディター]** の **[パラメーター マッピング]** ページで、次のマッピングを行います。</span><span class="sxs-lookup"><span data-stu-id="442de-157">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, do the following mapping:</span></span>  
  
    1.  <span data-ttu-id="442de-158">DataReady 変数をパラメーター 0 にマップします。</span><span class="sxs-lookup"><span data-stu-id="442de-158">Map the DataReady variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="442de-159">ExtractStartTime 変数をパラメーター 1 にマップします。</span><span class="sxs-lookup"><span data-stu-id="442de-159">Map the ExtractStartTime variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="442de-160">ExtractEndTime 変数をパラメーター 2 にマップします。</span><span class="sxs-lookup"><span data-stu-id="442de-160">Map the ExtractEndTime variable to parameter 2.</span></span>  
  
4.  <span data-ttu-id="442de-161">**[SQL 実行タスク エディター]** の **[結果セット]** ページで、結果名を SqlDataQuery 変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="442de-161">On the **Result Set** page of the **Execute SQL Task Editor**, map the Result Name to the SqlDataQuery variable.</span></span>  
  
     <span data-ttu-id="442de-162">結果名は、返される単一列の名前 SqlDataQuery になります。</span><span class="sxs-lookup"><span data-stu-id="442de-162">The Result Name is the name of the single column that is returned, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="442de-163">上記の手順で、ハードコーディングされた入力パラメーターの文字列値を使用してクエリ文字列を準備するタスクを構成しました。</span><span class="sxs-lookup"><span data-stu-id="442de-163">The previous procedures configure a task that prepares a query string with hard-coded string values for the input parameters.</span></span> <span data-ttu-id="442de-164">次に、このクエリ文字列のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="442de-164">The following code is an example of such a query string:</span></span>  
  
 `select * from CDCSample. uf_Customer('2007-06-11 14:21:58', '2007-06-12 14:21:58')`  
  
## <a name="adding-a-data-flow-task"></a><span data-ttu-id="442de-165">データ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="442de-165">Adding a Data Flow Task</span></span>  
 <span data-ttu-id="442de-166">パッケージの制御フローをデザインする最後の手順として、データ フロー タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="442de-166">The last step in designing the control flow for the package is to add a Data Flow task.</span></span>  
  
#### <a name="to-add-a-data-flow-task-and-complete-the-control-flow"></a><span data-ttu-id="442de-167">データ フロー タスクを追加して制御フローを完成させるには</span><span class="sxs-lookup"><span data-stu-id="442de-167">To add a Data Flow task and complete the control flow</span></span>  
  
-   <span data-ttu-id="442de-168">**[制御フロー]** タブで、データ フロー タスクを追加し、クエリ文字列を連結したタスクを連結します。</span><span class="sxs-lookup"><span data-stu-id="442de-168">On the **Control Flow** tab, add a Data Flow task and connect the task that concatenated the query string.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="442de-169">次の手順</span><span class="sxs-lookup"><span data-stu-id="442de-169">Next Step</span></span>  
 <span data-ttu-id="442de-170">クエリ文字列を準備してデータ フロー タスクを構成したら、次にデータベースから変更データを取得するテーブル値関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="442de-170">After you prepare the query string and configure the Data Flow task, the next step is create the table-valued function that will retrieve the change data from the database.</span></span>  
  
 <span data-ttu-id="442de-171">**次のトピック:** [変更データを取得する関数を作成する](create-the-function-to-retrieve-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="442de-171">**Next topic:** [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md)</span></span>  
  
  
