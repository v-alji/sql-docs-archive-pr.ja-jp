---
title: ネットワーク プロトコルとネットワーク ライブラリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server]
- configuration options [SQL Server], protocols
- network libraries [SQL Server]
- protocols [SQL Server], about network protocols
- pipes [SQL Server]
- network protocols [SQL Server]
- default SQL Server configurations
- library [SQL Server]
- network protocols [SQL Server], about network protocols
- configuration options [SQL Server], libraries
ms.assetid: 8cd437f6-9af1-44ce-9cb0-4d10c83da9ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be012ea2bc9499a99ca7763446c6f26cf219a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644787"
---
# <a name="network-protocols-and-network-libraries"></a><span data-ttu-id="14c30-102">ネットワーク プロトコルとネットワーク ライブラリ</span><span class="sxs-lookup"><span data-stu-id="14c30-102">Network Protocols and Network Libraries</span></span>
  <span data-ttu-id="14c30-103">サーバーは、一度に複数のネットワーク プロトコルでリッスンまたは監視することができます。</span><span class="sxs-lookup"><span data-stu-id="14c30-103">A server can listen on, or monitor, multiple network protocols at one time.</span></span> <span data-ttu-id="14c30-104">ただし、これには各プロトコルを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14c30-104">However, each protocol must be configured.</span></span> <span data-ttu-id="14c30-105">特定のプロトコルが構成されていない場合、サーバーはそのプロトコルでリッスンできません。</span><span class="sxs-lookup"><span data-stu-id="14c30-105">If a particular protocol is not configured, the server cannot listen on that protocol.</span></span> <span data-ttu-id="14c30-106">インストール後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、プロトコルの構成を変更できます。</span><span class="sxs-lookup"><span data-stu-id="14c30-106">After installation, you can change the protocol configurations using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="default-sql-server-network-configuration"></a><span data-ttu-id="14c30-107">SQL Server の既定のネットワーク構成</span><span class="sxs-lookup"><span data-stu-id="14c30-107">Default SQL Server Network Configuration</span></span>  
 <span data-ttu-id="14c30-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスは、TCP/IP ポート 1433 と名前付きパイプ \\\\.\pipe\sql\query です。</span><span class="sxs-lookup"><span data-stu-id="14c30-108">A default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for TCP/IP port 1433, and named pipe \\\\.\pipe\sql\query.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="14c30-109">の名前付きインスタンスは TCP 動的ポートに構成され、ポート番号がオペレーティング システムによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="14c30-109">named instances are configured for TCP dynamic ports, with a port number assigned by the operating system.</span></span>  
  
 <span data-ttu-id="14c30-110">動的ポート アドレスを使用できない場合 (たとえば、特定のポート アドレスを通過するように構成されたファイアウォール サーバーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の接続が通過する必要がある場合) は、</span><span class="sxs-lookup"><span data-stu-id="14c30-110">If you cannot use dynamic port addresses (for example, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections must pass through a firewall server configured to pass through specific port addresses).</span></span> <span data-ttu-id="14c30-111">未割り当てのポート番号を選択してください。</span><span class="sxs-lookup"><span data-stu-id="14c30-111">Select an unassigned port number.</span></span> <span data-ttu-id="14c30-112">ポート番号の割り当ては、Internet Assigned Numbers Authority によって管理され、[http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844) に一覧が掲載されています。</span><span class="sxs-lookup"><span data-stu-id="14c30-112">Port number assignments are managed by the Internet Assigned Numbers Authority and are listed at [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844).</span></span>  
  
 <span data-ttu-id="14c30-113">セキュリティを強化するため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時にネットワーク接続は完全には有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="14c30-113">To enhance security, network connectivity is not fully enabled when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="14c30-114">セットアップの完了後にネットワーク プロトコルを有効化、無効化、または構成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワークの構成領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="14c30-114">To enable, disable, and configure network protocols after Setup is complete, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Configuration area of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="server-message-block-protocol"></a><span data-ttu-id="14c30-115">サーバー メッセージ ブロック プロトコル</span><span class="sxs-lookup"><span data-stu-id="14c30-115">Server Message Block Protocol</span></span>  
 <span data-ttu-id="14c30-116">境界ネットワーク内のサーバーでは、サーバー メッセージ ブロック (SMB) を含め、不要なプロトコルをすべて無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14c30-116">Servers in the perimeter network should have all unnecessary protocols disabled, including server message block (SMB).</span></span> <span data-ttu-id="14c30-117">Web サーバーとドメイン ネーム システム (DNS) サーバーは SMB を必要としません。</span><span class="sxs-lookup"><span data-stu-id="14c30-117">Web servers and Domain Name System (DNS) servers do not require SMB.</span></span> <span data-ttu-id="14c30-118">ユーザー列挙の脅威に対抗するためには、このプロトコルを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14c30-118">This protocol should be disabled to counter the threat of user enumeration.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="14c30-119">サーバー メッセージ ブロックを無効にすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または Windows クラスター サービスからリモート ファイル共有にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="14c30-119">Disabling Server Message Block will block the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Windows Cluster service from accessing the remote file share.</span></span> <span data-ttu-id="14c30-120">以下のいずれかの作業を行う、または計画している場合は、SMB を無効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="14c30-120">Do not disable SMB if you do or plan to do one of the following:</span></span>  
