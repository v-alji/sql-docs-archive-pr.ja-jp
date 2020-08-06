---
title: タスクまたはコンテナーのプロパティを設定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], properties
ms.assetid: 52d47ca4-fb8c-493d-8b2b-48bb269f859b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0a4c556b94af02c2f874f2740a70b1294c35e653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742373"
---
# <a name="set-the-properties-of-a-task-or-container"></a><span data-ttu-id="a7e15-102">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="a7e15-102">Set the Properties of a Task or Container</span></span>
  <span data-ttu-id="a7e15-103">タスクおよびコンテナーのほとんどのプロパティは、 **[プロパティ]** ウィンドウを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-103">You can set most properties of tasks and containers by using the **Properties** window.</span></span> <span data-ttu-id="a7e15-104">例外は、タスク コレクションのプロパティと、 **[プロパティ]** ウィンドウを使用して設定するには複雑すぎるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a7e15-104">The exceptions are properties of task collections and properties that are too complex to set by using the **Properties** window.</span></span> <span data-ttu-id="a7e15-105">たとえば、Foreach ループ コンテナーが使用する列挙子を **[プロパティ]** ウィンドウで構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7e15-105">For example, you cannot configure the enumerator that the Foreach Loop container uses in the **Properties** window.</span></span> <span data-ttu-id="a7e15-106">これらの複雑なプロパティを設定するには、タスク エディターまたはコンテナー エディターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7e15-106">You must use a task or container editor to set these complex properties.</span></span> <span data-ttu-id="a7e15-107">ほとんどの場合、タスク エディターとコンテナー エディターには複数のノードがあり、各ノードには関連プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7e15-107">Most task and container editors have multiple nodes and each node contains related properties.</span></span> <span data-ttu-id="a7e15-108">ノードの名前は、ノードに含まれるプロパティの対象を示します。</span><span class="sxs-lookup"><span data-stu-id="a7e15-108">The name of the node indicates the subject of the properties that the node contains.</span></span>  
  
 <span data-ttu-id="a7e15-109">次の手順では、 **[プロパティ]** ウィンドウを使用するか、対応するタスク エディターまたはコンテナー エディターを使用してタスクまたはコンテナーのプロパティを設定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a7e15-109">The following procedures describe how to set the properties of a task or container by using either the **Properties** windows, or the corresponding task or container editor.</span></span>  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-the-properties-window"></a><span data-ttu-id="a7e15-110">[プロパティ] ウィンドウを使用してタスクまたはコンテナーのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="a7e15-110">To set the properties of a task or container by using the Properties window</span></span>  
  
1.  <span data-ttu-id="a7e15-111">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a7e15-112">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a7e15-113">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e15-113">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a7e15-114">**[制御フロー]** タブのデザイン画面でタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e15-114">On the design surface of the **Control Flow** tab, right-click the task or container, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="a7e15-115">**[プロパティ]** ウィンドウで、プロパティの値を更新します。</span><span class="sxs-lookup"><span data-stu-id="a7e15-115">In the **Properties** window, update the property value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7e15-116">ほとんどのプロパティは、テキスト ボックスに値を直接入力するか、一覧から値を選択することによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-116">Most properties can be set by typing a value directly in the text box, or by selecting a value from a list.</span></span> <span data-ttu-id="a7e15-117">ただし、カスタムのプロパティ エディターが用意されている複雑なプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="a7e15-117">However, some properties are more complex and have a custom property editor.</span></span> <span data-ttu-id="a7e15-118">このプロパティを設定するには、テキスト ボックス内をクリックしてから、作成ボタン ( **[...]** ) をクリックしてカスタム エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-118">To set the property, click in the text box, and then click the build **(...)** button to open the custom editor.</span></span>  
  
6.  <span data-ttu-id="a7e15-119">必要に応じて、タスクまたはコンテナーのプロパティを動的に更新するプロパティ式を作成します。</span><span class="sxs-lookup"><span data-stu-id="a7e15-119">Optionally, create property expressions to dynamically update the properties of the task or container.</span></span> <span data-ttu-id="a7e15-120">詳細については、「 [プロパティ式を追加または変更する](expressions/add-or-change-a-property-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e15-120">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="a7e15-121">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e15-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-a-task-or-container-editor"></a><span data-ttu-id="a7e15-122">タスク エディターまたはコンテナー エディターを使用してタスクまたはコンテナーのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="a7e15-122">To set the properties of a task or container by using a task or container editor</span></span>  
  
1.  <span data-ttu-id="a7e15-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a7e15-124">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-124">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a7e15-125">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e15-125">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a7e15-126">**[制御フロー]** タブのデザイン画面でタスクまたはコンテナーを右クリックし、ショートカット メニューの **[編集]** をクリックして、対応するタスク エディターまたはコンテナー エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7e15-126">On the design surface of the **Control Flow** tab, right-click the task or container, and then click **Edit** to open the corresponding task or container editor.</span></span>  
  
     <span data-ttu-id="a7e15-127">For ループ コンテナーの構成方法については、「 [Configure a For Loop Container](control-flow/for-loop-container.md)」(For ループ コンテナーを構成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e15-127">For information about how to configure the For Loop container, see [Configure a For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
     <span data-ttu-id="a7e15-128">Foreach ループコンテナーの構成方法については、「 [Foreach ループコンテナーを構成](control-flow/foreach-loop-container.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e15-128">For information about how to configure the Foreach Loop container, see [Configure a Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7e15-129">シーケンス コンテナーには、カスタム エディターはありません。</span><span class="sxs-lookup"><span data-stu-id="a7e15-129">The Sequence container has no custom editor.</span></span>  
  
5.  <span data-ttu-id="a7e15-130">タスク エディターまたはコンテナー エディターに複数のノードがある場合、設定するプロパティが含まれるノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e15-130">If the task or container editor has multiple nodes, click the node that contains the property that you want to set.</span></span>  
  
6.  <span data-ttu-id="a7e15-131">必要に応じて **[式]** をクリックし、 **[式]** ページで、タスクまたはコンテナーのプロパティを動的に更新するプロパティ式を作成します。</span><span class="sxs-lookup"><span data-stu-id="a7e15-131">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions to dynamically update the properties of the task or container.</span></span> <span data-ttu-id="a7e15-132">詳細については、「 [プロパティ式を追加または変更する](expressions/add-or-change-a-property-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e15-132">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="a7e15-133">プロパティ値を更新します。</span><span class="sxs-lookup"><span data-stu-id="a7e15-133">Update the property value.</span></span>  
  
8.  <span data-ttu-id="a7e15-134">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7e15-134">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e15-135">参照</span><span class="sxs-lookup"><span data-stu-id="a7e15-135">See Also</span></span>  
 <span data-ttu-id="a7e15-136">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a7e15-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="a7e15-137">Integration Services コンテナー</span><span class="sxs-lookup"><span data-stu-id="a7e15-137">Integration Services Containers</span></span>](control-flow/integration-services-containers.md)  
  
  
