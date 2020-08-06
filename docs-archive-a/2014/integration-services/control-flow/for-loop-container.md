---
title: For ループ コンテナー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainerdetails.f1
helpviewer_keywords:
- repeating control flow
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6c864779237fdbf4dd249f87b7c06655293c047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631203"
---
# <a name="for-loop-container"></a><span data-ttu-id="3b953-102">For ループ コンテナー</span><span class="sxs-lookup"><span data-stu-id="3b953-102">For Loop Container</span></span>
  <span data-ttu-id="3b953-103">For ループ コンテナーは、パッケージ内で繰り返す制御フローを定義します。</span><span class="sxs-lookup"><span data-stu-id="3b953-103">The For Loop container defines a repeating control flow in a package.</span></span> <span data-ttu-id="3b953-104">ループの実装は、プログラミング言語の **For** ループ構造と同じです。</span><span class="sxs-lookup"><span data-stu-id="3b953-104">The loop implementation is similar to the **For** looping structure in programming languages.</span></span> <span data-ttu-id="3b953-105">For ループ コンテナーは、ループの各繰り返しで式を評価し、式が `False` に評価されるまでそのワークフローを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3b953-105">In each repeat of the loop, the For Loop container evaluates an expression and repeats its workflow until the expression evaluates to `False`.</span></span>  
  
 <span data-ttu-id="3b953-106">For ループ コンテナーは、次の要素を使用してループを定義します。</span><span class="sxs-lookup"><span data-stu-id="3b953-106">The For Loop container usesthe following elements to define the loop:</span></span>  
  
-   <span data-ttu-id="3b953-107">ループ カウンターに値を割り当てる、省略可能な初期化式。</span><span class="sxs-lookup"><span data-stu-id="3b953-107">An optional initialization expression that assigns values to the loop counters.</span></span>  
  
-   <span data-ttu-id="3b953-108">ループの停止または続行のテストに使用する式を含む、評価式。</span><span class="sxs-lookup"><span data-stu-id="3b953-108">An evaluation expression that contains the expression used to test whether the loop should stop or continue.</span></span>  
  
