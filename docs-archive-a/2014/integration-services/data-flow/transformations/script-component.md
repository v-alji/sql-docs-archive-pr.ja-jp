---
title: スクリプト コンポーネント | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponentdetails.f1
helpviewer_keywords:
- Script transformation
- scripts [Integration Services], transformations
- Script component [Integration Services], about Script component
- Script component [Integration Services]
ms.assetid: 131c2d0c-2e33-4785-94af-ada5c049821e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af8e500e399b0f69a7e34c9e2e01c74d83256107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743414"
---
# <a name="script-component"></a><span data-ttu-id="f5424-102">スクリプト コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f5424-102">Script Component</span></span>
  <span data-ttu-id="f5424-103">スクリプト コンポーネントはスクリプトをホストします。これにより、パッケージにカスタム スクリプト コードを含めて実行できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-103">The Script component hosts script and enables a package to include and run custom script code.</span></span> <span data-ttu-id="f5424-104">スクリプト コンポーネントは、パッケージ内で次の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-104">You can use the Script component in packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="f5424-105">複数の変換をデータ フロー内で使用する代わりに、複数の変換をデータに適用します。</span><span class="sxs-lookup"><span data-stu-id="f5424-105">Apply multiple transformations to data instead of using multiple transformations in the data flow.</span></span> <span data-ttu-id="f5424-106">たとえば、スクリプトによって 2 つの列に値を追加し、その合計の平均を計算できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-106">For example, a script can add the values in two columns and then calculate the average of the sum.</span></span>  
  
-   <span data-ttu-id="f5424-107">既存の .NET アセンブリのビジネス ルールにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f5424-107">Access business rules in an existing .NET assembly.</span></span> <span data-ttu-id="f5424-108">たとえば、スクリプトによって `Income` 列で有効な値の範囲を指定するビジネス ルールを適用できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-108">For example, a script can apply a business rule that specifies the range of values that are valid in an `Income` column.</span></span>  
  
-   <span data-ttu-id="f5424-109">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 式の文法で定められた関数や演算子以外のカスタム式とカスタム関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5424-109">Use custom formulas and functions in addition to the functions and operators that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expression grammar provides.</span></span> <span data-ttu-id="f5424-110">たとえば、LUHN 式を使用して、クレジット カード番号を検証します。</span><span class="sxs-lookup"><span data-stu-id="f5424-110">For example, validate credit card numbers that use the LUHN formula.</span></span>  
  
