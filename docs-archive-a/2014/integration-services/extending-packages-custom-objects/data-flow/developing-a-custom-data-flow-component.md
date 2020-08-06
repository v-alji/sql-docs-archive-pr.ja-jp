---
title: カスタム データ フロー コンポーネントの開発 | Microsoft Docs
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
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7126129ede3f419c6fbdcae6245a47636e6e65ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718603"
---
# <a name="developing-a-custom-data-flow-component"></a><span data-ttu-id="808ae-102">カスタム データ フロー コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="808ae-102">Developing a Custom Data Flow Component</span></span>
  <span data-ttu-id="808ae-103">データ フロー タスクは、さまざまなデータ ソースに接続し、そのデータを高速で変換およびルーティングするコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="808ae-103">The data flow task consists of components that connect to a variety of data sources and then transform and route that data at high speed.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="808ae-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、拡張可能なオブジェクト モデルが用意されており、開発者はそのオブジェクト モデルを使用して、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] や配置されたパッケージで使用できるカスタム変換元、カスタム変換、およびカスタム変換先を作成できます。</span><span class="sxs-lookup"><span data-stu-id="808ae-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides an extensible object model that lets developers create custom sources, transformations, and destinations that you can use in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and in deployed packages.</span></span> <span data-ttu-id="808ae-105">ここでは、カスタム データ フロー コンポーネントの開発に役立つトピックを紹介します。</span><span class="sxs-lookup"><span data-stu-id="808ae-105">This section contains topics that will guide you in developing custom data flow components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="808ae-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="808ae-106">In This Section</span></span>
 <span data-ttu-id="808ae-107">[カスタムデータフローコンポーネントの作成](creating-a-custom-data-flow-component.md)カスタムデータフローコンポーネントを作成するための最初の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-107">[Creating a Custom Data Flow Component](creating-a-custom-data-flow-component.md) Describes the initial steps in creating a custom data flow component.</span></span>

 <span data-ttu-id="808ae-108">[データフローコンポーネントのデザイン時のメソッド](design-time-methods-of-a-data-flow-component.md)カスタムデータフローコンポーネントに実装するデザイン時のメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-108">[Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md) Describes the design-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="808ae-109">[データフローコンポーネントの実行時のメソッド](run-time-methods-of-a-data-flow-component.md)カスタムデータフローコンポーネントに実装する実行時のメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-109">[Run-time Methods of a Data Flow Component](run-time-methods-of-a-data-flow-component.md) Describes the run-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="808ae-110">[実行プランとバッファー割り当て](execution-plan-and-buffer-allocation.md)データフロー実行プランとデータバッファーの割り当てについて説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-110">[Execution Plan and Buffer Allocation](execution-plan-and-buffer-allocation.md) Describes the data flow execution plan and the allocation of data buffers.</span></span>

 <span data-ttu-id="808ae-111">[データフローでのデータ型の操作](working-with-data-types-in-the-data-flow.md)データフローがデータ [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 型を .NET Framework マネージデータ型にマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-111">[Working with Data Types in the Data Flow](working-with-data-types-in-the-data-flow.md) Explains how the data flow maps [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types to .NET Framework managed data types.</span></span>

 <span data-ttu-id="808ae-112">[データフローコンポーネントの検証](validating-a-data-flow-component.md)コンポーネントの構成を検証し、コンポーネントのメタデータを再構成するために使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-112">[Validating a Data Flow Component](validating-a-data-flow-component.md) Explains the methods used to validate component configuration and to reconfigure component metadata.</span></span>

 <span data-ttu-id="808ae-113">[外部メタデータの実装](implementing-external-metadata.md)データの検証に外部メタデータ列を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-113">[Implementing External Metadata](implementing-external-metadata.md) Explains how to use external metadata columns for data validation.</span></span>

 <span data-ttu-id="808ae-114">[データフローコンポーネントでのイベントの発生と定義](raising-and-defining-events-in-a-data-flow-component.md)定義済みおよびカスタムイベントを発生させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-114">[Raising and Defining Events in a Data Flow Component](raising-and-defining-events-in-a-data-flow-component.md) Explains how to raise predefined and custom events.</span></span>

 <span data-ttu-id="808ae-115">[データフローコンポーネントのログエントリのログ記録と定義](logging-and-defining-log-entries-in-a-data-flow-component.md)カスタムログエントリを作成して書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-115">[Logging and Defining Log Entries in a Data Flow Component](logging-and-defining-log-entries-in-a-data-flow-component.md) Explains how to create and write to custom log entries.</span></span>

 <span data-ttu-id="808ae-116">[データフローコンポーネントでのエラー出力の使用](using-error-outputs-in-a-data-flow-component.md)エラー行を別の出力にリダイレクトする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-116">[Using Error Outputs in a Data Flow Component](using-error-outputs-in-a-data-flow-component.md) Explains how to redirect error rows to an alternative output.</span></span>

 <span data-ttu-id="808ae-117">[データフローコンポーネントのバージョンのアップグレード](upgrading-the-version-of-a-data-flow-component.md)コンポーネントの新しいバージョンが最初に使用されたときに、保存されたコンポーネントのメタデータを更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-117">[Upgrading the Version of a Data Flow Component](upgrading-the-version-of-a-data-flow-component.md) Explains how to update saved component metadata when a new version of your component is first used.</span></span>

 <span data-ttu-id="808ae-118">[データフローコンポーネントのユーザーインターフェイスの開発](developing-a-user-interface-for-a-data-flow-component.md)コンポーネントのカスタムエディターを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-118">[Developing a User Interface for a Data Flow Component](developing-a-user-interface-for-a-data-flow-component.md) Explains how to implement a custom editor for a component.</span></span>

 <span data-ttu-id="808ae-119">[特定の種類のデータフローコンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)変換元、変換、および変換先という3種類のデータフローコンポーネントの開発について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-119">[Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Contains information about developing the three types of data flow components: sources, transformations, and destinations.</span></span>

## <a name="reference"></a><span data-ttu-id="808ae-120">リファレンス</span><span class="sxs-lookup"><span data-stu-id="808ae-120">Reference</span></span>
 <span data-ttu-id="808ae-121"><xref:Microsoft.SqlServer.Dts.Pipeline>カスタムデータフローコンポーネントの作成に使用されるクラスとインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="808ae-121"><xref:Microsoft.SqlServer.Dts.Pipeline> Contains the classes and interfaces used to create custom data flow components.</span></span>

 <span data-ttu-id="808ae-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>データフロータスクオブジェクトモデルを構成するクラスとインターフェイスが含まれています。これは、カスタムデータフローコンポーネントを作成したり、データフロータスクを作成したりするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="808ae-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> Contains the classes and interfaces that make up the data flow task object model, and is used to create custom data flow components or build a data flow task.</span></span>

 <span data-ttu-id="808ae-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design>データフローコンポーネントのユーザーインターフェイスを作成するために使用されるクラスとインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="808ae-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design> Contains the classes and interfaces used to create the user interface for data flow components.</span></span>

 <span data-ttu-id="808ae-124">[Integration Services のエラーとメッセージの参照](../../integration-services-error-and-message-reference.md)定義済みの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] エラーコードとそのシンボル名と説明を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="808ae-124">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="808ae-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="808ae-125">Related Sections</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="808ae-126">すべてのカスタム オブジェクトに共通の情報</span><span class="sxs-lookup"><span data-stu-id="808ae-126">Information Common to All Custom Objects</span></span>
 <span data-ttu-id="808ae-127">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="808ae-127">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="808ae-128">[Integration Services 用のカスタムオブジェクトの開発](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)のすべての種類のカスタムオブジェクトを実装するための基本的な手順について説明し [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="808ae-128">[Developing Custom Objects for Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="808ae-129">[カスタムオブジェクトの永続](../../extending-packages-custom-objects/persisting-custom-objects.md)化カスタムの永続性について説明し、必要な場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-129">[Persisting Custom Objects](../../extending-packages-custom-objects/persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="808ae-130">[カスタムオブジェクトのビルド、配置、およびデバッグ](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)カスタムオブジェクトのビルド、署名、配置、およびデバッグの手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-130">[Building, Deploying, and Debugging Custom Objects](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="808ae-131">その他のカスタム オブジェクトに関する情報</span><span class="sxs-lookup"><span data-stu-id="808ae-131">Information about Other Custom Objects</span></span>
 <span data-ttu-id="808ae-132">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="808ae-132">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="808ae-133">[カスタムタスクの開発](../../extending-packages-custom-objects/task/developing-a-custom-task.md)カスタムタスクをプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-133">[Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="808ae-134">[カスタム接続マネージャーの開発](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)カスタム接続マネージャーをプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-134">[Developing a Custom Connection Manager](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="808ae-135">[カスタムログプロバイダーの開発](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)カスタムログプロバイダーをプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-135">[Developing a Custom Log Provider](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Discusses how to program custom log providers.</span></span>

 <span data-ttu-id="808ae-136">[カスタム ForEach 列挙子の開発](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)カスタム列挙子をプログラミングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="808ae-136">[Developing a Custom ForEach Enumerator](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

<span data-ttu-id="808ae-137">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="808ae-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="808ae-138">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="808ae-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="808ae-139">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="808ae-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="808ae-140">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="808ae-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="808ae-141">参照</span><span class="sxs-lookup"><span data-stu-id="808ae-141">See Also</span></span>
 <span data-ttu-id="808ae-142">[スクリプトコンポーネントによるデータフローの拡張](../../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md[スクリプトソリューションとカスタムオブジェクトの比較](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)</span><span class="sxs-lookup"><span data-stu-id="808ae-142">[Extending the Data Flow with the Script Component](../../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md [Comparing Scripting Solutions and Custom Objects](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)</span></span>


