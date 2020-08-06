---
title: クエリパラメーターを SQL 実行タスクの変数にマップする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8511d70b40f2934680e1cb790763045c04e8204a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640127"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a><span data-ttu-id="411a0-102">クエリ パラメーターを SQL 実行タスクの変数にマップする方法</span><span class="sxs-lookup"><span data-stu-id="411a0-102">Map Query Parameters to Variables in an Execute SQL Task</span></span>

  <span data-ttu-id="411a0-103">このトピックでは、SQL 実行タスクでパラメーター化された SQL ステートメントを使用して、SQL ステートメント内の変数とパラメーター間のマッピングを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="411a0-103">This topic describes how to use a parameterized SQL statement in the Execute SQL task and create mappings between variables and the parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="411a0-104">異なる種類の接続で使用する SQL 実行タスク、パラメーター マーカー、およびパラメーター名の詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」および「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="411a0-104">To learn more about the Execute SQL task, the parameter markers, and parameter names you use with different connection types, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="411a0-105">クエリ パラメーターを変数にマップするには</span><span class="sxs-lookup"><span data-stu-id="411a0-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="411a0-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、操作する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="411a0-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="411a0-107">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="411a0-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="411a0-108">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="411a0-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="411a0-109">SQL 実行タスクがまだパッケージに含まれていない場合、SQL 実行タスクをパッケージの制御フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="411a0-109">If the package does not already include an Execute SQL task, add one to the control flow of the package.</span></span> <span data-ttu-id="411a0-110">詳細については、「[制御フローでのタスクまたはコンテナーの追加または削除](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="411a0-110">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="411a0-111">.</span><span class="sxs-lookup"><span data-stu-id="411a0-111">.</span></span>  
  
5.  <span data-ttu-id="411a0-112">SQL 実行タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="411a0-112">Double-click the Execute SQL task.</span></span>  
  
