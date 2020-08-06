---
title: Banyan VINES Packet Protocol (SPP)、マルチプロトコル、AppleTalk、または NWLink IPX SPX ネットワークプロトコルを使用する接続を変更します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 750b9c0b76ab6c3b43908ecb8454f31ac1a25b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740694"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a><span data-ttu-id="49610-102">Banyan VINES Sequenced Packet Protocol (SPP)、Multiprotocol、AppleTalk、または NWLink IPX/SPX ネットワーク プロトコルを使用する接続を変更する</span><span class="sxs-lookup"><span data-stu-id="49610-102">Modify connections that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX SPX network protocols</span></span>
  <span data-ttu-id="49610-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされていないクライアント サーバー接続プロトコルをアップグレード アドバイザーが検出しました。</span><span class="sxs-lookup"><span data-stu-id="49610-103">The Upgrade Advisor has detected client server connectivity protocols that are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="49610-104">Banyan VINES Sequenced Packet Protocol (SPP)、Multiprotocol (RPC)、AppleTalk、または NWLink IPX/SPX ネットワーク プロトコルを使用するクライアント接続は、サポート対象のプロトコルを使用して接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49610-104">Client applications that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk, or NWLink IPX/SPX network protocols must connect using a supported protocol.</span></span>  
  
## <a name="component"></a><span data-ttu-id="49610-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="49610-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="49610-106">説明</span><span class="sxs-lookup"><span data-stu-id="49610-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="49610-107">では、Banyan VINES Sequenced Packet Protocol (SPP)、Multiprotocol、AppleTalk、または NWLink IPX/SPX ネットワーク プロトコルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="49610-107">does not support the Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX/SPX network protocols.</span></span> <span data-ttu-id="49610-108">以前にこれらのプロトコルを使用して接続していたクライアントの場合、別のプロトコルを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49610-108">Clients previously connecting with these protocols must select a different protocol.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="49610-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="49610-109">Corrective Action</span></span>  
 <span data-ttu-id="49610-110">サポートされているプロトコルを使用してサーバーに接続するように、クライアント アプリケーションを変更します。</span><span class="sxs-lookup"><span data-stu-id="49610-110">Change the client applications to use a supported protocol when connecting to the server.</span></span> <span data-ttu-id="49610-111">サポートされていないプロトコルを使用するように別名を設定している場合は、サポートされるいずれかのプロトコルを使用するように別名を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49610-111">If you have an alias setup that uses one of the unsupported protocols then the alias must be modified to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="49610-112">アプリケーションの接続文字列が、これらのプロトコルのいずれかを明示的に使用または読み込む場合は、NETWORK = DBMSRPCN を RPC に指定します。 NETWORK = DBMSADSN for Appletalk、または NETWORK = DBMSVINN for Banyan VINES プロパティ、または「SPX:*server\instance*」 (bv vines の場合)、「Banyan:*Server*」 (VINES の場合)、「adsp: server」 (マルチプロトコルの場合)、「adsp:*server\*\*」 (* マルチプロトコルの場合) のいずれかを使用するようにアプリケーションを変更する必要</span><span class="sxs-lookup"><span data-stu-id="49610-112">If your application connection string specifically uses or loads one of these protocols, by either specifying NETWORK=DBMSRPCN for RPC, NETWORK=DBMSADSN for Appletalk, or NETWORK=DBMSVINN for Banyan VINES property, or by using an explicit prefix such as "spx:*server\instance*" for SPX, "bv:*server*" for Banyan VINES, "adsp:*server*" for AppleTalk, or "rpc:*server*" for multiprotocol, then you must modify your application to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="49610-113">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ネットワーク プロトコルの選択」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49610-113">For more information, see "Choosing a Network Protocol" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49610-114">参照</span><span class="sxs-lookup"><span data-stu-id="49610-114">See Also</span></span>  
 <span data-ttu-id="49610-115">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="49610-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="49610-116">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="49610-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
