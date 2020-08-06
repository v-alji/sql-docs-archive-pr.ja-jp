---
title: セキュリティ構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- reducing attackable surface area
- upgrading SQL Server, security
- surface area configuration [SQL Server]
- surface area configuration [SQL Server], about surface area configuration
- attackable surface area [SQL Server]
- installing SQL Server, security
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ef64fbbeb2b8953ff3816db63572b499d42f012e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713981"
---
# <a name="surface-area-configuration"></a><span data-ttu-id="d58bb-102">セキュリティ構成</span><span class="sxs-lookup"><span data-stu-id="d58bb-102">Surface Area Configuration</span></span>
  <span data-ttu-id="d58bb-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新規インストール時の既定の構成では、多くの機能が有効化されていません。</span><span class="sxs-lookup"><span data-stu-id="d58bb-103">In the default configuration of new installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], many features are not enabled.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d58bb-104">悪意あるユーザーの攻撃を受ける可能性がある機能を最小限にするために、主要なサービスおよび機能のみが選択的にインストールされ、起動されます。</span><span class="sxs-lookup"><span data-stu-id="d58bb-104">selectively installs and starts only key services and features, to minimize the number of features that can be attacked by a malicious user.</span></span> <span data-ttu-id="d58bb-105">システム管理者はインストール時のこれらの既定を変更することができ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス実行機能の有効化と無効化を選択的に行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="d58bb-105">A system administrator can change these defaults at installation time and also selectively enable or disable features of a running instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d58bb-106">また、別のコンピューターから接続する場合、一部のコンポーネントはプロトコルが構成されるまで使用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d58bb-106">Additionally, some components may not be available when connecting from other computers until protocols are configured.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d58bb-107">アップグレードを行う際には、新規インストールとは異なり、既存のサービスや機能を停止しないようにします。ただし、追加のセキュリティ構成オプションは、アップグレードが完了してから適用することができます。</span><span class="sxs-lookup"><span data-stu-id="d58bb-107">Unlike new installations, no existing services or features are turned off during an upgrade, but additional surface area configuration options can be applied after the upgrade is completed.</span></span>  
  
## <a name="protocols-connection-and-startup-options"></a><span data-ttu-id="d58bb-108">プロトコル、接続、およびスタートアップのオプション</span><span class="sxs-lookup"><span data-stu-id="d58bb-108">Protocols, Connection, and Startup Options</span></span>  
 <span data-ttu-id="d58bb-109">サービスを開始または停止したり、スタートアップ オプションを構成したり、プロトコルや他の接続オプションを有効にしたりするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-109">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to start and stop services, configure the startup options, and enable protocols and other connection options.</span></span>  
  
