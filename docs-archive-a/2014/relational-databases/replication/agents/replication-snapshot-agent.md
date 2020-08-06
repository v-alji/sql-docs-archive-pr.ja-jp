---
title: レプリケーション スナップショット エージェント | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a26aca7b33a7355500350572ea5e8ed21bddeacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632408"
---
# <a name="replication-snapshot-agent"></a><span data-ttu-id="9f49d-102">レプリケーション スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="9f49d-102">Replication Snapshot Agent</span></span>
  <span data-ttu-id="9f49d-103">レプリケーション スナップショット エージェントは、パブリッシュされたテーブルおよびデータベース オブジェクトのスキーマとデータを含むスナップショット ファイルを作成し、これらのファイルをスナップショット フォルダーに格納し、同期ジョブをディストリビューション データベースに記録する実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-103">The Replication Snapshot Agent is an executable file that prepares snapshot files containing schema and data of published tables and database objects, stores the files in the snapshot folder, and records synchronization jobs in the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f49d-104">パラメーターは任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-104">Parameters can be specified in any order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f49d-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f49d-105">Syntax</span></span>  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f49d-106">引数</span><span class="sxs-lookup"><span data-stu-id="9f49d-106">Arguments</span></span>  
 <span data-ttu-id="9f49d-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="9f49d-107">**-?**</span></span>  
 <span data-ttu-id="9f49d-108">使用できるすべてのパラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-108">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="9f49d-109">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="9f49d-109">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="9f49d-110">パブリッシャーの名前です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-110">Is the name of the Publisher.</span></span> <span data-ttu-id="9f49d-111">サーバー上の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-111">Specify server_name for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="9f49d-112">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-112">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="9f49d-113">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="9f49d-113">**-Publication** _publication_</span></span>  
 <span data-ttu-id="9f49d-114">パブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-114">Is the name of the publication.</span></span> <span data-ttu-id="9f49d-115">このパラメーターは、新規または再初期化されたサブスクリプションのスナップショットを常に利用できるようにパブリケーションを設定している場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-115">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="9f49d-116">**-70Subscribers**</span><span class="sxs-lookup"><span data-stu-id="9f49d-116">**-70Subscribers**</span></span>  
 <span data-ttu-id="9f49d-117">いずれかのサブスクライバーで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 が動作している場合に、必ず使用します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-117">Must be used if any Subscribers are running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version 7.0.</span></span>  
  
 <span data-ttu-id="9f49d-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span><span class="sxs-lookup"><span data-stu-id="9f49d-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span></span>  
 <span data-ttu-id="9f49d-119">一括コピー操作によって送られる行の数です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-119">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="9f49d-120">**bcp in** 操作を実行する場合、バッチ サイズは 1 つのトランザクションとしてサーバーに送る行数です。ディストリビューション エージェントが **bcp** 実行状況メッセージをログに記録する前に、これらの行数を送る必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f49d-120">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="9f49d-121">**bcp out** 操作を実行する場合は、固定バッチ サイズ 1000 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-121">When performing a **bcp out** operation, a fixed batch size of 1000 is used.</span></span> <span data-ttu-id="9f49d-122">値 0 は、メッセージをログに記録しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-122">A value of 0 indicates no message logging.</span></span>  
  
 <span data-ttu-id="9f49d-123">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="9f49d-123">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="9f49d-124">エージェント定義ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-124">Is the path of the agent definition file.</span></span> <span data-ttu-id="9f49d-125">エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-125">An agent definition file contains command line arguments for the agent.</span></span> <span data-ttu-id="9f49d-126">ファイルの内容は実行可能ファイルとして解析されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-126">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="9f49d-127">二重引用符 (") を使用して、任意の文字を含む引数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-127">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="9f49d-128">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="9f49d-128">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="9f49d-129">ディストリビューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-129">Is the Distributor name.</span></span> <span data-ttu-id="9f49d-130">サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-130">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="9f49d-131">サーバー上の _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-131">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="9f49d-132">**-DistributorDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-132">**-DistributorDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="9f49d-133">デッドロックが発生した場合のディストリビューターへのスナップショット エージェント接続の優先度です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-133">Is the priority of the Snapshot Agent connection to the Distributor when a deadlock occurs.</span></span> <span data-ttu-id="9f49d-134">このパラメーターは、スナップショットの生成中にスナップショット エージェントとユーザー アプリケーション間で発生する可能性のあるデッドロックを解決するために指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-134">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="9f49d-135">DistributorDeadlockPriority の値</span><span class="sxs-lookup"><span data-stu-id="9f49d-135">DistributorDeadlockPriority value</span></span>|<span data-ttu-id="9f49d-136">説明</span><span class="sxs-lookup"><span data-stu-id="9f49d-136">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="9f49d-137">**-1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-137">**-1**</span></span>|<span data-ttu-id="9f49d-138">ディストリビューター側でデッドロックが発生した場合、スナップショット エージェント以外のアプリケーションが優先されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-138">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Distributor.</span></span>|  
