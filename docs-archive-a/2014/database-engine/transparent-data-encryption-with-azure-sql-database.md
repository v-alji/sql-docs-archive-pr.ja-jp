---
title: Azure SQL Database での Transparent Data Encryption | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6af7c52741b85a2733b93c2b1ed8c03a14dd6343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641203"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a><span data-ttu-id="1c3d3-102">Azure SQL Database での Transparent Data Encryption</span><span class="sxs-lookup"><span data-stu-id="1c3d3-102">Transparent Data Encryption with Azure SQL Database</span></span>
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="1c3d3-103">の透過的なデータの暗号化 (プレビュー版) は、データベース、関連するバックアップ、および静止したトランザクション ログのリアルタイム暗号化および暗号化解除を実行して、悪意のあるアクティビティの脅威から保護するのに役立ちます。アプリケーションに変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-103">transparent data encryption (preview) helps protect against the threat of malicious activity by performing real-time encryption and decryption of the database, associated backups, and transaction log files at rest without requiring changes to the application.</span></span>

 <span data-ttu-id="1c3d3-104">TDE は、データベース暗号化キーと呼ばれる対称キーを使用してデータベース全体のストレージを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="1c3d3-105">[!INCLUDE[ssSDS](../includes/sssds-md.md)] では、データベース暗号化キーは、組み込みのサーバー証明書によって保護されます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-105">In [!INCLUDE[ssSDS](../includes/sssds-md.md)] the database encryption key is protected by a built-in server certificate.</span></span> <span data-ttu-id="1c3d3-106">組み込みのサーバー証明書は、各 [!INCLUDE[ssSDS](../includes/sssds-md.md)] サーバーに対して一意です。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-106">The built-in server certificate is unique for each [!INCLUDE[ssSDS](../includes/sssds-md.md)] server.</span></span> <span data-ttu-id="1c3d3-107">データベースが GeoDR リレーションシップの状態にある場合、データベースは各サーバーで異なるキーによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-107">If a database is in a GeoDR relationship, it is protected by a different key on each server.</span></span> <span data-ttu-id="1c3d3-108">2 つのデータベースが同じサーバーに接続している場合は、同じ組み込みの証明書を共有します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-108">If 2 databases are connected to the same server, they share the same built-in certificate.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="1c3d3-109">は、少なくとも 90 日ごとにこれらの証明書を自動的に回転します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-109">automatically rotates these certificates at least every 90 days.</span></span> <span data-ttu-id="1c3d3-110">TDE の一般的な説明については、「 [透過的なデータ暗号化 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-110">For a general description of TDE, see [Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).</span></span>

 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="1c3d3-111">は、Azure Key Vault と TDE との統合をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-111">does not support Azure Key Vault integration with TDE.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1c3d3-112">は、Key Vault の非対称キーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-112">running on an Azure virtual machine can use an asymmetric key from the Key Vault.</span></span> <span data-ttu-id="1c3d3-113">詳細については、「 [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-113">For more information, see [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).</span></span>

