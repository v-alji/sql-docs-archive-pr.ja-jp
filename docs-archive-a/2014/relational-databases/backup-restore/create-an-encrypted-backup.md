---
title: 暗号化されたバックアップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d46cc686684d87fe393a5db7cfe01194ae917836
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740087"
---
# <a name="create-an-encrypted-backup"></a><span data-ttu-id="3c973-102">暗号化されたバックアップの作成</span><span class="sxs-lookup"><span data-stu-id="3c973-102">Create an Encrypted Backup</span></span>
  <span data-ttu-id="3c973-103">このトピックでは、暗号化されたバックアップを Transact-SQL で作成するために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c973-103">This topic describes the steps necessary to create an encrypted backup using Transact-SQL.</span></span>  
  
## <a name="backup-to-disk-with-encryption"></a><span data-ttu-id="3c973-104">暗号化の使用によるディスクへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="3c973-104">Backup to Disk with Encryption</span></span>  
 <span data-ttu-id="3c973-105">**前提条件:**</span><span class="sxs-lookup"><span data-stu-id="3c973-105">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="3c973-106">データベースのバックアップを作成するための空き領域が十分にあるローカル ディスクまたはストレージへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="3c973-106">Access to a local disk or to storage with adequate space to create a backup of the database.</span></span>  
  
-   <span data-ttu-id="3c973-107">master データベースのデータベース マスター キー、SQL Server インスタンスで使用可能な証明書または非対称キー。</span><span class="sxs-lookup"><span data-stu-id="3c973-107">A Database Master Key for the master database, and a certificate or asymmetric key available on the instance of SQL Server.</span></span> <span data-ttu-id="3c973-108">暗号化の要件と権限については、「 [バックアップの暗号化](backup-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c973-108">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
 <span data-ttu-id="3c973-109">データベースの暗号化されたバックアップをローカル ディスクに作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3c973-109">Use the following steps to create an encrypted backup of a database to a local disk.</span></span> <span data-ttu-id="3c973-110">この例では、MyTestDB というユーザー データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c973-110">This example uses a user database called MyTestDB.</span></span>  
  
1.  <span data-ttu-id="3c973-111">**master データベースのデータベース マスター キーの作成:** データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c973-111">**Create a Database Master Key of the master database:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="3c973-112">データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-112">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  <span data-ttu-id="3c973-113">**バックアップ証明書の作成:** master データベースでバックアップ証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c973-113">**Create a Backup Certificate:** Create a backup certificate in the master database.</span></span> <span data-ttu-id="3c973-114">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-114">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="3c973-115">**データベースのバックアップ:** 使用する暗号化アルゴリズムと証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c973-115">**Backup the database:** Specify the encryption algorithm and certificate to use.</span></span> <span data-ttu-id="3c973-116">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-116">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 <span data-ttu-id="3c973-117">EKM で保護されているバックアップの暗号化の例については、「[Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c973-117">For an example of encrypting a backup protected by an EKM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
### <a name="backup-to-azure-storage-with-encryption"></a><span data-ttu-id="3c973-118">暗号化して Azure Storage にバックアップする</span><span class="sxs-lookup"><span data-stu-id="3c973-118">Backup to Azure Storage with Encryption</span></span>  
 <span data-ttu-id="3c973-119">**[SQL Server Backup to URL]** オプションを使用して Azure Storage へのバックアップを作成する場合、暗号化の手順は同じですが、バックアップ先として URL を使用し、Azure Storage への認証用に SQL 資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c973-119">If you are creating a backup to Azure storage using the **SQL Server Backup to URL** option, the encryption steps are the same, but you must use URL as the destination and a SQL Credential to authenticate to the Azure storage.</span></span> <span data-ttu-id="3c973-120">暗号化オプションを使用してを構成する場合は [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 、「 [azure への管理](enable-sql-server-managed-backup-to-microsoft-azure.md)されたバックアップのセットアップ SQL Server」および「 [azure への管理されたバックアップの SQL Server 設定](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c973-120">If you want to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with encryption options, see [Setting up SQL Server Managed Backup to Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 <span data-ttu-id="3c973-121">**前提条件:**</span><span class="sxs-lookup"><span data-stu-id="3c973-121">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="3c973-122">Windows ストレージ アカウントとコンテナー。</span><span class="sxs-lookup"><span data-stu-id="3c973-122">A windows storage account and a container.</span></span> <span data-ttu-id="3c973-123">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c973-123">For more information, see.</span></span> <span data-ttu-id="3c973-124">[レッスン 1:Azure ストレージ オブジェクトの作成](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="3c973-124">[Lesson 1: Create Azure Storage Objects](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).</span></span>  
  
-   <span data-ttu-id="3c973-125">master データベースのデータベース マスター キー、SQL Server インスタンス上の証明書または非対称キー。</span><span class="sxs-lookup"><span data-stu-id="3c973-125">A Database Master Key for the master database, and a certificate or asymmetric key  on the instance of SQL Server.</span></span> <span data-ttu-id="3c973-126">暗号化の要件と権限については、「 [バックアップの暗号化](backup-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c973-126">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
1.  <span data-ttu-id="3c973-127">**SQL Server 資格情報の作成:** SQL Server 資格情報を作成するには、データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-127">**Create SQL Server Credential:** To create a SQL Server credential, connect to the Database Engine, open a new query window, and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  <span data-ttu-id="3c973-128">**データベースのマスター キーを作成する:** データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c973-128">**Create a Database Master Key:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="3c973-129">データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-129">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="3c973-130">**バックアップ証明書の作成:** master データベースでバックアップ証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c973-130">**Create a Backup Certificate:** Create a Backup Certificate in the master database.</span></span> <span data-ttu-id="3c973-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-131">Copy and paste the following example in the query window and click **Execute**</span></span>  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  <span data-ttu-id="3c973-132">**データベースのバックアップ:** 使用する暗号化アルゴリズムと証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c973-132">**Backup the database:** Specify the encryption algorithm and the certificate to use.</span></span> <span data-ttu-id="3c973-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c973-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