|<span data-ttu-id="9f49d-139">**0** (既定値)</span><span class="sxs-lookup"><span data-stu-id="9f49d-139">**0** (Default)</span></span>|<span data-ttu-id="9f49d-140">優先度は割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="9f49d-140">Priority is not assigned.</span></span>|  
|<span data-ttu-id="9f49d-141">**1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-141">**1**</span></span>|<span data-ttu-id="9f49d-142">ディストリビューター側でデッドロックが発生した場合、スナップショット エージェントが優先されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-142">Snapshot Agent has priority when a deadlock occurs at the Distributor.</span></span>|  
  
 <span data-ttu-id="9f49d-143">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="9f49d-143">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="9f49d-144">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してディストリビューターに接続するときに使用されるログインです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-144">Is the login used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="9f49d-145">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="9f49d-145">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="9f49d-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してディストリビューターに接続するときに使用されるパスワードです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-146">Is the password used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9f49d-147">.</span><span class="sxs-lookup"><span data-stu-id="9f49d-147">.</span></span>  
  
 <span data-ttu-id="9f49d-148">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-148">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="9f49d-149">ディストリビューターのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-149">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="9f49d-150">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-150">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="9f49d-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span><span class="sxs-lookup"><span data-stu-id="9f49d-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span></span>  
 <span data-ttu-id="9f49d-152">動的スナップショットの作成時に、フィルター選択用の [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) の値を設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-152">Is used to set a value for [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="9f49d-153">たとえば、アーティクルに対してサブセット フィルター句 `rep_id = HOST_NAME()` を指定し、 **DynamicFilterHostName** プロパティを "FBJones" に設定した後でマージ エージェントを呼び出すと、 **rep_id** 列に "FBJones" が含まれる行だけがレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-153">For example, if the subset filter clause `rep_id = HOST_NAME()` is specified for an article, and you set the **DynamicFilterHostName** property to "FBJones" before calling the Merge Agent, only rows having "FBJones" in the **rep_id** column will be replicated.</span></span>  
  
 <span data-ttu-id="9f49d-154">**-DynamicFilterLogin** _dynamic_filter_login_</span><span class="sxs-lookup"><span data-stu-id="9f49d-154">**-DynamicFilterLogin** _dynamic_filter_login_</span></span>  
 <span data-ttu-id="9f49d-155">動的スナップショットの作成時に、フィルター選択用の [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) の値を設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-155">Is used to set a value for [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql)in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="9f49d-156">たとえば、アーティクルに対してサブセット フィルター句 `user_id = SUSER_SNAME()` を指定し、 **DynamicFilterLogin** プロパティを "rsmith" に設定した後で、 **SQLSnapshot** オブジェクトの **Run** メソッドを呼び出すと、 **user_id** 列に "rsmith" を含む行だけがスナップショットに含められます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-156">For example, if the subset filter clause `user_id = SUSER_SNAME()` is specified for an article, and you set the **DynamicFilterLogin** property to "rsmith" before calling the **Run** method of the **SQLSnapshot** object, only rows having "rsmith" in the **user_id** column will be included in the snapshot.</span></span>  
  
 <span data-ttu-id="9f49d-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="9f49d-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="9f49d-158">動的スナップショットの生成先の場所です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-158">Is the location where the dynamic snapshot should be generated.</span></span>  
  
 <span data-ttu-id="9f49d-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="9f49d-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="9f49d-160">スナップショット エージェントが接続時に使用する SSL (Secure Sockets Layer) 暗号化レベルです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-160">Is the level of Secure Sockets Layer (SSL) encryption used by the Snapshot Agent when making connections.</span></span>  
  
