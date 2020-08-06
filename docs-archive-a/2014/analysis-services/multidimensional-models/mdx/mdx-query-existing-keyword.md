---
title: EXISTING キーワード (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632143"
---
# <a name="existing-keyword-mdx"></a><span data-ttu-id="022e1-102">EXISTING キーワード (MDX)</span><span class="sxs-lookup"><span data-stu-id="022e1-102">EXISTING Keyword (MDX)</span></span>
  <span data-ttu-id="022e1-103">指定されたセットを現在のコンテキストで評価するように設定します。</span><span class="sxs-lookup"><span data-stu-id="022e1-103">Forces a specified set to be evaluated within the current context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="022e1-104">Syntax</span></span>  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="022e1-105">引数</span><span class="sxs-lookup"><span data-stu-id="022e1-105">Arguments</span></span>  
 <span data-ttu-id="022e1-106">*Set_Expression*</span><span class="sxs-lookup"><span data-stu-id="022e1-106">*Set_Expression*</span></span>  
 <span data-ttu-id="022e1-107">有効な多次元式 (MDX) セット式です。</span><span class="sxs-lookup"><span data-stu-id="022e1-107">A valid Multidimensional Expressions (MDX) set expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="022e1-108">解説</span><span class="sxs-lookup"><span data-stu-id="022e1-108">Remarks</span></span>  
 <span data-ttu-id="022e1-109">既定では、セットの評価は、そのセットのメンバーを含むキューブのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="022e1-109">By default, sets are evaluated within the context of the cube that contains the members of the set.</span></span> <span data-ttu-id="022e1-110">`Existing` キーワードを指定すると、指定されているセットの評価が現在のコンテキストで行われます。</span><span class="sxs-lookup"><span data-stu-id="022e1-110">The `Existing` keyword forces a specified set to be evaluated within the current context instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="022e1-111">例</span><span class="sxs-lookup"><span data-stu-id="022e1-111">Example</span></span>  
 <span data-ttu-id="022e1-112">次の例では、`Aggregate`  関数を使用して評価された、ユーザー選択の State-Province メンバー値に基づいて、1 つ前の期よりも売上が減少した再販業者の数を返します。</span><span class="sxs-lookup"><span data-stu-id="022e1-112">The following example returns the count of the resellers whose sales have declined over the previous time period, based on user-selected State-Province member values evaluated using the `Aggregate` function.</span></span> <span data-ttu-id="022e1-113">Product ディメンションに含まれる製品カテゴリに関して減少した売上の値を返すために、 [Hierarchize (MDX)](/sql/mdx/hierarchize-mdx) 関数および [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) 関数を使用しています。</span><span class="sxs-lookup"><span data-stu-id="022e1-113">The [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) and [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) functions are used to return values for declining sales for product categories in the Product dimension.</span></span> <span data-ttu-id="022e1-114">キーワードを使用 `Existing` すると、関数内のセットが `Filter` 現在のコンテキストで評価されるようになります。つまり、ワシントンおよびオレゴン州の属性階層のオレゴンメンバーに対して評価されます。</span><span class="sxs-lookup"><span data-stu-id="022e1-114">The `Existing` keyword forces the set in the `Filter` function to be evaluated in the current context - that is, for the Washington and Oregon members of the State-Province attribute hierarchy.</span></span>  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="022e1-115">参照</span><span class="sxs-lookup"><span data-stu-id="022e1-115">See Also</span></span>  
 <span data-ttu-id="022e1-116">[MDX&#41;&#41; &#40;設定 &#40;数](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-116">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="022e1-117">[MDX&#41;&#40;の Add演算メンバー](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="022e1-118">[MDX&#41;の集計 &#40;](/sql/mdx/aggregate-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-118">[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) </span></span>  
 <span data-ttu-id="022e1-119">[MDX&#41;のフィルター処理 &#40;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-119">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="022e1-120">[MDX&#41;&#40;プロパティ](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-120">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="022e1-121">[MDX&#41;&#40;ドリルダウンレベル](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="022e1-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="022e1-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 [<span data-ttu-id="022e1-123">MDX 関数リファレンス &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="022e1-123">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
