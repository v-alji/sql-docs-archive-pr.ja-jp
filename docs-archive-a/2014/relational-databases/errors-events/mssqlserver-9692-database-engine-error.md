---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6ba95771aafffa5a322ffa1b7443419936addd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639997"
---
# <a name="mssqlserver_9692"></a><span data-ttu-id="c33e0-102">MSSQLSERVER_9692</span><span class="sxs-lookup"><span data-stu-id="c33e0-102">MSSQLSERVER_9692</span></span>
    
## <a name="details"></a><span data-ttu-id="c33e0-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c33e0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c33e0-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c33e0-104">Product Name</span></span>|<span data-ttu-id="c33e0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c33e0-105">SQL Server</span></span>|  
|<span data-ttu-id="c33e0-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c33e0-106">Event ID</span></span>|<span data-ttu-id="c33e0-107">9692</span><span class="sxs-lookup"><span data-stu-id="c33e0-107">9692</span></span>|  
|<span data-ttu-id="c33e0-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c33e0-108">Event Source</span></span>|<span data-ttu-id="c33e0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c33e0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c33e0-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c33e0-110">Component</span></span>|<span data-ttu-id="c33e0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c33e0-111">SQLEngine</span></span>|  
|<span data-ttu-id="c33e0-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c33e0-112">Symbolic Name</span></span>|<span data-ttu-id="c33e0-113">SB2_CANT_LISTEN_PORT_IN_USE</span><span class="sxs-lookup"><span data-stu-id="c33e0-113">SB2_CANT_LISTEN_PORT_IN_USE</span></span>|  
|<span data-ttu-id="c33e0-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c33e0-114">Message Text</span></span>|<span data-ttu-id="c33e0-115">ポート %d は他のプロセスで使用中なので、%S_MSG プロトコルのトランスポートではそのポートでリッスンできません。</span><span class="sxs-lookup"><span data-stu-id="c33e0-115">The %S_MSG protocol transport cannot listen on port %d because it is in use by another process.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c33e0-116">説明</span><span class="sxs-lookup"><span data-stu-id="c33e0-116">Explanation</span></span>  
 <span data-ttu-id="c33e0-117">指定された TCP ポートが、コンピューター上の別のプログラムで使用されています。</span><span class="sxs-lookup"><span data-stu-id="c33e0-117">Another program on the computer is using the TCP port indicated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c33e0-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c33e0-118">User Action</span></span>  
 <span data-ttu-id="c33e0-119">を実行し `netstat -aon` て、ポートを使用しているプログラムを特定します。</span><span class="sxs-lookup"><span data-stu-id="c33e0-119">Run `netstat -aon` to determine what program is using the port.</span></span> <span data-ttu-id="c33e0-120">そのアプリケーションを無効にするか、Service Broker に対して別のポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="c33e0-120">Disable that application or specify a different port for Service Broker.</span></span>  
  
  
