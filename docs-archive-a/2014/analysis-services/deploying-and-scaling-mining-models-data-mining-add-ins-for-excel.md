---
title: マイニングモデルの配置とスケーリング (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- manage
ms.assetid: 4c617375-6b01-4a71-9680-de0cbf2cff05
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd2839144d4d1667da09830aaabd1ec3f17a9c21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643012"
---
# <a name="deploying-and-scaling-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="fd4d3-102">マイニング モデルの配置とスケーリング (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="fd4d3-102">Deploying and Scaling Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="fd4d3-103">**モデルの使用状況**と**管理**グループに含まれるツールは、既存のマイニングモデルの管理と参照に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-103">The tools in the **Model Usage** and **Management** group are provided to help you manage and browse existing mining models.</span></span> <span data-ttu-id="fd4d3-104">これらのツールを使用して、アドインを使用して作成したモデルに加え、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに格納されているモデルを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-104">You can use these tools to view any models that are stored on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], not just those created using the add-ins.</span></span>  
  
 <span data-ttu-id="fd4d3-105">必要な権限を持っている場合は、Excel を終了することなく、既存のマイニング モデルを、削除、変更、名前変更、または処理できます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-105">If you have the necessary permissions, you can delete, modify, rename, or process existing mining models and structures without leaving Excel.</span></span>  
  
## <a name="model-usage-toolbar"></a><span data-ttu-id="fd4d3-106">モデルの使用法ツール バー</span><span class="sxs-lookup"><span data-stu-id="fd4d3-106">Model Usage Toolbar</span></span>  
  
### <a name="browse"></a><span data-ttu-id="fd4d3-107">参照</span><span class="sxs-lookup"><span data-stu-id="fd4d3-107">Browse</span></span>  
 <span data-ttu-id="fd4d3-108">**参照**ウィザードを使用して、既存のデータマイニングモデルを選択し、複数のグラフおよびツールを含むビューアーでモデルを表示および調査します。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-108">Use the **Browse** wizard to select an existing data mining model, and then view and explore the model in a viewer that contains multiple graphs and tools.</span></span>  
  
 <span data-ttu-id="fd4d3-109">詳細については、「 [Excel でのモデルの参照 &#40;SQL Server データマイニングアドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-109">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="document-model"></a><span data-ttu-id="fd4d3-110">モデルのドキュメント化</span><span class="sxs-lookup"><span data-stu-id="fd4d3-110">Document Model</span></span>  
 <span data-ttu-id="fd4d3-111">[**モデルのドキュメント**化] をクリックすると、作成したマイニング構造およびマイニングモデルのレポートを作成するウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-111">Click **Document Model** to start a wizard that creates a report of the mining structures and mining models that you have created.</span></span> <span data-ttu-id="fd4d3-112">基本レポートと、より詳細なレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-112">You can create basic or advanced reports.</span></span> <span data-ttu-id="fd4d3-113">レポートには列とモデルのメタデータが含まれているため、作業のドキュメント化とモデル内の変更の追跡に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-113">The reports include column and model metadata, so are useful for documenting your work and tracking changes in models.</span></span>  
  
 <span data-ttu-id="fd4d3-114">詳細については、「 [Excel 用データマイニングアドイン &#40;マイニングモデルを文書化する&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-114">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
### <a name="query"></a><span data-ttu-id="fd4d3-115">クエリ</span><span class="sxs-lookup"><span data-stu-id="fd4d3-115">Query</span></span>  
 <span data-ttu-id="fd4d3-116">[**クエリ**] をクリックして、**クエリ**ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-116">Click **Query** to start the **Query** wizard.</span></span> <span data-ttu-id="fd4d3-117">このウィザードでは、既存のデータ マイニング モデルに対する予測クエリを対話形式で段階的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-117">The wizard interactively walks you through the process of creating a prediction query against an existing data mining model.</span></span>  
  
 <span data-ttu-id="fd4d3-118">クエリをさらにカスタマイズしたり、ウィザードに含まれていないクエリを作成したりするには、[**詳細設定**] ボタンをクリックして**詳細エディターデータマイニングクエリ**を開始します。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-118">To further customize the query, or build queries not included in the wizard, just click the **Advanced** button to start the **Data Mining Query Advanced Editor**.</span></span>  
  
 <span data-ttu-id="fd4d3-119">詳細については、「[クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-119">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="data-mining-advanced-query-editor"></a><span data-ttu-id="fd4d3-120">データ マイニング詳細クエリ エディター</span><span class="sxs-lookup"><span data-stu-id="fd4d3-120">Data Mining Advanced Query Editor</span></span>  
 <span data-ttu-id="fd4d3-121">このエディターを使用してデータ マイニング拡張機能 (DMX) テンプレートを開いてクエリの作成をすぐに開始し、入力、出力、アルゴリズム、およびパラメーターを対話的に変更しながら、カスタム マイニング モデル、マイニング構造、または予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-121">In this editor, you can use Data Mining Extensions (DMX) templates to jumpstart a query, and then modify the inputs, outputs, algorithms, and parameters to create a custom mining model, mining structure, or prediction query.</span></span>  
  
 <span data-ttu-id="fd4d3-122">詳細については、「[高度なデータマイニングクエリエディター](advanced-data-mining-query-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-122">For more information, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="management"></a><span data-ttu-id="fd4d3-123">管理</span><span class="sxs-lookup"><span data-stu-id="fd4d3-123">Management</span></span>  
 <span data-ttu-id="fd4d3-124">現在の接続の既存のモデルを表示するには、**モデルの管理**ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-124">Use the **Manage Models** wizard to view existing models on the current connection.</span></span> <span data-ttu-id="fd4d3-125">また、マイニング モデルと構造の削除、名前の変更、処理、インポート、およびエクスポートを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-125">You can also delete, rename, process, or import and export mining models and structures.</span></span>  
  
 <span data-ttu-id="fd4d3-126">詳細については、「 [Manage model &#40;SQL Server データマイニングアドイン&#41;](manage-models-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4d3-126">For more information, see [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4d3-127">参照</span><span class="sxs-lookup"><span data-stu-id="fd4d3-127">See Also</span></span>  
 <span data-ttu-id="fd4d3-128">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="fd4d3-128">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="fd4d3-129">Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;</span><span class="sxs-lookup"><span data-stu-id="fd4d3-129">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
