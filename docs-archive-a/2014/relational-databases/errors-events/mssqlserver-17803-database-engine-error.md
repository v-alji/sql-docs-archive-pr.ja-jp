---
title: MSSQLSERVER_17803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be63b3d05bff2ebf90122f66af4297d77376fce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643892"
---
# <a name="mssqlserver_17803"></a><span data-ttu-id="a5fe3-102">MSSQLSERVER_17803</span><span class="sxs-lookup"><span data-stu-id="a5fe3-102">MSSQLSERVER_17803</span></span>
    
## <a name="details"></a><span data-ttu-id="a5fe3-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a5fe3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5fe3-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a5fe3-104">Product Name</span></span>|<span data-ttu-id="a5fe3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5fe3-105">SQL Server</span></span>|  
|<span data-ttu-id="a5fe3-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a5fe3-106">Event ID</span></span>|<span data-ttu-id="a5fe3-107">17803</span><span class="sxs-lookup"><span data-stu-id="a5fe3-107">17803</span></span>|  
|<span data-ttu-id="a5fe3-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a5fe3-108">Event Source</span></span>|<span data-ttu-id="a5fe3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a5fe3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a5fe3-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a5fe3-110">Component</span></span>|<span data-ttu-id="a5fe3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a5fe3-111">SQLEngine</span></span>|  
|<span data-ttu-id="a5fe3-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a5fe3-112">Symbolic Name</span></span>|<span data-ttu-id="a5fe3-113">SRV_NOMEMORY</span><span class="sxs-lookup"><span data-stu-id="a5fe3-113">SRV_NOMEMORY</span></span>|  
|<span data-ttu-id="a5fe3-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a5fe3-114">Message Text</span></span>|<span data-ttu-id="a5fe3-115">接続の確立中にメモリの割り当てエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a5fe3-115">There was a memory allocation failure during connection establishment.</span></span> <span data-ttu-id="a5fe3-116">不要なメモリ負荷を減らすか、システム メモリを増やしてください。</span><span class="sxs-lookup"><span data-stu-id="a5fe3-116">Reduce nonessential memory load, or increase system memory.</span></span> <span data-ttu-id="a5fe3-117">接続が閉じられました。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="a5fe3-117">The connection has been closed.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5fe3-118">説明</span><span class="sxs-lookup"><span data-stu-id="a5fe3-118">Explanation</span></span>  
 <span data-ttu-id="a5fe3-119">サーバーのメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="a5fe3-119">Server is running out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5fe3-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a5fe3-120">User Action</span></span>  
 <span data-ttu-id="a5fe3-121">サーバーのメモリが不足している原因を特定してください。</span><span class="sxs-lookup"><span data-stu-id="a5fe3-121">Determine the cause for server running out of memory.</span></span> <span data-ttu-id="a5fe3-122">一般的なメモリのトラブルシューティング手順を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5fe3-122">Generic memory troubleshooting steps may be useful</span></span>  
  
  
