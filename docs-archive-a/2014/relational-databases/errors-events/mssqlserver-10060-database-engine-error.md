---
title: MSSQLSERVER_10060 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d634cfb06381fb916ef2e421e0677e76edb9ae02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738454"
---
# <a name="mssqlserver_10060"></a><span data-ttu-id="43082-102">MSSQLSERVER_10060</span><span class="sxs-lookup"><span data-stu-id="43082-102">MSSQLSERVER_10060</span></span>
    
## <a name="details"></a><span data-ttu-id="43082-103">詳細</span><span class="sxs-lookup"><span data-stu-id="43082-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43082-104">製品名</span><span class="sxs-lookup"><span data-stu-id="43082-104">Product Name</span></span>|<span data-ttu-id="43082-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="43082-105">SQL Server</span></span>|  
|<span data-ttu-id="43082-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43082-106">Event ID</span></span>|<span data-ttu-id="43082-107">10060</span><span class="sxs-lookup"><span data-stu-id="43082-107">10060</span></span>|  
|<span data-ttu-id="43082-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="43082-108">Event Source</span></span>|<span data-ttu-id="43082-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="43082-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="43082-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="43082-110">Component</span></span>|<span data-ttu-id="43082-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="43082-111">SQLEngine</span></span>|  
|<span data-ttu-id="43082-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="43082-112">Symbolic Name</span></span>||  
|<span data-ttu-id="43082-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="43082-113">Message Text</span></span>|<span data-ttu-id="43082-114">サーバーへの接続を確立中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="43082-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="43082-115">SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43082-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="43082-116">(プロバイダー:TCP プロバイダー、エラー:0 - 接続済みの呼び出し先が一定の時間を過ぎても正しく応答しなかったため、接続できませんでした。または接続済みのホストが応答しなかったため、確立された接続は失敗しました。) (Microsoft SQL Server、エラー:10060)</span><span class="sxs-lookup"><span data-stu-id="43082-116">(provider: TCP Provider, error: 0 - A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.) (Microsoft SQL Server, Error: 10060)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="43082-117">説明</span><span class="sxs-lookup"><span data-stu-id="43082-117">Explanation</span></span>  
 <span data-ttu-id="43082-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="43082-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="43082-119">このエラーは、サーバーのファイアウォールで接続が拒否されたか、サーバーがリモート接続を許可するように構成されていないことが原因で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="43082-119">This error could occur because either the firewall on the server has refused the connection or the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="43082-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="43082-120">User Action</span></span>  
 <span data-ttu-id="43082-121">このエラーを解決するには、以下のいずれかの操作を試してみます。</span><span class="sxs-lookup"><span data-stu-id="43082-121">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="43082-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのインスタンスで、接続を許可するようにファイアウォールを構成していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="43082-122">Make sure that you have configured the firewall on the computer to allow this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
-   <span data-ttu-id="43082-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー ツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリモート接続を許可できるようにします。</span><span class="sxs-lookup"><span data-stu-id="43082-123">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43082-124">参照</span><span class="sxs-lookup"><span data-stu-id="43082-124">See Also</span></span>  
 <span data-ttu-id="43082-125">[データベースエンジンアクセスできるように Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="43082-125">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="43082-126">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="43082-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="43082-127">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="43082-127">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="43082-128">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="43082-128">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="43082-129">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="43082-129">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="43082-130">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="43082-130">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
