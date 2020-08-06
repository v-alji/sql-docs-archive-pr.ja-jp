---
title: ヒストグラムターゲット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- bucketing target [SQL Server extended events]
- event bucketing target
- targets [SQL Server extended events], bucketing
ms.assetid: 2ea39141-7eb0-4c74-abf8-114c2c106a19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: acb124ef949849561a6bca0ba4016b40c1343384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715690"
---
# <a name="histogram-target"></a><span data-ttu-id="f8f6c-102">ヒストグラムのターゲット</span><span class="sxs-lookup"><span data-stu-id="f8f6c-102">Histogram Target</span></span>
  <span data-ttu-id="f8f6c-103">ヒストグラム ターゲットは、イベント データに基づいて、特定の種類のイベントの発生をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-103">The histogram target groups occurrences of a specific event type based on event data.</span></span> <span data-ttu-id="f8f6c-104">イベントのグループは、指定されたイベント列またはアクションに基づいてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-104">The groupings of events are counted based on a specified event column or action.</span></span> <span data-ttu-id="f8f6c-105">ヒストグラム ターゲットを使用して、パフォーマンス上の問題のトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-105">You can use the histogram target to troubleshoot performance issues.</span></span> <span data-ttu-id="f8f6c-106">どのイベントが最もよく発生するかを識別することで、パフォーマンス上の問題を引き起こす可能性を示す "ホットスポット" を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-106">By identifying which events are occurring most frequently, you can find "hotspots" that indicate a potential cause of a performance problem.</span></span>  
  
 <span data-ttu-id="f8f6c-107">次の表では、ヒストグラム ターゲットの構成に使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-107">The following table describes the options that can be used to configure the histogram target.</span></span>  
  
