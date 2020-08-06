---
title: データマイニングのクエリタスクと操作方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], how-to topics
ms.assetid: 1bc2a775-6e62-4c66-a53c-201f2ea66295
author: minewiskan
ms.author: owend
ms.openlocfilehash: 454a3af33d0c18232bb36771235b328a17da6b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645274"
---
# <a name="data-mining-query-tasks-and-how-tos"></a><span data-ttu-id="5cb63-102">データ マイニングのクエリ タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="5cb63-102">Data Mining Query Tasks and How-tos</span></span>
  <span data-ttu-id="5cb63-103">データ マイニング モデルを利用する場合は、クエリを作成できることが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="5cb63-103">The ability to create queries is critical if you are to make use of your data mining models.</span></span> <span data-ttu-id="5cb63-104">ここでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で提供されるツールを使用して、データ マイニング モデルに対するクエリの作成例のリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-104">This section provides links to examples of how to create queries against a data mining model by using the tools provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="5cb63-105">データ マイニング クエリとは何かに関する情報、または作成できるさまざまな種類のクエリに関する情報が必要な場合は、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cb63-105">If you need more information about what a data mining query is, or the different types of queries you can create, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="creating-queries-with-prediction-query-builder"></a><span data-ttu-id="5cb63-106">予測クエリ ビルダーでのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-106">Creating Queries with Prediction Query Builder</span></span>  
 <span data-ttu-id="5cb63-107">予測クエリ ビルダーは、データ マイニング モデルに対するクエリをグラフィカルに作成する方法として [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の両方で提供されます。</span><span class="sxs-lookup"><span data-stu-id="5cb63-107">The Prediction Query Builder is provided in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a way of graphically building queries against data mining models.</span></span> <span data-ttu-id="5cb63-108">次の各トピックでは、モデルの選択、データ ソースの指定、予測のカスタマイズ、および出力の保存の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-108">The following topics explain how you can select a model, specify a data source, customize the predictions, and save output.</span></span>  
  
-   [<span data-ttu-id="5cb63-109">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-109">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [<span data-ttu-id="5cb63-110">データ マイニング デザイナーでの単一クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-110">Create a Singleton Query in the Data Mining Designer</span></span>](create-a-singleton-query-in-the-data-mining-designer.md)  
  
-   [<span data-ttu-id="5cb63-111">予測クエリ ビルダーを使用した予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-111">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [<span data-ttu-id="5cb63-112">予測クエリの結果の表示および保存</span><span class="sxs-lookup"><span data-stu-id="5cb63-112">View and Save the Results of a Prediction Query</span></span>](view-and-save-the-results-of-a-prediction-query.md)  
  
-   [<span data-ttu-id="5cb63-113">手動での予測クエリの編集</span><span class="sxs-lookup"><span data-stu-id="5cb63-113">Manually Edit a Prediction Query</span></span>](manually-edit-a-prediction-query.md)  
  
-   [<span data-ttu-id="5cb63-114">モデルへの予測関数の適用</span><span class="sxs-lookup"><span data-stu-id="5cb63-114">Apply Prediction Functions to a Model</span></span>](apply-prediction-functions-to-a-model.md)  
  
-   [<span data-ttu-id="5cb63-115">予測クエリの入力データの選択およびマップ</span><span class="sxs-lookup"><span data-stu-id="5cb63-115">Choose and Map Input Data for a Prediction Query</span></span>](choose-and-map-input-data-for-a-prediction-query.md)  
  
## <a name="using-other-data-mining-query-tools"></a><span data-ttu-id="5cb63-116">他のデータ マイニング クエリ ツールの使用</span><span class="sxs-lookup"><span data-stu-id="5cb63-116">Using Other Data Mining Query Tools</span></span>  
 <span data-ttu-id="5cb63-117">予測クエリ ビルダーの使用に加えて、DMX または XMLA を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にクエリを直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="5cb63-117">In addition to using the Prediction Query Builder, you can type a query directly into [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using DMX or by using XMLA.</span></span> <span data-ttu-id="5cb63-118">プログラムを使用して予測クエリを作成し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="5cb63-118">You can also build prediction queries programmatically and send them to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="5cb63-119">次の各トピックでは、予測クエリ ビルダーの外部で予測クエリを作成および操作する方法の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-119">The following topics provide more information about how to create and work with prediction queries outside of the Prediction Query Builder.</span></span>  
  
 [<span data-ttu-id="5cb63-120">テンプレートからの単一予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-120">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
 <span data-ttu-id="5cb63-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のツールを使用して、予測クエリを作成および実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-121">Describes how to use the tools in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to build and run a prediction query.</span></span>  
  
 [<span data-ttu-id="5cb63-122">テンプレートからの単一予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-122">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
 <span data-ttu-id="5cb63-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に付属しているテンプレートを使用して、予測クエリにパラメーターを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-123">Describes how to use the templates that are provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add parameters to a prediction query.</span></span>  
  
 [<span data-ttu-id="5cb63-124">データ マイニング クエリのタイムアウト値の変更</span><span class="sxs-lookup"><span data-stu-id="5cb63-124">Change the Time-out Value for Data Mining Queries</span></span>](change-the-time-out-value-for-data-mining-queries.md)  
 <span data-ttu-id="5cb63-125">データ マイニング クエリ関連の動作を制御するサーバーのプロパティを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-125">Describes how to set properties on the server that control behavior related to data mining queries.</span></span>  
  
 [<span data-ttu-id="5cb63-126">マイニング モデルのコンテンツ クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-126">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
 <span data-ttu-id="5cb63-127">データ マイニング スキーマ行セットを使用して、マイニング モデルに格納されている詳細情報を返すクエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-127">Describes how to create queries that return detailed information that is stored in the mining model by using the data mining schema rowsets.</span></span>  
  
 [<span data-ttu-id="5cb63-128">XMLA を使用したデータ マイニング クエリの作成</span><span class="sxs-lookup"><span data-stu-id="5cb63-128">Create a Data Mining Query by Using XMLA</span></span>](create-a-data-mining-query-by-using-xmla.md)  
 <span data-ttu-id="5cb63-129">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の XMLA テンプレートを使用して、マイニング モデル コンテンツに対するクエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cb63-129">Describes how to create a query against mining model content by using the XMLA templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb63-130">参照</span><span class="sxs-lookup"><span data-stu-id="5cb63-130">See Also</span></span>  
 <span data-ttu-id="5cb63-131">[クエリと式言語のリファレンス &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx) </span><span class="sxs-lookup"><span data-stu-id="5cb63-131">[Query and Expression Language Reference &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx) </span></span>  
 [<span data-ttu-id="5cb63-132">データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="5cb63-132">Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;</span></span>](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
