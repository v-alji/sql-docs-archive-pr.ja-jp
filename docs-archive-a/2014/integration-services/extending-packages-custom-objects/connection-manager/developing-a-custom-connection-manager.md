---
title: カスタム接続マネージャーの開発 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], connections
- custom connection managers [Integration Services], about custom connection managers
- connection managers [Integration Services], custom
- Integration Services packages, connection managers
- SSIS packages, connection managers
- SQL Server Integration Services packages, connection managers
- custom connection managers [Integration Services]
ms.assetid: bda0b29e-57f5-4879-b04d-1396dc56daa8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19c5a9066db6542742537a41a7f567d1b4b1d23d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742405"
---
# <a name="developing-a-custom-connection-manager"></a><span data-ttu-id="40af5-102">カスタム接続マネージャーの開発</span><span class="sxs-lookup"><span data-stu-id="40af5-102">Developing a Custom Connection Manager</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="40af5-103">では、接続マネージャーを使用して、外部データ ソースに接続するために必要な情報をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="40af5-103">uses connection managers to encapsulate the information needed to connect to an external data source.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="40af5-104">には、エンタープライズ データベースからテキスト ファイルや Excel ワークシートまで、よく使用されるデータ ソースへの接続をサポートする、さまざまな接続マネージャーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="40af5-104">includes a variety of connection managers that support connections to the most commonly used data sources, from enterprise databases to text files and Excel worksheets.</span></span> <span data-ttu-id="40af5-105">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] でサポートされている接続マネージャーと外部データ ソースが、要件を必ずしも満たさない場合は、カスタム接続マネージャーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="40af5-105">If the connection managers and external data sources supported by [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not entirely meet your requirements, you can create a custom connection manager.</span></span>  
  
 <span data-ttu-id="40af5-106">カスタム接続マネージャーを作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性を適用し、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティや <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40af5-106">To create a custom connection manager, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="40af5-107">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に組み込まれているタスク、変換元、および変換先の多くは、組み込みの接続マネージャーの特定の種類でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="40af5-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="40af5-108">組み込みのタスクやコンポーネントで使用するカスタム接続マネージャーを開発する前に、それらのコンポーネントで使用できる接続マネージャーが、特定の種類に限定されるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="40af5-108">Before developing a custom connection manager for use with built-in tasks and components, check whether those components restrict the list of available connection managers to those of a specific type.</span></span> <span data-ttu-id="40af5-109">ソリューションがカスタム接続マネージャーを必要とする場合は、その接続マネージャーで機能するカスタムのタスク、変換元、および変換先も開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40af5-109">If your solution requires a custom connection manager, you might also have to develop a custom task, or a custom source or destination, for use with the connection manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40af5-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="40af5-110">In This Section</span></span>  
 <span data-ttu-id="40af5-111">ここでは、カスタム接続マネージャーとそのオプションのカスタム ユーザー インターフェイスを作成、構成、およびコーディングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-111">This section describes how to create, configure, and code a custom connection manager and its optional custom user interface.</span></span> <span data-ttu-id="40af5-112">このセクション内のコード スニペットは、Sql Server Custom Connection Manager のサンプルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="40af5-112">The code snippets shown in this section are drawn from the Sql Server Custom Connection Manager Sample.</span></span>  
  
 [<span data-ttu-id="40af5-113">カスタム接続マネージャーの作成</span><span class="sxs-lookup"><span data-stu-id="40af5-113">Creating a Custom Connection Manager</span></span>](creating-a-custom-connection-manager.md)  
 <span data-ttu-id="40af5-114">カスタム接続マネージャー プロジェクト用のクラスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-114">Describes how to create the classes for a custom connection manager project.</span></span>  
  
 [<span data-ttu-id="40af5-115">カスタム接続マネージャーのコーディング</span><span class="sxs-lookup"><span data-stu-id="40af5-115">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
 <span data-ttu-id="40af5-116">基本クラスのメソッドとプロパティのオーバーライドによる、カスタム接続マネージャーの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-116">Describes how to implement a custom connection manager by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="40af5-117">カスタム接続マネージャー用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="40af5-117">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
 <span data-ttu-id="40af5-118">ユーザー インターフェイス クラスと、カスタム接続マネージャーの構成に使用するフォームの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-118">Describes how to implement the user interface class and the form that is used to configure the custom connection manager.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40af5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="40af5-119">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="40af5-120">すべてのカスタム オブジェクトに共通の情報</span><span class="sxs-lookup"><span data-stu-id="40af5-120">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="40af5-121">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40af5-121">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="40af5-122">Integration Services 用のカスタム オブジェクトの開発</span><span class="sxs-lookup"><span data-stu-id="40af5-122">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="40af5-123">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のすべての型のカスタム オブジェクトを実装する基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-123">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="40af5-124">カスタム オブジェクトの永続化</span><span class="sxs-lookup"><span data-stu-id="40af5-124">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="40af5-125">カスタムの永続性と、それが必要な場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-125">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="40af5-126">カスタム オブジェクトのビルド、配置、デバッグ</span><span class="sxs-lookup"><span data-stu-id="40af5-126">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="40af5-127">カスタム オブジェクトをビルド、署名、配置、およびデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-127">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="40af5-128">その他のカスタム オブジェクトに関する情報</span><span class="sxs-lookup"><span data-stu-id="40af5-128">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="40af5-129">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40af5-129">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="40af5-130">カスタム タスクの開発</span><span class="sxs-lookup"><span data-stu-id="40af5-130">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="40af5-131">カスタム タスクのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-131">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="40af5-132">カスタム ログ プロバイダーの開発</span><span class="sxs-lookup"><span data-stu-id="40af5-132">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="40af5-133">カスタム ログ プロバイダーのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-133">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="40af5-134">カスタム ForEach 列挙子の開発</span><span class="sxs-lookup"><span data-stu-id="40af5-134">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="40af5-135">カスタム列挙子のプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-135">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="40af5-136">カスタム データ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="40af5-136">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="40af5-137">カスタム データ フローの変換元、変換、変換先のプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40af5-137">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="40af5-138">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="40af5-138">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="40af5-139">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40af5-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="40af5-140">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="40af5-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="40af5-141">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="40af5-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
