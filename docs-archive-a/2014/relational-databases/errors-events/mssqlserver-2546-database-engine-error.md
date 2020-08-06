---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c1c5f64ca0daba413f2b71c05f5b8e57b2d55df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713193"
---
# <a name="mssqlserver_2546"></a><span data-ttu-id="6e18e-102">MSSQLSERVER_2546</span><span class="sxs-lookup"><span data-stu-id="6e18e-102">MSSQLSERVER_2546</span></span>
    
## <a name="details"></a><span data-ttu-id="6e18e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6e18e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e18e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6e18e-104">Product Name</span></span>|<span data-ttu-id="6e18e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6e18e-105">SQL Server</span></span>|  
|<span data-ttu-id="6e18e-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6e18e-106">Event ID</span></span>|<span data-ttu-id="6e18e-107">2546</span><span class="sxs-lookup"><span data-stu-id="6e18e-107">2546</span></span>|  
|<span data-ttu-id="6e18e-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6e18e-108">Event Source</span></span>|<span data-ttu-id="6e18e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e18e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e18e-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e18e-110">Component</span></span>|<span data-ttu-id="6e18e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6e18e-111">SQLEngine</span></span>|  
|<span data-ttu-id="6e18e-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6e18e-112">Symbolic Name</span></span>|<span data-ttu-id="6e18e-113">DBCC_INDEX_MARKED_DISABLED</span><span class="sxs-lookup"><span data-stu-id="6e18e-113">DBCC_INDEX_MARKED_DISABLED</span></span>|  
|<span data-ttu-id="6e18e-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6e18e-114">Message Text</span></span>|<span data-ttu-id="6e18e-115">テーブル 'OBJECT_NAME' のインデックス 'INDEX_NAME' は無効に設定されています。</span><span class="sxs-lookup"><span data-stu-id="6e18e-115">Index 'INDEX_NAME' on table 'OBJECT_NAME' is marked as disabled.</span></span> <span data-ttu-id="6e18e-116">オンラインにするには、インデックスを再構築してください。</span><span class="sxs-lookup"><span data-stu-id="6e18e-116">Rebuild the index to bring it online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e18e-117">説明</span><span class="sxs-lookup"><span data-stu-id="6e18e-117">Explanation</span></span>  
 <span data-ttu-id="6e18e-118">指定されているインデックスは、オフラインまたは無効に設定されています。</span><span class="sxs-lookup"><span data-stu-id="6e18e-118">The specified index is marked as offline or is disabled.</span></span> <span data-ttu-id="6e18e-119">そのため、このインデックスをチェックできません。</span><span class="sxs-lookup"><span data-stu-id="6e18e-119">Therefore, this index cannot be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e18e-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6e18e-120">User Action</span></span>  
 <span data-ttu-id="6e18e-121">ALTER INDEX を使用してインデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="6e18e-121">Rebuild the index by using ALTER INDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e18e-122">参照</span><span class="sxs-lookup"><span data-stu-id="6e18e-122">See Also</span></span>  
 <span data-ttu-id="6e18e-123">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e18e-123">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="6e18e-124">インデックスの再編成と再構築</span><span class="sxs-lookup"><span data-stu-id="6e18e-124">Reorganize and Rebuild Indexes</span></span>](../indexes/indexes.md)  
  
  
