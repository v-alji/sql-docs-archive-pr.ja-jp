---
title: SQL Server Management Studio によるデータベース プロジェクトのビルド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ddf3f61e69623716b2987c5c4d849398e822d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630790"
---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a><span data-ttu-id="39651-102">SQL Server Management Studio によるデータベース プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="39651-102">Build Database Projects by Using SQL Server Management Studio</span></span>
  <span data-ttu-id="39651-103">データベース スクリプト プロジェクトは、データベースやデータベースの一部に関連付けられているスクリプト、接続情報、およびテンプレートを組織的にまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="39651-103">A database script project is an organized set of scripts, connection information, and templates that are all associated with a database or one part of a database.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="39651-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、スクリプト プロジェクトのコンテキスト内の [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] データベースの管理やデザインに使用できる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を提供しています。</span><span class="sxs-lookup"><span data-stu-id="39651-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for administering and designing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databases within the context of a script project.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="39651-105">には、データベースの開発、配置、管理に役立つ、デザイナー、エディター、ガイド、およびウィザードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39651-105">includes designers, editors, guides and wizards to assist users in developing, deploying and maintaining databases.</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="39651-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="39651-106">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="39651-107">は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のコンポーネントの管理に使用する管理ツールのセットです。</span><span class="sxs-lookup"><span data-stu-id="39651-107">is a suite of administrative tools for managing the components belonging to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39651-108">この統合環境を使用すると、データのバックアップやクエリの編集、共通関数の自動化など、さまざまな作業を 1 つのインターフェイスから実行できます。</span><span class="sxs-lookup"><span data-stu-id="39651-108">This integrated environment allows users to perform a variety of tasks, such as backing up data, editing queries, and automating common functions within a single interface.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="39651-109">には以下のツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39651-109">includes the following tools:</span></span>  
  
