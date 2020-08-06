---
title: ソリューションとプロジェクトを管理するためのファイル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c94f1f853263c3969961de91ec95b921f5d78ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715929"
---
# <a name="files-that-manage-solutions-and-projects"></a><span data-ttu-id="a88e9-102">ソリューションとプロジェクトを管理するためのファイル</span><span class="sxs-lookup"><span data-stu-id="a88e9-102">Files That Manage Solutions and Projects</span></span>
  <span data-ttu-id="a88e9-103">このトピックでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 固有のファイルの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="a88e9-103">This topic describes the file types that are specific to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a88e9-104">既定では、すべてのソリューションとプロジェクトが \My Documents\SQL Server Management Studio\Projects に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a88e9-104">By default, all solutions and their projects are created in \My Documents\SQL Server Management Studio Projects.</span></span>  
  
## <a name="management-studio-solution-files"></a><span data-ttu-id="a88e9-105">Management Studio のソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="a88e9-105">Management Studio Solution Files</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a88e9-106">では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio とは異なるファイルの種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a88e9-106">uses different file types than [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="a88e9-107">そのため、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のソリューションを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] や Visual Studio で開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="a88e9-107">This means you cannot open a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in Visual Studio.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a88e9-108">のソリューション ファイルの場合、ソリューション エクスプローラーを使用して、ファイルを管理するためのグラフィカル インターフェイスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a88e9-108">solution files allow Solution Explorer to display a graphical interface for managing your files.</span></span>  
  
|<span data-ttu-id="a88e9-109">拡張機能</span><span class="sxs-lookup"><span data-stu-id="a88e9-109">Extension</span></span>|<span data-ttu-id="a88e9-110">ファイルの種類</span><span class="sxs-lookup"><span data-stu-id="a88e9-110">File type</span></span>|<span data-ttu-id="a88e9-111">説明</span><span class="sxs-lookup"><span data-stu-id="a88e9-111">Description</span></span>|<span data-ttu-id="a88e9-112">作成者</span><span class="sxs-lookup"><span data-stu-id="a88e9-112">Created by</span></span>|  
|---------------|---------------|-----------------|----------------|  
|<span data-ttu-id="a88e9-113">.ssmssln</span><span class="sxs-lookup"><span data-stu-id="a88e9-113">.ssmssln</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a88e9-114">ソリューション オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a88e9-114">Solution Object</span></span>|<span data-ttu-id="a88e9-115">環境に対して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロジェクト、プロジェクト項目、およびソリューションのディスク上の場所に対する参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="a88e9-115">Provides the environment with references to the location on disk of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] projects, project items, and solution</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a><span data-ttu-id="a88e9-116">Management Studio のプロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="a88e9-116">Management Studio Project Files</span></span>  
 <span data-ttu-id="a88e9-117">ソリューションにソリューション ファイル (つまり、ソリューション内のオブジェクトを管理するためのファイル) があるのと同じように、プロジェクトにはプロジェクト ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="a88e9-117">In the same way that solutions contain solution files that manage objects in a solution, projects contain project files.</span></span> <span data-ttu-id="a88e9-118">プロジェクトのために [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] によって作成されるプロジェクト ファイルの種類は、プロジェクトの作成に使用するテンプレートによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a88e9-118">The type of project file that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates for a project depends on the template used to create the project.</span></span> <span data-ttu-id="a88e9-119">次の表に、各プロジェクトで作成されるファイルの種類をまとめます。</span><span class="sxs-lookup"><span data-stu-id="a88e9-119">The following table describes the type of file created for each project.</span></span>  
  
|<span data-ttu-id="a88e9-120">拡張機能</span><span class="sxs-lookup"><span data-stu-id="a88e9-120">Extension</span></span>|<span data-ttu-id="a88e9-121">プロジェクト テンプレート</span><span class="sxs-lookup"><span data-stu-id="a88e9-121">Project template</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="a88e9-122">.ssmssqlproj</span><span class="sxs-lookup"><span data-stu-id="a88e9-122">.ssmssqlproj</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a88e9-123">スクリプト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="a88e9-123">Scripts Project</span></span>|  
|<span data-ttu-id="a88e9-124">.ssmsasproj</span><span class="sxs-lookup"><span data-stu-id="a88e9-124">.ssmsasproj</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a88e9-125">スクリプト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="a88e9-125">Scripts Project</span></span>|  
  
## <a name="location-of-solution-level-files"></a><span data-ttu-id="a88e9-126">ソリューション レベルのファイルの場所</span><span class="sxs-lookup"><span data-stu-id="a88e9-126">Location of Solution-Level Files</span></span>  
 <span data-ttu-id="a88e9-127">既定では、ソリューション レベルのファイルは、そのソリューションで作成された最初のプロジェクトの物理ディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="a88e9-127">By default, solution-level files are created in the physical directory of the first project that is created with the solution.</span></span> <span data-ttu-id="a88e9-128">ソリューションを作成することによってソリューションのディレクトリを指定することも、新しいプロジェクトを作成するときにディレクトリを指定することも可能です。</span><span class="sxs-lookup"><span data-stu-id="a88e9-128">You can specify a directory for the solution by creating a solution, or you can specify the directory when you create a new project.</span></span>  
  
 <span data-ttu-id="a88e9-129">ソリューション エクスプローラーに表示される論理構造とよく似たディレクトリ構造があれば、プロジェクト ファイルとソリューション ファイルを見つけることや、チーム内の他の開発者と共有することが容易になります。</span><span class="sxs-lookup"><span data-stu-id="a88e9-129">If you have a directory structure similar to the logical structure shown in Solution Explorer, project and solution files are easier to locate and share with other developers on a team.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88e9-130">参照</span><span class="sxs-lookup"><span data-stu-id="a88e9-130">See Also</span></span>  
 <span data-ttu-id="a88e9-131">[エンコードを使用したファイルの管理](manage-files-with-encoding.md) </span><span class="sxs-lookup"><span data-stu-id="a88e9-131">[Manage Files with Encoding](manage-files-with-encoding.md) </span></span>  
 <span data-ttu-id="a88e9-132">[その他のファイル](miscellaneous-files.md) </span><span class="sxs-lookup"><span data-stu-id="a88e9-132">[Miscellaneous Files](miscellaneous-files.md) </span></span>  
 <span data-ttu-id="a88e9-133">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="a88e9-133">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="a88e9-134">[ソリューション &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a88e9-134">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="a88e9-135">[プロジェクト &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a88e9-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="a88e9-136">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="a88e9-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
