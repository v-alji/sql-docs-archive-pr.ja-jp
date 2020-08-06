---
title: 新しい Integration Services プロジェクトを作成する |Microsoft Docs
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
ms.assetid: 1e23f259-0401-4333-ab4f-89809aae63b1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f62d3ac2d33bb51a0ccc3b77d9f8b5ec0f52b345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639583"
---
# <a name="create-a-new-integration-services-project"></a><span data-ttu-id="6652a-102">新しい Integration Services プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="6652a-102">Create a New Integration Services Project</span></span>
  <span data-ttu-id="6652a-103">この手順では、新しいプロジェクトと新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="6652a-103">This procedure creates a new project and a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] solution.</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="6652a-104">新しい Integration Services プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="6652a-104">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="6652a-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="6652a-105">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="6652a-106">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6652a-106">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="6652a-107">**[新しいプロジェクト]** ダイアログ ボックスの **[テンプレート]** ペインで、**[Integration Services プロジェクト]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="6652a-107">In the **New Project** dialog box, in the **Templates** pane, select the **Integration Services Project** template.</span></span>  
  
     <span data-ttu-id="6652a-108">**[Integration Services プロジェクト]** テンプレートでは、空のパッケージを 1 つ含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6652a-108">The **Integration Services Project** template creates an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains a single, empty package.</span></span>  
  
4.  <span data-ttu-id="6652a-109">(省略可) プロジェクトの名前と場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="6652a-109">(Optional) Edit the project name and the location.</span></span>  
  
     <span data-ttu-id="6652a-110">ソリューション名は、プロジェクト名と一致するように自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="6652a-110">The solution name is automatically updated to match the project name.</span></span>  
  
5.  <span data-ttu-id="6652a-111">ソリューション ファイル用に別のフォルダーを作成するには、**[ソリューションのディレクトリを作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6652a-111">To create a separate folder for the solution file, select **Create directory for solution**.</span></span> <span data-ttu-id="6652a-112">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="6652a-112">This is the default option.</span></span>  
  
6.  <span data-ttu-id="6652a-113">ソース管理ソフトウェアがコンピューターにインストールされている場合、プロジェクトをソース管理に関連付けるには、**[ソース管理に追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6652a-113">If source control software is installed on the computer, select **Add to source control**  to associate the project with source control.</span></span>  
  
7.  <span data-ttu-id="6652a-114">ソース管理ソフトウェアが [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe の場合、**[Visual SourceSafe ログイン]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="6652a-114">If the source control software is [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, the **Visual SourceSafe Login** dialog box opens.</span></span> <span data-ttu-id="6652a-115">**[Visual SourceSafe ログイン]** ダイアログ ボックスで、ユーザー名、パスワード、および [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe データベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6652a-115">In **Visual SourceSafe Login**, provide a user name, a password, and the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database.</span></span> <span data-ttu-id="6652a-116">データベースを探すには、**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6652a-116">Click **Browse** to locate the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6652a-117">選択したソース管理プラグインを表示、変更したり、ソース管理の環境を構成するには、**[ツール]** メニューの **[オプション]** をクリックし、**[ソース管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="6652a-117">To view and change the selected source control plug-in and to configure the source control environment, click **Options** on the **Tools** menu, and then expand the **Source Control** node.</span></span>  
  
8.  <span data-ttu-id="6652a-118">[ **OK]** をクリックして**ソリューションをソリューション**に追加し、プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="6652a-118">Click **OK** to add the solution to **Solution Explore**r and add the project to the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6652a-119">参照</span><span class="sxs-lookup"><span data-stu-id="6652a-119">See Also</span></span>  
 <span data-ttu-id="6652a-120">[SSIS&#41; プロジェクトの Integration Services &#40;](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="6652a-120">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="6652a-121">ソリューション内の Integration Services プロジェクトを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="6652a-121">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
