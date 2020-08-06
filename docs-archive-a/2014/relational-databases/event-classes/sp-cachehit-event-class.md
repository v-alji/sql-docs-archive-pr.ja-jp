---
title: SP:CacheHit イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SP:CacheHit event class
ms.assetid: 396aa22a-4723-47f5-ae72-7de99d92dd6f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ffc477b299daeda004cca26d95f3d33e2e5509b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631964"
---
# <a name="spcachehit-event-class"></a><span data-ttu-id="1895b-102">SP:CacheHit イベント クラス</span><span class="sxs-lookup"><span data-stu-id="1895b-102">SP:CacheHit Event Class</span></span>
  <span data-ttu-id="1895b-103">SP:CacheHit イベント クラスは、ストアド プロシージャがプラン キャッシュに格納されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1895b-103">The SP:CacheHit event class indicates that a stored procedure is in the plan cache.</span></span>  
  
## <a name="spcachehit-event-class-data-columns"></a><span data-ttu-id="1895b-104">SP:CacheHit イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="1895b-104">SP:CacheHit Event Class Data Columns</span></span>  
  
|<span data-ttu-id="1895b-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="1895b-105">Data column name</span></span>|`Data type`|<span data-ttu-id="1895b-106">説明</span><span class="sxs-lookup"><span data-stu-id="1895b-106">Description</span></span>|<span data-ttu-id="1895b-107">列 ID</span><span class="sxs-lookup"><span data-stu-id="1895b-107">Column ID</span></span>|<span data-ttu-id="1895b-108">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="1895b-108">Filterable</span></span>|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|<span data-ttu-id="1895b-109">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="1895b-109">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="1895b-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="1895b-110">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1895b-111">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1895b-111">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="1895b-112">10</span><span class="sxs-lookup"><span data-stu-id="1895b-112">10</span></span>|<span data-ttu-id="1895b-113">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-113">Yes</span></span>|  
|<span data-ttu-id="1895b-114">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="1895b-114">ClientProcessID</span></span>|`int`|<span data-ttu-id="1895b-115">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-115">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="1895b-116">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1895b-116">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="1895b-117">9</span><span class="sxs-lookup"><span data-stu-id="1895b-117">9</span></span>|<span data-ttu-id="1895b-118">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-118">Yes</span></span>|  
|<span data-ttu-id="1895b-119">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="1895b-119">DatabaseID</span></span>|`int`|<span data-ttu-id="1895b-120">ストアド プロシージャが実行されているデータベースの ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-120">ID of the database in which the stored procedure is running.</span></span> <span data-ttu-id="1895b-121">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="1895b-121">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="1895b-122">3</span><span class="sxs-lookup"><span data-stu-id="1895b-122">3</span></span>|<span data-ttu-id="1895b-123">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-123">Yes</span></span>|  
|<span data-ttu-id="1895b-124">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="1895b-124">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="1895b-125">ストアド プロシージャが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="1895b-125">Name of the database in which the stored procedure is running.</span></span>|<span data-ttu-id="1895b-126">35</span><span class="sxs-lookup"><span data-stu-id="1895b-126">35</span></span>|<span data-ttu-id="1895b-127">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-127">Yes</span></span>|  
|<span data-ttu-id="1895b-128">EventClass</span><span class="sxs-lookup"><span data-stu-id="1895b-128">EventClass</span></span>|`int`|<span data-ttu-id="1895b-129">イベントの種類 = 38。</span><span class="sxs-lookup"><span data-stu-id="1895b-129">Type of event = 38.</span></span>|<span data-ttu-id="1895b-130">27</span><span class="sxs-lookup"><span data-stu-id="1895b-130">27</span></span>|<span data-ttu-id="1895b-131">いいえ</span><span class="sxs-lookup"><span data-stu-id="1895b-131">No</span></span>|  
|<span data-ttu-id="1895b-132">EventSequence</span><span class="sxs-lookup"><span data-stu-id="1895b-132">EventSequence</span></span>|`int`|<span data-ttu-id="1895b-133">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="1895b-133">The sequence of a given event within the request.</span></span>|<span data-ttu-id="1895b-134">51</span><span class="sxs-lookup"><span data-stu-id="1895b-134">51</span></span>|<span data-ttu-id="1895b-135">いいえ</span><span class="sxs-lookup"><span data-stu-id="1895b-135">No</span></span>|  
|<span data-ttu-id="1895b-136">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="1895b-136">EventSubClass</span></span>|`int`|<span data-ttu-id="1895b-137">イベントサブクラスの種類。</span><span class="sxs-lookup"><span data-stu-id="1895b-137">Types of event subclass.</span></span><br /><br /> <span data-ttu-id="1895b-138">1 = 実行コンテキスト ヒット: プラン キャッシュ内にフリー実行プランが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="1895b-138">1=Execution Context Hit: A free execution plan was found in the plan cache.</span></span><br /><br /> <span data-ttu-id="1895b-139">2 = コンパイル済みプラン ヒット: プラン キャッシュ内にコンパイル済みプランが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="1895b-139">2=Compplan Hit: A compiled plan was found in the plan cache.</span></span>|<span data-ttu-id="1895b-140">21</span><span class="sxs-lookup"><span data-stu-id="1895b-140">21</span></span>|<span data-ttu-id="1895b-141">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-141">Yes</span></span>|  
|<span data-ttu-id="1895b-142">GroupID</span><span class="sxs-lookup"><span data-stu-id="1895b-142">GroupID</span></span>|`int`|<span data-ttu-id="1895b-143">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-143">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="1895b-144">66</span><span class="sxs-lookup"><span data-stu-id="1895b-144">66</span></span>|<span data-ttu-id="1895b-145">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-145">Yes</span></span>|  
|<span data-ttu-id="1895b-146">HostName</span><span class="sxs-lookup"><span data-stu-id="1895b-146">HostName</span></span>|`nvarchar`|<span data-ttu-id="1895b-147">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="1895b-147">Name of the computer on which the client is running.</span></span> <span data-ttu-id="1895b-148">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1895b-148">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="1895b-149">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="1895b-149">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="1895b-150">8</span><span class="sxs-lookup"><span data-stu-id="1895b-150">8</span></span>|<span data-ttu-id="1895b-151">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-151">Yes</span></span>|  
|<span data-ttu-id="1895b-152">IsSystem</span><span class="sxs-lookup"><span data-stu-id="1895b-152">IsSystem</span></span>|`int`|<span data-ttu-id="1895b-153">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="1895b-153">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="1895b-154">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="1895b-154">1 = system, 0 = user.</span></span>|<span data-ttu-id="1895b-155">60</span><span class="sxs-lookup"><span data-stu-id="1895b-155">60</span></span>|<span data-ttu-id="1895b-156">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-156">Yes</span></span>|  
|<span data-ttu-id="1895b-157">LoginName</span><span class="sxs-lookup"><span data-stu-id="1895b-157">LoginName</span></span>|`nvarchar`|<span data-ttu-id="1895b-158">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="1895b-158">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="1895b-159">11</span><span class="sxs-lookup"><span data-stu-id="1895b-159">11</span></span>|<span data-ttu-id="1895b-160">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-160">Yes</span></span>|  
|<span data-ttu-id="1895b-161">LoginSid</span><span class="sxs-lookup"><span data-stu-id="1895b-161">LoginSid</span></span>|`image`|<span data-ttu-id="1895b-162">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="1895b-162">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="1895b-163">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="1895b-163">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="1895b-164">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="1895b-164">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="1895b-165">41</span><span class="sxs-lookup"><span data-stu-id="1895b-165">41</span></span>|<span data-ttu-id="1895b-166">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-166">Yes</span></span>|  
|<span data-ttu-id="1895b-167">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="1895b-167">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="1895b-168">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="1895b-168">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="1895b-169">7</span><span class="sxs-lookup"><span data-stu-id="1895b-169">7</span></span>|<span data-ttu-id="1895b-170">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-170">Yes</span></span>|  
|<span data-ttu-id="1895b-171">NTUserName</span><span class="sxs-lookup"><span data-stu-id="1895b-171">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="1895b-172">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="1895b-172">Windows user name.</span></span>|<span data-ttu-id="1895b-173">6</span><span class="sxs-lookup"><span data-stu-id="1895b-173">6</span></span>|<span data-ttu-id="1895b-174">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-174">Yes</span></span>|  
|<span data-ttu-id="1895b-175">ObjectID</span><span class="sxs-lookup"><span data-stu-id="1895b-175">ObjectID</span></span>|`int`|<span data-ttu-id="1895b-176">システムによって割り当てられた、キャッシュ内のストアド プロシージャの ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-176">System-assigned ID of the stored procedure found in the cache.</span></span>|<span data-ttu-id="1895b-177">22</span><span class="sxs-lookup"><span data-stu-id="1895b-177">22</span></span>|<span data-ttu-id="1895b-178">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-178">Yes</span></span>|  
|<span data-ttu-id="1895b-179">ObjectName</span><span class="sxs-lookup"><span data-stu-id="1895b-179">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="1895b-180">キャッシュ内のオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="1895b-180">Name of the object that was found in the cache.</span></span> <span data-ttu-id="1895b-181">ObjectName に値が設定されている場合、TextData に値は設定されません。</span><span class="sxs-lookup"><span data-stu-id="1895b-181">If ObjectName is populated, TextData will not be populated.</span></span>|<span data-ttu-id="1895b-182">34</span><span class="sxs-lookup"><span data-stu-id="1895b-182">34</span></span>|<span data-ttu-id="1895b-183">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-183">Yes</span></span>|  
|<span data-ttu-id="1895b-184">ObjectType</span><span class="sxs-lookup"><span data-stu-id="1895b-184">ObjectType</span></span>|`int`|<span data-ttu-id="1895b-185">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="1895b-185">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="1895b-186">この値は sys.objects カタログ ビューの type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="1895b-186">This value corresponds to the type column in the sys.objects catalog view.</span></span> <span data-ttu-id="1895b-187">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1895b-187">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="1895b-188">28</span><span class="sxs-lookup"><span data-stu-id="1895b-188">28</span></span>|<span data-ttu-id="1895b-189">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-189">Yes</span></span>|  
|<span data-ttu-id="1895b-190">RequestID</span><span class="sxs-lookup"><span data-stu-id="1895b-190">RequestID</span></span>|`int`|<span data-ttu-id="1895b-191">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-191">ID of the request containing the statement.</span></span>|<span data-ttu-id="1895b-192">49</span><span class="sxs-lookup"><span data-stu-id="1895b-192">49</span></span>|<span data-ttu-id="1895b-193">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-193">Yes</span></span>|  
|<span data-ttu-id="1895b-194">ServerName</span><span class="sxs-lookup"><span data-stu-id="1895b-194">ServerName</span></span>|`nvarchar`|<span data-ttu-id="1895b-195">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="1895b-195">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="1895b-196">26</span><span class="sxs-lookup"><span data-stu-id="1895b-196">26</span></span>|<span data-ttu-id="1895b-197">いいえ</span><span class="sxs-lookup"><span data-stu-id="1895b-197">No</span></span>|  
|<span data-ttu-id="1895b-198">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="1895b-198">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="1895b-199">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="1895b-199">Login name of the user who originated the session.</span></span> <span data-ttu-id="1895b-200">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1895b-200">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="1895b-201">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1895b-201">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="1895b-202">64</span><span class="sxs-lookup"><span data-stu-id="1895b-202">64</span></span>|<span data-ttu-id="1895b-203">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-203">Yes</span></span>|  
|<span data-ttu-id="1895b-204">SPID</span><span class="sxs-lookup"><span data-stu-id="1895b-204">SPID</span></span>|`int`|<span data-ttu-id="1895b-205">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-205">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="1895b-206">12</span><span class="sxs-lookup"><span data-stu-id="1895b-206">12</span></span>|<span data-ttu-id="1895b-207">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-207">Yes</span></span>|  
|<span data-ttu-id="1895b-208">StartTime</span><span class="sxs-lookup"><span data-stu-id="1895b-208">StartTime</span></span>|`datetime`|<span data-ttu-id="1895b-209">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="1895b-209">Time at which the event started, if available.</span></span>|<span data-ttu-id="1895b-210">14</span><span class="sxs-lookup"><span data-stu-id="1895b-210">14</span></span>|<span data-ttu-id="1895b-211">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-211">Yes</span></span>|  
|<span data-ttu-id="1895b-212">TextData</span><span class="sxs-lookup"><span data-stu-id="1895b-212">TextData</span></span>|`ntext`|<span data-ttu-id="1895b-213">キャッシュ内の SQL コードのテキスト。</span><span class="sxs-lookup"><span data-stu-id="1895b-213">Text of the SQL code that was found in the cache.</span></span> <span data-ttu-id="1895b-214">TextData に値が設定されている場合、ObjectName に値は設定されません。</span><span class="sxs-lookup"><span data-stu-id="1895b-214">If TextData is populated, ObjectName will not be populated.</span></span>|<span data-ttu-id="1895b-215">1</span><span class="sxs-lookup"><span data-stu-id="1895b-215">1</span></span>|<span data-ttu-id="1895b-216">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-216">Yes</span></span>|  
|<span data-ttu-id="1895b-217">TransactionID</span><span class="sxs-lookup"><span data-stu-id="1895b-217">TransactionID</span></span>|`bigint`|<span data-ttu-id="1895b-218">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="1895b-218">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="1895b-219">4</span><span class="sxs-lookup"><span data-stu-id="1895b-219">4</span></span>|<span data-ttu-id="1895b-220">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-220">Yes</span></span>|  
|<span data-ttu-id="1895b-221">XactSequence</span><span class="sxs-lookup"><span data-stu-id="1895b-221">XactSequence</span></span>|`bigint`|<span data-ttu-id="1895b-222">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="1895b-222">Token that describes the current transaction.</span></span>|<span data-ttu-id="1895b-223">50</span><span class="sxs-lookup"><span data-stu-id="1895b-223">50</span></span>|<span data-ttu-id="1895b-224">はい</span><span class="sxs-lookup"><span data-stu-id="1895b-224">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1895b-225">参照</span><span class="sxs-lookup"><span data-stu-id="1895b-225">See Also</span></span>  
 [<span data-ttu-id="1895b-226">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1895b-226">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  