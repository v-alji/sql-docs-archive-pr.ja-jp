---
title: プログラムによるデータ フロー コンポーネントの検出 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a18102f38f1ad06e918efe2ca529185d40deef9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715653"
---
# <a name="discovering-data-flow-components-programmatically"></a><span data-ttu-id="05951-102">プログラムによるデータ フロー コンポーネントの検出</span><span class="sxs-lookup"><span data-stu-id="05951-102">Discovering Data Flow Components Programmatically</span></span>
  <span data-ttu-id="05951-103">データ フロー タスクをパッケージに追加したら、次の手順として、使用できるようにするデータ フロー コンポーネントを決定できます。</span><span class="sxs-lookup"><span data-stu-id="05951-103">After you have added a data flow task to a package, your next step may be to determine what data flow components are available for your use.</span></span> <span data-ttu-id="05951-104">ローカル コンピューター上にインストールされ、使用可能なデータ フローの変換元、変換、および変換先は、プログラムによって検出できます。</span><span class="sxs-lookup"><span data-stu-id="05951-104">You can programmatically discover the data flow sources, transformations, and destinations that are installed and available on the local computer.</span></span> <span data-ttu-id="05951-105">パッケージにデータ フロー タスクを追加する方法について詳しくは、「[プログラムによるデータ フロー タスクの追加](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="05951-105">For information about adding a data flow task to the package, see [Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).</span></span>  
  
## <a name="discovering-components"></a><span data-ttu-id="05951-106">コンポーネントの検出</span><span class="sxs-lookup"><span data-stu-id="05951-106">Discovering Components</span></span>  
 <span data-ttu-id="05951-107"><xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスには、ローカル コンピューター上に正しくインストールされたコンポーネントごとに <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> オブジェクトを格納する、<xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> コレクションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="05951-107">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class provides the <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> collection, which contains a <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> object for each component correctly installed on the local computer.</span></span> <span data-ttu-id="05951-108">各 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> には、コンポーネントの名前、説明、および作成名など、コンポーネントに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05951-108">Each <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contains information about a component such as its name, description, and creation name.</span></span> <span data-ttu-id="05951-109">コンポーネントをパッケージに追加したら、<xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> プロパティの戻り値を使用して、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="05951-109">You can use the value returned in the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property to set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> when you add a component to a package.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="05951-110">次の手順</span><span class="sxs-lookup"><span data-stu-id="05951-110">Next Step</span></span>  
 <span data-ttu-id="05951-111">使用可能なコンポーネントを検出したら、次の手順として、コンポーネントを追加して構成します。この手順については、次のトピック「[プログラムによるデータ フロー コンポーネントの追加](../building-packages-programmatically/adding-data-flow-components-programmatically.md)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="05951-111">After discovering available components, the next step is to add and configure the components, which is discussed in the next topic, [Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="05951-112">サンプル</span><span class="sxs-lookup"><span data-stu-id="05951-112">Sample</span></span>  
 <span data-ttu-id="05951-113">次のコード例では、<xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.Application> コレクションを列挙し、ローカル コンピューターで使用可能なデータ フロー コンポーネントをプログラムによって検出する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="05951-113">The following code sample shows how to enumerate the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object to programmatically discover the data flow components available on the local computer.</span></span> <span data-ttu-id="05951-114">このサンプルでは、Microsoft.SqlServer.ManagedDTS アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="05951-114">This sample requires a reference to the Microsoft.SqlServer.ManagedDTS assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="05951-115">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="05951-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="05951-116">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="05951-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="05951-117">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="05951-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="05951-118">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="05951-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05951-119">参照</span><span class="sxs-lookup"><span data-stu-id="05951-119">See Also</span></span>  
 [<span data-ttu-id="05951-120">プログラムによるデータ フロー コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="05951-120">Adding Data Flow Components Programmatically</span></span>](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
