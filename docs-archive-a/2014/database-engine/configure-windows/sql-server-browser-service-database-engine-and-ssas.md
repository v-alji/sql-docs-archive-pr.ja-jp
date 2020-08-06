---
title: SQL Server Browser サービス (データベース エンジンと SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- services [SQL Server], security
- SQL Browser service (See SQL Server Browser service)
- Browser Service
- SQL Server Browser service
ms.assetid: 5c236ddc-766d-4a30-af1e-cc6176eca690
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b17b253ff3601b38783d81d56c0f803032cc11bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633297"
---
# <a name="sql-server-browser-service-database-engine-and-ssas"></a><span data-ttu-id="c0e5b-102">SQL Server Browser サービス (データベース エンジンと SSAS)</span><span class="sxs-lookup"><span data-stu-id="c0e5b-102">SQL Server Browser Service (Database Engine and SSAS)</span></span>
  <span data-ttu-id="c0e5b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser プログラムは Windows サービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser program runs as a Windows service.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-104">Browser では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種リソースに関する着信要求を受信し、このコンピューター上にインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-105">Browser は次の操作に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-105">Browser contributes to the following actions:</span></span>  
  
-   <span data-ttu-id="c0e5b-106">使用可能なサーバーの一覧の参照</span><span class="sxs-lookup"><span data-stu-id="c0e5b-106">Browsing a list of available servers</span></span>  
  
-   <span data-ttu-id="c0e5b-107">適切なサーバー インスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="c0e5b-107">Connecting to the correct server instance</span></span>  
  
-   <span data-ttu-id="c0e5b-108">専用管理者接続 (DAC) のエンドポイントへの接続</span><span class="sxs-lookup"><span data-stu-id="c0e5b-108">Connecting to dedicated administrator connection (DAC) endpoints</span></span>  
  
 <span data-ttu-id="c0e5b-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] Browser サービス (sqlbrowser) は、 [!INCLUDE[ssAS](../../includes/ssas-md.md)]と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスに対してインスタンス名とバージョン番号を提供します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-109">For each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssAS](../../includes/ssas-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service (sqlbrowser) provides the instance name and the version number.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-110">Browser は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-110">Browser is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-111">Browser は、セットアップ時に、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-111">Browser can be configured during setup or by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c0e5b-112">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは次の場合に自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-112">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service starts automatically:</span></span>  
  
-   <span data-ttu-id="c0e5b-113">インストールをアップグレードする場合</span><span class="sxs-lookup"><span data-stu-id="c0e5b-113">When upgrading an installation.</span></span>  
  
-   <span data-ttu-id="c0e5b-114">クラスターにインストールする場合</span><span class="sxs-lookup"><span data-stu-id="c0e5b-114">When installing on a cluster.</span></span>  
  
-   <span data-ttu-id="c0e5b-115">SQL Server Express のすべてのインスタンスを含む、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の名前付きインスタンスをインストールする場合</span><span class="sxs-lookup"><span data-stu-id="c0e5b-115">When installing a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] including all instances of SQL Server Express.</span></span>  
  
-   <span data-ttu-id="c0e5b-116">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の名前付きインスタンスをインストールする場合</span><span class="sxs-lookup"><span data-stu-id="c0e5b-116">When installing a named instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="background"></a><span data-ttu-id="c0e5b-117">バックグラウンド</span><span class="sxs-lookup"><span data-stu-id="c0e5b-117">Background</span></span>  
 <span data-ttu-id="c0e5b-118">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]より前は、コンピューターにインストールできる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスは 1 つだけでした。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-118">Prior to [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], only one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could be installed on a computer.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-119">は、公式の Internet Assigned Numbers Authority (IANA) によって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に割り当てられたポート 1433 で着信要求を待ちます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-119">listened for incoming requests on port 1433, assigned to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by the official Internet Assigned Numbers Authority (IANA).</span></span> <span data-ttu-id="c0e5b-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスしかポートを使用できないので、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の複数のインスタンスをサポートするようになったとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) が開発され、UDP ポート 1434 で受信待ちするようになりました。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-120">Only one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use a port, so when [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] introduced support for multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) was developed to listen on UDP port 1434.</span></span> <span data-ttu-id="c0e5b-121">このリスナー サービスは、インストールされているインスタンスの名前と、そのインスタンスが使用しているポートまたは名前付きパイプでクライアント要求に応答していました。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-121">This listener service responded to client requests with the names of the installed instances, and the ports or named pipes used by the instance.</span></span> <span data-ttu-id="c0e5b-122">SSRP システムの制限を解消するため、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では SSRP の代わりに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを導入しています。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-122">To resolve limitations of the SSRP system, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] introduced the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service as a replacement for SSRP.</span></span>  
  
