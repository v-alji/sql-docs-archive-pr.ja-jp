---
title: 'レッスン 1: Analysis Services データベースの準備 (基本的なデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a796977-6568-4705-9d27-86a9b36658c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 07647a940851fbdbdc65357e168747662dc88380
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742717"
---
# <a name="lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial"></a><span data-ttu-id="c6dfb-102">レッスン 1: Analysis Services データベースの準備 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c6dfb-102">Lesson 1: Preparing the Analysis Services Database (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="c6dfb-103">では、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ビジネスインテリジェンスアプリケーションの設計を担当してきた新しい従業員です [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-103">You are a new employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with designing a business intelligence application in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]<span data-ttu-id="c6dfb-104">データマイニングエクスペリエンスを活用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、自転車を購入したユーザーに関する興味のある実用的な情報を見つけることを希望しています。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-104">hopes to leverage your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data mining experience to discover interesting and actionable information about people who have purchased bicycles.</span></span> <span data-ttu-id="c6dfb-105">また、将来自転車を購入する可能性が最も高い顧客を予測することも求められています。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-105">They then want you to predict which prospective customers are most likely to purchase a bicycle in the future.</span></span>  
  
 <span data-ttu-id="c6dfb-106">でこのアプリケーションを設計するに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、まず、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モデリングとデータマイニングのプロジェクトテンプレートに基づくプロジェクトの作成を行います。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-106">Designing this application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with the creation in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project template for multidimensional modeling and data mining.</span></span> <span data-ttu-id="c6dfb-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを作成したら、データ ソースを 1 つ以上定義します。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-107">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you define one or more data sources.</span></span> <span data-ttu-id="c6dfb-108">次に、データソースから選択したテーブルおよびビューから、*データソースビュー*と呼ばれるメタデータのビューを定義します。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-108">Then, you define a view of the metadata, called a *data source view*, from selected tables and views from the data sources.</span></span>  
  
 <span data-ttu-id="c6dfb-109">このレッスンでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを作成し、データ ソースを 1 つ作成した後、テーブルのサブセットをデータ ソース ビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-109">In this lesson, you will create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, define a single data source, and add a subset of tables to a data source view.</span></span> <span data-ttu-id="c6dfb-110">このレッスンには、次のタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-110">This lesson includes the following tasks:</span></span>  
  
 [<span data-ttu-id="c6dfb-111">基本的なデータマイニングチュートリアル &#40;Analysis Services プロジェクトの作成&#41;</span><span class="sxs-lookup"><span data-stu-id="c6dfb-111">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="c6dfb-112">データソースの作成 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="c6dfb-112">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="c6dfb-113">データソースビューの作成基本的なデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="c6dfb-113">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="c6dfb-114">このレッスンの最初の作業</span><span class="sxs-lookup"><span data-stu-id="c6dfb-114">First Task in Lesson</span></span>  
 [<span data-ttu-id="c6dfb-115">基本的なデータマイニングチュートリアル &#40;Analysis Services プロジェクトの作成&#41;</span><span class="sxs-lookup"><span data-stu-id="c6dfb-115">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="c6dfb-116">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="c6dfb-116">Next Lesson</span></span>  
 [<span data-ttu-id="c6dfb-117">レッスン 2: &#40;の基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="c6dfb-117">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6dfb-118">参照</span><span class="sxs-lookup"><span data-stu-id="c6dfb-118">See Also</span></span>  
 <span data-ttu-id="c6dfb-119">[多次元モデルのデータソースビュー](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span><span class="sxs-lookup"><span data-stu-id="c6dfb-119">[Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span></span>  
 <span data-ttu-id="c6dfb-120">[SSAS 多次元&#41;&#40;サポートされるデータソース](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="c6dfb-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span></span>  
 <span data-ttu-id="c6dfb-121">[ビルド Analysis Services プロジェクト &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="c6dfb-121">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="c6dfb-122">Analysis Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c6dfb-122">Creating an Analysis Services Project</span></span>](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)  
  
  
