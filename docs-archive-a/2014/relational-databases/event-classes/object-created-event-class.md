---
title: Object:Created イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Object:Created event class
ms.assetid: 57536924-5e66-4b09-a76d-8fcea2131771
author: stevestein
ms.author: sstein
ms.openlocfilehash: e82f9d68a5b796c6152531437265a665a9b85a68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633870"
---
# <a name="objectcreated-event-class"></a><span data-ttu-id="32202-102">Object:Created イベント クラス</span><span class="sxs-lookup"><span data-stu-id="32202-102">Object:Created Event Class</span></span>
  <span data-ttu-id="32202-103">Object:Created イベント クラスは、CREATE INDEX、CREATE TABLE、CREATE DATABASE などのステートメントによって、オブジェクトが作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="32202-103">The Object:Created event class indicates that an object has been created, for example, by the CREATE INDEX, CREATE TABLE, or CREATE DATABASE statements.</span></span>  
  
 <span data-ttu-id="32202-104">このイベント クラスは、たとえば、頻繁に一時ストアド プロシージャを作成する ODBC アプリケーションによって、オブジェクトが作成されているかどうかを判断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="32202-104">This event class can be used to determine if objects are being created, for example, by ODBC applications that often create temporary stored procedures.</span></span> <span data-ttu-id="32202-105">LoginName データ列と NTUserName データ列を監視することで、オブジェクトを作成、削除、またはアクセスしたユーザーの名前を特定できます。</span><span class="sxs-lookup"><span data-stu-id="32202-105">By monitoring the LoginName and NTUserName data columns, you can determine the name of the user who is creating, deleting, or accessing objects.</span></span>  
  
## <a name="objectcreated-event-class-data-columns"></a><span data-ttu-id="32202-106">Object:Created イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="32202-106">Object:Created Event Class Data Columns</span></span>  
  
