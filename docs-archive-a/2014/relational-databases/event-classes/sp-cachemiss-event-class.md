---
title: SP:CacheMiss イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SP:CacheMiss event class
ms.assetid: 82229233-f772-4558-95a0-d54584d1b1ae
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91df12e64c24bb3e21bb69e73f5ac1741f18ba0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631948"
---
# <a name="spcachemiss-event-class"></a><span data-ttu-id="c5b27-102">SP:CacheMiss イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c5b27-102">SP:CacheMiss Event Class</span></span>
  <span data-ttu-id="c5b27-103">SP:CacheMiss イベント クラスは、プロシージャをキャッシュ内で検出できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="c5b27-103">The SP:CacheMiss event class indicates that the procedure is not found in the cache.</span></span> <span data-ttu-id="c5b27-104">SP:CacheMiss イベント クラスが頻繁に発生する場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やす必要があることを示している可能性があります。それによって、プロシージャ キャッシュのサイズが増えます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-104">If the SP:CacheMiss event class occurs frequently, it can indicate that more memory should be made available to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], thereby increasing the size of the procedure cache.</span></span>  
  
## <a name="spcachemiss-event-class-data-columns"></a><span data-ttu-id="c5b27-105">SP:CacheMiss イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="c5b27-105">SP:CacheMiss Event Class Data Columns</span></span>  
  