|<span data-ttu-id="9f49d-161">EncryptionLevel の値</span><span class="sxs-lookup"><span data-stu-id="9f49d-161">EncryptionLevel value</span></span>|<span data-ttu-id="9f49d-162">説明</span><span class="sxs-lookup"><span data-stu-id="9f49d-162">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="9f49d-163">**0**</span><span class="sxs-lookup"><span data-stu-id="9f49d-163">**0**</span></span>|<span data-ttu-id="9f49d-164">SSL は使用されません。</span><span class="sxs-lookup"><span data-stu-id="9f49d-164">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="9f49d-165">**1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-165">**1**</span></span>|<span data-ttu-id="9f49d-166">SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="9f49d-166">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="9f49d-167">**2**</span><span class="sxs-lookup"><span data-stu-id="9f49d-167">**2**</span></span>|<span data-ttu-id="9f49d-168">SSL が使用され、証明書の確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-168">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="9f49d-169">有効な SSL 証明書には、SQL Server の完全修飾ドメイン名が定義されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-169">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="9f49d-170">-EncryptionLevel を 2 に設定したときにエージェントが正しく接続されるようにするには、ローカルの SQL Server 上に別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-170">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="9f49d-171">'Alias Name' パラメーターはサーバー名にし、'Server' パラメーターは SQL Server の完全修飾名に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f49d-171">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="9f49d-172">詳細については、「 [SQL Server レプリケーションセキュリティ](../security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f49d-172">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="9f49d-173">**-FieldDelimiter** _field_delimiter_</span><span class="sxs-lookup"><span data-stu-id="9f49d-173">**-FieldDelimiter** _field_delimiter_</span></span>  
 <span data-ttu-id="9f49d-174">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一括コピーで扱うデータ ファイルのフィールドの末尾を示す 1 文字または文字列です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-174">Is the character or character sequence that marks the end of a field in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="9f49d-175">既定値は \n\<x$3>\n です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-175">The default is \n\<x$3>\n.</span></span>  
  
 <span data-ttu-id="9f49d-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="9f49d-177">スナップショット操作中にログに記録する履歴の量を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-177">Specifies the amount of history logged during a snapshot operation.</span></span> <span data-ttu-id="9f49d-178">**1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-178">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="9f49d-179">HistoryVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="9f49d-179">HistoryVerboseLevel value</span></span>|<span data-ttu-id="9f49d-180">説明</span><span class="sxs-lookup"><span data-stu-id="9f49d-180">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="9f49d-181">**0**</span><span class="sxs-lookup"><span data-stu-id="9f49d-181">**0**</span></span>|<span data-ttu-id="9f49d-182">進行状況メッセージがコンソールまたは出力ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-182">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="9f49d-183">履歴レコードは、ディストリビューション データベースのログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="9f49d-183">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="9f49d-184">**1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-184">**1**</span></span>|<span data-ttu-id="9f49d-185">同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-185">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="9f49d-186">前回の記録に同じ状態がない場合は、新しい記録を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-186">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="9f49d-187">**2** (既定値)</span><span class="sxs-lookup"><span data-stu-id="9f49d-187">**2** (default)</span></span>|<span data-ttu-id="9f49d-188">アイドル状態や長時間実行を示すメッセージでない場合、新しい履歴レコードを挿入します。アイドル状態などを示すメッセージの場合には、以前のレコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-188">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="9f49d-189">**3**</span><span class="sxs-lookup"><span data-stu-id="9f49d-189">**3**</span></span>|<span data-ttu-id="9f49d-190">アイドル状態を示すメッセージの場合以外は、常に新しいレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-190">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="9f49d-191">**-HRBcpBlocks** _number_of_blocks_</span><span class="sxs-lookup"><span data-stu-id="9f49d-191">**-HRBcpBlocks** _number_of_blocks_</span></span>  
 <span data-ttu-id="9f49d-192">ライター スレッドとリーダー スレッド間でキューに格納される **bcp** データ ブロックの数です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-192">Is the number of **bcp** data blocks that are queued between the writer and reader threads.</span></span> <span data-ttu-id="9f49d-193">既定値は 50 です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-193">The default value is 50.</span></span> <span data-ttu-id="9f49d-194">**HRBcpBlocks** は、Oracle パブリケーションでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-194">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f49d-195">このパラメーターは、Oracle パブリッシャーから **bcp** パフォーマンスのチューニングを行う場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-195">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="9f49d-196">-**Hrbcpblocksize**_block_size_</span><span class="sxs-lookup"><span data-stu-id="9f49d-196">-**HRBcpBlockSize**_block_size_</span></span>  
 <span data-ttu-id="9f49d-197">各 **bcp** データ ブロックのサイズ (KB) です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-197">Is the size, in kilobytes (KB), of each **bcp** data block.</span></span> <span data-ttu-id="9f49d-198">既定値は 64 KB です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-198">The default value is 64 KB.</span></span> <span data-ttu-id="9f49d-199">**HRBcpBlocks** は、Oracle パブリケーションでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-199">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f49d-200">このパラメーターは、Oracle パブリッシャーから **bcp** パフォーマンスのチューニングを行う場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-200">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="9f49d-201">**-HRBcpDynamicBlocks**</span><span class="sxs-lookup"><span data-stu-id="9f49d-201">**-HRBcpDynamicBlocks**</span></span>  
 <span data-ttu-id="9f49d-202">各 **bcp** データ ブロックのサイズが動的に拡張可能かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-202">Is whether or not the size of each **bcp** data block can grow dynamically.</span></span> <span data-ttu-id="9f49d-203">**HRBcpBlocks** は、Oracle パブリケーションでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-203">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f49d-204">このパラメーターは、Oracle パブリッシャーから **bcp** パフォーマンスのチューニングを行う場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-204">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="9f49d-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span><span class="sxs-lookup"><span data-stu-id="9f49d-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span></span>  
 <span data-ttu-id="9f49d-206">[MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) テーブルに "waiting for backend message" が記録されるまでのスナップショット エージェントの待機時間 (秒) です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-206">Is the amount of time, in seconds, that the Snapshot Agent waits before logging "waiting for backend message" to the [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) table.</span></span> <span data-ttu-id="9f49d-207">既定値は 300 秒です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-207">The default value is 300 seconds.</span></span>  
  
 <span data-ttu-id="9f49d-208">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="9f49d-208">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="9f49d-209">ログインがタイムアウトになるまでの秒数です。既定値は **15** 秒です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-209">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="9f49d-210">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="9f49d-210">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="9f49d-211">並列実行できる一括コピーの操作数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-211">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="9f49d-212">同時に存在するスレッドと ODBC 接続の最大数は、 **MaxBcpThreads** の値と、ディストリビューション データベースの同期トランザクションに示されている一括コピー要求の数の小さい方の値になります。</span><span class="sxs-lookup"><span data-stu-id="9f49d-212">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="9f49d-213">**MaxBcpThreads** は **0** よりも大きくする必要があり、上限はありません。</span><span class="sxs-lookup"><span data-stu-id="9f49d-213">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="9f49d-214">既定値は **1**です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-214">The default is **1**.</span></span>  
  
 <span data-ttu-id="9f49d-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span></span>  
 <span data-ttu-id="9f49d-216">無関係な削除がサブスクライバーに送られたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-216">Is if irrelevant deletes are sent to the Subscriber.</span></span> <span data-ttu-id="9f49d-217">無関係な削除とは、サブスクライバーのパーティションに属さない行に対する DELETE コマンドがサブスクライバーに送られたことを表します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-217">Irrelevant deletes are DELETE commands that are sent to Subscribers for rows that do not belong to the Subscriber's partition.</span></span> <span data-ttu-id="9f49d-218">無関係な削除はデータの整合性や収束には影響しませんが、不要なネットワーク トラフィックを生じます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-218">Irrelevant deletes do not affect data integrity or convergence, but they can result in unnecessary network traffic.</span></span> <span data-ttu-id="9f49d-219">**MaxNetworkOptimization** の既定値は **0**です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-219">The default value of **MaxNetworkOptimization** is **0**.</span></span> <span data-ttu-id="9f49d-220">**MaxNetworkOptimization** を **1** に設定すると、無関係な削除が発生する可能性が最小限に抑えられ、ネットワーク トラフィックが減少し、最もネットワークが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-220">Setting **MaxNetworkOptimization** to **1** minimizing the chances of irrelevant deletes thereby reducing network traffic and maximizing network optimization.</span></span> <span data-ttu-id="9f49d-221">ただし、このパラメーターを **1** に設定するとメタデータの保存領域が増加するため、複数レベルの結合フィルターと複雑なサブセット フィルターが存在する場合、パブリッシャーのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-221">Setting this parameter to **1** can also increase the storage of metadata and cause performance to degrade at the Publisher if multiple levels of join filters and complex subset filters are present.</span></span> <span data-ttu-id="9f49d-222">レプリケーション トポロジを慎重に評価する必要があります。無関係な削除によるネットワーク トラフィックが容認できないほど大きい場合に限り、 **MaxNetworkOptimization** を **1** に設定してください。</span><span class="sxs-lookup"><span data-stu-id="9f49d-222">You should carefully assess your replication topology and set **MaxNetworkOptimization** to **1** only if network traffic from irrelevant deletes is unacceptably high.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f49d-223">このパラメーターを**1**に設定すると、マージパブリケーションの同期最適化オプションが**true**に設定されている場合にのみ役立ち **@keep_partition_changes** ます ( [sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)のパラメーター)。</span><span class="sxs-lookup"><span data-stu-id="9f49d-223">Setting this parameter to **1** is useful only when the synchronization optimization option of the merge publication is set to **true** (the **@keep_partition_changes** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).</span></span>  
  
 <span data-ttu-id="9f49d-224">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="9f49d-224">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="9f49d-225">エージェントの出力ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-225">Is the path of the agent output file.</span></span> <span data-ttu-id="9f49d-226">ファイル名が指定されていない場合、出力はコンソールに送られます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-226">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="9f49d-227">指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-227">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="9f49d-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="9f49d-229">出力を詳細表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-229">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="9f49d-230">OutputVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="9f49d-230">OutputVerboseLevel value</span></span>|<span data-ttu-id="9f49d-231">説明</span><span class="sxs-lookup"><span data-stu-id="9f49d-231">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9f49d-232">**0**</span><span class="sxs-lookup"><span data-stu-id="9f49d-232">**0**</span></span>|<span data-ttu-id="9f49d-233">エラー メッセージのみが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-233">Only error messages are printed.</span></span>|  
