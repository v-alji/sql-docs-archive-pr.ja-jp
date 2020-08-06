---
title: OLEDB Call イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB Call event class
ms.assetid: e1be1e90-98cc-47a3-addd-59d4aeca6547
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a26781a34b75893dfb8aad54cea8e7f6d2c2e4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632506"
---
# <a name="oledb-call-event-class"></a><span data-ttu-id="5e56b-102">OLEDB Call イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5e56b-102">OLEDB Call Event Class</span></span>
  <span data-ttu-id="5e56b-103">**OLEDB Call** イベント クラスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から分散クエリやリモート ストアド プロシージャの OLE DB プロバイダーが呼び出されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="5e56b-103">The **OLEDB Call** event class occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] calls an OLE DB provider for distributed queries and remote stored procedures.</span></span>  
  
 <span data-ttu-id="5e56b-104">データを要求しない呼び出し、または **QueryInterface** メソッドに対して行われていない呼び出しだけを監視するには、トレースに **OLEDB Call** イベント クラスを含めます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-104">Include the **OLEDB Call** event class in traces to monitor only those calls that do not request data or calls that are not made to the **QueryInterface** method.</span></span> <span data-ttu-id="5e56b-105">**OLEDB Call** イベント クラスをトレースに含めた場合、発生するオーバーヘッドの量は、トレース中にデータベースに対して OLE DB 呼び出しが発生する頻度によって異なります。</span><span class="sxs-lookup"><span data-stu-id="5e56b-105">When the **OLEDB Call** event class is included in a trace the amount of overhead incurred depends on how frequently OLE DB calls occur against the database during the trace.</span></span> <span data-ttu-id="5e56b-106">呼び出しが頻繁に行われると、トレースによってパフォーマンスが大きく低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="5e56b-106">If calls occur frequently, the trace may significantly impede performance.</span></span>  
  
## <a name="oledb-call-event-class-data-columns"></a><span data-ttu-id="5e56b-107">OLEDB Call イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="5e56b-107">OLEDB Call Event Class Data Columns</span></span>  
  
