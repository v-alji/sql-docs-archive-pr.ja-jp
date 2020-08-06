---
title: OLE DB 接続マネージャーを使用してフルキャッシュモードの参照変換を実装する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: c4150e1b-bdff-4f7a-af4c-3401c34def83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f77a753dd71bc487d57492371906fc48bc114357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644106"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-ole-db-connection-manager"></a><span data-ttu-id="f3712-102">OLE DB 接続マネージャーを使用してフル キャッシュ モードの参照変換を実装する</span><span class="sxs-lookup"><span data-stu-id="f3712-102">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>
  <span data-ttu-id="f3712-103">フル キャッシュ モードおよび OLE DB 接続マネージャーを使用するように参照変換を構成できます。</span><span class="sxs-lookup"><span data-stu-id="f3712-103">You can configure the Lookup transformation to use full cache mode and an OLE DB connection manager.</span></span> <span data-ttu-id="f3712-104">フル キャッシュ モードでは、参照変換の実行前に参照データセットがキャッシュに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f3712-104">In the full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
 <span data-ttu-id="f3712-105">参照変換は、接続されているデータ ソースの入力列のデータを参照データセットの列と結合することにより参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="f3712-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="f3712-106">詳細については、「 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3712-106">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="f3712-107">OLE DB 接続マネージャーを使用するように参照変換を構成する場合は、テーブル、ビュー、または SQL クエリを選択して参照データセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="f3712-107">When you configure the Lookup transformation to use an OLE DB connection manager, you select a table, view, or SQL query to generate the reference dataset.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-ole-db-connection-manager"></a><span data-ttu-id="f3712-108">OLE DB 接続マネージャーを使用してフル キャッシュ モードの参照変換を実装するには</span><span class="sxs-lookup"><span data-stu-id="f3712-108">To implement a Lookup transformation in full cache mode by using OLE DB connection manager</span></span>  
  
1.  <span data-ttu-id="f3712-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開き、ソリューション エクスプローラーでそのパッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3712-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want, and then double-click the package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="f3712-110">**[データ フロー]** タブで、 **[ツールボックス]** から参照変換をデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f3712-110">On the **Data Flow** tab, from the **Toolbox**, drag the Lookup transformation to the design surface.</span></span>  
  
3.  <span data-ttu-id="f3712-111">参照変換をデータ フローに連結します。連結するには、変換元または前の変換から参照変換にコネクタをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f3712-111">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3712-112">参照変換が空の日付フィールドを含むフラット ファイルに接続される場合、その変換は検証されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f3712-112">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="f3712-113">変換が検証されるかどうかは、フラット ファイルの接続マネージャーが NULL 値を保持するように構成されているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="f3712-113">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="f3712-114">参照変換が検証されるようにするには、 **フラット ファイル ソース エディター**の **[接続マネージャー]** ページで、 **[データ ソースの NULL 値をデータ フローで NULL 値として保持する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3712-114">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
4.  <span data-ttu-id="f3712-115">変換元または前の変換をダブルクリックして、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f3712-115">Double-click the source or previous transformation to configure the component.</span></span>  
  
