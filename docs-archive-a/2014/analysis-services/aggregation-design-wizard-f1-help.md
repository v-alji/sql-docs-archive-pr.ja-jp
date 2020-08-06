---
title: 集計のデザインウィザードの F1 ヘルプ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregation Design Wizard
ms.assetid: 39e23cf1-6405-4fb6-bc14-ba103314362d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace30a07970b1871d037ebe6f31b2079f1895ffa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633690"
---
# <a name="aggregation-design-wizard-f1-help"></a><span data-ttu-id="f93d4-102">集計のデザイン ウィザードの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="f93d4-102">Aggregation Design Wizard F1 Help</span></span>
  <span data-ttu-id="f93d4-103">集計を使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] クエリごとに基になるデータソースのデータを再計算するのではなく、キューブストレージから事前計算済みの合計を直接取得できるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f93d4-103">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="f93d4-104">こうした集計のデザインは、集計のデザイン ウィザードを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="f93d4-104">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="f93d4-105">このウィザードでは、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f93d4-105">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="f93d4-106">パーティション、メジャー グループ、またはキューブのストレージとキャッシュのオプションに対して、標準またはカスタムの設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="f93d4-106">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="f93d4-107">パーティション、メジャー グループ、またはキューブによって参照されるオブジェクトの推定カウントまたは実際のカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="f93d4-107">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="f93d4-108">集計オプションと制限を指定して、デザインされた集計によって配信されるストレージとクエリのパフォーマンスを最適化します。</span><span class="sxs-lookup"><span data-stu-id="f93d4-108">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="f93d4-109">パーティション、メジャー グループ、またはキューブの保存と処理 (省略可) を行い、定義された集計を生成します。</span><span class="sxs-lookup"><span data-stu-id="f93d4-109">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 <span data-ttu-id="f93d4-110">集計のデザイン ウィザードを使用した後で、使用法に基づく最適化ウィザードを使用して、キューブをクエリするビジネス ユーザーとクライアント アプリケーションの使用パターンに基づいて集計をデザインできます。</span><span class="sxs-lookup"><span data-stu-id="f93d4-110">After you use the Aggregation Design Wizard, you can use the Usage-Based Optimization Wizard to design aggregations based on the usage patterns of the business users and client applications that query the cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f93d4-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f93d4-111">In This Section</span></span>  
  
-   [<span data-ttu-id="f93d4-112">集計のデザインウィザード &#40;変更するパーティションの選択&#41;</span><span class="sxs-lookup"><span data-stu-id="f93d4-112">Select Partitions to Modify &#40;Aggregation Design Wizard&#41;</span></span>](select-partitions-to-modify-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="f93d4-113">集計の使用状況の確認 &#40;集計のデザインウィザード&#41;</span><span class="sxs-lookup"><span data-stu-id="f93d4-113">Review Aggregation Usage &#40;Aggregation Design Wizard&#41;</span></span>](review-aggregation-usage-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="f93d4-114">集計のデザインウィザード &#40;オブジェクト数の指定&#41;</span><span class="sxs-lookup"><span data-stu-id="f93d4-114">Specify Object Counts &#40;Aggregation Design Wizard&#41;</span></span>](specify-object-counts-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="f93d4-115">集計のデザインウィザード &#40;集計オプションの設定&#41;</span><span class="sxs-lookup"><span data-stu-id="f93d4-115">Set Aggregation Options &#40;Aggregation Design Wizard&#41;</span></span>](set-aggregation-options-aggregation-design-wizard.md)  
  
-   <span data-ttu-id="f93d4-116">[集計のデザインウィザードの [ウィザードの完了] &#40;&#41;](completing-the-wizard-aggregation-design-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="f93d4-116">[Completing the Wizard &#40;Aggregation Design Wizard&#41;](completing-the-wizard-aggregation-design-wizard.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93d4-117">参照</span><span class="sxs-lookup"><span data-stu-id="f93d4-117">See Also</span></span>  
 <span data-ttu-id="f93d4-118">[集計と集計のデザイン](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="f93d4-118">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="f93d4-119">[多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="f93d4-119">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="f93d4-120">[使用法に基づく最適化ウィザードの F1 ヘルプ](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f93d4-120">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="f93d4-121">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="f93d4-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
