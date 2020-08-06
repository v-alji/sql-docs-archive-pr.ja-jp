---
title: MSSQLSERVER_11001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "12001"
helpviewer_keywords:
- 11001 (Database Engine error)
ms.assetid: 53d4d63a-61e3-441f-bfe9-9d44f7a05fd4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da7dd171d1b6a64e0cc1666eda1e3593a81eece1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643931"
---
# <a name="mssqlserver_11001"></a><span data-ttu-id="d3e26-102">MSSQLSERVER_11001</span><span class="sxs-lookup"><span data-stu-id="d3e26-102">MSSQLSERVER_11001</span></span>
    
## <a name="details"></a><span data-ttu-id="d3e26-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d3e26-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3e26-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d3e26-104">Product Name</span></span>|<span data-ttu-id="d3e26-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d3e26-105">SQL Server</span></span>|  
|<span data-ttu-id="d3e26-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d3e26-106">Event ID</span></span>|<span data-ttu-id="d3e26-107">11001</span><span class="sxs-lookup"><span data-stu-id="d3e26-107">11001</span></span>|  
|<span data-ttu-id="d3e26-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d3e26-108">Event Source</span></span>|<span data-ttu-id="d3e26-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d3e26-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d3e26-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d3e26-110">Component</span></span>|<span data-ttu-id="d3e26-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d3e26-111">SQLEngine</span></span>|  
|<span data-ttu-id="d3e26-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d3e26-112">Symbolic Name</span></span>||  
|<span data-ttu-id="d3e26-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d3e26-113">Message Text</span></span>|<span data-ttu-id="d3e26-114">サーバーへの接続を確立中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d3e26-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="d3e26-115">SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d3e26-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="d3e26-116">(プロバイダー:TCP プロバイダー、エラー:0 - そのようなホストは不明です。) (.Net SqlClient Data Provider)</span><span class="sxs-lookup"><span data-stu-id="d3e26-116">(provider: TCP Provider, error: 0 - No such host is known.) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d3e26-117">説明</span><span class="sxs-lookup"><span data-stu-id="d3e26-117">Explanation</span></span>  
 <span data-ttu-id="d3e26-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="d3e26-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="d3e26-119">このエラーは、クライアントがサーバー名を解決できないか、サーバー名が間違っていることが原因で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d3e26-119">The error could occur because either the client cannot resolve the name of the server or the name of the server is incorrect.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d3e26-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d3e26-120">User Action</span></span>  
 <span data-ttu-id="d3e26-121">クライアントで入力したサーバー名に間違いがなく、そのサーバー名を解決できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3e26-121">Make sure that you have entered the correct server name on the client, and that you can resolve the name of the server from the client.</span></span> <span data-ttu-id="d3e26-122">TCP/IP 名前解決を確認するには、Windows オペレーティング システムで **ping** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3e26-122">To check TCP/IP name resolution, you can use the **ping** command in the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e26-123">参照</span><span class="sxs-lookup"><span data-stu-id="d3e26-123">See Also</span></span>  
 <span data-ttu-id="d3e26-124">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="d3e26-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="d3e26-125">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d3e26-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="d3e26-126">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="d3e26-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="d3e26-127">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="d3e26-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
