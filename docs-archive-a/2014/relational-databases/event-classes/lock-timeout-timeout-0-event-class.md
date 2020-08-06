---
title: Lock:Timeout (timeout &gt; 0) イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Timeout event class
ms.assetid: d755833a-d7eb-4973-9352-67a2fba2442a
author: stevestein
ms.author: sstein
ms.openlocfilehash: dbb165b157fda7d2bd978a91f479d6c1f2a09272
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643382"
---
# <a name="locktimeout-timeout-gt-0-event-class"></a><span data-ttu-id="49119-102">Lock:Timeout (timeout &gt; 0) イベント クラス</span><span class="sxs-lookup"><span data-stu-id="49119-102">Lock:Timeout (timeout &gt; 0) Event Class</span></span>
  <span data-ttu-id="49119-103">**Lock:Timeout (timeout > 0)** イベント クラスは、要求したリソースで別のトランザクションがブロッキング ロックを保持しているために、ページなどのリソースのロック要求がタイムアウトしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="49119-103">The **Lock:Timeout (timeout > 0)** event class indicates that a request for a lock on a resource, such as a page, has timed out because another transaction is holding a blocking lock on the required resource.</span></span> <span data-ttu-id="49119-104">このイベント クラスの動作は、タイムアウト値が 0 であるイベントを含まないことを除いて、 **Lock:Timeout** イベント クラスと同じです。</span><span class="sxs-lookup"><span data-stu-id="49119-104">This event class behaves the same as the **Lock:Timeout** event class, except it does not include any events where the timeout value is 0.</span></span>  
  
 <span data-ttu-id="49119-105">タイムアウト値が 0 のロックのプローブやその他のプロセスを使用しているトレースに、**Lock:Timeout (timeout > 0)** イベント クラスを含めます。</span><span class="sxs-lookup"><span data-stu-id="49119-105">Include the **Lock:Timeout (timeout > 0)** event class in traces where you are using lock probes or other processes that have timeout values of zero.</span></span> <span data-ttu-id="49119-106">これにより、タイムアウト値が 0 のイベントを除外して、実際にタイムアウトが発生しているイベントを確認できます。</span><span class="sxs-lookup"><span data-stu-id="49119-106">This allows you to see where actual time-outs are occurring without seeing time-out values of zero.</span></span>  
  
## <a name="locktimeout-timeout--0-event-class-data-columns"></a><span data-ttu-id="49119-107">Lock:Timeout (timeout > 0) イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="49119-107">Lock:Timeout (timeout > 0) Event Class Data Columns</span></span>  
  
