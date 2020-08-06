---
title: ユーザー定義変数 | のプロパティを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf53be469e3d377f7efb379f78e85e31b26767b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742377"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a><span data-ttu-id="a732d-102">ユーザー定義変数のプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="a732d-102">Set the Properties of a User-Defined Variable</span></span>
  <span data-ttu-id="a732d-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]でユーザー定義変数のプロパティを設定するには、次の機能のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="a732d-103">To set the properties of a user-defined variable in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can use one of the following features:</span></span>  
  
-   <span data-ttu-id="a732d-104">[変数] ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="a732d-104">Variables window.</span></span>  
  
-   <span data-ttu-id="a732d-105">[プロパティ] ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="a732d-105">Properties window.</span></span> <span data-ttu-id="a732d-106">**[プロパティ]** ウィンドウには、 **[変数]** ウィンドウでは使用できない変数 (Description、EvaluateAsExpression、Expression、ReadOnly、ValueType、および IncludeInDebugDump) を構成するためのプロパティが一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="a732d-106">The **Properties** window lists properties for configuring variables that are not available in the **Variables** window: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType, and IncludeInDebugDump.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="a732d-107">には、RaiseChangedEvent プロパティを除き、更新できないプロパティを持つ一連のシステム変数もあります。</span><span class="sxs-lookup"><span data-stu-id="a732d-107">also provides a set of system variables whose properties cannot be updated, with the exception of the RaiseChangedEvent property.</span></span>  
  
 <span data-ttu-id="a732d-108">**変数への式の設定**</span><span class="sxs-lookup"><span data-stu-id="a732d-108">**Setting Expressions on Variables**</span></span>  
  
 <span data-ttu-id="a732d-109">**[プロパティ]** ウィンドウを使用してユーザー定義変数に式を設定する場合:</span><span class="sxs-lookup"><span data-stu-id="a732d-109">When you use the **Properties** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="a732d-110">変数の値は、Value プロパティまたは Expression プロパティによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="a732d-110">The value of a variable can be set by the Value or the Expression property.</span></span> <span data-ttu-id="a732d-111">既定では、EvaluateAsExpression プロパティはに設定され、 `False` 変数の値は value プロパティによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="a732d-111">By default, the EvaluateAsExpression property is set to `False` and the value of the variable is set by the Value property.</span></span> <span data-ttu-id="a732d-112">式を使用して値を設定するには、最初に EvaluateAsExpression をに設定し `True` てから、[式] プロパティに式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a732d-112">To use an expression to set the value, you must first set EvaluateAsExpression to `True`, and then provide an expression in the Expression property.</span></span> <span data-ttu-id="a732d-113">Value プロパティには、自動的に式の評価結果が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a732d-113">The Value property is automatically set to the evaluation result of the expression.</span></span>  
  
-   <span data-ttu-id="a732d-114">ValueType プロパティには、Value プロパティの値のデータ型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a732d-114">The ValueType property contains the data type of the value in the Value property.</span></span> <span data-ttu-id="a732d-115">Value が式によって設定される場合、ValueType は、式の評価結果と互換性があるデータ型に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="a732d-115">When Value is set by an expression, ValueType is automatically updated to a data type that is compatible with the evaluation result of the expression.</span></span> <span data-ttu-id="a732d-116">たとえば、値に0が含まれ、ValueType プロパティに**Int32**が含まれている場合、EXPRESSION を GETDATE () に設定すると、value には現在の日付と時刻が含まれ、ValueType はに設定され `DateTime` ます。</span><span class="sxs-lookup"><span data-stu-id="a732d-116">For example, if Value contains 0 and ValueType property contains **Int32** and you then set Expression to GETDATE(), Value contains the current date and time and ValueType is set to `DateTime`.</span></span>  
  
