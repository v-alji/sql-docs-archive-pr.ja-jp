---
title: スクリプト コンポーネントによる同期変換の作成 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34252f1caba4e2c1b3b99788d32527a33793b6ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641737"
---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a><span data-ttu-id="3f26d-102">スクリプト コンポーネントによる同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="3f26d-102">Creating a Synchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="3f26d-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内で変換コンポーネントを使用することにより、変換元から変換先にデータが受け渡される過程で、データを修正または分析できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="3f26d-104">同期出力型の変換では、各入力列はコンポーネントを通過するたびに処理されます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="3f26d-105">非同期出力型の変換では、処理を完了するための入力列をすべて受け取ってから、処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-105">A transformation with asynchronous outputs waits until it has received all input rows to complete its processing.</span></span> <span data-ttu-id="3f26d-106">このトピックでは、同期変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-106">This topic discusses a synchronous transformation.</span></span> <span data-ttu-id="3f26d-107">非同期変換については、「[スクリプト コンポーネントによる非同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-107">For information about asynchronous transformations, see [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span> <span data-ttu-id="3f26d-108">同期コンポーネントと非同期コンポーネントの相違点の詳細については、「[同期変換と非同期変換について](../understanding-synchronous-and-asynchronous-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-108">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="3f26d-109">スクリプト コンポーネントの概要については、「[スクリプト コンポーネントによるデータ フローの拡張](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="3f26d-110">スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-110">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="3f26d-111">ただし、スクリプト コンポーネントのしくみを理解するため、「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」のセクション、特に「[同期出力型のカスタム変換コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)」を参照して、カスタム データ フロー コンポーネントを開発する場合に従う必要がある手順に目を通しておくと役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-111">However, to understand how the Script component works, you may find it useful to read the steps that you must follow in developing a custom data flow component in the section on [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-a-synchronous-transformation-component"></a><span data-ttu-id="3f26d-112">同期変換コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="3f26d-112">Getting Started with a Synchronous Transformation Component</span></span>
 <span data-ttu-id="3f26d-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [データ フロー] ペインにスクリプト コンポーネントを追加すると、 **[スクリプト コンポーネントの種類を選択]** ダイアログ ボックスが開き、[変換元]、[変換先]、[変換] コンポーネントの種類のいずれかを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-113">When you add a Script component to the Data Flow pane of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a Source, Destination, or Transformation component type.</span></span> <span data-ttu-id="3f26d-114">このダイアログ ボックスで、 **[変換]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="3f26d-115">メタデータ デザイン モードでの同期変換コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="3f26d-115">Configuring a Synchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="3f26d-116">変換コンポーネントを作成するオプションを選択したら、 **[スクリプト変換エディター]** を使用して、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="3f26d-117">詳細については、「[スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="3f26d-118">スクリプト コンポーネントのスクリプト言語を設定するには、 **[スクリプト変換エディター]** の **[スクリプト]** ページにある **[ScriptLanguage]** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-118">To set the script language for the Script component, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor**.</span></span>

> [!NOTE]
>  <span data-ttu-id="3f26d-119">スクリプト コンポーネントの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="3f26d-120">詳細については、「 [General Page](../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="3f26d-121">データ フロー変換コンポーネントには 1 つの入力があり、1 つ以上の出力がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-121">A data flow transformation component has one input, and supports one or more outputs.</span></span> <span data-ttu-id="3f26d-122">コンポーネントの入力および出力の設定は、メタデータ デザイン モードでカスタム スクリプトを記述する前に完了する必要のある手順の 1 つです。これを行うには、 **[スクリプト変換エディター]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-122">Configuring the input and outputs for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="3f26d-123">入力列の設定</span><span class="sxs-lookup"><span data-stu-id="3f26d-123">Configuring Input Columns</span></span>
 <span data-ttu-id="3f26d-124">変換コンポーネントには 1 つの入力があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-124">A transformation component has one input.</span></span>

 <span data-ttu-id="3f26d-125">**[スクリプト変換エディター]** の **[入力列]** ページには、データ フローの上流コンポーネントの出力で使用できる列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-125">On the **Input Columns** page of the **Script Transformation Editor,** the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="3f26d-126">変換する列、またはそのまま出力する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="3f26d-127">変換するすべての列の適切な場所に、読み取り/書き込みのマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="3f26d-128">**[スクリプト変換エディター]** の **[入力列]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力列] ページ&#41;](../script-transformation-editor-input-columns-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="3f26d-129">入力、出力、および出力列の設定</span><span class="sxs-lookup"><span data-stu-id="3f26d-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="3f26d-130">変換コンポーネントには、1 つ以上の出力を設定できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="3f26d-131">**[スクリプト変換エディター]** の **[入力および出力]** ページには、1 つの出力が作成されていますが、その出力に列はありません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-131">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you can see that a single output has been created, but the output has no columns.</span></span> <span data-ttu-id="3f26d-132">エディターのこのページで、必要に応じて以下の項目を設定します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-132">On this page of the editor, you may need or want to configure the following items.</span></span>

-   <span data-ttu-id="3f26d-133">予期しない値を含む行に対するシミュレートされたエラー出力など、1 つ以上の出力を追加して作成する場合は、</span><span class="sxs-lookup"><span data-stu-id="3f26d-133">Create one or more additional outputs, such as a simulated error output for rows that contain unexpected values.</span></span> <span data-ttu-id="3f26d-134">**[出力の追加]** および **[出力の削除]** ボタンを使用して、同期変換コンポーネントの出力を管理します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-134">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your synchronous transformation component.</span></span> <span data-ttu-id="3f26d-135">すべての入力行は、使用できるすべての出力に送信されます。ただし、各行を出力のうちいずれか 1 つにリダイレクトするように指定した場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-135">All input rows are directed to all available outputs unless you indicate that you intend to redirect each row to one output or the other.</span></span> <span data-ttu-id="3f26d-136">行をリダイレクトするように指定するには、出力の `ExclusionGroup` プロパティに 0 以外の整数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-136">You indicate that you intend to redirect rows by specifying a non-zero integer value for the `ExclusionGroup` property on the outputs.</span></span> <span data-ttu-id="3f26d-137">出力を識別するために `ExclusionGroup` に入力した整数値に特別の意味はありませんが、指定した出力のグループでは一貫して同じ整数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-137">The specific integer value entered in `ExclusionGroup` to identify the outputs is not significant, but you must use the same integer consistently for the specified group of outputs.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="3f26d-138">すべての行を出力しない場合は、0 以外の `ExclusionGroup` プロパティ値を単一の出力で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-138">You can also use a non-zero `ExclusionGroup` property value with a single output when you do not want to output all rows.</span></span> <span data-ttu-id="3f26d-139">ただし、この場合は、出力に送信する各行について、**DirectRowTo\<outputbuffer>** メソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-139">However, in this case,  you must explicitly call the **DirectRowTo\<outputbuffer>** method for each row that you want to send to the output.</span></span>

-   <span data-ttu-id="3f26d-140">入力および出力に、わかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-140">Assign a more descriptive name to the input and outputs.</span></span> <span data-ttu-id="3f26d-141">スクリプト コンポーネントはこの名前を使用して、型指定されたアクセサー プロパティを生成します。これは、スクリプト内で入力や出力を参照するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="3f26d-142">同期変換の列は現状のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-142">Leave columns as is for synchronous transformations.</span></span> <span data-ttu-id="3f26d-143">通常、同期変換はデータ フローに列を追加しません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-143">Typically a synchronous transformation does not add columns to the data flow.</span></span> <span data-ttu-id="3f26d-144">データはバッファーの所定の位置で変更され、バッファーがデータ フロー内の次のコンポーネントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-144">Data is modified in place in the buffer, and the buffer is passed on to the next component in the data flow.</span></span> <span data-ttu-id="3f26d-145">このような場合、変換の出力に対して明示的に出力列を追加したり構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-145">If this is the case, you do not have to add and configure output columns explicitly on the transformation's outputs.</span></span> <span data-ttu-id="3f26d-146">出力がエディターに表示される際、明示的に定義された列は含まれません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-146">The outputs appear in the editor without any explicitly defined columns.</span></span>

-   <span data-ttu-id="3f26d-147">行レベルのエラー用のシミュレートされたエラー出力に新しい列を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-147">Add new columns to simulated error outputs for row-level errors.</span></span> <span data-ttu-id="3f26d-148">通常、同じ `ExclusionGroup` 内の複数の出力には、同じ出力列のセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-148">Ordinarily multiple outputs in the same `ExclusionGroup` have the same set of output columns.</span></span> <span data-ttu-id="3f26d-149">ただし、シミュレートされたエラー出力を作成するには、エラー情報を格納するために列の追加が必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-149">However, if you are creating a simulated error output, you may want to add more columns to contain error information.</span></span> <span data-ttu-id="3f26d-150">データ フロー エンジンがエラー行を処理する方法については、「[データ フロー コンポーネントでのエラー出力の使用](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-150">For information about how the data flow engine processes error rows, see [Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md).</span></span> <span data-ttu-id="3f26d-151">スクリプト コンポーネントでは、独自のコードを記述して、追加した列に該当するエラー情報を格納する必要があるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-151">Note that in the Script component you must write your own code to fill the additional columns with appropriate error information.</span></span> <span data-ttu-id="3f26d-152">詳細については、「[スクリプト コンポーネントに対するエラー出力のシミュレート](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-152">For more information, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="3f26d-153">**[スクリプト変換エディター]** の **[入力および出力]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力および出力] ページ&#41;](../script-transformation-editor-inputs-and-outputs-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-153">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="3f26d-154">変数の追加</span><span class="sxs-lookup"><span data-stu-id="3f26d-154">Adding Variables</span></span>
 <span data-ttu-id="3f26d-155">スクリプトで既存の変数を使用する場合は、 `ReadOnlyVariables` [ `ReadWriteVariables` **スクリプト変換エディター**] の [**スクリプト**] ページで、プロパティおよびプロパティフィールドに追加できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-155">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="3f26d-156">プロパティ フィールドに複数の変数を追加する場合は、各変数名をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-156">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="3f26d-157">また、プロパティフィールドの横にある省略記号 ([.**..**]) ボタンをクリックし、[ `ReadOnlyVariables` `ReadWriteVariables` **変数の選択**] ダイアログボックスで変数を選択することで、複数の変数を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-157">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="3f26d-158">スクリプト コンポーネントで変数を使用する方法に関する一般情報については、「[スクリプト コンポーネントでの変数の使用](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-158">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="3f26d-159">**[スクリプト変換エディター]** の **[スクリプト]** ページの詳細については、「[[スクリプト変換エディター] &#40;[スクリプト] ページ&#41;](../script-transformation-editor-script-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-159">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="3f26d-160">コード デザイン モードでの同期変換コンポーネントのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="3f26d-160">Scripting a Synchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="3f26d-161">コンポーネントのメタデータを構成した後、カスタム スクリプトを記述できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-161">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="3f26d-162">**[スクリプト変換エディター]** の **[スクリプト]** ページで **[スクリプトの編集]** をクリックし、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を開いて、カスタム スクリプトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-162">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="3f26d-163">使用するスクリプト言語は、 **[スクリプト]** ページの **[ScriptLanguage]** プロパティで、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のどちらをスクリプト言語として選択したかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-163">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="3f26d-164">スクリプト コンポーネントを使用して作成されたすべての種類のコンポーネントに適用される重要な情報については、「[スクリプト コンポーネントのコーディングおよびデバッグ](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-164">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="3f26d-165">自動生成されたコードについて</span><span class="sxs-lookup"><span data-stu-id="3f26d-165">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="3f26d-166">変換コンポーネントを作成して構成した後で VSTA IDE を開くと、コード エディターには `ScriptMain` クラスが編集可能な状態で表示されます。また、`ProcessInputRow` メソッドがスタブとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-166">When you open the VSTA IDE after you create and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="3f26d-167">カスタム コードは `ScriptMain` クラスに記述します。また、`ProcessInputRow` は変換コンポーネントの最重要メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3f26d-167">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a transformation component.</span></span>

 <span data-ttu-id="3f26d-168">VSTA で [**プロジェクトエクスプローラー** ] ウィンドウを開くと、スクリプトコンポーネントによって読み取り専用およびプロジェクト項目も生成されたことがわかり `BufferWrapper` `ComponentWrapper` ます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-168">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="3f26d-169">クラスは、 `ScriptMain` プロジェクト項目のクラスから継承さ `UserComponent` `ComponentWrapper` れます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-169">The `ScriptMain` class inherits from the `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="3f26d-170">実行時には、データ フロー エンジンが `ProcessInput` クラスの `UserComponent` メソッドを呼び出します。これは親クラスである <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3f26d-170">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="3f26d-171">`ProcessInput` メソッドは、入力バッファーに格納された行を順にループし、各行で 1 回ずつ `ProcessInputRow` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-171">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="3f26d-172">カスタム コードの記述</span><span class="sxs-lookup"><span data-stu-id="3f26d-172">Writing Your Custom Code</span></span>
 <span data-ttu-id="3f26d-173">同期出力型の変換コンポーネントは、記述するすべてのデータ フロー コンポーネントの中で最も単純です。</span><span class="sxs-lookup"><span data-stu-id="3f26d-173">A transformation component with synchronous outputs is the simplest of all data flow components to write.</span></span> <span data-ttu-id="3f26d-174">たとえば、このトピックの単一出力の例は、次のカスタム コードで構成されています。</span><span class="sxs-lookup"><span data-stu-id="3f26d-174">For example, the single-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
```

```csharp
Row.City = (Row.City).ToUpper();

```

 <span data-ttu-id="3f26d-175">同期型のカスタム変換コンポーネントの作成を完了するには、オーバーライドされた `ProcessInputRow` メソッドを使用して、入力バッファーにある各行のデータを変換します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-175">To finish creating a custom synchronous transformation component, you use the overridden `ProcessInputRow` method to transform the data in each row of the input buffer.</span></span> <span data-ttu-id="3f26d-176">データ フロー エンジンは、バッファーがいっぱいになると、データ フロー内の次のコンポーネントにこのバッファーを渡します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-176">The data flow engine passes this buffer, when full, to the next component in the data flow.</span></span>

 <span data-ttu-id="3f26d-177">必要に応じて、`PreExecute` クラスで使用できる `PostExecute` メソッドや `ScriptMain` メソッドにもスクリプトを記述して、準備処理や終了後の処理を行う場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-177">Depending on your requirements, you may also want to write script in the `PreExecute` and `PostExecute` methods, available in the `ScriptMain` class, to perform preliminary or final processing.</span></span>

### <a name="working-with-multiple-outputs"></a><span data-ttu-id="3f26d-178">複数の出力の処理</span><span class="sxs-lookup"><span data-stu-id="3f26d-178">Working with Multiple Outputs</span></span>
 <span data-ttu-id="3f26d-179">使用できる 2 つ以上の出力のいずれかに入力行を送信する場合でも、前述した単一出力の例と比べて、必要なカスタム コードはそれほど多くありません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-179">Directing input rows to one of two or more possible outputs does not require much more custom code than the single-output scenario discussed earlier.</span></span> <span data-ttu-id="3f26d-180">たとえば、このトピックの 2 つの出力の例は、次のカスタム コードで構成されています。</span><span class="sxs-lookup"><span data-stu-id="3f26d-180">For example, the two-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
If Row.City = "REDMOND" Then
    Row.DirectRowToMyRedmondAddresses()
Else
    Row.DirectRowToMyOtherAddresses()
End If
```

```csharp
Row.City = (Row.City).ToUpper();

if (Row.City=="REDMOND")
{
    Row.DirectRowToMyRedmondAddresses();
}
else
{
    Row.DirectRowToMyOtherAddresses();
}
```

 <span data-ttu-id="3f26d-181">この例では、ユーザーが設定した出力の名前に基づき、スクリプト コンポーネントが **DirectRowTo\<OutputBufferX>** メソッドを生成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-181">In this example, the Script component generates the **DirectRowTo\<OutputBufferX>** methods for you, based on the names of the outputs that you configured.</span></span> <span data-ttu-id="3f26d-182">同様のコードを使用して、シミュレートされたエラー出力にエラー行を送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-182">You can use similar code to direct error rows to a simulated error output.</span></span>

## <a name="examples"></a><span data-ttu-id="3f26d-183">例</span><span class="sxs-lookup"><span data-stu-id="3f26d-183">Examples</span></span>
 <span data-ttu-id="3f26d-184">この例では、同期変換コンポーネントを作成するために、`ScriptMain` クラスで必要なカスタム コードを示します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-184">The examples here demonstrate the custom code that is required in the `ScriptMain` class to create a synchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="3f26d-185">これらの例では、サンプルデータベースの**Person**テーブルを使用して、 `AdventureWorks` その第1列と第4列、つまり**intaddressid**列と**nvarchar (30) City**列をデータフローに渡します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-185">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="3f26d-186">このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-186">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="3f26d-187">他の前提条件および仮定条件については、それぞれの例で説明します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-187">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="single-output-synchronous-transformation-example"></a><span data-ttu-id="3f26d-188">単一出力の同期変換の例</span><span class="sxs-lookup"><span data-stu-id="3f26d-188">Single Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="3f26d-189">この例では、単一の出力が含まれる同期変換コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-189">This example demonstrates a synchronous transformation component with a single output.</span></span> <span data-ttu-id="3f26d-190">この変換では **AddressID** 列をパススルーして、**City** 列を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-190">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span>

 <span data-ttu-id="3f26d-191">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="3f26d-192">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="3f26d-193">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、変換元または他の変換の出力を、新しい変換コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-193">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="3f26d-194">この出力では、 **Person.Address** `AdventureWorks` **Addressid**列と**City**列を含むサンプルデータベースの Person テーブルからデータを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-194">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="3f26d-195">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="3f26d-196">**[入力列]** ページで、**AddressID** 列と **City** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="3f26d-197">**City** 列を、読み取り/書き込み可能としてマークします。</span><span class="sxs-lookup"><span data-stu-id="3f26d-197">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="3f26d-198">**[入力および出力]** ページで、入力と出力を **MyAddressInput** と **MyAddressOutput** などのわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-198">On the **Inputs and Outputs** page, rename the input and output with more descriptive names, such as **MyAddressInput** and **MyAddressOutput**.</span></span> <span data-ttu-id="3f26d-199">出力の `SynchronousInputID` は、入力の `ID` に対応していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-199">Notice that the `SynchronousInputID` of the output corresponds to the `ID` of the input.</span></span> <span data-ttu-id="3f26d-200">したがって、出力列を追加して設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-200">Therefore you do not have to add and configure output columns.</span></span>

5.  <span data-ttu-id="3f26d-201">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-201">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="3f26d-202">その後、スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-202">Then close the script development environment and the **Script Transformation Editor**.</span></span>

6.  <span data-ttu-id="3f26d-203">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の変換先、または「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で説明されている変換先コンポーネントの例など、**AddressID** および **City** 列が予期される変換先コンポーネントを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-203">Create and configure a destination component that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="3f26d-204">変換の出力を変換先コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-204">Then connect the output of the transformation to the destination component.</span></span> <span data-ttu-id="3f26d-205">`AdventureWorks` データベースで次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行して、変換先テーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-205">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

7.  <span data-ttu-id="3f26d-206">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-206">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

    }

}
```

### <a name="two-output-synchronous-transformation-example"></a><span data-ttu-id="3f26d-207">2 つの出力の同期変換の例</span><span class="sxs-lookup"><span data-stu-id="3f26d-207">Two-Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="3f26d-208">この例では、2 つの出力を持つ同期変換コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-208">This example demonstrates a synchronous transformation component with two outputs.</span></span> <span data-ttu-id="3f26d-209">この変換では **AddressID** 列をパススルーして、**City** 列を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-209">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span> <span data-ttu-id="3f26d-210">都市名が Redmond の場合、変換はその行を 1 つの出力に送信し、他のすべての行をもう 1 つの出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-210">If the city name is Redmond, it directs the row to one output; it directs all other rows to another output.</span></span>

 <span data-ttu-id="3f26d-211">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-211">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="3f26d-212">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-212">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="3f26d-213">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、変換元または他の変換の出力を、新しい変換コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-213">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="3f26d-214">この出力では、 **Person.Address** `AdventureWorks` 少なくとも**Addressid**列と**City**列を含むサンプルデータベースの Person テーブルからデータを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f26d-214">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="3f26d-215">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-215">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="3f26d-216">**[入力列]** ページで、**AddressID** 列と **City** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-216">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="3f26d-217">**City** 列を、読み取り/書き込み可能としてマークします。</span><span class="sxs-lookup"><span data-stu-id="3f26d-217">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="3f26d-218">**[入力および出力]** ページで、2 番目の出力を作成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-218">On the **Inputs and Outputs** page, create a second output.</span></span> <span data-ttu-id="3f26d-219">新しい出力を追加したら、`SynchronousInputID` が入力の `ID` に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-219">After you add the new output, make sure that you set its `SynchronousInputID` to the `ID` of the input.</span></span> <span data-ttu-id="3f26d-220">このプロパティは、既定として作成された最初の出力で既に設定されています。</span><span class="sxs-lookup"><span data-stu-id="3f26d-220">This property is already set on the first output, which is created by default.</span></span> <span data-ttu-id="3f26d-221">各出力で、`ExclusionGroup` プロパティを 0 以外の同じ値に設定し、入力行を 2 つの相互排他的な出力に分割することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-221">For each output, set the `ExclusionGroup` property to the same non-zero value to indicate that you will split the input rows between two mutually exclusive outputs.</span></span> <span data-ttu-id="3f26d-222">出力列を出力に追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3f26d-222">You do not have to add any output columns to the outputs.</span></span>

5.  <span data-ttu-id="3f26d-223">入力と出力を、**MyAddressInput**、**MyRedmondAddresses**、**MyOtherAddresses** などのわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-223">Rename the input and outputs with more descriptive names, such as **MyAddressInput**, **MyRedmondAddresses**, and **MyOtherAddresses**.</span></span>

6.  <span data-ttu-id="3f26d-224">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-224">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="3f26d-225">その後、スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="3f26d-225">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="3f26d-226">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の変換先、フラット ファイル変換先、または「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で説明されている変換先コンポーネントの例など、**AddressID** および **City** 列が予期される 2 つの変換先コンポーネントを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-226">Create and configure two destination components that expect the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, a Flat File destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="3f26d-227">変換の各出力をいずれかの変換先コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-227">Then connect each of the outputs of the transformation to one of the destination components.</span></span> <span data-ttu-id="3f26d-228">変換先テーブルを作成するには、`AdventureWorks` データベースで次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドと同様のコマンド (一意のテーブル名を使用) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-228">You can create destination tables by running a [!INCLUDE[tsql](../../includes/tsql-md.md)] command similar to the following (with unique table names) in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2](
        [AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL
    ```

8.  <span data-ttu-id="3f26d-229">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-229">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

        If Row.City = "REDMOND" Then
            Row.DirectRowToMyRedmondAddresses()
        Else
            Row.DirectRowToMyOtherAddresses()
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

        if (Row.City == "REDMOND")
        {
            Row.DirectRowToMyRedmondAddresses();
        }
        else
        {
            Row.DirectRowToMyOtherAddresses();
        }

    }
}
```

<span data-ttu-id="3f26d-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **Integration Services で最新情報を入手する**</span><span class="sxs-lookup"><span data-stu-id="3f26d-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3f26d-231">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f26d-231">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3f26d-232">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="3f26d-232">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3f26d-233">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="3f26d-233">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f26d-234">参照</span><span class="sxs-lookup"><span data-stu-id="3f26d-234">See Also</span></span>
 <span data-ttu-id="3f26d-235">[同期変換と非同期変換につい](../understanding-synchronous-and-asynchronous-transformations.md)[てスクリプトコンポーネントによる非同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)[同期出力型のカスタム変換コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="3f26d-235">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span></span>


