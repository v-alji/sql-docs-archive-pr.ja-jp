---
title: カスタム オブジェクトを使用したパッケージの拡張 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0159983f518e51aa082ea23745663e7f09eee1fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710969"
---
# <a name="extending-packages-with-custom-objects"></a><span data-ttu-id="04b0b-102">カスタム オブジェクトを使用したパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="04b0b-102">Extending Packages with Custom Objects</span></span>
  <span data-ttu-id="04b0b-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で提供されるコンポーネントがユーザーの要件を満たさない場合、独自の拡張機能をコーディングすることにより、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="04b0b-103">If you find that the components provided in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="04b0b-104">パッケージを拡張するには 2 つの方法があります。1 つ目は、スクリプト タスクおよびスクリプト コンポーネントによって提供される強力なラッパー内でコードを記述する方法です。2 つ目は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルによって提供される基本クラスを基にカスタム [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 拡張機能を最初から作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="04b0b-104">You have two discrete options for extending your packages: you can write code within the powerful wrappers provided by the Script task and the Script component, or you can create custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] extensions from scratch by deriving from the base classes provided by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="04b0b-105">ここでは、カスタム オブジェクトを使用してパッケージを拡張する 2 つの方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-105">This section explores the more advanced of the two options - extending packages with custom objects.</span></span>  
  
 <span data-ttu-id="04b0b-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カスタム ソリューションで、スクリプト タスクやスクリプト コンポーネントよりさらに柔軟な設定が必要な場合、または複数のパッケージで再利用できるコンポーネントが必要な場合は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルを使用すると、カスタム タスク、データ フロー コンポーネント、およびその他のパッケージ オブジェクトを、マネージド コードで最初から作成できます。</span><span class="sxs-lookup"><span data-stu-id="04b0b-106">When your custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] solution requires more flexibility than the Script task and the Script component provide, or when you need a component that you can reuse in multiple packages, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model lets you build custom tasks, data flow components, and other package objects in managed code from the ground up.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04b0b-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="04b0b-107">In This Section</span></span>  
 [<span data-ttu-id="04b0b-108">Integration Services 用のカスタム オブジェクトの開発</span><span class="sxs-lookup"><span data-stu-id="04b0b-108">Developing Custom Objects for Integration Services</span></span>](developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="04b0b-109">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で作成できるカスタム オブジェクトについて説明し、必要な手順や設定の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-109">Discusses the custom objects that can be created for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and summarizes the essential steps and settings.</span></span>  
  
 [<span data-ttu-id="04b0b-110">カスタム オブジェクトの永続化</span><span class="sxs-lookup"><span data-stu-id="04b0b-110">Persisting Custom Objects</span></span>](persisting-custom-objects.md)  
 <span data-ttu-id="04b0b-111">カスタム オブジェクトの既定の永続性、およびカスタムの永続性の実装プロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-111">Discusses the default persistence of custom objects, and the process of implementing custom persistence.</span></span>  
  
 [<span data-ttu-id="04b0b-112">カスタム オブジェクトのビルド、配置、デバッグ</span><span class="sxs-lookup"><span data-stu-id="04b0b-112">Building, Deploying, and Debugging Custom Objects</span></span>](building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="04b0b-113">さまざまな種類のカスタム オブジェクトの作成、配置、テストの一般的なアプローチについて説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-113">Discusses the common approaches to building, deploying and testing the various types of custom objects.</span></span>  
  
 [<span data-ttu-id="04b0b-114">カスタム タスクの開発</span><span class="sxs-lookup"><span data-stu-id="04b0b-114">Developing a Custom Task</span></span>](task/developing-a-custom-task.md)  
 <span data-ttu-id="04b0b-115">カスタム タスクのコードを記述する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-115">Describes the process of coding a custom task.</span></span>  
  
 [<span data-ttu-id="04b0b-116">カスタム接続マネージャーの開発</span><span class="sxs-lookup"><span data-stu-id="04b0b-116">Developing a Custom Connection Manager</span></span>](connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="04b0b-117">カスタム接続マネージャーのコードを記述する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-117">Describes the process of coding a custom connection manager.</span></span>  
  
 [<span data-ttu-id="04b0b-118">カスタム ログ プロバイダーの開発</span><span class="sxs-lookup"><span data-stu-id="04b0b-118">Developing a Custom Log Provider</span></span>](log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="04b0b-119">カスタム ログ プロバイダーのコードを記述する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-119">Describes the process of coding a custom log provider.</span></span>  
  
 [<span data-ttu-id="04b0b-120">カスタム ForEach 列挙子の開発</span><span class="sxs-lookup"><span data-stu-id="04b0b-120">Developing a Custom ForEach Enumerator</span></span>](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="04b0b-121">カスタム列挙子のコードを記述する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-121">Describes the process of coding a custom enumerator.</span></span>  
  
 [<span data-ttu-id="04b0b-122">カスタム データ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="04b0b-122">Developing a Custom Data Flow Component</span></span>](data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="04b0b-123">カスタム データ フローの変換元、変換、変換先のプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-123">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="04b0b-124">リファレンス</span><span class="sxs-lookup"><span data-stu-id="04b0b-124">Reference</span></span>  
 [<span data-ttu-id="04b0b-125">Integration Services のエラーとメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="04b0b-125">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="04b0b-126">事前に定義されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードと、そのシンボル名および説明の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-126">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="04b0b-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="04b0b-127">Related Sections</span></span>  
 [<span data-ttu-id="04b0b-128">スクリプトによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="04b0b-128">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="04b0b-129">スクリプト タスクを使用した制御フローの拡張方法や、スクリプト コンポーネントを使用したデータ フローの拡張方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-129">Discusses how to extend the control flow by using the Script task, or extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="04b0b-130">プログラムによるパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="04b0b-130">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="04b0b-131">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージをプログラムで作成、構成、実行、読み込み、保存、および管理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-131">Describes how to create, configure, run, load, save, and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="04b0b-132">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="04b0b-132">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="04b0b-133">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04b0b-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="04b0b-134">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="04b0b-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="04b0b-135">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="04b0b-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b0b-136">参照</span><span class="sxs-lookup"><span data-stu-id="04b0b-136">See Also</span></span>  
 <span data-ttu-id="04b0b-137">[スクリプトソリューションとカスタムオブジェクトの比較](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="04b0b-137">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="04b0b-138">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="04b0b-138">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
