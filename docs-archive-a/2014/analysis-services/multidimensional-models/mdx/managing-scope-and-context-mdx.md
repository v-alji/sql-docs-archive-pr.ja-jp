---
title: スコープとコンテキストの管理 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7cf1e6cea8df00b632e114a5a8756373738ca6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639704"
---
# <a name="managing-scope-and-context-mdx"></a><span data-ttu-id="1ced4-102">スコープとコンテキストの管理 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1ced4-102">Managing Scope and Context (MDX)</span></span>
  <span data-ttu-id="1ced4-103">では [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、多次元式 (MDX) スクリプトをキューブ全体に適用することも、スクリプトの実行内の特定の時点でキューブの特定の部分に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script can apply to the entire cube, or to specific portions of the cube, at specific points within the execution of the script.</span></span> <span data-ttu-id="1ced4-104">MDX スクリプトは、計算パスを使用することにより、階層化されたアプローチでキューブ内の計算を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-104">The MDX script can take a layered approach to calculations within a cube through the use of calculation passes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ced4-105">計算パスが計算に及ぼす影響の詳細については、「[パス順序と解決順序の概要 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1ced4-105">For more information on how calculation passes can affect calculations, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="1ced4-106">MDX スクリプト内の計算パス、スコープ、およびコンテキストを制御するための具体的な方法は、CALCULATE ステートメント、`This` 関数、および SCOPE ステートメントを使用することです。</span><span class="sxs-lookup"><span data-stu-id="1ced4-106">To control the calculation pass, scope, and context within an MDX script, you specifically use the CACULATE statement, the `This` function, and the SCOPE statement.</span></span>  
  
## <a name="using-the-calculate-statement"></a><span data-ttu-id="1ced4-107">CALCULATE ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="1ced4-107">Using the CALCULATE Statement</span></span>  
 <span data-ttu-id="1ced4-108">CALCULATE ステートメントは、キューブ内の各セルに集計データを格納します。</span><span class="sxs-lookup"><span data-stu-id="1ced4-108">The CALCULATE statement populates each cell in the cube with aggregated data.</span></span> <span data-ttu-id="1ced4-109">たとえば、既定の MDX スクリプトの冒頭には、単一の CALCULATE ステートメントが置かれています。</span><span class="sxs-lookup"><span data-stu-id="1ced4-109">For example, the default MDX script has a single CALCULATE statement at the beginning of the script.</span></span>  
  
 <span data-ttu-id="1ced4-110">CALCULATE ステートメントの構文の詳細については、「[CALCULATE ステートメント (MDX)](/sql/mdx/mdx-scripting-calculate)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1ced4-110">For more information on the syntax of the CALCULATE statement, see [CALCULATE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ced4-111">スクリプトの中で CALCULATE ステートメントが SCOPE ステートメントに入れられている場合、MDX は CALCULATE ステートメントの評価を、キューブ全体に対してではなく、SCOPE ステートメントで定義されるサブキューブのコンテキストの中で行います。</span><span class="sxs-lookup"><span data-stu-id="1ced4-111">If the script contains a SCOPE statement that contains a CALCULATE statement, MDX evaluates the CALCULATE statement within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
## <a name="using-the-this-function"></a><span data-ttu-id="1ced4-112">This 関数の使用</span><span class="sxs-lookup"><span data-stu-id="1ced4-112">Using the This Function</span></span>  
 <span data-ttu-id="1ced4-113">`This` 関数により、MDX スクリプトの中で現在のサブキューブを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-113">The `This` function lets you retrieve the current subcube within an MDX script.</span></span> <span data-ttu-id="1ced4-114">`This` 関数を使用すると、現在のサブキューブの中のセルの値を MDX 式にすばやく設定できます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-114">You can use the `This` function to quickly set the value of cells within the current subcube to an MDX expression.</span></span> <span data-ttu-id="1ced4-115">`This` 関数を SCOPE ステートメントと併用して、特定の計算パスの間に特定のサブキューブの内容を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-115">You often use the `This` function in conjunction with the SCOPE statement to change the contents of a specific subcube during a specific calculation pass.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ced4-116">スクリプトの中で `This` 関数が SCOPE ステートメントに入れられている場合、MDX は `This` 関数の評価を、キューブ全体に対してではなく、SCOPE ステートメントで定義されるサブキューブのコンテキストの中で行います。</span><span class="sxs-lookup"><span data-stu-id="1ced4-116">If the script contains a SCOPE statement that contains a `This` function, MDX evaluates the `This` function within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
### <a name="this-function-example"></a><span data-ttu-id="1ced4-117">This 関数の例</span><span class="sxs-lookup"><span data-stu-id="1ced4-117">This Function Example</span></span>  
 <span data-ttu-id="1ced4-118">次の MDX スクリプト コマンドの例では、`This` 関数を使用することにより、[!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] サンプル キューブにおいて、Customer ディメンションの Redmond メンバーの子に関して、Finance メジャー グループの Amount メジャーの値を 10% 増加させます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-118">The following MDX script command example uses the `This` function to increase the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension:</span></span>  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="1ced4-119">関数の構文の詳細につい `This` ては、「 [MDX&#41;の &#40;](/sql/mdx/this-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ced4-119">For more information on the syntax of the `This` function, see [This &#40;MDX&#41;](/sql/mdx/this-mdx).</span></span>  
  
## <a name="using-the-scope-statement"></a><span data-ttu-id="1ced4-120">SCOPE ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="1ced4-120">Using the SCOPE Statement</span></span>  
 <span data-ttu-id="1ced4-121">SCOPE ステートメントは、MDX スクリプト内の他の MDX 式およびステートメントが入っている現在のサブキューブを定義し、その MDX 式およびステートメントのスコープを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ced4-121">The SCOPE statement defines the current subcube that contains, and specifies the scope of, other MDX expressions and statements within an MDX script.</span></span> <span data-ttu-id="1ced4-122">MDX は、このような他の MDX 式およびステートメント (`This` 関数および  CALCULATE ステートメントを含む) の評価を、サブキューブのコンテキストの中で行います。</span><span class="sxs-lookup"><span data-stu-id="1ced4-122">MDX evaluates this other MDX expressions and statements, including the `This` function and the CALCULATE statement, within the context of the subcube.</span></span>  
  
 <span data-ttu-id="1ced4-123">SCOPE ステートメントは動的ですが、反復的な性質はありません。</span><span class="sxs-lookup"><span data-stu-id="1ced4-123">A SCOPE statement is dynamic, but not iterative in nature.</span></span> <span data-ttu-id="1ced4-124">SCOPE ステートメントに入っているステートメントは 1 回だけ実行されますが、サブキューブ自体は動的に決定されます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-124">The statements contained within a SCOPE statement run once, but the subcube itself can be dynamically determined.</span></span> <span data-ttu-id="1ced4-125">たとえば、SampleCube というキューブがあるとします。</span><span class="sxs-lookup"><span data-stu-id="1ced4-125">For example, you have a cube named SampleCube.</span></span> <span data-ttu-id="1ced4-126">SampleCube キューブに対して以下の SCOPE ステートメントを適用し、コンテキストを Measures ディメンション内の ALLMEMBERS に定義するサブキューブを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ced4-126">Against the SampleCube cube, you apply the following SCOPE statement to define a subcube the defines the context as the ALLMEMBERS within the Measures dimension:</span></span>  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 <span data-ttu-id="1ced4-127">この SCOPE ステートメント内のステートメントと式は 1 回だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-127">The statements and expressions within this SCOPE statement run once.</span></span>  
  
 <span data-ttu-id="1ced4-128">今度は、あるビジネス ユーザーが、ExistingMeasure という 1 つのメジャーが含まれている以下の MDX クエリを、SampleCube キューブに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="1ced4-128">Now, a business user runs the following MDX query that contains one measure, named ExistingMeasure, against the SampleCube cube:</span></span>  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 <span data-ttu-id="1ced4-129">クエリは、以下の表に示す出力のようなセル セットを返します。</span><span class="sxs-lookup"><span data-stu-id="1ced4-129">The cellset returned from the query resembles the output shown in the following table.</span></span>  
  
||<span data-ttu-id="1ced4-130">[ExistingMeasure]</span><span class="sxs-lookup"><span data-stu-id="1ced4-130">[ExistingMeasure]</span></span>|<span data-ttu-id="1ced4-131">[NewMeasure]</span><span class="sxs-lookup"><span data-stu-id="1ced4-131">[NewMeasure]</span></span>|  
|-|-------------------------|--------------------|  
|<span data-ttu-id="1ced4-132">[Customer].[All]</span><span class="sxs-lookup"><span data-stu-id="1ced4-132">[Customer].[All]</span></span>|<span data-ttu-id="1ced4-133">2</span><span class="sxs-lookup"><span data-stu-id="1ced4-133">2</span></span>|<span data-ttu-id="1ced4-134">2</span><span class="sxs-lookup"><span data-stu-id="1ced4-134">2</span></span>|  
  
 <span data-ttu-id="1ced4-135">返されたセル セットを見て、MDX スクリプトの SCOPE ステートメントに含まれている ExistingMeasure 値が、NewMeasure メジャーが定義された後で、どのように動的に更新されるかに注目してください。</span><span class="sxs-lookup"><span data-stu-id="1ced4-135">Looking at the returned cellset, notice how the ExistingMeasure value, included in the SCOPE statement within the MDX script, is dynamically updated after the measure NewMeasure was defined.</span></span>  
  
 <span data-ttu-id="1ced4-136">SCOPE ステートメントを別の SCOPE ステートメント内で入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-136">A SCOPE statement can be nested within another SCOPE statement.</span></span> <span data-ttu-id="1ced4-137">しかし、SCOPE ステートメントは反復的でないので、SCOPE ステートメントを入れ子にする主な目的は、特別な処理のためにサブキューブをさらに細かく分割することです。</span><span class="sxs-lookup"><span data-stu-id="1ced4-137">However, as the SCOPE statement is not iterative, the primary purpose for nesting SCOPE statements is to further subdivide a subcube for special treatment.</span></span>  
  
### <a name="scope-statement-example"></a><span data-ttu-id="1ced4-138">SCOPE ステートメントの例</span><span class="sxs-lookup"><span data-stu-id="1ced4-138">SCOPE Statement Example</span></span>  
 <span data-ttu-id="1ced4-139">次の MDX スクリプトの例では、SCOPE ステートメントを使用することにより、 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] サンプル キューブにおいて、Customer ディメンションの Redmond メンバーの子に関して、Finance メジャー グループの Amount メジャーの値を 10% 大きく設定します。</span><span class="sxs-lookup"><span data-stu-id="1ced4-139">The following MDX script example uses a SCOPE statement to sets the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension.</span></span> <span data-ttu-id="1ced4-140">しかし、別の SCOPE ステートメントにより、2002 年の子の Amount メジャーが含まれるようにサブキューブが変更されます。</span><span class="sxs-lookup"><span data-stu-id="1ced4-140">However, another SCOPE statement changes the subcube to include the Amount measure for the children of the 2002 calendar year.</span></span> <span data-ttu-id="1ced4-141">最終的に、Amount メジャーはこのサブキューブに関してのみ集計され、他の年の Amount メジャーの値は集計されません。</span><span class="sxs-lookup"><span data-stu-id="1ced4-141">Finally, the Amount measure is then aggregated only for that subcube, leaving the aggregated values for the Amount measure in other calendar years unchanged.</span></span>  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="1ced4-142">SCOPE ステートメントの構文の詳細については、「[SCOPE ステートメント (MDX)](/sql/mdx/mdx-scripting-scope)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1ced4-142">For more information on the syntax of the SCOPE statement, see [SCOPE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ced4-143">参照</span><span class="sxs-lookup"><span data-stu-id="1ced4-143">See Also</span></span>  
 <span data-ttu-id="1ced4-144">[Mdx 言語リファレンス &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="1ced4-144">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 <span data-ttu-id="1ced4-145">[MDX の基本的なスクリプト &#40;&#41;](the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="1ced4-145">[The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md) </span></span>  
 [<span data-ttu-id="1ced4-146">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ced4-146">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
