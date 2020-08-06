---
title: Azure へのマネージバックアップの SQL Server-保有期間とストレージの設定 |Microsoft Docs
description: このトピックでは SQL Server マネージバックアップをデータベースの Microsoft Azure に構成し、インスタンスの既定の設定を構成する方法について説明します。
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ebdb81f8aa9edb9cd9326bcb1d286d5d3fe632c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736744"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a><span data-ttu-id="3506a-103">Azure への SQL Server マネージド バックアップ - 保有期間とストレージの設定</span><span class="sxs-lookup"><span data-stu-id="3506a-103">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>
  <span data-ttu-id="3506a-104">このトピックでは、データベースの [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成する基本手順と、インスタンスの既定の設定を構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3506a-104">This topic describes the basic steps to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database and to configure default settings for the instance.</span></span> <span data-ttu-id="3506a-105">また、インスタンスの [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] サービスを一時停止して再開するために必要な手順についても説明します。</span><span class="sxs-lookup"><span data-stu-id="3506a-105">The topic also describes the steps necessary to pause and resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for the instance.</span></span>  
  
 <span data-ttu-id="3506a-106">セットアップの完全なチュートリアルについ [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ては、「 [azure への管理](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md)されたバックアップ SQL Server のセットアップ」 SQL Server と「 [azure への管理](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)されたバックアップの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-106">For a complete walkthrough of setting up [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] see [Setting up SQL Server Managed Backup to Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3506a-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="3506a-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3506a-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="3506a-108">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3506a-109">現在メンテナンス プランまたはログ配布を使用しているデータベースで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="3506a-109">Do not enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on databases that are currently using maintenance plans or log shipping.</span></span> <span data-ttu-id="3506a-110">他の SQL Server 機能との相互運用性と共存の詳細については、「 [Azure へのマネージバックアップの SQL Server: 相互運用性と共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-110">For more information on interoperability and coexistence with other SQL Server features, see [SQL Server Managed Backup to Azure: Interoperability and Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="3506a-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="3506a-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="3506a-112">SQL Server エージェントを実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3506a-112">SQL Server Agent should be running.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="3506a-113">SQL Server エージェントが一定期間停止された後に再起動された場合、SQL エージェントの停止から起動までの経過時間によっては、バックアップ アクティビティが増加する可能性があり、実行を待機しているログ バックアップのバックログが存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="3506a-113">If SQL Server Agent is stopped for a period of time and then restarted, you may see an increased backup activity depending on the length of time elapsed between the stop and start of SQL Agent, and there might be a backlog of log backups waiting to run.</span></span> <span data-ttu-id="3506a-114">起動時に SQL Server エージェントが自動的に開始されるように構成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-114">Consider configuring SQL Server Agent to start automatically on start up.</span></span>  
  
-   <span data-ttu-id="3506a-115">を構成する前に、Azure ストレージアカウントと、認証情報をストレージアカウントに格納する SQL 資格情報の両方を作成する必要があり [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-115">A Azure storage account and a SQL Credential that stores the authentication information to the storage account should both be created before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="3506a-116">詳細については、「 [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) 」の「 **Introduction to Key Components and Concepts** 」のセクション、および「 [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-116">For more information see [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) section of the **SQL Server Backup to URL** topic, and [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="3506a-117">は、バックアップを格納するために必要なコンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3506a-117">creates the necessary containers to store the backups.</span></span> <span data-ttu-id="3506a-118">コンテナー名は、"コンピューター名-インスタンス名" の形式を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-118">The container name is created using 'machine name-instance name' format.</span></span> <span data-ttu-id="3506a-119">AlwaysOn 可用性グループの場合、コンテナーの名前には、可用性グループの GUID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-119">For AlwaysOn Availability Groups the container is named using the GUID of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3506a-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3506a-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3506a-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="3506a-121">Permissions</span></span>  
 <span data-ttu-id="3506a-122">を有効にするストアドプロシージャを実行するに [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] `System Administrator` は、 **ALTER ANY CREDENTIAL**権限を持つまたは**db_backupoperator**データベースロールのメンバーであるか、 `EXECUTE` **sp_delete_backuphistory**、およびストアドプロシージャに対する権限を持っている必要があり `smart_admin.sp_backup_master_switch` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-122">To run the stored procedures that enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], you must be a  either a `System Administrator` or  member  in the **db_backupoperator** database role with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on the **sp_delete_backuphistory**, and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  <span data-ttu-id="3506a-123">既存の設定を確認するために使用するストアド プロシージャと関数には、通常、ストアド プロシージャに対する `Execute` 権限と、関数に対する `Select` 権限がそれぞれ必要です。</span><span class="sxs-lookup"><span data-stu-id="3506a-123">Stored procedures and functions used to review the existing settings typically require `Execute` permissions on the stored procedure and `Select` on the function respectively.</span></span>  
  

  
###  <a name="considerations-for-enabling-ss_smartbackup-for-databases-and-instances"></a><a name="Considerations"></a><span data-ttu-id="3506a-124">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]データベースとインスタンスに対してを有効にする場合の考慮事項</span><span class="sxs-lookup"><span data-stu-id="3506a-124">Considerations for enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for Databases and Instances</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="3506a-125">は、個々のデータベースに対して個別に有効にするか、インスタンス全体に対して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3506a-125">can be enabled for individual databases separately or for the entire instance.</span></span> <span data-ttu-id="3506a-126">選択肢は、インスタンス上のデータベースの復旧要件、複数のデータベースとインスタンスを管理するための要件、および Azure storage の戦略的な使用によって異なります。</span><span class="sxs-lookup"><span data-stu-id="3506a-126">The choices depend on the recoverability requirements for the databases on the instance, requirements for managing multiple databases and instances, and using Azure storage strategically.</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-database-level"></a><span data-ttu-id="3506a-127">データベース レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を有効にする</span><span class="sxs-lookup"><span data-stu-id="3506a-127">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Database Level</span></span>  
 <span data-ttu-id="3506a-128">インスタンス上の他のデータベースとは異なる、バックアップと保有期間 (復旧 SLA) の特定の要件があるデータベースの場合は、このデータベースに対して、データベース レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成します。</span><span class="sxs-lookup"><span data-stu-id="3506a-128">If a database has specific requirements for backup and retention period (recoverability SLA) that is different from other databases on the instance, configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level for this database.</span></span> <span data-ttu-id="3506a-129">データベース レベルの設定は、インスタンス レベルの構成設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3506a-129">Database level settings override instance level configuration settings.</span></span> <span data-ttu-id="3506a-130">ただし、これらのオプションは同じインスタンスで一緒に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3506a-130">However both these options can be used together on the same instance.</span></span> <span data-ttu-id="3506a-131">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] をデータベース レベルで有効にした場合の利点と注意点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3506a-131">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
-   <span data-ttu-id="3506a-132">より細かい設定: データベースごとに別々の構成設定。</span><span class="sxs-lookup"><span data-stu-id="3506a-132">More granular: Separate configuration settings for each database.</span></span> <span data-ttu-id="3506a-133">個々のデータベースに対して異なる保有期間をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="3506a-133">Can support different retention periods for individual databases.</span></span>  
  
-   <span data-ttu-id="3506a-134">データベースのインスタンス レベルの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3506a-134">Overrides instance level settings for the database.</span></span>  
  
-   <span data-ttu-id="3506a-135">バックアップするデータベースを個別に選択することで、ストレージ コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-135">Can be used to reduce storage costs by selecting individual databases to be backed up.</span></span>  
  
-   <span data-ttu-id="3506a-136">各データベースの管理が必要です。</span><span class="sxs-lookup"><span data-stu-id="3506a-136">Requires managing each database</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-instance-level-with-default-settings"></a><span data-ttu-id="3506a-137">既定の設定を使用してインスタンス レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を有効にする</span><span class="sxs-lookup"><span data-stu-id="3506a-137">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level with Default Settings</span></span>  
 <span data-ttu-id="3506a-138">インスタンス内のほとんどのデータベースでバックアップと保有ポリシーの要件が同じ場合、または新しいデータベース インスタンスが作成時に自動的にバックアップされるようにする場合は、この設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-138">Use this setting if most of the databases in the instance have the same requirements for backup and retention policies, or if you want new database instances to automatically be backed up on creation.</span></span> <span data-ttu-id="3506a-139">ポリシーの例外となる少数のデータベースを個別に構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3506a-139">A few databases that are exception to the policy can still be configured individually.</span></span> <span data-ttu-id="3506a-140">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] をインスタンス レベルで有効にした場合の利点と注意点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3506a-140">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level.</span></span>  
  
-   <span data-ttu-id="3506a-141">インスタンス レベルでの自動化: 後から追加される新しいデータベースにも自動的に適用される共通設定。</span><span class="sxs-lookup"><span data-stu-id="3506a-141">Automation at the instance level: Common settings applied to automatically for new databases added thereafter.</span></span>  
  
-   <span data-ttu-id="3506a-142">新しいデータベースは、インスタンスに作成されるとすぐに自動的にバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="3506a-142">New databases will be automatically backed up soon after they are created on the instances</span></span>  
  
-   <span data-ttu-id="3506a-143">保有期間の要件が同じであるデータベースに適用できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-143">Can be applied to databases that have the same retention period requirements.</span></span>  
  
-   <span data-ttu-id="3506a-144">既定の設定を使用してインスタンス レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] のバックアップが有効になっている場合でも、別の保有期間を必要とするデータベースを個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-144">You can still configure individual databases that require a different retention period even with [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] backup enabled at in instance level with default settings.</span></span> <span data-ttu-id="3506a-145">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]バックアップに Azure storage を使用しない場合は、データベースに対してを無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3506a-145">You can also disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases if you do not intend to use Azure storage for the backups.</span></span>  
  
##  <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><a name="DatabaseConfigure"></a><span data-ttu-id="3506a-146">データベースに対してを有効にして構成する [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3506a-146">Enable and Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="3506a-147">特定のデータベースについて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を有効にするには、システム ストアド プロシージャ `smart_admin.sp_set_db_backup` を使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-147">The system stored procedure `smart_admin.sp_set_db_backup` is used to enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database.</span></span> <span data-ttu-id="3506a-148">データベースについて初めて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を有効にする場合は、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の有効化に加えて、次の情報の指定が必要です。</span><span class="sxs-lookup"><span data-stu-id="3506a-148">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time on the database, the following information must be specified in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:</span></span>  
  
-   <span data-ttu-id="3506a-149">データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="3506a-149">The name of the database.</span></span>  
  
-   <span data-ttu-id="3506a-150">保有期間。</span><span class="sxs-lookup"><span data-stu-id="3506a-150">The retention period.</span></span>  
  
-   <span data-ttu-id="3506a-151">Azure ストレージアカウントに対する認証に使用される SQL 資格情報。</span><span class="sxs-lookup"><span data-stu-id="3506a-151">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="3506a-152">\* \@ Encryption_algorithm\*NO_ENCRYPTION を使用して暗号化しないように指定するか、  =  **NO_ENCRYPTION**サポートされている暗号化アルゴリズムを指定してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-152">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="3506a-153">暗号化の詳細については、「 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-153">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="3506a-154">データベース レベル構成の [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、Transact-SQL でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3506a-154">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for database level configuration is only supported through Transact-SQL.</span></span>  
  
 <span data-ttu-id="3506a-155">データベースで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] が有効になると、この情報は保持されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-155">Once [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for a database this information is persisted.</span></span> <span data-ttu-id="3506a-156">構成を変更する場合は、データベース名と変更する設定のみが必要です。他のパラメーターについては、指定がなければ、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] では既存値がそのまま使用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-156">If you are changing the configuration, only the database name and the setting you want to change is required, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values for other parameters when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3506a-157">データベースで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成する前に、既存の構成 (ある場合) が役に立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="3506a-157">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on a database it might be useful to existing configuration if any.</span></span> <span data-ttu-id="3506a-158">データベースの構成設定を確認する手順については、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="3506a-158">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
-   <span data-ttu-id="3506a-159">**Transact-sql の使用:**</span><span class="sxs-lookup"><span data-stu-id="3506a-159">**Using Transact-SQL:**</span></span>  
  
     <span data-ttu-id="3506a-160">を初めて有効にする場合 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 、必要なパラメーターは、 \* \@ database_name*、 \* \@ credential_name*、 \* \@ encryption_algorithm*、 \* \@ enable_backup* \* \@ storage_url\*パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3506a-160">If you are enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the first time, the required parameters are: *\@database_name*, *\@credential_name*, *\@encryption_algorithm*,  *\@enable_backup* The *\@storage_url* parameter is optional.</span></span> <span data-ttu-id="3506a-161">パラメーターの値を指定しない場合、 @storage_url 値は SQL 資格情報のストレージアカウント情報を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-161">If you do not provide a value for  the @storage_url parameter, the value is derived using the storage account information from the SQL Credential.</span></span> <span data-ttu-id="3506a-162">ストレージ URL を指定する場合、指定する必要があるのはストレージ アカウントのルート URL のみです。この値は、指定した SQL 資格情報と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3506a-162">If you provide the storage URL you should only provide the URL for the root of the storage account, and must match the information in the SQL Credential you specified.</span></span>  
  
    1.  <span data-ttu-id="3506a-163">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-163">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
    2.  <span data-ttu-id="3506a-164">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-164">From the Standard bar, click **New Query**.</span></span>  
  
    3.  <span data-ttu-id="3506a-165">次の例をコピーし、クエリウィンドウに貼り付けて、をクリックし `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-165">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="3506a-166">この例 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] では、データベース ' TestDB ' に対してを有効にします。</span><span class="sxs-lookup"><span data-stu-id="3506a-166">This example enables [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the database 'TestDB'.</span></span> <span data-ttu-id="3506a-167">保有期間は 30 日に設定されています。</span><span class="sxs-lookup"><span data-stu-id="3506a-167">The retention period is set to 30 days.</span></span> <span data-ttu-id="3506a-168">このサンプルでは、暗号化アルゴリズムおよび暗号化機能情報を指定して暗号化オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-168">This sample uses the encryption option by specifying the encryption algorithm and the encryptor information.</span></span>  
  
    ```sql
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3506a-169">保有期間には、1 ～ 30 日までの任意の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-169">The retention period can be set to any value from 1 to 30 days.</span></span>  
    >   
    >  <span data-ttu-id="3506a-170">暗号化に使用する証明書の作成の詳細については、「 [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)」の「バックアップ証明書の作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-170">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
     <span data-ttu-id="3506a-171">このストアドプロシージャの詳細については、「smart_admin」を参照してください[。 set_db_backup &#40;transact-sql&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="3506a-171">For more information on this stored procedure, see [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span></span>  
  
     <span data-ttu-id="3506a-172">データベースの構成設定を確認するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-172">To review the configuration settings for a database use the following query:</span></span>  
  
    ```sql
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="enable-and-configure-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceConfigure"></a><span data-ttu-id="3506a-173">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]インスタンスの既定の設定を有効にして構成する</span><span class="sxs-lookup"><span data-stu-id="3506a-173">Enable and Configure Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="3506a-174">インスタンスレベルで既定の設定を有効にして構成するには [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 、システムストアドプロシージャ `smart_admin.set_instance_backup` または**SQL Server Management Studio**を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="3506a-174">You can enable and configure default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings at the instance level in two ways:  By using the system stored procedure `smart_admin.set_instance_backup` or **SQL Server Management Studio**.</span></span> <span data-ttu-id="3506a-175">これら 2 つの方法について以下で説明します。</span><span class="sxs-lookup"><span data-stu-id="3506a-175">The two methods are explained below:</span></span>  
  
 <span data-ttu-id="3506a-176">**smart_admin。 set_instance_backup:**</span><span class="sxs-lookup"><span data-stu-id="3506a-176">**smart_admin.set_instance_backup:**.</span></span> <span data-ttu-id="3506a-177">\* \@ Enable_backup\*パラメーターに値**1**を指定することによって、バックアップを有効にし、既定の構成を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="3506a-177">By specifying the value **1** for *\@enable_backup* parameter, you can enable backup and set the default configurations.</span></span> <span data-ttu-id="3506a-178">これらの既定の設定は、インスタンス レベルで適用すると、このインスタンスに追加されるすべての新しいデータベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-178">Once applied at the instance level, these default settings are applied to any new database that is added to this instance.</span></span>  <span data-ttu-id="3506a-179">初めて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を有効にする場合は、インスタンスでの [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の有効化に加えて、次の情報の指定が必要です。</span><span class="sxs-lookup"><span data-stu-id="3506a-179">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time, the following information must be provided in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on the instance:</span></span>  
  
-   <span data-ttu-id="3506a-180">保有期間。</span><span class="sxs-lookup"><span data-stu-id="3506a-180">The retention period.</span></span>  
  
-   <span data-ttu-id="3506a-181">Azure ストレージアカウントに対する認証に使用される SQL 資格情報。</span><span class="sxs-lookup"><span data-stu-id="3506a-181">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="3506a-182">暗号化オプション。</span><span class="sxs-lookup"><span data-stu-id="3506a-182">The encryption option.</span></span> <span data-ttu-id="3506a-183">\* \@ Encryption_algorithm\*NO_ENCRYPTION を使用して暗号化しないように指定するか、  =  **NO_ENCRYPTION**サポートされている暗号化アルゴリズムを指定してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-183">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="3506a-184">暗号化の詳細については、「 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-184">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="3506a-185">有効にすると、これらの設定は保持されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-185">Once enabled these settings are persisted.</span></span> <span data-ttu-id="3506a-186">構成を変更する場合は、データベース名と変更する設定のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="3506a-186">If you are changing the configuration, only the database name and the setting you want to change is required.</span></span> <span data-ttu-id="3506a-187">指定がなければ、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では既存値がそのまま使用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-187">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3506a-188">インスタンスで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成する前に、既存の構成 (ある場合) を確認すると役に立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="3506a-188">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on an instance, it might be useful to check for existing configuration, if any.</span></span> <span data-ttu-id="3506a-189">データベースの構成設定を確認する手順については、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="3506a-189">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
 <span data-ttu-id="3506a-190">**SQL Server Management Studio:** SQL Server Management Studio でこのタスクを実行するには、オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[マネージド バックアップ]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-190">**SQL Server Management Studio:** To do this task in SQL Server Management Studio, go the object explorer, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="3506a-191">**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-191">Select **Configure**.</span></span> <span data-ttu-id="3506a-192">**[マネージド バックアップ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="3506a-192">This opens the **Managed Backup** dialog.</span></span> <span data-ttu-id="3506a-193">このダイアログ ボックスを使用して、保持期間、SQL 資格情報、ストレージ URL、暗号化の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3506a-193">Use this dialog to specify the retention period, SQL Credential, Storage URL, and the encryption settings.</span></span> <span data-ttu-id="3506a-194">このダイアログの具体的なヘルプについては、「 [Configure Managed Backup &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-194">For specific help with this dialog, see [Configure Managed Backup &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).</span></span>  
  
#### <a name="using-transact-sql"></a><span data-ttu-id="3506a-195">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3506a-195">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="3506a-196">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-196">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3506a-197">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-197">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3506a-198">次の例をコピーし、クエリウィンドウに貼り付けて、をクリックし `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-198">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3506a-199">保有期間には、1 ～ 30 日までの任意の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-199">The retention period can be set to any value from 1 to 30 days.</span></span>  
>   
>  <span data-ttu-id="3506a-200">暗号化に使用する証明書の作成の詳細については、「 [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)」の「バックアップ証明書の作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3506a-200">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
 <span data-ttu-id="3506a-201">インスタンスの既定の構成設定を確認するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-201">To view the default configuration settings for the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();
```  
  
#### <a name="using-powershell"></a><span data-ttu-id="3506a-202">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="3506a-202">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="3506a-203">PowerShell インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="3506a-203">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="3506a-204">次のスクリプトを設定に合わせて変更してから実行します。</span><span class="sxs-lookup"><span data-stu-id="3506a-204">Run the following script after modifying it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3506a-205">既定の設定を構成した後に新しいデータベースを作成すると、データベースが既定の設定で構成されるまで最大 15 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3506a-205">When you create a new database after configuring the default settings, it may take up to 15 minutes for the database to be configured with the default settings.</span></span> <span data-ttu-id="3506a-206">これは、復旧モデルが **Simple** から **Full** または **Bulk-Logged** に変更されるデータベースにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-206">This also applies to databases that are changed from **Simple** to **Full** or **Bulk-Logged** recovery model.</span></span>  
  
##  <a name="disable-ss_smartbackup-for-a-database"></a><a name="DatabaseDisable"></a> <span data-ttu-id="3506a-207">データベースに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を無効にする</span><span class="sxs-lookup"><span data-stu-id="3506a-207">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database</span></span>  
 <span data-ttu-id="3506a-208">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]システムストアドプロシージャを使用して設定を無効にすることができ `sp_set_db_backup` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-208">You can disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings by using the `sp_set_db_backup` system stored procedure.</span></span> <span data-ttu-id="3506a-209">\* \@ Enableparameter\*は、特定のデータベースの構成を有効または無効にするために使用され [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ます。1では、構成設定が有効になり、0が無効になります。</span><span class="sxs-lookup"><span data-stu-id="3506a-209">The *\@enableparameter* is used to enable and disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurations for a specific database, where 1 enables and 0 disables the configuration settings.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-for-a-specific-database"></a><span data-ttu-id="3506a-210">特定のデータベースに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を無効にするには</span><span class="sxs-lookup"><span data-stu-id="3506a-210">To Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database:</span></span>  
  
1.  <span data-ttu-id="3506a-211">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-211">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3506a-212">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-212">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3506a-213">次の例をコピーし、クエリウィンドウに貼り付けて、をクリックし `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-213">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO
```  
  
##  <a name="disable-ss_smartbackup-for-all-the-databases-on-the-instance"></a><a name="DatabaseAllDisable"></a> <span data-ttu-id="3506a-214">インスタンス上のすべてのデータベースについて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を無効にする</span><span class="sxs-lookup"><span data-stu-id="3506a-214">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for all the databases on the Instance</span></span>  
 <span data-ttu-id="3506a-215">インスタンスで現在 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] が有効になっているすべてのデータベースから [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の構成設定を無効にするための手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3506a-215">The following procedure is for when you want to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings from all the databases that currently have [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled on the instance.</span></span>  <span data-ttu-id="3506a-216">ストレージ URL、保有期間、SQL 資格情報などの構成設定はメタデータに残るため、後で [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] をデータベースに対して有効にした場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-216">The configuration settings like the storage URL, retention, and the SQL Credential will remain in the metadata and can be used  if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the database at a later time.</span></span> <span data-ttu-id="3506a-217">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] サービスを一時的に停止するだけの場合は、このトピックの以降のセクションで説明するマスターの切り替えを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3506a-217">If you want to just pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services temporarily, you can use the master switch explained in the following sections later in this topic.</span></span>  
  
#### <a name="to-disable-ss_smartbackupfor-all-the-databases"></a><span data-ttu-id="3506a-218">すべてのデータベースについて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を無効にするには:</span><span class="sxs-lookup"><span data-stu-id="3506a-218">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]for all the databases:</span></span>  
  
1.  <span data-ttu-id="3506a-219">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-219">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3506a-220">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-220">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3506a-221">次の例をコピーし、クエリウィンドウに貼り付けて、をクリックし `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-221">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="3506a-222">次の例では、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]がインスタンス レベルで構成されているかどうかと、インスタンス上のすべての [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]対応データベースを識別し、システム ストアド プロシージャ `sp_set_db_backup` を実行して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3506a-222">The following example identifies if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured at the instance level and all the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled databases on the instance, and executes the system stored procedure `sp_set_db_backup` to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span>  
  
```sql
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames 
       select @rowid = min(RowID) FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END
```  
  
 <span data-ttu-id="3506a-223">インスタンスのすべてのデータベースの構成設定を確認するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-223">To review the configuration settings for all the databases on the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO
```  
  
##  <a name="disable-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceDisable"></a> <span data-ttu-id="3506a-224">インスタンスについて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の既定設定を無効にする</span><span class="sxs-lookup"><span data-stu-id="3506a-224">Disable Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="3506a-225">インスタンス レベルの既定の設定は、そのインスタンスに作成されたすべての新しいデータベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-225">Default settings at the instance level apply to all new databases created on that instance.</span></span>  <span data-ttu-id="3506a-226">既定の設定が必要なくなった場合は、 **smart_admin.sp_set_instance_backup** システム ストアド プロシージャを使用してこの構成を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3506a-226">If you no longer need or require default settings, you can disable this configuration by using the **smart_admin.sp_set_instance_backup** System stored procedure.</span></span> <span data-ttu-id="3506a-227">無効にしても、ストレージ URL、保有期間の設定、SQL 資格情報名など、その他の構成設定は削除されません。</span><span class="sxs-lookup"><span data-stu-id="3506a-227">Disabling does not remove the other configuration settings like the storage URL, retention setting, or the SQL Credential name.</span></span> <span data-ttu-id="3506a-228">これらの設定は、後でインスタンスに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を有効にする場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-228">These settings will be used if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the instance at a later time.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-default-configuration-settings"></a><span data-ttu-id="3506a-229">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の既定の構成設定を無効にするには</span><span class="sxs-lookup"><span data-stu-id="3506a-229">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default configuration settings:</span></span>  
  
1.  <span data-ttu-id="3506a-230">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-230">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3506a-231">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-231">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3506a-232">次の例をコピーし、クエリウィンドウに貼り付けて、をクリックし `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-232">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
    ```sql
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO
    ```  
  
#### <a name="using-powershell"></a><span data-ttu-id="3506a-233">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="3506a-233">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="3506a-234">PowerShell インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="3506a-234">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="3506a-235">次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="3506a-235">Run the following script:</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="pause-ss_smartbackup-at-the-instance-level"></a><a name="InstancePause"></a> <span data-ttu-id="3506a-236">インスタンス レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を一時停止する</span><span class="sxs-lookup"><span data-stu-id="3506a-236">Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level</span></span>  
 <span data-ttu-id="3506a-237">一時的に少しの間 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] サービスを停止する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3506a-237">There might be times when you need to temporarily pause the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for a short period time.</span></span>  <span data-ttu-id="3506a-238">`smart_admin.sp_backup_master_switch` システム ストアド プロシージャを使用すると、インスタンス レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] サービスを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="3506a-238">The `smart_admin.sp_backup_master_switch` system stored procedure allows you to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] service at the instance level.</span></span>  <span data-ttu-id="3506a-239">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を再開するには、同じストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3506a-239">The same stored procedure is used to resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="3506a-240">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を無効にするか有効にするかを定義するには、@state パラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3506a-240">The @state parameter is used to define whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] should be turned off or on.</span></span>  
  
#### <a name="to-pause-ss_smartbackup-services-using-transact-sql"></a><span data-ttu-id="3506a-241">Transact-SQL を使用して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] サービスを一時停止するには</span><span class="sxs-lookup"><span data-stu-id="3506a-241">To Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Services Using Transact-SQL:</span></span>  
  
1.  <span data-ttu-id="3506a-242">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-242">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3506a-243">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-243">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3506a-244">次の例をコピーし、クエリウィンドウに貼り付けてから、[] をクリックします。`Execute`</span><span class="sxs-lookup"><span data-stu-id="3506a-244">Copy and paste the following example into the query window and then click `Execute`</span></span>  
  
```sql
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-ss_smartbackup-using-powershell"></a><span data-ttu-id="3506a-245">PowerShell を使用して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を一時停止するには</span><span class="sxs-lookup"><span data-stu-id="3506a-245">To pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="3506a-246">PowerShell インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="3506a-246">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="3506a-247">次のスクリプトを設定に合わせて変更してから実行します。</span><span class="sxs-lookup"><span data-stu-id="3506a-247">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-ss_smartbackup-using-transact-sql"></a><span data-ttu-id="3506a-248">Transact-SQL を使用して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を再開するには</span><span class="sxs-lookup"><span data-stu-id="3506a-248">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="3506a-249">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3506a-249">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3506a-250">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3506a-250">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3506a-251">次の例をコピーし、クエリウィンドウに貼り付けて、をクリックし `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="3506a-251">Copy and paste the following example into the query window and then click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO
```  
  
#### <a name="to-resume-ss_smartbackup-using-powershell"></a><span data-ttu-id="3506a-252">PowerShell を使用して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を再開するには</span><span class="sxs-lookup"><span data-stu-id="3506a-252">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="3506a-253">PowerShell インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="3506a-253">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="3506a-254">次のスクリプトを設定に合わせて変更してから実行します。</span><span class="sxs-lookup"><span data-stu-id="3506a-254">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
