---
title: '[ディメンションのキーと種類の指定] (ディメンションウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643526"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a><span data-ttu-id="31147-102">[ディメンションのキーおよび種類を指定] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="31147-102">Specify Dimension Key and Type (Dimension Wizard)</span></span>
  <span data-ttu-id="31147-103">**[ディメンションのキーおよび種類を指定]** ページを使用すると、ディメンションのキー属性を定義でき、ディメンションが SCD (緩やかに変化するディメンション) であるかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="31147-103">Use the **Specify Dimension Key and Type** page to define the key attribute of the dimension and to indicate whether the dimension is a slowly changing dimension (SCD).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31147-104">このページは、 **[構築方法の選択]** ページの **[データ ソースを使用せずにディメンションを構築する]** が選択され、 **[ディメンションの種類の選択]** ページの **[標準ディメンション]** が選択されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="31147-104">This page is displayed only if you selected **Build the dimension without using a data source** on the **Select Build Method** page and if you selected **Standard dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="31147-105">Options</span><span class="sxs-lookup"><span data-stu-id="31147-105">Options</span></span>  
 <span data-ttu-id="31147-106">**キー属性**</span><span class="sxs-lookup"><span data-stu-id="31147-106">**Key attribute**</span></span>  
 <span data-ttu-id="31147-107">ディメンションのキー属性となる属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="31147-107">Select the attribute that will be the key attribute for the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31147-108">ディメンションの属性が定義されていない場合、このオプションに使用できる値は **[キー属性を自動的に作成します]** のみとなります。</span><span class="sxs-lookup"><span data-stu-id="31147-108">If no attributes have been defined for the dimension, the only value available for this option is **Create key attribute automatically.**</span></span> <span data-ttu-id="31147-109">この値は、ディメンションの属性が定義されている場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="31147-109">This value is not available if any attributes are defined for the dimension.</span></span>  
  
 <span data-ttu-id="31147-110">**[変化するディメンション]**</span><span class="sxs-lookup"><span data-stu-id="31147-110">**This is a changing dimension**</span></span>  
 <span data-ttu-id="31147-111">ディメンションが緩やかに変化するディメンションであることを示します。</span><span class="sxs-lookup"><span data-stu-id="31147-111">Select to indicate that the dimension is a slowly changing dimension.</span></span> <span data-ttu-id="31147-112">このオプションを選択すると、時間経過と共にディメンションの階層内でメンバーが移動するのを追跡するために使用できる追加の列および属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="31147-112">Selecting this option will create additional columns and attributes that can be used to track the movement of members within the hierarchies of the dimension over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31147-113">参照</span><span class="sxs-lookup"><span data-stu-id="31147-113">See Also</span></span>  
 <span data-ttu-id="31147-114">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="31147-114">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="31147-115">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="31147-115">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="31147-116">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="31147-116">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
