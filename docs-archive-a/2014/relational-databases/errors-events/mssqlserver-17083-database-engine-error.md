---
title: MSSQLSERVER_17083 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 598cf9b0182178aa13a6d8b965ac10bedaaf5d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643898"
---
# <a name="mssqlserver_17083"></a><span data-ttu-id="bd91d-102">MSSQLSERVER_17083</span><span class="sxs-lookup"><span data-stu-id="bd91d-102">MSSQLSERVER_17083</span></span>
    
## <a name="details"></a><span data-ttu-id="bd91d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="bd91d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd91d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="bd91d-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="bd91d-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bd91d-105">Event ID</span></span>|<span data-ttu-id="bd91d-106">17083</span><span class="sxs-lookup"><span data-stu-id="bd91d-106">17083</span></span>|  
|<span data-ttu-id="bd91d-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="bd91d-107">Event Source</span></span>|<span data-ttu-id="bd91d-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bd91d-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bd91d-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bd91d-109">Component</span></span>|<span data-ttu-id="bd91d-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bd91d-110">SQLEngine</span></span>|  
|<span data-ttu-id="bd91d-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="bd91d-111">Symbolic Name</span></span>|<span data-ttu-id="bd91d-112">P3_HEKATON_NOT_ATOMIC</span><span class="sxs-lookup"><span data-stu-id="bd91d-112">P3_HEKATON_NOT_ATOMIC</span></span>|  
|<span data-ttu-id="bd91d-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="bd91d-113">Message Text</span></span>|<span data-ttu-id="bd91d-114">ネイティブ コンパイル ストアド プロシージャの本体は ATOMIC ブロックである必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd91d-114">The body of a natively compiled stored procedure must be an ATOMIC block.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bd91d-115">説明</span><span class="sxs-lookup"><span data-stu-id="bd91d-115">Explanation</span></span>  
 <span data-ttu-id="bd91d-116">ネイティブ コンパイル ストアド プロシージャの本体に ATOMIC ブロックがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="bd91d-116">The body of a natively compiled stored procedure did not have an ATOMIC block.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bd91d-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="bd91d-117">User Action</span></span>  
 <span data-ttu-id="bd91d-118">ネイティブ コンパイル ストアド プロシージャには ATOMIC ブロックが必要です。</span><span class="sxs-lookup"><span data-stu-id="bd91d-118">A natively compiled stored procedure must contain an ATOMIC block.</span></span> <span data-ttu-id="bd91d-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bd91d-119">For example:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="bd91d-120">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd91d-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd91d-121">参照</span><span class="sxs-lookup"><span data-stu-id="bd91d-121">See Also</span></span>  
 [<span data-ttu-id="bd91d-122">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="bd91d-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