5.  <span data-ttu-id="f3712-116">参照変換をダブルクリックし、 **参照変換エディター**の **[全般]** ページで **[フル キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3712-116">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
6.  <span data-ttu-id="f3712-117">**[接続の種類]** 領域で、 **[OLE DB 接続マネージャー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3712-117">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
7.  <span data-ttu-id="f3712-118">**[エントリが一致しない行の処理方法を指定する]** ボックスの一覧で、一致するエントリがない行のエラー処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3712-118">In the **Specify how to handle rows with no matching entries** list, select an error handling option for rows without matching entries.</span></span>  
  
8.  <span data-ttu-id="f3712-119">[接続] ページで、 **[OLE DB 接続マネージャー]** ボックスの一覧から接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3712-119">On the Connection page, select a connection manager from the **OLE DB connection manager** list or click **New** to create a new connection manager.</span></span> <span data-ttu-id="f3712-120">詳細については、「 [OLE DB 接続マネージャー](ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3712-120">For more information, see [OLE DB Connection Manager](ole-db-connection-manager.md).</span></span>  
  
9. <span data-ttu-id="f3712-121">次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f3712-121">Do one of the following tasks:</span></span>  
  
    -   <span data-ttu-id="f3712-122">**[テーブルまたはビューを使用する]** をクリックし、テーブルまたはビューを選択するか、 **[新規作成]** をクリックしてテーブルまたはビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3712-122">Click **Use a table or a view**, and then either select a table or view, or click **New** to create a table or view.</span></span>  
  
         <span data-ttu-id="f3712-123">または</span><span class="sxs-lookup"><span data-stu-id="f3712-123">-or-</span></span>  
  
    -   <span data-ttu-id="f3712-124">**[SQL クエリの結果を使用する]** をクリックし、 **[SQL コマンド]** ウィンドウでクエリを作成するか、 **[クエリの作成]** をクリックし、 **[クエリ ビルダー]** に用意されているグラフィック ツールを使用してクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3712-124">Click **Use results of an SQL query**, and then build a query in the **SQL Command** window, or click **Build Query** to build a query by using the graphical tools that the **Query Builder** provides.</span></span>  
  
         <span data-ttu-id="f3712-125">または</span><span class="sxs-lookup"><span data-stu-id="f3712-125">-or-</span></span>  
  
    -   <span data-ttu-id="f3712-126">**[参照]** をクリックして、ファイルから SQL ステートメントをインポートします。</span><span class="sxs-lookup"><span data-stu-id="f3712-126">Alternatively, click **Browse** to import an SQL statement from a file.</span></span>  
  
     <span data-ttu-id="f3712-127">SQL クエリを検証するには、 **[クエリの解析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3712-127">To validate the SQL query, click **Parse Query**.</span></span>  
  
     <span data-ttu-id="f3712-128">データのサンプルを表示するには、 **[プレビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3712-128">To view a sample of the data, click **Preview**.</span></span>  
  
10. <span data-ttu-id="f3712-129">**[列]** ページをクリックし、 **[使用できる入力列]** ボックスの一覧から 1 列以上を **[使用できる参照列]** ボックスの一覧の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f3712-129">Click the **Columns** page, and then from the **Available Input Columns** list, drag at least one column to a column in the **Available Lookup Column** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3712-130">参照変換は、同じ名前で同じデータ型を持つ列を自動的にマップします。</span><span class="sxs-lookup"><span data-stu-id="f3712-130">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3712-131">列をマップするには、データ型が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3712-131">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="f3712-132">詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3712-132">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
11. <span data-ttu-id="f3712-133">次のタスクを実行して、参照列を出力に追加します。</span><span class="sxs-lookup"><span data-stu-id="f3712-133">Include lookup columns in the output by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="f3712-134">**[使用できる参照列]** ボックスの一覧で、</span><span class="sxs-lookup"><span data-stu-id="f3712-134">In the **Available Lookup Columns** list.</span></span> <span data-ttu-id="f3712-135">列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3712-135">select columns.</span></span>  
  
    2.  <span data-ttu-id="f3712-136">**[参照操作]** ボックスの一覧で、参照列の値を入力列の値と置き換えるか、新しい列に書き出すかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3712-136">In **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
12. <span data-ttu-id="f3712-137">エラー出力を構成するには、 **[エラー出力]** ページをクリックし、エラー処理オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="f3712-137">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="f3712-138">詳細については、「[[参照変換エディター] ([エラー出力] ページ)](../lookup-transformation-editor-error-output-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f3712-138">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
13. <span data-ttu-id="f3712-139">**[OK]** をクリックして参照変換への変更を保存し、パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="f3712-139">Click **OK** to save your changes to the Lookup transformation, and then run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3712-140">参照</span><span class="sxs-lookup"><span data-stu-id="f3712-140">See Also</span></span>  
 <span data-ttu-id="f3712-141">[キャッシュ接続マネージャーを使用してフル キャッシュ モードの参照変換を実装する](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f3712-141">[Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="f3712-142">[キャッシュなしモードまたは部分キャッシュ モードの参照を実装する](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f3712-142">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="f3712-143">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="f3712-143">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
