---
title: バックアップの暗号化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6a78ae4969982fbfe5295ee4219855f48ac60793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743338"
---
# <a name="backup-encryption"></a><span data-ttu-id="66464-102">バックアップの暗号化</span><span class="sxs-lookup"><span data-stu-id="66464-102">Backup Encryption</span></span>
  <span data-ttu-id="66464-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップの暗号化オプションについて概説します。</span><span class="sxs-lookup"><span data-stu-id="66464-103">This topic provides an overview of the encryption options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="66464-104">バックアップ時の暗号化の使用、利点、および推奨される操作の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="66464-104">It includes details of the usage, benefits, and recommended practices for encrypting during backup.</span></span>  
  
  
##  <a name="overview"></a><a name="Overview"></a> <span data-ttu-id="66464-105">概要</span><span class="sxs-lookup"><span data-stu-id="66464-105">Overview</span></span>  
 <span data-ttu-id="66464-106">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]以降では、バックアップの作成時に SQL Server がデータを暗号化する機能があります。</span><span class="sxs-lookup"><span data-stu-id="66464-106">Starting in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SQL Server has the ability to encrypt the data while creating a backup.</span></span> <span data-ttu-id="66464-107">バックアップの作成時に暗号化アルゴリズムと暗号化機能 (証明書または非対称キー) を指定することにより、暗号化されたバックアップ ファイルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="66464-107">By specifying the encryption algorithm and the encryptor (a Certificate or Asymmetric Key) when creating a backup, you can create an encrypted backup file.</span></span> <span data-ttu-id="66464-108">あらゆるバックアップ先ストレージ、つまり内部設置型のストレージも Window Azure ストレージもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="66464-108">All storage destinations: on-premises and Window Azure storage are supported.</span></span> <span data-ttu-id="66464-109">また、暗号化オプションは、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] で導入された新機能である [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]の操作用に構成できます。</span><span class="sxs-lookup"><span data-stu-id="66464-109">In addition, encryption options can be configured for [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] operations, a new feature introduced in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="66464-110">バックアップ時に暗号化を行うには、暗号化アルゴリズムを指定し、暗号化キーを保護するための暗号化機能を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66464-110">To encrypt during backup, you must specify an encryption algorithm, and an encryptor to secure the encryption key.</span></span> <span data-ttu-id="66464-111">サポートされている暗号化オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="66464-111">The following are the supported encryption options:</span></span>  
  
-   <span data-ttu-id="66464-112">**暗号化アルゴリズム:** サポートされている暗号化アルゴリズムは、AES 128、AES 192、AES 256、および Triple DES です</span><span class="sxs-lookup"><span data-stu-id="66464-112">**Encryption Algorithm:** The supported encryption algorithms are: AES 128, AES 192, AES 256, and Triple DES</span></span>  
  
-   <span data-ttu-id="66464-113">**暗号化機能:** 証明書キーまたは非対称キー</span><span class="sxs-lookup"><span data-stu-id="66464-113">**Encryptor:** A certificate or asymmetric Key</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="66464-114">証明書または非対称キーをバックアップすることが非常に重要であり、これらを使用して暗号化したバックアップ ファイルとは別の場所に保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66464-114">It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt.</span></span> <span data-ttu-id="66464-115">証明書または非対称キーがないと、バックアップ ファイルが使用不可能になり、バックアップを復元することができません。</span><span class="sxs-lookup"><span data-stu-id="66464-115">Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable.</span></span>  
  
 <span data-ttu-id="66464-116">**暗号化されたバックアップの復元:** SQL Server の復元では、復元時に暗号化パラメーターを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66464-116">**Restoring the encrypted backup:** SQL Server restore does not require any encryption parameters to be specified during restores.</span></span> <span data-ttu-id="66464-117">ただし、バックアップ ファイルの暗号化に使用された証明書または非対称キーを復元先のインスタンスで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="66464-117">It does require that the certificate or the asymmetric key used to encrypt the backup file be available on the instance that you are restoring to.</span></span> <span data-ttu-id="66464-118">復元を実行するユーザー アカウントには、証明書またはキーに対する `VIEW DEFINITION` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="66464-118">The user account performing the restore must have `VIEW DEFINITION` permissions on the certificate or key.</span></span> <span data-ttu-id="66464-119">暗号化されたバックアップを別のインスタンスに復元する場合は、そのインスタンスで証明書を使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="66464-119">If you are restoring the encrypted backup to a different instance, you must make sure that the certificate is available on that instance.</span></span>  
  
 <span data-ttu-id="66464-120">TDE で暗号化されたデータベースからバックアップを復元する場合、復元先のインスタンスで TDE の証明書を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="66464-120">If you are restoring a backup from a TDE encrypted database, the TDE certificate should be available on the instance you are restoring to.</span></span>  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="66464-121">利点</span><span class="sxs-lookup"><span data-stu-id="66464-121">Benefits</span></span>  
  
