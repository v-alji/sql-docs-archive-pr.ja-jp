---
title: 複数の TCP ポートでリッスンするデータベース エンジンの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multiple
- TDS
- listen on multiple ports
- endpoints [SQL Server], TDS
- adding ports
- tabular data stream
- multiple ports
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab803bcaa5ab6b6187c1a994abef02f81ae105c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632698"
---
# <a name="configure-the-database-engine-to-listen-on-multiple-tcp-ports"></a><span data-ttu-id="36852-102">複数の TCP ポートでリッスンするデータベース エンジンの構成</span><span class="sxs-lookup"><span data-stu-id="36852-102">Configure the Database Engine to Listen on Multiple TCP Ports</span></span>
  <span data-ttu-id="36852-103">このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で SQL Server 構成マネージャーを使用して、複数の TCP ポートをリッスンするように [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36852-103">This topic describes how to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on multiple TCP ports in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="36852-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で TCP/IP を有効にしている場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、IP アドレスと TCP ポート番号で構成される接続ポイントで着信接続をリッスンします。次の手順では、表形式のデータ ストリーム (TDS) エンドポイントを作成し、追加の TCP ポートを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンするように設定します。</span><span class="sxs-lookup"><span data-stu-id="36852-104">When TCP/IP is enabled for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will listen for incoming connections on a connection point consisting of an IP address and TCP port number.The following procedures create a tabular data stream (TDS) endpoint, so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will listen on an additional TCP port.</span></span>  
  
 <span data-ttu-id="36852-105">2 つ目の TDS エンドポイントを作成する理由として考えられる点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36852-105">Possible reasons to create a second TDS endpoint include:</span></span>  
  
-   <span data-ttu-id="36852-106">特定のサブネットに存在するローカル クライアント コンピューターの既定のエンドポイントへのアクセスを制限するようにファイアウォールを構成することによって、セキュリティを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="36852-106">Increase security by configuring the firewall to restrict access to the default endpoint to local client computers on a specific subnet.</span></span> <span data-ttu-id="36852-107">サポート チーム向けに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのインターネット アクセスを保持する場合は、ファイアウォールからインターネットに公開する新しいエンドポイントを作成し、このエンドポイントへの接続の権利をサーバー サポート チームに制限します。</span><span class="sxs-lookup"><span data-stu-id="36852-107">Maintain Internet access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for your support team by creating a new endpoint that the firewall exposes to the Internet, and restricting connection rights to this endpoint to your server support team.</span></span>  
  
-   <span data-ttu-id="36852-108">NUMA (Non-Uniform Memory Access) を使用する場合に、特定のプロセッサに接続を関係付けることができます。</span><span class="sxs-lookup"><span data-stu-id="36852-108">Affinitizing connections to specific processors when using Non-Uniform Memory Access (NUMA).</span></span>  
  
 <span data-ttu-id="36852-109">TDS エンドポイントの構成手順は次のとおりです。実行する順序は問いません。</span><span class="sxs-lookup"><span data-stu-id="36852-109">Configuring a TDS endpoint consists of the following steps, which can be done in any order:</span></span>  
  
-   <span data-ttu-id="36852-110">TCP ポートに対して TDS エンドポイントを作成し、必要に応じて既定のエンドポイントへのアクセスを復元します。</span><span class="sxs-lookup"><span data-stu-id="36852-110">Create the TDS endpoint for the TCP port, and restore access to the default endpoint if appropriate.</span></span>  
  
-   <span data-ttu-id="36852-111">対象のサーバー プリンシパルにエンドポイントへのアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="36852-111">Grant access to the endpoint to the desired server principals.</span></span>  
  
-   <span data-ttu-id="36852-112">選択された IP アドレス用の TCP ポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="36852-112">Specify the TCP port number for the selected IP address.</span></span>  
  
 <span data-ttu-id="36852-113">Windows ファイアウォールの既定の設定の詳細と、データベース エンジン、Analysis Services、Reporting Services、および Integration Services に影響する TCP ポートの説明については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36852-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-tds-endpoint"></a><span data-ttu-id="36852-114">TDS エンドポイントを作成するには</span><span class="sxs-lookup"><span data-stu-id="36852-114">To create a TDS endpoint</span></span>  
  
-   <span data-ttu-id="36852-115">次のステートメントを実行し、サーバー上の利用できるすべての TCP アドレスのポート 1500 に対して **CustomConnection** という名前のエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="36852-115">Issue the following statement to create an endpoint named **CustomConnection** for port 1500 for all available TCP addresses on the server.</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 <span data-ttu-id="36852-116">新しい [!INCLUDE[tsql](../../includes/tsql-md.md)] エンドポイントを作成すると、既定の TDS エンドポイントに対する **public** の接続権限は取り消されます。</span><span class="sxs-lookup"><span data-stu-id="36852-116">When you create a new [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoint, connect permissions for **public** are revoked for the default TDS endpoint.</span></span> <span data-ttu-id="36852-117">既定のエンドポイントに対して **public** グループへのアクセスが必要な場合は、 `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` ステートメントを使用してこの権限を再適用します。</span><span class="sxs-lookup"><span data-stu-id="36852-117">If access to the **public** group is needed for the default endpoint, reapply this permission by using the `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` statement.</span></span>  
  
#### <a name="to-grant-access-to-the-endpoint"></a><span data-ttu-id="36852-118">エンドポイントへのアクセスを許可するには</span><span class="sxs-lookup"><span data-stu-id="36852-118">To grant access to the endpoint</span></span>  
  
-   <span data-ttu-id="36852-119">次のステートメントを実行し、corp ドメイン内の SQLSupport グループに対して **CustomConnection** エンドポイントへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="36852-119">Issue the following statement to grant access to the **CustomConnection** endpoint to the SQLSupport group in the corp domain.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### <a name="to-configure-the-sql-server-database-engine-to-listen-on-an-additional-tcp-port"></a><span data-ttu-id="36852-120">追加の TCP ポートでリッスンするように SQL Server データベース エンジンを構成するには</span><span class="sxs-lookup"><span data-stu-id="36852-120">To configure the SQL Server Database Engine to listen on an additional TCP port</span></span>  
  
1.  <span data-ttu-id="36852-121">SQL Server 構成マネージャーで **[SQL Server ネットワークの構成]** を展開し、 _[<instance_name>_ **のプロトコル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-121">In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for**_<instance_name>_.</span></span>  
  
2.  <span data-ttu-id="36852-122">**[ _<instance_name>_ のプロトコル]** を展開し、 **[TCP/IP]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-122">Expand **Protocols for**_<instance_name>_, and then click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="36852-123">右ペインで、無効になっている IP アドレスのうち、有効にする IP アドレスをそれぞれ右クリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-123">In the right pane, right-click each disabled IP address that you want to enable, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="36852-124">**[IPAll]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-124">Right-click **IPAll**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="36852-125">**[TCP ポート]** ボックスで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] がリッスンするポートを入力します。複数のポートを指定する場合はコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="36852-125">In the **TCP Port** box, type the ports that you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, separated by commas.</span></span> <span data-ttu-id="36852-126">この例では、既定のポート1433が一覧表示されている場合は、ボックスに「 `,1500` `1433,1500` 」と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-126">In our example, if the default port 1433 is listed, type `,1500` so the box reads `1433,1500`, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36852-127">一部の IP アドレスのポートだけを有効にする場合、[プロパティ] ダイアログ ボックスで、必要なアドレスに対してのみ追加のポートを構成します。</span><span class="sxs-lookup"><span data-stu-id="36852-127">If you are not enabling the port on all IP addresses, configure the additional port in the property box for only for the desired address.</span></span> <span data-ttu-id="36852-128">次に、コンソール ペインで、 **[TCP/IP]** を右クリックし、 **[プロパティ]** をクリックします。 **[すべて受信待ち]** ボックスで、 **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36852-128">Then, in the console pane, right-click **TCP/IP**, click **Properties**, and in the **Listen All** box, select **No**.</span></span>  
  
6.  <span data-ttu-id="36852-129">左ペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-129">In the left pane, click **SQL Server Services**.</span></span>  
  
7.  <span data-ttu-id="36852-130">右ペインで、 **[SQL Server _<instance_name>_ ]** を右クリックし、 **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36852-130">In the right pane, right-click **SQL Server**_<instance_name>_, and then click **Restart**.</span></span>  
  
     <span data-ttu-id="36852-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]が再起動すると、エラー ログには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンしているポートが記録されています。</span><span class="sxs-lookup"><span data-stu-id="36852-131">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] restarts, the Error log will list the ports on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening.</span></span>  
  
#### <a name="to-connect-to-the-new-endpoint"></a><span data-ttu-id="36852-132">新しいエンドポイントに接続するには</span><span class="sxs-lookup"><span data-stu-id="36852-132">To connect to the new endpoint</span></span>  
  
-   <span data-ttu-id="36852-133">次のステートメントを実行し、ACCT という名前のサーバー上にある、既定の SQL Server インスタンスの **CustomConnection** エンドポイントに接続します。このとき、信頼関係接続を使用します。ユーザーは [corp\SQLSupport] グループのメンバーであると想定しています。</span><span class="sxs-lookup"><span data-stu-id="36852-133">Issue the following statement to connect to the **CustomConnection** endpoint of the default instance of SQL Server on the server named ACCT, using a trusted connection, and assuming the user is a member of the [corp\SQLSupport] group.</span></span>  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36852-134">参照</span><span class="sxs-lookup"><span data-stu-id="36852-134">See Also</span></span>  
 <span data-ttu-id="36852-135">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36852-135">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="36852-136">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36852-136">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="36852-137">[GRANT (エンドポイントのアクセス許可の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36852-137">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="36852-138">NUMA ノードへの TCP/IP ポートのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="36852-138">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)  
  
  
