---
title: SQL Server へのログイン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, logging in
- services [SQL Server], logging in
- TCP connection string
- connecting to the Database Engine
- logins [SQL Server], about logging in
- named pipe connection string
- log ins [SQL Server]
- shared memory connection string
- logging in [SQL Server]
- logins [SQL Server]
ms.assetid: 77158a9a-d638-4818-90a1-cb2eb57df514
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dfe8aa5373c3aafe423f52c04b73c5b11d283c6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712382"
---
# <a name="logging-in-to-sql-server"></a><span data-ttu-id="54fbc-102">SQL Server へのログイン</span><span class="sxs-lookup"><span data-stu-id="54fbc-102">Logging In to SQL Server</span></span>
  <span data-ttu-id="54fbc-103">任意のグラフィカルな管理ツール、またはコマンド プロンプトを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにログインできます。</span><span class="sxs-lookup"><span data-stu-id="54fbc-103">You can log in to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using any of the graphical administration tools or from a command prompt.</span></span>  
  
 <span data-ttu-id="54fbc-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] などのグラフィカルな管理ツールを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のインスタンスにログインする場合、必要に応じて、サーバー名、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン、およびパスワードを指定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="54fbc-104">When you log in to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a graphical administration tool such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you are prompted to supply the server name, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, and a password, if necessary.</span></span> <span data-ttu-id="54fbc-105">Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログインする場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="54fbc-105">If you log in to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication, you do not have to provide a SQL Server login each time you access an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54fbc-106">代わりに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により自動的に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを使用したログインが行われます。</span><span class="sxs-lookup"><span data-stu-id="54fbc-106">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses your [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account to log you in automatically.</span></span> <span data-ttu-id="54fbc-107">混合モード認証 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードと Windows 認証モード) で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用してログインする場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログインとパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54fbc-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in mixed mode authentication ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication Mode), and you choose to log in using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span> <span data-ttu-id="54fbc-108">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="54fbc-108">When possible, use Windows Authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54fbc-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールしたときに大文字と小文字を区別する照合順序を選択した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインでも大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="54fbc-109">If you selected a case-sensitive collation when you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is also case sensitive.</span></span>  
  
## <a name="format-for-specifying-the-name-of-sql-server"></a><span data-ttu-id="54fbc-110">SQL Server の名前を指定する形式</span><span class="sxs-lookup"><span data-stu-id="54fbc-110">Format for Specifying the Name of SQL Server</span></span>  
 <span data-ttu-id="54fbc-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54fbc-111">When connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you must specify the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54fbc-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが既定のインスタンス (名前のないインスタンス) である場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているコンピューターの名前または IP アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="54fbc-112">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is the default instance (an unnamed instance), then specify the name of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, or the IP address of the computer.</span></span> <span data-ttu-id="54fbc-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが名前付きインスタンス (SQLEXPRESS など) である場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているコンピューターの名前または IP アドレスを指定し、スラッシュとインスタンス名を追加します。</span><span class="sxs-lookup"><span data-stu-id="54fbc-113">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is a named instance (such as SQLEXPRESS), then specify the name of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, or the IP address of the computer, and add a slash and the instance name.</span></span>  
  
 <span data-ttu-id="54fbc-114">次の例は、APPHOST という名前のコンピューターで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="54fbc-114">The following examples connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a computer named APPHOST.</span></span> <span data-ttu-id="54fbc-115">名前付きインスタンスを指定する場合は、インスタンス名の SQLEXPRESS を使用します。</span><span class="sxs-lookup"><span data-stu-id="54fbc-115">When specifying a named instance, the examples use an instance name SQLEXPRESS.</span></span>  
  
 <span data-ttu-id="54fbc-116">**例:**</span><span class="sxs-lookup"><span data-stu-id="54fbc-116">**Examples:**</span></span>  
  