|<span data-ttu-id="f8f6c-108">オプション</span><span class="sxs-lookup"><span data-stu-id="f8f6c-108">Option</span></span>|<span data-ttu-id="f8f6c-109">使用できる値</span><span class="sxs-lookup"><span data-stu-id="f8f6c-109">Allowed values</span></span>|<span data-ttu-id="f8f6c-110">説明</span><span class="sxs-lookup"><span data-stu-id="f8f6c-110">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="f8f6c-111">slots</span><span class="sxs-lookup"><span data-stu-id="f8f6c-111">slots</span></span>|<span data-ttu-id="f8f6c-112">任意の整数値。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-112">Any integer value.</span></span> <span data-ttu-id="f8f6c-113">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-113">This value is optional.</span></span>|<span data-ttu-id="f8f6c-114">保持するグループの最大数を示すユーザー指定の値。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-114">A user-specified value indicating the maximum number of groupings to retain.</span></span> <span data-ttu-id="f8f6c-115">この値に達した場合、既存のグループに属していない新しいイベントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-115">When this value is reached, new events that do not belong to the existing groups are ignored.</span></span><br /><br /> <span data-ttu-id="f8f6c-116">パフォーマンス向上のために、スロット数は 2 の次の累乗に切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-116">Note that to improve performance, the slot number is rounded up to the next power of 2.</span></span>|  
|<span data-ttu-id="f8f6c-117">filtering_event_name</span><span class="sxs-lookup"><span data-stu-id="f8f6c-117">filtering_event_name</span></span>|<span data-ttu-id="f8f6c-118">拡張イベント セッション内に存在するすべてのイベント。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-118">Any event present in the Extended Events session.</span></span> <span data-ttu-id="f8f6c-119">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-119">This value is optional.</span></span>|<span data-ttu-id="f8f6c-120">イベントのクラスを識別するためのユーザー指定の値。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-120">A user-specified value that is used to identify a class of events.</span></span> <span data-ttu-id="f8f6c-121">指定されたイベントのインスタンスだけがバケット化されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-121">Only instances of the specified event are bucketed.</span></span> <span data-ttu-id="f8f6c-122">それ以外のすべてのイベントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-122">All other events are ignored.</span></span><br /><br /> <span data-ttu-id="f8f6c-123">この値は、 *package_name*.*event_name*形式で指定する必要があります &#40;例: `'sqlserver.checkpoint_end'`&#41;。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-123">If you specify this value, you must use the format: *package_name*.*event_name*, for example `'sqlserver.checkpoint_end'`.</span></span> <span data-ttu-id="f8f6c-124">次のクエリを使用すると、パッケージ名を特定できます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-124">You can identify the package name by using the following query:</span></span><br /><br /> <span data-ttu-id="f8f6c-125">[P.name, se. event_name] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-125">SELECT p.name, se.event_name</span></span><br /><span data-ttu-id="f8f6c-126">Dm_xe_session_events se から</span><span class="sxs-lookup"><span data-stu-id="f8f6c-126">FROM sys.dm_xe_session_events se</span></span><br /><span data-ttu-id="f8f6c-127">Dm_xe_packages p に参加する</span><span class="sxs-lookup"><span data-stu-id="f8f6c-127">JOIN sys.dm_xe_packages p</span></span><br /><span data-ttu-id="f8f6c-128">Se_event_package_guid = p guid</span><span class="sxs-lookup"><span data-stu-id="f8f6c-128">ON se_event_package_guid = p.guid</span></span><br /><span data-ttu-id="f8f6c-129">ORDER BY p.name, se. event_name</span><span class="sxs-lookup"><span data-stu-id="f8f6c-129">ORDER BY p.name, se.event_name</span></span><br /><br /> <br /><br /> <span data-ttu-id="f8f6c-130">filtering_event_name 値を指定しない場合は、source_type を 1 (既定値) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-130">If you do not specify the filtering_event_name value, source_type must be set to 1 (the default).</span></span>|  
|<span data-ttu-id="f8f6c-131">source_type</span><span class="sxs-lookup"><span data-stu-id="f8f6c-131">source_type</span></span>|<span data-ttu-id="f8f6c-132">バケットの基になっているオブジェクトの種類。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-132">The type of object that the bucket is based on.</span></span> <span data-ttu-id="f8f6c-133">この値は省略可能で、指定しない場合は既定値 1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-133">This value is optional and if not specified has a default value of 1.</span></span>|<span data-ttu-id="f8f6c-134">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-134">Can have one of the following values:</span></span><br /><br /> <span data-ttu-id="f8f6c-135">0 (イベントの場合)</span><span class="sxs-lookup"><span data-stu-id="f8f6c-135">0 for an event</span></span><br /><br /> <span data-ttu-id="f8f6c-136">1 (アクションの場合)</span><span class="sxs-lookup"><span data-stu-id="f8f6c-136">1 for an action</span></span>|  
|<span data-ttu-id="f8f6c-137">source</span><span class="sxs-lookup"><span data-stu-id="f8f6c-137">source</span></span>|<span data-ttu-id="f8f6c-138">イベント列またはアクション名。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-138">Event column or action name.</span></span>|<span data-ttu-id="f8f6c-139">データ ソースとして使用されるイベント列またはアクション名です。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-139">The event column or action name that is used as the data source.</span></span><br /><br /> <span data-ttu-id="f8f6c-140">source に対してイベント列を指定する場合は、filtering_event_name 値に使用されているイベントの列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-140">When you specify an event column for source, you must specify a column from the event that is used for the filtering_event_name value.</span></span> <span data-ttu-id="f8f6c-141">次のクエリを使用すると、使用できる列を特定できます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-141">You can identify the potential columns by using the following query:</span></span><br /><br /> <span data-ttu-id="f8f6c-142">[名前] を [sys. dm_xe_object_columns から選択します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-142">SELECT name FROM sys.dm_xe_object_columns</span></span><br /><span data-ttu-id="f8f6c-143">WHERE object_name = ' \<eventname> '</span><span class="sxs-lookup"><span data-stu-id="f8f6c-143">WHERE object_name = '\<eventname>'</span></span><br /><span data-ttu-id="f8f6c-144">と column_type! = ' readonly '</span><span class="sxs-lookup"><span data-stu-id="f8f6c-144">AND column_type != 'readonly'</span></span><br /><br /> <span data-ttu-id="f8f6c-145">source に対してイベント列を指定する場合は、パッケージ名を source 値に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-145">When you specify an event column for source, you do not have to include the package name in the source value.</span></span><br /><br /> <span data-ttu-id="f8f6c-146">source に対してアクション名を指定する場合は、このターゲットが使用されているイベント セッションのコレクションに対して構成されているいずれかのアクションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-146">When you specify an action name for source, you must use one of the actions that is configured for collection in the event session for which this target is being used.</span></span> <span data-ttu-id="f8f6c-147">アクション名に使用できる値を調べるには、sys.dm_xe_sesssion_event_actions ビューの action_name 列に対するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-147">To find potential values for the action name, you can query the action_name column of the sys.dm_xe_sesssion_event_actions view.</span></span><br /><br /> <span data-ttu-id="f8f6c-148">アクション名をデータ ソースとして使用している場合は、 *package_name*.*action_name*形式で source 値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-148">If you are using an action name as the data source, you must specify the source value by using the format: *package_name*.*action_name*.</span></span>|  
  
 <span data-ttu-id="f8f6c-149">次の例では、ヒストグラム ターゲットによるデータ収集のしくみの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-149">The following example illustrates at a high level how the histogram target collects data.</span></span> <span data-ttu-id="f8f6c-150">この例では、ヒストグラム ターゲットを使用して、待機が何回発生したかを待機の種類別にカウントします。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-150">In this example, you want to use the histogram target to count how many waits of each wait type occurred.</span></span> <span data-ttu-id="f8f6c-151">この場合、ヒストグラム ターゲットを定義するときに次のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-151">To do this, you would specify the following options when you define the histogram target:</span></span>  
  
-   <span data-ttu-id="f8f6c-152">filtering_event_name = 'wait_info'</span><span class="sxs-lookup"><span data-stu-id="f8f6c-152">filtering_event_name = 'wait_info'</span></span>  
  
-   <span data-ttu-id="f8f6c-153">source = 'wait_type'</span><span class="sxs-lookup"><span data-stu-id="f8f6c-153">source = 'wait_type'</span></span>  
  
-   <span data-ttu-id="f8f6c-154">source_type = 0 (wait_type がイベント列のため)</span><span class="sxs-lookup"><span data-stu-id="f8f6c-154">source_type = 0 (because wait_type is an event column)</span></span>  
  
 <span data-ttu-id="f8f6c-155">この例のシナリオでは、wait_type ソースに対して次のデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-155">In the example scenario, the following data is recorded for the wait_type source.</span></span>  
  
|<span data-ttu-id="f8f6c-156">フィルター イベント名</span><span class="sxs-lookup"><span data-stu-id="f8f6c-156">Filtering event name</span></span>|<span data-ttu-id="f8f6c-157">ソース列値</span><span class="sxs-lookup"><span data-stu-id="f8f6c-157">Source column value</span></span>|  
|--------------------------|-------------------------|  
|<span data-ttu-id="f8f6c-158">wait_info</span><span class="sxs-lookup"><span data-stu-id="f8f6c-158">wait_info</span></span>|<span data-ttu-id="f8f6c-159">file_io</span><span class="sxs-lookup"><span data-stu-id="f8f6c-159">file_io</span></span>|  
|<span data-ttu-id="f8f6c-160">wait_info</span><span class="sxs-lookup"><span data-stu-id="f8f6c-160">wait_info</span></span>|<span data-ttu-id="f8f6c-161">file_io</span><span class="sxs-lookup"><span data-stu-id="f8f6c-161">file_io</span></span>|  
|<span data-ttu-id="f8f6c-162">wait_info</span><span class="sxs-lookup"><span data-stu-id="f8f6c-162">wait_info</span></span>|<span data-ttu-id="f8f6c-163">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f8f6c-163">network</span></span>|  
|<span data-ttu-id="f8f6c-164">wait_info</span><span class="sxs-lookup"><span data-stu-id="f8f6c-164">wait_info</span></span>|<span data-ttu-id="f8f6c-165">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f8f6c-165">network</span></span>|  
|<span data-ttu-id="f8f6c-166">wait_info</span><span class="sxs-lookup"><span data-stu-id="f8f6c-166">wait_info</span></span>|<span data-ttu-id="f8f6c-167">sleep</span><span class="sxs-lookup"><span data-stu-id="f8f6c-167">sleep</span></span>|  
  
 <span data-ttu-id="f8f6c-168">待機の種類値は、次の値とスロット数を持つ 3 つのスロットに分類されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-168">The wait type values would be categorized into three slots, with the following values and slot counts:</span></span>  
  
|<span data-ttu-id="f8f6c-169">値</span><span class="sxs-lookup"><span data-stu-id="f8f6c-169">Value</span></span>|<span data-ttu-id="f8f6c-170">スロット数</span><span class="sxs-lookup"><span data-stu-id="f8f6c-170">Slot count</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="f8f6c-171">file_io</span><span class="sxs-lookup"><span data-stu-id="f8f6c-171">file_io</span></span>|<span data-ttu-id="f8f6c-172">2</span><span class="sxs-lookup"><span data-stu-id="f8f6c-172">2</span></span>|  
|<span data-ttu-id="f8f6c-173">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f8f6c-173">network</span></span>|<span data-ttu-id="f8f6c-174">2</span><span class="sxs-lookup"><span data-stu-id="f8f6c-174">2</span></span>|  
|<span data-ttu-id="f8f6c-175">sleep</span><span class="sxs-lookup"><span data-stu-id="f8f6c-175">sleep</span></span>|<span data-ttu-id="f8f6c-176">1</span><span class="sxs-lookup"><span data-stu-id="f8f6c-176">1</span></span>|  
  
 <span data-ttu-id="f8f6c-177">ヒストグラム ターゲットによって保持されるのは、指定されたソースのイベント データだけです。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-177">The histogram target only retains event data for the specified source.</span></span> <span data-ttu-id="f8f6c-178">イベント データが大きすぎて全体を保持することができない場合もあります。その場合は、データが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-178">In some cases the event data may be too large to retain completely, in which case the data is truncated.</span></span> <span data-ttu-id="f8f6c-179">イベント データが切り捨てられた場合、バイト数が記録されて、XML 出力として表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-179">When event data is truncated, the number of bytes is recorded and displayed as XML output.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="f8f6c-180">セッションへのターゲットの追加</span><span class="sxs-lookup"><span data-stu-id="f8f6c-180">Adding the Target to a Session</span></span>  
 <span data-ttu-id="f8f6c-181">ヒストグラム ターゲットを拡張イベント セッションに追加するには、目的のターゲットの種類に応じて、イベント セッションの作成時または変更時に次のいずれかのステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-181">To add the histogram target to an Extended Events session, you must include either of the following statements when you create or alter an event session, depending on the desired target type:</span></span>  
  
```  
ADD TARGET package0.histogram  
```  
  
 <span data-ttu-id="f8f6c-182">SET ステートメントを使用して、さまざまなオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-182">You can use the SET statement to set the various options.</span></span> <span data-ttu-id="f8f6c-183">次の例では、sqlserver.checkpoint_end イベントのデータを収集するヒストグラム ターゲットの追加方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-183">The following example shows the addition of the histogram target, where data for the sqlserver.checkpoint_end event is collected.</span></span>  
  
```  
ADD TARGET package0.histogram  
(SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id')  
```  
  
 <span data-ttu-id="f8f6c-184">詳細については、「 [ロックの大半を取得しているオブジェクトを見つける](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md)」と「 [拡張イベントを使用したシステムの使用状況の監視](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-184">For more information, see [Find the Objects That Have the Most Locks Taken on Them](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md), and [Monitor System Activity Using Extended Events](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="f8f6c-185">ターゲット出力の確認</span><span class="sxs-lookup"><span data-stu-id="f8f6c-185">Reviewing the Target Output</span></span>  
 <span data-ttu-id="f8f6c-186">ヒストグラム ターゲットは、呼び出し元のプログラムまたはプロシージャに対するデータを XML 形式でシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-186">The histogram target serializes data to a calling program or procedure in XML format.</span></span> <span data-ttu-id="f8f6c-187">ターゲット出力は、いずれのスキーマにも準拠しません。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-187">The target output does not conform to any schema.</span></span>  
  
 <span data-ttu-id="f8f6c-188">ヒストグラム ターゲットの出力を確認するには、次のクエリを使用します。 *session_name* をイベント セッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-188">To review the output from the histogram target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="f8f6c-189">次の例は、ヒストグラム ターゲットの出力形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8f6c-189">The following example illustrates histogram target output format.</span></span>  
  
```  
<Slots truncated = "0" buckets=[count]>  
    <Slot count=[count] trunc=[truncated bytes]>  
        <value>  
        </value>  
    </Slot>  
</Slots>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8f6c-190">参照</span><span class="sxs-lookup"><span data-stu-id="f8f6c-190">See Also</span></span>  
 <span data-ttu-id="f8f6c-191">[SQL Server 拡張イベント ターゲット](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="f8f6c-191">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="f8f6c-192">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8f6c-192">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="f8f6c-193">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8f6c-193">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="f8f6c-194">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f8f6c-194">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
