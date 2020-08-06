---
title: MDX での名前付きセットの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91296f8c5d47afb15c67f0b60435c7f961734573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714653"
---
# <a name="building-named-sets-in-mdx-mdx"></a><span data-ttu-id="6afbb-102">MDX での名前付きセットの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="6afbb-102">Building Named Sets in MDX (MDX)</span></span>
  <span data-ttu-id="6afbb-103">セット式は、長く複雑な宣言になることがあり、そのような場合は読みにくく、理解するのが難しい式になります。</span><span class="sxs-lookup"><span data-stu-id="6afbb-103">A set expression can be a lengthy and complex declaration, and therefore be difficult to follow or understand.</span></span> <span data-ttu-id="6afbb-104">また、同じセット式を頻繁に使用する場合に、その同じセットを繰り返し定義しなければならないのは面倒です。</span><span class="sxs-lookup"><span data-stu-id="6afbb-104">Or, a set expression may be used so frequently that repeatedly defining the set becomes burdensome.</span></span> <span data-ttu-id="6afbb-105">長く複雑な式や頻繁に使用する式の取り扱いを簡略化するために、多次元式 (MDX) では、そのような式を *名前付きセット*として定義できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="6afbb-105">To help make working with a lengthy, complex or commonly used expression easier, Multidimensional Expressions (MDX) lets you such an expression as a *named set*.</span></span>  
  
 <span data-ttu-id="6afbb-106">基本的に、名前付きセットとは、別名を割り当てたセット式です。</span><span class="sxs-lookup"><span data-stu-id="6afbb-106">Basically, a named set is a set expression to which an alias has been assigned.</span></span> <span data-ttu-id="6afbb-107">名前付きセットには、通常 1 つのセットに組み込めるメンバーや関数を任意に組み込めます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-107">A named set can incorporate any members or functions that can ordinarily be incorporated into a set.</span></span> <span data-ttu-id="6afbb-108">MDX では、名前付きセットの別名をセット式として取り扱うので、セット式を使用できる場所であればどこででもその別名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-108">Because MDX treats the named set alias as a set expression, you can use that alias anywhere a set expression is accepted.</span></span>  
  
 <span data-ttu-id="6afbb-109">名前付きセットの定義では、以下のいずれかのコンテキストを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-109">You can define a named set to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="6afbb-110">**クエリ スコープ** MDX クエリの一部として定義される名前付きセットを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="6afbb-110">**Query-scoped** To create a named set that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="6afbb-111">その名前付きセットは、MDX の SELECT ステートメントの中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-111">You can then use the named set within an MDX SELECT statement.</span></span> <span data-ttu-id="6afbb-112">この方法では、WITH キーワードを使用して作成した名前付きセットを、SELECT ステートメントを修正せずに変更できます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-112">Using this approach, the named set created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="6afbb-113">WITH キーワードを使用して名前付きセットを作成する方法の詳細については、「[クエリ スコープの名前付きセットの作成 (MDX)](mdx-named-sets-creating-query-scoped-named-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6afbb-113">For more information about how to use the WITH keyword to create named sets, see [Creating Query-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md).</span></span>  
  
-   <span data-ttu-id="6afbb-114">**セッション スコープ** クエリのコンテキストよりも広いスコープを設定して名前付きセットを作成する場合 (つまり、スコープを MDX セッションの有効期間全体とする場合) は、CREATE SET ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6afbb-114">**Session-scoped** To create a named set whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE SET statement.</span></span> <span data-ttu-id="6afbb-115">CREATE SET ステートメントで定義した名前付きセットは、そのセッションのすべての MDX クエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-115">A named set defined by using the CREATE SET statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="6afbb-116">CREATE SET ステートメントを使用する方法は、たとえば、さまざまなクエリで 1 つのセットを使い回すクライアント アプリケーションで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6afbb-116">The CREATE SET statement makes sense, for example, in a client application that consistently reuses a set in a variety of queries.</span></span>  
  
     <span data-ttu-id="6afbb-117">CREATE SET ステートメントを使用してセッションでの名前付きセットを作成する方法の詳細については、「[セッション スコープの名前付きセットの作成 (MDX)](mdx-named-sets-creating-session-scoped-named-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6afbb-117">For more information about how to use the CREATE SET statement to create named sets in a session, see [Creating Session-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afbb-118">参照</span><span class="sxs-lookup"><span data-stu-id="6afbb-118">See Also</span></span>  
 <span data-ttu-id="6afbb-119">[SELECT ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="6afbb-119">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 <span data-ttu-id="6afbb-120">[CREATE SET ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span><span class="sxs-lookup"><span data-stu-id="6afbb-120">[CREATE SET Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span></span>  
 [<span data-ttu-id="6afbb-121">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6afbb-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
