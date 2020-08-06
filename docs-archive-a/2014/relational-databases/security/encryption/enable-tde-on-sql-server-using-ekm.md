---
title: EKM を使用して TDE を有効にする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], TDE using an EKM
- TDE, EKM how to
- EKM, TDE how to
- Transparent Data Encryption, using EKM
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: e659c5ff0245fdb17192b845eafc60badf5e295e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741710"
---
# <a name="enable-tde-using-ekm"></a><span data-ttu-id="74048-102">EKM を使用して TDE を有効にする</span><span class="sxs-lookup"><span data-stu-id="74048-102">Enable TDE Using EKM</span></span>
  <span data-ttu-id="74048-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]の拡張キー管理 (EKM) モジュールに格納されている非対称キーを使用してデータベース暗号化キーを保護する透過的なデータ暗号化 (TDE) を可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74048-103">This topic describes how to enable transparent data encryption (TDE) in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to protect a database encryption key by using an asymmetric key stored in an extensible key management (EKM) module with [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="74048-104">TDE は、データベース暗号化キーと呼ばれる対称キーを使用してデータベース全体のストレージを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="74048-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="74048-105">データベース暗号化キーは、master データベースのデータベース マスター キーによって保護される証明書を使用して保護することもできます。</span><span class="sxs-lookup"><span data-stu-id="74048-105">The database encryption key can also be protected using a certificate which is protected by the database master key of the master database.</span></span> <span data-ttu-id="74048-106">データベース マスター キーを使用してデータベース暗号化キーを保護する方法の詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](transparent-data-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74048-106">For more information about protecting the database encryption key by using the database master key, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span> <span data-ttu-id="74048-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が Azure 仮想マシンで実行されているときに TDE を構成する方法については、「[Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74048-107">For information about configuring TDE when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running on an Azure VM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
 <span data-ttu-id="74048-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="74048-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="74048-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="74048-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="74048-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="74048-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="74048-111">Security</span><span class="sxs-lookup"><span data-stu-id="74048-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="74048-112">Transact-SQL を使用して、EKM による TDE を可能にするには</span><span class="sxs-lookup"><span data-stu-id="74048-112">To enable TDE using EKM, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="74048-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="74048-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="74048-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="74048-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="74048-115">データベース暗号化キーの作成およびデータベースの暗号化は、高い特権を持つユーザー (システム管理者など) が行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="74048-115">You must be a high privileged user (such as a system administrator) to create a database encryption key and encrypt a database.</span></span> <span data-ttu-id="74048-116">このユーザーは、EKM モジュールが認証できるユーザーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="74048-116">That user must be able to be authenticated by the EKM module.</span></span>  
  
-   <span data-ttu-id="74048-117">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] は、起動時にデータベースを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="74048-117">Upon start up the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must open the database.</span></span> <span data-ttu-id="74048-118">これを行うには、EKM によって認証される資格情報を作成し、非対称キーに基づくログインにその資格情報を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74048-118">To do this, you should create a credential that will be authenticated by the EKM, and add it to a login that is based on an asymmetric key.</span></span> <span data-ttu-id="74048-119">ユーザーがこのログインを使用してログインすることはできませんが、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] は EKM デバイスで自身を認証することができます。</span><span class="sxs-lookup"><span data-stu-id="74048-119">Users cannot login using that login, but the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] will be able to authenticate itself with the EKM device.</span></span>  
  
-   <span data-ttu-id="74048-120">EKM モジュールに格納されている非対称キーが失われている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]はデータベースを開くことができません。</span><span class="sxs-lookup"><span data-stu-id="74048-120">If the asymmetric key stored in the EKM module is lost, the database will not be able to be opened by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74048-121">EKM プロバイダーを使用して非対称キーをバックアップできる場合は、バックアップを作成して安全な場所に保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="74048-121">If the EKM provider lets you back up the asymmetric key, you should create a back up and store it in a secure location.</span></span>  
  
-   <span data-ttu-id="74048-122">EKM プロバイダーによって要求されるオプションとパラメーターは、次のコード例に含まれるものとは異なっている場合があります。</span><span class="sxs-lookup"><span data-stu-id="74048-122">The options and parameters required by your EKM provider can differ from what is provided in the code example below.</span></span> <span data-ttu-id="74048-123">詳細については、EKM プロバイダーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="74048-123">For more information, see your EKM provider.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="74048-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="74048-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="74048-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="74048-125">Permissions</span></span>  
 <span data-ttu-id="74048-126">このトピックでは、次の権限を使用します。</span><span class="sxs-lookup"><span data-stu-id="74048-126">This topic uses the following permissions:</span></span>  
  
-   <span data-ttu-id="74048-127">構成オプションを変更して RECONFIGURE ステートメントを実行するには、ALTER SETTINGS サーバーレベル権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="74048-127">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="74048-128">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="74048-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
-   <span data-ttu-id="74048-129">ALTER ANY CREDENTIAL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="74048-129">Requires ALTER ANY CREDENTIAL permission.</span></span>  
  
-   <span data-ttu-id="74048-130">ALTER ANY LOGIN 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="74048-130">Requires ALTER ANY LOGIN permission.</span></span>  
  
-   <span data-ttu-id="74048-131">CREATE ASYMMETRIC KEY 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="74048-131">Requires CREATE ASYMMETRIC KEY permission.</span></span>  
  
-   <span data-ttu-id="74048-132">データベースを暗号化するには、データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="74048-132">Requires CONTROL permission on the database to encrypt the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="74048-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="74048-133">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-tde-using-ekm"></a><span data-ttu-id="74048-134">EKM を使用して TDE を有効にするには</span><span class="sxs-lookup"><span data-stu-id="74048-134">To enable TDE using EKM</span></span>  
  
1.  <span data-ttu-id="74048-135">EKM プロバイダーによって提供されるファイルを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンピューターの適切な場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="74048-135">Copy the files supplied by the EKM provider to an appropriate location on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="74048-136">この例では、 **C:\EKM** フォルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="74048-136">In this example, we use the **C:\EKM** folder.</span></span>  
  
2.  <span data-ttu-id="74048-137">EKM プロバイダーの要件に従ってコンピューターに証明書をインストールします。</span><span class="sxs-lookup"><span data-stu-id="74048-137">Install certificates to the computer as required by your EKM provider.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="74048-138">には、EKM プロバイダーは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="74048-138">does not supply an EKM provider.</span></span> <span data-ttu-id="74048-139">EKM プロバイダーごとに、インストール、構成、およびユーザー承認の手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="74048-139">Each EKM provider can have different procedures for installing, configuring and authorizing users.</span></span>  <span data-ttu-id="74048-140">この手順を完了するには、EKM プロバイダーのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="74048-140">Consult your EKM provider documentation to complete this step.</span></span>  
  
3.  <span data-ttu-id="74048-141">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="74048-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
4.  <span data-ttu-id="74048-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74048-142">On the Standard bar, click **New Query**.</span></span>  
  
5.  <span data-ttu-id="74048-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74048-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 <span data-ttu-id="74048-144">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="74048-144">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="74048-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [<span data-ttu-id="74048-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [<span data-ttu-id="74048-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="74048-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [<span data-ttu-id="74048-149">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-149">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [<span data-ttu-id="74048-150">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-150">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="74048-151">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-151">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
-   [<span data-ttu-id="74048-152">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-152">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [<span data-ttu-id="74048-153">Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74048-153">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
-   [<span data-ttu-id="74048-154">Azure SQL Database での Transparent Data Encryption</span><span class="sxs-lookup"><span data-stu-id="74048-154">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)  
  
  
