---
title: SQL Server Management Studio の使用 [SQL Server] | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Management Studio [SQL Server]
- Enterprise Manager (See SQL Server Management Studio [Analysis Services])
- SQL Server Management Studio [SQL Server], about SQL Server Management Studio
ms.assetid: f289e978-14ca-46ef-9e61-e1fe5fd593be
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fed75ae8d4a1cfba7fb890a5b0b9c159c13366f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632054"
---
# <a name="use-sql-server-management-studio"></a><span data-ttu-id="de5d9-102">SQL Server Management Studio の使用 [SQL Server]</span><span class="sxs-lookup"><span data-stu-id="de5d9-102">Use SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="de5d9-103">(SSMS) は、のすべてのコンポーネントにアクセスし、それらを構成、管理、および開発するための統合環境です [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="de5d9-103">(SSMS) is an integrated environment for accessing, configuring, managing, administering, and developing all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de5d9-104">SSMS では、さまざまなグラフィック ツールと、機能の豊富な多くのスクリプト エディターが用意されており、これらを使用して、あらゆるスキル レベルの開発者や管理者が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="de5d9-104">SSMS combines a broad group of graphical tools with a number of rich script editors to provide access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to developers and administrators of all skill levels.</span></span>  
  
 <span data-ttu-id="de5d9-105">SSMS では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の以前のリリースに含まれていた Enterprise Manager、クエリ アナライザー、分析マネージャーの機能が 1 つの環境に統合されています。</span><span class="sxs-lookup"><span data-stu-id="de5d9-105">SSMS combines the features of Enterprise Manager, Query Analyzer, and Analysis Manager, included in previous releases of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], into a single environment.</span></span> <span data-ttu-id="de5d9-106">さらに、SSMS は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のあらゆるコンポーネント ( [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]など) ともスムーズに連携できます。</span><span class="sxs-lookup"><span data-stu-id="de5d9-106">In addition, SSMS works with all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] such as [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="de5d9-107">この環境を使用して、開発者は使い慣れた操作で作業ができ、データベース管理者も、使いやすいグラフィック ツールと豊富なスクリプト機能を統合した 1 つの総合ユーティリティで作業できます。</span><span class="sxs-lookup"><span data-stu-id="de5d9-107">Developers get a familiar experience, and database administrators get a single comprehensive utility that combines easy-to-use graphical tools with rich scripting capabilities.</span></span>  
  
 <span data-ttu-id="de5d9-108">[Microsoft Developer Network](https://msdn.microsoft.com/library/dn434042.aspx)から SSMS をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="de5d9-108">Download and install SSMS from the [Microsoft Developer Network](https://msdn.microsoft.com/library/dn434042.aspx).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de5d9-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="de5d9-109">In This Section</span></span>  
 [<span data-ttu-id="de5d9-110">SQL Server Management Studio の機能</span><span class="sxs-lookup"><span data-stu-id="de5d9-110">Features in SQL Server Management Studio</span></span>](features-in-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-111">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の豊富な機能を紹介します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-111">Lists the rich feature set included in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-112">SQL Server Management Studio のツール ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="de5d9-112">Tool Windows in SQL Server Management Studio</span></span>](../ssms/tool-windows-in-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-113">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のコンポーネントである各種のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-113">Describes the tools that are components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-114">SQL Server Management Studio でのウィンドウの管理について</span><span class="sxs-lookup"><span data-stu-id="de5d9-114">Understand SQL Server Management Studio Windows Management</span></span>](../ssms/understand-sql-server-management-studio-windows-management.md)  
 <span data-ttu-id="de5d9-115">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で表示される各種のウィンドウを管理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-115">Describes how to manage the windows displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-116">SQL Server Management Studio によるサーバー管理</span><span class="sxs-lookup"><span data-stu-id="de5d9-116">Administer Servers with SQL Server Management Studio</span></span>](../ssms/administer-servers-with-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスを管理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-117">Describes how to administer instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-118">SQL Server Management Studio から SQL Server コンポーネントへの接続</span><span class="sxs-lookup"><span data-stu-id="de5d9-118">Connect to Any SQL Server Component from SQL Server Management Studio</span></span>](../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-119">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続する方法と、接続なしで特定のタスクを実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-119">Describes how to connect to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and how to perform certain tasks without a connection.</span></span>  
  
 <span data-ttu-id="de5d9-120">[[オブジェクト エクスプローラー]](../ssms/object/object-explorer.md)</span><span class="sxs-lookup"><span data-stu-id="de5d9-120">[Object Explorer](../ssms/object/object-explorer.md)</span></span>  
 <span data-ttu-id="de5d9-121">オブジェクト エクスプローラーの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-121">Describes the features of the Object Explorer.</span></span>  
  
 [<span data-ttu-id="de5d9-122">SQL Server Management Studio のユーザー サポート</span><span class="sxs-lookup"><span data-stu-id="de5d9-122">User Assistance in SQL Server Management Studio</span></span>](../ssms/user-assistance-in-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-123">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のユーザー支援機能 (ヘルプなど) を設定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-123">Describes how to configure user assistance, such as Help, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-124">クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="de5d9-124">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-125">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の機能に富んだ編集環境を使用して、 [!INCLUDE[tsql](../includes/tsql-md.md)]、MDX、DMX、XML/A の各スクリプトを編集する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-125">Describes how to use the rich editing environment in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to edit [!INCLUDE[tsql](../includes/tsql-md.md)], MDX, DMX and XML/A scripts.</span></span>  
  
 [<span data-ttu-id="de5d9-126">クエリ エディターによる SQLCMD スクリプトの編集</span><span class="sxs-lookup"><span data-stu-id="de5d9-126">Edit SQLCMD Scripts with Query Editor</span></span>](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)  
 <span data-ttu-id="de5d9-127">クエリ エディターを SQLCMD モードで使用する場合の機能と制限事項を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-127">Describes the capabilities and limitations of using Query Editor in SQLCMD mode.</span></span>  
  
 [<span data-ttu-id="de5d9-128">クエリ エディターでのコードの色分け</span><span class="sxs-lookup"><span data-stu-id="de5d9-128">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
 <span data-ttu-id="de5d9-129">コード エディターの各ウィンドウに表示されるコードの色分けの意味を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-129">Describes the meaning of the color coding in Code Editor windows.</span></span>  
  
 [<span data-ttu-id="de5d9-130">SQL Server Management Studio のキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="de5d9-130">SQL Server Management Studio Keyboard Shortcuts</span></span>](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
 <span data-ttu-id="de5d9-131">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で使用できるキーボード ショートカットを紹介します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-131">Lists the keyboard shortcuts available in the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-132">メニューとショートカット キーのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="de5d9-132">Customize Menus and Shortcut Keys</span></span>](../ssms/customize-menus-and-shortcut-keys.md)  
 <span data-ttu-id="de5d9-133">カスタム メニューやカスタム ショートカットを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-133">Describes how to create custom menus and shortcuts.</span></span>  
  
 [<span data-ttu-id="de5d9-134">ソリューション (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="de5d9-134">Solutions &#40;SQL Server Management Studio&#41;</span></span>](../ssms/solution/solutions-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-135">スクリプト プロジェクトとソリューションを開発する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-135">Describes how to develop script projects and solutions.</span></span>  
  
 [<span data-ttu-id="de5d9-136">テンプレート エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="de5d9-136">Template Explorer</span></span>](../ssms/template/template-explorer.md)  
 <span data-ttu-id="de5d9-137">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のテンプレートを使用する方法と、カスタム テンプレートを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-137">Describes how to use the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] templates and how to create custom templates.</span></span>  
  
 [<span data-ttu-id="de5d9-138">SQL Server Management Studio のプロパティ ページ</span><span class="sxs-lookup"><span data-stu-id="de5d9-138">Property Pages in SQL Server Management Studio</span></span>](../ssms/property-pages-in-sql-server-management-studio.md)  
 <span data-ttu-id="de5d9-139">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の [プロパティ] ウィンドウの新しいレイアウトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-139">Describes the new property window layout in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="de5d9-140">Visual Database Tools のデザイナー</span><span class="sxs-lookup"><span data-stu-id="de5d9-140">Visual Database Tool Designers</span></span>](../ssms/visual-db-tools/visual-database-tool-designers.md)  
 <span data-ttu-id="de5d9-141">クエリの作成、データベース構造のデザインまたは変更、データの更新などのために使用できる Visual Database Tools について説明します。</span><span class="sxs-lookup"><span data-stu-id="de5d9-141">Describes the Visual Database Tools that you can use to create queries, design or modify a database structure, or update data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5d9-142">参照</span><span class="sxs-lookup"><span data-stu-id="de5d9-142">See Also</span></span>  
 [<span data-ttu-id="de5d9-143">サーバー プロパティの表示または変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="de5d9-143">View or Change Server Properties &#40;SQL Server&#41;</span></span>](configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