|<span data-ttu-id="9f49d-234">**1** (既定値)</span><span class="sxs-lookup"><span data-stu-id="9f49d-234">**1** (default)</span></span>|<span data-ttu-id="9f49d-235">すべての進行状況レポート メッセージが出力されます (既定)。</span><span class="sxs-lookup"><span data-stu-id="9f49d-235">All the progress report messages are printed (default).</span></span>|  
|<span data-ttu-id="9f49d-236">**2**</span><span class="sxs-lookup"><span data-stu-id="9f49d-236">**2**</span></span>|<span data-ttu-id="9f49d-237">すべてのエラー メッセージと進行状況レポート メッセージが出力されます。これはデバッグの際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-237">All error messages and progress report messages are printed, which is useful for debugging.</span></span>|  

 <span data-ttu-id="9f49d-238">**-PrefetchTables** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-238">**-PrefetchTables** [ **0**| **1**]</span></span>  
 <span data-ttu-id="9f49d-239">テーブル オブジェクトがプリフェッチされてキャッシュされるかどうかを指定する、省略可能なパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-239">Optional parameter that specifies if the table objects will be prefetched and cached.</span></span>  <span data-ttu-id="9f49d-240">既定の動作では、内部の計算に基づき SMO コンポーネントを使用して特定のテーブルのプロパティがプリフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-240">The default behavior is to prefetch certain table properties using SMO component based on an internal calculation.</span></span>  <span data-ttu-id="9f49d-241">このパラメーターは、SMO のプリフェッチ操作の実行にかなりの時間がかかるシナリオで役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="9f49d-241">This parameter can be helpful in scenarios where SMO prefetch operation takes considerable longer to run.</span></span> <span data-ttu-id="9f49d-242">このパラメーターを使用しない場合は、パブリケーションにアーティクルとして追加されるテーブルの割合に基づいて、実行時にこの決定が行われます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-242">If this parameter is not used, this decision is made at runtime based on the percentage of tables that are added as articles to the publication.</span></span>  
  
