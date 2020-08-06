---
title: プログラムによるデータ フロー コンポーネントの接続 | Microsoft Docs
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
- data flow task [Integration Services], components
- paths [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 404ecab7-7698-447b-93d6-dd256beb11ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39494fee5314f309b79abfd30303fdd607fd3c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639607"
---
# <a name="connecting-data-flow-components-programmatically"></a><span data-ttu-id="1883b-102">プログラムによるデータ フロー コンポーネントの接続</span><span class="sxs-lookup"><span data-stu-id="1883b-102">Connecting Data Flow Components Programmatically</span></span>
  <span data-ttu-id="1883b-103">データ フロー タスクにコンポーネントを追加したら、コンポーネントを接続して、変換元から変換を経由して変換先に至るデータ フローを表す実行ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1883b-103">After you have added components to the data flow task, you connect them to create an execution tree that represents the flow of data from sources through transformations to destinations.</span></span> <span data-ttu-id="1883b-104">データ フロー内のコンポーネントを接続するには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1883b-104">You use <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects to connect the components in the data flow.</span></span>  
  
## <a name="creating-a-path"></a><span data-ttu-id="1883b-105">パスの作成</span><span class="sxs-lookup"><span data-stu-id="1883b-105">Creating a Path</span></span>  
 <span data-ttu-id="1883b-106"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> プロパティの New メソッドを呼び出して、新しいパスを作成し、データ フロー タスク内のパスのコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="1883b-106">Call the New method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe> interface to create a new path and add it to the collection of paths in the data flow task.</span></span> <span data-ttu-id="1883b-107">このメソッドは、新しく作成され、切断されている <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> オブジェクトを返します。これを使用して 2 つのコンポーネントを接続します。</span><span class="sxs-lookup"><span data-stu-id="1883b-107">This method returns a new, disconnected <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, which you then use to connect two components.</span></span>  
  
 <span data-ttu-id="1883b-108">パスを接続し、パスに含まれているコンポーネントが接続されたことを通知するには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1883b-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A> method to connect the path and to notify the components participating in the path that they have been connected.</span></span> <span data-ttu-id="1883b-109">このメソッドは、上流コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> および下流コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> をパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1883b-109">This method accepts an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the upstream component and an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> of the downstream component as parameters.</span></span> <span data-ttu-id="1883b-110">既定では、コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドを呼び出すと、入力を持つコンポーネントに 1 つの入力、および出力を持つコンポーネントに 1 つの出力が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1883b-110">By default, the call to the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method creates a single input for components that have inputs, and a single output for components that have outputs.</span></span> <span data-ttu-id="1883b-111">次の例では、この既定の変換元の出力および変換先の入力を使用します。</span><span class="sxs-lookup"><span data-stu-id="1883b-111">The following example uses this default output of the source and input of the destination.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1883b-112">次の手順</span><span class="sxs-lookup"><span data-stu-id="1883b-112">Next Step</span></span>  
 <span data-ttu-id="1883b-113">2 つのコンポーネント間のパスを確立したら、次に入力列を下流コンポーネントにマップします。この手順については、次の「[プログラムによる入力列の選択](../building-packages-programmatically/selecting-input-columns-programmatically.md)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="1883b-113">After you establish a path between two components, the next step is to map input columns in the downstream component, which is discussed in the next topic, [Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="1883b-114">サンプル</span><span class="sxs-lookup"><span data-stu-id="1883b-114">Sample</span></span>  
 <span data-ttu-id="1883b-115">次のコード例は、2 つのコンポーネント間でパスを確立する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1883b-115">The following code sample shows how to establish a path between two components.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Create the source component.    
      IDTSComponentMetaData100 source =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      source.ComponentClassID = "DTSAdapter.OleDbSource";  
      CManagedComponentWrapper srcDesignTime = source.Instantiate();  
      srcDesignTime.ProvideComponentProperties();  
  
      // Create the destination component.  
      IDTSComponentMetaData100 destination =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      destination.ComponentClassID = "DTSAdapter.OleDbDestination";  
      CManagedComponentWrapper destDesignTime = destination.Instantiate();  
      destDesignTime.ProvideComponentProperties();  
  
      // Create the path.  
      IDTSPath100 path = dataFlowTask.PathCollection.New();  
      path.AttachPathAndPropagateNotifications(source.OutputCollection[0],  
        destination.InputCollection[0]);  
    }  
  }  
```  
  
 <span data-ttu-id="1883b-116">}</span><span class="sxs-lookup"><span data-stu-id="1883b-116">}</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Create the source component.    
    Dim source As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    source.ComponentClassID = "DTSAdapter.OleDbSource"  
    Dim srcDesignTime As CManagedComponentWrapper = source.Instantiate()  
    srcDesignTime.ProvideComponentProperties()  
  
    ' Create the destination component.  
    Dim destination As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    destination.ComponentClassID = "DTSAdapter.OleDbDestination"  
    Dim destDesignTime As CManagedComponentWrapper = destination.Instantiate()  
    destDesignTime.ProvideComponentProperties()  
  
    ' Create the path.  
    Dim path As IDTSPath100 = dataFlowTask.PathCollection.New()  
    path.AttachPathAndPropagateNotifications(source.OutputCollection(0), _  
      destination.InputCollection(0))  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="1883b-117">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="1883b-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1883b-118">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1883b-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1883b-119">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="1883b-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1883b-120">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="1883b-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1883b-121">参照</span><span class="sxs-lookup"><span data-stu-id="1883b-121">See Also</span></span>  
 [<span data-ttu-id="1883b-122">プログラムによる入力列の選択</span><span class="sxs-lookup"><span data-stu-id="1883b-122">Selecting Input Columns Programmatically</span></span>](../building-packages-programmatically/selecting-input-columns-programmatically.md)  
  
  