-   <span data-ttu-id="a732d-117">変数の **[プロパティ]** ウィンドウからは **[式ビルダー]** ダイアログ ボックスを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a732d-117">The **Properties** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="a732d-118">このツールを使用すると、式の作成、検証、および評価を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a732d-118">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="a732d-119">詳しくは、「[式ビルダー](expressions/expression-builder.md)」と「[Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a732d-119">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="a732d-120">**[変数]** ウィンドウを使用してユーザー定義変数に式を設定する場合:</span><span class="sxs-lookup"><span data-stu-id="a732d-120">When you use the **Variables** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="a732d-121">式を使用して変数の値を設定するには、まず、変数のデータ型が式の評価結果と互換性があることを確認してから `Expression` 、[**変数**] ウィンドウの列に式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a732d-121">To use an expression to set the variable value, first confirm that the variable data type is compatible with the evaluation result of the expression and then provide an expression in the `Expression` column of the **Variables** window.</span></span> <span data-ttu-id="a732d-122">[**プロパティ**] ウィンドウの EvaluateAsExpression プロパティが自動的にに設定され `True` ます。</span><span class="sxs-lookup"><span data-stu-id="a732d-122">The EvaluateAsExpression property in the **Properties** window is automatically set to `True`.</span></span>  
  
-   <span data-ttu-id="a732d-123">変数に式を割り当てると、変数の横に特別なアイコン マーカーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a732d-123">When you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="a732d-124">この特別なアイコン マーカーは、式が設定されている接続マネージャーおよびタスクの横にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="a732d-124">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
-   <span data-ttu-id="a732d-125">変数の **[変数]** ウィンドウからは **[式ビルダー]** ダイアログ ボックスを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a732d-125">The **Variables** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="a732d-126">このツールを使用すると、式の作成、検証、および評価を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a732d-126">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="a732d-127">詳しくは、「[式ビルダー](expressions/expression-builder.md)」と「[Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a732d-127">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="a732d-128">[**変数**] ウィンドウと [**プロパティ**] ウィンドウの両方で、変数に式を割り当て、がに設定されている場合は、 `EvaluateAsExpression` 変数の `True` データ型を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="a732d-128">In both the **Variables** and **Properties** window, if you assign an expression to the variable, and `EvaluateAsExpression` is set to `True`, you cannot change the variable data type.</span></span>  
  
 <span data-ttu-id="a732d-129">**Namespace プロパティと Name プロパティの設定**</span><span class="sxs-lookup"><span data-stu-id="a732d-129">**Setting the Namespace and Name Properties**</span></span>  
  
 <span data-ttu-id="a732d-130">`Name` プロパティと `Namespace` プロパティの値の最初の文字は、Unicode Standard 2.0 に定義されているアルファベット文字か、アンダースコア (_) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a732d-130">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="a732d-131">2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (\_) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a732d-131">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="using-the-variables-window-to-set-properties"></a><span data-ttu-id="a732d-132">[変数] ウィンドウを使用したプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="a732d-132">Using the Variables Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a><span data-ttu-id="a732d-133">[変数] ウィンドウを使用して変数のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="a732d-133">To set the properties of a variable by using the Variables window</span></span>  
  
1.  <span data-ttu-id="a732d-134">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a732d-134">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a732d-135">ソリューション エクスプローラーで、パッケージを右クリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a732d-135">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a732d-136">**[SSIS]** メニューの **[変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a732d-136">On the **SSIS** menu, click **Variables**.</span></span>  
  
     <span data-ttu-id="a732d-137">必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[変数]** ウィンドウを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="a732d-137">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="a732d-138">必要に応じて、 **[変数]** ウィンドウで **[グリッドのオプション]** をクリックして、 **[変数]** ウィンドウに表示する列を選択したり、変数の一覧に適用するフィルターを選択したりします。</span><span class="sxs-lookup"><span data-stu-id="a732d-138">Optionally, in the **Variables** window click **Grid Options**, and then select the columns to appear in the **Variables** window and select the filters to apply to the list of variables.</span></span>  
  
5.  <span data-ttu-id="a732d-139">一覧で変数を選択し、、、 `Name` **データ型**、 `Value` 、、 `Namespace` **Raise Change イベント**、 **Description、** および columns の値を更新し `Expression` ます。</span><span class="sxs-lookup"><span data-stu-id="a732d-139">Select the variable in the list, and then update values in the `Name`, **Data Type**, `Value`, `Namespace`, **Raise Change Event**, **Description,** and `Expression` columns.</span></span>  
  
6.  <span data-ttu-id="a732d-140">一覧で変数を選択し、 **[変数の移動]** をクリックしてスコープを変更します。</span><span class="sxs-lookup"><span data-stu-id="a732d-140">Select the variable in the list, and then click **Move Variable** to change the scope.</span></span>  
  
7.  <span data-ttu-id="a732d-141">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a732d-141">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="using-the-properties-window-to-set-properties"></a><span data-ttu-id="a732d-142">[プロパティ] ウィンドウを使用したプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="a732d-142">Using the Properties Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a><span data-ttu-id="a732d-143">[プロパティ] ウィンドウを使用して変数のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="a732d-143">To set the properties of a variable by using the Properties window</span></span>  
  
1.  <span data-ttu-id="a732d-144">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a732d-144">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a732d-145">ソリューション エクスプローラーで、パッケージを右クリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a732d-145">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a732d-146">**[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a732d-146">On the **View** menu, click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="a732d-147">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、 **[パッケージ エクスプローラー]** タブをクリックし、[パッケージ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a732d-147">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Package Explorer** tab and expand the Package node.</span></span>  
  
5.  <span data-ttu-id="a732d-148">パッケージの適用範囲の変数を変更するには、[変数] ノードを展開します。それ以外の場合は、変更する変数が含まれている [変数] ノードが表示されるまで、[イベント ハンドラー] または [実行可能ファイル] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a732d-148">To modify variables with package scope, expand the Variables node; otherwise, expand the Event Handlers or Executables nodes until you locate the Variables node that contains the variable that you want to modify.</span></span>  
  
6.  <span data-ttu-id="a732d-149">変更するプロパティの変数をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a732d-149">Click the variable whose properties you want to modify.</span></span>  
  
7.  <span data-ttu-id="a732d-150">**[プロパティ]** ウィンドウで、読み取り/書き込みの変数プロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="a732d-150">In the **Properties** window, update the read/write variable properties.</span></span> <span data-ttu-id="a732d-151">ユーザー定義変数の場合は読み取り/読み取りのみのプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="a732d-151">Some properties are read/read only for user-defined variables.</span></span>  
  
     <span data-ttu-id="a732d-152">プロパティの詳細については、「[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a732d-152">For more information about the properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
8.  <span data-ttu-id="a732d-153">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a732d-153">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a732d-154">参照</span><span class="sxs-lookup"><span data-stu-id="a732d-154">See Also</span></span>  
 <span data-ttu-id="a732d-155">[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="a732d-155">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="a732d-156">[パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="a732d-156">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="a732d-157">パッケージ内のユーザー定義変数のスコープの追加、削除、変更</span><span class="sxs-lookup"><span data-stu-id="a732d-157">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
