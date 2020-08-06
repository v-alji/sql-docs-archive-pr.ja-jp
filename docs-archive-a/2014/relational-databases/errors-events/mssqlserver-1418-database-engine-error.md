---
title: MSSQLSERVER_1418 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1418 (Database Engine error)
ms.assetid: 6e9c7241-0201-44e0-9f8b-b3c4e293f0f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1fcac03f044aacce5e907824862eb589c97a07d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718206"
---
# <a name="mssqlserver_1418"></a><span data-ttu-id="d6250-102">MSSQLSERVER_1418</span><span class="sxs-lookup"><span data-stu-id="d6250-102">MSSQLSERVER_1418</span></span>
    
## <a name="details"></a><span data-ttu-id="d6250-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d6250-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6250-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d6250-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="d6250-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d6250-105">Event ID</span></span>|<span data-ttu-id="d6250-106">1418</span><span class="sxs-lookup"><span data-stu-id="d6250-106">1418</span></span>|  
|<span data-ttu-id="d6250-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d6250-107">Event Source</span></span>|<span data-ttu-id="d6250-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d6250-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d6250-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d6250-109">Component</span></span>|<span data-ttu-id="d6250-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d6250-110">SQLEngine</span></span>|  
|<span data-ttu-id="d6250-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d6250-111">Symbolic Name</span></span>|<span data-ttu-id="d6250-112">DBM_PARTNERNOTFOUND</span><span class="sxs-lookup"><span data-stu-id="d6250-112">DBM_PARTNERNOTFOUND</span></span>|  
|<span data-ttu-id="d6250-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d6250-113">Message Text</span></span>|<span data-ttu-id="d6250-114">サーバー ネットワーク アドレス "%.\*ls" にアクセスできないか、このアドレスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="d6250-114">The server network address "%.\*ls" can not be reached or does not exist.</span></span> <span data-ttu-id="d6250-115">ネットワーク アドレス名と、ローカル エンドポイントおよびリモート エンドポイントのポートが操作可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d6250-115">Check the network address name and that the ports for the local and remote endpoints are operational.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d6250-116">説明</span><span class="sxs-lookup"><span data-stu-id="d6250-116">Explanation</span></span>  
 <span data-ttu-id="d6250-117">指定されたサーバー ネットワーク アドレスにアクセスできないか、このアドレスが存在しないため、サーバー ネットワーク エンドポイントが応答しませんでした。</span><span class="sxs-lookup"><span data-stu-id="d6250-117">The server network endpoint did not respond because the specified server network address cannot be reached or does not exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6250-118">既定では、すべてのポートが [!INCLUDE[msCoName](../../includes/msconame-md.md)] オペレーティング システムによってブロックされます。</span><span class="sxs-lookup"><span data-stu-id="d6250-118">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] operating system blocks all ports.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d6250-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d6250-119">User Action</span></span>  
 <span data-ttu-id="d6250-120">ネットワーク アドレス名が正しいかどうかを確認して、コマンドを再発行します。</span><span class="sxs-lookup"><span data-stu-id="d6250-120">Verify the network address name and reissue the command.</span></span>  
  
 <span data-ttu-id="d6250-121">場合によっては、両方のパートナーで修正措置を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6250-121">Corrective action might be required on both partners.</span></span> <span data-ttu-id="d6250-122">たとえば、プリンシパル サーバー インスタンスで SET PARTNER を実行しようとしたときにこのメッセージが表示された場合、ミラー サーバー インスタンスでのみ修正措置を実行するよう指示されます。</span><span class="sxs-lookup"><span data-stu-id="d6250-122">For example, if this message is raised when you are trying to run SET PARTNER on the principal server instance, the message might imply that you only have to take corrective action on the mirror server instance.</span></span> <span data-ttu-id="d6250-123">しかし、実際には、両方のパートナーで修正措置を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6250-123">However, corrective actions might be required on both partners.</span></span>  
  
### <a name="additional-corrective-actions"></a><span data-ttu-id="d6250-124">その他の修正措置</span><span class="sxs-lookup"><span data-stu-id="d6250-124">Additional Corrective Actions</span></span>  
  
-   <span data-ttu-id="d6250-125">ミラー データベースがミラーリングできる状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-125">Make sure that the mirror database is ready for mirroring.</span></span>  
  
