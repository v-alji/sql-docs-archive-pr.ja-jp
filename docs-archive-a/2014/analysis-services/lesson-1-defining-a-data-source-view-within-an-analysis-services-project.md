---
title: 'レッスン 1: Analysis Services プロジェクト内でのデータソースビューの定義 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7d3ffabd-78ae-4204-8323-29949d030c16
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a3d69225217154e5072d0cd34349a247730ddaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740585"
---
# <a name="lesson-1-defining-a-data-source-view-within-an-analysis-services-project"></a><span data-ttu-id="5d102-102">レッスン 1:Analysis Services プロジェクト内でのデータ ソース ビューの定義</span><span class="sxs-lookup"><span data-stu-id="5d102-102">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>
  <span data-ttu-id="5d102-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でビジネス インテリジェンス アプリケーションを設計するには、まず、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d102-103">Designing a business intelligence application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with creating an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="5d102-104">このプロジェクト内で、ソリューションに必要なすべての要素を定義します。最初に定義するのはデータ ソース ビューです。</span><span class="sxs-lookup"><span data-stu-id="5d102-104">Within this project, you define all the elements of your solution, starting with a data source view.</span></span>  
  
 <span data-ttu-id="5d102-105">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5d102-105">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="5d102-106">Analysis Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="5d102-106">Creating an Analysis Services Project</span></span>](lesson-1-1-creating-an-analysis-services-project.md)  
 <span data-ttu-id="5d102-107">この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モデル テンプレートに基づいて [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d102-107">In this task, you create the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, based on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model template.</span></span>  
  
 [<span data-ttu-id="5d102-108">データ ソースの定義</span><span class="sxs-lookup"><span data-stu-id="5d102-108">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
 <span data-ttu-id="5d102-109">この実習では、この後のレッスンで定義する **ディメンションおよびキューブのデータ ソースとして、** AdventureWorksDW2012 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d102-109">In this task, you specify the **AdventureWorksDW2012** database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dimensions and cubes that you will define in subsequent lessons.</span></span>  
  
 [<span data-ttu-id="5d102-110">データ ソース ビューの定義</span><span class="sxs-lookup"><span data-stu-id="5d102-110">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
 <span data-ttu-id="5d102-111">この実習では、 **AdventureWorksDW2012** データベースの選択したテーブルに格納されているメタデータを 1 つにまとめた統合ビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="5d102-111">In this task, you define a single unified view of the metadata from selected tables in the **AdventureWorksDW2012** database.</span></span>  
  
 [<span data-ttu-id="5d102-112">既定のテーブル名の変更</span><span class="sxs-lookup"><span data-stu-id="5d102-112">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
 <span data-ttu-id="5d102-113">この実習では、この後で定義する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを識別しやすくするために、データ ソース ビューのテーブル名をわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="5d102-113">In this task, you modify table names in the data source view, so that the names of subsequent [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects that you define will be more user-friendly.</span></span>  
  
 <span data-ttu-id="5d102-114">結果を、このレッスン用にビルドされたサンプル プロジェクト ファイルと比較してください。</span><span class="sxs-lookup"><span data-stu-id="5d102-114">Compare your results against a sample project file that was built for this lesson.</span></span> <span data-ttu-id="5d102-115">このチュートリアルのサンプル プロジェクトのダウンロードの詳細については、CodePlex の製品サンプル ページで「 [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d102-115">For more information about downloading the sample projects that go with this tutorial, see [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) on the product samples page on codeplex.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="5d102-116">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="5d102-116">Next Lesson</span></span>  
 [<span data-ttu-id="5d102-117">レッスン 2: キューブの定義と配置</span><span class="sxs-lookup"><span data-stu-id="5d102-117">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d102-118">参照</span><span class="sxs-lookup"><span data-stu-id="5d102-118">See Also</span></span>  
 <span data-ttu-id="5d102-119">[SSDT&#41;&#40;Analysis Services プロジェクトを作成する](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="5d102-119">[Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span></span>  
 <span data-ttu-id="5d102-120">[SSAS 多次元&#41;&#40;サポートされるデータソース](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="5d102-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="5d102-121">[多次元モデルのデータソースビュー](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="5d102-121">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="5d102-122">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5d102-122">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="5d102-123">多次元モデリング (Adventure Works チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="5d102-123">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