> 
>  -   <span data-ttu-id="14c30-121">Windows クラスター ノードおよびファイル共有マジョリティ クォーラム モードを使用する</span><span class="sxs-lookup"><span data-stu-id="14c30-121">Use Windows Cluster Node and File Share Majority Quorum mode</span></span>  
> -   <span data-ttu-id="14c30-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に SMB ファイル共有をデータ ディレクトリとして指定する</span><span class="sxs-lookup"><span data-stu-id="14c30-122">Specify an SMB file share as the data directory during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation</span></span>  
> -   <span data-ttu-id="14c30-123">SMB ファイル共有でデータベース ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="14c30-123">Create a database file on an SMB file share</span></span>  
  
#### <a name="to-disable-smb"></a><span data-ttu-id="14c30-124">SMB を無効にするには</span><span class="sxs-lookup"><span data-stu-id="14c30-124">To disable SMB</span></span>  
  
1.  <span data-ttu-id="14c30-125">**[スタート]** ボタンをクリックし、 **[設定]** をポイントして、 **[ネットワークとダイヤルアップ接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14c30-125">On the **Start** menu, point to **Settings**, and then click **Network and Dial-up Connections**.</span></span>  
  
     <span data-ttu-id="14c30-126">インターネットに直接つながっている接続を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14c30-126">Right-click the Internet-facing connection, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="14c30-127">**[Microsoft ネットワーク用クライアント]** チェック ボックスをオンにして、 **[アンインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14c30-127">Select the **Client for Microsoft Networks** check box, and then click **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="14c30-128">アンインストールの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="14c30-128">Follow the uninstall steps.</span></span>  
  
4.  <span data-ttu-id="14c30-129">**[Microsoft ネットワーク用ファイルとプリンター共有]** チェック ボックスをオンにして、 **[アンインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14c30-129">Select **File and Printer Sharing for Microsoft Networks**, and then click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="14c30-130">アンインストールの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="14c30-130">Follow the uninstall steps.</span></span>  
  
#### <a name="to-disable-smb-on-servers-accessible-from-the-internet"></a><span data-ttu-id="14c30-131">インターネットからアクセス可能なサーバーで SMB を無効にするには</span><span class="sxs-lookup"><span data-stu-id="14c30-131">To disable SMB on servers accessible from the Internet</span></span>  
  
-   <span data-ttu-id="14c30-132">[ローカル エリア接続のプロパティ] で、 **[インターネット プロトコル (TCP/IP) のプロパティ]** ダイアログ ボックスを使用して、 **[Microsoft ネットワーク用ファイルとプリンター共有]** と **[Microsoft ネットワーク用クライアント]** を削除します。</span><span class="sxs-lookup"><span data-stu-id="14c30-132">In the Local Area Connection properties, use the **Transmission Control Protocol/Internet Protocol (TCP/IP) properties** dialog box to remove **File and Printer Sharing for Microsoft Networks** and **Client for Microsoft Networks**.</span></span>  
  
## <a name="endpoints"></a><span data-ttu-id="14c30-133">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="14c30-133">Endpoints</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="14c30-134">では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続に関して新しい概念が導入されました。接続は、 [!INCLUDE[tsql](../../includes/tsql-md.md)]*エンドポイント*によりサーバー エンドで表されます。</span><span class="sxs-lookup"><span data-stu-id="14c30-134">introduces a new concept for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections; the connection is represented on the server end by a [!INCLUDE[tsql](../../includes/tsql-md.md)]*endpoint*.</span></span> <span data-ttu-id="14c30-135">[!INCLUDE[tsql](../../includes/tsql-md.md)] エンドポイントに対して、権限の許可、取り消し、および拒否が行われます。</span><span class="sxs-lookup"><span data-stu-id="14c30-135">Permissions can be granted, revoked, and denied for [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints.</span></span> <span data-ttu-id="14c30-136">既定では、sysadmin グループのメンバーまたはエンドポイント所有者によって拒否または取り消しが行われない限り、エンドポイントへアクセスする権限はすべてのユーザーにあります。</span><span class="sxs-lookup"><span data-stu-id="14c30-136">By default, all users have permissions to access an endpoint unless the permissions are denied or revoked by a member of the sysadmin group or by the endpoint owner.</span></span> <span data-ttu-id="14c30-137">GRANT、REVOKE、および DENY ENDPOINT 構文では、管理者がエンドポイントのカタログ ビューから取得する必要があるエンドポイント ID を使用します。</span><span class="sxs-lookup"><span data-stu-id="14c30-137">The GRANT, REVOKE, and DENY ENDPOINT syntax uses an endpoint ID that the administrator must get from the endpoint's catalog view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="14c30-138">セットアップを実行すると、専用管理者接続のエンドポイントに加えて、サポートされるすべてのネットワーク プロトコルの [!INCLUDE[tsql](../../includes/tsql-md.md)] エンドポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="14c30-138">Setup creates [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints for all supported network protocols, as well as for the dedicated administrator connection.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="14c30-139">セットアップで作成される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エンドポイントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="14c30-139">endpoints created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup are as follows:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="14c30-140">ローカル マシン</span><span class="sxs-lookup"><span data-stu-id="14c30-140">local machine</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="14c30-141">名前付きパイプ</span><span class="sxs-lookup"><span data-stu-id="14c30-141">named pipes</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="14c30-142">既定 TCP</span><span class="sxs-lookup"><span data-stu-id="14c30-142">default TCP</span></span>  
  
 <span data-ttu-id="14c30-143">エンドポイントの詳細については、「[複数の TCP ポートでリッスンするデータベース エンジンの構成](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)」と「[エンドポイントのカタログ ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c30-143">For more information about endpoints, see [Configure the Database Engine to Listen on Multiple TCP Ports](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md) and [Endpoints Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql).</span></span>  
  
 <span data-ttu-id="14c30-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワーク構成の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="14c30-144">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network configurations, see the following topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="14c30-145">サーバー ネットワークの構成</span><span class="sxs-lookup"><span data-stu-id="14c30-145">Server Network Configuration</span></span>](../../database-engine/configure-windows/server-network-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="14c30-146">参照</span><span class="sxs-lookup"><span data-stu-id="14c30-146">See Also</span></span>  
 <span data-ttu-id="14c30-147">[セキュリティ構成](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="14c30-147">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 <span data-ttu-id="14c30-148">[SQL Server インストールにおけるセキュリティの考慮事項](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="14c30-148">[Security Considerations for a SQL Server Installation](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="14c30-149">SQL Server のインストール計画</span><span class="sxs-lookup"><span data-stu-id="14c30-149">Planning a SQL Server Installation</span></span>](../../../2014/sql-server/install/planning-a-sql-server-installation.md)  
  
  
