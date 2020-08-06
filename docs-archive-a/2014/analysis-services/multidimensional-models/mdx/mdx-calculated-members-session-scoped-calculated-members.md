---
title: セッションスコープの計算されるメンバーの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8fe7a9f137d8b74eaa5bad104dbfdb471dd14588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643579"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a><span data-ttu-id="7faf3-102">セッション スコープの計算されるメンバーの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="7faf3-102">Creating Session-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="7faf3-103">多次元式 (MDX) セッション全体で使用できる計算されるメンバーを作成するには、 [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7faf3-103">To create a calculated member that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span> <span data-ttu-id="7faf3-104">CREATE MEMBER ステートメントを使用して作成された計算されるメンバーは、MDX セッションが閉じるまで削除されません。</span><span class="sxs-lookup"><span data-stu-id="7faf3-104">A calculated member that is created by using the CREATE MEMBER statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="7faf3-105">このトピックで説明するように、CREATE MEMBER ステートメントの構文は非常に単純で使いやすいものです。</span><span class="sxs-lookup"><span data-stu-id="7faf3-105">As discussed in this topic, the syntax of the CREATE MEMBER statement is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7faf3-106">計算されるメンバーの詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7faf3-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="create-member-syntax"></a><span data-ttu-id="7faf3-107">CREATE MEMBER の構文</span><span class="sxs-lookup"><span data-stu-id="7faf3-107">CREATE MEMBER Syntax</span></span>  
 <span data-ttu-id="7faf3-108">MDX ステートメントに CREATE MEMBER ステートメントを追加するための構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7faf3-108">Use the following syntax to add the CREATE MEMBER statement to the MDX statement:</span></span>  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 <span data-ttu-id="7faf3-109">CREATE MEMBER ステートメントの構文で使用する `fully-qualified-member-name` の値は、計算されるメンバーの完全修飾名です。</span><span class="sxs-lookup"><span data-stu-id="7faf3-109">In the syntax for the CREATE MEMBER statement, the `fully-qualified-member-name` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="7faf3-110">完全修飾名には、計算されるメンバーを関連付けるディメンションまたはレベルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7faf3-110">The fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="7faf3-111">`expression` の値は、その式の値が評価された後の計算されるメンバーの値を返します。</span><span class="sxs-lookup"><span data-stu-id="7faf3-111">The `expression` value returns the value of the calculated member after the expression value has been evaluated,.</span></span>  
  
## <a name="create-member-example"></a><span data-ttu-id="7faf3-112">CREATE MEMBER の例</span><span class="sxs-lookup"><span data-stu-id="7faf3-112">CREATE MEMBER Example</span></span>  
 <span data-ttu-id="7faf3-113">以下の例では、CREATE MEMBER ステートメントを使用して、計算されるメンバー `LastFourStores` を作成しています。</span><span class="sxs-lookup"><span data-stu-id="7faf3-113">The following example uses the CREATE MEMBER statement to create the `LastFourStores` calculated member.</span></span> <span data-ttu-id="7faf3-114">この計算されるメンバーは、販売した単位の合計を最後の 4 つのストアに関して返します。このメンバーは、このキューブのセッション全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="7faf3-114">This calculated member returns the sum of units sold for the last four stores, and will be available throughout the whole session of the cube.</span></span>  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a><span data-ttu-id="7faf3-115">参照</span><span class="sxs-lookup"><span data-stu-id="7faf3-115">See Also</span></span>  
 [<span data-ttu-id="7faf3-116">クエリ スコープの計算されるメンバーの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="7faf3-116">Creating Query-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
