---
title: Integration Services (SSIS) の式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], expressions
- Integration Services packages, expressions
- SQL Server Integration Services packages, expressions
- expressions [Integration Services], packages
- SSIS packages, expressions
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff0bd46034108537ebede7567b042997c94871ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716513"
---
# <a name="integration-services-ssis-expressions"></a><span data-ttu-id="b783d-102">Integration Services (SSIS) の式</span><span class="sxs-lookup"><span data-stu-id="b783d-102">Integration Services (SSIS) Expressions</span></span>
  <span data-ttu-id="b783d-103">式は、単一のデータ値が得られる、識別子、リテラル、関数、演算子などの記号の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="b783d-103">An expression is a combination of symbols-identifiers, literals, functions, and operators-that yields a single data value.</span></span> <span data-ttu-id="b783d-104">単純式には、1 つの定数、変数、または関数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-104">Simple expressions can be a single constant, variable, or function.</span></span> <span data-ttu-id="b783d-105">より頻繁に使用されるのは複雑な式で、複数の演算子や関数を使用し、複数の列や変数を参照します。</span><span class="sxs-lookup"><span data-stu-id="b783d-105">More frequently, expressions are complex, using multiple operators and functions and referencing multiple columns and variables.</span></span> <span data-ttu-id="b783d-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、CASE ステートメントの条件の定義、データ列値の生成および更新、変数への値の代入、実行時のプロパティの更新および作成、優先順位制約の制約の定義、および For ループ コンテナーでの利用に式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-106">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expressions can be used to define conditions for CASE statements, create and update values in data columns, assign values to variables, update or populate properties at run time, define constraints in precedence constraints, and provide the expressions used by the For Loop container.</span></span>  
  
 <span data-ttu-id="b783d-107">式は、式の言語および式エバリュエーターに基づいています。</span><span class="sxs-lookup"><span data-stu-id="b783d-107">Expressions are based on an expression language, and the expression evaluator.</span></span> <span data-ttu-id="b783d-108">式エバリュエーターは式を解析して、式の言語のルールに従っているかどうか判断します。</span><span class="sxs-lookup"><span data-stu-id="b783d-108">The expression evaluator parses the expression and determines whether the expression follows the rules of the expression language.</span></span> <span data-ttu-id="b783d-109">式の構文およびサポートされているリテラルと識別子の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b783d-109">For more information about the expression syntax and supported literals and identifiers, see the following topics.</span></span>  
  
