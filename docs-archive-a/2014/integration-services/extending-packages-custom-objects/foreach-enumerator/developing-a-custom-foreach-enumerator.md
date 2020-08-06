---
title: カスタム ForEach 列挙子の開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3d61f98266320f63d7ee56262b7c85dfb64d39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641172"
---
# <a name="developing-a-custom-foreach-enumerator"></a><span data-ttu-id="80e7f-102">カスタム ForEach 列挙子の開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-102">Developing a Custom ForEach Enumerator</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="80e7f-103">では、foreach 列挙子を使用して、コレクション内のアイテムを繰り返し処理したり、各要素に対して同じタスクを実行したりします。</span><span class="sxs-lookup"><span data-stu-id="80e7f-103">uses foreach enumerators to iterate over the items in a collection and perform the same tasks for each element.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="80e7f-104">には、フォルダー内のすべてのファイル、データベース内のすべてのテーブル、パッケージ変数に格納された一覧のすべての要素など、最もよく使用されるコレクションをサポートする、さまざまな foreach 列挙子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="80e7f-104">includes a variety of foreach enumerators that support the most commonly used collections, such as all the files in a folder, all the tables in a database, or all the elements of a list stored in a package variable.</span></span> <span data-ttu-id="80e7f-105">提供される foreach 列挙子とコレクションが、要件を必ずしも満たさない場合は、カスタム foreach 列挙子を作成できます。</span><span class="sxs-lookup"><span data-stu-id="80e7f-105">If the foreach enumerators and collections that are provided do not entirely meet your requirements, you can create a custom foreach enumerator.</span></span>  
  
 <span data-ttu-id="80e7f-106">カスタム foreach 列挙子を作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性を適用し、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80e7f-106">To create a custom foreach enumerator, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80e7f-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="80e7f-107">In This Section</span></span>  
 <span data-ttu-id="80e7f-108">ここでは、カスタム foreach 列挙子とそのカスタム ユーザー インターフェイスを作成、構成、およびコーディングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-108">This section describes how to create, configure, and code a custom foreach enumerator and its custom user interface.</span></span>  
  
 [<span data-ttu-id="80e7f-109">カスタム Foreach 列挙子の作成</span><span class="sxs-lookup"><span data-stu-id="80e7f-109">Creating a Custom Foreach Enumerator</span></span>](creating-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="80e7f-110">カスタム foreach 列挙子プロジェクト用のクラスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-110">Describes how to create the classes for a custom foreach enumerator project.</span></span>  
  
 [<span data-ttu-id="80e7f-111">カスタム Foreach 列挙子のコーディング</span><span class="sxs-lookup"><span data-stu-id="80e7f-111">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="80e7f-112">基本クラスのメソッドとプロパティのオーバーライドによる、カスタム foreach 列挙子の実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-112">Describes how to implement a custom foreach enumerator by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="80e7f-113">カスタム ForEach 列挙子用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-113">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="80e7f-114">ユーザー インターフェイス クラスと、カスタム foreach 列挙子の構成に使用するフォームの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-114">Describes how to implement the user interface class and the form that is used to configure the custom foreach enumerator.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="80e7f-115">関連トピック</span><span class="sxs-lookup"><span data-stu-id="80e7f-115">Related Topics</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="80e7f-116">すべてのカスタム オブジェクトに共通の情報</span><span class="sxs-lookup"><span data-stu-id="80e7f-116">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="80e7f-117">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="80e7f-117">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="80e7f-118">Integration Services 用のカスタム オブジェクトの開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-118">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="80e7f-119">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のすべての型のカスタム オブジェクトを実装する基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-119">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="80e7f-120">カスタム オブジェクトの永続化</span><span class="sxs-lookup"><span data-stu-id="80e7f-120">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="80e7f-121">カスタムの永続性と、それが必要な場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-121">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="80e7f-122">カスタム オブジェクトのビルド、配置、デバッグ</span><span class="sxs-lookup"><span data-stu-id="80e7f-122">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="80e7f-123">カスタム オブジェクトをビルド、署名、配置、およびデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-123">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="80e7f-124">その他のカスタム オブジェクトに関する情報</span><span class="sxs-lookup"><span data-stu-id="80e7f-124">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="80e7f-125">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="80e7f-125">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="80e7f-126">カスタム タスクの開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-126">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="80e7f-127">カスタム タスクのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-127">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="80e7f-128">カスタム接続マネージャーの開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-128">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="80e7f-129">カスタム接続マネージャーのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-129">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="80e7f-130">カスタム ログ プロバイダーの開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-130">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="80e7f-131">カスタム ログ プロバイダーのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-131">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="80e7f-132">カスタム データ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="80e7f-132">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="80e7f-133">カスタム データ フローの変換元、変換、変換先のプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-133">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="80e7f-134">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="80e7f-134">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="80e7f-135">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="80e7f-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="80e7f-136">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="80e7f-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="80e7f-137">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="80e7f-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
