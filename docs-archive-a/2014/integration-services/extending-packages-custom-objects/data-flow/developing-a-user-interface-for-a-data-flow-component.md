---
title: データ フロー コンポーネント用ユーザー インターフェイスの開発 | Microsoft Docs
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
- data flow components [Integration Services], custom editors
- user interfaces [Integration Services]
- custom data flow components [Integration Services], custom editors
- custom component editors [Integration Services]
- IDtsComponentUI interface
- UITypeName property
- custom user interface [Integration Services], custom data flow component
- editors [Integration Services]
ms.assetid: 10b829a1-609b-42e3-9070-cfe5a2bb698c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f97f21ad14a5fa67fb49192931a0cb46d0cb41da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713345"
---
# <a name="developing-a-user-interface-for-a-data-flow-component"></a><span data-ttu-id="98eaa-102">データ フロー コンポーネント用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="98eaa-102">Developing a User Interface for a Data Flow Component</span></span>
  <span data-ttu-id="98eaa-103">コンポーネント開発者は、コンポーネント用のカスタム ユーザー インターフェイスを作成し、コンポーネントを編集するときに [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] に表示させることができます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-103">Component developers can provide a custom user interface for a component, which is displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] when the component is edited.</span></span> <span data-ttu-id="98eaa-104">カスタム ユーザー インターフェイスを実装すると、データ フロー タスクでコンポーネントが追加または削除されたとき、またはコンポーネントに関するヘルプが要求されたときに通知されます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-104">Implementing a custom user interface provides you with notification when the component is added to or deleted from a data flow task, and when help is requested for the component.</span></span>

 <span data-ttu-id="98eaa-105">コンポーネント用のカスタム ユーザー インターフェイスを提供しない場合でも、ユーザーは、詳細エディターを使用することで、コンポーネントおよびそのカスタム プロパティを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-105">If you do not provide a custom user interface for your component, users can still configure the component and its custom properties by using the Advanced Editor.</span></span> <span data-ttu-id="98eaa-106">詳細エディターでユーザーがカスタム プロパティ値を適切に変更できるようにするには、必要に応じて、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> および <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-106">You can ensure that the Advanced Editor allows users to edit custom property values appropriately by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> properties of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> when appropriate.</span></span> <span data-ttu-id="98eaa-107">詳細については、「[データ フロー コンポーネントのデザイン時のメソッド](design-time-methods-of-a-data-flow-component.md)」の「カスタム プロパティの作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98eaa-107">For more information, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>

## <a name="setting-the-uitypename-property"></a><span data-ttu-id="98eaa-108">UITypeName プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="98eaa-108">Setting the UITypeName Property</span></span>
 <span data-ttu-id="98eaa-109">カスタム ユーザー インターフェイスを提供するには、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティに、<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> インターフェイスを実装したクラスの名前を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98eaa-109">To provide a custom user interface, the developer must set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> to the name of a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="98eaa-110">このプロパティがコンポーネントによって設定されると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでコンポーネントを編集する際に、カスタム ユーザー インターフェイスが読み込まれ、必要な処理が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-110">When this property is set by the component, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] loads and calls the custom user interface when the component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="98eaa-111"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> プロパティは、型の完全修飾名を示すコンマ区切り形式の文字列です。</span><span class="sxs-lookup"><span data-stu-id="98eaa-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property is a comma-delimited string that identifies the fully qualified name of the type.</span></span> <span data-ttu-id="98eaa-112">次の一覧は、型を識別する要素を順に示したものです。</span><span class="sxs-lookup"><span data-stu-id="98eaa-112">The following list shows, in order, the elements that identify the type:</span></span>

-   <span data-ttu-id="98eaa-113">種類の名前。</span><span class="sxs-lookup"><span data-stu-id="98eaa-113">Type name</span></span>

-   <span data-ttu-id="98eaa-114">アセンブリ名</span><span class="sxs-lookup"><span data-stu-id="98eaa-114">Assembly name</span></span>

-   <span data-ttu-id="98eaa-115">ファイル バージョン</span><span class="sxs-lookup"><span data-stu-id="98eaa-115">File version</span></span>

-   <span data-ttu-id="98eaa-116">カルチャ</span><span class="sxs-lookup"><span data-stu-id="98eaa-116">Culture</span></span>

-   <span data-ttu-id="98eaa-117">パブリック キー トークン</span><span class="sxs-lookup"><span data-stu-id="98eaa-117">Public key token</span></span>

 <span data-ttu-id="98eaa-118">次のコード サンプルは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基本クラスから派生し、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> プロパティを指定するクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-118">The following code example shows a class that derives from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class and specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property.</span></span>

