---
title: カスタム データ フロー コンポーネントの作成 | Microsoft Docs
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
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 110d07ff88707ad1a01f299b6f532df99ce58404
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642192"
---
# <a name="creating-a-custom-data-flow-component"></a><span data-ttu-id="d6615-102">カスタム データ フロー コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="d6615-102">Creating a Custom Data Flow Component</span></span>
  <span data-ttu-id="d6615-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のデータ フロー タスクでは、開発者が [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] およびマネージド コードを使用してカスタム データ フロー コンポーネント (変換元、変換、および変換先) を作成するためのオブジェクト モデルが公開されます。</span><span class="sxs-lookup"><span data-stu-id="d6615-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the data flow task exposes an object model that lets developers create custom data flow components-sources, transformations, and destinations-by using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] and managed code.</span></span>  
  
 <span data-ttu-id="d6615-104">データ フロー タスクは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスを含むコンポーネントと、コンポーネント間のデータの移動を定義する <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> オブジェクトのコレクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d6615-104">A data flow task consists of components that contain an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface and a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects that define the movement of data between components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6615-105">カスタム プロバイダーを作成するときに、ProviderDescriptors.xml ファイルをメタデータ列の値で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6615-105">When you create a custom provider, you need to update the ProviderDescriptors.xml file with the metadata column values.</span></span>  
  
## <a name="design-time-and-run-time"></a><span data-ttu-id="d6615-106">デザイン時および実行時</span><span class="sxs-lookup"><span data-stu-id="d6615-106">Design Time and Run Time</span></span>  
 <span data-ttu-id="d6615-107">実行前のデータ フロー タスクは、増分的に変更が行われるため、デザイン時の状態にあると言えます。</span><span class="sxs-lookup"><span data-stu-id="d6615-107">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="d6615-108">追加される変更には、コンポーネントの追加または削除、コンポーネントを接続するパス オブジェクトの追加または削除、およびコンポーネントのメタデータに対する変更などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d6615-108">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="d6615-109">メタデータの変更が発生すると、コンポーネントはその変更を監視して対処できます。</span><span class="sxs-lookup"><span data-stu-id="d6615-109">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="d6615-110">たとえば、コンポーネントは特定の変更を禁止したり、ある変更に応じてさらに変更を加えたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="d6615-110">For example, a component can disallow certain changes or to make additional changes in response to a change.</span></span> <span data-ttu-id="d6615-111">デザイン時に、設計者はデザイン時インターフェイス <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> を介して、コンポーネントとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="d6615-111">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="d6615-112">データ フロー タスクは、実行時に、コンポーネントの順序の確認、実行プランの準備、および作業プランを実行するワーカー スレッドのプールの管理を行います。</span><span class="sxs-lookup"><span data-stu-id="d6615-112">At execution time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="d6615-113">各ワーカー スレッドはデータ フロー タスク内の一部の処理を実行しますが、ワーカー スレッドの主なタスクは、実行時インターフェイス <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> を介してコンポーネントのメソッドを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="d6615-113">Although each worker thread performs some work that is internal to the data flow task, the principal task of the worker thread is to call the methods of the component through the run-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interface.</span></span>  
  
## <a name="creating-a-component"></a><span data-ttu-id="d6615-114">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="d6615-114">Creating a Component</span></span>  
 <span data-ttu-id="d6615-115">データ フロー コンポーネントを作成するには、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基本クラスからクラスを派生し、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> クラスを適用して、基本クラスの適切なメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="d6615-115">To create a data flow component, you derive a class from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class, apply the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class, and then override the appropriate methods of the base class.</span></span> <span data-ttu-id="d6615-116"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> には <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> および <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> インターフェイスが実装され、それらのメソッドが公開されているので、ユーザーのコンポーネント内でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d6615-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interfaces, and exposes their methods for you to override in your component.</span></span>  
  
 <span data-ttu-id="d6615-117">コンポーネントで使用するオブジェクトによっては、次のアセンブリの一部またはすべてに対する参照がプロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="d6615-117">Depending on the objects used by your component, your project will require references to some or all of the following assemblies:</span></span>  
  
|<span data-ttu-id="d6615-118">機能</span><span class="sxs-lookup"><span data-stu-id="d6615-118">Feature</span></span>|<span data-ttu-id="d6615-119">参照するアセンブリ</span><span class="sxs-lookup"><span data-stu-id="d6615-119">Assembly to reference</span></span>|<span data-ttu-id="d6615-120">インポートする名前空間</span><span class="sxs-lookup"><span data-stu-id="d6615-120">Namespace to import</span></span>|  
|-------------|---------------------------|-------------------------|  
|<span data-ttu-id="d6615-121">Data flow</span><span class="sxs-lookup"><span data-stu-id="d6615-121">Data flow</span></span>|<span data-ttu-id="d6615-122">Microsoft.SqlServer.PipelineHost</span><span class="sxs-lookup"><span data-stu-id="d6615-122">Microsoft.SqlServer.PipelineHost</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|<span data-ttu-id="d6615-123">データ フロー ラッパー</span><span class="sxs-lookup"><span data-stu-id="d6615-123">Data flow wrapper</span></span>|<span data-ttu-id="d6615-124">Microsoft.SqlServer.DTSPipelineWrap</span><span class="sxs-lookup"><span data-stu-id="d6615-124">Microsoft.SqlServer.DTSPipelineWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|<span data-ttu-id="d6615-125">ランタイム</span><span class="sxs-lookup"><span data-stu-id="d6615-125">Runtime</span></span>|<span data-ttu-id="d6615-126">Microsoft.SQLServer.ManagedDTS</span><span class="sxs-lookup"><span data-stu-id="d6615-126">Microsoft.SQLServer.ManagedDTS</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|<span data-ttu-id="d6615-127">ランタイム ラッパー</span><span class="sxs-lookup"><span data-stu-id="d6615-127">Runtime wrapper</span></span>|<span data-ttu-id="d6615-128">Microsoft.SqlServer.DTSRuntimeWrap</span><span class="sxs-lookup"><span data-stu-id="d6615-128">Microsoft.SqlServer.DTSRuntimeWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 <span data-ttu-id="d6615-129">次のコード例では、基本クラスから派生し、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> を適用する簡単なコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="d6615-129">The following code example shows a simple component that derives from the base class, and applies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="d6615-130">DTSPipelineWrap アセンブリへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6615-130">You need to add a reference to the DTSPipelineWrap assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
<span data-ttu-id="d6615-131">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="d6615-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d6615-132">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6615-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d6615-133">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="d6615-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d6615-134">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="d6615-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6615-135">参照</span><span class="sxs-lookup"><span data-stu-id="d6615-135">See Also</span></span>  
 [<span data-ttu-id="d6615-136">データ フロー コンポーネント用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="d6615-136">Developing a User Interface for a Data Flow Component</span></span>](developing-a-user-interface-for-a-data-flow-component.md)  
  
  
