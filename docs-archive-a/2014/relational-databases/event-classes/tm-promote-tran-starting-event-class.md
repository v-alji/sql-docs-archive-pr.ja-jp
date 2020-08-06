---
title: 'TM: Promote Tran Starting イベント クラス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'TM: Promote Tran Starting event class'
ms.assetid: 32da85bb-d980-4044-8572-31372867649b
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8975b99640d539827b480d6e7650acb4fd089fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632491"
---
# <a name="tm-promote-tran-starting-event-class"></a><span data-ttu-id="d1712-102">TM: Promote Tran Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="d1712-102">TM: Promote Tran Starting Event Class</span></span>
  <span data-ttu-id="d1712-103">TM: Promote Tran Starting イベント クラスは、PROMOTE TRANSACTION 要求が開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="d1712-103">The TM: Promote Tran Starting event class indicates that a PROMOTE TRANSACTION request is starting.</span></span> <span data-ttu-id="d1712-104">要求は、トランザクション管理インターフェイスを使用してクライアントから送信されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-104">The request is sent from the client through the transaction management interface.</span></span>  
  
## <a name="tm-promote-tran-starting-event-class-data-columns"></a><span data-ttu-id="d1712-105">TM: Promote Tran Starting イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="d1712-105">TM: Promote Tran Starting Event Class Data Columns</span></span>  
  
