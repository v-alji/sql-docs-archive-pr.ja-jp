---
title: ソリューション内の Integration Services プロジェクトを追加または削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49984c61047a6b716015bd72e518b73cb08b3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631215"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a><span data-ttu-id="9e93c-102">ソリューション内の Integration Services プロジェクトを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="9e93c-102">Add or Remove an Integration Services Project in a Solution</span></span>
  <span data-ttu-id="9e93c-103">ソリューション内の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを追加または削除する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-103">The following procedures descibe how to add or remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution.</span></span>  
  
 <span data-ttu-id="9e93c-104">プロジェクトを既存のソリューションに追加したり、既存のソリューションから削除したりできるのは、そのソリューションが [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で表示されている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9e93c-104">You can only add a project to an existing solution, or remove a project from a solution, when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="9e93c-105">で [**常にソリューションを表示**] オプションを選択した場合 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ソリューションに含まれるプロジェクトが1つしかない場合でも、によってソリューションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-105">If you have selected the **Always show solution** option in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution even when that solution contains only one project.</span></span> <span data-ttu-id="9e93c-106">このオプションを選択していない場合は、ソリューションに 2 つ以上のプロジェクトが含まれているときに限り、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でソリューションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-106">Otherwise, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution only when that solution contains more than one project.</span></span> <span data-ttu-id="9e93c-107">その他のプロジェクトは、[!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトでも他の種類のプロジェクトでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="9e93c-107">The additional projects can be either [!INCLUDE[ssIS](../includes/ssis-md.md)] projects or projects of other types.</span></span>  
  
## <a name="adding-an-integration-services-project"></a><span data-ttu-id="9e93c-108">Integration Services プロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="9e93c-108">Adding an Integration Services Project</span></span>  
 <span data-ttu-id="9e93c-109">プロジェクトを追加する場合は、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で新しい空のプロジェクトを作成することも、別のソリューション用に既に作成したプロジェクトを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-109">When you add a project, you can have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] create a new, blank project, or you can add a project that you have already created for a different solution.</span></span> <span data-ttu-id="9e93c-110">プロジェクトを既存のソリューションに追加できるのは、そのソリューションが [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で表示されている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9e93c-110">You can only add a project to an existing solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a><span data-ttu-id="9e93c-111">新しい Integration Services プロジェクトをソリューションに追加するには</span><span class="sxs-lookup"><span data-stu-id="9e93c-111">To add a new Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="9e93c-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの追加先となるソリューションを開き、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="9e93c-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="9e93c-113">ソリューションを右クリックして **[追加]** をクリックし、**[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-113">Right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
    -   <span data-ttu-id="9e93c-114">**[ファイル]** メニューの **[追加]** をポイントし、**[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-114">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="9e93c-115">**[新しいプロジェクトの追加]** ダイアログ ボックスの **[テンプレート]** ペインで、**[Integration Services プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-115">In the **Add New Project** dialog box, click **Integration Services Project** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="9e93c-116">必要に応じて、プロジェクトの名前と場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="9e93c-116">Optionally, edit the project name and location.</span></span>  
  
4.  <span data-ttu-id="9e93c-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-117">Click **OK**.</span></span>  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a><span data-ttu-id="9e93c-118">既存の Integration Services プロジェクトをソリューションに追加するには</span><span class="sxs-lookup"><span data-stu-id="9e93c-118">To add an existing Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="9e93c-119">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、既存の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを追加するソリューションを開き、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="9e93c-119">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="9e93c-120">ソリューションを右クリックして **[追加]** をポイントし、**[既存のプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-120">Right-click the solution, point to **Add**, and then click **Existing Project**.</span></span>  
  
    -   <span data-ttu-id="9e93c-121">**[ファイル]** メニューの **[追加]** をクリックし、**[既存のプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-121">On the **File** menu, click **Add**, and then click **Existing Project**.</span></span>  
  
2.  <span data-ttu-id="9e93c-122">**[既存プロジェクトの追加]** ダイアログ ボックスで、追加するプロジェクトを選択して、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-122">In the **Add Existing Project** dialog box, browse to locate the project you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="9e93c-123">選択したプロジェクトが、**ソリューション エクスプローラー**のソリューション フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-123">The project is added to the solution folder in **Solution Explorer**.</span></span>  
  
## <a name="removing-an-integration-services-project"></a><span data-ttu-id="9e93c-124">Integration Services プロジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="9e93c-124">Removing an Integration Services Project</span></span>  
 <span data-ttu-id="9e93c-125">プロジェクトをソリューションから削除できるのは、そのソリューションが [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で表示されている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9e93c-125">You can only remove a project from a solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="9e93c-126">ソリューションが表示されていれば、1 つのプロジェクト以外はすべて削除できます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-126">After the solution is visible, you can remove all except one project.</span></span> <span data-ttu-id="9e93c-127">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、残りのプロジェクトが 1 つのみになった時点でソリューション フォルダーが表示されなくなるので、最後の 1 つのプロジェクトは削除できません。</span><span class="sxs-lookup"><span data-stu-id="9e93c-127">As soon as only one project remains, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] no longer displays the solution folder and you cannot remove the last project.</span></span>  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a><span data-ttu-id="9e93c-128">Integration Services プロジェクトをソリューションから削除するには</span><span class="sxs-lookup"><span data-stu-id="9e93c-128">To remove an Integration Services project from a solution</span></span>  
  
1.  <span data-ttu-id="9e93c-129">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを削除する対象となるソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="9e93c-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution from which you want to remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="9e93c-130">ソリューション エクスプローラーでプロジェクトを右クリックし、**[プロジェクトのアンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-130">In Solution Explorer, right-click the project, and then click **Unload Project**.</span></span>  
  
3.  <span data-ttu-id="9e93c-131">削除を確認するメッセージが表示されたら、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e93c-131">Click **OK** to confirm the removal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e93c-132">参照</span><span class="sxs-lookup"><span data-stu-id="9e93c-132">See Also</span></span>  
 <span data-ttu-id="9e93c-133">[SSIS&#41; プロジェクトの Integration Services &#40;](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="9e93c-133">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="9e93c-134">新しい Integration Services プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9e93c-134">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
