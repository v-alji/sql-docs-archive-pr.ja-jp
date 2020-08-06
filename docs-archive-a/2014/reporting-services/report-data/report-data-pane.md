---
title: レポート データ ペイン
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fc09c100cc8391bb1fd025b4bb5ac5f3b5e4379a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631571"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="ff2e9-102">SQL Server Reporting Services (SSRS) の [レポート データ] ペイン</span><span class="sxs-lookup"><span data-stu-id="ff2e9-102">Report Data pane in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="ff2e9-103">**[レポート データ]** ペインを使用すると、レポート内で現在定義されているパラメーター、データ ソース、データセット、フィールド コレクション、および画像が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-103">Use the **Report Data** pane to view the currently defined parameters, data sources, datasets, field collections, and images in your report.</span></span> <span data-ttu-id="ff2e9-104">[レポート データ] では、レポート内のデータを表すアイテムの階層ビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-104">The Report Dane displays a hierarchical view of the items that represent data in your report.</span></span> <span data-ttu-id="ff2e9-105">最上位のノードは、組み込みフィールド、パラメーター、画像、およびデータ ソース参照を表します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-105">The top level nodes represent built-in fields, parameters, images, and data source references.</span></span> <span data-ttu-id="ff2e9-106">データ アイテムを表示するには、各ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-106">Expand each node to view the data items.</span></span> <span data-ttu-id="ff2e9-107">たとえば、データ ソース ノードを展開すると、そのデータ ソース用に定義されたデータセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-107">For example, when you expand a data source node, the datasets defined for that data source appear.</span></span> <span data-ttu-id="ff2e9-108">データセットを展開すると、そのフィールド コレクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-108">When you expand a dataset, its field collection appears.</span></span> <span data-ttu-id="ff2e9-109">データをレポート ページ上のレポート アイテムにリンクするには、アイテムをレポート デザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-109">Drag items to the report design surface to link data with report items on the report page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ff2e9-110">オプション</span><span class="sxs-lookup"><span data-stu-id="ff2e9-110">Options</span></span>

 <span data-ttu-id="ff2e9-111">**組み込みフィールド**</span><span class="sxs-lookup"><span data-stu-id="ff2e9-111">**Built-in Fields**</span></span>  
 <span data-ttu-id="ff2e9-112">レポート名やページ番号など、レポートでよく使用される、Reporting Services に用意されているフィールドを表します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-112">Represents fields provided by Reporting Services that are commonly used in a report, such as the report name or page number.</span></span> <span data-ttu-id="ff2e9-113">詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-113">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="ff2e9-114">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ff2e9-114">**Parameters**</span></span>  
 <span data-ttu-id="ff2e9-115">レポート パラメーターのコレクションを表します。各パラメーターには単一の値または複数の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-115">Represents the collection of report parameters, each of which can be single-valued or multivalued.</span></span> <span data-ttu-id="ff2e9-116">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-116">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="ff2e9-117">**イメージ**</span><span class="sxs-lookup"><span data-stu-id="ff2e9-117">**Images**</span></span>  
 <span data-ttu-id="ff2e9-118">レポートで使用されている画像のセットを表します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-118">Represents the set of images used in the report.</span></span> <span data-ttu-id="ff2e9-119">詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](../report-design/images-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-119">For more information, see [Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ff2e9-120">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="ff2e9-120">**Data source**</span></span>  
 <span data-ttu-id="ff2e9-121">埋め込みデータ ソースまたは共有データ ソースへの単一のデータ ソース参照を表します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-121">Represents a single data source reference to an embedded data source or to a shared data source.</span></span> <span data-ttu-id="ff2e9-122">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、共有データ ソースがソリューション エクスプローラーの [共有データ ソース] フォルダーの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], shared data sources appear in Solution Explorer under the Shared Data Sources folder.</span></span> <span data-ttu-id="ff2e9-123">データ ソースは、Reporting Services でサポートされているデータ ソースの種類のうち 1 つを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-123">A data source specifies one of the data source types supported by Reporting Services.</span></span> <span data-ttu-id="ff2e9-124">データ ソースは、そのデータ ソースに基づくデータセットのコレクションの親ノードです。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-124">A data source is the parent node for the collection of datasets based on it.</span></span> <span data-ttu-id="ff2e9-125">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-125">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) .</span></span>  
  
 <span data-ttu-id="ff2e9-126">**データセット**</span><span class="sxs-lookup"><span data-stu-id="ff2e9-126">**Dataset**</span></span>  
 <span data-ttu-id="ff2e9-127">1 つのデータセットを表します。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-127">Represents a single dataset.</span></span> <span data-ttu-id="ff2e9-128">データセットは、クエリで指定され、計算フィールドを含むフィールドのコレクションの親ノードです。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-128">A dataset is the parent node for the collection of fields specified by the query and including any calculated fields.</span></span> <span data-ttu-id="ff2e9-129">Reporting Services では、クエリを指定できるようにクエリ デザイナーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-129">Reporting Services supports query designers to help you specify a query.</span></span> <span data-ttu-id="ff2e9-130">詳細については、「[レポートへのデータの追加 &#40;レポートビルダーと ssrs&#41;](report-datasets-ssrs.md) 」および「[レポートデザイナー SQL Server Data Tools &#40;Ssrs&#41;のクエリデザインツール](query-design-tools-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff2e9-130">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) and [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ff2e9-131">次のステップ</span><span class="sxs-lookup"><span data-stu-id="ff2e9-131">Next steps</span></span>

 - [<span data-ttu-id="ff2e9-132">データセット フィールド コレクション (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ff2e9-132">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)
 - [<span data-ttu-id="ff2e9-133">グループ化ペイン</span><span class="sxs-lookup"><span data-stu-id="ff2e9-133">Grouping Pane</span></span>](../tools/grouping-pane.md)