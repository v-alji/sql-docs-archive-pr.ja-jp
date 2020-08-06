---
title: affinity mask サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default affinity mask option
- reloading processor cache
- processor cache [SQL Server]
- CPU [SQL Server], licensing
- deferred process call
- affinity mask option
- processor affinity [SQL Server]
- SMP
- DPC
ms.assetid: 5823ba29-a75d-4b3e-ba7b-421c07ab3ac1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dfebde8a9431026e8faedb2a1e76eb2f2d82e207
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642315"
---
# <a name="affinity-mask-server-configuration-option"></a><span data-ttu-id="bbb17-102">affinity mask サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="bbb17-102">affinity mask Server Configuration Option</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="bbb17-103">代わりに [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-103">Use [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="bbb17-104">マルチタスクを実行するため、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows では、プロセス スレッドが別のプロセッサに移動される場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-104">To carry out multitasking, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sometimes move process threads among different processors.</span></span> <span data-ttu-id="bbb17-105">オペレーティング システムにとっては効率的であっても、この操作で各プロセッサのキャッシュに繰り返しデータが再読み込みされるため、システムの負荷が高くなり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-105">Although efficient from an operating system point of view, this activity can reduce [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performance under heavy system loads, as each processor cache is repeatedly reloaded with data.</span></span> <span data-ttu-id="bbb17-106">このような状況では、特定のスレッドにプロセッサを割り当てることで、プロセッサの再読み込みを回避し、プロセッサ間でのスレッドの移行回数を少なくできるため、コンテキストの切り替えを減らしてパフォーマンスを改善できます。このようなスレッドとプロセッサ間の関連付けを "プロセッサ関係 (processor affinity)" と言います。</span><span class="sxs-lookup"><span data-stu-id="bbb17-106">Assigning processors to specific threads can improve performance under these conditions by eliminating processor reloads and reducing thread migration across processors (thereby reducing context switching); such an association between a thread and a processor is called processor affinity.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="bbb17-107">では、affinity mask ( **CPU 関係マスク**とも呼ばれます) と affinity i/o mask の2つの affinity mask オプションにより、プロセッサ関係をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bbb17-107">supports processor affinity by means of two affinity mask options: affinity mask (also known as **CPU affinity mask**) and affinity I/O mask.</span></span> <span data-ttu-id="bbb17-108">affinity I/O mask オプションの詳細については、「 [affinity Input-Output mask サーバー構成オプション](affinity-input-output-mask-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbb17-108">For more information on the affinity I/O maskoption, see [affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md).</span></span> <span data-ttu-id="bbb17-109">プロセッサが 33 から 64 個のサーバーに対して CPU および I/O affinity をサポートするには、 [affinity64 mask サーバー構成オプション](affinity64-mask-server-configuration-option.md) および [affinity64 I/O mask サーバー構成オプション](affinity64-input-output-mask-server-configuration-option.md)がそれぞれ必要になります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-109">CPU and I/O affinity support for servers with 33 to 64 processors requires the additional use of the [affinity64 mask Server Configuration Option](affinity64-mask-server-configuration-option.md) and [affinity64 Input-Output mask Server Configuration Option](affinity64-input-output-mask-server-configuration-option.md), respectively.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bbb17-110">33 から 64 個までのプロセッサを搭載しているサーバーでの関係 (affinity) は、64 ビット オペレーティング システムでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-110">Affinity support for servers with 33 to 64 processors is only available on 64-bit operating systems.</span></span>  
  
 <span data-ttu-id="bbb17-111">affinity mask オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のリリースでも提供されており、動的に CPU 関係を制御します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-111">The affinity mask option, which existed in earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dynamically controls CPU affinity.</span></span>  
  
 <span data-ttu-id="bbb17-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを再起動しなくても affinity mask オプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-112">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the affinity mask option can be configured without requiring a restart of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bbb17-113">sp_configure を使用する場合は、構成オプションを設定した後、RECONFIGURE または RECONFIGURE WITH OVERRIDE のどちらかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-113">When you are using sp_configure, you must run either RECONFIGURE or RECONFIGURE WITH OVERRIDE after setting a configuration option.</span></span> <span data-ttu-id="bbb17-114">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を使用している場合、affinity mask オプションを変更しても再起動は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-114">When you are using [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], changing the affinity mask option does require a restart.</span></span>  
  
 <span data-ttu-id="bbb17-115">関係マスク (affinity mask) に対する変更は動的に行われるため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内のプロセス スレッドをバインドする CPU スケジューラのオンデマンドでの起動とシャットダウンが可能になります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-115">Changes to the affinity masks occur dynamically, allowing for on-demand startup and shutdown of the CPU schedulers that bind process threads within [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bbb17-116">この処理は、サーバーの状態の変化に伴って発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-116">This can occur as conditions change on the server.</span></span> <span data-ttu-id="bbb17-117">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンスをサーバーに追加したときに、プロセッサの負荷を再分散するために、affinity mask オプションを調整する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-117">For example, if a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is added to the server, it may be necessary to make adjustments to the affinity mask option to redistribute processor load.</span></span>  
  
 <span data-ttu-id="bbb17-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が新しい CPU スケジューラを有効にし、既存の CPU スケジューラを無効にするためには、関係ビットマスク (affinity bitmask) を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-118">Modifications to the affinity bitmasks require [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to enable a new CPU scheduler and disable the existing CPU scheduler.</span></span> <span data-ttu-id="bbb17-119">関係ビットマスクを変更すると、新しいスケジューラまたは継続して使用されているスケジューラで新しいバッチを処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-119">New batches can then be processed on the new or remaining schedulers.</span></span>  
  
 <span data-ttu-id="bbb17-120">新しい CPU スケジューラを起動するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により新しいスケジューラが作成され、これが標準のスケジューラのリストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-120">To start a new CPU scheduler, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates a new scheduler and adds it to the list of its standard schedulers.</span></span> <span data-ttu-id="bbb17-121">新しいスケジューラは、新しく受信するバッチ専用と見なされます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-121">The new scheduler is considered only for the new incoming batches.</span></span> <span data-ttu-id="bbb17-122">現在のバッチは、これまでと同じスケジューラで実行されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-122">Current batches continue to run on the same scheduler.</span></span> <span data-ttu-id="bbb17-123">ワーカーは、ワーカーが解放されたとき、または新しいワーカーが作成されたときに、新しいスケジューラに移行されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-123">The workers migrate to the new scheduler as they free up, or as new workers are created.</span></span>  
  
 <span data-ttu-id="bbb17-124">スケジューラをシャットダウンするには、スケジューラ上のすべてのバッチが操作を完了し、終了される必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-124">Shutting down a scheduler requires all batches on the scheduler to complete their activities and exit.</span></span> <span data-ttu-id="bbb17-125">シャットダウンされたスケジューラは、オフラインとしてマークされ、新しいバッチがこのスケジューラにより処理されないようにします。</span><span class="sxs-lookup"><span data-stu-id="bbb17-125">A scheduler that has been shut down is marked as offline so that no new batch is scheduled on it.</span></span>  
  
 <span data-ttu-id="bbb17-126">新しいスケジューラが追加または削除されても、ロック モニターやチェックポイント、システム タスク スレッド (DTC の処理)、シグナル プロセスなどの永続的なシステム タスクは、サーバーが稼働している間はスケジューラ上で継続して実行されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-126">Whether a new scheduler is added or removed, the permanent system tasks such as lockmonitor, checkpoint, system task thread (processing DTC), and signal process continue to run on the scheduler while the server is operational.</span></span> <span data-ttu-id="bbb17-127">このような永続的なシステム タスクについては、動的な移行は行われません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-127">These permanent system tasks do not dynamically migrate.</span></span> <span data-ttu-id="bbb17-128">スケジューラ間でこれらのシステム タスクのプロセッサ負荷を再分散するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-128">To redistribute processor load for these system tasks across schedulers, it is necessary to restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="bbb17-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が永続的なシステム タスクに関連付けられているスケジューラをシャットダウンした場合、タスクはオフラインになったスケジューラ上で引き続き実行されます (移行はされません)。</span><span class="sxs-lookup"><span data-stu-id="bbb17-129">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attempts to shut down a scheduler associated with a permanent system task, the task continues to run on the offline scheduler (no migration).</span></span> <span data-ttu-id="bbb17-130">このスケジューラは、変更された関係マスク内のプロセッサにバインドされているため、変更前に関係付けられていたプロセッサに負荷を分散させることはできません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-130">This scheduler is bound to the processors in the modified affinity mask and should not put any load on the processor it was affinitized with before the change.</span></span> <span data-ttu-id="bbb17-131">オフラインのスケジューラが増えたとしても、システムの負荷には目立った影響はありません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-131">Having extra offline schedulers, should not significantly affect the load of the system.</span></span> <span data-ttu-id="bbb17-132">負荷が大幅に増大した場合は、データベース サーバーを再起動して、これらのタスクを再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-132">If this is not the case, a database server reboot is required to reconfigure these tasks.</span></span>  
  
 <span data-ttu-id="bbb17-133">I/O 関係タスク (レイジーライターやログライターなど) は、直接 I/O 関係マスクの影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-133">The I/O affinity tasks (such as lazywriter and logwriter) are directly affected by the I/O affinity mask.</span></span> <span data-ttu-id="bbb17-134">レイジーライターおよびログライター タスクは、関係が設定されていなければ、ロック モニターやチェックポイントなど他の永続タスクに定義されているものと同じルールに従います。</span><span class="sxs-lookup"><span data-stu-id="bbb17-134">If the lazywriter and logwriter tasks are not affinitized, they follow the same rules defined for the other permanent tasks such as lockmonitor or checkpoint.</span></span>  
  
 <span data-ttu-id="bbb17-135">新しい関係マスクを確実に有効にするために、RECONFIGURE コマンドでは、通常の CPU 関係および I/O 関係が相互に排他的であるかどうかの確認を行います。</span><span class="sxs-lookup"><span data-stu-id="bbb17-135">To ensure that the new affinity mask is valid, the RECONFIGURE command verifies that the normal CPU and I/O affinities are mutually exclusive.</span></span> <span data-ttu-id="bbb17-136">相互に排他的でない場合は、そのような設定は推奨されないことを示すエラー メッセージがクライアント セッションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに報告されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-136">If this is not the case, an error message is reported to the client session and to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, indicating that such a setting is not recommended.</span></span> <span data-ttu-id="bbb17-137">RECONFIGURE WITH OVERRIDE を実行すると、相互に排他的ではない CPU 関係および I/O 関係が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-137">Running RECONFIGURE WITH OVERRIDE options allows CPU and I/O affinities that are not mutually exclusive.</span></span>  
  
 <span data-ttu-id="bbb17-138">存在しない CPU にマップしているような関係マスクを指定した場合、RECONFIGURE コマンドによりクライアント セッションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログの両方にエラー メッセージが報告されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-138">If you specify an affinity mask that attempts to map to a nonexistent CPU, the RECONFIGURE command reports an error message to both the client session and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span> <span data-ttu-id="bbb17-139">この場合、RECONFIGURE WITH OVERRIDE オプションを使用しても影響がなく、同じ構成エラーが再度報告されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-139">Using the RECONFIGURE WITH OVERRIDE option has no effect in this case, and the same configuration error is reported again.</span></span>  
  
 <span data-ttu-id="bbb17-140">Windows&#xA0;2000 または Windows&#xA0;Server&#xA0;2003 オペレーティング システムにより特定のワークロード割り当てが割り当てられているプロセッサから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の動作を除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-140">You can also exclude [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity from processors assigned specific workload assignments by the Windows 2000 or Windows Server 2003 operating system.</span></span> <span data-ttu-id="bbb17-141">プロセッサを表すビットを 1 に設定している場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンは、このプロセッサをスレッド割り当ての対象として選択します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-141">If you set a bit representing a processor to 1, that processor is selected by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine for thread assignment.</span></span> <span data-ttu-id="bbb17-142">`affinity mask`を 0 (既定値) に設定すると、Microsoft Windows 2000 または Windows Server 2003 のスケジューリングアルゴリズムによってスレッドのアフィニティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-142">When you set `affinity mask` to 0 (the default), the Microsoft Windows 2000 or Windows Server 2003 scheduling algorithms set the thread's affinity.</span></span> <span data-ttu-id="bbb17-143">`affinity mask` を 0 以外の値に設定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の関係 (affinity) により、選択可能なプロセッサを指定するビット マスクとしてその値が解釈されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-143">When you set `affinity mask` to any nonzero value, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinity interprets the value as a bitmask that specifies those processors eligible for selection.</span></span>  
  
 <span data-ttu-id="bbb17-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スレッドを特定のプロセッサ上の実行から隔離すると、Microsoft Windows&#xA0;2000 または Windows&#xA0;Server&#xA0;2003 では、システムによる Windows 固有のプロセス処理を評価しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-144">By segregating [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] threads from running on particular processors, Microsoft Windows 2000 or Windows Server 2003 can better evaluate the system's handling of processes specific to Windows.</span></span> <span data-ttu-id="bbb17-145">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを 2 つ (インスタンス A および B) を実行する 8 CPU サーバーで、システム管理者は affinity mask オプションを使用して最初の 4 個の CPU をインスタンス A に割り当て、残りの 4 個をインスタンス B に割り当てることができます。33 プロセッサ以上を構成する場合は、affinity mask および affinity64 mask の両方を設定します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-145">For example, on an 8-CPU server running two instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (instance A and B), the system administrator could use the affinity mask option to assign the first set of 4 CPUs to instance A and the second set of 4 to instance B. To configure more than 32 processors, set both the affinity mask and the affinity64 mask.</span></span> <span data-ttu-id="bbb17-146">`affinity mask` の値は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bbb17-146">The values for `affinity mask` are as follows:</span></span>  
  
-   <span data-ttu-id="bbb17-147">1 バイトの `affinity mask` はマルチプロセッサ コンピューターの最大 8 個の CPU に対応します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-147">A one-byte `affinity mask` covers up to 8 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="bbb17-148">2 バイトの `affinity mask` はマルチプロセッサ コンピューターの最大 16 個の CPU に対応します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-148">A two-byte `affinity mask` covers up to 16 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="bbb17-149">3 バイトの `affinity mask` はマルチプロセッサ コンピューターの最大 24 個の CPU に対応します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-149">A three-byte `affinity mask` covers up to 24 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="bbb17-150">4 バイトの `affinity mask` はマルチプロセッサ コンピューターの最大 32 個の CPU に対応します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-150">A four-byte `affinity mask` covers up to 32 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="bbb17-151">33 個以上の CPU に対応するには、最初の 32 個の CPU に 4 バイトの affinity mask を構成し、残りの CPU に 4 バイトの affinity64 mask を構成します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-151">To cover more than 32 CPUs, configure a four-byte affinity mask for the first 32 CPUs and up to a four-byte affinity64 mask for the remaining CPUs.</span></span>  
  
 <span data-ttu-id="bbb17-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセッサ関係を設定することは特別な操作なので、特に必要な場合にのみこのオプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbb17-152">Because setting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processor affinity is a specialized operation, it is recommended that it be used only when necessary.</span></span> <span data-ttu-id="bbb17-153">通常は、Microsoft Windows&#xA0;20000 または Windows&#xA0;Server&#xA0;2003 の既定の関係 (affinity) で、最適なパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-153">In most cases, the Microsoft Windows 2000 or Windows Server 2003 default affinity provides the best performance.</span></span> <span data-ttu-id="bbb17-154">また、関係マスクを設定する場合は、他のアプリケーションの CPU 要件も考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-154">You should also consider the CPU requirements for other applications when setting the affinity masks.</span></span> <span data-ttu-id="bbb17-155">詳細については、Windows オペレーティング システムのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbb17-155">For more information, see your Windows operating system documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bbb17-156">各プロセッサの利用状況を表示して分析するには、Windows のシステム モニターを使用します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-156">You can use the Windows System Monitor to view and analyze individual processor usage.</span></span>  
  
 <span data-ttu-id="bbb17-157">affinity I/O mask オプションを指定する場合は、affinity mask 構成オプションの設定を考慮して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-157">When specifying the affinity I/O mask option, you must use it in connection with the affinity mask configuration option.</span></span> <span data-ttu-id="bbb17-158">`affinity mask` スイッチと affinity I/O mask オプションの両方で同じ CPU を有効にしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bbb17-158">Do not enable the same CPU in both the `affinity mask` switch and the affinity I/O mask option.</span></span> <span data-ttu-id="bbb17-159">各 CPU に対応するビットは、次の 3 つの状態のうちのいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-159">The bits corresponding to each CPU should be in one of these three states:</span></span>  
  
-   <span data-ttu-id="bbb17-160">affinity mask オプションと affinity I/O mask オプションの両方で 0。</span><span class="sxs-lookup"><span data-stu-id="bbb17-160">0 in both the affinity mask option and the affinity I/O mask option.</span></span>  
  
-   <span data-ttu-id="bbb17-161">affinity mask オプションでは 1、affinity I/O mask オプションでは 0。</span><span class="sxs-lookup"><span data-stu-id="bbb17-161">1 in the affinity mask option and 0 in the affinity I/O mask option.</span></span>  
  
-   <span data-ttu-id="bbb17-162">affinity mask オプションでは 0、affinity I/O mask オプションでは 1。</span><span class="sxs-lookup"><span data-stu-id="bbb17-162">0 in the affinity mask option and 1 in the affinity I/O mask option.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="bbb17-163">Windows オペレーティング システムでの CPU 関係の構成と、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]での関係マスクの構成は、同時に行わないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bbb17-163">Do not configure CPU affinity in the Windows operating system and also configure the affinity mask in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bbb17-164">この 2 つの設定は、同じ効果をねらったものであり、これらの構成間に一貫性がない場合は、予期しない結果を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-164">These settings are attempting to achieve the same result, and if the configurations are inconsistent, you may have unpredictable results.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bbb17-165">CPU 関係を構成する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の sp_configure オプションを使用する方法が最適です。</span><span class="sxs-lookup"><span data-stu-id="bbb17-165">CPU affinity is best configured using the sp_configure option in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbb17-166">例</span><span class="sxs-lookup"><span data-stu-id="bbb17-166">Example</span></span>  
 <span data-ttu-id="bbb17-167">affinity mask オプションの設定例として、たとえば、ビット 1、2、および 5 を 1 に設定し、ビット 0、3、4、6、および 7 を 0 に設定して、プロセッサ 1、2、および 5 を使用可能として選択する場合は、16 進値 0x26 または 10 進値 `38` を指定します。</span><span class="sxs-lookup"><span data-stu-id="bbb17-167">As an example of setting the affinity mask option, if processors 1, 2, and 5 are selected as available with bits 1, 2, and 5 set to 1 and bits 0, 3, 4, 6, and 7 set to 0, a hexadecimal value of 0x26 or the decimal equivalent of `38` is specified.</span></span> <span data-ttu-id="bbb17-168">ビットの番号は右から左に数えます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-168">Number the bits from right to left.</span></span> <span data-ttu-id="bbb17-169">affinity mask オプションは、プロセッサを 0 から 31 までカウントします。したがって、次の例のカウンターの `1` は、サーバー上の 2 個目のプロセッサを表しています。</span><span class="sxs-lookup"><span data-stu-id="bbb17-169">The affinity mask option starts counting processors from 0 to 31, so that in the following example the counter `1` represents the second processor on the server.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'affinity mask', 38;  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="bbb17-170">8 CPU システムでの `affinity mask` の値は以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-170">These are `affinity mask` values for an 8-CPU system.</span></span>  
  
