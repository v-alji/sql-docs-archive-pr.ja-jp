---
title: MDX での計算されるメンバーの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30dc6562ec394065cf2f177608d4e5679cbd7df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639697"
---
# <a name="building-calculated-members-in-mdx-mdx"></a><span data-ttu-id="f69e6-102">MDX での計算されるメンバーの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="f69e6-102">Building Calculated Members in MDX (MDX)</span></span>
  <span data-ttu-id="f69e6-103">多次元式 (MDX) では、値を返す MDX 式の計算によって解決されるメンバーのことを、計算されるメンバーといいます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-103">In Multidimensional Expressions (MDX), a calculated member is a member that is resolved by calculating an MDX expression to return a value.</span></span> <span data-ttu-id="f69e6-104">これは一見なにげない定義ですが、非常に広範囲に影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="f69e6-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="f69e6-105">MDX クエリで計算されるメンバーを作成して使用する機能によって、多次元データの操作能力が大幅に向上するからです。</span><span class="sxs-lookup"><span data-stu-id="f69e6-105">The ability to construct and use calculated members in an MDX query provides a great deal of manipulation capability for multidimensional data.</span></span>  
  
 <span data-ttu-id="f69e6-106">計算されるメンバーは、階層内のどこにでも作成できます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-106">You can create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="f69e6-107">また、キューブ内の既存のメンバーだけでなく、同じ MDX 式で定義された他の計算されるメンバーにも依存するように、計算されるメンバーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-107">You can also create calculated members that depend not only on existing members in a cube, but also on other calculated members defined in the same MDX expression.</span></span>  
  
 <span data-ttu-id="f69e6-108">計算されるメンバーの定義では、以下のいずれかのコンテキストを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-108">You can define a calculated member to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="f69e6-109">**クエリ スコープ** MDX クエリの一部として定義する、計算されるメンバーを作成する場合 (スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f69e6-109">**Query-scoped** To create a calculated member that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="f69e6-110">その計算されるメンバーは、MDX の SELECT ステートメントの中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-110">You can then use the calculated member within an MDX SELECT statement.</span></span> <span data-ttu-id="f69e6-111">この方法では、WITH キーワードを使用して作成した計算されるメンバーを、SELECT ステートメントを修正せずに変更できます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-111">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="f69e6-112">WITH キーワードを使用して計算されるメンバーを作成する方法の詳細については、「[クエリ スコープの計算されるメンバーの作成 &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f69e6-112">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md).</span></span>  
  
-   <span data-ttu-id="f69e6-113">**セッション スコープ** クエリのコンテキストよりも広いスコープを設定して計算されるメンバーを作成する場合 (スコープを MDX セッションの有効期間全体とする場合) は、CREATE MEMBER ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f69e6-113">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE MEMBER statement.</span></span> <span data-ttu-id="f69e6-114">CREATE MEMBER ステートメントで定義した計算されるメンバーは、そのセッションのすべての MDX クエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-114">A calculated member defined by using the CREATE MEMBER statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="f69e6-115">CREATE MEMBER ステートメントを使用する方法は、たとえば、さまざまなクエリで同じセットを使い回すクライアント アプリケーションで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f69e6-115">The CREATE MEMBER statement makes sense, for example, in a client application that consistently reuses the same set in a variety of queries.</span></span>  
  
     <span data-ttu-id="f69e6-116">CREATE MEMBER ステートメントを使用してセッションでの計算されるメンバーを作成する方法の詳細については、「[セッション スコープの計算されるメンバーの作成 &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f69e6-116">For more information about how to use the CREATE MEMBER statement to create calculated members in a session, see [Creating Session-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69e6-117">参照</span><span class="sxs-lookup"><span data-stu-id="f69e6-117">See Also</span></span>  
 <span data-ttu-id="f69e6-118">[CREATE MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="f69e6-118">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="f69e6-119">[Mdx 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="f69e6-119">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="f69e6-120">SELECT ステートメント &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f69e6-120">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