|<span data-ttu-id="5e56b-108">データ列名</span><span class="sxs-lookup"><span data-stu-id="5e56b-108">Data column name</span></span>|<span data-ttu-id="5e56b-109">データ型</span><span class="sxs-lookup"><span data-stu-id="5e56b-109">Data type</span></span>|<span data-ttu-id="5e56b-110">説明</span><span class="sxs-lookup"><span data-stu-id="5e56b-110">Description</span></span>|<span data-ttu-id="5e56b-111">列 ID</span><span class="sxs-lookup"><span data-stu-id="5e56b-111">Column ID</span></span>|<span data-ttu-id="5e56b-112">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="5e56b-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="5e56b-113">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="5e56b-113">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="5e56b-114">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e56b-115">この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-115">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="5e56b-116">10</span><span class="sxs-lookup"><span data-stu-id="5e56b-116">10</span></span>|<span data-ttu-id="5e56b-117">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-117">Yes</span></span>|  
|<span data-ttu-id="5e56b-118">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="5e56b-118">ClientProcessID</span></span>|`Int`|<span data-ttu-id="5e56b-119">クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。</span><span class="sxs-lookup"><span data-stu-id="5e56b-119">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="5e56b-120">クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-120">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="5e56b-121">9</span><span class="sxs-lookup"><span data-stu-id="5e56b-121">9</span></span>|<span data-ttu-id="5e56b-122">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-122">Yes</span></span>|  
|<span data-ttu-id="5e56b-123">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="5e56b-123">DatabaseID</span></span>|`Int`|<span data-ttu-id="5e56b-124">USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。</span><span class="sxs-lookup"><span data-stu-id="5e56b-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="5e56b-125">では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="5e56b-126">データベースに対応する値は、DB_ID 関数を使用して特定します。</span><span class="sxs-lookup"><span data-stu-id="5e56b-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="5e56b-127">3</span><span class="sxs-lookup"><span data-stu-id="5e56b-127">3</span></span>|<span data-ttu-id="5e56b-128">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-128">Yes</span></span>|  
|<span data-ttu-id="5e56b-129">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="5e56b-129">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-130">ユーザーのステートメントが実行されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="5e56b-130">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="5e56b-131">35</span><span class="sxs-lookup"><span data-stu-id="5e56b-131">35</span></span>|<span data-ttu-id="5e56b-132">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-132">Yes</span></span>|  
|<span data-ttu-id="5e56b-133">Duration</span><span class="sxs-lookup"><span data-stu-id="5e56b-133">Duration</span></span>|`Bigint`|<span data-ttu-id="5e56b-134">OLE DB Call イベントを完了する時間長。</span><span class="sxs-lookup"><span data-stu-id="5e56b-134">Length of time to complete the OLE DB Call event.</span></span>|<span data-ttu-id="5e56b-135">13</span><span class="sxs-lookup"><span data-stu-id="5e56b-135">13</span></span>|<span data-ttu-id="5e56b-136">いいえ</span><span class="sxs-lookup"><span data-stu-id="5e56b-136">No</span></span>|  
|<span data-ttu-id="5e56b-137">EndTime</span><span class="sxs-lookup"><span data-stu-id="5e56b-137">EndTime</span></span>|`Datetime`|<span data-ttu-id="5e56b-138">イベントが終了する時刻。</span><span class="sxs-lookup"><span data-stu-id="5e56b-138">Time that the event ended.</span></span>|<span data-ttu-id="5e56b-139">15</span><span class="sxs-lookup"><span data-stu-id="5e56b-139">15</span></span>|<span data-ttu-id="5e56b-140">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-140">Yes</span></span>|  
|<span data-ttu-id="5e56b-141">エラー</span><span class="sxs-lookup"><span data-stu-id="5e56b-141">Error</span></span>|`int`|<span data-ttu-id="5e56b-142">特定のイベントのエラー番号。</span><span class="sxs-lookup"><span data-stu-id="5e56b-142">Error number of a given event.</span></span> <span data-ttu-id="5e56b-143">多くの場合、sys.messages カタログ ビューに保存されているエラー番号です。</span><span class="sxs-lookup"><span data-stu-id="5e56b-143">Often this is the error number stored in the sys.messages catalog view.</span></span>|<span data-ttu-id="5e56b-144">31</span><span class="sxs-lookup"><span data-stu-id="5e56b-144">31</span></span>|<span data-ttu-id="5e56b-145">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-145">Yes</span></span>|  
|<span data-ttu-id="5e56b-146">EventClass</span><span class="sxs-lookup"><span data-stu-id="5e56b-146">EventClass</span></span>|`Int`|<span data-ttu-id="5e56b-147">イベントの種類 = 119。</span><span class="sxs-lookup"><span data-stu-id="5e56b-147">Type of event = 119.</span></span>|<span data-ttu-id="5e56b-148">27</span><span class="sxs-lookup"><span data-stu-id="5e56b-148">27</span></span>|<span data-ttu-id="5e56b-149">いいえ</span><span class="sxs-lookup"><span data-stu-id="5e56b-149">No</span></span>|  
|<span data-ttu-id="5e56b-150">EventSequence</span><span class="sxs-lookup"><span data-stu-id="5e56b-150">EventSequence</span></span>|`Int`|<span data-ttu-id="5e56b-151">バッチ内の OLE DB イベント クラスのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="5e56b-151">Sequence of OLE DB event class in batch.</span></span>|<span data-ttu-id="5e56b-152">51</span><span class="sxs-lookup"><span data-stu-id="5e56b-152">51</span></span>|<span data-ttu-id="5e56b-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="5e56b-153">No</span></span>|  
|<span data-ttu-id="5e56b-154">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="5e56b-154">EventSubClass</span></span>|`Int`|<span data-ttu-id="5e56b-155">0 = 開始</span><span class="sxs-lookup"><span data-stu-id="5e56b-155">0=Starting</span></span><br /><br /> <span data-ttu-id="5e56b-156">1 = 完了</span><span class="sxs-lookup"><span data-stu-id="5e56b-156">1=Completed</span></span>|<span data-ttu-id="5e56b-157">21</span><span class="sxs-lookup"><span data-stu-id="5e56b-157">21</span></span>|<span data-ttu-id="5e56b-158">いいえ</span><span class="sxs-lookup"><span data-stu-id="5e56b-158">No</span></span>|  
|<span data-ttu-id="5e56b-159">GroupID</span><span class="sxs-lookup"><span data-stu-id="5e56b-159">GroupID</span></span>|`int`|<span data-ttu-id="5e56b-160">SQL トレース イベントが発生したワークロード グループの ID。</span><span class="sxs-lookup"><span data-stu-id="5e56b-160">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="5e56b-161">66</span><span class="sxs-lookup"><span data-stu-id="5e56b-161">66</span></span>|<span data-ttu-id="5e56b-162">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-162">Yes</span></span>|  
|<span data-ttu-id="5e56b-163">HostName</span><span class="sxs-lookup"><span data-stu-id="5e56b-163">HostName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-164">クライアントが実行されているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="5e56b-164">Name of the computer on which the client is running.</span></span> <span data-ttu-id="5e56b-165">このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-165">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="5e56b-166">ホスト名を指定するには、HOST_NAME 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="5e56b-166">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="5e56b-167">8</span><span class="sxs-lookup"><span data-stu-id="5e56b-167">8</span></span>|<span data-ttu-id="5e56b-168">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-168">Yes</span></span>|  
|<span data-ttu-id="5e56b-169">IsSystem</span><span class="sxs-lookup"><span data-stu-id="5e56b-169">IsSystem</span></span>|`int`|<span data-ttu-id="5e56b-170">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="5e56b-170">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="5e56b-171">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="5e56b-171">1 = system, 0 = user.</span></span>|<span data-ttu-id="5e56b-172">60</span><span class="sxs-lookup"><span data-stu-id="5e56b-172">60</span></span>|<span data-ttu-id="5e56b-173">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-173">Yes</span></span>|  
|<span data-ttu-id="5e56b-174">LinkedServerName</span><span class="sxs-lookup"><span data-stu-id="5e56b-174">LinkedServerName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-175">リンク サーバーの名前</span><span class="sxs-lookup"><span data-stu-id="5e56b-175">Name of the linked server.</span></span>|<span data-ttu-id="5e56b-176">45</span><span class="sxs-lookup"><span data-stu-id="5e56b-176">45</span></span>|<span data-ttu-id="5e56b-177">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-177">Yes</span></span>|  
|<span data-ttu-id="5e56b-178">LoginName</span><span class="sxs-lookup"><span data-stu-id="5e56b-178">LoginName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-179">ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。</span><span class="sxs-lookup"><span data-stu-id="5e56b-179">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\Username).</span></span>|<span data-ttu-id="5e56b-180">11</span><span class="sxs-lookup"><span data-stu-id="5e56b-180">11</span></span>|<span data-ttu-id="5e56b-181">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-181">Yes</span></span>|  
|<span data-ttu-id="5e56b-182">LoginSid</span><span class="sxs-lookup"><span data-stu-id="5e56b-182">LoginSid</span></span>|`Image`|<span data-ttu-id="5e56b-183">ログインしたユーザーのセキュリティ識別子 (SID)。</span><span class="sxs-lookup"><span data-stu-id="5e56b-183">Security identifier (SID) of the logged-in user.</span></span> <span data-ttu-id="5e56b-184">この情報は、sys.server_principals カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-184">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="5e56b-185">各 SID はサーバーのログインごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="5e56b-185">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="5e56b-186">41</span><span class="sxs-lookup"><span data-stu-id="5e56b-186">41</span></span>|<span data-ttu-id="5e56b-187">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-187">Yes</span></span>|  
|<span data-ttu-id="5e56b-188">MethodName</span><span class="sxs-lookup"><span data-stu-id="5e56b-188">MethodName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-189">OLE DB メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="5e56b-189">Name of the OLE DB method.</span></span>|<span data-ttu-id="5e56b-190">47</span><span class="sxs-lookup"><span data-stu-id="5e56b-190">47</span></span>|<span data-ttu-id="5e56b-191">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-191">Yes</span></span>|  
|<span data-ttu-id="5e56b-192">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="5e56b-192">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-193">ユーザーが所属する Windows ドメイン。</span><span class="sxs-lookup"><span data-stu-id="5e56b-193">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="5e56b-194">7</span><span class="sxs-lookup"><span data-stu-id="5e56b-194">7</span></span>|<span data-ttu-id="5e56b-195">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-195">Yes</span></span>|  
|<span data-ttu-id="5e56b-196">NTUserName</span><span class="sxs-lookup"><span data-stu-id="5e56b-196">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-197">Windows のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="5e56b-197">Windows user name.</span></span>|<span data-ttu-id="5e56b-198">6</span><span class="sxs-lookup"><span data-stu-id="5e56b-198">6</span></span>|<span data-ttu-id="5e56b-199">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-199">Yes</span></span>|  
|<span data-ttu-id="5e56b-200">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5e56b-200">ProviderName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-201">OLE DB プロバイダーの名前です。</span><span class="sxs-lookup"><span data-stu-id="5e56b-201">Name of the OLE DB provider.</span></span>|<span data-ttu-id="5e56b-202">46</span><span class="sxs-lookup"><span data-stu-id="5e56b-202">46</span></span>|<span data-ttu-id="5e56b-203">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-203">Yes</span></span>|  
|<span data-ttu-id="5e56b-204">RequestID</span><span class="sxs-lookup"><span data-stu-id="5e56b-204">RequestID</span></span>|`Int`|<span data-ttu-id="5e56b-205">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="5e56b-205">ID of the request containing the statement.</span></span>|<span data-ttu-id="5e56b-206">49</span><span class="sxs-lookup"><span data-stu-id="5e56b-206">49</span></span>|<span data-ttu-id="5e56b-207">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-207">Yes</span></span>|  
|<span data-ttu-id="5e56b-208">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="5e56b-208">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="5e56b-209">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="5e56b-209">Login name of the user who originated the session.</span></span> <span data-ttu-id="5e56b-210">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、`SessionLoginName` には Login1 が表示され、`LoginName` には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-210">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, `SessionLoginName` shows Login1 and `LoginName` shows Login2.</span></span> <span data-ttu-id="5e56b-211">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e56b-211">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="5e56b-212">64</span><span class="sxs-lookup"><span data-stu-id="5e56b-212">64</span></span>|<span data-ttu-id="5e56b-213">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-213">Yes</span></span>|  
|<span data-ttu-id="5e56b-214">SPID</span><span class="sxs-lookup"><span data-stu-id="5e56b-214">SPID</span></span>|`Int`|<span data-ttu-id="5e56b-215">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="5e56b-215">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="5e56b-216">12</span><span class="sxs-lookup"><span data-stu-id="5e56b-216">12</span></span>|<span data-ttu-id="5e56b-217">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-217">Yes</span></span>|  
|<span data-ttu-id="5e56b-218">StartTime</span><span class="sxs-lookup"><span data-stu-id="5e56b-218">StartTime</span></span>|`datetime`|<span data-ttu-id="5e56b-219">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="5e56b-219">Time at which the event started, if available.</span></span>|<span data-ttu-id="5e56b-220">14</span><span class="sxs-lookup"><span data-stu-id="5e56b-220">14</span></span>|<span data-ttu-id="5e56b-221">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-221">Yes</span></span>|  
|<span data-ttu-id="5e56b-222">TextData</span><span class="sxs-lookup"><span data-stu-id="5e56b-222">TextData</span></span>|`nvarchar`|<span data-ttu-id="5e56b-223">OLE DB 呼び出しで送受信されるパラメーター。</span><span class="sxs-lookup"><span data-stu-id="5e56b-223">Parameters sent and received in the OLE DB call.</span></span>|<span data-ttu-id="5e56b-224">1</span><span class="sxs-lookup"><span data-stu-id="5e56b-224">1</span></span>|<span data-ttu-id="5e56b-225">いいえ</span><span class="sxs-lookup"><span data-stu-id="5e56b-225">No</span></span>|  
|<span data-ttu-id="5e56b-226">TransactionID</span><span class="sxs-lookup"><span data-stu-id="5e56b-226">TransactionID</span></span>|`bigint`|<span data-ttu-id="5e56b-227">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="5e56b-227">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="5e56b-228">4</span><span class="sxs-lookup"><span data-stu-id="5e56b-228">4</span></span>|<span data-ttu-id="5e56b-229">はい</span><span class="sxs-lookup"><span data-stu-id="5e56b-229">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e56b-230">参照</span><span class="sxs-lookup"><span data-stu-id="5e56b-230">See Also</span></span>  
 <span data-ttu-id="5e56b-231">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="5e56b-231">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="5e56b-232">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e56b-232">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="5e56b-233">Transact-SQL での OLE オートメーション オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5e56b-233">OLE Automation Objects in Transact-SQL</span></span>](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  