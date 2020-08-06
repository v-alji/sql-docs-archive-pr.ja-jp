---
title: 優先順位制約 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a08fd1d66e43ede4c54284518bab191be8997a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642223"
---
# <a name="precedence-constraints"></a><span data-ttu-id="69727-102">優先順位制約</span><span class="sxs-lookup"><span data-stu-id="69727-102">Precedence Constraints</span></span>
  <span data-ttu-id="69727-103">優先順位制約は、パッケージ内の実行可能ファイル、コンテナー、およびタスクをリンクして制御フローを作成し、実行可能ファイルを実行するかどうかを決定する条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="69727-103">Precedence constraints link executables, containers, and tasks in packages in a control flow, and specify conditions that determine whether executables run.</span></span> <span data-ttu-id="69727-104">実行可能ファイルには、For ループ コンテナー、Foreach ループ コンテナー、シーケンス コンテナー、タスク、またはイベント ハンドラーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="69727-104">An executable can be a For Loop, Foreach Loop, or Sequence container; a task; or an event handler.</span></span> <span data-ttu-id="69727-105">また、イベント ハンドラーは優先順位制約を使用して実行可能ファイルをリンクし、制御フローを作成します。</span><span class="sxs-lookup"><span data-stu-id="69727-105">Event handlers also use precedence constraints to link their executables into a control flow.</span></span>

 <span data-ttu-id="69727-106">優先順位制約は、優先実行可能オブジェクトと制約付きの実行可能オブジェクトを連結します。</span><span class="sxs-lookup"><span data-stu-id="69727-106">A precedence constraint links two executables: the precedence executable and the constrained executable.</span></span> <span data-ttu-id="69727-107">優先実行可能オブジェクトは制約付きの実行可能オブジェクトの前に実行され、優先実行可能オブジェクトの実行結果により、制約付きの実行可能オブジェクトを実行するかどうかが決まる場合があります。</span><span class="sxs-lookup"><span data-stu-id="69727-107">The precedence executable runs before the constrained executable, and the execution result of the precedence executable may determine whether the constrained executable runs.</span></span> <span data-ttu-id="69727-108">次の図は、優先順位制約によってリンクされた 2 つの実行可能ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="69727-108">The following diagram shows two executables linked by a precedence constraint.</span></span>

 <span data-ttu-id="69727-109">![優先順位制約によって接続された実行可能ファイル](../media/ssis-pcsimple.gif "優先順位制約によって接続された実行可能ファイル")</span><span class="sxs-lookup"><span data-stu-id="69727-109">![Executables connected by a precedence constraint](../media/ssis-pcsimple.gif "Executables connected by a precedence constraint")</span></span>

 <span data-ttu-id="69727-110">直線的な制御フロー、つまり分岐のない制御フローでは、優先順位制約のみがタスクの実行順序を制御します。</span><span class="sxs-lookup"><span data-stu-id="69727-110">In a linear control flow, that is, one without branching, precedence constraints alone govern the sequence in which tasks run.</span></span> <span data-ttu-id="69727-111">制御フローに分岐がある場合には、 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイム エンジンが、分岐の直後に続くタスクとコンテナーの実行順序を決定します。</span><span class="sxs-lookup"><span data-stu-id="69727-111">If a control flow branches, the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine determines the execution order among the tasks and containers that immediately follow the branching.</span></span> <span data-ttu-id="69727-112">ランタイム エンジンは、制御フロー内で連結されていないワークフローの実行順序も決定します。</span><span class="sxs-lookup"><span data-stu-id="69727-112">The run-time engine also determines execution order among unconnected workflows in a control flow.</span></span>

 <span data-ttu-id="69727-113">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のアーキテクチャではコンテナーを入れ子にできるので、1 つのタスクのみをカプセル化するタスク ホスト コンテナーを除き、すべてのコンテナーに他のコンテナーと独自の制御フローを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="69727-113">The nested-container architecture of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enables all containers, except for the task host container that encapsulates only a single task, to include other containers, each with its own control flow.</span></span> <span data-ttu-id="69727-114">For ループ コンテナー、Foreach ループ コンテナー、およびシーケンス コンテナーには、タスクとその他のコンテナーを複数含めることができます。さらに、そのコンテナーにも複数のタスクとコンテナーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="69727-114">The For Loop, Foreach Loop, and Sequence containers can include multiple tasks and other containers, which in turn can include multiple tasks and containers.</span></span> <span data-ttu-id="69727-115">たとえば、スクリプト タスクとシーケンス コンテナーを持つパッケージに、そのスクリプト タスクとシーケンス コンテナーをリンクする優先順位制約を含めます。</span><span class="sxs-lookup"><span data-stu-id="69727-115">For example, a package with a Script task and a Sequence container has a precedence constraint that links the Script task and the Sequence container.</span></span> <span data-ttu-id="69727-116">シーケンス コンテナーには 3 つのスクリプト タスクが含まれ、その優先順位制約は 3 つのスクリプト タスクをリンクして制御フローを作成します。</span><span class="sxs-lookup"><span data-stu-id="69727-116">The Sequence container includes three Script tasks, and its precedence constraints link the three Script tasks into a control flow.</span></span> <span data-ttu-id="69727-117">次の図は、2 レベルの入れ子構造のパッケージの優先順位制約を示しています。</span><span class="sxs-lookup"><span data-stu-id="69727-117">The following diagram shows the precedence constraints in a package with two levels of nesting.</span></span>

 <span data-ttu-id="69727-118">![パッケージ内の優先順位制約](../media/mw-dts-12.gif "パッケージ内の優先順位制約")</span><span class="sxs-lookup"><span data-stu-id="69727-118">![Precedence contraints in a package](../media/mw-dts-12.gif "Precedence contraints in a package")</span></span>

 <span data-ttu-id="69727-119">パッケージは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] コンテナー階層の最上層にあるため、複数のパッケージを優先順位制約によってリンクすることはできません。ただし、パッケージ実行タスクをパッケージに追加して、別のパッケージを間接的に制御フローにリンクできます。</span><span class="sxs-lookup"><span data-stu-id="69727-119">Because the package is at the top of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] container hierarchy, multiple packages cannot be linked by precedence constraints; however, you can add an Execute Package task to a package and indirectly link another package into the control flow.</span></span>

 <span data-ttu-id="69727-120">優先順位制約は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="69727-120">You can configure precedence constraints in the following ways:</span></span>

