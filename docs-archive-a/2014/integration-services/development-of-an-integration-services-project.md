---
title: Integration Services のプロジェクトの開発 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 6e90b016-36a5-415e-9440-a20199fffff0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da648b3b09b25fa2a7b1cf886ad1bf770296f5ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644568"
---
# <a name="development-of-an-integration-services-project"></a><span data-ttu-id="74311-102">Integration Services プロジェクトの開発</span><span class="sxs-lookup"><span data-stu-id="74311-102">Development of an Integration Services Project</span></span>
  <span data-ttu-id="74311-103">プロジェクトに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="74311-103">You add [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to projects.</span></span> <span data-ttu-id="74311-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成して作業するには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 環境をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="74311-104">To create and work with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, you must install the [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] environment.</span></span> <span data-ttu-id="74311-105">詳細については、「 [Integration Services のインストール](install-windows/install-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74311-105">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
 <span data-ttu-id="74311-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で新しい [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]プロジェクトを作成する場合は、 **[新しいプロジェクト]** ダイアログ ボックスに **[Integration Services プロジェクト]** テンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74311-106">When you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the **New Project** dialog box includes an **Integration Services Project** template.</span></span> <span data-ttu-id="74311-107">このプロジェクト テンプレートでは、パッケージを 1 つ含む新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="74311-107">This project template creates a new project that contains a single package.</span></span>  
  
## <a name="projects-and-solutions"></a><span data-ttu-id="74311-108">プロジェクトおよびソリューション</span><span class="sxs-lookup"><span data-stu-id="74311-108">Projects and Solutions</span></span>  
 <span data-ttu-id="74311-109">プロジェクトはソリューション内に保存されます。</span><span class="sxs-lookup"><span data-stu-id="74311-109">Projects are stored in solutions.</span></span> <span data-ttu-id="74311-110">最初にソリューションを作成し、次に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトをそのソリューションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="74311-110">You can create a solution first and then add an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the solution.</span></span> <span data-ttu-id="74311-111">既存のソリューションがない場合、最初にプロジェクトを作成したときに [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] は自動的にソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="74311-111">If no solution exists, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates one for you when you first create the project.</span></span> <span data-ttu-id="74311-112">1 つのソリューションにさまざまな種類の複数のプロジェクトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="74311-112">A solution can contain multiple projects of different types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74311-113">既定では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で新しい [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]プロジェクトを作成すると、そのソリューションは **ソリューション エクスプローラー** ペインに表示されません。</span><span class="sxs-lookup"><span data-stu-id="74311-113">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the solution is not shown in the **Solution Explorer** pane.</span></span> <span data-ttu-id="74311-114">既定の動作を変更するには、 **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74311-114">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="74311-115">**[オプション]** ダイアログ ボックスで、 **[プロジェクトおよびソリューション]** を展開し、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74311-115">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="74311-116">**[全般]** ページで、 **[常にソリューションを表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="74311-116">On the **General** page, select **Always show solution**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="74311-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="74311-117">Related Tasks</span></span>  
  
-   [<span data-ttu-id="74311-118">新しい Integration Services プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="74311-118">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="74311-119">Integration Services プロジェクトにアイテムを追加する</span><span class="sxs-lookup"><span data-stu-id="74311-119">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
-   [<span data-ttu-id="74311-120">ソリューション内の Integration Services プロジェクトを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="74311-120">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
