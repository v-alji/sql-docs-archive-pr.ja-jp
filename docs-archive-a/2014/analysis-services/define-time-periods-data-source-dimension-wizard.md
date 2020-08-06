---
title: 時間間隔の定義 (データソース) (ディメンションウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.timeperioddefinition.f1
ms.assetid: a5e6b9ff-69fa-4896-a840-de2b3e063ca9
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2683aaece1a3f81537037531e3f78ce77817779
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712622"
---
# <a name="define-time-periods-data-source-dimension-wizard"></a><span data-ttu-id="e322e-102">[時間間隔の定義] (データ ソース) (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e322e-102">Define Time Periods (Data Source) (Dimension Wizard)</span></span>
  <span data-ttu-id="e322e-103">**[時間間隔の定義]** ページを使用すると、 **[ディメンションの種類の選択]** ページで指定されたテーブル内の列を使用して、時間ディメンション内の期間を表す属性を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e322e-103">Use the **Define Time Periods** page to define attributes representing time periods in the time dimension with columns in the table specified in the **Select the Dimension Type** page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e322e-104">このページは、 **[構築方法の選択]** ページで **[データ ソースを使用してディメンションを構築する]** を選択し、 **[ディメンションの種類の選択]** ページで **[時間ディメンション]** を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="e322e-104">This page will appear only if you have selected **Build the dimension using a data source** on the **Dimension Definition** page and **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e322e-105">Options</span><span class="sxs-lookup"><span data-stu-id="e322e-105">Options</span></span>  
 <span data-ttu-id="e322e-106">**[Time プロパティ名]**</span><span class="sxs-lookup"><span data-stu-id="e322e-106">**Time Property Name**</span></span>  
 <span data-ttu-id="e322e-107">時間ディメンション内の時間間隔を示すために使用される属性の種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="e322e-107">Displays the attribute types used to indicate time periods within time dimensions.</span></span> <span data-ttu-id="e322e-108">属性の種類の詳細については、[「Type 要素 (DimensionAttribute) (ASSL)」](https://docs.microsoft.com/bi-reference/assl/properties/type-element-dimensionattribute-assl) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e322e-108">For more information about attribute types, see [Type Element &#40;DimensionAttribute&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-dimensionattribute-assl).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e322e-109">`Date` 属性の種類は、DateTime データ型を持つ列に対してのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="e322e-109">The `Date` attribute type should be used only for columns with a DateTime data type.</span></span>  
  
 <span data-ttu-id="e322e-110">**[Time テーブル列]**</span><span class="sxs-lookup"><span data-stu-id="e322e-110">**Time Table Columns**</span></span>  
 <span data-ttu-id="e322e-111">対応する属性の種類の基準となる列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e322e-111">Lists the columns on which the corresponding attribute types will be based.</span></span>  
  
 <span data-ttu-id="e322e-112">列を変更するには、変更する列をクリックし、次に別の列を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="e322e-112">To change the column, click the column, and then select a different column from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e322e-113">参照</span><span class="sxs-lookup"><span data-stu-id="e322e-113">See Also</span></span>  
 <span data-ttu-id="e322e-114">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e322e-114">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="e322e-115">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e322e-115">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e322e-116">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="e322e-116">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