-   <span data-ttu-id="f5424-111">列データを検証し、無効なデータを含むレコードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="f5424-111">Validate column data and skip records that contain invalid data.</span></span> <span data-ttu-id="f5424-112">たとえば、スクリプトを使用すると、郵送料が妥当かどうかを査定して、極端に高い場合や極端に安い場合にレコードをスキップできます。</span><span class="sxs-lookup"><span data-stu-id="f5424-112">For example, a script can assess the reasonableness of a postage amount and skip records with extremely high or low amounts.</span></span>  
  
 <span data-ttu-id="f5424-113">スクリプト コンポーネントを使用すると、カスタム関数をデータ フローへ簡単、迅速に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f5424-113">The Script component provides an easy and quick way to include custom functions in a data flow.</span></span> <span data-ttu-id="f5424-114">ただし、複数のパッケージでスクリプト コードを再利用する場合、スクリプト コンポーネントを使用するのではなく、カスタム コンポーネントをプログラムすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f5424-114">However, if you plan to reuse the script code in multiple packages, you should consider programming a custom component instead of using the Script component.</span></span> <span data-ttu-id="f5424-115">詳細については、「 [カスタム データ フロー コンポーネントの開発](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-115">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5424-116">スクリプト コンポーネントに値が NULL である列の読み取りを試みるスクリプトが含まれる場合は、パッケージを実行すると、スクリプト コンポーネントが失敗します。</span><span class="sxs-lookup"><span data-stu-id="f5424-116">If the Script component contains a script that tries to read the value of a column that is NULL, the Script component fails when you run the package.</span></span> <span data-ttu-id="f5424-117">スクリプトでは <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> メソッドを使用して、列の値の読み取りを試みる前に列が NULL かどうかを判断することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f5424-117">We recommend that your script use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> method to determine whether the column is NULL before trying to read the column value.</span></span>  
  
 <span data-ttu-id="f5424-118">スクリプト コンポーネントは、変換元、変換、または変換先として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-118">The Script component can be used as a source, a transformation, or a destination.</span></span> <span data-ttu-id="f5424-119">このコンポーネントは、1 つの入力と複数の出力をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f5424-119">This component supports one input and multiple outputs.</span></span> <span data-ttu-id="f5424-120">コンポーネントの使用方法に応じて、入力または出力のどちらか、またはその両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5424-120">Depending on how the component is used, it supports either an input or outputs or both.</span></span> <span data-ttu-id="f5424-121">スクリプトは、入力または出力の列ごとに起動します。</span><span class="sxs-lookup"><span data-stu-id="f5424-121">The script is invoked by every row in the input or output.</span></span>  
  
-   <span data-ttu-id="f5424-122">スクリプト コンポーネントを変換元として使用する場合、複数の出力がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5424-122">If used as a source, the Script component supports multiple outputs.</span></span>  
  
-   <span data-ttu-id="f5424-123">スクリプト コンポーネントを変換として使用する場合、1 つの入力と複数の出力がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5424-123">If used as a transformation, the Script component supports one input and multiple outputs.</span></span>  
  
-   <span data-ttu-id="f5424-124">スクリプト コンポーネントを変換先として使用する場合、1 つの入力がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5424-124">If used as a destination, the Script component supports one input.</span></span>  
  
 <span data-ttu-id="f5424-125">スクリプト コンポーネントでは、エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f5424-125">The Script component does not support error outputs.</span></span>  
  
 <span data-ttu-id="f5424-126">スクリプト コンポーネントがパッケージにとって適切な選択である場合、入力と出力を構成し、コンポーネントが使用するスクリプトを開発して、コンポーネント自体を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5424-126">After you decide that the Script component is the appropriate choice for your package, you have to configure the inputs and outputs, develop the script that the component uses, and configure the component itself.</span></span>  
  
## <a name="understanding-the-script-component-modes"></a><span data-ttu-id="f5424-127">スクリプト コンポーネントのモードについて</span><span class="sxs-lookup"><span data-stu-id="f5424-127">Understanding the Script Component Modes</span></span>  
 <span data-ttu-id="f5424-128">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでは、スクリプト コンポーネントにメタデータ デザイン モードとコード デザイン モードの 2 つのモードがあります。</span><span class="sxs-lookup"><span data-stu-id="f5424-128">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata-design mode and code-design mode.</span></span> <span data-ttu-id="f5424-129">メタデータ デザイン モードでは、スクリプト コンポーネントの入力と出力を追加および変更できますが、コードは記述できません。</span><span class="sxs-lookup"><span data-stu-id="f5424-129">In metadata-design mode, you can add and modify the Script component inputs and outputs, but you cannot write code.</span></span> <span data-ttu-id="f5424-130">すべての入力と出力を構成した後に、コード デザイン モードに切り替え、スクリプトを記述します。</span><span class="sxs-lookup"><span data-stu-id="f5424-130">After all the inputs and outputs are configured, you switch to code-design mode to write the script.</span></span> <span data-ttu-id="f5424-131">スクリプト コンポーネントは、入力と出力のメタデータから、基本コードを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="f5424-131">The Script component automatically generates base code from the metadata of the inputs and outputs.</span></span> <span data-ttu-id="f5424-132">スクリプト コンポーネントで基本コードを生成した後にメタデータを変更すると、更新された基本コードと互換性がない可能性があるため、記述したコードをコンパイルできないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f5424-132">If you change the metadata after the Script component generates the base code, your code may no longer compile because the updated base code may be incompatible with your code.</span></span>  
  
## <a name="writing-the-script-that-the-component-uses"></a><span data-ttu-id="f5424-133">コンポーネントが使用するスクリプトの記述</span><span class="sxs-lookup"><span data-stu-id="f5424-133">Writing the Script that the Component Uses</span></span>  
 <span data-ttu-id="f5424-134">スクリプト コンポーネントでは、スクリプトを記述する環境として [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f5424-134">The Script component uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts.</span></span> <span data-ttu-id="f5424-135">**スクリプト変換エディター**から VSTA にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f5424-135">You access VSTA from the **Script Transformation Editor**.</span></span> <span data-ttu-id="f5424-136">詳細については、「 [スクリプト変換エディター ([スクリプト] ページ)](../../script-transformation-editor-script-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-136">For more information, see [Script Transformation Editor &#40;Script Page&#41;](../../script-transformation-editor-script-page.md).</span></span>  
  
 <span data-ttu-id="f5424-137">スクリプト コンポーネントでは、コンポーネントのメタデータを表す、ScriptMain という名前の自動生成クラスが含まれる VSTA プロジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f5424-137">The Script component provides a VSTA project that includes an auto-generated class, named ScriptMain, that represents the component metadata.</span></span> <span data-ttu-id="f5424-138">たとえば、スクリプト コンポーネントを 3 つの出力を持つ変換として使用する場合、ScriptMain には各出力のメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5424-138">For example, if the Script component is used as a transformation that has three outputs, ScriptMain includes a method for each output.</span></span> <span data-ttu-id="f5424-139">ScriptMain は、スクリプトに対するエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="f5424-139">ScriptMain is the entry point to the script.</span></span>  
  
 <span data-ttu-id="f5424-140">VSTA には、色分け表示が可能な [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] エディター、IntelliSense、オブジェクト ブラウザーなど、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 環境での標準機能がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="f5424-140">VSTA includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span> <span data-ttu-id="f5424-141">スクリプト コンポーネントが使用するスクリプトは、パッケージ定義に格納されます。</span><span class="sxs-lookup"><span data-stu-id="f5424-141">The script that the Script component uses is stored in the package definition.</span></span> <span data-ttu-id="f5424-142">パッケージをデザインする際、スクリプト コードは一時的にプロジェクト ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="f5424-142">When you are designing the package, the script code is temporarily written to a project file.</span></span>  
  
 <span data-ttu-id="f5424-143">VSTA では、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# と [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic の両方のプログラミング言語がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5424-143">VSTA supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic programming languages.</span></span>  
  
 <span data-ttu-id="f5424-144">スクリプト コンポーネントのプログラミング方法の詳細については、「 [スクリプト コンポーネントによるデータ フローの拡張](script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-144">For information about how to program the Script component, see [Extending the Data Flow with the Script Component](script-component.md).</span></span> <span data-ttu-id="f5424-145">スクリプト コンポーネントを変換元、変換、または変換先として構成する方法の詳細については、「 [特定の種類のスクリプト コンポーネントの開発](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-145">For more specific information about how to configure the Script component as a source, transformation, or destination, see [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span> <span data-ttu-id="f5424-146">ODBC 変換先など、スクリプト コンポーネントの使用法を示すその他の例については、「 [その他のスクリプト コンポーネントの例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-146">For additional examples such as an ODBC destination that demonstrate the use of the Script component, see [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5424-147">スクリプトをプリコンパイルするかどうかを指定できた以前のバージョンとは異なり、 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 以降のバージョンではすべてのスクリプトがプリコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="f5424-147">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="f5424-148">スクリプトがプリコンパイルされると、実行時に言語エンジンを読み込まないため、パッケージの実行速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="f5424-148">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="f5424-149">ただし、コンパイル済みのバイナリ ファイルは多量のディスク領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5424-149">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-component"></a><span data-ttu-id="f5424-150">スクリプト コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="f5424-150">Configuring the Script Component</span></span>  
 <span data-ttu-id="f5424-151">スクリプト コンポーネントは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-151">You can configure the Script component in the following ways:</span></span>  
  
-   <span data-ttu-id="f5424-152">参照する入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f5424-152">Select the input columns to reference.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f5424-153">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーを使用する場合、入力は 1 つのみ構成できます。</span><span class="sxs-lookup"><span data-stu-id="f5424-153">You can configure only one input when you use the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
-   <span data-ttu-id="f5424-154">コンポーネントが実行するスクリプトを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5424-154">Provide the script that the component runs.</span></span>  
  
-   <span data-ttu-id="f5424-155">スクリプト言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="f5424-155">Specify the script language.</span></span>  
  
-   <span data-ttu-id="f5424-156">読み取り専用変数と読み取り/書き込み変数を、コンマで区切られた一覧にして指定します。</span><span class="sxs-lookup"><span data-stu-id="f5424-156">Provide comma-separated lists of read-only and read/write variables.</span></span>  
  
-   <span data-ttu-id="f5424-157">出力を追加し、スクリプトが値を割り当てる出力列を追加します。</span><span class="sxs-lookup"><span data-stu-id="f5424-157">Add more outputs, and add output columns to which the script assigns.</span></span>  
  
 <span data-ttu-id="f5424-158">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="f5424-158">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-component-in-the-designer"></a><span data-ttu-id="f5424-159">デザイナーでのスクリプト コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="f5424-159">Configuring the Script Component in the Designer</span></span>  
 <span data-ttu-id="f5424-160">**[スクリプト変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-160">For more information about the properties that you can set in the **Script Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="f5424-161">[スクリプト変換エディター ([入力列] ページ)](../../script-transformation-editor-input-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="f5424-161">[Script Transformation Editor &#40;Input Columns Page&#41;](../../script-transformation-editor-input-columns-page.md)</span></span>  
  
-   <span data-ttu-id="f5424-162">[スクリプト変換エディター ([入力および出力] ページ)](../../script-transformation-editor-inputs-and-outputs-page.md)</span><span class="sxs-lookup"><span data-stu-id="f5424-162">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../script-transformation-editor-inputs-and-outputs-page.md)</span></span>  
  
-   <span data-ttu-id="f5424-163">[スクリプト変換エディター ([スクリプト] ページ)](../../script-transformation-editor-script-page.md)</span><span class="sxs-lookup"><span data-stu-id="f5424-163">[Script Transformation Editor &#40;Script Page&#41;](../../script-transformation-editor-script-page.md)</span></span>  
  
-   <span data-ttu-id="f5424-164">[スクリプト変換エディター ([接続マネージャー] ページ)](../../script-transformation-editor-connection-managers-page.md)</span><span class="sxs-lookup"><span data-stu-id="f5424-164">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../script-transformation-editor-connection-managers-page.md)</span></span>  
  
 <span data-ttu-id="f5424-165">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-165">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f5424-166">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="f5424-166">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
### <a name="configuring-the-script-component-programmatically"></a><span data-ttu-id="f5424-167">プログラムによるスクリプト コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="f5424-167">Configuring the Script Component Programmatically</span></span>  
 <span data-ttu-id="f5424-168">**[プロパティ]** ウィンドウまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-168">For more information about the properties that you can set in the **Properties** window or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f5424-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="f5424-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="f5424-170">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="f5424-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="f5424-171">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5424-171">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f5424-172">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="f5424-172">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="f5424-173">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="f5424-173">Related Content</span></span>  
 [<span data-ttu-id="f5424-174">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="f5424-174">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
 [<span data-ttu-id="f5424-175">スクリプト コンポーネントによるデータ フローの拡張</span><span class="sxs-lookup"><span data-stu-id="f5424-175">Extending the Data Flow with the Script Component</span></span>](script-component.md)  
  
  
