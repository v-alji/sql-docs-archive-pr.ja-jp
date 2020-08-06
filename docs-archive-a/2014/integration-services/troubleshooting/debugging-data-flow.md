---
title: データ フローのデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- data viewers [Integration Services]
- data flow [Integration Services], debugging
- debugging [Integration Services], data flow
- counting rows
ms.assetid: 1c574f1b-54f7-4c05-8e42-8620e2c1df0f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed1d1b7ebb119d452ca3de92fdad47552d1cc36c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718441"
---
# <a name="debugging-data-flow"></a><span data-ttu-id="9d955-102">データ フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9d955-102">Debugging Data Flow</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9d955-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] と [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローのトラブルシューティングを行うために使用できる機能とツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9d955-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer include features and tools that you can use to troubleshoot the data flows in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="9d955-104">デザイナーでは、データ ビューアーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9d955-104">Designer provides data viewers.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="9d955-105">デザイナーと [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換では、行数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9d955-105">Designer and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations provide row counts.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="9d955-106">デザイナーでは、実行時の進行状況レポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9d955-106">Designer provides progress reporting at run time.</span></span>  
  
## <a name="data-viewers"></a><span data-ttu-id="9d955-107">データ ビューアー</span><span class="sxs-lookup"><span data-stu-id="9d955-107">Data Viewers</span></span>  
 <span data-ttu-id="9d955-108">データ ビューアーは、データ フローの 2 つのコンポーネント間のデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d955-108">Data viewers display data between two components in a data flow.</span></span> <span data-ttu-id="9d955-109">データ ビューアーでデータを表示できるのは、データ ソースからデータが抽出され、最初にデータ フローに入るときと、変換によりデータが更新される前後、およびデータが変換先に読み込まれる前です。</span><span class="sxs-lookup"><span data-stu-id="9d955-109">Data viewers can display data when the data is extracted from a data source and first enters a data flow, before and after a transformation updates the data, and before the data is loaded into its destination.</span></span>  
  
 <span data-ttu-id="9d955-110">データを表示するには、2 つのデータ フロー コンポーネントを連結するパスに、データ ビューアーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="9d955-110">To view the data, you attach data viewers to the path that connects two data flow components.</span></span> <span data-ttu-id="9d955-111">データ フロー コンポーネント間のデータを表示する機能を使用すると、予期しないデータ値の識別、変換による列の値の変更方法の表示、および変換が失敗した原因の検出が容易になります。</span><span class="sxs-lookup"><span data-stu-id="9d955-111">The ability to view data between data flow components makes it easier to identify unexpected data values, view the way a transformation changes column values, and discover the reason that a transformation fails.</span></span> <span data-ttu-id="9d955-112">たとえば、参照テーブル内の参照が失敗する場合、それを修正するために、既定データを空白の列に提供する変換を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9d955-112">For example, you may find that a lookup in a reference table fails, and to correct this you may want to add a transformation that provides default data for blank columns.</span></span>  
  
 <span data-ttu-id="9d955-113">データ ビューアーでは、グリッドにデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9d955-113">A data viewer can display data in a grid.</span></span> <span data-ttu-id="9d955-114">グリッドを使用する場合は、表示する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d955-114">Using a grid, you select the columns to display.</span></span> <span data-ttu-id="9d955-115">選択した列の値は、表形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d955-115">The values for the selected columns display in a tabular format.</span></span>  
  
 <span data-ttu-id="9d955-116">1 つのパスに、複数のデータ ビューアーを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="9d955-116">You can also include multiple data viewers on a path.</span></span> <span data-ttu-id="9d955-117">このため、同じデータをさまざまな形式で表示できます。たとえば、データのグラフ表示とグリッド表示を作成したり、データの列ごとに異なるデータ ビューアーを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="9d955-117">You can display the same data in different formats-for example, create a chart view and a grid view of the data-or create different data viewers for different columns of data.</span></span>  
  
 <span data-ttu-id="9d955-118">データ ビューアーをパスに追加すると、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは、 **[データ フロー]** タブのデザイン画面のパスの隣に、データ ビューアーのアイコンが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9d955-118">When you add a data viewer to a path, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer adds a data viewer icon to the design surface of the **Data Flow** tab, next to the path.</span></span> <span data-ttu-id="9d955-119">条件分割変換など、複数の出力を持つ変換には、パスごとにデータ ビューアーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9d955-119">Transformations that can have multiple outputs, such as the Conditional Split transformation, can include a data viewer on each path.</span></span>  
  
 <span data-ttu-id="9d955-120">実行時には **[データ ビューアー]** ウィンドウが開き、データ ビューアーの形式で指定された情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d955-120">At run time, a **Data Viewer** window opens and displays the information specified by the data viewer format.</span></span> <span data-ttu-id="9d955-121">たとえば、グリッド形式を使用するデータ ビューアーでは、選択した列のデータ、データ フロー コンポーネントに渡される出力列の数、および表示される行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d955-121">For example, a data viewer that uses the grid format shows data for the selected columns, the number of output rows passed to the data flow component, and the number of rows displayed.</span></span> <span data-ttu-id="9d955-122">この情報はバッファーごとに表示されますが、データ フローの行の幅に応じて、バッファーが表示する行数は増減します。</span><span class="sxs-lookup"><span data-stu-id="9d955-122">The information displays buffer by buffer and, depending on the width of the rows in the data flow, a buffer may contain more or fewer rows.</span></span>  
  
 <span data-ttu-id="9d955-123">**[データ ビューアー]** ダイアログ ボックスでは、クリップボードへのデータのコピー、テーブルのすべてのデータの消去、データ ビューアーの再構成、データのフローの再開、およびデータ ビューアーのデタッチまたはアタッチを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9d955-123">In the **Data Viewer** dialog box, you can copy the data to the Clipboard, clear all data from the table, reconfigure the data viewer, resume the flow of data, and detach or attach the data viewer.</span></span>  
  
