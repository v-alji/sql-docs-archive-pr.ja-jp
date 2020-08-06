---
title: '[集計デザインの割り当て] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfc4f7a0847373360a79ddda366ad7aa3f02c5de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633676"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="30e49-102">[集計デザインの割り当て] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="30e49-102">Assign Aggregation Design Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="30e49-103">**の** [集計デザインの割り当て] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、1 つまたは複数のコピー先パーティションに集計デザインを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="30e49-103">Use the **Assign Aggregation Design** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to assign aggregation designs to one or more destination partitions.</span></span> <span data-ttu-id="30e49-104">**[集計デザインの割り当て]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** でパーティションまたは集計デザインを右クリックし、 **[集計デザインの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30e49-104">You can display the **Assign Aggregation Design** dialog box by right-clicking a partition or aggregation design in **Object Explorer** and selecting **Assign Aggregation Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="30e49-105">Options</span><span class="sxs-lookup"><span data-stu-id="30e49-105">Options</span></span>  
  
|<span data-ttu-id="30e49-106">期間</span><span class="sxs-lookup"><span data-stu-id="30e49-106">Term</span></span>|<span data-ttu-id="30e49-107">定義</span><span class="sxs-lookup"><span data-stu-id="30e49-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="30e49-108">**[集計のデザイン]**</span><span class="sxs-lookup"><span data-stu-id="30e49-108">**Aggregation designs**</span></span>|<span data-ttu-id="30e49-109">1 つまたは複数のコピー先パーティションに割り当てる集計デザインを選択します。</span><span class="sxs-lookup"><span data-stu-id="30e49-109">Select an aggregation design to assign to one or more destination partitions.</span></span>|  
|<span data-ttu-id="30e49-110">**[コピー先パーティション]**</span><span class="sxs-lookup"><span data-stu-id="30e49-110">**Destination partitions**</span></span>|<span data-ttu-id="30e49-111">集計デザインを割り当てるパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="30e49-111">Select the partitions to which to assign the aggregation design.</span></span> <span data-ttu-id="30e49-112">次のグリッドを使用して、コピー先パーティションを指定します。</span><span class="sxs-lookup"><span data-stu-id="30e49-112">The following grid is used to specify destination partitions:</span></span><br /><br /> <span data-ttu-id="30e49-113">\<check box>: 列ヘッダーのチェックボックスをオンまたはオフにして、一覧表示されているすべてのパーティションを対象パーティションとして追加または除外します。</span><span class="sxs-lookup"><span data-stu-id="30e49-113">\<check box>: Select or clear the check box in the column header to include or exclude all listed partitions as destination partitions.</span></span> <span data-ttu-id="30e49-114">パーティション横にあるチェック ボックスをオンまたはオフにすることで、そのパーティションをコピー先パーティションとして選択または選択解除できます。</span><span class="sxs-lookup"><span data-stu-id="30e49-114">Select or clear a check box next to a partition to include or exclude that partition as a destination partition.</span></span><br /><br /> <span data-ttu-id="30e49-115">**パーティション**: パーティションの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="30e49-115">**Partition**: Displays the name of the partition.</span></span><br /><br /> <span data-ttu-id="30e49-116">[**ソース**: パーティションのソーステーブルまたはクエリを表示します。</span><span class="sxs-lookup"><span data-stu-id="30e49-116">**Source**: Displays the source table or query for the partition.</span></span><br /><br /> <span data-ttu-id="30e49-117">**集計のデザイン**: パーティションの既存の集計デザインの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="30e49-117">**Aggregation Design**: Displays the name of the existing aggregation design for the partition.</span></span>|  
|<span data-ttu-id="30e49-118">**[集計デザインを含むパーティションを非表示にする]**</span><span class="sxs-lookup"><span data-stu-id="30e49-118">**Hide partitions with aggregation designs**</span></span>|<span data-ttu-id="30e49-119">オンにすると、集計デザインが割り当てられていないパーティションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30e49-119">Select to show only the partitions that do not have aggregation designs assigned to them.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30e49-120">参照</span><span class="sxs-lookup"><span data-stu-id="30e49-120">See Also</span></span>  
 [<span data-ttu-id="30e49-121">集計と集計デザイン</span><span class="sxs-lookup"><span data-stu-id="30e49-121">Aggregations and Aggregation Designs</span></span>](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