#### <a name="to-start-sql-server-configuration-manager"></a><span data-ttu-id="d58bb-110">SQL Server 構成マネージャーを起動するには</span><span class="sxs-lookup"><span data-stu-id="d58bb-110">To start SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="d58bb-111">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d58bb-111">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    -   <span data-ttu-id="d58bb-112">コンポーネントを起動して自動開始オプションを構成するには、 **[SQL Server のサービス]** 領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-112">Use the **SQL Server Services** area to start components and configure the automatic starting options.</span></span>  
  
    -   <span data-ttu-id="d58bb-113">接続プロトコル、固定 TCP/IP ポートなどの接続オプションを有効にしたり、暗号化を適用するには、 **[SQL Server ネットワークの構成]** 領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-113">Use the **SQL Server Network Configuration** area to enable connection protocols, and connection options such as fixed TCP/IP ports, or forcing encryption.</span></span>  
  
 <span data-ttu-id="d58bb-114">詳細については、「 [SQL Server Configuration Manager](../sql-server-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d58bb-114">For more information, see [SQL Server Configuration Manager](../sql-server-configuration-manager.md).</span></span> <span data-ttu-id="d58bb-115">リモート接続は、ファイアウォールの構成が正しいかどうかによっても異なります。</span><span class="sxs-lookup"><span data-stu-id="d58bb-115">Remote connectivity can also depend upon the correct configuration of a firewall.</span></span> <span data-ttu-id="d58bb-116">詳細については、[SQL Server アクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d58bb-116">For more information, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="enabling-and-disabling-features"></a><span data-ttu-id="d58bb-117">機能の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="d58bb-117">Enabling and Disabling Features</span></span>  
 <span data-ttu-id="d58bb-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の有効化と無効化は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]内のファセットを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="d58bb-118">Enabling and disabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features can be configured using facets in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-configure-surface-area-using-facets"></a><span data-ttu-id="d58bb-119">ファセットを使用してセキュリティを構成するには</span><span class="sxs-lookup"><span data-stu-id="d58bb-119">To configure surface area using facets</span></span>  
  
1.  <span data-ttu-id="d58bb-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のコンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-120">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] connect to a component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="d58bb-121">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[ファセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d58bb-121">In Object Explorer, right-click the server, and then click **Facets**.</span></span>  
  
3.  <span data-ttu-id="d58bb-122">**[ファセットの表示]** ダイアログ ボックスで、 **[ファセット]** の一覧を展開し、適切な **[セキュリティ構成]** ファセット ( **[セキュリティ構成]** 、 **[Analysis Services のセキュリティ構成]** 、または **[Reporting Services のセキュリティ構成]** ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-122">In the **View Facets** dialog box, expand the **Facet** list, and select the appropriate **Surface Area Configuration** facet (**Surface Area Configuration**, **Surface Area Configuration for Analysis Services**, or **Surface Area Configuration for Reporting Services**).</span></span>  
  
4.  <span data-ttu-id="d58bb-123">**[ファセットのプロパティ]** 領域で、それぞれのプロパティに使用する値を選択します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-123">In the **Facet properties** area, select the values that you want for each property.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d58bb-124">ファセットの構成を定期的に確認するには、ポリシー ベースの管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-124">To periodically check the configuration of a facet, use Policy-Based Management.</span></span> <span data-ttu-id="d58bb-125">条件と各ファセットおよびポリシーとの関係の詳細については、「 [ポリシー ベースの管理を使用したサーバーの管理](../policy-based-management/administer-servers-by-using-policy-based-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d58bb-125">For more information about Policy-Based Management, see [Administer Servers by Using Policy-Based Management](../policy-based-management/administer-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="d58bb-126">`sp_configure` ストアド プロシージャを使って[!INCLUDE[ssDE](../../includes/ssde-md.md)] オプションを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d58bb-126">You can also set [!INCLUDE[ssDE](../../includes/ssde-md.md)] options using the `sp_configure` stored procedure.</span></span> <span data-ttu-id="d58bb-127">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d58bb-127">For more information, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
 <span data-ttu-id="d58bb-128">**の** EnableIntegrated Security [!INCLUDE[ssRS](../../includes/ssrs.md)]プロパティを変更するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のプロパティ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-128">To change the **EnableIntegrated Security** property of [!INCLUDE[ssRS](../../includes/ssrs.md)], use the property settings in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d58bb-129">**[定期的なイベントおよびレポート配信]** プロパティと **[Web サービスおよび HTTP アクセス]** プロパティを変更するには、 **RSReportServer.config** 構成ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-129">To change the **Schedule events and report delivery** property and the **Web service and HTTP access** property, edit the **RSReportServer.config** configuration file.</span></span>  
  
## <a name="command-prompt-options"></a><span data-ttu-id="d58bb-130">コマンド プロンプト オプション</span><span class="sxs-lookup"><span data-stu-id="d58bb-130">Command-prompt Options</span></span>  
 <span data-ttu-id="d58bb-131">**Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell コマンドレットを使用して、セキュリティ構成ポリシーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-131">Use the **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell cmdlet to invoke Surface Area Configuration Policies.</span></span> <span data-ttu-id="d58bb-132">詳細については、「 [データベース エンジン コマンドレットの使用](../../database-engine/use-the-database-engine-cmdlets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d58bb-132">For more information, see [Use the Database Engine cmdlets](../../database-engine/use-the-database-engine-cmdlets.md).</span></span>  
  
## <a name="soap-and-service-broker-endpoints"></a><span data-ttu-id="d58bb-133">SOAP および Service Broker のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="d58bb-133">SOAP and Service Broker Endpoints</span></span>  
 <span data-ttu-id="d58bb-134">エンドポイントを無効にするには、ポリシー ベースの管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-134">To turn endpoints off, use Policy-Based Management.</span></span> <span data-ttu-id="d58bb-135">エンドポイントのプロパティを作成および変更するには、[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) および [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58bb-135">To create and alter the properties of endpoints, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) and [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d58bb-136">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="d58bb-136">Related Content</span></span>  
 [<span data-ttu-id="d58bb-137">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="d58bb-137">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="d58bb-138">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d58bb-138">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
