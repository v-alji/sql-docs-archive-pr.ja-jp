---
title: XTP (インメモリ OLTP) パフォーマンスカウンター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4363a526ada3694e92d18cac0d7abe8a26f6a92f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714250"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a><span data-ttu-id="d3e0b-102">XTP (インメモリ OLTP) パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="d3e0b-102">XTP (In-Memory OLTP) Performance Counters</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d3e0b-103">には、パフォーマンス モニターがインメモリ OLTP のアクティビティを監視するために使用できるオブジェクトとカウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-103">provides objects and counters that can be used by Performance Monitor to monitor In-Memory OLTP activity.</span></span>  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a><span data-ttu-id="d3e0b-104">XTP (インメモリ OLTP) パフォーマンスオブジェクト</span><span class="sxs-lookup"><span data-stu-id="d3e0b-104">XTP (In-Memory OLTP) Performance Objects</span></span>  
 <span data-ttu-id="d3e0b-105">次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-105">The following table describes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
|<span data-ttu-id="d3e0b-106">パフォーマンス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d3e0b-106">Performance object</span></span>|<span data-ttu-id="d3e0b-107">説明</span><span class="sxs-lookup"><span data-stu-id="d3e0b-107">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="d3e0b-108">XTP Cursors</span><span class="sxs-lookup"><span data-stu-id="d3e0b-108">XTP Cursors</span></span>](../cursors.md)|<span data-ttu-id="d3e0b-109">XTP Cursors パフォーマンス オブジェクトには、XTP エンジンの内部カーソルに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-109">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="d3e0b-110">カーソルとは、XTP エンジンが [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを処理するために使用する、低レベルの構成要素です。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-110">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="d3e0b-111">このため、通常はユーザー側でカーソルを直接管理することはありません。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-111">As such, you do not typically have direct control over them.</span></span>|  
|[<span data-ttu-id="d3e0b-112">XTP Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="d3e0b-112">XTP Garbage Collection</span></span>](sql-server-xtp-garbage-collection.md)|<span data-ttu-id="d3e0b-113">XTP Garbage Collection パフォーマンス オブジェクトには、XTP エンジンのガベージ コレクターに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-113">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>|  
|[<span data-ttu-id="d3e0b-114">XTP Phantom Processor</span><span class="sxs-lookup"><span data-stu-id="d3e0b-114">XTP Phantom Processor</span></span>](sql-server-xtp-phantom-processor.md)|<span data-ttu-id="d3e0b-115">XTP Phantom Processor パフォーマンス オブジェクトには、XTP エンジンのファントム処理サブシステムに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-115">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="d3e0b-116">このコンポーネントには、SERIALIZABLE 分離レベルで実行されているトランザクション内のファントム行を検出する役割があります。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-116">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>|  
|[<span data-ttu-id="d3e0b-117">XTP ストレージ</span><span class="sxs-lookup"><span data-stu-id="d3e0b-117">XTP Storage</span></span>](sql-server-xtp-storage.md)|<span data-ttu-id="d3e0b-118">XTP ストレージのパフォーマンス オブジェクトには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の XTP ストレージに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-118">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="d3e0b-119">XTP Transaction Log</span><span class="sxs-lookup"><span data-stu-id="d3e0b-119">XTP Transaction Log</span></span>](sql-server-xtp-transaction-log.md)|<span data-ttu-id="d3e0b-120">XTP Transaction Log パフォーマンス オブジェクトには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内の XTP トランザクション ログに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-120">The XTP Transaction Log performance object contains counters related to XTP transaction logging in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="d3e0b-121">XTP Transactions</span><span class="sxs-lookup"><span data-stu-id="d3e0b-121">XTP Transactions</span></span>](sql-server-xtp-transactions.md)|<span data-ttu-id="d3e0b-122">XTP Transactions パフォーマンス オブジェクトには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内の XTP エンジン トランザクションに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e0b-122">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
