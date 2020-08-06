---
title: イベントカウンターターゲット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f540f39176ec638cdc9236b315e306ecebfdcb1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716630"
---
# <a name="event-counter-target"></a><span data-ttu-id="938aa-102">イベント カウンター ターゲット</span><span class="sxs-lookup"><span data-stu-id="938aa-102">Event Counter Target</span></span>
  <span data-ttu-id="938aa-103">イベント カウンター ターゲットは、拡張イベント セッション中に発生したすべてのイベントをカウントします。</span><span class="sxs-lookup"><span data-stu-id="938aa-103">The event counter target counts all events that occur during an Extended Events session.</span></span> <span data-ttu-id="938aa-104">イベント カウンター ターゲットを使用すると、完全なイベント コレクションのオーバーヘッドを追加することなく負荷の特性に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="938aa-104">By using the event counter target, you can obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="938aa-105">このターゲットには、カスタマイズ可能なパラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="938aa-105">This target has no customizable parameters.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="938aa-106">セッションへのターゲットの追加</span><span class="sxs-lookup"><span data-stu-id="938aa-106">Adding the Target to a Session</span></span>  
 <span data-ttu-id="938aa-107">イベント カウンター ターゲットを拡張イベント セッションに追加するには、イベント セッションの作成時または変更時に次のステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="938aa-107">To add the event counter target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="938aa-108">ターゲット出力の確認</span><span class="sxs-lookup"><span data-stu-id="938aa-108">Reviewing the Target Output</span></span>  
 <span data-ttu-id="938aa-109">イベント カウンター ターゲットの出力を確認するには、 *session_name* をイベント セッションの名前に置き換えて、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="938aa-109">To review the output from the event counter target, you can use the following query, replacing *session_name* with the name of the event session:</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="938aa-110">次の例は、イベント カウンター ターゲットの出力形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="938aa-110">The following example shows the event counter target output format.</span></span>  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a><span data-ttu-id="938aa-111">参照</span><span class="sxs-lookup"><span data-stu-id="938aa-111">See Also</span></span>  
 <span data-ttu-id="938aa-112">[SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="938aa-112">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="938aa-113">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="938aa-113">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="938aa-114">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="938aa-114">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="938aa-115">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="938aa-115">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
