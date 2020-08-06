---
title: 'レッスン 5: OptionalTDE を使用してデータベースを暗号化する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 613b66c04a69364f3c9be1059f95021dd3eff595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642079"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a><span data-ttu-id="816ba-103">レッスン 5:</span><span class="sxs-lookup"><span data-stu-id="816ba-103">Lesson 5.</span></span> <span data-ttu-id="816ba-104">(省略可) TDE を使用してデータベースを暗号化する</span><span class="sxs-lookup"><span data-stu-id="816ba-104">(Optional) Encrypt your database using TDE</span></span>
  <span data-ttu-id="816ba-105">省略可能な手順として、新しく作成したデータベースを暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="816ba-105">As an optional step, you can encrypt the newly created database.</span></span> <span data-ttu-id="816ba-106">透過的なデータ暗号化 (TDE) では、データとログ ファイルの暗号化と暗号化解除がリアルタイムの I/O で実行されます。</span><span class="sxs-lookup"><span data-stu-id="816ba-106">Transparent data encryption (TDE) performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="816ba-107">この種の暗号化にはデータベース暗号化キー (DEK) が使用されます。これは、復旧時に使用できるようにデータベース ブート レコードに保存されます。</span><span class="sxs-lookup"><span data-stu-id="816ba-107">This kind of encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="816ba-108">詳細については、「 [tde&#41;の Transparent Data Encryption &#40;](security/encryption/transparent-data-encryption.md) [Tde で保護されたデータベースを別の SQL Server に移動する](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816ba-108">For more information, see [Transparent Data Encryption &#40;TDE&#41;](security/encryption/transparent-data-encryption.md) and [Move a TDE Protected Database to Another SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).</span></span>  
  
 <span data-ttu-id="816ba-109">このレッスンは、次の手順を完了済みであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="816ba-109">This lesson assumes you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="816ba-110">Azure Storage アカウントを持っています。</span><span class="sxs-lookup"><span data-stu-id="816ba-110">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="816ba-111">Azure Storage アカウントでコンテナーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="816ba-111">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="816ba-112">読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="816ba-112">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="816ba-113">SAS キーも生成しました。</span><span class="sxs-lookup"><span data-stu-id="816ba-113">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="816ba-114">ソース コンピューターで SQL Server 資格情報を作成しました。</span><span class="sxs-lookup"><span data-stu-id="816ba-114">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="816ba-115">レッスン 4 で説明された手順に従って、データベースを作成しました。</span><span class="sxs-lookup"><span data-stu-id="816ba-115">You have created a database by following the steps that are described in Lesson 4.</span></span>  
  
 <span data-ttu-id="816ba-116">データベースを暗号化する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="816ba-116">If you want to encrypt a database, follow these steps:</span></span>  
  
1.  <span data-ttu-id="816ba-117">ソース コンピューターで、クエリ ウィンドウで次のステートメントを変更して実行します。</span><span class="sxs-lookup"><span data-stu-id="816ba-117">In the source machine, modify and run the following statements in a query window:</span></span>  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  <span data-ttu-id="816ba-118">次の手順に従って、ソース コンピューターの新しいデータベースを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="816ba-118">Then, encrypt your new database in the source machine by following these steps:</span></span>  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 <span data-ttu-id="816ba-119">データベースの暗号化の状態と、関連付けられたデータベース暗号化キーを確認するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="816ba-119">If you want to learn the encryption state of a database and its associated database encryption keys, run the following statement:</span></span>  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 <span data-ttu-id="816ba-120">このレッスンで使用した Transact-sql ステートメントの詳細については、「 [CREATE database &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」、「 [ALTER database &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)」、「Create [MASTER KEY &#40;Transact-sql ](/sql/t-sql/statements/create-master-key-transact-sql)&#41;」、「 [create CERTIFICATE &#40;transact-sql ](/sql/t-sql/statements/create-certificate-transact-sql)&#41;、および dm_database_encryption_keys [&#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816ba-120">For detailed information the Transact-SQL statements that have been used in this lesson, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), and [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).</span></span>  
  
 <span data-ttu-id="816ba-121">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="816ba-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="816ba-122">レッスン 6: オンプレミスのソース コンピューターから Azure のターゲット コンピューターにデータベースを移行する</span><span class="sxs-lookup"><span data-stu-id="816ba-122">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
