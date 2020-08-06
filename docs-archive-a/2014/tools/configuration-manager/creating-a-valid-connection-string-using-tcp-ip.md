---
title: TCP/IP を使用した有効な接続文字列の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f761fa86ec4ed09c13bf4807489754c10b979ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640304"
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a><span data-ttu-id="4bc22-102">TCP/IP を使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="4bc22-102">Creating a Valid Connection String Using TCP IP</span></span>
  <span data-ttu-id="4bc22-103">TCP/IP を使用した有効な接続文字列を作成するには、次の操作を行ってください。</span><span class="sxs-lookup"><span data-stu-id="4bc22-103">To create a valid connection string using TCP/IP, you must:</span></span>  
  
-   <span data-ttu-id="4bc22-104">**[別名]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bc22-104">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="4bc22-105">**[サーバー]** ボックスに、 **PING** ユーティリティを使用して接続できるサーバー名か、 **PING** ユーティリティを使用して接続できる IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="4bc22-105">For the **Server**, enter either a server name to which you can connect using the **PING** utility, or an IP address to which you can connect using the **PING** utility.</span></span> <span data-ttu-id="4bc22-106">名前付きインスタンスの場合は、インスタンス名を追加します。</span><span class="sxs-lookup"><span data-stu-id="4bc22-106">For a named instance append the instance name.</span></span>  
  
-   <span data-ttu-id="4bc22-107">**[プロトコル]** に **[TCP/IP]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bc22-107">Specify **TCP/IP** for the **Protocol**.</span></span>  
  
-   <span data-ttu-id="4bc22-108">**[ポート番号]** にポート番号を入力します。ポート番号は省略できます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-108">Optionally, enter a port number for the **Port No**.</span></span> <span data-ttu-id="4bc22-109">省略した場合の既定値は 1433 です。この既定値は、サーバー上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] の既定インスタンスのポート番号です。</span><span class="sxs-lookup"><span data-stu-id="4bc22-109">The default is 1433, which is the port number of the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a server.</span></span> <span data-ttu-id="4bc22-110">ポート 1433 でリッスンしていない名前付きインスタンスまたは既定のインスタンスに接続する場合は、ポート番号を指定するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc22-110">To connect to a named instance or a default instance that is not listening on port 1433, you must provide the port number, or start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span> <span data-ttu-id="4bc22-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスの構成の詳細については、「 [SQL Server Browser サービス](../../../2014/tools/configuration-manager/sql-server-browser-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bc22-111">For information on configuring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service, see [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="4bc22-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client コンポーネントは接続の時点で、指定された別名のサーバー、プロトコル、ポート番号の値をレジストリから読み取り、 `tcp:<servername>[\<instancename>],<port>` または `tcp:<IPAddress>[\<instancename>],<port>`の形式で接続文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4bc22-112">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and port values from the registry for the specified alias name, and creates a connection string in the format `tcp:<servername>[\<instancename>],<port>` or `tcp:<IPAddress>[\<instancename>],<port>`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bc22-113">既定では、ポート 1433 が [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ファイアウォールによって閉じられます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 1433 by default.</span></span> <span data-ttu-id="4bc22-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はポート 1433 経由で通信するため、TCP/IP を使用する着信クライアントをリッスンするように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を構成している場合は、このポートを再度開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bc22-114">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 1433, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using TCP/IP.</span></span> <span data-ttu-id="4bc22-115">ファイアウォールの構成方法については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SQL Server アクセスのためのファイアウォール構成方法」か、またはファイアウォールについてのドキュメンテーションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bc22-115">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4bc22-116">および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、インターネット プロトコル バージョン 4 (IPv4) とインターネット プロトコル バージョン 6 (IPv6) の両方が完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-116">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4bc22-117">構成マネージャーは、IPv4 と IPv6 のどちらの形式の IP アドレスも受け入れます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-117">Configuration Manager accepts both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="4bc22-118">IPv6 の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「IPv6 を使用した接続」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bc22-118">For information on IPv6, see "Connecting Using IPv6" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="4bc22-119">ローカル サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="4bc22-119">Connecting to the Local Server</span></span>  
 <span data-ttu-id="4bc22-120">クライアントと同じコンピューター上で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合は、サーバー名として `(local)` を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-120">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)` as the server name.</span></span> <span data-ttu-id="4bc22-121">このような指定はあいまいさを残すのでお勧めできませんが、対象のコンピューター上でクライアントを実行していることがわかっている場合には便利な機能です。</span><span class="sxs-lookup"><span data-stu-id="4bc22-121">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="4bc22-122">たとえば、営業スタッフは、ノート型コンピューター上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行し、プロジェクト データもそのノート型コンピューターに保存しておきます。このように、ネットワークに接続しないモバイル ユーザー用のアプリケーションの場合、 `(local)` に接続するクライアントは、常にそのノート型コンピューターで実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することになります。</span><span class="sxs-lookup"><span data-stu-id="4bc22-122">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to `(local)` would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="4bc22-123">`localhost` の代わりに**またはピリオド (** . `(local)`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-123">The word `localhost` or a period (**.**) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="4bc22-124">接続プロトコルの確認</span><span class="sxs-lookup"><span data-stu-id="4bc22-124">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="4bc22-125">次のクエリからは、現在の接続で使用しているプロトコルが返されます。</span><span class="sxs-lookup"><span data-stu-id="4bc22-125">The following query returns the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="4bc22-126">例</span><span class="sxs-lookup"><span data-stu-id="4bc22-126">Examples</span></span>  
 <span data-ttu-id="4bc22-127">サーバー名による接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-127">Connecting by server name:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="4bc22-128">名前付きのインスタンスに対するサーバー名による接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-128">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 <span data-ttu-id="4bc22-129">指定したポートに対するサーバー名による接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-129">Connecting by server name to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="4bc22-130">IP アドレスによる接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-130">Connecting by IP address:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="4bc22-131">名前付きのインスタンスに対する IP アドレスによる接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-131">Connecting by IP address to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 <span data-ttu-id="4bc22-132">指定したポートに対する IP アドレスによる接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-132">Connecting by IP address to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="4bc22-133">ローカル コンピューターに対する `(local)`による接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-133">Connecting to the local computer using `(local)`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 <span data-ttu-id="4bc22-134">ローカル コンピューターに対する `localhost`による接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-134">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 <span data-ttu-id="4bc22-135">ローカル コンピューター上の名前付きのインスタンスに対する `localhost`による接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-135">Connecting to a named instance on the local computer `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 <span data-ttu-id="4bc22-136">ローカル コンピューターに対するピリオドによる接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-136">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 <span data-ttu-id="4bc22-137">ローカル コンピューター上の名前付きのインスタンスに対するピリオドによる接続:</span><span class="sxs-lookup"><span data-stu-id="4bc22-137">Connecting to a named instance on the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4bc22-138">**sqlcmd** パラメーターとしてネットワーク プロトコルを指定することについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sqlcmd.exe を使用してデータベース エンジンに接続する方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bc22-138">For information on specifying the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc22-139">参照</span><span class="sxs-lookup"><span data-stu-id="4bc22-139">See Also</span></span>  
 <span data-ttu-id="4bc22-140">[共有メモリ プロトコルを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="4bc22-140">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="4bc22-141">[名前付きパイプを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="4bc22-141">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="4bc22-142">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="4bc22-142">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