|<span data-ttu-id="54fbc-117">インスタンスの型</span><span class="sxs-lookup"><span data-stu-id="54fbc-117">Type of Instance</span></span>|<span data-ttu-id="54fbc-118">サーバー名の入力</span><span class="sxs-lookup"><span data-stu-id="54fbc-118">Entry for the server name</span></span>|  
|----------------------|-------------------------------|  
|<span data-ttu-id="54fbc-119">既定のプロトコルによる既定のインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="54fbc-119">Connection to a default instance using the default protocol.</span></span> <span data-ttu-id="54fbc-120">(これが既定のインスタンスへの推奨される入力です)。</span><span class="sxs-lookup"><span data-stu-id="54fbc-120">(This is the recommended entry for a default instance.)</span></span>|<span data-ttu-id="54fbc-121">APPHOST</span><span class="sxs-lookup"><span data-stu-id="54fbc-121">APPHOST</span></span>|  
|<span data-ttu-id="54fbc-122">既定のプロトコルによる名前付きインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="54fbc-122">Connection to a named instance using the default protocol.</span></span> <span data-ttu-id="54fbc-123">(これが名前付きインスタンスへの推奨される入力です)。</span><span class="sxs-lookup"><span data-stu-id="54fbc-123">(This is the recommended entry for a named instance.)</span></span>|<span data-ttu-id="54fbc-124">APPHOST\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-124">APPHOST\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-125">ピリオドを使用して、インスタンスがローカル コンピューター上で実行されていることを示す、同じコンピューター上の既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-125">Connection to a default instance on the same computer using a period to indicate that the instance is running on the local computer.</span></span>|<span data-ttu-id="54fbc-126">。</span><span class="sxs-lookup"><span data-stu-id="54fbc-126">.</span></span>|  
|<span data-ttu-id="54fbc-127">ピリオドを使用して、インスタンスがローカル コンピューター上で実行されていることを示す、同じコンピューター上の名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-127">Connection to a named instance on the same computer using a period to indicate that the instance is running on the local computer.</span></span>|<span data-ttu-id="54fbc-128">.\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-128">.\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-129">localhost を使用して、インスタンスがローカル コンピューター上で実行されていることを示す、同じコンピューター上の既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-129">Connection to a default instance on the same computer using localhost to indicate that the instance is running on the local computer.</span></span>|<span data-ttu-id="54fbc-130">localhost</span><span class="sxs-lookup"><span data-stu-id="54fbc-130">localhost</span></span>|  
|<span data-ttu-id="54fbc-131">localhost を使用して、インスタンスがローカル コンピューター上で実行されていることを示す、同じコンピューター上の名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-131">Connection to a named instance on the same computer using localhost to indicate that the instance is running on the local computer.</span></span>|<span data-ttu-id="54fbc-132">localhost\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-132">localhost\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-133">(local) を使用して、インスタンスがローカル コンピューター上で実行されていることを示す、同じコンピューター上の既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-133">Connection to a default instance on the same computer using (local) to indicate that the instance is running on the local computer.</span></span>|<span data-ttu-id="54fbc-134">(local)</span><span class="sxs-lookup"><span data-stu-id="54fbc-134">(local)</span></span>|  
|<span data-ttu-id="54fbc-135">(local) を使用して、インスタンスがローカル コンピューター上で実行されていることを示す、同じコンピューター上の名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-135">Connection to a named instance on the same computer using (local) to indicate that the instance is running on the local computer.</span></span>|<span data-ttu-id="54fbc-136">(local)\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-136">(local)\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-137">共有メモリ接続を適用している同じコンピューター上の既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-137">Connection to a default instance on the same computer forcing a shared memory connection.</span></span>|<span data-ttu-id="54fbc-138">lpc:APPHOST</span><span class="sxs-lookup"><span data-stu-id="54fbc-138">lpc:APPHOST</span></span>|  
|<span data-ttu-id="54fbc-139">共有メモリ接続を適用している同じコンピューター上の名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-139">Connection to a named instance on the same computer forcing a shared memory connection.</span></span>|<span data-ttu-id="54fbc-140">lpc:APPHOST\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-140">lpc:APPHOST\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-141">IP アドレスを使用した、TCP アドレス 192.168.17.28 をリッスンしている既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-141">Connection to a default instance listening on TCP address 192.168.17.28 using an IP address.</span></span>|<span data-ttu-id="54fbc-142">192.168.17.28</span><span class="sxs-lookup"><span data-stu-id="54fbc-142">192.168.17.28</span></span>|  
|<span data-ttu-id="54fbc-143">IP アドレスを使用した、TCP アドレス 192.168.17.28 をリッスンしている名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-143">Connection to a named instance listening on TCP address 192.168.17.28 using an IP address.</span></span>|<span data-ttu-id="54fbc-144">192.168.17.28\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-144">192.168.17.28\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-145">使用されているポート (ここでは 2828) の指定による、既定の TCP ポートをリッスンしていない既定のインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="54fbc-145">Connection to a default instance that is not listening on the default TCP port, by specifying the port that is being used, in this case 2828.</span></span> <span data-ttu-id="54fbc-146">( [!INCLUDE[ssDE](../../includes/ssde-md.md)] が既定のポート (1433) をリッスンしている場合は不要)。</span><span class="sxs-lookup"><span data-stu-id="54fbc-146">(This is not necessary if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on the default port (1433).)</span></span>|<span data-ttu-id="54fbc-147">APPHOST,2828</span><span class="sxs-lookup"><span data-stu-id="54fbc-147">APPHOST,2828</span></span>|  
|<span data-ttu-id="54fbc-148">指定された TCP ポート (ここでは 2828) 上の名前付きインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="54fbc-148">Connection to a named instance on a designated TCP port, in this case 2828.</span></span> <span data-ttu-id="54fbc-149">(ホスト コンピューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合に、よく必要になります)。</span><span class="sxs-lookup"><span data-stu-id="54fbc-149">(This is often necessary if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is not running on the host computer.)</span></span>|<span data-ttu-id="54fbc-150">APPHOST,2828</span><span class="sxs-lookup"><span data-stu-id="54fbc-150">APPHOST,2828</span></span>|  
|<span data-ttu-id="54fbc-151">IP アドレスと使用されている TCP ポート (ここでは 2828) の指定による、既定の TCP ポートをリッスンしていない既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-151">Connection to a default instance that is not listening on the default TCP port, by specifying both the IP address and the TCP port that is being used, in this case 2828.</span></span>|<span data-ttu-id="54fbc-152">192.168.17.28,2828</span><span class="sxs-lookup"><span data-stu-id="54fbc-152">192.168.17.28,2828</span></span>|  
|<span data-ttu-id="54fbc-153">IP アドレスと使用されている TCP ポート (ここでは 2828) の指定による、名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-153">Connection to a named instance by specifying both the IP address and the TCP port that is being used, in this case 2828.</span></span>|<span data-ttu-id="54fbc-154">192.168.17.28,2828</span><span class="sxs-lookup"><span data-stu-id="54fbc-154">192.168.17.28,2828</span></span>|  
|<span data-ttu-id="54fbc-155">TCP 接続を適用する、名前による既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-155">Connecting to default instance by name, forcing a TCP connection.</span></span>|<span data-ttu-id="54fbc-156">tcp:APPHOST</span><span class="sxs-lookup"><span data-stu-id="54fbc-156">tcp:APPHOST</span></span>|  
|<span data-ttu-id="54fbc-157">TCP 接続を適用する、名前による名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-157">Connecting to named instance by name, forcing a TCP connection.</span></span>|<span data-ttu-id="54fbc-158">tcp:APPHOST\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-158">tcp:APPHOST\SQLEXPRESS</span></span>|  
|<span data-ttu-id="54fbc-159">名前付きパイプ名の指定による、既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-159">Connecting to a default instance by specifying a named pipe name.</span></span>|<span data-ttu-id="54fbc-160">\\\APPHOST\pipe\unit\app</span><span class="sxs-lookup"><span data-stu-id="54fbc-160">\\\APPHOST\pipe\unit\app</span></span>|  
|<span data-ttu-id="54fbc-161">名前付きパイプ名の指定による、名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-161">Connecting to a named instance by specifying a named pipe name.</span></span>|<span data-ttu-id="54fbc-162">\\\APPHOST\pipe\MSSQL$SQLEXPRESS\SQL\query</span><span class="sxs-lookup"><span data-stu-id="54fbc-162">\\\APPHOST\pipe\MSSQL$SQLEXPRESS\SQL\query</span></span>|  
|<span data-ttu-id="54fbc-163">名前付きパイプ接続を適用する、名前による既定のインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-163">Connecting to default instance by name, forcing a named pipes connection.</span></span>|<span data-ttu-id="54fbc-164">np:APPHOST</span><span class="sxs-lookup"><span data-stu-id="54fbc-164">np:APPHOST</span></span>|  
|<span data-ttu-id="54fbc-165">名前付きパイプ接続を適用する、名前による名前付きインスタンスへの接続。</span><span class="sxs-lookup"><span data-stu-id="54fbc-165">Connecting to named instance by name, forcing a named pipes connection.</span></span>|<span data-ttu-id="54fbc-166">np:APPHOST\SQLEXPRESS</span><span class="sxs-lookup"><span data-stu-id="54fbc-166">np:APPHOST\SQLEXPRESS</span></span>|  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="54fbc-167">接続プロトコルの確認</span><span class="sxs-lookup"><span data-stu-id="54fbc-167">Verifying your Connection Protocol</span></span>  
 <span data-ttu-id="54fbc-168">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続している場合、次のクエリは現在の接続に使用されているプロトコルと認証方法 (NTLM または Kerberos) を返し、接続が暗号化されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="54fbc-168">When connected to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], the following query will return the protocol  used for the current connection, along with the authentication method (NTLM or Kerberos), and will indicate if the connection is encrypted.</span></span>  
  
