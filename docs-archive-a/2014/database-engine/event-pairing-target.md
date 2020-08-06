---
title: イベントペアリングターゲット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a1a6beb1c6996e6e12f16c4555fd9dfcab97617d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716622"
---
# <a name="event-pairing-target"></a><span data-ttu-id="85a51-102">イベント ペアリング ターゲット</span><span class="sxs-lookup"><span data-stu-id="85a51-102">Event Pairing Target</span></span>
  <span data-ttu-id="85a51-103">イベント ペアリング ターゲットは、各イベントに存在する単一列または複数列のデータを使って 2 つのイベントを照合します。</span><span class="sxs-lookup"><span data-stu-id="85a51-103">The event pairing target matches two events using one or more columns of data that are present in each event.</span></span> <span data-ttu-id="85a51-104">ロックの取得とロックの解放など、対で発生するイベントが数多く存在します。</span><span class="sxs-lookup"><span data-stu-id="85a51-104">Many events come in pairs, for example, lock acquires and lock releases.</span></span> <span data-ttu-id="85a51-105">イベント シーケンスが対で発生した後は、両方のイベントが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-105">After an event sequence is paired, both events are discarded.</span></span> <span data-ttu-id="85a51-106">一対のイベントを破棄することによって、取得されたまま解放されていないロックを容易に検出できます。</span><span class="sxs-lookup"><span data-stu-id="85a51-106">Discarding matched sets allows for easy detection of lock acquisitions that have not been released.</span></span>  
  
 <span data-ttu-id="85a51-107">イベント レベルのフィルターを使用すると、設定済みの条件に合致しないイベントだけを、ペアリング ターゲットを使ってキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="85a51-107">By using event-level filters, the pairing target can be used to only capture events that do not match pre-set criteria.</span></span>  
  
 <span data-ttu-id="85a51-108">イベント ペアリング ターゲットを使用する場合は、照合に使用する列のシーケンスのほか、照合する 2 つのイベントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="85a51-108">When you use the event pairing target, you can choose two events that will be matched, together with a sequence of columns to perform the matching on.</span></span> <span data-ttu-id="85a51-109">このシーケンス内のすべての列は、同じ型であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="85a51-109">All the columns in this sequence must be of the same type.</span></span>  
  
 <span data-ttu-id="85a51-110">次の表では、イベント ペアリングの構成に使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="85a51-110">The following table describes the available options for configuring event pairing.</span></span>  
  
