---
title: プログラムによるパッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ef8fd0b6b5bdeead718f204a0933771fe58924a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639609"
---
# <a name="building-packages-programmatically"></a><span data-ttu-id="081a9-102">プログラムによるパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="081a9-102">Building Packages Programmatically</span></span>
  <span data-ttu-id="081a9-103">パッケージを動的に作成する必要がある場合、または開発環境以外で [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理および実行する必要がある場合は、プログラムでパッケージを操作できます。</span><span class="sxs-lookup"><span data-stu-id="081a9-103">If you need to create packages dynamically, or to manage and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="081a9-104">この場合、次に示すような一連の方法があります。</span><span class="sxs-lookup"><span data-stu-id="081a9-104">In this approach, you have a continuous range of options:</span></span>

-   <span data-ttu-id="081a9-105">既存のパッケージを読み込んで、変更せずに実行します。</span><span class="sxs-lookup"><span data-stu-id="081a9-105">Load and execute an existing package without modification.</span></span>

-   <span data-ttu-id="081a9-106">既存のパッケージを読み込み、(別のデータ ソースを指定するなど) 再構成してから実行します。</span><span class="sxs-lookup"><span data-stu-id="081a9-106">Load an existing package, reconfigure it (for example, for a different data source), and execute it.</span></span>

-   <span data-ttu-id="081a9-107">新しいパッケージを作成し、オブジェクト単位やプロパティ単位でコンポーネントを追加および構成し、保存してから実行します。</span><span class="sxs-lookup"><span data-stu-id="081a9-107">Create a new package, add and configure components object by object and property by property, save it, and execute it.</span></span>

 <span data-ttu-id="081a9-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルを使用すると、任意のマネージド プログラミング言語でパッケージを作成、構成、および実行するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="081a9-108">You can use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to write code that creates, configures, and executes packages in any managed programming language.</span></span> <span data-ttu-id="081a9-109">たとえば、選択したデータ ソースとそのテーブルおよび列に基づいて、パッケージの接続またはデータ ソース、変換、および変換先を構成するメタデータ ドリブン パッケージの作成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="081a9-109">For example, you may want to create metadata-driven packages that configure their connections or their data sources, transformations, and destinations based on the selected data source and its tables and columns.</span></span>

 <span data-ttu-id="081a9-110">ここでは、プログラムを使用してパッケージを行単位で作成および構成する方法を説明し、その例を示します。</span><span class="sxs-lookup"><span data-stu-id="081a9-110">This section describes and demonstrates how to create and configure a package programmatically line by line.</span></span> <span data-ttu-id="081a9-111">パッケージ プログラミングの最も簡単な方法では、「[プログラムによるパッケージの実行と管理](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)」に示すように、既存のパッケージを読み込んで、変更せずに実行できます。</span><span class="sxs-lookup"><span data-stu-id="081a9-111">At the less complex end of the range of package programming options, you can simply load and run an existing package without modification as described in [Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).</span></span>

 <span data-ttu-id="081a9-112">ここに示されていない中レベルの方法としては、既存のパッケージをテンプレートとして読み込み、再構成 (異なるデータ ソースの指定など) してから実行する方法があります。</span><span class="sxs-lookup"><span data-stu-id="081a9-112">An intermediate option not described here is that of loading an existing package as a template, reconfiguring it (for example, for a different data source), and executing it.</span></span> <span data-ttu-id="081a9-113">ここに記載された情報を使用して、パッケージ内の既存のオブジェクトを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="081a9-113">You can also use the information in this section to modify the existing objects in a package.</span></span>

> [!NOTE]
>  <span data-ttu-id="081a9-114">既存のパッケージをテンプレートとして使用し、データ フロー内の既存の列を変更する場合、状況によっては、既存の列を削除してから、影響を受けるコンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="081a9-114">When you use an existing package as a template and modify existing columns in the data flow, you may have to remove existing columns and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method of affected components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="081a9-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="081a9-115">In This Section</span></span>
 <span data-ttu-id="081a9-116">[プログラムによるパッケージの作成](../building-packages-programmatically/creating-a-package-programmatically.md)プログラムによってパッケージを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-116">[Creating a Package Programmatically](../building-packages-programmatically/creating-a-package-programmatically.md) Describes how to create a package programmatically.</span></span>

 <span data-ttu-id="081a9-117">[プログラムによるタスクの追加](../building-packages-programmatically/adding-tasks-programmatically.md)パッケージにタスクを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-117">[Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md) Describes how to add tasks to the package.</span></span>

 <span data-ttu-id="081a9-118">[プログラムによるタスクの接続](../building-packages-programmatically/connecting-tasks-programmatically.md)前のタスクまたはコンテナーの実行結果に基づいて、パッケージ内のコンテナーおよびタスクの実行を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-118">[Connecting Tasks Programmatically](../building-packages-programmatically/connecting-tasks-programmatically.md) Describes how to control execution of the containers and tasks in a package based on the result of the execution of a previous task or container.</span></span>

 <span data-ttu-id="081a9-119">[プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)接続マネージャーをパッケージに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-119">[Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md) Describes how to add connection managers to a package.</span></span>

 <span data-ttu-id="081a9-120">[プログラムによる変数の](../building-packages-programmatically/working-with-variables-programmatically.md)使用パッケージの実行中に変数を追加して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-120">[Working with Variables Programmatically](../building-packages-programmatically/working-with-variables-programmatically.md) Describes how to add and use variables during package execution.</span></span>

 <span data-ttu-id="081a9-121">[プログラムによるイベントの処理](../building-packages-programmatically/handling-events-programmatically.md)パッケージとタスクのイベントを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-121">[Handling Events Programmatically](../building-packages-programmatically/handling-events-programmatically.md) Describes how to handle package and task events.</span></span>

 <span data-ttu-id="081a9-122">[プログラムによるログ記録の有効化](../building-packages-programmatically/enabling-logging-programmatically.md)パッケージまたはタスクのログ記録を有効にする方法と、カスタムフィルターをログイベントに適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-122">[Enabling Logging Programmatically](../building-packages-programmatically/enabling-logging-programmatically.md) Describes how to enable logging for a package or task, and how to apply custom filters to log events.</span></span>

 <span data-ttu-id="081a9-123">[プログラムによるデータフロータスクの追加](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)データフロータスクとそのコンポーネントを追加して構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-123">[Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) Describes how to add and configure the Data Flow task and its components.</span></span>

 <span data-ttu-id="081a9-124">[プログラムによるデータフローコンポーネントの検出](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)ローカルコンピューターにインストールされているコンポーネントを検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-124">[Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) Describes how to detect the components that are installed on the local computer.</span></span>

 <span data-ttu-id="081a9-125">[プログラムによるデータフローコンポーネントの追加](../building-packages-programmatically/adding-data-flow-components-programmatically.md)コンポーネントをデータフロータスクに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-125">[Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md) Describes how to add a component to a data flow task.</span></span>

 <span data-ttu-id="081a9-126">[プログラムによるデータフローコンポーネントの接続](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)2つのデータフローコンポーネントを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-126">[Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) Describes how to connect two data flow components.</span></span>

 <span data-ttu-id="081a9-127">[プログラムによる入力列の選択](../building-packages-programmatically/selecting-input-columns-programmatically.md)データフローの上流コンポーネントによってコンポーネントに提供される入力列を選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-127">[Selecting Input Columns Programmatically](../building-packages-programmatically/selecting-input-columns-programmatically.md) Describes how to select input columns from those that are provided to a component by upstream components in the data flow.</span></span>

 <span data-ttu-id="081a9-128">[プログラムによるパッケージの保存](../building-packages-programmatically/saving-a-package-programmatically.md)プログラムによってパッケージを保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-128">[Saving a Package Programmatically](../building-packages-programmatically/saving-a-package-programmatically.md) Describes how to save a package programmatically.</span></span>

## <a name="reference"></a><span data-ttu-id="081a9-129">リファレンス</span><span class="sxs-lookup"><span data-stu-id="081a9-129">Reference</span></span>
 <span data-ttu-id="081a9-130">[Integration Services のエラーとメッセージの参照](../integration-services-error-and-message-reference.md)定義済みの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラーコードとそのシンボル名と説明を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="081a9-130">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="081a9-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="081a9-131">Related Sections</span></span>
 <span data-ttu-id="081a9-132">[スクリプトを使用したパッケージの拡張](../extending-packages-scripting/extending-packages-with-scripting.md)スクリプトタスクを使用して制御フローを拡張する方法と、スクリプトコンポーネントを使用してデータフローを拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-132">[Extending Packages with Scripting](../extending-packages-scripting/extending-packages-with-scripting.md) Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>

 <span data-ttu-id="081a9-133">[カスタムオブジェクトを使用したパッケージの拡張](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)複数のパッケージで使用するプログラムカスタムタスク、データフローコンポーネント、およびその他のパッケージオブジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-133">[Extending Packages with Custom Objects](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>

 <span data-ttu-id="081a9-134">[プログラムによるパッケージの実行と管理](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)パッケージ、およびパッケージが格納されているフォルダーを列挙、実行、および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="081a9-134">[Running and Managing Packages Programmatically](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) Discusses how to enumerate, run, and manage packages and the folders in which they are stored.</span></span>

## <a name="external-resources"></a><span data-ttu-id="081a9-135">外部リソース</span><span class="sxs-lookup"><span data-stu-id="081a9-135">External Resources</span></span>

-   <span data-ttu-id="081a9-136">[www.codeplex.com/MSFTISProdSamples](www.codeplex.com/MSFTISProdSamples) の CodePlex サンプル「[Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkID=131204)」</span><span class="sxs-lookup"><span data-stu-id="081a9-136">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>

-   <span data-ttu-id="081a9-137">blogs.msdn.com のブログ「[カスタム拡張機能のパフォーマンスのプロファイル](https://go.microsoft.com/fwlink/?LinkId=238831)」</span><span class="sxs-lookup"><span data-stu-id="081a9-137">Blog entry, [Performance profiling your custom extensions](https://go.microsoft.com/fwlink/?LinkId=238831), on blogs.msdn.com.</span></span>

<span data-ttu-id="081a9-138">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="081a9-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="081a9-139">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="081a9-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="081a9-140">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="081a9-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="081a9-141">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="081a9-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="081a9-142">参照</span><span class="sxs-lookup"><span data-stu-id="081a9-142">See Also</span></span>
 [<span data-ttu-id="081a9-143">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="081a9-143">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)