-   <span data-ttu-id="39651-110">コード エディター。豊富な機能を持つスクリプト エディターで、スクリプトの作成や編集に使用します。</span><span class="sxs-lookup"><span data-stu-id="39651-110">Code Editor is a rich script editor for writing and editing scripts.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="39651-111">のコード エディターには、 [!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディター ( [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプト用)、DMX クエリ エディター、MDX クエリ エディター、および XML/A クエリ エディターの 4 種類のバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="39651-111">provides four versions of the Code Editor; the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor for [!INCLUDE[tsql](../includes/tsql-md.md)] scripts, the DMX Query Editor, the MDX Query Editor, and the XML/A Query Editor.</span></span>  
  
-   <span data-ttu-id="39651-112">オブジェクト エクスプローラー。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに所属するオブジェクトの検索、変更、スクリプト作成、実行に使用します。</span><span class="sxs-lookup"><span data-stu-id="39651-112">Object Explorer for locating, modifying, scripting or running objects belonging to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="39651-113">テンプレート エクスプローラー。テンプレートの検索およびスクリプト作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="39651-113">Template Explorer for locating and scripting templates.</span></span>  
  
-   <span data-ttu-id="39651-114">ソリューション エクスプローラー。プロジェクトに含まれる関連スクリプトの編成および格納に使用します。</span><span class="sxs-lookup"><span data-stu-id="39651-114">Solution Explorer for organizing and storing related scripts as parts of a project.</span></span>  
  
-   <span data-ttu-id="39651-115">プロパティ ウィンドウ。選択したオブジェクトの現在のプロパティの表示に使用します。</span><span class="sxs-lookup"><span data-stu-id="39651-115">Properties Window for displaying the current properties of selected objects.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="39651-116">は、以下の機能を提供して効率的な作業プロセスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="39651-116">supports efficient work processes by providing:</span></span>  
  
-   <span data-ttu-id="39651-117">非接続アクセス。</span><span class="sxs-lookup"><span data-stu-id="39651-117">Disconnected access.</span></span> <span data-ttu-id="39651-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに接続しないで、スクリプトを作成および編集できます。</span><span class="sxs-lookup"><span data-stu-id="39651-118">You can write and edit scripts without connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="39651-119">すべてのダイアログ ボックスからのスクリプト作成。</span><span class="sxs-lookup"><span data-stu-id="39651-119">Scripting from any dialog box.</span></span> <span data-ttu-id="39651-120">どのダイアログ ボックスからでもスクリプトを作成できるので、スクリプト作成後に、これを読み取り、編集、格納、再利用できます。</span><span class="sxs-lookup"><span data-stu-id="39651-120">You can create a script from any dialog box so that you can read, modify, store and reuse the scripts after you create them.</span></span>  
  
-   <span data-ttu-id="39651-121">非モーダル ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="39651-121">Nonmodal dialog boxes.</span></span> <span data-ttu-id="39651-122">UI ダイアログ ボックスにアクセスしたときに、そのダイアログ ボックスを閉じなくても、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の他のリソースを参照できます。</span><span class="sxs-lookup"><span data-stu-id="39651-122">When you access a UI dialog box you can browse other resources in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] without closing the dialog box.</span></span>  
  
## <a name="solutions-and-script-projects"></a><span data-ttu-id="39651-123">ソリューションおよびスクリプト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="39651-123">Solutions and Script Projects</span></span>  
 <span data-ttu-id="39651-124">ソリューション エクスプローラーは、データベース ソリューションを保存したり、再度開くためのユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="39651-124">Solution Explorer is a utility to store and reopen database solutions.</span></span> <span data-ttu-id="39651-125">ソリューションは、関連するスクリプト プロジェクトとファイルを編成したものです。</span><span class="sxs-lookup"><span data-stu-id="39651-125">Solutions organize related script projects and files.</span></span> <span data-ttu-id="39651-126">スクリプト プロジェクトには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スクリプト ファイル、SQL テンプレート、接続情報、およびその他のファイルが格納されています。</span><span class="sxs-lookup"><span data-stu-id="39651-126">Script projects store [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] script files, SQL templates, connection information and other miscellaneous files.</span></span> <span data-ttu-id="39651-127">スクリプトをスクリプト プロジェクト内に保存すると、次の操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="39651-127">When a script is saved in a script project, users are able to:</span></span>  
  
-   <span data-ttu-id="39651-128">スクリプトのバージョン管理。</span><span class="sxs-lookup"><span data-stu-id="39651-128">Maintain version control on scripts.</span></span>  
  
-   <span data-ttu-id="39651-129">スクリプトを使用した結果オプションの保存。</span><span class="sxs-lookup"><span data-stu-id="39651-129">Store results options with a script.</span></span>  
  
-   <span data-ttu-id="39651-130">関連するスクリプトを 1 つのスクリプト プロジェクトに編成。</span><span class="sxs-lookup"><span data-stu-id="39651-130">Organize related scripts in a single script project.</span></span>  
  
-   <span data-ttu-id="39651-131">スクリプトを使用した接続情報の保存。</span><span class="sxs-lookup"><span data-stu-id="39651-131">Save connection information with scripts.</span></span>  
  
 <span data-ttu-id="39651-132">ソリューション エクスプローラーは、同じプロジェクトに関連するスクリプトの作成および再利用を支援するツールです。</span><span class="sxs-lookup"><span data-stu-id="39651-132">Solution Explorer is a tool for developers who are creating and reusing scripts that are related to the same project.</span></span> <span data-ttu-id="39651-133">同じような作業が後で必要になった場合、プロジェクトに保存されている一連のスクリプトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="39651-133">If a similar task is required later, you can use group of scripts that were stored in a project.</span></span> <span data-ttu-id="39651-134">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を使用してアプリケーションを作成したことがあるユーザーにとって、ソリューション エクスプローラーはとてもなじみやすいものです。</span><span class="sxs-lookup"><span data-stu-id="39651-134">If you have created applications by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], you will find Solution Explorer very familiar.</span></span>  
  
 <span data-ttu-id="39651-135">ソリューションは、1 つ以上のスクリプト プロジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="39651-135">A solution consists of one or more script projects.</span></span> <span data-ttu-id="39651-136">プロジェクトは、1 つ以上のスクリプトまたは接続で構成されています。</span><span class="sxs-lookup"><span data-stu-id="39651-136">A project consists of one or more scripts or connections.</span></span> <span data-ttu-id="39651-137">プロジェクトには、スクリプト以外のファイルも含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="39651-137">A project may also include nonscript files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39651-138">参照</span><span class="sxs-lookup"><span data-stu-id="39651-138">See Also</span></span>  
 <span data-ttu-id="39651-139">[SQL Server Management Studio を使用する](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="39651-139">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="39651-140">[クエリエディターとテキストエディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="39651-140">[Query and Text Editors &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="39651-141">ソリューション (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="39651-141">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solution/solutions-sql-server-management-studio.md)  
  
  
