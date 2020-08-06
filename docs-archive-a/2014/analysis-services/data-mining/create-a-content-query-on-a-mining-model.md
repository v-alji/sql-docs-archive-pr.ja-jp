---
title: マイニングモデルに対するコンテンツクエリの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: a0ce837a-89ed-46cf-9ce1-801ccb75fa04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26af1100d6ba80185c1cc4de18548df0e387824c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711161"
---
# <a name="create-a-content-query-on-a-mining-model"></a><span data-ttu-id="6cb6f-102">マイニング モデルのコンテンツ クエリの作成</span><span class="sxs-lookup"><span data-stu-id="6cb6f-102">Create a Content Query on a Mining Model</span></span>
  <span data-ttu-id="6cb6f-103">AMO や XML/A を使用すると、プログラムでマイニング モデル コンテンツにクエリを実行できますが、DMX を使用してクエリを作成する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-103">You can query the mining model content programmatically by using AMO or XML/A, but it is easier to create queries by using DMX.</span></span> <span data-ttu-id="6cb6f-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへの接続を確立し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]によって提供される DMV を使用してクエリを作成することにより、データ マイニング スキーマ行セットに対するクエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-104">You can also create queries against the data mining schema rowsets by establishing a connection to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and creating a query using the DMVs provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6cb6f-105">次の手順では、DMX を使用してマイニング モデルに対するクエリを作成する方法と、データ マイニング スキーマ行セットに対するクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-105">The following procedures demonstrate how to create queries against a mining model by using DMX, and how to query the data mining schema rowsets.</span></span>  
  
 <span data-ttu-id="6cb6f-106">XML/A を使用して類似のクエリを作成する方法の例については、「 [XMLA を使用したデータ マイニング クエリの作成](create-a-data-mining-query-by-using-xmla.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-106">For an example of how to create a similar query by using XML/A, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="querying-data-mining-model-content-by-using-dmx"></a><span data-ttu-id="6cb6f-107">DMX を使用したデータ マイニング モデル コンテンツのクエリ</span><span class="sxs-lookup"><span data-stu-id="6cb6f-107">Querying Data Mining Model Content by Using DMX</span></span>  
  
#### <a name="to-create-a-dmx-model-content-query"></a><span data-ttu-id="6cb6f-108">DMX モデル コンテンツ クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="6cb6f-108">To create a DMX model content query</span></span>  
  
1.  <span data-ttu-id="6cb6f-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="6cb6f-110">**[テンプレート エクスプローラー]** ペインで、キューブ アイコンをクリックして一覧を変更し、Analysis Services テンプレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-110">In the **Template Explorer** pane, click the cube icon to change the list and display Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="6cb6f-111">テンプレート カテゴリの一覧で、 **[DMX]**、 **[モデル コンテンツ]** の順に展開し、 **[コンテンツ クエリ]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-111">In the list of template categories, expand **DMX**, expand **Model Content**, and double-click **Content Query**.</span></span>  
  
4.  <span data-ttu-id="6cb6f-112">**[Analysis Services への接続]** ダイアログ ボックスで、クエリを実行するマイニング モデルを含むインスタンスを選択し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-112">In the **Connect to Analysis Services** dialog box, select the instance that contains the mining model you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="6cb6f-113">コード エディターに **[コンテンツ クエリ]** テンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-113">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="6cb6f-114">メタデータ ペインに、現在のデータベースで使用可能なモデルが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-114">The metadata pane lists the models that are available in the current database.</span></span> <span data-ttu-id="6cb6f-115">データベースを変更するには、 **[使用できるデータベース]** の一覧から別のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-115">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
5.  <span data-ttu-id="6cb6f-116">[] 行に、マイニングモデルの名前を入力 `FROM` し *\<mining model, name, MyModel>* `.CONTENT` ます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-116">Enter the name of a mining model in the line, `FROM` [*\<mining model, name, MyModel>*]`.CONTENT`.</span></span> <span data-ttu-id="6cb6f-117">マイニング モデル名にスペースが含まれる場合は、名前を角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-117">If the mining model name contains spaces, you must enclose the name in brackets.</span></span>  
  
     <span data-ttu-id="6cb6f-118">名前を入力せずに、 **オブジェクト エクスプローラー** でマイニング モデルを選択してテンプレートにドラッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-118">If you don't want to type the name, you can select a mining model in **Object Explorer** and drag it into the template.</span></span>  
  
6.  <span data-ttu-id="6cb6f-119">行に、 `SELECT` *\<select list, expr list, \*>* マイニングモデルコンテンツスキーマ行セットの列の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-119">In the line, `SELECT`*\<select list, expr list, \*>*, type the names of columns in the mining model content schema rowset.</span></span>  
  
     <span data-ttu-id="6cb6f-120">マイニング モデル コンテンツ クエリで返すことができる列の一覧については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)によって提供される DMV を使用してクエリを作成することにより、データ マイニング スキーマ行セットに対するクエリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-120">To view a list of columns that you can return in mining model content queries, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
