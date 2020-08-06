---
title: 複数のテーブルの増分読み込みを実行する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],multiple tables
ms.assetid: 39252dd5-09c3-46f9-a17b-15208cfd336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf81d1d529e8102271c66839440ef712219600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633273"
---
# <a name="perform-an-incremental-load-of-multiple-tables"></a><span data-ttu-id="cb256-102">複数のテーブルの増分読み込みを実行する</span><span class="sxs-lookup"><span data-stu-id="cb256-102">Perform an Incremental Load of Multiple Tables</span></span>
  <span data-ttu-id="cb256-103">「 [変更データ キャプチャによる増分読み込みの向上](change-data-capture-ssis.md)」の図は、1 つのみのテーブルの増分読み込みを実行する基本的なパッケージを示しています。</span><span class="sxs-lookup"><span data-stu-id="cb256-103">In the topic, [Improving Incremental Loads with Change Data Capture](change-data-capture-ssis.md), the diagram illustrates a basic package that performs an incremental load on just one table.</span></span> <span data-ttu-id="cb256-104">ただし、1 つのテーブルの読み込みよりも、複数のテーブルの増分読み込みを実行する必要がある場合の方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="cb256-104">However, loading one table is not as common as having to perform an incremental load of multiple tables.</span></span>  
  
 <span data-ttu-id="cb256-105">複数のテーブルの増分読み込みを実行する場合の手順には、すべてのテーブルに対して一度実行する必要があるものと、ソース テーブルごとに繰り返し実行する必要があるものがあります。</span><span class="sxs-lookup"><span data-stu-id="cb256-105">When you perform an incremental load of multiple tables, some steps have to be performed once for all the tables, and other steps have to be repeated for each source table.</span></span> <span data-ttu-id="cb256-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]でこれらの手順を実装する方法は複数あります。</span><span class="sxs-lookup"><span data-stu-id="cb256-106">You have more than one option for implementing these steps in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="cb256-107">親パッケージと子パッケージを使用する。</span><span class="sxs-lookup"><span data-stu-id="cb256-107">Use a parent package and child packages.</span></span>  
  
-   <span data-ttu-id="cb256-108">1 つのパッケージ内の複数のデータ フロー タスクを使用する。</span><span class="sxs-lookup"><span data-stu-id="cb256-108">Use multiple Data Flow tasks in a single package.</span></span>  
  
## <a name="loading-multiple-tables-by-using-a-parent-package-and-multiple-child-packages"></a><span data-ttu-id="cb256-109">親パッケージと複数の子パッケージを使用した複数のテーブルの読み込み</span><span class="sxs-lookup"><span data-stu-id="cb256-109">Loading Multiple Tables by Using a Parent Package and Multiple Child Packages</span></span>  
 <span data-ttu-id="cb256-110">親パッケージを使用して、一度実行するだけで済む手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb256-110">You can use a parent package to perform those steps that only have to be done once.</span></span> <span data-ttu-id="cb256-111">子パッケージでは、ソース テーブルごとに実行する必要がある手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cb256-111">The child packages will perform those steps that have to be done for each source table.</span></span>  
  
#### <a name="to-create-a-parent-package-that-performs-those-steps-that-only-have-to-be-done-once"></a><span data-ttu-id="cb256-112">一度実行するだけで済む手順を実行する親パッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb256-112">To create a parent package that performs those steps that only have to be done once</span></span>  
  
1.  <span data-ttu-id="cb256-113">親パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-113">Create a parent package.</span></span>  
  
