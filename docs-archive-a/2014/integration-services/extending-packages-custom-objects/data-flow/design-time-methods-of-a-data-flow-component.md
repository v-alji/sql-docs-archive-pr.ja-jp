---
title: データ フロー コンポーネントのデザイン時のメソッド | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e33fc4eb5805318dac217d2c5cbaedfd4bca70fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642925"
---
# <a name="design-time-methods-of-a-data-flow-component"></a><span data-ttu-id="dda62-102">データ フロー コンポーネントのデザイン時のメソッド</span><span class="sxs-lookup"><span data-stu-id="dda62-102">Design-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="dda62-103">実行前のデータ フロー タスクは、増分的に変更が行われるため、デザイン時の状態にあると言えます。</span><span class="sxs-lookup"><span data-stu-id="dda62-103">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="dda62-104">追加される変更には、コンポーネントの追加または削除、コンポーネントを接続するパス オブジェクトの追加または削除、およびコンポーネントのメタデータに対する変更などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dda62-104">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="dda62-105">メタデータの変更が発生すると、コンポーネントはその変更を監視して対処できます。</span><span class="sxs-lookup"><span data-stu-id="dda62-105">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="dda62-106">たとえば、コンポーネントは特定の変更を禁止したり、ある変更に応じてさらに変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="dda62-106">For example, a component can disallow certain changes or make additional changes in response to a change.</span></span> <span data-ttu-id="dda62-107">デザイン時に、設計者はデザイン時インターフェイス <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> を介して、コンポーネントとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="dda62-107">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>

## <a name="design-time-implementation"></a><span data-ttu-id="dda62-108">デザイン時の実装</span><span class="sxs-lookup"><span data-stu-id="dda62-108">Design-Time Implementation</span></span>
 <span data-ttu-id="dda62-109">コンポーネントのデザイン時のインターフェイスは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> インターフェイスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="dda62-109">The design-time interface of a component is described by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span> <span data-ttu-id="dda62-110">このインターフェイスをユーザーが明示的に実装することはありませんが、このインターフェイスで定義されるメソッドを理解しておくと、コンポーネントのデザイン時のインスタンスに対応した基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> のメソッドがわかります。</span><span class="sxs-lookup"><span data-stu-id="dda62-110">Although you do not explicitly implement this interface, a familiarity with the methods defined in this interface will help you understand which methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class correspond to the design-time instance of a component.</span></span>

 <span data-ttu-id="dda62-111">コンポーネントを [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] に読み込むと、コンポーネントのデザイン時のインスタンスがインスタンス化され、コンポーネントを編集すると、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> インターフェイスのメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dda62-111">When a component is loaded in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], the design-time instance of the component is instantiated and the methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface are called as the component is edited.</span></span> <span data-ttu-id="dda62-112">基本クラスを実装すると、コンポーネントで必要なこれらのメソッドのみをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="dda62-112">The implementation of the base class lets you override only those methods that your component requires.</span></span> <span data-ttu-id="dda62-113">多くの場合、これらのメソッドをオーバーライドするとコンポーネントへの不適切な編集が回避できます。</span><span class="sxs-lookup"><span data-stu-id="dda62-113">In many cases, you may override these methods to prevent inappropriate edits to a component.</span></span> <span data-ttu-id="dda62-114">たとえば、ユーザーがコンポーネントに出力を追加できないようにするには、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="dda62-114">For example, to prevent users from adding an output to a component, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> method.</span></span> <span data-ttu-id="dda62-115">この処理を行わない場合、基本クラスによるこのメソッドの実装を呼び出すと、コンポーネントに出力が追加されます。</span><span class="sxs-lookup"><span data-stu-id="dda62-115">Otherwise, when the implementation of this method by the base class is called, it adds an output to the component.</span></span>

 <span data-ttu-id="dda62-116">コンポーネントの目的または機能に関係なく、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>、および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dda62-116">Regardless of the purpose or functionality of your component, you should override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> methods.</span></span> <span data-ttu-id="dda62-117"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> の詳細については、「[データ フロー コンポーネントの検証](validating-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dda62-117">For more information about <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>, see [Validating a Data Flow Component](validating-a-data-flow-component.md).</span></span>

