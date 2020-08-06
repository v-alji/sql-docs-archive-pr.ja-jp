---
title: データベース サイズの見積もり | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3a390c4ade2c2dc08f67d2d1461955516e866c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640061"
---
# <a name="estimate-the-size-of-a-database"></a><span data-ttu-id="0adf2-102">データベース サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="0adf2-102">Estimate the Size of a Database</span></span>
  <span data-ttu-id="0adf2-103">データベースをデザインするときは、データを格納したときにデータベースのサイズがどのくらい大きくなるかを見積もる必要性が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0adf2-103">When you design a database, you may have to estimate how large the database will be when filled with data.</span></span> <span data-ttu-id="0adf2-104">データベースのサイズを見積もると、次の目的に必要なハードウェア構成の決定に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0adf2-104">Estimating the size of the database can help you determine the hardware configuration you will require to do the following:</span></span>  
  
-   <span data-ttu-id="0adf2-105">アプリケーションが必要とするパフォーマンスの実現。</span><span class="sxs-lookup"><span data-stu-id="0adf2-105">Achieve the performance required by your applications.</span></span>  
  
-   <span data-ttu-id="0adf2-106">データとインデックスの格納に必要となる適切な量の物理ディスク領域の確保。</span><span class="sxs-lookup"><span data-stu-id="0adf2-106">Guarantee the appropriate physical amount of disk space required to store the data and indexes.</span></span>  
  
 <span data-ttu-id="0adf2-107">データベースのサイズを見積もると、データベースのデザインを改良する必要があるかどうかを判断する場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0adf2-107">Estimating the size of a database can also help you determine whether the database design needs refining.</span></span> <span data-ttu-id="0adf2-108">たとえば、見積もったデータベースのサイズが大きすぎて組織内で実装できず、正規化の必要性があるとわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0adf2-108">For example, you may determine that the estimated size of the database is too large to implement in your organization and that more normalization is required.</span></span> <span data-ttu-id="0adf2-109">逆に、見積もったサイズが予想より小さい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0adf2-109">Conversely, the estimated size may be smaller than expected.</span></span> <span data-ttu-id="0adf2-110">この場合は、データベースを非正規化してクエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="0adf2-110">This would allow you to denormalize the database to improve query performance.</span></span>  
  
 <span data-ttu-id="0adf2-111">データベースのサイズを見積もるには、各テーブルのサイズを個別に見積もり、それぞれの値を合計します。</span><span class="sxs-lookup"><span data-stu-id="0adf2-111">To estimate the size of a database, estimate the size of each table individually and then add the values obtained.</span></span> <span data-ttu-id="0adf2-112">テーブルのサイズは、テーブルにインデックスが含まれているかどうかにより異なり、インデックスが含まれている場合はそのインデックスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="0adf2-112">The size of a table depends on whether the table has indexes and, if they do, what type of indexes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0adf2-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0adf2-113">In This Section</span></span>  
  
|<span data-ttu-id="0adf2-114">トピック</span><span class="sxs-lookup"><span data-stu-id="0adf2-114">Topic</span></span>|<span data-ttu-id="0adf2-115">説明</span><span class="sxs-lookup"><span data-stu-id="0adf2-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0adf2-116">テーブル サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="0adf2-116">Estimate the Size of a Table</span></span>](estimate-the-size-of-a-table.md)|<span data-ttu-id="0adf2-117">テーブルおよび関連付けられたインデックスにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0adf2-117">Defines the steps and calculations needed to estimate the amount of space required to store the data in a table and associated indexes.</span></span>|  
|[<span data-ttu-id="0adf2-118">ヒープ サイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="0adf2-118">Estimate the Size of a Heap</span></span>](estimate-the-size-of-a-heap.md)|<span data-ttu-id="0adf2-119">ヒープにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0adf2-119">Defines the steps and calculations needed to estimate the amount of space required to store the data in a heap.</span></span> <span data-ttu-id="0adf2-120">ヒープとは、クラスター化インデックスを含まないテーブルのことです。</span><span class="sxs-lookup"><span data-stu-id="0adf2-120">A heap is a table that does not have a clustered index.</span></span>|  
|[<span data-ttu-id="0adf2-121">クラスター化インデックスのサイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="0adf2-121">Estimate the Size of a Clustered Index</span></span>](estimate-the-size-of-a-clustered-index.md)|<span data-ttu-id="0adf2-122">クラスター化インデックスにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0adf2-122">Defines the steps and calculations needed to estimate the amount of space required to store the data in a clustered index.</span></span>|  
|[<span data-ttu-id="0adf2-123">非クラスター化インデックスのサイズの算出</span><span class="sxs-lookup"><span data-stu-id="0adf2-123">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)|<span data-ttu-id="0adf2-124">非クラスター化インデックスにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0adf2-124">Defines the steps and calculations needed to estimate the amount of space required to store the data in a nonclustered index.</span></span>|  
  
  
