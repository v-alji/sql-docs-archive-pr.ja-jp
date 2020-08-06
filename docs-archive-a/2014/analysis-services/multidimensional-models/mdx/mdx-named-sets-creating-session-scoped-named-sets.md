---
title: セッションスコープの名前付きセットの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d35bd61dcc59eca8bcb920ed99f2e791631047c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718788"
---
# <a name="creating-session-scoped-named-sets-mdx"></a><span data-ttu-id="6d2e8-102">セッション スコープの名前付きセットの作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="6d2e8-102">Creating Session-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="6d2e8-103">多次元式 (MDX) セッション全体で使用できる名前付きセットを作成するには、 [CREATE SET](/sql/mdx/mdx-data-definition-create-set) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-103">To create a named set that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE SET](/sql/mdx/mdx-data-definition-create-set) statement.</span></span> <span data-ttu-id="6d2e8-104">CREATE SET ステートメントを使用して作成された名前付きセットは、MDX セッションが閉じるまで削除されません。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-104">A named set that is created by using the CREATE SET statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="6d2e8-105">このトピックで説明するように、WITH キーワードの構文は非常に単純で使いやすいものです。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-105">As discussed in this topic, the syntax of the WITH keyword is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d2e8-106">名前付きセットの詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="create-set-syntax"></a><span data-ttu-id="6d2e8-107">CREATE SET の構文</span><span class="sxs-lookup"><span data-stu-id="6d2e8-107">CREATE SET Syntax</span></span>  
 <span data-ttu-id="6d2e8-108">CREATE SET ステートメントの構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-108">Use the following syntax for the CREATE SET statement:</span></span>  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 <span data-ttu-id="6d2e8-109">CREATE SET の構文において、 `cube name` パラメーターには、名前付きセットのメンバーを格納するキューブの名前が入ります。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-109">In the CREATE SET syntax, the `cube name` parameter contains the name of the cube that contains the members for the named set.</span></span> <span data-ttu-id="6d2e8-110">`cube name` パラメーターが指定されなかった場合は、名前付きセットのメンバーを格納するキューブとして、現在のキューブが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-110">If the `cube name` parameter is not specified, the current cube will be used as the cube that contains the member for the named set.</span></span> <span data-ttu-id="6d2e8-111">さらに、 `Set_Identifier` パラメーターには名前付きセットの別名が入り、 `Set_Expression` パラメーターには名前付きセットの別名の参照先であるセット式が入ります。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-111">Also, the `Set_Identifier` parameter contains the alias for the named set, and the `Set_Expression` parameter contains the set expression to which the named set alias will refer.</span></span>  
  
## <a name="create-set-example"></a><span data-ttu-id="6d2e8-112">CREATE SET の例</span><span class="sxs-lookup"><span data-stu-id="6d2e8-112">CREATE SET Example</span></span>  
 <span data-ttu-id="6d2e8-113">次の例では、Store キューブに基づいて `SetCities_2_3` 名前付きセットを作成するために CREATE SET ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-113">The following example uses the CREATE SET statement to create the `SetCities_2_3` named set based on the Store cube.</span></span> <span data-ttu-id="6d2e8-114">`SetCities_2_3` 名前付きセットのメンバーは、City&#xA0;2 および City&#xA0;3 にあるストアです。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-114">The members of the `SetCities_2_3` named set are the stores within City 2 and City 3.</span></span>  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 <span data-ttu-id="6d2e8-115">CREATE SET ステートメントを使って `SetCities_2_3` 名前付きセットを定義しているので、この名前付きセットは現在の MDX セッションが続く限り使用可能です。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-115">By using the CREATE SET statement to define the `SetCities_2_3` named set, this named set remains available for the length of the current MDX session.</span></span> <span data-ttu-id="6d2e8-116">次の例は、City&#xA0;2 と City&#xA0;3 のメンバーを返す有効なクエリです。 `SetCities_2_3` 名前付きセットを作成した後、セッションが閉じる前の任意の時点でこのクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="6d2e8-116">The following example is a valid query that would return City 2 and City 3 members, and that could be run anytime after you create the `SetCities_2_3` named set and before the session closes.</span></span>  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d2e8-117">参照</span><span class="sxs-lookup"><span data-stu-id="6d2e8-117">See Also</span></span>  
 [<span data-ttu-id="6d2e8-118">クエリ スコープの名前付きセットの作成 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="6d2e8-118">Creating Query-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
