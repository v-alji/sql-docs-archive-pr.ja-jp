---
title: Developer&#39;s ガイド (Integration Services) |Microsoft Docs
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
- Integration Services, programming
- SSIS, programming
- SQL Server Integration Services, programming
- packages [Integration Services], programming
ms.assetid: 60fe148b-a7c4-4289-ae3e-2e949fc1886c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c16ec1a21cf7ebb711f6d3996eb6239ea052c83c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644019"
---
# <a name="developer39s-guide-integration-services"></a><span data-ttu-id="d622c-102">Developer&#39;s ガイド (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="d622c-102">Developer&#39;s Guide (Integration Services)</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="d622c-103">には、完全に再記述されたオブジェクト モデルが含まれています。それは、多数の機能で強化されています。この結果、パッケージのプログラミングや拡張作業は、より簡単に、柔軟に、また強力に行えるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d622c-103">includes a completely rewritten object model, which has been enhanced with many features that make extending and programming packages easier, more flexible, and more powerful.</span></span> <span data-ttu-id="d622c-104">開発者は、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージのほとんどすべての側面を拡張およびプログラミングできます。</span><span class="sxs-lookup"><span data-stu-id="d622c-104">Developers can extend and program almost every aspect of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="d622c-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の開発者として、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のプログラミングでは、次の 2 つの基本的な方法を採用できます。</span><span class="sxs-lookup"><span data-stu-id="d622c-105">As an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] developer, there are two fundamental approaches that you can take to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming:</span></span>  
  
-   <span data-ttu-id="d622c-106">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナー内で使用可能になるコンポーネントを記述してパッケージを拡張し、パッケージにカスタム機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="d622c-106">You can extend packages by writing components that become available within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to provide custom functionality in a package.</span></span>  
  
-   <span data-ttu-id="d622c-107">開発者独自のアプリケーションから、プログラムでパッケージを作成、構成、および実行することができます。</span><span class="sxs-lookup"><span data-stu-id="d622c-107">You can create, configure, and run packages programmatically from your own applications.</span></span>  
  
 <span data-ttu-id="d622c-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で組み込みコンポーネントが要件を満たしていない場合は、独自の拡張機能をコーディングすることによって [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d622c-108">If you find that the built-in components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="d622c-109">この方法をとる場合、以下のように 2 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="d622c-109">In this approach, you have two discrete options:</span></span>  
  
-   <span data-ttu-id="d622c-110">単一のパッケージで臨時に使用する場合は、スクリプト タスクでコードを記述してカスタム タスクを作成するか、またはスクリプト コンポーネントでコードを記述してカスタム データ フロー コンポーネントを作成し、変換元、変換、あるいは変換先として設定することができます。</span><span class="sxs-lookup"><span data-stu-id="d622c-110">For ad hoc use in a single package, you can create a custom task by writing code in the Script task, or a custom data flow component by writing code in the Script component, which you can configure as a source, transformation, or destination.</span></span> <span data-ttu-id="d622c-111">これらの強力なラッパーによってインフラストラクチャ コードが自動的に記述されるため、開発者はカスタム機能の開発に集中できます。ただし、他の場所で簡単に再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d622c-111">These powerful wrappers write the infrastructure code for you and let you focus exclusively on developing your custom functionality; however, they are not easily reusable elsewhere.</span></span>  
  
