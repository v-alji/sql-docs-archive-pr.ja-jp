---
title: 変換先に変更を適用する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],applying changes
ms.assetid: 338a56db-cb14-4784-a692-468eabd30f41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dd7ab93a299ffaab2259c3d462a5c0a69160ad5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645758"
---
# <a name="apply-the-changes-to-the-destination"></a><span data-ttu-id="34eb0-102">変換先に変更を適用する</span><span class="sxs-lookup"><span data-stu-id="34eb0-102">Apply the Changes to the Destination</span></span>
  <span data-ttu-id="34eb0-103">変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローにおいて、3 番目に行う最後のタスクは、変更を変換先に適用することです。</span><span class="sxs-lookup"><span data-stu-id="34eb0-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to apply the changes to your destination.</span></span> <span data-ttu-id="34eb0-104">挿入を適用するコンポーネント、更新を適用するコンポーネント、および削除を適用するコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="34eb0-104">You will need one component to apply inserts, one to apply updates, and one to apply deletes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34eb0-105">変更データの増分読み込みを実行するパッケージのデータ フローをデザインするための 2 番目のタスクは、挿入、更新、および削除を分割することです。</span><span class="sxs-lookup"><span data-stu-id="34eb0-105">The second task in designing the data flow of a package that performs an incremental load of change data is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="34eb0-106">このコンポーネントの詳細については、「 [挿入、更新、および削除を処理する](process-inserts-updates-and-deletes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34eb0-106">For more information about this component, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span> <span data-ttu-id="34eb0-107">変更データの増分読み込みを実行するパッケージを作成するプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34eb0-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="applying-inserts"></a><span data-ttu-id="34eb0-108">挿入の適用</span><span class="sxs-lookup"><span data-stu-id="34eb0-108">Applying Inserts</span></span>  
 <span data-ttu-id="34eb0-109">挿入を適用するには、新しい行で特別な処理は必要ないので、OLE DB 変換先を使用します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-109">To apply inserts, you use an OLE DB destination because the new rows do not require any special handling.</span></span>  
  
#### <a name="to-process-inserts-by-using-an-ole-db-destination"></a><span data-ttu-id="34eb0-110">OLE DB 変換先を使用して挿入を処理するには</span><span class="sxs-lookup"><span data-stu-id="34eb0-110">To process inserts by using an OLE DB Destination</span></span>  
  
1.  <span data-ttu-id="34eb0-111">**[データ フロー]** タブで、OLE DB 変換先を追加します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-111">On the **Data flow** tab, add an OLE DB destination.</span></span>  
  
2.  <span data-ttu-id="34eb0-112">条件分割変換から挿入を受け取った出力を OLE DB 変換先に接続します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-112">Connect the output that contains inserts from the Conditional Split transformation to the OLE DB destination.</span></span>  
  
3.  <span data-ttu-id="34eb0-113">**[OLE DB 変換先エディター]** の **[接続マネージャー]** ページで、次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-113">In the **OLE DB Destination Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="34eb0-114">変換先データベースの OLE DB 接続マネージャーを選択または作成します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-114">Select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
    2.  <span data-ttu-id="34eb0-115">**[データ アクセス モード]** オプションを選択して、変換先テーブルを選択するか、変換先列を含む SQL ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-115">Select a **Data access mode** option, and then select the destination table or enter a SQL statement that contains the destination columns.</span></span>  
  
4.  <span data-ttu-id="34eb0-116">エディターの **[マッピング]** ページで、変更データの適切な列を変換先テーブルにマップします。</span><span class="sxs-lookup"><span data-stu-id="34eb0-116">On the **Mappings** page of the editor, map the appropriate columns from the change data to the destination table.</span></span>  
  
## <a name="applying-updates"></a><span data-ttu-id="34eb0-117">更新の適用</span><span class="sxs-lookup"><span data-stu-id="34eb0-117">Applying Updates</span></span>  
 <span data-ttu-id="34eb0-118">更新を適用するには、OLE DB コマンド変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-118">To apply updates, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="34eb0-119">一度に 1 行を新しい列の値で更新する、パラメーター化された UPDATE ステートメントを使用する必要があるので、この変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-119">You use this transformation because you have to use a parameterized UPDATE statement to update one row at a time with the new column values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34eb0-120">変換先コンポーネントを使用して更新を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="34eb0-120">You can also use destination components to apply updates.</span></span> <span data-ttu-id="34eb0-121">この方法を使用する場合は、変換先コンポーネントを使用して、このために作成した一時テーブルに行を保存します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-121">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="34eb0-122">次に、SQL 実行タスクを使用して、一時テーブルから変換先に対して一括更新および一括削除操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-122">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-updates-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="34eb0-123">OLE DB コマンド変換を使用して更新を処理するには</span><span class="sxs-lookup"><span data-stu-id="34eb0-123">To process updates by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="34eb0-124">**[データ フロー]** タブで、OLE DB コマンド変換を追加します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-124">On the **Data flow** tab, add an OLE DB Command transformation.</span></span>  
  
2.  <span data-ttu-id="34eb0-125">条件分割変換から更新を受け取った出力を OLE DB コマンド変換に接続します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-125">Connect the output that contains updates from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="34eb0-126">**[OLE DB コマンドの詳細エディター]** の **[接続マネージャー]** タブで、変換先データベースの OLE DB 接続マネージャーを選択または作成します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-126">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
4.  <span data-ttu-id="34eb0-127">**[OLE DB コマンドの詳細エディター]** の **[コンポーネントのプロパティ]** タブの **[SqlCommand]** に、パラメーター化された UPDATE ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-127">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab, for **SqlCommand**, enter a parameterized UPDATE statement.</span></span>  
  
     <span data-ttu-id="34eb0-128">たとえば、Customer テーブルの UPDATE ステートメントの構文は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="34eb0-128">For example, an UPDATE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    update CDCSample.Customer  
    set TerritoryID  = ?,  
        CustomerType  = ?,  
        rowguid  = ?,  
        ModifiedDate  = ?  
    where CustomerID = ?  
  
    ```  
  
5.  <span data-ttu-id="34eb0-129">エディターの **[列マッピング]** タブで、変更データの適切な列を UPDATE ステートメントのパラメーターにマップします。</span><span class="sxs-lookup"><span data-stu-id="34eb0-129">On the **Column Mappings** tab of the editor, map the appropriate columns from the change data to the parameters in the UPDATE statement.</span></span>  
  
## <a name="applying-deletes"></a><span data-ttu-id="34eb0-130">削除の適用</span><span class="sxs-lookup"><span data-stu-id="34eb0-130">Applying Deletes</span></span>  
 <span data-ttu-id="34eb0-131">削除を適用するには、OLE DB コマンド変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-131">To apply deletes, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="34eb0-132">行を一意に識別する列の値に基づいて一度に 1 行を削除する、パラメーター化された DELETE ステートメントを使用する必要があるので、この変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-132">You use this transformation because you have to use a parameterized DELETE statement that deletes a single row at a time based on the column value that uniquely identifies the row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34eb0-133">変換先コンポーネントを使用して削除を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="34eb0-133">You can also use destination components to apply deletes.</span></span> <span data-ttu-id="34eb0-134">この方法を使用する場合は、変換先コンポーネントを使用して、このために作成した一時テーブルに行を保存します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-134">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="34eb0-135">次に、SQL 実行タスクを使用して、一時テーブルから変換先に対して一括更新および一括削除操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-135">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-deletes-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="34eb0-136">OLE DB コマンド変換を使用して削除を処理するには</span><span class="sxs-lookup"><span data-stu-id="34eb0-136">To process deletes by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="34eb0-137">**[データ フロー]** タブで、OLE DB コマンド変換をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-137">On the **Data flow** tab, add an OLE DB Command transformation to the data flow.</span></span>  
  
2.  <span data-ttu-id="34eb0-138">条件分割変換から削除を受け取った出力を OLE DB コマンド変換に接続します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-138">Connect the output that contains deletes from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="34eb0-139">詳細エディターを開いて変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-139">Open the Advanced Editor to configure the transformation.</span></span>  
  
4.  <span data-ttu-id="34eb0-140">**[OLE DB コマンドの詳細エディター]** の **[接続マネージャー]** タブで、変換先データベースの OLE DB 接続マネージャーを選択または作成します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-140">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
5.  <span data-ttu-id="34eb0-141">**[OLE DB コマンドの詳細エディター]** の **[コンポーネントのプロパティ]** タブの **[SqlCommand]** に、パラメーター化された DELETE ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-141">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab of the editor, for **SqlCommand**, enter a parameterized DELETE statement.</span></span>  
  
     <span data-ttu-id="34eb0-142">たとえば、Customer テーブルの DELETE ステートメントの構文は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="34eb0-142">For example, a DELETE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    delete from Customer where CustomerID = ?  
  
    ```  
  
6.  <span data-ttu-id="34eb0-143">エディターの **[列マッピング]** タブで、変更データの適切な列を DELETE ステートメントのパラメーターにマップします。</span><span class="sxs-lookup"><span data-stu-id="34eb0-143">On the **Column Mappings** tab of the editor, map the appropriate column from the change data to the parameter in the DELETE statement.</span></span>  
  
## <a name="optimizing-inserts-and-updates-by-using-merge-functionality"></a><span data-ttu-id="34eb0-144">MERGE 機能を使用した挿入と更新の最適化</span><span class="sxs-lookup"><span data-stu-id="34eb0-144">Optimizing Inserts and Updates by Using MERGE Functionality</span></span>  
 <span data-ttu-id="34eb0-145">特定の変更データ キャプチャ オプションと Transact-SQL の MERGE キーワードを組み合わせて使用することによって、挿入と更新の処理を最適化できます。</span><span class="sxs-lookup"><span data-stu-id="34eb0-145">You can optimize the processing of inserts and updates by combining certain change data capture options with the use of the Transact-SQL MERGE keyword.</span></span> <span data-ttu-id="34eb0-146">MERGE キーワードの詳細については、「[MERGE (Transact-SQL)](/sql/t-sql/statements/merge-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34eb0-146">For more information about the MERGE keyword, see [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql).</span></span>  
  
 <span data-ttu-id="34eb0-147">変更データを取得する Transact-SQL ステートメントで、**cdc.fn_cdc_get_net_changes_<capture_instance>** 関数を呼び出すときに、*row_filter_option* パラメーターの値として *all with merge* を指定できます。</span><span class="sxs-lookup"><span data-stu-id="34eb0-147">In the Transact-SQL statement that retrieves the change data, you can specify *all with merge* as the value of the *row_filter_option* parameter when you call the **cdc.fn_cdc_get_net_changes_<capture_instance>** function.</span></span> <span data-ttu-id="34eb0-148">この変更データ キャプチャの関数は、挿入と更新を区別するために必要な追加の処理を実行する必要がない場合、効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="34eb0-148">This change data capture function operates more efficiently when it does not have to perform the extra processing that is required to distinguish inserts from updates.</span></span> <span data-ttu-id="34eb0-149">*all with merge* パラメーター値を指定すると、変更データの **__$operation** 値は、削除の場合は 1、挿入または更新によって生じた変更の場合は 5 になります。</span><span class="sxs-lookup"><span data-stu-id="34eb0-149">When you specify the *all with merge* parameter value, the **__$operation** value of the change data is 1 for deletes or 5 for changes that were caused by inserts or updates.</span></span> <span data-ttu-id="34eb0-150">変更データの取得に使用する Transact-SQL 関数の詳細については、「 [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)」を参照してください。 *all with merge* パラメーター値を使用して変更を取得したら、削除を適用して、残りの行を一時テーブルまたはステージング テーブルに出力することができます。</span><span class="sxs-lookup"><span data-stu-id="34eb0-150">For more information about the Transact-SQL function that is used to retrieve the change data, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).After retrieving changes with the *all with merge* parameter value, you can apply deletes, and output the remaining rows to a temporary table or a staging table.</span></span> <span data-ttu-id="34eb0-151">その後、下流の SQL 実行タスクで単一の MERGE ステートメントを使用して、すべての挿入または更新をステージング テーブルから変換先に適用できます。</span><span class="sxs-lookup"><span data-stu-id="34eb0-151">Then, in a downstream Execute SQL Task, you can use a single MERGE statement to apply all the inserts or updates from the staging table to the destination.</span></span>  
  
  
