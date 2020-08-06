---
title: Audit App Role Change Password イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit App Role Change Password event class
ms.assetid: 28a76c12-e997-48bb-bb0e-9624237a188e
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac9633cdde5aa42f360249861abf711c1e81c8ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736384"
---
# <a name="audit-app-role-change-password-event-class"></a><span data-ttu-id="81773-102">Audit App Role Change Password イベント クラス</span><span class="sxs-lookup"><span data-stu-id="81773-102">Audit App Role Change Password Event Class</span></span>
  <span data-ttu-id="81773-103">**Audit App Role Change Password** イベント クラスは、アプリケーション ロールのパスワードが変更された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="81773-103">The **Audit App Role Change Password** event class occurs whenever a password is changed for an application role.</span></span>  
  
## <a name="audit-app-role-change-password-event-class-data-columns"></a><span data-ttu-id="81773-104">Audit App Role Change Password イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="81773-104">Audit App Role Change Password Event Class Data Columns</span></span>  
  
|<span data-ttu-id="81773-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="81773-105">Data column name</span></span>|<span data-ttu-id="81773-106">データ型</span><span class="sxs-lookup"><span data-stu-id="81773-106">Data type</span></span>|<span data-ttu-id="81773-107">説明</span><span class="sxs-lookup"><span data-stu-id="81773-107">Description</span></span>|<span data-ttu-id="81773-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="81773-108">Column ID</span></span>|<span data-ttu-id="81773-109">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="81773-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="81773-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="81773-110">**ApplicationName**</span></span>|<span data-ttu-id="81773-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-111">**nvarchar**</span></span>|<span data-ttu-id="81773-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="81773-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="81773-113">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81773-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="81773-114">10</span><span class="sxs-lookup"><span data-stu-id="81773-114">10</span></span>|<span data-ttu-id="81773-115">はい</span><span class="sxs-lookup"><span data-stu-id="81773-115">Yes</span></span>|  
|<span data-ttu-id="81773-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="81773-116">**ClientProcessID**</span></span>|<span data-ttu-id="81773-117">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-117">**int**</span></span>|<span data-ttu-id="81773-118">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="81773-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="81773-119">クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="81773-119">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="81773-120">9</span><span class="sxs-lookup"><span data-stu-id="81773-120">9</span></span>|<span data-ttu-id="81773-121">はい</span><span class="sxs-lookup"><span data-stu-id="81773-121">Yes</span></span>|  
|<span data-ttu-id="81773-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="81773-122">**DatabaseID**</span></span>|<span data-ttu-id="81773-123">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-123">**int**</span></span>|<span data-ttu-id="81773-124">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="81773-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="81773-125">では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81773-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="81773-126">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="81773-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="81773-127">3</span><span class="sxs-lookup"><span data-stu-id="81773-127">3</span></span>|<span data-ttu-id="81773-128">はい</span><span class="sxs-lookup"><span data-stu-id="81773-128">Yes</span></span>|  
|<span data-ttu-id="81773-129">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="81773-129">**DatabaseName**</span></span>|<span data-ttu-id="81773-130">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-130">**nvarchar**</span></span>|<span data-ttu-id="81773-131">アプリケーション ロールが変更されるデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="81773-131">Name of the database where the application role is being modified.</span></span>|<span data-ttu-id="81773-132">35</span><span class="sxs-lookup"><span data-stu-id="81773-132">35</span></span>|<span data-ttu-id="81773-133">はい</span><span class="sxs-lookup"><span data-stu-id="81773-133">Yes</span></span>|  
|<span data-ttu-id="81773-134">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="81773-134">**DBUserName**</span></span>|<span data-ttu-id="81773-135">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-135">**nvarchar**</span></span>|<span data-ttu-id="81773-136">データベース内の発行者のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="81773-136">Issuer's username in the database.</span></span>|<span data-ttu-id="81773-137">40</span><span class="sxs-lookup"><span data-stu-id="81773-137">40</span></span>|<span data-ttu-id="81773-138">はい</span><span class="sxs-lookup"><span data-stu-id="81773-138">Yes</span></span>|  
|<span data-ttu-id="81773-139">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="81773-139">**EventClass**</span></span>|<span data-ttu-id="81773-140">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-140">**int**</span></span>|<span data-ttu-id="81773-141">イベントの種類 = 112。</span><span class="sxs-lookup"><span data-stu-id="81773-141">Type of event = 112.</span></span>|<span data-ttu-id="81773-142">27</span><span class="sxs-lookup"><span data-stu-id="81773-142">27</span></span>|<span data-ttu-id="81773-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="81773-143">No</span></span>|  
|<span data-ttu-id="81773-144">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="81773-144">**EventSequence**</span></span>|<span data-ttu-id="81773-145">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-145">**int**</span></span>|<span data-ttu-id="81773-146">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="81773-146">Sequence of a given event within the request.</span></span>|<span data-ttu-id="81773-147">51</span><span class="sxs-lookup"><span data-stu-id="81773-147">51</span></span>|<span data-ttu-id="81773-148">いいえ</span><span class="sxs-lookup"><span data-stu-id="81773-148">No</span></span>|  
|<span data-ttu-id="81773-149">**HostName**</span><span class="sxs-lookup"><span data-stu-id="81773-149">**HostName**</span></span>|<span data-ttu-id="81773-150">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-150">**nvarchar**</span></span>|<span data-ttu-id="81773-151">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="81773-151">Name of the computer on which the client is running.</span></span> <span data-ttu-id="81773-152">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81773-152">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="81773-153">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="81773-153">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="81773-154">8</span><span class="sxs-lookup"><span data-stu-id="81773-154">8</span></span>|<span data-ttu-id="81773-155">はい</span><span class="sxs-lookup"><span data-stu-id="81773-155">Yes</span></span>|  
|<span data-ttu-id="81773-156">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="81773-156">**IsSystem**</span></span>|<span data-ttu-id="81773-157">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-157">**int**</span></span>|<span data-ttu-id="81773-158">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="81773-158">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="81773-159">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="81773-159">1 = system, 0 = user.</span></span>|<span data-ttu-id="81773-160">60</span><span class="sxs-lookup"><span data-stu-id="81773-160">60</span></span>|<span data-ttu-id="81773-161">はい</span><span class="sxs-lookup"><span data-stu-id="81773-161">Yes</span></span>|  
|<span data-ttu-id="81773-162">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="81773-162">**LoginName**</span></span>|<span data-ttu-id="81773-163">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-163">**nvarchar**</span></span>|<span data-ttu-id="81773-164">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログイン、または DOMAIN\username の形式で表された [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="81773-164">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="81773-165">11</span><span class="sxs-lookup"><span data-stu-id="81773-165">11</span></span>|<span data-ttu-id="81773-166">はい</span><span class="sxs-lookup"><span data-stu-id="81773-166">Yes</span></span>|  
|<span data-ttu-id="81773-167">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="81773-167">**LoginSid**</span></span>|<span data-ttu-id="81773-168">**画像**</span><span class="sxs-lookup"><span data-stu-id="81773-168">**image**</span></span>|<span data-ttu-id="81773-169">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="81773-169">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="81773-170">この情報は、 **sys.server_principals** カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="81773-170">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="81773-171">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="81773-171">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="81773-172">41</span><span class="sxs-lookup"><span data-stu-id="81773-172">41</span></span>|<span data-ttu-id="81773-173">はい</span><span class="sxs-lookup"><span data-stu-id="81773-173">Yes</span></span>|  
|<span data-ttu-id="81773-174">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="81773-174">**NTDomainName**</span></span>|<span data-ttu-id="81773-175">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-175">**nvarchar**</span></span>|<span data-ttu-id="81773-176">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="81773-176">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="81773-177">7</span><span class="sxs-lookup"><span data-stu-id="81773-177">7</span></span>|<span data-ttu-id="81773-178">はい</span><span class="sxs-lookup"><span data-stu-id="81773-178">Yes</span></span>|  
|<span data-ttu-id="81773-179">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="81773-179">**NTUserName**</span></span>|<span data-ttu-id="81773-180">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-180">**nvarchar**</span></span>|<span data-ttu-id="81773-181">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="81773-181">Windows user name.</span></span>|<span data-ttu-id="81773-182">6</span><span class="sxs-lookup"><span data-stu-id="81773-182">6</span></span>|<span data-ttu-id="81773-183">はい</span><span class="sxs-lookup"><span data-stu-id="81773-183">Yes</span></span>|  
|<span data-ttu-id="81773-184">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="81773-184">**ObjectName**</span></span>|<span data-ttu-id="81773-185">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-185">**nvarchar**</span></span>|<span data-ttu-id="81773-186">参照されているオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="81773-186">Name of the object being referenced.</span></span>|<span data-ttu-id="81773-187">34</span><span class="sxs-lookup"><span data-stu-id="81773-187">34</span></span>|<span data-ttu-id="81773-188">はい</span><span class="sxs-lookup"><span data-stu-id="81773-188">Yes</span></span>|  
|<span data-ttu-id="81773-189">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="81773-189">**ObjectType**</span></span>|<span data-ttu-id="81773-190">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-190">**int**</span></span>|<span data-ttu-id="81773-191">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="81773-191">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="81773-192">この値は **sys.objects** カタログ ビューの type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="81773-192">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="81773-193">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81773-193">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="81773-194">28</span><span class="sxs-lookup"><span data-stu-id="81773-194">28</span></span>|<span data-ttu-id="81773-195">はい</span><span class="sxs-lookup"><span data-stu-id="81773-195">Yes</span></span>|  
|<span data-ttu-id="81773-196">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="81773-196">**OwnerName**</span></span>|<span data-ttu-id="81773-197">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-197">**nvarchar**</span></span>|<span data-ttu-id="81773-198">オブジェクト所有者のデータベース ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="81773-198">Database user name of the object owner.</span></span>|<span data-ttu-id="81773-199">37</span><span class="sxs-lookup"><span data-stu-id="81773-199">37</span></span>|<span data-ttu-id="81773-200">はい</span><span class="sxs-lookup"><span data-stu-id="81773-200">Yes</span></span>|  
|<span data-ttu-id="81773-201">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="81773-201">**RequestID**</span></span>|<span data-ttu-id="81773-202">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-202">**int**</span></span>|<span data-ttu-id="81773-203">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="81773-203">ID of the request containing the statement.</span></span>|<span data-ttu-id="81773-204">49</span><span class="sxs-lookup"><span data-stu-id="81773-204">49</span></span>|<span data-ttu-id="81773-205">はい</span><span class="sxs-lookup"><span data-stu-id="81773-205">Yes</span></span>|  
|<span data-ttu-id="81773-206">**RoleName**</span><span class="sxs-lookup"><span data-stu-id="81773-206">**RoleName**</span></span>|<span data-ttu-id="81773-207">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-207">**nvarchar**</span></span>|<span data-ttu-id="81773-208">アプリケーション ロールの名前。</span><span class="sxs-lookup"><span data-stu-id="81773-208">Name of the application role.</span></span>|<span data-ttu-id="81773-209">38</span><span class="sxs-lookup"><span data-stu-id="81773-209">38</span></span>|<span data-ttu-id="81773-210">はい</span><span class="sxs-lookup"><span data-stu-id="81773-210">Yes</span></span>|  
|<span data-ttu-id="81773-211">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="81773-211">**ServerName**</span></span>|<span data-ttu-id="81773-212">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-212">**nvarchar**</span></span>|<span data-ttu-id="81773-213">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="81773-213">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="81773-214">26</span><span class="sxs-lookup"><span data-stu-id="81773-214">26</span></span>|<span data-ttu-id="81773-215">いいえ</span><span class="sxs-lookup"><span data-stu-id="81773-215">No</span></span>|  
|<span data-ttu-id="81773-216">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="81773-216">**SessionLoginName**</span></span>|<span data-ttu-id="81773-217">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="81773-217">**nvarchar**</span></span>|<span data-ttu-id="81773-218">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="81773-218">Login name of the user who originated the session.</span></span> <span data-ttu-id="81773-219">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81773-219">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="81773-220">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81773-220">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="81773-221">64</span><span class="sxs-lookup"><span data-stu-id="81773-221">64</span></span>|<span data-ttu-id="81773-222">はい</span><span class="sxs-lookup"><span data-stu-id="81773-222">Yes</span></span>|  
|<span data-ttu-id="81773-223">**SPID**</span><span class="sxs-lookup"><span data-stu-id="81773-223">**SPID**</span></span>|<span data-ttu-id="81773-224">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-224">**int**</span></span>|<span data-ttu-id="81773-225">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="81773-225">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="81773-226">12</span><span class="sxs-lookup"><span data-stu-id="81773-226">12</span></span>|<span data-ttu-id="81773-227">はい</span><span class="sxs-lookup"><span data-stu-id="81773-227">Yes</span></span>|  
|<span data-ttu-id="81773-228">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="81773-228">**StartTime**</span></span>|<span data-ttu-id="81773-229">**datetime**</span><span class="sxs-lookup"><span data-stu-id="81773-229">**datetime**</span></span>|<span data-ttu-id="81773-230">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="81773-230">Time at which the event started, when available.</span></span>|<span data-ttu-id="81773-231">14</span><span class="sxs-lookup"><span data-stu-id="81773-231">14</span></span>|<span data-ttu-id="81773-232">はい</span><span class="sxs-lookup"><span data-stu-id="81773-232">Yes</span></span>|  
|<span data-ttu-id="81773-233">**Success**</span><span class="sxs-lookup"><span data-stu-id="81773-233">**Success**</span></span>|<span data-ttu-id="81773-234">**int**</span><span class="sxs-lookup"><span data-stu-id="81773-234">**int**</span></span>|<span data-ttu-id="81773-235">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="81773-235">1 = success.</span></span> <span data-ttu-id="81773-236">0 = 失敗。</span><span class="sxs-lookup"><span data-stu-id="81773-236">0 = failure.</span></span> <span data-ttu-id="81773-237">たとえば、値 1 は権限チェックの成功を示し、値 0 は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="81773-237">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="81773-238">23</span><span class="sxs-lookup"><span data-stu-id="81773-238">23</span></span>|<span data-ttu-id="81773-239">はい</span><span class="sxs-lookup"><span data-stu-id="81773-239">Yes</span></span>|  
|<span data-ttu-id="81773-240">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="81773-240">**TransactionID**</span></span>|<span data-ttu-id="81773-241">**bigint**</span><span class="sxs-lookup"><span data-stu-id="81773-241">**bigint**</span></span>|<span data-ttu-id="81773-242">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="81773-242">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="81773-243">4</span><span class="sxs-lookup"><span data-stu-id="81773-243">4</span></span>|<span data-ttu-id="81773-244">はい</span><span class="sxs-lookup"><span data-stu-id="81773-244">Yes</span></span>|  
|<span data-ttu-id="81773-245">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="81773-245">**XactSequence**</span></span>|<span data-ttu-id="81773-246">**bigint**</span><span class="sxs-lookup"><span data-stu-id="81773-246">**bigint**</span></span>|<span data-ttu-id="81773-247">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="81773-247">Token used to describe the current transaction.</span></span>|<span data-ttu-id="81773-248">50</span><span class="sxs-lookup"><span data-stu-id="81773-248">50</span></span>|<span data-ttu-id="81773-249">はい</span><span class="sxs-lookup"><span data-stu-id="81773-249">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81773-250">参照</span><span class="sxs-lookup"><span data-stu-id="81773-250">See Also</span></span>  
 [<span data-ttu-id="81773-251">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="81773-251">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  