|<span data-ttu-id="c5b27-106">データ列名</span><span class="sxs-lookup"><span data-stu-id="c5b27-106">Data column name</span></span>|<span data-ttu-id="c5b27-107">データ型</span><span class="sxs-lookup"><span data-stu-id="c5b27-107">Data type</span></span>|<span data-ttu-id="c5b27-108">説明</span><span class="sxs-lookup"><span data-stu-id="c5b27-108">Description</span></span>|<span data-ttu-id="c5b27-109">列 ID</span><span class="sxs-lookup"><span data-stu-id="c5b27-109">Column ID</span></span>|<span data-ttu-id="c5b27-110">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="c5b27-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="c5b27-111">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="c5b27-111">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="c5b27-112">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5b27-113">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="c5b27-114">10</span><span class="sxs-lookup"><span data-stu-id="c5b27-114">10</span></span>|<span data-ttu-id="c5b27-115">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-115">Yes</span></span>|  
|<span data-ttu-id="c5b27-116">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="c5b27-116">ClientProcessID</span></span>|`int`|<span data-ttu-id="c5b27-117">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-117">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="c5b27-118">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-118">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="c5b27-119">9</span><span class="sxs-lookup"><span data-stu-id="c5b27-119">9</span></span>|<span data-ttu-id="c5b27-120">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-120">Yes</span></span>|  
|<span data-ttu-id="c5b27-121">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="c5b27-121">DatabaseID</span></span>|`int`|<span data-ttu-id="c5b27-122">ストアド プロシージャが実行されているデータベースの ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-122">ID of the database in which the stored procedure is running.</span></span> <span data-ttu-id="c5b27-123">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="c5b27-123">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="c5b27-124">3</span><span class="sxs-lookup"><span data-stu-id="c5b27-124">3</span></span>|<span data-ttu-id="c5b27-125">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-125">Yes</span></span>|  
|<span data-ttu-id="c5b27-126">EventClass</span><span class="sxs-lookup"><span data-stu-id="c5b27-126">EventClass</span></span>|`int`|<span data-ttu-id="c5b27-127">イベントの種類 = 34。</span><span class="sxs-lookup"><span data-stu-id="c5b27-127">Type of event = 34.</span></span>|<span data-ttu-id="c5b27-128">27</span><span class="sxs-lookup"><span data-stu-id="c5b27-128">27</span></span>|<span data-ttu-id="c5b27-129">いいえ</span><span class="sxs-lookup"><span data-stu-id="c5b27-129">No</span></span>|  
|<span data-ttu-id="c5b27-130">EventSequence</span><span class="sxs-lookup"><span data-stu-id="c5b27-130">EventSequence</span></span>|`int`|<span data-ttu-id="c5b27-131">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="c5b27-131">Sequence of a given event within the request.</span></span>|<span data-ttu-id="c5b27-132">51</span><span class="sxs-lookup"><span data-stu-id="c5b27-132">51</span></span>|<span data-ttu-id="c5b27-133">いいえ</span><span class="sxs-lookup"><span data-stu-id="c5b27-133">No</span></span>|  
|<span data-ttu-id="c5b27-134">GroupID</span><span class="sxs-lookup"><span data-stu-id="c5b27-134">GroupID</span></span>|`int`|<span data-ttu-id="c5b27-135">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-135">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="c5b27-136">66</span><span class="sxs-lookup"><span data-stu-id="c5b27-136">66</span></span>|<span data-ttu-id="c5b27-137">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-137">Yes</span></span>|  
|<span data-ttu-id="c5b27-138">HostName</span><span class="sxs-lookup"><span data-stu-id="c5b27-138">HostName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-139">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="c5b27-139">Name of the computer on which the client is running.</span></span> <span data-ttu-id="c5b27-140">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-140">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="c5b27-141">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5b27-141">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="c5b27-142">8</span><span class="sxs-lookup"><span data-stu-id="c5b27-142">8</span></span>|<span data-ttu-id="c5b27-143">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-143">Yes</span></span>|  
|<span data-ttu-id="c5b27-144">IsSystem</span><span class="sxs-lookup"><span data-stu-id="c5b27-144">IsSystem</span></span>|`int`|<span data-ttu-id="c5b27-145">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="c5b27-145">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="c5b27-146">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="c5b27-146">1 = system, 0 = user.</span></span>|<span data-ttu-id="c5b27-147">60</span><span class="sxs-lookup"><span data-stu-id="c5b27-147">60</span></span>|<span data-ttu-id="c5b27-148">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-148">Yes</span></span>|  
|<span data-ttu-id="c5b27-149">LoginName</span><span class="sxs-lookup"><span data-stu-id="c5b27-149">LoginName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-150">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="c5b27-150">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="c5b27-151">11</span><span class="sxs-lookup"><span data-stu-id="c5b27-151">11</span></span>|<span data-ttu-id="c5b27-152">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-152">Yes</span></span>|  
|<span data-ttu-id="c5b27-153">LoginSid</span><span class="sxs-lookup"><span data-stu-id="c5b27-153">LoginSid</span></span>|`image`|<span data-ttu-id="c5b27-154">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="c5b27-154">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="c5b27-155">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-155">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="c5b27-156">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="c5b27-156">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="c5b27-157">41</span><span class="sxs-lookup"><span data-stu-id="c5b27-157">41</span></span>|<span data-ttu-id="c5b27-158">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-158">Yes</span></span>|  
|<span data-ttu-id="c5b27-159">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="c5b27-159">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-160">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="c5b27-160">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="c5b27-161">7</span><span class="sxs-lookup"><span data-stu-id="c5b27-161">7</span></span>|<span data-ttu-id="c5b27-162">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-162">Yes</span></span>|  
|<span data-ttu-id="c5b27-163">NTUserName</span><span class="sxs-lookup"><span data-stu-id="c5b27-163">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-164">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="c5b27-164">Windows user name.</span></span>|<span data-ttu-id="c5b27-165">6</span><span class="sxs-lookup"><span data-stu-id="c5b27-165">6</span></span>|<span data-ttu-id="c5b27-166">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-166">Yes</span></span>|  
|<span data-ttu-id="c5b27-167">ObjectID</span><span class="sxs-lookup"><span data-stu-id="c5b27-167">ObjectID</span></span>|`int`|<span data-ttu-id="c5b27-168">システムによって割り当てられたオブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-168">System-assigned ID of the object.</span></span>|<span data-ttu-id="c5b27-169">22</span><span class="sxs-lookup"><span data-stu-id="c5b27-169">22</span></span>|<span data-ttu-id="c5b27-170">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-170">Yes</span></span>|  
|<span data-ttu-id="c5b27-171">ObjectName</span><span class="sxs-lookup"><span data-stu-id="c5b27-171">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-172">ストアド プロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="c5b27-172">Name of the stored procedure.</span></span> <span data-ttu-id="c5b27-173">ObjectName に値が設定された場合、TextData には値が設定されません。</span><span class="sxs-lookup"><span data-stu-id="c5b27-173">If ObjectName is populated, then TextData will not be populated.</span></span>|<span data-ttu-id="c5b27-174">34</span><span class="sxs-lookup"><span data-stu-id="c5b27-174">34</span></span>|<span data-ttu-id="c5b27-175">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-175">Yes</span></span>|  
|<span data-ttu-id="c5b27-176">ObjectType</span><span class="sxs-lookup"><span data-stu-id="c5b27-176">ObjectType</span></span>|`int`|<span data-ttu-id="c5b27-177">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="c5b27-177">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="c5b27-178">この値は sys.objects カタログ ビューの type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="c5b27-178">This value corresponds to the type column in the sys.objects catalog view.</span></span> <span data-ttu-id="c5b27-179">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5b27-179">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="c5b27-180">28</span><span class="sxs-lookup"><span data-stu-id="c5b27-180">28</span></span>|<span data-ttu-id="c5b27-181">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-181">Yes</span></span>|  
|<span data-ttu-id="c5b27-182">RequestID</span><span class="sxs-lookup"><span data-stu-id="c5b27-182">RequestID</span></span>|`int`|<span data-ttu-id="c5b27-183">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-183">ID of the request containing the statement.</span></span>|<span data-ttu-id="c5b27-184">49</span><span class="sxs-lookup"><span data-stu-id="c5b27-184">49</span></span>|<span data-ttu-id="c5b27-185">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-185">Yes</span></span>|  
|<span data-ttu-id="c5b27-186">ServerName</span><span class="sxs-lookup"><span data-stu-id="c5b27-186">ServerName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-187">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="c5b27-187">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="c5b27-188">26</span><span class="sxs-lookup"><span data-stu-id="c5b27-188">26</span></span>|<span data-ttu-id="c5b27-189">いいえ</span><span class="sxs-lookup"><span data-stu-id="c5b27-189">No</span></span>|  
|<span data-ttu-id="c5b27-190">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="c5b27-190">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="c5b27-191">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="c5b27-191">Login name of the user who originated the session.</span></span> <span data-ttu-id="c5b27-192">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-192">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="c5b27-193">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5b27-193">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="c5b27-194">64</span><span class="sxs-lookup"><span data-stu-id="c5b27-194">64</span></span>|<span data-ttu-id="c5b27-195">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-195">Yes</span></span>|  
|<span data-ttu-id="c5b27-196">SPID</span><span class="sxs-lookup"><span data-stu-id="c5b27-196">SPID</span></span>|`int`|<span data-ttu-id="c5b27-197">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-197">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="c5b27-198">12</span><span class="sxs-lookup"><span data-stu-id="c5b27-198">12</span></span>|<span data-ttu-id="c5b27-199">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-199">Yes</span></span>|  
|<span data-ttu-id="c5b27-200">StartTime</span><span class="sxs-lookup"><span data-stu-id="c5b27-200">StartTime</span></span>|`datetime`|<span data-ttu-id="c5b27-201">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="c5b27-201">Time at which the event started, if available.</span></span>|<span data-ttu-id="c5b27-202">14</span><span class="sxs-lookup"><span data-stu-id="c5b27-202">14</span></span>|<span data-ttu-id="c5b27-203">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-203">Yes</span></span>|  
|<span data-ttu-id="c5b27-204">TextData</span><span class="sxs-lookup"><span data-stu-id="c5b27-204">TextData</span></span>|`ntext`|<span data-ttu-id="c5b27-205">キャッシュされている SQL コードのテキスト。</span><span class="sxs-lookup"><span data-stu-id="c5b27-205">Text of the SQL code that is being cached.</span></span> <span data-ttu-id="c5b27-206">TextData に値が設定された場合、ObjectName には値が設定されません。</span><span class="sxs-lookup"><span data-stu-id="c5b27-206">If TextData is populated, ObjectName is not populated.</span></span>|<span data-ttu-id="c5b27-207">1</span><span class="sxs-lookup"><span data-stu-id="c5b27-207">1</span></span>|<span data-ttu-id="c5b27-208">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-208">Yes</span></span>|  
|<span data-ttu-id="c5b27-209">TransactionID</span><span class="sxs-lookup"><span data-stu-id="c5b27-209">TransactionID</span></span>|`bigint`|<span data-ttu-id="c5b27-210">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="c5b27-210">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="c5b27-211">4</span><span class="sxs-lookup"><span data-stu-id="c5b27-211">4</span></span>|<span data-ttu-id="c5b27-212">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-212">Yes</span></span>|  
|<span data-ttu-id="c5b27-213">XactSequence</span><span class="sxs-lookup"><span data-stu-id="c5b27-213">XactSequence</span></span>|`bigint`|<span data-ttu-id="c5b27-214">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="c5b27-214">Token that describes the current transaction.</span></span>|<span data-ttu-id="c5b27-215">50</span><span class="sxs-lookup"><span data-stu-id="c5b27-215">50</span></span>|<span data-ttu-id="c5b27-216">はい</span><span class="sxs-lookup"><span data-stu-id="c5b27-216">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5b27-217">参照</span><span class="sxs-lookup"><span data-stu-id="c5b27-217">See Also</span></span>  
 <span data-ttu-id="c5b27-218">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="c5b27-218">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="c5b27-219">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5b27-219">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="c5b27-220">SP:CacheInsert イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c5b27-220">SP:CacheInsert Event Class</span></span>](sp-cacheinsert-event-class.md)  
  
  