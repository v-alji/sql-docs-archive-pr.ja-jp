---
title: スクリプト コンポーネントによる変換元の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], source components
- output columns [Integration Services]
- sources [Integration Services], components
ms.assetid: 547c4179-ea82-4265-8c6f-04a2aa77a3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a352348f7f47157c5f2ec6d3ff01cea47de0ffb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641739"
---
# <a name="creating-a-source-with-the-script-component"></a><span data-ttu-id="5100c-102">スクリプト コンポーネントによる変換元の作成</span><span class="sxs-lookup"><span data-stu-id="5100c-102">Creating a Source with the Script Component</span></span>
  <span data-ttu-id="5100c-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内で変換元コンポーネントを使用すると、データ ソースからデータを読み込み、下流にある変換や変換先に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5100c-103">You use a source component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to load data from a data source to pass on to downstream transformations and destinations.</span></span> <span data-ttu-id="5100c-104">通常、データ ソースへの接続には、既存の接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="5100c-104">Ordinarily you connect to the data source through an existing connection manager.</span></span>

 <span data-ttu-id="5100c-105">スクリプトコンポーネントの概要については、「スクリプトコンポーネントによるデータフローの拡張」 (../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="5100c-105">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span></span>

 <span data-ttu-id="5100c-106">スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="5100c-106">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="5100c-107">スクリプト コンポーネントの動作のしくみを理解するため、カスタム データ フロー コンポーネントの開発手順を理解しておくと役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-107">However, to understand how the Script component works, you may find it useful to read through the steps that are involved in developing a custom data flow component.</span></span> <span data-ttu-id="5100c-108">「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」セクション、特に「[カスタム変換元コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-108">See the section [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), especially the topic [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).</span></span>

## <a name="getting-started-with-a-source-component"></a><span data-ttu-id="5100c-109">変換元コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="5100c-109">Getting Started with a Source Component</span></span>
 <span data-ttu-id="5100c-110">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [データ フロー] ペインにスクリプト コンポーネントを追加すると、 **[スクリプト コンポーネントの種類を選択]** ダイアログ ボックスが開き、[変換元]、[変換先]、[変換] スクリプトのいずれかを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="5100c-110">When you add a Script component to the Data Flow pane of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a Source, Destination, or Transformation script.</span></span> <span data-ttu-id="5100c-111">このダイアログ ボックスで、 **[変換元]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5100c-111">In this dialog box, select **Source**.</span></span>

## <a name="configuring-a-source-component-in-metadata-design-mode"></a><span data-ttu-id="5100c-112">メタデータ デザイン モードでの変換元コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="5100c-112">Configuring a Source Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="5100c-113">変換元コンポーネントの作成を選択したら、 **[スクリプト変換エディター]** を使用して、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-113">After selecting to create a source component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="5100c-114">詳細については、「[スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-114">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="5100c-115">データ フロー変換元コンポーネントに入力はありませんが、1 つ以上の出力を設定できます。</span><span class="sxs-lookup"><span data-stu-id="5100c-115">A data flow source component has no inputs and supports one or more outputs.</span></span> <span data-ttu-id="5100c-116">コンポーネントの出力の設定は、メタデータ デザイン モードでカスタム スクリプトを記述する前に完了する必要のある手順の 1 つです。これを行うには、 **[スクリプト変換エディター]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="5100c-116">Configuring the outputs for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

 <span data-ttu-id="5100c-117">**[スクリプト変換エディター]** の **[スクリプト]** ページにある **[ScriptLanguage]** プロパティを設定して、スクリプト言語を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5100c-117">You can also specify the script language by setting the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor**.</span></span>

> [!NOTE]
>  <span data-ttu-id="5100c-118">スクリプト コンポーネントとスクリプト タスクの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="5100c-118">To set the default script language for Script components and Script Tasks, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="5100c-119">詳細については、「 [General Page](../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-119">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="adding-connection-managers"></a><span data-ttu-id="5100c-120">接続マネージャーの追加</span><span class="sxs-lookup"><span data-stu-id="5100c-120">Adding Connection Managers</span></span>
 <span data-ttu-id="5100c-121">通常、変換元コンポーネントは既存の接続マネージャーを使用してデータ ソースに接続し、データをデータ フローに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5100c-121">Ordinarily a source component uses an existing connection manager to connect to the data source from which it loads data into the data flow.</span></span> <span data-ttu-id="5100c-122">**[スクリプト変換エディター]** の **[接続マネージャー]** ページで **[追加]** をクリックして、適切な接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="5100c-122">On the **Connection Managers** page of the **Script Transformation Editor**, click **Add** to add the appropriate connection manager.</span></span>

 <span data-ttu-id="5100c-123">ただし、接続マネージャーは、便宜上、特定の種類のデータ ソースに接続するために必要な情報をカプセル化して格納するユニットにすぎません。</span><span class="sxs-lookup"><span data-stu-id="5100c-123">However, a connection manager is only a convenient unit that encapsulates and stores the information that it must have to connect to a data source of a particular type.</span></span> <span data-ttu-id="5100c-124">データの読み込みや保存、場合によってはデータ ソースとの接続や切断を行うためには、独自のカスタム コードを記述する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="5100c-124">You must write your own custom code to load or save your data, and possibly to open and close the connection to the data source also.</span></span>

 <span data-ttu-id="5100c-125">スクリプト コンポーネントで接続マネージャーを使用する方法の一般情報については、「[スクリプト コンポーネントでのデータ ソースへの接続](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-125">For general information about how to use connection managers with the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).</span></span>

 <span data-ttu-id="5100c-126">**[スクリプト変換エディター]** の **[接続マネージャー]** ページの詳細については、「[スクリプト変換エディター &#40;[接続マネージャー] ページ&#41;](../script-transformation-editor-connection-managers-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-126">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Connection Managers Page&#41;](../script-transformation-editor-connection-managers-page.md).</span></span>

### <a name="configuring-outputs-and-output-columns"></a><span data-ttu-id="5100c-127">出力および出力列の設定</span><span class="sxs-lookup"><span data-stu-id="5100c-127">Configuring Outputs and Output Columns</span></span>
 <span data-ttu-id="5100c-128">変換元コンポーネントに入力はありませんが、1 つ以上の出力を設定できます。</span><span class="sxs-lookup"><span data-stu-id="5100c-128">A source component has no inputs and supports one or more outputs.</span></span> <span data-ttu-id="5100c-129">**[スクリプト変換エディター]** の **[入力および出力]** ページには、既定で 1 つの出力が作成されていますが、出力列は作成されていません。</span><span class="sxs-lookup"><span data-stu-id="5100c-129">On the **Inputs and Outputs** page of the **Script Transformation Editor**, a single output has been created by default, but no output columns have been created.</span></span> <span data-ttu-id="5100c-130">エディターのこのページで、必要に応じて以下の項目を設定します。</span><span class="sxs-lookup"><span data-stu-id="5100c-130">On this page of the editor, you may need or want to configure the following items.</span></span>

-   <span data-ttu-id="5100c-131">各出力に対する出力列は、手動で追加して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-131">You must add and configure output columns manually for each output.</span></span> <span data-ttu-id="5100c-132">各出力に対する [出力列] フォルダーを選択し、 **[列の追加]** および **[列の削除]** ボタンを使用して、変換元コンポーネントの各出力に対する出力列を管理します。</span><span class="sxs-lookup"><span data-stu-id="5100c-132">Select the Output Columns folder for each output, and then use the **Add Column** and **Remove Column** buttons to manage the output columns for each output of the source component.</span></span> <span data-ttu-id="5100c-133">後でスクリプト内で出力列を参照する際には、ここで割り当てた名前、および自動生成されたコードによって作成された、型指定されたアクセサー プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="5100c-133">Later, you will refer to the output columns in your script by the names that you assign here, by using the typed accessor properties created for you in the auto-generated code.</span></span>

-   <span data-ttu-id="5100c-134">予期しない値を含む行に対するシミュレートされたエラー出力など、1 つ以上の出力を追加して作成できます。</span><span class="sxs-lookup"><span data-stu-id="5100c-134">You may want to create one or more additional outputs, such as a simulated error output for rows that contain unexpected values.</span></span> <span data-ttu-id="5100c-135">**[出力の追加]** および **[出力の削除]** ボタンを使用して、変換元コンポーネントの出力を管理します。</span><span class="sxs-lookup"><span data-stu-id="5100c-135">Use the **Add Output** and **Remove Output** buttons to manage the outputs of the source component.</span></span> <span data-ttu-id="5100c-136">すべての入力行は使用可能なすべての出力に送られます。ただし、出力の `ExclusionGroup` プロパティに 0 でない同じ値を指定すると、各行を、同じ `ExclusionGroup` の値を共有する出力のうちいずれか 1 つにのみ送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="5100c-136">All input rows are directed to all available outputs unless you also specify an identical non-zero value for the `ExclusionGroup` property of those outputs where you intend to direct each row to only one of the outputs that share the same `ExclusionGroup` value.</span></span> <span data-ttu-id="5100c-137">`ExclusionGroup` に指定するために選択した整数値に、特別な意味はありません。</span><span class="sxs-lookup"><span data-stu-id="5100c-137">The particular integer value selected to identify the `ExclusionGroup` is not significant.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5100c-138">すべての行を出力しない場合は、0 以外の `ExclusionGroup` プロパティ値を単一の出力で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5100c-138">You can also use a non-zero `ExclusionGroup` property value with a single output when you do not want to output all rows.</span></span> <span data-ttu-id="5100c-139">ただし、この場合は、出力に送信する各行について、**DirectRowTo\<outputbuffer>** メソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-139">In this case, however, you must explicitly call the **DirectRowTo\<outputbuffer>** method for each row that you want to send to the output.</span></span>

-   <span data-ttu-id="5100c-140">出力にはわかりやすい名前を付けておくことができます。</span><span class="sxs-lookup"><span data-stu-id="5100c-140">You may want to assign a friendly name to the outputs.</span></span> <span data-ttu-id="5100c-141">後で出力を参照する際には、スクリプト内での名前、および自動生成されたコードによって作成された、型指定されたアクセサー プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="5100c-141">Later, you will refer to the outputs by their names in your script, by using the typed accessor properties created for you in the auto-generated code.</span></span>

-   <span data-ttu-id="5100c-142">通常、同じ `ExclusionGroup` 内の複数の出力には、同じ出力列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5100c-142">Ordinarily multiple outputs in the same `ExclusionGroup` have the same output columns.</span></span> <span data-ttu-id="5100c-143">ただし、シミュレートされたエラー出力を作成するには、エラー情報を格納するために列の追加が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-143">However, if you are creating a simulated error output, you may want to add more columns to store error information.</span></span> <span data-ttu-id="5100c-144">データ フロー エンジンがエラー行を処理する方法については、「[データ フロー コンポーネントでのエラー出力の使用](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-144">For information about how the data flow engine processes error rows, see [Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md).</span></span> <span data-ttu-id="5100c-145">ただし、スクリプト コンポーネントでは、独自のコードを記述して、追加した列に該当するエラー情報を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-145">In the Script component, however, you must write your own code to fill the additional columns with appropriate error information.</span></span> <span data-ttu-id="5100c-146">詳細については、「[スクリプト コンポーネントに対するエラー出力のシミュレート](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-146">For more information, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="5100c-147">**[スクリプト変換エディター]** の **[入力および出力]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力および出力] ページ&#41;](../script-transformation-editor-inputs-and-outputs-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-147">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="5100c-148">変数の追加</span><span class="sxs-lookup"><span data-stu-id="5100c-148">Adding Variables</span></span>
 <span data-ttu-id="5100c-149">スクリプトで値を使用する既存の変数がある場合は、 `ReadOnlyVariables` [ `ReadWriteVariables` **スクリプト変換エディター**] の [**スクリプト**] ページで、プロパティおよびプロパティフィールドに追加できます。</span><span class="sxs-lookup"><span data-stu-id="5100c-149">If there are any existing variables whose values you want to use in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="5100c-150">プロパティ フィールドに複数の変数を入力する場合は、変数名をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="5100c-150">When you enter multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="5100c-151">また、プロパティフィールドの横にある省略記号 ([.**..**]) ボタンを `ReadOnlyVariables` クリック `ReadWriteVariables` し、 **[変数の選択**] ダイアログボックスで変数を選択することで、複数の変数を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="5100c-151">You can also enter multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields and selecting variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="5100c-152">スクリプト コンポーネントで変数を使用する方法に関する一般情報については、「[スクリプト コンポーネントでの変数の使用](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-152">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="5100c-153">**[スクリプト変換エディター]** の **[スクリプト]** ページの詳細については、「[[スクリプト変換エディター] &#40;[スクリプト] ページ&#41;](../script-transformation-editor-script-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-153">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-source-component-in-code-design-mode"></a><span data-ttu-id="5100c-154">コード デザイン モードでの変換元コンポーネントのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="5100c-154">Scripting a Source Component in Code-Design Mode</span></span>
 <span data-ttu-id="5100c-155">コンポーネントのメタデータを構成したら、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を開き、カスタム スクリプトのコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-155">After you have configured the metadata for your component, open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE to code your custom script.</span></span> <span data-ttu-id="5100c-156">VSTA を開くには、 **[スクリプト変換エディター]** の **[スクリプト]** ページで、 **[スクリプトの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5100c-156">To open VSTA, click **Edit Script** on the **Script** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="5100c-157">**[ScriptLanguage]** プロパティで選択したスクリプト言語に応じて [!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Basic または [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のいずれかを使用し、独自のスクリプトを記述できます。</span><span class="sxs-lookup"><span data-stu-id="5100c-157">You can write your script by using either [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#, depending on the script language selected for the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="5100c-158">スクリプト コンポーネントを使用して作成されたすべての種類のコンポーネントに適用される重要な情報については、「[スクリプト コンポーネントのコーディングおよびデバッグ](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-158">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="5100c-159">自動生成されたコードについて</span><span class="sxs-lookup"><span data-stu-id="5100c-159">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="5100c-160">変換元コンポーネントを作成、設定した後で VSTA IDE を開くと、コード エディターには `ScriptMain` クラスが編集可能な状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5100c-160">When you open the VSTA IDE after creating and configuring a source component, the editable `ScriptMain` class appears in the code editor.</span></span> <span data-ttu-id="5100c-161">この `ScriptMain` クラスにカスタム コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="5100c-161">You write your custom code in the `ScriptMain` class.</span></span>

 <span data-ttu-id="5100c-162">`ScriptMain` クラスには、`CreateNewOutputRows` メソッドのスタブが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5100c-162">The `ScriptMain` class includes a stub for the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="5100c-163">`CreateNewOutputRows` は、変換元コンポーネントの最重要メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5100c-163">The `CreateNewOutputRows` is the most important method in a source component.</span></span>

 <span data-ttu-id="5100c-164">VSTA で [**プロジェクトエクスプローラー** ] ウィンドウを開くと、スクリプトコンポーネントによって読み取り専用およびプロジェクト項目も生成されたことがわかり `BufferWrapper` `ComponentWrapper` ます。</span><span class="sxs-lookup"><span data-stu-id="5100c-164">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="5100c-165">`ScriptMain` クラスは、`UserComponent` プロジェクト アイテム内の `ComponentWrapper` クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="5100c-165">The `ScriptMain` class inherits from `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="5100c-166">実行時には、データ フロー エンジンが `PrimeOutput` クラスの `UserComponent` メソッドを呼び出します。これは親クラスである <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5100c-166">At run time, the data flow engine invokes the `PrimeOutput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="5100c-167">次に、`PrimeOutput` メソッドは次のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5100c-167">The `PrimeOutput` method in turn calls the following methods:</span></span>

1.  <span data-ttu-id="5100c-168">`CreateNewOutputRows` メソッド。これを `ScriptMain` でオーバーライドして、最初は空である出力バッファーに、データ ソースの行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5100c-168">The `CreateNewOutputRows` method, which you override in `ScriptMain` to add rows from the data source to the output buffers, which are empty at first.</span></span>

2.  <span data-ttu-id="5100c-169">`FinishOutputs` メソッド。既定では空です。</span><span class="sxs-lookup"><span data-stu-id="5100c-169">The `FinishOutputs` method, which is empty by default.</span></span> <span data-ttu-id="5100c-170">このメソッドを `ScriptMain` でオーバーライドして、出力を完了するために必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="5100c-170">Override this method in `ScriptMain` to perform any processing that is required to complete the output.</span></span>

3.  <span data-ttu-id="5100c-171">`MarkOutputsAsFinished` プライベート メソッド。これは、親クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> メソッドを呼び出し、出力が完了したことをデータ フロー エンジンに通知します。</span><span class="sxs-lookup"><span data-stu-id="5100c-171">The private `MarkOutputsAsFinished` method, which calls the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> parent class to indicate to the data flow engine that the output is finished.</span></span> <span data-ttu-id="5100c-172">独自に記述するコード内で、`SetEndOfRowset` を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5100c-172">You do not have to call `SetEndOfRowset` explicitly in your own code.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="5100c-173">カスタム コードの記述</span><span class="sxs-lookup"><span data-stu-id="5100c-173">Writing Your Custom Code</span></span>
 <span data-ttu-id="5100c-174">カスタム変換元コンポーネントの作成を終了するには、必要に応じて `ScriptMain` クラスで使用できる次のメソッドにスクリプトを記述する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-174">To finish creating a custom source component, you may want to write script in the following methods available in the `ScriptMain` class.</span></span>

1.  <span data-ttu-id="5100c-175">外部データ ソースに接続する場合は、`AcquireConnections` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5100c-175">Override the `AcquireConnections` method to connect to the external data source.</span></span> <span data-ttu-id="5100c-176">接続マネージャーから、接続オブジェクトまたは必要な接続情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="5100c-176">Extract the connection object, or the required connection information, from the connection manager.</span></span>

2.  <span data-ttu-id="5100c-177">変換元データをすべて同時に読み込める場合は、`PreExecute` メソッドをオーバーライドしてデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5100c-177">Override the `PreExecute` method to load data, if you can load all the source data at the same time.</span></span> <span data-ttu-id="5100c-178">たとえば、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースへの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続に対して `SqlCommand` を実行し、すべての変換元データを同時に `SqlDataReader` に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5100c-178">For example, you can execute a `SqlCommand` against an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and load all the source data at the same time into a `SqlDataReader`.</span></span> <span data-ttu-id="5100c-179">たとえば、テキスト ファイルを読み取る場合など、変換元データを 1 行ずつ読み込む必要がある場合は、`CreateNewOutputRows` の行をループするたびにデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5100c-179">If you must load the source data one row at a time (for example, when reading a text file), you can load the data as you loop through rows in `CreateNewOutputRows`.</span></span>

3.  <span data-ttu-id="5100c-180">オーバーライドされた `CreateNewOutputRows` メソッドを使用して、空の出力バッファーに新しい行を追加し、新しい出力行に各列の値を格納します。</span><span class="sxs-lookup"><span data-stu-id="5100c-180">Use the overridden `CreateNewOutputRows` method to add new rows to the empty output buffers and to fill in the values of each column in the new output rows.</span></span> <span data-ttu-id="5100c-181">各出力バッファーの `AddRow` メソッドを使用して空の行を新しく追加し、各列の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5100c-181">Use the `AddRow` method of each output buffer to add an empty new row, and then set the values of each column.</span></span> <span data-ttu-id="5100c-182">通常は、外部ソースから読み込まれた列から値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="5100c-182">Typically you copy values from the columns loaded from the external source.</span></span>

4.  <span data-ttu-id="5100c-183">`PostExecute` メソッドをオーバーライドして、データの処理を終了します。</span><span class="sxs-lookup"><span data-stu-id="5100c-183">Override the `PostExecute` method to finish processing the data.</span></span> <span data-ttu-id="5100c-184">たとえば、データを読み込むために使用した `SqlDataReader` を閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="5100c-184">For example, you can close the `SqlDataReader` that you used to load data.</span></span>

5.  <span data-ttu-id="5100c-185">`ReleaseConnections` メソッドを必要に応じてオーバーライドして、外部データ ソースとの接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="5100c-185">Override the `ReleaseConnections` method to disconnect from the external data source, if required.</span></span>

## <a name="examples"></a><span data-ttu-id="5100c-186">例</span><span class="sxs-lookup"><span data-stu-id="5100c-186">Examples</span></span>
 <span data-ttu-id="5100c-187">次の例では、変換元コンポーネントを作成するために、`ScriptMain` クラスで必要なカスタム コードを示します。</span><span class="sxs-lookup"><span data-stu-id="5100c-187">The following examples demonstrate the custom code that is required in the `ScriptMain` class to create a source component.</span></span>

> [!NOTE]
>  <span data-ttu-id="5100c-188">これらの例では、サンプルデータベースの**Person**テーブルを使用して、 `AdventureWorks` その第1列と第4列、つまり**intaddressid**列と**nvarchar (30) City**列をデータフローに渡します。</span><span class="sxs-lookup"><span data-stu-id="5100c-188">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="5100c-189">このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5100c-189">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="5100c-190">他の前提条件および仮定条件については、それぞれの例で説明します。</span><span class="sxs-lookup"><span data-stu-id="5100c-190">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="adonet-source-example"></a><span data-ttu-id="5100c-191">ADO.NET ソースの例</span><span class="sxs-lookup"><span data-stu-id="5100c-191">ADO.NET Source Example</span></span>
 <span data-ttu-id="5100c-192">この例では、既存の [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルからデータを読み込み、データ フローに送る変換元コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="5100c-192">This example demonstrates a source component that uses an existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to load data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into the data flow.</span></span>

 <span data-ttu-id="5100c-193">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-193">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="5100c-194">`SqlClient` プロバイダーを使用する [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを作成して、`AdventureWorks` データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="5100c-194">Create an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the `SqlClient` provider to connect to the `AdventureWorks` database.</span></span>

2.  <span data-ttu-id="5100c-195">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換元として構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-195">Add a new Script component to the Data Flow designer surface and configure it as a source.</span></span>

3.  <span data-ttu-id="5100c-196">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="5100c-196">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="5100c-197">**[入力および出力]** ページで、既定の出力を **MyAddressOutput** などのわかりやすい名前に変更し、**AddressID** と **City** という 2 つの出力列を追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-197">On the **Inputs and Outputs** page, rename the default output with a more descriptive name such as **MyAddressOutput**, and add and configure the two output columns, **AddressID** and **City**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5100c-198">**City** 出力列のデータ型は必ず DT_WSTR に変更してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-198">Be sure to change the data type of the **City** output column to DT_WSTR.</span></span>

4.  <span data-ttu-id="5100c-199">**[接続マネージャー]** ページで、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを追加または作成し、**MyADONETConnection** などの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5100c-199">On the **Connection Managers** page, add or create the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager and give it a name such as **MyADONETConnection**.</span></span>

5.  <span data-ttu-id="5100c-200">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="5100c-200">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="5100c-201">その後、スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="5100c-201">Then close the script development environment and the **Script Transformation Editor**.</span></span>

6.  <span data-ttu-id="5100c-202">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の変換先、または「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で説明されている変換先コンポーネントの例など、**AddressID** および **City** 列が予期される変換先コンポーネントを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-202">Create and configure a destination component, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), that expects the **AddressID** and **City** columns.</span></span> <span data-ttu-id="5100c-203">変換元のコンポーネントを変換先に接続します</span><span class="sxs-lookup"><span data-stu-id="5100c-203">Then connect the source component to the destination.</span></span> <span data-ttu-id="5100c-204">(変換を行わずに変換元を直接変換先に接続できます)。データベースで次のコマンドを実行して、変換先テーブルを作成でき [!INCLUDE[tsql](../../includes/tsql-md.md)] `AdventureWorks` ます。</span><span class="sxs-lookup"><span data-stu-id="5100c-204">(You can connect a source directly to a destination without any transformations.) You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

7.  <span data-ttu-id="5100c-205">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="5100c-205">Run the sample.</span></span>

    ```vb
    Imports System.Data.SqlClient
    ...
    Public Class ScriptMain
        Inherits UserComponent

        Dim connMgr As IDTSConnectionManager100
        Dim sqlConn As SqlConnection
        Dim sqlReader As SqlDataReader

        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

            connMgr = Me.Connections.MyADONETConnection
            sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

        End Sub

        Public Overrides Sub PreExecute()

            Dim cmd As New SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn)
            sqlReader = cmd.ExecuteReader

        End Sub

        Public Overrides Sub CreateNewOutputRows()

            Do While sqlReader.Read
                With MyAddressOutputBuffer
                    .AddRow()
                    .AddressID = sqlReader.GetInt32(0)
                    .City = sqlReader.GetString(1)
                End With
            Loop

        End Sub

        Public Overrides Sub PostExecute()

            sqlReader.Close()

        End Sub

        Public Overrides Sub ReleaseConnections()

            connMgr.ReleaseConnection(sqlConn)

        End Sub

    End Class
    ```

    ```csharp
    using System.Data.SqlClient;
    public class ScriptMain:
        UserComponent

    {
        IDTSConnectionManager100 connMgr;
        SqlConnection sqlConn;
        SqlDataReader sqlReader;

        public override void AcquireConnections(object Transaction)
        {
            connMgr = this.Connections.MyADONETConnection;
            sqlConn = (SqlConnection)connMgr.AcquireConnection(null);

        }

        public override void PreExecute()
        {

            SqlCommand cmd = new SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn);
            sqlReader = cmd.ExecuteReader();

        }

        public override void CreateNewOutputRows()
        {

            while (sqlReader.Read())
            {
                {
                    MyAddressOutputBuffer.AddRow();
                    MyAddressOutputBuffer.AddressID = sqlReader.GetInt32(0);
                    MyAddressOutputBuffer.City = sqlReader.GetString(1);
                }
            }

        }

        public override void PostExecute()
        {

            sqlReader.Close();

        }

        public override void ReleaseConnections()
        {

            connMgr.ReleaseConnection(sqlConn);

        }

    }
    ```

### <a name="flat-file-source-example"></a><span data-ttu-id="5100c-206">フラット ファイル ソースの例</span><span class="sxs-lookup"><span data-stu-id="5100c-206">Flat File Source Example</span></span>
 <span data-ttu-id="5100c-207">この例では、既存のフラット ファイル接続マネージャーを使用して、フラット ファイルからデータを読み込み、データ フローに送る変換元コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="5100c-207">This example demonstrates a source component that uses an existing Flat File connection manager to load data from a flat file into the data flow.</span></span> <span data-ttu-id="5100c-208">フラット ファイル ソースのデータは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からエクスポートすることにより作成されます。</span><span class="sxs-lookup"><span data-stu-id="5100c-208">The flat file source data is created by exporting it from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="5100c-209">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5100c-209">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="5100c-210">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポートウィザードを使用して、サンプルデータベースの**Person**テーブルを `AdventureWorks` コンマ区切りフラットファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="5100c-210">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard to export the **Person.Address** table from the `AdventureWorks` sample database to a comma-delimited flat file.</span></span> <span data-ttu-id="5100c-211">この例では、ファイル名を ExportedAddresses.txt とします。</span><span class="sxs-lookup"><span data-stu-id="5100c-211">This sample uses the file name ExportedAddresses.txt.</span></span>

2.  <span data-ttu-id="5100c-212">エクスポートされたデータ ファイルに接続するフラット ファイル接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-212">Create a Flat File connection manager that connects to the exported data file.</span></span>

3.  <span data-ttu-id="5100c-213">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換元として構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-213">Add a new Script component to the Data Flow designer surface and configure it as a source.</span></span>

4.  <span data-ttu-id="5100c-214">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="5100c-214">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="5100c-215">**[入力および出力]** ページで、既定の出力を **MyAddressOutput** などのわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="5100c-215">On the **Inputs and Outputs** page, rename the default output with a more descriptive name such as **MyAddressOutput**.</span></span> <span data-ttu-id="5100c-216">**AddressID** と **City** という 2 つの出力列を追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-216">Add and configure the two output columns, **AddressID** and **City**.</span></span>

5.  <span data-ttu-id="5100c-217">**[接続マネージャー]** ページで、**MyFlatFileSrcConnectionManager** などのわかりやすい名前を使用して、フラット ファイル接続マネージャーを追加または作成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-217">On the **Connection Managers** page, add or create the Flat File connection manager, using a descriptive name such as **MyFlatFileSrcConnectionManager**.</span></span>

6.  <span data-ttu-id="5100c-218">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="5100c-218">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="5100c-219">その後、スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="5100c-219">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="5100c-220">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の変換先、または「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で説明されている変換先コンポーネントの例など、変換先コンポーネントを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="5100c-220">Create and configure a destination component, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="5100c-221">変換元のコンポーネントを変換先に接続します</span><span class="sxs-lookup"><span data-stu-id="5100c-221">Then connect the source component to the destination.</span></span> <span data-ttu-id="5100c-222">(変換を行わずに変換元を直接変換先に接続できます)。データベースで次のコマンドを実行して、変換先テーブルを作成でき [!INCLUDE[tsql](../../includes/tsql-md.md)] `AdventureWorks` ます。</span><span class="sxs-lookup"><span data-stu-id="5100c-222">(You can connect a source directly to a destination without any transformations.) You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

8.  <span data-ttu-id="5100c-223">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="5100c-223">Run the sample.</span></span>

    ```vb
    Imports System.IO
    ...
    Public Class ScriptMain
        Inherits UserComponent

        Private textReader As StreamReader
        Private exportedAddressFile As String

        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

            Dim connMgr As IDTSConnectionManager100 = _
                Me.Connections.MyFlatFileSrcConnectionManager
            exportedAddressFile = _
                CType(connMgr.AcquireConnection(Nothing), String)

        End Sub

        Public Overrides Sub PreExecute()
            MyBase.PreExecute()
            textReader = New StreamReader(exportedAddressFile)
        End Sub

        Public Overrides Sub CreateNewOutputRows()

            Dim nextLine As String
            Dim columns As String()

            Dim delimiters As Char()
            delimiters = ",".ToCharArray

            nextLine = textReader.ReadLine
            Do While nextLine IsNot Nothing
                columns = nextLine.Split(delimiters)
                With MyAddressOutputBuffer
                    .AddRow()
                    .AddressID = columns(0)
                    .City = columns(3)
                End With
                nextLine = textReader.ReadLine
            Loop

        End Sub

        Public Overrides Sub PostExecute()
            MyBase.PostExecute()
            textReader.Close()

        End Sub

    End Class
    ```

    ```csharp
    using System.IO;
    public class ScriptMain:
        UserComponent

    {
        private StreamReader textReader;
        private string exportedAddressFile;

        public override void AcquireConnections(object Transaction)
        {

            IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileSrcConnectionManager;
            exportedAddressFile = (string)connMgr.AcquireConnection(null);

        }

        public override void PreExecute()
        {
            base.PreExecute();
            textReader = new StreamReader(exportedAddressFile);
        }

        public override void CreateNewOutputRows()
        {

            string nextLine;
            string[] columns;

            char[] delimiters;
            delimiters = ",".ToCharArray();

            nextLine = textReader.ReadLine();
            while (nextLine != null)
            {
                columns = nextLine.Split(delimiters);
                {
                    MyAddressOutputBuffer.AddRow();
                    MyAddressOutputBuffer.AddressID = columns[0];
                    MyAddressOutputBuffer.City = columns[3];
                }
                nextLine = textReader.ReadLine();
            }

        }

        public override void PostExecute()
        {

            base.PostExecute();
            textReader.Close();

        }

    }
    ```

<span data-ttu-id="5100c-224">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="5100c-224">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5100c-225">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5100c-225">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5100c-226">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="5100c-226">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5100c-227">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="5100c-227">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="5100c-228">参照</span><span class="sxs-lookup"><span data-stu-id="5100c-228">See Also</span></span>
 <span data-ttu-id="5100c-229">[スクリプトコンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)[カスタム変換元コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)</span><span class="sxs-lookup"><span data-stu-id="5100c-229">[Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md) [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)</span></span>


