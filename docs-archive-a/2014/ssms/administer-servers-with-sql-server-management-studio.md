---
title: SQL Server Management Studio によるサーバー管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb2a6b9afba7d838cf71144f88ed7866c54ad796
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737519"
---
# <a name="administer-servers-with-sql-server-management-studio"></a><span data-ttu-id="527bf-102">SQL Server Management Studio によるサーバー管理</span><span class="sxs-lookup"><span data-stu-id="527bf-102">Administer Servers with SQL Server Management Studio</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="527bf-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理者のサーバー管理要件を満たすように設計された、充実した統合管理クライアントです。</span><span class="sxs-lookup"><span data-stu-id="527bf-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is a rich, integrated administrative client designed to meet the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] administrator's server management requirements.</span></span> <span data-ttu-id="527bf-104">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]では、オブジェクト エクスプローラーを使用して管理タスクを実行します。オブジェクト エクスプローラーでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ファミリのあらゆるサーバーに接続して、その内容をグラフィカルに表示できます。</span><span class="sxs-lookup"><span data-stu-id="527bf-104">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], administrative tasks are accomplished using Object Explorer, which allows you to connect to any server in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] family and graphically browse its contents.</span></span> <span data-ttu-id="527bf-105">対象になるサーバーは、[!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、または [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="527bf-105">A server can be an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="527bf-106">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] のツール コンポーネントとしては、登録済みサーバー、オブジェクト エクスプローラー、ソリューション エクスプローラー、テンプレート エクスプローラー、[オブジェクト エクスプローラーの詳細] ページ、ドキュメント ウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="527bf-106">The tool components of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] include Registered Servers, Object Explorer, Solution Explorer, Template Explorer, the Object Explorer Details page, and the document window.</span></span> <span data-ttu-id="527bf-107">ツールを表示するには、 **[表示]** メニューでツール名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="527bf-107">To display a tool, on the **View** menu, click the tool name.</span></span> <span data-ttu-id="527bf-108">クエリ エディター ツールを表示するには、ツール バーの **[新しいクエリ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="527bf-108">To display the Query Editor tool, click the **New Query** button on the toolbar.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="527bf-109">既定では、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の間のネットワーク通信は暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="527bf-109">Network traffic between [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is unencrypted by default.</span></span> <span data-ttu-id="527bf-110">暗号化接続を確立しない限り、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ではパスワードなどの機密データを処理しないでください。</span><span class="sxs-lookup"><span data-stu-id="527bf-110">Do not work with sensitive data (including passwords) in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] unless you have established an encrypted connection.</span></span> <span data-ttu-id="527bf-111">詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="527bf-111">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
 <span data-ttu-id="527bf-112">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] を使用して以下の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="527bf-112">Use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="527bf-113">サーバーの登録</span><span class="sxs-lookup"><span data-stu-id="527bf-113">Register servers.</span></span>  
  
-   <span data-ttu-id="527bf-114">[!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssAS](../includes/ssas-md.md)]、[!INCLUDE[ssRS](../includes/ssrs.md)]、または [!INCLUDE[ssIS](../includes/ssis-md.md)] のインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="527bf-114">Connect to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs.md)], or [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
-   <span data-ttu-id="527bf-115">サーバー プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="527bf-115">Configure server properties.</span></span>  
  
-   <span data-ttu-id="527bf-116">データベースや [!INCLUDE[ssAS](../includes/ssas-md.md)] オブジェクト (キューブ、ディメンション、アセンブリなど) の管理</span><span class="sxs-lookup"><span data-stu-id="527bf-116">Manage database and [!INCLUDE[ssAS](../includes/ssas-md.md)] objects such as cubes, dimensions, and assemblies.</span></span>  
  
-   <span data-ttu-id="527bf-117">オブジェクト (データベース、テーブル、キューブ、データベース ユーザー、ログインなど) の作成</span><span class="sxs-lookup"><span data-stu-id="527bf-117">Create objects, such as databases, tables, cubes, database users, and logins.</span></span>  
  
-   <span data-ttu-id="527bf-118">ファイルとファイル グループの管理</span><span class="sxs-lookup"><span data-stu-id="527bf-118">Manage files and filegroups.</span></span>  
  
-   <span data-ttu-id="527bf-119">データベースのインポート/デタッチ</span><span class="sxs-lookup"><span data-stu-id="527bf-119">Attach or detach databases.</span></span>  
  
-   <span data-ttu-id="527bf-120">スクリプト ツールの起動</span><span class="sxs-lookup"><span data-stu-id="527bf-120">Launch scripting tools.</span></span>  
  
-   <span data-ttu-id="527bf-121">セキュリティの管理</span><span class="sxs-lookup"><span data-stu-id="527bf-121">Manage security.</span></span>  
  
-   <span data-ttu-id="527bf-122">システム ログの表示</span><span class="sxs-lookup"><span data-stu-id="527bf-122">View system logs.</span></span>  
  
-   <span data-ttu-id="527bf-123">現在の利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="527bf-123">Monitor current activity.</span></span>  
  
-   <span data-ttu-id="527bf-124">レプリケーションの設定</span><span class="sxs-lookup"><span data-stu-id="527bf-124">Configure replication.</span></span>  
  
-   <span data-ttu-id="527bf-125">フルテキスト インデックスの管理</span><span class="sxs-lookup"><span data-stu-id="527bf-125">Manage full-text indexes.</span></span>  
  
 <span data-ttu-id="527bf-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントの開始と停止には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="527bf-126">To start and stop [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527bf-127">参照</span><span class="sxs-lookup"><span data-stu-id="527bf-127">See Also</span></span>  
 <span data-ttu-id="527bf-128">[SQL Server Management Studio を使用する](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="527bf-128">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="527bf-129">サーバー プロパティの表示または変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="527bf-129">View or Change Server Properties &#40;SQL Server&#41;</span></span>](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