-   <span data-ttu-id="69727-121">評価操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="69727-121">Specify an evaluation operation.</span></span> <span data-ttu-id="69727-122">優先順位制約は、制約値および式の両方、またはいずれか 1 つを使用して、制約付き実行可能ファイルを実行するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="69727-122">The precedence constraint uses a constraint value, an expression, both, or either to determine whether the constrained executable runs.</span></span>

-   <span data-ttu-id="69727-123">優先順位制約で実行結果を使用する場合、成功、失敗、完了のいずれかの実行結果を指定できます。</span><span class="sxs-lookup"><span data-stu-id="69727-123">If the precedence constraint uses an execution result, you can specify the execution result to be success, failure, or completion.</span></span>

-   <span data-ttu-id="69727-124">優先順位制約で実行結果を使用する場合、ブール型に評価される式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="69727-124">If the precedence constraint uses an evaluation result, you can provide an expression that evaluates to a Boolean.</span></span>

-   <span data-ttu-id="69727-125">優先順位制約を単独で評価するか、制約付き実行可能ファイルに適用する別の制約と共に評価するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="69727-125">Specify whether the precedence constraint is evaluated singly or together with other constraints that apply to the constrained executable.</span></span>

## <a name="evaluation-operations"></a><span data-ttu-id="69727-126">評価操作</span><span class="sxs-lookup"><span data-stu-id="69727-126">Evaluation Operations</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="69727-127">には、次の評価操作が用意されています。</span><span class="sxs-lookup"><span data-stu-id="69727-127">provides the following evaluation operations:</span></span>

-   <span data-ttu-id="69727-128">優先順位付き実行可能ファイルの実行結果のみを使用して、制約付き実行可能ファイルを実行するかどうかを決定する制約。</span><span class="sxs-lookup"><span data-stu-id="69727-128">A constraint that uses only the execution result of the precedence executable to determine whether the constrained executable runs.</span></span> <span data-ttu-id="69727-129">優先順位付き実行可能ファイルの実行結果には、完了、成功、または失敗を設定できます。</span><span class="sxs-lookup"><span data-stu-id="69727-129">The execution result of the precedence executable can be completion, success, or failure.</span></span> <span data-ttu-id="69727-130">これは既定の操作です。</span><span class="sxs-lookup"><span data-stu-id="69727-130">This is the default operation.</span></span>

-   <span data-ttu-id="69727-131">評価する式。これを使用して制約付き実行可能ファイルを実行するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="69727-131">An expression that is evaluated to determine whether the constrained executable runs.</span></span> <span data-ttu-id="69727-132">式が TRUE に評価された場合、制限付き実行可能ファイルは実行されます。</span><span class="sxs-lookup"><span data-stu-id="69727-132">If the expression evaluates to true, the constrained executable runs.</span></span>

-   <span data-ttu-id="69727-133">優先順位付き実行可能ファイルの実行結果と、式を評価した戻り結果の両方を必須とする、式および制約。</span><span class="sxs-lookup"><span data-stu-id="69727-133">An expression and a constraint that combines the requirements of execution results of the precedence executable and the return results of evaluating the expression.</span></span>

