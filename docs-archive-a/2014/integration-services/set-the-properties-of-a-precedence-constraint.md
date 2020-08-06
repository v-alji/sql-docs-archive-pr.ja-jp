---
title: 優先順位制約のプロパティを設定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55b95bdb79d801156bef6198bc0f57accb5d9517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644535"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a><span data-ttu-id="c5b40-102">優先順位制約のプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="c5b40-102">Set the Properties of a Precedence Constraint</span></span>
  <span data-ttu-id="c5b40-103">優先順位制約のプロパティを設定するには、次のいずれかのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-103">To set properties on precedence constraints, you can use one of these tools:</span></span>  
  
-   <span data-ttu-id="c5b40-104">**[優先順位制約エディター]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-104">You can use the **Precedence Constraint Editor** dialog box.</span></span>  
  
-   <span data-ttu-id="c5b40-105">[プロパティ] ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-105">You can use the Properties window.</span></span> <span data-ttu-id="c5b40-106">[プロパティ] ウィンドウには、 **[優先順位制約エディター]** ダイアログ ボックスでは使用できない優先順位制約を構成するためのプロパティが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-106">The Properties window lists properties for configuring precedence constraints that are not available in the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="c5b40-107">[プロパティ] ウィンドウでは、優先順位制約の説明と名前を指定し、デザイン画面に表示する優先順位制約の注釈を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-107">In the Properties window, you can provide a description and name of the precedence constraint, and configure the annotation to display for the precedence constraint on the design surface.</span></span>  
  
 <span data-ttu-id="c5b40-108">次の手順では、これらの各ツールを使用して優先順位制約のプロパティを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-108">The following procedures describe how to set properties on precedence constraints by using each of these tools.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a><span data-ttu-id="c5b40-109">[優先順位制約エディター] を使用して優先順位制約のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="c5b40-109">To set the properties of a precedence constraint by using the Precedence Constraint Editor</span></span>  
  
1.  <span data-ttu-id="c5b40-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c5b40-111">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c5b40-112">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b40-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="c5b40-113">優先順位制約をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b40-113">Double-click the precedence constraint.</span></span>  
  
     <span data-ttu-id="c5b40-114">**[優先順位制約エディター]** が開きます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-114">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="c5b40-115">**[評価操作]** ドロップダウン リストで、評価操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-115">In the **Evaluation operation** drop-down list, select an evaluation operation.</span></span>  
  
6.  <span data-ttu-id="c5b40-116">`Value`ドロップダウンリストで、優先順位付き実行可能ファイルの実行結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-116">In the `Value` drop-down list, select the execution result of the precedence executable.</span></span>  
  
7.  <span data-ttu-id="c5b40-117">評価操作で式を使用する場合は、 `Expression` ボックスに式を入力し、[**テスト**] をクリックして式を評価します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-117">If the evaluation operation uses an expression, in the `Expression` box, type an expression, and click **Test** to evaluate the expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c5b40-118">変数名の大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-118">Variable names are case-sensitive.</span></span>  
  
8.  <span data-ttu-id="c5b40-119">複数のタスクまたはコンテナーが制約付き実行可能ファイルに接続されている場合は、[**論理 AND** ] を選択して、上記のすべての実行可能ファイルの実行結果をに評価する必要があることを指定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-119">If multiple tasks or containers are connected to the constrained executable, select **Logical AND** to specify that the execution results of all preceding executables must evaluate to `true`.</span></span> <span data-ttu-id="c5b40-120">[**論理 OR** ] を選択して、1つの実行結果のみをに評価する必要があることを指定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-120">Select **Logical OR** to specify that only one execution result must evaluate to `true`.</span></span>  
  