-   <span data-ttu-id="3b953-109">ループ カウンターを増減する、省略可能な初期化式。</span><span class="sxs-lookup"><span data-stu-id="3b953-109">An optional iteration expression that increments or decrements the loop counter.</span></span>  
  
 <span data-ttu-id="3b953-110">次の図は、メール送信タスクの For ループ コンテナーを示しています。</span><span class="sxs-lookup"><span data-stu-id="3b953-110">The following diagram shows a For Loop container with a Send Mail task.</span></span> <span data-ttu-id="3b953-111">初期化式が `@Counter = 0`の場合、評価式は `@Counter < 4`になり、初期化式が `@Counter = @Counter + 1`の場合、ループは 4 回繰り返して 4 つの電子メール メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="3b953-111">If the initialization expression is `@Counter = 0`, the evaluation expression is `@Counter < 4`, and the iteration expression is `@Counter = @Counter + 1`, the loop repeats four times and sends four e-mail messages.</span></span>  
  
 <span data-ttu-id="3b953-112">![タスクを 4 回繰り返す For ループ コンテナー](../media/ssis-forloop.gif "タスクを 4 回繰り返す For ループ コンテナー")</span><span class="sxs-lookup"><span data-stu-id="3b953-112">![A For Loop container repeats a task four times](../media/ssis-forloop.gif "A For Loop container repeats a task four times")</span></span>  
  
 <span data-ttu-id="3b953-113">この式は、有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b953-113">The expressions must be valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="3b953-114">初期化式および代入式を作成するには、代入演算子 (=) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b953-114">To create the initialization and assignment expressions, you can use the assignment operator (=).</span></span> <span data-ttu-id="3b953-115">この演算子は、Integration Services の式文法以外ではサポートされておらず、For ループ コンテナーの初期化式および代入式の種類によってのみ、使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b953-115">This operator is not otherwise supported by the Integration Services expression grammar and can only be used by the initialization and assignment expression types in the For Loop container.</span></span> <span data-ttu-id="3b953-116">代入演算子を使用するあらゆる式には、構文 `@Var = <expression>` が含まれる必要があります。この構文の **Var** は実行時の変数で、\<expression> は [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 式の構文の規則に従う式です。</span><span class="sxs-lookup"><span data-stu-id="3b953-116">Any expression that uses the assignment operator must have the syntax `@Var = <expression>`, where **Var** is a run-time variable and \<expression> is an expression that follows the rules of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="3b953-117">この式には、変数、リテラル、および、SSIS の式文法でサポートされるあらゆる演算子と関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3b953-117">The expression can include the variables, literals, and any operators and functions that the SSIS expression grammar supports.</span></span> <span data-ttu-id="3b953-118">この式は、変数のデータ型にキャスト可能なデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b953-118">The expression must evaluate to a data type that can be cast to the data type of the variable.</span></span>  
  
 <span data-ttu-id="3b953-119">For ループ コンテナーでは、評価式を 1 つだけ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3b953-119">A For Loop container can have only one evaluation expression.</span></span> <span data-ttu-id="3b953-120">したがって、For ループ コンテナーは、すべての制御フローの要素を同一回数実行します。</span><span class="sxs-lookup"><span data-stu-id="3b953-120">This means that the For Loop container runs all its control flow elements the same number of times.</span></span> <span data-ttu-id="3b953-121">For ループ コンテナーには、別の For ループ コンテナーを含めることができるため、パッケージ内で、入れ子になっているループを構築したり複合型のループを実装できます。</span><span class="sxs-lookup"><span data-stu-id="3b953-121">Because the For Loop container can include other For Loop containers, you can build nested loops and implement complex looping in packages.</span></span>  
  
 <span data-ttu-id="3b953-122">For ループ コンテナー上でトランザクションのプロパティを設定し、パッケージ制御フローのサブセットのトランザクションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="3b953-122">You can set a transaction property on the For Loop container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="3b953-123">この方法により、より細かなレベルでトランザクションを管理できます。</span><span class="sxs-lookup"><span data-stu-id="3b953-123">In this way, you can manage transactions at a more granular level.</span></span> <span data-ttu-id="3b953-124">たとえば、For ループ コンテナーが、テーブル内のデータを複数回更新する制御フローを繰り返す場合、For ループおよびその制御フローを構成して、1 つでも正常に更新できないデータがある場合すべてのデータを更新しない、というトランザクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b953-124">For example, if a For Loop container repeats a control flow that updates data in a table multiple times, you can configure the For Loop and its control flow to use a transaction to ensure that if not all data is updated successfully, no data is updated.</span></span> <span data-ttu-id="3b953-125">詳細については、「 [Integration Services のトランザクション](../integration-services-transactions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b953-125">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-for-loop-container"></a><span data-ttu-id="3b953-126">For ループ コンテナーの構成</span><span class="sxs-lookup"><span data-stu-id="3b953-126">Configuration of the For Loop Container</span></span>  
 <span data-ttu-id="3b953-127">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="3b953-127">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3b953-128">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b953-128">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="3b953-129">[[For ループ エディター]](../for-loop-editor.md)</span><span class="sxs-lookup"><span data-stu-id="3b953-129">[For Loop Editor](../for-loop-editor.md)</span></span>  
  
-   <span data-ttu-id="3b953-130">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="3b953-130">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="3b953-131">プログラムによってこれらのプロパティを設定する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** クラスのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b953-131">For more information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3b953-132">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3b953-132">Related Tasks</span></span>  
 <span data-ttu-id="3b953-133">Foreach ループ コンテナーの構成方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b953-133">For information about how to configure a For Loop Container, see the following topics.</span></span>  
  
-   [<span data-ttu-id="3b953-134">For ループ コンテナーを構成する</span><span class="sxs-lookup"><span data-stu-id="3b953-134">Configure a For Loop Container</span></span>](for-loop-container.md)  
  
-   [<span data-ttu-id="3b953-135">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="3b953-135">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b953-136">参照</span><span class="sxs-lookup"><span data-stu-id="3b953-136">See Also</span></span>  
 <span data-ttu-id="3b953-137">[制御フロー](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3b953-137">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="3b953-138">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="3b953-138">Integration Services &#40;SSIS&#41; Expressions</span></span>](../expressions/integration-services-ssis-expressions.md)  
  
  
