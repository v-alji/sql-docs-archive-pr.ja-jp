---
title: クエリ (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90794aae8a3d664d47ab251ffdd954f22d48f992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738922"
---
# <a name="query-sql-server-data-mining-add-ins"></a><span data-ttu-id="f70c4-102">クエリ (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="f70c4-102">Query (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="f70c4-103">![[データ マイニング] リボンの [クエリ モデル] ボタン](media/dmc-query.gif "[データ マイニング] リボンの [クエリ モデル] ボタン")</span><span class="sxs-lookup"><span data-stu-id="f70c4-103">![Query Model button, Data Mining ribbon](media/dmc-query.gif "Query Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="f70c4-104">**クエリ**ウィザードを使用すると、既存のマイニングモデルを操作して、excel テーブル、excel 範囲、または別のデータソースのデータに基づいて予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-104">The **Query** wizard helps you interact with existing mining models to make predictions based on data in an Excel table, an Excel range, or another data source.</span></span> <span data-ttu-id="f70c4-105">既存のモデルに新しいデータを適用して傾向を予測するプロセスを、*予測クエリ*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-105">The process of applying new data to an existing model to predict trends is called a *prediction query*.</span></span>  
  
 <span data-ttu-id="f70c4-106">**クエリ**ウィザードでは、データマイニングモデルの作成または変更、カスタムクエリの生成、または入れ子になったデータセットなどの他のツールでサポートされていない構造の操作を行うための高度なエディターも用意されています。</span><span class="sxs-lookup"><span data-stu-id="f70c4-106">The **Query** wizard also provides an advanced editor for creating or modifying data mining models, for generating custom queries, or for working with structures not supported in the other tools, such as nested datasets.</span></span>  
  
-   <span data-ttu-id="f70c4-107">テキストエディターを使用して、他の場所で作成したデータマイニング拡張機能 (DMX) ステートメントを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-107">Use the text editor to type or paste in the Data Mining Extensions (DMX) statements you've created elsewhere.</span></span>  
  
-   <span data-ttu-id="f70c4-108">対話的なクエリ ビルダーを使用して、テンプレートとダイアログ ボックスの助けを借りて、カスタム DMX ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="f70c4-108">Use the interactive Query Builder to compose a custom DMX statement with the help of templates and dialog boxes.</span></span>  
  
-   <span data-ttu-id="f70c4-109">DMX ステートメントを作成して、マイニング モデルおよび構造を管理またはバックアップします。</span><span class="sxs-lookup"><span data-stu-id="f70c4-109">Create DMX statements to manage or back up mining models and structures.</span></span>  
  
## <a name="using-the-query-wizard"></a><span data-ttu-id="f70c4-110">クエリ ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="f70c4-110">Using the Query Wizard</span></span>  
  
1.  <span data-ttu-id="f70c4-111">最初に、入力として使用するデータ ソースを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f70c4-111">First, you must specify a source for the data to use as input.</span></span> <span data-ttu-id="f70c4-112">既存の Excel テーブルまたは範囲のデータを使用できます。また、データを取得する SQL ステートメントを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-112">You can use data in an existing Excel table or range, or you can specify a SQL statement to retrieve the data.</span></span>  
  
2.  <span data-ttu-id="f70c4-113">次に、接続しているサーバーのデータ マイニング モデルの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-113">Next, the wizard presents a list of data mining models on the server to which you are connected.</span></span> <span data-ttu-id="f70c4-114">必要なモデルがわかっていて、データマイニングに精通している場合は、[**詳細設定**] をクリックして、**データマイニング詳細クエリエディター**を開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-114">If you know the model you want and are familiar with data mining, you can also click **Advanced** to open the **Data Mining Advanced Query Editor**.</span></span>  
  
3.  <span data-ttu-id="f70c4-115">選択したモデルの種類に応じて、評価するデータが格納されている列の指定、および入力データ列とモデル列のマッピングの定義を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f70c4-115">Depending on the type of model that you choose, you must specify the column that contains the data to be evaluated, and define mappings between the input data columns and the model columns.</span></span> <span data-ttu-id="f70c4-116">選択したアルゴリズムに応じて、モデルのその他のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f70c4-116">Depending on the algorithm you choose, you can set other properties on the model.</span></span>  
  
4.  <span data-ttu-id="f70c4-117">最後に、1 つまたは複数の予測を選択し、結果の保存先を指定します。</span><span class="sxs-lookup"><span data-stu-id="f70c4-117">Finally, the wizard also gives you the ability to choose one or more predictions, and specify a destination in which to store the results.</span></span>  
  
 <span data-ttu-id="f70c4-118">いつでも、[**詳細設定**] をクリックして**データマイニング詳細クエリエディター**に切り替えることができます。これにより、DMX ステートメントの各部分をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-118">At any time, you can click **Advanced** to switch to the **Data Mining Advanced Query Editor**, which gives you more control over each part of the DMX statement.</span></span> <span data-ttu-id="f70c4-119">高度なクエリ編集ツールの使用方法の詳細については、「[高度なデータマイニングクエリエディター](advanced-data-mining-query-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f70c4-119">For more information about how to use the advanced query editing tools, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="f70c4-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="f70c4-120">Requirements</span></span>  
 <span data-ttu-id="f70c4-121">**クエリ**ウィザードを使用するには、のインスタンスに接続されている必要があり [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-121">To use the **Query** wizard, you must be connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="f70c4-122">また、サーバーに適切な種類のデータ マイニング モデルが少なくとも 1 つ保存されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f70c4-122">Moreover, the server must contain at least one data mining model of an appropriate type.</span></span> <span data-ttu-id="f70c4-123">使用できるモデルが 1 つもない場合は、Excel 用のデータ マイニング クライアントのウィザードを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="f70c4-123">If no mining models are available, you can create one by using the wizards provided in the Data Mining Client for Excel.</span></span> <span data-ttu-id="f70c4-124">ウィザードを使用して新しいマイニングモードを作成する方法については、「[データマイニングモデルの作成](creating-a-data-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f70c4-124">For information about how to create a new mining mode by using a wizard, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70c4-125">参照</span><span class="sxs-lookup"><span data-stu-id="f70c4-125">See Also</span></span>  
 <span data-ttu-id="f70c4-126">[Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f70c4-126">[Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="f70c4-127">Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="f70c4-127">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
