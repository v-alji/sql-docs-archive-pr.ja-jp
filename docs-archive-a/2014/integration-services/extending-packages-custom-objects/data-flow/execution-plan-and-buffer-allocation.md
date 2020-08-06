---
title: 実行プランおよびバッファーの割り当て | Microsoft Docs
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
- custom data flow components [Integration Services], buffer allocations
- custom data flow components [Integration Services], execution plans
- buffer allocations [Integration Services]
- data flow components [Integration Services], buffer allocations
- data flow components [Integration Services], execution plans
- execution plans [Integration Services]
ms.assetid: 679d9ff0-641e-47c3-abb8-d1a7dcb279dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03b8bb22988ccf77f8920252ac2d600478c92f3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713346"
---
# <a name="execution-plan-and-buffer-allocation"></a><span data-ttu-id="18f3c-102">実行プランおよびバッファーの割り当て</span><span class="sxs-lookup"><span data-stu-id="18f3c-102">Execution Plan and Buffer Allocation</span></span>
  <span data-ttu-id="18f3c-103">実行前に、データ フロー タスクはそのコンポーネントを確認し、コンポーネントの各処理手順に応じて、実行プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-103">Before execution, the data flow task examines its components and generates an execution plan for each sequence of components.</span></span> <span data-ttu-id="18f3c-104">このセクションでは、実行プラン、プランの表示方法、および実行プランに基づいて入力および出力バッファーを割り当てる方法に関する詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-104">This section provides details about the execution plan, how to view the plan, and how input and output buffers are allocated based on the execution plan.</span></span>  
  
## <a name="understanding-the-execution-plan"></a><span data-ttu-id="18f3c-105">実行プランについて</span><span class="sxs-lookup"><span data-stu-id="18f3c-105">Understanding the Execution Plan</span></span>  
 <span data-ttu-id="18f3c-106">実行プランには、ソース スレッドと作業スレッドが含まれています。各スレッドには作業一覧が含まれており、ソース スレッドには出力作業一覧が、作業スレッドには入力と出力の作業一覧が指定されています。</span><span class="sxs-lookup"><span data-stu-id="18f3c-106">An execution plan contains source threads and work threads, and each thread contains work lists that specify output work lists for source threads or input and output work lists for work threads.</span></span> <span data-ttu-id="18f3c-107">実行プラン内のソース スレッドは、データ フロー内の変換元コンポーネントを表し、実行プラン内では *SourceThread\*\*n* によって識別されます。ここで *n* は、0 から始まるソース スレッドの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-107">The source threads in an execution plan represent the source components in the data flow and are identified in the execution plan by *SourceThread\*\*n*, where *n* is the zero-based number of the source thread.</span></span>  
  
 <span data-ttu-id="18f3c-108">各ソース スレッドはバッファーを作成してリスナーを設定し、変換元コンポーネントで <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-108">Each source thread creates a buffer, sets a listener, and calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method on the source component.</span></span> <span data-ttu-id="18f3c-109">ここで、実行が開始されてデータが生成され、データ フロー タスクによって用意された出力バッファーに、変換元コンポーネントが行を追加し始めます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-109">This is where execution starts and data originates, as the source component starts adding rows to the output buffers that are provided to it by the data flow task.</span></span> <span data-ttu-id="18f3c-110">ソース スレッドが実行されると、作業スレッド間で作業の負荷が分散されます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-110">After the source threads are running, the balance of work is distributed among work threads.</span></span>  
  
 <span data-ttu-id="18f3c-111">作業スレッドは、入力および出力の両方の作業一覧を含む場合があり、実行プラン内では *WorkThread\*\*n* によって識別されます。ここで *n* は、0 から始まる作業スレッドの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-111">A work thread may contain both input and output work lists and is identified in the execution plan as *WorkThread\*\*n*, where *n* is the zero-based number of the work thread.</span></span> <span data-ttu-id="18f3c-112">非同期出力型のコンポーネントがグラフに含まれている場合、このスレッドには出力作業一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-112">These threads contain output work lists when the graph contains a component with asynchronous outputs.</span></span>  
  
 <span data-ttu-id="18f3c-113">次のサンプル実行プランは、変換元コンポーネントが非同期出力型の変換に連結され、その変換が変換先コンポーネントに連結されているデータ フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="18f3c-113">The following sample execution plan represents a data flow that contains a source component connected to a transformation with an asynchronous output connected to a destination component.</span></span> <span data-ttu-id="18f3c-114">この例では、変換コンポーネントに非同期出力が含まれているので、WorkThread0 には出力作業一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-114">In this example, WorkThread0 contains an output work list because the transformation component has an asynchronous output.</span></span>  
  