|<span data-ttu-id="9f49d-243">OutputVerboseLevel の値</span><span class="sxs-lookup"><span data-stu-id="9f49d-243">OutputVerboseLevel value</span></span>|<span data-ttu-id="9f49d-244">説明</span><span class="sxs-lookup"><span data-stu-id="9f49d-244">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9f49d-245">**0**</span><span class="sxs-lookup"><span data-stu-id="9f49d-245">**0**</span></span>|<span data-ttu-id="9f49d-246">SMO コンポーネントのプリフェッチ メソッドの呼び出しは無効です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-246">Call to Prefetch method of SMO component is disabled.</span></span>|  
|<span data-ttu-id="9f49d-247">**1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-247">**1**</span></span>|<span data-ttu-id="9f49d-248">スナップショット エージェントはプリフェッチ メソッドを呼び出し、SMO を使用していくつかのテーブルのプロパティをキャッシュします</span><span class="sxs-lookup"><span data-stu-id="9f49d-248">Snapshot Agent will call Prefetch method to cache some table properties using SMO</span></span>|  
  
 <span data-ttu-id="9f49d-249">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="9f49d-249">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="9f49d-250">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]への接続中にスナップショット エージェントが使用するパケット サイズ (バイト) です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-250">Is the packet size (in bytes) used by the Snapshot Agent when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9f49d-251">既定値は 8,192 バイトです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-251">The default value is 8192 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f49d-252">パフォーマンスの向上が明確でない限り、パケット サイズは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f49d-252">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="9f49d-253">多くのアプリケーションでは、既定のパケット サイズが最適です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-253">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="9f49d-254">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="9f49d-254">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="9f49d-255">エージェント パラメーターに使用するエージェント プロファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-255">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="9f49d-256">**ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="9f49d-256">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="9f49d-257">**ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-257">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="9f49d-258">詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f49d-258">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="9f49d-259">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="9f49d-259">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="9f49d-260">パブリケーション データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-260">Is the name of the publication database.</span></span> <span data-ttu-id="9f49d-261">*このパラメーターは、Oracle パブリッシャーについてはサポートされません。*</span><span class="sxs-lookup"><span data-stu-id="9f49d-261">*This parameter is not supported for Oracle Publishers*.</span></span>  
  
 <span data-ttu-id="9f49d-262">**-PublisherDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-262">**-PublisherDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="9f49d-263">デッドロックが発生した場合のパブリッシャーへのスナップショット エージェント接続の優先度です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-263">Is the priority of the Snapshot Agent connection to the Publisher when a deadlock occurs.</span></span> <span data-ttu-id="9f49d-264">このパラメーターは、スナップショットの生成中にスナップショット エージェントとユーザー アプリケーション間で発生する可能性のあるデッドロックを解決するために指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-264">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="9f49d-265">PublisherDeadlockPriority の値</span><span class="sxs-lookup"><span data-stu-id="9f49d-265">PublisherDeadlockPriority value</span></span>|<span data-ttu-id="9f49d-266">説明</span><span class="sxs-lookup"><span data-stu-id="9f49d-266">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="9f49d-267">**-1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-267">**-1**</span></span>|<span data-ttu-id="9f49d-268">パブリッシャー側でデッドロックが発生した場合、スナップショット エージェント以外のアプリケーションが優先されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-268">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Publisher.</span></span>|  
