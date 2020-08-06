---
title: Log File Auto Grow イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Log File Auto Grow event class
ms.assetid: e9b023db-6944-4035-9a83-300f34a58454
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7e2df6f0c16ce747617af7db180398042fbb30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643378"
---
# <a name="log-file-auto-grow-event-class"></a><span data-ttu-id="5cd0a-102">Log File Auto Grow イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5cd0a-102">Log File Auto Grow Event Class</span></span>
  <span data-ttu-id="5cd0a-103">**Log File Auto Grow** イベント クラスは、ログ ファイルが自動的に拡張されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-103">The **Log File Auto Grow** event class indicates that the log file grew automatically.</span></span> <span data-ttu-id="5cd0a-104">ログ ファイルが ALTER DATABASE により明示的に拡張された場合、このイベントはトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-104">This event is not triggered if the log file is grown explicitly through ALTER DATABASE.</span></span>  
  
 <span data-ttu-id="5cd0a-105">**Log File Auto Grow** イベント クラスは、ログ ファイルの拡張を監視するトレースに含めます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-105">Include the **Log File Auto Grow** event class in traces that are monitoring the log file growth.</span></span> <span data-ttu-id="5cd0a-106">このイベント クラスをトレースに含めても、ログ ファイルが頻繁に自動拡張されない限り、オーバーヘッドはそれほど発生しません。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-106">When this event class is included in a trace the amount of overhead incurred will be low unless the log file is growing automatically frequently.</span></span>  
  
## <a name="log-file-auto-grow-event-class-data-columns"></a><span data-ttu-id="5cd0a-107">Log File Auto Grow イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="5cd0a-107">Log File Auto Grow Event Class Data Columns</span></span>  
  
