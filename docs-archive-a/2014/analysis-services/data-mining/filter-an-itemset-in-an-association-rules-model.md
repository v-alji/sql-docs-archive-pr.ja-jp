---
title: アソシエーションルールモデルのアイテムセットをフィルター処理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f841280a6dd39a5f824f2e6a10975b0f80ed0761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632177"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a><span data-ttu-id="95fe4-102">アソシエーション ルール モデルのアイテムセットのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="95fe4-102">Filter an Itemset in an Association Rules Model</span></span>
  <span data-ttu-id="95fe4-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、 **アソシエーション ルール ビューアーの** [アイテムセット] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブに表示されるアイテムセットをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="95fe4-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can filter the itemsets that are displayed in the **Itemsets** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer.</span></span>  
  
### <a name="to-filter-an-itemset"></a><span data-ttu-id="95fe4-104">アイテムセットをフィルター選択するには</span><span class="sxs-lookup"><span data-stu-id="95fe4-104">To filter an itemset</span></span>  
  
1.  <span data-ttu-id="95fe4-105">**のデータ マイニング デザイナーの** [マイニング モデル ビューアー] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、 **アソシエーション ルール ビューアー** の **[アイテムセット]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="95fe4-105">On the **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Itemsets** tab of the **Association Rules Viewer**.</span></span>  
  
2.  <span data-ttu-id="95fe4-106">**[アイテムセットのフィルター]** ボックスにルールの条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="95fe4-106">Enter a rule condition in the **Filter itemset** box.</span></span> <span data-ttu-id="95fe4-107">たとえば、「Touring-1000 = existing」などの条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="95fe4-107">For example, a rule condition might be "Touring-1000 = existing"</span></span>  
  
3.  <span data-ttu-id="95fe4-108">**Enter**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95fe4-108">Click **Enter**.</span></span>  
  
 <span data-ttu-id="95fe4-109">これでアイテムセットにフィルターが適用され、選択されたアイテムを含んだアイテムセットのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95fe4-109">The itemsets are now filtered to display only those itemsets that contain the selected items.</span></span> <span data-ttu-id="95fe4-110">このボックスでは、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="95fe4-110">The box is not case-sensitive.</span></span> <span data-ttu-id="95fe4-111">フィルターはメモリに保存されるので、一覧から古いフィルターを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="95fe4-111">Filters are stored in memory so that you can select an old filter from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fe4-112">参照</span><span class="sxs-lookup"><span data-stu-id="95fe4-112">See Also</span></span>  
 [<span data-ttu-id="95fe4-113">マイニング モデル ビューアーのタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="95fe4-113">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