## <a name="how-sql-server-browser-works"></a><span data-ttu-id="c0e5b-123">SQL Server Browser のしくみ</span><span class="sxs-lookup"><span data-stu-id="c0e5b-123">How SQL Server Browser Works</span></span>  
 <span data-ttu-id="c0e5b-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対して TCP/IP プロトコルが有効な場合は、サーバーに TCP/IP ポートが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-124">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts, if the TCP/IP protocol is enabled for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the server is assigned a TCP/IP port.</span></span> <span data-ttu-id="c0e5b-125">名前付きパイプのプロトコルが有効な場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は特定の名前付きパイプでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-125">If the named pipes protocol is enabled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on a specific named pipe.</span></span> <span data-ttu-id="c0e5b-126">クライアント アプリケーションとのデータの交換には、このポート、つまり "パイプ" がそのインスタンスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-126">This port, or "pipe," is used by that specific instance to exchange data with client applications.</span></span> <span data-ttu-id="c0e5b-127">インストール中、TCP ポート 1433 とパイプ `\sql\query` が既定のインスタンスに割り当てられますが、これは後でサーバー管理者が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-127">During installation, TCP port 1433 and pipe `\sql\query` are assigned to the default instance, but those can be changed later by the server administrator using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c0e5b-128">ポートまたはパイプを使用できるのは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスだけなので、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を含めて、名前付きインスタンスには別のポート番号とパイプ名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-128">Because only one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use a port or pipe, different port numbers and pipe names are assigned for named instances, including [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="c0e5b-129">既定では、名前付きインスタンスと [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] が有効な場合、両方とも動的ポートを使用するように設定されています。つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時に使用可能なポートが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-129">By default, when enabled, both named instances and [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] are configured to use dynamic ports, that is, an available port is assigned when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="c0e5b-130">必要であれば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに特定のポートを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-130">If you want, a specific port can be assigned to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c0e5b-131">クライアントは接続時に特定のポートを指定できますが、ポートが動的に割り当てられる場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再起動されるたびにポート番号が変わる可能性があるので、クライアントは正しいポート番号を特定できません。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-131">When connecting, clients can specify a specific port; but if the port is dynamically assigned, the port number can change anytime [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted, so the correct port number is unknown to the client.</span></span>  
  
 <span data-ttu-id="c0e5b-132">起動時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser が開始されて UDP ポート 1434 が要求されます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-132">Upon startup, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser starts and claims UDP port 1434.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-133">Browser はレジストリを読み取って、コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインスタンスを識別し、使用されているポートと名前付きパイプを確認します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-133">Browser reads the registry, identifies all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer, and notes the ports and named pipes that they use.</span></span> <span data-ttu-id="c0e5b-134">サーバーに複数のネットワーク カードがある場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser が最初に検出したポートを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に返します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-134">When a server has two or more network cards, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser returns the first enabled port it encounters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-135">Browser では ipv6 と ipv4 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-135">Browser support ipv6 and ipv4.</span></span>  
  
 <span data-ttu-id="c0e5b-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースを要求すると、ポート 1434 を使用しているサーバーにクライアント ネットワーク ライブラリが UDP メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-136">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients request [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources, the client network library sends a UDP message to the server using port 1434.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-137">Browser は、要求されたインスタンスの TCP/IP ポートまたは名前付きパイプで応答します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-137">Browser responds with the TCP/IP port or named pipe of the requested instance.</span></span> <span data-ttu-id="c0e5b-138">その後、クライアント アプリケーションのネットワーク ライブラリが、目的のインスタンスのポートまたは名前付きパイプを使用しているサーバーに要求を送って接続を完了します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-138">The network library on the client application then completes the connection by sending a request to the server using the port or named pipe of the desired instance.</span></span> <span data-ttu-id="c0e5b-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser では既定のインスタンスのポート情報は返されません。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser does not return port information for the default instance.</span></span>  
  
 <span data-ttu-id="c0e5b-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスの開始と停止の詳細については、「 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](start-stop-pause-resume-restart-sql-server-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-140">For information about starting and stopping the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
## <a name="using-sql-server-browser"></a><span data-ttu-id="c0e5b-141">SQL Server Browser の使用</span><span class="sxs-lookup"><span data-stu-id="c0e5b-141">Using SQL Server Browser</span></span>  
 <span data-ttu-id="c0e5b-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合でも、正しいポート番号か名前付きパイプを指定すれば [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続できます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-142">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is not running, you are still able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if you provide the correct port number or named pipe.</span></span> <span data-ttu-id="c0e5b-143">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスがポート 1433 で実行されている場合は、TCP/IP を使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-143">For instance, you can connect to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with TCP/IP if it is running on port 1433.</span></span>  
  
 <span data-ttu-id="c0e5b-144">ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合は、次の接続が機能しません。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-144">However, if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is not running, the following connections do not work:</span></span>  
  
-   <span data-ttu-id="c0e5b-145">パラメーター (たとえば TCP/IP ポートや名前付きパイプ) を完全に指定せずに名前付きインスタンスに接続しようとするコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-145">Any component that tries to connect to a named instance without fully specifying all the parameters (such as the TCP/IP port or named pipe).</span></span>  
  
-   <span data-ttu-id="c0e5b-146">後で他のコンポーネントが再接続に使用する可能性のあるサーバーまたはインスタンス情報を生成するかまたは渡すコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-146">Any component that generates or passes server\instance information that could later be used by other components to reconnect.</span></span>  
  
-   <span data-ttu-id="c0e5b-147">ポート番号やパイプを指定せずに名前付きインスタンスに接続する。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-147">Connecting to a named instance without providing the port number or pipe.</span></span>  
  
-   <span data-ttu-id="c0e5b-148">TCP/IP ポート 1433 を使用していない場合は、名前付きインスタンスや既定のインスタンスへの DAC。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-148">DAC to a named instance or the default instance if not using TCP/IP port 1433.</span></span>  
  
-   <span data-ttu-id="c0e5b-149">OLAP リダイレクター サービス。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-149">The OLAP redirector service.</span></span>  
  
-   <span data-ttu-id="c0e5b-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、Enterprise Manager、またはクエリ アナライザーでのサーバーの列挙。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-150">Enumerating servers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Enterprise Manager, or Query Analyzer.</span></span>  
  
 <span data-ttu-id="c0e5b-151">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をクライアント/サーバーのシナリオで使用している場合 (たとえば、アプリケーションがネットワーク経由で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアクセスしている場合)、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを停止または無効化するには、各インスタンスに特定のポート番号を割り当て、常にそのポート番号が使用されるようにクライアント アプリケーションのコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-151">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a client-server scenario (for example, when your application is accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] across a network), if you stop or disable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service, you must assign a specific port number to each instance and write your client application code to always use that port number.</span></span> <span data-ttu-id="c0e5b-152">この方法には次の問題があります。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-152">This approach has the following problems:</span></span>  
  
-   <span data-ttu-id="c0e5b-153">クライアント アプリケーションが必ず適切なポートに接続するように、コードを更新および管理しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-153">You must update and maintain client application code to ensure it is connecting to the proper port.</span></span>  
  
-   <span data-ttu-id="c0e5b-154">各インスタンスに対して選択したポートがサーバー上の別のサービスまたはアプリケーションによって使用されている場合があります。この場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-154">The port you choose for each instance may be used by another service or application on the server, causing the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be unavailable.</span></span>  
  
## <a name="clustering"></a><span data-ttu-id="c0e5b-155">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="c0e5b-155">Clustering</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-156">Browser はクラスター化されたリソースではなく、クラスター ノード間のフェールオーバーはサポートしません。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-156">Browser is not a clustered resource and does not support failover from one cluster node to the other.</span></span> <span data-ttu-id="c0e5b-157">そのため、クラスターの場合は、クラスターのノードごとに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser をインストールして有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-157">Therefore, in the case of a cluster, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser should be installed and turned on for each node of the cluster.</span></span> <span data-ttu-id="c0e5b-158">クラスターでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser は IP_ANY で受信待ちします。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-158">On clusters, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser listens on IP_ANY.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0e5b-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser では最初に検出された IP とポートのペアが返されるため、IP_ANY で受信待ちのときに特定の IP での受信待ちを有効にする場合は、各 IP に同じ TCP ポートを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-159">When listening on IP_ANY, when you enable listening on specific IPs, the user must configure the same TCP port on each IP, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser returns the first IP/port pair that it encounters.</span></span>  
  
## <a name="installing-uninstalling-and-running-from-the-command-line"></a><span data-ttu-id="c0e5b-160">コマンド ラインからのインストール、アンインストール、実行</span><span class="sxs-lookup"><span data-stu-id="c0e5b-160">Installing, Uninstalling, and Running from the Command Line</span></span>  
 <span data-ttu-id="c0e5b-161">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser プログラムは C:\Program Files (x86)\Microsoft SQL Server\90\Shared\sqlbrowser.exe にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-161">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program is installed at C:\Program Files (x86)\Microsoft SQL Server\90\Shared\sqlbrowser.exe.</span></span>  
  
 <span data-ttu-id="c0e5b-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最後のインスタンスを削除すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-162">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is uninstalled when the last instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is removed.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-163">Browser は、トラブルシューティングの目的で、コマンド プロンプトから **-c** スイッチを使用して起動できます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-163">Browser can be started from the command prompt for troubleshooting, by using the **-c** switch:</span></span>  
  
```  
<drive>\<path>\sqlbrowser.exe -c  
```  
  
## <a name="security"></a><span data-ttu-id="c0e5b-164">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c0e5b-164">Security</span></span>  
  
### <a name="account-privileges"></a><span data-ttu-id="c0e5b-165">アカウントの権限</span><span class="sxs-lookup"><span data-stu-id="c0e5b-165">Account Privileges</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-166">Browser は UDP ポートで受信待ちし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) を使用して、認証されていない要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-166">Browser listens on a UDP port and accepts unauthenticated requests by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e5b-167">Browser を権限が制限されているユーザーのセキュリティ コンテキストで実行することにより、悪意のある攻撃にさらされる危険性を最小限に抑える必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-167">Browser should be run in the security context of a low privileged user to minimize exposure to a malicious attack.</span></span> <span data-ttu-id="c0e5b-168">ログオン アカウントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-168">The logon account can be changed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c0e5b-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser の最小限のユーザー権限は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-169">The minimum user rights for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser are the following:</span></span>  
  
-   <span data-ttu-id="c0e5b-170">ネットワークからこのコンピューターへのアクセスを拒否</span><span class="sxs-lookup"><span data-stu-id="c0e5b-170">Deny access to this computer from the network</span></span>  
  
-   <span data-ttu-id="c0e5b-171">ローカルでのログオンを拒否</span><span class="sxs-lookup"><span data-stu-id="c0e5b-171">Deny logon locally</span></span>  
  
-   <span data-ttu-id="c0e5b-172">バッチ ジョブとしてのログオンを拒否</span><span class="sxs-lookup"><span data-stu-id="c0e5b-172">Deny Log on as a batch job</span></span>  
  
-   <span data-ttu-id="c0e5b-173">ターミナル サービス経由のログオンを拒否</span><span class="sxs-lookup"><span data-stu-id="c0e5b-173">Deny Log On Through Terminal Services</span></span>  
  
-   <span data-ttu-id="c0e5b-174">サービスとしてログオン</span><span class="sxs-lookup"><span data-stu-id="c0e5b-174">Log on as a service</span></span>  
  
-   <span data-ttu-id="c0e5b-175">ネットワーク通信に関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レジストリ キーの読み取りおよび書き込み (ポートおよびパイプ)</span><span class="sxs-lookup"><span data-stu-id="c0e5b-175">Read and write the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registry keys related to network communication (ports and pipes)</span></span>  
  
### <a name="default-account"></a><span data-ttu-id="c0e5b-176">既定のアカウント</span><span class="sxs-lookup"><span data-stu-id="c0e5b-176">Default Account</span></span>  
 <span data-ttu-id="c0e5b-177">セットアップ プログラムは、セットアップ中にサービス用に選択したアカウントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser が使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-177">Setup configures [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser to use the account selected for services during setup.</span></span> <span data-ttu-id="c0e5b-178">他に可能なアカウントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-178">Other possible accounts include the following:</span></span>  
  
-   <span data-ttu-id="c0e5b-179">すべての **domain\local** アカウント</span><span class="sxs-lookup"><span data-stu-id="c0e5b-179">Any **domain\local** account</span></span>  
  
-   <span data-ttu-id="c0e5b-180">**ローカル サービス** アカウント</span><span class="sxs-lookup"><span data-stu-id="c0e5b-180">The **local service** account</span></span>  
  
-   <span data-ttu-id="c0e5b-181">**ローカル システム** アカウント (不要な権限があるので推奨しません)</span><span class="sxs-lookup"><span data-stu-id="c0e5b-181">The **local system** account (not recommended as has unnecessary privileges)</span></span>  
  
### <a name="hiding-sql-server"></a><span data-ttu-id="c0e5b-182">SQL Server の非表示</span><span class="sxs-lookup"><span data-stu-id="c0e5b-182">Hiding SQL Server</span></span>  
 <span data-ttu-id="c0e5b-183">非表示インスタンスは、共有メモリ接続のみをサポートする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-183">Hidden instances are instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support only shared memory connections.</span></span> <span data-ttu-id="c0e5b-184">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の場合は、 `HideInstance` Browser がこのサーバー インスタンスに関する情報を返さないことを示すために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-184">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], set the `HideInstance` flag to indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser should not respond with information about this server instance.</span></span>  
  