-   <span data-ttu-id="d6250-126">ミラー サーバー インスタンスの名前およびポートが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-126">Make sure that the name and port of the mirror server instance are correct.</span></span>  
  
-   <span data-ttu-id="d6250-127">対象となるミラー サーバー インスタンスがファイアウォールの背後に配置されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-127">Make sure that the destination mirror server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="d6250-128">プリンシパル サーバー インスタンスがファイアウォールの背後に配置されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-128">Make sure that the principal server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="d6250-129">**sys.database_mirroring_endpoints** カタログ ビューの **state** または **state_desc** 列を使用して、両方のパートナーでエンドポイントが開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-129">Verify that the endpoints are started on the partners by using the **state** or **state_desc** column the of the **sys.database_mirroring_endpoints** catalog view.</span></span> <span data-ttu-id="d6250-130">いずれかのエンドポイントが開始されていない場合は、ALTER ENDPOINT ステートメントを実行して開始します。</span><span class="sxs-lookup"><span data-stu-id="d6250-130">If either endpoint is not started, execute an ALTER ENDPOINT statement to start it.</span></span>  
  
-   <span data-ttu-id="d6250-131">プリンシパル サーバー インスタンスがデータベース ミラーリング エンドポイントに割り当てられているポートでリッスンし、ミラー サーバー インスタンスがミラー サーバー インスタンスのポートでリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-131">Make sure that the principal server instance is listening on the port assigned to its database mirroring endpoint and that and the mirror server instance is listening on its port.</span></span> <span data-ttu-id="d6250-132">詳細については、このトピックの「ポートの可用性の検証」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6250-132">For more information, see "Verifying Port Availability," later in this topic.</span></span> <span data-ttu-id="d6250-133">パートナーが割り当てられたポートでリッスンしていない場合は、データベース ミラーリング エンドポイントを変更して、別のポートでリッスンするようにします。</span><span class="sxs-lookup"><span data-stu-id="d6250-133">If a partner is not listening on its assigned port, modify the database mirroring endpoint to listen on a different port.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d6250-134">セキュリティ構成が不適切な場合、一般的なセットアップ エラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d6250-134">Improperly configured security can cause a general setup error message.</span></span> <span data-ttu-id="d6250-135">通常、サーバー インスタンスは無効な接続要求に応答せず、破棄してしまいます。</span><span class="sxs-lookup"><span data-stu-id="d6250-135">Typically, the server instance drops the bad connection request without responding.</span></span> <span data-ttu-id="d6250-136">呼び出し元には、ミラー データベースの状態が正しくない、ミラー データベースが存在しない、権限が不適切など、別のさまざまな理由でセキュリティ構成エラーが発生したように示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d6250-136">To the caller, a security-configuration error could appear to have occurred for a variety of other reasons, such as the mirror database in a bad state or does not exist, incorrect permissions, and so on.</span></span>  
  
### <a name="using-the-error-log-file-for-diagnosis"></a><span data-ttu-id="d6250-137">診断のためのエラー ログ ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="d6250-137">Using the Error Log File for Diagnosis</span></span>  
 <span data-ttu-id="d6250-138">調査のために利用できるのがエラー ログ ファイルだけである場合があります。</span><span class="sxs-lookup"><span data-stu-id="d6250-138">In some cases, only error log files are available for investigation.</span></span> <span data-ttu-id="d6250-139">その場合は、エラー ログを参照し、データベース ミラーリング エンドポイントの TCP ポートに対するエラー メッセージ 26023 が含まれていないかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="d6250-139">In these cases, determine whether the error log contains error message 26023 for the TCP port of the database mirroring endpoint.</span></span> <span data-ttu-id="d6250-140">重大度 16 のこのエラーは、データベース ミラーリング エンドポイントが開始されていないことを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d6250-140">This error, which is severity 16, might indicate that the database mirroring endpoint is not started.</span></span> <span data-ttu-id="d6250-141">これは、**sys.database_mirroring_endpoints** でエンドポイントの状態が開始済みと示されている場合でも発生します。</span><span class="sxs-lookup"><span data-stu-id="d6250-141">This message can occur even if **sys.database_mirroring_endpoints** shows the endpoint state as started.</span></span>  
  
 <span data-ttu-id="d6250-142">発生している問題をすべて解決した後、プリンシパル サーバーで ALTER DATABASE *database_name* SET PARTNER ステートメントを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="d6250-142">After resolving any issues that you encounter, rerun the ALTER DATABASE *database_name* SET PARTNER statement on the principal server.</span></span>  
  