1.  <span data-ttu-id="66464-122">データベースのバックアップを暗号化することは、データの保護に役立ちます。SQL Server では、バックアップの作成時にバックアップ データを暗号化するためのオプションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="66464-122">Encrypting the database backups helps secure the data: SQL Server provides the option to encrypt the backup data while creating a backup.</span></span>  
  
2.  <span data-ttu-id="66464-123">暗号化は、TDE を使用して暗号化されたデータベースにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="66464-123">Encryption can also be used for databases that are encrypted using TDE.</span></span>  
  
3.  <span data-ttu-id="66464-124">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]によって実行されたバックアップでも暗号化がサポートされるため、オフサイト バックアップのセキュリティを強化できます。</span><span class="sxs-lookup"><span data-stu-id="66464-124">Encryption is supported for backups done by [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], which provides additional security for off-site backups.</span></span>  
  
4.  <span data-ttu-id="66464-125">この機能では、AES 256 ビットまでの複数の暗号化アルゴリズムがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="66464-125">This feature supports multiple encryption algorithms up to AES 256 bit.</span></span> <span data-ttu-id="66464-126">このため、要件に合うアルゴリズムを選択できます。</span><span class="sxs-lookup"><span data-stu-id="66464-126">This gives you the option to select an algorithm that aligns with your requirements.</span></span>  
  
5.  <span data-ttu-id="66464-127">暗号化キーは拡張キー管理 (EKM) プロバイダーと統合できます。</span><span class="sxs-lookup"><span data-stu-id="66464-127">You can integrate encryption keys with Extended Key Management (EKM) providers.</span></span>  
  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="66464-128">前提条件</span><span class="sxs-lookup"><span data-stu-id="66464-128">Prerequisites</span></span>  
 <span data-ttu-id="66464-129">バックアップを暗号化するための前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="66464-129">The following are prerequisites for encrypting a backup:</span></span>  
  
