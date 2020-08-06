---
title: データベースオブジェクト (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d61e3213356146e1cf9e452e0b62e02c96bd4902
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743566"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="79454-102">データベース オブジェクト (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="79454-102">Database Objects (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="79454-103">インスタンスには、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オンライン分析処理 (OLAP) およびデータマイニングで使用するデータベースオブジェクトとアセンブリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79454-103">A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance contains database objects and assemblies for use with online analytical processing (OLAP) and data mining.</span></span>  
  
-   <span data-ttu-id="79454-104">データベースには、OLAP と、データ ソース、データ ソース ビュー、キューブ、メジャー、メジャー グループ、ディメンション、属性、階層、マイニング構造、マイニング モデル、ロールなどのデータ マイニング オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79454-104">Databases contain OLAP and data mining objects, such as data sources, data source views, cubes, measures, measure groups, dimensions, attributes, hierarchies, mining structures, mining models and roles.</span></span>  
  
-   <span data-ttu-id="79454-105">アセンブリには、ユーザー定義関数が含まれており、多次元式 (MDX) 言語およびデータ マイニング拡張機能 (DMX) 言語が提供されている固有の関数の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="79454-105">Assemblies contain user-defined functions that extend the functionality of the intrinsic functions provided with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span>  
  
 <span data-ttu-id="79454-106"><xref:Microsoft.AnalysisServices.Database> オブジェクトは、ビジネス インテリジェンス プロジェクトに必要なすべてのデータ オブジェクト (OLAP キューブ、ディメンション、データ マイニング構造など) とそのサポート オブジェクト (<xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.Account>、<xref:Microsoft.AnalysisServices.Role> など) のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="79454-106">The <xref:Microsoft.AnalysisServices.Database> object is the container for all data objects that are needed for a business intelligence project (such as OLAP cubes, dimensions, and data mining structures), and their supporting objects (such as <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account>, and <xref:Microsoft.AnalysisServices.Role>).</span></span>  
  
 <span data-ttu-id="79454-107"><xref:Microsoft.AnalysisServices.Database> オブジェクトは、次のオブジェクトや属性へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="79454-107">A <xref:Microsoft.AnalysisServices.Database> object provides access to objects and attributes that include the following:</span></span>  
  
-   <span data-ttu-id="79454-108">アクセスできるすべてのキューブ (コレクション)</span><span class="sxs-lookup"><span data-stu-id="79454-108">All cubes that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="79454-109">アクセスできるすべてのディメンション (コレクション)</span><span class="sxs-lookup"><span data-stu-id="79454-109">All dimensions that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="79454-110">アクセスできるすべてのマイニング構造 (コレクション)</span><span class="sxs-lookup"><span data-stu-id="79454-110">All mining structures that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="79454-111">すべてのデータ ソースとデータ ソース ビュー (2 つのコレクション)</span><span class="sxs-lookup"><span data-stu-id="79454-111">All data sources and data source views, as two collections.</span></span>  
  
-   <span data-ttu-id="79454-112">すべてのロールとデータベース権限 (2 つのコレクション)</span><span class="sxs-lookup"><span data-stu-id="79454-112">All roles and database permissions, as two collections.</span></span>  
  
-   <span data-ttu-id="79454-113">データベースの照合順序の値</span><span class="sxs-lookup"><span data-stu-id="79454-113">The collation value for the database.</span></span>  
  
-   <span data-ttu-id="79454-114">データベースの推定サイズ</span><span class="sxs-lookup"><span data-stu-id="79454-114">The estimated size of the database.</span></span>  
  
-   <span data-ttu-id="79454-115">データベースの言語の値</span><span class="sxs-lookup"><span data-stu-id="79454-115">The language value of the database.</span></span>  
  
-   <span data-ttu-id="79454-116">データベースの表示の設定</span><span class="sxs-lookup"><span data-stu-id="79454-116">The visible setting for the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79454-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="79454-117">In This Section</span></span>  
 <span data-ttu-id="79454-118">次のトピックでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で OLAP とデータ マイニング機能の両方によって共有されるオブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79454-118">The following topics describe objects shared by both OLAP and data mining features in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="79454-119">トピック</span><span class="sxs-lookup"><span data-stu-id="79454-119">Topic</span></span>|<span data-ttu-id="79454-120">説明</span><span class="sxs-lookup"><span data-stu-id="79454-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="79454-121">多次元モデルのデータ ソース</span><span class="sxs-lookup"><span data-stu-id="79454-121">Data Sources in Multidimensional Models</span></span>](../data-sources-in-multidimensional-models.md)|<span data-ttu-id="79454-122">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79454-122">Describes a data source in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="79454-123">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="79454-123">Data Source Views in Multidimensional Models</span></span>](../data-source-views-in-multidimensional-models.md)|<span data-ttu-id="79454-124">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で、1 つ以上のデータ ソースに基づく論理データ モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79454-124">Describes a logical data model based on one or more data sources, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="79454-125">多次元モデルのキューブ</span><span class="sxs-lookup"><span data-stu-id="79454-125">Cubes in Multidimensional Models</span></span>](../cubes-in-multidimensional-models.md)|<span data-ttu-id="79454-126">キューブと、メジャー、メジャー グループ、ディメンションの使用法とリレーションシップ、計算、主要業績評価指標 (KPI)、アクション、翻訳、パーティション、パースペクティブなどのキューブ オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79454-126">Describes cubes and cube objects, including measures, measure groups, dimension usage relationships, calculations, key performance indicators, actions, translations, partitions, and perspectives.</span></span>|  
|[<span data-ttu-id="79454-127">ディメンション &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="79454-127">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="79454-128">ディメンションと、属性、属性リレーションシップ、階層、レベル、メンバーなどのディメンション オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79454-128">Describes dimensions and dimension objects, including attributes, attribute relationships, hierarchies, levels, and members.</span></span>|  
|[<span data-ttu-id="79454-129">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="79454-129">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../data-mining/mining-structures-analysis-services-data-mining.md)|<span data-ttu-id="79454-130">マイニング構造と、マイニング モデルなどのマイニング オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79454-130">Describes mining structures and mining objects, including mining models.</span></span>|  
|[<span data-ttu-id="79454-131">セキュリティ ロール (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="79454-131">Security Roles  &#40;Analysis Services - Multidimensional Data&#41;</span></span>](security-roles-analysis-services-multidimensional-data.md)|<span data-ttu-id="79454-132">ロールについて説明します。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でオブジェクトへのアクセスを制御するために使用するセキュリティ メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="79454-132">Describes a role, the security mechanism used to control access to objects in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="79454-133">多次元モデルのアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="79454-133">Multidimensional Model Assemblies Management</span></span>](../multidimensional-model-assemblies-management.md)|<span data-ttu-id="79454-134">アセンブリについて説明します。これは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で、MDX 言語と DMX 言語を拡張するために使用するユーザー定義関数のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="79454-134">Describes an assembly, a collection of user-defined functions used to extend the MDX and DMX languages, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79454-135">参照</span><span class="sxs-lookup"><span data-stu-id="79454-135">See Also</span></span>  
 <span data-ttu-id="79454-136">[SSAS 多次元&#41;&#40;サポートされるデータソース](../supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="79454-136">[Data Sources Supported &#40;SSAS Multidimensional&#41;](../supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="79454-137">[SSAS&#41;&#40;の多次元モデルソリューション](../multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="79454-137">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="79454-138">データ マイニング ソリューション</span><span class="sxs-lookup"><span data-stu-id="79454-138">Data Mining Solutions</span></span>](../../data-mining/data-mining-solutions.md)  
  
  