```csharp
[DtsPipelineComponent(
DisplayName="SampleComponent",
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...",
ComponentType = ComponentType.Transform)]
public class SampleComponent : PipelineComponent
{
//TODO: Implement the component here.
}
```

```vb
<DtsPipelineComponent(DisplayName="SampleComponent", _
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...", ComponentType=ComponentType.Transform)> _ 
Public Class SampleComponent 
 Inherits PipelineComponent 
End Class
```

## <a name="implementing-the-idtscomponentui-interface"></a><span data-ttu-id="98eaa-119">IDtsComponentUI インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="98eaa-119">Implementing the IDtsComponentUI Interface</span></span>
 <span data-ttu-id="98eaa-120"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> インターフェイスには、コンポーネントが追加、削除、および編集されたときに [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーが呼び出すメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="98eaa-120">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface contains methods that [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls when a component is added, deleted, and edited.</span></span> <span data-ttu-id="98eaa-121">コンポーネント開発者は、これらのメソッドを実装する際にコードを記述することにより、ユーザーがコンポーネントを対話的に操作できるようにできます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-121">Component developers can provide code in their implementation of these methods to interact with users of the component.</span></span>

 <span data-ttu-id="98eaa-122">このクラスは通常、コンポーネント自体とは別個のアセンブリに実装します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-122">This class is typically implemented in an assembly separate from the component itself.</span></span> <span data-ttu-id="98eaa-123">別個のアセンブリの使用は必須ではありませんが、これを使用することで、開発者はコンポーネントとユーザー インターフェイスを相互に独立に作成および配置することができ、コンポーネントのバイナリの占有領域を少なく抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-123">Although use of a separate assembly is not required, this lets the developer build and deploy the component and the user interface independently of each other, and keeps the binary footprint of the component small.</span></span>

 <span data-ttu-id="98eaa-124">カスタム ユーザー インターフェイスを実装すると、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでコンポーネントを編集する場合に比べ、コンポーネントの制御に関して開発者の意図をより反映することができます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-124">Implementing a custom user interface gives the component developer more control over the component as it is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="98eaa-125">たとえば <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> メソッドにコードを追加し、データ フロー タスクに最初にコンポーネントが追加されたときにこのコードを呼び出して、コンポーネントの初期設定の手順を示すウィザードを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-125">For example, a component can add code to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> method, which is called when a component is initially added to a data flow task, and display a wizard that guides the user through the initial configuration of the component.</span></span>

 <span data-ttu-id="98eaa-126"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> インターフェイスを実装するクラスを作成した後、ユーザーがコンポーネントに対して操作を行ったときに応答するコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98eaa-126">After you have created a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, you must add code to respond to user interaction with the component.</span></span> <span data-ttu-id="98eaa-127"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> メソッドは、コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスを提供するもので、<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> メソッドや <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> メソッドの実行前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-127">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component, and is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> methods.</span></span> <span data-ttu-id="98eaa-128">この参照は、プライベート メンバー変数に保存しておき、後でコンポーネントのメタデータを修正する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-128">This reference should be stored in a private member variable and used to modify the component's metadata thereafter.</span></span>

## <a name="modifying-a-component-and-persisting-changes"></a><span data-ttu-id="98eaa-129">コンポーネントの修正と変更の保存</span><span class="sxs-lookup"><span data-stu-id="98eaa-129">Modifying a Component and Persisting Changes</span></span>
 <span data-ttu-id="98eaa-130"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスは、パラメーターとして <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-130">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface is provided as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method.</span></span> <span data-ttu-id="98eaa-131">この参照は、ユーザー インターフェイスを実装するコードによってメンバー変数にキャッシュされ、このユーザー インターフェイスに対するユーザー操作に応じてコンポーネントを修正するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-131">This reference should be cached in a member variable by the user interface code, and then used to modify the component in response to user interaction with the user interface.</span></span>

 <span data-ttu-id="98eaa-132"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスを介してコンポーネントを直接修正することも可能ですが、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> メソッドを使用して、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> のインスタンスを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="98eaa-132">Although you can modify the component directly through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, it is better to create an instance of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method.</span></span> <span data-ttu-id="98eaa-133">インターフェイスを使用してコンポーネントを直接編集すると、コンポーネントの検証処理が省略されるためです。</span><span class="sxs-lookup"><span data-stu-id="98eaa-133">When you edit the component directly by using the interface, you bypass the component's validation safeguards.</span></span> <span data-ttu-id="98eaa-134"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> を介してコンポーネントのデザイン時インスタンスを使用する利点は、コンポーネントに加えられた変更が確実にコンポーネント側で制御されるという点です。</span><span class="sxs-lookup"><span data-stu-id="98eaa-134">The advantage of using the design-time instance of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> is that you ensure that the component has control over the changes made to it.</span></span>

 <span data-ttu-id="98eaa-135"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> メソッドの戻り値は、コンポーネントに加えられた変更が保存されたか、破棄されたかを示します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-135">The return value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method determines whether changes made to a component are persisted or discarded.</span></span> <span data-ttu-id="98eaa-136">このメソッドによって `false` が返される場合、変更はすべて破棄されます。`true` の場合、コンポーネントに対する変更が保存され、パッケージを保存する必要があることを示すマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-136">When this method returns `false`, all changes are discarded; `true` persists the changes to the component and marks the package as needing to be saved.</span></span>

### <a name="using-the-services-of-the-ssis-designer"></a><span data-ttu-id="98eaa-137">SSIS デザイナーのサービスの使用</span><span class="sxs-lookup"><span data-stu-id="98eaa-137">Using the Services of the SSIS Designer</span></span>
 <span data-ttu-id="98eaa-138"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> メソッドの `IServiceProvider` パラメーターにより、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーの、次のサービスにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-138">The `IServiceProvider` parameter of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides access to the following services of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer:</span></span>

|<span data-ttu-id="98eaa-139">サービス</span><span class="sxs-lookup"><span data-stu-id="98eaa-139">Service</span></span>|<span data-ttu-id="98eaa-140">説明</span><span class="sxs-lookup"><span data-stu-id="98eaa-140">Description</span></span>|
|-------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsClipboardService>|<span data-ttu-id="98eaa-141">コンポーネントがコピー/貼り付け、または切り取り/貼り付け操作の一部として生成されたかどうかを判別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-141">Used to determine whether the component was generated as part of a copy/paste or cut/paste operation.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionService>|<span data-ttu-id="98eaa-142">パッケージ内の既存の接続へのアクセス、または新しい接続の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-142">Used to access existing connections or to create new connections in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IErrorCollectionService>|<span data-ttu-id="98eaa-143">最後に発生したエラーまたは警告だけを受け取るのではなく、コンポーネントで生成されたすべてのエラーおよび警告をキャプチャする必要がある場合に、データ フロー コンポーネントからのイベントをキャプチャするために使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-143">Used to capture events from data flow components when you need to capture all the errors and warnings raised by the component instead of receiving only the last error or warning.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsVariableService>|<span data-ttu-id="98eaa-144">パッケージ内の既存の変数へのアクセス、または新しい変数の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-144">Used to access existing variables or to create new variables in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsPipelineEnvironmentService>|<span data-ttu-id="98eaa-145">データ フロー コンポーネントで親データ フロー タスクおよびデータ フロー内の他のコンポーネントにアクセスするために使用します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-145">Used by data flow components to access the parent Data Flow task and other components in the data flow.</span></span> <span data-ttu-id="98eaa-146">この機能は、必要に応じて追加のデータ フロー コンポーネントを作成して接続するための、緩やかに変化するディメンション ウィザードなどのコンポーネントを開発する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-146">This feature could be used to develop a component like the Slowly Changing Dimension Wizard that creates and connects additional data flow components as needed.</span></span>|

 <span data-ttu-id="98eaa-147">コンポーネント開発者は、これらのサービスを利用することにより、コンポーネントを読み込むパッケージ内のオブジェクトへのアクセスやオブジェクトの作成を行えます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-147">These services provide component developers the ability to access and create objects in the package in which the component is loaded.</span></span>

## <a name="sample"></a><span data-ttu-id="98eaa-148">サンプル</span><span class="sxs-lookup"><span data-stu-id="98eaa-148">Sample</span></span>
 <span data-ttu-id="98eaa-149">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> インターフェイスを実装したカスタム ユーザー インターフェイス クラスと、コンポーネントのエディターとして使用できる Windows フォームの統合を示します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-149">The following code example shows the integration of a custom user interface class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, and a Windows form that serves as the editor for a component.</span></span>

### <a name="custom-user-interface-class"></a><span data-ttu-id="98eaa-150">カスタム ユーザー インターフェイス クラス</span><span class="sxs-lookup"><span data-stu-id="98eaa-150">Custom User Interface Class</span></span>
 <span data-ttu-id="98eaa-151">次のコードは、<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> インターフェイスを実装するクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-151">The following code shows the class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="98eaa-152"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> メソッドは、コンポーネント エディターを作成し、そのフォームを表示します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-152">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method creates the component editor and then displays the form.</span></span> <span data-ttu-id="98eaa-153">フォームの戻り値により、コンポーネントに対する変更が保持されるかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="98eaa-153">The return value of the form determines whether changes to the component are persisted.</span></span>

```csharp
using System;
using System.Windows.Forms;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Pipeline.Design;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    public class SampleComponentUI : IDtsComponentUI
    {
        IDTSComponentMetaData100 md;
        IServiceProvider sp;

        public void Help(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void New(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void Delete(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Variables vars, Connections cons)
        {
            // Create and display the form for the user interface.
            SampleComponentUIForm componentEditor = new SampleComponentUIForm(cons, vars, md);

            DialogResult result  = componentEditor.ShowDialog(parentWindow);

            if (result == DialogResult.OK)
                return true;

            return false;
        }
        public void Initialize(IDTSComponentMetaData100 dtsComponentMetadata, IServiceProvider serviceProvider)
        {
            // Store the component metadata.
            this.md = dtsComponentMetadata;
        }
    }
}
```

```vb
Imports System 
Imports System.Windows.Forms 
Imports Microsoft.SqlServer.Dts.Runtime 
Imports Microsoft.SqlServer.Dts.Pipeline.Design 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Class SampleComponentUI 
 Implements IDtsComponentUI 
   Private md As IDTSComponentMetaData100 
   Private sp As IServiceProvider 

   Public Sub Help(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub New(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub Delete(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal vars As Variables, ByVal cons As Connections) As Boolean 
     ' Create and display the form for the user interface.
     Dim componentEditor As SampleComponentUIForm = New SampleComponentUIForm(cons, vars, md) 
     Dim result As DialogResult = componentEditor.ShowDialog(parentWindow) 
     If result = DialogResult.OK Then 
       Return True 
     End If 
     Return False 
   End Function 

   Public Sub Initialize(ByVal dtsComponentMetadata As IDTSComponentMetaData100, ByVal serviceProvider As IServiceProvider) 
     Me.md = dtsComponentMetadata 
   End Sub 
 End Class 

End Namespace
```

### <a name="custom-editor"></a><span data-ttu-id="98eaa-154">カスタム エディター</span><span class="sxs-lookup"><span data-stu-id="98eaa-154">Custom Editor</span></span>
 <span data-ttu-id="98eaa-155">次のコードは、<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> メソッドを呼び出すと表示される Windows フォームの実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="98eaa-155">The following code shows the implementation of the Windows form that is shown during the call to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method.</span></span>

```csharp
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;

using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    public partial class SampleComponentUIForm : System.Windows.Forms.Form
    {
        private Connections connections;
        private Variables variables;
        private IDTSComponentMetaData100 metaData;
        private CManagedComponentWrapper designTimeInstance;
        private System.ComponentModel.IContainer components = null;

        public SampleComponentUIForm( Connections cons, Variables vars, IDTSComponentMetaData100 md)
        {
            variables = vars;
            connections = cons;
            metaData = md;
        }

        private void btnOk_Click(object sender, System.EventArgs e)
        {
            if (designTimeInstance == null)
                designTimeInstance = metaData.Instantiate();

            designTimeInstance.SetComponentProperty( "CustomProperty", txtCustomPropertyValue.Text);

            this.Close();
        }

        private void btnCancel_Click(object sender, System.EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System 
Imports System.Drawing 
Imports System.Collections 
Imports System.ComponentModel 
Imports System.Windows.Forms 
Imports System.Data 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Partial Class SampleComponentUIForm 
  Inherits System.Windows.Forms.Form 
   Private connections As Connections 
   Private variables As Variables 
   Private metaData As IDTSComponentMetaData100 
   Private designTimeInstance As CManagedComponentWrapper 
   Private components As System.ComponentModel.IContainer = Nothing 

   Public Sub New(ByVal cons As Connections, ByVal vars As Variables, ByVal md As IDTSComponentMetaData100) 
     variables = vars 
     connections = cons 
     metaData = md 
   End Sub 

   Private Sub btnOk_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     If designTimeInstance Is Nothing Then 
       designTimeInstance = metaData.Instantiate 
     End If 
     designTimeInstance.SetComponentProperty("CustomProperty", txtCustomPropertyValue.Text) 
     Me.Close 
   End Sub 

   Private Sub btnCancel_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     Me.Close 
   End Sub 
 End Class 

End Namespace
```

<span data-ttu-id="98eaa-156">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="98eaa-156">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="98eaa-157">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="98eaa-157">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="98eaa-158">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="98eaa-158">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="98eaa-159">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="98eaa-159">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="98eaa-160">参照</span><span class="sxs-lookup"><span data-stu-id="98eaa-160">See Also</span></span>
 [<span data-ttu-id="98eaa-161">カスタム データ フロー コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="98eaa-161">Creating a Custom Data Flow Component</span></span>](creating-a-custom-data-flow-component.md)


