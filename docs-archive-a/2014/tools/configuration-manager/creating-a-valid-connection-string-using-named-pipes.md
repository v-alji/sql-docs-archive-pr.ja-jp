---
title: 名前付きパイプを使用した有効な接続文字列の作成 |Microsoft Docs
description: 名前付きパイププロトコルを使用して SQL Server のインスタンスに接続するときに、有効な接続文字列を作成する方法について説明します。 有効なパイプ名の例を表示します。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f3e1d01e9e5b7b1d1c0d1bb822bf233ceee636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640306"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a><span data-ttu-id="ee006-104">名前付きパイプを使用した有効な接続文字列の作成</span><span class="sxs-lookup"><span data-stu-id="ee006-104">Creating a Valid Connection String Using Named Pipes</span></span>
  <span data-ttu-id="ee006-105">ユーザーが変更しない限り、の既定のインスタンスは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名前付きパイププロトコルをリッスンするときに、を `\\.\pipe\sql\query` パイプ名として使用します。</span><span class="sxs-lookup"><span data-stu-id="ee006-105">Unless changed by the user, when the default instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on the named pipes protocol, it uses `\\.\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="ee006-106">ここで、ピリオドはコンピューターがローカル コンピューターであることを示し、`pipe` は接続が名前付きパイプであることを示します。`sql\query` はパイプの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="ee006-106">The period indicates that the computer is the local computer, `pipe` indicates that the connection is a named pipe, and `sql\query` is the name of the pipe.</span></span> <span data-ttu-id="ee006-107">既定のパイプに接続するには、別名でもパイプ名に `\\<computer_name>\pipe\sql\query` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee006-107">To connect to the default pipe, the alias must have `\\<computer_name>\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="ee006-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が別のパイプで受信を待機する構成になっている場合は、パイプ名としてそのパイプを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee006-108">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to listen on a different pipe, the pipe name must use that pipe.</span></span> <span data-ttu-id="ee006-109">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がパイプとして `\\.\pipe\unit\app` を使用している場合、別名ではパイプ名として `\\<computer_name>\pipe\unit\app` を使用しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ee006-109">For instance, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using `\\.\pipe\unit\app` as the pipe, the alias must use `\\<computer_name>\pipe\unit\app` as the pipe name.</span></span>  
  
 <span data-ttu-id="ee006-110">有効なパイプ名を作成するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee006-110">To create a valid pipe name, you must:</span></span>  
  
-   <span data-ttu-id="ee006-111">**[別名]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee006-111">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="ee006-112">**プロトコル**として [**名前付きパイプ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ee006-112">Select **Named Pipes** as the **Protocol**.</span></span>  
  
-   <span data-ttu-id="ee006-113">**パイプ名**を入力します。</span><span class="sxs-lookup"><span data-stu-id="ee006-113">Enter the **Pipe Name**.</span></span> <span data-ttu-id="ee006-114">または、[**パイプ名**] を空白のままにして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **プロトコル**と**サーバー**を指定した後に適切なパイプ名を入力 Configuration Manager ます。</span><span class="sxs-lookup"><span data-stu-id="ee006-114">Alternatively, you can leave **Pipe Name** blank and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager will complete the appropriate pipe name after you specify the **Protocol** and **Server**</span></span>  
  