## <a name="providecomponentproperties-method"></a><span data-ttu-id="dda62-118">ProvideComponentProperties メソッド</span><span class="sxs-lookup"><span data-stu-id="dda62-118">ProvideComponentProperties Method</span></span>
 <span data-ttu-id="dda62-119">コンポーネントの初期化は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="dda62-119">The initialization of a component occurs in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="dda62-120">このメソッドは、クラス コンストラクターと同様、コンポーネントがデータ フロー タスクに追加されたときに [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dda62-120">This method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer when a component is added to the data flow task, and is similar to a class constructor.</span></span> <span data-ttu-id="dda62-121">コンポーネントの開発者は、このメソッドが呼び出されている間に、コンポーネントの入力、出力、およびカスタム プロパティを作成して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dda62-121">Component developers should create and initialize their inputs, outputs, and custom properties during this method call.</span></span> <span data-ttu-id="dda62-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドは、コンポーネントのデザイン時のインスタンスまたは実行時のインスタンスがインスタンス化されるたびに呼び出されるわけではない点が、コンストラクターとは異なります。</span><span class="sxs-lookup"><span data-stu-id="dda62-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method differs from a constructor because it is not called every time that the design-time instance or run-time instance of the component is instantiated.</span></span>

 <span data-ttu-id="dda62-123">メソッドの基本クラスの実装により、入力および出力がコンポーネントに追加され、入力の ID が <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="dda62-123">The base class implementation of the method adds an input and an output to the component and assigns the ID of the input to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property.</span></span> <span data-ttu-id="dda62-124">ただし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、この基本クラスによって追加された入力オブジェクトおよび出力オブジェクトには、名前が付けられていません。</span><span class="sxs-lookup"><span data-stu-id="dda62-124">However, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the input and output objects added by the base class are not named.</span></span> <span data-ttu-id="dda62-125">Name プロパティが設定されていない入力または出力オブジェクトを持つコンポーネントが含まれるパッケージは、正しく読み取れません。</span><span class="sxs-lookup"><span data-stu-id="dda62-125">Packages that contain a component with input or output objects whose Name property is not set will not successfully load.</span></span> <span data-ttu-id="dda62-126">したがって、基本実装を使用する場合は、既定の入力および出力の Name プロパティに明示的に値を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dda62-126">Therefore, when you use the base implementation, you must assign values explicitly to the Name property of the default input and output.</span></span>

```csharp
public override void ProvideComponentProperties()
{
    /// TODO: Reset the component.
    /// TODO: Add custom properties.
    /// TODO: Add input objects.
    /// TODO: Add output objects.
}
```

```vb
Public Overrides Sub ProvideComponentProperties()
    ' TODO: Reset the component.
    ' TODO: Add custom properties.
    ' TODO: Add input objects.
    ' TODO: Add output objects.
End Sub
```

### <a name="creating-custom-properties"></a><span data-ttu-id="dda62-127">カスタム プロパティの作成</span><span class="sxs-lookup"><span data-stu-id="dda62-127">Creating Custom Properties</span></span>
 <span data-ttu-id="dda62-128">コンポーネントの開発者は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドへの呼び出しで、カスタム プロパティ (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) をコンポーネントに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dda62-128">The call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method is where component developers should add custom properties (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) to the component.</span></span> <span data-ttu-id="dda62-129">カスタム プロパティにはデータ型プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="dda62-129">Custom properties do not have a data type property.</span></span> <span data-ttu-id="dda62-130">カスタム プロパティのデータ型は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> プロパティに割り当てた値のデータ型によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="dda62-130">The data type of a custom property is set by the data type of the value that you assign to its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> property.</span></span> <span data-ttu-id="dda62-131">ただし、カスタム プロパティに初期値を割り当てた後、別のデータ型の値を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="dda62-131">However, after you have assigned an initial value to the custom property, you cannot assign a value with a different data type.</span></span>

> [!NOTE]
>  <span data-ttu-id="dda62-132"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> インターフェイスは、`Object` 型のプロパティ値を制限付きでサポートしています。</span><span class="sxs-lookup"><span data-stu-id="dda62-132">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> interface has limited support for property values of type `Object`.</span></span> <span data-ttu-id="dda62-133">カスタム プロパティの値として格納できるオブジェクトは、文字列や整数などの単純型の配列のみです。</span><span class="sxs-lookup"><span data-stu-id="dda62-133">The only object that you can store as the value of a custom property is an array of simple types such as strings or integers.</span></span>

 <span data-ttu-id="dda62-134">次の例に示すように、カスタム プロパティの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> プロパティの値を、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> 列挙値の `CPET_NOTIFY` に設定すると、カスタム プロパティでプロパティ式をサポートすることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dda62-134">You can indicate that your custom property supports property expressions by setting the value of its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> property to `CPET_NOTIFY` from the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> enumeration, as shown in the following example.</span></span> <span data-ttu-id="dda62-135">ユーザーによって入力されたプロパティ式を処理または検証するためのコードを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dda62-135">You do not have to add any code to handle or to validate the property expression entered by the user.</span></span> <span data-ttu-id="dda62-136">プロパティの既定値を設定し、値を検証し、値を読み取って正常に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="dda62-136">You can set a default value for the property, validate its value, and read and use its value normally.</span></span>

```csharp
IDTSCustomProperty100 myCustomProperty;
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;
```

```vb
Dim myCustomProperty As IDTSCustomProperty100
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY
```

 <span data-ttu-id="dda62-137">次の例に示すように、プロパティを使用すると、ユーザーが列挙からカスタムプロパティ値を選択できるように制限できます。この例では、 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> という名前のパブリック列挙型が定義されていることを前提としてい `MyValidValues` ます。</span><span class="sxs-lookup"><span data-stu-id="dda62-137">You can limit users to selecting a custom property value from an enumeration by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> property, as shown in the following example, which assumes that you have defined a public enumeration named `MyValidValues`.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the type with the custom property.
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;
// Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne;  
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the type with the custom property.
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName 
' Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne
```

 <span data-ttu-id="dda62-138">詳細については、[MSDN ライブラリ](https://go.microsoft.com/fwlink/?LinkId=7022)の「一般的な型変換」および「型コンバーターの実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dda62-138">For more information, see "Generalized Type Conversion" and "Implementing a Type Converter" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

 <span data-ttu-id="dda62-139">次の例に示すように、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> プロパティを使用すると、カスタム プロパティの値を設定するカスタム エディター ダイアログ ボックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dda62-139">You can specify a custom editor dialog box for the value of your custom property by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property, as shown in the following example.</span></span> <span data-ttu-id="dda62-140">ニーズに合った既存の UI 型エディターのクラスが見つからない場合は、最初に `System.Drawing.Design.UITypeEditor` を継承するカスタム型のエディターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dda62-140">First, you must create a custom type editor that inherits from `System.Drawing.Design.UITypeEditor`, if you cannot locate an existing UI type editor class that fits your needs.</span></span>

```csharp
public class MyCustomTypeEditor : UITypeEditor
{
...
}
```

```vb
Public Class MyCustomTypeEditor
  Inherits UITypeEditor 
  ...
End Class
```

 <span data-ttu-id="dda62-141">次に、カスタム プロパティの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> プロパティの値として、このクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dda62-141">Next, specify this class as the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property of your custom property.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the editor with the custom property.
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the editor with the custom property.
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName
```

 <span data-ttu-id="dda62-142">詳細については、[MSDN ライブラリ](https://go.microsoft.com/fwlink/?LinkId=7022)の「UI 型エディターの実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dda62-142">For more information, see "Implementing a UI Type Editor" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

<span data-ttu-id="dda62-143">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="dda62-143">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="dda62-144">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dda62-144">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="dda62-145">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="dda62-145">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="dda62-146">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="dda62-146">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="dda62-147">参照</span><span class="sxs-lookup"><span data-stu-id="dda62-147">See Also</span></span>
 [<span data-ttu-id="dda62-148">データ フロー コンポーネントの実行時のメソッド</span><span class="sxs-lookup"><span data-stu-id="dda62-148">Run-time Methods of a Data Flow Component</span></span>](run-time-methods-of-a-data-flow-component.md)


