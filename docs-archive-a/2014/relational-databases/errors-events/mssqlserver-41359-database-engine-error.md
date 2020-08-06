---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cf45a117dcda0827672c6072c603a1fc0866a33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644470"
---
# <a name="mssqlserver_41359"></a><span data-ttu-id="e6e9e-102">MSSQLSERVER_41359</span><span class="sxs-lookup"><span data-stu-id="e6e9e-102">MSSQLSERVER_41359</span></span>
    
## <a name="details"></a><span data-ttu-id="e6e9e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e6e9e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6e9e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e6e9e-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="e6e9e-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e6e9e-105">Event ID</span></span>|<span data-ttu-id="e6e9e-106">41359</span><span class="sxs-lookup"><span data-stu-id="e6e9e-106">41359</span></span>|  
|<span data-ttu-id="e6e9e-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e6e9e-107">Event Source</span></span>|<span data-ttu-id="e6e9e-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e6e9e-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e6e9e-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e6e9e-109">Component</span></span>|<span data-ttu-id="e6e9e-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e6e9e-110">SQLEngine</span></span>|  
|<span data-ttu-id="e6e9e-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e6e9e-111">Symbolic Name</span></span>|<span data-ttu-id="e6e9e-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="e6e9e-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="e6e9e-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e6e9e-113">Message Text</span></span>|<span data-ttu-id="e6e9e-114">メモリ最適化テーブルにアクセスするクエリで分離レベルに READ COMMITTED が使用されており、データベース オプション READ_COMMITTED_SNAPSHOT が ON に設定されている場合には、ディスク ベース テーブルにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="e6e9e-114">A query that accesses memory optimized tables using the READ COMMITTED isolation level, cannot access disk based tables when the database option READ_COMMITTED_SNAPSHOT is set to ON.</span></span> <span data-ttu-id="e6e9e-115">メモリ最適化テーブルには WITH (SNAPSHOT) などのテーブル ヒントを使用して、サポートされる分離レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6e9e-115">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e6e9e-116">説明</span><span class="sxs-lookup"><span data-stu-id="e6e9e-116">Explanation</span></span>  
 <span data-ttu-id="e6e9e-117">READ_COMMITTED_SNAPSHOT が ON のデータベースでは、メモリ最適化テーブルとディスク ベース テーブルのどちらにもアクセスするトランザクションがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e6e9e-117">The database with READ_COMMITTED_SNAPSHOT=ON does not support the transactions that access both memory-optimized tables and disk based tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e6e9e-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e6e9e-118">User Action</span></span>  
 <span data-ttu-id="e6e9e-119">READ_COMMITTED_SNAPSHOT を OFF に設定するか、WITH (SNAPSHOT) などのテーブル レベルのヒントを使用してメモリ最適化テーブルでサポートされる分離レベルを指定してください。</span><span class="sxs-lookup"><span data-stu-id="e6e9e-119">Set READ_COMMITTED_SNAPSHOT to OFF or supply a supported isolation level for the memory-optimized table using a table-level hint, such as WITH (SNAPSHOT).</span></span> <span data-ttu-id="e6e9e-120">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6e9e-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e9e-121">参照</span><span class="sxs-lookup"><span data-stu-id="e6e9e-121">See Also</span></span>  
 [<span data-ttu-id="e6e9e-122">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="e6e9e-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