```sql  
SELECT net_transport, auth_scheme, encrypt_option   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="54fbc-169">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="54fbc-169">Related Tasks</span></span>  
 [<span data-ttu-id="54fbc-170">SQL Server インスタンスへのログイン &#40;コマンド プロンプト&#41;</span><span class="sxs-lookup"><span data-stu-id="54fbc-170">Log In to an Instance of SQL Server &#40;Command Prompt&#41;</span></span>](log-in-to-an-instance-of-sql-server-command-prompt.md)  
  
 <span data-ttu-id="54fbc-171">以下のリソースは、接続の問題に関するトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="54fbc-171">The following resources can help you troubleshoot a connection problem.</span></span>  
  
-   [<span data-ttu-id="54fbc-172">SQL Server データベース エンジンへの接続のトラブルシューティングの方法</span><span class="sxs-lookup"><span data-stu-id="54fbc-172">How to Troubleshoot Connecting to the SQL Server Database Engine</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
-   [<span data-ttu-id="54fbc-173">SQL の接続問題のトラブルシューティングの手順</span><span class="sxs-lookup"><span data-stu-id="54fbc-173">Steps to troubleshoot SQL connectivity issues</span></span>](https://docs.microsoft.com/archive/blogs/sql_protocols/steps-to-troubleshoot-sql-connectivity-issues)  
  
## <a name="related-content"></a><span data-ttu-id="54fbc-174">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="54fbc-174">Related Content</span></span>  
 [<span data-ttu-id="54fbc-175">認証モードの選択</span><span class="sxs-lookup"><span data-stu-id="54fbc-175">Choose an Authentication Mode</span></span>](../../relational-databases/security/choose-an-authentication-mode.md)  
  
 [<span data-ttu-id="54fbc-176">sqlcmd ユーティリティの使用</span><span class="sxs-lookup"><span data-stu-id="54fbc-176">Use the sqlcmd Utility</span></span>](../../relational-databases/scripting/sqlcmd-use-the-utility.md)  
  
 [<span data-ttu-id="54fbc-177">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="54fbc-177">Creating a Login</span></span>](../../t-sql/lesson-2-1-creating-a-login.md)  
  
  