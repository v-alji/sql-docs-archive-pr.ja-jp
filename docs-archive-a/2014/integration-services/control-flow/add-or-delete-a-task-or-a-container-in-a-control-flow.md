---
title: 制御フローのタスクまたはコンテナーを追加または削除する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], adding
- adding tasks
- adding containers
- tasks [Integration Services], adding
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8338a4143358d732a974287e587f482dc5c36a22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641821"
---
# <a name="add-or-delete-a-task-or-a-container-in-a-control-flow"></a><span data-ttu-id="bbb33-102">制御フローのタスクまたはコンテナーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="bbb33-102">Add or Delete a Task or a Container in a Control Flow</span></span>
  <span data-ttu-id="bbb33-103">制御フロー デザイナーでの作業中、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーのツールボックスには、パッケージの制御フローの作成用に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で用意されているタスクが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-103">When you are working in the control flow designer, the Toolbox in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists the tasks that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides for building control flow in a package.</span></span> <span data-ttu-id="bbb33-104">ツールボックスの詳細については、「 [SSIS ツールボックス](../ssis-toolbox.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbb33-104">For more information about the Toolbox, see [SSIS Toolbox](../ssis-toolbox.md).</span></span>  
  
 <span data-ttu-id="bbb33-105">1 つのパッケージには、同じタスクのインスタンスを複数含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-105">A package can include multiple instances of the same task.</span></span> <span data-ttu-id="bbb33-106">タスクの各インスタンスは、パッケージ内で一意に識別され、各インスタンスは個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-106">Each instance of a task is uniquely identified in the package, and you can configure each instance differently.</span></span>  
  
 <span data-ttu-id="bbb33-107">タスクを削除すると、そのタスクを制御フロー内の別のタスクやコンテナーに連結する優先順位制約も、同様に削除されます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-107">If you delete a task, the precedence constraints that connect the task to other tasks and containers in the control flow are also deleted.</span></span>  
  
 <span data-ttu-id="bbb33-108">次の手順では、パッケージの制御フローのタスクまたはコンテナーを追加または削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb33-108">The following procedures describe how to add or delete a task or container in the control flow of a package.</span></span>  
  
### <a name="to-add-a-task-or-a-container-to-a-control-flow"></a><span data-ttu-id="bbb33-109">制御フローにタスクまたはコンテナーを追加するには</span><span class="sxs-lookup"><span data-stu-id="bbb33-109">To add a task or a container to a control flow</span></span>  
  
1.  <span data-ttu-id="bbb33-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="bbb33-111">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="bbb33-112">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="bbb33-113">**[ツールボックス]** を開くには、 **[表示]** メニューの **[ツールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-113">To open the **Toolbox**, click **Toolbox** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="bbb33-114">**[制御フロー項目]** と **[メンテナンス タスク]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="bbb33-114">Expand **Control Flow Items** and **Maintenance Tasks**.</span></span>  
  
6.  <span data-ttu-id="bbb33-115">タスクとコンテナーを、 **[ツールボックス]** から **[制御フロー]** タブのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-115">Drag tasks and containers from the **Toolbox** to the design surface of the **Control Flow** tab.</span></span>  
  
7.  <span data-ttu-id="bbb33-116">パッケージの制御フロー内のタスクまたはコンテナーのコネクタをドラッグし、タスクまたはコンテナーを制御フロー内の別のコンポーネントに連結します。</span><span class="sxs-lookup"><span data-stu-id="bbb33-116">Connect a task or container within the package control flow by dragging its connector to another component in the control flow.</span></span>  
  
8.  <span data-ttu-id="bbb33-117">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-117">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-task-or-a-container-from-a-control-flow"></a><span data-ttu-id="bbb33-118">制御フローからタスクまたはコンテナーを削除するには</span><span class="sxs-lookup"><span data-stu-id="bbb33-118">To delete a task or a container from a control flow</span></span>  
  
1.  <span data-ttu-id="bbb33-119">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="bbb33-120">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-120">In Solution Explorer, double-click the package to open it.</span></span> <span data-ttu-id="bbb33-121">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="bbb33-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="bbb33-122">**[制御フロー]** タブをクリックし、削除するタスクまたはコンテナーを右クリックして **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-122">Click the **Control Flow** tab, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
    -   <span data-ttu-id="bbb33-123">**パッケージ エクスプローラー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="bbb33-123">Open **Package Explorer**.</span></span> <span data-ttu-id="bbb33-124">**[実行可能ファイル]** フォルダーで削除するタスクまたはコンテナーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-124">From the **Executables** folder, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="bbb33-125">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbb33-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb33-126">参照</span><span class="sxs-lookup"><span data-stu-id="bbb33-126">See Also</span></span>  
 <span data-ttu-id="bbb33-127">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bbb33-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="bbb33-128">[Integration Services コンテナー](integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="bbb33-128">[Integration Services Containers](integration-services-containers.md) </span></span>  
 [<span data-ttu-id="bbb33-129">制御フロー</span><span class="sxs-lookup"><span data-stu-id="bbb33-129">Control Flow</span></span>](control-flow.md)  
  
  
