---
title: コンポーネントのグループ化とグループの解除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6811dffca41a12fe0afeeeb334e0107ac127c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632584"
---
# <a name="group-or-ungroup-components"></a><span data-ttu-id="d0f5b-102">コンポーネントのグループ化とグループの解除</span><span class="sxs-lookup"><span data-stu-id="d0f5b-102">Group or Ungroup Components</span></span>
  <span data-ttu-id="d0f5b-103">**デザイナーの**[制御フロー] **、** [データ フロー] **、および** [イベント ハンドラー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブでは、折りたたみ可能なグループ化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-103">The **Control Flow**, **Data Flow**, and **Event Handlers** tabs in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer supports collapsible grouping.</span></span> <span data-ttu-id="d0f5b-104">パッケージに多数のコンポーネントがある場合、タブは過密状態になることがあります。このような状態になると、すべてのコンポーネントを一度に表示するのが難しくなり、操作する項目を探すのも困難になります。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-104">If a package has many components, the tabs can become crowded, making it difficult to view all the components at one time and to locate the item with which you want to work.</span></span> <span data-ttu-id="d0f5b-105">折りたたみ可能なグループ化機能を使用すると、作業画面上の領域を節約でき、大きなパッケージの処理が容易になります。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-105">The collapsible grouping feature can conserve space on the work surface and make it easier to work with large packages.</span></span>  
  
 <span data-ttu-id="d0f5b-106">グループ化機能では、グループ化するコンポーネントを選択し、それらをグループ化します。次に、作業に合わせてグループを展開するか、折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-106">You select the components that you want to group, group them, and then expand or collapse the groups to suit your work.</span></span> <span data-ttu-id="d0f5b-107">グループを展開すると、グループ内のコンポーネントのプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-107">Expanding a group provides access to the properties of the components in the group.</span></span> <span data-ttu-id="d0f5b-108">タスクとコンテナーを連結する優先順位制約は、自動的にグループ内に含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-108">The precedence constraints that connect tasks and containers are automatically included in the group.</span></span>  
  
 <span data-ttu-id="d0f5b-109">コンポーネントのグループ化に関する注意事項は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-109">The following are considerations for grouping components.</span></span>  
  
-   <span data-ttu-id="d0f5b-110">コンポーネントをグループ化するには、コントロール フロー、データ フロー、またはイベント ハンドラーに複数のコンポーネントが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-110">To group components, the control flow, data flow, or event handler must contain more than one component.</span></span>  
  
-   <span data-ttu-id="d0f5b-111">グループは入れ子にすることもできます。これにより、グループ内にグループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-111">Groups can also be nested, making it possible to create groups within groups.</span></span> <span data-ttu-id="d0f5b-112">デザイン画面は、入れ子になっていないグループを複数実装できます。ただし、グループが入れ子になっていない場合、コンポーネントが所属できるのは 1 グループのみです。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-112">The design surface can implement multiple un-nested groups, but a component can belong to only one group, unless the groups are nested.</span></span>  
  
-   <span data-ttu-id="d0f5b-113">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーは、パッケージの保存時にグループ化を保存します。ただし、グループ化はパッケージの実行には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-113">When a package is saved, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the grouping, but the grouping has no effect on package execution.</span></span> <span data-ttu-id="d0f5b-114">コンポーネントのグループ化機能は、デザイン時の機能であり、パッケージの実行時の動作には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-114">The ability to group components is a design-time feature; it does not affect the run-time behavior of the package.</span></span>  
  
### <a name="to-group-components"></a><span data-ttu-id="d0f5b-115">コンポーネントをグループ化するには</span><span class="sxs-lookup"><span data-stu-id="d0f5b-115">To group components</span></span>  
  
1.  <span data-ttu-id="d0f5b-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d0f5b-117">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d0f5b-118">**[制御フロー]** 、 **[データ フロー]** 、または **[イベント ハンドラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-118">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="d0f5b-119">タブのデザイン画面で、グループ化するコンポーネントを選択します。選択したコンポーネントを右クリックし、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-119">On the design surface of the tab, select the components you want to group, right-click a selected component, and then click **Group**.</span></span>  
  
5.  <span data-ttu-id="d0f5b-120">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-ungroup-components"></a><span data-ttu-id="d0f5b-121">コンポーネントのグループを解除するには</span><span class="sxs-lookup"><span data-stu-id="d0f5b-121">To ungroup components</span></span>  
  
1.  <span data-ttu-id="d0f5b-122">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d0f5b-123">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d0f5b-124">**[制御フロー]** 、 **[データ フロー]** 、または **[イベント ハンドラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-124">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="d0f5b-125">タブのデザイン画面で、グループを解除するコンポーネントが含まれているグループを選択します。そのグループを右クリックし、 **[グループ解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-125">On the design surface of the tab, select the group that contains the component you want to ungroup, right-click, and then click **Ungroup**.</span></span>  
  
5.  <span data-ttu-id="d0f5b-126">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0f5b-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f5b-127">参照</span><span class="sxs-lookup"><span data-stu-id="d0f5b-127">See Also</span></span>  
 [<span data-ttu-id="d0f5b-128">制御フローのタスクまたはコンテナーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="d0f5b-128">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
     
 [<span data-ttu-id="d0f5b-129">既定の優先順位制約を使用してタスクとコンテナーを連結する</span><span class="sxs-lookup"><span data-stu-id="d0f5b-129">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
  
