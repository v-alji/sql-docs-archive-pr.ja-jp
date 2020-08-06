---
title: MSSQLSERVER_233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c51fac7c0af16c520d7cf5538e512912e62cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714390"
---
# <a name="mssqlserver_233"></a><span data-ttu-id="f2241-102">MSSQLSERVER_233</span><span class="sxs-lookup"><span data-stu-id="f2241-102">MSSQLSERVER_233</span></span>
    
## <a name="details"></a><span data-ttu-id="f2241-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f2241-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2241-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f2241-104">Product Name</span></span>|<span data-ttu-id="f2241-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f2241-105">SQL Server</span></span>|  
|<span data-ttu-id="f2241-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f2241-106">Event ID</span></span>|<span data-ttu-id="f2241-107">233</span><span class="sxs-lookup"><span data-stu-id="f2241-107">233</span></span>|  
|<span data-ttu-id="f2241-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f2241-108">Event Source</span></span>|<span data-ttu-id="f2241-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f2241-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f2241-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f2241-110">Component</span></span>|<span data-ttu-id="f2241-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f2241-111">SQLEngine</span></span>|  
|<span data-ttu-id="f2241-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f2241-112">Symbolic Name</span></span>||  
|<span data-ttu-id="f2241-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f2241-113">Message Text</span></span>|<span data-ttu-id="f2241-114">サーバーとの接続は正常に確立されましたが、ログイン プロセスでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f2241-114">A connection was successfully established with the server, but then an error occurred during the login process.</span></span> <span data-ttu-id="f2241-115">(プロバイダー:共有メモリ プロバイダー、エラー:0 - パイプの他端にプロセスがありません。) (Microsoft SQL Server、エラー:233)</span><span class="sxs-lookup"><span data-stu-id="f2241-115">(provider: Shared Memory Provider, error: 0 - No process is on the other end of the pipe.) (Microsoft SQL Server, Error: 233)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2241-116">説明</span><span class="sxs-lookup"><span data-stu-id="f2241-116">Explanation</span></span>  
 <span data-ttu-id="f2241-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントがサーバーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="f2241-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="f2241-118">このエラーは、サーバーがリモート接続を許可するように構成されていないことが原因で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="f2241-118">This error could occur because the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2241-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f2241-119">User Action</span></span>  
 <span data-ttu-id="f2241-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー ツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリモート接続を許可できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f2241-120">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2241-121">参照</span><span class="sxs-lookup"><span data-stu-id="f2241-121">See Also</span></span>  
 <span data-ttu-id="f2241-122">[ネットワークプロトコルとネットワークライブラリ](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="f2241-122">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="f2241-123">[クライアント ネットワーク構成](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f2241-123">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="f2241-124">[クライアントプロトコルの構成](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="f2241-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="f2241-125">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="f2241-125">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
