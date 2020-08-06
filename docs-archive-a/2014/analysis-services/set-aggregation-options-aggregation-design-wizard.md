---
title: 集計オプションの設定 (集計のデザインウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.setaggregateoptions.f1
ms.assetid: 4672d686-10c0-43f8-a53e-a16dfa840c81
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1970e13ca6532ebbeb71e1401a75677bf7a89aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736912"
---
# <a name="set-aggregation-options-aggregation-design-wizard"></a><span data-ttu-id="e4c2a-102">[集計オプションの設定] (集計のデザイン ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e4c2a-102">Set Aggregation Options (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="e4c2a-103">**[集計オプションの設定]** ページを使用すると、集計のデザイン プロセスを開始したり、生成する集計のストレージ制限やパフォーマンス制限を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-103">Use the **Set Aggregation Options** page to start the aggregation design process, and specify storage or performance limits for the generated aggregations.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e4c2a-104">Options</span><span class="sxs-lookup"><span data-stu-id="e4c2a-104">Options</span></span>  
 <span data-ttu-id="e4c2a-105">**[ストレージの到達見積もり]**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-105">**Estimated storage reaches**</span></span>  
 <span data-ttu-id="e4c2a-106">集計の生成に使用できるメガバイト (MB) またはギガバイト (GB) の最大値を指定することにより、集計デザインを制限します。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-106">Limit the aggregation design by indicating the maximum number of megabytes (MB) or gigabytes (GB) that can be used to generate the aggregations.</span></span>  
  
 <span data-ttu-id="e4c2a-107">**[パフォーマンスの到達率]**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-107">**Performance gain reaches**</span></span>  
 <span data-ttu-id="e4c2a-108">集計のデザインによって実現できると推定される、最大のパフォーマンスの到達率を指定することで、集計のデザインを制限します。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-108">Limit the aggregation design by indicating the maximum percentage of estimated performance gain that the aggregation design can provided.</span></span>  
  
 <span data-ttu-id="e4c2a-109">**[[停止] をクリックする]**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-109">**I click Stop**</span></span>  
 <span data-ttu-id="e4c2a-110">デザイン プロセス中に **[停止]** をクリックすることにより、集計デザインを制限します。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-110">Limit the aggregation design by clicking **Stop** during the design process.</span></span>  
  
 <span data-ttu-id="e4c2a-111">**[集計をデザインしない (0%)]**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-111">**Do not design aggregations (0%)**</span></span>  
 <span data-ttu-id="e4c2a-112">集計のデザインに集計が含まれないように指定します。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-112">Specify that the aggregation design contains no aggregations.</span></span> <span data-ttu-id="e4c2a-113">このオプションを使用すると、パーティション、メジャー グループ、またはキューブに対する既存の集計デザインが消去されます。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-113">Use this option to clear an existing aggregation design for a partition, measure group, or cube.</span></span>  
  
 <span data-ttu-id="e4c2a-114">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-114">**Start**</span></span>  
 <span data-ttu-id="e4c2a-115">集計のデザイン プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-115">Starts the aggregation design process.</span></span>  
  
 <span data-ttu-id="e4c2a-116">**Stop**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-116">**Stop**</span></span>  
 <span data-ttu-id="e4c2a-117">集計のデザイン プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-117">Ends the aggregation design process.</span></span>  
  
 <span data-ttu-id="e4c2a-118">**リセット**</span><span class="sxs-lookup"><span data-stu-id="e4c2a-118">**Reset**</span></span>  
 <span data-ttu-id="e4c2a-119">このページにある集計のオプションをすべて既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="e4c2a-119">Resets all the aggregation options on this page to their default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c2a-120">参照</span><span class="sxs-lookup"><span data-stu-id="e4c2a-120">See Also</span></span>  
 <span data-ttu-id="e4c2a-121">[集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e4c2a-121">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="e4c2a-122">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="e4c2a-122">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
