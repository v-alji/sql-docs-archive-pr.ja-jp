---
title: '[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [全般] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 72e4a77df553ac8e97609e82bd51c8fd93b64b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645565"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a><span data-ttu-id="fda97-102">[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [全般] ページ</span><span class="sxs-lookup"><span data-stu-id="fda97-102">Create New Condition or Open Condition Dialog Box, General Page</span></span>
  <span data-ttu-id="fda97-103">このダイアログ ボックスを使用すると、ポリシー ベースの管理条件を作成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="fda97-103">Use this dialog box to create or change a Policy-Based Management condition.</span></span> <span data-ttu-id="fda97-104">条件とは、ポリシー ベースの管理で管理する対象に許可されている状態のセットをファセットについて指定するブール式です。</span><span class="sxs-lookup"><span data-stu-id="fda97-104">A condition is a Boolean expression that specifies a set of allowed states of a Policy-Based Management managed target with regard to facets.</span></span> <span data-ttu-id="fda97-105">**[式]/[フィールド]** ボックスで選択できるプロパティは、使用するファセットによって異なります。</span><span class="sxs-lookup"><span data-stu-id="fda97-105">The properties that can be selected in the **Expression/Field** box depend upon the facet that is used.</span></span> <span data-ttu-id="fda97-106">条件と各ファセットおよびポリシーとの関係の詳細については、「 [ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fda97-106">For more information about how conditions relate to facets and policies, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fda97-107">Options</span><span class="sxs-lookup"><span data-stu-id="fda97-107">Options</span></span>  
 <span data-ttu-id="fda97-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="fda97-108">**Name**</span></span>  
 <span data-ttu-id="fda97-109">新しい条件の場合は、新しい条件名を入力します。</span><span class="sxs-lookup"><span data-stu-id="fda97-109">For a new condition, type the new condition name.</span></span> <span data-ttu-id="fda97-110">既存の条件の場合は、その名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fda97-110">For an existing condition, the name is displayed.</span></span>  
  
 <span data-ttu-id="fda97-111">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="fda97-111">**Facet**</span></span>  
 <span data-ttu-id="fda97-112">この条件で使用されるファセット。</span><span class="sxs-lookup"><span data-stu-id="fda97-112">The facet used by this condition.</span></span>  
  
 <span data-ttu-id="fda97-113">**[AndOr]**</span><span class="sxs-lookup"><span data-stu-id="fda97-113">**AndOr**</span></span>  
 <span data-ttu-id="fda97-114">複数の式を追加する場合は、 **And** または **Or**を使用して式を結合するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fda97-114">When you add multiple expressions, indicates whether the expressions should be joined by using **And** or **Or**.</span></span> <span data-ttu-id="fda97-115">式が 1 つだけしかない場合は空白になります。</span><span class="sxs-lookup"><span data-stu-id="fda97-115">Remains blank when there is only one expression.</span></span>  
  
 <span data-ttu-id="fda97-116">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="fda97-116">**Field**</span></span>  
 <span data-ttu-id="fda97-117">各ファセットは、設定可能な 1 つまたは複数のプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="fda97-117">Each facet exposes one or more properties that can be set.</span></span> <span data-ttu-id="fda97-118">[フィールド] ボックスで、この条件の式を作成するために使用できるプロパティの一覧からプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="fda97-118">In the field box, select a property from the list of available properties to create an expression for this condition.</span></span>  
  
 <span data-ttu-id="fda97-119">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="fda97-119">**Operator**</span></span>  
 <span data-ttu-id="fda97-120">この式の比較演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="fda97-120">Select a comparison operator for this expression.</span></span> <span data-ttu-id="fda97-121">演算子には、=、!=、>、>=、<、<=、[NOT]LIKE、[NOT]IN があります。</span><span class="sxs-lookup"><span data-stu-id="fda97-121">Operators are as follows: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN.</span></span> <span data-ttu-id="fda97-122">プロパティによっては、使用できない演算子もあります。</span><span class="sxs-lookup"><span data-stu-id="fda97-122">Not all operators are available for some properties.</span></span>  
  
 <span data-ttu-id="fda97-123">**Value**</span><span class="sxs-lookup"><span data-stu-id="fda97-123">**Value**</span></span>  
 <span data-ttu-id="fda97-124">この式の値の設定。</span><span class="sxs-lookup"><span data-stu-id="fda97-124">The value setting for this expression.</span></span> <span data-ttu-id="fda97-125">許容値は、ファセットによって異なります。</span><span class="sxs-lookup"><span data-stu-id="fda97-125">The allowed values depend on the facet.</span></span> <span data-ttu-id="fda97-126">値は、TRUE/FALSE、文字列、または数値です。</span><span class="sxs-lookup"><span data-stu-id="fda97-126">Values can be TRUE/FALSE, string, or numeric.</span></span> <span data-ttu-id="fda97-127">文字列値は、 **'AdventureWorks'** のように、一重引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="fda97-127">String values must be enclosed in single quotation marks, for example: **'AdventureWorks'**.</span></span> <span data-ttu-id="fda97-128">プロパティによっては、使用できない演算子もあります。</span><span class="sxs-lookup"><span data-stu-id="fda97-128">Not all operators are available for some properties.</span></span>  
  
## <a name="group-clauses"></a><span data-ttu-id="fda97-129">句のグループ化</span><span class="sxs-lookup"><span data-stu-id="fda97-129">Group Clauses</span></span>  
 <span data-ttu-id="fda97-130">句をグループ化すると、クエリの他の部分とは別個の、単一のまとまりとして操作できます。これは、数式や論理ステートメントで式の前後をかっこで囲むのと似ています。</span><span class="sxs-lookup"><span data-stu-id="fda97-130">Clauses can be grouped to operate as a single unit separate from the rest of the query, just like putting parentheses around an expression in a mathematical equation or logic statement.</span></span> <span data-ttu-id="fda97-131">句のグループ化は、複雑なクエリを作成するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fda97-131">Grouping clauses is useful when you are building complex queries.</span></span>  
  
 <span data-ttu-id="fda97-132">**句をグループ化するには**</span><span class="sxs-lookup"><span data-stu-id="fda97-132">**To group clauses**</span></span>  
  
-   <span data-ttu-id="fda97-133">Shift キーまたは Ctrl キーを押しながら複数の句をクリックして範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="fda97-133">Press the SHIFT or CTRL keys, and then click two or more clauses to select a range.</span></span> <span data-ttu-id="fda97-134">選択した領域を右クリックし、 **[句のグループ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-134">Right-click the selected area, and then click **Group Clauses**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda97-135">参照</span><span class="sxs-lookup"><span data-stu-id="fda97-135">See Also</span></span>  
 [<span data-ttu-id="fda97-136">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="fda97-136">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
