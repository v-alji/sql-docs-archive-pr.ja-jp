---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72a87838673f07f7a40596517ab54533d944e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642838"
---
# <a name="mssqlserver_41332"></a><span data-ttu-id="ee619-102">MSSQLSERVER_41332</span><span class="sxs-lookup"><span data-stu-id="ee619-102">MSSQLSERVER_41332</span></span>
    
## <a name="details"></a><span data-ttu-id="ee619-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ee619-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee619-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ee619-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="ee619-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ee619-105">Event ID</span></span>|<span data-ttu-id="ee619-106">41332</span><span class="sxs-lookup"><span data-stu-id="ee619-106">41332</span></span>|  
|<span data-ttu-id="ee619-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ee619-107">Event Source</span></span>|<span data-ttu-id="ee619-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ee619-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ee619-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ee619-109">Component</span></span>|<span data-ttu-id="ee619-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ee619-110">SQLEngine</span></span>|  
|<span data-ttu-id="ee619-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ee619-111">Symbolic Name</span></span>|<span data-ttu-id="ee619-112">SQL_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="ee619-112">SQL_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="ee619-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ee619-113">Message Text</span></span>|<span data-ttu-id="ee619-114">セッション TRANSACTION ISOLATION LEVEL が SNAPSHOT に設定されている場合、メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャはアクセスまたは作成できません。</span><span class="sxs-lookup"><span data-stu-id="ee619-114">Memory optimized tables and natively compiled stored procedures cannot be accessed or created when the session TRANSACTION ISOLATION LEVEL is set to SNAPSHOT.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee619-115">説明</span><span class="sxs-lookup"><span data-stu-id="ee619-115">Explanation</span></span>  
 <span data-ttu-id="ee619-116">トランザクションはスナップショット分離レベルで開始され、互換性のない機能を使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="ee619-116">The transaction was started in snapshot isolation level and then attempted to use an incompatible feature.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee619-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ee619-117">User Action</span></span>  
 <span data-ttu-id="ee619-118">他の分離レベルでトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="ee619-118">Start the transaction with a different isolation level.</span></span> <span data-ttu-id="ee619-119">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee619-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee619-120">参照</span><span class="sxs-lookup"><span data-stu-id="ee619-120">See Also</span></span>  
 [<span data-ttu-id="ee619-121">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="ee619-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