-   <span data-ttu-id="d622c-112">複数のパッケージで使用する場合は、接続マネージャー、タスク、列挙子、ログ プロバイダー、およびデータ フロー コンポーネントなどの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のカスタム拡張機能を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d622c-112">For use in multiple packages, you can create custom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] extensions such as connection managers, tasks, enumerators, log providers, and data flow components.</span></span> <span data-ttu-id="d622c-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のマネージド オブジェクト モデルには、基になる基本クラスが含まれており、従来よりもカスタム拡張機能の開発が簡単になっています。</span><span class="sxs-lookup"><span data-stu-id="d622c-113">The managed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model contains base classes that provide a starting point and make developing custom extensions easier than ever.</span></span>  
  
 <span data-ttu-id="d622c-114">パッケージを動的に作成する場合、または開発環境以外で [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理および実行する場合は、プログラムでパッケージを操作できます。</span><span class="sxs-lookup"><span data-stu-id="d622c-114">If you want to create packages dynamically, or to manage and run [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="d622c-115">既存のパッケージを読み込み、変更し、実行できます。または、まったく新しいパッケージをプログラムで作成および実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="d622c-115">You can load, modify, and run existing packages, or you can create and run entirely new packages programmatically.</span></span> <span data-ttu-id="d622c-116">この場合、次に示すような一連の方法があります。</span><span class="sxs-lookup"><span data-stu-id="d622c-116">In this approach, you have a continuous range of options:</span></span>  
  
-   <span data-ttu-id="d622c-117">既存のパッケージを読み込んで、変更せずに実行します。</span><span class="sxs-lookup"><span data-stu-id="d622c-117">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="d622c-118">既存のパッケージを読み込み、再構成 (異なるデータ ソースの指定など) してから実行します。</span><span class="sxs-lookup"><span data-stu-id="d622c-118">Load an existing package, reconfigure it (for example, specify a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="d622c-119">新しいパッケージを作成し、コンポーネントを追加および構成後、オブジェクト単位やプロパティ単位で変更し、保存してから実行します。</span><span class="sxs-lookup"><span data-stu-id="d622c-119">Create a new package, add and configure components, making changes object by object and property by property, save it, and then run it.</span></span>  
  
 <span data-ttu-id="d622c-120">ここでは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のプログラミングに対するこれらの方法について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="d622c-120">These approaches to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming are described in this section and demonstrated with examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d622c-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d622c-121">In This Section</span></span>  
 [<span data-ttu-id="d622c-122">Integration Services プログラミングの概要</span><span class="sxs-lookup"><span data-stu-id="d622c-122">Integration Services Programming Overview</span></span>](integration-services-programming-overview.md)  
 <span data-ttu-id="d622c-123">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 開発での制御フローおよびデータ フローの役割について説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-123">Describes the roles of control flow and data flow in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] development.</span></span>  
  
 [<span data-ttu-id="d622c-124">同期変換と非同期変換について</span><span class="sxs-lookup"><span data-stu-id="d622c-124">Understanding Synchronous and Asynchronous Transformations</span></span>](understanding-synchronous-and-asynchronous-transformations.md)  
 <span data-ttu-id="d622c-125">同期出力と非同期出力の重要な相違点、およびデータ フローでこれらの出力を使用するコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-125">Describes the important distinction between synchronous and asynchronous outputs and the components that use them in the data flow.</span></span>  
  
 [<span data-ttu-id="d622c-126">プログラムによる接続マネージャーの操作</span><span class="sxs-lookup"><span data-stu-id="d622c-126">Working with Connection Managers Programmatically</span></span>](working-with-connection-managers-programmatically.md)  
 <span data-ttu-id="d622c-127">マネージド コードで使用できる接続マネージャーと、コードが `AcquireConnection` メソッドを呼び出した場合に接続マネージャーが返す値の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="d622c-127">Lists the connection managers that you can use from managed code, and the values that the connection managers return when the code calls the `AcquireConnection` method.</span></span>  
  
 [<span data-ttu-id="d622c-128">スクリプトによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="d622c-128">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="d622c-129">スクリプト タスクを使用した制御フローの拡張方法、またはスクリプト コンポーネントを使用したデータ フローの拡張方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-129">Describes how to extend the control flow by using the Script task, or the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="d622c-130">カスタム オブジェクトを使用したパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="d622c-130">Extending Packages with Custom Objects</span></span>](extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="d622c-131">複数のパッケージで使用するプログラム カスタム タスク、データ フロー コンポーネント、およびその他のパッケージ オブジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-131">Describes how to create and program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="d622c-132">プログラムによるパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="d622c-132">Building Packages Programmatically</span></span>](building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="d622c-133">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージをプログラムで作成、構成、および保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-133">Describes how to create, configure, and save [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
 [<span data-ttu-id="d622c-134">プログラムによるパッケージの実行と管理</span><span class="sxs-lookup"><span data-stu-id="d622c-134">Running and Managing Packages Programmatically</span></span>](run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 <span data-ttu-id="d622c-135">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージをプログラムで列挙、実行、および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-135">Describes how to enumerate, run, and manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d622c-136">リファレンス</span><span class="sxs-lookup"><span data-stu-id="d622c-136">Reference</span></span>  
 [<span data-ttu-id="d622c-137">Integration Services のエラーとメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="d622c-137">Integration Services Error and Message Reference</span></span>](integration-services-error-and-message-reference.md)  
 <span data-ttu-id="d622c-138">定義済みの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] エラー コードと、そのシンボル名および説明の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="d622c-138">Lists the predefined [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error codes, together with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d622c-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="d622c-139">Related Sections</span></span>  
 [<span data-ttu-id="d622c-140">パッケージ開発のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="d622c-140">Troubleshooting Tools for Package Development</span></span>](troubleshooting/troubleshooting-tools-for-package-development.md)  
 <span data-ttu-id="d622c-141">開発時にパッケージのトラブルシューティングを行うために [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に用意されている機能とツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d622c-141">Describes the features and tools that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides for troubleshooting packages during development.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d622c-142">外部リソース</span><span class="sxs-lookup"><span data-stu-id="d622c-142">External Resources</span></span>  
  
-   <span data-ttu-id="d622c-143">www.codeplex.com/MSFTISProdSamples の CodePlex サンプル「[Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkID=131204)」</span><span class="sxs-lookup"><span data-stu-id="d622c-143">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d622c-144">参照</span><span class="sxs-lookup"><span data-stu-id="d622c-144">See Also</span></span>  
 [<span data-ttu-id="d622c-145">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="d622c-145">SQL Server Integration Services</span></span>](sql-server-integration-services.md)  
  
  