|<span data-ttu-id="bbb17-171">10 進値</span><span class="sxs-lookup"><span data-stu-id="bbb17-171">Decimal value</span></span>|<span data-ttu-id="bbb17-172">2 進ビット マスク</span><span class="sxs-lookup"><span data-stu-id="bbb17-172">Binary bit mask</span></span>|<span data-ttu-id="bbb17-173">SQL Server スレッドを有効にするプロセッサ</span><span class="sxs-lookup"><span data-stu-id="bbb17-173">Allow SQL Server threads on processors</span></span>|  
|-------------------|---------------------|--------------------------------------------|  
|<span data-ttu-id="bbb17-174">1</span><span class="sxs-lookup"><span data-stu-id="bbb17-174">1</span></span>|<span data-ttu-id="bbb17-175">00000001</span><span class="sxs-lookup"><span data-stu-id="bbb17-175">00000001</span></span>|<span data-ttu-id="bbb17-176">0</span><span class="sxs-lookup"><span data-stu-id="bbb17-176">0</span></span>|  
|<span data-ttu-id="bbb17-177">3</span><span class="sxs-lookup"><span data-stu-id="bbb17-177">3</span></span>|<span data-ttu-id="bbb17-178">00000011</span><span class="sxs-lookup"><span data-stu-id="bbb17-178">00000011</span></span>|<span data-ttu-id="bbb17-179">0 と 1</span><span class="sxs-lookup"><span data-stu-id="bbb17-179">0 and 1</span></span>|  
|<span data-ttu-id="bbb17-180">7</span><span class="sxs-lookup"><span data-stu-id="bbb17-180">7</span></span>|<span data-ttu-id="bbb17-181">00000111</span><span class="sxs-lookup"><span data-stu-id="bbb17-181">00000111</span></span>|<span data-ttu-id="bbb17-182">0、1、および 2</span><span class="sxs-lookup"><span data-stu-id="bbb17-182">0, 1, and 2</span></span>|  
|<span data-ttu-id="bbb17-183">15</span><span class="sxs-lookup"><span data-stu-id="bbb17-183">15</span></span>|<span data-ttu-id="bbb17-184">00001111</span><span class="sxs-lookup"><span data-stu-id="bbb17-184">00001111</span></span>|<span data-ttu-id="bbb17-185">0、1、2、および 3</span><span class="sxs-lookup"><span data-stu-id="bbb17-185">0, 1, 2, and 3</span></span>|  
|<span data-ttu-id="bbb17-186">31</span><span class="sxs-lookup"><span data-stu-id="bbb17-186">31</span></span>|<span data-ttu-id="bbb17-187">00011111</span><span class="sxs-lookup"><span data-stu-id="bbb17-187">00011111</span></span>|<span data-ttu-id="bbb17-188">0、1、2、3、および 4</span><span class="sxs-lookup"><span data-stu-id="bbb17-188">0, 1, 2, 3, and 4</span></span>|  
|<span data-ttu-id="bbb17-189">63</span><span class="sxs-lookup"><span data-stu-id="bbb17-189">63</span></span>|<span data-ttu-id="bbb17-190">00111111</span><span class="sxs-lookup"><span data-stu-id="bbb17-190">00111111</span></span>|<span data-ttu-id="bbb17-191">0、1、2、3、4、および 5</span><span class="sxs-lookup"><span data-stu-id="bbb17-191">0, 1, 2, 3, 4, and 5</span></span>|  
|<span data-ttu-id="bbb17-192">127</span><span class="sxs-lookup"><span data-stu-id="bbb17-192">127</span></span>|<span data-ttu-id="bbb17-193">01111111</span><span class="sxs-lookup"><span data-stu-id="bbb17-193">01111111</span></span>|<span data-ttu-id="bbb17-194">0、1、2、3、4、5、および 6</span><span class="sxs-lookup"><span data-stu-id="bbb17-194">0, 1, 2, 3, 4, 5, and 6</span></span>|  
|<span data-ttu-id="bbb17-195">255</span><span class="sxs-lookup"><span data-stu-id="bbb17-195">255</span></span>|<span data-ttu-id="bbb17-196">11111111</span><span class="sxs-lookup"><span data-stu-id="bbb17-196">11111111</span></span>|<span data-ttu-id="bbb17-197">0、1、2、3、4、5、6、および 7</span><span class="sxs-lookup"><span data-stu-id="bbb17-197">0, 1, 2, 3, 4, 5, 6, and 7</span></span>|  
  
 <span data-ttu-id="bbb17-198">affinity mask オプションは拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="bbb17-198">The affinity mask option is an advanced option.</span></span> <span data-ttu-id="bbb17-199">Sp_configure システムストアドプロシージャを使用して設定を変更する場合は、 `affinity mask` **show advanced options**が1に設定されている場合にのみ変更できます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-199">If you are using the sp_configure system stored procedure to change the setting, you can change `affinity mask` only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="bbb17-200">[!INCLUDE[tsql](../../includes/tsql-md.md)] の RECONFIGURE コマンドの実行が完了すると、新しい設定は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-200">After executing the [!INCLUDE[tsql](../../includes/tsql-md.md)] RECONFIGURE command, the new setting takes effect immediately without requiring a restart of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