### <a name="using-a-firewall"></a><span data-ttu-id="c0e5b-185">ファイアウォールの使用</span><span class="sxs-lookup"><span data-stu-id="c0e5b-185">Using a Firewall</span></span>  
 <span data-ttu-id="c0e5b-186">ファイアウォールの背後にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスと通信するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用される TCP ポート (1433 など) のほかに UDP ポート 1434 も開きます。</span><span class="sxs-lookup"><span data-stu-id="c0e5b-186">To communicate with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on a server behind a firewall, open UDP port 1434, in addition to the TCP port used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (e.g., 1433).</span></span> <span data-ttu-id="c0e5b-187">ファイアウォールの使用方法については、次をご覧ください。「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアクセス用にファイアウォールを構成する」([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブック)</span><span class="sxs-lookup"><span data-stu-id="c0e5b-187">For information about working with a firewall, see "How to: Configure a Firewall for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e5b-188">参照</span><span class="sxs-lookup"><span data-stu-id="c0e5b-188">See Also</span></span>  
 [<span data-ttu-id="c0e5b-189">ネットワーク プロトコルとネットワーク ライブラリ</span><span class="sxs-lookup"><span data-stu-id="c0e5b-189">Network Protocols and Network Libraries</span></span>](../../sql-server/install/network-protocols-and-network-libraries.md)  
  
  