---
title: 特定の TCP ポートでリッスンするようにサーバーを構成する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb740910c65580e8ea3170d03481e6cb628860
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632109"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a><span data-ttu-id="42732-102">特定の TCP ポートで受信待ちするようにサーバーを構成する方法 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="42732-102">Configure a Server to Listen on a Specific TCP Port (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="42732-103">このトピックでは、SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスが特定の固定ポートで受信待ちするように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42732-103">This topic describes how to configure an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to listen on a specific fixed port by using the SQL Server Configuration Manager.</span></span> <span data-ttu-id="42732-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の既定のインスタンスは、有効であれば TCP ポート 1433 で受信待ちします。</span><span class="sxs-lookup"><span data-stu-id="42732-104">If enabled, the default instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on TCP port 1433.</span></span> <span data-ttu-id="42732-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] と [!INCLUDE[ssEW](../../includes/ssew-md.md)] の名前付きインスタンスは、動的ポートを使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="42732-105">Named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] are configured for dynamic ports.</span></span> <span data-ttu-id="42732-106">つまり、これらのインスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの開始時に、使用可能なポートが選択されます。</span><span class="sxs-lookup"><span data-stu-id="42732-106">This means they select an available port when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is started.</span></span> <span data-ttu-id="42732-107">名前付きインスタンスにファイアウォール経由で接続する場合は、特定のポートで受信待ちするように [!INCLUDE[ssDE](../../includes/ssde-md.md)] を構成します。これにより、ファイアウォールで適切なポートを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="42732-107">When you are connecting to a named instance through a firewall, configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on a specific port, so that the appropriate port can be opened in the firewall.</span></span>  
  
 <span data-ttu-id="42732-108">Windows ファイアウォールの既定の設定の詳細と、データベース エンジン、Analysis Services、Reporting Services、および Integration Services に影響する TCP ポートの説明については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="42732-108">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="42732-109">ポート番号を選択する際は、特定のアプリケーションに割り当てられているポート番号の一覧を [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) で確認し、</span><span class="sxs-lookup"><span data-stu-id="42732-109">When selecting a port number, consult [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) for a list of port numbers that are assigned to specific applications.</span></span> <span data-ttu-id="42732-110">未割り当てのポート番号を選択してください。</span><span class="sxs-lookup"><span data-stu-id="42732-110">Select an unassigned port number.</span></span> <span data-ttu-id="42732-111">詳細については、「 [Windows Vista および Windows Server 2008 では TCP/IP の既定の動的ポート範囲が変更されている](https://support.microsoft.com/kb/929851)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42732-111">For more information, see [The default dynamic port range for TCP/IP has changed in Windows Vista and in Windows Server 2008](https://support.microsoft.com/kb/929851).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="42732-112">データベース エンジンは、再起動時に新しいポート上でリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="42732-112">The Database Engine begins listening on a new port when restarted.</span></span> <span data-ttu-id="42732-113">ただし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは、レジストリを監視し、データベース エンジンが使用していない可能性があっても、構成が変更されるとすぐに新しいポート番号をレポートします。</span><span class="sxs-lookup"><span data-stu-id="42732-113">However the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service monitors the registry and reports the new port number as soon as the configuration is changed, even though the Database Engine might not be using it.</span></span> <span data-ttu-id="42732-114">一貫性を確保し、接続エラーを避けるために、データベース エンジンを再開します。</span><span class="sxs-lookup"><span data-stu-id="42732-114">Restart the Database Engine to ensure consistency and avoid connection failures.</span></span>  
  
 <span data-ttu-id="42732-115">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="42732-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="42732-116">**サーバーが特定の TCP ポートで受信待ちするよう構成する方法:**</span><span class="sxs-lookup"><span data-stu-id="42732-116">**To configure a server to listen on a specific TCP port, using:**</span></span>  
  
     [<span data-ttu-id="42732-117">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="42732-117">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42732-118">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="42732-118">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a><span data-ttu-id="42732-119">SQL Server データベース エンジンに TCP/IP ポート番号を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="42732-119">To assign a TCP/IP port number to the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="42732-120">SQL Server 構成マネージャーのコンソール ペインで、 **[SQL Server ネットワークの構成]** 、 **[\<instance name> のプロトコル]** の順に展開し、 **[TCP/IP]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="42732-120">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, expand **Protocols for \<instance name>**, and then double-click **TCP/IP**.</span></span>  
  
2.  <span data-ttu-id="42732-121">**[TCP/IP のプロパティ]** ダイアログ ボックスの **[IP アドレス]** タブに、 **IP1**、 **IP2**という形式で **IPAll**まで IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42732-121">In the **TCP/IP Properties** dialog box, on the **IP Addresses** tab, several IP addresses appear in the format **IP1**, **IP2**, up to **IPAll**.</span></span> <span data-ttu-id="42732-122">このうちいずれかが、ループバック アダプターの IP アドレス 127.0.0.1 です。</span><span class="sxs-lookup"><span data-stu-id="42732-122">One of these is for the IP address of the loopback adapter, 127.0.0.1.</span></span> <span data-ttu-id="42732-123">追加の IP アドレスがコンピューターの各 IP アドレスとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="42732-123">Additional IP addresses appear for each IP Address on the computer.</span></span> <span data-ttu-id="42732-124">各アドレスを右クリックし、**[プロパティ]** をクリックして、構成する IP アドレスを識別します。</span><span class="sxs-lookup"><span data-stu-id="42732-124">Right-click each address, and then click **Properties** to identify the IP address that you want to configure.</span></span>  
  
3.  <span data-ttu-id="42732-125">**[TCP 動的ポート]** ダイアログ ボックスには、 **が動的ポートで受信待ちすることを示す**0 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が表示されています。この 0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="42732-125">If the **TCP Dynamic Ports** dialog box contains **0**, indicating the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on dynamic ports, delete the 0.</span></span>  
  
4.  <span data-ttu-id="42732-126">[**IP**_n_ **のプロパティ**] ボックスの **[TCP ポート]** ボックスに、この IP アドレスが受信待ちするポート番号を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42732-126">In the **IP**_n_ **Properties** area box, in the **TCP Port** box, type the port number you want this IP address to listen on, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="42732-127">コンソール ペインで、 **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42732-127">In the console pane, click **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="42732-128">詳細ペインで、 **[SQL Server (** \<instance name> **)]** を右クリックします。 **[再起動]** をクリックして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止し、再起動します。</span><span class="sxs-lookup"><span data-stu-id="42732-128">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="42732-129">特定のポートで受信待ちするように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を構成した後、次の 3 つの方法でクライアント アプリケーションを使用して特定のポートに接続できます。</span><span class="sxs-lookup"><span data-stu-id="42732-129">After you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a specific port, there are three ways to connect to a specific port with a client application:</span></span>  
  
-   <span data-ttu-id="42732-130">サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行し、名前を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続する。</span><span class="sxs-lookup"><span data-stu-id="42732-130">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance by name.</span></span>  
  
-   <span data-ttu-id="42732-131">ポート番号を指定してクライアント上に別名を作成する。</span><span class="sxs-lookup"><span data-stu-id="42732-131">Create an alias on the client, specifying the port number.</span></span>  
  
-   <span data-ttu-id="42732-132">クライアントで、カスタム接続文字列を使用して接続するように指定します。</span><span class="sxs-lookup"><span data-stu-id="42732-132">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42732-133">参照</span><span class="sxs-lookup"><span data-stu-id="42732-133">See Also</span></span>  
 [<span data-ttu-id="42732-134">クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="42732-134">Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;</span></span>](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