## <a name="non-uniform-memory-access-numa"></a><span data-ttu-id="bbb17-201">NUMA (Non-uniform Memory Access)</span><span class="sxs-lookup"><span data-stu-id="bbb17-201">Non-uniform Memory Access (NUMA)</span></span>  
 <span data-ttu-id="bbb17-202">NUMA (non-uniform memory access) ベースのハードウェアを使用し、affinity mask を設定する場合、ノード内のすべてのスケジューラがそのノードの CPU に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-202">When using hardware based non-uniform memory access (NUMA) and the affinity mask is set, every scheduler in a node will be affinitized to its own CPU.</span></span> <span data-ttu-id="bbb17-203">affinity mask を設定しない場合、各スケジューラは NUMA ノード内の CPU のグループに関連付けられ、NUMA ノード N1 にマップされたスケジューラはノード内の任意の CPU で作業をスケジュールできますが、他のノードに関連付けられた CPU ではスケジュールできません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-203">When the affinity mask is not set, each scheduler is affinitized to the group of CPUs within the NUMA node and a scheduler mapped to NUMA node N1 can schedule work on any CPU in the node, but not on CPUs associated with another node.</span></span>  
  
 <span data-ttu-id="bbb17-204">1 つの NUMA ノードで実行中のすべての操作は、そのノードのバッファー ページのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-204">Any operation running on a single NUMA node can only use buffer pages from that node.</span></span> <span data-ttu-id="bbb17-205">操作を複数のノードの CPU で並行して実行する場合、メモリは関連する任意のノードから使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-205">When an operation is run in parallel on CPUs from multiple nodes, memory can be used from any node involved.</span></span>  
  
