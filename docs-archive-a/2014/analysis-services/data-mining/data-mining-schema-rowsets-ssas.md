---
title: データマイニングスキーマ行セットに対するクエリの実行 (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60c802256454ee68d04392e685fa4acabf6c12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643640"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a><span data-ttu-id="43c61-102">データ マイニング スキーマ行セットのクエリ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="43c61-102">Querying the Data Mining Schema Rowsets (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="43c61-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、既存の OLE DB データ マイニング スキーマ行セットの多くが、データ マイニング拡張機能 (DMX) ステートメントを使用して照会できるシステム テーブルのセットとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], many of the existing OLE DB data mining schema rowsets are exposed as a set of system tables that you can query by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="43c61-104">データ マイニング スキーマ行セットに対するクエリを作成することによって、利用可能なサービスの特定、モデルおよび構造の状態の更新、モデル コンテンツまたはパラメーターに関する詳細の確認を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="43c61-104">By creating queries against the data mining schema rowset, you can identify the services that are available, get updates on the status of your models and structures, and find out details about the model content or parameters.</span></span> <span data-ttu-id="43c61-105">データ マイニング スキーマ行セットの説明については、「 [データ マイニング スキーマ行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43c61-105">For a description of the data mining schema rowsets, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43c61-106">データ マイニング スキーマ行セットに対するクエリは、XMLA を使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="43c61-106">You can also query the data mining schema rowsets by using XMLA.</span></span> <span data-ttu-id="43c61-107">これを SQL Server Management Studio で実行する方法については、「 [XMLA を使用したデータ マイニング クエリの作成](create-a-data-mining-query-by-using-xmla.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43c61-107">For more information about how to do this in SQL Server Management Studio, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="list-of-data-mining-schema-rowsets"></a><span data-ttu-id="43c61-108">データ マイニング スキーマ行セットの一覧</span><span class="sxs-lookup"><span data-stu-id="43c61-108">List of Data Mining Schema Rowsets</span></span>  
 <span data-ttu-id="43c61-109">次の表に、クエリおよび監視に役立つデータ マイニング スキーマ行セットの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="43c61-109">The following table lists the data mining schema rowsets that may be useful for querying and monitoring.</span></span>  
  
|<span data-ttu-id="43c61-110">行セット名</span><span class="sxs-lookup"><span data-stu-id="43c61-110">Rowset name</span></span>|<span data-ttu-id="43c61-111">説明</span><span class="sxs-lookup"><span data-stu-id="43c61-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="43c61-112">DMSCHEMA_MINING_MODELS</span><span class="sxs-lookup"><span data-stu-id="43c61-112">DMSCHEMA_MINING_MODELS</span></span>|<span data-ttu-id="43c61-113">現在のコンテキスト内のすべてのマイニング モデルの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-113">Lists all mining models in the current context.</span></span><br /><br /> <span data-ttu-id="43c61-114">作成日、モデルの作成に使用されたパラメーター、トレーニング セットのサイズなどの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-114">Includes such information as the date created, parameters used to create the model, and the size of the training set.</span></span>|  
|<span data-ttu-id="43c61-115">DMSCHEMA_MINING_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="43c61-115">DMSCHEMA_MINING_COLUMNS</span></span>|<span data-ttu-id="43c61-116">現在のコンテキスト内のマイニング モデルで使用されるすべての列の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-116">Lists all columns used in mining models in the current context.</span></span><br /><br /> <span data-ttu-id="43c61-117">マイニング構造ソース列へのマッピング、データ型、有効桁数、列で使用できる予測関数などの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-117">Information includes mapping to mining structure source column, data type, precision, and prediction functions that can be used with the column.</span></span>|  
|<span data-ttu-id="43c61-118">DMSCHEMA_MINING_STRUCTURES</span><span class="sxs-lookup"><span data-stu-id="43c61-118">DMSCHEMA_MINING_STRUCTURES</span></span>|<span data-ttu-id="43c61-119">現在のコンテキスト内のすべてのマイニング構造の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-119">Lists all mining structure in the current context.</span></span><br /><br /> <span data-ttu-id="43c61-120">構造にデータが設定されているかどうか、構造が最後に処理された日付、構造の予約データ セットの定義などの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-120">Information includes whether the structure is populated, the date the structure was last processed, and the definition of the holdout data set for the structure, if any.</span></span>|  
|<span data-ttu-id="43c61-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="43c61-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span></span>|<span data-ttu-id="43c61-122">現在のコンテキスト内のマイニング構造で使用されるすべての列の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-122">Lists all columns used in mining structures in the current context.</span></span><br /><br /> <span data-ttu-id="43c61-123">コンテンツの種類、データ型、NULL 値の許容属性、入れ子になったテーブル データが列に格納されるかどうかなどの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-123">Information includes content type and data type, nullability, and whether the column contains nested table data.</span></span>|  
|<span data-ttu-id="43c61-124">DMSCHEMA_MINING_SERVICES</span><span class="sxs-lookup"><span data-stu-id="43c61-124">DMSCHEMA_MINING_SERVICES</span></span>|<span data-ttu-id="43c61-125">指定されたサーバーで利用可能なすべてのマイニング サービスまたはアルゴリズムの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="43c61-125">Lists all mining services, or algorithms, that are available on the specified server.</span></span><br /><br /> <span data-ttu-id="43c61-126">サポートされているモデリング フラグ、入力の種類、サポートされているデータ ソースの種類などの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-126">Information includes supported modeling flags, input types, and supported data source types.</span></span>|  
|<span data-ttu-id="43c61-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43c61-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span></span>|<span data-ttu-id="43c61-128">現在のインスタンス上で利用可能なマイニング サービスのすべてのパラメーターの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="43c61-128">Lists all parameters for the mining services that are available on the current instance.</span></span><br /><br /> <span data-ttu-id="43c61-129">各パラメーターのデータ型、既定値、上限値と下限値などの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-129">Information includes the data type for each parameter, the default values, and the upper and lower limits.</span></span>|  
|<span data-ttu-id="43c61-130">DMSCHEMA_MODEL_CONTENT</span><span class="sxs-lookup"><span data-stu-id="43c61-130">DMSCHEMA_MODEL_CONTENT</span></span>|<span data-ttu-id="43c61-131">モデルが処理された場合、モデルの内容を返します。</span><span class="sxs-lookup"><span data-stu-id="43c61-131">Returns the content of the model if the model has been processed.</span></span><br /><br /> <span data-ttu-id="43c61-132">詳細については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43c61-132">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>|  
|<span data-ttu-id="43c61-133">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="43c61-133">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="43c61-134">Analysis Services の現在のインスタンス内のすべてのデータベース (カタログ) の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-134">Lists all databases (catalogs) in the current instance of Analysis Services.</span></span>|  
|<span data-ttu-id="43c61-135">MDSCHEMA_INPUT_DATASOURCES</span><span class="sxs-lookup"><span data-stu-id="43c61-135">MDSCHEMA_INPUT_DATASOURCES</span></span>|<span data-ttu-id="43c61-136">Analysis Services の現在のインスタンス内のすべてのデータ ソースの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-136">Lists all data sources in the current instance of Analysis Services.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="43c61-137">表で示した内容がすべてではありません。トラブルシューティングに特に必要と思われる行セットのみを示しています。</span><span class="sxs-lookup"><span data-stu-id="43c61-137">The list in the table is not comprehensive; it shows only those rowsets that may be of most interest for troubleshooting.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="43c61-138">例</span><span class="sxs-lookup"><span data-stu-id="43c61-138">Examples</span></span>  
 <span data-ttu-id="43c61-139">次のセクションで、データ マイニング スキーマ行セットに対するクエリの例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="43c61-139">The following section provides some examples of queries against the data mining schema rowsets.</span></span>  
  
### <a name="example-1-list-data-mining-services"></a><span data-ttu-id="43c61-140">例 1: データ マイニング サービスの一覧表示</span><span class="sxs-lookup"><span data-stu-id="43c61-140">Example 1: List Data Mining Services</span></span>  
 <span data-ttu-id="43c61-141">次のクエリでは、現在のサーバーで使用できるマイニング サービス、すなわち有効なアルゴリズムの一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-141">The following query returns a list of the mining services that are available on the current server, meaning the algorithms that are enabled.</span></span> <span data-ttu-id="43c61-142">各マイニング サービスに対して指定される列には、各アルゴリズムで使用できるモデリング フラグとコンテンツの種類、各サービスの GUID、および各サービスに対して追加されている予測の制限が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43c61-142">The columns provided for each mining service include the modeling flags and content types that can be used by each algorithm, the GUID for each service, and any prediction limits that may have been added for each service.</span></span>  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a><span data-ttu-id="43c61-143">例 2: データ マイニング モデル パラメーターの一覧表示</span><span class="sxs-lookup"><span data-stu-id="43c61-143">Example 2: List Mining Model Parameters</span></span>  
 <span data-ttu-id="43c61-144">次の例では、特定のマイニング モデルの作成に使用されたパラメーターを返します。</span><span class="sxs-lookup"><span data-stu-id="43c61-144">The following example returns the parameters that were used to create a specific mining model:</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a><span data-ttu-id="43c61-145">例 3: すべての行セットの一覧表示</span><span class="sxs-lookup"><span data-stu-id="43c61-145">Example 3: List All Rowsets</span></span>  
 <span data-ttu-id="43c61-146">次のクエリでは、現在のサーバーで使用できる行セットの詳細な一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="43c61-146">The following example returns a comprehensive list of the rowsets that are available on the current server:</span></span>  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a><span data-ttu-id="43c61-147">参照</span><span class="sxs-lookup"><span data-stu-id="43c61-147">See Also</span></span>  
 [<span data-ttu-id="43c61-148">トラブルシューティングの概念 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="43c61-148">Troubleshooting Concepts (Analysis Services - Data Mining)</span></span>](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
