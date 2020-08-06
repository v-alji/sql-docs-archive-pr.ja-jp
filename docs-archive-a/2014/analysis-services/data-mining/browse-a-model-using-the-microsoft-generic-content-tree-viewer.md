---
title: Microsoft 汎用コンテンツツリービューアーを使用したモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
ms.assetid: 4a5f7c51-c704-4214-b05d-21cf735e6d96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90d47262a09060a11020e50b3724753799d2d188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645287"
---
# <a name="browse-a-model-using-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="60a86-102">Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="60a86-102">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>
  <span data-ttu-id="60a86-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用マイニング モデル コンテンツ ビューアーは、マイニング アルゴリズムによって発見されたパターンについての詳細情報を提供します。また、分析処理中に生成されたさまざまな統計情報へのアクセスも提供します。</span><span class="sxs-lookup"><span data-stu-id="60a86-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Mining Model Content Viewer provides detailed information about the patterns found by the mining algorithm, and also provides access to various statistics generated during the analysis process.</span></span> <span data-ttu-id="60a86-104">情報の量と種類は、使用されたアルゴリズムによって異なりますが、次のカテゴリを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="60a86-104">The amount and type of information depends on the algorithm that was used, but can include the following categories:</span></span>  
  
-   <span data-ttu-id="60a86-105">データのセグメントとその特性</span><span class="sxs-lookup"><span data-stu-id="60a86-105">Segments of data, and their characteristics.</span></span>  
  
-   <span data-ttu-id="60a86-106">各グループまたはデータセット全体に関する説明的な統計情報</span><span class="sxs-lookup"><span data-stu-id="60a86-106">Descriptive statistics about each group or about the whole set of data.</span></span>  
  
-   <span data-ttu-id="60a86-107">ツリー内の分岐または子ノードの数</span><span class="sxs-lookup"><span data-stu-id="60a86-107">The number of branches or child nodes in a tree.</span></span>  
  
-   <span data-ttu-id="60a86-108">クラスターまたはデータセット全体に対する、分散や平均などの計算</span><span class="sxs-lookup"><span data-stu-id="60a86-108">Calculations, such as variance and mean, for a cluster or a whole set of data.</span></span>  
  
 <span data-ttu-id="60a86-109">この情報を表示すると、分析結果を理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="60a86-109">Viewing this information can help you better understand the results of your analysis.</span></span> <span data-ttu-id="60a86-110">モデルを調整および再トレーニングする方法を特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="60a86-110">You can also identify ways to fine-tune, and then retrain, your model.</span></span> <span data-ttu-id="60a86-111">また、別のアルゴリズムを使用して再トレーニングすることもできます。</span><span class="sxs-lookup"><span data-stu-id="60a86-111">Or, you might decide to retrain by using a different algorithm.</span></span>  
  
## <a name="viewing-mining-model-content"></a><span data-ttu-id="60a86-112">マイニング モデル コンテンツの表示</span><span class="sxs-lookup"><span data-stu-id="60a86-112">Viewing Mining Model Content</span></span>  
 <span data-ttu-id="60a86-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ビューアーは、列、ルール、プロパティ、属性、ノードなど、マイニング モデルの *コンテンツ スキーマ行セット* のコンテンツを表示します。</span><span class="sxs-lookup"><span data-stu-id="60a86-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Viewer displays the columns, rules, properties, attributes, nodes, and other content from the *content schema rowset* of the mining model.</span></span> <span data-ttu-id="60a86-114">コンテンツ スキーマ行セットは、データ マイニング モデルのコンテンツに関する詳細情報を表すための汎用フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="60a86-114">The content schema rowset is a generic framework for presenting detailed information about the content of a data mining model.</span></span>  
  
 <span data-ttu-id="60a86-115">この詳細情報は、モデル内のパターン、クラスター、またはツリーを表す HTML テーブルにノードとして格納されています。</span><span class="sxs-lookup"><span data-stu-id="60a86-115">This detailed information is contained in an HTML table that represents the patterns, clusters, or trees in the model as nodes.</span></span> <span data-ttu-id="60a86-116">各ノードをクリックして展開し、数値属性の数式や個別の値数などの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="60a86-116">You can click on each node and expand it to see more detail, such as the formulas or the count of distinct values for a numeric attribute.</span></span> <span data-ttu-id="60a86-117">ノード間の親子リレーションシップを調べることもできます。</span><span class="sxs-lookup"><span data-stu-id="60a86-117">You can also explore the child-parent relationships among the nodes.</span></span>  
  
 <span data-ttu-id="60a86-118">マイニング モデルのコンテンツに使用されている用語の一般的な意味については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60a86-118">For more information about the general meaning of the terms used in the mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span> <span data-ttu-id="60a86-119">このトピックには、特定の種類のモデルのマイニング モデルのコンテンツに関する情報へのリンクも含まれています。</span><span class="sxs-lookup"><span data-stu-id="60a86-119">The topic also contains links to information about mining model content for specific types of models.</span></span> <span data-ttu-id="60a86-120">それぞれの種類のマイニング モデルにはアルゴリズムに固有の情報とデータ内で見つかったパターンが含まれるため、各モデルの種類を十分に理解するために各モデルの種類のテクニカル リファレンス トピックを参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60a86-120">Each type of mining model contains information that is highly specific to the algorithm and the patterns found in the data, so we recommend that you consult the technical reference topic for each model type in order to fully understand each model type.</span></span>  
  
## <a name="querying-mining-model-content"></a><span data-ttu-id="60a86-121">マイニング モデルのコンテンツのクエリ</span><span class="sxs-lookup"><span data-stu-id="60a86-121">Querying Mining Model Content</span></span>  
 <span data-ttu-id="60a86-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーで表示される情報は、マイニング モデルにクエリを実行することによっても取得できます。</span><span class="sxs-lookup"><span data-stu-id="60a86-122">The same information that is provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer is also available by querying the mining model.</span></span> <span data-ttu-id="60a86-123">マイニング モデル コンテンツに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="60a86-123">You can create queries against mining model content by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="60a86-124">たとえば、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でコンテンツ クエリを実行するには、次の DMX ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="60a86-124">For example, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can run a content query by executing the following DMX statement:</span></span>  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 <span data-ttu-id="60a86-125">詳細については、「 [データ マイニング クエリ](data-mining-queries.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="60a86-125">For more information, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a86-126">参照</span><span class="sxs-lookup"><span data-stu-id="60a86-126">See Also</span></span>  
 <span data-ttu-id="60a86-127">[Microsoft 汎用コンテンツツリービューアー &#40;データマイニング&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="60a86-127">[Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span></span>  
 [<span data-ttu-id="60a86-128">データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="60a86-128">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
  
