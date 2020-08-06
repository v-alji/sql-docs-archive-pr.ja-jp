---
title: MSSQLSERVER_41307 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98407a65d5529fd73bccc638df11167131bd9f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718188"
---
# <a name="mssqlserver_41307"></a><span data-ttu-id="bd915-102">MSSQLSERVER_41307</span><span class="sxs-lookup"><span data-stu-id="bd915-102">MSSQLSERVER_41307</span></span>
    
## <a name="details"></a><span data-ttu-id="bd915-103">詳細</span><span class="sxs-lookup"><span data-stu-id="bd915-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd915-104">製品名</span><span class="sxs-lookup"><span data-stu-id="bd915-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="bd915-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bd915-105">Event ID</span></span>|<span data-ttu-id="bd915-106">41307</span><span class="sxs-lookup"><span data-stu-id="bd915-106">41307</span></span>|  
|<span data-ttu-id="bd915-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="bd915-107">Event Source</span></span>|<span data-ttu-id="bd915-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bd915-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bd915-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bd915-109">Component</span></span>|<span data-ttu-id="bd915-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bd915-110">SQLEngine</span></span>|  
|<span data-ttu-id="bd915-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="bd915-111">Symbolic Name</span></span>|<span data-ttu-id="bd915-112">HK_HEKATON_ROW_LIMIT</span><span class="sxs-lookup"><span data-stu-id="bd915-112">HK_HEKATON_ROW_LIMIT</span></span>|  
|<span data-ttu-id="bd915-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="bd915-113">Message Text</span></span>|<span data-ttu-id="bd915-114">メモリ最適化テーブルの行サイズの上限である *number* バイトを超えました。</span><span class="sxs-lookup"><span data-stu-id="bd915-114">The row size limit of *number* bytes for memory optimized tables has been exceeded.</span></span> <span data-ttu-id="bd915-115">テーブル定義を簡素化してください。</span><span class="sxs-lookup"><span data-stu-id="bd915-115">Please simplify the table definition.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bd915-116">説明</span><span class="sxs-lookup"><span data-stu-id="bd915-116">Explanation</span></span>  
 <span data-ttu-id="bd915-117">メモリ最適化テーブルの行サイズの上限は 8,060 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bd915-117">The row size limit for memory optimized tables is 8,060 bytes.</span></span> <span data-ttu-id="bd915-118">詳細については、「 [メモリ最適化テーブルのテーブルと行のサイズ](../in-memory-oltp/memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd915-118">For more information, see [Table and Row Size in Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span> <span data-ttu-id="bd915-119">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd915-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd915-120">参照</span><span class="sxs-lookup"><span data-stu-id="bd915-120">See Also</span></span>  
 [<span data-ttu-id="bd915-121">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="bd915-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
