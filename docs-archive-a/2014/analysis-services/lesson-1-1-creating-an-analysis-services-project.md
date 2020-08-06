---
title: Analysis Services プロジェクトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 065fdc60-1791-4e27-9ed5-51d751b3f8c4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50640dd7821943dfc3914326f7e8cba32253d307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631312"
---
# <a name="creating-an-analysis-services-project"></a><span data-ttu-id="c59a0-102">Analysis Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c59a0-102">Creating an Analysis Services Project</span></span>
  <span data-ttu-id="c59a0-103">次のタスクでは、を使用して [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] `Analysis Services Tutorial` 、プロジェクトテンプレートに基づいてという名前の新しいプロジェクトを作成し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c59a0-103">In the following task, you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project named `Analysis Services Tutorial`, based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Project template.</span></span> <span data-ttu-id="c59a0-104">*プロジェクト* とは、関連するオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="c59a0-104">A *project* is a collection of related objects.</span></span> <span data-ttu-id="c59a0-105">プロジェクトはソリューションに追加され、各ソリューションは 1 つ以上のプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c59a0-105">Projects exist within a solution, which includes one or more projects.</span></span> <span data-ttu-id="c59a0-106">詳しくは、「 [Analysis Services プロジェクトの作成 (SSDT)](multidimensional-models/create-an-analysis-services-project-ssdt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c59a0-106">For more information, see [Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project"></a><span data-ttu-id="c59a0-107">Analysis Services プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="c59a0-107">To create a new Analysis Services project</span></span>  
  
1.  <span data-ttu-id="c59a0-108">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server 2012]** の順にポイントし、 **[SQL Server データ ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c59a0-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2012**, and then click **SQL Server Data Tools**.</span></span>  
  
     <span data-ttu-id="c59a0-109">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 開発環境が開きます。</span><span class="sxs-lookup"><span data-stu-id="c59a0-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment opens.</span></span>  
  
2.  <span data-ttu-id="c59a0-110">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]のスタート ページで、 **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c59a0-110">On the Start page of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New Project**.</span></span>  
  
3.  <span data-ttu-id="c59a0-111">**[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** ペインで **[ビジネス インテリジェンス]** を展開し、 **[Analysis Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c59a0-111">In the **New Project** dialog box, in the **Installed Templates** pane, expand **Business Intelligence**, and then select **Analysis Services**.</span></span> <span data-ttu-id="c59a0-112">**[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c59a0-112">Choose the **Analysis Services Multidimensional and Data Mining Project** template.</span></span>  
  
     <span data-ttu-id="c59a0-113">ダイアログ ボックスの下部に、既定のプロジェクト名、場所、および既定のソリューション名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c59a0-113">Notice the default project name, location, and the default solution name are generated in the bottom of the dialog box.</span></span> <span data-ttu-id="c59a0-114">既定では、このソリューション用に新しいディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c59a0-114">By default, a new directory is created for the solution.</span></span>  
  
4.  <span data-ttu-id="c59a0-115">プロジェクト名をに変更し `Analysis Services Tutorial` 、[**ソリューション名**] ボックスも変更します。次に、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c59a0-115">Change the project Name to `Analysis Services Tutorial`, which also changes the **Solution name** box, and then click **OK**.</span></span>  
  
 <span data-ttu-id="c59a0-116">これで、 `Analysis Services Tutorial` **Analysis Services 多次元およびデータマイニングプロジェクト**テンプレートに基づいて、という名前の新しいソリューション内にプロジェクトが作成されました `Analysis Services Tutorial` 。</span><span class="sxs-lookup"><span data-stu-id="c59a0-116">You have successfully created the `Analysis Services Tutorial` project, based on the **Analysis Services Multidimensional and Data Mining Project** template, within a new solution that is also named `Analysis Services Tutorial`.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c59a0-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="c59a0-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c59a0-118">データ ソースの定義</span><span class="sxs-lookup"><span data-stu-id="c59a0-118">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="c59a0-119">参照</span><span class="sxs-lookup"><span data-stu-id="c59a0-119">See Also</span></span>  
 <span data-ttu-id="c59a0-120">[SQL Server Data Tools &#40;SSDT&#41;を使用した多次元モデルの作成](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="c59a0-120">[Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;](multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span></span>  
 [<span data-ttu-id="c59a0-121">Analysis Services プロジェクトの作成 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="c59a0-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