|<span data-ttu-id="d1712-106">データ列名</span><span class="sxs-lookup"><span data-stu-id="d1712-106">Data column name</span></span>|<span data-ttu-id="d1712-107">データ型</span><span class="sxs-lookup"><span data-stu-id="d1712-107">Data type</span></span>|<span data-ttu-id="d1712-108">説明</span><span class="sxs-lookup"><span data-stu-id="d1712-108">Description</span></span>|<span data-ttu-id="d1712-109">列 ID</span><span class="sxs-lookup"><span data-stu-id="d1712-109">Column ID</span></span>|<span data-ttu-id="d1712-110">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="d1712-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="d1712-111">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="d1712-111">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="d1712-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="d1712-112">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d1712-113">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="d1712-114">10</span><span class="sxs-lookup"><span data-stu-id="d1712-114">10</span></span>|<span data-ttu-id="d1712-115">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-115">Yes</span></span>|  
|<span data-ttu-id="d1712-116">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="d1712-116">ClientProcessID</span></span>|`int`|<span data-ttu-id="d1712-117">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="d1712-117">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="d1712-118">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-118">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="d1712-119">9</span><span class="sxs-lookup"><span data-stu-id="d1712-119">9</span></span>|<span data-ttu-id="d1712-120">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-120">Yes</span></span>|  
|<span data-ttu-id="d1712-121">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="d1712-121">DatabaseID</span></span>|`int`|<span data-ttu-id="d1712-122">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="d1712-122">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="d1712-123">では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-123">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="d1712-124">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="d1712-124">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="d1712-125">3</span><span class="sxs-lookup"><span data-stu-id="d1712-125">3</span></span>|<span data-ttu-id="d1712-126">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-126">Yes</span></span>|  
|<span data-ttu-id="d1712-127">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="d1712-127">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="d1712-128">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="d1712-128">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="d1712-129">35</span><span class="sxs-lookup"><span data-stu-id="d1712-129">35</span></span>|<span data-ttu-id="d1712-130">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-130">Yes</span></span>|  
|<span data-ttu-id="d1712-131">EventClass</span><span class="sxs-lookup"><span data-stu-id="d1712-131">EventClass</span></span>|`int`|<span data-ttu-id="d1712-132">イベントの種類 = 183。</span><span class="sxs-lookup"><span data-stu-id="d1712-132">Type of event = 183.</span></span>|<span data-ttu-id="d1712-133">27</span><span class="sxs-lookup"><span data-stu-id="d1712-133">27</span></span>|<span data-ttu-id="d1712-134">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1712-134">No</span></span>|  
|<span data-ttu-id="d1712-135">EventSequence</span><span class="sxs-lookup"><span data-stu-id="d1712-135">EventSequence</span></span>|`int`|<span data-ttu-id="d1712-136">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="d1712-136">The sequence of a given event within the request.</span></span>|<span data-ttu-id="d1712-137">51</span><span class="sxs-lookup"><span data-stu-id="d1712-137">51</span></span>|<span data-ttu-id="d1712-138">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1712-138">No</span></span>|  
|<span data-ttu-id="d1712-139">GroupID</span><span class="sxs-lookup"><span data-stu-id="d1712-139">GroupID</span></span>|`int`|<span data-ttu-id="d1712-140">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="d1712-140">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="d1712-141">66</span><span class="sxs-lookup"><span data-stu-id="d1712-141">66</span></span>|<span data-ttu-id="d1712-142">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-142">Yes</span></span>|  
|<span data-ttu-id="d1712-143">HostName</span><span class="sxs-lookup"><span data-stu-id="d1712-143">HostName</span></span>|`nvarchar`|<span data-ttu-id="d1712-144">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="d1712-144">Name of the computer on which the client is running.</span></span> <span data-ttu-id="d1712-145">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-145">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="d1712-146">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1712-146">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="d1712-147">8</span><span class="sxs-lookup"><span data-stu-id="d1712-147">8</span></span>|<span data-ttu-id="d1712-148">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-148">Yes</span></span>|  
|<span data-ttu-id="d1712-149">IsSystem</span><span class="sxs-lookup"><span data-stu-id="d1712-149">IsSystem</span></span>|`int`|<span data-ttu-id="d1712-150">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="d1712-150">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="d1712-151">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="d1712-151">1 = system, 0 = user.</span></span>|<span data-ttu-id="d1712-152">60</span><span class="sxs-lookup"><span data-stu-id="d1712-152">60</span></span>|<span data-ttu-id="d1712-153">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-153">Yes</span></span>|  
|<span data-ttu-id="d1712-154">LoginName</span><span class="sxs-lookup"><span data-stu-id="d1712-154">LoginName</span></span>|`nvarchar`|<span data-ttu-id="d1712-155">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="d1712-155">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="d1712-156">11</span><span class="sxs-lookup"><span data-stu-id="d1712-156">11</span></span>|<span data-ttu-id="d1712-157">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-157">Yes</span></span>|  
|<span data-ttu-id="d1712-158">LoginSid</span><span class="sxs-lookup"><span data-stu-id="d1712-158">LoginSid</span></span>|`image`|<span data-ttu-id="d1712-159">ログイン ユーザーのセキュリティ ID 番号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="d1712-159">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="d1712-160">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="d1712-160">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="d1712-161">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="d1712-161">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="d1712-162">41</span><span class="sxs-lookup"><span data-stu-id="d1712-162">41</span></span>|<span data-ttu-id="d1712-163">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-163">Yes</span></span>|  
|<span data-ttu-id="d1712-164">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="d1712-164">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="d1712-165">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="d1712-165">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="d1712-166">7</span><span class="sxs-lookup"><span data-stu-id="d1712-166">7</span></span>|<span data-ttu-id="d1712-167">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-167">Yes</span></span>|  
|<span data-ttu-id="d1712-168">NTUserName</span><span class="sxs-lookup"><span data-stu-id="d1712-168">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="d1712-169">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="d1712-169">Windows user name.</span></span>|<span data-ttu-id="d1712-170">6</span><span class="sxs-lookup"><span data-stu-id="d1712-170">6</span></span>|<span data-ttu-id="d1712-171">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-171">Yes</span></span>|  
|<span data-ttu-id="d1712-172">RequestID</span><span class="sxs-lookup"><span data-stu-id="d1712-172">RequestID</span></span>|`int`|<span data-ttu-id="d1712-173">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="d1712-173">The ID of the request containing the statement.</span></span>|<span data-ttu-id="d1712-174">49</span><span class="sxs-lookup"><span data-stu-id="d1712-174">49</span></span>|<span data-ttu-id="d1712-175">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-175">Yes</span></span>|  
|<span data-ttu-id="d1712-176">ServerName</span><span class="sxs-lookup"><span data-stu-id="d1712-176">ServerName</span></span>|`nvarchar`|<span data-ttu-id="d1712-177">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="d1712-177">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="d1712-178">26</span><span class="sxs-lookup"><span data-stu-id="d1712-178">26</span></span>|<span data-ttu-id="d1712-179">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1712-179">No</span></span>|  
|<span data-ttu-id="d1712-180">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="d1712-180">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="d1712-181">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="d1712-181">Login name of the user who originated the session.</span></span> <span data-ttu-id="d1712-182">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-182">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="d1712-183">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1712-183">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="d1712-184">64</span><span class="sxs-lookup"><span data-stu-id="d1712-184">64</span></span>|<span data-ttu-id="d1712-185">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-185">Yes</span></span>|  
|<span data-ttu-id="d1712-186">SPID</span><span class="sxs-lookup"><span data-stu-id="d1712-186">SPID</span></span>|`int`|<span data-ttu-id="d1712-187">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="d1712-187">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="d1712-188">12</span><span class="sxs-lookup"><span data-stu-id="d1712-188">12</span></span>|<span data-ttu-id="d1712-189">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-189">Yes</span></span>|  
|<span data-ttu-id="d1712-190">StartTime</span><span class="sxs-lookup"><span data-stu-id="d1712-190">StartTime</span></span>|`datetime`|<span data-ttu-id="d1712-191">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="d1712-191">Time at which the event started, if available.</span></span>|<span data-ttu-id="d1712-192">14</span><span class="sxs-lookup"><span data-stu-id="d1712-192">14</span></span>|<span data-ttu-id="d1712-193">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-193">Yes</span></span>|  
|<span data-ttu-id="d1712-194">TransactionID</span><span class="sxs-lookup"><span data-stu-id="d1712-194">TransactionID</span></span>|`bigint`|<span data-ttu-id="d1712-195">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="d1712-195">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="d1712-196">4</span><span class="sxs-lookup"><span data-stu-id="d1712-196">4</span></span>|<span data-ttu-id="d1712-197">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-197">Yes</span></span>|  
|<span data-ttu-id="d1712-198">XactSequence</span><span class="sxs-lookup"><span data-stu-id="d1712-198">XactSequence</span></span>|`bigint`|<span data-ttu-id="d1712-199">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="d1712-199">Token that describes the current transaction.</span></span>|<span data-ttu-id="d1712-200">50</span><span class="sxs-lookup"><span data-stu-id="d1712-200">50</span></span>|<span data-ttu-id="d1712-201">はい</span><span class="sxs-lookup"><span data-stu-id="d1712-201">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1712-202">参照</span><span class="sxs-lookup"><span data-stu-id="d1712-202">See Also</span></span>  
 [<span data-ttu-id="d1712-203">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d1712-203">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  