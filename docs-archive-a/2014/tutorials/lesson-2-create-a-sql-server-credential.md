---
title: 'レッスン 2: SQL Server の資格情報を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e8b13c8d4d9e5937064cef5503ec64bfd6e4a2d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742705"
---
# <a name="lesson-2-create-a-sql-server-credential"></a><span data-ttu-id="63f4c-102">レッスン 2: SQL Server 資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="63f4c-102">Lesson 2: Create a SQL Server Credential</span></span>
  <span data-ttu-id="63f4c-103">**資格情報:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="63f4c-103">**Credential:** A [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="63f4c-104">ここでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップと復元のプロセスで、Azure Blob ストレージサービスに対する認証に資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="63f4c-104">Here, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="63f4c-105">資格情報には、ストレージ アカウントの名前とその **アクセス キー** 値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="63f4c-105">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="63f4c-106">作成した資格情報は、BACKUP/RESTORE ステートメントの実行時に WITH CREDENTIAL オプションで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63f4c-106">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="63f4c-107">ストレージアカウントの**アクセスキー**を表示、コピー、または再生成する方法の詳細については、「[ストレージアカウントのアクセスキー](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63f4c-107">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="63f4c-108">資格情報に関する一般情報については、「[資格](../relational-databases/security/authentication-access/credentials-database-engine.md)情報」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63f4c-108">For general information about credentials, see [Credentials](../relational-databases/security/authentication-access/credentials-database-engine.md).</span></span>  
  
 <span data-ttu-id="63f4c-109">資格情報が使用されるその他の例については、「 [Create a SQL Server エージェント Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63f4c-109">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63f4c-110">以下で説明する SQL Server 資格情報を作成するための要件は、SQL Server バックアッププロセス ([SQL Server backup TO URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)、および[SQL Server Managed backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)) に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="63f4c-110">The requirements for creating a SQL Server credential described below are specific to SQL Server backup processes ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), and [SQL Server Managed  Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)).</span></span> <span data-ttu-id="63f4c-111">SQL Server では、Azure ストレージにアクセスしてバックアップの書き込みまたは読み取りを行う場合、ストレージ アカウント名とアクセス キーの情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="63f4c-111">SQL Server, when accessing Azure storage to write or read backups uses the storage account name and access key information.</span></span>  <span data-ttu-id="63f4c-112">Azure ストレージにデータベース ファイルを格納するための資格情報の作成方法については、「 [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63f4c-112">For more information on creating credentials for storing database files in Azure storage, see [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)</span></span>  
  
## <a name="create-a-sql-server-credential"></a><span data-ttu-id="63f4c-113">SQL Server 資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="63f4c-113">Create a SQL Server Credential</span></span>  
 <span data-ttu-id="63f4c-114">SQL Server 資格情報を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="63f4c-114">To create a SQL Server Credential, use the following steps:</span></span>  
  
1.  <span data-ttu-id="63f4c-115">SQL Server Management Studio に接続します。</span><span class="sxs-lookup"><span data-stu-id="63f4c-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="63f4c-116">オブジェクト エクスプローラーで、AdventureWorks2012 データベースがインストールされているデータベース エンジンのインスタンスに接続するか、このチュートリアルに使用する独自のデータベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="63f4c-116">In Object Explorer, connect to the instance of Database Engine that has AdventureWorks2012 database installed, or use your own database you plan to use for this tutorial.</span></span>  
  
3.  <span data-ttu-id="63f4c-117">**[標準]** ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63f4c-117">On the **Standard** tool bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="63f4c-118">次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="63f4c-118">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     <span data-ttu-id="63f4c-119">![sql 資格情報へのストレージ アカウントのマッピング](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "sql 資格情報へのストレージ アカウントのマッピング")</span><span class="sxs-lookup"><span data-stu-id="63f4c-119">![mapping storage account to sql credentials](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
5.  <span data-ttu-id="63f4c-120">T-sql ステートメントを確認し、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63f4c-120">Verify the T-SQL statement and click **Execute**.</span></span>  
  
 <span data-ttu-id="63f4c-121">バックアップの概念と要件に関する Azure Blob storage サービスの詳細については、「 [Azure Blob Storage サービスを使用したバックアップと復元の SQL Server](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63f4c-121">For more information about the Azure Blob storage service for backup concepts and requirements, see [SQL Server Backup and Restore with Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="63f4c-122">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="63f4c-122">Next Lesson</span></span>  
 <span data-ttu-id="63f4c-123">[レッスン 3: Azure Blob Storage サービスにデータベースの完全バックアップを書き込み](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)ます。</span><span class="sxs-lookup"><span data-stu-id="63f4c-123">[Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).</span></span>  
  
  