## <a name="licensing-issues"></a><span data-ttu-id="bbb17-206">ライセンスに関する問題点</span><span class="sxs-lookup"><span data-stu-id="bbb17-206">Licensing Issues</span></span>  
 <span data-ttu-id="bbb17-207">動的関係は、CPU ライセンスにより厳密に制限されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-207">Dynamic affinity is tightly constrained by CPU licensing.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bbb17-208">では、ライセンス ポリシーに違反する関係マスク オプションの構成が許可されていません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-208">does not allow any configuration of affinity mask options that violates the licensing policy.</span></span>  
  
### <a name="startup"></a><span data-ttu-id="bbb17-209">スタートアップ</span><span class="sxs-lookup"><span data-stu-id="bbb17-209">Startup</span></span>  
 <span data-ttu-id="bbb17-210">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時またはデータベースのアタッチ時に、指定された関係マスクがライセンス ポリシーに違反する場合、エンジン層により起動処理や、データベースのアタッチおよび復元操作は完了されますが、その後、関係マスクの sp_configure 実行値が 0 にリセットされ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログにエラー メッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="bbb17-210">If a specified affinity mask violates the licensing policy during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup or during database attach, the engine layer will complete the startup process or database attach/restore operation, and then it will reset the sp_configure run value for the affinity mask to zero, issuing an error message to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
