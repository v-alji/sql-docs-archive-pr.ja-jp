---
title: MSSQLSERVER_41396 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715301"
---
# <a name="mssqlserver_41396"></a><span data-ttu-id="430ed-102">MSSQLSERVER_41396</span><span class="sxs-lookup"><span data-stu-id="430ed-102">MSSQLSERVER_41396</span></span>
    
## <a name="details"></a><span data-ttu-id="430ed-103">詳細</span><span class="sxs-lookup"><span data-stu-id="430ed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="430ed-104">製品名</span><span class="sxs-lookup"><span data-stu-id="430ed-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="430ed-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="430ed-105">Event ID</span></span>|<span data-ttu-id="430ed-106">41396</span><span class="sxs-lookup"><span data-stu-id="430ed-106">41396</span></span>|  
|<span data-ttu-id="430ed-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="430ed-107">Event Source</span></span>|<span data-ttu-id="430ed-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="430ed-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="430ed-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="430ed-109">Component</span></span>|<span data-ttu-id="430ed-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="430ed-110">SQLEngine</span></span>|  
|<span data-ttu-id="430ed-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="430ed-111">Symbolic Name</span></span>|<span data-ttu-id="430ed-112">MAX_SORT_ROWS_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="430ed-112">MAX_SORT_ROWS_EXCEEDED</span></span>|  
|<span data-ttu-id="430ed-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="430ed-113">Message Text</span></span>|<span data-ttu-id="430ed-114">並べ替え操作がバッファーの制限を超えました。</span><span class="sxs-lookup"><span data-stu-id="430ed-114">The sort operation exceeded the buffer limit.</span></span> <span data-ttu-id="430ed-115">ストアド プロシージャの実行は中断されました。</span><span class="sxs-lookup"><span data-stu-id="430ed-115">The stored procedure execution was aborted.</span></span> <span data-ttu-id="430ed-116">詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="430ed-116">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="430ed-117">説明</span><span class="sxs-lookup"><span data-stu-id="430ed-117">Explanation</span></span>  
 <span data-ttu-id="430ed-118">ネイティブ コンパイル ストアド プロシージャは、メモリ内で並べ替え操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="430ed-118">Natively compiled stored procedures perform sort operations in memory.</span></span> <span data-ttu-id="430ed-119">並べ替えバッファーのサイズには制限があります。</span><span class="sxs-lookup"><span data-stu-id="430ed-119">There is a limit on the size of the sort buffer.</span></span> <span data-ttu-id="430ed-120">このエラーは、並べ替えバッファーのサイズがこの制限を超えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="430ed-120">This error means that the size of the sort buffer exceeds this limit.</span></span> <span data-ttu-id="430ed-121">並べ替え操作およびストアド プロシージャの実行は中断されます。</span><span class="sxs-lookup"><span data-stu-id="430ed-121">The sort operation and the stored procedure execution aborted.</span></span>  
  
 <span data-ttu-id="430ed-122">並べ替えバッファー内の各行またはエントリのサイズは、並べ替えられる行の数に加え、結合の数、およびクエリ内の集計関数の数と種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="430ed-122">The size of each row or entry in the sort buffer is determined by the number of rows sorted as well as the number of joins and the number and type of aggregate functions in the query.</span></span> <span data-ttu-id="430ed-123">クエリを単純化することで、各行のサイズを小さくできるため、並べ替えバッファー内にはより多くの行が収まります。</span><span class="sxs-lookup"><span data-stu-id="430ed-123">By simplifying the query, you can reduce the size of each row thereby fitting more rows in the sort buffer.</span></span> <span data-ttu-id="430ed-124">ベース テーブル内の行のサイズは、並べ替えバッファー内の各行またはエントリのサイズに影響しません。</span><span class="sxs-lookup"><span data-stu-id="430ed-124">The size of the rows in the base tables does not affect the size of each row or entry in the sort buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="430ed-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="430ed-125">User Action</span></span>  
 <span data-ttu-id="430ed-126">選択する行を減らすか、結合または集計関数を削除してクエリの複雑さを軽減してください。</span><span class="sxs-lookup"><span data-stu-id="430ed-126">Select fewer rows or decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430ed-127">参照</span><span class="sxs-lookup"><span data-stu-id="430ed-127">See Also</span></span>  
 [<span data-ttu-id="430ed-128">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="430ed-128">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
