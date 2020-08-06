---
title: カスタム タスクの開発 | Microsoft Docs
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
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9d3446acff7ced73ab47014bec51708dba225b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642920"
---
# <a name="developing-a-custom-task"></a><span data-ttu-id="06405-102">カスタム タスクの開発</span><span class="sxs-lookup"><span data-stu-id="06405-102">Developing a Custom Task</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="06405-103">は、作業単位を実行するタスクを使用して、データの抽出、変換、および読み込みをサポートします。</span><span class="sxs-lookup"><span data-stu-id="06405-103">uses tasks to perform units of work in support of the extraction, transformation, and loading of data.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="06405-104">には、SQL ステートメントの実行から、FTP サイトからのファイルのダウンロードまで、頻繁に使用される操作を実行するためのさまざまなタスクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="06405-104">includes a variety of tasks that perform the most frequently used actions, from executing an SQL statement to downloading a file from an FTP site.</span></span> <span data-ttu-id="06405-105">用意されているタスクとサポートされている操作が、要件を完全には満たない場合は、カスタム タスクを作成できます。</span><span class="sxs-lookup"><span data-stu-id="06405-105">If the included tasks and supported actions do not completely meet your requirements, you can create a custom task.</span></span>  
  
 <span data-ttu-id="06405-106">カスタム タスクを作成するには、[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性を適用して、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="06405-106">To create a custom task, you have to create a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06405-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="06405-107">In This Section</span></span>  
 <span data-ttu-id="06405-108">ここでは、カスタム タスクとそのオプションのカスタム ユーザー インターフェイスを作成、構成、およびコーディングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-108">This section describes how to create, configure, and code a custom task and its optional custom user interface.</span></span>  
  
 [<span data-ttu-id="06405-109">カスタム タスクの作成</span><span class="sxs-lookup"><span data-stu-id="06405-109">Creating a Custom Task</span></span>](creating-a-custom-task.md)  
 <span data-ttu-id="06405-110">カスタム タスクを作成する最初の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-110">Describes the first step, which is creating the custom task.</span></span>  
  
 [<span data-ttu-id="06405-111">カスタム タスクのコーディング</span><span class="sxs-lookup"><span data-stu-id="06405-111">Coding a Custom Task</span></span>](coding-a-custom-task.md)  
 <span data-ttu-id="06405-112">カスタム タスクの主なメソッドのコードを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-112">Describes how to code the principal methods of a custom task.</span></span>  
  
 [<span data-ttu-id="06405-113">カスタム タスクでのデータ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="06405-113">Connecting to Data Sources in a Custom Task</span></span>](connecting-to-data-sources-in-a-custom-task.md)  
 <span data-ttu-id="06405-114">カスタム タスクをデータ ソースに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-114">Describes how to connect a custom task to a data source.</span></span>  
  
 [<span data-ttu-id="06405-115">カスタム タスクでのイベントの発生と定義</span><span class="sxs-lookup"><span data-stu-id="06405-115">Raising and Defining Events in a Custom Task</span></span>](raising-and-defining-events-in-a-custom-task.md)  
 <span data-ttu-id="06405-116">カスタム タスクからカスタム イベントを発生させ、定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-116">Describes how to raise events and define custom events from the custom task.</span></span>  
  
 [<span data-ttu-id="06405-117">カスタム タスクにおけるデバッグのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="06405-117">Adding Support for Debugging in a Custom Task</span></span>](adding-support-for-debugging-in-a-custom-task.md)  
 <span data-ttu-id="06405-118">カスタム タスクでのブレークポイント ターゲットの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-118">Describes how to create breakpoint targets in the custom task.</span></span>  
  
 [<span data-ttu-id="06405-119">カスタム タスク用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="06405-119">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
 <span data-ttu-id="06405-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーに表示され、カスタム タスクのプロパティを構成するユーザー インターフェイスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-120">Describes how to create a user interface that shows in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to configure properties on the custom task.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06405-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="06405-121">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="06405-122">すべてのカスタム オブジェクトに共通の情報</span><span class="sxs-lookup"><span data-stu-id="06405-122">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="06405-123">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="06405-123">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="06405-124">Integration Services 用のカスタム オブジェクトの開発</span><span class="sxs-lookup"><span data-stu-id="06405-124">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="06405-125">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のすべての種類のカスタム オブジェクトを実装する基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-125">Describes the basic steps in implementing all kinds of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="06405-126">カスタム オブジェクトの永続化</span><span class="sxs-lookup"><span data-stu-id="06405-126">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="06405-127">カスタムの永続性と、それが必要な場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-127">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="06405-128">カスタム オブジェクトのビルド、配置、デバッグ</span><span class="sxs-lookup"><span data-stu-id="06405-128">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="06405-129">カスタム オブジェクトをビルド、署名、配置、およびデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-129">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="06405-130">その他のカスタム オブジェクトに関する情報</span><span class="sxs-lookup"><span data-stu-id="06405-130">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="06405-131">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="06405-131">For information about the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="06405-132">カスタム接続マネージャーの開発</span><span class="sxs-lookup"><span data-stu-id="06405-132">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="06405-133">カスタム接続マネージャーのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-133">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="06405-134">カスタム ログ プロバイダーの開発</span><span class="sxs-lookup"><span data-stu-id="06405-134">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="06405-135">カスタム ログ プロバイダーのプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-135">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="06405-136">カスタム ForEach 列挙子の開発</span><span class="sxs-lookup"><span data-stu-id="06405-136">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="06405-137">カスタム列挙子のプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-137">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="06405-138">カスタム データ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="06405-138">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="06405-139">カスタム データ フローの変換元、変換、変換先のプログラム方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06405-139">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="06405-140">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="06405-140">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="06405-141">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="06405-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="06405-142">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="06405-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="06405-143">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="06405-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06405-144">参照</span><span class="sxs-lookup"><span data-stu-id="06405-144">See Also</span></span>  
 <span data-ttu-id="06405-145">[スクリプト タスクによるパッケージの拡張](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span><span class="sxs-lookup"><span data-stu-id="06405-145">[Extending the Package with the Script Task](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span></span>  
 [<span data-ttu-id="06405-146">スクリプティング ソリューションとカスタム オブジェクトとの比較</span><span class="sxs-lookup"><span data-stu-id="06405-146">Comparing Scripting Solutions and Custom Objects</span></span>](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
