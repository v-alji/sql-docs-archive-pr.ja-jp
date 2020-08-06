---
title: データ フロー コンポーネントの検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ReinitializeMetaData method
- Validate method
- component validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- data flow components [Integration Services], validating
- validation [Integration Services]
ms.assetid: 1a7d5925-b387-4e31-af7f-c7f3c5151040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9a78588c1e75697235e62e8955b65da466a37ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634578"
---
# <a name="validating-a-data-flow-component"></a><span data-ttu-id="aa68b-102">データ フロー コンポーネントの検証</span><span class="sxs-lookup"><span data-stu-id="aa68b-102">Validating a Data Flow Component</span></span>
  <span data-ttu-id="aa68b-103">基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドを使用すると、正しく構成されていないコンポーネントが実行されることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-103">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is provided to prevent execution of a component that is not configured correctly.</span></span> <span data-ttu-id="aa68b-104">このメソッドを使用すると、コンポーネントが想定どおりの数の入出力オブジェクトを持ち、カスタム プロパティの値が許容範囲内で、接続が必要な場合はそれが指定されていることを検証できます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-104">Use this method to verify that a component has the expected number of input and output objects, that the custom properties of the component have acceptable values, and that any connections, if required, are specified.</span></span> <span data-ttu-id="aa68b-105">また、入出力コレクションの各列のデータ型が正しいこと、各列の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType> がコンポーネント用に正しく設定されていることも検証できます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-105">Use this method also to verify that the columns in the input and output collections have the correct data types and that the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType> of each column is set appropriately for the component.</span></span> <span data-ttu-id="aa68b-106">この基本クラスを実装すると、コンポーネントの入力列コレクションをチェックし、コレクションの各列が上流コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100> にある列を参照していることを確認できるため、検証プロセスの作業に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-106">The base class implementation assists in the validation process by checking the input column collection of the component and ensuring that each column in the collection refers to a column in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100> of the upstream component.</span></span>  
  
