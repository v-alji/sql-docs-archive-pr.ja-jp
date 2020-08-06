---
title: 基本的な MDX スクリプト (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default MDX scripts
- statements [MDX]
- expressions [MDX], scripts
- scripts [MDX], about scripts
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
author: minewiskan
ms.author: owend
ms.openlocfilehash: de0d2fea002beda0eca480bd27140bdd202fcb83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737003"
---
# <a name="the-basic-mdx-script-mdx"></a><span data-ttu-id="69874-102">基本的な MDX スクリプト (MDX)</span><span class="sxs-lookup"><span data-stu-id="69874-102">The Basic MDX Script (MDX)</span></span>
  <span data-ttu-id="69874-103">多次元式 (MDX) スクリプトでは、のキューブの計算プロセスを定義 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="69874-103">A Multidimensional Expressions (MDX) script defines the calculation process for a cube in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="69874-104">MDX スクリプトには、以下の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="69874-104">There are two types of MDX scripts:</span></span>  
  
 <span data-ttu-id="69874-105">**既定の MDX スクリプト**</span><span class="sxs-lookup"><span data-stu-id="69874-105">**The default MDX script**</span></span>  
 <span data-ttu-id="69874-106">キューブを作成すると、そのキューブの既定の MDX スクリプトが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="69874-106">At the time that you create a cube, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates a default MDX script for that cube.</span></span> <span data-ttu-id="69874-107">このスクリプトは、キューブ全体の計算パスを定義します。</span><span class="sxs-lookup"><span data-stu-id="69874-107">This script defines a calculation pass for the whole cube.</span></span>  
  
 <span data-ttu-id="69874-108">**ユーザー定義の MDX スクリプト**</span><span class="sxs-lookup"><span data-stu-id="69874-108">**User-defined MDX script**</span></span>  
 <span data-ttu-id="69874-109">キューブを作成した後で、キューブの計算機能を拡張するためにユーザー定義の MDX スクリプトを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="69874-109">After you have created a cube, you can add user-defined MDX scripts that extend the calculation capabilities of the cube.</span></span>  
  
## <a name="the-default-mdx-script"></a><span data-ttu-id="69874-110">既定の MDX スクリプト</span><span class="sxs-lookup"><span data-stu-id="69874-110">The Default MDX Script</span></span>  
 <span data-ttu-id="69874-111">キューブを定義したときに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって作成される既定の MDX スクリプトには、CALCULATE ステートメントが 1 つ入っています。</span><span class="sxs-lookup"><span data-stu-id="69874-111">The default MDX script that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates when you define a cube contains a single CALCULATE statement.</span></span> <span data-ttu-id="69874-112">この単一の CALCULATE ステートメントは既定の MDX スクリプトの先頭に置かれており、最初の計算パスでキューブ全体が計算されるということを示しています。</span><span class="sxs-lookup"><span data-stu-id="69874-112">This single CALCULATE statement is at the beginning of the default MDX script, and indicates that the entire cube should be calculated during the first calculation pass.</span></span>  
  
 <span data-ttu-id="69874-113">既定の MDX スクリプトには、キューブ デザイナーで作成された、名前付きセット、割り当て、および計算されるメンバーを作成するためのスクリプト コマンドも入ります。</span><span class="sxs-lookup"><span data-stu-id="69874-113">The default MDX script also contains the script commands that create named sets, assignments, and calculated members created in Cube Designer:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="69874-114">は既定の MDX スクリプトに直接スクリプト コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="69874-114">directly adds script commands to the default MDX script.</span></span>  
  
-   <span data-ttu-id="69874-115">キューブ内の名前付きセットごとに、対応する CREATE SET ステートメントが既定の MDX スクリプトに存在します。</span><span class="sxs-lookup"><span data-stu-id="69874-115">For each named set in the cube, a corresponding CREATE SET statement exists in the default MDX script.</span></span>  
  
-   <span data-ttu-id="69874-116">キューブに定義されている計算されるメンバーごとに、対応する CREATE MEMBER ステートメントが既定の MDX スクリプトに存在します。</span><span class="sxs-lookup"><span data-stu-id="69874-116">For each calculated member defined in the cube, a corresponding CREATE MEMBER statement exists in the default MDX script.</span></span>  
  
 <span data-ttu-id="69874-117">既定の MDX スクリプトの中のスクリプト コマンド、名前付きセット、および計算されるメンバーの順番は、キューブ デザイナーの **[計算]** タブを使って制御できます。</span><span class="sxs-lookup"><span data-stu-id="69874-117">You can control the order of script commands, named sets, and calculated members in the default MDX script by using the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="69874-118">既定の MDX スクリプトに格納されている計算の定義の詳細については、「 [多次元モデルの計算](../calculations-in-multidimensional-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69874-118">For more information on defining calculations stored in the default MDX script, see [Calculations in Multidimensional Models](../calculations-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="69874-119">関連付けられている MDX スクリプトがない場合、キューブは既定の MDX スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="69874-119">If there is no MDX script associated with a cube, the cube assumes the default MDX script.</span></span> <span data-ttu-id="69874-120">キューブには最低 1 つの MDX スクリプトを関連付ける必要があります。これは、キューブが計算の動作を決定するにあたって MDX スクリプトに依存しているためです。</span><span class="sxs-lookup"><span data-stu-id="69874-120">A cube needs to be associated with at least one MDX script because a cube relies on the MDX script to determine calculation behavior.</span></span> <span data-ttu-id="69874-121">つまり、キューブが MDX スクリプトに関連付けられていない場合、または関連付けられている MDX が空の場合、そのキューブはセルの計算がまったくできないことになります。</span><span class="sxs-lookup"><span data-stu-id="69874-121">In other words, a cube that was not associated with an MDX script or was associated with an empty MDX script could not and would not be able to calculate any cells.</span></span> <span data-ttu-id="69874-122">Analysis Services Scripting Language (ASSL) コマンドまたは分析管理オブジェクト (AMO) のいずれかを使用してプログラム的にキューブを作成する場合は、単一の CALCULATE ステートメントが入った既定の MDX スクリプトをキューブのために作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69874-122">If you programmatically create cubes, either by using Analysis Services Scripting Language (ASSL) commands or by using Analysis Management Objects (AMO), it is recommended that you create a default MDX script containing a single CALCULATE statement for the cube.</span></span>  
  
## <a name="mdx-script-content"></a><span data-ttu-id="69874-123">MDX スクリプトの内容</span><span class="sxs-lookup"><span data-stu-id="69874-123">MDX Script Content</span></span>  
 <span data-ttu-id="69874-124">MDX スクリプトには以下のステートメントと式を入れることができます。</span><span class="sxs-lookup"><span data-stu-id="69874-124">An MDX script can contain the following statements and expressions:</span></span>  
  
 <span data-ttu-id="69874-125">すべての MDX スクリプト ステートメント</span><span class="sxs-lookup"><span data-stu-id="69874-125">All MDX scripting statements</span></span>  
 <span data-ttu-id="69874-126">MDX スクリプトにおいて、MDX スクリプト ステートメントは、計算のコンテキストと範囲を制御し、MDX スクリプト内の他のステートメントの動作を管理します。</span><span class="sxs-lookup"><span data-stu-id="69874-126">In MDX scripts, MDX scripting statements control the context and scope of calculations, and manage the behavior of other statements in the MDX script.</span></span> <span data-ttu-id="69874-127">このカテゴリには以下のステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="69874-127">This category includes the following statements:</span></span>  
  
-   [<span data-ttu-id="69874-128">行なう</span><span class="sxs-lookup"><span data-stu-id="69874-128">CALCULATE</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
-   [<span data-ttu-id="69874-129">あせん</span><span class="sxs-lookup"><span data-stu-id="69874-129">FREEZE</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
-   [<span data-ttu-id="69874-130">検索</span><span class="sxs-lookup"><span data-stu-id="69874-130">SCOPE</span></span>](/sql/mdx/mdx-scripting-scope)  
  
 <span data-ttu-id="69874-131">MDX スクリプト ステートメントの詳細については、「[MDX スクリプト ステートメント &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69874-131">For more information on MDX scripting statements, see [MDX Scripting Statements &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx).</span></span>  
  
 [<span data-ttu-id="69874-132">CREATE MEMBER</span><span class="sxs-lookup"><span data-stu-id="69874-132">CREATE MEMBER</span></span>](/sql/mdx/mdx-data-definition-create-member)  
 <span data-ttu-id="69874-133">CREATE MEMBER ステートメントは、計算されるメンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="69874-133">The CREATE MEMBER statement creates calculated members.</span></span> <span data-ttu-id="69874-134">計算されるメンバーの作成方法の詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69874-134">For more information about how to create calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
 [<span data-ttu-id="69874-135">CREATE SET</span><span class="sxs-lookup"><span data-stu-id="69874-135">CREATE SET</span></span>](/sql/mdx/mdx-data-definition-create-set)  
 <span data-ttu-id="69874-136">CREATE SET ステートメントは名前付きセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="69874-136">The CREATE SET statement creates named sets.</span></span> <span data-ttu-id="69874-137">名前付きセットの作成方法の詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69874-137">For more information about how to create names sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="69874-138">条件付きステートメント</span><span class="sxs-lookup"><span data-stu-id="69874-138">Conditional statements</span></span>  
 <span data-ttu-id="69874-139">条件ステートメントは、MDX スクリプトに条件ロジックを追加します。</span><span class="sxs-lookup"><span data-stu-id="69874-139">Conditional statements add conditional logic to MDX scripts.</span></span> <span data-ttu-id="69874-140">このカテゴリには [CASE](/sql/mdx/case-statement-mdx) および [IF](/sql/mdx/mdx-scripting-if) ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="69874-140">This category includes the [CASE](/sql/mdx/case-statement-mdx) and [IF](/sql/mdx/mdx-scripting-if) statements.</span></span>  
  
 <span data-ttu-id="69874-141">代入式</span><span class="sxs-lookup"><span data-stu-id="69874-141">Assignment expressions</span></span>  
 <span data-ttu-id="69874-142">代入式は、制約されたサブキューブに式 (値など) を代入します。</span><span class="sxs-lookup"><span data-stu-id="69874-142">An assignment expression assigns an expression, such as a value, to a constrained subcube.</span></span> <span data-ttu-id="69874-143">制約されたサブキューブ式は、MDX スクリプト内でサブキューブの "境界" を定義する、制約されたセット式の集合です。</span><span class="sxs-lookup"><span data-stu-id="69874-143">A constrained subcube expression is a collection of constrained set expressions that define the "edges" of a subcube within an MDX script.</span></span> <span data-ttu-id="69874-144">以下のコードに、制約されたサブキューブ式の構文を示します。</span><span class="sxs-lookup"><span data-stu-id="69874-144">The following codes shows the syntax for a constrained subcube expression:</span></span>  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## <a name="see-also"></a><span data-ttu-id="69874-145">参照</span><span class="sxs-lookup"><span data-stu-id="69874-145">See Also</span></span>  
 <span data-ttu-id="69874-146">[Mdx 言語リファレンス &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="69874-146">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="69874-147">MDX スクリプティングの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="69874-147">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
