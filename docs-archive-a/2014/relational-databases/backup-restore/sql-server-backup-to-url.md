---
title: SQL Server Backup to URL | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6918a099e00b1de9e773320b5c6c0e4089859e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718327"
---
# <a name="sql-server-backup-to-url"></a><span data-ttu-id="d1f0a-102">SQL Server Backup to URL</span><span class="sxs-lookup"><span data-stu-id="d1f0a-102">SQL Server Backup to URL</span></span>
  <span data-ttu-id="d1f0a-103">このトピックでは、Azure Blob ストレージサービスをバックアップ先として使用するために必要な概念、要件、およびコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-103">This topic introduces the concepts, requirements and components necessary to use the Azure Blob storage service as a backup destination.</span></span> <span data-ttu-id="d1f0a-104">バックアップと復元の機能は、ディスクまたはテープを使用する場合とよく似ていますが、いくつか相違点もあります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-104">The backup and restore functionality are same or similar to when using DISK or TAPE, with a few differences.</span></span> <span data-ttu-id="d1f0a-105">相違点、重要な例外、コード例についても、このトピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-105">The differences are and any notable exceptions, and a few code examples are included in this topic.</span></span>  
  
## <a name="requirements-components-and-concepts"></a><span data-ttu-id="d1f0a-106">要件、コンポーネント、および概念</span><span class="sxs-lookup"><span data-stu-id="d1f0a-106">Requirements, Components, and Concepts</span></span>  
 <span data-ttu-id="d1f0a-107">**このセクションの内容:**</span><span class="sxs-lookup"><span data-stu-id="d1f0a-107">**In this section:**</span></span>  
  
