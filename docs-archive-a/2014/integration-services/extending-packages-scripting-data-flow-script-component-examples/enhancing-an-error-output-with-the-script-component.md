---
title: スクリプト コンポーネントによるエラー出力の強化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18637aa1e147ce989645ae859681929f4d0c438a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645188"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a><span data-ttu-id="6b06c-102">スクリプト コンポーネントによるエラー出力の強化</span><span class="sxs-lookup"><span data-stu-id="6b06c-102">Enhancing an Error Output with the Script Component</span></span>
  <span data-ttu-id="6b06c-103">既定では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のエラー出力の 2 つの追加列 (ErrorCode と ErrorColumn) には、エラー番号を表す数値コードと、エラーが発生した列の ID しか含まれていません。</span><span class="sxs-lookup"><span data-stu-id="6b06c-103">By default, the two extra columns in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error output, ErrorCode and ErrorColumn, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="6b06c-104">これらの数値は、対応するエラー説明がないとあまり役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="6b06c-104">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="6b06c-105">ここでは、スクリプト コンポーネントを使用して、データ フローの既存のエラー出力データにエラー説明の列を追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-105">This topic describes how to add an error description column to existing error output data in the data flow by using the Script component.</span></span> <span data-ttu-id="6b06c-106">この例では、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> メソッドを使用して、事前定義された特定の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードに対応するエラーの説明を追加します。これは、スクリプト コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> プロパティから使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b06c-106">The example adds the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the Script component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b06c-107">複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、このスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="6b06c-107">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="6b06c-108">詳細については、「 [カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b06c-108">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b06c-109">例</span><span class="sxs-lookup"><span data-stu-id="6b06c-109">Example</span></span>  
 <span data-ttu-id="6b06c-110">次に示す例では、変換として構成されたスクリプト コンポーネントを使用して、データ フローの既存のエラー出力データにエラー説明の列を追加します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-110">The example shown here uses a Script component configured as a transformation to add an error description column to existing error output data in the data flow.</span></span>  
  
 <span data-ttu-id="6b06c-111">データフローで変換として使用するスクリプトコンポーネントを構成する方法の詳細については、「[スクリプトコンポーネントによる同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)」および「[スクリプトコンポーネントによる非同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b06c-111">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="6b06c-112">このスクリプト コンポーネントの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="6b06c-112">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="6b06c-113">新しいスクリプト コンポーネントを作成する前に、データ フローの上流コンポーネントを構成して、エラーや切り捨てが発生した場合に行をエラー出力にリダイレクトするようにします。</span><span class="sxs-lookup"><span data-stu-id="6b06c-113">Before creating the new Script component, configure an upstream component in the data flow to redirect rows to its error output when an error or truncation occurs.</span></span> <span data-ttu-id="6b06c-114">テスト目的の場合、たとえば、参照が失敗するような 2 つのテーブル間の参照変換を構成するなどして、エラーが発生するような形でコンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-114">For testing purposes, you may want to configure a component in a manner that ensures that errors will occur-for example, by configuring a Lookup transformation between two tables where the lookup will fail.</span></span>  
  
2.  <span data-ttu-id="6b06c-115">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-115">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>  
  
3.  <span data-ttu-id="6b06c-116">上流コンポーネントからのエラー出力を新しいスクリプト コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-116">Connect the error output from the upstream component to the new Script component.</span></span>  
  
4.  <span data-ttu-id="6b06c-117">**[スクリプト変換エディター]** を開き、**[スクリプト]** ページの **[ScriptLanguage]** プロパティでスクリプト言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-117">Open the **Script Transformation Editor**, and on the **Script** page, for the **ScriptLanguage** property, select the script language.</span></span>  
  
5.  <span data-ttu-id="6b06c-118">**[スクリプトの編集]** をクリックして [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を開き、以下に示すサンプル コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-118">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE and add the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="6b06c-119">VSTA を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6b06c-119">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="6b06c-120">[スクリプト変換エディター] の [**入力列**] ページで、[ErrorCode] 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-120">In the Script Transformation Editor, on the **Input Columns** page, select the ErrorCode column.</span></span>  
  
8.  <span data-ttu-id="6b06c-121">[**入力および出力**] ページで、 `String` **ErrorDescription**という型の新しい出力列を追加します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-121">On the **Inputs and Outputs** page, add a new output column of type `String` named **ErrorDescription**.</span></span> <span data-ttu-id="6b06c-122">長いメッセージをサポートするために、新しい列の既定の長さを 255 に拡張します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-122">Increase the default length of the new column to 255 to support long messages.</span></span>  
  
9. <span data-ttu-id="6b06c-123">**[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6b06c-123">Close the **Script Transformation Editor.**</span></span>  
  
10. <span data-ttu-id="6b06c-124">スクリプト コンポーネントの出力を、適切な変換先にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="6b06c-124">Attach the output of the Script component to a suitable destination.</span></span> <span data-ttu-id="6b06c-125">アドホック テスト用に最も構成しやすいのは、フラット ファイル変換先です。</span><span class="sxs-lookup"><span data-stu-id="6b06c-125">A Flat File destination is the easiest to configure for ad hoc testing.</span></span>  
  
11. <span data-ttu-id="6b06c-126">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-126">Run the package.</span></span>  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
<span data-ttu-id="6b06c-127">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="6b06c-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6b06c-128">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b06c-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6b06c-129">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="6b06c-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6b06c-130">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="6b06c-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b06c-131">参照</span><span class="sxs-lookup"><span data-stu-id="6b06c-131">See Also</span></span>  
 <span data-ttu-id="6b06c-132">[データのエラー処理](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="6b06c-132">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="6b06c-133">[データ フロー コンポーネントでのエラー出力の使用](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="6b06c-133">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="6b06c-134">スクリプト コンポーネントによる同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="6b06c-134">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
