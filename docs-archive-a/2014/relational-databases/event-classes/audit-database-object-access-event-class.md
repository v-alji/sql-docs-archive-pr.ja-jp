---
title: Audit Database Object Access イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Database Object Access event class
ms.assetid: 0294ba51-6085-4de2-a52d-dac1a87fbd4d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0549e6b4980dd0e0e0e569b9dd95cf404b216c29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631054"
---
# <a name="audit-database-object-access-event-class"></a><span data-ttu-id="55f70-102">Audit Database Object Access イベント クラス</span><span class="sxs-lookup"><span data-stu-id="55f70-102">Audit Database Object Access Event Class</span></span>
  <span data-ttu-id="55f70-103">**Audit Database Object Access** イベント クラスは、スキーマなどのデータベース オブジェクトがアクセスされたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="55f70-103">The **Audit Database Object Access** event class occurs when database objects, such as schemas, are accessed.</span></span>  
  
## <a name="audit-database-object-access-event-class-data-columns"></a><span data-ttu-id="55f70-104">Audit Database Object Access イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="55f70-104">Audit Database Object Access Event Class Data Columns</span></span>  
  
|<span data-ttu-id="55f70-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="55f70-105">Data column name</span></span>|<span data-ttu-id="55f70-106">データ型</span><span class="sxs-lookup"><span data-stu-id="55f70-106">Data type</span></span>|<span data-ttu-id="55f70-107">説明</span><span class="sxs-lookup"><span data-stu-id="55f70-107">Description</span></span>|<span data-ttu-id="55f70-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="55f70-108">Column ID</span></span>|<span data-ttu-id="55f70-109">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="55f70-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="55f70-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="55f70-110">**ApplicationName**</span></span>|<span data-ttu-id="55f70-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-111">**nvarchar**</span></span>|<span data-ttu-id="55f70-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="55f70-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="55f70-113">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="55f70-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="55f70-114">10</span><span class="sxs-lookup"><span data-stu-id="55f70-114">10</span></span>|<span data-ttu-id="55f70-115">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-115">Yes</span></span>|  
|<span data-ttu-id="55f70-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="55f70-116">**DatabaseID**</span></span>|<span data-ttu-id="55f70-117">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-117">**int**</span></span>|<span data-ttu-id="55f70-118">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="55f70-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="55f70-119">では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55f70-119">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="55f70-120">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="55f70-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="55f70-121">3</span><span class="sxs-lookup"><span data-stu-id="55f70-121">3</span></span>|<span data-ttu-id="55f70-122">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-122">Yes</span></span>|  
|<span data-ttu-id="55f70-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="55f70-123">**DatabaseName**</span></span>|<span data-ttu-id="55f70-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-124">**nvarchar**</span></span>|<span data-ttu-id="55f70-125">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="55f70-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="55f70-126">35</span><span class="sxs-lookup"><span data-stu-id="55f70-126">35</span></span>|<span data-ttu-id="55f70-127">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-127">Yes</span></span>|  
|<span data-ttu-id="55f70-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="55f70-128">**DBUserName**</span></span>|<span data-ttu-id="55f70-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="55f70-130">ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="55f70-130">user name of the client.</span></span>|<span data-ttu-id="55f70-131">40</span><span class="sxs-lookup"><span data-stu-id="55f70-131">40</span></span>|<span data-ttu-id="55f70-132">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-132">Yes</span></span>|  
|<span data-ttu-id="55f70-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="55f70-133">**EventSequence**</span></span>|<span data-ttu-id="55f70-134">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-134">**int**</span></span>|<span data-ttu-id="55f70-135">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="55f70-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="55f70-136">51</span><span class="sxs-lookup"><span data-stu-id="55f70-136">51</span></span>|<span data-ttu-id="55f70-137">いいえ</span><span class="sxs-lookup"><span data-stu-id="55f70-137">No</span></span>|  
|<span data-ttu-id="55f70-138">**HostName**</span><span class="sxs-lookup"><span data-stu-id="55f70-138">**HostName**</span></span>|<span data-ttu-id="55f70-139">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-139">**nvarchar**</span></span>|<span data-ttu-id="55f70-140">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="55f70-140">Name of the computer on which the client is running.</span></span> <span data-ttu-id="55f70-141">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="55f70-141">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="55f70-142">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="55f70-142">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="55f70-143">8</span><span class="sxs-lookup"><span data-stu-id="55f70-143">8</span></span>|<span data-ttu-id="55f70-144">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-144">Yes</span></span>|  
|<span data-ttu-id="55f70-145">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="55f70-145">**IsSystem**</span></span>|<span data-ttu-id="55f70-146">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-146">**int**</span></span>|<span data-ttu-id="55f70-147">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="55f70-147">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="55f70-148">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="55f70-148">1 = system, 0 = user.</span></span>|<span data-ttu-id="55f70-149">60</span><span class="sxs-lookup"><span data-stu-id="55f70-149">60</span></span>|<span data-ttu-id="55f70-150">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-150">Yes</span></span>|  
|<span data-ttu-id="55f70-151">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="55f70-151">**LoginName**</span></span>|<span data-ttu-id="55f70-152">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-152">**nvarchar**</span></span>|<span data-ttu-id="55f70-153">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログイン、または DOMAIN\username の形式で表された [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="55f70-153">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="55f70-154">11</span><span class="sxs-lookup"><span data-stu-id="55f70-154">11</span></span>|<span data-ttu-id="55f70-155">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-155">Yes</span></span>|  
|<span data-ttu-id="55f70-156">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="55f70-156">**LoginSid**</span></span>|<span data-ttu-id="55f70-157">**画像**</span><span class="sxs-lookup"><span data-stu-id="55f70-157">**image**</span></span>|<span data-ttu-id="55f70-158">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="55f70-158">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="55f70-159">この情報は、 **sys.server_principals** カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="55f70-159">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="55f70-160">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="55f70-160">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="55f70-161">41</span><span class="sxs-lookup"><span data-stu-id="55f70-161">41</span></span>|<span data-ttu-id="55f70-162">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-162">Yes</span></span>|  
|<span data-ttu-id="55f70-163">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="55f70-163">**NTDomainName**</span></span>|<span data-ttu-id="55f70-164">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-164">**nvarchar**</span></span>|<span data-ttu-id="55f70-165">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="55f70-165">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="55f70-166">7</span><span class="sxs-lookup"><span data-stu-id="55f70-166">7</span></span>|<span data-ttu-id="55f70-167">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-167">Yes</span></span>|  
|<span data-ttu-id="55f70-168">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="55f70-168">**NTUserName**</span></span>|<span data-ttu-id="55f70-169">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-169">**nvarchar**</span></span>|<span data-ttu-id="55f70-170">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="55f70-170">Windows user name.</span></span>|<span data-ttu-id="55f70-171">6</span><span class="sxs-lookup"><span data-stu-id="55f70-171">6</span></span>|<span data-ttu-id="55f70-172">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-172">Yes</span></span>|  
|<span data-ttu-id="55f70-173">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="55f70-173">**ObjectName**</span></span>|<span data-ttu-id="55f70-174">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-174">**nvarchar**</span></span>|<span data-ttu-id="55f70-175">参照されているオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="55f70-175">Name of the object being referenced.</span></span>|<span data-ttu-id="55f70-176">34</span><span class="sxs-lookup"><span data-stu-id="55f70-176">34</span></span>|<span data-ttu-id="55f70-177">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-177">Yes</span></span>|  
|<span data-ttu-id="55f70-178">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="55f70-178">**ObjectType**</span></span>|<span data-ttu-id="55f70-179">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-179">**int**</span></span>|<span data-ttu-id="55f70-180">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="55f70-180">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="55f70-181">この値は **sys.objects** カタログ ビューの type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="55f70-181">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="55f70-182">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55f70-182">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="55f70-183">28</span><span class="sxs-lookup"><span data-stu-id="55f70-183">28</span></span>|<span data-ttu-id="55f70-184">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-184">Yes</span></span>|  
|<span data-ttu-id="55f70-185">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="55f70-185">**OwnerName**</span></span>|<span data-ttu-id="55f70-186">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-186">**nvarchar**</span></span>|<span data-ttu-id="55f70-187">オブジェクト所有者のデータベース ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="55f70-187">Database user name of the object owner.</span></span>|<span data-ttu-id="55f70-188">37</span><span class="sxs-lookup"><span data-stu-id="55f70-188">37</span></span>|<span data-ttu-id="55f70-189">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-189">Yes</span></span>|  
|<span data-ttu-id="55f70-190">**アクセス許可**</span><span class="sxs-lookup"><span data-stu-id="55f70-190">**Permissions**</span></span>|<span data-ttu-id="55f70-191">**bigint**</span><span class="sxs-lookup"><span data-stu-id="55f70-191">**bigint**</span></span>|<span data-ttu-id="55f70-192">チェックする権限の種類を表す整数値。</span><span class="sxs-lookup"><span data-stu-id="55f70-192">Integer value representing the type of permissions checked.</span></span><br /><br /> <span data-ttu-id="55f70-193">1 = SELECT ALL</span><span class="sxs-lookup"><span data-stu-id="55f70-193">1 = SELECT ALL</span></span><br /><br /> <span data-ttu-id="55f70-194">2 = UPDATE ALL</span><span class="sxs-lookup"><span data-stu-id="55f70-194">2 = UPDATE ALL</span></span><br /><br /> <span data-ttu-id="55f70-195">4 = REFERENCES ALL</span><span class="sxs-lookup"><span data-stu-id="55f70-195">4 = REFERENCES ALL</span></span><br /><br /> <span data-ttu-id="55f70-196">8 = INSERT</span><span class="sxs-lookup"><span data-stu-id="55f70-196">8 = INSERT</span></span><br /><br /> <span data-ttu-id="55f70-197">16 = DELETE</span><span class="sxs-lookup"><span data-stu-id="55f70-197">16 = DELETE</span></span><br /><br /> <span data-ttu-id="55f70-198">32 = EXECUTE (プロシージャのみ)</span><span class="sxs-lookup"><span data-stu-id="55f70-198">32 = EXECUTE (procedures only)</span></span>|<span data-ttu-id="55f70-199">19</span><span class="sxs-lookup"><span data-stu-id="55f70-199">19</span></span>|<span data-ttu-id="55f70-200">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-200">Yes</span></span>|  
|<span data-ttu-id="55f70-201">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="55f70-201">**RequestID**</span></span>|<span data-ttu-id="55f70-202">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-202">**int**</span></span>|<span data-ttu-id="55f70-203">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="55f70-203">ID of the request containing the statement.</span></span>|<span data-ttu-id="55f70-204">49</span><span class="sxs-lookup"><span data-stu-id="55f70-204">49</span></span>|<span data-ttu-id="55f70-205">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-205">Yes</span></span>|  
|<span data-ttu-id="55f70-206">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="55f70-206">**ServerName**</span></span>|<span data-ttu-id="55f70-207">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-207">**nvarchar**</span></span>|<span data-ttu-id="55f70-208">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="55f70-208">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="55f70-209">26</span><span class="sxs-lookup"><span data-stu-id="55f70-209">26</span></span>|<span data-ttu-id="55f70-210">いいえ</span><span class="sxs-lookup"><span data-stu-id="55f70-210">No</span></span>|  
|<span data-ttu-id="55f70-211">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="55f70-211">**SessionLoginName**</span></span>|<span data-ttu-id="55f70-212">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="55f70-212">**nvarchar**</span></span>|<span data-ttu-id="55f70-213">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="55f70-213">The login name of the user who originated the session.</span></span> <span data-ttu-id="55f70-214">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55f70-214">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="55f70-215">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55f70-215">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="55f70-216">64</span><span class="sxs-lookup"><span data-stu-id="55f70-216">64</span></span>|<span data-ttu-id="55f70-217">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-217">Yes</span></span>|  
|<span data-ttu-id="55f70-218">**SPID**</span><span class="sxs-lookup"><span data-stu-id="55f70-218">**SPID**</span></span>|<span data-ttu-id="55f70-219">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-219">**int**</span></span>|<span data-ttu-id="55f70-220">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="55f70-220">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="55f70-221">12</span><span class="sxs-lookup"><span data-stu-id="55f70-221">12</span></span>|<span data-ttu-id="55f70-222">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-222">Yes</span></span>|  
|<span data-ttu-id="55f70-223">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="55f70-223">**StartTime**</span></span>|<span data-ttu-id="55f70-224">**datetime**</span><span class="sxs-lookup"><span data-stu-id="55f70-224">**datetime**</span></span>|<span data-ttu-id="55f70-225">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="55f70-225">Time at which the event started, if available.</span></span>|<span data-ttu-id="55f70-226">14</span><span class="sxs-lookup"><span data-stu-id="55f70-226">14</span></span>|<span data-ttu-id="55f70-227">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-227">Yes</span></span>|  
|<span data-ttu-id="55f70-228">**Success**</span><span class="sxs-lookup"><span data-stu-id="55f70-228">**Success**</span></span>|<span data-ttu-id="55f70-229">**int**</span><span class="sxs-lookup"><span data-stu-id="55f70-229">**int**</span></span>|<span data-ttu-id="55f70-230">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="55f70-230">1 = success.</span></span> <span data-ttu-id="55f70-231">0 = 失敗。</span><span class="sxs-lookup"><span data-stu-id="55f70-231">0 = failure.</span></span> <span data-ttu-id="55f70-232">たとえば、値 1 は権限チェックの成功を示し、値 0 は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="55f70-232">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="55f70-233">23</span><span class="sxs-lookup"><span data-stu-id="55f70-233">23</span></span>|<span data-ttu-id="55f70-234">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-234">Yes</span></span>|  
|<span data-ttu-id="55f70-235">**TextData**</span><span class="sxs-lookup"><span data-stu-id="55f70-235">**TextData**</span></span>|<span data-ttu-id="55f70-236">**ntext**</span><span class="sxs-lookup"><span data-stu-id="55f70-236">**ntext**</span></span>|<span data-ttu-id="55f70-237">トレースでキャプチャされたイベント クラスに依存するテキスト値。</span><span class="sxs-lookup"><span data-stu-id="55f70-237">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="55f70-238">1</span><span class="sxs-lookup"><span data-stu-id="55f70-238">1</span></span>|<span data-ttu-id="55f70-239">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-239">Yes</span></span>|  
|<span data-ttu-id="55f70-240">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="55f70-240">**TransactionID**</span></span>|<span data-ttu-id="55f70-241">**bigint**</span><span class="sxs-lookup"><span data-stu-id="55f70-241">**bigint**</span></span>|<span data-ttu-id="55f70-242">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="55f70-242">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="55f70-243">4</span><span class="sxs-lookup"><span data-stu-id="55f70-243">4</span></span>|<span data-ttu-id="55f70-244">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-244">Yes</span></span>|  
|<span data-ttu-id="55f70-245">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="55f70-245">**XactSequence**</span></span>|<span data-ttu-id="55f70-246">**bigint**</span><span class="sxs-lookup"><span data-stu-id="55f70-246">**bigint**</span></span>|<span data-ttu-id="55f70-247">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="55f70-247">Token used to describe the current transaction.</span></span>|<span data-ttu-id="55f70-248">50</span><span class="sxs-lookup"><span data-stu-id="55f70-248">50</span></span>|<span data-ttu-id="55f70-249">はい</span><span class="sxs-lookup"><span data-stu-id="55f70-249">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55f70-250">参照</span><span class="sxs-lookup"><span data-stu-id="55f70-250">See Also</span></span>  
 <span data-ttu-id="55f70-251">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="55f70-251">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="55f70-252">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="55f70-252">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  