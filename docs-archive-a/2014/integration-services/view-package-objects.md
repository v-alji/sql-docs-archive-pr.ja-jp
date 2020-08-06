---
title: パッケージ オブジェクトを表示する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffe46be35db26186f715b18ba6114732d130e02e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642861"
---
# <a name="view-package-objects"></a><span data-ttu-id="93d96-102">パッケージ オブジェクトを表示する</span><span class="sxs-lookup"><span data-stu-id="93d96-102">View Package Objects</span></span>
  <span data-ttu-id="93d96-103">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでは、 **[パッケージ エクスプローラー]** タブで、パッケージをエクスプローラー表示できます。</span><span class="sxs-lookup"><span data-stu-id="93d96-103">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the **Package Explorer** tab provides an explorer view of the package.</span></span> <span data-ttu-id="93d96-104">この表示には、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] アーキテクチャのコンテナー階層が反映されます。</span><span class="sxs-lookup"><span data-stu-id="93d96-104">The view reflects the container hierarchy of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] architecture.</span></span> <span data-ttu-id="93d96-105">パッケージ コンテナーはこの階層の最上層にあり、パッケージを展開すると、そのパッケージ内にある接続、実行可能ファイル、イベント ハンドラー、ログ プロバイダー、優先順位制約、および変数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="93d96-105">The package container is at the top of the hierarchy, and you expand the package to view the connections, executables, event handlers, log providers, precedence constraints, and variables in the package.</span></span>

 <span data-ttu-id="93d96-106">実行可能ファイルとは、パッケージ内のコンテナーおよびタスクのことで、イベント ハンドラー、優先順位制約、および変数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="93d96-106">The executables, which are the containers and tasks in the package, can include event handlers, precedence constraints, and variables.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="93d96-107">では、入れ子構造の階層のコンテナーがサポートされているため、For ループ コンテナー、Foreach ループ コンテナー、およびシーケンス コンテナーは他の実行可能ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="93d96-107">supports a nested hierarchy of containers, and the For Loop, Foreach Loop, and Sequence containers can include other executables.</span></span>

 <span data-ttu-id="93d96-108">パッケージにデータ フローが含まれる場合、 **パッケージ エクスプローラー** にはデータ フロー タスクが一覧表示され、データ フロー コンポーネントを一覧表示する **[コンポーネント]** フォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="93d96-108">If a package includes a data flow, the **Package Explorer** lists the Data Flow task and includes a **Components** folder that lists the data flow components.</span></span>

 <span data-ttu-id="93d96-109">**[パッケージ エクスプローラー]** タブでは、パッケージ内のオブジェクトを削除したり、 **[プロパティ]** ウィンドウにアクセスしてオブジェクトのプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="93d96-109">From the **Package Explorer** tab, you can delete objects in a package and access the **Properties** window to view object properties.</span></span>

 <span data-ttu-id="93d96-110">次の図は、簡単なパッケージのツリー ビューを示しています。</span><span class="sxs-lookup"><span data-stu-id="93d96-110">The following diagram shows a tree view of a simple package.</span></span>

 <span data-ttu-id="93d96-111">![[パッケージ エクスプローラー] タブのスクリーンショット](media/packageexplorer.gif "[パッケージ エクスプローラー] タブのスクリーンショット")</span><span class="sxs-lookup"><span data-stu-id="93d96-111">![Screenshot of the Package Explorer tab](media/packageexplorer.gif "Screenshot of the Package Explorer tab")</span></span>

### <a name="to-view-package-content"></a><span data-ttu-id="93d96-112">パッケージの内容を表示するには</span><span class="sxs-lookup"><span data-stu-id="93d96-112">To view package content</span></span>

-   [<span data-ttu-id="93d96-113">パッケージ エクスプローラーでパッケージ オブジェクトを表示する</span><span class="sxs-lookup"><span data-stu-id="93d96-113">View Package Objects in Package Explorer</span></span>](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a><span data-ttu-id="93d96-114">参照</span><span class="sxs-lookup"><span data-stu-id="93d96-114">See Also</span></span>
 <span data-ttu-id="93d96-115">[Integration Services タスク](control-flow/integration-services-tasks.md) [Integration Services コンテナーの](control-flow/integration-services-containers.md)[優先順位制約](control-flow/precedence-constraints.md) [Integration Services &#40;Ssis](integration-services-ssis-variables.md)&#41; INTEGRATION SERVICES &#40;ssis&#41;[イベントハンドラー](integration-services-ssis-event-handlers.md) Integration Services &#40;ssis&#41; の[ログ記録](performance/integration-services-ssis-logging.md)</span><span class="sxs-lookup"><span data-stu-id="93d96-115">[Integration Services Tasks](control-flow/integration-services-tasks.md) [Integration Services Containers](control-flow/integration-services-containers.md) [Precedence Constraints](control-flow/precedence-constraints.md) [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md)</span></span>


