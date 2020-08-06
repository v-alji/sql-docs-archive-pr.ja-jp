---
title: レプリケーション マージ エージェント | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Merge Agent, executables
- Merge Agent, parameter reference
- agents [SQL Server replication], Merge Agent
- command prompt [SQL Server replication]
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b3d74dcc6be62ae8a01d911a8404c7bc32fd651
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632413"
---
# <a name="replication-merge-agent"></a><span data-ttu-id="70471-102">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="70471-102">Replication Merge Agent</span></span>
  <span data-ttu-id="70471-103">レプリケーション マージ エージェントは、データベース テーブルに保持された初期スナップショットをサブスクライバーに適用するユーティリティ実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="70471-103">The Replication Merge Agent is a utility executable that applies the initial snapshot held in the database tables to the Subscribers.</span></span> <span data-ttu-id="70471-104">さらに、初期スナップショットの作成後にパブリッシャーで発生したデータの増分変更をマージし、ユーザーが構成したルールに従って、またはユーザーが作成したカスタム競合回避モジュールを使用して、競合を調整します。</span><span class="sxs-lookup"><span data-stu-id="70471-104">It also merges incremental data changes that occurred at the Publisher after the initial snapshot was created, and reconciles conflicts either according to the rules you configure or using a custom resolver you create.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70471-105">パラメーターは任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="70471-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="70471-106">省略可能なパラメーターを省略する場合、ローカル コンピューターであらかじめ定義されているレジストリ設定の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="70471-106">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70471-107">構文</span><span class="sxs-lookup"><span data-stu-id="70471-107">Syntax</span></span>  
  
```  
  
      replmerg [-?]   
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Publicationpublication-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database  
[-AltSnapshotFolderalt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-DestThreadsnumber_of_destination_threads]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatchdownload_generations_per_batch]  
[-DownloadReadChangesPerBatchdownload_read_changes_per_batch]  
[-DownloadWriteChangesPerBatchdownload_write_changes_per_batch]  
[-DynamicSnapshotLocationdynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]  
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogininternet_login]  
[-InternetPasswordinternet_password]  
[-InternetProxyLogininternet_proxy_login]  
[-InternetProxyPasswordinternet_proxy_password]  
[-InternetProxyServerinternet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeoutinternet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MakeGenerationIntervalmake_generation_interval_seconds]  
[-MaxBcpThreadsnumber_of_threads]  
[-MaxDownloadChangesnumber_of_download_changes]  
[-MaxUploadChangesnumber_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSizepacket_size]   
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOutquery_time_out_seconds]  
[-SrcThreadsnumber_of_source_threads]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatchupload_generations_per_batch]  
[-UploadReadChangesPerBatchupload_read_changes_per_batch]  
[-UploadWriteChangesPerBatchupload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateIntervalvalidate_interval]  
```  
  