|<span data-ttu-id="32202-107">データ列名</span><span class="sxs-lookup"><span data-stu-id="32202-107">Data column name</span></span>|<span data-ttu-id="32202-108">データ型</span><span class="sxs-lookup"><span data-stu-id="32202-108">Data type</span></span>|<span data-ttu-id="32202-109">説明</span><span class="sxs-lookup"><span data-stu-id="32202-109">Description</span></span>|<span data-ttu-id="32202-110">列 ID</span><span class="sxs-lookup"><span data-stu-id="32202-110">Column ID</span></span>|<span data-ttu-id="32202-111">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="32202-111">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="32202-112">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="32202-112">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="32202-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="32202-113">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="32202-114">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="32202-114">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="32202-115">10</span><span class="sxs-lookup"><span data-stu-id="32202-115">10</span></span>|<span data-ttu-id="32202-116">はい</span><span class="sxs-lookup"><span data-stu-id="32202-116">Yes</span></span>|  
|<span data-ttu-id="32202-117">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="32202-117">ClientProcessID</span></span>|`int`|<span data-ttu-id="32202-118">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="32202-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="32202-119">クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="32202-119">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="32202-120">9</span><span class="sxs-lookup"><span data-stu-id="32202-120">9</span></span>|<span data-ttu-id="32202-121">はい</span><span class="sxs-lookup"><span data-stu-id="32202-121">Yes</span></span>|  
|<span data-ttu-id="32202-122">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="32202-122">DatabaseID</span></span>|`int`|<span data-ttu-id="32202-123">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="32202-123">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="32202-124">では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="32202-124">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="32202-125">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="32202-125">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="32202-126">3</span><span class="sxs-lookup"><span data-stu-id="32202-126">3</span></span>|<span data-ttu-id="32202-127">はい</span><span class="sxs-lookup"><span data-stu-id="32202-127">Yes</span></span>|  
|<span data-ttu-id="32202-128">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="32202-128">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="32202-129">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="32202-129">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="32202-130">35</span><span class="sxs-lookup"><span data-stu-id="32202-130">35</span></span>|<span data-ttu-id="32202-131">はい</span><span class="sxs-lookup"><span data-stu-id="32202-131">Yes</span></span>|  
|<span data-ttu-id="32202-132">EventClass</span><span class="sxs-lookup"><span data-stu-id="32202-132">EventClass</span></span>|`int`|<span data-ttu-id="32202-133">イベントの種類 = 46。</span><span class="sxs-lookup"><span data-stu-id="32202-133">Type of event = 46.</span></span>|<span data-ttu-id="32202-134">27</span><span class="sxs-lookup"><span data-stu-id="32202-134">27</span></span>|<span data-ttu-id="32202-135">いいえ</span><span class="sxs-lookup"><span data-stu-id="32202-135">No</span></span>|  
|<span data-ttu-id="32202-136">EventSequence</span><span class="sxs-lookup"><span data-stu-id="32202-136">EventSequence</span></span>|`int`|<span data-ttu-id="32202-137">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="32202-137">The sequence of a given event within the request.</span></span>|<span data-ttu-id="32202-138">51</span><span class="sxs-lookup"><span data-stu-id="32202-138">51</span></span>|<span data-ttu-id="32202-139">いいえ</span><span class="sxs-lookup"><span data-stu-id="32202-139">No</span></span>|  
|<span data-ttu-id="32202-140">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="32202-140">EventSubClass</span></span>|`int`|<span data-ttu-id="32202-141">イベント サブクラスの種類。</span><span class="sxs-lookup"><span data-stu-id="32202-141">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="32202-142">0 = 開始</span><span class="sxs-lookup"><span data-stu-id="32202-142">0=Begin</span></span><br /><br /> <span data-ttu-id="32202-143">1 = コミット</span><span class="sxs-lookup"><span data-stu-id="32202-143">1=Commit</span></span><br /><br /> <span data-ttu-id="32202-144">2 = ロールバック</span><span class="sxs-lookup"><span data-stu-id="32202-144">2=Rollback</span></span>|<span data-ttu-id="32202-145">21</span><span class="sxs-lookup"><span data-stu-id="32202-145">21</span></span>|<span data-ttu-id="32202-146">はい</span><span class="sxs-lookup"><span data-stu-id="32202-146">Yes</span></span>|  
|<span data-ttu-id="32202-147">GroupID</span><span class="sxs-lookup"><span data-stu-id="32202-147">GroupID</span></span>|`int`|<span data-ttu-id="32202-148">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="32202-148">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="32202-149">66</span><span class="sxs-lookup"><span data-stu-id="32202-149">66</span></span>|<span data-ttu-id="32202-150">はい</span><span class="sxs-lookup"><span data-stu-id="32202-150">Yes</span></span>|  
|<span data-ttu-id="32202-151">HostName</span><span class="sxs-lookup"><span data-stu-id="32202-151">HostName</span></span>|`nvarchar`|<span data-ttu-id="32202-152">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="32202-152">Name of the computer on which the client is running.</span></span> <span data-ttu-id="32202-153">このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="32202-153">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="32202-154">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="32202-154">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="32202-155">8</span><span class="sxs-lookup"><span data-stu-id="32202-155">8</span></span>|<span data-ttu-id="32202-156">はい</span><span class="sxs-lookup"><span data-stu-id="32202-156">Yes</span></span>|  
|<span data-ttu-id="32202-157">IndexID</span><span class="sxs-lookup"><span data-stu-id="32202-157">IndexID</span></span>|`int`|<span data-ttu-id="32202-158">イベントの影響を受けるオブジェクトに付けられたインデックス用の ID。</span><span class="sxs-lookup"><span data-stu-id="32202-158">ID for the index on the object affected by the event.</span></span> <span data-ttu-id="32202-159">オブジェクトのインデックス ID を特定するには、sys.indexes カタログ ビューの index_id 列を使用します。</span><span class="sxs-lookup"><span data-stu-id="32202-159">To determine the index ID for an object, use the index_id column of the sys.indexes catalog view.</span></span>|<span data-ttu-id="32202-160">24</span><span class="sxs-lookup"><span data-stu-id="32202-160">24</span></span>|<span data-ttu-id="32202-161">はい</span><span class="sxs-lookup"><span data-stu-id="32202-161">Yes</span></span>|  
|<span data-ttu-id="32202-162">IntegerData</span><span class="sxs-lookup"><span data-stu-id="32202-162">IntegerData</span></span>|`int`|<span data-ttu-id="32202-163">トレースでキャプチャされたイベント クラスに依存する整数値。</span><span class="sxs-lookup"><span data-stu-id="32202-163">Integer value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="32202-164">25</span><span class="sxs-lookup"><span data-stu-id="32202-164">25</span></span>|<span data-ttu-id="32202-165">はい</span><span class="sxs-lookup"><span data-stu-id="32202-165">Yes</span></span>|  
|<span data-ttu-id="32202-166">IsSystem</span><span class="sxs-lookup"><span data-stu-id="32202-166">IsSystem</span></span>|`int`|<span data-ttu-id="32202-167">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="32202-167">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="32202-168">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="32202-168">1 = system, 0 = user.</span></span>|<span data-ttu-id="32202-169">60</span><span class="sxs-lookup"><span data-stu-id="32202-169">60</span></span>|<span data-ttu-id="32202-170">はい</span><span class="sxs-lookup"><span data-stu-id="32202-170">Yes</span></span>|  
|<span data-ttu-id="32202-171">LoginName</span><span class="sxs-lookup"><span data-stu-id="32202-171">LoginName</span></span>|`nvarchar`|<span data-ttu-id="32202-172">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="32202-172">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="32202-173">11</span><span class="sxs-lookup"><span data-stu-id="32202-173">11</span></span>|<span data-ttu-id="32202-174">はい</span><span class="sxs-lookup"><span data-stu-id="32202-174">Yes</span></span>|  
|<span data-ttu-id="32202-175">LoginSid</span><span class="sxs-lookup"><span data-stu-id="32202-175">LoginSid</span></span>|`image`|<span data-ttu-id="32202-176">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="32202-176">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="32202-177">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="32202-177">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="32202-178">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="32202-178">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="32202-179">41</span><span class="sxs-lookup"><span data-stu-id="32202-179">41</span></span>|<span data-ttu-id="32202-180">はい</span><span class="sxs-lookup"><span data-stu-id="32202-180">Yes</span></span>|  
|<span data-ttu-id="32202-181">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="32202-181">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="32202-182">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="32202-182">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="32202-183">7</span><span class="sxs-lookup"><span data-stu-id="32202-183">7</span></span>|<span data-ttu-id="32202-184">はい</span><span class="sxs-lookup"><span data-stu-id="32202-184">Yes</span></span>|  
|<span data-ttu-id="32202-185">NTUserName</span><span class="sxs-lookup"><span data-stu-id="32202-185">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="32202-186">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="32202-186">Windows user name.</span></span>|<span data-ttu-id="32202-187">6</span><span class="sxs-lookup"><span data-stu-id="32202-187">6</span></span>|<span data-ttu-id="32202-188">はい</span><span class="sxs-lookup"><span data-stu-id="32202-188">Yes</span></span>|  
|<span data-ttu-id="32202-189">ObjectID</span><span class="sxs-lookup"><span data-stu-id="32202-189">ObjectID</span></span>|`int`|<span data-ttu-id="32202-190">システムによって割り当てられたオブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="32202-190">System-assigned ID of the object.</span></span>|<span data-ttu-id="32202-191">22</span><span class="sxs-lookup"><span data-stu-id="32202-191">22</span></span>|<span data-ttu-id="32202-192">はい</span><span class="sxs-lookup"><span data-stu-id="32202-192">Yes</span></span>|  
|<span data-ttu-id="32202-193">ObjectID2</span><span class="sxs-lookup"><span data-stu-id="32202-193">ObjectID2</span></span>|`bigint`|<span data-ttu-id="32202-194">関連するオブジェクトまたはエンティティの ID</span><span class="sxs-lookup"><span data-stu-id="32202-194">ID of the related object or entity.</span></span>|<span data-ttu-id="32202-195">56</span><span class="sxs-lookup"><span data-stu-id="32202-195">56</span></span>|<span data-ttu-id="32202-196">はい</span><span class="sxs-lookup"><span data-stu-id="32202-196">Yes</span></span>|  
|<span data-ttu-id="32202-197">ObjectName</span><span class="sxs-lookup"><span data-stu-id="32202-197">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="32202-198">参照されているオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="32202-198">Name of the object being referenced.</span></span>|<span data-ttu-id="32202-199">34</span><span class="sxs-lookup"><span data-stu-id="32202-199">34</span></span>|<span data-ttu-id="32202-200">はい</span><span class="sxs-lookup"><span data-stu-id="32202-200">Yes</span></span>|  
|<span data-ttu-id="32202-201">ObjectType</span><span class="sxs-lookup"><span data-stu-id="32202-201">ObjectType</span></span>|`int`|<span data-ttu-id="32202-202">イベントに関係するオブジェクトの種類を表す値。</span><span class="sxs-lookup"><span data-stu-id="32202-202">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="32202-203">この値は sys.objects の type 列に対応します。</span><span class="sxs-lookup"><span data-stu-id="32202-203">This value corresponds to the type column in sys.objects.</span></span> <span data-ttu-id="32202-204">値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32202-204">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="32202-205">28</span><span class="sxs-lookup"><span data-stu-id="32202-205">28</span></span>|<span data-ttu-id="32202-206">はい</span><span class="sxs-lookup"><span data-stu-id="32202-206">Yes</span></span>|  
|<span data-ttu-id="32202-207">RequestID</span><span class="sxs-lookup"><span data-stu-id="32202-207">RequestID</span></span>|`int`|<span data-ttu-id="32202-208">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="32202-208">ID of the request containing the statement.</span></span>|<span data-ttu-id="32202-209">49</span><span class="sxs-lookup"><span data-stu-id="32202-209">49</span></span>|<span data-ttu-id="32202-210">はい</span><span class="sxs-lookup"><span data-stu-id="32202-210">Yes</span></span>|  
|<span data-ttu-id="32202-211">ServerName</span><span class="sxs-lookup"><span data-stu-id="32202-211">ServerName</span></span>|`nvarchar`|<span data-ttu-id="32202-212">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="32202-212">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="32202-213">26</span><span class="sxs-lookup"><span data-stu-id="32202-213">26</span></span>|<span data-ttu-id="32202-214">いいえ</span><span class="sxs-lookup"><span data-stu-id="32202-214">No</span></span>|  
|<span data-ttu-id="32202-215">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="32202-215">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="32202-216">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="32202-216">Login name of the user who originated the session.</span></span> <span data-ttu-id="32202-217">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="32202-217">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows as Login2.</span></span> <span data-ttu-id="32202-218">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="32202-218">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="32202-219">64</span><span class="sxs-lookup"><span data-stu-id="32202-219">64</span></span>|<span data-ttu-id="32202-220">はい</span><span class="sxs-lookup"><span data-stu-id="32202-220">Yes</span></span>|  
|<span data-ttu-id="32202-221">SPID</span><span class="sxs-lookup"><span data-stu-id="32202-221">SPID</span></span>|`int`|<span data-ttu-id="32202-222">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="32202-222">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="32202-223">12</span><span class="sxs-lookup"><span data-stu-id="32202-223">12</span></span>|<span data-ttu-id="32202-224">はい</span><span class="sxs-lookup"><span data-stu-id="32202-224">Yes</span></span>|  
|<span data-ttu-id="32202-225">StartTime</span><span class="sxs-lookup"><span data-stu-id="32202-225">StartTime</span></span>|`datetime`|<span data-ttu-id="32202-226">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="32202-226">Time at which the event started, if available.</span></span>|<span data-ttu-id="32202-227">14</span><span class="sxs-lookup"><span data-stu-id="32202-227">14</span></span>|<span data-ttu-id="32202-228">はい</span><span class="sxs-lookup"><span data-stu-id="32202-228">Yes</span></span>|  
|<span data-ttu-id="32202-229">TransactionID</span><span class="sxs-lookup"><span data-stu-id="32202-229">TransactionID</span></span>|`bigint`|<span data-ttu-id="32202-230">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="32202-230">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="32202-231">4</span><span class="sxs-lookup"><span data-stu-id="32202-231">4</span></span>|<span data-ttu-id="32202-232">はい</span><span class="sxs-lookup"><span data-stu-id="32202-232">Yes</span></span>|  
|<span data-ttu-id="32202-233">XactSequence</span><span class="sxs-lookup"><span data-stu-id="32202-233">XactSequence</span></span>|`bigint`|<span data-ttu-id="32202-234">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="32202-234">Token used to describe the current transaction.</span></span>|<span data-ttu-id="32202-235">50</span><span class="sxs-lookup"><span data-stu-id="32202-235">50</span></span>|<span data-ttu-id="32202-236">はい</span><span class="sxs-lookup"><span data-stu-id="32202-236">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32202-237">参照</span><span class="sxs-lookup"><span data-stu-id="32202-237">See Also</span></span>  
 [<span data-ttu-id="32202-238">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32202-238">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  