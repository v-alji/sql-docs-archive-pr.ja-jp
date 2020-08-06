---
title: Azure への管理されたバックアップ SQL Server のトラブルシューティング |Microsoft Docs
description: この記事では、Microsoft Azure 操作のために SQL Server マネージバックアップ中に発生する可能性のあるエラーのトラブルシューティングに使用できるタスクとツールについて説明します。
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: a34d35b0-48eb-4ed1-9f19-ea14754650da
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9c7ed5dd25ed2b02445bfae5eb78ac03b2270552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716574"
---
# <a name="troubleshooting-sql-server-managed--backup-to-azure"></a><span data-ttu-id="17131-103">Azure への SQL Server マネージド バックアップのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="17131-103">Troubleshooting SQL Server Managed  Backup to Azure</span></span>
  <span data-ttu-id="17131-104">このトピックでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の操作中に発生する可能性があるエラーのトラブルシューティングに使用できるツールとタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="17131-104">This topic describes the tasks and tools you can use to troubleshoot errors that may occur during [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="17131-105">概要</span><span class="sxs-lookup"><span data-stu-id="17131-105">Overview</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="17131-106">には、組み込みのチェックとトラブルシューティング機能が用意されているため、多くの場合、内部エラーは [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] プロセス自体によって対処されます。</span><span class="sxs-lookup"><span data-stu-id="17131-106">has built in checks and troubleshooting, so in many cases internal failures are taken care of by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] process itself.</span></span>  
  
 <span data-ttu-id="17131-107">このような場合の例として、バックアップファイルを削除した結果、回復性に影響を与えるログチェーンが壊れている場合は [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 、ログチェーンの中断を特定し、すぐにバックアップを実行するようにスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="17131-107">Example of one such case is a deletion of a backup file resulting in a break of the log chain affecting recoverability - [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will identify the break in log chain and schedule a backup to be taken immediately.</span></span> <span data-ttu-id="17131-108">ただし、状態を監視して、手動による介入を必要とするエラーには対処することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="17131-108">However we recommend that you monitor the status and address any errors that require manual intervention.</span></span>  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="17131-109">では、システム ストアド プロシージャ、システム ビュー、および拡張イベントを使用して、イベントとエラーがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="17131-109">logs events and errors using system stored procedures, system views and extended events.</span></span> <span data-ttu-id="17131-110">システム ビューとストアド プロシージャでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成情報、バックアップの状態、定期的なバックアップ、さらに、拡張イベントによってキャプチャされたエラーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="17131-110">System views and stored procedures provide [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration information, status of backup scheduled backups, and also the errors captured by Extended Events.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="17131-111">は、拡張イベントを使用して、トラブルシューティングに使用するエラーをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="17131-111">uses Extended Events to capture the errors to use for troubleshooting.</span></span> <span data-ttu-id="17131-112">SQL Server Smart Admin ポリシーは、イベントのログ記録に加え、正常性状態も提供します。正常性状態は、通知またはエラーや問題を示すために電子メール通知ジョブで使用されます。</span><span class="sxs-lookup"><span data-stu-id="17131-112">In addition to logging events, SQL Server Smart Admin Policies provide a health status which is used by an email notification job to provide notification or errors and issues.</span></span> <span data-ttu-id="17131-113">詳細については、「 [Monitor SQL Server Managed Backup To Azure」を](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-113">For more information see [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="17131-114">では、Azure storage に手動でバックアップするときに使用するのと同じログ記録も使用されます (SQL Server Backup to URL)。</span><span class="sxs-lookup"><span data-stu-id="17131-114">also uses the same logging that is used when manually backing up to Azure storage (SQL Server Backup to URL).</span></span> <span data-ttu-id="17131-115">Backup to URL 関連の問題の詳細については、「 [SQL Server backup TO url のベストプラクティスとトラブルシューティング](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)」のトラブルシューティングのセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-115">For more information on Backup to URL related issues, see the troubleshooting section in [SQL Server Backup to URL Best Practices and Troubleshooting](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span></span>  
  
### <a name="general-troubleshooting-steps"></a><span data-ttu-id="17131-116">一般的なトラブルシューティング手順</span><span class="sxs-lookup"><span data-stu-id="17131-116">General Troubleshooting Steps</span></span>  
  
1.  <span data-ttu-id="17131-117">電子メール通知を有効にして、エラーと警告に関する電子メールの受信を開始します。</span><span class="sxs-lookup"><span data-stu-id="17131-117">Enable Email Notification to start to receive emails for error and warnings.</span></span>  
  
     <span data-ttu-id="17131-118">また、定期的に `smart_admin.fn_get_health_status` を実行して集計されたエラーおよび数を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="17131-118">Alternatively, you can also periodically run `smart_admin.fn_get_health_status` to check the aggregated errors and counts.</span></span> <span data-ttu-id="17131-119">たとえば、`number_of_invalid_credential_errors` は、スマート バックアップでバックアップを試行して "無効な資格情報" エラーが発生した回数です。</span><span class="sxs-lookup"><span data-stu-id="17131-119">For example, `number_of_invalid_credential_errors` is the number of times smart backup attempted a backup but got invalid credential error.</span></span> <span data-ttu-id="17131-120">`Number_of_backup_loops` と `number_of_retention_loops` はエラーではなく、バックアップ スレッドと保有期間スレッドがデータベースの一覧をスキャンした回数を示します。</span><span class="sxs-lookup"><span data-stu-id="17131-120">`Number_of_backup_loops` and `number_of_retention_loops` are not errors; but they indicate the number of times backup thread and retention thread scanned the list of databases.</span></span> <span data-ttu-id="17131-121">通常、 @begin_time と @end_time が指定されていない場合、関数は過去30分間の情報を表示します。この2つの列には、通常、0以外の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17131-121">Typically, when @begin_time and @end_time are not provided, the function is showing the information from last 30 minutes, then we should normally see non-zero values for these two columns.</span></span> <span data-ttu-id="17131-122">これらの値がゼロの場合は、システムがオーバーロードされたかシステムが応答していないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="17131-122">If they are zero then it implies system overloaded or even system not responding.</span></span> <span data-ttu-id="17131-123">詳細については、このトピックで後述する「**システムの問題のトラブルシューティング**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-123">For more information, see **Troubleshooting System Issues** section later in this topic.</span></span>  
  
2.  <span data-ttu-id="17131-124">拡張イベント ログを確認して、エラーと関連するその他のイベントの詳細を理解します。</span><span class="sxs-lookup"><span data-stu-id="17131-124">Review the Extended Event logs to learn more details on the errors and other associated events.</span></span>  
  
3.  <span data-ttu-id="17131-125">ログの情報を使用して、問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="17131-125">Use the information in the logs to resolve the issue.</span></span>  <span data-ttu-id="17131-126">システムに関する問題またはエラーが発生した場合は、サービスまたは SQL Server エージェントの再起動が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="17131-126">In case of a system issue or error, you may need to restart the service or SQL Server Agent.</span></span>  
  
### <a name="common-causes-of-errors"></a><span data-ttu-id="17131-127">エラーの一般的な原因</span><span class="sxs-lookup"><span data-stu-id="17131-127">Common Causes of Errors</span></span>  
 <span data-ttu-id="17131-128">エラーの一般的な原因の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17131-128">Following is the list of common causes resulting in failures:</span></span>  
  
1.  <span data-ttu-id="17131-129">**SQL 資格情報に対する変更:** によって使用される資格情報の名前が変更された場合 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 、または削除された場合、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] はバックアップを実行できません。</span><span class="sxs-lookup"><span data-stu-id="17131-129">**Changes to SQL Credential:** If the name of the credential used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is changed or if it is deleted, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will not be able to take backups.</span></span> <span data-ttu-id="17131-130">変更は [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成設定に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17131-130">The change should be applied to [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings.</span></span>  
  
2.  <span data-ttu-id="17131-131">**ストレージアクセスキーの値の変更:** Azure アカウントのストレージキーの値が変更されても、SQL 資格情報が新しい値で更新されない場合、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] はストレージに対する認証時に失敗し、このアカウントを使用するように構成されたデータベースのバックアップに失敗します。</span><span class="sxs-lookup"><span data-stu-id="17131-131">**Changes to storage access key values:** If the storage key values are changed for the Azure account, but SQL Credential is not updated with the new values, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will fail when authenticating to the storage, and fails to backup databases configured to use this account.</span></span>  
  
3.  <span data-ttu-id="17131-132">**Azure Storage アカウントの変更:** SQL 資格情報に対応する変更を行わずにストレージアカウントを削除または名前変更すると、が [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 失敗し、バックアップは作成されません。</span><span class="sxs-lookup"><span data-stu-id="17131-132">**Changes to Azure Storage Account:** Deleting or renaming storage account without corresponding changes to the SQL Credential will cause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to fail and no backups will be taken.</span></span> <span data-ttu-id="17131-133">ストレージ アカウントを削除する場合は、有効なストレージ アカウント情報を使用してデータベースを再構成してください。</span><span class="sxs-lookup"><span data-stu-id="17131-133">If you delete a storage account, ensure that the databases are reconfigured with valid storage account information.</span></span> <span data-ttu-id="17131-134">ストレージ アカウントの名前を変更したり、キー値を変更したりする場合は、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]で使用されている SQL 資格情報にこれらの変更が反映されるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="17131-134">If a storage account is renamed or the key values are changed, ensure that these changes are reflected in the SQL Credential used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span>  
  
4.  <span data-ttu-id="17131-135">**データベースのプロパティに対する変更:** 復旧モデルを変更したり、名前を変更したりすると、バックアップが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17131-135">**Changes to Database Properties:** Changes to recovery models or changing the name can cause backups to fail.</span></span>  
  
5.  <span data-ttu-id="17131-136">**復旧モデルの変更:** データベースの復旧モデルが完全または一括ログから単純に変更された場合、バックアップは停止し、によってデータベースがスキップされ [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="17131-136">**Changes to Recovery Model:** If the recovery model of the database is changed to simple from full or bulk-logged, backups will stop, and the databases will be skipped by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="17131-137">詳細については、「 [Azure へのマネージバックアップの SQL Server: 相互運用性と共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-137">For more information, see [SQL Server Managed Backup to Azure: Interoperability and Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span></span>  
  
### <a name="most-common-error-messages-and-solutions"></a><span data-ttu-id="17131-138">最も一般的なエラー メッセージと解決方法</span><span class="sxs-lookup"><span data-stu-id="17131-138">Most Common Error Messages and Solutions</span></span>  
  
1.  <span data-ttu-id="17131-139">**有効化または構成中にエラーが発生した場合 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] :**</span><span class="sxs-lookup"><span data-stu-id="17131-139">**Errors when enabling or configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:**</span></span>  
  
     <span data-ttu-id="17131-140">エラー: "ストレージ URL にアクセスできませんでした....有効な SQL 資格情報を指定してください... ": SQL 資格情報を参照している、これと同様のエラーが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="17131-140">Error: " Failed to access the storage URL.... Provide a valid SQL Credential..." : You may see this and other similar errors referring to SQL Credentials.</span></span>  <span data-ttu-id="17131-141">このような場合は、指定した SQL 資格情報の名前と、SQL 資格情報に格納されている情報 (ストレージアカウント名とストレージアクセスキー) を確認し、それらが最新で有効であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="17131-141">In such cases, review the name of the SQL Credential you provided, and also the information stored in the SQL Credential - the storage account name, and the storage access key and make sure that they are current and valid.</span></span>  
  
     <span data-ttu-id="17131-142">エラー: "...データベースを構成できません...システムデータベースであるため、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] システムデータベースに対してを有効にしようとすると、このエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17131-142">Error: "... cannot configure the database....because it is a system database": You will see this error if you try to enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a system database.</span></span>  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="17131-143">では、システム データベースのバックアップがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="17131-143">does not support backups for system databases.</span></span>  <span data-ttu-id="17131-144">システム データベースのバックアップを構成するには、メンテナンス プランなどの別の SQL Server バックアップ テクノロジを使用してください。</span><span class="sxs-lookup"><span data-stu-id="17131-144">To configure backup for a system database use other SQL Server Backup technologies such as maintenance plans.</span></span>  
  
     <span data-ttu-id="17131-145">エラー: "...保有期間の指定.... ": これらの値を初めて構成するときに、データベースまたはインスタンスの保有期間を指定していない場合は、保有期間に関するエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="17131-145">Error:" ... Provide a retention period...." : You may see errors regarding the retention period if you either have not specified a retention period for the database or instance when you are configuring these values for the first time.</span></span> <span data-ttu-id="17131-146">また、1 ～ 30 の数値以外の値を指定した場合にもエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="17131-146">You may also see an error if you provide a value other than a number between 1 and 30.</span></span> <span data-ttu-id="17131-147">保有期間に許可される値は 1 ～ 30 の数値です。</span><span class="sxs-lookup"><span data-stu-id="17131-147">The allowed value for the retention period is a number between 1 and 30.</span></span>  
  
2.  <span data-ttu-id="17131-148">**電子メール通知エラー:**</span><span class="sxs-lookup"><span data-stu-id="17131-148">**Email Notification Errors:**</span></span>  
  
     <span data-ttu-id="17131-149">エラー: "データベースメールが有効になっていません..."-電子メール通知を有効にしたが、データベースメールがインスタンスで構成されていない場合に、このエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17131-149">Error: "Database Mail is not enabled..." - You will see this error if you enable e-mail notifications, but Database Mail is not configured on the instance.</span></span> <span data-ttu-id="17131-150">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の正常性状態の通知を受信できるように、インスタンス上のデータベース メールを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17131-150">You must configure Database Mail on the instance to be able to receive notification of the health status of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="17131-151">データベースメールを有効にする方法の詳細については、「 [Configure データベースメール](../relational-databases/database-mail/configure-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-151">For information about how to enable database mail, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span> <span data-ttu-id="17131-152">また、通知にデータベース メールを使用するには、SQL Server エージェントを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17131-152">You must also enable SQL Server Agent to use Database Mail for notifications.</span></span> <span data-ttu-id="17131-153">詳細については、「[開始する前に](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-153">For more information, see [Before You Begin](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin).</span></span>  
  
     <span data-ttu-id="17131-154">電子メール通知に関連するエラー番号を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17131-154">Following is a list of error numbers you might see that are associated with email notifications:</span></span>  
  
    -   <span data-ttu-id="17131-155">エラー番号: 45209</span><span class="sxs-lookup"><span data-stu-id="17131-155">ErrorNumber: 45209</span></span>  
  
    -   <span data-ttu-id="17131-156">エラー番号: 45210</span><span class="sxs-lookup"><span data-stu-id="17131-156">ErrorNumber: 45210</span></span>  
  
    -   <span data-ttu-id="17131-157">エラー番号: 45211</span><span class="sxs-lookup"><span data-stu-id="17131-157">ErrorNumber: 45211</span></span>  
  
3.  <span data-ttu-id="17131-158">**接続エラー:**</span><span class="sxs-lookup"><span data-stu-id="17131-158">**Connectivity Errors:**</span></span>  
  
    -   <span data-ttu-id="17131-159">**SQL 接続に関連するエラー:** これらのエラーは、SQL Server インスタンスに接続するときに問題が発生した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="17131-159">**Errors Related to SQL Connectivity:** These errors happen when there are issues connecting to SQL Server instance.</span></span> <span data-ttu-id="17131-160">拡張イベントは、管理チャネルを介してこの種のエラーを公開します。</span><span class="sxs-lookup"><span data-stu-id="17131-160">The extended events expose these type of errors through the admin channel.</span></span> <span data-ttu-id="17131-161">次の 2 つの拡張イベントにより、この種の接続の問題に関連するエラーを確認できます。</span><span class="sxs-lookup"><span data-stu-id="17131-161">Following are the two extended events that you might see for errors related to this type of connectivity issues:</span></span>  
  
         <span data-ttu-id="17131-162">event_type が SqlError である FileRetentionAdminXEvent。</span><span class="sxs-lookup"><span data-stu-id="17131-162">FileRetentionAdminXEvent with event_type = SqlError.</span></span> <span data-ttu-id="17131-163">このエラーの詳細については、このイベントの error_code、error_message、および stack_trace を確認してください。</span><span class="sxs-lookup"><span data-stu-id="17131-163">For details of this error, look at the error_code, error_message and stack_trace of that event.</span></span> <span data-ttu-id="17131-164">Error_code は、SqlException のエラー番号です。</span><span class="sxs-lookup"><span data-stu-id="17131-164">The error_code is the SqlException's error number.</span></span>  
  
         <span data-ttu-id="17131-165">次のメッセージまたはメッセージ プレフィックスが含まれた SmartBackupAdminXevent。</span><span class="sxs-lookup"><span data-stu-id="17131-165">SmartBackupAdminXevent with the following messages/message prefixes:</span></span>  
  
         <span data-ttu-id="17131-166">*"SQL Server マネージバックアップを Azure の既定の設定に構成中に内部エラーが発生しました。エラーは一時的なものである可能性があります。 "*</span><span class="sxs-lookup"><span data-stu-id="17131-166">*"An internal error occurred while configuring SQL Server Managed Backup to Azure default settings for instance. Error might be transient."*</span></span>  
  
         <span data-ttu-id="17131-167">*「SQL Server で接続の問題が発生していることが考えられます。現在の反復処理でデータベースをスキップしています。 "*</span><span class="sxs-lookup"><span data-stu-id="17131-167">*"Probably experiencing connectivity issues with SQL Server. Skipping database in the current iteration."*</span></span>  
  
         <span data-ttu-id="17131-168">*"ログの使用状況情報を照会できませんでした。このエラーは一時的なものである可能性があります。現在の反復処理でデータベースをスキップしています。 "*</span><span class="sxs-lookup"><span data-stu-id="17131-168">*"Querying log usage info failed. The failure might be transient. Skipping database in the current iteration."*</span></span>  
  
         <span data-ttu-id="17131-169">*SSMBackup2WA エージェントメタデータの読み込み中に SQL 例外が発生しました。このエラーは一時的なものである可能性があります。操作は再試行されます。 "*</span><span class="sxs-lookup"><span data-stu-id="17131-169">*"SQL exception encountered while loading SSMBackup2WA agent metadata. The failure might be transient. Operation will be retried."*</span></span>  
  
         <span data-ttu-id="17131-170">*"SSMBackup2WA で SQL 例外が発生しました..."*</span><span class="sxs-lookup"><span data-stu-id="17131-170">*"SSMBackup2WA encountered SQL exception while ... "*</span></span>  
  
    -   <span data-ttu-id="17131-171">**ストレージ アカウントへの接続時のエラー:**</span><span class="sxs-lookup"><span data-stu-id="17131-171">**Errors Connecting to the storage account:**</span></span>  
  
         <span data-ttu-id="17131-172">event_type が XstoreError である FileRetentionAdminXEvent では、ストレージ例外が報告されます。</span><span class="sxs-lookup"><span data-stu-id="17131-172">Storage exceptions are reported in FileRetentionAdminXEvent with event_type = XstoreError.</span></span> <span data-ttu-id="17131-173">このエラーの詳細については、このイベントの error_message と stack_trace を確認してください。</span><span class="sxs-lookup"><span data-stu-id="17131-173">For details of the error, look at the error_message and stack_trace of that event.</span></span>  
  
         <span data-ttu-id="17131-174">SQL Server マネージド バックアップでは基になる Backup to URL テクノロジを使用するため、ストレージ接続に関連するエラーは両方の機能に適用されます。</span><span class="sxs-lookup"><span data-stu-id="17131-174">Since SQL Server Managed Backup uses the underlying Backup to URL technology, the errors related to storage connectivity apply to both the features.</span></span> <span data-ttu-id="17131-175">トラブルシューティングの手順の詳細については、 [SQL Server Backup TO URL のベストプラクティスとトラブルシューティング](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)に関する記事の**トラブルシューティング**に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17131-175">For more information on troubleshooting steps, see **troubleshooting section** of the [SQL Server Backup to URL Best Practices and Troubleshooting](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) article.</span></span>  
  
### <a name="troubleshooting-system-issues"></a><span data-ttu-id="17131-176">システムに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="17131-176">Troubleshooting System Issues</span></span>  
 <span data-ttu-id="17131-177">システム (SQL Server、SQL Server エージェント) で問題が発生した場合のシナリオと、その場合に [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が受ける影響を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17131-177">Following are some scenarios when there is an issue with the system (SQL Server, SQL Server Agent) and its effects on [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:</span></span>  
  
-   <span data-ttu-id="17131-178">\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] が実行\*\*されている場合、Sqlservr.exe は応答しなくなるか、動作を停止します。 SQL Server が動作を停止した場合、sql エージェントは正常にシャットダウンされます。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] また、イベントが sql エージェントの出力ファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="17131-178">**Sqlservr.exe stops responding or stops working when [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is running:** If SQL Server stops working, SQL Agent will gracefully shut down, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] also stops and the events are logged in SQL Agent.out file.</span></span>  
  
     <span data-ttu-id="17131-179">SQL Server が応答を停止した場合は、イベント ログが管理チャネルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="17131-179">If SQL Server stops responding, events are logged in the admin channel.</span></span>  <span data-ttu-id="17131-180">イベント ログの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17131-180">An example of the event log:</span></span>  
  
     <span data-ttu-id="17131-181">*Sql エラー (エンジンが応答していないか、sqlException を取得しています: SqlException:* </span><span class="sxs-lookup"><span data-stu-id="17131-181">*Sql Error (engine not responding or get sqlException: SqlException:* </span></span>  
     <span data-ttu-id="17131-182">*エラーコード、メッセージ、および stacktrace は、次のような追加情報と共に管理チャネル xevent に表示されます。* </span><span class="sxs-lookup"><span data-stu-id="17131-182">*error code, message and stacktrace will be displayed in an admin channel xevent, together with some extra information, such as :* </span></span>  
    <span data-ttu-id="17131-183">*「SQL Server で接続の問題が発生していることが考えられます。現在の反復処理でデータベースをスキップしています "*</span><span class="sxs-lookup"><span data-stu-id="17131-183">*"Probably experiencing connectivity issues with SQL Server. Skipping database in the current iteration"*</span></span>  
  
-   <span data-ttu-id="17131-184">**が実行されている場合、SQL エージェントが応答を停止するか、動作を停止し [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ます。**</span><span class="sxs-lookup"><span data-stu-id="17131-184">**SQL Agent stops responding or stops working when [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is running:**</span></span>  
  
     <span data-ttu-id="17131-185">SQL エージェントが動作を停止すると、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]も停止され、イベント ログが管理チャネルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="17131-185">If SQL Agent stops working, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] also stops and events are logged in the admin channel.</span></span> <span data-ttu-id="17131-186">これは、SQL Server が応答を停止した場合のシナリオに似ています。</span><span class="sxs-lookup"><span data-stu-id="17131-186">This is similar to the scenarios when SQL Server stops responding.</span></span>  
  
     <span data-ttu-id="17131-187">SQL エージェントが応答を停止した場合、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はバックアップ操作を継続できず、イベント ログが管理チャネルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="17131-187">If SQL Agent stops responding, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will be unable to continue with backup operations, and events are logged in the admin channel.</span></span> <span data-ttu-id="17131-188">イベント ログの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17131-188">An example of the event log:</span></span>  
  
     <span data-ttu-id="17131-189">*ジョブがハングした場合: 管理チャネル xevent を参照してください* </span><span class="sxs-lookup"><span data-stu-id="17131-189">*Job hangs: see admin channel xevents* </span></span>  
    <span data-ttu-id="17131-190">*"SQL Server からの進行状況の更新は、データベースのバックアップに対して" + DBBackupInfoMsgMaxWaitTime + "時間を超えています。  SSM Cloud Backup は引き続き待機します。 "*</span><span class="sxs-lookup"><span data-stu-id="17131-190">*"A progress update hasn't been received from SQL Server in more than " + Constants.DBBackupInfoMsgMaxWaitTime  + " hours for database backup.   SSM Cloud Backup will continue to wait."*</span></span>  
  
 <span data-ttu-id="17131-191">電子メール通知を有効にした場合は、**バックアップループの数**と**保有期間のループの数**を含む通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17131-191">If you have enabled email notification, you will receive a notification which includes **Number of Backup Loops** and **Number of Retention Loops**.</span></span> <span data-ttu-id="17131-192">これらの列の一方または両方について、通知に示されている値がゼロであれば、システムが応答していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17131-192">If the value returned in the notification for one or both of these two columns is zero, it could be an indication that the system is not responding.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="17131-193">レポートの結果を生成する内部プロセスは、エンジンの診断ログが SQL エージェント エラー ログと同じ場所に存在することを想定します。SQL エージェント エラー ログは、既定では SQL Server インスタンスのエラー ログと同じフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="17131-193">The internal processes that generate the results for the report, assumes that the engine diagnostic logs are in the same location of SQL Agent error log, which by default is in the same folder as the error logs of the SQL Server instance.</span></span> <span data-ttu-id="17131-194">エンジンの診断ログを、SQL エージェント エラー ログとは異なる場所に移動した場合は、システムはスマート バックアップの診断ログを見つけることができなくなるため、電子メール通知内のレポートが正しくなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17131-194">If the engine diagnostic logs are moved to a location other than SQL Agent error log location, the system is unable to find the smart backup diagnostic logs, and hence the report in the email notification may not be correct.</span></span> <span data-ttu-id="17131-195">たとえば、バックアップループの数と保有期間のループの数を含む、報告されたすべてのフィールドに**0**という値が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="17131-195">For example, you might see a value of **0** in all the fields reported including the Number of Backup Loops and Number of Retention Loops.</span></span> <span data-ttu-id="17131-196">この場合、診断ログを別の場所に移動した状況で、システムが応答しなくなるわけではなく、システムがログを見つけられなくなることを意味します。</span><span class="sxs-lookup"><span data-stu-id="17131-196">In this case where the diagnostic logs are moved to a different location, it may not mean that the system is not responding, but that the system is unable to find the logs.</span></span> <span data-ttu-id="17131-197">最初に、診断ログと SQL エージェント エラー ログが同じ場所にあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="17131-197">Ensure that the location of the diagnostic logs and SQL Agent error logs are at the same location first.</span></span> <span data-ttu-id="17131-198">診断ログの現在の場所を確認するには、 [dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations)を使用します。</span><span class="sxs-lookup"><span data-stu-id="17131-198">To verify the current location of the diagnostic logs, you can use [sys.dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations).</span></span> <span data-ttu-id="17131-199">列は、 `path` エンジン診断ログの現在の場所を返します。</span><span class="sxs-lookup"><span data-stu-id="17131-199">The `path` column returns the current location of the engine diagnostic logs.</span></span>  <span data-ttu-id="17131-200">SQL エージェントのエラーログと同じフォルダーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17131-200">It should be in the same folder as the SQL Agent error logs.</span></span> <span data-ttu-id="17131-201">`dbo.sp_get_sqlagent_properties` ストアド プロシージャを使用して、SQL エージェント エラー ログのパスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="17131-201">You can get SQL Agent error log path using the `dbo.sp_get_sqlagent_properties` stored procedure.</span></span>  
  
 <span data-ttu-id="17131-202">拡張イベント ログでエラーの詳細を確認してください。</span><span class="sxs-lookup"><span data-stu-id="17131-202">Check the extended event logs to see details of the errors.</span></span> <span data-ttu-id="17131-203">エラーを修正するか、SQL Server エージェントを再起動して状況を修正します。</span><span class="sxs-lookup"><span data-stu-id="17131-203">fix the errors, or restart SQL Server Agent to correct the situation.</span></span>  
  
  