## <a name="arguments"></a><span data-ttu-id="70471-108">引数</span><span class="sxs-lookup"><span data-stu-id="70471-108">Arguments</span></span>  
 <span data-ttu-id="70471-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="70471-109">**-?**</span></span>  
 <span data-ttu-id="70471-110">使用できるすべてのパラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="70471-110">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="70471-111">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="70471-111">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="70471-112">パブリッシャーの名前です。</span><span class="sxs-lookup"><span data-stu-id="70471-112">Is the name of the Publisher.</span></span> <span data-ttu-id="70471-113">サーバー上の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、*server_name* を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-113">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="70471-114">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-114">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="70471-115">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="70471-115">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="70471-116">パブリッシャー データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="70471-116">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="70471-117">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="70471-117">**-Publication** _publication_</span></span>  
 <span data-ttu-id="70471-118">パブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="70471-118">Is the name of the publication.</span></span> <span data-ttu-id="70471-119">このパラメーターは、新規または再初期化されたサブスクリプションのスナップショットを常に利用できるようにパブリケーションを設定している場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="70471-119">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="70471-120">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="70471-120">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="70471-121">サブスクライバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="70471-121">Is the name of the Subscriber.</span></span> <span data-ttu-id="70471-122">サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-122">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="70471-123">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-123">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="70471-124">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="70471-124">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="70471-125">サブスクライバー データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="70471-125">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="70471-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="70471-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="70471-127">サブスクリプションの初期スナップショットが含まれるフォルダーへのパスです。</span><span class="sxs-lookup"><span data-stu-id="70471-127">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="70471-128">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="70471-128">**-Continuous**</span></span>  
 <span data-ttu-id="70471-129">エージェントがレプリケートされたトランザクションの呼び出しを継続的に試みるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-129">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="70471-130">このパラメーターを指定する場合、保留されているトランザクションがなくても、エージェントはポーリング間隔でレプリケートされたトランザクションをソースから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70471-130">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="70471-131">**-DestThreads** _number_of_destination_threads_</span><span class="sxs-lookup"><span data-stu-id="70471-131">**-DestThreads** _number_of_destination_threads_</span></span>  
 <span data-ttu-id="70471-132">マージ エージェントが変更の対象で変更を適用するために使用する対象スレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-132">Specifies the number of destination threads that the Merge Agent uses to apply changes at the destination.</span></span> <span data-ttu-id="70471-133">変更の対象は、アップロード実行時はパブリッシャーであり、ダウンロード実行時はサブスクライバーです。</span><span class="sxs-lookup"><span data-stu-id="70471-133">The destination is the Publisher during upload and the Subscriber during download.</span></span> <span data-ttu-id="70471-134">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="70471-134">The default is 4.</span></span>  
  
 <span data-ttu-id="70471-135">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="70471-135">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="70471-136">エージェント定義ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="70471-136">Is the path of the agent definition file.</span></span> <span data-ttu-id="70471-137">エージェント定義ファイルには、エージェントのコマンド プロンプト引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="70471-137">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="70471-138">ファイルの内容は実行可能ファイルとして解析されます。</span><span class="sxs-lookup"><span data-stu-id="70471-138">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="70471-139">二重引用符 (") を使用して、任意の文字を含む引数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-139">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="70471-140">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="70471-140">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="70471-141">ディストリビューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="70471-141">Is the Distributor name.</span></span> <span data-ttu-id="70471-142">サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-142">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="70471-143">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-143">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="70471-144">ディストリビューター (プッシュ) ディストリビューションの場合、既定の名前は、ローカル コンピューターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="70471-144">For Distributor (push) distribution, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="70471-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="70471-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="70471-146">ディストリビューターのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="70471-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="70471-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="70471-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="70471-148">ディストリビューターのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="70471-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="70471-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="70471-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="70471-150">ディストリビューターのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="70471-151">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-151">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="70471-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="70471-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span></span>  
 <span data-ttu-id="70471-153">パブリッシャーからサブスクライバーに変更をダウンロードする間に、1 つのバッチで処理される生成結果の数です。</span><span class="sxs-lookup"><span data-stu-id="70471-153">Is the number of generations to be processed in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="70471-154">生成結果は、アーティクルごとに変更の論理グループとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="70471-154">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="70471-155">信頼性の高い通信リンクの既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="70471-155">The default for a reliable communication link is 100.</span></span> <span data-ttu-id="70471-156">信頼性の低い通信リンクの既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="70471-156">The default for an unreliable communication link is 10.</span></span>  
  
 <span data-ttu-id="70471-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="70471-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span></span>  
 <span data-ttu-id="70471-158">パブリッシャーからサブスクライバーに変更をダウンロードする間に、1 つのバッチで読み取られる変更の数です。</span><span class="sxs-lookup"><span data-stu-id="70471-158">Is the number of changes to be read in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="70471-159">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="70471-159">The default is 100.</span></span>  
  
 <span data-ttu-id="70471-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="70471-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span></span>  
 <span data-ttu-id="70471-161">パブリッシャーからサブスクライバーに変更をダウンロードする間に、1 つのバッチで適用される変更の数です。</span><span class="sxs-lookup"><span data-stu-id="70471-161">Is the number of changes to be applied in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="70471-162">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="70471-162">The default is 100.</span></span>  
  
 <span data-ttu-id="70471-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="70471-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="70471-164">パブリケーションでパラメーター化された行フィルターを使用する場合のフィルター選択されたデータ スナップショット ファイルの位置です。</span><span class="sxs-lookup"><span data-stu-id="70471-164">Is the location of the filtered data snapshot files when the publication uses parameterized row filters.</span></span>  
  
 <span data-ttu-id="70471-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="70471-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="70471-166">接続時にマージ エージェントで使用される SSL (Secure Sockets Layer) 暗号化のレベルです。</span><span class="sxs-lookup"><span data-stu-id="70471-166">Is the level of Secure Sockets Layer (SSL) encryption used by the Merge Agent when making connections.</span></span>  
  
|<span data-ttu-id="70471-167">EncryptionLevel の値</span><span class="sxs-lookup"><span data-stu-id="70471-167">EncryptionLevel value</span></span>|<span data-ttu-id="70471-168">説明</span><span class="sxs-lookup"><span data-stu-id="70471-168">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="70471-169">**0**</span><span class="sxs-lookup"><span data-stu-id="70471-169">**0**</span></span>|<span data-ttu-id="70471-170">SSL は使用されません。</span><span class="sxs-lookup"><span data-stu-id="70471-170">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="70471-171">**1**</span><span class="sxs-lookup"><span data-stu-id="70471-171">**1**</span></span>|<span data-ttu-id="70471-172">SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="70471-172">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="70471-173">**2**</span><span class="sxs-lookup"><span data-stu-id="70471-173">**2**</span></span>|<span data-ttu-id="70471-174">SSL が使用され、証明書の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="70471-174">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="70471-175">有効な SSL 証明書には、SQL Server の完全修飾ドメイン名が定義されます。</span><span class="sxs-lookup"><span data-stu-id="70471-175">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="70471-176">-EncryptionLevel を 2 に設定したときにエージェントが正しく接続されるようにするには、ローカルの SQL Server 上に別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="70471-176">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="70471-177">'Alias Name' パラメーターはサーバー名にし、'Server' パラメーターは SQL Server の完全修飾名に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70471-177">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="70471-178">詳細については、「 [SQL Server レプリケーションセキュリティ](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70471-178">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="70471-179">**-ExchangeType** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="70471-179">**-ExchangeType** [ **1**| **2**| **3**]</span></span>  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="70471-180">アップロードを制限するには、`@subscriber_upload_options` の `sp_addmergearticle` を代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="70471-180">To restrict uploading, use the `@subscriber_upload_options` of `sp_addmergearticle` instead.</span></span>  
  
 <span data-ttu-id="70471-181">同期中のデータ交換の種類を指定します。次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="70471-181">Specifies the type of data exchange during synchronization, which can be one of the following:</span></span>  
  
|<span data-ttu-id="70471-182">ExchangeType の値</span><span class="sxs-lookup"><span data-stu-id="70471-182">ExchangeType value</span></span>|<span data-ttu-id="70471-183">説明</span><span class="sxs-lookup"><span data-stu-id="70471-183">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="70471-184">**1**</span><span class="sxs-lookup"><span data-stu-id="70471-184">**1**</span></span>|<span data-ttu-id="70471-185">エージェントは、サブスクライバーからパブリッシャーにデータ変更をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="70471-185">Agent should upload data changes from the Subscriber to the Publisher.</span></span>|  
|<span data-ttu-id="70471-186">**2**</span><span class="sxs-lookup"><span data-stu-id="70471-186">**2**</span></span>|<span data-ttu-id="70471-187">エージェントは、パブリッシャーからサブスクライバーにデータ変更をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="70471-187">Agent should download data changes from the Publisher to the Subscriber.</span></span>|  
|<span data-ttu-id="70471-188">**3** (既定値)</span><span class="sxs-lookup"><span data-stu-id="70471-188">**3** (default)</span></span>|<span data-ttu-id="70471-189">エージェントは最初にサブスクライバーからパブリッシャーにデータ変更をアップロードし、次にパブリッシャーからサブスクライバーにデータ変更をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="70471-189">Agent should first upload data changes from the Subscriber to the Publisher and then download data changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="70471-190">このオプションは、Web 同期で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70471-190">You must use this option with Web synchronization.</span></span>|  
  
 <span data-ttu-id="70471-191">ダウンロード専用のアーティクルによって、パブリケーション内の個別のアーティクルの同期の動作を制御して、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="70471-191">Download-only articles enable you to control the synchronization behavior of individual articles in a publication, and they can provide a performance benefit.</span></span> <span data-ttu-id="70471-192">詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70471-192">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="70471-193">`ExchangeType` を使用してマージ レプリケーションのアップロード フェーズとダウンロード フェーズを個別のセッションとして分ける場合は、`ExchangeType` を 1 に設定してマージ エージェントを実行し、その後でこのパラメーターの値を 2 に設定してマージ エージェントを再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70471-193">If using `ExchangeType` to separate the upload and download phase of merge replication into separate sessions, you must run the merge agent with `ExchangeType` set to 1 first and then run the merge agent again with the value 2.</span></span> <span data-ttu-id="70471-194">どちらのパラメーターを使用してもマージ エージェントの実行が失敗する場合、メタデータが削除され、サブスクリプションの再初期化 (アップロードは行わない) を要求される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70471-194">Failure to run the merge agent with both parameters will cause metadata to be deleted and require you to reinitialize the subscription (without upload).</span></span>  
  
 <span data-ttu-id="70471-195">**-FastRowCount** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-195">**-FastRowCount** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-196">行数の検証に使用する行数計算方法の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-196">Specifies what type of rowcount calculation method should be used for rowcount validation.</span></span> <span data-ttu-id="70471-197">値 **1** (既定) は高速計算法を示します。</span><span class="sxs-lookup"><span data-stu-id="70471-197">A value of **1** (default) indicates the fast method.</span></span> <span data-ttu-id="70471-198">値 **0** は、完全行数計算法を示します。</span><span class="sxs-lookup"><span data-stu-id="70471-198">A value of **0** indicates the full rowcount method.</span></span>  
  
 <span data-ttu-id="70471-199">**-FileTransferType** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-199">**-FileTransferType** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-200">ファイル転送の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-200">Specifies the file transfer type.</span></span> <span data-ttu-id="70471-201">**0** の値は UNC (汎用名前付け規則) を示し、 **1** の値は FTP (ファイル転送プロトコル) を示します。</span><span class="sxs-lookup"><span data-stu-id="70471-201">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="70471-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span><span class="sxs-lookup"><span data-stu-id="70471-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span></span>  
 <span data-ttu-id="70471-203">マージ エージェントが使用する収束のレベルを指定します。次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="70471-203">Specifies the level of convergence the Merge Agent should use, and can be one of the following:</span></span>  
  
|<span data-ttu-id="70471-204">ForceConvergenceLevel の値</span><span class="sxs-lookup"><span data-stu-id="70471-204">ForceConvergenceLevel value</span></span>|<span data-ttu-id="70471-205">説明</span><span class="sxs-lookup"><span data-stu-id="70471-205">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="70471-206">**0** (既定値)</span><span class="sxs-lookup"><span data-stu-id="70471-206">**0** (default)</span></span>|<span data-ttu-id="70471-207">既定値。</span><span class="sxs-lookup"><span data-stu-id="70471-207">Default.</span></span> <span data-ttu-id="70471-208">追加の収束なしで標準のマージを実行します。</span><span class="sxs-lookup"><span data-stu-id="70471-208">Perform a standard merge without additional convergence.</span></span>|  
|<span data-ttu-id="70471-209">**1**</span><span class="sxs-lookup"><span data-stu-id="70471-209">**1**</span></span>|<span data-ttu-id="70471-210">すべての生成結果の収束を強制します。</span><span class="sxs-lookup"><span data-stu-id="70471-210">Force convergence for all generations.</span></span>|  
|<span data-ttu-id="70471-211">**2**</span><span class="sxs-lookup"><span data-stu-id="70471-211">**2**</span></span>|<span data-ttu-id="70471-212">すべての生成結果の収束を強制し、破損した系列を修正します。</span><span class="sxs-lookup"><span data-stu-id="70471-212">Force convergence for all generations and correct corrupt lineages.</span></span> <span data-ttu-id="70471-213">この値を指定する場合は、系列を修正する場所 (パブリッシャー、サブスクライバー、またはパブリッシャーとサブスクライバーの両方) を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-213">When specifying this value, specify where lineages should be corrected: the Publisher, the Subscriber, or both the Publisher and the Subscriber.</span></span>|  
  
 <span data-ttu-id="70471-214">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="70471-214">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="70471-215">ディストリビューター用の FTP サービスのネットワーク アドレスです。</span><span class="sxs-lookup"><span data-stu-id="70471-215">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="70471-216">このパラメーターを指定しない場合、 **Distributor** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="70471-216">When not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="70471-217">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="70471-217">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="70471-218">FTP サービスに接続するときに使用するユーザー パスワードです。</span><span class="sxs-lookup"><span data-stu-id="70471-218">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="70471-219">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="70471-219">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="70471-220">ディストリビューター用の FTP サービスのポート番号です。</span><span class="sxs-lookup"><span data-stu-id="70471-220">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="70471-221">このパラメーターを指定しない場合、FTP サービスの既定のポート番号 (21) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="70471-221">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="70471-222">**-FtpUserName** _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="70471-222">**-FtpUserName** _ftp_user_name_</span></span>  
 <span data-ttu-id="70471-223">FTP サービスに接続するときに使用するユーザー名です。</span><span class="sxs-lookup"><span data-stu-id="70471-223">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="70471-224">この引数を指定しない場合は、匿名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="70471-224">When not specified, anonymous is used.</span></span>  
  
 <span data-ttu-id="70471-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="70471-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="70471-226">マージ操作中にログに記録する履歴の量を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-226">Specifies the amount of history logged during a merge operation.</span></span> <span data-ttu-id="70471-227">**1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="70471-227">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="70471-228">HistoryVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="70471-228">HistoryVerboseLevel value</span></span>|<span data-ttu-id="70471-229">説明</span><span class="sxs-lookup"><span data-stu-id="70471-229">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="70471-230">**0**</span><span class="sxs-lookup"><span data-stu-id="70471-230">**0**</span></span>|<span data-ttu-id="70471-231">エージェントの状態の最終メッセージ、最終のセッションの詳細、およびすべてのエラーをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="70471-231">Log the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="70471-232">**1**</span><span class="sxs-lookup"><span data-stu-id="70471-232">**1**</span></span>|<span data-ttu-id="70471-233">各セッションの状態における増分セッションの詳細をログに記録します。エージェントの状態の最終メッセージ、最終のセッションの詳細、およびすべてのエラーに加えて、進行状況が含まれます。</span><span class="sxs-lookup"><span data-stu-id="70471-233">Log incremental session details at each session status, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="70471-234">**2**</span><span class="sxs-lookup"><span data-stu-id="70471-234">**2**</span></span>|<span data-ttu-id="70471-235">既定値。</span><span class="sxs-lookup"><span data-stu-id="70471-235">Default.</span></span> <span data-ttu-id="70471-236">各セッションの状態における増分セッションの詳細、およびアーティクル レベルのセッションの詳細をログに記録します。エージェントの状態の最終メッセージ、最終のセッションの詳細、およびすべてのエラーに加えて、進行状況が含まれます。</span><span class="sxs-lookup"><span data-stu-id="70471-236">Log both incremental session details at each session status and article level session details, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span> <span data-ttu-id="70471-237">エージェントの状態のメッセージもログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="70471-237">Agent status messages are also logged.</span></span>|  
|<span data-ttu-id="70471-238">**3**</span><span class="sxs-lookup"><span data-stu-id="70471-238">**3**</span></span>|<span data-ttu-id="70471-239">**-HistoryVerboseLevel** = **2**と同じですが、より多くのエージェント進行状況メッセージがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="70471-239">The same as **-HistoryVerboseLevel** = **2**, except that more agent progress messages are logged.</span></span>|  
  
 <span data-ttu-id="70471-240">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="70471-240">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="70471-241">ローカル コンピューターのネットワーク名です。</span><span class="sxs-lookup"><span data-stu-id="70471-241">Is the network name of the local computer.</span></span> <span data-ttu-id="70471-242">既定値は、ローカル コンピューターの名前になります。</span><span class="sxs-lookup"><span data-stu-id="70471-242">The default is the local computer name.</span></span>  
  
 <span data-ttu-id="70471-243">**-InteractiveResolution** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-243">**-InteractiveResolution** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-244">同期中に競合が発生した場合に、インタラクティブ競合回避を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-244">Specifies whether interactive conflict resolution is used when a conflict occurs during synchronization.</span></span> <span data-ttu-id="70471-245">既定値の **0**は、インタラクティブ競合回避を使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-245">The default is **0**, indicating that interactive conflict resolution is not used.</span></span>  
  
 <span data-ttu-id="70471-246">**-InternetLogin** _internet_login_</span><span class="sxs-lookup"><span data-stu-id="70471-246">**-InternetLogin** _internet_login_</span></span>  
 <span data-ttu-id="70471-247">認証を必要とする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL への接続時に使用されるログイン名を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-247">Specifies the login name used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="70471-248">**-InternetPassword** _internet_password_</span><span class="sxs-lookup"><span data-stu-id="70471-248">**-InternetPassword** _internet_password_</span></span>  
 <span data-ttu-id="70471-249">認証を必要とする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL への接続時に使用されるパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-249">Specifies the password used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="70471-250">**-InternetProxyLogin**  *internet_proxy_login*</span><span class="sxs-lookup"><span data-stu-id="70471-250">**-InternetProxyLogin**  *internet_proxy_login*</span></span>  
 <span data-ttu-id="70471-251">認証を必要とする、 *internet_proxy_server*で定義されたプロキシ サーバーへの接続時に使用されるログイン名を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-251">Specifies the login name used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="70471-252">**-InternetProxyPassword**  *internet_proxy_password*</span><span class="sxs-lookup"><span data-stu-id="70471-252">**-InternetProxyPassword**  *internet_proxy_password*</span></span>  
 <span data-ttu-id="70471-253">認証を必要とする、 *internet_proxy_server*で定義されたプロキシ サーバーへの接続時に使用されるパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-253">Specifies the password used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="70471-254">**-InternetProxyServer**  *internet_proxy_server*</span><span class="sxs-lookup"><span data-stu-id="70471-254">**-InternetProxyServer**  *internet_proxy_server*</span></span>  
 <span data-ttu-id="70471-255">*internet_url*で指定した HTTP リソースへのアクセス時に使用するプロキシ サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-255">Specifies the proxy server to use when accessing the HTTP resource specified in *internet_url*.</span></span>  
  
 <span data-ttu-id="70471-256">**-InternetSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-256">**-InternetSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-257">Web 同期時の Web サーバーとの接続に使用される IIS セキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-257">Specifies the IIS security mode used when connecting to the Web server during Web synchronization.</span></span> <span data-ttu-id="70471-258">値 **0** は基本認証を示し、値 **1** は Windows 統合認証 (既定値) を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-258">A value of **0** indicates Basic Authentication, and a value of **1** indicates Windows Integrated Authentication (default).</span></span>  
  
 <span data-ttu-id="70471-259">**-InternetTimeout** _internet_timeout_</span><span class="sxs-lookup"><span data-stu-id="70471-259">**-InternetTimeout** _internet_timeout_</span></span>  
 <span data-ttu-id="70471-260">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL がタイムアウトになるまでの秒数です。</span><span class="sxs-lookup"><span data-stu-id="70471-260">Is the number of seconds before a connection to the to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL times out.</span></span>  
  
 <span data-ttu-id="70471-261">**-InternetURL** _internet_url_</span><span class="sxs-lookup"><span data-stu-id="70471-261">**-InternetURL** _internet_url_</span></span>  
 <span data-ttu-id="70471-262">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション リスナー ISAPI DLL への接続に使用される URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-262">Specifies the URL used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL.</span></span> <span data-ttu-id="70471-263">このプロパティの指定は必須です。</span><span class="sxs-lookup"><span data-stu-id="70471-263">This property must be specified.</span></span>  
  
 <span data-ttu-id="70471-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="70471-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="70471-265">既存の接続がサーバーからの応答を待機しているかどうかを、履歴スレッドがチェックするまでの秒数です。</span><span class="sxs-lookup"><span data-stu-id="70471-265">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="70471-266">長時間実行のときに、照合エージェントがマージ エージェントに SUSPECT のマークを付けないようにするには、この値を小さくします。</span><span class="sxs-lookup"><span data-stu-id="70471-266">This value can be decreased to avoid having the checkup agent mark the Merge Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="70471-267">既定値は **300** 秒です。</span><span class="sxs-lookup"><span data-stu-id="70471-267">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="70471-268">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="70471-268">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="70471-269">ログインがタイムアウトになるまでの秒数です。既定値は **15** 秒です。</span><span class="sxs-lookup"><span data-stu-id="70471-269">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="70471-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="70471-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span></span>  
 <span data-ttu-id="70471-271">クライアントにダウンロードする生成結果 (変更のバッチ) を作成する間隔 (秒) です。</span><span class="sxs-lookup"><span data-stu-id="70471-271">Is the number of seconds to wait between creating generations, or batches of changes, to download to the client.</span></span> <span data-ttu-id="70471-272">既定値は **1** 秒です。</span><span class="sxs-lookup"><span data-stu-id="70471-272">The default is **1** second.</span></span>  
  
 <span data-ttu-id="70471-273">Makegeneration は、パブリッシャーの変更をサブスクライバーにダウンロードするように準備するプロセスです。また、ダウンロード中にパフォーマンスのボトルネックになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="70471-273">Makegeneration is the process that prepares Publisher changes to be downloaded to Subscribers, and it can be a performance bottleneck during downloads.</span></span> <span data-ttu-id="70471-274">makegeneration プロセスが **-MakeGenerationInterval**で指定された間隔で既に実行された場合、現在の同期セッションでは、このプロセスはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="70471-274">If the makegeneration process already ran within the interval specified by **-MakeGenerationInterval**, the process is skipped for the current synchronization session.</span></span> <span data-ttu-id="70471-275">これは、同期のコンカレンシーに役立つ場合があります。特に、サブスクライバーが変更をダウンロードしない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="70471-275">This can benefit synchronization concurrency and is especially helpful if Subscribers do not expect to download changes.</span></span>  
  
 <span data-ttu-id="70471-276">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="70471-276">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="70471-277">並列実行できる一括コピーの操作数を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-277">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="70471-278">同時に存在するスレッドおよび ODBC 接続の最大数は、 **MaxBcpThreads** 、またはパブリケーション データベース内のシステム テーブル **sysmergeschemachange** に表示される一括コピー要求数のいずれか少ない方の値になります。</span><span class="sxs-lookup"><span data-stu-id="70471-278">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the system table **sysmergeschemachange** in the publication database.</span></span> <span data-ttu-id="70471-279">**MaxBcpThreads** の値は、0 よりも大きくする必要がありますが、ハードコーディングされた上限はありません。</span><span class="sxs-lookup"><span data-stu-id="70471-279">**MaxBcpThreads** must have a value greater than 0 and has no hard-coded upper limit.</span></span> <span data-ttu-id="70471-280">既定値は **1**です。</span><span class="sxs-lookup"><span data-stu-id="70471-280">The default is **1**.</span></span>  
  
 <span data-ttu-id="70471-281">**-MaxDownloadChanges** _number_of_download_changes_</span><span class="sxs-lookup"><span data-stu-id="70471-281">**-MaxDownloadChanges** _number_of_download_changes_</span></span>  
 <span data-ttu-id="70471-282">パブリッシャーからサブスクライバーにダウンロードする必要のある変更済みの行の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-282">Specifies the maximum number of changed rows that should be downloaded from the Publisher to the Subscriber.</span></span> <span data-ttu-id="70471-283">ダウンロードする行数が、指定した最大数より多くなる場合があります。完全な生成結果が処理されること、および並列の対象スレッドが実行されて最初のパスでそれぞれ 100 以上の変更が処理されることが原因です。</span><span class="sxs-lookup"><span data-stu-id="70471-283">The number of rows downloaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="70471-284">既定では、ダウンロードの準備が整っている変更がすべて送信されます。</span><span class="sxs-lookup"><span data-stu-id="70471-284">By default all changes that are ready to be downloaded are sent.</span></span>  
  
 <span data-ttu-id="70471-285">**-MaxUploadChanges** _number_of_upload_changes_</span><span class="sxs-lookup"><span data-stu-id="70471-285">**-MaxUploadChanges** _number_of_upload_changes_</span></span>  
 <span data-ttu-id="70471-286">サブスクライバーからパブリッシャーにアップロードする必要のある変更済みの行の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-286">Specifies the maximum number of changed rows that should be uploaded from the Subscriber to the Publisher.</span></span> <span data-ttu-id="70471-287">アップロードする行数が、指定した最大数より多くなる場合があります。完全な生成結果が処理されること、および並列の対象スレッドが実行されて最初のパスでそれぞれ 100 以上の変更が処理されることが原因です。</span><span class="sxs-lookup"><span data-stu-id="70471-287">The number of rows uploaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="70471-288">既定では、アップロードの準備が整っている変更がすべて送信されます。</span><span class="sxs-lookup"><span data-stu-id="70471-288">By default all changes that are ready to be uploaded are sent.</span></span>  
  
 <span data-ttu-id="70471-289">**-MetadataRetentionCleanup** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-289">**-MetadataRetentionCleanup** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-290">パブリケーション保有期間に基づいて、メタデータを [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)、および [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) から削除するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-290">Specifies if metadata is removed from [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) based on the publication retention period.</span></span> <span data-ttu-id="70471-291">既定値の **1**は、クリーンアップを行う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-291">The default is **1**, indicating that cleanup should occur.</span></span> <span data-ttu-id="70471-292">値 **0** は、クリーンアップを自動的に実行しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-292">A value of **0** indicates that cleanup should not occur automatically.</span></span>  
  
 <span data-ttu-id="70471-293">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="70471-293">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="70471-294">エージェントの出力ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="70471-294">Is the path of the agent output file.</span></span> <span data-ttu-id="70471-295">ファイル名が指定されていない場合、出力はコンソールに送られます。</span><span class="sxs-lookup"><span data-stu-id="70471-295">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="70471-296">指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="70471-296">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="70471-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span><span class="sxs-lookup"><span data-stu-id="70471-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span></span>  
 <span data-ttu-id="70471-298">出力を詳細表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-298">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="70471-299">詳細レベルが **0**の場合、エラー メッセージだけが出力されます。</span><span class="sxs-lookup"><span data-stu-id="70471-299">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="70471-300">詳細レベルが **1**の場合、すべての実行状況報告メッセージが印刷されます。</span><span class="sxs-lookup"><span data-stu-id="70471-300">If the verbose level is **1**, all of the progress report messages are printed.</span></span> <span data-ttu-id="70471-301">詳細レベルが **2** (既定値) の場合、すべてのエラー メッセージと実行状況報告メッセージが出力されます。これはデバッグ時に便利です。</span><span class="sxs-lookup"><span data-stu-id="70471-301">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="70471-302">**-ParallelUploadDownload** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-302">**-ParallelUploadDownload** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-303">パブリッシャーにアップロードする変更とサブスクライバーにダウンロードする変更をマージ エージェントが並列で処理するかどうかを指定します。帯域幅が広いネットワークを使用している大容量環境で有用です。</span><span class="sxs-lookup"><span data-stu-id="70471-303">Specifies whether the Merge Agent should process in parallel the changes uploaded to the Publisher and those downloaded to the Subscriber, which is useful in high volume environments with high network bandwidth.</span></span> <span data-ttu-id="70471-304">**ParallelUploadDownload** が **1**の場合は、並列処理が有効です。</span><span class="sxs-lookup"><span data-stu-id="70471-304">If **ParallelUploadDownload** is **1**, then parallel processing is enabled.</span></span>  
  
 <span data-ttu-id="70471-305">**-PacketSize**</span><span class="sxs-lookup"><span data-stu-id="70471-305">**-PacketSize**</span></span>  
 <span data-ttu-id="70471-306">パケット サイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-306">Is the packet size, in bytes.</span></span> <span data-ttu-id="70471-307">既定値は 4096 (バイト) です。</span><span class="sxs-lookup"><span data-stu-id="70471-307">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="70471-308">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="70471-308">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="70471-309">パブリッシャーまたはサブスクライバーへのデータ変更をクエリする間隔 (秒数) を示します。</span><span class="sxs-lookup"><span data-stu-id="70471-309">Is how often, in seconds, the Publisher or Subscriber is queried for data changes.</span></span> <span data-ttu-id="70471-310">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="70471-310">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="70471-311">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="70471-311">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="70471-312">エージェント パラメーターに使用するエージェント プロファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-312">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="70471-313">**ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="70471-313">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="70471-314">**ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。</span><span class="sxs-lookup"><span data-stu-id="70471-314">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="70471-315">詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70471-315">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="70471-316">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="70471-316">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="70471-317">パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-317">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="70471-318">詳細については、「 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="70471-318">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="70471-319">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="70471-319">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="70471-320">パブリッシャーのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="70471-320">Is the Publisher login name.</span></span> <span data-ttu-id="70471-321">**PublisherSecurityMode** が **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証) の場合、このパラメーターの指定は必須です。</span><span class="sxs-lookup"><span data-stu-id="70471-321">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="70471-322">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="70471-322">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="70471-323">パブリッシャーのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="70471-323">Is the Publisher password.</span></span> <span data-ttu-id="70471-324">**PublisherSecurityMode** が **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証) の場合、このパラメーターの指定は必須です。</span><span class="sxs-lookup"><span data-stu-id="70471-324">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="70471-325">**-PublisherSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="70471-325">**-PublisherSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="70471-326">パブリッシャーのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-326">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="70471-327">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-327">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="70471-328">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="70471-328">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="70471-329">クエリがタイムアウトになるまでの秒数です。既定では 300 秒です。</span><span class="sxs-lookup"><span data-stu-id="70471-329">Is the number of seconds before the query times out. The default is 300 seconds.</span></span> <span data-ttu-id="70471-330">マージ エージェントも `QueryTimeout` の値を使用して、この値が 1800 を超える場合にパーティション スナップショットの生成をどのくらいの期間待機するかを判断します。</span><span class="sxs-lookup"><span data-stu-id="70471-330">The Merge Agent also uses the value of `QueryTimeout` to determine how long to wait for generation of a partitioned snapshot when this value is greater than 1800.</span></span>  
  
 <span data-ttu-id="70471-331">**-SrcThreads** _number_of_source_threads_</span><span class="sxs-lookup"><span data-stu-id="70471-331">**-SrcThreads** _number_of_source_threads_</span></span>  
 <span data-ttu-id="70471-332">マージ エージェントが変更元から変更を列挙するために使用するソース スレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-332">Specifies the number of source threads that the Merge Agent uses to enumerate changes from the source.</span></span> <span data-ttu-id="70471-333">変更元は、アップロード実行時はサブスクライバーであり、ダウンロード実行時はパブリッシャーです。</span><span class="sxs-lookup"><span data-stu-id="70471-333">The source is the Subscriber during upload and the Publisher during download.</span></span> <span data-ttu-id="70471-334">既定値は **3**です。</span><span class="sxs-lookup"><span data-stu-id="70471-334">The default is **3**.</span></span>  
  
 <span data-ttu-id="70471-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="70471-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="70471-336">同時に実行されるマージプロセスの数が sp_addmergepublication のプロパティによって設定された上限に達したときに、マージエージェントが待機する最大秒数を指定し **@max_concurrent_merge** ます。 **sp_addmergepublication**</span><span class="sxs-lookup"><span data-stu-id="70471-336">Is the maximum number of seconds that the Merge Agent waits when the number of concurrent merge processes running is at the limit set by the **@max_concurrent_merge** property of **sp_addmergepublication**.</span></span> <span data-ttu-id="70471-337">最長秒数に達したときにマージ エージェントが待機中である場合、マージ エージェントは終了します。</span><span class="sxs-lookup"><span data-stu-id="70471-337">If the maximum number of seconds is reached and the Merge Agent is still waiting, it will exit.</span></span> <span data-ttu-id="70471-338">値 0 は、エージェントが無制限に待機することを示します。ただし、キャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="70471-338">A value of 0 means that the agent waits indefinitely, although it can be cancelled.</span></span>  
  
 <span data-ttu-id="70471-339">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="70471-339">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="70471-340">**SubscriberType** が **2** の場合、Jet データベース (.mdb) ファイルへのパスを指定します。この指定では、ODBC データ ソース名 (DSN) なしで Jet データベースに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="70471-340">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="70471-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="70471-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="70471-342">既存のサブスクライバー データベースがあるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-342">Specifies whether there is an existing Subscriber database.</span></span>  
  
