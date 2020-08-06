---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e134cbc8b39a3c65d9c515183243f0b4caed434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639536"
---
# <a name="mssqlserver_41399"></a><span data-ttu-id="8a0b9-102">MSSQLSERVER_41399</span><span class="sxs-lookup"><span data-stu-id="8a0b9-102">MSSQLSERVER_41399</span></span>
    
## <a name="details"></a><span data-ttu-id="8a0b9-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8a0b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a0b9-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8a0b9-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="8a0b9-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8a0b9-105">Event ID</span></span>|<span data-ttu-id="8a0b9-106">41399</span><span class="sxs-lookup"><span data-stu-id="8a0b9-106">41399</span></span>|  
|<span data-ttu-id="8a0b9-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8a0b9-107">Event Source</span></span>|<span data-ttu-id="8a0b9-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8a0b9-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8a0b9-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8a0b9-109">Component</span></span>|<span data-ttu-id="8a0b9-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8a0b9-110">SQLEngine</span></span>|  
|<span data-ttu-id="8a0b9-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8a0b9-111">Symbolic Name</span></span>|<span data-ttu-id="8a0b9-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="8a0b9-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span></span>|  
|<span data-ttu-id="8a0b9-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8a0b9-113">Message Text</span></span>|<span data-ttu-id="8a0b9-114">並べ替え操作が複雑すぎます。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-114">The sort operation is too complex.</span></span> <span data-ttu-id="8a0b9-115">詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-115">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a0b9-116">説明</span><span class="sxs-lookup"><span data-stu-id="8a0b9-116">Explanation</span></span>  
 <span data-ttu-id="8a0b9-117">結合操作と集計操作の結果を並べ替えると、並べ替えバッファー内の行のサイズが大きくなり、並べ替え操作の複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-117">Sorting the result of join and aggregation operations increases the complexity of the sort operation by increasing the size of the row in the sort buffer.</span></span> <span data-ttu-id="8a0b9-118">このエラーは、行のサイズが、ネイティブ コンパイル ストアド プロシージャの Sort 演算子でサポートされる最大サイズを超えていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-118">This error means that the size of the row is larger than the maximum size supported by the sort operator in natively compiled stored procedures.</span></span> <span data-ttu-id="8a0b9-119">並べ替えバッファー内の行のサイズは、単純に、結合の数および集計関数の数と種類で決まることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-119">Note that the size of a row in the sort buffer is determined solely by the number of joins and the number and type of aggregate functions.</span></span> <span data-ttu-id="8a0b9-120">ベース テーブル内の行のサイズは、バッファー内の行のサイズに影響しません。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-120">The size of the rows in the base tables does not affect the size of the row in the buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a0b9-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8a0b9-121">User Action</span></span>  
 <span data-ttu-id="8a0b9-122">結合または集計関数を削除することでクエリの複雑さを軽減してください。</span><span class="sxs-lookup"><span data-stu-id="8a0b9-122">Decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0b9-123">参照</span><span class="sxs-lookup"><span data-stu-id="8a0b9-123">See Also</span></span>  
 [<span data-ttu-id="8a0b9-124">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="8a0b9-124">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
