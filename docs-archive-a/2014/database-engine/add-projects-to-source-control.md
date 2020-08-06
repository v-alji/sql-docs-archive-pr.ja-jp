---
title: ソース管理にプロジェクトを追加する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0afef4ef91e4d80db7e956d03a95a2ecffe1dc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633301"
---
# <a name="add-projects-to-source-control"></a><span data-ttu-id="7daa7-102">ソース管理へのプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="7daa7-102">Add Projects to Source Control</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7daa7-103">ソリューションには、複数のスクリプト プロジェクトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-103">solutions can host multiple script projects.</span></span> <span data-ttu-id="7daa7-104">ソース管理にプロジェクトを追加する方法は、そのプロジェクトが属しているソリューションがソース管理の下にあるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="7daa7-104">How you add a project to source control depends upon whether the solution to which the project belongs is under source control.</span></span> <span data-ttu-id="7daa7-105">ソリューションがソース管理の対象である場合は、ソリューションをチェックインすると、ソース管理にプロジェクトが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-105">If the solution is under source control, checking in the solution automatically adds the project to source control.</span></span> <span data-ttu-id="7daa7-106">ソリューションをチェックインする方法の詳細については、「[ファイルをチェックイン](../../2014/database-engine/check-in-files.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7daa7-106">For more information about checking in solutions, see [Check In Files](../../2014/database-engine/check-in-files.md).</span></span>  
  
 <span data-ttu-id="7daa7-107">対象のプロジェクトが属しているソリューションがソース管理の対象でない場合は、ソリューションをソース管理に追加すると、ソリューションのプロジェクトが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-107">If the solution that this project belongs to is not under source control, you can add that solution to source control, which then automatically adds the solution's projects.</span></span> <span data-ttu-id="7daa7-108">ソース管理にソリューションを追加する方法の詳細については、「[ソース管理へのソリューションの追加](../../2014/database-engine/add-solutions-to-source-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7daa7-108">For more information about adding solutions to source control, see [Add Solutions to Source Control](../../2014/database-engine/add-solutions-to-source-control.md).</span></span>  
  
 <span data-ttu-id="7daa7-109">ソース管理にソリューションを追加しない場合は、[**ソース管理に選択項目を追加**] コマンドを使用して、プロジェクトを手動で追加できます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-109">If you do not want to add the solution to source control, you can use the **Add Selection to Source Control** command to add the project manually.</span></span>  
  
 <span data-ttu-id="7daa7-110">データベース オブジェクトはソース管理プロバイダーによって直接保護されませんが、データベース オブジェクトのスクリプトを作成し、そのスクリプトをソース管理の下で保存することができます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-110">Database objects are not directly protected by the source control provider, but you can create scripts of database objects and save the scripts under source control.</span></span>  
  
### <a name="to-add-a-project-to-source-control"></a><span data-ttu-id="7daa7-111">ソース管理にプロジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="7daa7-111">To add a project to source control</span></span>  
  
1.  <span data-ttu-id="7daa7-112">ソリューション エクスプローラーで、プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7daa7-112">In Solution Explorer, select a project.</span></span>  
  
2.  <span data-ttu-id="7daa7-113">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**選択したプロジェクトをソース管理に追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7daa7-113">On the **File** menu, point to **Source Control**, and then click **Add Selected Projects to Source Control**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7daa7-114">[**選択したプロジェクトをソース管理に追加**] コマンドを使用して、ソース管理されたソリューションに属するプロジェクトを追加する場合、ソース管理ソリューションのサブフォルダーとしてプロジェクトを追加するか、プロジェクトを別のフォルダーとして追加するかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-114">If you use the **Add Selected Projects to Source Control** command to add a project that belongs to a source-controlled solution, you are prompted whether you want to add the project as a subfolder of the source-controlled solution or to add the project as a separate folder.</span></span>  
  
3.  <span data-ttu-id="7daa7-115">ログオンを指示するメッセージが表示されたら、ソース管理プロバイダーにログオンします。</span><span class="sxs-lookup"><span data-stu-id="7daa7-115">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="7daa7-116">[ **Visual SourceSafe に追加**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-116">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="7daa7-117">プロジェクトの名前が [**プロジェクト**] ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-117">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="7daa7-118">[**フォルダー** ] ボックスの一覧で、プロジェクトを配置するフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-118">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="7daa7-119">または、[**作成**] をクリックして、[**プロジェクト**] ボックスに表示された名前のフォルダーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7daa7-119">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7daa7-120">参照</span><span class="sxs-lookup"><span data-stu-id="7daa7-120">See Also</span></span>  
 [<span data-ttu-id="7daa7-121">ソース管理へのソリューションとプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="7daa7-121">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
