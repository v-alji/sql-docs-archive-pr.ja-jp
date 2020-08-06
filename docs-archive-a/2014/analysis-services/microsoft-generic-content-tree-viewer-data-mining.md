---
title: Microsoft 汎用コンテンツツリービューアー (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0dab06d6af8f2c5af029d9ce831f518faa4067e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740572"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a><span data-ttu-id="27be8-102">Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="27be8-102">Microsoft Generic Content Tree Viewer (Data Mining)</span></span>
  <span data-ttu-id="27be8-103">**Microsoft 汎用コンテンツ ツリー ビューアー** には、データ マイニング モデルのコンテンツに関する詳細情報が、標準化された HTML テーブル形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="27be8-103">The **Microsoft Generic Content Tree Viewer** displays detailed information about the contents of a data mining mode in a standardized HTML table format.</span></span> <span data-ttu-id="27be8-104">このビューを使用すると、モデルの基になる構造に加え、係数や値の分布などの詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="27be8-104">This view is useful because it exposes the underlying structure of the model, as well details about coefficients, the distribution of values, and much more.</span></span>  
  
 <span data-ttu-id="27be8-105">テーブルに実際に表示される内容は使用されたアルゴリズムによって異なり、列、ルール、プロパティ、属性、ノード、および数式が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="27be8-105">The actual content displayed in the table varies depending on the algorithm that was used and might include columns, rules, properties, attributes, nodes, and formulas.</span></span> <span data-ttu-id="27be8-106">モデル コンテンツ、および各モデルの種類の情報を解釈する方法の詳細については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27be8-106">For more information about model content, and how to interpret the information for each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="27be8-107">ビューアーに表示される情報は、マイニング モデルのコンテンツ スキーマ行セットに基づく共通の構造を使用します。</span><span class="sxs-lookup"><span data-stu-id="27be8-107">The information that is displayed in the viewer uses a common structure that is based on the content schema rowset for mining models.</span></span> <span data-ttu-id="27be8-108">コンテンツ スキーマ行セットは、データ マイニング モデルのパターン、統計、およびその他のコンテンツを格納するための汎用フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="27be8-108">The content schema rowset is a generic framework for storing patterns, statistics, and other contents of a data mining model.</span></span> <span data-ttu-id="27be8-109">マイニング モデルのデータ マイニング スキーマ行セット内の列の一覧については、「 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27be8-109">For a list of the columns in the data mining schema rowset for mining models, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
## <a name="options"></a><span data-ttu-id="27be8-110">Options</span><span class="sxs-lookup"><span data-stu-id="27be8-110">Options</span></span>  
 <span data-ttu-id="27be8-111">**[ノードのキャプション (一意の ID)]**</span><span class="sxs-lookup"><span data-stu-id="27be8-111">**Node caption (Unique ID)**</span></span>  
 <span data-ttu-id="27be8-112">このペインには、選択したマイニング モデルのすべてのノードが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="27be8-112">This pane displays a list of all the nodes in the selected mining model.</span></span> <span data-ttu-id="27be8-113">ツリーでのノードの配置方法は、表示中のモデルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="27be8-113">The way the nodes are arranged in the tree is different depending on the type of model you are viewing.</span></span>  
  
 <span data-ttu-id="27be8-114">ノードをクリックすることで、そのノードに関する詳細を **[ノードの詳細]** ペインに表示できます。</span><span class="sxs-lookup"><span data-stu-id="27be8-114">You can click each node to display details about the node in the **Node details** pane.</span></span>  
  
 <span data-ttu-id="27be8-115">**ノードの詳細**</span><span class="sxs-lookup"><span data-stu-id="27be8-115">**Node details**</span></span>  
 <span data-ttu-id="27be8-116">選択したノードのコンテンツに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="27be8-116">Displays detailed information about the content of the selected node.</span></span> <span data-ttu-id="27be8-117">各ノードの情報は標準化された形式で格納されますが、テーブルの各行の内容と意味は、表示中のモデルの種類またはノードの型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="27be8-117">Each node stores its information in a standardized format, but the contents and significance of each line of the table depends on the type of model or type of node that you are viewing.</span></span> <span data-ttu-id="27be8-118">たとえば、関連モデルのルールを表すノードに保存される情報は、デシジョン ツリー モデルのツリーを表すノードとは別の情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="27be8-118">For example, the information stored for a node that represents a rule in an association model contains different information than a node that represents a tree in a decision trees model.</span></span>  
  
 <span data-ttu-id="27be8-119">特定のモデルの種類のノード情報を解釈する方法については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27be8-119">For information about how to interpret the node information for a specific model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27be8-120">参照</span><span class="sxs-lookup"><span data-stu-id="27be8-120">See Also</span></span>  
 <span data-ttu-id="27be8-121">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="27be8-121">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="27be8-122">[データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="27be8-122">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="27be8-123">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="27be8-123">Data Mining Queries</span></span>](data-mining/data-mining-queries.md)  
  
  
