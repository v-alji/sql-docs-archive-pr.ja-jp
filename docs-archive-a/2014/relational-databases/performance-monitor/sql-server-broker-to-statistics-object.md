---
title: 'SQL Server: Broker TO Statistics オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 93d9c24a175dedfee171eccfccb34673501660ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643779"
---
# <a name="sql-server-broker-to-statistics-object"></a><span data-ttu-id="d77b7-102">SQL Server: Broker TO Statistics オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d77b7-102">SQL Server, Broker TO Statistics Object</span></span>
  <span data-ttu-id="d77b7-103">SQLServer:Broker TO Statistics パフォーマンス オブジェクトは、[!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログが転送オブジェクトを要求した回数、および転送オブジェクトが **tempdb** に書き込まれた頻度に関する情報を報告します。</span><span class="sxs-lookup"><span data-stu-id="d77b7-103">The SQLServer:Broker TO Statistics performance object reports information about how many times [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialogs request transmission objects, and how often transmission objects are written to **tempdb**.</span></span>  
  
 <span data-ttu-id="d77b7-104">転送オブジェクトには、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログのメッセージ転送状態が記録されます。</span><span class="sxs-lookup"><span data-stu-id="d77b7-104">Transmission objects record the state of message transmissions for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog.</span></span> <span data-ttu-id="d77b7-105">このオブジェクトはメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d77b7-105">They are stored in memory.</span></span> <span data-ttu-id="d77b7-106">メモリを解放するために、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] は非アクティブな転送オブジェクトのバッチを定期的に **tempdb**内の作業テーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d77b7-106">To free memory, [!INCLUDE[ssSB](../../includes/sssb-md.md)] periodically writes batches of inactive transmission objects to work tables in **tempdb**.</span></span>  
  
 <span data-ttu-id="d77b7-107">次の表は、このオブジェクトに含まれているカウンターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="d77b7-107">The following table lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="d77b7-108">SQL Server Broker TO Statistics カウンター</span><span class="sxs-lookup"><span data-stu-id="d77b7-108">SQL Server Broker TO Statistics counters</span></span>|<span data-ttu-id="d77b7-109">説明</span><span class="sxs-lookup"><span data-stu-id="d77b7-109">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<span data-ttu-id="d77b7-110">**平均Length of Batched Writes**</span><span class="sxs-lookup"><span data-stu-id="d77b7-110">**Avg. Length of Batched Writes**</span></span>|<span data-ttu-id="d77b7-111">バッチに保存される転送オブジェクトの平均数。</span><span class="sxs-lookup"><span data-stu-id="d77b7-111">The average number of transmission objects saved in a batch.</span></span>|  
|<span data-ttu-id="d77b7-112">**平均Time To Write Batch (ms)**</span><span class="sxs-lookup"><span data-stu-id="d77b7-112">**Avg. Time To Write Batch (ms)**</span></span>|<span data-ttu-id="d77b7-113">転送オブジェクトのバッチを保存するために必要な平均時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="d77b7-113">The average number of milliseconds required to save a batch of transmission objects.</span></span>|  
|<span data-ttu-id="d77b7-114">**平均Time Between Batches (ms)**</span><span class="sxs-lookup"><span data-stu-id="d77b7-114">**Avg. Time Between Batches (ms)**</span></span>|<span data-ttu-id="d77b7-115">転送オブジェクトのバッチが書き込まれる時間間隔の平均値 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="d77b7-115">The average number of milliseconds between writes of transmission object batches.</span></span>|  
|<span data-ttu-id="d77b7-116">**Tran Object Gets/sec**</span><span class="sxs-lookup"><span data-stu-id="d77b7-116">**Tran Object Gets/sec**</span></span>|<span data-ttu-id="d77b7-117">ダイアログが転送オブジェクトを要求した 1 秒あたりの回数。</span><span class="sxs-lookup"><span data-stu-id="d77b7-117">The number of times per second that dialogs requested transmission objects.</span></span>|  
|<span data-ttu-id="d77b7-118">**Tran Objects Marked Dirty/sec**</span><span class="sxs-lookup"><span data-stu-id="d77b7-118">**Tran Objects Marked Dirty/sec**</span></span>|<span data-ttu-id="d77b7-119">転送オブジェクトがダーティとマークされた 1 秒あたりの回数。</span><span class="sxs-lookup"><span data-stu-id="d77b7-119">The number of times per second that transmission objects were marked as dirty.</span></span> <span data-ttu-id="d77b7-120">最初の変更でメモリ内のコピーが **tempdb**に格納されているコピーと同一でなくなると、転送オブジェクトがダーティとマークされます。</span><span class="sxs-lookup"><span data-stu-id="d77b7-120">Transmission objects are marked as dirty by the first modification that causes the in-memory copy to differ from the copy stored in **tempdb**.</span></span> <span data-ttu-id="d77b7-121">転送オブジェクトは、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] がダイアログのメッセージ転送状態の変化を記録する必要がある場合に変更されます。</span><span class="sxs-lookup"><span data-stu-id="d77b7-121">Transmission objects are modified when [!INCLUDE[ssSB](../../includes/sssb-md.md)] has to record a change in the state of message transmissions for the dialog.</span></span>|  
|<span data-ttu-id="d77b7-122">**Tran Object Writes/sec**</span><span class="sxs-lookup"><span data-stu-id="d77b7-122">**Tran Object Writes/sec**</span></span>|<span data-ttu-id="d77b7-123">転送オブジェクトのバッチが **tempdb** の作業テーブルに書き込まれた 1 秒あたりの回数。</span><span class="sxs-lookup"><span data-stu-id="d77b7-123">The number of times per second that a batch of transmission objects were written to **tempdb** work tables.</span></span> <span data-ttu-id="d77b7-124">書き込み回数が多い場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリに負荷がかかっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d77b7-124">Large numbers of writes could indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory is being stressed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d77b7-125">参照</span><span class="sxs-lookup"><span data-stu-id="d77b7-125">See Also</span></span>  
 <span data-ttu-id="d77b7-126">[SQL Server の Access Methods オブジェクト](sql-server-access-methods-object.md) </span><span class="sxs-lookup"><span data-stu-id="d77b7-126">[SQL Server, Access Methods Object](sql-server-access-methods-object.md) </span></span>  
 <span data-ttu-id="d77b7-127">[SQL Server: Memory Manager オブジェクト](sql-server-memory-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="d77b7-127">[SQL Server, Memory Manager Object](sql-server-memory-manager-object.md) </span></span>  
 [<span data-ttu-id="d77b7-128">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="d77b7-128">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