1.  <span data-ttu-id="66464-130">**master データベースのデータベース マスター キーの作成:** データベース マスター キーは対称キーで、証明書の秘密キーやデータベース内にある非対称キーを保護するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="66464-130">**Create a Database Master Key for the master database:** The database master key is a symmetric key that is used to protect the private keys of certificates and asymmetric keys that are present in the database.</span></span> <span data-ttu-id="66464-131">詳細については、「[SQL Server とデータベースの暗号化キー &#40;データベース エンジン&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66464-131">For more information, see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md).</span></span>  
  
2.  <span data-ttu-id="66464-132">バックアップの暗号化に使用する証明書または非対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="66464-132">Create a certificate or asymmetric Key to use for backup encryption.</span></span> <span data-ttu-id="66464-133">証明書の作成の詳細については、「[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66464-133">For more information on creating a certificate, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span> <span data-ttu-id="66464-134">証明書の作成の詳細については、「[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66464-134">For more information on creating an asymmetric key, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="66464-135">サポートされるのは、拡張キー管理 (EKM) に存在する非対称キーのみです。</span><span class="sxs-lookup"><span data-stu-id="66464-135">Only asymmetric keys residing in an Extended Key Management (EKM) are supported.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="66464-136">制限</span><span class="sxs-lookup"><span data-stu-id="66464-136">Restrictions</span></span>  
 <span data-ttu-id="66464-137">暗号化オプションに適用される制限事項は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="66464-137">The following are restrictions that apply to the encryption options:</span></span>  
  
-   <span data-ttu-id="66464-138">バックアップ データの暗号化に非対称キーを使用する場合は、EKM プロバイダーに存在する非対称キーのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="66464-138">If you are using asymmetric key to encrypt the backup data, only asymmetric keys residing in the EKM provider are supported.</span></span>  
  
-   <span data-ttu-id="66464-139">SQL Server Express および SQL Server Web では、バックアップ時の暗号化がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="66464-139">SQL Server Express and SQL Server Web do not support encryption during backup.</span></span> <span data-ttu-id="66464-140">ただし、暗号化されたバックアップから SQL Server Express インスタンスまたは SQL Server Web インスタンスへの復旧は、サポートされます。</span><span class="sxs-lookup"><span data-stu-id="66464-140">However restoring from an encrypted backup to an instance of SQL Server Express or SQL Server Web is supported.</span></span>  
  
-   <span data-ttu-id="66464-141">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、暗号化されたバックアップを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="66464-141">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read encrypted backups.</span></span>  
  
-   <span data-ttu-id="66464-142">[既存のバックアップ セットに追加する] オプションは、暗号化されたバックアップに対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="66464-142">Appending to an existing backup set option is not supported for encrypted backups.</span></span>  
  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="66464-143">Permissions</span><span class="sxs-lookup"><span data-stu-id="66464-143">Permissions</span></span>  
 <span data-ttu-id="66464-144">**バックアップの暗号化または暗号化されたバックアップからの復元を行うには:**</span><span class="sxs-lookup"><span data-stu-id="66464-144">**To encrypt a backup or to restore from an encrypted backup:**</span></span>  
  
 <span data-ttu-id="66464-145">データベース バックアップの暗号化に使用する証明書または非対称キーに対する `VIEW DEFINITION` 権限。</span><span class="sxs-lookup"><span data-stu-id="66464-145">`VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database backup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66464-146">TDE で保護されたデータベースをバックアップまたは復元する場合、TDE 証明書へのアクセスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="66464-146">Access to the TDE certificate is not required to back up or restore a TDE protected database.</span></span>  
  
##  <a name="backup-encryption-methods"></a><a name="Methods"></a> <span data-ttu-id="66464-147">バックアップの暗号化方法</span><span class="sxs-lookup"><span data-stu-id="66464-147">Backup Encryption Methods</span></span>  
 <span data-ttu-id="66464-148">以下のセクションでは、バックアップ時にデータを暗号化する手順の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="66464-148">The sections below provide a brief introduction to the steps to encrypting the data during backup.</span></span> <span data-ttu-id="66464-149">Transact-SQL を使用して既存のバックアップを暗号化するためのさまざまな手順を示した完全なチュートリアルについては、「 [暗号化されたバックアップの作成](create-an-encrypted-backup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66464-149">For a complete walkthrough of the different steps of encrypting your backup using Transact-SQL, see [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
### <a name="using-sql-server-management-studio"></a><span data-ttu-id="66464-150">SQL Server Management Studio を使用する</span><span class="sxs-lookup"><span data-stu-id="66464-150">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="66464-151">次のいずれかのダイアログ ボックスを使用して、データベース バックアップの作成時にバックアップを暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="66464-151">You can encrypt a backup when creating the backup of a database in any of the following dialog boxes:</span></span>  
  
1.  <span data-ttu-id="66464-152">[データベースのバックアップ &#40;[バックアップ オプション] ページ&#41;](back-up-database-backup-options-page.md): **[バックアップ オプション]** ページで、 **[暗号化]** を選択し、暗号化に使用する暗号化アルゴリズムと証明書または非対称キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="66464-152">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) On the **Backup Options** page, you can select **Encryption**, and specify the encryption algorithm and the certificate or asymmetric key to use for the encryption.</span></span>  
  
2.  <span data-ttu-id="66464-153">[メンテナンス プラン ウィザードの使用](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) : **[データベースのバックアップ () タスクの定義]** ページの **[オプション]** タブでバックアップ タスクを選択する場合は、 **[バックアップの暗号化]** を選択し、暗号化に使用する暗号化アルゴリズムと証明書またはキーを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="66464-153">[Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) When you select a backup task, on the **Options** tab of the **Define Backup ()Task** page, you can select **Backup Encryption**, and specify the encryption algorithm and the certificate or key to use for the encryption.</span></span>  
  
### <a name="using-transact-sql"></a><span data-ttu-id="66464-154">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="66464-154">Using Transact SQL</span></span>  
 <span data-ttu-id="66464-155">バックアップ ファイルを暗号化するためのサンプル Transact-SQL ステートメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="66464-155">Following is a sample Transact-SQL statement to encrypt the backup file:</span></span>  
  
```sql
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO
```  
  
 <span data-ttu-id="66464-156">Transact-SQL ステートメントの完全な構文については、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66464-156">For the full Transact-SQL statement syntax, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="using-powershell"></a><span data-ttu-id="66464-157">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="66464-157">Using PowerShell</span></span>  
 <span data-ttu-id="66464-158">この例では、暗号化オプションを作成し、それを **Backup-SqlDatabase** コマンドレットのパラメーター値として使用して暗号化されたバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="66464-158">This example creates the encryption options and uses it as a parameter value in **Backup-SqlDatabase** cmdlet to create an encrypted backup.</span></span>  
  
```powershell
$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  
Backup-SqlDatabase -ServerInstance . -Database "MyTestDB" -BackupFile "MyTestDB.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="recommended-practices"></a><a name="RecommendedPractices"></a> <span data-ttu-id="66464-159">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="66464-159">Recommended Practices</span></span>  
 <span data-ttu-id="66464-160">インスタンスがインストールされているローカル コンピューター以外の場所に暗号化証明書とキーのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="66464-160">Create a backup of the encryption certificate and keys to a location other than your local machine where the instance is installed.</span></span> <span data-ttu-id="66464-161">ディザスター リカバリー シナリオに対応するには、証明書またはキーのバックアップをオフサイトに保管することを検討します。</span><span class="sxs-lookup"><span data-stu-id="66464-161">To account for disaster recovery scenarios, consider storing a backup of the certificate or key to an off-site location.</span></span> <span data-ttu-id="66464-162">バックアップの暗号化に使用された証明書がないと、暗号化されたバックアップを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="66464-162">You cannot restore an encrypted backup without the certificate used to encrypt the backup.</span></span>  
  
 <span data-ttu-id="66464-163">暗号化されたバックアップを復元するには、復元先のインスタンスで、バックアップの作成時に使用された元の証明書および対応する拇印を使用できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="66464-163">To restore an encrypted backup, the original certificate used when the backup was taken with the matching thumbprint should be available on the instance you are restoring to.</span></span> <span data-ttu-id="66464-164">このため証明書には、有効期限切れによる更新またはその他の変更を行わないでください。</span><span class="sxs-lookup"><span data-stu-id="66464-164">Therefore, the certificate should not be renewed on expiry or changed in any way.</span></span> <span data-ttu-id="66464-165">更新すると証明書が更新され拇印の変更が発生するため、バックアップ ファイルに対して証明書が無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="66464-165">Renewal can result in updating the certificate triggering the change of the thumbprint, therefore making the certificate invalid for the backup file.</span></span> <span data-ttu-id="66464-166">復元を実行するアカウントには、バックアップ時に暗号化に使用される証明書または非対称キーに対する VIEW DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="66464-166">The account performing the restore should have VIEW DEFINITION permissions on the certificate or the asymmetric key used to encrypt during backup.</span></span>  
  
 <span data-ttu-id="66464-167">可用性グループ データベースのバックアップは、通常は優先されるバックアップ レプリカで実施します。</span><span class="sxs-lookup"><span data-stu-id="66464-167">Availability Group database backups are typically performed on the preferred backup replica.</span></span>  <span data-ttu-id="66464-168">バックアップを実施したのとは異なるレプリカでバックアップを復元する場合は、バックアップに使用した元の証明書が、復元先のレプリカで利用できることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="66464-168">If restoring a backup on a replica other than where the backup was taken from, ensure that the original certificate used for backup is available on the replica you are restoring to.</span></span>  
  
 <span data-ttu-id="66464-169">データベースが TDE 対応の場合は、データベースの暗号化とバックアップに別々の証明書または非対象キーを選択することにより、セキュリティを強化します。</span><span class="sxs-lookup"><span data-stu-id="66464-169">If the database is TDE enabled, choose different certificates or asymmetric keys for encrypting the database and the backup to increase security.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="66464-170">関連タスク</span><span class="sxs-lookup"><span data-stu-id="66464-170">Related Tasks</span></span>  
  
|<span data-ttu-id="66464-171">トピック/タスク</span><span class="sxs-lookup"><span data-stu-id="66464-171">Topic/Task</span></span>|<span data-ttu-id="66464-172">説明</span><span class="sxs-lookup"><span data-stu-id="66464-172">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="66464-173">暗号化されたバックアップの作成</span><span class="sxs-lookup"><span data-stu-id="66464-173">Create an Encrypted Backup</span></span>](create-an-encrypted-backup.md)|<span data-ttu-id="66464-174">暗号化されたバックアップを作成するために必要な基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="66464-174">Describes the basic steps required to create an encrypted backup</span></span>|  
|[<span data-ttu-id="66464-175">Azure への SQL Server マネージド バックアップ - 保有期間とストレージの設定</span><span class="sxs-lookup"><span data-stu-id="66464-175">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|<span data-ttu-id="66464-176">指定された暗号化オプションで [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成するために必要な基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="66464-176">Describes the basic steps required to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with the encryption options specified.</span></span>|  
|[<span data-ttu-id="66464-177">Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66464-177">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|<span data-ttu-id="66464-178">Azure Key Vault のキーで保護される暗号化されたバックアップを作成する例を示します。</span><span class="sxs-lookup"><span data-stu-id="66464-178">Provides an example of creating an encrypted backup protected by keys in the Azure Key Vault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66464-179">参照</span><span class="sxs-lookup"><span data-stu-id="66464-179">See Also</span></span>  
 [<span data-ttu-id="66464-180">バックアップの概要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="66464-180">Backup Overview &#40;SQL Server&#41;</span></span>](backup-overview-sql-server.md)  
  
  
