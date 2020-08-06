---
title: Lock:Released イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Released event class
ms.assetid: a150c300-72fa-4231-8f41-f1abd550a429
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee61532c806ca52b9e9d08ef6052c4da0c564ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642103"
---
# <a name="lockreleased-event-class"></a><span data-ttu-id="4f384-102">Lock:Released イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4f384-102">Lock:Released Event Class</span></span>
  <span data-ttu-id="4f384-103">Lock:Released イベント クラスは、ページなどのリソースのロックが解放されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="4f384-103">The Lock:Released event class indicates that a lock on a resource, such as a page, has been released.</span></span>  
  
 <span data-ttu-id="4f384-104">Lock:Acquired イベント クラスおよび Lock:Released イベント クラスを使用すると、オブジェクトがロックされている時点、取得するロックの種類、およびロックが保持されていた期間を監視できます。</span><span class="sxs-lookup"><span data-stu-id="4f384-104">The Lock:Acquired and Lock:Released event classes can be used to monitor when objects are being locked, the type of locks taken, and for how long the locks were retained.</span></span> <span data-ttu-id="4f384-105">長時間ロックが保持されると、競合の問題が発生する原因となり、調査が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4f384-105">Locks retained for long periods of time may cause contention issues and should be investigated.</span></span> <span data-ttu-id="4f384-106">たとえば、アプリケーションでは、テーブルの行のロックを取得して、ユーザー入力を待機できます。</span><span class="sxs-lookup"><span data-stu-id="4f384-106">For example, an application can be acquiring locks on rows in a table, and then waiting for user input.</span></span> <span data-ttu-id="4f384-107">ユーザー入力は行われるまでに長時間かかることがあるので、ロックによって他のユーザーがブロックされることがあります。</span><span class="sxs-lookup"><span data-stu-id="4f384-107">Because the user input can take a long time to occur, the locks can block other users.</span></span> <span data-ttu-id="4f384-108">この場合、アプリケーションは、必要なときにだけロックを要求し、ロックが取得されている場合はユーザー入力を要求しないように再設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f384-108">In this instance, the application should be redesigned to make lock requests only when needed and not require user input when locks have been acquired.</span></span>  
  
## <a name="lock-released-event-class-data-columns"></a><span data-ttu-id="4f384-109">Lock:Released イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="4f384-109">Lock: Released Event Class Data Columns</span></span>  
  
