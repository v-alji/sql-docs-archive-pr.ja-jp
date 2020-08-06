---
title: リングバッファーターゲット |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 186e847bb9f9b621543119c25510dc5d6107e274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644118"
---
# <a name="ring-buffer-target"></a><span data-ttu-id="6d8c3-102">リング バッファー ターゲット</span><span class="sxs-lookup"><span data-stu-id="6d8c3-102">Ring Buffer Target</span></span>
  <span data-ttu-id="6d8c3-103">リング バッファー ターゲットは、メモリにイベント データを一時的に保持します。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-103">The ring buffer target briefly holds event data in memory.</span></span> <span data-ttu-id="6d8c3-104">このターゲットでは、2 種類のモードのいずれかでイベントを管理できます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-104">This target can manage events in one of two modes.</span></span>  
  
-   <span data-ttu-id="6d8c3-105">1 つ目のモードは厳密な先入れ先出し (FIFO) です。このモードでは、ターゲットに割り当てられたメモリがすべて使用されると、最も古いイベントが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-105">The first mode is strict first-in first-out (FIFO), where the oldest event is discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="6d8c3-106">このモード (既定値) では、occurrence_number オプションは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-106">In this mode (the default), the occurrence_number option is set to 0.</span></span>  
  
-   <span data-ttu-id="6d8c3-107">2 つ目のモードはイベントごとの FIFO です。このモードでは、各種イベントが指定した数だけ保持されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-107">The second mode is per-event FIFO, where a specified number of events of each type is kept.</span></span> <span data-ttu-id="6d8c3-108">このモードでは、ターゲットに割り当てられたすべてのメモリが使用されると、各種類の最も古いイベントが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-108">In this mode, the oldest events of each type are discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="6d8c3-109">occurrence_number オプションを構成して、種類ごとに保持するイベントの数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-109">You can configure the occurrence_number option to specify the number of events of each type to keep.</span></span>  
  
 <span data-ttu-id="6d8c3-110">次の表では、リング バッファー ターゲットの構成に使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-110">The following table describes the available options for configuring the ring buffer target.</span></span>  
  
|<span data-ttu-id="6d8c3-111">オプション</span><span class="sxs-lookup"><span data-stu-id="6d8c3-111">Option</span></span>|<span data-ttu-id="6d8c3-112">使用できる値</span><span class="sxs-lookup"><span data-stu-id="6d8c3-112">Allowed values</span></span>|<span data-ttu-id="6d8c3-113">説明</span><span class="sxs-lookup"><span data-stu-id="6d8c3-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="6d8c3-114">max_memory</span><span class="sxs-lookup"><span data-stu-id="6d8c3-114">max_memory</span></span>|<span data-ttu-id="6d8c3-115">任意の32ビット整数。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-115">Any 32-bit integer.</span></span> <span data-ttu-id="6d8c3-116">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-116">This value is optional.</span></span>|<span data-ttu-id="6d8c3-117">使用するメモリの最大量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-117">The maximum amount of memory in kilobytes (KB) to use.</span></span> <span data-ttu-id="6d8c3-118">max_event_limit と max_memory のうち先に制限に達した方に基づいて、既存のイベントが削除されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-118">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="6d8c3-119">最大値は 4194303 KB です。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-119">The maximum value is 4194303 KB.</span></span> <span data-ttu-id="6d8c3-120">では、他のメモリコンシューマーに影響を与える可能性があるため、リングバッファーサイズを GB 範囲の制限に設定する前に、慎重に考慮する必要があり SQL Server</span><span class="sxs-lookup"><span data-stu-id="6d8c3-120">A careful consideration should be made before setting the ring buffer size to limits in the GB range as it may impact other memory consumers in SQL Server</span></span>|  
|<span data-ttu-id="6d8c3-121">max_event_limit</span><span class="sxs-lookup"><span data-stu-id="6d8c3-121">max_event_limit</span></span>|<span data-ttu-id="6d8c3-122">任意の32ビット整数。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-122">Any 32-bit integer.</span></span> <span data-ttu-id="6d8c3-123">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-123">This value is optional.</span></span>|<span data-ttu-id="6d8c3-124">ring_buffer に保持されるイベントの最大数。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-124">The maximum number of events kept in the ring_buffer.</span></span> <span data-ttu-id="6d8c3-125">max_event_limit と max_memory のうち先に制限に達した方に基づいて、既存のイベントが削除されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-125">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="6d8c3-126">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-126">Default = 1000.</span></span>|  
|<span data-ttu-id="6d8c3-127">occurrence_number</span><span class="sxs-lookup"><span data-stu-id="6d8c3-127">occurrence_number</span></span>|<span data-ttu-id="6d8c3-128">次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-128">One of the following values:</span></span><br /><br /> <span data-ttu-id="6d8c3-129">0 (既定値) = ターゲットに割り当てられたメモリがすべて使用されると、最も古いイベントが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-129">0 (the default) = Oldest event is discarded when all the memory allocated to the target is used.</span></span><br /><br /> <span data-ttu-id="6d8c3-130">任意の32ビット整数 = イベントごとの FIFO で破棄されるまでに、各種類のイベントの数を保持します。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-130">Any 32-bit integer = The number of events of each type to keep before being discarded on a per-event FIFO basis.</span></span><br /><br /> <br /><br /> <span data-ttu-id="6d8c3-131">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-131">This value is optional.</span></span>|<span data-ttu-id="6d8c3-132">使用する FIFO モード。0 を超える値に設定した場合は、種類ごとにバッファーに保持するイベントの数を表します。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-132">The FIFO mode to use, and, if set to a value greater than 0, the preferred number of events of each type to keep in the buffer.</span></span>|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="6d8c3-133">セッションへのターゲットの追加</span><span class="sxs-lookup"><span data-stu-id="6d8c3-133">Adding the Target to a Session</span></span>  
 <span data-ttu-id="6d8c3-134">リング バッファー ターゲットを拡張イベント セッションに追加するには、イベント セッションの作成時または変更時に次のステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-134">To add the ring buffer target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="6d8c3-135">ターゲット出力の確認</span><span class="sxs-lookup"><span data-stu-id="6d8c3-135">Reviewing the Target Output</span></span>  
 <span data-ttu-id="6d8c3-136">リング バッファー ターゲットの出力を確認するには、次のクエリを使用します。 *session_name* をイベント セッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-136">To review the output from the ring buffer target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="6d8c3-137">次の例は、リング バッファー ターゲットの出力形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d8c3-137">The following example shows the ring buffer target output format.</span></span>  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a><span data-ttu-id="6d8c3-138">参照</span><span class="sxs-lookup"><span data-stu-id="6d8c3-138">See Also</span></span>

- [<span data-ttu-id="6d8c3-139">SQL Server 拡張イベント ターゲット</span><span class="sxs-lookup"><span data-stu-id="6d8c3-139">SQL Server Extended Events Targets</span></span>](../../2014/database-engine/sql-server-extended-events-targets.md)
- [<span data-ttu-id="6d8c3-140">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6d8c3-140">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="6d8c3-141">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6d8c3-141">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="6d8c3-142">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6d8c3-142">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