#### <a name="to-add-a-data-viewer"></a><span data-ttu-id="9d955-124">データ ビューアーを追加するには</span><span class="sxs-lookup"><span data-stu-id="9d955-124">To add a data viewer</span></span>  
  
-   [<span data-ttu-id="9d955-125">データ フローにデータ ビューアーを追加する</span><span class="sxs-lookup"><span data-stu-id="9d955-125">Add a Data Viewer to a Data Flow</span></span>](../add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="row-counts"></a><span data-ttu-id="9d955-126">行数</span><span class="sxs-lookup"><span data-stu-id="9d955-126">Row Counts</span></span>  
 <span data-ttu-id="9d955-127">**デザイナーでは、** [データ フロー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブのデザイン画面のパスの隣に、パスを通過した行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d955-127">The number of rows that have passed through a path is displayed on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer next to the path.</span></span> <span data-ttu-id="9d955-128">データがパスを移動する間、表示される行数が定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="9d955-128">The number is updated periodically while the data moves through the path.</span></span>  
  
 <span data-ttu-id="9d955-129">また、データ フローに行数変換を追加して、最終的な行数を変数に取り込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="9d955-129">You can also add a Row Count transformation to the data flow to capture the final row count in a variable.</span></span> <span data-ttu-id="9d955-130">詳細については、「 [Row Count Transformation](../data-flow/transformations/row-count-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d955-130">For more information, see [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).</span></span>  
  
## <a name="progress-reporting"></a><span data-ttu-id="9d955-131">進行状況レポート</span><span class="sxs-lookup"><span data-stu-id="9d955-131">Progress Reporting</span></span>  
 <span data-ttu-id="9d955-132">パッケージを実行すると、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの **[データ フロー]** タブのデザイン画面に、各データ フロー コンポーネントが状態を示す色で表示され、進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9d955-132">When you run a package, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer depicts progress on the design surface of the **Data Flow** tab by displaying each data flow component in a color that indicates status.</span></span> <span data-ttu-id="9d955-133">各コンポーネントが作業を開始すると、コンポーネントは無色から黄色に変わり、正常に完了すると、緑色に変わります。</span><span class="sxs-lookup"><span data-stu-id="9d955-133">When each component starts to perform its work, it changes from no color to yellow, and when it finishes successfully, it changes to green.</span></span> <span data-ttu-id="9d955-134">赤色は、コンポーネントが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9d955-134">A red color indicates that the component failed.</span></span>  
  
 <span data-ttu-id="9d955-135">次の表では、色分けについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9d955-135">The following table describes the color-coding.</span></span>  
  
|<span data-ttu-id="9d955-136">Color</span><span class="sxs-lookup"><span data-stu-id="9d955-136">Color</span></span>|<span data-ttu-id="9d955-137">説明</span><span class="sxs-lookup"><span data-stu-id="9d955-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d955-138">無色</span><span class="sxs-lookup"><span data-stu-id="9d955-138">No color</span></span>|<span data-ttu-id="9d955-139">データ フロー エンジンによる呼び出しの待機中です。</span><span class="sxs-lookup"><span data-stu-id="9d955-139">Waiting to be called by the data flow engine.</span></span>|  
|<span data-ttu-id="9d955-140">黄</span><span class="sxs-lookup"><span data-stu-id="9d955-140">Yellow</span></span>|<span data-ttu-id="9d955-141">変換の実行、データの抽出、またはデータの読み込みを行っています。</span><span class="sxs-lookup"><span data-stu-id="9d955-141">Performing a transformation, extracting data, or loading data.</span></span>|  
|<span data-ttu-id="9d955-142">[緑]</span><span class="sxs-lookup"><span data-stu-id="9d955-142">Green</span></span>|<span data-ttu-id="9d955-143">正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="9d955-143">Ran successfully.</span></span>|  
|<span data-ttu-id="9d955-144">赤</span><span class="sxs-lookup"><span data-stu-id="9d955-144">red</span></span>|<span data-ttu-id="9d955-145">実行されましたがエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9d955-145">Ran with errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d955-146">参照</span><span class="sxs-lookup"><span data-stu-id="9d955-146">See Also</span></span>  
 [<span data-ttu-id="9d955-147">パッケージ開発のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="9d955-147">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