-   [<span data-ttu-id="b783d-110">構文 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="b783d-110">Syntax &#40;SSIS&#41;</span></span>](syntax-ssis.md)  
  
-   [<span data-ttu-id="b783d-111">リテラル (SSIS)</span><span class="sxs-lookup"><span data-stu-id="b783d-111">Literals &#40;SSIS&#41;</span></span>](numeric-string-and-boolean-literals.md)  
  
-   [<span data-ttu-id="b783d-112">識別子 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="b783d-112">Identifiers &#40;SSIS&#41;</span></span>](identifiers-ssis.md)  
  
## <a name="components-that-use-expressions"></a><span data-ttu-id="b783d-113">式を使用するコンポーネント</span><span class="sxs-lookup"><span data-stu-id="b783d-113">Components that Use Expressions</span></span>  
 <span data-ttu-id="b783d-114">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の次の要素で式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-114">The following elements in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] can use expressions:</span></span>  
  
-   <span data-ttu-id="b783d-115">条件分割変換では、式に基づいて、データ行を別の出力先に出力するかどうかを決定する決定構造が実装されます。</span><span class="sxs-lookup"><span data-stu-id="b783d-115">The Conditional Split transformation implements a decision structure based on expressions to direct data rows to different destinations.</span></span> <span data-ttu-id="b783d-116">条件分割変換で使用する式は、`true` または `false` に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b783d-116">Expressions used in a Conditional Split transformation must evaluate to `true` or `false`.</span></span> <span data-ttu-id="b783d-117">たとえば、式 "Column1 > Column2" の条件を満たす行は、別の出力にルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="b783d-117">For example, rows that meet the condition in the expression "Column1 > Column2" can be routed to a separate output.</span></span>  
  
-   <span data-ttu-id="b783d-118">派生列変換では、式で生成された値を使用して、データ フローに新しい列を作成するか、または既存の列を更新します。</span><span class="sxs-lookup"><span data-stu-id="b783d-118">The Derived Column transformation uses values created by using expressions either to populate new columns in a data flow, or to update existing columns.</span></span> <span data-ttu-id="b783d-119">たとえば、Column1 + " ABC" という式を使用して連結された文字列で、値を更新したり、新しい値を生成できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-119">For example, the expression Column1 + " ABC" can be used to update a value or to create a new value with the concatenated string.</span></span>  
  
-   <span data-ttu-id="b783d-120">変数に値を設定するために式を使用します。</span><span class="sxs-lookup"><span data-stu-id="b783d-120">Variables use an expression to set their value.</span></span> <span data-ttu-id="b783d-121">たとえば、GETDATE() を使用すると、変数の値として現在の日付が設定されます。</span><span class="sxs-lookup"><span data-stu-id="b783d-121">For example, GETDATE() sets the value of the variable to the current date.</span></span>  
  
-   <span data-ttu-id="b783d-122">優先順位制約では、式を使用して、パッケージ内の制約付きタスクまたはコンテナーを実行するかどうか判断する条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="b783d-122">Precedence constraints can use expressions to specify the conditions that determine whether the constrained task or container in a package runs.</span></span> <span data-ttu-id="b783d-123">優先順位制約で使用する式は、`true` または `false` に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b783d-123">Expressions used in a precedence constraint must evaluate to `true` or `false`.</span></span> <span data-ttu-id="b783d-124">たとえば、\@A > \@B という式は 2 つのユーザー定義変数を比較して、制約付きタスクを実行するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="b783d-124">For example, the expression \@A > \@B compares two user-defined variables to determine whether the constrained task runs.</span></span>  
  
-   <span data-ttu-id="b783d-125">For ループ コンテナーでは、式を使用して、ループ構造で使用する初期化ステートメント、評価ステートメント、および増分ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b783d-125">The For Loop container can use expressions to build the initialization, evaluation, and the incrementing statements that the looping structure uses.</span></span> <span data-ttu-id="b783d-126">たとえば、\@Counter = 1 という式はループ カウンターを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b783d-126">For example, the expression \@Counter = 1 initializes the loop counter.</span></span>  
  
 <span data-ttu-id="b783d-127">式は、パッケージ、For ループや Foreach ループなどのコンテナー、タスク、パッケージおよびプロジェクト レベルの接続マネージャー、ログ プロバイダー、Foreach 列挙子のプロパティ値の更新にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-127">Expressions can also be used to update the values of properties of packages, containers such as the For Loop and Foreach Loop, tasks, package and project level connection managers, log providers, and Foreach enumerators.</span></span> <span data-ttu-id="b783d-128">たとえば、プロパティの式を使用して、"Localhost.AdventureWorks" という文字列を SQL 実行タスクの ConnectionName プロパティに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="b783d-128">For example, using a property expression, the string "Localhost.AdventureWorks" can be assigned to the ConnectionName property of the Execute SQL task.</span></span> <span data-ttu-id="b783d-129">詳細については、「 [パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b783d-129">For more information, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="icon-markers-for-expressions"></a><span data-ttu-id="b783d-130">式のアイコン マーカー</span><span class="sxs-lookup"><span data-stu-id="b783d-130">Icon Markers for Expressions</span></span>  
 <span data-ttu-id="b783d-131">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、式が設定されている接続マネージャー、変数、およびタスクの横に特別なアイコン マーカーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b783d-131">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], a special icon marker displays next to connection managers, variables, and tasks that have expressions set on them.</span></span> <span data-ttu-id="b783d-132">**HasExpressions** プロパティは、変数を除き、式をサポートするすべての SSIS オブジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-132">The **HasExpressions** property is available on all SSIS objects that support expresions, with the exception of variables.</span></span> <span data-ttu-id="b783d-133">このプロパティにより、式が設定されているオブジェクトを簡単に識別できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-133">The property enables you to easily identy which objects have expressions.</span></span>  
  
## <a name="expression-builder"></a><span data-ttu-id="b783d-134">式ビルダー</span><span class="sxs-lookup"><span data-stu-id="b783d-134">Expression Builder</span></span>  
 <span data-ttu-id="b783d-135">式ビルダーは、式を作成するためのグラフィック ツールです。</span><span class="sxs-lookup"><span data-stu-id="b783d-135">The expression builder is a graphical tool for building expressions.</span></span> <span data-ttu-id="b783d-136">**[条件分割変換エディター]** ダイアログ ボックス、 **[派生列変換エディター]** ダイアログ ボックス、および **[式ビルダー]** ダイアログ ボックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b783d-136">It is available in the **Conditional Split Transformation Editor**, **Derived Column Transformation Editor** dialog boxes, and in the **Expression Builder** dialog box, is a graphical tool for building expressions.</span></span>  
  
 <span data-ttu-id="b783d-137">式ビルダーでは、パッケージ固有の要素が格納されているフォルダーと、式の言語で使用される関数、型キャスト、演算子が格納されているフォルダーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b783d-137">The expression builder provides folders that contain package-specific elements, and folders that contain the functions, type casts, and operators that the expression language provides.</span></span> <span data-ttu-id="b783d-138">パッケージ固有の要素として、システム変数とユーザー定義変数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b783d-138">The package-specific elements include system variables and user-defined variables.</span></span> <span data-ttu-id="b783d-139">**[条件分割変換エディター]** ダイアログ ボックスおよび **[派生列変換エディター]** ダイアログ ボックスでは、データ列も表示されます。</span><span class="sxs-lookup"><span data-stu-id="b783d-139">In the **Conditional Split Transformation Editor** and **Derived Column Transformation Editor** dialog boxes, you can also view data columns.</span></span> <span data-ttu-id="b783d-140">変換のための式を作成するには、フォルダー内のアイテムを **[条件]** または **[式]** 列にドラッグするか、式を列に直接入力します。</span><span class="sxs-lookup"><span data-stu-id="b783d-140">To build expressions for the transformations, you can drag items from the folders to the **Condition** or **Expression** column or you can type the expression directly in the column.</span></span> <span data-ttu-id="b783d-141">式ビルダーは、変数名の \@ プレフィックスなど、必要な構文要素を自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="b783d-141">The expression builder automatically adds needed syntax elements such as the \@ prefix on variable names.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b783d-142">ユーザー定義変数およびシステム変数の名前では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="b783d-142">The names of user-defined and system variables are case-sensitive.</span></span>  
  
 <span data-ttu-id="b783d-143">変数にはスコープがあるため、式ビルダーの **[変数]** フォルダーにはスコープ内で使用できる変数のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b783d-143">Variables have scope, and the **Variables** folder in the expression builder lists only variables that are in scope and available to use.</span></span> <span data-ttu-id="b783d-144">詳細については、「 [Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b783d-144">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b783d-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b783d-145">Related Tasks</span></span>  
 [<span data-ttu-id="b783d-146">データ フロー コンポーネントで式を使用する</span><span class="sxs-lookup"><span data-stu-id="b783d-146">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="b783d-147">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b783d-147">Related Content</span></span>  
 <span data-ttu-id="b783d-148">social.technet.microsoft.com の技術記事「 [SSIS 式の例](https://go.microsoft.com/fwlink/?LinkId=220761)」</span><span class="sxs-lookup"><span data-stu-id="b783d-148">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b783d-149">参照</span><span class="sxs-lookup"><span data-stu-id="b783d-149">See Also</span></span>  
 [<span data-ttu-id="b783d-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="b783d-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