|<span data-ttu-id="85a51-111">オプション</span><span class="sxs-lookup"><span data-stu-id="85a51-111">Option</span></span>|<span data-ttu-id="85a51-112">使用できる値</span><span class="sxs-lookup"><span data-stu-id="85a51-112">Allowed values</span></span>|<span data-ttu-id="85a51-113">説明</span><span class="sxs-lookup"><span data-stu-id="85a51-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="85a51-114">begin_event</span><span class="sxs-lookup"><span data-stu-id="85a51-114">begin_event</span></span>|<span data-ttu-id="85a51-115">現在のセッションに存在する任意のイベント名。</span><span class="sxs-lookup"><span data-stu-id="85a51-115">Any event name that is present in the current session.</span></span>|<span data-ttu-id="85a51-116">対で発生するイベントのうち最初に発生するイベントの名前です。</span><span class="sxs-lookup"><span data-stu-id="85a51-116">The event name specifying the beginning event in a paired sequence.</span></span>|  
|<span data-ttu-id="85a51-117">end_event</span><span class="sxs-lookup"><span data-stu-id="85a51-117">end_event</span></span>|<span data-ttu-id="85a51-118">現在のセッションに存在する任意のイベント名。</span><span class="sxs-lookup"><span data-stu-id="85a51-118">Any event name that is present in the current session.</span></span>|<span data-ttu-id="85a51-119">対で発生するイベントのうち最後に発生するイベントの名前です。</span><span class="sxs-lookup"><span data-stu-id="85a51-119">The event name specifying the ending event in a paired sequence.</span></span>|  
|<span data-ttu-id="85a51-120">begin_matching_columns</span><span class="sxs-lookup"><span data-stu-id="85a51-120">begin_matching_columns</span></span>|<span data-ttu-id="85a51-121">コンマ区切りで順に指定された列名。</span><span class="sxs-lookup"><span data-stu-id="85a51-121">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="85a51-122">照合に使用する列です。</span><span class="sxs-lookup"><span data-stu-id="85a51-122">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="85a51-123">end_matching_columns</span><span class="sxs-lookup"><span data-stu-id="85a51-123">end_matching_columns</span></span>|<span data-ttu-id="85a51-124">コンマ区切りで順に指定された列名。</span><span class="sxs-lookup"><span data-stu-id="85a51-124">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="85a51-125">照合に使用する列です。</span><span class="sxs-lookup"><span data-stu-id="85a51-125">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="85a51-126">begin_matching_actions</span><span class="sxs-lookup"><span data-stu-id="85a51-126">begin_matching_actions</span></span>|<span data-ttu-id="85a51-127">コンマ区切りで順に指定されたアクション。</span><span class="sxs-lookup"><span data-stu-id="85a51-127">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="85a51-128">照合に使用するアクションです。</span><span class="sxs-lookup"><span data-stu-id="85a51-128">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="85a51-129">end_matching_actions</span><span class="sxs-lookup"><span data-stu-id="85a51-129">end_matching_actions</span></span>|<span data-ttu-id="85a51-130">コンマ区切りで順に指定されたアクション。</span><span class="sxs-lookup"><span data-stu-id="85a51-130">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="85a51-131">照合に使用するアクションです。</span><span class="sxs-lookup"><span data-stu-id="85a51-131">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="85a51-132">respond_to_memory_pressure</span><span class="sxs-lookup"><span data-stu-id="85a51-132">respond_to_memory_pressure</span></span>|<span data-ttu-id="85a51-133">次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="85a51-133">One of the following values:</span></span><br /><br /> <span data-ttu-id="85a51-134">0 = 応答しません。</span><span class="sxs-lookup"><span data-stu-id="85a51-134">0 = Do not respond.</span></span><br /><br /> <span data-ttu-id="85a51-135">1 = メモリが不足している場合、対になっていないイベントを新たに追加することはしません。</span><span class="sxs-lookup"><span data-stu-id="85a51-135">1 = Stop adding new orphans to the list when there is memory pressure.</span></span>|<span data-ttu-id="85a51-136">ターゲットは、メモリ イベントに応答します。</span><span class="sxs-lookup"><span data-stu-id="85a51-136">The target response to memory events.</span></span> <span data-ttu-id="85a51-137">1 に設定した場合、サーバーのメモリが不足すると、それまで保持されていた、対になっていない情報は削除されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-137">If set to 1 and the server is low on memory, unpaired information that is being maintained is removed.</span></span>|  
|<span data-ttu-id="85a51-138">max_orphans</span><span class="sxs-lookup"><span data-stu-id="85a51-138">max_orphans</span></span>||<span data-ttu-id="85a51-139">ターゲットで収集される、対になっていないイベントの合計数を指定します。</span><span class="sxs-lookup"><span data-stu-id="85a51-139">Specifies the total number of unpaired events that will be collected in the target.</span></span> <span data-ttu-id="85a51-140">制限に達すると、対になっていないイベントは先入れ先出し (FIFO) 順で削除されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-140">Once the limit is reached, unpaired events are removed on a first-in, first-out (FIFO) basis.</span></span> <span data-ttu-id="85a51-141">既定値は 10,000 です。</span><span class="sxs-lookup"><span data-stu-id="85a51-141">Default = 10,000.</span></span>|  
  
 <span data-ttu-id="85a51-142">イベントに関連付けられているすべてのデータはキャプチャされて、その後のペアリングに備えて保存されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-142">All the data associated with an event is captured and stored for future pairing.</span></span> <span data-ttu-id="85a51-143">また、アクションによって追加されたデータも収集されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-143">In addition, data added by actions is also collected.</span></span> <span data-ttu-id="85a51-144">収集されたイベント データはメモリに格納されるため、格納できるサイズには上限があります。</span><span class="sxs-lookup"><span data-stu-id="85a51-144">The collected event data is stored in memory, and therefore has a finite limit.</span></span> <span data-ttu-id="85a51-145">この制限は、システムの容量とアクティビティに依存します。</span><span class="sxs-lookup"><span data-stu-id="85a51-145">This limit is based on system capacity and activity.</span></span> <span data-ttu-id="85a51-146">使用メモリ量は利用可能なシステム リソースに基づくため、使用可能な最大メモリ量をパラメーターとして指定することはありません。</span><span class="sxs-lookup"><span data-stu-id="85a51-146">Instead of taking the maximum amount of memory to be used as a parameter, the amount of memory used will be based on available system resources.</span></span> <span data-ttu-id="85a51-147">システム リソースが不足した場合、それまで保持されていた、対になっていないイベントは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-147">When these are not available, unpaired events that have been retained will be dropped.</span></span> <span data-ttu-id="85a51-148">イベントが対になっておらず破棄された場合、照合イベントは、対になっていないイベントとして発生します。</span><span class="sxs-lookup"><span data-stu-id="85a51-148">If an event has not been paired and is dropped, the matching event will appear as an unpaired event.</span></span>  
  
 <span data-ttu-id="85a51-149">対になっていないイベントは、ペアリング ターゲットによって XML 形式にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="85a51-149">The pairing target serializes unpaired events to an XML format.</span></span> <span data-ttu-id="85a51-150">この形式は、いずれのスキーマにも準拠しません。</span><span class="sxs-lookup"><span data-stu-id="85a51-150">This format does not conform to any schema.</span></span> <span data-ttu-id="85a51-151">この形式に含まれる要素は 2 種類だけです。</span><span class="sxs-lookup"><span data-stu-id="85a51-151">The format only contains two element types.</span></span> <span data-ttu-id="85a51-152">**\<unpaired>** 要素はルートで、その後に1が続きます。</span><span class="sxs-lookup"><span data-stu-id="85a51-152">The **\<unpaired>** element is the root, followed by one.</span></span> <span data-ttu-id="85a51-153">**\<event>** 現在追跡されている対になっていない各イベントの要素。</span><span class="sxs-lookup"><span data-stu-id="85a51-153">**\<event>** element for each unpaired event that is currently being tracked.</span></span> <span data-ttu-id="85a51-154">要素には、対になってい **\<event>** ないイベントの名前を含む属性が1つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="85a51-154">The **\<event>** element contains one attribute that contains the name of the unpaired event.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="85a51-155">セッションへのターゲットの追加</span><span class="sxs-lookup"><span data-stu-id="85a51-155">Adding the Target to a Session</span></span>  
 <span data-ttu-id="85a51-156">ペア照合ターゲットを拡張イベント セッションに追加するには、イベント セッションの作成時または変更時に次のステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="85a51-156">To add the pair matching target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 <span data-ttu-id="85a51-157">この後に、最初と最後のイベント、および照合するアクションまたは列を定義する SET ステートメントを続けます。</span><span class="sxs-lookup"><span data-stu-id="85a51-157">You would follow this with a SET statement, to define the beginning and ending events, and which actions or columns to match.</span></span> <span data-ttu-id="85a51-158">以下は、sqlserver.lock_acquired イベントと sqlserver.lock_released イベントのペア照合のサンプル構文です。</span><span class="sxs-lookup"><span data-stu-id="85a51-158">The following example shows sample syntax for pair matching the sqlserver.lock_acquired and sqlserver.lock_released events.</span></span>  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 <span data-ttu-id="85a51-159">詳細については、「 [ロックを保持しているクエリの特定](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85a51-159">For more information, see [Determine Which Queries Are Holding Locks](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="85a51-160">ターゲット出力の確認</span><span class="sxs-lookup"><span data-stu-id="85a51-160">Reviewing the Target Output</span></span>  
 <span data-ttu-id="85a51-161">ペア照合ターゲットの出力を確認するには、次のクエリを使用します。 *session_name* をイベント セッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="85a51-161">To review the output for the pair matching target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="85a51-162">次の例は、ペアリング ターゲットの出力形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="85a51-162">The following example shows the pairing target output format.</span></span>  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85a51-163">参照</span><span class="sxs-lookup"><span data-stu-id="85a51-163">See Also</span></span>  
 <span data-ttu-id="85a51-164">[SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="85a51-164">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="85a51-165">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="85a51-165">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="85a51-166">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="85a51-166">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="85a51-167">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85a51-167">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
