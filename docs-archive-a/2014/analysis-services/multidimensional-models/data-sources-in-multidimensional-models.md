---
title: 多次元モデルのデータソース |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- Analysis Services objects, data sources
- storing data [Analysis Services], data sources
- data sources [Analysis Services], about data sources
- security [Analysis Services], data sources
- data sources [Analysis Services]
- storage [Analysis Services], data sources
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41386c1c7abb0324aa17df24b3c427ca8cbb5615
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644190"
---
# <a name="data-sources-in-multidimensional-models"></a><span data-ttu-id="eebe9-102">多次元モデルのデータ ソース</span><span class="sxs-lookup"><span data-stu-id="eebe9-102">Data Sources in Multidimensional Models</span></span>
  <span data-ttu-id="eebe9-103">多次元モデルにインポートするデータまたは読み込むデータは、すべて外部データ ソースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="eebe9-103">All data that you import or load into a multidimensional model originates from an external data source.</span></span> <span data-ttu-id="eebe9-104">通常、ソース データはレポート生成用に設計されたデータ ウェアハウスから取得されますが、直接的または [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージなどを介して間接的にアクセスされるリレーショナル データベースから取得される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="eebe9-104">Typically, source data is from a data warehouse designed for reporting purposes, but it could come from any relational database that is accessed directly or indirectly through an intermediary, such as an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
 <span data-ttu-id="eebe9-105">**の** データ ソース [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトでは、外部データ ソースへの直接接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-105">A **data source** object in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specifies a direct connection to an external data source.</span></span> <span data-ttu-id="eebe9-106">物理的な場所だけでなく、接続文字列、データ プロバイダー、資格情報、および接続動作を制御する他のプロパティも指定します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-106">In addition to physical location, a data source object specifies the connection string, data provider, credentials, and other properties that control connection behavior.</span></span>  
  
 <span data-ttu-id="eebe9-107">データ ソース オブジェクトによって提供される情報は、次の操作で使用されます。</span><span class="sxs-lookup"><span data-stu-id="eebe9-107">Information provided by the data source object is used during the following operations:</span></span>  
  
-   <span data-ttu-id="eebe9-108">データ ソース ビューの生成に使用されるスキーマ情報とその他のメタデータのモデルへの取り込み</span><span class="sxs-lookup"><span data-stu-id="eebe9-108">Get schema information and other metadata used to generate data source views into a model.</span></span>  
  
-   <span data-ttu-id="eebe9-109">処理中のクエリの実行またはモデルへのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="eebe9-109">Query or load data into a model during processing.</span></span>  
  
-   <span data-ttu-id="eebe9-110">ROLAP ストレージ モードを使用する多次元モデルまたはデータ マイニング モデルに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="eebe9-110">Run queries against multidimensional or data mining models that use ROLAP storage mode.</span></span>  
  
-   <span data-ttu-id="eebe9-111">リモート パーティションに対する読み取りまたは書き込み</span><span class="sxs-lookup"><span data-stu-id="eebe9-111">Read or write to remote partitions.</span></span>  
  
-   <span data-ttu-id="eebe9-112">リンク オブジェクトへの接続と、ターゲットからソースへの同期</span><span class="sxs-lookup"><span data-stu-id="eebe9-112">Connect to linked objects, as well as synchronize from target to source.</span></span>  
  
-   <span data-ttu-id="eebe9-113">リレーショナル データベースに格納されているファクト テーブル データを更新する書き戻し操作の実行</span><span class="sxs-lookup"><span data-stu-id="eebe9-113">Perform write back operations that update fact table data stored in a relational database.</span></span>  
  
 <span data-ttu-id="eebe9-114">多次元モデルを最初から作成するときは、まずデータ ソース オブジェクトを作成します。次に、このオブジェクトを使用して、次のオブジェクト ( **データ ソース ビュー**) を生成します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-114">When building a multidimensional model from the bottom up, you start by creating the data source object, and then use it to generate the next object, a **data source view**.</span></span> <span data-ttu-id="eebe9-115">データ ソース ビューは、モデルのデータ抽象化レイヤーです。</span><span class="sxs-lookup"><span data-stu-id="eebe9-115">A data source view is the data abstraction layer in the model.</span></span> <span data-ttu-id="eebe9-116">通常は、ソース データベースのスキーマを基盤として使用して、データ ソース オブジェクトの後に作成されます。</span><span class="sxs-lookup"><span data-stu-id="eebe9-116">It is typically created after the data source object, using the schema of the source database as the basis.</span></span> <span data-ttu-id="eebe9-117">ただし、他の方法でモデルを作成することもできます。たとえば、キューブとディメンションから作成する方法や、デザインを最適にサポートするスキーマを生成する方法などがあります。</span><span class="sxs-lookup"><span data-stu-id="eebe9-117">However, you can choose other ways to build a model, including starting with cubes and dimensions, and generating the schema that best supports your design.</span></span>  
  
 <span data-ttu-id="eebe9-118">モデルの作成方法に関係なく、各モデルにはソース データへの接続を指定する 1 つ以上のデータ ソース オブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="eebe9-118">Regardless of how you build it, each model requires at least one data source object that specifies a connection to source data.</span></span> <span data-ttu-id="eebe9-119">1 つのモデルに複数のデータ ソース オブジェクトを作成して、さまざまなソースのデータを使用したり、特定のオブジェクトの接続プロパティを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="eebe9-119">You can create multiple data source objects in a single model to use data from different sources or vary connection properties for specific objects.</span></span>  
  
 <span data-ttu-id="eebe9-120">データ ソース オブジェクトは、モデルの他のオブジェクトとは別に管理できます。</span><span class="sxs-lookup"><span data-stu-id="eebe9-120">Data source objects can be managed independently of other objects in your model.</span></span> <span data-ttu-id="eebe9-121">データ ソースを作成した後にプロパティを変更し、データが正しく取得されるようにモデルを前処理できます。</span><span class="sxs-lookup"><span data-stu-id="eebe9-121">After you create a data source, you can change its properties later, and then preprocess the model to ensure the data is retrieved correctly.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="eebe9-122">関連項目およびタスク</span><span class="sxs-lookup"><span data-stu-id="eebe9-122">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="eebe9-123">トピック</span><span class="sxs-lookup"><span data-stu-id="eebe9-123">Topic</span></span>|<span data-ttu-id="eebe9-124">説明</span><span class="sxs-lookup"><span data-stu-id="eebe9-124">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="eebe9-125">SSAS 多次元&#41;&#40;サポートされるデータソース</span><span class="sxs-lookup"><span data-stu-id="eebe9-125">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)|<span data-ttu-id="eebe9-126">多次元モデルで使用できるデータ ソースの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-126">Describes the types of data sources that can be used in a multidimensional model.</span></span>|  
|[<span data-ttu-id="eebe9-127">データ ソースの作成 &#40;SSAS 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="eebe9-127">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](create-a-data-source-ssas-multidimensional.md)|<span data-ttu-id="eebe9-128">多次元モデルにデータ ソース オブジェクトを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-128">Explains how to add a data source object to a multidimensional model.</span></span>|  
|[<span data-ttu-id="eebe9-129">ソリューション エクスプローラーでのデータ ソースの削除 &#40;SSAS 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="eebe9-129">Delete a Data Source in Solution Explorer &#40;SSAS Multidimensional&#41;</span></span>](delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|<span data-ttu-id="eebe9-130">この手順で、多次元モデルからデータ ソース オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-130">Use this procedure to delete a data source object from a multidimensional model.</span></span>|  
|[<span data-ttu-id="eebe9-131">データ ソースのプロパティの設定 &#40;SSAS 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="eebe9-131">Set Data Source Properties &#40;SSAS Multidimensional&#41;</span></span>](set-data-source-properties-ssas-multidimensional.md)|<span data-ttu-id="eebe9-132">各プロパティとその設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-132">Describes each property and explains how to set each one.</span></span>|  
|[<span data-ttu-id="eebe9-133">権限借用オプションの設定 &#40;SSAS - 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="eebe9-133">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](set-impersonation-options-ssas-multidimensional.md)|<span data-ttu-id="eebe9-134">[権限借用情報] ダイアログ ボックスのオプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eebe9-134">Explains how to configure options in the Impersonation Information dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eebe9-135">参照</span><span class="sxs-lookup"><span data-stu-id="eebe9-135">See Also</span></span>  
 <span data-ttu-id="eebe9-136">[データベースオブジェクト &#40;Analysis Services-多次元データ&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="eebe9-136">[Database Objects &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="eebe9-137">[論理アーキテクチャ &#40;Analysis Services-多次元データ&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="eebe9-137">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="eebe9-138">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="eebe9-138">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="eebe9-139">データ ソースとバインド &#40;SSAS 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="eebe9-139">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](data-sources-and-bindings-ssas-multidimensional.md)  
  
  