```  
SourceThread0   
    Influences: 72 158   
    Output Work List   
        CreatePrimeBuffer of type 1 for output id 10   
        SetBufferListener: "WorkThread0" for input ID 73   
        CallPrimeOutput on component "OLE DB Source" (1)   
    End Output Work List   
    This thread drives 0 distributors   
End SourceThread0   
WorkThread0   
    Influences: 72 158   
    Input Work list, input ID 73   
        CallProcessInput on input ID 73 on component "Sort" (72) for view type 2   
    End Input Work list for input 73   
    Output Work List   
        CreatePrimeBuffer of type 3 for output id 74   
        SetBufferListener: "WorkThread1" for input ID 171with internal handoff   
        CallPrimeOutput on component "Sort" (72)   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread0   
WorkThread1   
    Influences: 158   
    Input Work list, input ID 171  
        CallProcessInput on input ID 171 on component "OLE DB Destination" (158) for view type 4  
    End Input Work list for input 171   
    Output Work List   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="18f3c-115">実行プランはパッケージが実行されるたびに生成され、ログ プロバイダーをパッケージに追加し、ログ記録を有効にして **PipelineExecutionPlan** イベントを選択することにより、実行プランをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-115">The execution plan is generated every time a package is executed, and can be captured by adding a log provider to the package, enabling logging, and selecting the **PipelineExecutionPlan** event.</span></span>  
  
## <a name="understanding-buffer-allocation"></a><span data-ttu-id="18f3c-116">バッファーの割り当てについて</span><span class="sxs-lookup"><span data-stu-id="18f3c-116">Understanding Buffer Allocation</span></span>  
 <span data-ttu-id="18f3c-117">実行プランに基づき、データ フロー タスクは、データ フロー コンポーネントの出力で定義された列を格納するバッファーを作成します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-117">Based on the execution plan, the data flow task creates buffers that contain the columns defined in the outputs of the data flow components.</span></span> <span data-ttu-id="18f3c-118">このバッファーは、非同期出力型のコンポーネントを検出するまで、コンポーネントの処理手順を通じてデータ フロー内で再使用されます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-118">The buffer is reused as the data flows through the sequence of components, until a component with asynchronous outputs is encountered.</span></span> <span data-ttu-id="18f3c-119">次に、新しいバッファーが作成され、非同期出力の出力列と下流コンポーネントの出力列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-119">Then, a new buffer is created, which contains the output columns of the asynchronous output and the output columns of downstream components.</span></span>  
  
 <span data-ttu-id="18f3c-120">実行中、コンポーネントは現在のソース スレッドまたは作業スレッド内のバッファーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-120">During execution, components have access to the buffer in the current source or work thread.</span></span> <span data-ttu-id="18f3c-121">そのバッファーは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドによって提供される入力バッファーか、または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドによって提供される出力バッファーのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="18f3c-121">The buffer is either an input buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, or an output buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="18f3c-122">各バッファーは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> プロパティにより、入力バッファーまたは出力バッファーに識別されます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> also identifies each buffer as an input or output buffer.</span></span>  
  
 <span data-ttu-id="18f3c-123">非同期出力型の変換コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドから既存の入力バッファーを受け取り、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドから新しい出力バッファーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="18f3c-123">Transformation components with asynchronous outputs receive the existing input buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, and receive the new output buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="18f3c-124">非同期出力型の変換コンポーネントは、入力バッファーおよび出力バッファーの両方を受け取る、唯一のデータ フロー コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="18f3c-124">A transformation component with asynchronous outputs is the only type of data flow component that receives both an input and an output buffer.</span></span>  
  
 <span data-ttu-id="18f3c-125">コンポーネントに提供されるバッファーには、コンポーネントの入力列コレクションまたは出力列コレクションにない列が含まれる場合があるため、コンポーネントの開発者は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> メソッドを呼び出し、列の `LineageID` を指定することによってバッファー内の列を探すことができます。</span><span class="sxs-lookup"><span data-stu-id="18f3c-125">Because the buffer provided to a component is likely to contain more columns than the component has in its input or output column collections, component developers can call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method to locate a column in the buffer by specifying its `LineageID`.</span></span>  
  
<span data-ttu-id="18f3c-126">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="18f3c-126">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="18f3c-127">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="18f3c-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="18f3c-128">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="18f3c-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="18f3c-129">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="18f3c-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
