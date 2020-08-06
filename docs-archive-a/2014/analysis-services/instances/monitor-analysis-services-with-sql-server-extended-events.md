---
title: SQL Server 拡張イベント (Xevent) を使用して Analysis Services を監視する |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d12d9bc8d6a56702e1b44f8404b25681a1033f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642999"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a><span data-ttu-id="75246-102">SQL Server 拡張イベント (XEvent) を使用した Analysis Services の監視</span><span class="sxs-lookup"><span data-stu-id="75246-102">Use SQL Server Extended Events (XEvents) to Monitor Analysis Services</span></span>
  <span data-ttu-id="75246-103">Analysis Services は、[拡張イベント](../../relational-databases/extended-events/extended-events.md)を使用してトレース機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="75246-103">Analysis Services provides tracing capabilities through the usage of [Extended Events](../../relational-databases/extended-events/extended-events.md).</span></span>  
  
 <span data-ttu-id="75246-104">拡張イベントは、高い拡張性と柔軟な構成を備えた、サーバー システムのためのイベント インフラストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="75246-104">Extended Events is an event infrastructure that is highly scalable and configurable for server systems.</span></span> <span data-ttu-id="75246-105">拡張イベントは軽量なパフォーマンス監視システムであり、使用されるパフォーマンス リソースはごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="75246-105">Extended Events is a light weight performance monitoring system that uses very few performance resources.</span></span>  
  
 <span data-ttu-id="75246-106">Xevent を通じて、すべての Analysis Services イベントをキャプチャし、[拡張イベント](../../relational-databases/extended-events/extended-events.md)で定義されている特定のコンシューマーを対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="75246-106">All Analysis Services events can be captured and target to specific consumers, as defined in [Extended Events](../../relational-databases/extended-events/extended-events.md), through XEvents.</span></span>  
  
## <a name="initiating-extended-events-in-analysis-services"></a><span data-ttu-id="75246-107">Analysis Services での拡張イベントの開始</span><span class="sxs-lookup"><span data-stu-id="75246-107">Initiating Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="75246-108">拡張イベントのトレースは、以下のような XMLA のオブジェクト作成スクリプト コマンドを使用して有効にします。</span><span class="sxs-lookup"><span data-stu-id="75246-108">Extended Event tracing is enabled using a similar XMLA create object script command as shown below:</span></span>  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="75246-109">ユーザーは、トレースのニーズに応じて、次の要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="75246-109">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="75246-110">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="75246-110">*trace_id*</span></span>  
 <span data-ttu-id="75246-111">このトレースの一意識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="75246-111">Defines the unique identifier for this trace.</span></span>  
  
 <span data-ttu-id="75246-112">*trace_name*</span><span class="sxs-lookup"><span data-stu-id="75246-112">*trace_name*</span></span>  
 <span data-ttu-id="75246-113">このトレースに付ける名前を指定します (通常は、人間が判読できるトレースの定義です)。</span><span class="sxs-lookup"><span data-stu-id="75246-113">The name given to this trace; usually a human readable definition of the trace.</span></span> <span data-ttu-id="75246-114">*trace_id* の値を名前として使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="75246-114">It is a common practice to use the *trace_id* value as the name.</span></span>  
  
 <span data-ttu-id="75246-115">*AS_event*</span><span class="sxs-lookup"><span data-stu-id="75246-115">*AS_event*</span></span>  
 <span data-ttu-id="75246-116">公開する Analysis Services イベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="75246-116">The Analysis Services event to be exposed.</span></span> <span data-ttu-id="75246-117">イベントの名前については、「 [Analysis Services トレース イベント](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75246-117">See [Analysis Services Trace Events](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) for names of the events.</span></span>  
  
 <span data-ttu-id="75246-118">*data_filename*</span><span class="sxs-lookup"><span data-stu-id="75246-118">*data_filename*</span></span>  
 <span data-ttu-id="75246-119">イベント データを含むファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="75246-119">The name of the file that contains the events data.</span></span> <span data-ttu-id="75246-120">この名前には、トレースを繰り返し送信する場合にデータが上書きされないように、タイムスタンプを使用したサフィックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="75246-120">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
 <span data-ttu-id="75246-121">*metadata_filename*</span><span class="sxs-lookup"><span data-stu-id="75246-121">*metadata_filename*</span></span>  
 <span data-ttu-id="75246-122">イベント メタデータを含むファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="75246-122">The name of the file that contains the events metadata.</span></span> <span data-ttu-id="75246-123">この名前には、トレースを繰り返し送信する場合にデータが上書きされないように、タイムスタンプを使用したサフィックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="75246-123">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
## <a name="stopping-extended-events-in-analysis-services"></a><span data-ttu-id="75246-124">Analysis Services での拡張イベントの停止</span><span class="sxs-lookup"><span data-stu-id="75246-124">Stopping Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="75246-125">拡張イベントのトレース オブジェクトを停止するには、以下のような XMLA のオブジェクト削除スクリプト コマンドを使用して、そのオブジェクトを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75246-125">To stop the Extended Events tracing object you need to delete that object using a similar XMLA delete object script command as shown below:</span></span>  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="75246-126">ユーザーは、トレースのニーズに応じて、次の要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="75246-126">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="75246-127">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="75246-127">*trace_id*</span></span>  
 <span data-ttu-id="75246-128">削除するトレースの一意識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="75246-128">Defines the unique identifier for the trace to be deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75246-129">参照</span><span class="sxs-lookup"><span data-stu-id="75246-129">See Also</span></span>  
 [<span data-ttu-id="75246-130">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="75246-130">Extended Events</span></span>](../../relational-databases/extended-events/extended-events.md)  
  
  
