---
title: MDX でのサブキューブの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
author: minewiskan
ms.author: owend
ms.openlocfilehash: 653b4d30aa86f52179c7b13619ac4347aa65c339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642378"
---
# <a name="building-subcubes-in-mdx-mdx"></a><span data-ttu-id="ccf24-102">MDX でのサブキューブの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ccf24-102">Building Subcubes in MDX (MDX)</span></span>
  <span data-ttu-id="ccf24-103">サブキューブは、基になるデータにフィルターを適用したビューを表す、キューブのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="ccf24-103">A subcube is a subset of a cube on representing a filtered view of the underlying data.</span></span> <span data-ttu-id="ccf24-104">キューブをサブキューブに限定することによって、クエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-104">By limiting the cube to a subcube, you can improve query performance.</span></span>  
  
 <span data-ttu-id="ccf24-105">サブキューブを定義するには、このトピックで説明されている [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="ccf24-105">To define a subcube, you use the [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) statement, as described in this topic.</span></span>  
  
## <a name="create-subcube-syntax"></a><span data-ttu-id="ccf24-106">CREATE SUBCUBE の構文</span><span class="sxs-lookup"><span data-stu-id="ccf24-106">CREATE SUBCUBE Syntax</span></span>  
 <span data-ttu-id="ccf24-107">サブキューブを作成するための構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ccf24-107">Use the following syntax to create a subcube:</span></span>  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 <span data-ttu-id="ccf24-108">CREATE SUBCUBE の構文は非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="ccf24-108">The CREATE SUBCUBE syntax is fairly simple.</span></span> <span data-ttu-id="ccf24-109">*Subcube_Identifier* パラメーターは、サブキューブの基になるキューブを識別します。</span><span class="sxs-lookup"><span data-stu-id="ccf24-109">The *Subcube_Identifier* parameter identifies the cube on which the subcube will be based.</span></span> <span data-ttu-id="ccf24-110">*Subcube_Expression* パラメーターでは、サブキューブにするキューブの部分を選択します。</span><span class="sxs-lookup"><span data-stu-id="ccf24-110">The *Subcube_Expression* parameter selects the part of the cube that will become the subcube</span></span>  
  
 <span data-ttu-id="ccf24-111">サブキューブを作成すると、そのサブキューブは、セッションが閉じるまで、あるいは [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) ステートメントを実行するまですべての MDX クエリのコンテキストになります。</span><span class="sxs-lookup"><span data-stu-id="ccf24-111">After you create a subcube, that subcube becomes the context for all MDX queries until either the session closes or you run the [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) statement.</span></span>  
  
### <a name="what-a-subcube-contains"></a><span data-ttu-id="ccf24-112">サブキューブの内容</span><span class="sxs-lookup"><span data-stu-id="ccf24-112">What a Subcube Contains</span></span>  
 <span data-ttu-id="ccf24-113">CREATE SUBCUBE ステートメントの使用法は単純ですが、サブキューブに含まれるすべてのメンバーがステートメント自体で明示的に指定されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ccf24-113">Although the CREATE SUBCUBE statement is fairly simple to use, the statement itself does not explicitly show all the members that become part of a subcube.</span></span> <span data-ttu-id="ccf24-114">サブキューブを定義する場合には、以下の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-114">In defining a subcube, the following rules apply:</span></span>  
  
-   <span data-ttu-id="ccf24-115">ある階層の `(All)` メンバーを含める場合、その階層のすべてのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-115">If you include the `(All)` member of a hierarchy, you include every member of that hierarchy.</span></span>  
  
-   <span data-ttu-id="ccf24-116">任意のメンバーを含める場合、そのメンバーの先祖と子孫も含まれます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-116">If you include any member, you include that member's ascendants and descendants.</span></span>  
  
-   <span data-ttu-id="ccf24-117">あるレベルの各メンバーを含める場合、階層のすべてのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-117">If you include every member from a level, you include all members from the hierarchy.</span></span> <span data-ttu-id="ccf24-118">他の階層のメンバーは、そのレベルのメンバーと共に存在していない場合 (たとえば、顧客を含まない都市のような不均衡階層など)、除外されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-118">Members from other hierarchies will be excluded if those members do not exist with members from the level (for example, an unbalanced hierarchy such as a city that does not contain customers).</span></span>  
  
-   <span data-ttu-id="ccf24-119">サブキューブには、キューブの各 `(All)` メンバーが常に含まれます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-119">A subcube will always contain every `(All)` member from the cube.</span></span>  
  
 <span data-ttu-id="ccf24-120">さらに、サブキューブ内の集計値は視覚的に合計されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-120">Additionally, aggregate values within the subcube are visually totaled.</span></span> <span data-ttu-id="ccf24-121">たとえば、 `USA`、 `WA`、 `OR`を含むサブキューブがあるとします。</span><span class="sxs-lookup"><span data-stu-id="ccf24-121">For example, a subcube contains `USA`, `WA`, and `OR`.</span></span> <span data-ttu-id="ccf24-122">サブキューブによって定義されている州は `USA` と `{WA,OR}` だけなので、 `WA` の集計値は `OR` の合計になります。</span><span class="sxs-lookup"><span data-stu-id="ccf24-122">The aggregate value for `USA` will be the sum of `{WA,OR}` because `WA` and `OR` are the only states defined by the subcube.</span></span> <span data-ttu-id="ccf24-123">他の州は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-123">All other states will be ignored.</span></span>  
  
 <span data-ttu-id="ccf24-124">また、サブキューブの外部にあるセルへの明示的な参照を行うと、キューブ全体のコンテキストで評価されるセル値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-124">Also, explicit references to cells outside the subcube return cell values that are evaluated in the context of the whole cube.</span></span> <span data-ttu-id="ccf24-125">たとえば、今年度に限定したサブキューブを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="ccf24-125">For example, you create a subcube that is limited to the current year.</span></span> <span data-ttu-id="ccf24-126">この場合、 [ParallelPeriod](/sql/mdx/parallelperiod-mdx) 関数を使用して今年度を前年度と比較することができます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-126">You then use the [ParallelPeriod](/sql/mdx/parallelperiod-mdx) function to compare the current year to the previous year.</span></span> <span data-ttu-id="ccf24-127">前年の値がサブキューブの外側にある場合でも、値の違いが返されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-127">The difference in values will be returned even though the previous year's value lies outside the subcube.</span></span>  
  
 <span data-ttu-id="ccf24-128">さらに、元のコンテキストを上書きしない場合、サブセレクト内で評価されるセット関数は、サブセレクトのコンテキストで評価されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-128">Finally, if the original context is not overwritten, set functions evaluated in a subselect are evaluated in the context of the subselect.</span></span> <span data-ttu-id="ccf24-129">コンテキストを上書きする場合、セット関数はキューブ全体のコンテキストで評価されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-129">If the context is overwritten, set functions are evaluated in the context of the whole cube.</span></span>  
  
## <a name="create-subcube-example"></a><span data-ttu-id="ccf24-130">CREATE SUBCUBE の例</span><span class="sxs-lookup"><span data-stu-id="ccf24-130">CREATE SUBCUBE Example</span></span>  
 <span data-ttu-id="ccf24-131">以下の例では、Budget キューブを 4200 と 4300 のアカウントに限定するサブキューブを作成しています。</span><span class="sxs-lookup"><span data-stu-id="ccf24-131">The following example creates a subcube that restricts the Budget cube to only accounts 4200 and 4300:</span></span>  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 <span data-ttu-id="ccf24-132">セッションに対するサブキューブが作成されるので、以降のクエリは、キューブ全体ではなくサブキューブに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-132">Having created a subcube for the session, any subsequent queries will be against the subcube, not the whole cube.</span></span> <span data-ttu-id="ccf24-133">たとえば、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ccf24-133">For example, you run the following query.</span></span> <span data-ttu-id="ccf24-134">このクエリでは、アカウント 4200 と 4300 のメンバーだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="ccf24-134">This query will only return members from accounts 4200 and 4300.</span></span>  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a><span data-ttu-id="ccf24-135">参照</span><span class="sxs-lookup"><span data-stu-id="ccf24-135">See Also</span></span>  
 <span data-ttu-id="ccf24-136">[MDX&#41;&#40;クエリでのキューブコンテキストの確立](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="ccf24-136">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 [<span data-ttu-id="ccf24-137">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ccf24-137">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