9. <span data-ttu-id="c5b40-121">**[OK]** をクリックし、 **[優先順位制約エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-121">Click **OK** to close the **Precedence Constraint Editor**.</span></span>  
  
10. <span data-ttu-id="c5b40-122">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b40-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a><span data-ttu-id="c5b40-123">[プロパティ] ウィンドウを使用して優先順位制約のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="c5b40-123">To set the properties of a precedence constraint by using the Properties window</span></span>  
  
1.  <span data-ttu-id="c5b40-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、変更するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to modify.</span></span>  
  
2.  <span data-ttu-id="c5b40-125">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c5b40-126">[**制御フロー** ] タブをクリックします。[**制御フロー** ] タブのデザイン画面で、優先順位制約を右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b40-126">Click the **Control Flow** tab. On the design surface of the **Control Flow** tab, right-click the precedence constraint, and then click **Properties**.</span></span> <span data-ttu-id="c5b40-127">[プロパティ] ウィンドウで、プロパティの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-127">In the Properties window, modify the property values.</span></span>  
  
4.  <span data-ttu-id="c5b40-128">**[プロパティ]** ウィンドウで、優先順位制約の次の読み取り/書き込みプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-128">In the **Properties** window, set the following read/write properties of precedence constraints:</span></span>  
  
    |<span data-ttu-id="c5b40-129">読み取り/書き込みプロパティ</span><span class="sxs-lookup"><span data-stu-id="c5b40-129">Read/write property</span></span>|<span data-ttu-id="c5b40-130">構成アクション</span><span class="sxs-lookup"><span data-stu-id="c5b40-130">Configuration action</span></span>|  
    |--------------------------|--------------------------|  
    |<span data-ttu-id="c5b40-131">説明</span><span class="sxs-lookup"><span data-stu-id="c5b40-131">Description</span></span>|<span data-ttu-id="c5b40-132">説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-132">Provide a description.</span></span>|  
    |<span data-ttu-id="c5b40-133">EvalOp</span><span class="sxs-lookup"><span data-stu-id="c5b40-133">EvalOp</span></span>|<span data-ttu-id="c5b40-134">評価操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-134">Select an evaluation operation.</span></span> <span data-ttu-id="c5b40-135">`Expression`、式、および**定数**または式のいずれかの操作が選択されている**場合は、** 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-135">If the `Expression`, **ExpressionAndConstant**, or **ExpressionOrConstant** operation is selected, you can specify an expression.</span></span>|  
    |<span data-ttu-id="c5b40-136">式</span><span class="sxs-lookup"><span data-stu-id="c5b40-136">Expression</span></span>|<span data-ttu-id="c5b40-137">評価操作に and 式が含まれる場合は、式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-137">If the evaluation operation includes and expression, provide an expression.</span></span> <span data-ttu-id="c5b40-138">式はブール値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5b40-138">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="c5b40-139">式言語の詳細については、「[Integration Services &#40;SSIS&#41; 式](expressions/integration-services-ssis-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5b40-139">For more information about the expression language, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>|  
    |<span data-ttu-id="c5b40-140">LogicalAnd</span><span class="sxs-lookup"><span data-stu-id="c5b40-140">LogicalAnd</span></span>|<span data-ttu-id="c5b40-141">`LogicalAnd`優先順位制約を他の優先順位制約と共に評価するかどうかを指定するには、複数の実行可能ファイルの前に、制約付き実行可能ファイルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c5b40-141">Set `LogicalAnd` to specify whether the precedence constraint is evaluated in concert with other precedence constraints, when multiple executables precede and are linked to the constrained executable</span></span>|  
    |<span data-ttu-id="c5b40-142">名前</span><span class="sxs-lookup"><span data-stu-id="c5b40-142">Name</span></span>|<span data-ttu-id="c5b40-143">優先順位制約の名前を更新します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-143">Update the name of the precedence constraint.</span></span>|  
    |<span data-ttu-id="c5b40-144">ShowAnnotation</span><span class="sxs-lookup"><span data-stu-id="c5b40-144">ShowAnnotation</span></span>|<span data-ttu-id="c5b40-145">使用する注釈の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-145">Specify the type of annotation to use.</span></span> <span data-ttu-id="c5b40-146">注釈を無効にするには **[Never]** 、要求時に注釈を有効にするには **[AsNeeded]** 、Name プロパティの値を使用して注釈を自動的に設定するには **[ConstraintName]** 、Description プロパティの値を使用して注釈を自動的に設定するには **[ConstraintDescription]** 、Value プロパティと Expression プロパティの値を使用して注釈を自動的に設定するには **[ConstraintOptions]** をそれぞれ選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-146">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **ConstraintName** to automatically annotate using the value of the Name property, **ConstraintDescription** to automatically annotate using the value of the Description property, and **ConstraintOptions** to automatically annotate using the values of the Value and Expression properties.</span></span>|  
    |<span data-ttu-id="c5b40-147">値</span><span class="sxs-lookup"><span data-stu-id="c5b40-147">Value</span></span>|<span data-ttu-id="c5b40-148">EvalOP プロパティで指定された評価操作に制約が含まれる場合は、制約付き実行可能ファイルの実行結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b40-148">If the evaluation operation specified in the EvalOP property includes a constraint, select the execution result of the constraining executable.</span></span>|  
  
5.  <span data-ttu-id="c5b40-149">[プロパティ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c5b40-149">Close the Properties window.</span></span>  
  
6.  <span data-ttu-id="c5b40-150">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b40-150">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b40-151">参照</span><span class="sxs-lookup"><span data-stu-id="c5b40-151">See Also</span></span>  
 <span data-ttu-id="c5b40-152">[優先順位制約](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="c5b40-152">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="c5b40-153">[既定の優先順位制約を使用してタスクとコンテナーを連結する](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="c5b40-153">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="c5b40-154">[ショートカットメニューを使用して優先順位制約の値を設定する](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="c5b40-154">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 [<span data-ttu-id="c5b40-155">優先順位制約で式を使用する</span><span class="sxs-lookup"><span data-stu-id="c5b40-155">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
