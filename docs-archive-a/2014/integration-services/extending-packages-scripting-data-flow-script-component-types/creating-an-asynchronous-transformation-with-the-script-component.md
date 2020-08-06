---
title: スクリプト コンポーネントによる非同期変換の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 465c4a597b4a18d7bd956116cd5d7640a5393958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641736"
---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a><span data-ttu-id="59a23-102">スクリプト コンポーネントによる非同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="59a23-102">Creating an Asynchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="59a23-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内で変換コンポーネントを使用することにより、変換元から変換先にデータが受け渡される過程で、データを修正または分析できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="59a23-104">同期出力型の変換では、各入力列はコンポーネントを通過するたびに処理されます。</span><span class="sxs-lookup"><span data-stu-id="59a23-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="59a23-105">非同期出力型の変換では、変換が入力行をすべて受け取るまで処理の実行を待機する場合と、変換が入力行をすべて受け取る前に一部の行を出力する場合があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-105">A transformation with asynchronous outputs may wait to complete its processing until the transformation has received all input rows, or the transformation may output certain rows before it has received all input rows.</span></span> <span data-ttu-id="59a23-106">このトピックでは、非同期変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="59a23-106">This topic discusses an asynchronous transformation.</span></span> <span data-ttu-id="59a23-107">処理で同期変換が必要な場合は、「[スクリプト コンポーネントによる同期変換の作成](../data-flow/transformations/script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-107">If your processing requires a synchronous transformation, see [Creating a Synchronous Transformation with the Script Component](../data-flow/transformations/script-component.md).</span></span> <span data-ttu-id="59a23-108">同期コンポーネントと非同期コンポーネントの相違点の詳細については、「[同期変換と非同期変換について](../understanding-synchronous-and-asynchronous-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-108">For more information about the differences between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="59a23-109">スクリプト コンポーネントの概要については、「[スクリプト コンポーネントによるデータ フローの拡張](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="59a23-110">スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-110">The Script component and the infrastructure code that it generates for you simplify the process of developing a custom data flow component.</span></span> <span data-ttu-id="59a23-111">ただし、スクリプト コンポーネントのしくみを理解するため、「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」セクション、特に「[同期出力型のカスタム変換コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)」を参照して、カスタム データ フロー コンポーネントを開発する場合に従う必要がある手順に目を通しておくと役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="59a23-111">However, to understand how the Script component works, you may find it useful to read through the steps that you must follow in developing a custom data flow component in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-an-asynchronous-transformation-component"></a><span data-ttu-id="59a23-112">非同期変換コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="59a23-112">Getting Started with an Asynchronous Transformation Component</span></span>
 <span data-ttu-id="59a23-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [データ フロー] タブにスクリプト コンポーネントを追加すると、 **[スクリプト コンポーネントの種類を選択]** ダイアログ ボックスが表示され、変換元、変換、または変換先としてあらかじめ設定するコンポーネントの入力を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59a23-113">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box appears, prompting you to preconfigure the component as a source, transformation, or destination.</span></span> <span data-ttu-id="59a23-114">このダイアログ ボックスで、 **[変換]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="59a23-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="59a23-115">メタデータ デザイン モードでの非同期変換コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="59a23-115">Configuring an Asynchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="59a23-116">変換コンポーネントを作成するオプションを選択したら、 **[スクリプト変換エディター]** を使用して、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="59a23-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="59a23-117">詳細については、「[スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="59a23-118">スクリプト コンポーネントで使用するスクリプト言語を選択するには、 **[スクリプト変換エディター]** ダイアログ ボックスの **[スクリプト]** ページにある **[ScriptLanguage]** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="59a23-118">To select the script language that the Script component will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="59a23-119">スクリプト コンポーネントの既定のスクリプト言語を設定するには、**[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="59a23-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="59a23-120">詳細については、「 [General Page](../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="59a23-121">データ フロー変換コンポーネントには 1 つの入力があり、1 つ以上の出力を設定できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-121">A data flow transformation component has one input and supports one or more outputs.</span></span> <span data-ttu-id="59a23-122">コンポーネントの入力および出力の設定は、メタデータ デザイン モードでカスタム スクリプトを記述する前に完了する必要のある手順の 1 つです。これを行うには、 **[スクリプト変換エディター]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="59a23-122">Configuring the input and outputs of your component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="59a23-123">入力列の設定</span><span class="sxs-lookup"><span data-stu-id="59a23-123">Configuring Input Columns</span></span>
 <span data-ttu-id="59a23-124">スクリプト コンポーネントを使用して作成した変換コンポーネントには、1 つの入力があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-124">A transformation component created by using the Script component has a single input.</span></span>

 <span data-ttu-id="59a23-125">**[スクリプト変換エディター]** の **[入力列]** ページには、データ フローの上流コンポーネントの出力で使用できる列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="59a23-125">On the **Input Columns** page of the **Script Transformation Editor**, the columns list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="59a23-126">変換する列、またはそのまま出力する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="59a23-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="59a23-127">変換するすべての列の適切な場所に、読み取り/書き込みのマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="59a23-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="59a23-128">**[スクリプト変換エディター]** の **[入力列]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力列] ページ&#41;](../script-transformation-editor-input-columns-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="59a23-129">入力、出力、および出力列の設定</span><span class="sxs-lookup"><span data-stu-id="59a23-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="59a23-130">変換コンポーネントには、1 つ以上の出力を設定できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="59a23-131">通常、非同期出力型の変換には、2 つの出力を設定します。</span><span class="sxs-lookup"><span data-stu-id="59a23-131">Frequently a transformation with asynchronous outputs has two outputs.</span></span> <span data-ttu-id="59a23-132">たとえば、特定の市内にある住所を数えたい場合、1 つの出力に住所データをそのまま送り、もう 1 つの出力に集計結果を送信します。</span><span class="sxs-lookup"><span data-stu-id="59a23-132">For example, when you count the number of addresses located in a specific city, you may want to pass the address data through to one output, while sending the result of the aggregation to another output.</span></span> <span data-ttu-id="59a23-133">集計結果を出力するには、新しい出力列も 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="59a23-133">The aggregation output also requires a new output column.</span></span>

 <span data-ttu-id="59a23-134">**[スクリプト変換エディター]** の **[入力および出力]** ページには、既定で 1 つの出力が作成されていますが、出力列は作成されていません。</span><span class="sxs-lookup"><span data-stu-id="59a23-134">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you see that a single output has been created by default, but no output columns have been created.</span></span> <span data-ttu-id="59a23-135">エディターのこのページでは、次の項目を設定できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-135">On this page of the editor, you can configure the following items:</span></span>

-   <span data-ttu-id="59a23-136">集計結果の出力など、1 つ以上の出力を追加して作成する場合は、</span><span class="sxs-lookup"><span data-stu-id="59a23-136">You may want to create one or more additional outputs, such as an output for the result of an aggregation.</span></span> <span data-ttu-id="59a23-137">**[出力の追加]** および **[出力の削除]** ボタンを使用して、非同期変換コンポーネントの出力を管理します。</span><span class="sxs-lookup"><span data-stu-id="59a23-137">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your asynchronous transformation component.</span></span> <span data-ttu-id="59a23-138">各出力の `SynchronousInputID` プロパティを 0 に設定すると、上流コンポーネントからのデータをそのまま出力するのではなく、変換を実行して、既存の行や列の適切な位置に出力することを示します。</span><span class="sxs-lookup"><span data-stu-id="59a23-138">Set the `SynchronousInputID` property of each output to zero to indicate that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns.</span></span> <span data-ttu-id="59a23-139">この設定によって、出力が入力に対して非同期になります。</span><span class="sxs-lookup"><span data-stu-id="59a23-139">It is this setting that makes the outputs asynchronous to the input.</span></span>

-   <span data-ttu-id="59a23-140">入力や出力にはわかりやすい名前を付けておくことができます。</span><span class="sxs-lookup"><span data-stu-id="59a23-140">You may want to assign a friendly name to the input and outputs.</span></span> <span data-ttu-id="59a23-141">スクリプト コンポーネントはこの名前を使用して、型指定されたアクセサー プロパティを生成します。これは、スクリプト内で入力や出力を参照するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="59a23-142">通常、非同期変換は列をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="59a23-142">Frequently an asynchronous transformation adds columns to the data flow.</span></span> <span data-ttu-id="59a23-143">出力の `SynchronousInputID` プロパティが 0 の場合、上流コンポーネントからのデータはそのまま出力されず、変換を実行して、既存の行や列の適切な位置に出力されることを示します。この場合、出力に対して出力列を明示的に追加して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-143">When the `SynchronousInputID` property of an output is zero, indicating that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns, you must add and configure output columns explicitly on the output.</span></span> <span data-ttu-id="59a23-144">出力列の名前は、マップ先の入力列と同じ名前にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="59a23-144">Output columns do not have to have the same names as the input columns to which they are mapped.</span></span>

-   <span data-ttu-id="59a23-145">追加情報を格納するために列を追加する場合があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-145">You may want to add more columns to contain additional information.</span></span> <span data-ttu-id="59a23-146">その場合、追加した列にデータを格納するには、独自のコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-146">You must write your own code to fill the additional columns with data.</span></span> <span data-ttu-id="59a23-147">標準エラー出力の動作の再現については、「[スクリプト コンポーネントに対するエラー出力のシミュレート](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-147">For information about reproducing the behavior of a standard error output, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="59a23-148">**[スクリプト変換エディター]** の **[入力および出力]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力および出力] ページ&#41;](../script-transformation-editor-inputs-and-outputs-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-148">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="59a23-149">変数の追加</span><span class="sxs-lookup"><span data-stu-id="59a23-149">Adding Variables</span></span>
 <span data-ttu-id="59a23-150">値をスクリプト内で使用する既存の変数がある場合は、 **[スクリプト変換エディター]** の **[スクリプト]** ページで、ReadOnlyVariables および ReadWriteVariables プロパティ フィールドに追加できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-150">If there are any existing variables whose values you want to use in your script, you can add them in the ReadOnlyVariables and ReadWriteVariables property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="59a23-151">プロパティ フィールドに複数の変数を追加する場合は、各変数名をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="59a23-151">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="59a23-152">また、プロパティフィールドの横にある省略記号 ([.**..**]) ボタンをクリックし、[ `ReadOnlyVariables` `ReadWriteVariables` **変数の選択**] ダイアログボックスで変数を選択することで、複数の変数を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="59a23-152">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="59a23-153">スクリプト コンポーネントで変数を使用する方法に関する一般情報については、「[スクリプト コンポーネントでの変数の使用](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-153">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="59a23-154">**[スクリプト変換エディター]** の **[スクリプト]** ページの詳細については、「[[スクリプト変換エディター] &#40;[スクリプト] ページ&#41;](../script-transformation-editor-script-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-154">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="59a23-155">コード デザイン モードでの非同期変換コンポーネントのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="59a23-155">Scripting an Asynchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="59a23-156">コンポーネントのメタデータをすべて構成した後、カスタム スクリプトを記述できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-156">After you have configured all the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="59a23-157">**[スクリプト変換エディター]** の **[スクリプト]** ページで **[スクリプトの編集]** をクリックし、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を開いて、カスタム スクリプトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-157">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="59a23-158">使用するスクリプト言語は、**[スクリプト]** ページの **[ScriptLanguage]** プロパティで、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のどちらをスクリプト言語として選択したかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="59a23-158">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="59a23-159">スクリプト コンポーネントを使用して作成されたすべての種類のコンポーネントに適用される重要な情報については、「[スクリプト コンポーネントのコーディングおよびデバッグ](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-159">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="59a23-160">自動生成されたコードについて</span><span class="sxs-lookup"><span data-stu-id="59a23-160">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="59a23-161">変換コンポーネントを作成して構成した後で VSTA IDE を開くと、 `ScriptMain` コードエディターには編集可能なクラスが表示され、ProcessInputRow と CreateNewOutputRows メソッドのスタブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59a23-161">When you open the VSTA IDE after creating and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with stubs for the ProcessInputRow and the CreateNewOutputRows methods.</span></span> <span data-ttu-id="59a23-162">ScriptMain クラスはカスタム コードを記述する場所であり、ProcessInputRow は変換コンポーネントの最重要メソッドです。</span><span class="sxs-lookup"><span data-stu-id="59a23-162">The ScriptMain class is where you will write your custom code, and ProcessInputRow is the most important method in a transformation component.</span></span> <span data-ttu-id="59a23-163">`CreateNewOutputRows` メソッドは変換元コンポーネントで一般的に使用され、両方のコンポーネントが独自の出力行を作成する必要のある、非同期変換と似ています。</span><span class="sxs-lookup"><span data-stu-id="59a23-163">The `CreateNewOutputRows` method is more typically used in a source component, which is like an asynchronous transformation in that both components must create their own output rows.</span></span>

 <span data-ttu-id="59a23-164">VSTA の [**プロジェクトエクスプローラー** ] ウィンドウを開くと、スクリプトコンポーネントによって読み取り専用およびプロジェクト項目も生成されたことがわかり `BufferWrapper` `ComponentWrapper` ます。</span><span class="sxs-lookup"><span data-stu-id="59a23-164">If you open the VSTA **Project Explorer** window, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="59a23-165">ScriptMain クラスは、プロジェクトアイテムの UserComponent クラスから継承され `ComponentWrapper` ます。</span><span class="sxs-lookup"><span data-stu-id="59a23-165">The ScriptMain class inherits from the UserComponent class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="59a23-166">実行時に、データフローエンジンはクラスの PrimeOutput メソッドを呼び出します `UserComponent` 。これにより、 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> 親クラスのメソッドがオーバーライドされ <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> ます。</span><span class="sxs-lookup"><span data-stu-id="59a23-166">At run time, the data flow engine calls the PrimeOutput method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="59a23-167">その後、PrimeOutput メソッドは CreateNewOutputRows メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="59a23-167">The PrimeOutput method in turn calls the CreateNewOutputRows method.</span></span>

 <span data-ttu-id="59a23-168">次に、データ フロー エンジンが UserComponent クラスの ProcessInput メソッドを呼び出します。これにより、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 親クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> メソッドがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="59a23-168">Next, the data flow engine invokes the ProcessInput method in the UserComponent class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="59a23-169">ProcessInput メソッドは、入力バッファーの行を順にループし、各行で 1 回ずつ ProcessInputRow メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="59a23-169">The ProcessInput method in turn loops through the rows in the input buffer and calls the ProcessInputRow method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="59a23-170">カスタム コードの記述</span><span class="sxs-lookup"><span data-stu-id="59a23-170">Writing Your Custom Code</span></span>
 <span data-ttu-id="59a23-171">非同期型のカスタム変換コンポーネントの作成を完了するには、オーバーライドされた ProcessInputRow メソッドを使用して、入力バッファーの各行のデータを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-171">To finish creating a custom asynchronous transformation component, you must use the overridden ProcessInputRow method to process the data in each row of the input buffer.</span></span> <span data-ttu-id="59a23-172">出力は入力に同期しないため、データの行を明示的に出力に書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-172">Because the outputs are not synchronous to the input, you must explicitly write rows of data to the outputs.</span></span>

 <span data-ttu-id="59a23-173">非同期変換では、AddRow メソッドを使用して、ProcessInputRow または ProcessInput メソッド内から必要に応じて行を出力に追加できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-173">In an asynchronous transformation, you can use the AddRow method to add rows to the output as appropriate from within the ProcessInputRow or ProcessInput methods.</span></span> <span data-ttu-id="59a23-174">CreateNewOutputRows メソッドを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="59a23-174">You do not have to use the CreateNewOutputRows method.</span></span> <span data-ttu-id="59a23-175">集計結果などの結果の単一行を特定の出力に書き込んでいる場合は、CreateNewOutputRows メソッドを使用してあらかじめ出力行を作成し、その値をすべての入力行を処理した後に入力できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-175">If you are writing a single row of results, such as aggregation results, to a particular output, you can create the output row beforehand by using the CreateNewOutputRows method, and fill in its values later after processing all input rows.</span></span> <span data-ttu-id="59a23-176">ただし、スクリプト コンポーネントでは入力または出力で現在の行のみを使用できるため、CreateNewOutputRows メソッドで複数の行を作成しても役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="59a23-176">However it is not useful to create multiple rows in the CreateNewOutputRows method, because the Script component only lets you use the current row in an input or output.</span></span> <span data-ttu-id="59a23-177">CreateNewOutputRows メソッドは、処理する入力行のない変換元コンポーネントでより重要になります。</span><span class="sxs-lookup"><span data-stu-id="59a23-177">The CreateNewOutputRows method is more important in a source component where there are no input rows to process.</span></span>

 <span data-ttu-id="59a23-178">また、ProcessInput メソッド自体をオーバーライドし、入力バッファー内をループして各行で ProcessInputRow を呼び出す前後に、準備処理や終了処理を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="59a23-178">You may also want to override the ProcessInput method itself, so that you can do additional preliminary or final processing before or after you loop through the input buffer and call ProcessInputRow for each row.</span></span> <span data-ttu-id="59a23-179">たとえば、このトピックのコード例の1つでは、ProcessInput をオーバーライドして、特定の都市にある住所の数をカウントし `.` ます。この例では、すべての行が処理された後に、集計値が2番目の出力に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="59a23-179">For example, one of the code examples in this topic overrides ProcessInput to count the number of addresses in a specific city as ProcessInputRow loops through rows`.` The example writes the summary value to the second output after all rows have been processed.</span></span> <span data-ttu-id="59a23-180">この例で出力の終了処理が ProcessInput で行われているのは、PostExecute が呼び出される時点では、出力バッファーが既に使用できなくなっているためです。</span><span class="sxs-lookup"><span data-stu-id="59a23-180">The example completes the output in ProcessInput because the output buffers are no longer available when PostExecute is called.</span></span>

 <span data-ttu-id="59a23-181">必要に応じて、ScriptMain クラスで使用できる PreExecute メソッドや PostExecute メソッドにもスクリプトを記述して、準備処理や終了処理を行う場合もあります。</span><span class="sxs-lookup"><span data-stu-id="59a23-181">Depending on your requirements, you may also want to write script in the PreExecute and PostExecute methods available in the ScriptMain class to perform any preliminary or final processing.</span></span>

> [!NOTE]
>  <span data-ttu-id="59a23-182">カスタム データ フロー コンポーネントを最初から開発した場合、PrimeOutput メソッドをオーバーライドして、出力バッファーに対する参照をキャッシュに保存し、後でデータの行をバッファーに追加できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-182">If you were developing a custom data flow component from scratch, it would be important to override the PrimeOutput method to cache references to the output buffers so that you could add rows of data to the buffers later.</span></span> <span data-ttu-id="59a23-183">スクリプト コンポーネントを使用する場合は、オーバーライドする必要はありません。`BufferWrapper` プロジェクト アイテム内に、各出力バッファーを表すクラスが自動生成されるためです。</span><span class="sxs-lookup"><span data-stu-id="59a23-183">In the Script component, this is not necessary because you have an automatically generated class representing each output buffer in the `BufferWrapper` project item.</span></span>

## <a name="example"></a><span data-ttu-id="59a23-184">例</span><span class="sxs-lookup"><span data-stu-id="59a23-184">Example</span></span>
 <span data-ttu-id="59a23-185">この例では、非同期変換コンポーネントを作成するために ScriptMain クラスで必要なカスタム コードを示します。</span><span class="sxs-lookup"><span data-stu-id="59a23-185">This example demonstrates the custom code that is required in the ScriptMain class to create an asynchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="59a23-186">これらの例では、**AdventureWorks** サンプル データベースの **Person.Address** テーブルを使用して、その第 1 列および第 4 列、つまり、**intAddressID** 列および **nvarchar(30)City** 列をデータ フローにそのまま渡します。</span><span class="sxs-lookup"><span data-stu-id="59a23-186">These examples use the **Person.Address** table in the **AdventureWorks** sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="59a23-187">このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="59a23-187">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="59a23-188">他の前提条件および仮定条件については、それぞれの例で説明します。</span><span class="sxs-lookup"><span data-stu-id="59a23-188">Additional prerequisites and assumptions are documented for each example.</span></span>

 <span data-ttu-id="59a23-189">次の例では、2 つの出力を持つ非同期変換コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="59a23-189">This example demonstrates an asynchronous transformation component with two outputs.</span></span> <span data-ttu-id="59a23-190">この変換では、**AddressID** 列および **City** 列のデータを 1 つの出力にそのまま渡し、特定の都市 (Redmond, Washington, U.S.A.) 内にある住所の数をカウントし、その結果の値を 2 番目の出力に送ります。</span><span class="sxs-lookup"><span data-stu-id="59a23-190">This transformation passes through the **AddressID** and **City** columns to one output, while it counts the number of addresses located in a specific city (Redmond, Washington, U.S.A.), and then outputs the resulting value to a second output.</span></span>

 <span data-ttu-id="59a23-191">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="59a23-192">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="59a23-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="59a23-193">デザイナーで、変換元または他の変換の出力を、新しい変換コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="59a23-193">Connect the output of a source or of another transformation to the new transformation component in the designer.</span></span> <span data-ttu-id="59a23-194">この出力には、サンプル データベース **AdventureWorks** の **Person.Address** テーブルから、少なくとも **AddressID** 列および **City** 列を含むデータが供給される必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a23-194">This output should provide data from the **Person.Address** table of the **AdventureWorks** sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="59a23-195">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="59a23-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="59a23-196">**[入力列]** ページで、**AddressID** 列と **City** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="59a23-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="59a23-197">**[入力および出力]** ページで、最初の出力の **AddressID** 出力列と **City** 出力列を追加および構成します。</span><span class="sxs-lookup"><span data-stu-id="59a23-197">On the **Inputs and Outputs** page, add and configure the **AddressID** and **City** output columns on the first output.</span></span> <span data-ttu-id="59a23-198">2 番目の出力を追加し、集計値を格納する出力列をその出力に追加します。</span><span class="sxs-lookup"><span data-stu-id="59a23-198">Add a second output, and add an output column for the summary value on the second output.</span></span> <span data-ttu-id="59a23-199">この例により各入力行が最初の出力に明示的にコピーされるため、最初の出力の SynchronousInputID プロパティを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="59a23-199">Set the SynchronousInputID property of the first output to 0, because this example copies each input row explicitly to the first output.</span></span> <span data-ttu-id="59a23-200">新しく作成された出力の SynchronousInputID プロパティは既に 0 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="59a23-200">The SynchronousInputID property of the newly-created output is already set to 0.</span></span>

5.  <span data-ttu-id="59a23-201">入力、出力、および新しい出力列をわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="59a23-201">Rename the input, the outputs, and the new output column to give them more descriptive names.</span></span> <span data-ttu-id="59a23-202">この例では、入力の名前として **MyAddressInput**、出力には **MyAddressOutput** および **MySummaryOutput** を使用し、2 番目の出力の出力列には **MyRedmondCount** を使用します。</span><span class="sxs-lookup"><span data-stu-id="59a23-202">The example uses **MyAddressInput** as the name of the input, **MyAddressOutput** and **MySummaryOutput** for the outputs, and **MyRedmondCount** for the output column on the second output.</span></span>

6.  <span data-ttu-id="59a23-203">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="59a23-203">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="59a23-204">その後、スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="59a23-204">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="59a23-205">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の変換先、または「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で説明されている変換先コンポーネントの例など、**AddressID** および **City** 列が予期される最初の出力の変換先コンポーネントを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="59a23-205">Create and configure a destination component for the first output that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), .</span></span> <span data-ttu-id="59a23-206">次に、変換の最初の出力である **MyAddressOutput** を変換先コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="59a23-206">Then connect the first output of the transformation, **MyAddressOutput**, to the destination component.</span></span> <span data-ttu-id="59a23-207">**AdventureWorks** データベースで次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行して、変換先テーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="59a23-207">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the **AdventureWorks** database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

8.  <span data-ttu-id="59a23-208">2 番目の出力に接続する別の変換先コンポーネントを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="59a23-208">Create and configure another destination component for the second output.</span></span> <span data-ttu-id="59a23-209">次に、変換の 2 番目の出力である **MySummaryOutput** を変換先コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="59a23-209">Then connect the second output of the transformation, **MySummaryOutput**, to the destination component.</span></span> <span data-ttu-id="59a23-210">2 番目の出力からは 1 つの値を格納した行が 1 つ出力されるだけなので、フラット ファイル接続マネージャーを使用して、1 つの列を含む新しいファイルに接続する設定を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="59a23-210">Because the second output writes a single row with a single value, you can easily configure a destination with a Flat File connection manager that connects to a new file that has a single column.</span></span> <span data-ttu-id="59a23-211">この例では、この変換先の列に **MyRedmondCount** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="59a23-211">In the example, this destination column is named **MyRedmondCount**.</span></span>

9. <span data-ttu-id="59a23-212">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="59a23-212">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Private myRedmondAddressCount As Integer

    Public Overrides Sub CreateNewOutputRows()

        MySummaryOutputBuffer.AddRow()

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)

        While Buffer.NextRow()
            MyAddressInput_ProcessInputRow(Buffer)
        End While

        If Buffer.EndOfRowset Then
            MyAddressOutputBuffer.SetEndOfRowset()
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount
            MySummaryOutputBuffer.SetEndOfRowset()
        End If

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With MyAddressOutputBuffer
            .AddRow()
            .AddressID = Row.AddressID
            .City = Row.City
        End With

        If Row.City.ToUpper = "REDMOND" Then
            myRedmondAddressCount += 1
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    private int myRedmondAddressCount;

    public override void CreateNewOutputRows()
    {

        MySummaryOutputBuffer.AddRow();

    }

    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)
    {

        while (Buffer.NextRow())
        {
            MyAddressInput_ProcessInputRow(Buffer);
        }

        if (Buffer.EndOfRowset())
        {
            MyAddressOutputBuffer.SetEndOfRowset();
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;
            MySummaryOutputBuffer.SetEndOfRowset();
        }

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            MyAddressOutputBuffer.AddRow();
            MyAddressOutputBuffer.AddressID = Row.AddressID;
            MyAddressOutputBuffer.City = Row.City;
        }

        if (Row.City.ToUpper() == "REDMOND")
        {
            myRedmondAddressCount += 1;
        }

    }

}

```

<span data-ttu-id="59a23-213">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="59a23-213">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="59a23-214">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="59a23-214">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="59a23-215">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="59a23-215">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="59a23-216">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="59a23-216">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="59a23-217">参照</span><span class="sxs-lookup"><span data-stu-id="59a23-217">See Also</span></span>
 <span data-ttu-id="59a23-218">[同期変換と非同期変換につい](../understanding-synchronous-and-asynchronous-transformations.md)[てスクリプトコンポーネントによる同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)[非同期出力型のカスタム変換コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="59a23-218">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span></span>


