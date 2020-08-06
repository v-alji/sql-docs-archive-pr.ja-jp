---
title: スクリプト コンポーネントによる変換先の作成 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1245dde111b24d1c37e2c5550d236c97126ee725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642921"
---
# <a name="creating-a-destination-with-the-script-component"></a><span data-ttu-id="ac6aa-102">スクリプト コンポーネントによる変換先の作成</span><span class="sxs-lookup"><span data-stu-id="ac6aa-102">Creating a Destination with the Script Component</span></span>
  <span data-ttu-id="ac6aa-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フロー内では、変換先コンポーネントを使用して、上流の変換元や変換から受け取ったデータをデータ ソースに保存します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-103">You use a destination component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to save data received from upstream sources and transformations to a data source.</span></span> <span data-ttu-id="ac6aa-104">通常、変換先コンポーネントをデータ ソースに接続するには、既存の接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-104">Ordinarily the destination component connects to the data source through an existing connection manager.</span></span>

 <span data-ttu-id="ac6aa-105">スクリプトコンポーネントの概要については、「スクリプトコンポーネントによるデータフローの拡張」 (../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="ac6aa-105">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span></span>

 <span data-ttu-id="ac6aa-106">スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-106">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="ac6aa-107">ただし、スクリプト コンポーネントのしくみを理解するため、「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」セクション、特に「[カスタム変換先コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)」を参照して、カスタム データ フロー コンポーネント開発の手順に目を通しておくと役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-107">However, to understand how the Script component works, you may find it useful to read through the steps for developing a custom data flow components in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).</span></span>

## <a name="getting-started-with-a-destination-component"></a><span data-ttu-id="ac6aa-108">変換先コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="ac6aa-108">Getting Started with a Destination Component</span></span>
 <span data-ttu-id="ac6aa-109">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [データ フロー] タブにスクリプト コンポーネントを追加すると、 **[スクリプト コンポーネントの種類を選択]** ダイアログ ボックスが開き、 **[変換元]** 、 **[変換先]** 、または **[変換]** スクリプトのいずれかを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-109">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a **Source**, **Destination**, or **Transformation** script.</span></span> <span data-ttu-id="ac6aa-110">このダイアログ ボックスで、 **[変換先]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-110">In this dialog box, select **Destination**.</span></span>

 <span data-ttu-id="ac6aa-111">次に、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、変換の出力を変換先コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-111">Next, connect the output of a transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ac6aa-112">テスト目的の場合、変換を介さずに変換元を直接変換先に接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-112">For testing, you can connect a source directly to a destination without any transformations.</span></span>