|<span data-ttu-id="5cd0a-108">データ列名</span><span class="sxs-lookup"><span data-stu-id="5cd0a-108">Data column name</span></span>|<span data-ttu-id="5cd0a-109">データ型</span><span class="sxs-lookup"><span data-stu-id="5cd0a-109">Data type</span></span>|<span data-ttu-id="5cd0a-110">説明</span><span class="sxs-lookup"><span data-stu-id="5cd0a-110">Description</span></span>|<span data-ttu-id="5cd0a-111">列 ID</span><span class="sxs-lookup"><span data-stu-id="5cd0a-111">Column ID</span></span>|<span data-ttu-id="5cd0a-112">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="5cd0a-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="5cd0a-113">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-113">**ApplicationName**</span></span>|<span data-ttu-id="5cd0a-114">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-114">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-115">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5cd0a-116">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-116">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="5cd0a-117">10</span><span class="sxs-lookup"><span data-stu-id="5cd0a-117">10</span></span>|<span data-ttu-id="5cd0a-118">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-118">Yes</span></span>|  
|<span data-ttu-id="5cd0a-119">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-119">**ClientProcessID**</span></span>|<span data-ttu-id="5cd0a-120">**Int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-120">**Int**</span></span>|<span data-ttu-id="5cd0a-121">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-121">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="5cd0a-122">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-122">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="5cd0a-123">9</span><span class="sxs-lookup"><span data-stu-id="5cd0a-123">9</span></span>|<span data-ttu-id="5cd0a-124">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-124">Yes</span></span>|  
|<span data-ttu-id="5cd0a-125">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-125">**DatabaseID**</span></span>|<span data-ttu-id="5cd0a-126">**int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-126">**int**</span></span>|<span data-ttu-id="5cd0a-127">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-127">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="5cd0a-128">では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-128">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="5cd0a-129">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-129">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="5cd0a-130">3</span><span class="sxs-lookup"><span data-stu-id="5cd0a-130">3</span></span>|<span data-ttu-id="5cd0a-131">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-131">Yes</span></span>|  
|<span data-ttu-id="5cd0a-132">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-132">**DatabaseName**</span></span>|<span data-ttu-id="5cd0a-133">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-133">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-134">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-134">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="5cd0a-135">35</span><span class="sxs-lookup"><span data-stu-id="5cd0a-135">35</span></span>|<span data-ttu-id="5cd0a-136">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-136">Yes</span></span>|  
|<span data-ttu-id="5cd0a-137">**Duration**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-137">**Duration**</span></span>|<span data-ttu-id="5cd0a-138">**bigint**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-138">**bigint**</span></span>|<span data-ttu-id="5cd0a-139">ファイルの拡張に必要な時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-139">Length of time (in milliseconds) necessary to extend the file.</span></span>|<span data-ttu-id="5cd0a-140">13</span><span class="sxs-lookup"><span data-stu-id="5cd0a-140">13</span></span>|<span data-ttu-id="5cd0a-141">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-141">Yes</span></span>|  
|<span data-ttu-id="5cd0a-142">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-142">**EndTime**</span></span>|<span data-ttu-id="5cd0a-143">**datetime**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-143">**datetime**</span></span>|<span data-ttu-id="5cd0a-144">ログ ファイルの **自動拡張** が終了した時刻。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-144">Time that the log file **auto grow** ended.</span></span>|<span data-ttu-id="5cd0a-145">18</span><span class="sxs-lookup"><span data-stu-id="5cd0a-145">18</span></span>|<span data-ttu-id="5cd0a-146">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-146">Yes</span></span>|  
|<span data-ttu-id="5cd0a-147">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-147">**EventClass**</span></span>|<span data-ttu-id="5cd0a-148">**int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-148">**int**</span></span>|<span data-ttu-id="5cd0a-149">イベントの種類 = 93。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-149">Type of event = 93.</span></span>|<span data-ttu-id="5cd0a-150">27</span><span class="sxs-lookup"><span data-stu-id="5cd0a-150">27</span></span>|<span data-ttu-id="5cd0a-151">いいえ</span><span class="sxs-lookup"><span data-stu-id="5cd0a-151">No</span></span>|  
|<span data-ttu-id="5cd0a-152">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-152">**EventSequence**</span></span>|<span data-ttu-id="5cd0a-153">**int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-153">**int**</span></span>|<span data-ttu-id="5cd0a-154">バッチ内の **CursorClose** イベント クラスのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-154">Sequence of **CursorClose** event class in batch.</span></span>|<span data-ttu-id="5cd0a-155">51</span><span class="sxs-lookup"><span data-stu-id="5cd0a-155">51</span></span>|<span data-ttu-id="5cd0a-156">いいえ</span><span class="sxs-lookup"><span data-stu-id="5cd0a-156">No</span></span>|  
|<span data-ttu-id="5cd0a-157">**Filename**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-157">**Filename**</span></span>|<span data-ttu-id="5cd0a-158">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-158">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-159">拡張されているファイルの論理名。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-159">Logical name of the file being extended.</span></span>|<span data-ttu-id="5cd0a-160">36</span><span class="sxs-lookup"><span data-stu-id="5cd0a-160">36</span></span>|<span data-ttu-id="5cd0a-161">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-161">Yes</span></span>|  
|<span data-ttu-id="5cd0a-162">**HostName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-162">**HostName**</span></span>|<span data-ttu-id="5cd0a-163">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-163">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-164">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-164">Name of the computer on which the client is running.</span></span> <span data-ttu-id="5cd0a-165">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-165">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="5cd0a-166">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-166">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="5cd0a-167">8</span><span class="sxs-lookup"><span data-stu-id="5cd0a-167">8</span></span>|<span data-ttu-id="5cd0a-168">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-168">Yes</span></span>|  
|<span data-ttu-id="5cd0a-169">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-169">**IntegerData**</span></span>|<span data-ttu-id="5cd0a-170">**Int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-170">**Int**</span></span>|<span data-ttu-id="5cd0a-171">ファイルの拡張単位を表す 8 KB ページの数。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-171">Number of 8-kilobyte (KB) pages by which the file increased.</span></span>|<span data-ttu-id="5cd0a-172">25</span><span class="sxs-lookup"><span data-stu-id="5cd0a-172">25</span></span>|<span data-ttu-id="5cd0a-173">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-173">Yes</span></span>|  
|<span data-ttu-id="5cd0a-174">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-174">**IsSystem**</span></span>|<span data-ttu-id="5cd0a-175">**int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-175">**int**</span></span>|<span data-ttu-id="5cd0a-176">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-176">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="5cd0a-177">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-177">1 = system, 0 = user.</span></span>|<span data-ttu-id="5cd0a-178">60</span><span class="sxs-lookup"><span data-stu-id="5cd0a-178">60</span></span>|<span data-ttu-id="5cd0a-179">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-179">Yes</span></span>|  
|<span data-ttu-id="5cd0a-180">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-180">**LoginName**</span></span>|<span data-ttu-id="5cd0a-181">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-181">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-182">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-182">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\Username).</span></span>|<span data-ttu-id="5cd0a-183">11</span><span class="sxs-lookup"><span data-stu-id="5cd0a-183">11</span></span>|<span data-ttu-id="5cd0a-184">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-184">Yes</span></span>|  
|<span data-ttu-id="5cd0a-185">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-185">**LoginSid**</span></span>|<span data-ttu-id="5cd0a-186">**画像**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-186">**image**</span></span>|<span data-ttu-id="5cd0a-187">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-187">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="5cd0a-188">この情報は、 **sys.server_principals** カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-188">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="5cd0a-189">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-189">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="5cd0a-190">41</span><span class="sxs-lookup"><span data-stu-id="5cd0a-190">41</span></span>|<span data-ttu-id="5cd0a-191">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-191">Yes</span></span>|  
|<span data-ttu-id="5cd0a-192">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-192">**NTDomainName**</span></span>|<span data-ttu-id="5cd0a-193">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-193">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-194">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-194">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="5cd0a-195">7</span><span class="sxs-lookup"><span data-stu-id="5cd0a-195">7</span></span>|<span data-ttu-id="5cd0a-196">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-196">Yes</span></span>|  
|<span data-ttu-id="5cd0a-197">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-197">**ServerName**</span></span>|<span data-ttu-id="5cd0a-198">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-198">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-199">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-199">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="5cd0a-200">26</span><span class="sxs-lookup"><span data-stu-id="5cd0a-200">26</span></span>|<span data-ttu-id="5cd0a-201">いいえ</span><span class="sxs-lookup"><span data-stu-id="5cd0a-201">No</span></span>|  
|<span data-ttu-id="5cd0a-202">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-202">**SessionLoginName**</span></span>|<span data-ttu-id="5cd0a-203">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-203">**nvarchar**</span></span>|<span data-ttu-id="5cd0a-204">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-204">Login name of the user who originated the session.</span></span> <span data-ttu-id="5cd0a-205">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-205">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="5cd0a-206">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-206">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="5cd0a-207">64</span><span class="sxs-lookup"><span data-stu-id="5cd0a-207">64</span></span>|<span data-ttu-id="5cd0a-208">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-208">Yes</span></span>|  
|<span data-ttu-id="5cd0a-209">**SPID**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-209">**SPID**</span></span>|<span data-ttu-id="5cd0a-210">**Int**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-210">**Int**</span></span>|<span data-ttu-id="5cd0a-211">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-211">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="5cd0a-212">12</span><span class="sxs-lookup"><span data-stu-id="5cd0a-212">12</span></span>|<span data-ttu-id="5cd0a-213">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-213">Yes</span></span>|  
|<span data-ttu-id="5cd0a-214">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-214">**StartTime**</span></span>|<span data-ttu-id="5cd0a-215">**datetime**</span><span class="sxs-lookup"><span data-stu-id="5cd0a-215">**datetime**</span></span>|<span data-ttu-id="5cd0a-216">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="5cd0a-216">Time at which the event started, if available.</span></span>|<span data-ttu-id="5cd0a-217">14</span><span class="sxs-lookup"><span data-stu-id="5cd0a-217">14</span></span>|<span data-ttu-id="5cd0a-218">はい</span><span class="sxs-lookup"><span data-stu-id="5cd0a-218">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5cd0a-219">参照</span><span class="sxs-lookup"><span data-stu-id="5cd0a-219">See Also</span></span>  
 <span data-ttu-id="5cd0a-220">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="5cd0a-220">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="5cd0a-221">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5cd0a-221">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="5cd0a-222">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5cd0a-222">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  