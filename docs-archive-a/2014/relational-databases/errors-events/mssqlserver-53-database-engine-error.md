---
title: MSSQLSERVER_53 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "53"
helpviewer_keywords:
- 53 (Database Engine error)
ms.assetid: 1234f5a2-b3d1-425a-b29f-480fa792305f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 85fda292fb956047f51b9c7cd1d229ac0afce6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641691"
---
# <a name="mssqlserver_53"></a><span data-ttu-id="8ffdf-102">MSSQLSERVER_53</span><span class="sxs-lookup"><span data-stu-id="8ffdf-102">MSSQLSERVER_53</span></span>
    
## <a name="details"></a><span data-ttu-id="8ffdf-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8ffdf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ffdf-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8ffdf-104">Product Name</span></span>|<span data-ttu-id="8ffdf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ffdf-105">SQL Server</span></span>|  
|<span data-ttu-id="8ffdf-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8ffdf-106">Event ID</span></span>|<span data-ttu-id="8ffdf-107">53</span><span class="sxs-lookup"><span data-stu-id="8ffdf-107">53</span></span>|  
|<span data-ttu-id="8ffdf-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8ffdf-108">Event Source</span></span>|<span data-ttu-id="8ffdf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8ffdf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8ffdf-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8ffdf-110">Component</span></span>|<span data-ttu-id="8ffdf-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8ffdf-111">SQLEngine</span></span>|  
|<span data-ttu-id="8ffdf-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8ffdf-112">Symbolic Name</span></span>||  
|<span data-ttu-id="8ffdf-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8ffdf-113">Message Text</span></span>|<span data-ttu-id="8ffdf-114">サーバーへの接続を確立中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8ffdf-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="8ffdf-115">SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8ffdf-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="8ffdf-116">(プロバイダー:名前付きパイプ プロバイダー、エラー:40 - SQL Server への接続を開けませんでした) (.Net SqlClient Data Provider)</span><span class="sxs-lookup"><span data-stu-id="8ffdf-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8ffdf-117">説明</span><span class="sxs-lookup"><span data-stu-id="8ffdf-117">Explanation</span></span>  
 <span data-ttu-id="8ffdf-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="8ffdf-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="8ffdf-119">このエラーは、クライアントがサーバー名を解決できないか、サーバー名が間違っていることが原因で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8ffdf-119">This error could occur because either the client cannot resolve the name of the server or the name of the server is incorrect.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8ffdf-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8ffdf-120">User Action</span></span>  
 <span data-ttu-id="8ffdf-121">クライアントで入力したサーバー名に間違いがなく、そのサーバー名を解決できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ffdf-121">Make sure that you have entered the correct server name on the client, and that you can resolve the name of the server from the client.</span></span> <span data-ttu-id="8ffdf-122">TCP/IP 名前解決を確認するには、Windows オペレーティング システムで **ping** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ffdf-122">To check TCP/IP name resolution, you can use the **ping** command in the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffdf-123">参照</span><span class="sxs-lookup"><span data-stu-id="8ffdf-123">See Also</span></span>  
 <span data-ttu-id="8ffdf-124">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="8ffdf-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="8ffdf-125">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="8ffdf-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="8ffdf-126">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="8ffdf-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="8ffdf-127">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="8ffdf-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
