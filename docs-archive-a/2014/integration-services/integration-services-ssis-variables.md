---
title: Integration Services (SSIS) の変数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- user-defined variables [Integration Services]
- scope [Integration Services]
- system variables [Integration Services]
- variables [Integration Services]
- variables [Integration Services], about variables
- values [Integration Services]
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 956211ec971d69dc2fdb430dcada82a097280808
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641117"
---
# <a name="integration-services-ssis-variables"></a><span data-ttu-id="0d18a-102">Integration Services (SSIS) の変数</span><span class="sxs-lookup"><span data-stu-id="0d18a-102">Integration Services (SSIS) Variables</span></span>
  <span data-ttu-id="0d18a-103">変数には、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージとそのコンテナー、タスク、およびイベント ハンドラーが実行時に使用できる値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-103">Variables store values that a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its containers, tasks, and event handlers can use at run time.</span></span> <span data-ttu-id="0d18a-104">スクリプト タスクおよびスクリプト コンポーネント内のスクリプトも、変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-104">The scripts in the Script task and the Script component can also use variables.</span></span> <span data-ttu-id="0d18a-105">タスクとコンテナーにワークフロー内での順位を付ける優先順位制約では、制約の定義に式を含める場合に変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-105">The precedence constraints that sequence tasks and containers into a workflow can use variables when their constraint definitions include expressions.</span></span>  
  
 <span data-ttu-id="0d18a-106">変数は、次の目的で [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージ内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-106">You can use variables in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="0d18a-107">実行時に、パッケージ要素のプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-107">Updating properties of package elements at run time.</span></span> <span data-ttu-id="0d18a-108">たとえば、1 つの Foreach ループ コンテナーで許可できる実行可能ファイルの数を動的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-108">For example, you can dynamically set the number of concurrent executables that a Foreach Loop container allows.</span></span>  
  
-   <span data-ttu-id="0d18a-109">メモリ内に参照テーブルを組み込みます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-109">Including an in-memory lookup table.</span></span> <span data-ttu-id="0d18a-110">たとえば、パッケージは、データ値を持つ変数を読み込む SQL 実行タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-110">For example, a package can run an Execute SQL task that loads a variable with data values.</span></span>  
  
-   <span data-ttu-id="0d18a-111">データ値を持つ変数を読み込み、それらを使用して WHERE 句の検索条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-111">Loading variables with data values and then using them to specify a search condition in a WHERE clause.</span></span> <span data-ttu-id="0d18a-112">たとえば、SQL 実行タスク内の Transact-SQL ステートメントによって使用される変数の値をスクリプト タスク内のスクリプトで更新できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-112">For example, the script in a Script task can update the value of a variable that is used by a Transact-SQL statement in an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="0d18a-113">整数値を持つ変数を読み込み、その値を使用してパッケージ制御フロー内のループを制御します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-113">Loading a variable with an integer and then using the value to control looping within a package control flow.</span></span> <span data-ttu-id="0d18a-114">たとえば、For ループ コンテナーの評価式内の変数を使用して繰り返しを制御できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-114">For example, you can use a variable in the evaluation expression of a For Loop container to control iteration.</span></span>  
  
-   <span data-ttu-id="0d18a-115">実行時に Transact-SQL ステートメントのパラメーター値を作成します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-115">Populating parameter values for Transact-SQL statements at run time.</span></span> <span data-ttu-id="0d18a-116">たとえば、パッケージは SQL 実行タスクを実行し、変数を使用して Transact-SQL ステートメント内のパラメーターを動的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-116">For example, a package can run an Execute SQL task and then use variables to dynamically set the parameters in a Transact-SQL statement.</span></span>  
  
-   <span data-ttu-id="0d18a-117">変数値が含まれる式を構築します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-117">Building expressions that include variable values.</span></span> <span data-ttu-id="0d18a-118">たとえば、派生列の変換は、変数値に列の値を乗算することによって取得した結果を使用して、列の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-118">For example, the Derived Column transformation can populate a column with the result obtained by multiplying a variable value by a column value.</span></span>  
  
## <a name="system-and-user-defined-variables"></a><span data-ttu-id="0d18a-119">システム変数とユーザー定義変数</span><span class="sxs-lookup"><span data-stu-id="0d18a-119">System and User-Defined Variables</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0d18a-120">では、ユーザー定義変数とシステム変数の、2 種類の変数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0d18a-120">supports two types of variables: user-defined variables and system variables.</span></span> <span data-ttu-id="0d18a-121">ユーザー定義変数とはパッケージの開発者によって定義された変数で、システム変数とは [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]によって定義された変数です。</span><span class="sxs-lookup"><span data-stu-id="0d18a-121">User-defined variables are defined by package developers, and system variables are defined by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="0d18a-122">ユーザー定義変数は、パッケージで必要な数だけ作成できますが、システム変数は追加作成できません。</span><span class="sxs-lookup"><span data-stu-id="0d18a-122">You can create as many user-defined variables as a package requires, but you cannot create additional system variables.</span></span>  
  
 <span data-ttu-id="0d18a-123">変数 (システム変数とユーザー定義変数) はすべて、SQL 実行タスクが使用するパラメーター バインドで使用して、SQL ステートメントのパラメーターに変数をマップできます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-123">All variables-system and user-defined-can be used in the parameter bindings that the Execute SQL task uses to map variables to parameters in SQL statements.</span></span> <span data-ttu-id="0d18a-124">詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d18a-124">For more information, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d18a-125">ユーザー定義変数とシステム変数の名前では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-125">The names of user-defined and system variables are case sensitive.</span></span>  
  
 <span data-ttu-id="0d18a-126">パッケージ、Foreach ループ コンテナー、For ループ コンテナー、シーケンス コンテナー、タスク、およびイベント ハンドラーの、すべての種類の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンテナーに対してユーザー定義変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-126">You can create user-defined variables for all [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types: packages, Foreach Loop containers, For Loop containers, Sequence containers, tasks, and event handlers.</span></span> <span data-ttu-id="0d18a-127">ユーザー定義変数は、コンテナーの変数のコレクションのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="0d18a-127">User-defined variables are members of the Variables collection of the container.</span></span>  
  
 <span data-ttu-id="0d18a-128">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用してパッケージを作成すると、変数のコレクションのメンバーは、 **デザイナーの** [パッケージ エクスプローラー] **タブ上の** [変数] [!INCLUDE[ssIS](../includes/ssis-md.md)] フォルダー内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-128">If you create the package using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, you can see the members of the Variables collections in the **Variables** folders on the **Package Explorer** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="0d18a-129">このフォルダーには、ユーザー定義変数とシステム変数が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-129">The folders list user-defined variables and system variables.</span></span>  
  
 <span data-ttu-id="0d18a-130">ユーザー定義変数は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-130">You can configure user-defined variables in the following ways:</span></span>  
  
-   <span data-ttu-id="0d18a-131">変数の名前と説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-131">Provide a name and description for the variable.</span></span>  
  
-   <span data-ttu-id="0d18a-132">変数の名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-132">Specify a namespace for the variable.</span></span>  
  
-   <span data-ttu-id="0d18a-133">変数値が変更されたときに、変数がイベントを起動するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-133">Indicate whether the variable raises an event when its value changes.</span></span>  
  
-   <span data-ttu-id="0d18a-134">変数は読み取り専用か、読み取り/書き込み可能かを示します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-134">Indicate whether the variable is read-only or read/write.</span></span>  
  
-   <span data-ttu-id="0d18a-135">式の評価結果を使用して、変数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-135">Use the evaluation result of an expression to set the variable value.</span></span>  
  
-   <span data-ttu-id="0d18a-136">パッケージ、またはタスクなどのパッケージ オブジェクトのスコープ内に、変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-136">Create the variable in the scope of the package or a package object such as a task.</span></span>  
  
-   <span data-ttu-id="0d18a-137">変数の値とデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-137">Specify the value and data type of the variable.</span></span>  
  
 <span data-ttu-id="0d18a-138">システム変数で構成可能なオプションは、変数値が変更されたときにイベントを起動するかどうかを指定するオプションのみです。</span><span class="sxs-lookup"><span data-stu-id="0d18a-138">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="0d18a-139">コンテナーの種類ごとに、異なるセットのシステム変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-139">A different set of system variables is available for different container types.</span></span> <span data-ttu-id="0d18a-140">パッケージとパッケージ要素が使用するシステム変数の詳細については、「 [システム変数](system-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d18a-140">For more information about the system variables used by packages and their elements, see [System Variables](system-variables.md).</span></span>  
  
 <span data-ttu-id="0d18a-141">変数の実際的な使用シナリオの詳細については、「 [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d18a-141">For more information about real-life use scenarios for variables, see [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
## <a name="variable-properties"></a><span data-ttu-id="0d18a-142">変数のプロパティ</span><span class="sxs-lookup"><span data-stu-id="0d18a-142">Variable Properties</span></span>  
 <span data-ttu-id="0d18a-143">**[変数]** ウィンドウまたは **[プロパティ]** ウィンドウで、次のプロパティを設定してユーザー定義変数を構成できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-143">You can configure user-defined variables by setting the following properties in either the **Variables** window or the **Properties** window.</span></span> <span data-ttu-id="0d18a-144">一部のプロパティは [プロパティ] ウィンドウでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-144">Certain properties are available only in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d18a-145">システム変数で構成可能なオプションは、変数値が変更されたときにイベントを起動するかどうかを指定するオプションのみです。</span><span class="sxs-lookup"><span data-stu-id="0d18a-145">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="0d18a-146">説明</span><span class="sxs-lookup"><span data-stu-id="0d18a-146">Description</span></span>  
 <span data-ttu-id="0d18a-147">変数の説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-147">Specifies the description of the variable.</span></span>  
  
 <span data-ttu-id="0d18a-148">EvaluateAsExpression</span><span class="sxs-lookup"><span data-stu-id="0d18a-148">EvaluateAsExpression</span></span>  
 <span data-ttu-id="0d18a-149">プロパティがに設定されている場合は、指定された式を使用して `True` 変数の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-149">When the property is set to `True`, the expression provided is used to set the variable value.</span></span>  
  
 <span data-ttu-id="0d18a-150">式</span><span class="sxs-lookup"><span data-stu-id="0d18a-150">Expression</span></span>  
 <span data-ttu-id="0d18a-151">変数に割り当てられる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-151">Specifies the expression that is assigned to the variable.</span></span>  
  
 <span data-ttu-id="0d18a-152">名前</span><span class="sxs-lookup"><span data-stu-id="0d18a-152">Name</span></span>  
 <span data-ttu-id="0d18a-153">変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-153">Specifies the variable name.</span></span>  
  
 <span data-ttu-id="0d18a-154">名前空間</span><span class="sxs-lookup"><span data-stu-id="0d18a-154">Namespace</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0d18a-155">には、**User** および **System** という 2 つの名前空間が用意されています。</span><span class="sxs-lookup"><span data-stu-id="0d18a-155">provides two namespaces, **User** and **System**.</span></span> <span data-ttu-id="0d18a-156">既定では、カスタム変数は **User** 名前空間に属し、システム変数は **System** 名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-156">By default, custom variables are in the **User** namespace, and system variables are in the **System** namespace.</span></span> <span data-ttu-id="0d18a-157">ユーザー定義変数用に追加の名前空間を作成し、 **User** 名前空間の名前を変更することはできますが、 **System** 名前空間の名前を変更したり、変数を **System** 名前空間に追加したり、システム変数を別の名前空間に割り当てたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0d18a-157">You can create additional namespaces for user-defined variables and change the name of the **User** namespace, but you cannot change the name of the **System** namespace, add variables to the **System** namespace, or assign system variables to a different namespace.</span></span>  
  
 <span data-ttu-id="0d18a-158">RaiseChangedEvent</span><span class="sxs-lookup"><span data-stu-id="0d18a-158">RaiseChangedEvent</span></span>  
 <span data-ttu-id="0d18a-159">このプロパティを `True` に設定すると、変数の値が変更された場合に `OnVariableValueChanged` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-159">When the property is set to `True`, the `OnVariableValueChanged` event is raised when the variable changes value.</span></span>  
  
 <span data-ttu-id="0d18a-160">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="0d18a-160">ReadOnly</span></span>  
 <span data-ttu-id="0d18a-161">このプロパティを `False` に設定すると、変数は読み取り/書き込み用となります。</span><span class="sxs-lookup"><span data-stu-id="0d18a-161">When the property is set to `False`, the variable is read\write.</span></span>  
  
 <span data-ttu-id="0d18a-162">Scope</span><span class="sxs-lookup"><span data-stu-id="0d18a-162">Scope</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="0d18a-163">**[変数]** ウィンドウの **[変数の移動]** をクリックすることによってしか、このプロパティの設定は変更できません。</span><span class="sxs-lookup"><span data-stu-id="0d18a-163">You can change this property setting only by clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="0d18a-164">変数は、パッケージのスコープ内、またはパッケージ内のコンテナー、タスク、またはイベント ハンドラーのスコープ内で作成されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-164">A variable is created within the scope of a package or within the scope of a container, task, or event handler in the package.</span></span> <span data-ttu-id="0d18a-165">パッケージ コンテナーは、コンテナー階層の最上層にあるため、パッケージ スコープを持つ変数はグローバル変数と同じように機能し、パッケージ内のすべてのコンテナーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-165">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables and can be used by all containers in the package.</span></span> <span data-ttu-id="0d18a-166">同様に、For ループ コンテナーなどのコンテナーのスコープ内で定義された変数は、For ループ コンテナー内のすべてのタスクまたはコンテナーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-166">Similarly, variables defined within the scope of a container such as a For Loop container can be used by all tasks or containers within the For Loop container.</span></span>  
  
 <span data-ttu-id="0d18a-167">パッケージでパッケージ実行タスクを使用して他のパッケージを実行する場合、呼び出し元のパッケージのスコープまたはパッケージ実行タスクで定義された変数は、構成の種類で親パッケージ変数を使用することにより、呼び出し先のパッケージで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-167">If a package runs other packages by using the Execute Package task, the variables defined in the scope of the calling package or the Execute Package task can be made available to the called package by using the Parent Package Variable configuration type.</span></span> <span data-ttu-id="0d18a-168">詳細については、「 [パッケージ構成](../../2014/integration-services/package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d18a-168">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
 <span data-ttu-id="0d18a-169">[IncludeInDebugDump]</span><span class="sxs-lookup"><span data-stu-id="0d18a-169">IncludeInDebugDump</span></span>  
 <span data-ttu-id="0d18a-170">変数値がデバッグ ダンプ ファイルに含まれるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-170">Indicate whether the variable value is included in the debug dump files.</span></span>  
  
 <span data-ttu-id="0d18a-171">ユーザー定義変数およびシステム変数の場合、 **[inclueindebugdump]** オプションの既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="0d18a-171">For user-defined variables and system variables, the default value for the **InclueInDebugDump** option is `true`.</span></span>  
  
 <span data-ttu-id="0d18a-172">ただし、ユーザー定義変数の場合、次の**IncludeInDebugDump** `false` 条件が満たされると、システムは [includeindebugdump] オプションをにリセットします。</span><span class="sxs-lookup"><span data-stu-id="0d18a-172">However, for user-defined variables, the system resets the **IncludeInDebugDump** option to `false` when the following conditions are met:</span></span>  
  
-   <span data-ttu-id="0d18a-173">**EvaluateAsExpression** variable プロパティがに設定されている場合、 `true` システムは **[includeindebugdump]** オプションをにリセットし `false` ます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-173">If the **EvaluateAsExpression** variable property is set to `true`, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
     <span data-ttu-id="0d18a-174">式のテキストを変数値としてデバッグダンプファイルに含めるには、 **[includeindebugdump]** オプションをに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-174">To include the text of the expression as the variable value in the debug dump files, set the **IncludeInDebugDump** option to `true`.</span></span>  
  
-   <span data-ttu-id="0d18a-175">変数のデータ型が文字列に変更されると、システムは **[includeindebugdump]** オプションをにリセットし `false` ます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-175">If the variable data type is changed to a string, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
 <span data-ttu-id="0d18a-176">システムによって **[includeindebugdump]** オプションがにリセットされると `false` 、ユーザーが選択した値が上書きされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0d18a-176">When the system resets the **IncludeInDebugDump** option to `false`, this might override the value selected by the user.</span></span>  
  
 <span data-ttu-id="0d18a-177">値</span><span class="sxs-lookup"><span data-stu-id="0d18a-177">Value</span></span>  
 <span data-ttu-id="0d18a-178">ユーザー定義変数の値には、リテラルまたは式を設定できます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-178">The value of a user-defined variable can be a literal or an expression.</span></span> <span data-ttu-id="0d18a-179">変数には、変数値および変数のデータ型を設定するオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d18a-179">A variable includes options for setting the variable value and the data type of the value.</span></span> <span data-ttu-id="0d18a-180">この 2 つのプロパティには互換性が必要です。たとえば、文字列の値を整数データ型に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d18a-180">The two properties must be compatible: for example, the use of a string value together with an integer data type is not valid.</span></span>  
  
 <span data-ttu-id="0d18a-181">変数を式として評価するように構成した場合は、式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d18a-181">If the variable is configured to evaluate as an expression, you must provide an expression.</span></span> <span data-ttu-id="0d18a-182">式は実行時に評価され、変数は評価結果に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-182">At run time, the expression is evaluated, and the variable is set to the evaluation result.</span></span> <span data-ttu-id="0d18a-183">たとえば、変数が式 `DATEPART("month", GETDATE())` を使用している場合、変数の値は、現在の日付の月と等しい数値になります。</span><span class="sxs-lookup"><span data-stu-id="0d18a-183">For example, if a variable uses the expression `DATEPART("month", GETDATE())` the value of the variable is the number equivalent of the month for the current date.</span></span> <span data-ttu-id="0d18a-184">式は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] 式の構文文法を使用する、有効な式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d18a-184">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../includes/ssis-md.md)] expression grammar syntax.</span></span> <span data-ttu-id="0d18a-185">変数に式を使用する場合、リテラルおよび式文法が提供する演算子と関数も使用できますが、パッケージ内のデータ フローの列は参照できません。</span><span class="sxs-lookup"><span data-stu-id="0d18a-185">When an expression is used with variables, the expression can use literals and the operators and functions that the expression grammar provides, but the expression cannot reference the columns from a data flow in the package.</span></span> <span data-ttu-id="0d18a-186">式の最大長は 4,000 文字です。</span><span class="sxs-lookup"><span data-stu-id="0d18a-186">The maximum length of an expression is 4000 characters.</span></span> <span data-ttu-id="0d18a-187">詳細については、「 [Integration Services (SSIS) 式](expressions/integration-services-ssis-expressions.md)に評価されるまでそのワークフローを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-187">For more information, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="0d18a-188">ValueType</span><span class="sxs-lookup"><span data-stu-id="0d18a-188">ValueType</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="0d18a-189">このプロパティの値は **[変数]** ウィンドウの **[データ型]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d18a-189">The property value appears in the **Data type** column in the **Variables** window.</span></span>  
  
 <span data-ttu-id="0d18a-190">変数の値のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-190">Specifies the data type of the variable value.</span></span>  
  
## <a name="configuring-variables"></a><span data-ttu-id="0d18a-191">変数の構成</span><span class="sxs-lookup"><span data-stu-id="0d18a-191">Configuring Variables</span></span>  
 <span data-ttu-id="0d18a-192">プロパティを設定するには [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="0d18a-192">You can set properties through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0d18a-193">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[変数] ウィンドウ](../../2014/integration-services/variables-window.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d18a-193">For more information about the properties that you can set in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, see [Variables Window](../../2014/integration-services/variables-window.md).</span></span>  
  
 <span data-ttu-id="0d18a-194">変数のプロパティ、およびプログラムによるこれらのプロパティの設定方法の詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.Variable>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d18a-194">To learn more about variable properties, and for more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0d18a-195">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0d18a-195">Related Tasks</span></span>  
 [<span data-ttu-id="0d18a-196">パッケージ内のユーザー定義変数のスコープの追加、削除、変更</span><span class="sxs-lookup"><span data-stu-id="0d18a-196">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
 [<span data-ttu-id="0d18a-197">ユーザー定義変数のプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="0d18a-197">Set the Properties of a User-Defined Variable</span></span>](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
 [<span data-ttu-id="0d18a-198">子パッケージでの変数とパラメーターの値の使用</span><span class="sxs-lookup"><span data-stu-id="0d18a-198">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [<span data-ttu-id="0d18a-199">クエリ パラメーターをデータ フロー コンポーネントの変数にマップする</span><span class="sxs-lookup"><span data-stu-id="0d18a-199">Map Query Parameters to Variables in a Data Flow Component</span></span>](data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  
