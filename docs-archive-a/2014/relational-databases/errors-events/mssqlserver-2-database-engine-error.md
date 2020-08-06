---
title: MSSQLSERVER_2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 87d19a24219fda79de2cad4c06af4f1936b37b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643889"
---
# <a name="mssqlserver_2"></a><span data-ttu-id="92b95-102">MSSQLSERVER_2</span><span class="sxs-lookup"><span data-stu-id="92b95-102">MSSQLSERVER_2</span></span>
    
## <a name="details"></a><span data-ttu-id="92b95-103">詳細</span><span class="sxs-lookup"><span data-stu-id="92b95-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92b95-104">製品名</span><span class="sxs-lookup"><span data-stu-id="92b95-104">Product Name</span></span>|<span data-ttu-id="92b95-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="92b95-105">SQL Server</span></span>|  
|<span data-ttu-id="92b95-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="92b95-106">Event ID</span></span>|<span data-ttu-id="92b95-107">2</span><span class="sxs-lookup"><span data-stu-id="92b95-107">2</span></span>|  
|<span data-ttu-id="92b95-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="92b95-108">Event Source</span></span>|<span data-ttu-id="92b95-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="92b95-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="92b95-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="92b95-110">Component</span></span>|<span data-ttu-id="92b95-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="92b95-111">SQLEngine</span></span>|  
|<span data-ttu-id="92b95-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="92b95-112">Symbolic Name</span></span>||  
|<span data-ttu-id="92b95-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="92b95-113">Message Text</span></span>|<span data-ttu-id="92b95-114">サーバーへの接続を確立中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="92b95-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="92b95-115">SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92b95-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="92b95-116">(プロバイダー:名前付きパイプ プロバイダー、エラー:40 - SQL Server への接続を開けませんでした) (.Net SqlClient Data Provider)</span><span class="sxs-lookup"><span data-stu-id="92b95-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="92b95-117">説明</span><span class="sxs-lookup"><span data-stu-id="92b95-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92b95-118">がクライアント要求に応答しませんでした。おそらくサーバーが起動していません。</span><span class="sxs-lookup"><span data-stu-id="92b95-118">did not respond to the client request because the server is probably not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="92b95-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="92b95-119">User Action</span></span>  
 <span data-ttu-id="92b95-120">サーバーが起動していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="92b95-120">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b95-121">参照</span><span class="sxs-lookup"><span data-stu-id="92b95-121">See Also</span></span>  
 <span data-ttu-id="92b95-122">[データベース エンジン サービスの管理](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="92b95-122">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="92b95-123">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="92b95-123">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="92b95-124">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="92b95-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="92b95-125">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="92b95-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="92b95-126">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="92b95-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="92b95-127">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="92b95-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
