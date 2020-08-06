---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 880212b1d2e9572bbb31535a5ba68b445c7e6f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719965"
---
# <a name="mssqlserver_-1"></a><span data-ttu-id="13592-102">MSSQLSERVER_-1</span><span class="sxs-lookup"><span data-stu-id="13592-102">MSSQLSERVER_-1</span></span>
    
## <a name="details"></a><span data-ttu-id="13592-103">詳細</span><span class="sxs-lookup"><span data-stu-id="13592-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13592-104">製品名</span><span class="sxs-lookup"><span data-stu-id="13592-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="13592-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13592-105">Event ID</span></span>|<span data-ttu-id="13592-106">-1</span><span class="sxs-lookup"><span data-stu-id="13592-106">-1</span></span>|  
|<span data-ttu-id="13592-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="13592-107">Event Source</span></span>|<span data-ttu-id="13592-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="13592-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="13592-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="13592-109">Component</span></span>|<span data-ttu-id="13592-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="13592-110">SQLEngine</span></span>|  
|<span data-ttu-id="13592-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="13592-111">Symbolic Name</span></span>||  
|<span data-ttu-id="13592-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="13592-112">Message Text</span></span>|<span data-ttu-id="13592-113">サーバーへの接続を確立中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="13592-113">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="13592-114">接続先が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] である場合、既定の設定では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリモート接続を許可していないために、このエラーが発生した可能性があります</span><span class="sxs-lookup"><span data-stu-id="13592-114">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this failure may be caused by the fact that under the default settings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow remote connections.</span></span> <span data-ttu-id="13592-115">(プロバイダー:SQL Network Interfaces、エラー:28 - サーバーは要求されたプロトコルをサポートしていません) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、エラー: -1)。</span><span class="sxs-lookup"><span data-stu-id="13592-115">(provider: SQL Network Interfaces, error: 28 - Server doesn't support requested protocol) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Error: -1)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="13592-116">説明</span><span class="sxs-lookup"><span data-stu-id="13592-116">Explanation</span></span>  
 <span data-ttu-id="13592-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="13592-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="13592-118">このエラーは、次のいずれかの原因により起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13592-118">This error could be caused by one of the following reasons:</span></span>  
  
-   <span data-ttu-id="13592-119">指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="13592-119">A specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name is not valid.</span></span>  
  
-   <span data-ttu-id="13592-120">TCP または名前付きパイプ プロトコルが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="13592-120">The TCP, or named pipes protocols are not enabled.</span></span>  
  
-   <span data-ttu-id="13592-121">サーバー上のファイアウォールで接続が拒否されました。</span><span class="sxs-lookup"><span data-stu-id="13592-121">The firewall on the server has refused the connection.</span></span>  
  
-   <span data-ttu-id="13592-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービス (sqlbrowser) が開始されていません。</span><span class="sxs-lookup"><span data-stu-id="13592-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service (sqlbrowser) is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="13592-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="13592-123">User Action</span></span>  
 <span data-ttu-id="13592-124">このエラーを解決するには、以下のいずれかの操作を試してみます。</span><span class="sxs-lookup"><span data-stu-id="13592-124">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="13592-125">接続文字列で指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="13592-125">Check the spelling of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name that is specified in the connection string.</span></span>  
  
-   <span data-ttu-id="13592-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー ツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が TCP や名前付きパイプのプロトコルを経由したリモート接続を受け入れられるようにします。</span><span class="sxs-lookup"><span data-stu-id="13592-126">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections over the TCP or named pipes protocols.</span></span>  
  
-   <span data-ttu-id="13592-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバー インスタンスで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のポートおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ポート (UDP 1434) を開くようにファイアウォールを構成していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13592-127">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open ports for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser port (UDP 1434).</span></span>  
  
-   <span data-ttu-id="13592-128">サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13592-128">Make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is started on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13592-129">参照</span><span class="sxs-lookup"><span data-stu-id="13592-129">See Also</span></span>  
 <span data-ttu-id="13592-130">[データベースエンジンアクセスできるように Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="13592-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="13592-131">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="13592-131">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="13592-132">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="13592-132">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="13592-133">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="13592-133">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="13592-134">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="13592-134">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="13592-135">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="13592-135">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