7.  <span data-ttu-id="6cb6f-121">必要に応じて、テンプレートの WHERE 句に条件を入力し、特定のノードや値に対して返される行を制限します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-121">Optionally, type a condition in the WHERE clause of the template to restrict the rows returned to specific nodes or values.</span></span>  
  
8.  <span data-ttu-id="6cb6f-122">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-122">Click **Execute**.</span></span>  
  
## <a name="querying-the-data-mining-schema-rowsets"></a><span data-ttu-id="6cb6f-123">データ マイニング スキーマ行セットのクエリ</span><span class="sxs-lookup"><span data-stu-id="6cb6f-123">Querying the Data Mining Schema Rowsets</span></span>  
  
#### <a name="to-create-a-query-against-the-data-mining-schema-rowset"></a><span data-ttu-id="6cb6f-124">データ マイニング スキーマ行セットに対するクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="6cb6f-124">To create a query against the data mining schema rowset</span></span>  
  
1.  <span data-ttu-id="6cb6f-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の **[新しいクエリ]** ツール バーで、 **[Analysis Services DMX クエリ]** または **[Analysis Services MDX クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **New Query** toolbar, click **Analysis Services DMX Query**, or **Analysis Services MDX query**.</span></span>  
  
2.  <span data-ttu-id="6cb6f-126">**[Analysis Services への接続]** ダイアログ ボックスで、クエリを実行するオブジェクトを含むインスタンスを選択し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-126">In the **Connect to Analysis Services** dialog box, select the instance that contains the objects you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="6cb6f-127">コード エディターに **[コンテンツ クエリ]** テンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-127">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="6cb6f-128">メタデータ ペインに、現在のデータベースで使用可能なオブジェクトが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-128">The metadata pane lists the objects that are available in the current database.</span></span> <span data-ttu-id="6cb6f-129">データベースを変更するには、 **[使用できるデータベース]** の一覧から別のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-129">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
3.  <span data-ttu-id="6cb6f-130">クエリ エディターに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-130">In the query editor, type the following:</span></span>  
  
     `SELECT *`  
  
     `FROM $system.DMSCHEMA_MINING_MODEL_CONTENT`  
  
     `WHERE MODEL_NAME = '<model name>'`  
  
4.  <span data-ttu-id="6cb6f-131">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="6cb6f-132">結果ペインにモデルのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-132">The Results pane displays the contents of the model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6cb6f-133">現在のインスタンスでクエリを実行できるすべてのスキーマ行セットを一覧表示するには、 `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS というクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-133">To view a list of all the schema rowsets that you can query on the current instance, use this query: `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS.</span></span> <span data-ttu-id="6cb6f-134">データ マイニング固有のスキーマ行セットの一覧については、「 [データ マイニング スキーマ行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cb6f-134">Or, for a list of schema rowsets specific to data mining, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb6f-135">参照</span><span class="sxs-lookup"><span data-stu-id="6cb6f-135">See Also</span></span>  
 <span data-ttu-id="6cb6f-136">[マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6cb6f-136">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="6cb6f-137">データ マイニング スキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="6cb6f-137">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
