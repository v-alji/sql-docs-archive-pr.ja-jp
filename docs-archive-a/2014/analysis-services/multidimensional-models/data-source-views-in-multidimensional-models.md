---
title: 多次元モデルのデータソースビュー |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services]
- data source views [Analysis Services], about data source views
- SQL Server Analysis Services, data source views
- data source views [Analysis Services], multiple
- Analysis Services, data source views
- multiple data source views
- SSAS, data source views
ms.assetid: 4c12376f-4fc2-492b-9a00-93eec34571ed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1aef6b6d716ec71ac082ca8b7c042492c1712b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741410"
---
# <a name="data-source-views-in-multidimensional-models"></a><span data-ttu-id="881cd-102">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="881cd-102">Data Source Views in Multidimensional Models</span></span>
  <span data-ttu-id="881cd-103">データ ソース ビュー (DSV) は、リレーショナル データ ソースを抽象化し、多次元プロジェクト内でキューブやディメンションを作成する基礎となります。</span><span class="sxs-lookup"><span data-stu-id="881cd-103">A data source view (DSV) is an abstraction of a relational data source that becomes the basis of the cubes and dimensions you create in a multidimensional project.</span></span> <span data-ttu-id="881cd-104">DSV の目的は、プロジェクトで使用するデータ構造をユーザーが制御できるようにすることと、基になるデータ ソースから独立して動作することです (たとえば、元のデータ ソースを変更せずに、列の名前の変更や列の連結を行うことができます)。</span><span class="sxs-lookup"><span data-stu-id="881cd-104">The purpose of a DSV is to give you control over the data structures used in your project, and to work independently of the underlying data sources (for example, the ability to rename or concatenate columns without directly modifying the original data source).</span></span>  
  
 <span data-ttu-id="881cd-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベースでは 1 つまたは複数のデータ ソースに関する複数のデータ ソース ビューを構築して、各ソリューションの要件を各ビューが満たすようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="881cd-105">You can build multiple data source views in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database on one or more data sources, and construct each one to satisfy the requirements for a different solution.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="881cd-106">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="881cd-106">Related Tasks</span></span>  
 [<span data-ttu-id="881cd-107">データ ソース ビューの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-107">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](defining-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-108">データ ソース ビューでのテーブルまたはビューの追加または削除 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-108">Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;</span></span>](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-109">データ ソース ビューのプロパティの変更 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="881cd-109">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-110">データ ソース ビューでの論理リレーションシップの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-110">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-relationships-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-111">データ ソース ビューでの論理主キーの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-111">Define Logical Primary Keys in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-primary-keys-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-112">データ ソース ビューでの名前付き計算の定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-112">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-113">データ ソース ビューでの名前付きクエリの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-113">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-114">データ ソース ビュー内のテーブルまたは名前付きクエリの置換 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-114">Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;</span></span>](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-115">データ ソース ビュー デザイナーでのダイアグラムの操作 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-115">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
 [<span data-ttu-id="881cd-116">データ ソース ビューでのデータの検索 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-116">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](explore-data-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-117">データ ソース ビューの削除 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-117">Delete a Data Source View &#40;Analysis Services&#41;</span></span>](delete-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="881cd-118">データ ソース ビューでのスキーマの更新 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="881cd-118">Refresh the Schema in a Data Source View &#40;Analysis Services&#41;</span></span>](refresh-the-schema-in-a-data-source-view-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="881cd-119">参照</span><span class="sxs-lookup"><span data-stu-id="881cd-119">See Also</span></span>  
 <span data-ttu-id="881cd-120">[スキーマ生成ウィザード &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="881cd-120">[Schema Generation Wizard &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span></span>  
 [<span data-ttu-id="881cd-121">SSAS 多次元&#41;&#40;サポートされるデータソース</span><span class="sxs-lookup"><span data-stu-id="881cd-121">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
