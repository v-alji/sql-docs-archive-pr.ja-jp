---
title: レプリケーション キュー リーダー エージェント | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 854c425db3fbaa346dab5eb2c41bd58cf03f65c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632412"
---
# <a name="replication-queue-reader-agent"></a><span data-ttu-id="3bafc-102">Replication Queue Reader Agent</span><span class="sxs-lookup"><span data-stu-id="3bafc-102">Replication Queue Reader Agent</span></span>
  <span data-ttu-id="3bafc-103">レプリケーション キュー リーダー エージェントは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のキューまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] のメッセージ キューに格納されたメッセージを読み取り、これらのメッセージをパブリッシャーに適用する実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3bafc-103">The Replication Queue Reader Agent is an executable that reads messages stored in a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue or a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Message Queue and then applies those messages to the Publisher.</span></span> <span data-ttu-id="3bafc-104">キュー リーダー エージェントは、スナップショット、およびキュー更新を許可するトランザクション パブリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-104">Queue Reader Agent is used with snapshot and transactional publications that allow queued updating.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bafc-105">パラメーターは任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="3bafc-106">オプション パラメーターを指定しなかった場合、既定のエージェント プロファイルの定義済みの値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-106">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bafc-107">構文</span><span class="sxs-lookup"><span data-stu-id="3bafc-107">Syntax</span></span>  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3bafc-108">引数</span><span class="sxs-lookup"><span data-stu-id="3bafc-108">Arguments</span></span>  
 <span data-ttu-id="3bafc-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="3bafc-109">**-?**</span></span>  
 <span data-ttu-id="3bafc-110">使用方法に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-110">Displays usage information.</span></span>  
  
 <span data-ttu-id="3bafc-111">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="3bafc-111">**-Continuous**</span></span>  
 <span data-ttu-id="3bafc-112">キューに格納されたトランザクションの処理を、エージェントが継続的に試みるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-112">Specifies whether the agent attempts to process queued transactions continuously.</span></span> <span data-ttu-id="3bafc-113">指定した場合、エージェントは、サブスクライバーから受け取った保留中のトランザクションがキューに存在しない場合でも、実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-113">If specified, the agent continues execution even if there are no queued transactions pending from any of the subscribers.</span></span>  
  
 <span data-ttu-id="3bafc-114">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="3bafc-114">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="3bafc-115">エージェント定義ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="3bafc-115">Is the path of the agent definition file.</span></span> <span data-ttu-id="3bafc-116">エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-116">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="3bafc-117">ファイルの内容は実行可能ファイルとして解析されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-117">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="3bafc-118">二重引用符 (") を使用して、任意の文字を含む引数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-118">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="3bafc-119">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="3bafc-119">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="3bafc-120">ディストリビューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-120">Is the Distributor name.</span></span> <span data-ttu-id="3bafc-121">サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-121">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="3bafc-122">サーバー上の *server_name*\\*instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-122">Specify *server_name*\\*instance_name* for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="3bafc-123">指定しなかった場合、既定値はローカル コンピューターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの名前になります。</span><span class="sxs-lookup"><span data-stu-id="3bafc-123">If not specified, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="3bafc-124">**-DistributionDB** _distribution_database_</span><span class="sxs-lookup"><span data-stu-id="3bafc-124">**-DistributionDB** _distribution_database_</span></span>  
 <span data-ttu-id="3bafc-125">ディストリビューション データベース名です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-125">Is the distribution database.</span></span>  
  
 <span data-ttu-id="3bafc-126">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="3bafc-126">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="3bafc-127">ディストリビューターのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-127">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="3bafc-128">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="3bafc-128">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="3bafc-129">ディストリビューターのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="3bafc-129">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="3bafc-130">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="3bafc-130">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="3bafc-131">ディストリビューターのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-131">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="3bafc-132">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-132">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="3bafc-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="3bafc-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="3bafc-134">接続確立時にキュー リーダー エージェントが使用する SSL (Secure Sockets Layer) の暗号化レベルです。</span><span class="sxs-lookup"><span data-stu-id="3bafc-134">Is the level of Secure Sockets Layer (SSL) encryption used by the Queue Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="3bafc-135">EncryptionLevel の値</span><span class="sxs-lookup"><span data-stu-id="3bafc-135">EncryptionLevel value</span></span>|<span data-ttu-id="3bafc-136">説明</span><span class="sxs-lookup"><span data-stu-id="3bafc-136">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="3bafc-137">**0**</span><span class="sxs-lookup"><span data-stu-id="3bafc-137">**0**</span></span>|<span data-ttu-id="3bafc-138">SSL は使用されません。</span><span class="sxs-lookup"><span data-stu-id="3bafc-138">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="3bafc-139">**1**</span><span class="sxs-lookup"><span data-stu-id="3bafc-139">**1**</span></span>|<span data-ttu-id="3bafc-140">SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="3bafc-140">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="3bafc-141">**2**</span><span class="sxs-lookup"><span data-stu-id="3bafc-141">**2**</span></span>|<span data-ttu-id="3bafc-142">SSL が使用され、証明書の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-142">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="3bafc-143">有効な SSL 証明書には、SQL Server の完全修飾ドメイン名が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-143">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="3bafc-144">-EncryptionLevel を 2 に設定したときにエージェントが正しく接続されるようにするには、ローカルの SQL Server 上に別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-144">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="3bafc-145">'Alias Name' パラメーターはサーバー名にし、'Server' パラメーターは SQL Server の完全修飾名に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bafc-145">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="3bafc-146">詳細については、「 [SQL Server レプリケーションセキュリティ](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bafc-146">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="3bafc-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="3bafc-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="3bafc-148">キュー リーダー操作中にログに記録する履歴の量を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-148">Specifies the amount of history logged during a queue reader operation.</span></span> <span data-ttu-id="3bafc-149">**1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-149">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="3bafc-150">HistoryVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="3bafc-150">HistoryVerboseLevel value</span></span>|<span data-ttu-id="3bafc-151">説明</span><span class="sxs-lookup"><span data-stu-id="3bafc-151">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="3bafc-152">**0**</span><span class="sxs-lookup"><span data-stu-id="3bafc-152">**0**</span></span>|<span data-ttu-id="3bafc-153">履歴はログに記録されません。この設定はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="3bafc-153">No history logging (not recommended).</span></span>|  
|<span data-ttu-id="3bafc-154">**1**</span><span class="sxs-lookup"><span data-stu-id="3bafc-154">**1**</span></span>|<span data-ttu-id="3bafc-155">既定値。</span><span class="sxs-lookup"><span data-stu-id="3bafc-155">Default.</span></span> <span data-ttu-id="3bafc-156">同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-156">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="3bafc-157">前回の記録に同じ状態がない場合は、新しい記録を挿入します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-157">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="3bafc-158">**2**</span><span class="sxs-lookup"><span data-stu-id="3bafc-158">**2**</span></span>|<span data-ttu-id="3bafc-159">アイドル状態のメッセージや長時間実行されるジョブのメッセージを含む新しい履歴レコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-159">Insert new history records, including idle messages or long-running job messages.</span></span>|  
|<span data-ttu-id="3bafc-160">**3**</span><span class="sxs-lookup"><span data-stu-id="3bafc-160">**3**</span></span>|<span data-ttu-id="3bafc-161">トラブルシューティングに役立つ補足的な情報を含む新しい履歴レコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-161">Insert new history records that include additional details that may be useful for troubleshooting.</span></span>|  
  
 <span data-ttu-id="3bafc-162">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="3bafc-162">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="3bafc-163">ログインがタイムアウトになるまでの秒数です。既定値は 15 秒です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-163">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="3bafc-164">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="3bafc-164">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="3bafc-165">エージェントの出力ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="3bafc-165">Is the path of the agent output file.</span></span> <span data-ttu-id="3bafc-166">ファイル名が指定されていない場合、出力はコンソールに送られます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-166">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="3bafc-167">指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-167">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="3bafc-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="3bafc-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="3bafc-169">出力を詳細表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-169">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="3bafc-170">詳細レベルが **0**の場合、エラー メッセージだけが出力されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-170">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="3bafc-171">詳細レベルが **1**の場合、すべての実行状況報告メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-171">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="3bafc-172">詳細レベルが **2** (既定値) の場合、すべてのエラー メッセージと実行状況報告メッセージが出力されます。これはデバッグ時に便利です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-172">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="3bafc-173">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="3bafc-173">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="3bafc-174">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ベースのキューを使用したサブスクリプションの更新時にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-174">Is relevant only for updating subscriptions that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] based queues.</span></span> <span data-ttu-id="3bafc-175">保留中のトランザクションがキューに格納されているかどうかを確認するために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のキューをポーリングする頻度を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-175">Specifies how often, in seconds, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue is polled for pending queued transactions.</span></span> <span data-ttu-id="3bafc-176">有効値は、0 ～ 240 秒です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-176">The value can be between 0 and 240 seconds.</span></span> <span data-ttu-id="3bafc-177">既定値は 5 秒です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-177">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="3bafc-178">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="3bafc-178">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="3bafc-179">パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-179">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="3bafc-180">詳細については、「 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3bafc-180">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="3bafc-181">**-ProfileName** _agent_profile_name_</span><span class="sxs-lookup"><span data-stu-id="3bafc-181">**-ProfileName** _agent_profile_name_</span></span>  
 <span data-ttu-id="3bafc-182">エージェントに対して既定値を提供するエージェント プロファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-182">Is the name of an agent profile used to supply a set of default values to the agent.</span></span> <span data-ttu-id="3bafc-183">詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bafc-183">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="3bafc-184">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="3bafc-184">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="3bafc-185">クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。</span><span class="sxs-lookup"><span data-stu-id="3bafc-185">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="3bafc-186">**-ResolverState** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="3bafc-186">**-ResolverState** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="3bafc-187">キュー更新における競合の解決方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-187">Specifies how queued updating conflicts are resolved.</span></span> <span data-ttu-id="3bafc-188">**1** はパブリッシャーが優先されることを示します。この場合、現在キューの中で競合しているトランザクションはパブリッシャー側、およびキューを更新しようとしたサブスクライバー側でロールバックされます。キューに格納されている、それ以降のトランザクションについては、処理が継続されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-188">A value of **1** indicates the Publisher wins the conflict, and the current conflicting queued transaction will be rolled back on the Publisher and the originating updating Subscriber; the processing of subsequent queued transactions will continue.</span></span> <span data-ttu-id="3bafc-189">**2** はサブスクライバーがオーバーライドされることを示します。つまり、キューに格納されたトランザクションの方がパブリッシャー側の値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3bafc-189">A value of **2** indicates the Subscriber wins the conflict, and the queued transaction will override the values on the Publisher.</span></span> <span data-ttu-id="3bafc-190">**3** は、競合が発生した場合は常にサブスクライバーが再初期化されることを示します (つまり、パブリッシャーが優先されます)。この場合、キューに格納された後続のトランザクションは強制的に終了され、サブスクリプションが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="3bafc-190">A value of **3** indicates that any conflict will result in Subscriber re-initialization; the Publisher wins the conflict, processing of subsequent queued transactions will be terminated, and the subscription will be reinitialized.</span></span> <span data-ttu-id="3bafc-191">既定の設定は、トランザクション パブリケーションの場合は **1** に、スナップショット パブリケーションの場合は **3** になります。</span><span class="sxs-lookup"><span data-stu-id="3bafc-191">The default setting is **1** for transactional publications and **3** for snapshot publications.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bafc-192">解説</span><span class="sxs-lookup"><span data-stu-id="3bafc-192">Remarks</span></span>  
 <span data-ttu-id="3bafc-193">キュー リーダー エージェントを起動するには、コマンド プロンプトから **qrdrsvc.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="3bafc-193">To start the Queue Reader Agent, execute **qrdrsvc.exe** from the command prompt.</span></span> <span data-ttu-id="3bafc-194">詳細については、「 [レプリケーション エージェント実行可能ファイルのプログラミング](../concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bafc-194">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bafc-195">参照</span><span class="sxs-lookup"><span data-stu-id="3bafc-195">See Also</span></span>  
 [<span data-ttu-id="3bafc-196">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="3bafc-196">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
