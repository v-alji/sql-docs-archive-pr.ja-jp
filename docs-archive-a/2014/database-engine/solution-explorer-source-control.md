---
title: ソリューションエクスプローラーソース管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 46471ba8149c26f80e78006bc3a8befc2e81b416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642948"
---
# <a name="solution-explorer-source-control"></a><span data-ttu-id="7b8ec-102">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="7b8ec-102">Solution Explorer Source Control</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="7b8ec-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ソリューションエクスプローラーは、別のソース管理システムに統合できます。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Solution Explorer can be integrated into a separate source control system.</span></span> <span data-ttu-id="7b8ec-104">ソリューションまたはプロジェクトをソース管理システムに統合すると、プロジェクト内のスクリプトとクエリを対象に、ファイル アクセスとバージョン管理を制御できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-104">Once a solution or project is integrated into a source control system, you can control file access and versioning for the scripts and queries in your projects.</span></span>  
  
## <a name="solution-and-project-source-control"></a><span data-ttu-id="7b8ec-105">ソリューションとプロジェクトのソース管理</span><span class="sxs-lookup"><span data-stu-id="7b8ec-105">Solution and Project Source Control</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="7b8ec-106">ソース管理とは、サーバー ソフトウェアの主要部分がファイルのバージョンを格納および追跡し、ファイルへのアクセスを制御するシステムです。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-106">Source control refers to a system in which a central piece of server software stores and tracks file versions, and also controls access to files.</span></span> <span data-ttu-id="7b8ec-107">標準的なソース管理システムは、1 つのソース管理プロバイダー、および 2 つ以上のソース管理クライアントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-107">A typical source control system includes a source control provider and two or more source control clients.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7b8ec-108">はソース管理サービスに統合することができます。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-108">can be integrated with a source control service.</span></span> <span data-ttu-id="7b8ec-109">そのため、このツールはソース管理プロバイダーに対するクライアントとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-109">This means you can use the tool as a client for your source control provider.</span></span> <span data-ttu-id="7b8ec-110">環境を離れることなく、個人およびチームのプロジェクトを簡単に管理できます。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-110">Without leaving the environment, you can manage your individual and team projects easily.</span></span> <span data-ttu-id="7b8ec-111">ソース管理プロバイダーは、[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-111">The source control provider is not included with [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
#### <a name="to-select-a-source-control-provider"></a><span data-ttu-id="7b8ec-112">ソース管理プロバイダーを選択するには</span><span class="sxs-lookup"><span data-stu-id="7b8ec-112">To select a source control provider</span></span>  
  
1.  <span data-ttu-id="7b8ec-113">ソース管理プロバイダーのクライアント部分をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-113">Install the client portion of your source control provider.</span></span>  
  
2.  <span data-ttu-id="7b8ec-114">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]で、 **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-114">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="7b8ec-115">[**オプション**] ダイアログボックスで、[**ソース管理**] を展開し、[**プラグインの選択**] ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-115">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
4.  <span data-ttu-id="7b8ec-116">[**現在のソース管理プラグイン**] ボックスで、ソース管理プラグインを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-116">In the **Current source control plug-in** box, select the source control plug-in.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b8ec-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7b8ec-117">In This Section</span></span>  
  
|<span data-ttu-id="7b8ec-118">トピック</span><span class="sxs-lookup"><span data-stu-id="7b8ec-118">Topic</span></span>|<span data-ttu-id="7b8ec-119">説明</span><span class="sxs-lookup"><span data-stu-id="7b8ec-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7b8ec-120">ソース管理の基礎</span><span class="sxs-lookup"><span data-stu-id="7b8ec-120">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)|<span data-ttu-id="7b8ec-121">ソース管理に関する基本的な用語を定義し、プロジェクトでソース管理を使用する利点について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-121">Defines basic source control terminology, and explains how your project can benefit from using source control services.</span></span>|  
|[<span data-ttu-id="7b8ec-122">ソース管理へのソリューションとプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="7b8ec-122">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|<span data-ttu-id="7b8ec-123">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境を使用して、ソース管理にソリューションおよびプロジェクトを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-123">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to add solutions and projects to source control.</span></span>|  
|[<span data-ttu-id="7b8ec-124">ソース管理からソリューションやプロジェクトを開く方法</span><span class="sxs-lookup"><span data-stu-id="7b8ec-124">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|<span data-ttu-id="7b8ec-125">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境を使用して、ソース管理の対象であるソリューションおよびプロジェクトを開く方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-125">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to open source-controlled solutions and projects.</span></span>|  
|[<span data-ttu-id="7b8ec-126">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="7b8ec-126">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)|<span data-ttu-id="7b8ec-127">ソリューションやファイルをソース管理からチェックアウトする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-127">Explains how to check out solutions and files from source control.</span></span>|  
|[<span data-ttu-id="7b8ec-128">チェックインの管理</span><span class="sxs-lookup"><span data-stu-id="7b8ec-128">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)|<span data-ttu-id="7b8ec-129">ソリューションやファイルをソース管理にチェックインする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-129">Explains how to check solutions and files into source control.</span></span>|  
|[<span data-ttu-id="7b8ec-130">バージョン情報の設定と取得</span><span class="sxs-lookup"><span data-stu-id="7b8ec-130">Set and Retrieve Version Information</span></span>](../../2014/database-engine/set-and-retrieve-version-information.md)|<span data-ttu-id="7b8ec-131">プロジェクトや項目の履歴を取得したり、項目のローカル コピーを取得したり、2 つの項目のバージョンを比較したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b8ec-131">Explains how to retrieve the history of a project or item, retrieve a local copy of an item, or compare two item versions.</span></span>|  
|||  
  
## <a name="see-also"></a><span data-ttu-id="7b8ec-132">参照</span><span class="sxs-lookup"><span data-stu-id="7b8ec-132">See Also</span></span>  
 <span data-ttu-id="7b8ec-133">[ソリューション エクスプローラー](../ssms/solution/solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="7b8ec-133">[Solution Explorer](../ssms/solution/solution-explorer.md) </span></span>  
 <span data-ttu-id="7b8ec-134">[ソリューション &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="7b8ec-134">[Solutions &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span></span>  
 <span data-ttu-id="7b8ec-135">[プロジェクト &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7b8ec-135">[Projects &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="7b8ec-136">ソリューションとプロジェクトを管理するためのファイル</span><span class="sxs-lookup"><span data-stu-id="7b8ec-136">Files That Manage Solutions and Projects</span></span>](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