## <a name="validate-method"></a><span data-ttu-id="aa68b-107">Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="aa68b-107">Validate Method</span></span>  
 <span data-ttu-id="aa68b-108"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> メソッドは、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでコンポーネントが編集されるたびに、繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-108">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method is called repeatedly when a component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="aa68b-109">コンポーネントのデザイナーやユーザーに対するフィードバックは、列挙型 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> の戻り値や、警告、エラーの発生によって通知できます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-109">You can provide feedback to the designer and to users of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> enumeration return value, and by posting warnings and errors.</span></span> <span data-ttu-id="aa68b-110"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> 列挙に含まれる値のうち 3 つはさまざまな段階での検証失敗を示します。4 番目の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID> という値は、コンポーネントが正しく構成されていて、いつでも実行可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-110">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> enumeration contains three values that indicate various stages of failure, and a fourth, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID>, that indicates whether the component is correctly configured and ready to execute.</span></span>  
  
 <span data-ttu-id="aa68b-111">値 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> にエラーがあるが、コンポーネントはエラーを修復できることを示します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> value indicates that an error exists in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>, and that the component can repair the errors.</span></span> <span data-ttu-id="aa68b-112">コンポーネントがメタデータのエラーを修復できる場合でも、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> メソッドのエラーは修復せず、また、検証中に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> を変更することも避けてください。</span><span class="sxs-lookup"><span data-stu-id="aa68b-112">If a component encounters a metadata error that it can repair, it should not fix the error in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> should not be modified during validation.</span></span> <span data-ttu-id="aa68b-113">代わりに、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> メソッドが <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> のみを返し、コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドの呼び出し中にエラーを修復するようにします。詳細についてはこのセクションの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-113">Instead, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method should return only <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA>, and the component should repair the error in a call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method, as described later in this section.</span></span>  
  
 <span data-ttu-id="aa68b-114">値 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> は、コンポーネントにエラーがあるが、デザイナーで編集することにより修復できることを示します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-114">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> value indicates that the component has an error that can be rectified by editing the component in the designer.</span></span> <span data-ttu-id="aa68b-115">このエラーが発生するのは、通常、カスタム プロパティまたは必要な接続が指定されていない、または正しく設定されていないためです。</span><span class="sxs-lookup"><span data-stu-id="aa68b-115">The error is typically caused by a custom property or a required connection that is not specified or is set incorrectly.</span></span>  
  
 <span data-ttu-id="aa68b-116">値 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT> は、パッケージ XML の編集、またはオブジェクト モデルの使用により、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> プロパティが直接修正された場合にのみ発生するエラーがコンポーネントで見つかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-116">The final error value is <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT>, which indicates that the component has discovered errors that should only occur if the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property has been modified directly, either by editing the package XML or by using the object model.</span></span> <span data-ttu-id="aa68b-117">たとえば、コンポーネントに入力が 1 つしか追加されていないのに、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> に複数の入力が存在することが検証で確認された場合、この種のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-117">For example, this kind of error occurs when a component has added only a single input, but validation discovers that more than one input exists in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>.</span></span> <span data-ttu-id="aa68b-118">この戻り値を生成するエラーを修正するには、**[詳細エディター]** ダイアログ ボックスで **[リセット]** をクリックして、コンポーネントをリセットするしか方法がありません。</span><span class="sxs-lookup"><span data-stu-id="aa68b-118">Errors that generate this return value can only be repaired by resetting the component by using the **Reset** button in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="aa68b-119">戻り値としてエラーを返す以外に、検証中に警告やエラーを通知し、コンポーネントにフィードバックを送信する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="aa68b-119">Besides returning error values, components provide feedback by posting warnings or errors during validation.</span></span> <span data-ttu-id="aa68b-120">このメカニズムは、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> メソッドによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-120">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods provide this mechanism.</span></span> <span data-ttu-id="aa68b-121">これらのメソッドが呼び出されると、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] の **[エラー一覧]** ウィンドウにイベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-121">When these methods are called, these events are posted in the **Error List** window of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="aa68b-122">コンポーネント開発者は、発生したエラーに関するフィードバックや、必要に応じて、修正方法を直接ユーザーに通知することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-122">Component developers can then provide direct feedback to users on the errors that have occurred, and if appropriate, how to correct them.</span></span>  
  
 <span data-ttu-id="aa68b-123">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> メソッドをオーバーライドして実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aa68b-123">The following code example shows an overridden implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    bool pbCancel = false;  
  
    // Validate that there is one input.  
    if (ComponentMetaData.InputCollection.Count != 1)  
    {  
    ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, out pbCancel);  
    return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Validate that the UserName custom property is set.  
    if (ComponentMetaData.CustomPropertyCollection["UserName"].Value == null || ((string)ComponentMetaData.CustomPropertyCollection["UserName"].Value).Length == 0)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISBROKEN;  
    }  
  
    // Validate that there is one output.  
    if (ComponentMetaData.OutputCollection.Count != 1)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Let the base class verify that the input column reflects the output   
    // of the upstream component.  
    return base.Validate();  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
  
 Dim pbCancel As Boolean = False  
  
 ' Validate that there is one input.  
 If Not (ComponentMetaData.InputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Validate that the UserName custom property is set.  
 If ComponentMetaData.CustomPropertyCollection("UserName").Value Is Nothing OrElse CType(ComponentMetaData.CustomPropertyCollection("UserName").Value, String).Length = 0 Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISBROKEN   
 End If   
  
 ' Validate that there is one output.  
 If Not (ComponentMetaData.OutputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Let the base class verify that the input column reflects the output   
 ' of the upstream component.  
  
 Return MyBase.Validate   
  
End Function  
```  
  
## <a name="reinitializemetadata-method"></a><span data-ttu-id="aa68b-124">ReinitializeMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="aa68b-124">ReinitializeMetaData Method</span></span>  
 <span data-ttu-id="aa68b-125"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> メソッドの戻り値が <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> のコンポーネントを編集する場合に、常に [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aa68b-125">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer whenever you edit a component that returns <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> from its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method.</span></span> <span data-ttu-id="aa68b-126">コンポーネントには、検証中に見つかった問題を検出して修正するコードを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa68b-126">Components should contain code that detects and corrects the problems identified by the component during validation.</span></span>  
  
 <span data-ttu-id="aa68b-127">次の例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドで、検証中に問題を検出して修正するコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="aa68b-127">The following example shows a component that detects problems during validation and fixes these errors in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method.</span></span>  
  
```csharp  
private bool areInputColumnsValid = true;  
public override DTSValidationStatus Validate()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
    bool Cancel = false;  
    foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
    {  
        try  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
        }  
        catch  
        {  
            ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, out Cancel);  
            areInputColumnsValid = false;  
            return DTSValidationStatus.VS_NEEDSNEWMETADATA;  
        }  
    }  
  
    return DTSValidationStatus.VS_ISVALID;  
}  
public override void ReinitializeMetaData()  
{  
    if (!areInputColumnsValid)  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection[0];  
        IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
        foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
  
            if (vColumn == null)  
                input.InputColumnCollection.RemoveObjectByID(column.ID);  
        }  
        areInputColumnsValid = true;  
    }  
}  
```  
  
```vb  
Private areInputColumnsValid As Boolean = True   
  
Public  Overrides Function Validate() As DTSValidationStatus   
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
 Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
 Dim Cancel As Boolean = False   
 For Each column As IDTSInputColumn100 In input.InputColumnCollection   
   Try   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
   Catch   
     ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, Cancel)   
     areInputColumnsValid = False   
     Return DTSValidationStatus.VS_NEEDSNEWMETADATA   
   End Try   
 Next   
 Return DTSValidationStatus.VS_ISVALID   
End Function   
  
Public  Overrides Sub ReinitializeMetaData()   
 If Not areInputColumnsValid Then   
   Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
   Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
   For Each column As IDTSInputColumn100 In input.InputColumnCollection   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
     If vColumn Is Nothing Then   
       input.InputColumnCollection.RemoveObjectByID(column.ID)   
     End If   
   Next   
   areInputColumnsValid = True   
 End If   
End Sub  
```  
  
<span data-ttu-id="aa68b-128">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="aa68b-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="aa68b-129">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa68b-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="aa68b-130">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="aa68b-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="aa68b-131">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="aa68b-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
