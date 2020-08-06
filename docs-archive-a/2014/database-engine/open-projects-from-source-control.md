---
title: ソース管理からプロジェクトを開く |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 944b121516e3782e35e213e165405b0ecceb7456
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644614"
---
# <a name="open-projects-from-source-control"></a><span data-ttu-id="3dd7d-102">ソース管理からプロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="3dd7d-102">Open Projects from Source Control</span></span>
  <span data-ttu-id="3dd7d-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、ソース管理からプロジェクトを直接開くことができます。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open projects directly from source control.</span></span> <span data-ttu-id="3dd7d-104">プロジェクトを直接開く場合は、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] によって、このプロジェクトの最新のバージョンが取得され、ローカル ディスクにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-104">When you do this, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] retrieves the latest version of the project and copies it to your local disk.</span></span> <span data-ttu-id="3dd7d-105">また、[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境によって、そのプロジェクトのソリューションが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-105">The [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment also creates a solution for the project automatically.</span></span>  
  
 <span data-ttu-id="3dd7d-106">ソース管理からプロジェクトを開いた後、プロジェクト ファイルをチェックアウトして修正することができます。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-106">After you have opened a project from source control, you can check out and modify the project files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dd7d-107">次に示す手順は一度だけ実行します。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-107">The following procedure should only be used once.</span></span> <span data-ttu-id="3dd7d-108">その後は、他のプロジェクトと同様に、プロジェクトを開く必要があります ([**ファイル**]、[**開く**]、[**プロジェクト**] の順にクリック)。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-108">Thereafter, you should open the project like any other project (by clicking **File**, **Open**, and then **Project**).</span></span>  
  
### <a name="to-open-a-project-from-source-control"></a><span data-ttu-id="3dd7d-109">ソース管理からプロジェクトを開くには</span><span class="sxs-lookup"><span data-stu-id="3dd7d-109">To open a project from source control</span></span>  
  
1.  <span data-ttu-id="3dd7d-110">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**ソース管理から開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-110">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="3dd7d-111">ログオンを指示するメッセージが表示されたら、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe にログオンします。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-111">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="3dd7d-112">[ **SourceSafe からローカルプロジェクトを作成**] ダイアログボックスで、開くプロジェクトが格納されているフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-112">In the **Create local project from SourceSafe** dialog box, open the folder that contains the project to open.</span></span>  
  
4.  <span data-ttu-id="3dd7d-113">[**フォルダーに新しいプロジェクトを作成**する] ボックスが変更され、プロジェクトが作成されるローカルディレクトリが識別されます。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-113">The **Create a new project in the folder** box changes to identify the local directory in which the project will be created.</span></span> <span data-ttu-id="3dd7d-114">プロジェクトを別のディレクトリに配置する場合は、ディレクトリへのパスを入力するか、[**参照**] ボタンを使用してローカルディスク上のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-114">If you want to place the project in a different directory, type the path to the directory or use the **Browse** button to locate the directory on your local disk.</span></span>  
  
5.  <span data-ttu-id="3dd7d-115">[**フォルダーに新しいプロジェクトを作成] ボックス**に、正しいフォルダーが表示されていることを確認し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-115">In the **Create a new project in the folder box**, verify that the correct folder is displayed, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="3dd7d-116">[**ソリューションを開く**] ダイアログボックスで、開くプロジェクトを選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dd7d-116">In the **Open Solution** dialog box, select the project you want to open, and click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd7d-117">参照</span><span class="sxs-lookup"><span data-stu-id="3dd7d-117">See Also</span></span>  
 <span data-ttu-id="3dd7d-118">[ソース管理からソリューションとプロジェクトを開く](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="3dd7d-118">[Open Solutions and Projects from Source Control](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span></span>  
 [<span data-ttu-id="3dd7d-119">ソース管理からソリューションを開く</span><span class="sxs-lookup"><span data-stu-id="3dd7d-119">Open Solutions from Source Control</span></span>](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
