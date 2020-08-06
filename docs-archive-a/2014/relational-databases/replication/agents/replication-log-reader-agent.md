---
title: レプリケーション ログ リーダー エージェント | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 120c7418d8b16fe6d083961affcf0b8a9c9f6c65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640883"
---
# <a name="replication-log-reader-agent"></a><span data-ttu-id="53bcf-102">レプリケーション ログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="53bcf-102">Replication Log Reader Agent</span></span>
  <span data-ttu-id="53bcf-103">レプリケーション ログ リーダー エージェントは、トランザクション レプリケーション用に構成した各データベースのトランザクション ログを監視し、レプリケーションのマークが付けられたトランザクションをトランザクション ログからディストリビューション データベースにコピーする実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-103">The Replication Log Reader Agent is an executable that monitors the transaction log of each database configured for transactional replication and copies the transactions marked for replication from the transaction log into the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53bcf-104">パラメーターは任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="53bcf-105">オプション パラメーターを指定しなかった場合、既定のエージェント プロファイルの定義済みの値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-105">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bcf-106">構文</span><span class="sxs-lookup"><span data-stu-id="53bcf-106">Syntax</span></span>  
  
```  
  
      logread [-?]   
-Publisherserver_name[\instance_name]   
-PublisherDBpublisher_database   
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-LogScanThresholdscan_threshold]  
[-MaxCmdsInTrannumber_of_commands]  
[-MessageIntervalmessage_interval]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]   
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-QueryTimeOutquery_time_out_seconds]  
[-ReadBatchSizenumber_of_transactions]   
[-ReadBatchThresholdread_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a><span data-ttu-id="53bcf-107">引数</span><span class="sxs-lookup"><span data-stu-id="53bcf-107">Arguments</span></span>  
 <span data-ttu-id="53bcf-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="53bcf-108">**-?**</span></span>  
 <span data-ttu-id="53bcf-109">使用方法に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-109">Displays usage information.</span></span>  
  
 <span data-ttu-id="53bcf-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="53bcf-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="53bcf-111">パブリッシャーの名前です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-111">Is the name of the Publisher.</span></span> <span data-ttu-id="53bcf-112">サーバー上の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、*server_name* を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="53bcf-113">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="53bcf-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="53bcf-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="53bcf-115">パブリッシャー データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="53bcf-116">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="53bcf-116">**-Continuous**</span></span>  
 <span data-ttu-id="53bcf-117">エージェントがレプリケートされたトランザクションの呼び出しを継続的に試みるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-117">Specifies whether the agent tries to poll replicated transactions continually.</span></span> <span data-ttu-id="53bcf-118">このパラメーターを指定する場合は、保留されているトランザクションがなくても、エージェントはポーリング間隔でレプリケートされたトランザクションをソースから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-118">If specified, the agent polls replicated transactions from the source at polling intervals even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="53bcf-119">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="53bcf-119">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="53bcf-120">エージェント定義ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-120">Is the path of the agent definition file.</span></span> <span data-ttu-id="53bcf-121">エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-121">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="53bcf-122">ファイルの内容は実行可能ファイルとして解析されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-122">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="53bcf-123">二重引用符 (") を使用して、任意の文字を含む引数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-123">Use double quotation marks (") to specify argument values that contain arbitrary characters.</span></span>  
  
 <span data-ttu-id="53bcf-124">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="53bcf-124">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="53bcf-125">ディストリビューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-125">Is the Distributor name.</span></span> <span data-ttu-id="53bcf-126">サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-126">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="53bcf-127">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-127">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="53bcf-128">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="53bcf-128">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="53bcf-129">ディストリビューターのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-129">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="53bcf-130">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="53bcf-130">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="53bcf-131">ディストリビューターのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-131">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="53bcf-132">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="53bcf-132">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="53bcf-133">ディストリビューターのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-133">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="53bcf-134">**0** の値は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、 **1** の値は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-134">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="53bcf-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="53bcf-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="53bcf-136">ログ リーダー エージェントが接続を行うときに使用する SSL (Secure Sockets Layer) 暗号化レベルです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-136">Is the level of Secure Sockets Layer (SSL) encryption that is used by the Log Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="53bcf-137">EncryptionLevel の値</span><span class="sxs-lookup"><span data-stu-id="53bcf-137">EncryptionLevel value</span></span>|<span data-ttu-id="53bcf-138">説明</span><span class="sxs-lookup"><span data-stu-id="53bcf-138">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="53bcf-139">**0**</span><span class="sxs-lookup"><span data-stu-id="53bcf-139">**0**</span></span>|<span data-ttu-id="53bcf-140">SSL は使用されません。</span><span class="sxs-lookup"><span data-stu-id="53bcf-140">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="53bcf-141">**1**</span><span class="sxs-lookup"><span data-stu-id="53bcf-141">**1**</span></span>|<span data-ttu-id="53bcf-142">SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="53bcf-142">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="53bcf-143">**2**</span><span class="sxs-lookup"><span data-stu-id="53bcf-143">**2**</span></span>|<span data-ttu-id="53bcf-144">SSL が使用され、証明書の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-144">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="53bcf-145">有効な SSL 証明書には、SQL Server の完全修飾ドメイン名が定義されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-145">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="53bcf-146">-EncryptionLevel を 2 に設定したときにエージェントが正しく接続されるようにするには、ローカルの SQL Server 上に別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-146">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="53bcf-147">'Alias Name' パラメーターはサーバー名にし、'Server' パラメーターは SQL Server の完全修飾名に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bcf-147">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
 
 <span data-ttu-id="53bcf-148">詳細については、「 [SQL Server レプリケーションセキュリティ](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bcf-148">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="53bcf-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="53bcf-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="53bcf-150">拡張イベントの XML 構成ファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-150">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="53bcf-151">拡張イベントの構成ファイルによって、追跡に必要なセッションを構成し、イベントを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-151">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="53bcf-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="53bcf-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="53bcf-153">ログ リーダー操作中にログに記録する履歴の量を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-153">Specifies the amount of history logged during a log reader operation.</span></span> <span data-ttu-id="53bcf-154">**1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-154">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="53bcf-155">HistoryVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="53bcf-155">HistoryVerboseLevel value</span></span>|<span data-ttu-id="53bcf-156">説明</span><span class="sxs-lookup"><span data-stu-id="53bcf-156">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="53bcf-157">**0**</span><span class="sxs-lookup"><span data-stu-id="53bcf-157">**0**</span></span>||  
|<span data-ttu-id="53bcf-158">**1**</span><span class="sxs-lookup"><span data-stu-id="53bcf-158">**1**</span></span>|<span data-ttu-id="53bcf-159">既定値。</span><span class="sxs-lookup"><span data-stu-id="53bcf-159">Default.</span></span> <span data-ttu-id="53bcf-160">同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-160">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="53bcf-161">前回の記録に同じ状態がない場合は、新しい記録を挿入します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-161">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="53bcf-162">**2**</span><span class="sxs-lookup"><span data-stu-id="53bcf-162">**2**</span></span>|<span data-ttu-id="53bcf-163">アイドル状態や長時間実行を示すメッセージでない場合、新しい履歴レコードを挿入します。アイドル状態などを示すメッセージの場合には、以前のレコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-163">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
  
 <span data-ttu-id="53bcf-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="53bcf-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="53bcf-165">既存の接続がサーバーからの応答を待機しているかどうかを、履歴スレッドがチェックするまでの秒数です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-165">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="53bcf-166">長時間実行のときに、照合エージェントによってログ リーダー エージェントに SUSPECT とマークされないようにするには、この値を小さくします。</span><span class="sxs-lookup"><span data-stu-id="53bcf-166">This value can be decreased to avoid having the checkup agent mark the Log Reader Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="53bcf-167">既定では 300 秒です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-167">The default is 300 seconds.</span></span>  
  
 <span data-ttu-id="53bcf-168">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="53bcf-168">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="53bcf-169">ログインがタイムアウトになるまでの秒数です。既定値は 15 秒です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-169">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="53bcf-170">**-LogScanThreshold** _scan_threshold_</span><span class="sxs-lookup"><span data-stu-id="53bcf-170">**-LogScanThreshold** _scan_threshold_</span></span>  
 <span data-ttu-id="53bcf-171">内部使用のみです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-171">Internal use only.</span></span>  
  
 <span data-ttu-id="53bcf-172">**-MaxCmdsInTran** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="53bcf-172">**-MaxCmdsInTran** _number_of_commands_</span></span>  
 <span data-ttu-id="53bcf-173">ログ リーダーがディストリビューション データベースにコマンドを書き込む際に、トランザクションにグループ化されるステートメントの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-173">Specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="53bcf-174">このパラメーターを使用すると、ログ リーダー エージェントおよびディストリビューション エージェントは、サブスクライバーでコマンドを適用するときに、パブリッシャーで (多数のコマンドで構成される) 大きなトランザクションを複数の小さなトランザクションに分割できます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-174">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applied at the Subscriber.</span></span> <span data-ttu-id="53bcf-175">このパラメーターを指定すると、ディストリビューターでの競合を減らし、パブリッシャーとサブスクライバーの間の待機時間を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-175">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="53bcf-176">元のトランザクションはより小さな単位で適用されるため、サブスクライバーは元のトランザクションが終了する前に、大きな論理パブリッシャー トランザクションの行にアクセスし、トランザクションの厳密な原子性を損なうことがあります。</span><span class="sxs-lookup"><span data-stu-id="53bcf-176">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="53bcf-177">既定値は **0**です。この場合、パブリッシャーのトランザクション境界が保護されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-177">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53bcf-178">このパラメーターは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリケーション以外では無視されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-178">This parameter is ignored for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publications.</span></span> <span data-ttu-id="53bcf-179">詳細については、「 [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)」の「トランザクション セット ジョブの構成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bcf-179">For more information, see the section "Configuring the Transaction Set Job" in [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
 <span data-ttu-id="53bcf-180">**-MessageInterval** _message_interval_</span><span class="sxs-lookup"><span data-stu-id="53bcf-180">**-MessageInterval** _message_interval_</span></span>  
 <span data-ttu-id="53bcf-181">履歴をログに記録する間隔です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-181">Is the time interval used for history logging.</span></span> <span data-ttu-id="53bcf-182">最後の履歴イベントがログに記録された後で **MessageInterval** 値に到達すると、次の履歴イベントがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-182">A history event is logged when the **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="53bcf-183">ソースに利用可能なレプリケートされたトランザクションがない場合、エージェントはディストリビューターに対してトランザクションなしのメッセージを報告します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-183">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="53bcf-184">このオプションは、エージェントが次にトランザクションなしのメッセージを報告するまでの待ち時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-184">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="53bcf-185">前回レプリケートされたトランザクションを処理した後で、ソースに利用可能なトランザクションがないことを検出すると、エージェントは必ずトランザクションなしのメッセージを報告します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-185">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="53bcf-186">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-186">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="53bcf-187">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="53bcf-187">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="53bcf-188">エージェントの出力ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-188">Is the path of the agent output file.</span></span> <span data-ttu-id="53bcf-189">ファイル名が指定されていない場合、出力はコンソールに送られます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-189">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="53bcf-190">指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-190">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="53bcf-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span><span class="sxs-lookup"><span data-stu-id="53bcf-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span></span>  
 <span data-ttu-id="53bcf-192">出力を詳細表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-192">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="53bcf-193">値</span><span class="sxs-lookup"><span data-stu-id="53bcf-193">Value</span></span>|<span data-ttu-id="53bcf-194">説明</span><span class="sxs-lookup"><span data-stu-id="53bcf-194">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="53bcf-195">**0**</span><span class="sxs-lookup"><span data-stu-id="53bcf-195">**0**</span></span>|<span data-ttu-id="53bcf-196">エラー メッセージのみが記録されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-196">Only error messages are printed.</span></span>|  
|<span data-ttu-id="53bcf-197">**1**</span><span class="sxs-lookup"><span data-stu-id="53bcf-197">**1**</span></span>|<span data-ttu-id="53bcf-198">すべてのエージェント進行状況レポート メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-198">All agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="53bcf-199">**2** (既定値)</span><span class="sxs-lookup"><span data-stu-id="53bcf-199">**2** (default)</span></span>|<span data-ttu-id="53bcf-200">すべてのエラー メッセージおよびエージェント進行状況レポート メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-200">All error messages and agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="53bcf-201">**3**</span><span class="sxs-lookup"><span data-stu-id="53bcf-201">**3**</span></span>|<span data-ttu-id="53bcf-202">レプリケートされた各コマンドの最初の 100 バイトが出力されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-202">The first 100 bytes of each replicated command are printed.</span></span>|  
|<span data-ttu-id="53bcf-203">**4**</span><span class="sxs-lookup"><span data-stu-id="53bcf-203">**4**</span></span>|<span data-ttu-id="53bcf-204">すべてのレプリケートされたコマンドが出力されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-204">All replicated commands are printed.</span></span>|  
  
 <span data-ttu-id="53bcf-205">値 2 ～ 4 はデバッグ時に有用です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-205">Values 2-4 are useful when debugging.</span></span>  
  
 <span data-ttu-id="53bcf-206">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="53bcf-206">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="53bcf-207">パケット サイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-207">Is the packet size, in bytes.</span></span> <span data-ttu-id="53bcf-208">既定値は 4096 (バイト) です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-208">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="53bcf-209">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="53bcf-209">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="53bcf-210">ログを対象としてレプリケートされたトランザクションをクエリする間隔を表す秒単位の値です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-210">Is how often, in seconds, the log is queried for replicated transactions.</span></span> <span data-ttu-id="53bcf-211">既定値は 5 秒です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-211">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="53bcf-212">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="53bcf-212">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="53bcf-213">エージェント パラメーターに使用するエージェント プロファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-213">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="53bcf-214">**ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="53bcf-214">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="53bcf-215">**ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-215">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="53bcf-216">詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bcf-216">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="53bcf-217">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="53bcf-217">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="53bcf-218">パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-218">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="53bcf-219">詳細については、「 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="53bcf-219">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="53bcf-220">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="53bcf-220">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="53bcf-221">パブリッシャーのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-221">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="53bcf-222">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-222">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="53bcf-223">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="53bcf-223">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="53bcf-224">パブリッシャーのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-224">Is the Publisher login name.</span></span>  
  
 <span data-ttu-id="53bcf-225">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="53bcf-225">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="53bcf-226">パブリッシャーのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="53bcf-226">Is the Publisher password.</span></span>  
  
 <span data-ttu-id="53bcf-227">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="53bcf-227">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="53bcf-228">クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-228">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="53bcf-229">**-ReadBatchSize** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="53bcf-229">**-ReadBatchSize** _number_of_transactions_</span></span>  
 <span data-ttu-id="53bcf-230">パブリッシング データベースのトランザクション ログから読み取られるトランザクションの処理サイクルあたりの最大数であり、既定値は 500 です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-230">Is the maximum number of transactions read out of the transaction log of the publishing database per processing cycle, with a default of 500.</span></span> <span data-ttu-id="53bcf-231">エージェントは、すべてのトランザクションをログから読み取るまで、トランザクションの読み取りをバッチ処理で継続します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-231">The agent will continue to read transactions in batches until all transactions are read from the log.</span></span> <span data-ttu-id="53bcf-232">このパラメーターは、Oracle パブリッシャーに対してサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="53bcf-232">This parameter is not supported for Oracle Publishers.</span></span>  
  
 <span data-ttu-id="53bcf-233">**-ReadBatchThreshold** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="53bcf-233">**-ReadBatchThreshold** _number_of_commands_</span></span>  
 <span data-ttu-id="53bcf-234">ディストリビューション エージェントによってサブスクライバーに発行される前に、トランザクション ログから読み取られるレプリケーション コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-234">Is the number of replication commands to be read from the transaction log before being issued to the Subscriber by the Distribution Agent.</span></span> <span data-ttu-id="53bcf-235">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-235">The default is 0.</span></span> <span data-ttu-id="53bcf-236">このパラメーターが指定されていない場合、ログ リーダー エージェントは、ログの最後まで読み取るか、または **-ReadBatchSize** (トランザクション数) で指定された数だけ読み取ります。</span><span class="sxs-lookup"><span data-stu-id="53bcf-236">If this parameter is not specified, the Log Reader Agent will read to the end of the log or to the number specified in **-ReadBatchSize** (number of transactions).</span></span>  
  
 <span data-ttu-id="53bcf-237">**-RecoverFromDataErrors**</span><span class="sxs-lookup"><span data-stu-id="53bcf-237">**-RecoverFromDataErrors**</span></span>  
 <span data-ttu-id="53bcf-238">SQL Server 以外のパブリッシャーからパブリッシュされる列データでエラーが発生しても、ログ リーダー エージェントを継続して実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-238">Specifies that the Log Reader Agent continue to run when it encounters errors in column data published from a non-SQL Server Publisher.</span></span> <span data-ttu-id="53bcf-239">既定では、このようなエラーが発生するとログ リーダー エージェントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-239">By default, such errors cause the Log Reader Agent to fail.</span></span> <span data-ttu-id="53bcf-240">**-RecoverFromDataErrors**を使用する場合、エラーのある列データは NULL または適切な NULL 以外の値としてレプリケートされ、警告メッセージが [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) テーブルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-240">When you use **-RecoverFromDataErrors**, erroneous column data is replicated either as NULL or an appropriate nonnull value, and warning messages are logged to the [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) table.</span></span> <span data-ttu-id="53bcf-241">このパラメーターは、Oracle パブリッシャーに対してのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-241">This parameter is only supported for Oracle Publishers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53bcf-242">解説</span><span class="sxs-lookup"><span data-stu-id="53bcf-242">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="53bcf-243">ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントをインストールした場合、サービスはローカル コンピューターにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="53bcf-243">If you installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account instead of under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="53bcf-244">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントから実行されるログ リーダー エージェントで、Windows 認証モードを使用するように構成すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]へのログイン時にログ リーダー エージェントは異常終了します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-244">If the Log Reader Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Log Reader Agent fails.</span></span> <span data-ttu-id="53bcf-245">既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。</span><span class="sxs-lookup"><span data-stu-id="53bcf-245">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="53bcf-246">セキュリティ アカウント変更の詳細については、「 [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bcf-246">For information about changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="53bcf-247">ログ リーダー エージェントを開始するには、コマンド プロンプトから **logread.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="53bcf-247">To start the Log Reader Agent, execute **logread.exe** from the command prompt.</span></span> <span data-ttu-id="53bcf-248">詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bcf-248">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="53bcf-249">変更履歴</span><span class="sxs-lookup"><span data-stu-id="53bcf-249">Change History</span></span>  
  
|<span data-ttu-id="53bcf-250">変更内容</span><span class="sxs-lookup"><span data-stu-id="53bcf-250">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="53bcf-251">**-ExtendedEventConfigFile** パラメーターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="53bcf-251">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53bcf-252">参照</span><span class="sxs-lookup"><span data-stu-id="53bcf-252">See Also</span></span>  
 [<span data-ttu-id="53bcf-253">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="53bcf-253">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