## <a name="configuring-a-destination-component-in-metadata-design-mode"></a><span data-ttu-id="ac6aa-113">メタデータ デザイン モードでの変換先コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="ac6aa-113">Configuring a Destination Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="ac6aa-114">変換先コンポーネントを作成するオプションを選択したら、 **[スクリプト変換エディター]** を使用して、コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-114">After you select the option to create a destination component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="ac6aa-115">詳細については、「[スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-115">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="ac6aa-116">スクリプト変換先で使用するスクリプト言語を選択するには、 **[スクリプト変換エディター]** ダイアログ ボックスの **[スクリプト]** ページにある **[ScriptLanguage]** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-116">To select the script language that the Script destination will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="ac6aa-117">スクリプト コンポーネントの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-117">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="ac6aa-118">詳細については、「 [General Page](../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-118">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="ac6aa-119">データ フローの変換先コンポーネントには、1 つの入力があり、出力はありません。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-119">A data flow destination component has one input and no outputs.</span></span> <span data-ttu-id="ac6aa-120">コンポーネントの入力の設定は、メタデータ デザイン モードでカスタム スクリプトを記述する前に完了する必要のある作業の 1 つです。これを行うには、 **[スクリプト変換エディター]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-120">Configuring the input for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="adding-connection-managers"></a><span data-ttu-id="ac6aa-121">接続マネージャーの追加</span><span class="sxs-lookup"><span data-stu-id="ac6aa-121">Adding Connection Managers</span></span>
 <span data-ttu-id="ac6aa-122">通常、変換先コンポーネントは既存の接続マネージャーを使用してデータ ソースに接続し、データ フローからのデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-122">Ordinarily a destination component uses an existing connection manager to connect to the data source to which it saves data from the data flow.</span></span> <span data-ttu-id="ac6aa-123">**[スクリプト変換エディター]** の **[接続マネージャー]** ページで **[追加]** をクリックして、適切な接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-123">On the **Connection Managers** page of the **Script Transformation Editor**, click **Add** to add the appropriate connection manager.</span></span>

 <span data-ttu-id="ac6aa-124">ただし、接続マネージャーは、便宜上、特定の種類のデータ ソースに接続するために必要な情報をカプセル化して格納するユニットにすぎません。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-124">However, a connection manager is just a convenient unit that encapsulates and stores the information that is required to connect to a data source of a particular type.</span></span> <span data-ttu-id="ac6aa-125">データの読み込みや保存、場合によってはデータ ソースとの接続や切断を行うためには、独自のカスタム コードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-125">You must write your own custom code to load or save your data, and possibly to open and close the connection to the data source.</span></span>

 <span data-ttu-id="ac6aa-126">スクリプト コンポーネントで接続マネージャーを使用する方法の一般情報については、「[スクリプト コンポーネントでのデータ ソースへの接続](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-126">For general information about how to use connection managers with the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).</span></span>

 <span data-ttu-id="ac6aa-127">**[スクリプト変換エディター]** の **[接続マネージャー]** ページの詳細については、「[スクリプト変換エディター &#40;[接続マネージャー] ページ&#41;](../script-transformation-editor-connection-managers-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-127">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Connection Managers Page&#41;](../script-transformation-editor-connection-managers-page.md).</span></span>

### <a name="configuring-inputs-and-input-columns"></a><span data-ttu-id="ac6aa-128">入力および入力列の設定</span><span class="sxs-lookup"><span data-stu-id="ac6aa-128">Configuring Inputs and Input Columns</span></span>
 <span data-ttu-id="ac6aa-129">変換先コンポーネントには、1 つの入力があり、出力はありません。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-129">A destination component has one input and no outputs.</span></span>

 <span data-ttu-id="ac6aa-130">**[スクリプト変換エディター]** の **[入力列]** ページには、データ フローの上流コンポーネントの出力で使用できる列が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-130">On the **Input Columns** page of the **Script Transformation Editor**, the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="ac6aa-131">保存する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-131">Select the columns that you want to save.</span></span>

 <span data-ttu-id="ac6aa-132">**[スクリプト変換エディター]** の **[入力列]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力列] ページ&#41;](../script-transformation-editor-input-columns-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-132">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

 <span data-ttu-id="ac6aa-133">**[スクリプト変換エディター]** の **[入力および出力]** ページには入力が 1 つ表示されています。この入力の名前は変更できます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-133">The **Inputs and Outputs** page of the **Script Transformation Editor** shows a single input, which you can rename.</span></span> <span data-ttu-id="ac6aa-134">スクリプト内ではこの名前で入力を参照しますが、参照には自動生成されたコードによって作成されたアクセサー プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-134">You will refer to the input by its name in your script by using the accessor property created in the auto-generated code.</span></span>

 <span data-ttu-id="ac6aa-135">**[スクリプト変換エディター]** の **[入力および出力]** ページの詳細については、「[[スクリプト変換エディター] &#40;[入力および出力] ページ&#41;](../script-transformation-editor-inputs-and-outputs-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-135">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="ac6aa-136">変数の追加</span><span class="sxs-lookup"><span data-stu-id="ac6aa-136">Adding Variables</span></span>
 <span data-ttu-id="ac6aa-137">スクリプトで既存の変数を使用する場合は、 `ReadOnlyVariables` [ `ReadWriteVariables` **スクリプト変換エディター**] の [**スクリプト**] ページで、プロパティおよびプロパティフィールドに追加できます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-137">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="ac6aa-138">プロパティ フィールドに複数の変数を追加する場合は、各変数名をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-138">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="ac6aa-139">また、プロパティフィールドの横にある省略記号 ([.**..**]) ボタンをクリックし、[ `ReadOnlyVariables` `ReadWriteVariables` **変数の選択**] ダイアログボックスで変数を選択することで、複数の変数を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-139">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="ac6aa-140">スクリプト コンポーネントで変数を使用する方法に関する一般情報については、「[スクリプト コンポーネントでの変数の使用](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-140">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="ac6aa-141">**[スクリプト変換エディター]** の **[スクリプト]** ページの詳細については、「[[スクリプト変換エディター] &#40;[スクリプト] ページ&#41;](../script-transformation-editor-script-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-141">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-destination-component-in-code-design-mode"></a><span data-ttu-id="ac6aa-142">コード デザイン モードでの変換先コンポーネントのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="ac6aa-142">Scripting a Destination Component in Code-Design Mode</span></span>
 <span data-ttu-id="ac6aa-143">コンポーネントのメタデータを構成した後、カスタム スクリプトを記述できます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-143">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="ac6aa-144">**[スクリプト変換エディター]** の **[スクリプト]** ページで **[スクリプトの編集]** をクリックし、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を開いて、カスタム スクリプトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-144">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="ac6aa-145">使用するスクリプト言語は、 **[スクリプト]** ページの **[ScriptLanguage]** プロパティで、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のどちらをスクリプト言語として選択したかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-145">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="ac6aa-146">スクリプト コンポーネントを使用して作成されたすべての種類のコンポーネントに適用される重要な情報については、「[スクリプト コンポーネントのコーディングおよびデバッグ](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-146">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="ac6aa-147">自動生成されたコードについて</span><span class="sxs-lookup"><span data-stu-id="ac6aa-147">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="ac6aa-148">変換先コンポーネントを作成、構成した後で VSTA IDE を開くと、コード エディターには `ScriptMain` クラスが編集可能な状態で表示されます。また、`ProcessInputRow` メソッドがスタブとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-148">When you open the VSTA IDE after you create and configuring a destination component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="ac6aa-149">カスタム コードは `ScriptMain` クラスに記述します。また、`ProcessInputRow` は変換先コンポーネントの最重要メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-149">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a destination component.</span></span>

 <span data-ttu-id="ac6aa-150">VSTA で [**プロジェクトエクスプローラー** ] ウィンドウを開くと、スクリプトコンポーネントによって読み取り専用およびプロジェクト項目も生成されたことがわかり `BufferWrapper` `ComponentWrapper` ます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-150">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="ac6aa-151">`ScriptMain` クラスは、`UserComponent` プロジェクト アイテム内の `ComponentWrapper` クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-151">The `ScriptMain` class inherits from `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="ac6aa-152">実行時には、データ フロー エンジンが `ProcessInput` クラスの `UserComponent` メソッドを呼び出します。これは親クラスである <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-152">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="ac6aa-153">`ProcessInput` メソッドは、入力バッファーに格納された行を順にループし、各行で 1 回ずつ `ProcessInputRow` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-153">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="ac6aa-154">カスタム コードの記述</span><span class="sxs-lookup"><span data-stu-id="ac6aa-154">Writing Your Custom Code</span></span>
 <span data-ttu-id="ac6aa-155">カスタム変換先コンポーネントの作成を終了するには、必要に応じて `ScriptMain` クラスで使用できる次のメソッドにスクリプトを記述する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-155">To finish creating a custom destination component, you may want to write script in the following methods available in the `ScriptMain` class.</span></span>

1.  <span data-ttu-id="ac6aa-156">外部データ ソースに接続する場合は、`AcquireConnections` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-156">Override the `AcquireConnections` method to connect to the external data source.</span></span> <span data-ttu-id="ac6aa-157">接続マネージャーから、接続オブジェクトまたは必要な接続情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-157">Extract the connection object, or the required connection information, from the connection manager.</span></span>

2.  <span data-ttu-id="ac6aa-158">データを保存する準備のため、`PreExecute` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-158">Override the `PreExecute` method to prepare to save the data.</span></span> <span data-ttu-id="ac6aa-159">たとえば、このメソッド内で `SqlCommand` およびそのパラメーターを作成し、設定することができます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-159">For example, you may want to create and configure a `SqlCommand` and its parameters in this method.</span></span>

3.  <span data-ttu-id="ac6aa-160">各入力行を外部データ ソースにコピーするには、オーバーライドされた `ProcessInputRow` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-160">Use the overridden `ProcessInputRow` method to copy each input row to the external data source.</span></span> <span data-ttu-id="ac6aa-161">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先の場合、列の値を `SqlCommand` のパラメーターにコピーし、各行で 1 回ずつコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-161">For example, for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, you can copy the column values into the parameters of a `SqlCommand` and execute the command one time for each row.</span></span> <span data-ttu-id="ac6aa-162">フラット ファイル変換先の場合、各列の値を列区切り記号で区切って `StreamWriter` に書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-162">For a flat file destination, you can write the values for each column to a `StreamWriter`, separating the values by the column delimiter.</span></span>

4.  <span data-ttu-id="ac6aa-163">必要に応じて外部データ ソースとの接続を切断し、その他の必要なクリーンアップ作業を実行するには、`PostExecute` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-163">Override the `PostExecute` method to disconnect from the external data source, if required, and to perform any other required cleanup.</span></span>

## <a name="examples"></a><span data-ttu-id="ac6aa-164">例</span><span class="sxs-lookup"><span data-stu-id="ac6aa-164">Examples</span></span>
 <span data-ttu-id="ac6aa-165">次の例では、変換先コンポーネントを作成するために `ScriptMain` クラスで必要なコードを示します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-165">The examples that follow demonstrate code that is required in the `ScriptMain` class to create a destination component.</span></span>

> [!NOTE]
>  <span data-ttu-id="ac6aa-166">これらの例では、サンプルデータベースの**Person**テーブルを使用して、 `AdventureWorks` その第1列と第4列、つまり**int \* addressid**\* および**nvarchar (30) City**列をデータフローに渡します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-166">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="ac6aa-167">このセクションの変換元、変換、および変換先の例でも、同じデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-167">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="ac6aa-168">他の前提条件および仮定条件については、それぞれの例で説明します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-168">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="adonet-destination-example"></a><span data-ttu-id="ac6aa-169">ADO.NET 変換先の例</span><span class="sxs-lookup"><span data-stu-id="ac6aa-169">ADO.NET Destination Example</span></span>
 <span data-ttu-id="ac6aa-170">この例では、既存の [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用して、データ フローのデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存する変換先コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-170">This example demonstrates a destination component that uses an existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to save data from the data flow into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="ac6aa-171">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-171">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="ac6aa-172">`SqlClient` プロバイダーを使用する [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを作成して、`AdventureWorks` データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-172">Create an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the `SqlClient` provider to connect to the `AdventureWorks` database.</span></span>

2.  <span data-ttu-id="ac6aa-173">`AdventureWorks` データベースで次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行して、変換先テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-173">Create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

3.  <span data-ttu-id="ac6aa-174">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-174">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

4.  <span data-ttu-id="ac6aa-175">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します</span><span class="sxs-lookup"><span data-stu-id="ac6aa-175">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ac6aa-176">(変換を行わずに変換元を直接変換先に接続できます)。この出力では、 **Person.Address** `AdventureWorks` 少なくとも**Addressid**列と**City**列を含むサンプルデータベースの Person テーブルからデータを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-176">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="ac6aa-177">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-177">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="ac6aa-178">**[入力列]** ページで、**AddressID** 入力列と **City** 入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-178">On the **Input Columns** page, select the **AddressID** and **City** input columns.</span></span>

6.  <span data-ttu-id="ac6aa-179">**[入力および出力]** ページで、入力を **MyAddressInput** などのわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-179">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>

7.  <span data-ttu-id="ac6aa-180">**[接続マネージャー]** ページで、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを追加または作成し、**MyADONETConnectionManager** などの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-180">On the **Connection Managers** page, add or create the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager with a name such as **MyADONETConnectionManager**.</span></span>

8.  <span data-ttu-id="ac6aa-181">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-181">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="ac6aa-182">スクリプト開発環境を閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-182">Then close the script development environment.</span></span>

9. <span data-ttu-id="ac6aa-183">**[スクリプト変換エディター]** を閉じ、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-183">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.Data.SqlClient
...
Public Class ScriptMain
    Inherits UserComponent

    Dim connMgr As IDTSConnectionManager100
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        connMgr = Me.Connections.MyADONETConnectionManager
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

    End Sub

    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)
        With sqlCmd
            .Parameters("@addressid").Value = Row.AddressID
            .Parameters("@city").Value = Row.City
            .ExecuteNonQuery()
        End With
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
    SqlCommand sqlCmd;
    SqlParameter sqlParam;

    public override void AcquireConnections(object Transaction)
    {

        connMgr = this.Connections.MyADONETConnectionManager;
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +
            "VALUES(@addressid, @city)", sqlConn);
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);
        sqlCmd.Parameters.Add(sqlParam);
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);
        sqlCmd.Parameters.Add(sqlParam);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {
        {
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;
            sqlCmd.Parameters["@city"].Value = Row.City;
            sqlCmd.ExecuteNonQuery();
        }
    }

    public override void ReleaseConnections()
    {

        connMgr.ReleaseConnection(sqlConn);

    }

}
```

### <a name="flat-file-destination-example"></a><span data-ttu-id="ac6aa-184">フラット ファイル変換先の例</span><span class="sxs-lookup"><span data-stu-id="ac6aa-184">Flat File Destination Example</span></span>
 <span data-ttu-id="ac6aa-185">この例では、既存のフラット ファイル接続マネージャーを使用して、データ フローのデータをフラット ファイルに保存する変換先コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-185">This example demonstrates a destination component that uses an existing Flat File connection manager to save data from the data flow to a flat file.</span></span>

 <span data-ttu-id="ac6aa-186">このサンプル コードを実行する場合は、パッケージやコンポーネントを次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-186">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="ac6aa-187">変換先ファイルに接続するフラット ファイル接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-187">Create a Flat File connection manager that connects to a destination file.</span></span> <span data-ttu-id="ac6aa-188">ファイルが存在しない場合は、変換先コンポーネントによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-188">The file does not have to exist; the destination component will create it.</span></span> <span data-ttu-id="ac6aa-189">変換先ファイルを、**AddressID** 列および **City** 列を含む、コンマ区切りファイルとして構成します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-189">Configure the destination file as a comma-delimited file that contains the **AddressID** and **City** columns.</span></span>

2.  <span data-ttu-id="ac6aa-190">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-190">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

3.  <span data-ttu-id="ac6aa-191">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します</span><span class="sxs-lookup"><span data-stu-id="ac6aa-191">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ac6aa-192">(変換を行わずに変換元を直接変換先に接続できます)。この出力では、サンプルデータベースの**Person**テーブルからデータを提供する必要があり `AdventureWorks` ます。また、少なくとも**Addressid**列と**City**列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-192">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database, and should contain at least the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="ac6aa-193">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-193">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="ac6aa-194">**[入力列]** ページで、**AddressID** 列と **City** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-194">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="ac6aa-195">**[入力および出力]** ページで、入力を **MyAddressInput** などのわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-195">On the **Inputs and Outputs** page, rename the input with a more descriptive name, such as **MyAddressInput**.</span></span>

6.  <span data-ttu-id="ac6aa-196">**[接続マネージャー]** ページで、フラット ファイル接続マネージャーを追加または作成し、**MyFlatFileDestConnectionManager** などのわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-196">On the **Connection Managers** page, add or create the Flat File connection manager with a descriptive name such as **MyFlatFileDestConnectionManager**.</span></span>

7.  <span data-ttu-id="ac6aa-197">**[スクリプト]** ページで、 **[スクリプトの編集]** をクリックし、続きのスクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-197">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="ac6aa-198">スクリプト開発環境を閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-198">Then close the script development environment.</span></span>

8.  <span data-ttu-id="ac6aa-199">**[スクリプト変換エディター]** を閉じ、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-199">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.IO
...
Public Class ScriptMain
    Inherits UserComponent

    Dim copiedAddressFile As String
    Private textWriter As StreamWriter
    Private columnDelimiter As String = ","

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        Dim connMgr As IDTSConnectionManager100 = _
            Me.Connections.MyFlatFileDestConnectionManager
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)

    End Sub

    Public Overrides Sub PreExecute()

        textWriter = New StreamWriter(copiedAddressFile, False)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With textWriter
            If Not Row.AddressID_IsNull Then
                .Write(Row.AddressID)
            End If
            .Write(columnDelimiter)
            If Not Row.City_IsNull Then
                .Write(Row.City)
            End If
            .WriteLine()
        End With

    End Sub

    Public Overrides Sub PostExecute()

        textWriter.Close()

    End Sub

End Class
```

```csharp
using System.IO;
public class ScriptMain:
    UserComponent

{
    string copiedAddressFile;
    private StreamWriter textWriter;
    private string columnDelimiter = ",";

    public override void AcquireConnections(object Transaction)
    {

        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;
        copiedAddressFile = (string) connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        textWriter = new StreamWriter(copiedAddressFile, false);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            if (!Row.AddressID_IsNull)
            {
                textWriter.Write(Row.AddressID);
            }
            textWriter.Write(columnDelimiter);
            if (!Row.City_IsNull)
            {
                textWriter.Write(Row.City);
            }
            textWriter.WriteLine();
        }

    }

    public override void PostExecute()
    {

        textWriter.Close();

    }

}
```

<span data-ttu-id="ac6aa-200">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="ac6aa-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ac6aa-201">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ac6aa-202">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="ac6aa-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ac6aa-203">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="ac6aa-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac6aa-204">参照</span><span class="sxs-lookup"><span data-stu-id="ac6aa-204">See Also</span></span>
 <span data-ttu-id="ac6aa-205">[スクリプトコンポーネントによる変換元の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)[カスタム変換先コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span><span class="sxs-lookup"><span data-stu-id="ac6aa-205">[Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span></span>


