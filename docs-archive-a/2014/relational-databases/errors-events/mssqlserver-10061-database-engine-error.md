---
title: MSSQLSERVER_10061 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c866bd8dce01f65036f1d508a94252a97613424
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719958"
---
# <a name="mssqlserver_10061"></a><span data-ttu-id="03ddd-102">MSSQLSERVER_10061</span><span class="sxs-lookup"><span data-stu-id="03ddd-102">MSSQLSERVER_10061</span></span>
    
## <a name="details"></a><span data-ttu-id="03ddd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="03ddd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03ddd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="03ddd-104">Product Name</span></span>|<span data-ttu-id="03ddd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="03ddd-105">SQL Server</span></span>|  
|<span data-ttu-id="03ddd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="03ddd-106">Event ID</span></span>|<span data-ttu-id="03ddd-107">10061</span><span class="sxs-lookup"><span data-stu-id="03ddd-107">10061</span></span>|  
|<span data-ttu-id="03ddd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="03ddd-108">Event Source</span></span>|<span data-ttu-id="03ddd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="03ddd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="03ddd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="03ddd-110">Component</span></span>|<span data-ttu-id="03ddd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="03ddd-111">SQLEngine</span></span>|  
|<span data-ttu-id="03ddd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="03ddd-112">Symbolic Name</span></span>||  
|<span data-ttu-id="03ddd-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="03ddd-113">Message Text</span></span>|<span data-ttu-id="03ddd-114">サーバーへの接続を確立中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="03ddd-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="03ddd-115">SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="03ddd-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="03ddd-116">(プロバイダー:TCP プロバイダー、エラー:0 - 対象のコンピューターによって拒否されたため、接続できませんでした。) (Microsoft SQL Server、エラー:10061)</span><span class="sxs-lookup"><span data-stu-id="03ddd-116">(provider: TCP Provider, error: 0 - No connection could be made because the target machine actively refused it.) (Microsoft SQL Server, Error: 10061)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="03ddd-117">説明</span><span class="sxs-lookup"><span data-stu-id="03ddd-117">Explanation</span></span>  
 <span data-ttu-id="03ddd-118">サーバーがクライアント要求に応答しませんでした。</span><span class="sxs-lookup"><span data-stu-id="03ddd-118">The server did not respond to the client request.</span></span> <span data-ttu-id="03ddd-119">このエラーは、サーバーが起動していないことが原因で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="03ddd-119">This error could occur because the server is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="03ddd-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="03ddd-120">User Action</span></span>  
 <span data-ttu-id="03ddd-121">サーバーが起動していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="03ddd-121">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ddd-122">参照</span><span class="sxs-lookup"><span data-stu-id="03ddd-122">See Also</span></span>  
 <span data-ttu-id="03ddd-123">[データベース エンジン サービスの管理](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="03ddd-123">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="03ddd-124">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="03ddd-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="03ddd-125">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="03ddd-125">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="03ddd-126">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="03ddd-126">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="03ddd-127">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="03ddd-127">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="03ddd-128">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="03ddd-128">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
