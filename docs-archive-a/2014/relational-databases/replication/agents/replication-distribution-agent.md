---
title: レプリケーション ディストリビューション エージェント | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distribution Agent, executables
- agents [SQL Server replication], Distribution Agent
- Distribution Agent, parameter reference
- command prompt [SQL Server replication]
ms.assetid: 7b4fd480-9eaf-40dd-9a07-77301e44e2ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5bd0b61626f4af268f93043114d5945d00a37b5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640885"
---
# <a name="replication-distribution-agent"></a><span data-ttu-id="5ed62-102">レプリケーション ディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="5ed62-102">Replication Distribution Agent</span></span>
  <span data-ttu-id="5ed62-103">レプリケーション ディストリビューション エージェントは、ディストリビューション データベース テーブルに登録されたスナップショット (スナップショット レプリケーションの場合) とトランザクション (トランザクション レプリケーションの場合) を、サブスクライバーのレプリケーション先のテーブルに移動する実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-103">The Replication Distribution Agent is an executable that moves the snapshot (for snapshot replication and transactional replication) and the transactions held in the distribution database tables (for transactional replication) to the destination tables at the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ed62-104">パラメーターは任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="5ed62-105">省略可能なパラメーターを省略する場合、ローカル コンピューターであらかじめ定義されているレジストリ設定の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-105">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed62-106">構文</span><span class="sxs-lookup"><span data-stu-id="5ed62-106">Syntax</span></span>  
  
