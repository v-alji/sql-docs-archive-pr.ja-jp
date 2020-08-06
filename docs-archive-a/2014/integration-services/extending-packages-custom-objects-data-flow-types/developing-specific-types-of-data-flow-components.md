---
title: 特定の種類のデータ フロー コンポーネントの開発 | Microsoft Docs
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
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e168c866e03bfa5fd1f32127e4bfd6e58a2e8d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736601"
---
# <a name="developing-specific-types-of-data-flow-components"></a><span data-ttu-id="957b0-102">特定の種類のデータ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="957b0-102">Developing Specific Types of Data Flow Components</span></span>
  <span data-ttu-id="957b0-103">このセクションでは、変換元コンポーネント、同期出力型変換コンポーネント、非同期出力型変換コンポーネント、および変換先コンポーネントの開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="957b0-103">This section covers the specifics of developing source components, transformation components with synchronous outputs, transformation components with asynchronous outputs, and destination components.</span></span>  
  
 <span data-ttu-id="957b0-104">コンポーネント開発全般の詳細については、「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="957b0-104">For information about component development in general, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="957b0-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="957b0-105">In This Section</span></span>  
 [<span data-ttu-id="957b0-106">カスタム変換元コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="957b0-106">Developing a Custom Source Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 <span data-ttu-id="957b0-107">外部データ ソースのデータにアクセスし、そのデータをデータ フローの下流コンポーネントに提供するコンポーネントの開発について説明します。</span><span class="sxs-lookup"><span data-stu-id="957b0-107">Contains information on developing a component that accesses data from an external data source and supplies it to downstream components in the data flow.</span></span>  
  
 [<span data-ttu-id="957b0-108">同期出力型のカスタム変換コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="957b0-108">Developing a Custom Transformation Component with Synchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 <span data-ttu-id="957b0-109">入力に同期して出力する変換コンポーネントの開発について説明します。</span><span class="sxs-lookup"><span data-stu-id="957b0-109">Contains information on developing a transformation component whose outputs are synchronous to its inputs.</span></span> <span data-ttu-id="957b0-110">これらのコンポーネントは、データ フローにデータを追加せず、データが渡されるたびに処理を行います。</span><span class="sxs-lookup"><span data-stu-id="957b0-110">These components do not add data to the data flow, but process data as it passes through.</span></span>  
  
 [<span data-ttu-id="957b0-111">非同期出力型のカスタム変換コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="957b0-111">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 <span data-ttu-id="957b0-112">出力が入力に同期しない変換コンポーネントの開発について説明します。</span><span class="sxs-lookup"><span data-stu-id="957b0-112">Contains information on developing a transformation component whose outputs are not synchronous to its inputs.</span></span> <span data-ttu-id="957b0-113">これらのコンポーネントは、上流コンポーネントからデータを受け取ると共に、データをデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="957b0-113">These components receive data from upstream components, but also add data to the dataflow.</span></span>  
  
 [<span data-ttu-id="957b0-114">カスタム変換先コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="957b0-114">Developing a Custom Destination Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 <span data-ttu-id="957b0-115">データ フローの上流コンポーネントから行を受け取り、外部データ ソースに書き込むコンポーネントの開発について説明します。</span><span class="sxs-lookup"><span data-stu-id="957b0-115">Contains information on developing a component that receives rows from upstream components in the data flow and writes them to an external data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="957b0-116">リファレンス</span><span class="sxs-lookup"><span data-stu-id="957b0-116">Reference</span></span>  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 <span data-ttu-id="957b0-117">カスタム データ フロー コンポーネントを作成するために使用するクラスやインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="957b0-117">Contains the classes and interfaces used to create custom data flow components.</span></span>  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 <span data-ttu-id="957b0-118">データ フロー タスクのアンマネージ クラスやアンマネージ インターフェイスを示します。</span><span class="sxs-lookup"><span data-stu-id="957b0-118">Contains the unmanaged classes and interfaces of the data flow task.</span></span> <span data-ttu-id="957b0-119">プログラムによってデータ フローを構築する場合、またはカスタム データ フロー コンポーネントを作成する場合、開発者はこれらを使用します。また、マネージド <xref:Microsoft.SqlServer.Dts.Pipeline> 名前空間も同じ目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="957b0-119">The developer uses these, and the managed <xref:Microsoft.SqlServer.Dts.Pipeline> namespace, when building a data flow programmatically or creating custom data flow components.</span></span>  
  
<span data-ttu-id="957b0-120">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="957b0-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="957b0-121">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="957b0-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="957b0-122">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="957b0-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="957b0-123">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="957b0-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="957b0-124">参照</span><span class="sxs-lookup"><span data-stu-id="957b0-124">See Also</span></span>  
 <span data-ttu-id="957b0-125">[スクリプトソリューションとカスタムオブジェクトの比較](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="957b0-125">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="957b0-126">特定の種類のスクリプト コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="957b0-126">Developing Specific Types of Script Components</span></span>](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