### <a name="verifying-port-availability"></a><span data-ttu-id="d6250-143">ポートの可用性の検証</span><span class="sxs-lookup"><span data-stu-id="d6250-143">Verifying Port Availability</span></span>  
 <span data-ttu-id="d6250-144">データベース ミラーリング セッションのネットワークを構成する際、各サーバー インスタンスのデータベース ミラーリング エンドポイントがデータベース ミラーリング プロセスでのみ使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6250-144">When you are configuring the network for a database mirroring session, make sure the database mirroring endpoint of each server instance is used by only the database mirroring process.</span></span> <span data-ttu-id="d6250-145">データベース ミラーリング エンドポイントに割り当てられたポートで別のプロセスがリッスンしている場合、他のサーバー インスタンスのデータベース ミラーリング プロセスはそのエンドポイントに接続できません。</span><span class="sxs-lookup"><span data-stu-id="d6250-145">If another process is listening on the port assigned to a database mirroring endpoint, the database mirroring processes of the other server instances cannot connect to the endpoint.</span></span>  
  
 <span data-ttu-id="d6250-146">Windows ベースのサーバーがリッスンしているすべてのポートを表示するには、**netstat** コマンド プロンプト ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6250-146">To display all the ports on which a Windows-based server is listening, use the **netstat** command-prompt utility.</span></span> <span data-ttu-id="d6250-147">**netstat** の構文は、Windows オペレーティング システムのバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d6250-147">The syntax for **netstat** depends on the version of the Windows operating system.</span></span> <span data-ttu-id="d6250-148">詳細については、オペレーティング システムのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6250-148">For more information, see the operating system documentation.</span></span>  
  
#### <a name="windows-server-2003-service-pack-1-sp1"></a><span data-ttu-id="d6250-149">Windows Server 2003 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="d6250-149">Windows Server 2003 Service Pack 1 (SP1)</span></span>  
 <span data-ttu-id="d6250-150">リッスンしているポートおよびそれらのポートを開いているプロセスを一覧表示するには、Windows コマンド プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d6250-150">To list listening ports and the processes that have those ports opened, enter the following command at the Windows command prompt:</span></span>  
  
 <span data-ttu-id="d6250-151">**netstat -abn**</span><span class="sxs-lookup"><span data-stu-id="d6250-151">**netstat -abn**</span></span>  
  
#### <a name="windows-server-2003-pre-sp1"></a><span data-ttu-id="d6250-152">Windows Server 2003 (SP1 適用前)</span><span class="sxs-lookup"><span data-stu-id="d6250-152">Windows Server 2003 (pre-SP1)</span></span>  
 <span data-ttu-id="d6250-153">リッスンしているポートおよびそれらのポートを開いているプロセスを確認するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d6250-153">To identify the listening ports and the processes that have those ports opened, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d6250-154">プロセス ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6250-154">Obtain the process ID.</span></span>  
  
     <span data-ttu-id="d6250-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプロセス ID を調べるには、そのインスタンスに接続し、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6250-155">To learn the process ID of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connect to that instance and use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT SERVERPROPERTY('ProcessID')   
    ```  
  
     <span data-ttu-id="d6250-156">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SERVERPROPERTY (Transact-SQL)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6250-156">For more information, see "SERVERPROPERTY (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="d6250-157">取得したプロセス ID と、次の **netstat** コマンドの出力とを照合します。</span><span class="sxs-lookup"><span data-stu-id="d6250-157">Match the process ID with the output of the following **netstat** command:</span></span>  
  
     <span data-ttu-id="d6250-158">**netstat -ano**</span><span class="sxs-lookup"><span data-stu-id="d6250-158">**netstat -ano**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6250-159">参照</span><span class="sxs-lookup"><span data-stu-id="d6250-159">See Also</span></span>  
 <span data-ttu-id="d6250-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6250-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="d6250-161">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d6250-161">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="d6250-162">[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d6250-162">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="d6250-163">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6250-163">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="d6250-164">[サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="d6250-164">[Specify a Server Network Address &#40;Database Mirroring&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="d6250-165">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6250-165">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="d6250-166">データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d6250-166">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