```  
  
      distrib [-?]  
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database   
[-AltSnapshotFolderalt_snapshot_folder_path]   
[-BcpBatchSizebcp_batch_size]  
[-CommitBatchSizecommit_batch_size]  
[-CommitBatchThresholdcommit_batch_threshold]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributordistributor]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ErrorFileerror_path_and_file_name]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-FileTransferType [0|1]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]   
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreads]  
[-MaxDeliveredTransactionsnumber_of_transactions]  
[-MessageIntervalmessage_interval]  
[-OledbStreamThresholdoledb_stream_threshold]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-Publicationpublication]  
[-QueryTimeOutquery_time_out_seconds]  
[-QuotedIdentifierquoted_identifier]  
[-SkipErrorsnative_error_id [:...n]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password]  
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|3]]  
[-SubscriptionStreams [1|2|...64]]  
[-SubscriptionTableNamesubscription_table]  
[-SubscriptionType [0|1|2]]  
[-TransactionsPerHistory [0|1|...10000]]  
[-UseDTS]  
[-UseInprocLoader]  
[-UseOledbStreaming]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ed62-107">引数</span><span class="sxs-lookup"><span data-stu-id="5ed62-107">Arguments</span></span>  
 <span data-ttu-id="5ed62-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="5ed62-108">**-?**</span></span>  
 <span data-ttu-id="5ed62-109">使用できるすべてのパラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-109">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="5ed62-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="5ed62-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="5ed62-111">パブリッシャーの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-111">Is the name of the Publisher.</span></span> <span data-ttu-id="5ed62-112">サーバー上の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、*server_name* を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="5ed62-113">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="5ed62-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="5ed62-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="5ed62-115">パブリッシャー データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="5ed62-116">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="5ed62-116">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="5ed62-117">サブスクライバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-117">Is the name of the Subscriber.</span></span> <span data-ttu-id="5ed62-118">サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-118">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="5ed62-119">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-119">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="5ed62-120">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="5ed62-120">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="5ed62-121">サブスクライバー データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-121">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="5ed62-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="5ed62-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="5ed62-123">サブスクリプションの初期スナップショットが含まれるフォルダーへのパスです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-123">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="5ed62-124">**-BcpBatchSize** _bcp_batch_size_</span><span class="sxs-lookup"><span data-stu-id="5ed62-124">**-BcpBatchSize** _bcp_batch_size_</span></span>  
 <span data-ttu-id="5ed62-125">一括コピー操作によって送られる行の数です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-125">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="5ed62-126">**bcp in** 操作を実行する場合、バッチ サイズは 1 つのトランザクションとしてサーバーに送る行数です。ディストリビューション エージェントが **bcp** 実行状況メッセージをログに記録する前に、これらの行数を送る必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-126">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="5ed62-127">**bcp out** 操作を実行する場合は、固定バッチ サイズ **1000** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-127">When performing a **bcp out** operation, a fixed batch size of **1000** is used.</span></span>  
  
 <span data-ttu-id="5ed62-128">**-CommitBatchSize** _commit_batch_size_</span><span class="sxs-lookup"><span data-stu-id="5ed62-128">**-CommitBatchSize** _commit_batch_size_</span></span>  
 <span data-ttu-id="5ed62-129">COMMIT ステートメントを実行する前に、サブスクライバーに対して実行するトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-129">Is the number of transactions to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="5ed62-130">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-130">The default is 100.</span></span>  
  
 <span data-ttu-id="5ed62-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span><span class="sxs-lookup"><span data-stu-id="5ed62-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span></span>  
 <span data-ttu-id="5ed62-132">COMMIT ステートメントを実行する前に、サブスクライバーに対して実行するレプリケーション コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-132">Is the number of replication commands to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="5ed62-133">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-133">The default is 1000.</span></span>  
  
 <span data-ttu-id="5ed62-134">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="5ed62-134">**-Continuous**</span></span>  
 <span data-ttu-id="5ed62-135">エージェントがレプリケートされたトランザクションの呼び出しを継続的に試みるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-135">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="5ed62-136">このパラメーターを指定する場合、保留されているトランザクションがなくても、エージェントはポーリング間隔でレプリケートされたトランザクションをソースから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-136">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="5ed62-137">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-137">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="5ed62-138">エージェント定義ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-138">Is the path of the agent definition file.</span></span> <span data-ttu-id="5ed62-139">エージェント定義ファイルには、エージェントのコマンド プロンプト引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-139">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="5ed62-140">ファイルの内容は実行可能ファイルとして解析されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-140">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="5ed62-141">二重引用符 (") を使用して、任意の文字を含む引数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-141">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="5ed62-142">**-Distributor** _distributor_</span><span class="sxs-lookup"><span data-stu-id="5ed62-142">**-Distributor** _distributor_</span></span>  
 <span data-ttu-id="5ed62-143">ディストリビューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-143">Is the Distributor name.</span></span> <span data-ttu-id="5ed62-144">ディストリビューター (プッシュ) ディストリビューションの場合、既定値はローカル ディストリビューターの名前になります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-144">For Distributor (push) distribution, the name defaults to the name of the local Distributor.</span></span>  
  
 <span data-ttu-id="5ed62-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="5ed62-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="5ed62-146">ディストリビューターのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="5ed62-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="5ed62-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="5ed62-148">ディストリビューターのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="5ed62-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5ed62-150">ディストリビューターのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="5ed62-151">値 0 は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モードを指定し、値 1 は Windows 認証モード (既定値) を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-151">A value of 0 indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode, and a value of 1 indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="5ed62-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="5ed62-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="5ed62-153">接続確立時にディストリビューション エージェントが使用する SSL (Secure Sockets Layer) の暗号化レベルです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-153">Is the level of Secure Sockets Layer (SSL) encryption used by the Distribution Agent when making connections.</span></span>  
  
|<span data-ttu-id="5ed62-154">EncryptionLevel の値</span><span class="sxs-lookup"><span data-stu-id="5ed62-154">EncryptionLevel value</span></span>|<span data-ttu-id="5ed62-155">説明</span><span class="sxs-lookup"><span data-stu-id="5ed62-155">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="5ed62-156">**0**</span><span class="sxs-lookup"><span data-stu-id="5ed62-156">**0**</span></span>|<span data-ttu-id="5ed62-157">SSL は使用されません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-157">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="5ed62-158">**1**</span><span class="sxs-lookup"><span data-stu-id="5ed62-158">**1**</span></span>|<span data-ttu-id="5ed62-159">SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-159">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="5ed62-160">**2**</span><span class="sxs-lookup"><span data-stu-id="5ed62-160">**2**</span></span>|<span data-ttu-id="5ed62-161">SSL が使用され、証明書の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-161">Specifies that SSL is used, and that the certificate is verified.</span></span>|  
 
 > [!NOTE]  
 >  <span data-ttu-id="5ed62-162">有効な SSL 証明書には、SQL Server の完全修飾ドメイン名が定義されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-162">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="5ed62-163">-EncryptionLevel を 2 に設定したときにエージェントが正しく接続されるようにするには、ローカルの SQL Server 上に別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-163">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="5ed62-164">'Alias Name' パラメーターはサーバー名にし、'Server' パラメーターは SQL Server の完全修飾名に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-164">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>

 <span data-ttu-id="5ed62-165">詳細については、「 [SQL Server レプリケーションセキュリティ](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-165">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="5ed62-166">**-ErrorFile** _error_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-166">**-ErrorFile** _error_path_and_file_name_</span></span>  
 <span data-ttu-id="5ed62-167">ディストリビューション エージェントが作成するエラー ファイルのパスとファイル名です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-167">Is the path and file name of the error file generated by the Distribution Agent.</span></span> <span data-ttu-id="5ed62-168">このファイルは、サブスクライバーでレプリケーション トランザクションを適用しているときに、エラーが発生すると生成されます。パブリッシャーまたはディストリビューターで発生したエラーについては、このファイルには記録されません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-168">This file is generated at any point where failure occurred while applying replication transactions at the Subscriber; errors that occur at the Publisher or Distributor are not logged in this file.</span></span> <span data-ttu-id="5ed62-169">このファイルには、障害が発生したレプリケーション トランザクションおよび関連するエラー メッセージが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-169">This file contains the failed replication transactions and associated error messages.</span></span> <span data-ttu-id="5ed62-170">指定しない場合は、エラー ファイルはディストリビューション エージェントの現在のディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-170">When not specified, the error file is generated in the current directory of the Distribution Agent.</span></span> <span data-ttu-id="5ed62-171">エラー ファイル名は、ディストリビューション エージェントの名前に .err 拡張子を付けた名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-171">The error file name is the name of the Distribution Agent with an .err extension.</span></span> <span data-ttu-id="5ed62-172">指定したファイル名が既存の場合、エラー メッセージはこのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-172">If the specified file name exists, error messages are appended to the file.</span></span> <span data-ttu-id="5ed62-173">このパラメーターには最大 256 個の Unicode 文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-173">This parameter can be a maximum of 256 Unicode characters.</span></span>  
  
 <span data-ttu-id="5ed62-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="5ed62-175">拡張イベントの XML 構成ファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-175">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="5ed62-176">拡張イベントの構成ファイルによって、追跡に必要なセッションを構成し、イベントを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-176">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="5ed62-177">**-FileTransferType** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-177">**-FileTransferType** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5ed62-178">ファイル転送の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-178">Specifies the file transfer type.</span></span> <span data-ttu-id="5ed62-179">**0** の値は UNC (汎用名前付け規則) を示し、 **1** の値は FTP (ファイル転送プロトコル) を示します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-179">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="5ed62-180">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="5ed62-180">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="5ed62-181">ディストリビューター用の FTP サービスのネットワーク アドレスです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-181">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="5ed62-182">このパラメーターを指定しない場合、 **DistributorAddress** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-182">When not specified, **DistributorAddress** is used.</span></span> <span data-ttu-id="5ed62-183">**DistributorAddress** が指定されていない場合、 **Distributor** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-183">If **DistributorAddress** is not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="5ed62-184">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="5ed62-184">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="5ed62-185">FTP サービスに接続するときに使用するユーザー パスワードです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-185">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="5ed62-186">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="5ed62-186">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="5ed62-187">ディストリビューター用の FTP サービスのポート番号です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-187">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="5ed62-188">このパラメーターを指定しない場合、FTP サービスの既定のポート番号 (21) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-188">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="5ed62-189">**-FtpUserName**  _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-189">**-FtpUserName**  _ftp_user_name_</span></span>  
 <span data-ttu-id="5ed62-190">FTP サービスに接続するときに使用するユーザー名です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-190">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="5ed62-191">指定しない場合、 **anonymous** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-191">When not specified, **anonymous** is used.</span></span>  
  
 <span data-ttu-id="5ed62-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span><span class="sxs-lookup"><span data-stu-id="5ed62-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span></span>  
 <span data-ttu-id="5ed62-193">ディストリビューション操作中にログに記録する履歴の量を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-193">Specifies the amount of history logged during a distribution operation.</span></span> <span data-ttu-id="5ed62-194">**1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-194">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="5ed62-195">HistoryVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="5ed62-195">HistoryVerboseLevel value</span></span>|<span data-ttu-id="5ed62-196">説明</span><span class="sxs-lookup"><span data-stu-id="5ed62-196">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="5ed62-197">**0**</span><span class="sxs-lookup"><span data-stu-id="5ed62-197">**0**</span></span>|<span data-ttu-id="5ed62-198">進行状況メッセージがコンソールまたは出力ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-198">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="5ed62-199">履歴レコードは、ディストリビューション データベースのログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-199">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="5ed62-200">**1**</span><span class="sxs-lookup"><span data-stu-id="5ed62-200">**1**</span></span>|<span data-ttu-id="5ed62-201">既定値。</span><span class="sxs-lookup"><span data-stu-id="5ed62-201">Default.</span></span> <span data-ttu-id="5ed62-202">同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-202">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="5ed62-203">前回の記録に同じ状態がない場合は、新しい記録を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-203">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="5ed62-204">**2**</span><span class="sxs-lookup"><span data-stu-id="5ed62-204">**2**</span></span>|<span data-ttu-id="5ed62-205">アイドル状態や長時間実行を示すメッセージでない場合、新しい履歴レコードを挿入します。アイドル状態などを示すメッセージの場合には、以前のレコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-205">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="5ed62-206">**3**</span><span class="sxs-lookup"><span data-stu-id="5ed62-206">**3**</span></span>|<span data-ttu-id="5ed62-207">アイドル状態を示すメッセージの場合以外は、常に新しいレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-207">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="5ed62-208">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-208">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="5ed62-209">パブリッシャーとの接続時に使用するホスト名です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-209">Is the host name used when connecting to the Publisher.</span></span> <span data-ttu-id="5ed62-210">このパラメーターには最大 128 個の Unicode 文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-210">This parameter can be a maximum of 128 Unicode characters.</span></span>  
  
 <span data-ttu-id="5ed62-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="5ed62-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="5ed62-212">既存の接続がサーバーからの応答を待機しているかどうかを、履歴スレッドがチェックするまでの秒数です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-212">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="5ed62-213">この値を小さくすれば、ディストリビューション エージェントが時間のかかるバッチを実行しているとき、照合エージェントによって SUSPECT とマークされるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-213">This value can be decreased to avoid having the checkup agent mark the Distribution Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="5ed62-214">既定値は **300** 秒です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-214">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="5ed62-215">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="5ed62-215">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="5ed62-216">ログインがタイムアウトになるまでの秒数です。既定値は **15** 秒です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-216">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="5ed62-217">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="5ed62-217">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="5ed62-218">並列実行できる一括コピーの操作数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-218">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="5ed62-219">同時に存在するスレッドと ODBC 接続の最大数は、 **MaxBcpThreads** の値と、ディストリビューション データベースの同期トランザクションに示されている一括コピー要求の数の小さい方の値になります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-219">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="5ed62-220">**MaxBcpThreads** は **0** よりも大きくする必要があり、上限はありません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-220">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="5ed62-221">既定値は、プロセッサ数の **2** 倍の値です。最大値は、 **8**になります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-221">The default is **2** times the number of processors, up to a maximum value of **8**.</span></span> <span data-ttu-id="5ed62-222">パブリッシャー側で同時実行スナップショット オプションを使って生成されたスナップショットを適用する場合は、 **MaxBcpThreads**に指定した値に関係なく、単一のスレッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-222">When applying a snapshot that was generated at the Publisher using the concurrent snapshot option, one thread is used, regardless of the number you specify for **MaxBcpThreads**.</span></span>  
  
 <span data-ttu-id="5ed62-223">**-MaxDeliveredTransactions** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="5ed62-223">**-MaxDeliveredTransactions** _number_of_transactions_</span></span>  
 <span data-ttu-id="5ed62-224">1 回の同期でサブスクライバーに適用するプッシュまたはプル トランザクションの最大数です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-224">Is the maximum number of push or pull transactions applied to Subscribers in one synchronization.</span></span> <span data-ttu-id="5ed62-225">値 **0** は、トランザクション数に制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-225">A value of **0** indicates that the maximum is an infinite number of transactions.</span></span> <span data-ttu-id="5ed62-226">その他の値は、サブスクライバーがパブリッシャーからプルする同期の経過時間を短縮するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-226">Other values can be used by Subscribers to shorten the duration of a synchronization being pulled from a Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ed62-227">-MaxDeliveredTransactions と -Continuous を両方とも指定すると、ディストリビューション エージェントは、指定した数のトランザクションを配信してから、停止します (-Continuous が指定されている場合であっても)。</span><span class="sxs-lookup"><span data-stu-id="5ed62-227">If -MaxDeliveredTransactions and -Continuous are both specified, the Distribution Agent delivers the specified number of transactions and then stops (even though -Continuous is specified).</span></span> <span data-ttu-id="5ed62-228">ジョブが完了した後、ディストリビューション エージェントを再起動してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-228">You must restart the Distribution Agent after the job completes.</span></span>  
  
 <span data-ttu-id="5ed62-229">**-MessageInterval**  _message_interval_</span><span class="sxs-lookup"><span data-stu-id="5ed62-229">**-MessageInterval**  _message_interval_</span></span>  
 <span data-ttu-id="5ed62-230">履歴をログに記録する間隔です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-230">Is the time interval used for history logging.</span></span> <span data-ttu-id="5ed62-231">次のいずれかの場合、履歴イベントはログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-231">A history event is logged when one of these parameters is reached:</span></span>  
  
-   <span data-ttu-id="5ed62-232">最後の履歴イベントをログに記録した後、 **TransactionsPerHistory** の値が経過した場合</span><span class="sxs-lookup"><span data-stu-id="5ed62-232">The **TransactionsPerHistory** value is reached after the last history event is logged.</span></span>  
  
-   <span data-ttu-id="5ed62-233">最後の履歴イベントをログに記録した後、 **MessageInterval** の値が経過した場合</span><span class="sxs-lookup"><span data-stu-id="5ed62-233">The **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="5ed62-234">ソースに利用可能なレプリケートされたトランザクションがない場合、エージェントはディストリビューターに対してトランザクションなしのメッセージを報告します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-234">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="5ed62-235">このオプションは、エージェントが次にトランザクションなしのメッセージを報告するまでの待ち時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-235">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="5ed62-236">前回レプリケートされたトランザクションを処理した後で、ソースに利用可能なトランザクションがないことを検出すると、エージェントは必ずトランザクションなしのメッセージを報告します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-236">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="5ed62-237">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-237">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="5ed62-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span><span class="sxs-lookup"><span data-stu-id="5ed62-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span></span>  
 <span data-ttu-id="5ed62-239">BLOB データの最小バイト サイズを指定します。この値を超えると、データはストリームとしてバインドされます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-239">Specifies the minimum size, in bytes, for binary large object data above which the data will be bound as a stream.</span></span> <span data-ttu-id="5ed62-240">このパラメーターを使用するためには、 **-UseOledbStreaming** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-240">You must specify **-UseOledbStreaming** to use this parameter.</span></span> <span data-ttu-id="5ed62-241">400 バイトから 1048576 バイトまでの値を指定できます。既定値は 16384 バイトです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-241">Values can range from 400 to 1048576 bytes, with a default of 16384 bytes.</span></span>  
  
 <span data-ttu-id="5ed62-242">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-242">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="5ed62-243">エージェントの出力ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-243">Is the path of the agent output file.</span></span> <span data-ttu-id="5ed62-244">ファイル名が指定されていない場合、出力はコンソールに送られます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-244">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="5ed62-245">指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-245">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="5ed62-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="5ed62-247">出力を詳細表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-247">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="5ed62-248">詳細レベルが **0**の場合、エラー メッセージだけが出力されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-248">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="5ed62-249">詳細レベルが **1**の場合、すべての実行状況報告メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-249">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="5ed62-250">詳細レベルが **2** (既定値) の場合、すべてのエラー メッセージと実行状況報告メッセージが出力されます。これはデバッグ時に便利です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-250">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="5ed62-251">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="5ed62-251">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="5ed62-252">パケット サイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-252">Is the packet size, in bytes.</span></span> <span data-ttu-id="5ed62-253">既定値は 4096 (バイト) です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-253">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="5ed62-254">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="5ed62-254">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="5ed62-255">レプリケートされたトランザクションに関してディストリビューション データベースをクエリする間隔を秒単位で示します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-255">Is how often, in seconds, the distribution database is queried for replicated transactions.</span></span> <span data-ttu-id="5ed62-256">既定値は 5 秒です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-256">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="5ed62-257">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="5ed62-257">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="5ed62-258">エージェント パラメーターに使用するエージェント プロファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-258">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="5ed62-259">**ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-259">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="5ed62-260">**ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-260">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="5ed62-261">詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-261">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="5ed62-262">**-Publication**  _publication_</span><span class="sxs-lookup"><span data-stu-id="5ed62-262">**-Publication**  _publication_</span></span>  
 <span data-ttu-id="5ed62-263">パブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-263">Is the name of the publication.</span></span> <span data-ttu-id="5ed62-264">このパラメーターは、新規または再初期化されたサブスクリプションのスナップショットを常に利用できるようにパブリケーションを設定している場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-264">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="5ed62-265">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="5ed62-265">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="5ed62-266">クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-266">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="5ed62-267">**-QuotedIdentifier** _quoted_identifier_</span><span class="sxs-lookup"><span data-stu-id="5ed62-267">**-QuotedIdentifier** _quoted_identifier_</span></span>  
 <span data-ttu-id="5ed62-268">使用する引用符で囲まれた識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-268">Specifies the quoted identifier character to use.</span></span> <span data-ttu-id="5ed62-269">値の最初の文字は、ディストリビューション エージェントが使用する値を示します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-269">The first character of the value indicates the value the Distribution Agent uses.</span></span> <span data-ttu-id="5ed62-270">値を指定せずに **QuotedIdentifier** を使用する場合、ディストリビューション エージェントはスペースを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-270">If **QuotedIdentifier** is used with no value, the Distribution Agent uses a space.</span></span> <span data-ttu-id="5ed62-271">**QuotedIdentifier** を使用しない場合には、ディストリビューション エージェントはサブスクライバーがサポートしている引用符で囲まれた識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-271">If **QuotedIdentifier** is not used, the Distribution Agent uses whatever quoted identifier the Subscriber supports.</span></span>  
  
 <span data-ttu-id="5ed62-272">**-SkipErrors** _native_error_id_ [ **:** _...n_]</span><span class="sxs-lookup"><span data-stu-id="5ed62-272">**-SkipErrors** _native_error_id_ [**:**_...n_]</span></span>  
 <span data-ttu-id="5ed62-273">このエージェントでスキップされる一連のエラー番号をコロンで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-273">Is a colon-separated list that specifies the error numbers to be skipped by this agent.</span></span>  
  
 <span data-ttu-id="5ed62-274">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="5ed62-274">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="5ed62-275">**SubscriberType** が **2** の場合、Jet データベース (.mdb) ファイルへのパスを指定します。この指定では、ODBC データ ソース名 (DSN) なしで Jet データベースに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-275">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="5ed62-276">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="5ed62-276">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="5ed62-277">サブスクライバーのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-277">Is the Subscriber login name.</span></span> <span data-ttu-id="5ed62-278">**SubscriberSecurityMode** が **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード) の場合は、このパラメーターを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-278">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="5ed62-279">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="5ed62-279">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="5ed62-280">サブスクライバーのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="5ed62-280">Is the Subscriber password.</span></span> <span data-ttu-id="5ed62-281">**SubscriberSecurityMode** が **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード) の場合は、このパラメーターを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-281">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="5ed62-282">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-282">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="5ed62-283">サブスクライバーのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-283">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="5ed62-284">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モードを指定し、値 **1** は Windows 認証モード (既定値) を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-284">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, and a value of **1** indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="5ed62-285">**-SubscriberType** [ **0**| **1**| **3**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-285">**-SubscriberType** [ **0**| **1**| **3**]</span></span>  
 <span data-ttu-id="5ed62-286">ディストリビューション エージェントが使用するサブスクライバー接続の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-286">Specifies the type of Subscriber connection used by the Distribution Agent.</span></span>  
  
|<span data-ttu-id="5ed62-287">サブスクライバーの種類</span><span class="sxs-lookup"><span data-stu-id="5ed62-287">SubscriberType value</span></span>|<span data-ttu-id="5ed62-288">説明</span><span class="sxs-lookup"><span data-stu-id="5ed62-288">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="5ed62-289">**0**</span><span class="sxs-lookup"><span data-stu-id="5ed62-289">**0**</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="5ed62-290">**1**</span><span class="sxs-lookup"><span data-stu-id="5ed62-290">**1**</span></span>|<span data-ttu-id="5ed62-291">ODBC データ ソース (ODBC data source)</span><span class="sxs-lookup"><span data-stu-id="5ed62-291">ODBC data source</span></span>|  
|<span data-ttu-id="5ed62-292">**3**</span><span class="sxs-lookup"><span data-stu-id="5ed62-292">**3**</span></span>|<span data-ttu-id="5ed62-293">OLE DB データ ソース</span><span class="sxs-lookup"><span data-stu-id="5ed62-293">OLE DB data source</span></span>|  
  
 <span data-ttu-id="5ed62-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span></span>  
 <span data-ttu-id="5ed62-295">単一のスレッドを使用しているときに、トランザクションに関連したさまざまな特性を維持しながら、サブスクライバーに対してバッチ変更を適用することのできる、ディストリビューション エージェントあたりの接続数です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-295">Is the number of connections allowed per Distribution Agent to apply batches of changes in parallel to a Subscriber, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="5ed62-296">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーの場合、1 から 64 までの値がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-296">For a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, a range of values from 1 to 64 is supported.</span></span> <span data-ttu-id="5ed62-297">このパラメーターは、パブリッシャーとディストリビューターが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで実行されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-297">This parameter is only supported when the Publisher and Distributor are running on [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later versions.</span></span> <span data-ttu-id="5ed62-298">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーまたはピア ツー ピア サブスクリプションの場合は、このパラメーターを使用しないか、0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-298">This parameter is not supported or must be 0 for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers or peer-to-peer subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ed62-299">いずれかの接続が実行またはコミットに失敗した場合、進行中のバッチがすべての接続について中止されます。その場合、エージェントは、単一のストリームを使用して、失敗したバッチを再試行します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-299">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="5ed62-300">この再試行フェーズが完了するまでは、サブスクライバー側に、トランザクションの一時的な不整合が存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-300">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="5ed62-301">サブスクライバーのトランザクション一貫性は、前回失敗したバッチが正常にコミットされた後で復元されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-301">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5ed62-302">**-SubscriptionStreams**に対して 2 以上の値を指定すると、サブスクライバー側でトランザクションが受信される順序が、パブリッシャー側でトランザクションが作成された順序と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-302">When you specify a value of 2 or greater for **-SubscriptionStreams**, the order in which transactions are received at the Subscriber may differ from the order in which they were made at the Publisher.</span></span> <span data-ttu-id="5ed62-303">この動作が原因で同期中に制約違反が発生する場合は、NOT FOR REPLICATION オプションを使用して同期中の制約の適用を無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-303">If this behavior causes constraint violations during synchronization, you should use the NOT FOR REPLICATION option to disable the enforcement of constraints during synchronization.</span></span> <span data-ttu-id="5ed62-304">詳細については、「[同期中にトリガと制約の動作を制御する方法 &#40;レプリケーション Transact-SQL プログラミング&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-304">For more information, see [Control the Behavior of Triggers and Constraints During Synchronization &#40;Replication Transact-SQL Programming&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ed62-305">Subscriptionstreams は、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]を渡すように構成されたアーティクルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-305">Subscriptionstreams do not work for articles configured to deliver [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5ed62-306">subscriptionstreams を使用するには、代わりにストアド プロシージャの呼び出しを渡すようにアーティクルを構成します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-306">To use subscriptionstreams, configure articles to deliver stored procedure calls instead.</span></span>  
  
 <span data-ttu-id="5ed62-307">**-SubscriptionTableName** _subscription_table_</span><span class="sxs-lookup"><span data-stu-id="5ed62-307">**-SubscriptionTableName** _subscription_table_</span></span>  
 <span data-ttu-id="5ed62-308">指定したサブスクライバーで作成または使用するサブスクリプション テーブルの名前です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-308">Is the name of the subscription table generated or used at the given Subscriber.</span></span> <span data-ttu-id="5ed62-309">指定しない場合、[MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) テーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-309">When not specified, the [MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) table is used.</span></span> <span data-ttu-id="5ed62-310">長いファイル名をサポートしないデータベース管理システム (DBMS) にはこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-310">Use this option for database management systems (DBMS) that do not support long file names.</span></span>  
  
 <span data-ttu-id="5ed62-311">**-SubscriptionType** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-311">**-SubscriptionType** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="5ed62-312">ディストリビューションのサブスクリプションの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-312">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="5ed62-313">値 **0** はプッシュ サブスクリプションを、値 **1** はプル サブスクリプションを、値 **2** は匿名サブスクリプションを示します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-313">A value of **0** indicates a push subscription, a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="5ed62-314">**-TransactionsPerHistory** [ **0**| **1**|...**10000**]</span><span class="sxs-lookup"><span data-stu-id="5ed62-314">**-TransactionsPerHistory** [ **0**| **1**|... **10000**]</span></span>  
 <span data-ttu-id="5ed62-315">履歴をログに記録するトランザクション間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-315">Specifies the transaction interval for history logging.</span></span> <span data-ttu-id="5ed62-316">最後に履歴をログに記録してからコミットしたトランザクションの数がこのオプションより多い場合、履歴メッセージがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-316">If the number of committed transactions after the last instance of history logging is greater than this option, a history message is logged.</span></span> <span data-ttu-id="5ed62-317">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-317">The default is 100.</span></span> <span data-ttu-id="5ed62-318">値 **0** は、 **TransactionsPerHistory**が無制限であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-318">A value of **0** indicates infinite **TransactionsPerHistory**.</span></span> <span data-ttu-id="5ed62-319">**MessageInterval**パラメーターを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-319">See the preceding **-MessageInterval**parameter.</span></span>  
  
 <span data-ttu-id="5ed62-320">**-UseDTS**</span><span class="sxs-lookup"><span data-stu-id="5ed62-320">**-UseDTS**</span></span>  
 <span data-ttu-id="5ed62-321">データ変換を許可するパブリケーションでは、このパラメーターを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-321">Must be specified as a parameter for a publication that allows data transformation.</span></span>  
  
 <span data-ttu-id="5ed62-322">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="5ed62-322">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="5ed62-323">ディストリビューション エージェントがスナップショット ファイルをサブスクライバーに適用するときに、BULK INSERT コマンドが使用され、初期スナップショットのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-323">Improves the performance of the initial snapshot by causing the Distribution Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="5ed62-324">このパラメーターは XML データ型との互換性がないため非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-324">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="5ed62-325">XML データをレプリケートしない場合にのみ、このパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-325">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="5ed62-326">このパラメーターを、キャラクター モードのスナップショットや、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-326">This parameter cannot be used with character mode snapshots or non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span> <span data-ttu-id="5ed62-327">このパラメーターを使用する場合は、サブスクライバー側の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントに、スナップショットの .bcp データ ファイルが格納されたディレクトリの読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-327">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="5ed62-328">このパラメーターを使用しない場合、これらのファイルが、エージェント ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーの場合) またはエージェントが読み込む ODBC ドライバー ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーの場合) によって読み取られるため、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5ed62-328">When this parameter is not used, the agent (for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) or the ODBC driver loaded by the agent (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="5ed62-329">**-UseOledbStreaming**</span><span class="sxs-lookup"><span data-stu-id="5ed62-329">**-UseOledbStreaming**</span></span>  
 <span data-ttu-id="5ed62-330">指定した場合、BLOB データをストリームとしてバインドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="5ed62-330">When specified, enables the binding of binary large object data as a stream.</span></span> <span data-ttu-id="5ed62-331">ストリームが使用されるしきい値 (バイト サイズ) を指定するには、 **-OledbStreamThreshold** を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-331">Use **-OledbStreamThreshold** to specify the size, in bytes, above which a stream will be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed62-332">解説</span><span class="sxs-lookup"><span data-stu-id="5ed62-332">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5ed62-333">ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントをインストールした場合、サービスはローカル コンピューターにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5ed62-333">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can only access the local computer.</span></span> <span data-ttu-id="5ed62-334">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへのログイン時に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]エージェントの下で実行するディストリビューション エージェントで、Windows 認証モードを使用するように構成すると、ディストリビューション エージェントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-334">If the Distribution Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Distribution Agent fails.</span></span> <span data-ttu-id="5ed62-335">既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。</span><span class="sxs-lookup"><span data-stu-id="5ed62-335">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="5ed62-336">セキュリティ アカウント変更の詳細については、「 [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-336">For information on changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="5ed62-337">ディストリビューション エージェントを起動するには、コマンド プロンプトから **distrib.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="5ed62-337">To start the Distribution Agent, execute **distrib.exe** from the command prompt.</span></span> <span data-ttu-id="5ed62-338">詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed62-338">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="5ed62-339">変更履歴</span><span class="sxs-lookup"><span data-stu-id="5ed62-339">Change History</span></span>  
  
|<span data-ttu-id="5ed62-340">変更内容</span><span class="sxs-lookup"><span data-stu-id="5ed62-340">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="5ed62-341">**-ExtendedEventConfigFile** パラメーターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="5ed62-341">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ed62-342">参照</span><span class="sxs-lookup"><span data-stu-id="5ed62-342">See Also</span></span>  
 [<span data-ttu-id="5ed62-343">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="5ed62-343">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
