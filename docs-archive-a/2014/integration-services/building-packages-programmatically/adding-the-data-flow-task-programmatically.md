---
title: プログラムによるデータ フロー タスクの追加 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f7e699cc8e88bafb2a4508fdac8560fa73befe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639611"
---
# <a name="adding-the-data-flow-task-programmatically"></a><span data-ttu-id="411d3-102">プログラムによるデータ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="411d3-102">Adding the Data Flow Task Programmatically</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="411d3-103">にはデータ フロー タスクというタスクがあります。これは、オブジェクト モデルでは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> 名前空間として表されます。</span><span class="sxs-lookup"><span data-stu-id="411d3-103">includes a task called the Data Flow task, which is represented by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> namespace in the object model.</span></span> <span data-ttu-id="411d3-104">データ フロー タスクは、パッケージの実行時にデータを変換、移動する目的専用の、特殊で高性能なタスクです。</span><span class="sxs-lookup"><span data-stu-id="411d3-104">The Data Flow task is a specialized, high-performance task, dedicated to transforming and moving data during package execution.</span></span> <span data-ttu-id="411d3-105">他のタスクと同様、データ フロー タスクは <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトによってラップされており、ランタイム エンジンはこれを単にパッケージ内のタスクの 1 つとして扱います。</span><span class="sxs-lookup"><span data-stu-id="411d3-105">Like other tasks, the Data Flow task is wrapped by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object, and from the perspective of the run-time engine, this task is just another task in the package.</span></span> <span data-ttu-id="411d3-106">ただし、データ フロー内には、別にデータ フロー コンポーネントというオブジェクトもあります。</span><span class="sxs-lookup"><span data-stu-id="411d3-106">However, the data flow contains additional objects called data flow components.</span></span> <span data-ttu-id="411d3-107">これは変換元から変換先にデータを移動するコンポーネントで、その際に変換を経由する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="411d3-107">These components are the components that make data move from a source to a destination, sometimes through a transformation.</span></span> <span data-ttu-id="411d3-108">コンポーネントには、移動の方向とデータの変換方法が定義されています。</span><span class="sxs-lookup"><span data-stu-id="411d3-108">The components define both the direction of movement and how data is transformed.</span></span> <span data-ttu-id="411d3-109">データ フロー タスクを設定するには、タスクにコンポーネントを追加し、それを接続します。これにより、データ フローの確立と目的の変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="411d3-109">Configuring the Data Flow task involves adding components to the task, and then connecting them to establish the flow of data and achieve the intended transformation.</span></span>  
  
 <span data-ttu-id="411d3-110">データ フロー タスク内のコンポーネントには、 **[データ フローの変換元]** 、 **[データ フロー変換]** 、 **[データ フローの変換先]** の 3 種類があり、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナー ツールボックスにこの順序で表示されています。</span><span class="sxs-lookup"><span data-stu-id="411d3-110">There are three types of components within a Data Flow task: **Data Flow Sources**, **Data Flow Transformations**, and **Data Flow Destinations**, shown in that order within the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer toolbox.</span></span> <span data-ttu-id="411d3-111">これらの種類は単に変換元、変換、変換先と呼ばれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="411d3-111">These types are also referred to more simply as sources, transformations, or destinations.</span></span> <span data-ttu-id="411d3-112">名前からもわかるように、データは変換元から変換へと流れ、次に変換から変換先へと流れます。</span><span class="sxs-lookup"><span data-stu-id="411d3-112">As implied by the names, data flows from a source to a transformation, and then to a destination.</span></span> <span data-ttu-id="411d3-113">これはデータ フローの概念をごく簡単に説明したにすぎません。データ フロー タスクは柔軟で強力なタスクであり、複数の変換元を処理することも、複数の変換先に出力を送信する変換を多数接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="411d3-113">This is a simplistic description of the data flow to illustrate the concept, but the Data Flow task is flexible and powerful enough to handle multiple sources, and to connect together many transformations that send output to multiple destinations.</span></span>  
  
 <span data-ttu-id="411d3-114">データ フロー タスクをパッケージに追加する方法は、他のタスクの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="411d3-114">The Data Flow task is added to a package the same way other tasks are added.</span></span> <span data-ttu-id="411d3-115">タスクを追加したら、コンポーネントをデータ フロー タスクに追加したり、タスク内でコンポーネントを設定および接続することにより、データ フロー タスクを設定します。</span><span class="sxs-lookup"><span data-stu-id="411d3-115">After the task has been added, it is configured by adding components to the data flow task, and configuring and connecting components in the task.</span></span>  
  
## <a name="sample"></a><span data-ttu-id="411d3-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="411d3-116">Sample</span></span>  
 <span data-ttu-id="411d3-117">次のコード サンプルは、データ フロー タスクをパッケージに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="411d3-117">The following code sample shows how to add a Data Flow task to a package.</span></span> <span data-ttu-id="411d3-118">この例では、Microsoft.SqlServer.PipelineHost、Microsoft.SqlServer.DTSPipelineWrap、および Microsoft.SqlServer.ManagedDTS アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="411d3-118">This example requires a reference to the assemblies Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap, and Microsoft.SqlServer.ManagedDTS.</span></span>  
  
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
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="411d3-119">外部リソース</span><span class="sxs-lookup"><span data-stu-id="411d3-119">External Resources</span></span>  
 <span data-ttu-id="411d3-120">blogs.msdn.com のブログ「[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223)」(EzAPI - SQL Server 2012 用の更新)</span><span class="sxs-lookup"><span data-stu-id="411d3-120">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="411d3-121">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="411d3-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="411d3-122">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="411d3-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="411d3-123">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="411d3-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="411d3-124">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="411d3-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411d3-125">参照</span><span class="sxs-lookup"><span data-stu-id="411d3-125">See Also</span></span>  
 [<span data-ttu-id="411d3-126">プログラムによるデータ フロー コンポーネントの検出</span><span class="sxs-lookup"><span data-stu-id="411d3-126">Discovering Data Flow Components Programmatically</span></span>](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  