-   <span data-ttu-id="ee006-115">**サーバー**を指定してください。</span><span class="sxs-lookup"><span data-stu-id="ee006-115">Specify a **Server**.</span></span> <span data-ttu-id="ee006-116">名前付きのインスタンスの場合は、サーバー名とインスタンス名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ee006-116">For a named instance you can provide a server name and instance name.</span></span>  
  
 <span data-ttu-id="ee006-117">Native Client コンポーネントは、接続時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指定されたエイリアス名のサーバー、プロトコル、パイプ名の値をレジストリから読み取り、またはの形式でパイプ名を作成し `np:\\<computer_name>\pipe\<pipename>` `np:\\<IPAddress>\pipe\<pipename>` ます。名前付きインスタンスの場合、既定のパイプ名は `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query` です。</span><span class="sxs-lookup"><span data-stu-id="ee006-117">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and pipe name values from the registry for the specified alias name, and creates a pipe name in the format `np:\\<computer_name>\pipe\<pipename>` or `np:\\<IPAddress>\pipe\<pipename>`.For a named instance, the default pipe name is `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee006-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)]既定では、Windows ファイアウォールはポート445を閉じます。</span><span class="sxs-lookup"><span data-stu-id="ee006-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 445 by default.</span></span> <span data-ttu-id="ee006-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はポート445を介して通信するため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が名前付きパイプを使用して受信クライアント接続をリッスンするように構成されている場合は、ポートを再度開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee006-119">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 445, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using named pipes.</span></span> <span data-ttu-id="ee006-120">ファイアウォールの構成方法については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SQL Server アクセスのためのファイアウォール構成方法」か、またはファイアウォールについてのドキュメンテーションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee006-120">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="ee006-121">ローカル サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="ee006-121">Connecting to the Local Server</span></span>  
 <span data-ttu-id="ee006-122">クライアントと同じコンピューター上で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合は、サーバー名として `(local)` を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee006-122">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)`as the server name.</span></span> <span data-ttu-id="ee006-123">`(local)` の使用はあいまいさを残すのでお勧めできませんが、対象のコンピューター上でクライアントを実行していることがわかっている場合には便利な機能です。</span><span class="sxs-lookup"><span data-stu-id="ee006-123">Using `(local)` is not encouraged because it leads to ambiguity; however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="ee006-124">たとえば、営業スタッフは、ノート型コンピューター上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行し、プロジェクト データもそのノート型コンピューターに保存しておきます。このように、ネットワークに接続しないモバイル ユーザー用のアプリケーションの場合、(local) に接続するクライアントは、常にそのノート型コンピューターで実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することになります。</span><span class="sxs-lookup"><span data-stu-id="ee006-124">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to (local) would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="ee006-125">`localhost` の代わりに、`(local)` またはピリオド (.) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee006-125">The word `localhost` or a period (.) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="ee006-126">接続プロトコルの確認</span><span class="sxs-lookup"><span data-stu-id="ee006-126">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="ee006-127">以下のクエリは、現在の接続に使用しているプロトコルを返します。</span><span class="sxs-lookup"><span data-stu-id="ee006-127">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="ee006-128">例</span><span class="sxs-lookup"><span data-stu-id="ee006-128">Examples</span></span>  
 <span data-ttu-id="ee006-129">既定のパイプに対するサーバー名による接続:</span><span class="sxs-lookup"><span data-stu-id="ee006-129">Connecting by server name to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="ee006-130">既定のパイプに対する IP アドレスによる接続:</span><span class="sxs-lookup"><span data-stu-id="ee006-130">Connecting by IP Address to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="ee006-131">既定以外のパイプに対するサーバー名による接続:</span><span class="sxs-lookup"><span data-stu-id="ee006-131">Connecting by server name to a non-default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="ee006-132">名前付きのインスタンスに対するサーバー名による接続:</span><span class="sxs-lookup"><span data-stu-id="ee006-132">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="ee006-133">ローカル コンピューターに対する `localhost`による接続:</span><span class="sxs-lookup"><span data-stu-id="ee006-133">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 <span data-ttu-id="ee006-134">ローカル コンピューターに対するピリオドによる接続:</span><span class="sxs-lookup"><span data-stu-id="ee006-134">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ee006-135">ネットワークプロトコルを**sqlcmd**パラメーターとして指定する方法については、オンラインブックの「sqlcmd.exe を使用してデータベースエンジンに接続する方法」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee006-135">To specify the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee006-136">参照</span><span class="sxs-lookup"><span data-stu-id="ee006-136">See Also</span></span>  
 <span data-ttu-id="ee006-137">[共有メモリプロトコルを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="ee006-137">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="ee006-138">[TCP IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="ee006-138">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 [<span data-ttu-id="ee006-139">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="ee006-139">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
