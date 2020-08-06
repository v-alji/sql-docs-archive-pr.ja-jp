---
title: カスタム ログ プロバイダーの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88d4f70fa9d50628b831b56f9fa22100648fce51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632625"
---
# <a name="developing-a-custom-log-provider"></a><span data-ttu-id="22421-102">カスタム ログ プロバイダーの開発</span><span class="sxs-lookup"><span data-stu-id="22421-102">Developing a Custom Log Provider</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="22421-103">には、パッケージの実行中に発生したイベントをキャプチャできるようにする広範なログ記録機能があります。</span><span class="sxs-lookup"><span data-stu-id="22421-103">has extensive logging capabilities that make it possible to capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="22421-104">では、さまざまなログ プロバイダーを使用でき、ログを作成して XML、テキスト、データベースなどの形式で保存したり、Windows イベント ログに格納したりできます。</span><span class="sxs-lookup"><span data-stu-id="22421-104">includes a variety of log providers that enable logs to be created and stored in formats such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="22421-105">提供されるログ プロバイダーと出力形式が、要件を必ずしも満たさない場合は、カスタム ログ プロバイダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="22421-105">If the log providers and the output formats that are provided do not entirely meet your requirements, you can create a custom log provider.</span></span>

 <span data-ttu-id="22421-106">カスタム ログ プロバイダーを作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性を適用し、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティや <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="22421-106">To create a custom log provider, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="22421-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="22421-107">In This Section</span></span>
 <span data-ttu-id="22421-108">ここでは、カスタム ログ プロバイダーを作成、構成、およびコーディングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-108">This section describes how to create, configure, and code a custom log provider.</span></span>

 <span data-ttu-id="22421-109">[カスタムログプロバイダーの作成](creating-a-custom-log-provider.md)カスタムログプロバイダープロジェクトのクラスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-109">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) Describes how to create the classes for a custom log provider project.</span></span>

 <span data-ttu-id="22421-110">[カスタムログプロバイダーのコーディング](coding-a-custom-log-provider.md)基本クラスのメソッドとプロパティをオーバーライドすることによって、カスタムログプロバイダーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-110">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) Describes how to implement a custom log provider by overriding the methods and properties of the base class.</span></span>

 <span data-ttu-id="22421-111">[カスタムログプロバイダーのユーザーインターフェイスの開発](developing-a-user-interface-for-a-custom-log-provider.md)カスタムログプロバイダーのカスタムユーザーインターフェイスは、ではサポートされていません [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="22421-111">[Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md) Custom user interfaces for custom log providers are not supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="related-topics"></a><span data-ttu-id="22421-112">関連トピック</span><span class="sxs-lookup"><span data-stu-id="22421-112">Related Topics</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="22421-113">すべてのカスタム オブジェクトに共通の情報</span><span class="sxs-lookup"><span data-stu-id="22421-113">Information Common to all Custom Objects</span></span>
 <span data-ttu-id="22421-114">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22421-114">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="22421-115">[Integration Services 用のカスタムオブジェクトの開発](../developing-custom-objects-for-integration-services.md)のすべての種類のカスタムオブジェクトを実装するための基本的な手順について説明し [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="22421-115">[Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="22421-116">[カスタムオブジェクトの永続](../persisting-custom-objects.md)化カスタムの永続性について説明し、必要な場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-116">[Persisting Custom Objects](../persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="22421-117">[カスタムオブジェクトのビルド、配置、およびデバッグ](../building-deploying-and-debugging-custom-objects.md)カスタムオブジェクトのビルド、署名、配置、およびデバッグの手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-117">[Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="22421-118">その他のカスタム オブジェクトに関する情報</span><span class="sxs-lookup"><span data-stu-id="22421-118">Information about Other Custom Objects</span></span>
 <span data-ttu-id="22421-119">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22421-119">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="22421-120">[カスタムタスクの開発](../task/developing-a-custom-task.md)カスタムタスクをプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-120">[Developing a Custom Task](../task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="22421-121">[カスタム接続マネージャーの開発](../connection-manager/developing-a-custom-connection-manager.md)カスタム接続マネージャーをプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-121">[Developing a Custom Connection Manager](../connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="22421-122">[カスタム ForEach 列挙子の開発](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)カスタム列挙子をプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-122">[Developing a Custom ForEach Enumerator](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

 <span data-ttu-id="22421-123">[カスタムデータフローコンポーネントの開発](../data-flow/developing-a-custom-data-flow-component.md)カスタムデータフローの変換元、変換、および変換先をプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22421-123">[Developing a Custom Data Flow Component](../data-flow/developing-a-custom-data-flow-component.md) Discusses how to program custom data flow sources, transformations, and destinations.</span></span>

<span data-ttu-id="22421-124">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="22421-124">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="22421-125">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22421-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="22421-126">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="22421-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="22421-127">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="22421-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>