|<span data-ttu-id="49119-108">データ列名</span><span class="sxs-lookup"><span data-stu-id="49119-108">Data column name</span></span>|<span data-ttu-id="49119-109">データ型</span><span class="sxs-lookup"><span data-stu-id="49119-109">Data type</span></span>|<span data-ttu-id="49119-110">説明</span><span class="sxs-lookup"><span data-stu-id="49119-110">Description</span></span>|<span data-ttu-id="49119-111">列 ID</span><span class="sxs-lookup"><span data-stu-id="49119-111">Column ID</span></span>|<span data-ttu-id="49119-112">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="49119-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="49119-113">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="49119-113">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="49119-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="49119-114">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="49119-115">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="49119-115">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="49119-116">10</span><span class="sxs-lookup"><span data-stu-id="49119-116">10</span></span>|<span data-ttu-id="49119-117">はい</span><span class="sxs-lookup"><span data-stu-id="49119-117">Yes</span></span>|  
|<span data-ttu-id="49119-118">BinaryData</span><span class="sxs-lookup"><span data-stu-id="49119-118">BinaryData</span></span>|`image`|<span data-ttu-id="49119-119">ロック リソース ID。</span><span class="sxs-lookup"><span data-stu-id="49119-119">Lock resource identifier.</span></span>|<span data-ttu-id="49119-120">2</span><span class="sxs-lookup"><span data-stu-id="49119-120">2</span></span>|<span data-ttu-id="49119-121">はい</span><span class="sxs-lookup"><span data-stu-id="49119-121">Yes</span></span>|  
|<span data-ttu-id="49119-122">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="49119-122">ClientProcessID</span></span>|`int`|<span data-ttu-id="49119-123">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="49119-123">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="49119-124">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="49119-124">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="49119-125">9</span><span class="sxs-lookup"><span data-stu-id="49119-125">9</span></span>|<span data-ttu-id="49119-126">はい</span><span class="sxs-lookup"><span data-stu-id="49119-126">Yes</span></span>|  
|<span data-ttu-id="49119-127">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="49119-127">DatabaseID</span></span>|`int`|<span data-ttu-id="49119-128">タイムアウトが発生したデータベースの ID。</span><span class="sxs-lookup"><span data-stu-id="49119-128">ID of the database in which the timeout occurred.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="49119-129">では、`ServerName` データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49119-129">displays the name of the database if the `ServerName` data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="49119-130">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="49119-130">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="49119-131">3</span><span class="sxs-lookup"><span data-stu-id="49119-131">3</span></span>|<span data-ttu-id="49119-132">はい</span><span class="sxs-lookup"><span data-stu-id="49119-132">Yes</span></span>|  
|<span data-ttu-id="49119-133">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="49119-133">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="49119-134">タイムアウトが発生したデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="49119-134">Name of the database in which the time-out occurred.</span></span>|<span data-ttu-id="49119-135">35</span><span class="sxs-lookup"><span data-stu-id="49119-135">35</span></span>|<span data-ttu-id="49119-136">はい</span><span class="sxs-lookup"><span data-stu-id="49119-136">Yes</span></span>|  
|<span data-ttu-id="49119-137">Duration</span><span class="sxs-lookup"><span data-stu-id="49119-137">Duration</span></span>|`bigint`|<span data-ttu-id="49119-138">イベントにかかった時間 (マイクロ秒)。</span><span class="sxs-lookup"><span data-stu-id="49119-138">Amount of time (in microseconds) taken by the event.</span></span>|<span data-ttu-id="49119-139">13</span><span class="sxs-lookup"><span data-stu-id="49119-139">13</span></span>|<span data-ttu-id="49119-140">はい</span><span class="sxs-lookup"><span data-stu-id="49119-140">Yes</span></span>|  
|<span data-ttu-id="49119-141">EndTime</span><span class="sxs-lookup"><span data-stu-id="49119-141">EndTime</span></span>|`datetime`|<span data-ttu-id="49119-142">イベントの終了時刻。</span><span class="sxs-lookup"><span data-stu-id="49119-142">Time at which the event ended.</span></span> <span data-ttu-id="49119-143">**SQL:BatchStarting** や **SP:Starting**などの開始イベント クラスについては、この列に値が格納されません。</span><span class="sxs-lookup"><span data-stu-id="49119-143">This column is not populated for starting event classes, such as **SQL:BatchStarting** or **SP:Starting**.</span></span>|<span data-ttu-id="49119-144">15</span><span class="sxs-lookup"><span data-stu-id="49119-144">15</span></span>|<span data-ttu-id="49119-145">はい</span><span class="sxs-lookup"><span data-stu-id="49119-145">Yes</span></span>|  
|<span data-ttu-id="49119-146">EventClass</span><span class="sxs-lookup"><span data-stu-id="49119-146">EventClass</span></span>|`int`|<span data-ttu-id="49119-147">イベントの種類 = 189。</span><span class="sxs-lookup"><span data-stu-id="49119-147">Type of event=189.</span></span>|<span data-ttu-id="49119-148">27</span><span class="sxs-lookup"><span data-stu-id="49119-148">27</span></span>|<span data-ttu-id="49119-149">いいえ</span><span class="sxs-lookup"><span data-stu-id="49119-149">No</span></span>|  
|<span data-ttu-id="49119-150">EventSequence</span><span class="sxs-lookup"><span data-stu-id="49119-150">EventSequence</span></span>|`int`|<span data-ttu-id="49119-151">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="49119-151">Sequence of a given event within the request.</span></span>|<span data-ttu-id="49119-152">51</span><span class="sxs-lookup"><span data-stu-id="49119-152">51</span></span>|<span data-ttu-id="49119-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="49119-153">No</span></span>|  
|<span data-ttu-id="49119-154">GroupID</span><span class="sxs-lookup"><span data-stu-id="49119-154">GroupID</span></span>|`int`|<span data-ttu-id="49119-155">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="49119-155">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="49119-156">66</span><span class="sxs-lookup"><span data-stu-id="49119-156">66</span></span>|<span data-ttu-id="49119-157">はい</span><span class="sxs-lookup"><span data-stu-id="49119-157">Yes</span></span>|  
|<span data-ttu-id="49119-158">HostName</span><span class="sxs-lookup"><span data-stu-id="49119-158">HostName</span></span>|`nvarchar`|<span data-ttu-id="49119-159">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="49119-159">Name of the computer on which the client is running.</span></span> <span data-ttu-id="49119-160">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="49119-160">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="49119-161">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="49119-161">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="49119-162">8</span><span class="sxs-lookup"><span data-stu-id="49119-162">8</span></span>|<span data-ttu-id="49119-163">はい</span><span class="sxs-lookup"><span data-stu-id="49119-163">Yes</span></span>|  
|<span data-ttu-id="49119-164">IntegerData2</span><span class="sxs-lookup"><span data-stu-id="49119-164">IntegerData2</span></span>|`int`|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|<span data-ttu-id="49119-165">55</span><span class="sxs-lookup"><span data-stu-id="49119-165">55</span></span>|<span data-ttu-id="49119-166">はい</span><span class="sxs-lookup"><span data-stu-id="49119-166">Yes</span></span>|  
|<span data-ttu-id="49119-167">IsSystem</span><span class="sxs-lookup"><span data-stu-id="49119-167">IsSystem</span></span>|`int`|<span data-ttu-id="49119-168">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="49119-168">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="49119-169">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="49119-169">1 = system, 0 = user.</span></span>|<span data-ttu-id="49119-170">60</span><span class="sxs-lookup"><span data-stu-id="49119-170">60</span></span>|<span data-ttu-id="49119-171">はい</span><span class="sxs-lookup"><span data-stu-id="49119-171">Yes</span></span>|  
|<span data-ttu-id="49119-172">LoginName</span><span class="sxs-lookup"><span data-stu-id="49119-172">LoginName</span></span>|`nvarchar`|<span data-ttu-id="49119-173">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="49119-173">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="49119-174">11</span><span class="sxs-lookup"><span data-stu-id="49119-174">11</span></span>|<span data-ttu-id="49119-175">はい</span><span class="sxs-lookup"><span data-stu-id="49119-175">Yes</span></span>|  
|<span data-ttu-id="49119-176">LoginSid</span><span class="sxs-lookup"><span data-stu-id="49119-176">LoginSid</span></span>|`image`|<span data-ttu-id="49119-177">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="49119-177">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="49119-178">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="49119-178">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="49119-179">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="49119-179">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="49119-180">41</span><span class="sxs-lookup"><span data-stu-id="49119-180">41</span></span>|<span data-ttu-id="49119-181">はい</span><span class="sxs-lookup"><span data-stu-id="49119-181">Yes</span></span>|  
|<span data-ttu-id="49119-182">モード</span><span class="sxs-lookup"><span data-stu-id="49119-182">Mode</span></span>|`int`|<span data-ttu-id="49119-183">イベントが受信された状態またはイベントを要求中の状態。</span><span class="sxs-lookup"><span data-stu-id="49119-183">State that the event has received or is requesting.</span></span><br /><br /> <span data-ttu-id="49119-184">0 = NULL</span><span class="sxs-lookup"><span data-stu-id="49119-184">0=NULL</span></span><br /><br /> <span data-ttu-id="49119-185">1 = Sch-S</span><span class="sxs-lookup"><span data-stu-id="49119-185">1=Sch-S</span></span><br /><br /> <span data-ttu-id="49119-186">2 = Sch-M</span><span class="sxs-lookup"><span data-stu-id="49119-186">2=Sch-M</span></span><br /><br /> <span data-ttu-id="49119-187">3 = S</span><span class="sxs-lookup"><span data-stu-id="49119-187">3=S</span></span><br /><br /> <span data-ttu-id="49119-188">4 = U</span><span class="sxs-lookup"><span data-stu-id="49119-188">4=U</span></span><br /><br /> <span data-ttu-id="49119-189">5 = X</span><span class="sxs-lookup"><span data-stu-id="49119-189">5=X</span></span><br /><br /> <span data-ttu-id="49119-190">6 = IS</span><span class="sxs-lookup"><span data-stu-id="49119-190">6=IS</span></span><br /><br /> <span data-ttu-id="49119-191">7 = IU</span><span class="sxs-lookup"><span data-stu-id="49119-191">7=IU</span></span><br /><br /> <span data-ttu-id="49119-192">8 = IX</span><span class="sxs-lookup"><span data-stu-id="49119-192">8=IX</span></span><br /><br /> <span data-ttu-id="49119-193">9 = SIU</span><span class="sxs-lookup"><span data-stu-id="49119-193">9=SIU</span></span><br /><br /> <span data-ttu-id="49119-194">10 = SIX</span><span class="sxs-lookup"><span data-stu-id="49119-194">10=SIX</span></span><br /><br /> <span data-ttu-id="49119-195">11 = UIX</span><span class="sxs-lookup"><span data-stu-id="49119-195">11=UIX</span></span><br /><br /> <span data-ttu-id="49119-196">12 = BU</span><span class="sxs-lookup"><span data-stu-id="49119-196">12=BU</span></span><br /><br /> <span data-ttu-id="49119-197">13 = RangeS-S</span><span class="sxs-lookup"><span data-stu-id="49119-197">13=RangeS-S</span></span><br /><br /> <span data-ttu-id="49119-198">14 = RangeS-U</span><span class="sxs-lookup"><span data-stu-id="49119-198">14=RangeS-U</span></span><br /><br /> <span data-ttu-id="49119-199">15 = RangeI-N</span><span class="sxs-lookup"><span data-stu-id="49119-199">15=RangeI-N</span></span><br /><br /> <span data-ttu-id="49119-200">16 = RangeI-S</span><span class="sxs-lookup"><span data-stu-id="49119-200">16=RangeI-S</span></span><br /><br /> <span data-ttu-id="49119-201">17 = RangeI-U</span><span class="sxs-lookup"><span data-stu-id="49119-201">17=RangeI-U</span></span><br /><br /> <span data-ttu-id="49119-202">18 = RangeI-X</span><span class="sxs-lookup"><span data-stu-id="49119-202">18=RangeI-X</span></span><br /><br /> <span data-ttu-id="49119-203">19 = RangeX-S</span><span class="sxs-lookup"><span data-stu-id="49119-203">19=RangeX-S</span></span><br /><br /> <span data-ttu-id="49119-204">20 = RangeX-U</span><span class="sxs-lookup"><span data-stu-id="49119-204">20=RangeX-U</span></span><br /><br /> <span data-ttu-id="49119-205">21 = RangeX-X</span><span class="sxs-lookup"><span data-stu-id="49119-205">21=RangeX-X</span></span>|<span data-ttu-id="49119-206">32</span><span class="sxs-lookup"><span data-stu-id="49119-206">32</span></span>|<span data-ttu-id="49119-207">はい</span><span class="sxs-lookup"><span data-stu-id="49119-207">Yes</span></span>|  
|<span data-ttu-id="49119-208">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="49119-208">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="49119-209">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="49119-209">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="49119-210">7</span><span class="sxs-lookup"><span data-stu-id="49119-210">7</span></span>|<span data-ttu-id="49119-211">はい</span><span class="sxs-lookup"><span data-stu-id="49119-211">Yes</span></span>|  
|<span data-ttu-id="49119-212">NTUserName</span><span class="sxs-lookup"><span data-stu-id="49119-212">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="49119-213">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="49119-213">Windows user name.</span></span>|<span data-ttu-id="49119-214">6</span><span class="sxs-lookup"><span data-stu-id="49119-214">6</span></span>|<span data-ttu-id="49119-215">はい</span><span class="sxs-lookup"><span data-stu-id="49119-215">Yes</span></span>|  
|<span data-ttu-id="49119-216">ObjectID</span><span class="sxs-lookup"><span data-stu-id="49119-216">ObjectID</span></span>|`int`|<span data-ttu-id="49119-217">オブジェクトの ID (使用可能かつ適用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="49119-217">ID of the object, if available and applicable.</span></span>|<span data-ttu-id="49119-218">22</span><span class="sxs-lookup"><span data-stu-id="49119-218">22</span></span>|<span data-ttu-id="49119-219">はい</span><span class="sxs-lookup"><span data-stu-id="49119-219">Yes</span></span>|  
|<span data-ttu-id="49119-220">ObjectID2</span><span class="sxs-lookup"><span data-stu-id="49119-220">ObjectID2</span></span>|`bigint`|<span data-ttu-id="49119-221">関連するオブジェクトまたはエンティティの ID (使用可能かつ適用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="49119-221">ID of the related object or entity, if available and applicable.</span></span>|<span data-ttu-id="49119-222">56</span><span class="sxs-lookup"><span data-stu-id="49119-222">56</span></span>|<span data-ttu-id="49119-223">はい</span><span class="sxs-lookup"><span data-stu-id="49119-223">Yes</span></span>|  
|<span data-ttu-id="49119-224">OwnerID</span><span class="sxs-lookup"><span data-stu-id="49119-224">OwnerID</span></span>|`int`|<span data-ttu-id="49119-225">1 = TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="49119-225">1=TRANSACTION</span></span><br /><br /> <span data-ttu-id="49119-226">2 = CURSOR</span><span class="sxs-lookup"><span data-stu-id="49119-226">2=CURSOR</span></span><br /><br /> <span data-ttu-id="49119-227">3 = SESSION</span><span class="sxs-lookup"><span data-stu-id="49119-227">3=SESSION</span></span><br /><br /> <span data-ttu-id="49119-228">4 = SHARED_TRANSACTION_WORKSPACE</span><span class="sxs-lookup"><span data-stu-id="49119-228">4=SHARED_TRANSACTION_WORKSPACE</span></span><br /><br /> <span data-ttu-id="49119-229">5 = EXCLUSIVE_TRANSACTION_WORKSPACE</span><span class="sxs-lookup"><span data-stu-id="49119-229">5=EXCLUSIVE_TRANSACTION_WORKSPACE</span></span>|<span data-ttu-id="49119-230">58</span><span class="sxs-lookup"><span data-stu-id="49119-230">58</span></span>|<span data-ttu-id="49119-231">はい</span><span class="sxs-lookup"><span data-stu-id="49119-231">Yes</span></span>|  
|<span data-ttu-id="49119-232">RequestID</span><span class="sxs-lookup"><span data-stu-id="49119-232">RequestID</span></span>|`int`|<span data-ttu-id="49119-233">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="49119-233">ID of the request containing the statement.</span></span>|<span data-ttu-id="49119-234">49</span><span class="sxs-lookup"><span data-stu-id="49119-234">49</span></span>|<span data-ttu-id="49119-235">はい</span><span class="sxs-lookup"><span data-stu-id="49119-235">Yes</span></span>|  
|<span data-ttu-id="49119-236">ServerName</span><span class="sxs-lookup"><span data-stu-id="49119-236">ServerName</span></span>|`nvarchar`|<span data-ttu-id="49119-237">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="49119-237">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="49119-238">26</span><span class="sxs-lookup"><span data-stu-id="49119-238">26</span></span>|<span data-ttu-id="49119-239">いいえ</span><span class="sxs-lookup"><span data-stu-id="49119-239">No</span></span>|  
|<span data-ttu-id="49119-240">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="49119-240">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="49119-241">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="49119-241">Login name of the user who originated the session.</span></span> <span data-ttu-id="49119-242">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、`SessionLoginName` には Login1 が表示され、`LoginName` には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49119-242">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, `SessionLoginName` shows Login1 and `LoginName` shows Login2.</span></span> <span data-ttu-id="49119-243">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49119-243">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="49119-244">64</span><span class="sxs-lookup"><span data-stu-id="49119-244">64</span></span>|<span data-ttu-id="49119-245">はい</span><span class="sxs-lookup"><span data-stu-id="49119-245">Yes</span></span>|  
|<span data-ttu-id="49119-246">SPID</span><span class="sxs-lookup"><span data-stu-id="49119-246">SPID</span></span>|`int`|<span data-ttu-id="49119-247">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="49119-247">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="49119-248">12</span><span class="sxs-lookup"><span data-stu-id="49119-248">12</span></span>|<span data-ttu-id="49119-249">はい</span><span class="sxs-lookup"><span data-stu-id="49119-249">Yes</span></span>|  
|<span data-ttu-id="49119-250">StartTime</span><span class="sxs-lookup"><span data-stu-id="49119-250">StartTime</span></span>|`datetime`|<span data-ttu-id="49119-251">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="49119-251">Time at which the event started, if available.</span></span>|<span data-ttu-id="49119-252">14</span><span class="sxs-lookup"><span data-stu-id="49119-252">14</span></span>|<span data-ttu-id="49119-253">はい</span><span class="sxs-lookup"><span data-stu-id="49119-253">Yes</span></span>|  
|<span data-ttu-id="49119-254">TextData</span><span class="sxs-lookup"><span data-stu-id="49119-254">TextData</span></span>|`ntext`|<span data-ttu-id="49119-255">トレースでキャプチャされたイベント クラスに依存するテキスト値。</span><span class="sxs-lookup"><span data-stu-id="49119-255">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="49119-256">1</span><span class="sxs-lookup"><span data-stu-id="49119-256">1</span></span>|<span data-ttu-id="49119-257">はい</span><span class="sxs-lookup"><span data-stu-id="49119-257">Yes</span></span>|  
|<span data-ttu-id="49119-258">TransactionID</span><span class="sxs-lookup"><span data-stu-id="49119-258">TransactionID</span></span>|`bigint`|<span data-ttu-id="49119-259">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="49119-259">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="49119-260">4</span><span class="sxs-lookup"><span data-stu-id="49119-260">4</span></span>|<span data-ttu-id="49119-261">はい</span><span class="sxs-lookup"><span data-stu-id="49119-261">Yes</span></span>|  
|<span data-ttu-id="49119-262">Type</span><span class="sxs-lookup"><span data-stu-id="49119-262">Type</span></span>|`int`|<span data-ttu-id="49119-263">1 = NULL_RESOURCE</span><span class="sxs-lookup"><span data-stu-id="49119-263">1=NULL_RESOURCE</span></span><br /><br /> <span data-ttu-id="49119-264">2 = DATABASE</span><span class="sxs-lookup"><span data-stu-id="49119-264">2=DATABASE</span></span><br /><br /> <span data-ttu-id="49119-265">3 = FILE</span><span class="sxs-lookup"><span data-stu-id="49119-265">3=FILE</span></span><br /><br /> <span data-ttu-id="49119-266">5 = OBJECT</span><span class="sxs-lookup"><span data-stu-id="49119-266">5=OBJECT</span></span><br /><br /> <span data-ttu-id="49119-267">6 = PAGE</span><span class="sxs-lookup"><span data-stu-id="49119-267">6=PAGE</span></span><br /><br /> <span data-ttu-id="49119-268">7 = KEY</span><span class="sxs-lookup"><span data-stu-id="49119-268">7=KEY</span></span><br /><br /> <span data-ttu-id="49119-269">8 = EXTENT</span><span class="sxs-lookup"><span data-stu-id="49119-269">8=EXTENT</span></span><br /><br /> <span data-ttu-id="49119-270">9 = RID</span><span class="sxs-lookup"><span data-stu-id="49119-270">9=RID</span></span><br /><br /> <span data-ttu-id="49119-271">10 = APPLICATION</span><span class="sxs-lookup"><span data-stu-id="49119-271">10=APPLICATION</span></span><br /><br /> <span data-ttu-id="49119-272">11 = METADATA</span><span class="sxs-lookup"><span data-stu-id="49119-272">11=METADATA</span></span><br /><br /> <span data-ttu-id="49119-273">12 = AUTONAMEDB</span><span class="sxs-lookup"><span data-stu-id="49119-273">12=AUTONAMEDB</span></span><br /><br /> <span data-ttu-id="49119-274">13 = HOBT</span><span class="sxs-lookup"><span data-stu-id="49119-274">13=HOBT</span></span><br /><br /> <span data-ttu-id="49119-275">14 = ALLOCATION_UNIT</span><span class="sxs-lookup"><span data-stu-id="49119-275">14=ALLOCATION_UNIT</span></span>|<span data-ttu-id="49119-276">57</span><span class="sxs-lookup"><span data-stu-id="49119-276">57</span></span>|<span data-ttu-id="49119-277">はい</span><span class="sxs-lookup"><span data-stu-id="49119-277">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49119-278">参照</span><span class="sxs-lookup"><span data-stu-id="49119-278">See Also</span></span>  
 <span data-ttu-id="49119-279">[Lock: Timeout イベントクラス](lock-timeout-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="49119-279">[Lock:Timeout Event Class](lock-timeout-event-class.md) </span></span>  
 <span data-ttu-id="49119-280">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="49119-280">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="49119-281">sys.dm_tran_locks &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49119-281">sys.dm_tran_locks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
  