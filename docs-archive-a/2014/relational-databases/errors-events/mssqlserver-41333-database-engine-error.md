---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ba3cfc9627b4b44c3c9eccc620fb16bb94b861b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716374"
---
# <a name="mssqlserver_41333"></a><span data-ttu-id="e3160-102">MSSQLSERVER_41333</span><span class="sxs-lookup"><span data-stu-id="e3160-102">MSSQLSERVER_41333</span></span>
    
## <a name="details"></a><span data-ttu-id="e3160-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e3160-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3160-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e3160-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="e3160-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e3160-105">Event ID</span></span>|<span data-ttu-id="e3160-106">41333</span><span class="sxs-lookup"><span data-stu-id="e3160-106">41333</span></span>|  
|<span data-ttu-id="e3160-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e3160-107">Event Source</span></span>|<span data-ttu-id="e3160-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e3160-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e3160-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e3160-109">Component</span></span>|<span data-ttu-id="e3160-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e3160-110">SQLEngine</span></span>|  
|<span data-ttu-id="e3160-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e3160-111">Symbolic Name</span></span>|<span data-ttu-id="e3160-112">CROSS_CONTAINER_ISOLATION_FAILURE</span><span class="sxs-lookup"><span data-stu-id="e3160-112">CROSS_CONTAINER_ISOLATION_FAILURE</span></span>|  
|<span data-ttu-id="e3160-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e3160-113">Message Text</span></span>|<span data-ttu-id="e3160-114">次に示すトランザクションは、スナップショット分離を使用したうえでメモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャにアクセスする必要があります。RepeatableRead トランザクション、Serializable トランザクション、RepeatableRead または Serializable 分離でメモリ最適化されていないテーブルにアクセスするトランザクション。</span><span class="sxs-lookup"><span data-stu-id="e3160-114">The following transactions must access memory optimized tables and natively compiled stored procedures under snapshot isolation: RepeatableRead transactions, Serializable transactions, and transactions that access tables that are not memory optimized in RepeatableRead or Serializable isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3160-115">説明</span><span class="sxs-lookup"><span data-stu-id="e3160-115">Explanation</span></span>  
 <span data-ttu-id="e3160-116">ディスク ベース トランザクションと XTP トランザクションの間の分離レベルが高いユーザーに対しては、制約があります。</span><span class="sxs-lookup"><span data-stu-id="e3160-116">There are restrictions against the user of the higher isolation levels between disk based transactions and XTP transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3160-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e3160-117">User Action</span></span>  
 <span data-ttu-id="e3160-118">メモリ最適化テーブル (およびネイティブ コンパイル プロシージャ) とディスク ベース テーブルでは、高レベルの分離操作を実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="e3160-118">Don't attempt high level isolation operations on memory-optimized tables (and natively compiled procedures) and disk based tables.</span></span>  
  
 <span data-ttu-id="e3160-119">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3160-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3160-120">参照</span><span class="sxs-lookup"><span data-stu-id="e3160-120">See Also</span></span>  
 [<span data-ttu-id="e3160-121">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="e3160-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
