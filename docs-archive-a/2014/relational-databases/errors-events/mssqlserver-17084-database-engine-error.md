---
title: MSSQLSERVER_17084 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59b0fc3e0884ddd89809767a068b937b5c145f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643893"
---
# <a name="mssqlserver_17084"></a><span data-ttu-id="8bf31-102">MSSQLSERVER_17084</span><span class="sxs-lookup"><span data-stu-id="8bf31-102">MSSQLSERVER_17084</span></span>
    
## <a name="details"></a><span data-ttu-id="8bf31-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8bf31-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8bf31-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8bf31-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="8bf31-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8bf31-105">Event ID</span></span>|<span data-ttu-id="8bf31-106">17084</span><span class="sxs-lookup"><span data-stu-id="8bf31-106">17084</span></span>|  
|<span data-ttu-id="8bf31-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8bf31-107">Event Source</span></span>|<span data-ttu-id="8bf31-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8bf31-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8bf31-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8bf31-109">Component</span></span>|<span data-ttu-id="8bf31-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8bf31-110">SQLEngine</span></span>|  
|<span data-ttu-id="8bf31-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8bf31-111">Symbolic Name</span></span>|<span data-ttu-id="8bf31-112">P3_ATOMIC_WITH_MISSING_OPTION</span><span class="sxs-lookup"><span data-stu-id="8bf31-112">P3_ATOMIC_WITH_MISSING_OPTION</span></span>|  
|<span data-ttu-id="8bf31-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8bf31-113">Message Text</span></span>|<span data-ttu-id="8bf31-114">BEGIN ATOMIC ステートメントの WITH 句は、オプション '%ls' の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8bf31-114">The WITH clause of BEGIN ATOMIC statement must specify a value for the option '%ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8bf31-115">説明</span><span class="sxs-lookup"><span data-stu-id="8bf31-115">Explanation</span></span>  
 <span data-ttu-id="8bf31-116">BEGIN ATOMIC ステートメントの WITH 句で、オプションの値が指定されませんでした。</span><span class="sxs-lookup"><span data-stu-id="8bf31-116">The WITH clause of BEGIN ATOMIC statement did not specify a value for an option.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8bf31-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8bf31-117">User Action</span></span>  
 <span data-ttu-id="8bf31-118">`ATOMIC` ブロックでは、`WITH` オプションの `TRANSACTION ISOLATION LEVEL` および `LANGUAGE` に値が必要です。</span><span class="sxs-lookup"><span data-stu-id="8bf31-118">`ATOMIC` blocks require values for the `WITH` options `TRANSACTION ISOLATION LEVEL` and `LANGUAGE`.</span></span> <span data-ttu-id="8bf31-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8bf31-119">For example::</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="8bf31-120">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8bf31-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf31-121">参照</span><span class="sxs-lookup"><span data-stu-id="8bf31-121">See Also</span></span>  
 [<span data-ttu-id="8bf31-122">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="8bf31-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
