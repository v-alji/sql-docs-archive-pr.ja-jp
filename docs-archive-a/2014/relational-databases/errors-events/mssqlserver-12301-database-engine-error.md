---
title: MSSQLSERVER_12301 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12301 (Database Engine error)
ms.assetid: 69455df4-4ce9-4a6f-af5a-8bbc93e21245
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 849ba6d2b3c4f77061289eb86a2a572413d8ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631067"
---
# <a name="mssqlserver_12301"></a><span data-ttu-id="f6190-102">MSSQLSERVER_12301</span><span class="sxs-lookup"><span data-stu-id="f6190-102">MSSQLSERVER_12301</span></span>
    
## <a name="details"></a><span data-ttu-id="f6190-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f6190-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6190-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f6190-104">Product Name</span></span>|<span data-ttu-id="f6190-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f6190-105">SQL Server</span></span>|  
|<span data-ttu-id="f6190-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f6190-106">Event ID</span></span>|<span data-ttu-id="f6190-107">12301</span><span class="sxs-lookup"><span data-stu-id="f6190-107">12301</span></span>|  
|<span data-ttu-id="f6190-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f6190-108">Event Source</span></span>|<span data-ttu-id="f6190-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f6190-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f6190-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f6190-110">Component</span></span>|<span data-ttu-id="f6190-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f6190-111">SQLEngine</span></span>|  
|<span data-ttu-id="f6190-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f6190-112">Symbolic Name</span></span>|<span data-ttu-id="f6190-113">HK_UNSUPPORTED_NULLABLE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="f6190-113">HK_UNSUPPORTED_NULLABLE_COLUMNS</span></span>|  
|<span data-ttu-id="f6190-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f6190-114">Message Text</span></span>|<span data-ttu-id="f6190-115">インデックス キー内の NULL 値を許容する列は '*construct*' でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f6190-115">Nullable columns in the index key are not supported with '*construct*'.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="f6190-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f6190-116">User Action</span></span>  
 <span data-ttu-id="f6190-117">インデックス キー内では NULL 値を許容する列を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f6190-117">Do not use nullable columns in the index key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6190-118">参照</span><span class="sxs-lookup"><span data-stu-id="f6190-118">See Also</span></span>  
 [<span data-ttu-id="f6190-119">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="f6190-119">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
