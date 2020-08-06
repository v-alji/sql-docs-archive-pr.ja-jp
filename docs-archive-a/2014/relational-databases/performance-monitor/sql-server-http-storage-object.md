---
title: SQL Server:HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62cd5b8422213624cfd8609027c477760f682239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633092"
---
# <a name="sql-server-http_storage_object"></a><span data-ttu-id="68f50-102">SQL Server:HTTP_STORAGE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="68f50-102">SQL Server, HTTP_STORAGE_OBJECT</span></span>
  <span data-ttu-id="68f50-103">**SQLServer: HTTP_STORAGE_OBJECT**パフォーマンスオブジェクトは、Azure Storage アカウントを監視するパフォーマンスカウンターで構成されています。</span><span class="sxs-lookup"><span data-stu-id="68f50-103">The **SQLServer:HTTP_STORAGE_OBJECT** performance object consists of performance counters that monitor Azure Storage account.</span></span> <span data-ttu-id="68f50-104">[Azure 機能で SQL Server データファイル](../databases/sql-server-data-files-in-microsoft-azure.md)を使用すると、Azure Storage blob にデータベースファイルを格納できます。</span><span class="sxs-lookup"><span data-stu-id="68f50-104">Using [SQL Server Data Files in Azure](../databases/sql-server-data-files-in-microsoft-azure.md) feature, you can store database files in Azure Storage Blobs.</span></span> <span data-ttu-id="68f50-105">このパフォーマンス オブジェクトでは、各 Azure ストレージ アカウントが別々のドライブとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="68f50-105">This performance object treats each Azure Storage account as a different drive.</span></span>  
  
|<span data-ttu-id="68f50-106">カウンター名</span><span class="sxs-lookup"><span data-stu-id="68f50-106">Counter Name</span></span>|<span data-ttu-id="68f50-107">説明</span><span class="sxs-lookup"><span data-stu-id="68f50-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="68f50-108">**Read Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="68f50-108">**Read Bytes/sec**</span></span>|<span data-ttu-id="68f50-109">読み取り操作中に HTTP ストレージから転送されている 1 秒あたりのデータ量。</span><span class="sxs-lookup"><span data-stu-id="68f50-109">Amount of data being transferred from the HTTP storage per second during read operations.</span></span>|  
|<span data-ttu-id="68f50-110">**Write Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="68f50-110">**Write Bytes/sec**</span></span>|<span data-ttu-id="68f50-111">書き込み操作中に HTTP ストレージから転送されている 1 秒あたりのデータ量。</span><span class="sxs-lookup"><span data-stu-id="68f50-111">Amount of data being transferred from the HTTP storage per second during write operations.</span></span>|  
|<span data-ttu-id="68f50-112">**Total Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="68f50-112">**Total Bytes/sec**</span></span>|<span data-ttu-id="68f50-113">読み取りまたは書き込み操作中に HTTP ストレージから転送されている 1 秒あたりのデータ量。</span><span class="sxs-lookup"><span data-stu-id="68f50-113">Amount of data being transferred from the HTTP storage per second during read or write operations.</span></span>|  
|<span data-ttu-id="68f50-114">**Reads/sec**</span><span class="sxs-lookup"><span data-stu-id="68f50-114">**Reads/sec**</span></span>|<span data-ttu-id="68f50-115">HTTP ストレージでの 1 秒あたりの読み取り数。</span><span class="sxs-lookup"><span data-stu-id="68f50-115">Number of reads per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-116">**Writes/sec**</span><span class="sxs-lookup"><span data-stu-id="68f50-116">**Writes/sec**</span></span>|<span data-ttu-id="68f50-117">HTTP ストレージでの 1 秒あたりの書き込み数。</span><span class="sxs-lookup"><span data-stu-id="68f50-117">Number of writer per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-118">**Transfers/sec**</span><span class="sxs-lookup"><span data-stu-id="68f50-118">**Transfers/sec**</span></span>|<span data-ttu-id="68f50-119">HTTP ストレージでの 1 秒あたりの読み取りおよび書き込み操作数。</span><span class="sxs-lookup"><span data-stu-id="68f50-119">Number of read and write operations per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-120">**平均Bytes/Read**</span><span class="sxs-lookup"><span data-stu-id="68f50-120">**Avg. Bytes/Read**</span></span>|<span data-ttu-id="68f50-121">読み取りごとに HTTP ストレージから転送された平均バイト数。</span><span class="sxs-lookup"><span data-stu-id="68f50-121">Average number of bytes transferred from the HTTP storage per read.</span></span>|  
|<span data-ttu-id="68f50-122">**平均Bytes/Write**</span><span class="sxs-lookup"><span data-stu-id="68f50-122">**Avg. Bytes/Write**</span></span>|<span data-ttu-id="68f50-123">書き込みごとに HTTP ストレージから転送された平均バイト数。</span><span class="sxs-lookup"><span data-stu-id="68f50-123">Average number of bytes transferred from the HTTP storage per write.</span></span>|  
|<span data-ttu-id="68f50-124">**平均Bytes/Transfer**</span><span class="sxs-lookup"><span data-stu-id="68f50-124">**Avg. Bytes/Transfer**</span></span>|<span data-ttu-id="68f50-125">読み取りまたは書き込み操作中に HTTP ストレージから転送された平均バイト数。</span><span class="sxs-lookup"><span data-stu-id="68f50-125">Average number of bytes transferred from the HTTP storage during read or write operations.</span></span>|  
|<span data-ttu-id="68f50-126">**Avg. microsec/Read**</span><span class="sxs-lookup"><span data-stu-id="68f50-126">**Avg. microsec/Read**</span></span>|<span data-ttu-id="68f50-127">HTTP ストレージからの読み取りごとに要する平均マイクロ秒数。</span><span class="sxs-lookup"><span data-stu-id="68f50-127">The average number of microseconds it takes to do each read from the HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-128">**Avg. microsec/Write**</span><span class="sxs-lookup"><span data-stu-id="68f50-128">**Avg. microsec/Write**</span></span>|<span data-ttu-id="68f50-129">HTTP ストレージへの書き込みごとに要する平均マイクロ秒数。</span><span class="sxs-lookup"><span data-stu-id="68f50-129">The average number of microseconds it takes to do each write to the HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-130">**Avg. microsec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="68f50-130">**Avg. microsec/Transfer**</span></span>|<span data-ttu-id="68f50-131">HTTP ストレージへの転送ごとに要する平均マイクロ秒数。</span><span class="sxs-lookup"><span data-stu-id="68f50-131">The average number of microseconds it takes to do each transfer to the HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-132">**Outstanding HTTP Storage I/O**</span><span class="sxs-lookup"><span data-stu-id="68f50-132">**Outstanding HTTP Storage I/O**</span></span>|<span data-ttu-id="68f50-133">HTTP ストレージに対する未処理 I/O の合計数。</span><span class="sxs-lookup"><span data-stu-id="68f50-133">The total number of outstanding I/Os towards a HTTP storage.</span></span>|  
|<span data-ttu-id="68f50-134">**HTTP ストレージの i/o 再試行数/秒**</span><span class="sxs-lookup"><span data-stu-id="68f50-134">**HTTP Storage I/O Retry/sec**</span></span>|<span data-ttu-id="68f50-135">HTTP ストレージに送信された 1 秒あたりの再試行要求数。</span><span class="sxs-lookup"><span data-stu-id="68f50-135">Number of retry requests sent to the HTTP storage per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68f50-136">参照</span><span class="sxs-lookup"><span data-stu-id="68f50-136">See Also</span></span>  
 [<span data-ttu-id="68f50-137">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="68f50-137">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
