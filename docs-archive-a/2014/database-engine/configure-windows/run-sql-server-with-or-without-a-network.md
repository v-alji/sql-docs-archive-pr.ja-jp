---
title: ネットワークを使用する場合とネットワークを使用しない場合の SQL Server の実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a80e7e4d42f322bc42d0c67c57e3a1f9bddb87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641230"
---
# <a name="run-sql-server-with-or-without-a-network"></a><span data-ttu-id="95796-102">ネットワークを使用する場合とネットワークを使用しない場合の SQL Server の実行</span><span class="sxs-lookup"><span data-stu-id="95796-102">Run SQL Server With or Without a Network</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="95796-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はネットワーク上で実行できます。また、ネットワークを使用せずに機能させることもできます。</span><span class="sxs-lookup"><span data-stu-id="95796-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can run on a network, or it can function without a network.</span></span>  
  
## <a name="running-sql-server-on-a-network"></a><span data-ttu-id="95796-104">ネットワーク上での SQL Server の実行</span><span class="sxs-lookup"><span data-stu-id="95796-104">Running SQL Server on a Network</span></span>  
 <span data-ttu-id="95796-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がネットワーク経由で通信するようにするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95796-105">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to communicate over a network, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service must be running.</span></span> <span data-ttu-id="95796-106">既定では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows により、組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="95796-106">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows automatically starts the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="95796-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが開始されているかどうかを調べるには、コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="95796-107">To find out whether the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has been started, at the command prompt, type the following:</span></span>  
  
 <span data-ttu-id="95796-108">**net start**</span><span class="sxs-lookup"><span data-stu-id="95796-108">**net start**</span></span>  
  
 <span data-ttu-id="95796-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に関連付けれらたサービスが開始されている場合は、以下のサービスが **net start** の出力に表示されます。</span><span class="sxs-lookup"><span data-stu-id="95796-109">If the services associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have been started, the following services will appear in the **net start** output:</span></span>  
  
-   <span data-ttu-id="95796-110">Analysis Services (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="95796-110">Analysis Services (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="95796-111">SQL Server (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="95796-111">SQL Server (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="95796-112">SQL Server Agent (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="95796-112">SQL Server Agent (MSSQLSERVER)</span></span>  
  
## <a name="running-sql-server-without-a-network"></a><span data-ttu-id="95796-113">ネットワークを使用しない SQL Server の実行</span><span class="sxs-lookup"><span data-stu-id="95796-113">Running SQL Server Without a Network</span></span>  
 <span data-ttu-id="95796-114">ネットワークを使用せずに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを実行する場合は、組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを開始する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="95796-114">When running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without a network, you do not need to start the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="95796-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、SQL Server 構成マネージャー、および **net start** コマンドと **net stop** コマンドは、ネットワークを使用していなくても機能するので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動および停止する手順は、ネットワークを使用している場合もスタンドアロン運用の場合も同じです。</span><span class="sxs-lookup"><span data-stu-id="95796-115">Because [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SQL Server Configuration Manager, and the **net start** and **net stop** commands are functional even without a network, the procedures for starting and stopping an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are identical for a network or stand-alone operation.</span></span>  
  
 <span data-ttu-id="95796-116">**sqlcmd** などのローカル クライアントからスタンドアロンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときは、ネットワークを使用せずに、ローカル パイプを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに直接接続します。</span><span class="sxs-lookup"><span data-stu-id="95796-116">When connecting to an instance of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a local client such as **sqlcmd**, you bypass the network and connect directly to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a local pipe.</span></span> <span data-ttu-id="95796-117">ローカル パイプとネットワーク パイプの相違は、ネットワークを使用するかしないかです。</span><span class="sxs-lookup"><span data-stu-id="95796-117">The difference between a local pipe and a network pipe is whether you are using a network.</span></span> <span data-ttu-id="95796-118">他に指定がない限り、ローカル パイプでもネットワーク パイプでも、標準パイプ (\\\\.\pipe\sql\query) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスとの接続が確立されます。</span><span class="sxs-lookup"><span data-stu-id="95796-118">Both local and network pipes establish a connection with an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the standard pipe (\\\\.\pipe\sql\query), unless otherwise directed.</span></span>  
  
 <span data-ttu-id="95796-119">サーバー名を指定せずにローカル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続しているときは、ローカル パイプを使用していることになります。</span><span class="sxs-lookup"><span data-stu-id="95796-119">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without specifying a server name, you are using a local pipe.</span></span> <span data-ttu-id="95796-120">ローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、明示的にサーバー名を指定しているときは、ネットワーク パイプまたは IPX/SPX (Internetwork Packet Exchange/Sequenced Packet Exchange) などの別のネットワーク プロセス間通信 (IPC) メカニズムを使用していることになります (複数のネットワークを使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を構成している場合)。</span><span class="sxs-lookup"><span data-stu-id="95796-120">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and specify a server name explicitly, you are using either a network pipe or another network interprocess communication (IPC) mechanism, such as Internetwork Packet Exchange/Sequenced Packet Exchange (IPX/SPX) (assuming you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use multiple networks).</span></span> <span data-ttu-id="95796-121">スタンドアロンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではネットワーク パイプがサポートされないので、クライアントから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するときに、不要な **/** _Server_name>_ 引数を省略する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95796-121">Because a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support network pipes, you must omit the unnecessary **/**_<Server_name>_ argument when connecting to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client.</span></span> <span data-ttu-id="95796-122">たとえば、 **osql** から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロンのインスタンスに接続するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="95796-122">For example, to connect to a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from **osql**, type:</span></span>  
  
 <span data-ttu-id="95796-123">**osql /Usa /P** _\<saPassword>_</span><span class="sxs-lookup"><span data-stu-id="95796-123">**osql /Usa /P** _\<saPassword>_</span></span>  
  
  
