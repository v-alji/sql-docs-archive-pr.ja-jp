---
title: スキーマ生成ウィザード (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2cd58ada8ea4c2dd17ba4427578ac1336a6bd353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642987"
---
# <a name="schema-generation-wizard-analysis-services"></a><span data-ttu-id="ac0d3-102">スキーマ生成ウィザード (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ac0d3-102">Schema Generation Wizard (Analysis Services)</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="ac0d3-103">では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベース内で OLAP プロジェクトを定義する際の、2 種類のリレーショナル スキーマ操作方法をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-103">supports two methods of working with relational schemas when defining OLAP objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="ac0d3-104">一般的に、OLAP オブジェクトは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベース内のデータ ソース ビューで作成される論理データ モデルに基づいて定義します。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-104">Generally, you will define OLAP objects based on a logical data model constructed in a data source view within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="ac0d3-105">このデータ ソース ビューは、データ ソース ビューでカスタマイズされる、1 つ以上のリレーショナル データ ソースのスキーマ要素に基づいて定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-105">This data source view is defined based on schema elements from one or more relational data sources, as customized in the data source view.</span></span>  
  
 <span data-ttu-id="ac0d3-106">または、OLAP オブジェクトを最初に定義してから、これらの OLAP オブジェクトをサポートするデータ ソース ビュー、データ ソース、および基になるリレーショナル データベース スキーマを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-106">Alternatively, you can define OLAP objects first, and then generate a data source view, a data source, and the underlying relational database schema that supports these OLAP objects.</span></span> <span data-ttu-id="ac0d3-107">このリレーショナル データベースは、サブジェクト領域データベースと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-107">This relational database is referred to as the subject area database.</span></span>  
  
 <span data-ttu-id="ac0d3-108">この方法はトップダウン デザインと呼ばれることもあり、プロトタイプや分析モデルの作成によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-108">This approach is sometimes called top-down design and is frequently used for prototyping and analysis modeling.</span></span> <span data-ttu-id="ac0d3-109">このアプローチに従う場合は、スキーマ生成ウィザードを使用することによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のプロジェクトまたはデータベースで定義されている OLAP オブジェクトに基づいて、基になるデータ ソース ビューとデータ ソース オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-109">When you use this approach, you use the Schema Generation Wizard to create the underlying data source view and data source objects based on the OLAP objects defined in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="ac0d3-110">これは、反復的なアプローチです。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-110">This is an iterative approach.</span></span> <span data-ttu-id="ac0d3-111">ほとんどの場合、ディメンションとキューブのデザインを変更するためにウィザードを何度か再実行することになります。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-111">You will most likely rerun the wizard multiple times as you change the design of the dimensions and cubes.</span></span> <span data-ttu-id="ac0d3-112">ウィザードを実行するたびに、基になるオブジェクトに変更内容が組み込まれ、基になるデータベースに含まれているデータができる限り保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-112">Each time you run the wizard, it incorporates the changes into the underlying objects and, as much as is possible, preserves the data contained in the underlying databases.</span></span>  
  
 <span data-ttu-id="ac0d3-113">生成されるスキーマは、SQL Server のリレーショナル データベース エンジン スキーマです。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-113">The schema that is generated is a SQL Server relational database engine schema.</span></span> <span data-ttu-id="ac0d3-114">このウィザードでは、他のリレーショナル データベース製品のスキーマは生成されません。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-114">The wizard does not generate schemas for other relational database products.</span></span>  
  
 <span data-ttu-id="ac0d3-115">サブジェクト領域データベースに入力されるデータは、SQL Server のリレーショナル データベースに入力するときに使用するツールとテクニックを使用して、別々に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-115">The data that is populated in the subject area database is added separately, using whatever tools and techniques you use to populate a SQL Server relational database.</span></span> <span data-ttu-id="ac0d3-116">ほとんどの場合、データはウィザードを再実行したときに保持されますが、例外もあります。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-116">In most cases, the data is preserved when you rerun the wizard, but there are exceptions.</span></span> <span data-ttu-id="ac0d3-117">たとえば、データを含んでいるディメンションまたは属性を削除した場合は、一部のデータが失われます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-117">For example, some data must be dropped if you delete a dimension or an attribute that contains data.</span></span> <span data-ttu-id="ac0d3-118">スキーマが変更されたため、スキーマ生成ウィザードで一部のデータを削除する必要がある場合は、データが削除される前に警告が表示されるので、再生成をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-118">If the Schema Generation Wizard must drop some data because of a schema change, you receive a warning before the data is dropped and can then cancel the regeneration.</span></span>  
  
 <span data-ttu-id="ac0d3-119">一般的に、スキーマ生成ウィザードによって生成されたオブジェクトに対する変更は、スキーマ生成ウィザードが次にそのオブジェクトを再生成したときに上書きされます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-119">As a general rule, any change that you make to an object that was originally generated by the Schema Generation Wizard is overwritten when the Schema Generation Wizard subsequently regenerates that object.</span></span> <span data-ttu-id="ac0d3-120">この主な例外は、スキーマ生成ウィザードで生成されたテーブルに列を追加する場合です。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-120">The primary exception to this rule is when you add columns to a table that the Schema Generation Wizard generated.</span></span> <span data-ttu-id="ac0d3-121">この場合、スキーマ生成ウィザードによって、テーブルに追加した列だけでなく、その列のデータも保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-121">In this case, the Schema Generation Wizard preserves the columns that you added to the table, as well as the data in these columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac0d3-122">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ac0d3-122">In this section</span></span>  
 <span data-ttu-id="ac0d3-123">次の表に、スキーマ生成ウィザードの操作方法を説明するその他のトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-123">The following table lists additional topics that explain how to work with the Schema Generation Wizard.</span></span>  
  
|<span data-ttu-id="ac0d3-124">トピック</span><span class="sxs-lookup"><span data-stu-id="ac0d3-124">Topic</span></span>|<span data-ttu-id="ac0d3-125">説明</span><span class="sxs-lookup"><span data-stu-id="ac0d3-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ac0d3-126">スキーマ生成ウィザードの使用 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ac0d3-126">Use the Schema Generation Wizard &#40;Analysis Services&#41;</span></span>](schema-generation-wizard-analysis-services.md)|<span data-ttu-id="ac0d3-127">サブジェクト領域データベースとステージング領域データベースのスキーマの生成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-127">Describes how to generate the schema for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="ac0d3-128">データベース スキーマの理解</span><span class="sxs-lookup"><span data-stu-id="ac0d3-128">Understanding the Database Schemas</span></span>](understanding-the-database-schemas.md)|<span data-ttu-id="ac0d3-129">サブジェクト領域データベースとステージング領域データベースに対して生成されるスキーマについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-129">Describes the schema that is generated for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="ac0d3-130">増分生成の理解</span><span class="sxs-lookup"><span data-stu-id="ac0d3-130">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)|<span data-ttu-id="ac0d3-131">スキーマ生成ウィザードの増分生成機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac0d3-131">Describes the incremental generation capabilities of the Schema Generation Wizard.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac0d3-132">参照</span><span class="sxs-lookup"><span data-stu-id="ac0d3-132">See Also</span></span>  
 <span data-ttu-id="ac0d3-133">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="ac0d3-133">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="ac0d3-134">[多次元モデルのデータソース](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="ac0d3-134">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="ac0d3-135">SSAS 多次元&#41;&#40;サポートされるデータソース</span><span class="sxs-lookup"><span data-stu-id="ac0d3-135">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
