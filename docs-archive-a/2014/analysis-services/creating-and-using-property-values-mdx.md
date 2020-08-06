---
title: プロパティ値の作成と使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- property values [MDX]
- queries [MDX], property values
- MDX [Analysis Services], property values
- Multidimensional Expressions [Analysis Services], property values
ms.assetid: 0cafb269-03c8-4183-b6e9-220f071e4ef2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67eadc6bc2f0bf6f318f20ad42a5cc9e7a5afa5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641908"
---
# <a name="creating-and-using-property-values-mdx"></a><span data-ttu-id="b44e4-102">プロパティ値の作成および使用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b44e4-102">Creating and Using Property Values (MDX)</span></span>
  <span data-ttu-id="b44e4-103">多次元式 (MDX) では、ディメンション、レベル、メンバー、およびセルの固有プロパティとユーザー定義プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b44e4-103">Multidimensional Expressions (MDX) supports intrinsic and user-defined properties for dimensions, levels, members, and cells.</span></span> <span data-ttu-id="b44e4-104">固有プロパティでは、一意な名前、キャプション、および書式やフォント サイズを、個別のセルに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="b44e4-104">The intrinsic properties provide unique names, captions, and even formatting and font sizes for individual cells.</span></span> <span data-ttu-id="b44e4-105">一方、ユーザー定義プロパティを使用すると、ほぼどんな属性でもメンバーに追加指定できます。</span><span class="sxs-lookup"><span data-stu-id="b44e4-105">User-defined properties, on the other hand, can provide almost any kind of additional attribute to members.</span></span>  
  
 <span data-ttu-id="b44e4-106">固有プロパティとユーザー定義プロパティは、以下のレベルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b44e4-106">Intrinsic and user-defined properties are available at the following levels:</span></span>  
  
 <span data-ttu-id="b44e4-107">**メンバーのプロパティ**</span><span class="sxs-lookup"><span data-stu-id="b44e4-107">**Member properties**</span></span>  
 <span data-ttu-id="b44e4-108">メンバー プロパティは、各組内の各メンバーに関する基本的な情報を対象とします。</span><span class="sxs-lookup"><span data-stu-id="b44e4-108">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="b44e4-109">基本的な情報には、メンバー名、親レベル、子の数などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b44e4-109">This basic information includes the member name, parent level, the number of children, and so on.</span></span>  
  
 <span data-ttu-id="b44e4-110">メンバー プロパティとその使用方法については、「[メンバー プロパティの使用 (MDX)](multidimensional-models/mdx/mdx-member-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b44e4-110">For information about member properties and how to use them, see [Using Member Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
 <span data-ttu-id="b44e4-111">**セル プロパティ**</span><span class="sxs-lookup"><span data-stu-id="b44e4-111">**Cell properties**</span></span>  
 <span data-ttu-id="b44e4-112">セル プロパティには、キューブなどの多次元データ ソース内のセルの内容や書式に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b44e4-112">Cell properties contain information about the content and format of cells in a multidimensional data source, such as a cube.</span></span>  
  
 <span data-ttu-id="b44e4-113">メンバー プロパティとその使用方法については、「[セル プロパティの使用 (MDX)](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b44e4-113">For more information about cell properties and how to use them, see [Using Cell Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44e4-114">参照</span><span class="sxs-lookup"><span data-stu-id="b44e4-114">See Also</span></span>  
 [<span data-ttu-id="b44e4-115">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b44e4-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