||
|-|
|<span data-ttu-id="1c3d3-114">**適用対象**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([一部の地域ではプレビュー](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)版)。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-114">**Applies to**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="1c3d3-115">現在、これはプレビュー機能です。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-115">This is currently a preview feature.</span></span> <span data-ttu-id="1c3d3-116">[!INCLUDE[ssSDS](../includes/sssds-md.md)] の透過的なデータ暗号化をデータベースに実装すると、使用許諾契約書 (マイクロソフト エンタープライズ契約、Microsoft Azure 契約、マイクロソフト オンライン サブスクリプション契約など) に規定されたプレビューに関する条件、ならびに適用されるあらゆる [Microsoft Azure プレビューの追加使用条件](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)の対象となることを認め、それに同意したことになります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-116">I acknowledge and agree that implementation of [!INCLUDE[ssSDS](../includes/sssds-md.md)] transparent data encryption in my database(s) is subject to the preview terms in my license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

 <span data-ttu-id="1c3d3-117">TDE のプレビューの状態は、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] のバージョン ファミリ V12 が現在一般提供の段階にあると発表されている地理的リージョンのサブセットにおいても適用されます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-117">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="1c3d3-118">TDE がプレビューから GA に昇格されたことを [!INCLUDE[ssSDS](../includes/sssds-md.md)] が発表するまで、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 用の TDE の実稼働データベースでの使用は想定されていません。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-118">TDE for [!INCLUDE[ssSDS](../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="1c3d3-119">[!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 の詳細については、「 [Azure SQL Database の新機能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-119">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1c3d3-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="1c3d3-120">Permissions</span></span>
 <span data-ttu-id="1c3d3-121">プレビュー版にサインアップして Azure ポータル経由で、REST API または PowerShell を使用して TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-121">To sign up for the preview and to configure TDE through the Azure portal, by using the REST API, or by using PowerShell, you must be connected as the Azure Owner, Contributor, or SQL Security Manager.</span></span>

 <span data-ttu-id="1c3d3-122">[!INCLUDE[tsql](../includes/tsql-md.md)] を使用して TDE を構成するには、以下が必要です。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-122">To configure TDE by using [!INCLUDE[tsql](../includes/tsql-md.md)] requires the following:</span></span>

-   <span data-ttu-id="1c3d3-123">TDE のプレビュー版に既にサインアップしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-123">You must be already signed up for the TDE preview.</span></span>

-   <span data-ttu-id="1c3d3-124">データベースの暗号化キーを作成するには、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 管理者であるか、またはマスター データベースの **dbmanager** ロールのメンバーでありかつデータベースに対する **CONTROL** 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-124">To create the database encryption key you must be a [!INCLUDE[ssSDS](../includes/sssds-md.md)] administrator or you must be a member of the **dbmanager** role in the master database and have the **CONTROL** permission on the database.</span></span>

-   <span data-ttu-id="1c3d3-125">ALTER DATABASE ステートメントを SET オプション付きで実行するには、 **dbmanager** ロールのメンバーシップだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-125">To execute the ALTER DATABASE statement with the SET option only requires membership in the **dbmanager** role.</span></span>

##  <a name="sign-up-for-the-preview-of-tde-and-enable-tde-on-a-database"></a><a name="Preview"></a><span data-ttu-id="1c3d3-126">TDE のプレビューにサインアップして、データベースで TDE を有効にする</span><span class="sxs-lookup"><span data-stu-id="1c3d3-126">Sign Up for the Preview of TDE and Enable TDE on a Database</span></span>

1.  <span data-ttu-id="1c3d3-127">Azure Portal にアクセス [https://portal.azure.com](https://portal.azure.com) し、Azure 管理者または共同作成者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-127">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="1c3d3-128">左のバナーの [**参照**] をクリックしてから、[**SQL データベース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-128">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="1c3d3-129">左側のウィンドウの [**SQL データベース**] を選択して、ユーザー データベースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-129">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="1c3d3-130">データベース ブレードで、 **[すべての設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-130">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="1c3d3-131">**[設定]** ブレードで、 **[透過的なデータ暗号化 (プレビュー)]** 部分をクリックして **[透過的なデータ暗号化 (プレビュー版)]** ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-131">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span> <span data-ttu-id="1c3d3-132">TDE のプレビュー版にまだサインアップしていない場合は、サインアップが完了するまでデータ暗号化設定は無効になります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-132">If you have not already signed up for the TDE preview, the data encryption settings will be disabled until you complete signup.</span></span>

6.  <span data-ttu-id="1c3d3-133">**[プレビュー版の使用条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-133">Click **PREVIEW TERMS**.</span></span>

7.  <span data-ttu-id="1c3d3-134">プレビューの使用条件を読み、条項に同意する場合は [ **Transparent Data encryptionPreview**の使用条件] チェックボックスをオンにして、ページの下部の近くにある [ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-134">Read the terms of the preview, and if you agree to the terms, select the **Transparent Data encryptionPreview terms** check box, and then click **OK** near the bottom of the page.</span></span> <span data-ttu-id="1c3d3-135">**Data encryptionPREVIEW**ブレードに戻ります。ここで、[**データの暗号化**] ボタンを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-135">Returning to the **Data encryptionPREVIEW** blade, where the **Data encryption** button should now be enabled.</span></span>

8.  <span data-ttu-id="1c3d3-136">**[データの暗号化 (プレビュー版)]** ブレードで **[データの暗号化]** ボタンを **[オン]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-136">In the **Data encryption PREVIEW** blade, move the **Data encryption** button to **On**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="1c3d3-137">**暗号化の状態**は、透過的なデータ暗号化の進行状況を概算します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-137">The **Encryption status** will approximate the progress of the transparent data encryption.</span></span>

     <span data-ttu-id="1c3d3-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span><span class="sxs-lookup"><span data-stu-id="1c3d3-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span></span>

     <span data-ttu-id="1c3d3-139">また、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化の進行状況を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-139">You can also monitor the progress of encryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="1c3d3-140">Dm_database_encryption_keys ビューの列に対してクエリを実行 `encryption_state` します。 [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="1c3d3-140">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="enabling-tde-on-sssds-by-using-transact-sql"></a><a name="Encrypt"></a><span data-ttu-id="1c3d3-141">Transact-sql を使用してで TDE を有効にする [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3d3-141">Enabling TDE on [!INCLUDE[ssSDS](../includes/sssds-md.md)] by Using Transact-SQL</span></span>
 <span data-ttu-id="1c3d3-142">次の手順は、既にプレビュー版にサインアップしていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-142">The following steps, assume you have already signed up for the preview.</span></span>

###  <a name="TsqlProcedure"></a>

1.  <span data-ttu-id="1c3d3-143">管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-143">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="1c3d3-144">データベース暗号化キーを作成してデータベースを暗号化するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-144">Execute the following statements to create a database encryption key and encrypt the database.</span></span>

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  <span data-ttu-id="1c3d3-145">での暗号化の進行状況を監視するために [!INCLUDE[ssSDS](../includes/sssds-md.md)] 、 **VIEW database STATE**権限を持つデータベースユーザーは、 `encryption_state` [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)ビューの列に対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-145">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a><span data-ttu-id="1c3d3-146">PowerShell を使用して SQL Database で TDE を有効にする</span><span class="sxs-lookup"><span data-stu-id="1c3d3-146">Enabling TDE on SQL Database by Using PowerShell</span></span>
 <span data-ttu-id="1c3d3-147">Azure PowerShell を使用すると、次のコマンドを実行して TDE を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-147">Using the Azure PowerShell you can run the following command to turn TDE on/off.</span></span> <span data-ttu-id="1c3d3-148">コマンドを実行するには、事前にアカウントを PS ウィンドウに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-148">You do have to connect your account to the PS window before running the command.</span></span> <span data-ttu-id="1c3d3-149">次の手順は、既にプレビュー版にサインアップしていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-149">The following steps, assume you have already signed up for the preview.</span></span> <span data-ttu-id="1c3d3-150">PowerShell の詳細については、「 [Azure PowerShell をインストールおよび構成する方法](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-150">For additional information about PowerShell, see [How to install and configure Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).</span></span>

1.  <span data-ttu-id="1c3d3-151">TDE を有効にするには、TDE の状態表示に戻り、暗号化のアクティビティを表示します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-151">To enable TDE, return the TDE status, and view the encryption activity.</span></span>

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  <span data-ttu-id="1c3d3-152">TDE を無効にするには、</span><span class="sxs-lookup"><span data-stu-id="1c3d3-152">To disable TDE:</span></span>

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="decrypting-a-tde-protected-database-on-sssds"></a><a name="Decrypt"></a><span data-ttu-id="1c3d3-153">で TDE で保護されたデータベースの暗号化を解除する[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3d3-153">Decrypting a TDE Protected Database on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>

#### <a name="to-disable-tde-by-using-the-azure-portal"></a><span data-ttu-id="1c3d3-154">Azure ポータルを使用して TDE を無効にするには</span><span class="sxs-lookup"><span data-stu-id="1c3d3-154">To Disable TDE by Using the Azure Portal</span></span>

1.  <span data-ttu-id="1c3d3-155">Azure Portal にアクセス [https://portal.azure.com](https://portal.azure.com) し、Azure 管理者または共同作成者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-155">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="1c3d3-156">左のバナーの [**参照**] をクリックしてから、[**SQL データベース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-156">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="1c3d3-157">左側のウィンドウの [**SQL データベース**] を選択して、ユーザー データベースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-157">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="1c3d3-158">データベース ブレードで、 **[すべての設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-158">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="1c3d3-159">**[設定]** ブレードで、 **[透過的なデータ暗号化 (プレビュー)]** 部分をクリックして **[透過的なデータ暗号化 (プレビュー版)]** ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-159">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span>

6.  <span data-ttu-id="1c3d3-160">**[透過的なデータの暗号化 (プレビュー版)]** ブレードで、 **[データの暗号化]** ボタンを **[オフ]** にしてから、(ページ上部の) **[保存]** をクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-160">In the **Transparent data encryption PREVIEW** blade, move the **Data encryption** button to **Off**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="1c3d3-161">**[暗号化の状態]** には、透過的なデータの暗号化解除のおおよその進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-161">The **Encryption status** will approximate the progress of the transparent data decryption.</span></span>

     <span data-ttu-id="1c3d3-162">また、 [!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 権限を持つデータベース ユーザーとして、 **などのクエリ ツールを使用して** に接続することで、暗号化解除の進行状況を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-162">You can also monitor the progress of decryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="1c3d3-163">Dm_database_encryption_keys ビューの列に対してクエリを実行 `encryption_state` します。 [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="1c3d3-163">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)view.</span></span>

#### <a name="to-disable-tde-by-using-transact-sql"></a><span data-ttu-id="1c3d3-164">Transact SQL を使用して TDE を無効にするには</span><span class="sxs-lookup"><span data-stu-id="1c3d3-164">To Disable TDE by Using Transact-SQL</span></span>

1.  <span data-ttu-id="1c3d3-165">管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-165">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="1c3d3-166">データベースの暗号化を解除するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-166">Execute the following statements to decrypt the database.</span></span>

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  <span data-ttu-id="1c3d3-167">での暗号化の進行状況を監視するために [!INCLUDE[ssSDS](../includes/sssds-md.md)] 、 **VIEW database STATE**権限を持つデータベースユーザーは、 `encryption_state` [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)ビューの列に対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-167">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="working-with-tde-protected-databases-on-sssds"></a><a name="Working"></a><span data-ttu-id="1c3d3-168">で TDE で保護されたデータベースを操作する[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3d3-168">Working with TDE Protected Databases on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>
 <span data-ttu-id="1c3d3-169">Azure 内での操作用にデータベースの暗号化を解除する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-169">You do not need to decrypt databases for operations within Azure.</span></span> <span data-ttu-id="1c3d3-170">ソース データベースまたはプライマリ データベースの TDE の設定は、ターゲットに透過的に継承されます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-170">The TDE settings on the source database or primary database are transparently inherited on the target.</span></span> <span data-ttu-id="1c3d3-171">これには次の操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-171">This includes operations involving:</span></span>

-   <span data-ttu-id="1c3d3-172">geo リストア</span><span class="sxs-lookup"><span data-stu-id="1c3d3-172">Geo-Restore</span></span>

-   <span data-ttu-id="1c3d3-173">セルフ サービスによる特定の時点での復元</span><span class="sxs-lookup"><span data-stu-id="1c3d3-173">Self-Service Point in Time Restore</span></span>

-   <span data-ttu-id="1c3d3-174">削除されたデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="1c3d3-174">Restore a Deleted Database</span></span>

-   <span data-ttu-id="1c3d3-175">アクティブな Geo_Replication</span><span class="sxs-lookup"><span data-stu-id="1c3d3-175">Active Geo_Replication</span></span>

-   <span data-ttu-id="1c3d3-176">データベースのコピーの作成</span><span class="sxs-lookup"><span data-stu-id="1c3d3-176">Creating a Database Copy</span></span>

##  <a name="moving-a-tde-protected-database-on-using-bacpac-files"></a><a name="Moving"></a><span data-ttu-id="1c3d3-177">を使用して、TDE で保護されたデータベースを移動します。Bacpac ファイル</span><span class="sxs-lookup"><span data-stu-id="1c3d3-177">Moving a TDE Protected Database on using .Bacpac Files</span></span>
 <span data-ttu-id="1c3d3-178">[!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] ポータルまたは [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインポートおよびエクスポート] ウィザードでデータベースのエクスポート機能を使用して TDE で保護されたデータベースをエクスポートする場合、データベースのコンテンツは暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-178">When exporting a TDE protected database using the Export Database function in the [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] Portal or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard, the content of the database is not encrypted.</span></span> <span data-ttu-id="1c3d3-179">コンテンツは、暗号化されていない .bacpac ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-179">The content is stored in .bacpac files which are not encrypted.</span></span>  <span data-ttu-id="1c3d3-180">.bacpac ファイルは必ず適切に保護し、新しいデータベースのインポートが完了したら TDE を有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="1c3d3-180">Be sure to protect the .bacpac files appropriately and enable TDE once import of the new database is completed.</span></span>

## <a name="related-sql-server-topic"></a><span data-ttu-id="1c3d3-181">関連する SQL Server のトピック</span><span class="sxs-lookup"><span data-stu-id="1c3d3-181">Related SQL Server Topic</span></span>
 [<span data-ttu-id="1c3d3-182">EKM を使用して TDE を有効にする</span><span class="sxs-lookup"><span data-stu-id="1c3d3-182">Enable TDE Using EKM</span></span>](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a><span data-ttu-id="1c3d3-183">参照</span><span class="sxs-lookup"><span data-stu-id="1c3d3-183">See Also</span></span>
 <span data-ttu-id="1c3d3-184">[Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [Create CREDENTIAL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [create 非対称 KEY &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) create [DATABASE Encryption KEY](/sql/t-sql/statements/create-database-encryption-key-transact-sql) &#40;transact-sql&#41;[alter database &#40;](/sql/t-sql/statements/alter-database-transact-sql) transact-sql&#41;alter database [SET Options](/sql/t-sql/statements/alter-database-transact-sql-set-options) (transact-sql &#40;) を作成&#41;</span><span class="sxs-lookup"><span data-stu-id="1c3d3-184">[Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql) [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)</span></span>
