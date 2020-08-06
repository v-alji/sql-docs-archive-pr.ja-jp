---
title: Audit Server Scope GDR イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Scope GDR event class
ms.assetid: d3b1e47f-2ba2-49af-b404-1aa231d4e4a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa94f6f8d7705a0784da66d3d353e9537bc7d1a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715285"
---
# <a name="audit-server-scope-gdr-event-class"></a><span data-ttu-id="8523f-102">Audit Server Scope GDR イベント クラス</span><span class="sxs-lookup"><span data-stu-id="8523f-102">Audit Server Scope GDR Event Class</span></span>
  <span data-ttu-id="8523f-103">**Audit Server Scope GDR** イベント クラスは、ログインの作成など、サーバー スコープでの権限に対して GRANT、REVOKE、または DENY が実行されているときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8523f-103">The **Audit Server Scope GDR** event class occurs when a GRANT, REVOKE, or DENY is issued for permissions in the server scope, such as creating a login.</span></span>  
  
## <a name="audit-server-scope-gdr-event-class-data-columns"></a><span data-ttu-id="8523f-104">Audit Server Scope GDR イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="8523f-104">Audit Server Scope GDR Event Class Data Columns</span></span>  
  
|<span data-ttu-id="8523f-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="8523f-105">Data column name</span></span>|<span data-ttu-id="8523f-106">データ型</span><span class="sxs-lookup"><span data-stu-id="8523f-106">Data type</span></span>|<span data-ttu-id="8523f-107">説明</span><span class="sxs-lookup"><span data-stu-id="8523f-107">Description</span></span>|<span data-ttu-id="8523f-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="8523f-108">Column ID</span></span>|<span data-ttu-id="8523f-109">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="8523f-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="8523f-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="8523f-110">**ApplicationName**</span></span>|<span data-ttu-id="8523f-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-111">**nvarchar**</span></span>|<span data-ttu-id="8523f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="8523f-112">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8523f-113">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8523f-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="8523f-114">10</span><span class="sxs-lookup"><span data-stu-id="8523f-114">10</span></span>|<span data-ttu-id="8523f-115">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-115">Yes</span></span>|  
|<span data-ttu-id="8523f-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="8523f-116">**ClientProcessID**</span></span>|<span data-ttu-id="8523f-117">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-117">**int**</span></span>|<span data-ttu-id="8523f-118">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="8523f-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="8523f-119">クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8523f-119">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="8523f-120">9</span><span class="sxs-lookup"><span data-stu-id="8523f-120">9</span></span>|<span data-ttu-id="8523f-121">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-121">Yes</span></span>|  
|<span data-ttu-id="8523f-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="8523f-122">**DatabaseID**</span></span>|<span data-ttu-id="8523f-123">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-123">**int**</span></span>|<span data-ttu-id="8523f-124">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="8523f-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="8523f-125">では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8523f-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="8523f-126">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="8523f-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="8523f-127">3</span><span class="sxs-lookup"><span data-stu-id="8523f-127">3</span></span>|<span data-ttu-id="8523f-128">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-128">Yes</span></span>|  
|<span data-ttu-id="8523f-129">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="8523f-129">**DatabaseName**</span></span>|<span data-ttu-id="8523f-130">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-130">**nvarchar**</span></span>|<span data-ttu-id="8523f-131">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="8523f-131">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="8523f-132">35</span><span class="sxs-lookup"><span data-stu-id="8523f-132">35</span></span>|<span data-ttu-id="8523f-133">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-133">Yes</span></span>|  
|<span data-ttu-id="8523f-134">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="8523f-134">**DBUserName**</span></span>|<span data-ttu-id="8523f-135">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-135">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8523f-136">ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="8523f-136">user name of the client.</span></span>|<span data-ttu-id="8523f-137">40</span><span class="sxs-lookup"><span data-stu-id="8523f-137">40</span></span>|<span data-ttu-id="8523f-138">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-138">Yes</span></span>|  
|<span data-ttu-id="8523f-139">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="8523f-139">**EventClass**</span></span>|<span data-ttu-id="8523f-140">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-140">**int**</span></span>|<span data-ttu-id="8523f-141">イベントの種類 = 170。</span><span class="sxs-lookup"><span data-stu-id="8523f-141">Type of event = 170.</span></span>|<span data-ttu-id="8523f-142">27</span><span class="sxs-lookup"><span data-stu-id="8523f-142">27</span></span>|<span data-ttu-id="8523f-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="8523f-143">No</span></span>|  
|<span data-ttu-id="8523f-144">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="8523f-144">**EventSequence**</span></span>|<span data-ttu-id="8523f-145">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-145">**int**</span></span>|<span data-ttu-id="8523f-146">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="8523f-146">Sequence of a given event within the request.</span></span>|<span data-ttu-id="8523f-147">51</span><span class="sxs-lookup"><span data-stu-id="8523f-147">51</span></span>|<span data-ttu-id="8523f-148">いいえ</span><span class="sxs-lookup"><span data-stu-id="8523f-148">No</span></span>|  
|<span data-ttu-id="8523f-149">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="8523f-149">**EventSubClass**</span></span>|<span data-ttu-id="8523f-150">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-150">**int**</span></span>|<span data-ttu-id="8523f-151">イベント サブクラスの種類。</span><span class="sxs-lookup"><span data-stu-id="8523f-151">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="8523f-152">1 = 許可</span><span class="sxs-lookup"><span data-stu-id="8523f-152">1=Grant</span></span><br /><br /> <span data-ttu-id="8523f-153">2 = 取り消し</span><span class="sxs-lookup"><span data-stu-id="8523f-153">2=Revoke</span></span><br /><br /> <span data-ttu-id="8523f-154">3 = 拒否</span><span class="sxs-lookup"><span data-stu-id="8523f-154">3=Deny</span></span>|<span data-ttu-id="8523f-155">21</span><span class="sxs-lookup"><span data-stu-id="8523f-155">21</span></span>|<span data-ttu-id="8523f-156">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-156">Yes</span></span>|  
|<span data-ttu-id="8523f-157">**HostName**</span><span class="sxs-lookup"><span data-stu-id="8523f-157">**HostName**</span></span>|<span data-ttu-id="8523f-158">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-158">**nvarchar**</span></span>|<span data-ttu-id="8523f-159">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="8523f-159">Name of the computer on which the client is running.</span></span> <span data-ttu-id="8523f-160">このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="8523f-160">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="8523f-161">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="8523f-161">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="8523f-162">8</span><span class="sxs-lookup"><span data-stu-id="8523f-162">8</span></span>|<span data-ttu-id="8523f-163">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-163">Yes</span></span>|  
|<span data-ttu-id="8523f-164">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="8523f-164">**IsSystem**</span></span>|<span data-ttu-id="8523f-165">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-165">**int**</span></span>|<span data-ttu-id="8523f-166">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="8523f-166">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="8523f-167">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="8523f-167">1 = system, 0 = user.</span></span>|<span data-ttu-id="8523f-168">60</span><span class="sxs-lookup"><span data-stu-id="8523f-168">60</span></span>|<span data-ttu-id="8523f-169">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-169">Yes</span></span>|  
|<span data-ttu-id="8523f-170">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="8523f-170">**LoginName**</span></span>|<span data-ttu-id="8523f-171">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-171">**nvarchar**</span></span>|<span data-ttu-id="8523f-172">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログイン、または DOMAIN\username の形式で表された [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="8523f-172">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="8523f-173">11</span><span class="sxs-lookup"><span data-stu-id="8523f-173">11</span></span>|<span data-ttu-id="8523f-174">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-174">Yes</span></span>|  
|<span data-ttu-id="8523f-175">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="8523f-175">**LoginSid**</span></span>|<span data-ttu-id="8523f-176">**画像**</span><span class="sxs-lookup"><span data-stu-id="8523f-176">**image**</span></span>|<span data-ttu-id="8523f-177">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="8523f-177">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="8523f-178">この情報は、 **sys.server_principals** カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="8523f-178">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="8523f-179">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="8523f-179">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="8523f-180">41</span><span class="sxs-lookup"><span data-stu-id="8523f-180">41</span></span>|<span data-ttu-id="8523f-181">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-181">Yes</span></span>|  
|<span data-ttu-id="8523f-182">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="8523f-182">**NTDomainName**</span></span>|<span data-ttu-id="8523f-183">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-183">**nvarchar**</span></span>|<span data-ttu-id="8523f-184">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="8523f-184">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="8523f-185">7</span><span class="sxs-lookup"><span data-stu-id="8523f-185">7</span></span>|<span data-ttu-id="8523f-186">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-186">Yes</span></span>|  
|<span data-ttu-id="8523f-187">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="8523f-187">**NTUserName**</span></span>|<span data-ttu-id="8523f-188">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-188">**nvarchar**</span></span>|<span data-ttu-id="8523f-189">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="8523f-189">Windows user name.</span></span>|<span data-ttu-id="8523f-190">6</span><span class="sxs-lookup"><span data-stu-id="8523f-190">6</span></span>|<span data-ttu-id="8523f-191">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-191">Yes</span></span>|  
|<span data-ttu-id="8523f-192">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="8523f-192">**ObjectName**</span></span>|<span data-ttu-id="8523f-193">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-193">**nvarchar**</span></span>|<span data-ttu-id="8523f-194">参照されているオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="8523f-194">Name of the object being referenced.</span></span>|<span data-ttu-id="8523f-195">34</span><span class="sxs-lookup"><span data-stu-id="8523f-195">34</span></span>|<span data-ttu-id="8523f-196">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-196">Yes</span></span>|  
|<span data-ttu-id="8523f-197">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="8523f-197">**ObjectType**</span></span>|<span data-ttu-id="8523f-198">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-198">**int**</span></span>|<span data-ttu-id="8523f-199">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="8523f-199">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="8523f-200">この値は **sys.objects** カタログ ビューの type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="8523f-200">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="8523f-201">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8523f-201">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="8523f-202">28</span><span class="sxs-lookup"><span data-stu-id="8523f-202">28</span></span>|<span data-ttu-id="8523f-203">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-203">Yes</span></span>|  
|<span data-ttu-id="8523f-204">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="8523f-204">**OwnerName**</span></span>|<span data-ttu-id="8523f-205">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-205">**nvarchar**</span></span>|<span data-ttu-id="8523f-206">オブジェクト所有者のデータベース ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="8523f-206">Database user name of the object owner.</span></span>|<span data-ttu-id="8523f-207">37</span><span class="sxs-lookup"><span data-stu-id="8523f-207">37</span></span>|<span data-ttu-id="8523f-208">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-208">Yes</span></span>|  
|<span data-ttu-id="8523f-209">**アクセス許可**</span><span class="sxs-lookup"><span data-stu-id="8523f-209">**Permissions**</span></span>|<span data-ttu-id="8523f-210">**bigint**</span><span class="sxs-lookup"><span data-stu-id="8523f-210">**bigint**</span></span>|<span data-ttu-id="8523f-211">チェックする権限の種類を表す整数値。</span><span class="sxs-lookup"><span data-stu-id="8523f-211">Integer value representing the type of permissions checked.</span></span><br /><br /> <span data-ttu-id="8523f-212">1 = SELECT ALL</span><span class="sxs-lookup"><span data-stu-id="8523f-212">1 = SELECT ALL</span></span><br /><br /> <span data-ttu-id="8523f-213">2 = UPDATE ALL</span><span class="sxs-lookup"><span data-stu-id="8523f-213">2 = UPDATE ALL</span></span><br /><br /> <span data-ttu-id="8523f-214">4 = REFERENCES ALL</span><span class="sxs-lookup"><span data-stu-id="8523f-214">4 = REFERENCES ALL</span></span><br /><br /> <span data-ttu-id="8523f-215">8 = INSERT</span><span class="sxs-lookup"><span data-stu-id="8523f-215">8 = INSERT</span></span><br /><br /> <span data-ttu-id="8523f-216">16 = DELETE</span><span class="sxs-lookup"><span data-stu-id="8523f-216">16 = DELETE</span></span><br /><br /> <span data-ttu-id="8523f-217">32 = EXECUTE (プロシージャのみ)</span><span class="sxs-lookup"><span data-stu-id="8523f-217">32 = EXECUTE (procedures only)</span></span><br /><br /> <span data-ttu-id="8523f-218">4096 = SELECT ANY (1 列以上)</span><span class="sxs-lookup"><span data-stu-id="8523f-218">4096 = SELECT ANY (at least one column)</span></span><br /><br /> <span data-ttu-id="8523f-219">8192 = UPDATE ANY</span><span class="sxs-lookup"><span data-stu-id="8523f-219">8192 = UPDATE ANY</span></span>|<span data-ttu-id="8523f-220">19</span><span class="sxs-lookup"><span data-stu-id="8523f-220">19</span></span>|<span data-ttu-id="8523f-221">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-221">Yes</span></span>|  
|<span data-ttu-id="8523f-222">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="8523f-222">**RequestID**</span></span>|<span data-ttu-id="8523f-223">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-223">**int**</span></span>|<span data-ttu-id="8523f-224">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="8523f-224">ID of the request containing the statement.</span></span>|<span data-ttu-id="8523f-225">49</span><span class="sxs-lookup"><span data-stu-id="8523f-225">49</span></span>|<span data-ttu-id="8523f-226">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-226">Yes</span></span>|  
|<span data-ttu-id="8523f-227">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="8523f-227">**ServerName**</span></span>|<span data-ttu-id="8523f-228">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-228">**nvarchar**</span></span>|<span data-ttu-id="8523f-229">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="8523f-229">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="8523f-230">26</span><span class="sxs-lookup"><span data-stu-id="8523f-230">26</span></span>|<span data-ttu-id="8523f-231">いいえ</span><span class="sxs-lookup"><span data-stu-id="8523f-231">No</span></span>|  
|<span data-ttu-id="8523f-232">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="8523f-232">**SessionLoginName**</span></span>|<span data-ttu-id="8523f-233">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-233">**nvarchar**</span></span>|<span data-ttu-id="8523f-234">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="8523f-234">Login name of the user who originated the session.</span></span> <span data-ttu-id="8523f-235">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8523f-235">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="8523f-236">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8523f-236">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="8523f-237">64</span><span class="sxs-lookup"><span data-stu-id="8523f-237">64</span></span>|<span data-ttu-id="8523f-238">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-238">Yes</span></span>|  
|<span data-ttu-id="8523f-239">**SPID**</span><span class="sxs-lookup"><span data-stu-id="8523f-239">**SPID**</span></span>|<span data-ttu-id="8523f-240">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-240">**int**</span></span>|<span data-ttu-id="8523f-241">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="8523f-241">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="8523f-242">12</span><span class="sxs-lookup"><span data-stu-id="8523f-242">12</span></span>|<span data-ttu-id="8523f-243">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-243">Yes</span></span>|  
|<span data-ttu-id="8523f-244">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="8523f-244">**StartTime**</span></span>|<span data-ttu-id="8523f-245">**datetime**</span><span class="sxs-lookup"><span data-stu-id="8523f-245">**datetime**</span></span>|<span data-ttu-id="8523f-246">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="8523f-246">Time at which the event started, if available.</span></span>|<span data-ttu-id="8523f-247">14</span><span class="sxs-lookup"><span data-stu-id="8523f-247">14</span></span>|<span data-ttu-id="8523f-248">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-248">Yes</span></span>|  
|<span data-ttu-id="8523f-249">**Success**</span><span class="sxs-lookup"><span data-stu-id="8523f-249">**Success**</span></span>|<span data-ttu-id="8523f-250">**int**</span><span class="sxs-lookup"><span data-stu-id="8523f-250">**int**</span></span>|<span data-ttu-id="8523f-251">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="8523f-251">1 = success.</span></span> <span data-ttu-id="8523f-252">0 = 失敗。</span><span class="sxs-lookup"><span data-stu-id="8523f-252">0 = failure.</span></span> <span data-ttu-id="8523f-253">たとえば、値 1 は権限チェックの成功を示し、値 0 は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="8523f-253">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="8523f-254">23</span><span class="sxs-lookup"><span data-stu-id="8523f-254">23</span></span>|<span data-ttu-id="8523f-255">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-255">Yes</span></span>|  
|<span data-ttu-id="8523f-256">**TargetLoginName**</span><span class="sxs-lookup"><span data-stu-id="8523f-256">**TargetLoginName**</span></span>|<span data-ttu-id="8523f-257">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8523f-257">**nvarchar**</span></span>|<span data-ttu-id="8523f-258">新しいログインの追加など、ログインを対象とする操作で、対象となるログインの名前。</span><span class="sxs-lookup"><span data-stu-id="8523f-258">For actions that target a login (for example, adding a new login), the name of the targeted login.</span></span>|<span data-ttu-id="8523f-259">42</span><span class="sxs-lookup"><span data-stu-id="8523f-259">42</span></span>|<span data-ttu-id="8523f-260">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-260">Yes</span></span>|  
|<span data-ttu-id="8523f-261">**TargetLoginSid**</span><span class="sxs-lookup"><span data-stu-id="8523f-261">**TargetLoginSid**</span></span>|<span data-ttu-id="8523f-262">**画像**</span><span class="sxs-lookup"><span data-stu-id="8523f-262">**image**</span></span>|<span data-ttu-id="8523f-263">新しいログインの追加など、ログインを対象とする操作で、対象となるログインのセキュリティ識別番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="8523f-263">For actions that target a login (for example, adding a new login), the security identification number (SID) of the targeted login.</span></span>|<span data-ttu-id="8523f-264">43</span><span class="sxs-lookup"><span data-stu-id="8523f-264">43</span></span>|<span data-ttu-id="8523f-265">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-265">Yes</span></span>|  
|<span data-ttu-id="8523f-266">**TextData**</span><span class="sxs-lookup"><span data-stu-id="8523f-266">**TextData**</span></span>|<span data-ttu-id="8523f-267">**ntext**</span><span class="sxs-lookup"><span data-stu-id="8523f-267">**ntext**</span></span>|<span data-ttu-id="8523f-268">トレースでキャプチャされたイベント クラスに依存するテキスト値。</span><span class="sxs-lookup"><span data-stu-id="8523f-268">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="8523f-269">1</span><span class="sxs-lookup"><span data-stu-id="8523f-269">1</span></span>|<span data-ttu-id="8523f-270">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-270">Yes</span></span>|  
|<span data-ttu-id="8523f-271">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="8523f-271">**TransactionID**</span></span>|<span data-ttu-id="8523f-272">**bigint**</span><span class="sxs-lookup"><span data-stu-id="8523f-272">**bigint**</span></span>|<span data-ttu-id="8523f-273">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="8523f-273">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="8523f-274">4</span><span class="sxs-lookup"><span data-stu-id="8523f-274">4</span></span>|<span data-ttu-id="8523f-275">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-275">Yes</span></span>|  
|<span data-ttu-id="8523f-276">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="8523f-276">**XactSequence**</span></span>|<span data-ttu-id="8523f-277">**bigint**</span><span class="sxs-lookup"><span data-stu-id="8523f-277">**bigint**</span></span>|<span data-ttu-id="8523f-278">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="8523f-278">Token used to describe the current transaction.</span></span>|<span data-ttu-id="8523f-279">50</span><span class="sxs-lookup"><span data-stu-id="8523f-279">50</span></span>|<span data-ttu-id="8523f-280">はい</span><span class="sxs-lookup"><span data-stu-id="8523f-280">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8523f-281">参照</span><span class="sxs-lookup"><span data-stu-id="8523f-281">See Also</span></span>  
 <span data-ttu-id="8523f-282">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="8523f-282">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="8523f-283">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8523f-283">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="8523f-284">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8523f-284">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="8523f-285">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8523f-285">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 [<span data-ttu-id="8523f-286">DENY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8523f-286">DENY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/deny-transact-sql)  
  
  