### <a name="reconfigure"></a><span data-ttu-id="bbb17-211">再構成</span><span class="sxs-lookup"><span data-stu-id="bbb17-211">Reconfigure</span></span>  
 <span data-ttu-id="bbb17-212">[!INCLUDE[tsql](../../includes/tsql-md.md)] の RECONFIGURE コマンドの実行時に、指定された関係マスクがライセンス ポリシーに違反する場合は、エラー メッセージがクライアント セッションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに報告されます。データベース管理者による関係マスクの再構成作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="bbb17-212">If a specified affinity mask violates the licensing policy when running [!INCLUDE[tsql](../../includes/tsql-md.md)] RECONFIGURE command, an error message is reported to the client session and to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, requiring the database administrator to reconfigure the affinity mask.</span></span> <span data-ttu-id="bbb17-213">この場合、RECONFIGURE WITH OVERRIDE コマンドの実行が許可されません。</span><span class="sxs-lookup"><span data-stu-id="bbb17-213">No RECONFIGURE WITH OVERRIDE command is accepted in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb17-214">参照</span><span class="sxs-lookup"><span data-stu-id="bbb17-214">See Also</span></span>  
 <span data-ttu-id="bbb17-215">[リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="bbb17-215">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="bbb17-216">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bbb17-216">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="bbb17-217">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bbb17-217">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="bbb17-218">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bbb17-218">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="bbb17-219">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bbb17-219">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  