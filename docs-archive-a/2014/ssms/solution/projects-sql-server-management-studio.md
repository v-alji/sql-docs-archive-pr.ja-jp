---
title: プロジェクト (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fed02e84b154a86788b350812ad8fd5137c14b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644782"
---
# <a name="projects-sql-server-management-studio"></a><span data-ttu-id="66391-102">プロジェクト (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="66391-102">Projects (SQL Server Management Studio)</span></span>
  <span data-ttu-id="66391-103">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のプロジェクトは、論理的に関連したスクリプトやファイルの集合体であり、データベースの管理と開発のためにスクリプトやファイルをまとめて保存できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="66391-103">A [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] project is a collection of logically related scripts and files that can be saved together for database administration and development.</span></span>  
  
## <a name="script-project-overview"></a><span data-ttu-id="66391-104">スクリプト プロジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="66391-104">Script Project Overview</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66391-105">スクリプト プロジェクトは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のコンポーネントであるソリューション エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="66391-105">script projects are displayed in the Solution Explorer component of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="66391-106">1 つのスクリプト プロジェクトにはゼロ個以上のプロジェクト ファイルを組み込めます。</span><span class="sxs-lookup"><span data-stu-id="66391-106">A script project can contain zero or more project files.</span></span> <span data-ttu-id="66391-107">1 つのソリューションに 1 つのプロジェクトを追加することも、複数のプロジェクトをまとめて組み込むことも可能です。</span><span class="sxs-lookup"><span data-stu-id="66391-107">You can add a project to a solution or combine more than one project within a solution.</span></span>  
  
 <span data-ttu-id="66391-108">プロジェクトには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="66391-108">Projects can include the following:</span></span>  
  
-   <span data-ttu-id="66391-109">**接続**。</span><span class="sxs-lookup"><span data-stu-id="66391-109">**Connections**.</span></span> <span data-ttu-id="66391-110">プロジェクト内に保存される接続には、ログイン情報、サーバー名、既定のデータベース、優先プロトコル、認証の種類、接続プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="66391-110">A connection, as persisted within a project, will contain login information, server name, default database, preferred protocol, authentication type, and connection properties.</span></span> <span data-ttu-id="66391-111">接続情報をスクリプトと一緒に格納することも可能です (以下の説明を参照)。</span><span class="sxs-lookup"><span data-stu-id="66391-111">Connection information may optionally be stored with a script (see below).</span></span>  
  
-   <span data-ttu-id="66391-112">**SQL スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="66391-112">**SQLScripts**.</span></span> <span data-ttu-id="66391-113">ユーザーが頻繁に使用する SQL スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="66391-113">Frequently used SQL scripts for the user.</span></span> <span data-ttu-id="66391-114">プロジェクト内の .sql ファイルをダブルクリックすると、そのスクリプトが SQL エディターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="66391-114">Double-clicking a .sql file within the project will cause the SQL Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="66391-115">**MDX、DMX、および XMLA スクリプト**。</span><span class="sxs-lookup"><span data-stu-id="66391-115">**MDX, DMX, and XMLAScripts**.</span></span> <span data-ttu-id="66391-116">ユーザーが頻繁に使用する MDX スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="66391-116">Frequently used MDX scripts for the user.</span></span> <span data-ttu-id="66391-117">プロジェクト内の .mdx ファイルをダブルクリックすると、そのスクリプトが SQL エディターに表示されます。</span><span class="sxs-lookup"><span data-stu-id="66391-117">Double-clicking an .mdx file within the project will cause the Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="66391-118">**その他**。このフォルダーには、他の既定の種類のノードのどれにも適さないファイル (プロジェクトの目的を記述したテキスト ファイルなど) を込むことができます。</span><span class="sxs-lookup"><span data-stu-id="66391-118">**Misc**. This folder can be used for files that do not neatly fit into any of the other default node types, such as a text file that contains the project objectives.</span></span>  
  
 <span data-ttu-id="66391-119">プロジェクトをソース コード管理システムに統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="66391-119">Projects can also be integrated into a source code control system.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a><span data-ttu-id="66391-120">スクリプト プロジェクトから SQL Server インスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="66391-120">Connecting to an Instance of SQL Server from a Script Project</span></span>  
 <span data-ttu-id="66391-121">スクリプト プロジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続を組み込めます。</span><span class="sxs-lookup"><span data-stu-id="66391-121">A script project may contain connections to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="66391-122">その接続をクリックすることで、プロジェクト内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="66391-122">You can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a project by clicking the connection.</span></span> <span data-ttu-id="66391-123">接続できた時点で、その選択した接続に定義されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続している SQL スクリプト ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="66391-123">This will open an SQL Script window that is connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defined in the connection you selected.</span></span> <span data-ttu-id="66391-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する接続で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または MDX のスクリプトを開いた場合、エディターが開き、スクリプトが読み込まれてから、 **[SQL Server への接続]** ダイアログ ボックスでパスワードを入力するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="66391-124">If you open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or MDX script with a connection that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, you will be prompted for the password using the **Connect to SQL Server** dialog box after the Editor has been opened and the script loaded.</span></span>  
  
 <span data-ttu-id="66391-125">ウィンドウを閉じると、それに対応する接続も終了します。</span><span class="sxs-lookup"><span data-stu-id="66391-125">The connection will be closed after the corresponding window is closed.</span></span>  
  
 <span data-ttu-id="66391-126">接続情報の修正には、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の [プロパティ] ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="66391-126">To modify information about a connection, use the properties window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="project-tasks"></a><span data-ttu-id="66391-127">プロジェクト タスク</span><span class="sxs-lookup"><span data-stu-id="66391-127">Project Tasks</span></span>  
  
|<span data-ttu-id="66391-128">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="66391-128">Task Description</span></span>|<span data-ttu-id="66391-129">トピック</span><span class="sxs-lookup"><span data-stu-id="66391-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="66391-130">ソリューションに新しいプロジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-130">Describes how to create a new project in a solution.</span></span>|[<span data-ttu-id="66391-131">プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="66391-131">Create a Project</span></span>](create-a-project.md)|  
|<span data-ttu-id="66391-132">既存のプロジェクトをソリューションに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-132">Describes how to add an existing project to a solution.</span></span>|[<span data-ttu-id="66391-133">ソリューションへの既存のプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="66391-133">Add an Existing Project to a Solution</span></span>](add-an-existing-project-to-a-solution.md)|  
|<span data-ttu-id="66391-134">プロジェクト ファイルが保存される既定の場所を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-134">Describes how to change the default location at which project files are saved.</span></span>|[<span data-ttu-id="66391-135">プロジェクトの既定の場所の変更</span><span class="sxs-lookup"><span data-stu-id="66391-135">Change the Default Location for Projects</span></span>](change-the-default-location-for-projects.md)|  
|<span data-ttu-id="66391-136">プロジェクトの現在のプロパティを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-136">Describes how to view the current properties for a project.</span></span>|[<span data-ttu-id="66391-137">プロジェクトのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="66391-137">View Project Properties</span></span>](view-project-properties.md)|  
|<span data-ttu-id="66391-138">接続やスクリプト ファイルなどの新しい項目をプロジェクトに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-138">Describes how to add new items, such as connections or script files, to a project.</span></span>|[<span data-ttu-id="66391-139">プロジェクトへの新規項目の追加</span><span class="sxs-lookup"><span data-stu-id="66391-139">Add New Items to a Project</span></span>](add-new-items-to-a-project.md)|  
|<span data-ttu-id="66391-140">クエリの接続情報を確立する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-140">Describes how to establish the connection information for a query.</span></span>|[<span data-ttu-id="66391-141">クエリとプロジェクト内の接続との関連付け</span><span class="sxs-lookup"><span data-stu-id="66391-141">Associate a Query with a Connection in a Project</span></span>](associate-a-query-with-a-connection-in-a-project.md)|  
|<span data-ttu-id="66391-142">クエリの接続情報を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-142">Describes how to change the connection information for a query.</span></span>|[<span data-ttu-id="66391-143">クエリに関連付けられた接続の変更</span><span class="sxs-lookup"><span data-stu-id="66391-143">Change the Connection Associated with a Query</span></span>](change-the-connection-associated-with-a-query.md)|  
|<span data-ttu-id="66391-144">接続プロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66391-144">Describes how to change connection properties.</span></span>|[<span data-ttu-id="66391-145">プロジェクト内の接続のプロパティを表示または変更する方法</span><span class="sxs-lookup"><span data-stu-id="66391-145">View or Change the Properties of a Connection in a Project</span></span>](view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a><span data-ttu-id="66391-146">参照</span><span class="sxs-lookup"><span data-stu-id="66391-146">See Also</span></span>  
 <span data-ttu-id="66391-147">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="66391-147">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="66391-148">[ソリューション &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="66391-148">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="66391-149">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="66391-149">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