|<span data-ttu-id="70471-343">SubscriberDBAddOption の値</span><span class="sxs-lookup"><span data-stu-id="70471-343">SubscriberDBAddOption value</span></span>|<span data-ttu-id="70471-344">説明</span><span class="sxs-lookup"><span data-stu-id="70471-344">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="70471-345">**0**</span><span class="sxs-lookup"><span data-stu-id="70471-345">**0**</span></span>|<span data-ttu-id="70471-346">既存のデータベースを使用します (既定値)。</span><span class="sxs-lookup"><span data-stu-id="70471-346">Use the existing database (default).</span></span>|  
|<span data-ttu-id="70471-347">**1**</span><span class="sxs-lookup"><span data-stu-id="70471-347">**1**</span></span>|<span data-ttu-id="70471-348">新しい空のサブスクライバー データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="70471-348">Create a new, empty Subscriber database.</span></span>|  
|<span data-ttu-id="70471-349">**2**</span><span class="sxs-lookup"><span data-stu-id="70471-349">**2**</span></span>|<span data-ttu-id="70471-350">新しいデータベースを作成して、指定されたファイルにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="70471-350">Create a new database and attach it to the specified file.</span></span>|  
|<span data-ttu-id="70471-351">**3**</span><span class="sxs-lookup"><span data-stu-id="70471-351">**3**</span></span>|<span data-ttu-id="70471-352">新しいデータベースを作成し、データベースをアタッチして、ファイルに存在する可能性のあるすべてのサブスクリプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="70471-352">Create a new database, attach the database, and enable all subscriptions that might exist at the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="70471-353">値 **2** および **3**を使用する場合は、サブスクライバーのデータベース パスを **SubscriberDatabasePath** オプションで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70471-353">When you use values **2** and **3**, the database path for the Subscriber must be specified in the **SubscriberDatabasePath** option.</span></span>  
  
 <span data-ttu-id="70471-354">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="70471-354">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="70471-355">サブスクライバーのログイン名です。</span><span class="sxs-lookup"><span data-stu-id="70471-355">Is the Subscriber login name.</span></span> <span data-ttu-id="70471-356">**SubscriberSecurityMode** が **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード) の場合は、このパラメーターを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="70471-356">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="70471-357">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="70471-357">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="70471-358">サブスクライバーのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="70471-358">Is the Subscriber password.</span></span> <span data-ttu-id="70471-359">**SubscriberSecurityMode** が **0** ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード) の場合は、このパラメーターを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="70471-359">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="70471-360">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="70471-360">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="70471-361">サブスクライバーのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-361">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="70471-362">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-362">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="70471-363">**-SubscriberConflictClean** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="70471-363">**-SubscriberConflictClean** [ **0**| **1**]</span></span>  
 <span data-ttu-id="70471-364">同期処理中にサブスクライバーで競合テーブルがクリーンアップされるかどうかを示します。値 **1** は、サブスクライバーで競合テーブルがクリーンアップされることを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-364">Is if conflict tables are cleaned-up at the Subscriber during the synchronization process, where a value of **1** indicates that conflict tables at the Subscriber are cleaned-up.</span></span> <span data-ttu-id="70471-365">このパラメーターは、競合のログ記録が集中管理されていないパブリケーションに対するサブスクリプションにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="70471-365">This parameter is used only for subscriptions to publications with decentralized conflict logging.</span></span>  
  
 <span data-ttu-id="70471-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span><span class="sxs-lookup"><span data-stu-id="70471-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span></span>  
 <span data-ttu-id="70471-367">マージ エージェントによって使用されるサブスクライバー接続の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-367">Specifies the type of Subscriber connection used by the Merge Agent.</span></span> <span data-ttu-id="70471-368">このパラメーターでは、既定値の **0** のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="70471-368">Only the default value of **0** is supported for this parameter.</span></span>  
  
 <span data-ttu-id="70471-369">**-SubscriptionType**[ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="70471-369">**-SubscriptionType**[ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="70471-370">ディストリビューションのサブスクリプションの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-370">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="70471-371">値 **0** は、プッシュ サブスクリプション (既定値) を示します。値 **1** はプル サブスクリプションを示し、値 **2** は匿名サブスクリプションを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-371">A value of **0** indicates a push subscription (default), a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="70471-372">**-SyncToAlternate** **[0|1]**</span><span class="sxs-lookup"><span data-stu-id="70471-372">**-SyncToAlternate** [ **0|1**]</span></span>  
 <span data-ttu-id="70471-373">マージ エージェントがサブスクリプションと代替パブリッシャー間での同期を実行しているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-373">Specifies whether the Merge Agent is synchronizing between a Subscriber and an alternate Publisher.</span></span> <span data-ttu-id="70471-374">値 **1** は、これが代替パブリッシャーであることを示します。</span><span class="sxs-lookup"><span data-stu-id="70471-374">A value of **1** indicates that it is an alternate Publisher.</span></span> <span data-ttu-id="70471-375">既定値は **0**です。</span><span class="sxs-lookup"><span data-stu-id="70471-375">The default is **0**.</span></span>  
  
 <span data-ttu-id="70471-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="70471-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span></span>  
 <span data-ttu-id="70471-377">サブスクライバーからパブリッシャーに変更をアップロードする間に、1 つのバッチで処理される生成結果の数です。</span><span class="sxs-lookup"><span data-stu-id="70471-377">Is the number of generations to be processed in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="70471-378">生成結果は、アーティクルごとに変更の論理グループとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="70471-378">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="70471-379">信頼性の高い通信リンクの既定値は **100**です。</span><span class="sxs-lookup"><span data-stu-id="70471-379">The default for a reliable communication link is **100**.</span></span> <span data-ttu-id="70471-380">信頼性の低い通信リンクの既定値は **1**です。</span><span class="sxs-lookup"><span data-stu-id="70471-380">The default for an unreliable communication link is **1**.</span></span>  
  
 <span data-ttu-id="70471-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="70471-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span></span>  
 <span data-ttu-id="70471-382">サブスクライバーからパブリッシャーに変更をアップロードする間に、1 つのバッチで読み取られる変更の数です。</span><span class="sxs-lookup"><span data-stu-id="70471-382">Is the number of changes to be read in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="70471-383">既定値は **100**です。</span><span class="sxs-lookup"><span data-stu-id="70471-383">The default is **100**.</span></span>  
  
 <span data-ttu-id="70471-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="70471-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span></span>  
 <span data-ttu-id="70471-385">サブスクライバーからパブリッシャーに変更をアップロードする間に、1 つのバッチで適用される変更の数です。</span><span class="sxs-lookup"><span data-stu-id="70471-385">Is the number of changes to be applied in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="70471-386">既定値は **100**です。</span><span class="sxs-lookup"><span data-stu-id="70471-386">The default is **100**.</span></span>  
  
 <span data-ttu-id="70471-387">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="70471-387">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="70471-388">マージ エージェントでスナップショット ファイルをサブスクライバーに適用するときに BULK INSERT コマンドを使用することによって、初期スナップショットのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="70471-388">Improves the performance of the initial snapshot by causing the Merge Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="70471-389">このパラメーターは XML データ型との互換性がないため非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="70471-389">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="70471-390">XML データをレプリケートしない場合にのみ、このパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="70471-390">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="70471-391">このパラメーターは、キャラクター モードのスナップショットでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="70471-391">This parameter cannot be used with character mode snapshots.</span></span> <span data-ttu-id="70471-392">このパラメーターを使用する場合は、サブスクライバー側の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントに、スナップショットの .bcp データ ファイルが格納されたディレクトリの読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="70471-392">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="70471-393">このパラメーターを使用しない場合、エージェントによって読み込まれた ODBC ドライバーがファイルから読み取るので、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストは使用されません。</span><span class="sxs-lookup"><span data-stu-id="70471-393">When this parameter is not used, the ODBC driver loaded by the agent reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="70471-394">**-Validate** [**0**|**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="70471-394">**-Validate** [**0**|**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="70471-395">マージ セッションの最後に検証を行うかどうかを指定し、行う場合は検証の種類も指定します。</span><span class="sxs-lookup"><span data-stu-id="70471-395">Specifies whether validation should be done at the end of the merge session, and, if so, what type of validation.</span></span> <span data-ttu-id="70471-396">推奨値は **3** です。</span><span class="sxs-lookup"><span data-stu-id="70471-396">The value of **3** is the recommended value.</span></span>  
  
|<span data-ttu-id="70471-397">Validate の値</span><span class="sxs-lookup"><span data-stu-id="70471-397">Validate value</span></span>|<span data-ttu-id="70471-398">説明</span><span class="sxs-lookup"><span data-stu-id="70471-398">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="70471-399">**0** (既定値)</span><span class="sxs-lookup"><span data-stu-id="70471-399">**0** (default)</span></span>|<span data-ttu-id="70471-400">検証なし。</span><span class="sxs-lookup"><span data-stu-id="70471-400">No validation.</span></span>|  
|<span data-ttu-id="70471-401">**1**</span><span class="sxs-lookup"><span data-stu-id="70471-401">**1**</span></span>|<span data-ttu-id="70471-402">行数のみの検証。</span><span class="sxs-lookup"><span data-stu-id="70471-402">Rowcount-only validation.</span></span>|  
|<span data-ttu-id="70471-403">**2**</span><span class="sxs-lookup"><span data-stu-id="70471-403">**2**</span></span>|<span data-ttu-id="70471-404">行数とチェックサムの検証。</span><span class="sxs-lookup"><span data-stu-id="70471-404">Rowcount and checksum validation.</span></span>|  
|<span data-ttu-id="70471-405">**3**</span><span class="sxs-lookup"><span data-stu-id="70471-405">**3**</span></span>|<span data-ttu-id="70471-406">行数とバイナリ チェックサムの検証。</span><span class="sxs-lookup"><span data-stu-id="70471-406">Rowcount and binary checksum validation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="70471-407">バイナリ チェックサムまたはチェックサムを使用した検証では、データ型がサブスクライバー側とパブリッシャー側とで異なる場合には、誤ってエラーを報告することがあります。</span><span class="sxs-lookup"><span data-stu-id="70471-407">Validation by using binary checksum or checksum can incorrectly report a failure if data types are different at the Subscriber than they are at the Publisher.</span></span> <span data-ttu-id="70471-408">詳細については、「[レプリケートされたデータの検証](../validate-data-at-the-subscriber.md)」の「データ検証に関する注意点」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70471-408">For more information, see the section "Considerations for Data Validation" in [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="70471-409">**-ValidateInterval** _validate_interval_</span><span class="sxs-lookup"><span data-stu-id="70471-409">**-ValidateInterval** _validate_interval_</span></span>  
 <span data-ttu-id="70471-410">サブスクリプションが継続モードで検証される間隔 (分) です。</span><span class="sxs-lookup"><span data-stu-id="70471-410">Is how often, in minutes, the subscription is validated in continuous mode.</span></span> <span data-ttu-id="70471-411">既定値は **60** 分です。</span><span class="sxs-lookup"><span data-stu-id="70471-411">The default is **60** minutes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70471-412">解説</span><span class="sxs-lookup"><span data-stu-id="70471-412">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70471-413">ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントがインストールされている場合、サービスがアクセスできるのはローカル コンピューターのみです。</span><span class="sxs-lookup"><span data-stu-id="70471-413">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="70471-414">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントの下で実行するマージ エージェントで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]へのログイン時に Windows 認証モードが使用されるように構成すると、マージ エージェントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="70471-414">If the Merge Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Merge Agent fails.</span></span> <span data-ttu-id="70471-415">既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。</span><span class="sxs-lookup"><span data-stu-id="70471-415">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="70471-416">マージ エージェントを起動するには、コマンド プロンプトから **replmerg.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="70471-416">To start the Merge Agent, execute **replmerg.exe** from the command prompt.</span></span> <span data-ttu-id="70471-417">詳細については、「 [レプリケーション エージェント実行可能ファイルのプログラミング](../concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70471-417">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
 <span data-ttu-id="70471-418">現在のセッションのマージ エージェントの履歴は、連続モードでの実行中には削除されません。</span><span class="sxs-lookup"><span data-stu-id="70471-418">The merge agent history for the current session is not removed while running in continuous mode.</span></span> <span data-ttu-id="70471-419">エージェントが長時間実行されると、マージ履歴テーブルに多数のエントリが発生し、パフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70471-419">A long running agent can result in a large number of entries in the merge history tables which could impact performance.</span></span> <span data-ttu-id="70471-420">この問題を解決するには、スケジュールされたモードに切り替えるか、引き続き連続モードを使用する場合は、定期的にマージ エージェントを再起動するための専用のジョブを作成するか、履歴の詳細レベルを下げて行数を減らして、パフォーマンスへの影響を軽減してください。</span><span class="sxs-lookup"><span data-stu-id="70471-420">To resolve this problem switch to scheduled mode, or continue to use continuous mode but create a dedicated job to periodically restart the merge agent, or reduce the verbosity of the history level to reduce the number of rows and therefor reduce the performance impact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70471-421">参照</span><span class="sxs-lookup"><span data-stu-id="70471-421">See Also</span></span>  
 [<span data-ttu-id="70471-422">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="70471-422">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