-   [<span data-ttu-id="d1f0a-108">Security</span><span class="sxs-lookup"><span data-stu-id="d1f0a-108">Security</span></span>](#security)  
  
-   [<span data-ttu-id="d1f0a-109">主なコンポーネントと概念の概要</span><span class="sxs-lookup"><span data-stu-id="d1f0a-109">Introduction to Key Components and Concepts</span></span>](#intorkeyconcepts)  
  
-   [<span data-ttu-id="d1f0a-110">Azure Blob Storage サービス</span><span class="sxs-lookup"><span data-stu-id="d1f0a-110">Azure Blob Storage Service</span></span>](#Blob)  
  
-   [<span data-ttu-id="d1f0a-111">SQL Server コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d1f0a-111">SQL Server Components</span></span>](#sqlserver)  
  
-   [<span data-ttu-id="d1f0a-112">制限事項</span><span class="sxs-lookup"><span data-stu-id="d1f0a-112">Limitations</span></span>](#limitations)  
  
-   [<span data-ttu-id="d1f0a-113">Backup/Restore ステートメントのサポート</span><span class="sxs-lookup"><span data-stu-id="d1f0a-113">Support for Backup/Restore Statements</span></span>](#Support)  
  
-   [<span data-ttu-id="d1f0a-114">SQL Server Management Studio でのバックアップ タスクの使用</span><span class="sxs-lookup"><span data-stu-id="d1f0a-114">Using Backup Task in SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [<span data-ttu-id="d1f0a-115">メンテナンス プラン ウィザードを使用した SQL Server Backup to URL</span><span class="sxs-lookup"><span data-stu-id="d1f0a-115">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [<span data-ttu-id="d1f0a-116">SQL Server Management Studio を使用した Azure ストレージからの復元</span><span class="sxs-lookup"><span data-stu-id="d1f0a-116">Restoring from Azure storage Using SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a><a name="security"></a> <span data-ttu-id="d1f0a-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d1f0a-117">Security</span></span>  
 <span data-ttu-id="d1f0a-118">次に、Azure Blob ストレージサービスとの間でバックアップまたは復元を行う際のセキュリティに関する考慮事項と要件を示します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-118">The following are security considerations and requirements when backing up to or restoring from the Azure Blob storage services.</span></span>  
  
-   <span data-ttu-id="d1f0a-119">Azure Blob ストレージサービスのコンテナーを作成するときは、アクセス権を**private**に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-119">When creating a container for the Azure Blob storage service, we recommend that you set the access to **private**.</span></span> <span data-ttu-id="d1f0a-120">アクセス権を private に設定すると、Azure アカウントの認証に必要な情報を指定できるユーザーまたはアカウントだけがアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-120">Setting the access to private restricts the access to users or accounts able to provide the necessary information to authenticate to the Azure account.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d1f0a-121">Azure アカウント名とアクセスキー認証が資格情報に格納されている必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-121">requires Azure account name and access key authentication to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential.</span></span> <span data-ttu-id="d1f0a-122">この情報は、バックアップ操作または復元操作の実行時に Azure アカウントに対して認証を行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-122">This information is used to authenticate to the Azure account when it performs backup or restore operations.</span></span>  
  
-   <span data-ttu-id="d1f0a-123">BACKUP コマンドまたは RESTORE コマンドの発行に使用するユーザー アカウントは、 **資格情報の変更** 権限を持つ **db_backup operator** データベース ロールに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-123">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
###  <a name="introduction-to-key-components-and-concepts"></a><a name="intorkeyconcepts"></a><span data-ttu-id="d1f0a-124">主要なコンポーネントと概念の概要</span><span class="sxs-lookup"><span data-stu-id="d1f0a-124">Introduction to Key Components and Concepts</span></span>  
 <span data-ttu-id="d1f0a-125">次の2つのセクションでは、azure Blob ストレージサービスと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure blob ストレージサービスとの間でバックアップまたは復元を行うときに使用するコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-125">The following two sections introduce the Azure Blob storage service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components used when backing up to or restoring from the Azure Blob storage service.</span></span> <span data-ttu-id="d1f0a-126">Azure Blob ストレージサービスとの間でバックアップまたは復元を実行するには、コンポーネントと、コンポーネント間のやり取りを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-126">It is important to understand the components and the interaction between them to do a backup to or restore from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="d1f0a-127">このプロセスの最初の手順として、Azure アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-127">Creating an Azure account is the first step to this process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d1f0a-128">は、 **Azure ストレージアカウント名**とその**アクセスキー**値を使用して、ストレージサービスに対して認証および blob の読み書きを行います。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-128">uses the **Azure storage account name** and its **access key** values to authenticate and write and read blobs to the storage service.</span></span> <span data-ttu-id="d1f0a-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報はこの認証情報を格納するため、バックアップ操作または復元操作中に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-129">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential stores this authentication information and is used during the backup or restore operations.</span></span> <span data-ttu-id="d1f0a-130">ストレージアカウントを作成し、単純な復元を実行する完全なチュートリアルについては、「 [Azure Storage サービスを使用した SQL Server のバックアップと復元のチュートリアル](https://go.microsoft.com/fwlink/?LinkId=271615)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-130">For a complete walkthrough of creating a storage account and performing a simple restore, see [Tutorial Using Azure Storage Service for SQL Server Backup and Restore](https://go.microsoft.com/fwlink/?LinkId=271615).</span></span>  
  
 <span data-ttu-id="d1f0a-131">![sql 資格情報へのストレージ アカウントのマッピング](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "sql 資格情報へのストレージ アカウントのマッピング")</span><span class="sxs-lookup"><span data-stu-id="d1f0a-131">![mapping storage account to sql credentials](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
###  <a name="azure-blob-storage-service"></a><a name="Blob"></a><span data-ttu-id="d1f0a-132">Azure Blob Storage サービス</span><span class="sxs-lookup"><span data-stu-id="d1f0a-132">Azure Blob Storage Service</span></span>  
 <span data-ttu-id="d1f0a-133">**ストレージ アカウント:** ストレージ アカウントは、すべてのストレージ サービスの開始点となります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-133">**Storage Account:** The storage account is the starting point for all storage services.</span></span> <span data-ttu-id="d1f0a-134">Azure Blob Storage サービスにアクセスするには、まず Azure ストレージアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-134">To access the Azure Blob Storage service, first create an Azure storage account.</span></span> <span data-ttu-id="d1f0a-135">**ストレージアカウント名**とその**アクセスキー**プロパティは、Azure Blob Storage サービスとそのコンポーネントに対して認証を行うために必要です。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-135">The **storage account name** and its **access key** properties are required to authenticate to the Azure Blob Storage service and its components.</span></span>  
  
 <span data-ttu-id="d1f0a-136">**コンテナー:** コンテナーは一連の Blob をグループ化したもので、無制限の数の Blob を格納できます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-136">**Container:** A container provides a grouping of a set of Blobs, and can store an unlimited number of Blobs.</span></span> <span data-ttu-id="d1f0a-137">Azure Blob service にバックアップを書き込むには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 少なくともルートコンテナーが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-137">To write a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to the Azure Blob service, you must have at least the root container created.</span></span>  
  
 <span data-ttu-id="d1f0a-138">**BLOB:** 任意の種類とサイズのファイルです。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-138">**Blob:** A file of any type and size.</span></span> <span data-ttu-id="d1f0a-139">Azure Blob ストレージサービスに格納できる blob には、ブロック blob とページ blob の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-139">There are two types of blobs that can be stored in the Azure Blob storage service: block and page blobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1f0a-140">バックアップでは、BLOB の種類としてページ BLOB を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-140">backup uses page Blobs as the Blob type.</span></span> <span data-ttu-id="d1f0a-141">Blob は、次の URL 形式を使用してアドレス指定できます。 https:// \<storage account> . blob.core.windows.net/\<container>/\<blob></span><span class="sxs-lookup"><span data-stu-id="d1f0a-141">Blobs are addressable using the following URL format: https://\<storage account>.blob.core.windows.net/\<container>/\<blob></span></span>  
  
 <span data-ttu-id="d1f0a-142">![Azure Blob Storage](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob Storage")</span><span class="sxs-lookup"><span data-stu-id="d1f0a-142">![Azure Blob Storage](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob Storage")</span></span>  
  
 <span data-ttu-id="d1f0a-143">Azure Blob ストレージサービスの詳細については、「 [How to use the Azure Blob Storage service](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-143">For more information about the Azure Blob storage service, see [How to use the Azure Blob Storage Service](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)</span></span>  
  
 <span data-ttu-id="d1f0a-144">ページ BLOB の詳細については、「[ブロック BLOB およびページ BLOB について](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-144">For more information about page Blobs, see [Understanding Block and Page Blobs](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)</span></span>  
  
###  <a name="ssnoversion-components"></a><a name="sqlserver"></a> <span data-ttu-id="d1f0a-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d1f0a-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components</span></span>  
 <span data-ttu-id="d1f0a-146">**URL:** 一意なバックアップ ファイルの Uniform Resource Identifier (URI) を示します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-146">**URL:** A URL specifies a Uniform Resource Identifier (URI) to a unique backup file.</span></span> <span data-ttu-id="d1f0a-147">URL は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ ファイルの場所と名前を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-147">The URL is used to provide the location and name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup file.</span></span> <span data-ttu-id="d1f0a-148">この実装では、有効な URL は、Azure ストレージアカウント内のページ Blob を指す URL のみです。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-148">In this implementation, the only valid URL is one that points to a page Blob in an Azure storage account.</span></span> <span data-ttu-id="d1f0a-149">URL は、コンテナーだけでなく、実際の BLOB を指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-149">The URL must point to an actual Blob, not just a container.</span></span> <span data-ttu-id="d1f0a-150">BLOB が存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-150">If the Blob does not exist, it is created.</span></span> <span data-ttu-id="d1f0a-151">既存の Blob が指定されている場合、"WITH FORMAT" オプションが指定されていない限り、BACKUP は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-151">If an existing Blob is specified, BACKUP fails, unless the "WITH FORMAT" option is specified.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d1f0a-152">バックアップファイルをコピーして Azure Blob ストレージサービスにアップロードする場合は、ストレージオプションとしてページ Blob を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-152">If you choose to copy and upload a backup file to the Azure Blob storage service, use page blob as your storage option.</span></span> <span data-ttu-id="d1f0a-153">ブロック BLOB からの復元はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-153">Restores from Block Blobs are not supported.</span></span> <span data-ttu-id="d1f0a-154">ブロック BLOB から RESTORE ステートメントを実行すると、エラーが発生して失敗します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-154">RESTORE from a block blob type fails with an error.</span></span>  
  
 <span data-ttu-id="d1f0a-155">URL 値の例を次に示します: http [s]://ACCOUNTNAME.Blob.core.windows.net/ \<CONTAINER> / \<FILENAME.bak> 。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-155">Here is a sample URL value: http[s]://ACCOUNTNAME.Blob.core.windows.net/\<CONTAINER>/\<FILENAME.bak>.</span></span> <span data-ttu-id="d1f0a-156">HTTPS は必須ではありませんが、推奨されています。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-156">HTTPS is not required, but is recommended.</span></span>  
  
 <span data-ttu-id="d1f0a-157">**資格情報:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-157">**Credential:** A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="d1f0a-158">ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップと復元のプロセスで、Azure Blob ストレージサービスに対する認証に資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-158">Here, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="d1f0a-159">資格情報には、ストレージ アカウントの名前とその **アクセス キー** 値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-159">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="d1f0a-160">作成した資格情報は、BACKUP/RESTORE ステートメントの実行時に WITH CREDENTIAL オプションで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-160">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="d1f0a-161">ストレージアカウントの**アクセスキー**を表示、コピー、または再生成する方法の詳細については、「[ストレージアカウントのアクセスキー](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-161">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="d1f0a-162">資格情報を作成する方法の詳細な手順については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、このトピックの「[資格情報の作成の](#credential)例」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-162">For step by step instructions about how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential, see [Create a Credential](#credential) example later in this topic.</span></span>  
  
 <span data-ttu-id="d1f0a-163">資格情報の全般的な情報については、「 [資格情報](../security/authentication-access/credentials-database-engine.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-163">For general information about credentials, see [Credentials](../security/authentication-access/credentials-database-engine.md)</span></span>  
  
 <span data-ttu-id="d1f0a-164">資格情報が使用されるその他の例については、「 [Create a SQL Server エージェント Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-164">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
###  <a name="limitations"></a><a name="limitations"></a> <span data-ttu-id="d1f0a-165">制限事項</span><span class="sxs-lookup"><span data-stu-id="d1f0a-165">Limitations</span></span>  
  
-   <span data-ttu-id="d1f0a-166">Premium Storage へのバックアップはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-166">Backup to premium storage is not supported.</span></span>  
  
-   <span data-ttu-id="d1f0a-167">サポートされるバックアップの最大サイズは 1 TB です。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-167">The maximum backup size supported is 1 TB.</span></span>  
  
-   <span data-ttu-id="d1f0a-168">TSQL、SMO、または PowerShell コマンドレットを使用してバックアップ ステートメントや復元ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-168">You can issue backup or restore statements by using TSQL, SMO, or PowerShell cmdlets.</span></span> <span data-ttu-id="d1f0a-169">SQL Server Management Studio のバックアップまたは復元ウィザードを使用して Azure Blob ストレージサービスとの間でバックアップまたは復元を行うことは、現在有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-169">A backup to or restoring from the Azure Blob storage service by using SQL Server Management Studio Backup or Restore wizard is not currently enabled.</span></span>  
  
-   <span data-ttu-id="d1f0a-170">論理デバイス名の作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-170">Creating a logical device name is not supported.</span></span> <span data-ttu-id="d1f0a-171">そのため、sp_dumpdevice または SQL Server Management Studio を使用してバックアップ デバイスとして URL を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-171">So adding URL as a backup device using sp_dumpdevice or through SQL Server Management Studio is not supported.</span></span>  
  
-   <span data-ttu-id="d1f0a-172">既存のバックアップ BLOB への追加はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-172">Appending to existing backup blobs is not supported.</span></span> <span data-ttu-id="d1f0a-173">既存の BLOB へのバックアップは WITH FORMAT オプションを使用した場合にのみ上書きできます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-173">Backups to an existing Blob can only be overwritten by using the WITH FORMAT option.</span></span>  
  
-   <span data-ttu-id="d1f0a-174">1 回のバックアップ操作で複数の BLOB にバックアップすることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-174">Backup to multiple blobs in a single backup operation is not supported.</span></span> <span data-ttu-id="d1f0a-175">たとえば、次のコードではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-175">For example, the following returns an error:</span></span>  
  
    ```sql
    BACKUP DATABASE AdventureWorks2012
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'
          WITH CREDENTIAL = 'mycredential'
         ,STATS = 5;  
    GO
    ```  
  
-   <span data-ttu-id="d1f0a-176">`BACKUP` ステートメントでブロック サイズを指定することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-176">Specifying a block size with `BACKUP` is not supported.</span></span>  
  
-   <span data-ttu-id="d1f0a-177">`MAXTRANSFERSIZE` を指定することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-177">Specifying `MAXTRANSFERSIZE` is not supported.</span></span>  
  
-   <span data-ttu-id="d1f0a-178">バックアップセットのオプション (`RETAINDAYS` および `EXPIREDATE`) を指定することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-178">Specifying backupset options - `RETAINDAYS` and `EXPIREDATE` are not supported.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1f0a-179">では、バックアップ デバイス名に最大 259 文字の制限があります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-179">has a maximum limit of 259 characters for a backup device name.</span></span> <span data-ttu-id="d1f0a-180">BACKUP TO URL では、URL の指定に使用する必須要素に 'https://.blob.core.windows.net//.bak ' の 36 文字が使用されるため、アカウント、コンテナー、および BLOB の名前は残りの 223 文字で構成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-180">The BACKUP TO URL consumes 36 characters for the required elements used to specify the URL - 'https://.blob.core.windows.net//.bak', leaving 223 characters for account, container, and blob names put together.</span></span>  
  
###  <a name="support-for-backuprestore-statements"></a><a name="Support"></a> <span data-ttu-id="d1f0a-181">BACKUP/RESTORE ステートメントのサポート</span><span class="sxs-lookup"><span data-stu-id="d1f0a-181">Support for Backup/Restore Statements</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="d1f0a-182">BACKUP/RESTORE ステートメント</span><span class="sxs-lookup"><span data-stu-id="d1f0a-182">Backup/Restore Statement</span></span>|<span data-ttu-id="d1f0a-183">サポートされています</span><span class="sxs-lookup"><span data-stu-id="d1f0a-183">Supported</span></span>|<span data-ttu-id="d1f0a-184">例外</span><span class="sxs-lookup"><span data-stu-id="d1f0a-184">Exceptions</span></span>|<span data-ttu-id="d1f0a-185">説明</span><span class="sxs-lookup"><span data-stu-id="d1f0a-185">Comments</span></span>|  
|<span data-ttu-id="d1f0a-186">BACKUP</span><span class="sxs-lookup"><span data-stu-id="d1f0a-186">BACKUP</span></span>|<span data-ttu-id="d1f0a-187">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-187">&#x2713;</span></span>|<span data-ttu-id="d1f0a-188">BLOCKSIZE および MAXTRANSFERSIZE はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-188">BLOCKSIZE, and MAXTRANSFERSIZE are not supported.</span></span>|<span data-ttu-id="d1f0a-189">WITH CREDENTIAL を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="d1f0a-189">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="d1f0a-190">RESTORE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-190">RESTORE</span></span>|<span data-ttu-id="d1f0a-191">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-191">&#x2713;</span></span>||<span data-ttu-id="d1f0a-192">WITH CREDENTIAL を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="d1f0a-192">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="d1f0a-193">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-193">RESTORE FILELISTONLY</span></span>|<span data-ttu-id="d1f0a-194">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-194">&#x2713;</span></span>||<span data-ttu-id="d1f0a-195">WITH CREDENTIAL を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="d1f0a-195">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="d1f0a-196">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-196">RESTORE HEADERONLY</span></span>|<span data-ttu-id="d1f0a-197">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-197">&#x2713;</span></span>||<span data-ttu-id="d1f0a-198">WITH CREDENTIAL を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="d1f0a-198">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="d1f0a-199">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-199">RESTORE LABELONLY</span></span>|<span data-ttu-id="d1f0a-200">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-200">&#x2713;</span></span>||<span data-ttu-id="d1f0a-201">WITH CREDENTIAL を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="d1f0a-201">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="d1f0a-202">RESTORE VERIFYONLY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-202">RESTORE VERIFYONLY</span></span>|<span data-ttu-id="d1f0a-203">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-203">&#x2713;</span></span>||<span data-ttu-id="d1f0a-204">WITH CREDENTIAL を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="d1f0a-204">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="d1f0a-205">RESTORE REWINDONLY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-205">RESTORE REWINDONLY</span></span>|<span data-ttu-id="d1f0a-206">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-206">&#x2713;</span></span>|||  
  
 <span data-ttu-id="d1f0a-207">BACKUP ステートメントの構文と一般的な情報については、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-207">For syntax and general information about backup statements, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="d1f0a-208">RESTORE ステートメントの構文と一般的な情報については、「[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-208">For syntax and general information about restore statements, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
### <a name="support-for-backup-arguments"></a><span data-ttu-id="d1f0a-209">BACKUP の引数のサポート</span><span class="sxs-lookup"><span data-stu-id="d1f0a-209">Support for Backup Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="d1f0a-210">引数</span><span class="sxs-lookup"><span data-stu-id="d1f0a-210">Argument</span></span>|<span data-ttu-id="d1f0a-211">サポートされています</span><span class="sxs-lookup"><span data-stu-id="d1f0a-211">Supported</span></span>|<span data-ttu-id="d1f0a-212">例外</span><span class="sxs-lookup"><span data-stu-id="d1f0a-212">Exception</span></span>|<span data-ttu-id="d1f0a-213">説明</span><span class="sxs-lookup"><span data-stu-id="d1f0a-213">Comments</span></span>|  
|<span data-ttu-id="d1f0a-214">DATABASE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-214">DATABASE</span></span>|<span data-ttu-id="d1f0a-215">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-215">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-216">LOG</span><span class="sxs-lookup"><span data-stu-id="d1f0a-216">LOG</span></span>|<span data-ttu-id="d1f0a-217">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-217">&#x2713;</span></span>|||  
||  
|<span data-ttu-id="d1f0a-218">TO (URL)</span><span class="sxs-lookup"><span data-stu-id="d1f0a-218">TO (URL)</span></span>|<span data-ttu-id="d1f0a-219">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-219">&#x2713;</span></span>|<span data-ttu-id="d1f0a-220">ディスクまたはテープの場合とは異なり、URL では論理名の指定と作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-220">Unlike DISK and TAPE, URL does not support specifying or creating a logical name.</span></span>|<span data-ttu-id="d1f0a-221">この引数は、バックアップ ファイルの URL パスの指定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-221">This argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="d1f0a-222">MIRROR TO</span><span class="sxs-lookup"><span data-stu-id="d1f0a-222">MIRROR TO</span></span>|<span data-ttu-id="d1f0a-223">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-223">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-224">**WITH オプション:**</span><span class="sxs-lookup"><span data-stu-id="d1f0a-224">**WITH OPTIONS:**</span></span>||||  
|<span data-ttu-id="d1f0a-225">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="d1f0a-225">CREDENTIAL</span></span>|<span data-ttu-id="d1f0a-226">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-226">&#x2713;</span></span>||<span data-ttu-id="d1f0a-227">WITH CREDENTIAL は、BACKUP TO URL オプションを使用して Azure Blob ストレージサービスにバックアップする場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-227">WITH CREDENTIAL is only supported when using BACKUP TO URL option to back up to the Azure Blob storage service.</span></span>|  
|<span data-ttu-id="d1f0a-228">DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="d1f0a-228">DIFFERENTIAL</span></span>|<span data-ttu-id="d1f0a-229">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-229">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-230">COPY_ONLY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-230">COPY_ONLY</span></span>|<span data-ttu-id="d1f0a-231">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-231">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-232">COMPRESSION&#124;NO_COMPRESSION</span><span class="sxs-lookup"><span data-stu-id="d1f0a-232">COMPRESSION&#124;NO_COMPRESSION</span></span>|<span data-ttu-id="d1f0a-233">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-233">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-234">Description</span><span class="sxs-lookup"><span data-stu-id="d1f0a-234">DESCRIPTION</span></span>|<span data-ttu-id="d1f0a-235">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-235">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-236">NAME</span><span class="sxs-lookup"><span data-stu-id="d1f0a-236">NAME</span></span>|<span data-ttu-id="d1f0a-237">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-237">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-238">EXPIREDATE &#124; RETAINDAYS</span><span class="sxs-lookup"><span data-stu-id="d1f0a-238">EXPIREDATE &#124; RETAINDAYS</span></span>|<span data-ttu-id="d1f0a-239">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-239">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-240">NOINIT &#124; INIT</span><span class="sxs-lookup"><span data-stu-id="d1f0a-240">NOINIT &#124; INIT</span></span>|<span data-ttu-id="d1f0a-241">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-241">&#x2713;</span></span>||<span data-ttu-id="d1f0a-242">このオプションは使用しても無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-242">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="d1f0a-243">BLOB に追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-243">Appending to blobs is not possible.</span></span> <span data-ttu-id="d1f0a-244">バックアップを上書きするには、FORMAT 引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-244">To overwrite a backup use the FORMAT argument.</span></span>|  
|<span data-ttu-id="d1f0a-245">NOSKIP &#124; SKIP</span><span class="sxs-lookup"><span data-stu-id="d1f0a-245">NOSKIP &#124; SKIP</span></span>|<span data-ttu-id="d1f0a-246">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-246">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-247">NOFORMAT &#124; FORMAT</span><span class="sxs-lookup"><span data-stu-id="d1f0a-247">NOFORMAT &#124; FORMAT</span></span>|<span data-ttu-id="d1f0a-248">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-248">&#x2713;</span></span>||<span data-ttu-id="d1f0a-249">このオプションは使用しても無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-249">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="d1f0a-250">WITH FORMAT を指定した場合を除き、既存の BLOB に対して実行されるバックアップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-250">A backup taken to an existing blob fails unless WITH FORMAT is specified.</span></span> <span data-ttu-id="d1f0a-251">WITH FORMAT を指定すると、既存の BLOB が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-251">The existing blob is overwritten when WITH FORMAT is specified.</span></span>|  
|<span data-ttu-id="d1f0a-252">MEDIADESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d1f0a-252">MEDIADESCRIPTION</span></span>|<span data-ttu-id="d1f0a-253">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-253">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-254">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="d1f0a-254">MEDIANAME</span></span>|<span data-ttu-id="d1f0a-255">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-255">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-256">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-256">BLOCKSIZE</span></span>|<span data-ttu-id="d1f0a-257">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-257">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-258">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="d1f0a-258">BUFFERCOUNT</span></span>|<span data-ttu-id="d1f0a-259">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-259">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-260">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-260">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="d1f0a-261">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-261">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-262">NO_CHECKSUM &#124; CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="d1f0a-262">NO_CHECKSUM &#124; CHECKSUM</span></span>|<span data-ttu-id="d1f0a-263">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-263">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="d1f0a-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="d1f0a-265">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-265">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-266">[統計]</span><span class="sxs-lookup"><span data-stu-id="d1f0a-266">STATS</span></span>|<span data-ttu-id="d1f0a-267">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-267">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-268">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="d1f0a-268">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="d1f0a-269">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-269">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-270">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="d1f0a-270">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="d1f0a-271">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-271">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-272">NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-272">NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="d1f0a-273">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-273">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-274">NO_TRUNCATE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-274">NO_TRUNCATE</span></span>|<span data-ttu-id="d1f0a-275">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-275">&#x2713;</span></span>|||  
  
 <span data-ttu-id="d1f0a-276">BACKUP の引数の詳細については、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-276">For more information about backup arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="support-for-restore-arguments"></a><span data-ttu-id="d1f0a-277">RESTORE の引数のサポート</span><span class="sxs-lookup"><span data-stu-id="d1f0a-277">Support for Restore Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="d1f0a-278">引数</span><span class="sxs-lookup"><span data-stu-id="d1f0a-278">Argument</span></span>|<span data-ttu-id="d1f0a-279">サポートされています</span><span class="sxs-lookup"><span data-stu-id="d1f0a-279">Supported</span></span>|<span data-ttu-id="d1f0a-280">例外</span><span class="sxs-lookup"><span data-stu-id="d1f0a-280">Exceptions</span></span>|<span data-ttu-id="d1f0a-281">説明</span><span class="sxs-lookup"><span data-stu-id="d1f0a-281">Comments</span></span>|  
|<span data-ttu-id="d1f0a-282">DATABASE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-282">DATABASE</span></span>|<span data-ttu-id="d1f0a-283">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-283">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-284">LOG</span><span class="sxs-lookup"><span data-stu-id="d1f0a-284">LOG</span></span>|<span data-ttu-id="d1f0a-285">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-285">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-286">FROM (URL)</span><span class="sxs-lookup"><span data-stu-id="d1f0a-286">FROM (URL)</span></span>|<span data-ttu-id="d1f0a-287">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-287">&#x2713;</span></span>||<span data-ttu-id="d1f0a-288">FROM URL 引数は、バックアップ ファイルの URL パスの指定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-288">The FROM URL argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="d1f0a-289">**WITH Options:**</span><span class="sxs-lookup"><span data-stu-id="d1f0a-289">**WITH Options:**</span></span>||||  
|<span data-ttu-id="d1f0a-290">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="d1f0a-290">CREDENTIAL</span></span>|<span data-ttu-id="d1f0a-291">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-291">&#x2713;</span></span>||<span data-ttu-id="d1f0a-292">WITH CREDENTIAL は、RESTORE FROM URL オプションを使用して Azure Blob Storage サービスから復元する場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-292">WITH CREDENTIAL is only supported when using RESTORE FROM URL option to restore from Azure Blob Storage service.</span></span>|  
|<span data-ttu-id="d1f0a-293">PARTIAL</span><span class="sxs-lookup"><span data-stu-id="d1f0a-293">PARTIAL</span></span>|<span data-ttu-id="d1f0a-294">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-294">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="d1f0a-296">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-296">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-297">LOADHISTORY</span><span class="sxs-lookup"><span data-stu-id="d1f0a-297">LOADHISTORY</span></span>|<span data-ttu-id="d1f0a-298">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-298">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-299">MOVE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-299">MOVE</span></span>|<span data-ttu-id="d1f0a-300">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-300">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-301">REPLACE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-301">REPLACE</span></span>|<span data-ttu-id="d1f0a-302">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-302">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-303">RESTART</span><span class="sxs-lookup"><span data-stu-id="d1f0a-303">RESTART</span></span>|<span data-ttu-id="d1f0a-304">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-304">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-305">RESTRICTED_USER</span><span class="sxs-lookup"><span data-stu-id="d1f0a-305">RESTRICTED_USER</span></span>|<span data-ttu-id="d1f0a-306">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-306">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-307">FILE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-307">FILE</span></span>|<span data-ttu-id="d1f0a-308">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-308">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-309">PASSWORD</span><span class="sxs-lookup"><span data-stu-id="d1f0a-309">PASSWORD</span></span>|<span data-ttu-id="d1f0a-310">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-310">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-311">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="d1f0a-311">MEDIANAME</span></span>|<span data-ttu-id="d1f0a-312">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-312">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-313">MEDIAPASSWORD</span><span class="sxs-lookup"><span data-stu-id="d1f0a-313">MEDIAPASSWORD</span></span>|<span data-ttu-id="d1f0a-314">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-314">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-315">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-315">BLOCKSIZE</span></span>|<span data-ttu-id="d1f0a-316">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-316">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-317">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="d1f0a-317">BUFFERCOUNT</span></span>|<span data-ttu-id="d1f0a-318">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-318">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-319">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="d1f0a-319">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="d1f0a-320">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-320">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-321">CHECKSUM &#124; NO_CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="d1f0a-321">CHECKSUM &#124; NO_CHECKSUM</span></span>|<span data-ttu-id="d1f0a-322">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-322">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="d1f0a-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="d1f0a-324">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-324">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-325">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="d1f0a-325">FILESTREAM</span></span>|<span data-ttu-id="d1f0a-326">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-326">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-327">[統計]</span><span class="sxs-lookup"><span data-stu-id="d1f0a-327">STATS</span></span>|<span data-ttu-id="d1f0a-328">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-328">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-329">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="d1f0a-329">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="d1f0a-330">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-330">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-331">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="d1f0a-331">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="d1f0a-332">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-332">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-333">KEEP_REPLICATION</span><span class="sxs-lookup"><span data-stu-id="d1f0a-333">KEEP_REPLICATION</span></span>|<span data-ttu-id="d1f0a-334">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-334">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-335">KEEP_CDC</span><span class="sxs-lookup"><span data-stu-id="d1f0a-335">KEEP_CDC</span></span>|<span data-ttu-id="d1f0a-336">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-336">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span><span class="sxs-lookup"><span data-stu-id="d1f0a-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span></span>|<span data-ttu-id="d1f0a-338">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-338">&#x2713;</span></span>|||  
|<span data-ttu-id="d1f0a-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span><span class="sxs-lookup"><span data-stu-id="d1f0a-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span></span>|<span data-ttu-id="d1f0a-340">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-340">&#x2713;</span></span>|||  
  
 <span data-ttu-id="d1f0a-341">RESTORE の引数の詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-341">For more information about Restore arguments, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
##  <a name="using-backup-task-in-sql-server-management-studio"></a><a name="BackupTaskSSMS"></a><span data-ttu-id="d1f0a-342">SQL Server Management Studio でのバックアップタスクの使用</span><span class="sxs-lookup"><span data-stu-id="d1f0a-342">Using Backup Task in SQL Server Management Studio</span></span>  
 <span data-ttu-id="d1f0a-343">SQL Server Management Studio のバックアップタスクが拡張され、ターゲットオプションの1つとして URL が含められるようになりました。また、SQL 資格情報などの Azure storage へのバックアップに必要なその他のサポートオブジェクトも追加されました。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-343">The Backup task in SQL Server Management Studio has been enhanced to include URL as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span>  
  
 <span data-ttu-id="d1f0a-344">次の手順では、Azure storage へのバックアップを許可するためにデータベースのバックアップタスクに加えられた変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-344">The following steps describe the changes made to the Back Up Database task to allow for backing up to Azure storage.:</span></span>  
  
1.  <span data-ttu-id="d1f0a-345">SQL Server Management Studio を起動し、SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-345">Start SQL Server Management Studio and connect to the SQL Server instance.</span></span>  <span data-ttu-id="d1f0a-346">バックアップするデータベースを選択し、[**タスク**] を右クリックして、[**バックアップ**] を選択します。[データベースのバックアップ] ダイアログボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-346">Select a database you want to backup, and right click on **Tasks**, and select **Back Up..**. This opens the Back Up Database dialog box.</span></span>  
  
2.  <span data-ttu-id="d1f0a-347">[全般] ページの [ **URL** ] オプションを使用して、Azure storage へのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-347">On the general page the **URL** option is used to create a backup to Azure storage.</span></span> <span data-ttu-id="d1f0a-348">このオプションを選択すると、このページの他のオプションも有効になります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-348">When you select this option, you see other options enabled on this page:</span></span>  
  
    1.  <span data-ttu-id="d1f0a-349">**[ファイル名]:** バックアップ ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-349">**File Name:** Name of the backup file.</span></span>  
  
    2.  <span data-ttu-id="d1f0a-350">**[SQL 資格情報]:** 既存の SQL Server 資格情報を指定することも、[SQL 資格情報] の横にある **[作成]** をクリックして新しい資格情報を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-350">**SQL Credential:** You can either specify an existing SQL Server Credential, or can create a new one by clicking on the **Create** next to the SQL Credential box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="d1f0a-351">**[作成]** をクリックすると開くダイアログでは、サブスクリプションの管理証明書または公開プロファイルが求められます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-351">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="d1f0a-352">SQL Server では現在、公開プロファイルのバージョン 2.0 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-352">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="d1f0a-353">公開プロファイルのサポート対象バージョンをダウンロードするには、「 [公開プロファイルのバージョン 2.0 のダウンロード](https://go.microsoft.com/fwlink/?LinkId=396421)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-353">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
        >   
        >  <span data-ttu-id="d1f0a-354">管理証明書または公開プロファイルにアクセスできない場合は、Transact-SQL または SQL Server Management Studio を使用してストレージ アカウント名とアクセス キーの情報を指定し、SQL 資格情報を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-354">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="d1f0a-355">Transact-sql を使用して資格情報を作成するには、「[資格情報の作成](#credential)」セクションのサンプルコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-355">See the sample code in the [Create a Credential](#credential) section to create a credential using Transact-SQL.</span></span> <span data-ttu-id="d1f0a-356">または SQL Server Management Studio を使用して、データベース エンジン インスタンスから、 **[セキュリティ]** を右クリックし、 **[新規作成]**、 **[資格情報]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-356">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="d1f0a-357">**[ID]** にストレージ アカウント名、 **[パスワード]** にアクセス キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-357">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
    3.  <span data-ttu-id="d1f0a-358">**Azure ストレージコンテナー:** バックアップファイルを格納する Azure storage コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-358">**Azure storage container:** The name of the Azure storage container to store the backup files.</span></span>  
  
    4.  <span data-ttu-id="d1f0a-359">**[URL プレフィックス]:** 前の手順で説明したフィールドで指定された情報を使用して、自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-359">**URL prefix:** This is built automatically using the information specified in the fields described in the previous steps.</span></span> <span data-ttu-id="d1f0a-360">この値を手動で編集する場合は、前に入力した他の情報と一致することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-360">If you do edit this value manually, make sure it matches with the other information you provided previously.</span></span> <span data-ttu-id="d1f0a-361">たとえばストレージの URL を変更する場合は、[SQL 資格情報] も、同じストレージ アカウントに対する認証を行うように設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-361">For example if you modify the storage URL, make sure the SQL Credential is set to authenticate to the same storage account.</span></span>  
  
 <span data-ttu-id="d1f0a-362">バックアップ先として [URL] を選択すると、 **[メディア オプション]** ページの一部のオプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-362">When you select URL as the destination, certain options in the **Media Options** page are disabled.</span></span>  <span data-ttu-id="d1f0a-363">[データベースのバックアップ] ダイアログの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-363">The following topics have more information on the Back Up Database dialog:</span></span>  
  
 [<span data-ttu-id="d1f0a-364">データベースのバックアップ &#40;全般ページ&#41;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-364">Back Up Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [<span data-ttu-id="d1f0a-365">データベースのバックアップ &#40;メディア オプション ページ&#41;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-365">Back Up Database &#40;Media Options Page&#41;</span></span>](back-up-database-media-options-page.md)  
  
 [<span data-ttu-id="d1f0a-366">データベースのバックアップ &#40;バックアップ オプション ページ&#41;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-366">Back Up Database &#40;Backup Options Page&#41;</span></span>](back-up-database-backup-options-page.md)  
  
 [<span data-ttu-id="d1f0a-367">資格情報の作成 - Azure ストレージに対する認証</span><span class="sxs-lookup"><span data-stu-id="d1f0a-367">Create Credential - Authenticate to Azure Storage</span></span>](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="sql-server-backup-to-url-using-maintenance-plan-wizard"></a><a name="MaintenanceWiz"></a><span data-ttu-id="d1f0a-368">メンテナンスプランウィザードを使用した URL へのバックアップの SQL Server</span><span class="sxs-lookup"><span data-stu-id="d1f0a-368">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>  
 <span data-ttu-id="d1f0a-369">前に説明したバックアップタスクと同様に、SQL Server Management Studio のメンテナンスプランウィザードが拡張され、ターゲットオプションの1つとして**URL**が含められるようになりました。また、SQL 資格情報などの Azure storage へのバックアップに必要なその他のサポートオブジェクトも追加されました。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-369">Similar to the backup task described previously, the Maintenance Plan Wizard in SQL Server Management Studio has been enhanced to include **URL** as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span> <span data-ttu-id="d1f0a-370">詳細については、「 **Using Maintenance Plan Wizard** 」の「 [バックアップ タスクを定義する](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-370">For more information, see  the **Define Backup Tasks** section in [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).</span></span>  
  
##  <a name="restoring-from-azure-storage-using-sql-server-management-studio"></a><a name="RestoreSSMS"></a><span data-ttu-id="d1f0a-371">SQL Server Management Studio を使用した Azure storage からの復元</span><span class="sxs-lookup"><span data-stu-id="d1f0a-371">Restoring from Azure storage Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d1f0a-372">データベースを復元する場合、復元元のデバイスとして **[URL]** が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-372">If you are restoring a database, **URL** is included as the device to restore from.</span></span> <span data-ttu-id="d1f0a-373">次の手順では、Azure storage からの復元を可能にする復元タスクの変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-373">Following steps describe the changes in the Restore task to allow restoring from Azure storage:</span></span>  
  
1.  <span data-ttu-id="d1f0a-374">SQL Server Management Studio の復元タスクの **[全般]** ページで **[デバイス]** を選択すると、 **[バックアップ デバイスの選択]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは、バックアップ メディアの種類として **[URL]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-374">When you select **Devices** in the **General** page of the Restore task in SQL Server Management Studio, this takes you to the **Select backup devices** dialog box which includes **URL** as a backup media type.</span></span>  
  
2.  <span data-ttu-id="d1f0a-375">**[URL]** を選択し、 **[追加]** をクリックすると、 **[Azure ストレージへの接続]** ダイアログが開きます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-375">When you select **URL** and click **Add**, this opens the **Connect to Azure storage** dialog.</span></span> <span data-ttu-id="d1f0a-376">Azure storage に対して認証する SQL 資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-376">Specify the SQL Credential information to authenticate to Azure storage.</span></span>  
  
3.  <span data-ttu-id="d1f0a-377">SQL Server、指定した SQL 資格情報を使用して Azure storage に接続し、[ **azure でのバックアップファイルの検索**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-377">SQL Server then connects to Azure storage using the SQL Credential information you provided and opens the **Locate Backup File in Azure** dialog.</span></span> <span data-ttu-id="d1f0a-378">このページには、ストレージに存在するバックアップ ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-378">The backup files residing in the storage are displayed on this page.</span></span> <span data-ttu-id="d1f0a-379">復元に使用するファイルを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-379">Select the file you want to use to restore and click **OK**.</span></span> <span data-ttu-id="d1f0a-380">これにより、 **[バックアップデバイスの選択**] ダイアログボックスが表示されます。このダイアログボックスで [ **OK]** をクリックすると、メインの [**復元**] ダイアログに戻り、復元を完了できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-380">This takes you back to the **Select Backup Devices** dialog, and Clicking **OK** on this dialog takes you back to the main **Restore** dialog where you will be able complete the restore.</span></span>  <span data-ttu-id="d1f0a-381">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-381">For more information see, the following topics:</span></span>  
  
     <span data-ttu-id="d1f0a-382">[[データベースの復元] &#40;[全般] ページ&#41;](restore-database-general-page.md)</span><span class="sxs-lookup"><span data-stu-id="d1f0a-382">[Restore Database &#40;General Page&#41;](restore-database-general-page.md)</span></span>  
  
     <span data-ttu-id="d1f0a-383">[[データベースの復元] &#40;[ファイル] ページ&#41;](restore-database-files-page.md)</span><span class="sxs-lookup"><span data-stu-id="d1f0a-383">[Restore Database &#40;Files Page&#41;](restore-database-files-page.md)</span></span>  
  
     <span data-ttu-id="d1f0a-384">[[データベースの復元] &#40;[オプション] ページ&#41;](restore-database-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="d1f0a-384">[Restore Database &#40;Options Page&#41;](restore-database-options-page.md)</span></span>  
  
##  <a name="code-examples"></a><a name="Examples"></a> <span data-ttu-id="d1f0a-385">コード例</span><span class="sxs-lookup"><span data-stu-id="d1f0a-385">Code Examples</span></span>  
 <span data-ttu-id="d1f0a-386">ここでは、次の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-386">This section contains the following examples.</span></span>  
  
-   [<span data-ttu-id="d1f0a-387">Shared Access Signature の作成</span><span class="sxs-lookup"><span data-stu-id="d1f0a-387">Create a Credential</span></span>](#credential)  
  
-   [<span data-ttu-id="d1f0a-388">データベース全体をバックアップする</span><span class="sxs-lookup"><span data-stu-id="d1f0a-388">Backing up a complete database</span></span>](#complete)  
  
-   [<span data-ttu-id="d1f0a-389">データベースおよびログをバックアップする</span><span class="sxs-lookup"><span data-stu-id="d1f0a-389">Backing up the database and log</span></span>](#databaselog)  
  
-   [<span data-ttu-id="d1f0a-390">プライマリ ファイル グループのファイル全体のバックアップを作成する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-390">Creating a full file backup of the primary filegroup</span></span>](#filebackup)  
  
-   [<span data-ttu-id="d1f0a-391">プライマリ ファイル グループのファイルの差分バックアップを作成する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-391">Creating a differential file backup of the primary filegroups</span></span>](#differential)  
  
-   [<span data-ttu-id="d1f0a-392">データベースを復元しファイルを移動する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-392">Restoring a database and move files</span></span>](#restoredbwithmove)  
  
-   [<span data-ttu-id="d1f0a-393">STOPAT を使って特定の時点の状態に復元する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-393">Restoring to a point-in-time using STOPAT</span></span>](#PITR)  
  
###  <a name="create-a-credential"></a><a name="credential"></a> <span data-ttu-id="d1f0a-394">Shared Access Signature の作成</span><span class="sxs-lookup"><span data-stu-id="d1f0a-394">Create a Credential</span></span>  
 <span data-ttu-id="d1f0a-395">次の例では、Azure Storage 認証情報を格納する資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-395">The following example creates a credential that stores the Azure Storage authentication information.</span></span>  

   ```sql
   IF NOT EXISTS  
   (SELECT * FROM sys.credentials   
   WHERE credential_identity = 'mycredential')  
   CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
   ,SECRET = '<storage access key>' ;  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
   string secret = "<storage access key>";  
  
   // Create a Credential  
   string credentialName = "mycredential";  
   Credential credential = new Credential(server, credentialName);  
   credential.Create(identity, secret);  
   ```  
  
   ```powershell
   # create variables  
   $storageAccount = "mystorageaccount"  
   $storageKey = "<storage access key>"  
   $secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
   $credentialName = "mycredential"  
  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Create a credential  
   New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString
   ```  
  
###  <a name="backing-up-a-complete-database"></a><a name="complete"></a><span data-ttu-id="d1f0a-396">データベース全体のバックアップ</span><span class="sxs-lookup"><span data-stu-id="d1f0a-396">Backing up a complete database</span></span>  
 <span data-ttu-id="d1f0a-397">次の例では、AdventureWorks2012 データベースを Azure Blob ストレージサービスにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-397">The following example backs up the AdventureWorks2012 database to the Azure Blob storage service.</span></span>
  
   ```sql
   BACKUP DATABASE AdventureWorks2012   
   TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
         WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
   GO
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);  
   ```
  
   ```powershell
   # create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
   # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance  
   CD $srvPath   
   $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On
   ```  
  
###  <a name="backing-up-the-database-and-log"></a><a name="databaselog"></a><span data-ttu-id="d1f0a-398">データベースとログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="d1f0a-398">Backing up the database and log</span></span>  
 <span data-ttu-id="d1f0a-399">次の例では、AdventureWorks2012 サンプル データベースをバックアップします。このデータベースでは、既定で単純復旧モデルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-399">The following example backups up the AdventureWorks2012 sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="d1f0a-400">ここではまず、ログをバックアップするため、完全復旧モデルを使用するよう AdventureWorks2012 データベースを変更します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-400">To support log backups, the AdventureWorks2012 database is modified to use the full recovery model.</span></span> <span data-ttu-id="d1f0a-401">この例では、Azure Blob へのデータベースの完全バックアップを作成し、更新操作の期間後に、ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-401">The example then creates a full database backup to Azure Blob, and after a period of update activity, backs up the log.</span></span> <span data-ttu-id="d1f0a-402">この例では、日付と時刻のタイム スタンプを含むバックアップ ファイル名を作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-402">This example creates a backup file name with a datetime stamp.</span></span>  
  
   ```sql
   -- To permit log backups, before the full database backup, modify the database   
   -- to use the full recovery model.  
   USE master;  
   GO  
   ALTER DATABASE AdventureWorks2012  
      SET RECOVERY FULL;  
   GO  
  
   -- Back up the full AdventureWorks2012 database.  
          -- First create a file name for the backup file with DateTime stamp  
  
   DECLARE @Full_Filename AS VARCHAR (300);  
   SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
   --Back up Adventureworks2012 database  
  
   BACKUP DATABASE AdventureWorks2012  
   TO URL =  @Full_Filename  
   WITH CREDENTIAL = 'mycredential';  
   ,COMPRESSION  
   GO  
   -- Back up the AdventureWorks2012 log.  
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url for data backup  
   string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database to Url  
   Backup backupData = new Backup();  
   backupData.CredentialName = credentialName;  
   backupData.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
   backupData.SqlBackup(server);  
  
   // Generate Unique Url for data backup  
   string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database Log to Url  
   Backup backupLog = new Backup();  
   backupLog.CredentialName = credentialName;  
   backupLog.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
   backupLog.Action = BackupActionType.Log;  
   backupLog.SqlBackup(server);  
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to theSQL Server Instance
   CD $srvPath   
   #Create a unique file name for the full database backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Backup Database to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
   #Create a unique file name for log backup  
  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup Log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log
   ```  
  
###  <a name="creating-a-full-file-backup-of-the-primary-filegroup"></a><a name="filebackup"></a><span data-ttu-id="d1f0a-403">プライマリファイルグループの完全ファイルバックアップを作成する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-403">Creating a full file backup of the primary filegroup</span></span>  
 <span data-ttu-id="d1f0a-404">次の例では、プライマリ ファイル グループのファイル全体のバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-404">The following example creates a full file backup of the primary filegroup.</span></span>
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to the SQL Server Instance  
  
   CD $srvPath   
   #Create a unique file name for the file backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
   #Backup Primary File Group to URL  
  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary
   ```  
  
###  <a name="creating-a-differential-file-backup-of-the-primary-filegroup"></a><a name="differential"></a><span data-ttu-id="d1f0a-405">プライマリファイルグループのファイルの差分バックアップを作成する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-405">Creating a differential file backup of the primary filegroup</span></span>  
 <span data-ttu-id="d1f0a-406">次の例では、プライマリ ファイル グループのファイルの差分バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-406">The following example creates a differential file backup of the primary filegroup.</span></span>  
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
   GO
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.Incremental = true;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server); 
   ```

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Create a differential backup of the primary filegroup
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental
   ```  
  
###  <a name="restore-a-database-and-move-files"></a><a name="restoredbwithmove"></a><span data-ttu-id="d1f0a-407">データベースを復元してファイルを移動する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-407">Restore a database and move files</span></span>  
 <span data-ttu-id="d1f0a-408">データベースの完全バックアップを復元し、復元したデータベースを C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data ディレクトリに移動するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-408">To restore a full database backup and move the restored database to C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data directory, use the following steps.</span></span>
  
   ```sql
   -- Backup the tail of the log first
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
   GO  
  
   RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
   WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for tail log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
   restore.SqlRestore(server);
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)
   ```  
  
###  <a name="restoring-to-a-point-in-time-using-stopat"></a><a name="PITR"></a> <span data-ttu-id="d1f0a-409">STOPAT を使って特定の時点の状態に復元する</span><span class="sxs-lookup"><span data-stu-id="d1f0a-409">Restoring to a point-in-time using STOPAT</span></span>  
 <span data-ttu-id="d1f0a-410">次の例では、データベースを特定の時点の状態に復元し、復元操作を示します。</span><span class="sxs-lookup"><span data-stu-id="d1f0a-410">The following example restores a database to its state to a point in time, and shows a restore operation.</span></span>  
  
   ```sql
   RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
   WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
   GO   
  
   RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
   WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
   GO  
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for Tail Log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.NoRecovery = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
   restore.SqlRestore(server);  
      
   // Restore transaction Log with stop at   
   Restore restoreLog = new Restore();  
   restoreLog.CredentialName = credentialName;  
   restoreLog.Database = dbName;  
   restoreLog.Action = RestoreActionType.Log;  
   restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restoreLog.ToPointInTime = DateTime.Now.ToString();   
   restoreLog.SqlRestore(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Navigate to SQL Server Instance Directory
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
   # Restore Transaction log with Stop At:  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()
   ```  
  
## <a name="see-also"></a><span data-ttu-id="d1f0a-411">参照</span><span class="sxs-lookup"><span data-stu-id="d1f0a-411">See Also</span></span>  
 <span data-ttu-id="d1f0a-412">[SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="d1f0a-412">[SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span></span>  
 [<span data-ttu-id="d1f0a-413">システム データベースのバックアップと復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1f0a-413">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](back-up-and-restore-of-system-databases-sql-server.md)   
