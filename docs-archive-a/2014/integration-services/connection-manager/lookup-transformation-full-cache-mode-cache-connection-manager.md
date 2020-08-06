---
title: キャッシュ接続マネージャーを使用してフルキャッシュモードの参照変換を実装する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: 58bc7611-5fb5-4113-9742-10959e06b94c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b8c77f7ecfbe79db00acce09f706468ec0a0055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644107"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-cache-connection-manager"></a><span data-ttu-id="49bf6-102">キャッシュ接続マネージャーの変換を使用してフル キャッシュ モードの参照変換を実装する</span><span class="sxs-lookup"><span data-stu-id="49bf6-102">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>
  <span data-ttu-id="49bf6-103">フル キャッシュ モードおよびキャッシュ接続マネージャーを使用するように参照変換を構成できます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-103">You can configure the Lookup transformation to use full cache mode and a Cache connection manager.</span></span> <span data-ttu-id="49bf6-104">フル キャッシュ モードでは、参照変換の実行前に参照データセットがキャッシュに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-104">In full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49bf6-105">キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="49bf6-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="49bf6-106">参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="49bf6-107">**[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="49bf6-108">詳細については、「 [キャッシュ接続マネージャー エディター](../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-108">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="49bf6-109">参照変換は、接続されているデータ ソースの入力列のデータを参照データセットの列と結合することにより参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-109">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="49bf6-110">詳細については、「 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-110">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="49bf6-111">参照データセットを生成するには、次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-111">You use one of the following to generate a reference dataset:</span></span>  
  
-   <span data-ttu-id="49bf6-112">キャッシュ ファイル (.caw)</span><span class="sxs-lookup"><span data-stu-id="49bf6-112">Cache file (.caw)</span></span>  
  
     <span data-ttu-id="49bf6-113">既存のキャッシュ ファイルからデータを読み取るようにキャッシュ接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-113">You configure the Cache connection manager to read data from an existing cache file.</span></span>  
  
-   <span data-ttu-id="49bf6-114">データ フロー内の接続されているデータ ソース</span><span class="sxs-lookup"><span data-stu-id="49bf6-114">Connected data source in the data flow</span></span>  
  
     <span data-ttu-id="49bf6-115">キャッシュ変換を使用して、データ フロー内の接続されているデータ ソースのデータをキャッシュ接続マネージャーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-115">You use a Cache Transform transformation to write data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="49bf6-116">データは常にメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-116">The data is always stored in memory.</span></span>  
  
     <span data-ttu-id="49bf6-117">参照変換は、別のデータ フローに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-117">You must add the Lookup transformation to a separate data flow.</span></span> <span data-ttu-id="49bf6-118">これにより、参照変換を実行する前に、キャッシュ変換でキャッシュ接続マネージャーにデータを設定できます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-118">This enables the Cache Transform to populate the Cache connection manager before the Lookup transformation is executed.</span></span> <span data-ttu-id="49bf6-119">データ フローは、同じパッケージに含まれていても、2 つの異なるパッケージに含まれていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="49bf6-119">The data flows can be in the same package or in two separate packages.</span></span>  
  
     <span data-ttu-id="49bf6-120">データ フローが同じパッケージに含まれている場合は、優先順位制約を使用してデータ フローを接続します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-120">If the data flows are in the same package, use a precedence constraint to connect the data flows.</span></span> <span data-ttu-id="49bf6-121">これにより、参照変換を実行する前にキャッシュ変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-121">This enables the Cache Transform to run before the Lookup transformation runs.</span></span>  
  
     <span data-ttu-id="49bf6-122">データ フローが異なるパッケージに含まれている場合は、パッケージ実行タスクを使用して、親パッケージから子パッケージを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-122">If the data flows are in separate packages, you can use the Execute Package task to call the child package from the parent package.</span></span> <span data-ttu-id="49bf6-123">複数の子パッケージを呼び出すには、親パッケージ内のシーケンス コンテナー タスクに複数のパッケージ実行タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-123">You can call multiple child packages by adding multiple Execute Package tasks to a Sequence Container task in the parent package.</span></span>  
  
 <span data-ttu-id="49bf6-124">次のいずれかの方法を使用して、キャッシュに格納された参照データセットを複数の参照変換で共有できます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-124">You can share the reference dataset stored in cache, between multiple Lookup transformations by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="49bf6-125">単一のパッケージ内の参照変換で同じキャッシュ接続マネージャーが使用されるように構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-125">Configure the Lookup transformations in a single package to use the same Cache connection manager.</span></span>  
  
-   <span data-ttu-id="49bf6-126">異なるパッケージ内のキャッシュ接続マネージャーで同じキャッシュ ファイルが使用されるように構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-126">Configure the Cache connection managers in different packages to use the same cache file.</span></span>  
  
 <span data-ttu-id="49bf6-127">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-127">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="49bf6-128">キャッシュ変換</span><span class="sxs-lookup"><span data-stu-id="49bf6-128">Cache Transform</span></span>](../data-flow/transformations/cache-transform.md)  
  
-   [<span data-ttu-id="49bf6-129">キャッシュ接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="49bf6-129">Cache Connection Manager</span></span>](cache-connection-manager.md)  
  
-   [<span data-ttu-id="49bf6-130">優先順位制約</span><span class="sxs-lookup"><span data-stu-id="49bf6-130">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
-   [<span data-ttu-id="49bf6-131">パッケージ実行タスク</span><span class="sxs-lookup"><span data-stu-id="49bf6-131">Execute Package Task</span></span>](../control-flow/execute-package-task.md)  
  
-   [<span data-ttu-id="49bf6-132">シーケンス コンテナー</span><span class="sxs-lookup"><span data-stu-id="49bf6-132">Sequence Container</span></span>](../control-flow/sequence-container.md)  
  
 <span data-ttu-id="49bf6-133">キャッシュ接続マネージャーを使用してフル キャッシュ モードで参照変換を実装する方法のデモ ビデオについては、「 [フル キャッシュ モードで参照変換を実装する方法 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=131031)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-133">For a video that demonstrates how to implement a Lookup transformation in Full Cache mode using the Cache connection manager, see [How to: Implement a Lookup Transformation in Full Cache Mode (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131031).</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-one-package-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="49bf6-134">キャッシュ接続マネージャーおよびデータ フロー内のデータ ソースを使用して 1 つのパッケージでフル キャッシュ モードの参照変換を実装するには</span><span class="sxs-lookup"><span data-stu-id="49bf6-134">To implement a Lookup transformation in full cache mode in one package by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="49bf6-135">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開いてからパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-135">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="49bf6-136">**[制御フロー]** タブで、2 つのデータ フロー タスクを追加し、緑色のコネクタを使用してタスクを接続します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-136">On the **Control Flow** tab, add two Data Flow tasks, and then connect the tasks by using a green connector:</span></span>  
  
3.  <span data-ttu-id="49bf6-137">最初のデータ フローでキャッシュ変換を追加し、変換をデータ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-137">In the first data flow, add a Cache Transform transformation, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="49bf6-138">必要に応じて、データ ソースを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-138">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="49bf6-139">キャッシュ変換をダブルクリックし、 **[キャッシュ変換エディター]** の **[接続マネージャー]** ページで **[新規作成]** をクリックして、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-139">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="49bf6-140">**[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[列]** タブをクリックし、 **[インデックス位置]** オプションを使用して、インデックス列として使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-140">Click the **Columns** tab of the **Cache Connection Manager Editor** dialog box, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="49bf6-141">インデックス以外の列の場合、インデックス位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="49bf6-141">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="49bf6-142">インデックス列の場合、インデックスの位置は連続した正の数になります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-142">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-143">参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-143">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="49bf6-144">また、すべてのインデックス列をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-144">Also, all index columns must be mapped.</span></span> <span data-ttu-id="49bf6-145">詳細については、「 [キャッシュ接続マネージャー エディター](../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-145">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
6.  <span data-ttu-id="49bf6-146">キャッシュをファイルに保存するには、 **[キャッシュ接続マネージャー エディター]** の **[全般]** タブで、次のオプションを設定してキャッシュ接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-146">To save the cache to a file, in the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="49bf6-147">**[ファイル キャッシュを使用する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-147">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="49bf6-148">**[ファイル名]** にファイル パスを入力するか、 **[参照]** をクリックしてファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-148">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="49bf6-149">存在していないファイルのパスを入力した場合、パッケージを実行するとそのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-149">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-150">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="49bf6-150">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="49bf6-151">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-151">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="49bf6-152">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-152">You should enable access only to certain accounts.</span></span> <span data-ttu-id="49bf6-153">詳細については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-153">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
7.  <span data-ttu-id="49bf6-154">必要に応じてキャッシュ変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-154">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="49bf6-155">詳細については、「[キャッシュ変換エディター &#40;[接続マネージャー] ページ&#41;](../cache-transformation-editor-connection-manager-page.md)」および「[キャッシュ変換エディター &#40;[マッピング] ページ&#41;](../cache-transformation-editor-mappings-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-155">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="49bf6-156">2 番目のデータ フローで参照変換を追加し、次のタスクを実行して変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-156">In the second data flow, add a Lookup transformation, and then configure the transformation by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="49bf6-157">参照変換をデータ フローに連結します。連結するには、変換元または前の変換から参照変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-157">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-158">参照変換が空の日付フィールドを含むフラット ファイルに接続される場合、その変換は検証されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-158">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="49bf6-159">変換が検証されるかどうかは、フラット ファイルの接続マネージャーが NULL 値を保持するように構成されているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-159">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="49bf6-160">参照変換が検証されるようにするには、 **フラット ファイル ソース エディター**の **[接続マネージャー]** ページで、 **[データ ソースの NULL 値をデータ フローで NULL 値として保持する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-160">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="49bf6-161">変換元または前の変換をダブルクリックして、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-161">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="49bf6-162">参照変換をダブルクリックし、 **参照変換エディター**の **[全般]** ページで **[フル キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-162">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="49bf6-163">**[接続の種類]** 領域で、 **[キャッシュ接続マネージャー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-163">In the **Connection type** area, select **Cache connection manager**.</span></span>  
  
    5.  <span data-ttu-id="49bf6-164">**[一致するエントリがない行の処理方法の指定]** 一覧から、エラー処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-164">From the **Specify how to handle rows with no matching entries** list, select an error handling option.</span></span>  
  
    6.  <span data-ttu-id="49bf6-165">**[接続]** ページで、 **[キャッシュ接続マネージャー]** 一覧からキャッシュ接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-165">On the **Connection** page, from the **Cache connection manager** list, select a Cache connection manager.</span></span>  
  
    7.  <span data-ttu-id="49bf6-166">**[列]** ページをクリックし、 **[使用できる入力列]** 一覧の 1 列以上を **[使用できる参照列]** 一覧の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-166">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-167">参照変換は、同じ名前で同じデータ型を持つ列を自動的にマップします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-167">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-168">列をマップするには、データ型が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-168">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="49bf6-169">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-169">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="49bf6-170">**[使用できる参照列]** 一覧で列を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-170">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="49bf6-171">次に、 **[参照操作]** 一覧で、参照列の値を入力列の値と置き換えるか、新しい列に書き出すかを指定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-171">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="49bf6-172">エラー出力を構成するには、 **[エラー出力]** ページをクリックし、エラー処理オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-172">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="49bf6-173">詳細については、「[[参照変換エディター] ([エラー出力] ページ)](../lookup-transformation-editor-error-output-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-173">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="49bf6-174">**[OK]** をクリックして、参照変換への変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-174">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="49bf6-175">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-175">Run the package.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-two-packages-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="49bf6-176">キャッシュ接続マネージャーおよびデータ フロー内のデータ ソースを使用して 2 つのパッケージでフル キャッシュ モードの参照変換を実装するには</span><span class="sxs-lookup"><span data-stu-id="49bf6-176">To implement a Lookup transformation in full cache mode in two packages by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="49bf6-177">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開き、2 つのパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-177">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open two packages.</span></span>  
  
2.  <span data-ttu-id="49bf6-178">各パッケージの [制御フロー] タブで、データ フロー タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-178">On the Control Flow tab in each package, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="49bf6-179">親パッケージで、データ フローにキャッシュ変換を追加し、変換をデータ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-179">In the parent package, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="49bf6-180">必要に応じて、データ ソースを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-180">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="49bf6-181">キャッシュ変換をダブルクリックし、 **[キャッシュ変換エディター]** の **[接続マネージャー]** ページで **[新規作成]** をクリックして、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-181">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="49bf6-182">**[キャッシュ接続マネージャー エディター]** の **[全般]** タブで、次のオプションを設定してキャッシュ接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-182">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="49bf6-183">**[ファイル キャッシュを使用する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-183">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="49bf6-184">**[ファイル名]** にファイル パスを入力するか、 **[参照]** をクリックしてファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-184">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="49bf6-185">存在していないファイルのパスを入力した場合、パッケージを実行するとそのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-185">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-186">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="49bf6-186">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="49bf6-187">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-187">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="49bf6-188">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-188">You should enable access only to certain accounts.</span></span> <span data-ttu-id="49bf6-189">詳細については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-189">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="49bf6-190">**[列]** タブをクリックし、 **[インデックス位置]** オプションを使用して、インデックス列として使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-190">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="49bf6-191">インデックス以外の列の場合、インデックス位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="49bf6-191">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="49bf6-192">インデックス列の場合、インデックスの位置は連続した正の数になります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-192">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-193">参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-193">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="49bf6-194">また、すべてのインデックス列をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-194">Also, all index columns must be mapped.</span></span> <span data-ttu-id="49bf6-195">詳細については、「 [キャッシュ接続マネージャー エディター](../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-195">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="49bf6-196">必要に応じてキャッシュ変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-196">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="49bf6-197">詳細については、「[キャッシュ変換エディター &#40;[接続マネージャー] ページ&#41;](../cache-transformation-editor-connection-manager-page.md)」および「[キャッシュ変換エディター &#40;[マッピング] ページ&#41;](../cache-transformation-editor-mappings-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-197">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="49bf6-198">次のいずれかの操作を実行し、2 番目のパッケージで使用されるキャッシュ接続マネージャーにデータを設定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-198">Do one of the following to populate the Cache connection manager that is used in the second package:</span></span>  
  
    -   <span data-ttu-id="49bf6-199">親パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-199">Run the parent package.</span></span>  
  
    -   <span data-ttu-id="49bf6-200">手順 4. で作成したキャッシュ接続マネージャーをダブルクリックし、 **[列]** をクリックして、行を選択し、Ctrl キーを押しながら C キーを押して列のメタデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-200">Double-click the Cache connection manager you created in step 4, click **Columns**, select the rows, and then press CTRL+C to copy the column metadata.</span></span>  
  
9. <span data-ttu-id="49bf6-201">子パッケージで、キャッシュ接続マネージャーを作成します。その場合、 **[接続マネージャー]** 領域内を右クリックして **[新しい接続]** をクリックし、 **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[CACHE] を選択し** 、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-201">In the child package, create a Cache connection manager by right-clicking in the **Connection Managers** area, clicking **New Connection**, selecting **CACHE** in the **Add SSIS Connection Manager** dialog box, and then clicking **Add**.</span></span>  
  
     <span data-ttu-id="49bf6-202">**デザイナーの** [制御フロー] **タブ、** [データ フロー] **タブ、および**[イベント ハンドラー] **タブの下部に、** [接続マネージャー] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-202">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
10. <span data-ttu-id="49bf6-203">**[キャッシュ接続マネージャー エディター]** の **[全般]** タブで、次のオプションを設定して選択したキャッシュ ファイルからデータを読み取るようにキャッシュ接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-203">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to read the data from the cache file that you selected by setting the following options:</span></span>  
  
    -   <span data-ttu-id="49bf6-204">**[ファイル キャッシュを使用する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-204">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="49bf6-205">**[ファイル名]** にファイル パスを入力するか、 **[参照]** をクリックしてファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-205">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-206">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="49bf6-206">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="49bf6-207">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-207">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="49bf6-208">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-208">You should enable access only to certain accounts.</span></span> <span data-ttu-id="49bf6-209">詳細については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-209">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
11. <span data-ttu-id="49bf6-210">手順 8. で列のメタデータをコピーした場合、 **[列]** をクリックして空白行を選択し、Ctrl キーを押しながら V キーを押して列のメタデータを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-210">If you copied the column metadata in step 8, click **Columns**, select the empty row, and then press CTRL+V to paste the column metadata.</span></span>  
  
12. <span data-ttu-id="49bf6-211">参照変換を追加し、次の操作を行って変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-211">Add a Lookup transformation, and then configure the transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="49bf6-212">参照変換をデータ フローに連結します。連結するには、変換元または前の変換から参照変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-212">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-213">参照変換が空の日付フィールドを含むフラット ファイルに接続される場合、その変換は検証されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-213">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="49bf6-214">変換が検証されるかどうかは、フラット ファイルの接続マネージャーが NULL 値を保持するように構成されているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-214">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="49bf6-215">参照変換が検証されるようにするには、 **フラット ファイル ソース エディター**の **[接続マネージャー]** ページで、 **[データ ソースの NULL 値をデータ フローで NULL 値として保持する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-215">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="49bf6-216">変換元または前の変換をダブルクリックして、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-216">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="49bf6-217">参照変換をダブルクリックし、 **[参照変換エディター]** の **[全般]** ページで **[フル キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-217">Double-click the Lookup transformation, and then select **Full cache** on the **General** page of the **Lookup Transformation Editor**.</span></span>  
  
    4.  <span data-ttu-id="49bf6-218">**[接続の種類]** 領域で、 **[キャッシュ接続マネージャー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-218">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="49bf6-219">**[一致するエントリがない行の処理方法の指定]** 一覧で、一致するエントリがない行のエラー処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-219">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="49bf6-220">**[接続]** ページの **[キャッシュ接続マネージャー]** 一覧から、追加したキャッシュ接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-220">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="49bf6-221">**[列]** ページをクリックし、 **[使用できる入力列]** 一覧の 1 列以上を **[使用できる参照列]** 一覧の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-221">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-222">参照変換は、同じ名前で同じデータ型を持つ列を自動的にマップします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-222">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-223">列をマップするには、データ型が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-223">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="49bf6-224">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-224">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="49bf6-225">**[使用できる参照列]** 一覧で列を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-225">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="49bf6-226">次に、 **[参照操作]** 一覧で、参照列の値を入力列の値と置き換えるか、新しい列に書き出すかを指定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-226">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="49bf6-227">エラー出力を構成するには、 **[エラー出力]** ページをクリックし、エラー処理オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-227">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="49bf6-228">詳細については、「[[参照変換エディター] ([エラー出力] ページ)](../lookup-transformation-editor-error-output-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-228">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="49bf6-229">**[OK]** をクリックして、参照変換への変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-229">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
13. <span data-ttu-id="49bf6-230">親パッケージを開き、パッケージ実行タスクを制御フローに追加して、子パッケージを呼び出すようにタスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-230">Open the parent package, add an Execute Package task to the control flow, and then configure the task to call the child package.</span></span> <span data-ttu-id="49bf6-231">詳細については、「 [パッケージ実行タスク](../control-flow/execute-package-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-231">For more information, see [Execute Package Task](../control-flow/execute-package-task.md).</span></span>  
  
14. <span data-ttu-id="49bf6-232">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-232">Run the packages.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-cache-connection-manager-and-an-existing-cache-file"></a><span data-ttu-id="49bf6-233">キャッシュ接続マネージャーおよび既存のキャッシュ ファイルを使用してフル キャッシュ モードの参照変換を実装するには</span><span class="sxs-lookup"><span data-stu-id="49bf6-233">To implement a Lookup transformation in full cache mode by using Cache connection manager and an existing cache file</span></span>  
  
1.  <span data-ttu-id="49bf6-234">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開いてからパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-234">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="49bf6-235">**[接続マネージャー]** 領域内を右クリックし、 **[新しい接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-235">Right-click in the **Connection Managers** area, and then click **New Connection**.</span></span>  
  
     <span data-ttu-id="49bf6-236">**デザイナーの** [制御フロー] **タブ、** [データ フロー] **タブ、および**[イベント ハンドラー] **タブの下部に、** [接続マネージャー] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-236">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
3.  <span data-ttu-id="49bf6-237">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[CACHE]** を選択し、 **[追加]** をクリックしてキャッシュ接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-237">In the **Add SSIS Connection Manager** dialog box, select **CACHE**, and then click **Add** to add a Cache connection manager.</span></span>  
  
4.  <span data-ttu-id="49bf6-238">キャッシュ接続マネージャーをダブルクリックして、 **[キャッシュ接続マネージャー エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-238">Double-click the Cache connection manager to open the **Cache Connection Manager Editor**.</span></span>  
  
5.  <span data-ttu-id="49bf6-239">**[キャッシュ接続マネージャー エディター]** の **[全般]** タブで、次のオプションを設定してキャッシュ接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-239">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="49bf6-240">**[ファイル キャッシュを使用する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-240">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="49bf6-241">**[ファイル名]** にファイル パスを入力するか、 **[参照]** をクリックしてファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-241">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-242">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="49bf6-242">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="49bf6-243">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-243">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="49bf6-244">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-244">You should enable access only to certain accounts.</span></span> <span data-ttu-id="49bf6-245">詳細については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-245">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="49bf6-246">**[列]** タブをクリックし、 **[インデックス位置]** オプションを使用して、インデックス列として使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-246">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="49bf6-247">インデックス以外の列の場合、インデックス位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="49bf6-247">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="49bf6-248">インデックス列の場合、インデックスの位置は連続した正の数になります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-248">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49bf6-249">参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="49bf6-249">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="49bf6-250">また、すべてのインデックス列をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-250">Also, all index columns must be mapped.</span></span> <span data-ttu-id="49bf6-251">詳細については、「 [キャッシュ接続マネージャー エディター](../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-251">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="49bf6-252">**[制御フロー]** タブで、データ フロー タスクをパッケージに追加し、参照変換をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-252">On the **Control Flow** tab, add a Data Flow task to the package, and then add a Lookup transformation to the data flow.</span></span>  
  
8.  <span data-ttu-id="49bf6-253">次の操作を実行して参照変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-253">Configure the Lookup transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="49bf6-254">参照変換をデータ フローに連結します。連結するには、変換元または前の変換から参照変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-254">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-255">参照変換が空の日付フィールドを含むフラット ファイルに接続される場合、その変換は検証されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-255">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="49bf6-256">変換が検証されるかどうかは、フラット ファイルの接続マネージャーが NULL 値を保持するように構成されているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-256">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="49bf6-257">参照変換が検証されるようにするには、 **フラット ファイル ソース エディター**の **[接続マネージャー]** ページで、 **[データ ソースの NULL 値をデータ フローで NULL 値として保持する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-257">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="49bf6-258">変換元または前の変換をダブルクリックして、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-258">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="49bf6-259">参照変換をダブルクリックし、 **参照変換エディター**の **[全般]** ページで **[フル キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-259">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="49bf6-260">**[接続の種類]** 領域で、 **[キャッシュ接続マネージャー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-260">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="49bf6-261">**[一致するエントリがない行の処理方法の指定]** 一覧で、一致するエントリがない行のエラー処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-261">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="49bf6-262">**[接続]** ページの **[キャッシュ接続マネージャー]** 一覧から、追加したキャッシュ接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-262">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="49bf6-263">**[列]** ページをクリックし、 **[使用できる入力列]** 一覧の 1 列以上を **[使用できる参照列]** 一覧の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-263">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-264">参照変換は、同じ名前で同じデータ型を持つ列を自動的にマップします。</span><span class="sxs-lookup"><span data-stu-id="49bf6-264">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="49bf6-265">列をマップするには、データ型が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bf6-265">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="49bf6-266">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-266">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="49bf6-267">**[使用できる参照列]** 一覧で列を選択します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-267">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="49bf6-268">次に、 **[参照操作]** 一覧で、参照列の値を入力列の値と置き換えるか、新しい列に書き出すかを指定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-268">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="49bf6-269">エラー出力を構成するには、 **[エラー出力]** ページをクリックし、エラー処理オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-269">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="49bf6-270">詳細については、「[[参照変換エディター] ([エラー出力] ページ)](../lookup-transformation-editor-error-output-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="49bf6-270">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="49bf6-271">**[OK]** をクリックして、参照変換への変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-271">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="49bf6-272">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="49bf6-272">Run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bf6-273">参照</span><span class="sxs-lookup"><span data-stu-id="49bf6-273">See Also</span></span>  
 <span data-ttu-id="49bf6-274">[OLE DB 接続マネージャーを使用してフル キャッシュ モードの参照変換を実装する](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="49bf6-274">[Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="49bf6-275">[キャッシュなしモードまたは部分キャッシュ モードの参照を実装する](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="49bf6-275">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="49bf6-276">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="49bf6-276">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