6.  <span data-ttu-id="411a0-113">パラメーター化 SQL コマンドを、次のいずれかの方法で指定します。</span><span class="sxs-lookup"><span data-stu-id="411a0-113">Provide a parameterized SQL command in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="411a0-114">直接入力を使用して、SQLStatement プロパティに SQL コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="411a0-114">Use direct input and type the SQL command in the SQLStatement property.</span></span>  
  
    -   <span data-ttu-id="411a0-115">直接入力を使用して、 **[クエリの作成]** をクリックし、クエリ ビルダーで用意されているグラフィック ツールを使用して、SQL コマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="411a0-115">Use direct input, click **Build Query**, and then create an SQL command using the graphical tools that the Query Builder provides.</span></span>  
  
    -   <span data-ttu-id="411a0-116">ファイル接続を使用し、SQL コマンドが含まれるファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="411a0-116">Use a file connection and then reference the file that contains the SQL command.</span></span>  
  
    -   <span data-ttu-id="411a0-117">変数を使用し、SQL コマンドが含まれる変数を参照します。</span><span class="sxs-lookup"><span data-stu-id="411a0-117">Use a variable and then reference the variable that contains the SQL command.</span></span>  
  
     <span data-ttu-id="411a0-118">パラメーター化された SQL ステートメントで使用するパラメーター マーカーは、SQL 実行タスクが使用する接続の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="411a0-118">The parameter markers that you use in parameterized SQL statements depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="411a0-119">接続の種類</span><span class="sxs-lookup"><span data-stu-id="411a0-119">Connection type</span></span>|<span data-ttu-id="411a0-120">パラメーター マーカー</span><span class="sxs-lookup"><span data-stu-id="411a0-120">Parameter marker</span></span>|  
    |---------------------|----------------------|  
    |<span data-ttu-id="411a0-121">ADO (ADO)</span><span class="sxs-lookup"><span data-stu-id="411a0-121">ADO</span></span>|<span data-ttu-id="411a0-122">?</span><span class="sxs-lookup"><span data-stu-id="411a0-122">?</span></span>|  
    |<span data-ttu-id="411a0-123">ADO.NET および SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="411a0-123">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="411a0-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="411a0-124">ODBC</span></span>|<span data-ttu-id="411a0-125">?</span><span class="sxs-lookup"><span data-stu-id="411a0-125">?</span></span>|  
    |<span data-ttu-id="411a0-126">EXCEL および OLE DB</span><span class="sxs-lookup"><span data-stu-id="411a0-126">EXCEL and OLE DB</span></span>|<span data-ttu-id="411a0-127">?</span><span class="sxs-lookup"><span data-stu-id="411a0-127">?</span></span>|  
  
     <span data-ttu-id="411a0-128">次の表に、SELECT コマンドの例を接続マネージャーの種類別に示します。</span><span class="sxs-lookup"><span data-stu-id="411a0-128">The following table lists examples of the SELECT command by connection manager type.</span></span> <span data-ttu-id="411a0-129">パラメーターは、WHERE 句で使用されるフィルター値を提供します。</span><span class="sxs-lookup"><span data-stu-id="411a0-129">Parameters provide the filter values in the WHERE clauses.</span></span> <span data-ttu-id="411a0-130">この例では、SELECT を使用して、2 つのパラメーターで指定された値よりも **ProductID** の値が大きい製品と小さい製品を、 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] の **Product** テーブルから返します。</span><span class="sxs-lookup"><span data-stu-id="411a0-130">The examples use SELECT to return products from the **Product** table in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] that have a **ProductID** greater than and less than the values specified by two parameters.</span></span>  
  
    |<span data-ttu-id="411a0-131">接続の種類</span><span class="sxs-lookup"><span data-stu-id="411a0-131">Connection type</span></span>|<span data-ttu-id="411a0-132">SELECT 構文</span><span class="sxs-lookup"><span data-stu-id="411a0-132">SELECT syntax</span></span>|  
    |---------------------|-------------------|  
    |<span data-ttu-id="411a0-133">EXCEL、ODBC、OLEDB</span><span class="sxs-lookup"><span data-stu-id="411a0-133">EXCEL, ODBC, and OLEDB</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |<span data-ttu-id="411a0-134">ADO (ADO)</span><span class="sxs-lookup"><span data-stu-id="411a0-134">ADO</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     <span data-ttu-id="411a0-135">ストアド プロシージャでパラメーターを使用する例については、「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="411a0-135">For examples of using parameters with stored procedures, see [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
7.  <span data-ttu-id="411a0-136">**[パラメーター マッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="411a0-136">Click **Parameter Mapping**.</span></span>  
  
8.  <span data-ttu-id="411a0-137">パラメーター マッピングを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="411a0-137">To add a parameter mapping, click **Add**.</span></span>  
  
9. <span data-ttu-id="411a0-138">**[パラメーター名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="411a0-138">Provide a name in the **Parameter Name** box.</span></span>  
  
     <span data-ttu-id="411a0-139">使用するパラメーター名は、SQL 実行タスクが使用する接続の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="411a0-139">The parameter names that you use depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="411a0-140">接続の種類</span><span class="sxs-lookup"><span data-stu-id="411a0-140">Connection type</span></span>|<span data-ttu-id="411a0-141">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="411a0-141">Parameter name</span></span>|  
    |---------------------|--------------------|  
    |<span data-ttu-id="411a0-142">ADO (ADO)</span><span class="sxs-lookup"><span data-stu-id="411a0-142">ADO</span></span>|<span data-ttu-id="411a0-143">Param1、Param2、...</span><span class="sxs-lookup"><span data-stu-id="411a0-143">Param1, Param2, ...</span></span>|  
    |<span data-ttu-id="411a0-144">ADO.NET および SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="411a0-144">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="411a0-145">ODBC</span><span class="sxs-lookup"><span data-stu-id="411a0-145">ODBC</span></span>|<span data-ttu-id="411a0-146">1、2、3、...</span><span class="sxs-lookup"><span data-stu-id="411a0-146">1, 2, 3, ...</span></span>|  
    |<span data-ttu-id="411a0-147">EXCEL および OLE DB</span><span class="sxs-lookup"><span data-stu-id="411a0-147">EXCEL and OLE DB</span></span>|<span data-ttu-id="411a0-148">0、1、2、3、…</span><span class="sxs-lookup"><span data-stu-id="411a0-148">0, 1, 2, 3, ...</span></span>|  
  
10. <span data-ttu-id="411a0-149">**[変数名]** 一覧で、変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="411a0-149">From the **Variable Name** list, select a variable.</span></span> <span data-ttu-id="411a0-150">詳細については、「 [パッケージ内のユーザー定義変数のスコープの追加、削除、変更](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="411a0-150">For more information, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
11. <span data-ttu-id="411a0-151">**[方向]** 一覧で、パラメーターが入力、出力、または戻り値のいずれであるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="411a0-151">In the **Direction** list, specify if the parameter is an input, an output, or a return value.</span></span>  
  
12. <span data-ttu-id="411a0-152">**[データ型]** 一覧で、パラメーターのデータ型を設定します。</span><span class="sxs-lookup"><span data-stu-id="411a0-152">In the **Data Type** list, set the data type of the parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="411a0-153">パラメーターのデータ型は、変数のデータ型と互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="411a0-153">The data type of the parameter must be compatible with the data type of the variable.</span></span>  
  
13. <span data-ttu-id="411a0-154">SQL ステートメントの各パラメーターに対して、手順 8. ～ 11. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="411a0-154">Repeat steps 8 through 11 for each parameter in the SQL statement.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="411a0-155">パラメーター マッピングの順序は、SQL ステートメントで使用されるパラメーターの順序と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="411a0-155">The order of parameter mappings must be the same as the order in which the parameters appear in the SQL statement.</span></span>  
  
14. <span data-ttu-id="411a0-156">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="411a0-156">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411a0-157">参照</span><span class="sxs-lookup"><span data-stu-id="411a0-157">See Also</span></span>  
 <span data-ttu-id="411a0-158">[SQL 実行タスク](control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="411a0-158">[Execute SQL Task](control-flow/execute-sql-task.md) </span></span>  
 <span data-ttu-id="411a0-159">[SQL 実行タスクのパラメーターとリターンコード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="411a0-159">[Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span></span>  
 [<span data-ttu-id="411a0-160">Integration Services &#40;SSIS&#41; の変数</span><span class="sxs-lookup"><span data-stu-id="411a0-160">Integration Services &#40;SSIS&#41; Variables</span></span>](integration-services-ssis-variables.md)  
  
  
