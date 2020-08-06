---
title: '[パーティションのプロパティ] ダイアログボックス (SSMS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionpropertiesdialog.f1
ms.assetid: dfb5b7a0-7543-4e5e-8a30-4b734606e157
author: minewiskan
ms.author: owend
ms.openlocfilehash: b606a39ef99e5313b526ab0210448e295c5f04cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711073"
---
# <a name="partition-properties-dialog-box-ssms"></a><span data-ttu-id="436c8-102">[パーティションのプロパティ] (SSMS)</span><span class="sxs-lookup"><span data-stu-id="436c8-102">Partition Properties Dialog Box (SSMS)</span></span>
  <span data-ttu-id="436c8-103">SQL Server Management Studio の **[パーティションのプロパティ]** ダイアログ ボックスを使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのキューブに対してパーティションのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="436c8-103">Use the **Partition Properties** dialog box in SQL Server Management Studio to set the properties of a partition for a cube in an [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="436c8-104">**[パーティションのプロパティ]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー**でパーティションを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="436c8-104">To open the **Partition Properties** dialog box, in **Object Explorer**, right-click a partition, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="436c8-105">**[パーティションのプロパティ]** ダイアログ ボックスには、次のページがあります。</span><span class="sxs-lookup"><span data-stu-id="436c8-105">The **Partition Properties** dialog box contains the following pages:</span></span>  
  
## <a name="pages"></a><span data-ttu-id="436c8-106">ページ</span><span class="sxs-lookup"><span data-stu-id="436c8-106">Pages</span></span>  
  
|<span data-ttu-id="436c8-107">ページ</span><span class="sxs-lookup"><span data-stu-id="436c8-107">Page</span></span>|<span data-ttu-id="436c8-108">説明</span><span class="sxs-lookup"><span data-stu-id="436c8-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="436c8-109">**選択内容**</span><span class="sxs-lookup"><span data-stu-id="436c8-109">**Selection**</span></span>|<span data-ttu-id="436c8-110">**[選択項目]** ページを使用して、プロパティの表示や変更を行うメジャー グループのパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="436c8-110">Use the **Selection** page to select the partition in the measure group for which you want to display or modify properties.</span></span> <span data-ttu-id="436c8-111">このページの詳細については、「[[選択項目] &#40;[パーティションのプロパティ] ダイアログ ボックス&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="436c8-111">For more information about this page, see [Selection &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="436c8-112">**全般**</span><span class="sxs-lookup"><span data-stu-id="436c8-112">**General**</span></span>|<span data-ttu-id="436c8-113">**[全般]** ページを使用して、 **[選択項目]** ページで選択したパーティションの全般プロパティの表示と変更を行います。</span><span class="sxs-lookup"><span data-stu-id="436c8-113">Use the **General** page to display and modify the general properties of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="436c8-114">このページの詳細については、「[[全般] &#40;[パーティションのプロパティ] ダイアログ ボックス&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="436c8-114">For more information about this page, see [General &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="436c8-115">**プロアクティブキャッシュ**</span><span class="sxs-lookup"><span data-stu-id="436c8-115">**Proactive Caching**</span></span>|<span data-ttu-id="436c8-116">**[プロアクティブ キャッシュ]** ページを使用して、 **[選択項目]** ページで選択したパーティションのストレージとプロアクティブ キャッシュ設定の表示と変更を行います。</span><span class="sxs-lookup"><span data-stu-id="436c8-116">Use the **Proactive Caching** page to display and modify the storage and proactive caching settings of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="436c8-117">このページの詳細については、「[[プロアクティブ キャッシュ] &#40;[パーティションのプロパティ] ダイアログ ボックス&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="436c8-117">For more information about this page, see [Proactive Caching &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="436c8-118">**[エラーの構成]**</span><span class="sxs-lookup"><span data-stu-id="436c8-118">**Error Configuration**</span></span>|<span data-ttu-id="436c8-119">**[エラーの構成]** ページを使用して、 **[選択項目]** ページで選択したパーティションを処理するためのエラー構成設定の表示と変更を行います。</span><span class="sxs-lookup"><span data-stu-id="436c8-119">Use the **Error Configuration** page to display and modify the error configuration settings for processing the partition selected in the **Selection** page.</span></span> <span data-ttu-id="436c8-120">このページの詳細については、「[キューブ、パーティション、およびディメンションに関する処理のエラー構成 &#40;SSAS - 多次元&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="436c8-120">For more information about this page, see [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="436c8-121">参照</span><span class="sxs-lookup"><span data-stu-id="436c8-121">See Also</span></span>  
 <span data-ttu-id="436c8-122">[パーティション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="436c8-122">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="436c8-123">[リモートパーティション](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="436c8-123">[Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span></span>  
 [<span data-ttu-id="436c8-124">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="436c8-124">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
