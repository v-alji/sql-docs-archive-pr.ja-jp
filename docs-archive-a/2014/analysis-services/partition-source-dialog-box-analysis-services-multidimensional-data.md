---
title: '[パーティションソース] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionsourcedialog.f1
ms.assetid: c414dabe-9bad-49b7-9a3c-dfca87fef92b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6732e8f00dc0d01e0d3b708794a1d9c497ae4cf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711066"
---
# <a name="partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="81947-102">[パーティション ソース] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="81947-102">Partition Source Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="81947-103">**の** [パーティション ソース] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、パーティションのファクト テーブル データのソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="81947-103">Use the **Partition Source** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to specify the source of fact table data for a partition.</span></span> <span data-ttu-id="81947-104">**[パーティション ソース]** ダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="81947-104">You can display the **Partition Source** dialog box by:</span></span>  
  
-   <span data-ttu-id="81947-105">キューブ デザイナーの **[パーティション]** タブで、 **[メジャー グループ]** ペインにあるメジャー グループの **[パーティション]** グリッドを選択し、セル上の **[...]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="81947-105">Clicking the **...** button on a cell from the **Partitions** grid of a selected measure group in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="81947-106">**の** [プロパティ] **ウィンドウで、** Partition **オブジェクトの** [Source] **プロパティ値の** [...] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="81947-106">Clicking the **...** button on the **Source** property value of a **Partition** object in the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="81947-107">Options</span><span class="sxs-lookup"><span data-stu-id="81947-107">Options</span></span>  
  
|<span data-ttu-id="81947-108">オプション</span><span class="sxs-lookup"><span data-stu-id="81947-108">Option</span></span>|<span data-ttu-id="81947-109">定義</span><span class="sxs-lookup"><span data-stu-id="81947-109">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="81947-110">**バインドの種類**</span><span class="sxs-lookup"><span data-stu-id="81947-110">**Binding type**</span></span>|<span data-ttu-id="81947-111">バインドの種類を選択して、指定したパーティションのソースに使用します。</span><span class="sxs-lookup"><span data-stu-id="81947-111">Select the binding type to use for the source of the specified partition.</span></span> <span data-ttu-id="81947-112">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="81947-112">The following options are available:</span></span><br /><br /> <span data-ttu-id="81947-113">[**テーブルバインド**]:**テーブルバインドの詳細**ペインを表示し、パーティションがデータソースまたはデータソースビューのテーブルの内容にバインドされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="81947-113">**Table binding**: Select to display the **Table Binding Detail** pane and indicate that the partition is bound to the contents of a table in a data source or data source view.</span></span> <span data-ttu-id="81947-114">**[テーブル バインドの詳細]** ペインの詳細については、「[テーブル バインドの詳細 &#40;[パーティション ソース] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81947-114">For more information about the **Table Binding Detail** pane, see [Table Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="81947-115">**詳細**: [**クエリバインドの詳細**] ペインを表示し、データソースに対して実行されるクエリの内容にパーティションがバインドされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="81947-115">**Detail**: Select to display the **Query Binding Detail** pane and indicate that the partition is bound to the contents of a query executed on a data source.</span></span> <span data-ttu-id="81947-116">**[クエリ バインドの詳細]** ペインの詳細については、「[ バインドの詳細 &#40;[パーティション ソース] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81947-116">For more information about the **Query Binding Detail** pane, see [Query Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="81947-117">**詳細**</span><span class="sxs-lookup"><span data-stu-id="81947-117">**Detail**</span></span>|<span data-ttu-id="81947-118">**[バインドの種類]** オプションの値に応じて、 **テーブル バインドの詳細** または **クエリ バインドの詳細** のどちらかを表示します。</span><span class="sxs-lookup"><span data-stu-id="81947-118">Displays either the **Table Binding Detail** dialog box or the **Query Binding Detail** dialog box, depending on the value of the **Binding type** option.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81947-119">参照</span><span class="sxs-lookup"><span data-stu-id="81947-119">See Also</span></span>  
 <span data-ttu-id="81947-120">[パーティション &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="81947-120">[Partitions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="81947-121">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="81947-121">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
