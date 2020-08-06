---
title: テーブル サイズの見積もり | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a16d439d3b2bc59479866b7bb36295ec4fc8950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736373"
---
# <a name="estimate-the-size-of-a-table"></a><span data-ttu-id="830c9-102">テーブル サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="830c9-102">Estimate the Size of a Table</span></span>
  <span data-ttu-id="830c9-103">次の手順を実行して、テーブルにデータを格納するために必要な領域を見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="830c9-103">You can use the following steps to estimate the amount of space required to store data in a table:</span></span>  
  
1.  <span data-ttu-id="830c9-104">「 [ヒープ サイズの見積もり](estimate-the-size-of-a-heap.md) 」または「 [クラスター化インデックスのサイズの見積もり](estimate-the-size-of-a-clustered-index.md)」の説明に従って、ヒープまたはクラスター化インデックスに必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="830c9-104">Calculate the space required for the heap or clustered index following the instructions in [Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) or [Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md).</span></span>  
  
2.  <span data-ttu-id="830c9-105">「 [非クラスター化インデックスのサイズの算出](estimate-the-size-of-a-nonclustered-index.md)」に記載されている手順に従って、非クラスター化インデックスごとに必要な領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="830c9-105">For each nonclustered index, calculate the space required for it by following the instructions in [Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md).</span></span>  
  
3.  <span data-ttu-id="830c9-106">手順 1. と手順 2. で計算した値を加算します。</span><span class="sxs-lookup"><span data-stu-id="830c9-106">Add the values calculated in steps 1 and 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830c9-107">参照</span><span class="sxs-lookup"><span data-stu-id="830c9-107">See Also</span></span>  
 <span data-ttu-id="830c9-108">[データベース サイズの見積もり](estimate-the-size-of-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="830c9-108">[Estimate the Size of a Database](estimate-the-size-of-a-database.md) </span></span>  
 <span data-ttu-id="830c9-109">[ヒープ サイズの見積もり](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="830c9-109">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 <span data-ttu-id="830c9-110">[クラスター化インデックスのサイズの見積もり](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="830c9-110">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 [<span data-ttu-id="830c9-111">非クラスター化インデックスのサイズの算出</span><span class="sxs-lookup"><span data-stu-id="830c9-111">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)  
  
  
