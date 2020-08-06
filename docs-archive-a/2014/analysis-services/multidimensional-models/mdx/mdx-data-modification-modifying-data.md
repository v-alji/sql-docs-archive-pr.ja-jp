---
title: データの変更 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01df67471753922e3e7db39c56a9ed50aae900dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641887"
---
# <a name="modifying-data-mdx"></a><span data-ttu-id="1f30f-102">データの変更 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1f30f-102">Modifying Data (MDX)</span></span>
  <span data-ttu-id="1f30f-103">多次元式 (MDX) は、ディメンションやキューブのデータの取得や操作を行うためだけでなく、ディメンションやキューブのデータの更新、つまり *書き戻し* を行うためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f30f-103">Besides using Multidimensional Expressions (MDX) to retrieve and handle data from dimensions and cubes, you can use MDX to update or *writeback* dimension and cube data.</span></span> <span data-ttu-id="1f30f-104">これらの更新は、推測分析または "what-if" 分析の場合のように一時的なものであることも、データ分析に基づいて変更を加える必要がある場合のように永続的なものになることもあります。</span><span class="sxs-lookup"><span data-stu-id="1f30f-104">These updates can be temporary, as with speculative, or "what if", analysis, or permanent, as when changes must occur based upon data analysis.</span></span>  
  
 <span data-ttu-id="1f30f-105">データの更新は、ディメンション レベルまたはキューブ レベルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="1f30f-105">Updates to data can occur at the dimension or cube level:</span></span>  
  
 <span data-ttu-id="1f30f-106">**ディメンションの書き戻し**</span><span class="sxs-lookup"><span data-stu-id="1f30f-106">**Dimension writebacks**</span></span>  
 <span data-ttu-id="1f30f-107">書き込み可能なディメンションのデータを変更するには、 [ALTER CUBE ステートメント (MDX)](/sql/mdx/mdx-data-definition-alter-cube) を使用します。属性値の削除、作成、更新を反映するには、 [REFRESH CUBE ステートメント (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f30f-107">You use the [ALTER CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-alter-cube) statement to change a write-enabled dimension's data and the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to reflect the deletion, creation, and updating of attribute values.</span></span> <span data-ttu-id="1f30f-108">ALTER CUBE ステートメントを使用すると、階層内のサブツリー全体を削除したり、削除されたメンバーの子を昇格させるなど、複雑な操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="1f30f-108">You can also use the ALTER CUBE statement to perform complex operations, such as deleting a whole sub-tree in a hierarchy and promoting the children of a deleted member.</span></span>  
  
 <span data-ttu-id="1f30f-109">**キューブの書き戻し**</span><span class="sxs-lookup"><span data-stu-id="1f30f-109">**Cube writebacks**</span></span>  
 <span data-ttu-id="1f30f-110">書き込み可能なキューブに対する更新を実行するには、 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f30f-110">You use the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement to make updates to a write-enabled cube.</span></span> <span data-ttu-id="1f30f-111">UPDATE CUBE ステートメントを使用すると、特定の値で組を更新できます。</span><span class="sxs-lookup"><span data-stu-id="1f30f-111">The UPDATE CUBE statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="1f30f-112">サーバーにある更新されたデータをクライアント セッションのデータに適用するには、 [REFRESH CUBE ステートメント (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f30f-112">You use the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to refresh data in a client session with updated data from the server.</span></span>  
  
 <span data-ttu-id="1f30f-113">詳細については、「[キューブの書き戻しの使用 (MDX)](mdx-data-modification-using-cube-writebacks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f30f-113">For more information, see [Using Cube Writebacks &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f30f-114">参照</span><span class="sxs-lookup"><span data-stu-id="1f30f-114">See Also</span></span>  
 [<span data-ttu-id="1f30f-115">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1f30f-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
