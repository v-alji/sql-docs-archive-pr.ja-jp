---
title: Audit Server Operation イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Operation event class
ms.assetid: 6cc3dbb9-817e-4329-9f45-c3adcff3b511
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a3359de449dcce4a976dec2debd9b5be99addd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631049"
---
# <a name="audit-server-operation-event-class"></a><span data-ttu-id="e0db3-102">Audit Server Operation イベント クラス</span><span class="sxs-lookup"><span data-stu-id="e0db3-102">Audit Server Operation Event Class</span></span>
  <span data-ttu-id="e0db3-103">**Audit Server Operation** イベント クラスは、設定、リソース、外部アクセス、承認を変更するなど、セキュリティ監査の操作が使用されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="e0db3-103">The **Audit Server Operation** event class occurs when Security Audit operations such as altering settings, resources, external access, or authorization are used.</span></span>  
  
## <a name="audit-server-operation-event-class-data-columns"></a><span data-ttu-id="e0db3-104">Audit Server Operation イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="e0db3-104">Audit Server Operation Event Class Data Columns</span></span>  
  
|<span data-ttu-id="e0db3-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="e0db3-105">Data column name</span></span>|<span data-ttu-id="e0db3-106">データ型</span><span class="sxs-lookup"><span data-stu-id="e0db3-106">Data type</span></span>|<span data-ttu-id="e0db3-107">説明</span><span class="sxs-lookup"><span data-stu-id="e0db3-107">Description</span></span>|<span data-ttu-id="e0db3-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="e0db3-108">Column ID</span></span>|<span data-ttu-id="e0db3-109">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="e0db3-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="e0db3-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-110">**ApplicationName**</span></span>|<span data-ttu-id="e0db3-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-111">**nvarchar**</span></span>|<span data-ttu-id="e0db3-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="e0db3-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0db3-113">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e0db3-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="e0db3-114">10</span><span class="sxs-lookup"><span data-stu-id="e0db3-114">10</span></span>|<span data-ttu-id="e0db3-115">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-115">Yes</span></span>|  
|<span data-ttu-id="e0db3-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="e0db3-116">**DatabaseID**</span></span>|<span data-ttu-id="e0db3-117">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-117">**int**</span></span>|<span data-ttu-id="e0db3-118">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="e0db3-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="e0db3-119">では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0db3-119">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="e0db3-120">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="e0db3-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="e0db3-121">3</span><span class="sxs-lookup"><span data-stu-id="e0db3-121">3</span></span>|<span data-ttu-id="e0db3-122">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-122">Yes</span></span>|  
|<span data-ttu-id="e0db3-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-123">**DatabaseName**</span></span>|<span data-ttu-id="e0db3-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-124">**nvarchar**</span></span>|<span data-ttu-id="e0db3-125">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="e0db3-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="e0db3-126">35</span><span class="sxs-lookup"><span data-stu-id="e0db3-126">35</span></span>|<span data-ttu-id="e0db3-127">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-127">Yes</span></span>|  
|<span data-ttu-id="e0db3-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-128">**DBUserName**</span></span>|<span data-ttu-id="e0db3-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e0db3-130">ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="e0db3-130">user name of the client.</span></span>|<span data-ttu-id="e0db3-131">40</span><span class="sxs-lookup"><span data-stu-id="e0db3-131">40</span></span>|<span data-ttu-id="e0db3-132">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-132">Yes</span></span>|  
|<span data-ttu-id="e0db3-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="e0db3-133">**EventSequence**</span></span>|<span data-ttu-id="e0db3-134">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-134">**int**</span></span>|<span data-ttu-id="e0db3-135">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="e0db3-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="e0db3-136">51</span><span class="sxs-lookup"><span data-stu-id="e0db3-136">51</span></span>|<span data-ttu-id="e0db3-137">いいえ</span><span class="sxs-lookup"><span data-stu-id="e0db3-137">No</span></span>|  
|<span data-ttu-id="e0db3-138">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="e0db3-138">**EventSubClass**</span></span>|<span data-ttu-id="e0db3-139">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-139">**int**</span></span>|<span data-ttu-id="e0db3-140">イベント サブクラスの種類。</span><span class="sxs-lookup"><span data-stu-id="e0db3-140">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="e0db3-141">1 = 一括操作の管理</span><span class="sxs-lookup"><span data-stu-id="e0db3-141">1=Administer Bulk Operations</span></span><br /><br /> <span data-ttu-id="e0db3-142">2 = 設定の変更</span><span class="sxs-lookup"><span data-stu-id="e0db3-142">2=Alter Settings</span></span><br /><br /> <span data-ttu-id="e0db3-143">3 = リソースの変更</span><span class="sxs-lookup"><span data-stu-id="e0db3-143">3=Alter Resources</span></span><br /><br /> <span data-ttu-id="e0db3-144">4 = 認証</span><span class="sxs-lookup"><span data-stu-id="e0db3-144">4=Authenticate</span></span><br /><br /> <span data-ttu-id="e0db3-145">5 = 外部アクセス</span><span class="sxs-lookup"><span data-stu-id="e0db3-145">5=External Access</span></span><br /><br /> <span data-ttu-id="e0db3-146">6=サーバー状態の変更</span><span class="sxs-lookup"><span data-stu-id="e0db3-146">6=Alter Server State</span></span><br /><br /> <span data-ttu-id="e0db3-147">7=安全でないアセンブリ</span><span class="sxs-lookup"><span data-stu-id="e0db3-147">7=Unsafe Assembly</span></span><br /><br /> <span data-ttu-id="e0db3-148">8=	接続の変更</span><span class="sxs-lookup"><span data-stu-id="e0db3-148">8=Alter Connection</span></span><br /><br /> <span data-ttu-id="e0db3-149">9=リソース ガバナーの変更</span><span class="sxs-lookup"><span data-stu-id="e0db3-149">9=Alter Resource Governor</span></span><br /><br /> <span data-ttu-id="e0db3-150">10=任意のワークロード グループの使用</span><span class="sxs-lookup"><span data-stu-id="e0db3-150">10=Use Any Workload Group</span></span><br /><br /> <span data-ttu-id="e0db3-151">11=サーバー状態の表示</span><span class="sxs-lookup"><span data-stu-id="e0db3-151">11=View Server State</span></span>|<span data-ttu-id="e0db3-152">21</span><span class="sxs-lookup"><span data-stu-id="e0db3-152">21</span></span>|<span data-ttu-id="e0db3-153">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-153">Yes</span></span>|  
|<span data-ttu-id="e0db3-154">**HostName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-154">**HostName**</span></span>|<span data-ttu-id="e0db3-155">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-155">**nvarchar**</span></span>|<span data-ttu-id="e0db3-156">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="e0db3-156">Name of the computer on which the client is running.</span></span> <span data-ttu-id="e0db3-157">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e0db3-157">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="e0db3-158">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0db3-158">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="e0db3-159">8</span><span class="sxs-lookup"><span data-stu-id="e0db3-159">8</span></span>|<span data-ttu-id="e0db3-160">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-160">Yes</span></span>|  
|<span data-ttu-id="e0db3-161">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="e0db3-161">**IsSystem**</span></span>|<span data-ttu-id="e0db3-162">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-162">**int**</span></span>|<span data-ttu-id="e0db3-163">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="e0db3-163">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="e0db3-164">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="e0db3-164">1 = system, 0 = user.</span></span>|<span data-ttu-id="e0db3-165">60</span><span class="sxs-lookup"><span data-stu-id="e0db3-165">60</span></span>|<span data-ttu-id="e0db3-166">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-166">Yes</span></span>|  
|<span data-ttu-id="e0db3-167">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-167">**LoginName**</span></span>|<span data-ttu-id="e0db3-168">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-168">**nvarchar**</span></span>|<span data-ttu-id="e0db3-169">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログイン、または DOMAIN\username の形式で表された [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="e0db3-169">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="e0db3-170">11</span><span class="sxs-lookup"><span data-stu-id="e0db3-170">11</span></span>|<span data-ttu-id="e0db3-171">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-171">Yes</span></span>|  
|<span data-ttu-id="e0db3-172">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="e0db3-172">**LoginSid**</span></span>|<span data-ttu-id="e0db3-173">**画像**</span><span class="sxs-lookup"><span data-stu-id="e0db3-173">**image**</span></span>|<span data-ttu-id="e0db3-174">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="e0db3-174">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="e0db3-175">この情報は、 **sys.server_principals** カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="e0db3-175">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="e0db3-176">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="e0db3-176">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="e0db3-177">41</span><span class="sxs-lookup"><span data-stu-id="e0db3-177">41</span></span>|<span data-ttu-id="e0db3-178">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-178">Yes</span></span>|  
|<span data-ttu-id="e0db3-179">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-179">**NTDomainName**</span></span>|<span data-ttu-id="e0db3-180">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-180">**nvarchar**</span></span>|<span data-ttu-id="e0db3-181">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="e0db3-181">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="e0db3-182">7</span><span class="sxs-lookup"><span data-stu-id="e0db3-182">7</span></span>|<span data-ttu-id="e0db3-183">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-183">Yes</span></span>|  
|<span data-ttu-id="e0db3-184">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-184">**NTUserName**</span></span>|<span data-ttu-id="e0db3-185">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-185">**nvarchar**</span></span>|<span data-ttu-id="e0db3-186">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="e0db3-186">Windows user name.</span></span>|<span data-ttu-id="e0db3-187">6</span><span class="sxs-lookup"><span data-stu-id="e0db3-187">6</span></span>|<span data-ttu-id="e0db3-188">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-188">Yes</span></span>|  
|<span data-ttu-id="e0db3-189">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-189">**ObjectName**</span></span>|<span data-ttu-id="e0db3-190">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-190">**nvarchar**</span></span>|<span data-ttu-id="e0db3-191">参照されているオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="e0db3-191">Name of the object being referenced.</span></span>|<span data-ttu-id="e0db3-192">34</span><span class="sxs-lookup"><span data-stu-id="e0db3-192">34</span></span>|<span data-ttu-id="e0db3-193">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-193">Yes</span></span>|  
|<span data-ttu-id="e0db3-194">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="e0db3-194">**ObjectType**</span></span>|<span data-ttu-id="e0db3-195">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-195">**int**</span></span>|<span data-ttu-id="e0db3-196">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="e0db3-196">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="e0db3-197">この値は **sys.objects** カタログ ビューの type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="e0db3-197">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="e0db3-198">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0db3-198">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="e0db3-199">28</span><span class="sxs-lookup"><span data-stu-id="e0db3-199">28</span></span>|<span data-ttu-id="e0db3-200">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-200">Yes</span></span>|  
|<span data-ttu-id="e0db3-201">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-201">**OwnerName**</span></span>|<span data-ttu-id="e0db3-202">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-202">**nvarchar**</span></span>|<span data-ttu-id="e0db3-203">オブジェクト所有者のデータベース ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="e0db3-203">Database user name of the object owner.</span></span>|<span data-ttu-id="e0db3-204">37</span><span class="sxs-lookup"><span data-stu-id="e0db3-204">37</span></span>|<span data-ttu-id="e0db3-205">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-205">Yes</span></span>|  
|<span data-ttu-id="e0db3-206">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="e0db3-206">**RequestID**</span></span>|<span data-ttu-id="e0db3-207">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-207">**int**</span></span>|<span data-ttu-id="e0db3-208">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="e0db3-208">ID of the request containing the statement.</span></span>|<span data-ttu-id="e0db3-209">49</span><span class="sxs-lookup"><span data-stu-id="e0db3-209">49</span></span>|<span data-ttu-id="e0db3-210">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-210">Yes</span></span>|  
|<span data-ttu-id="e0db3-211">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-211">**ServerName**</span></span>|<span data-ttu-id="e0db3-212">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-212">**nvarchar**</span></span>|<span data-ttu-id="e0db3-213">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="e0db3-213">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="e0db3-214">26</span><span class="sxs-lookup"><span data-stu-id="e0db3-214">26</span></span>|<span data-ttu-id="e0db3-215">いいえ</span><span class="sxs-lookup"><span data-stu-id="e0db3-215">No</span></span>|  
|<span data-ttu-id="e0db3-216">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="e0db3-216">**SessionLoginName**</span></span>|<span data-ttu-id="e0db3-217">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e0db3-217">**nvarchar**</span></span>|<span data-ttu-id="e0db3-218">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="e0db3-218">Login name of the user who originated the session.</span></span> <span data-ttu-id="e0db3-219">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0db3-219">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="e0db3-220">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0db3-220">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="e0db3-221">64</span><span class="sxs-lookup"><span data-stu-id="e0db3-221">64</span></span>|<span data-ttu-id="e0db3-222">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-222">Yes</span></span>|  
|<span data-ttu-id="e0db3-223">**SPID**</span><span class="sxs-lookup"><span data-stu-id="e0db3-223">**SPID**</span></span>|<span data-ttu-id="e0db3-224">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-224">**int**</span></span>|<span data-ttu-id="e0db3-225">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="e0db3-225">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="e0db3-226">12</span><span class="sxs-lookup"><span data-stu-id="e0db3-226">12</span></span>|<span data-ttu-id="e0db3-227">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-227">Yes</span></span>|  
|<span data-ttu-id="e0db3-228">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="e0db3-228">**StartTime**</span></span>|<span data-ttu-id="e0db3-229">**datetime**</span><span class="sxs-lookup"><span data-stu-id="e0db3-229">**datetime**</span></span>|<span data-ttu-id="e0db3-230">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="e0db3-230">Time at which the event started, if available.</span></span>|<span data-ttu-id="e0db3-231">14</span><span class="sxs-lookup"><span data-stu-id="e0db3-231">14</span></span>|<span data-ttu-id="e0db3-232">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-232">Yes</span></span>|  
|<span data-ttu-id="e0db3-233">**Success**</span><span class="sxs-lookup"><span data-stu-id="e0db3-233">**Success**</span></span>|<span data-ttu-id="e0db3-234">**int**</span><span class="sxs-lookup"><span data-stu-id="e0db3-234">**int**</span></span>|<span data-ttu-id="e0db3-235">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="e0db3-235">1 = success.</span></span> <span data-ttu-id="e0db3-236">0 = 失敗。</span><span class="sxs-lookup"><span data-stu-id="e0db3-236">0 = failure.</span></span> <span data-ttu-id="e0db3-237">たとえば、値 1 は権限チェックの成功を示し、値 0 は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="e0db3-237">For example, a value of 1 means success of a permissions check and a value of 0 means a failure of that check.</span></span>|<span data-ttu-id="e0db3-238">23</span><span class="sxs-lookup"><span data-stu-id="e0db3-238">23</span></span>|<span data-ttu-id="e0db3-239">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-239">Yes</span></span>|  
|<span data-ttu-id="e0db3-240">**TextData**</span><span class="sxs-lookup"><span data-stu-id="e0db3-240">**TextData**</span></span>|<span data-ttu-id="e0db3-241">**ntext**</span><span class="sxs-lookup"><span data-stu-id="e0db3-241">**ntext**</span></span>|<span data-ttu-id="e0db3-242">トレースでキャプチャされたイベント クラスに依存するテキスト値。</span><span class="sxs-lookup"><span data-stu-id="e0db3-242">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="e0db3-243">1</span><span class="sxs-lookup"><span data-stu-id="e0db3-243">1</span></span>|<span data-ttu-id="e0db3-244">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-244">Yes</span></span>|  
|<span data-ttu-id="e0db3-245">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="e0db3-245">**TransactionID**</span></span>|<span data-ttu-id="e0db3-246">**bigint**</span><span class="sxs-lookup"><span data-stu-id="e0db3-246">**bigint**</span></span>|<span data-ttu-id="e0db3-247">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="e0db3-247">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="e0db3-248">4</span><span class="sxs-lookup"><span data-stu-id="e0db3-248">4</span></span>|<span data-ttu-id="e0db3-249">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-249">Yes</span></span>|  
|<span data-ttu-id="e0db3-250">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="e0db3-250">**XactSequence**</span></span>|<span data-ttu-id="e0db3-251">**bigint**</span><span class="sxs-lookup"><span data-stu-id="e0db3-251">**bigint**</span></span>|<span data-ttu-id="e0db3-252">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="e0db3-252">Token used to describe the current transaction.</span></span>|<span data-ttu-id="e0db3-253">50</span><span class="sxs-lookup"><span data-stu-id="e0db3-253">50</span></span>|<span data-ttu-id="e0db3-254">はい</span><span class="sxs-lookup"><span data-stu-id="e0db3-254">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0db3-255">参照</span><span class="sxs-lookup"><span data-stu-id="e0db3-255">See Also</span></span>  
 <span data-ttu-id="e0db3-256">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="e0db3-256">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="e0db3-257">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e0db3-257">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  