|<span data-ttu-id="9f49d-269">**0** (既定値)</span><span class="sxs-lookup"><span data-stu-id="9f49d-269">**0** (Default)</span></span>|<span data-ttu-id="9f49d-270">優先度は割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="9f49d-270">Priority is not assigned.</span></span>|  
|<span data-ttu-id="9f49d-271">**1**</span><span class="sxs-lookup"><span data-stu-id="9f49d-271">**1**</span></span>|<span data-ttu-id="9f49d-272">パブリッシャー側でデッドロックが発生した場合、スナップショット エージェントが優先されます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-272">Snapshot Agent has priority when a deadlock occurs at the Publisher.</span></span>|  
  
 <span data-ttu-id="9f49d-273">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="9f49d-273">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="9f49d-274">パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-274">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="9f49d-275">詳細については、「 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9f49d-275">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="9f49d-276">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="9f49d-276">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="9f49d-277">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してパブリッシャーに接続するときに使用されるログインです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-277">Is the login used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="9f49d-278">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="9f49d-278">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="9f49d-279">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してパブリッシャーに接続するときに使用されるパスワードです。</span><span class="sxs-lookup"><span data-stu-id="9f49d-279">Is the password used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9f49d-280">.</span><span class="sxs-lookup"><span data-stu-id="9f49d-280">.</span></span>  
  
 <span data-ttu-id="9f49d-281">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-281">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="9f49d-282">パブリッシャーのセキュリティ モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-282">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="9f49d-283">値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-283">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="9f49d-284">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="9f49d-284">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="9f49d-285">クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-285">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="9f49d-286">**-ReplicationType** [ **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="9f49d-286">**-ReplicationType** [ **1**| **2**]</span></span>  
 <span data-ttu-id="9f49d-287">レプリケーションの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-287">Specifies the type of replication.</span></span> <span data-ttu-id="9f49d-288">値 **1** はトランザクション レプリケーションを示し、値 **2** はマージ レプリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-288">A value of **1** indicates transactional replication, and a value of **2** indicates merge replication.</span></span>  
  
 <span data-ttu-id="9f49d-289">**-RowDelimiter** _row_delimiter_</span><span class="sxs-lookup"><span data-stu-id="9f49d-289">**-RowDelimiter** _row_delimiter_</span></span>  
 <span data-ttu-id="9f49d-290">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一括コピーで扱うデータ ファイルの各行の末尾を示す 1 文字または文字列です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-290">Is the character or character sequence that marks the end of a row in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="9f49d-291">既定値は \n\<,@g>\n です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-291">The default is \n\<,@g>\n.</span></span>  
  
 <span data-ttu-id="9f49d-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="9f49d-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="9f49d-293">実行中の同時実行動的スナップショット処理の数が、 **@max_concurrent_dynamic_snapshots** [Sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)のプロパティによって設定された制限値に達したときに、スナップショットエージェントが待機する最大秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-293">Is the maximum number of seconds that the Snapshot Agent waits when the number of concurrent dynamic snapshot processes running is at the limit set by the **@max_concurrent_dynamic_snapshots** property of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="9f49d-294">最大秒数に達したときにスナップショット エージェントがまだ待機している場合、スナップショット エージェントは待機を終了します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-294">If the maximum number of seconds is reached and the Snapshot Agent is still waiting, it will exit.</span></span> <span data-ttu-id="9f49d-295">値が 0 の場合は、このエージェントが無期限に待機することを意味しますが、取り消すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-295">A value of 0 means that the agent waits indefinitely, although it can be canceled.</span></span>  
  
 <span data-ttu-id="9f49d-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span><span class="sxs-lookup"><span data-stu-id="9f49d-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span></span>  
 <span data-ttu-id="9f49d-297">このパラメーターは非推奨とされます。旧バージョンとの互換性のためにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9f49d-297">This parameter has been deprecated and is supported for backward-compatibility only.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f49d-298">解説</span><span class="sxs-lookup"><span data-stu-id="9f49d-298">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f49d-299">ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントをインストールした場合、サービスはローカル コンピューターにだけアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9f49d-299">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a Local System account rather than under a Domain User account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="9f49d-300">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント下で実行するスナップショット エージェントで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]へのログイン時に Windows 認証モードを使用するように構成すると、スナップショット エージェントは異常終了します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-300">If the Snapshot Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Snapshot Agent fails.</span></span> <span data-ttu-id="9f49d-301">既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。</span><span class="sxs-lookup"><span data-stu-id="9f49d-301">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="9f49d-302">スナップショット エージェントを開始するには、コマンド プロンプトから **snapshot.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="9f49d-302">To start the Snapshot Agent, execute **snapshot.exe** from the command prompt.</span></span> <span data-ttu-id="9f49d-303">詳細については、「 [レプリケーション エージェント実行可能ファイルのプログラミング](../concepts/replication-agent-executables-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f49d-303">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f49d-304">参照</span><span class="sxs-lookup"><span data-stu-id="9f49d-304">See Also</span></span>  
 [<span data-ttu-id="9f49d-305">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="9f49d-305">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