2.  <span data-ttu-id="cb256-114">制御フローで、SQL 実行タスクまたは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式を使用してエンドポイントを計算します。</span><span class="sxs-lookup"><span data-stu-id="cb256-114">In the control flow, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="cb256-115">エンドポイントの計算方法の例については、「 [変更データの間隔を指定する](specify-an-interval-of-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-115">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="cb256-116">必要に応じて、選択した期間の変更データが準備できるまで実行を遅延させる For ループ コンテナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-116">If needed, use a For Loop container to delay execution until change data for the selected period is ready.</span></span>  
  
     <span data-ttu-id="cb256-117">このような For ループ コンテナーの例については、「 [データの変更の準備ができているかどうかを判断する](determine-whether-the-change-data-is-ready.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-117">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="cb256-118">複数のパッケージ実行タスクを使用して、読み込むテーブルごとに子パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="cb256-118">Use multiple Execute Package tasks to execute child packages for each table to be loaded.</span></span> <span data-ttu-id="cb256-119">親パッケージ変数の構成を使用して、親パッケージで計算したエンドポイントを各子パッケージに渡します。</span><span class="sxs-lookup"><span data-stu-id="cb256-119">Pass the endpoints calculated in the parent package to each child package by using Parent Package Variable configurations.</span></span>  
  
     <span data-ttu-id="cb256-120">詳細については、「 [パッケージ実行タスク](../control-flow/execute-package-task.md) 」および「 [子パッケージでの変数およびパラメーターの値の使用](../use-the-values-of-variables-and-parameters-in-a-child-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-120">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
#### <a name="to-create-child-packages-to-perform-those-steps-that-have-to-be-done-for-each-source-table"></a><span data-ttu-id="cb256-121">ソース テーブルごとに実行する必要がある手順を実行する子パッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb256-121">To create child packages to perform those steps that have to be done for each source table</span></span>  
  
1.  <span data-ttu-id="cb256-122">ソース テーブルごとに子パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-122">For each source table, create a child package.</span></span>  
  
2.  <span data-ttu-id="cb256-123">制御フローで、スクリプト タスクまたは SQL 実行タスクを使用して、変更をクエリで確認するために使用する SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-123">In the control flow, use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="cb256-124">クエリの作成方法の例については、「 [変更データのクエリを準備する](prepare-to-query-for-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-124">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
3.  <span data-ttu-id="cb256-125">子パッケージごとに 1 つのデータ フロー タスクを使用して、変更データを読み込んで変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-125">Use a single Data Flow task in each child package to load the change data and apply it to the destination.</span></span> <span data-ttu-id="cb256-126">次の手順に従って、データ フローを構成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-126">Configure the Data Flow as described in the following steps:</span></span>  
  
    1.  <span data-ttu-id="cb256-127">データ フローで、変換元コンポーネントを使用して、選択したエンドポイント内にある変更をクエリで変更テーブルから取得します。</span><span class="sxs-lookup"><span data-stu-id="cb256-127">In the data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="cb256-128">変更テーブルに対するクエリの実行方法の例については、「 [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-128">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="cb256-129">条件分割変換を使用して、適切な処理のために挿入、更新、および削除を異なる出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="cb256-129">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="cb256-130">この変換を構成して出力先を分ける方法の例については、「 [挿入、更新、および削除を処理する](process-inserts-updates-and-deletes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-130">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="cb256-131">変換先コンポーネントを使用して、挿入を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-131">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="cb256-132">OLE DB コマンド変換とパラメーター化された UPDATE および DELETE ステートメントを使用して、更新と削除を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-132">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="cb256-133">この変換を使用して更新と削除を適用する方法の例については、「 [変換先に変更を適用する](apply-the-changes-to-the-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-133">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
## <a name="loading-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="cb256-134">1 つのパッケージ内の複数のデータ フロー タスクを使用した複数のテーブルの読み込み</span><span class="sxs-lookup"><span data-stu-id="cb256-134">Loading Multiple Tables by Using Multiple Data Flow Tasks in a Single Package</span></span>  
 <span data-ttu-id="cb256-135">読み込むソース テーブルごとに個別のデータ フロー タスクを用意している 1 つのパッケージを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb256-135">Alternatively, you can use a single package that contains a separate Data Flow task for each source table to be loaded.</span></span>  
  
#### <a name="to-load-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="cb256-136">1 つのパッケージ内の複数のデータ フロー タスクを使用して複数のテーブルを読み込むには</span><span class="sxs-lookup"><span data-stu-id="cb256-136">To load multiple tables by using multiple Data Flow tasks in a single package</span></span>  
  
1.  <span data-ttu-id="cb256-137">1 つのパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-137">Create a single package.</span></span>  
  
2.  <span data-ttu-id="cb256-138">制御フローで、SQL 実行タスクまたは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式を使用してエンドポイントを計算します。</span><span class="sxs-lookup"><span data-stu-id="cb256-138">In the control flow, use an Execute SQL Task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="cb256-139">エンドポイントの計算方法の例については、「 [変更データの間隔を指定する](specify-an-interval-of-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-139">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="cb256-140">必要に応じて、選択した間隔の変更データが準備できるまで実行を遅延させる For ループ コンテナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-140">If needed, use a For Loop container to delay execution until the change data for the selected interval is ready.</span></span>  
  
     <span data-ttu-id="cb256-141">このような For ループ コンテナーの例については、「 [データの変更の準備ができているかどうかを判断する](determine-whether-the-change-data-is-ready.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-141">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="cb256-142">スクリプト タスクまたは SQL 実行タスクを使用して、変更をクエリで確認するために使用する SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-142">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="cb256-143">クエリの作成方法の例については、「 [変更データのクエリを準備する](prepare-to-query-for-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-143">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
5.  <span data-ttu-id="cb256-144">複数のデータ フロー タスクを使用して、各ソース テーブルから変更データを読み込んで変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-144">Use multiple Data Flow tasks to load the change data from each source table and apply it to the destination.</span></span> <span data-ttu-id="cb256-145">次の手順に従って、各データ フロー タスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="cb256-145">Configure each Data Flow task as described in the following steps.</span></span>  
  
    1.  <span data-ttu-id="cb256-146">各データ フローで、変換元コンポーネントを使用して、選択したエンドポイント内にある変更をクエリで変更テーブルから取得します。</span><span class="sxs-lookup"><span data-stu-id="cb256-146">In each data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="cb256-147">変更テーブルに対するクエリの実行方法の例については、「 [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-147">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="cb256-148">条件分割変換を使用して、適切な処理のために挿入、更新、および削除を異なる出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="cb256-148">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="cb256-149">この変換を構成して出力先を分ける方法の例については、「 [挿入、更新、および削除を処理する](process-inserts-updates-and-deletes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-149">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="cb256-150">変換先コンポーネントを使用して、挿入を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-150">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="cb256-151">OLE DB コマンド変換とパラメーター化された UPDATE および DELETE ステートメントを使用して、更新と削除を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="cb256-151">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="cb256-152">この変換を使用して更新と削除を適用する方法の例については、「 [変換先に変更を適用する](apply-the-changes-to-the-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb256-152">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
  
