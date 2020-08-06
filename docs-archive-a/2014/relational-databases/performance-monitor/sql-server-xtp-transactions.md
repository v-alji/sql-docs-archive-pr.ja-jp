---
title: XTP トランザクション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 75fa8bc9a673d9e0e018b8578a35af2e46b5044c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714242"
---
# <a name="xtp-transactions"></a><span data-ttu-id="bc881-102">XTP Transactions</span><span class="sxs-lookup"><span data-stu-id="bc881-102">XTP Transactions</span></span>
  <span data-ttu-id="bc881-103">XTP Transactions パフォーマンス オブジェクトには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内の XTP エンジン トランザクションに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc881-103">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bc881-104">次の表では、 **XTP トランザクション**カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bc881-104">This table describes the **XTP Transactions** counters.</span></span>  
  
|<span data-ttu-id="bc881-105">カウンター</span><span class="sxs-lookup"><span data-stu-id="bc881-105">Counter</span></span>|<span data-ttu-id="bc881-106">説明</span><span class="sxs-lookup"><span data-stu-id="bc881-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc881-107">**Cascading aborts/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-107">**Cascading aborts/sec**</span></span>|<span data-ttu-id="bc881-108">コミット依存ロールバックが原因でロールバックされたトランザクション数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-108">The number of transactions that rolled back to due a commit dependency rollback (on average), per second.</span></span>|  
|<span data-ttu-id="bc881-109">**Commit dependencies taken/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-109">**Commit dependencies taken/sec**</span></span>|<span data-ttu-id="bc881-110">トランザクションにより処理されたコミット依存の数に関する 1 秒間の平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-110">The number of commit dependencies taken by transactions (on average), per second.</span></span>|  
|<span data-ttu-id="bc881-111">**Read-only transactions prepared/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-111">**Read-only transactions prepared/sec**</span></span>|<span data-ttu-id="bc881-112">コミット処理の目的で準備された読み取り専用トランザクションの数に関する 1 秒あたりの値です。</span><span class="sxs-lookup"><span data-stu-id="bc881-112">The number of read-only transactions that were prepared for commit processing, per second.</span></span>|  
|<span data-ttu-id="bc881-113">**Save point refreshes/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-113">**Save point refreshes/sec**</span></span>|<span data-ttu-id="bc881-114">セーブポイントが "更新" された回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-114">The number of times a savepoint was "refreshed", (on average), per second.</span></span> <span data-ttu-id="bc881-115">セーブポイントの更新が発生するのは、既存のセーブポイントを、トランザクションの有効期間内での現在の状態にリセットしたときです。</span><span class="sxs-lookup"><span data-stu-id="bc881-115">A savepoint refresh is when an existing savepoint is reset to the current point in the transaction's lifetime.</span></span>|  
|<span data-ttu-id="bc881-116">**Save point rollbacks/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-116">**Save point rollbacks/sec**</span></span>|<span data-ttu-id="bc881-117">トランザクションがセーブポイントまでロールバックされた回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-117">The number of times a transaction rolled back to a save point (on average), per second.</span></span>|  
|<span data-ttu-id="bc881-118">**Save points created /sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-118">**Save points created /sec**</span></span>|<span data-ttu-id="bc881-119">セーブポイントが作成された回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-119">The number of save points created (on average), per second.</span></span>|  
|<span data-ttu-id="bc881-120">**Transaction validation failure/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-120">**Transaction validation failure/sec**</span></span>|<span data-ttu-id="bc881-121">トランザクションが検証処理に失敗した回数に関する 1 秒間の平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-121">The number of transactions that failed validation processing (on average), per second.</span></span>|  
|<span data-ttu-id="bc881-122">**Transactions aborted by user/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-122">**Transactions aborted by user/sec**</span></span>|<span data-ttu-id="bc881-123">トランザクションがユーザーによって中止された回数に関する 1 秒間の平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-123">The number of transactions that were aborted by the user (on average), per second.</span></span>|  
|<span data-ttu-id="bc881-124">**Transactions aborted/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-124">**Transactions aborted/sec**</span></span>|<span data-ttu-id="bc881-125">トランザクションが (ユーザーとシステムの両方によって) 中止された回数に関する 1 秒間の平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-125">The number of transactions that aborted (both by the user and the system, on average), per second.</span></span>|  
|<span data-ttu-id="bc881-126">**Transactions created/sec**</span><span class="sxs-lookup"><span data-stu-id="bc881-126">**Transactions created/sec**</span></span>|<span data-ttu-id="bc881-127">システム内でトランザクションが作成された回数に関する 1 秒間の平均です。</span><span class="sxs-lookup"><span data-stu-id="bc881-127">The number of transactions created in the system (on average), per second.</span></span><br /><br /> <span data-ttu-id="bc881-128">XTP トランザクションは、ディスク ベース トランザクションとは別にカウントされます (Databases:Transactions/sec に反映)。</span><span class="sxs-lookup"><span data-stu-id="bc881-128">XTP transactions are counted differently than disk-based transactions (as reflected in Databases:Transactions/sec).</span></span> <span data-ttu-id="bc881-129">たとえば、読み取り専用トランザクションは Transactions created/sec でカウントされますが、Databases:Transactions/sec ではカウントされません。</span><span class="sxs-lookup"><span data-stu-id="bc881-129">For example, Transactions created/sec counts read/only transactions, while Databases:Transactions/sec does not.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc881-130">参照</span><span class="sxs-lookup"><span data-stu-id="bc881-130">See Also</span></span>  
 [<span data-ttu-id="bc881-131">XTP &#40;インメモリ OLTP&#41; パフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="bc881-131">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
