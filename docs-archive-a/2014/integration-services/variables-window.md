---
title: '[変数] ウィンドウ | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variables.f1
helpviewer_keywords:
- Variables Window dialog box
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffd6da67386291c14ebf588da9a1cf8f399214b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642860"
---
# <a name="variables-window"></a><span data-ttu-id="048dc-102">[変数] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="048dc-102">Variables Window</span></span>
  <span data-ttu-id="048dc-103">**[変数]** ウィンドウを使用すると、ユーザー定義変数を作成、変更し、システム変数を表示できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-103">Use the **Variables** window to create and modify user-defined variables and view system variables.</span></span>  
  
 <span data-ttu-id="048dc-104">既定では、 **[変数]** ウィンドウは **の SSIS デザイナーの** [接続マネージャー] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]領域の下にあります。</span><span class="sxs-lookup"><span data-stu-id="048dc-104">By default, the **Variables** window is located below the **Connection Managers** area in the SSIS Designer, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="048dc-105">**[変数]** ウィンドウが表示されない場合は、 **[SSIS]** メニューの **[変数]** をクリックして、ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-105">If you don't see the **Variables** window, click **Variables** on the **SSIS** menu to display the window.</span></span>  
  
 <span data-ttu-id="048dc-106">必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[変数]** ウィンドウを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="048dc-106">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="048dc-107">`Name` プロパティと `Namespace` プロパティの値の最初の文字は、Unicode Standard 2.0 に定義されているアルファベット文字か、アンダースコア (_) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="048dc-107">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="048dc-108">2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (\_) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-108">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="options"></a><span data-ttu-id="048dc-109">オプション</span><span class="sxs-lookup"><span data-stu-id="048dc-109">Options</span></span>  
 <span data-ttu-id="048dc-110">**変数の追加**</span><span class="sxs-lookup"><span data-stu-id="048dc-110">**Add Variable**</span></span>  
 <span data-ttu-id="048dc-111">ユーザー定義変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="048dc-111">Add a user-defined variable.</span></span>  
  
 <span data-ttu-id="048dc-112">**変数の移動**</span><span class="sxs-lookup"><span data-stu-id="048dc-112">**Move Variable**</span></span>  
 <span data-ttu-id="048dc-113">一覧で変数をクリックし、 **[変数の移動]** をクリックして変数のスコープを変更します。</span><span class="sxs-lookup"><span data-stu-id="048dc-113">Click a variable in the list, and then click **Move Variable** to change the variable scope.</span></span> <span data-ttu-id="048dc-114">**[新しいスコープの選択]** ダイアログ ボックスで、パッケージまたはパッケージ内のコンテナー、タスク、またはイベント ハンドラーを選択して、変数のスコープを変更します。</span><span class="sxs-lookup"><span data-stu-id="048dc-114">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
 <span data-ttu-id="048dc-115">変数のスコープの詳細については、「 [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)領域の下にあります。</span><span class="sxs-lookup"><span data-stu-id="048dc-115">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="048dc-116">**変数の削除**</span><span class="sxs-lookup"><span data-stu-id="048dc-116">**Delete Variable**</span></span>  
 <span data-ttu-id="048dc-117">変数を一覧から選択し、 **[変数の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-117">Select a variable from the list, and then click **Delete Variable**.</span></span>  
  
 <span data-ttu-id="048dc-118">**グリッドのオプション**</span><span class="sxs-lookup"><span data-stu-id="048dc-118">**Grid Options**</span></span>  
 <span data-ttu-id="048dc-119">クリックすると **[可変グリッドのオプション]** ダイアログ ボックスが開きます。このダイアログ ボックスで、列の選択を変更したり、 **[変数]** ウィンドウにフィルターを適用したりできます。</span><span class="sxs-lookup"><span data-stu-id="048dc-119">Click to open the **Variable Grid Options** dialog box where you can change the column selection and apply filters to the **Variables** window.</span></span> <span data-ttu-id="048dc-120">詳細については、「 [可変グリッドのオプション](../../2014/integration-services/variable-grid-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="048dc-120">For more information, see [Variable Grid Options](../../2014/integration-services/variable-grid-options.md).</span></span>  
  
 `Name`  
 <span data-ttu-id="048dc-121">変数名を表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-121">View the variable name.</span></span> <span data-ttu-id="048dc-122">ユーザー定義変数の名前を更新できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-122">You can update the name for user-defined variables.</span></span>  
  
 <span data-ttu-id="048dc-123">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="048dc-123">**Scope**</span></span>  
 <span data-ttu-id="048dc-124">変数のスコープを表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-124">View the scope of the variable.</span></span> <span data-ttu-id="048dc-125">変数には、パッケージ全体のスコープまたはコンテナーやタスクのスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="048dc-125">A variable has either the scope of the entire package, or the scope of a container or task.</span></span> <span data-ttu-id="048dc-126">変数のスコープは、変数の値の読み取りや設定を必要とする他のタスクやコンポーネントからアクセスできるように十分な範囲を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="048dc-126">The scope of the variable must be sufficient so that the variable is visible to any other tasks or components that need to read or set its value.</span></span>  
  
 <span data-ttu-id="048dc-127">スコープを変更するには、変数をクリックして **[変数]** ウィンドウの **[変数の移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-127">You can change the scope by clicking the variable and then clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="048dc-128">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="048dc-128">**Data Type**</span></span>  
 <span data-ttu-id="048dc-129">変数のデータ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="048dc-129">View the data type of the variable.</span></span> <span data-ttu-id="048dc-130">一覧からユーザー定義変数のデータ型を選択できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-130">You can select a data type from the list for user-defined variables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="048dc-131">変数に式を割り当てる場合は、データ型を変更できません。</span><span class="sxs-lookup"><span data-stu-id="048dc-131">If you assign an expression to the variable, you cannot change the data type.</span></span>  
  
 <span data-ttu-id="048dc-132">**Value**</span><span class="sxs-lookup"><span data-stu-id="048dc-132">**Value**</span></span>  
 <span data-ttu-id="048dc-133">変数の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-133">View the variable value.</span></span> <span data-ttu-id="048dc-134">ユーザー定義変数の値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-134">You can update the value for user-defined variables.</span></span> <span data-ttu-id="048dc-135">この値は、リテラルまたは式にすることができます。また、複数行の文字列にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="048dc-135">This value can be a literal or an expression, and the value can be a multi-line string.</span></span> <span data-ttu-id="048dc-136">変数に式を割り当てるには、 **[変数]** ウィンドウの **[式]** 列の横にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-136">To assign an expression to the variable, click the ellipse button that is next to the **Expression** column in the **Variables** window.</span></span>  
  
 `Namespace`  
 <span data-ttu-id="048dc-137">名前空間名を表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-137">View the namespace name.</span></span> <span data-ttu-id="048dc-138">ユーザー定義変数は、最初に**ユーザー**名前空間で作成されますが、フィールドの名前空間の名前を変更することもでき `Namespace` ます。</span><span class="sxs-lookup"><span data-stu-id="048dc-138">User-defined variables are initially created in the **User** namespace, but you can change the namespace name in the `Namespace` field.</span></span> <span data-ttu-id="048dc-139">この列を表示するには、 **[グリッドのオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-139">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="048dc-140">**[Raise Change Event]**</span><span class="sxs-lookup"><span data-stu-id="048dc-140">**Raise Change Event**</span></span>  
 <span data-ttu-id="048dc-141">値を変更した場合に `OnVariableValueChanged` イベントを発生させるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-141">Indicate whether to raise the `OnVariableValueChanged` event when a value changes.</span></span> <span data-ttu-id="048dc-142">ユーザー定義変数およびシステム変数の値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-142">You can update the value for user-defined and system variables.</span></span> <span data-ttu-id="048dc-143">既定では、 **[変数]** ウィンドウにこの列は表示されません。</span><span class="sxs-lookup"><span data-stu-id="048dc-143">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="048dc-144">この列を表示するには、 **[グリッドのオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-144">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="048dc-145">**説明**</span><span class="sxs-lookup"><span data-stu-id="048dc-145">**Description**</span></span>  
 <span data-ttu-id="048dc-146">変数の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-146">View the variable description.</span></span> <span data-ttu-id="048dc-147">ユーザー定義変数の説明を変更できます。</span><span class="sxs-lookup"><span data-stu-id="048dc-147">You can change the description for user-defined variables.</span></span> <span data-ttu-id="048dc-148">既定では、 **[変数]** ウィンドウにこの列は表示されません。</span><span class="sxs-lookup"><span data-stu-id="048dc-148">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="048dc-149">この列を表示するには、 **[グリッドのオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-149">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="048dc-150">**[式]**</span><span class="sxs-lookup"><span data-stu-id="048dc-150">**Expression**</span></span>  
 <span data-ttu-id="048dc-151">変数に割り当てられた式を表示します。</span><span class="sxs-lookup"><span data-stu-id="048dc-151">View the expression assigned to the variable.</span></span> <span data-ttu-id="048dc-152">式を割り当てるには、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="048dc-152">To assign an expression, click the ellipse button.</span></span>  
  
 <span data-ttu-id="048dc-153">変数に式を割り当てると、変数の横に特別なアイコン マーカーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="048dc-153">If you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="048dc-154">この特別なアイコン マーカーは、式が設定されている接続マネージャーおよびタスクの横にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="048dc-154">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048dc-155">参照</span><span class="sxs-lookup"><span data-stu-id="048dc-155">See Also</span></span>  
 <span data-ttu-id="048dc-156">[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="048dc-156">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="048dc-157">[パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="048dc-157">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="048dc-158">[SSIS&#41; 式の Integration Services &#40;](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="048dc-158">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="048dc-159">パッケージ実行用のダンプ ファイルを生成する</span><span class="sxs-lookup"><span data-stu-id="048dc-159">Generating Dump Files for Package Execution</span></span>](troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
