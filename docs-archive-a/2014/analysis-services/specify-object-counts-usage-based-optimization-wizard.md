---
title: オブジェクト数の指定 (使用法に基づく最適化ウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 862be19f12308def815a280dba04f42f0cbe6878
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643513"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a><span data-ttu-id="3ff23-102">[オブジェクト カウントの指定] (使用法に基づく最適化ウィザード)</span><span class="sxs-lookup"><span data-stu-id="3ff23-102">Specify Object Counts (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="3ff23-103">**[オブジェクト カウントの指定]** ページを使用すると、キューブ内のオブジェクト数を自動的に計算したり、推定カウントを手動で入力したりできます。</span><span class="sxs-lookup"><span data-stu-id="3ff23-103">Use the **Specify Object Counts** page to automatically calculate the count of objects in the cube or to manually enter estimated counts.</span></span> <span data-ttu-id="3ff23-104">使用法に基づく最適化ウィザードでは、オブジェクト カウントを使用してストレージ要件を推定します。</span><span class="sxs-lookup"><span data-stu-id="3ff23-104">The Usage-Based Optimization Wizard uses the object counts to estimate storage requirements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ff23-105">Options</span><span class="sxs-lookup"><span data-stu-id="3ff23-105">Options</span></span>  
 <span data-ttu-id="3ff23-106">**[キューブ オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="3ff23-106">**Cube Objects**</span></span>  
 <span data-ttu-id="3ff23-107">キューブ内のディメンションおよび属性を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ff23-107">Displays the dimensions and attributes in the cube.</span></span> <span data-ttu-id="3ff23-108">`AggregationUsage`ウィザードの [**集計使用法の確認**] ページでプロパティが [なし] に設定されていない属性のみが表示されます。カウントを指定する必要がある属性はこれらの属性だけであるためです。</span><span class="sxs-lookup"><span data-stu-id="3ff23-108">Only the attributes that do not have their `AggregationUsage` property set to None in the **Review Aggregation Usage** page of the wizard are shown because those are the only attributes that need counts specified.</span></span>  
  
 <span data-ttu-id="3ff23-109">**[推定カウント]**</span><span class="sxs-lookup"><span data-stu-id="3ff23-109">**Estimated count**</span></span>  
 <span data-ttu-id="3ff23-110">メジャー グループ内の推定行数およびデータベース ディメンション内の属性の推定メンバー数を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ff23-110">Displays the estimated number of rows in the measure group and the estimated attribute member counts in the database dimensions.</span></span> <span data-ttu-id="3ff23-111">推定カウントとして使用する値を入力することも、推定カウントの値を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="3ff23-111">You can type a value to use as the estimated count or you can calculate the estimated count values.</span></span> <span data-ttu-id="3ff23-112">カウントの値を計算するには、フィールドに「 0 」を入力して **[カウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ff23-112">To calculate the count values, type 0 in the field and then click **Count**.</span></span> <span data-ttu-id="3ff23-113">既にカウントが表示されているフィールドは更新されません。</span><span class="sxs-lookup"><span data-stu-id="3ff23-113">Fields that already display a count are not updated.</span></span>  
  
 <span data-ttu-id="3ff23-114">**パーティション数**</span><span class="sxs-lookup"><span data-stu-id="3ff23-114">**Partition count**</span></span>  
 <span data-ttu-id="3ff23-115">(省略可) メジャー グループ内の推定行数およびディメンション内の属性の推定メンバー数を竜力します。</span><span class="sxs-lookup"><span data-stu-id="3ff23-115">(Optional) Type the estimated number of rows in the measure group and the estimated attribute member counts in the partitions.</span></span>  
  
 <span data-ttu-id="3ff23-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="3ff23-116">**Count**</span></span>  
 <span data-ttu-id="3ff23-117">空のすべてのフィールドに対する **[推定カウント]** 列の値を計算し、再作成します。</span><span class="sxs-lookup"><span data-stu-id="3ff23-117">Calculates and repopulates the values in the **Estimated count** column for all empty fields.</span></span> <span data-ttu-id="3ff23-118">既にカウントが表示されているフィールドは更新されません。</span><span class="sxs-lookup"><span data-stu-id="3ff23-118">Fields that already display a count are not updated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff23-119">参照</span><span class="sxs-lookup"><span data-stu-id="3ff23-119">See Also</span></span>  
 <span data-ttu-id="3ff23-120">[集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3ff23-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="3ff23-121">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="3ff23-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