-   <span data-ttu-id="69727-134">優先順位付き実行可能ファイルの実行結果か、式を評価した戻り結果を使用する、式または制約。</span><span class="sxs-lookup"><span data-stu-id="69727-134">An expression or a constraint that uses either the execution results of the precedence executable or the return results of evaluating the expression.</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="69727-135">デザイナーでは、優先順位制約の種類を色で識別します。</span><span class="sxs-lookup"><span data-stu-id="69727-135">Designer uses color to identify the type of precedence constraint.</span></span> <span data-ttu-id="69727-136">成功制約は緑、失敗制約は赤、完了制約は青で表示されます。</span><span class="sxs-lookup"><span data-stu-id="69727-136">The Success constraint is green, the Failure constraint is red, and the Completion constraint is blue.</span></span> <span data-ttu-id="69727-137">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで制約の種類を示すテキスト ラベルを表示するには、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーのユーザー補助機能を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69727-137">To display text labels in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer that show the type of the constraint, you must configure the accessibility features of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="69727-138">式は、有効な [!INCLUDE[ssIS](../../../includes/ssis-md.md)] の式である必要があります。この式には、関数、演算子、システム関数およびカスタム関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="69727-138">The expression must be a valid [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression, and it can include functions, operators, and system and custom variables.</span></span> <span data-ttu-id="69727-139">詳細については、「[Integration Services &#40;SSIS&#41; の式](../expressions/integration-services-ssis-expressions.md)」および「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69727-139">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>

## <a name="execution-results"></a><span data-ttu-id="69727-140">実行結果</span><span class="sxs-lookup"><span data-stu-id="69727-140">Execution Results</span></span>
 <span data-ttu-id="69727-141">優先順位制約は、次の実行結果を単独で、または式との組み合わせで使用できます。</span><span class="sxs-lookup"><span data-stu-id="69727-141">The precedence constraint can use the following execution results alone or in combination with an expression.</span></span>

-   <span data-ttu-id="69727-142">完了。制約付き実行可能ファイルを実行するには、結果にかかわらず優先順位付き実行可能ファイルが完了することだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="69727-142">Completion requires only that the precedence executable has completed, without regard to outcome, in order for the constrained executable to run.</span></span>

-   <span data-ttu-id="69727-143">成功。制約付き実行可能ファイルを実行するには、優先順位付き実行可能ファイルが正常に完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69727-143">Success requires that the precedence executable must complete successfully for the constrained executable to run.</span></span>

-   <span data-ttu-id="69727-144">失敗。制約付き実行可能ファイルを実行するには、優先順位付き実行可能ファイルが失敗する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69727-144">Failure requires that the precedence executable fail for the constrained executable to run.</span></span>

> [!NOTE]
>  <span data-ttu-id="69727-145">同じ `Precedence Constraint` コレクションのメンバーである優先順位制約のみが、論理 AND 条件でグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="69727-145">Only precedence constraints that are members of the same `Precedence Constraint` collection can be grouped in a logical AND condition.</span></span> <span data-ttu-id="69727-146">たとえば、2 つの Foreach ループ コンテナーの優先順位制約を組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="69727-146">For example, you cannot combine precedence constraints from two Foreach Loop containers.</span></span>

## <a name="configuration-of-the-precedence-constraint"></a><span data-ttu-id="69727-147">優先順位制約の構成</span><span class="sxs-lookup"><span data-stu-id="69727-147">Configuration of the Precedence Constraint</span></span>
 <span data-ttu-id="69727-148">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="69727-148">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>

 <span data-ttu-id="69727-149">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティについては、「 [優先順位制約エディター](../precedence-constraint-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69727-149">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Precedence Constraint Editor](../precedence-constraint-editor.md).</span></span>

 <span data-ttu-id="69727-150">プログラムによってこれらのプロパティを設定する方法については、 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69727-150">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="69727-151">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="69727-151">Related Tasks</span></span>
 <span data-ttu-id="69727-152">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69727-152">For details about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>

-   [<span data-ttu-id="69727-153">優先順位制約のプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="69727-153">Set the Properties of a Precedence Constraint</span></span>](../set-the-properties-of-a-precedence-constraint.md)

-   [<span data-ttu-id="69727-154">ショートカット メニューを使用して優先順位制約の値を設定する</span><span class="sxs-lookup"><span data-stu-id="69727-154">Set the Value of a Precedence Constraint by Using the Shortcut Menu</span></span>](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)

-   [<span data-ttu-id="69727-155">既定の優先順位制約を使用してタスクとコンテナーを連結する</span><span class="sxs-lookup"><span data-stu-id="69727-155">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)

     <span data-ttu-id="69727-156">このトピックでは、優先順位制約の既定の動作を設定する方法、および既定の優先順位制約を使用して実行可能ファイルを連結する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="69727-156">This topic provides information on how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints, see.</span></span>

## <a name="related-content"></a><span data-ttu-id="69727-157">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="69727-157">Related Content</span></span>
 <span data-ttu-id="69727-158">social.technet.microsoft.com の技術記事「 [SSIS 式の例](https://go.microsoft.com/fwlink/?LinkId=220761)」</span><span class="sxs-lookup"><span data-stu-id="69727-158">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>

## <a name="see-also"></a><span data-ttu-id="69727-159">参照</span><span class="sxs-lookup"><span data-stu-id="69727-159">See Also</span></span>
 <span data-ttu-id="69727-160">[優先順位制約に式を追加する複数の](../add-expressions-to-precedence-constraints.md)[優先順位制約](../multiple-precedence-constraints.md)</span><span class="sxs-lookup"><span data-stu-id="69727-160">[Add Expressions to Precedence Constraints](../add-expressions-to-precedence-constraints.md) [Multiple Precedence Constraints](../multiple-precedence-constraints.md)</span></span>


