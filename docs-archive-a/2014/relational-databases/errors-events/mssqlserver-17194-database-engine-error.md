---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3f56a104841c4825bba1f60b3588fadd63555c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640044"
---
# <a name="mssqlserver_17194"></a><span data-ttu-id="992e6-102">MSSQLSERVER_17194</span><span class="sxs-lookup"><span data-stu-id="992e6-102">MSSQLSERVER_17194</span></span>
    
## <a name="details"></a><span data-ttu-id="992e6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="992e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="992e6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="992e6-104">Product Name</span></span>|<span data-ttu-id="992e6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="992e6-105">SQL Server</span></span>|  
|<span data-ttu-id="992e6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="992e6-106">Event ID</span></span>|<span data-ttu-id="992e6-107">17194</span><span class="sxs-lookup"><span data-stu-id="992e6-107">17194</span></span>|  
|<span data-ttu-id="992e6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="992e6-108">Event Source</span></span>|<span data-ttu-id="992e6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="992e6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="992e6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="992e6-110">Component</span></span>|<span data-ttu-id="992e6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="992e6-111">SQLEngine</span></span>|  
|<span data-ttu-id="992e6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="992e6-112">Symbolic Name</span></span>||  
|<span data-ttu-id="992e6-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="992e6-113">Message Text</span></span>|<span data-ttu-id="992e6-114">サーバーはログインに必要な SSL プロバイダーを読み込めませんでした。接続が閉じられました。</span><span class="sxs-lookup"><span data-stu-id="992e6-114">The server was unable to load the SSL provider library needed to log in; the connection has been closed.</span></span> <span data-ttu-id="992e6-115">SSL は、管理者が行ったサーバーの構成方法に応じて、ログイン シーケンスの暗号化またはすべての通信の暗号化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="992e6-115">SSL is used to encrypt either the login sequence or all communications, depending on how the administrator has configured the server.</span></span> <span data-ttu-id="992e6-116">エラー メッセージ(0xXXXX) の詳細については、オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="992e6-116">See Books Online for information on this error message:  0xXXXX.</span></span> <span data-ttu-id="992e6-117">[CLIENT:11.11.11.11]</span><span class="sxs-lookup"><span data-stu-id="992e6-117">[CLIENT: 11.11.11.11]</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="992e6-118">説明</span><span class="sxs-lookup"><span data-stu-id="992e6-118">Explanation</span></span>  
 <span data-ttu-id="992e6-119">このエラーは、クライアントが接続を閉じたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="992e6-119">This error indicates that the client has closed the connection.</span></span> <span data-ttu-id="992e6-120">このエラーは、接続のタイムアウトが原因で発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="992e6-120">This error could occur because the connection time-out has expired.</span></span> <span data-ttu-id="992e6-121">エラー メッセージにはオペレーティング システムで生成された値が表示されます。この値で、原因となっている問題を確認できます。</span><span class="sxs-lookup"><span data-stu-id="992e6-121">The error message displays a value from the operating system that describes the underlying problem.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="992e6-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="992e6-122">User Action</span></span>  
 <span data-ttu-id="992e6-123">メッセージ内のエラー コードが 0x2746 (10 進値では 10054) の場合、接続がクライアントによってリセットされたことを意味します。通常はタイムアウトが原因です。エラーを解決するには、クライアントまたは呼び出し側のプログラムで接続のタイムアウトを増やします。</span><span class="sxs-lookup"><span data-stu-id="992e6-123">If the error code in the message is 0x2746 (decimal value 10054), this means that the connection was reset by the client, typically because of a time-out. To resolve the error, increase the connection time-out on the client or calling program.</span></span>  
  
 <span data-ttu-id="992e6-124">エラー メッセージにその他の値が示されている場合、解決方法を確認するには、オペレーティング システム コマンド **net helpmsg** を実行します (実行時に、エラー コードの 10 進値を指定します)。</span><span class="sxs-lookup"><span data-stu-id="992e6-124">To determine a possible solution for other error message values, use the operating system command **net helpmsg** and specify the decimal value of the error code.</span></span>  
  
 <span data-ttu-id="992e6-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する方法の詳細については、「[Server Network Configuration](../../database-engine/configure-windows/server-network-configuration.md)」 (サーバー ネットワークの構成) と「[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md)」 (クライアント ネットワーク構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="992e6-125">For more information about how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Server Network Configuration](../../database-engine/configure-windows/server-network-configuration.md) and [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="992e6-126">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="992e6-126">Internal-Only</span></span>  
  
