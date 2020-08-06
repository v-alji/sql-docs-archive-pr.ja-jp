---
title: マイニングモデルの作成に使用するパラメーターを照会する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a3802a0d70579f613accbe6abd310da909751b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717025"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a><span data-ttu-id="9a314-102">マイニング モデルの作成に使用されたパラメーターのクエリ</span><span class="sxs-lookup"><span data-stu-id="9a314-102">Query the Parameters Used to Create a Mining Model</span></span>
  <span data-ttu-id="9a314-103">マイニング モデルの構成は、トレーニング ケースだけでなく、モデルの作成時に設定されたパラメーターの影響も受けます。</span><span class="sxs-lookup"><span data-stu-id="9a314-103">The composition of a mining model is affected not only by the training cases, but by the parameters that were set when the model was created.</span></span> <span data-ttu-id="9a314-104">したがって、既存のモデルのパラメーター設定を取得すると、モデルの動作をよりよく理解できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a314-104">Therefore, you might find it useful to retrieve the parameter settings of an existing model to better understand the behavior of the model.</span></span> <span data-ttu-id="9a314-105">そのモデルの特定のバージョンのドキュメントを作成する場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="9a314-105">Retrieving parameters is also useful when documenting a particular version of that model.</span></span>  
  
 <span data-ttu-id="9a314-106">モデルの作成時に使用されたパラメーターを確認するには、いずれかのマイニング モデル スキーマ行セットに対するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a314-106">To find the parameters that were used when the model was created, you create a query against one of the mining model schema rowsets.</span></span> <span data-ttu-id="9a314-107">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]では、それらのスキーマ行セットが、Transact-SQL 構文を使用して簡単にクエリできる一連のシステム ビューとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="9a314-107">In [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], these schema rowsets are exposed as a set of system views that you can query easily by using Transact-SQL syntax.</span></span> <span data-ttu-id="9a314-108">この手順では、指定したマイニング モデルの作成に使用されたパラメーターを返すクエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a314-108">This procedure describes how to create a query that returns the parameters that were used to create the specified mining model.</span></span>  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a><span data-ttu-id="9a314-109">スキーマ行セットのクエリのためのクエリ ウィンドウを開くには</span><span class="sxs-lookup"><span data-stu-id="9a314-109">To open a Query window for a schema rowset query</span></span>  
  
1.  <span data-ttu-id="9a314-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、クエリするモデルが含まれている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="9a314-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the model you want to query.</span></span>  
  
2.  <span data-ttu-id="9a314-111">インスタンス名を右クリックし、 **[新しいクエリ]** をポイントして **[DMX]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a314-111">Right-click the instance name, select **New Query**, and then select **DMX**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a314-112">データ マイニング モデルに対するクエリは、 **MDX** テンプレートを使用して作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a314-112">You can also create a query against a data mining model by using the **MDX** template.</span></span>  
  
3.  <span data-ttu-id="9a314-113">インスタンスに複数のデータベースが含まれている場合は、クエリするモデルが含まれているデータベースをツール バーの **[使用できるデータベース]** の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="9a314-113">If the instance contains multiple databases, select the database that contains the model you want to query from the **Available Databases** list in the toolbar.</span></span>  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a><span data-ttu-id="9a314-114">既存のマイニング モデルのモデル パラメーターを取得するには</span><span class="sxs-lookup"><span data-stu-id="9a314-114">To return model parameters for an existing mining model</span></span>  
  
1.  <span data-ttu-id="9a314-115">DMX クエリ ペインで、次のテキストを入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9a314-115">In the DMX query pane, type or paste the following text:</span></span>  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  <span data-ttu-id="9a314-116">オブジェクト エクスプローラーで目的のマイニング モデルをクリックし、DMX クエリ ペインの単一引用符の間にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9a314-116">In Object Explorer, select the mining model you want, and then drag it into the DMX Query pane, between the single quotation marks.</span></span>  
  
3.  <span data-ttu-id="9a314-117">F5&lt;/localizedText&gt; キーを押すか、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a314-117">Press F5, or click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a314-118">例</span><span class="sxs-lookup"><span data-stu-id="9a314-118">Example</span></span>  
 <span data-ttu-id="9a314-119">次のコードは、「 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)」のマイニング モデルの作成に使用されたパラメーターのリストを返します。</span><span class="sxs-lookup"><span data-stu-id="9a314-119">The following code returns a list of the parameters that were used to create the mining model that you build in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="9a314-120">返されるパラメーターには、サーバー上のプロバイダーで利用可能なマイニング サービスによって使用される既定値の明示的な値も含まれます。</span><span class="sxs-lookup"><span data-stu-id="9a314-120">These parameters include the explicit values for any defaults used by the mining services available from providers on the server.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 <span data-ttu-id="9a314-121">このコード例では、クラスター モデルについて次のパラメーターが返されます。</span><span class="sxs-lookup"><span data-stu-id="9a314-121">The code example returns the following parameters for the clustering model:</span></span>  
  
 <span data-ttu-id="9a314-122">例の結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9a314-122">eExample Results:</span></span>  
  
 <span data-ttu-id="9a314-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a314-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="9a314-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="9a314-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a314-125">参照</span><span class="sxs-lookup"><span data-stu-id="9a314-125">See Also</span></span>  
 <span data-ttu-id="9a314-126">[データマイニングのクエリタスクと操作方法](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="9a314-126">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="9a314-127">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="9a314-127">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
