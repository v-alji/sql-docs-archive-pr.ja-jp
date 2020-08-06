---
title: マイニング構造のプロパティを変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c1e63ad5fada770394e2fc283e0e592319281b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711162"
---
# <a name="change-the-properties-of-a-mining-structure"></a><span data-ttu-id="ed4e7-102">マイニング構造のプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="ed4e7-102">Change the Properties of a Mining Structure</span></span>
  <span data-ttu-id="ed4e7-103">マイニング構造には次の 2 種類のプロパティがあり、どちらも変更できます。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-103">There are two kinds of properties on a mining structure, both of which can be modified:</span></span>  
  
-   <span data-ttu-id="ed4e7-104">構造全体に影響するマイニング構造のプロパティ</span><span class="sxs-lookup"><span data-stu-id="ed4e7-104">Properties of the mining structure that affect the entire structure</span></span>  
  
-   <span data-ttu-id="ed4e7-105">構造の各列のプロパティ</span><span class="sxs-lookup"><span data-stu-id="ed4e7-105">Properties on individual columns in the structure</span></span>  
  
 <span data-ttu-id="ed4e7-106">他のプロパティの設定に依存するプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-106">Note that some properties are dependent on other property settings.</span></span> <span data-ttu-id="ed4e7-107">たとえば、ビン分割動作を制御するプロパティ (<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティや <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> プロパティ) は、その列のデータ型が `Discretized` に設定されていないと設定できません。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-107">For example, you cannot set properties that control binning behavior (such as <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> or <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) until you have set the data type of the column to `Discretized`.</span></span>  
  
 <span data-ttu-id="ed4e7-108">マイニング構造プロパティの詳細については、「 [マイニング構造列](mining-structure-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-108">For more information about mining structure properties, see [Mining Structure Columns](mining-structure-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a><span data-ttu-id="ed4e7-109">マイニング構造のプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="ed4e7-109">To change the properties of a mining structure</span></span>  
  
1.  <span data-ttu-id="ed4e7-110">データ マイニング デザイナーの **[マイニング構造]** タブで、マイニング構造またはマイニング構造内の列を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-110">On the **Mining Structure** tab in Data Mining Designer, right-click either the mining structure or a column in the mining structure, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="ed4e7-111">**[プロパティ]** ウィンドウが画面の右側に表示されます (まだ表示されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-111">The **Properties** window opens on the right side of the screen, if it was not already visible.</span></span>  
  
2.  <span data-ttu-id="ed4e7-112">**[プロパティ]** ウィンドウで、変更するプロパティに対応する値を選択し、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-112">In the **Properties** window, select the value that corresponds to the property that you want to change, and then enter the new value.</span></span>  
  
     <span data-ttu-id="ed4e7-113">新しい値は、デザイナーで別の要素を選択したときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="ed4e7-113">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4e7-114">参照</span><span class="sxs-lookup"><span data-stu-id="ed4e7-114">See Also</span></span>  
 [<span data-ttu-id="ed4e7-115">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="ed4e7-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