|<span data-ttu-id="4f384-110">データ列名</span><span class="sxs-lookup"><span data-stu-id="4f384-110">Data column name</span></span>|<span data-ttu-id="4f384-111">データ型</span><span class="sxs-lookup"><span data-stu-id="4f384-111">Data type</span></span>|<span data-ttu-id="4f384-112">説明</span><span class="sxs-lookup"><span data-stu-id="4f384-112">Description</span></span>|<span data-ttu-id="4f384-113">列 ID</span><span class="sxs-lookup"><span data-stu-id="4f384-113">Column ID</span></span>|<span data-ttu-id="4f384-114">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="4f384-114">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="4f384-115">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="4f384-115">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="4f384-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="4f384-116">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4f384-117">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-117">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="4f384-118">10</span><span class="sxs-lookup"><span data-stu-id="4f384-118">10</span></span>|<span data-ttu-id="4f384-119">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-119">Yes</span></span>|  
|<span data-ttu-id="4f384-120">BinaryData</span><span class="sxs-lookup"><span data-stu-id="4f384-120">BinaryData</span></span>|`image`|<span data-ttu-id="4f384-121">ロック リソース ID。</span><span class="sxs-lookup"><span data-stu-id="4f384-121">Lock resource identifier.</span></span>|<span data-ttu-id="4f384-122">2</span><span class="sxs-lookup"><span data-stu-id="4f384-122">2</span></span>|<span data-ttu-id="4f384-123">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-123">Yes</span></span>|  
|<span data-ttu-id="4f384-124">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="4f384-124">ClientProcessID</span></span>|`int`|<span data-ttu-id="4f384-125">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="4f384-125">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="4f384-126">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-126">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="4f384-127">9</span><span class="sxs-lookup"><span data-stu-id="4f384-127">9</span></span>|<span data-ttu-id="4f384-128">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-128">Yes</span></span>|  
|<span data-ttu-id="4f384-129">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="4f384-129">DatabaseID</span></span>|`int`|<span data-ttu-id="4f384-130">ロックが解放されたデータベースの ID です。</span><span class="sxs-lookup"><span data-stu-id="4f384-130">ID of the database in which the lock was released.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="4f384-131">では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-131">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="4f384-132">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="4f384-132">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="4f384-133">3</span><span class="sxs-lookup"><span data-stu-id="4f384-133">3</span></span>|<span data-ttu-id="4f384-134">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-134">Yes</span></span>|  
|<span data-ttu-id="4f384-135">EventClass</span><span class="sxs-lookup"><span data-stu-id="4f384-135">EventClass</span></span>|`int`|<span data-ttu-id="4f384-136">イベントの種類 = 23。</span><span class="sxs-lookup"><span data-stu-id="4f384-136">Type of event = 23.</span></span>|<span data-ttu-id="4f384-137">27</span><span class="sxs-lookup"><span data-stu-id="4f384-137">27</span></span>|<span data-ttu-id="4f384-138">いいえ</span><span class="sxs-lookup"><span data-stu-id="4f384-138">No</span></span>|  
|<span data-ttu-id="4f384-139">EventSequence</span><span class="sxs-lookup"><span data-stu-id="4f384-139">EventSequence</span></span>|`int`|<span data-ttu-id="4f384-140">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="4f384-140">Sequence of a given event within the request.</span></span>|<span data-ttu-id="4f384-141">51</span><span class="sxs-lookup"><span data-stu-id="4f384-141">51</span></span>|<span data-ttu-id="4f384-142">いいえ</span><span class="sxs-lookup"><span data-stu-id="4f384-142">No</span></span>|  
|<span data-ttu-id="4f384-143">GroupID</span><span class="sxs-lookup"><span data-stu-id="4f384-143">GroupID</span></span>|`int`|<span data-ttu-id="4f384-144">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="4f384-144">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="4f384-145">66</span><span class="sxs-lookup"><span data-stu-id="4f384-145">66</span></span>|<span data-ttu-id="4f384-146">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-146">Yes</span></span>|  
|<span data-ttu-id="4f384-147">HostName</span><span class="sxs-lookup"><span data-stu-id="4f384-147">HostName</span></span>|`nvarchar`|<span data-ttu-id="4f384-148">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="4f384-148">Name of the computer on which the client is running.</span></span> <span data-ttu-id="4f384-149">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-149">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="4f384-150">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f384-150">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="4f384-151">8</span><span class="sxs-lookup"><span data-stu-id="4f384-151">8</span></span>|<span data-ttu-id="4f384-152">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-152">Yes</span></span>|  
|<span data-ttu-id="4f384-153">IntegerData2</span><span class="sxs-lookup"><span data-stu-id="4f384-153">IntegerData2</span></span>|`int`|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|<span data-ttu-id="4f384-154">55</span><span class="sxs-lookup"><span data-stu-id="4f384-154">55</span></span>|<span data-ttu-id="4f384-155">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-155">Yes</span></span>|  
|<span data-ttu-id="4f384-156">IsSystem</span><span class="sxs-lookup"><span data-stu-id="4f384-156">IsSystem</span></span>|`int`|<span data-ttu-id="4f384-157">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="4f384-157">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="4f384-158">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="4f384-158">1 = system, 0 = user.</span></span>|<span data-ttu-id="4f384-159">60</span><span class="sxs-lookup"><span data-stu-id="4f384-159">60</span></span>|<span data-ttu-id="4f384-160">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-160">Yes</span></span>|  
|<span data-ttu-id="4f384-161">LoginName</span><span class="sxs-lookup"><span data-stu-id="4f384-161">LoginName</span></span>|`nvarchar`|<span data-ttu-id="4f384-162">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="4f384-162">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="4f384-163">11</span><span class="sxs-lookup"><span data-stu-id="4f384-163">11</span></span>|<span data-ttu-id="4f384-164">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-164">Yes</span></span>|  
|<span data-ttu-id="4f384-165">LoginSid</span><span class="sxs-lookup"><span data-stu-id="4f384-165">LoginSid</span></span>|`image`|<span data-ttu-id="4f384-166">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="4f384-166">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="4f384-167">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="4f384-167">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="4f384-168">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="4f384-168">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="4f384-169">41</span><span class="sxs-lookup"><span data-stu-id="4f384-169">41</span></span>|<span data-ttu-id="4f384-170">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-170">Yes</span></span>|  
|<span data-ttu-id="4f384-171">モード</span><span class="sxs-lookup"><span data-stu-id="4f384-171">Mode</span></span>|`int`|<span data-ttu-id="4f384-172">ロックが解放された後のモード。</span><span class="sxs-lookup"><span data-stu-id="4f384-172">Resulting mode after the lock was released.</span></span><br /><br /> <span data-ttu-id="4f384-173">0 = NULL - 他のすべてのロック モードと互換性あり (LCK_M_NL)</span><span class="sxs-lookup"><span data-stu-id="4f384-173">0=NULL - Compatible with all other lock modes (LCK_M_NL)</span></span><br /><br /> <span data-ttu-id="4f384-174">1 = スキーマ安定度ロック (LCK_M_SCH_S)</span><span class="sxs-lookup"><span data-stu-id="4f384-174">1=Schema Stability lock (LCK_M_SCH_S)</span></span><br /><br /> <span data-ttu-id="4f384-175">2 = スキーマ変更ロック (LCK_M_SCH_M)</span><span class="sxs-lookup"><span data-stu-id="4f384-175">2=Schema Modification Lock (LCK_M_SCH_M)</span></span><br /><br /> <span data-ttu-id="4f384-176">3 = 共有ロック (LCK_M_S)</span><span class="sxs-lookup"><span data-stu-id="4f384-176">3=Shared Lock (LCK_M_S)</span></span><br /><br /> <span data-ttu-id="4f384-177">4 = 更新ロック (LCK_M_U)</span><span class="sxs-lookup"><span data-stu-id="4f384-177">4=Update Lock (LCK_M_U)</span></span><br /><br /> <span data-ttu-id="4f384-178">5 = 排他ロック (LCK_M_X)</span><span class="sxs-lookup"><span data-stu-id="4f384-178">5=Exclusive Lock (LCK_M_X)</span></span><br /><br /> <span data-ttu-id="4f384-179">6 = インテント共有ロック (LCK_M_IS)</span><span class="sxs-lookup"><span data-stu-id="4f384-179">6=Intent Shared Lock (LCK_M_IS)</span></span><br /><br /> <span data-ttu-id="4f384-180">7 = インテント更新ロック (LCK_M_IU)</span><span class="sxs-lookup"><span data-stu-id="4f384-180">7=Intent Update Lock (LCK_M_IU)</span></span><br /><br /> <span data-ttu-id="4f384-181">8 = インテント排他ロック (LCK_M_IX)</span><span class="sxs-lookup"><span data-stu-id="4f384-181">8=Intent Exclusive Lock (LCK_M_IX)</span></span><br /><br /> <span data-ttu-id="4f384-182">9 = 更新のためのインテント付き共有 (LCK_M_SIU)</span><span class="sxs-lookup"><span data-stu-id="4f384-182">9=Shared with intent to Update (LCK_M_SIU)</span></span><br /><br /> <span data-ttu-id="4f384-183">10 = インテント排他付き共有 (LCK_M_SIX)</span><span class="sxs-lookup"><span data-stu-id="4f384-183">10=Shared with Intent Exclusive (LCK_M_SIX)</span></span><br /><br /> <span data-ttu-id="4f384-184">11 = インテント排他付き更新 (LCK_M_UIX)</span><span class="sxs-lookup"><span data-stu-id="4f384-184">11=Update with Intent Exclusive (LCK_M_UIX)</span></span><br /><br /> <span data-ttu-id="4f384-185">12 = 一括更新ロック (LCK_M_BU)</span><span class="sxs-lookup"><span data-stu-id="4f384-185">12=Bulk Update Lock (LCK_M_BU)</span></span><br /><br /> <span data-ttu-id="4f384-186">13 = 共有キー範囲/共有 (LCK_M_RS_S)</span><span class="sxs-lookup"><span data-stu-id="4f384-186">13=Key range Shared/Shared (LCK_M_RS_S)</span></span><br /><br /> <span data-ttu-id="4f384-187">14 = 共有キー範囲/更新 (LCK_M_RS_U)</span><span class="sxs-lookup"><span data-stu-id="4f384-187">14=Key range Shared/Update (LCK_M_RS_U)</span></span><br /><br /> <span data-ttu-id="4f384-188">15 = キー範囲挿入/NULL (LCK_M_RI_NL)</span><span class="sxs-lookup"><span data-stu-id="4f384-188">15=Key Range Insert NULL (LCK_M_RI_NL)</span></span><br /><br /> <span data-ttu-id="4f384-189">16 = 挿入キー範囲/共有 (LCK_M_RI_S)</span><span class="sxs-lookup"><span data-stu-id="4f384-189">16=Key Range Insert Shared (LCK_M_RI_S)</span></span><br /><br /> <span data-ttu-id="4f384-190">17 = 挿入キー範囲/更新 (LCK_M_RI_U)</span><span class="sxs-lookup"><span data-stu-id="4f384-190">17=Key Range Insert Update (LCK_M_RI_U)</span></span><br /><br /> <span data-ttu-id="4f384-191">18 = 挿入キー範囲/排他 (LCK_M_RI_X)</span><span class="sxs-lookup"><span data-stu-id="4f384-191">18=Key Range Insert Exclusive (LCK_M_RI_X)</span></span><br /><br /> <span data-ttu-id="4f384-192">19 = 排他キー範囲/共有 (LCK_M_RX_S)</span><span class="sxs-lookup"><span data-stu-id="4f384-192">19=Key Range Exclusive Shared (LCK_M_RX_S)</span></span><br /><br /> <span data-ttu-id="4f384-193">20 = 排他キー範囲/更新 (LCK_M_RX_U)</span><span class="sxs-lookup"><span data-stu-id="4f384-193">20=Key Range Exclusive Update (LCK_M_RX_U)</span></span><br /><br /> <span data-ttu-id="4f384-194">21 = 排他キー範囲/排他 (LCK_M_RX_X)</span><span class="sxs-lookup"><span data-stu-id="4f384-194">21=Key Range Exclusive Exclusive (LCK_M_RX_X)</span></span>|<span data-ttu-id="4f384-195">32</span><span class="sxs-lookup"><span data-stu-id="4f384-195">32</span></span>|<span data-ttu-id="4f384-196">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-196">Yes</span></span>|  
|<span data-ttu-id="4f384-197">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="4f384-197">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="4f384-198">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="4f384-198">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="4f384-199">7</span><span class="sxs-lookup"><span data-stu-id="4f384-199">7</span></span>|<span data-ttu-id="4f384-200">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-200">Yes</span></span>|  
|<span data-ttu-id="4f384-201">NTUserName</span><span class="sxs-lookup"><span data-stu-id="4f384-201">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="4f384-202">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="4f384-202">Windows user name.</span></span>|<span data-ttu-id="4f384-203">6</span><span class="sxs-lookup"><span data-stu-id="4f384-203">6</span></span>|<span data-ttu-id="4f384-204">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-204">Yes</span></span>|  
|<span data-ttu-id="4f384-205">ObjectID</span><span class="sxs-lookup"><span data-stu-id="4f384-205">ObjectID</span></span>|`int`|<span data-ttu-id="4f384-206">解放されたオブジェクトのシステム割り当て ID (使用可能かつ適用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="4f384-206">System-assigned ID of the object which was released, if available and applicable.</span></span>|<span data-ttu-id="4f384-207">22</span><span class="sxs-lookup"><span data-stu-id="4f384-207">22</span></span>|<span data-ttu-id="4f384-208">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-208">Yes</span></span>|  
|<span data-ttu-id="4f384-209">ObjectID2</span><span class="sxs-lookup"><span data-stu-id="4f384-209">ObjectID2</span></span>|`bigint`|<span data-ttu-id="4f384-210">関連するオブジェクトまたはエンティティの ID (使用可能かつ適用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="4f384-210">ID of the related object or entity, if available and applicable.</span></span>|<span data-ttu-id="4f384-211">56</span><span class="sxs-lookup"><span data-stu-id="4f384-211">56</span></span>|<span data-ttu-id="4f384-212">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-212">Yes</span></span>|  
|<span data-ttu-id="4f384-213">OwnerID</span><span class="sxs-lookup"><span data-stu-id="4f384-213">OwnerID</span></span>|`int`|<span data-ttu-id="4f384-214">1 = TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="4f384-214">1=TRANSACTION</span></span><br /><br /> <span data-ttu-id="4f384-215">2 = CURSOR</span><span class="sxs-lookup"><span data-stu-id="4f384-215">2=CURSOR</span></span><br /><br /> <span data-ttu-id="4f384-216">3 = SESSION</span><span class="sxs-lookup"><span data-stu-id="4f384-216">3=SESSION</span></span><br /><br /> <span data-ttu-id="4f384-217">4 = SHARED_TRANSACTION_WORKSPACE</span><span class="sxs-lookup"><span data-stu-id="4f384-217">4=SHARED_TRANSACTION_WORKSPACE</span></span><br /><br /> <span data-ttu-id="4f384-218">5 = EXCLUSIVE_TRANSACTION_WORKSPACE</span><span class="sxs-lookup"><span data-stu-id="4f384-218">5=EXCLUSIVE_TRANSACTION_WORKSPACE</span></span>|<span data-ttu-id="4f384-219">58</span><span class="sxs-lookup"><span data-stu-id="4f384-219">58</span></span>|<span data-ttu-id="4f384-220">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-220">Yes</span></span>|  
|<span data-ttu-id="4f384-221">RequestID</span><span class="sxs-lookup"><span data-stu-id="4f384-221">RequestID</span></span>|`int`|<span data-ttu-id="4f384-222">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="4f384-222">ID of the request containing the statement.</span></span>|<span data-ttu-id="4f384-223">49</span><span class="sxs-lookup"><span data-stu-id="4f384-223">49</span></span>|<span data-ttu-id="4f384-224">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-224">Yes</span></span>|  
|<span data-ttu-id="4f384-225">ServerName</span><span class="sxs-lookup"><span data-stu-id="4f384-225">ServerName</span></span>|`nvarchar`|<span data-ttu-id="4f384-226">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="4f384-226">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="4f384-227">26</span><span class="sxs-lookup"><span data-stu-id="4f384-227">26</span></span>|<span data-ttu-id="4f384-228">いいえ</span><span class="sxs-lookup"><span data-stu-id="4f384-228">No</span></span>|  
|<span data-ttu-id="4f384-229">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="4f384-229">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="4f384-230">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="4f384-230">Login name of the user who originated the session.</span></span> <span data-ttu-id="4f384-231">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-231">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="4f384-232">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-232">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="4f384-233">64</span><span class="sxs-lookup"><span data-stu-id="4f384-233">64</span></span>|<span data-ttu-id="4f384-234">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-234">Yes</span></span>|  
|<span data-ttu-id="4f384-235">SPID</span><span class="sxs-lookup"><span data-stu-id="4f384-235">SPID</span></span>|`int`|<span data-ttu-id="4f384-236">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="4f384-236">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="4f384-237">12</span><span class="sxs-lookup"><span data-stu-id="4f384-237">12</span></span>|<span data-ttu-id="4f384-238">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-238">Yes</span></span>|  
|<span data-ttu-id="4f384-239">StartTime</span><span class="sxs-lookup"><span data-stu-id="4f384-239">StartTime</span></span>|`datetime`|<span data-ttu-id="4f384-240">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="4f384-240">Time at which the event started, if available.</span></span>|<span data-ttu-id="4f384-241">14</span><span class="sxs-lookup"><span data-stu-id="4f384-241">14</span></span>|<span data-ttu-id="4f384-242">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-242">Yes</span></span>|  
|<span data-ttu-id="4f384-243">TextData</span><span class="sxs-lookup"><span data-stu-id="4f384-243">TextData</span></span>|`ntext`|<span data-ttu-id="4f384-244">トレースでキャプチャされたイベント クラスに依存するテキスト値。</span><span class="sxs-lookup"><span data-stu-id="4f384-244">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="4f384-245">1</span><span class="sxs-lookup"><span data-stu-id="4f384-245">1</span></span>|<span data-ttu-id="4f384-246">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-246">Yes</span></span>|  
|<span data-ttu-id="4f384-247">TransactionID</span><span class="sxs-lookup"><span data-stu-id="4f384-247">TransactionID</span></span>|`bigint`|<span data-ttu-id="4f384-248">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="4f384-248">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="4f384-249">4</span><span class="sxs-lookup"><span data-stu-id="4f384-249">4</span></span>|<span data-ttu-id="4f384-250">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-250">Yes</span></span>|  
|<span data-ttu-id="4f384-251">Type</span><span class="sxs-lookup"><span data-stu-id="4f384-251">Type</span></span>|`int`|<span data-ttu-id="4f384-252">1 = NULL_RESOURCE</span><span class="sxs-lookup"><span data-stu-id="4f384-252">1=NULL_RESOURCE</span></span><br /><br /> <span data-ttu-id="4f384-253">2 = DATABASE</span><span class="sxs-lookup"><span data-stu-id="4f384-253">2=DATABASE</span></span><br /><br /> <span data-ttu-id="4f384-254">3 = FILE</span><span class="sxs-lookup"><span data-stu-id="4f384-254">3=FILE</span></span><br /><br /> <span data-ttu-id="4f384-255">5 = OBJECT</span><span class="sxs-lookup"><span data-stu-id="4f384-255">5=OBJECT</span></span><br /><br /> <span data-ttu-id="4f384-256">6 = PAGE</span><span class="sxs-lookup"><span data-stu-id="4f384-256">6=PAGE</span></span><br /><br /> <span data-ttu-id="4f384-257">7 = KEY</span><span class="sxs-lookup"><span data-stu-id="4f384-257">7=KEY</span></span><br /><br /> <span data-ttu-id="4f384-258">8 = EXTENT</span><span class="sxs-lookup"><span data-stu-id="4f384-258">8=EXTENT</span></span><br /><br /> <span data-ttu-id="4f384-259">9 = RID</span><span class="sxs-lookup"><span data-stu-id="4f384-259">9=RID</span></span><br /><br /> <span data-ttu-id="4f384-260">10 = APPLICATION</span><span class="sxs-lookup"><span data-stu-id="4f384-260">10=APPLICATION</span></span><br /><br /> <span data-ttu-id="4f384-261">11 = METADATA</span><span class="sxs-lookup"><span data-stu-id="4f384-261">11=METADATA</span></span><br /><br /> <span data-ttu-id="4f384-262">12 = AUTONAMEDB</span><span class="sxs-lookup"><span data-stu-id="4f384-262">12=AUTONAMEDB</span></span><br /><br /> <span data-ttu-id="4f384-263">13 = HOBT</span><span class="sxs-lookup"><span data-stu-id="4f384-263">13=HOBT</span></span><br /><br /> <span data-ttu-id="4f384-264">14 = ALLOCATION_UNIT</span><span class="sxs-lookup"><span data-stu-id="4f384-264">14=ALLOCATION_UNIT</span></span>|<span data-ttu-id="4f384-265">57</span><span class="sxs-lookup"><span data-stu-id="4f384-265">57</span></span>|<span data-ttu-id="4f384-266">はい</span><span class="sxs-lookup"><span data-stu-id="4f384-266">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f384-267">参照</span><span class="sxs-lookup"><span data-stu-id="4f384-267">See Also</span></span>  
 <span data-ttu-id="4f384-268">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4f384-268">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="4f384-269">[Lock: 獲得されたイベントクラス](lock-acquired-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="4f384-269">[Lock:Acquired Event Class](lock-acquired-event-class.md) </span></span>  
 [<span data-ttu-id="4f384-270">sys.dm_tran_locks &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4f384-270">sys.dm_tran_locks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
  