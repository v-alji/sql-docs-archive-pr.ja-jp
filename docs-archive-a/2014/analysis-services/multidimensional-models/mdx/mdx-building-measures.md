---
title: MDX でメジャーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac49d37f11584bfbc5d372241056da39e7dd8c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639703"
---
# <a name="building-measures-in-mdx"></a><span data-ttu-id="4b8e1-102">MDX 内でのメジャーの作成</span><span class="sxs-lookup"><span data-stu-id="4b8e1-102">Building Measures in MDX</span></span>
  <span data-ttu-id="4b8e1-103">多次元式 (MDX) では、メジャーは、テーブル モデルで値を返す式を計算することで解決される名前付き DAX 式です。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-103">In Multidimensional Expressions (MDX), a measure is a named DAX expression that is resolved by calculating the expression to return a value in a Tabular Model.</span></span> <span data-ttu-id="4b8e1-104">これは一見なにげない定義ですが、非常に広範囲に影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="4b8e1-105">MDX クエリでメジャーを作成して使用する機能によって、テーブル データの操作能力が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-105">The ability to construct and use measures in an MDX query provides a great deal of manipulation capability for tabular data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4b8e1-106">メジャーは、テーブル モデルでのみ定義できます。データベースが多次元モードに設定されている場合、メジャーを作成するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-106">Measures can only be defined in tabular models; if your database is set in multidimensional mode, creating a measure will generate an error</span></span>  
  
 <span data-ttu-id="4b8e1-107">MDX クエリの一部として定義されるメジャーを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-107">To create a measure that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="4b8e1-108">そのメジャーは、MDX の SELECT ステートメントの中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-108">You can then use the measure within an MDX SELECT statement.</span></span> <span data-ttu-id="4b8e1-109">この方法では、WITH キーワードを使用して作成した計算されるメンバーを、SELECT ステートメントを修正せずに変更できます。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-109">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span> <span data-ttu-id="4b8e1-110">ただし、MDX では、DAX 式とは異なる方法でメジャーを参照します。メジャーを参照するには、[Measures] ディメンションのメンバーとして指定します。次の MDX の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-110">However, in MDX you reference the measure in a different way than when in DAX expressions; to reference the measure you name it as a member of the [Measures] dimension, see the following MDX example:</span></span>  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 <span data-ttu-id="4b8e1-111">これを実行すると、次のデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="4b8e1-111">It will return the following data when executed:</span></span>  
  
||<span data-ttu-id="4b8e1-112">Total Sales Amount</span><span class="sxs-lookup"><span data-stu-id="4b8e1-112">Total Sales Amount</span></span>||  
|-|------------------------|-|  
|<span data-ttu-id="4b8e1-113">2001</span><span class="sxs-lookup"><span data-stu-id="4b8e1-113">2001</span></span>|<span data-ttu-id="4b8e1-114">11331808.96</span><span class="sxs-lookup"><span data-stu-id="4b8e1-114">11331808.96</span></span>||  
|<span data-ttu-id="4b8e1-115">2002</span><span class="sxs-lookup"><span data-stu-id="4b8e1-115">2002</span></span>|<span data-ttu-id="4b8e1-116">30674773.18</span><span class="sxs-lookup"><span data-stu-id="4b8e1-116">30674773.18</span></span>||  
|<span data-ttu-id="4b8e1-117">2003</span><span class="sxs-lookup"><span data-stu-id="4b8e1-117">2003</span></span>|<span data-ttu-id="4b8e1-118">41993729.72</span><span class="sxs-lookup"><span data-stu-id="4b8e1-118">41993729.72</span></span>||  
|<span data-ttu-id="4b8e1-119">2004</span><span class="sxs-lookup"><span data-stu-id="4b8e1-119">2004</span></span>|<span data-ttu-id="4b8e1-120">25808962.34</span><span class="sxs-lookup"><span data-stu-id="4b8e1-120">25808962.34</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="4b8e1-121">参照</span><span class="sxs-lookup"><span data-stu-id="4b8e1-121">See Also</span></span>  
 <span data-ttu-id="4b8e1-122">[CREATE MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="4b8e1-122">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="4b8e1-123">[Mdx 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="4b8e1-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="4b8e1-124">SELECT ステートメント &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b8e1-124">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
