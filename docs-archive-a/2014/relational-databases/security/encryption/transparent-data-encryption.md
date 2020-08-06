---
title: 透過的なデータ暗号化 (TDE) | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: a8118f0781d7c9e3d839c029c6bdaf8b01e074b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641572"
---
# <a name="transparent-data-encryption-tde"></a><span data-ttu-id="29849-102">Transparent Data Encryption (TDE)</span><span class="sxs-lookup"><span data-stu-id="29849-102">Transparent Data Encryption (TDE)</span></span>
  <span data-ttu-id="29849-103">*Transparent Data Encryption* (TDE) は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] のデータ ファイルを暗号化します。これは保存データの暗号化と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="29849-103">*Transparent Data Encryption* (TDE) encrypts [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] data files, known as encrypting data at rest.</span></span> <span data-ttu-id="29849-104">セキュリティで保護されたシステムの設計、機密資産の暗号化、データベース サーバーに対するファイアウォールの構築などの、データベースを保護するいくつかの対策を講じることができます。</span><span class="sxs-lookup"><span data-stu-id="29849-104">You can take several precautions to help secure the database such as designing a secure system, encrypting confidential assets, and building a firewall around the database servers.</span></span> <span data-ttu-id="29849-105">ただし、物理メディア (ドライブやバックアップ テープなど) が盗まれるシナリオでは、悪意のある第三者がデータベースを復元するかアタッチするだけでデータを閲覧することができます。</span><span class="sxs-lookup"><span data-stu-id="29849-105">However, in a scenario where the physical media (such as drives or backup tapes) are stolen, a malicious party can just restore or attach the database and browse the data.</span></span> <span data-ttu-id="29849-106">解決策の 1 つは、データベース内の機密データを暗号化し、データの暗号化に使用されるキーを証明書で保護することです。</span><span class="sxs-lookup"><span data-stu-id="29849-106">One solution is to encrypt the sensitive data in the database and protect the keys that are used to encrypt the data with a certificate.</span></span> <span data-ttu-id="29849-107">これにより、キーを持たない人物によるデータの使用を防止できますが、このような保護は事前に計画する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-107">This prevents anyone without the keys from using the data, but this kind of protection must be planned in advance.</span></span>

 <span data-ttu-id="29849-108">TDE は、データとログ ファイルの I/O 暗号化と複合化をリアルタイムで実行します。</span><span class="sxs-lookup"><span data-stu-id="29849-108">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="29849-109">暗号化は、復旧中に、可用性のためのデータベース ブート レコードに格納されるデータベース暗号化キー (DEK) を使用します。</span><span class="sxs-lookup"><span data-stu-id="29849-109">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="29849-110">DEK は、サーバーの master データベースに保存されている証明書を使用して保護される対称キーか、EKM モジュールによって保護される非対称キーです。</span><span class="sxs-lookup"><span data-stu-id="29849-110">The DEK is a symmetric key secured by using a certificate stored in the master database of the server or an asymmetric key protected by an EKM module.</span></span> <span data-ttu-id="29849-111">TDE では、"静止した" データ、つまりデータとログ ファイルが保護されます。</span><span class="sxs-lookup"><span data-stu-id="29849-111">TDE protects data "at rest", meaning the data and log files.</span></span> <span data-ttu-id="29849-112">この暗号化は、法律、規制、およびさまざまな業界で確立されているガイドラインの多くに準拠できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="29849-112">It provides the ability to comply with many laws, regulations, and guidelines established in various industries.</span></span> <span data-ttu-id="29849-113">これによりソフトウェア開発者は、既存のアプリケーションを変更することなく、AES および 3DES 暗号化アルゴリズムを使用してデータを暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="29849-113">This enables software developers to encrypt data by using AES and 3DES encryption algorithms without changing existing applications.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="29849-114">TDE では、通信チャネル全体を暗号化することはできません。</span><span class="sxs-lookup"><span data-stu-id="29849-114">TDE does not provide encryption across communication channels.</span></span> <span data-ttu-id="29849-115">通信チャネル全体でデータを暗号化する方法の詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-115">For more information about how to encrypt data across communication channels, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>
> 
>  <span data-ttu-id="29849-116">**関連項目:**</span><span class="sxs-lookup"><span data-stu-id="29849-116">**Related topics:**</span></span>
> 
>  -   [<span data-ttu-id="29849-117">Azure SQL Database での Transparent Data Encryption</span><span class="sxs-lookup"><span data-stu-id="29849-117">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)
> -   [<span data-ttu-id="29849-118">別の SQL Server への TDE で保護されたデータベースの移動</span><span class="sxs-lookup"><span data-stu-id="29849-118">Move a TDE Protected Database to Another SQL Server</span></span>](move-a-tde-protected-database-to-another-sql-server.md)
> -   [<span data-ttu-id="29849-119">EKM を使用して TDE を有効にする</span><span class="sxs-lookup"><span data-stu-id="29849-119">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)

## <a name="about-tde"></a><span data-ttu-id="29849-120">TDE について</span><span class="sxs-lookup"><span data-stu-id="29849-120">About TDE</span></span>
 <span data-ttu-id="29849-121">データベース ファイルの暗号化は、ページ レベルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="29849-121">Encryption of the database file is performed at the page level.</span></span> <span data-ttu-id="29849-122">暗号化されたデータベースのページは、ディスクに書き込まれる前に暗号化され、メモリに読み込まれるときに暗号化解除されます。</span><span class="sxs-lookup"><span data-stu-id="29849-122">The pages in an encrypted database are encrypted before they are written to disk and decrypted when read into memory.</span></span> <span data-ttu-id="29849-123">TDE では、暗号化されたデータベースのサイズが増えることはありません。</span><span class="sxs-lookup"><span data-stu-id="29849-123">TDE does not increase the size of the encrypted database.</span></span>

 <span data-ttu-id="29849-124">**に適用される情報[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="29849-124">**Information applicable to [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span></span>

 <span data-ttu-id="29849-125">TDE を [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12 ([一部のリージョンではプレビュー版](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) と一緒に使用すると、マスター データベースに格納されるサーバー レベルの証明書が [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]によって自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="29849-125">When using TDE with [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12  ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) the server-level certificate stored in the master database is automatically created for you by [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="29849-126">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] で TDE データベースを移動するには、データベースの暗号化を解除してデータベースを移動し、移動先の [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]で TDE を再度有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-126">To move a TDE database on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] you must decrypt the database, move the database, and then re-enable TDE on the destination [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="29849-127">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]での TDE に関する詳細な手順については、「 [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-127">For step-by-step instructions for TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], see [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md).</span></span>

 <span data-ttu-id="29849-128">TDE のプレビューの状態は、 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] のバージョン ファミリ V12 が現在一般提供の段階にあると発表されている地理的リージョンのサブセットにおいても適用されます。</span><span class="sxs-lookup"><span data-stu-id="29849-128">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="29849-129">TDE がプレビューから GA に昇格されたことを [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] が発表するまで、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 用の TDE の実稼働データベースでの使用は想定されていません。</span><span class="sxs-lookup"><span data-stu-id="29849-129">TDE for [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../../../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="29849-130">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12 の詳細については、「 [Azure SQL Database の新機能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="29849-130">For more information about [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

 <span data-ttu-id="29849-131">**に適用される情報[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="29849-131">**Information applicable to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span></span>

 <span data-ttu-id="29849-132">セキュリティで保護されたデータベースは、正しい証明書を使用することで復元できます。</span><span class="sxs-lookup"><span data-stu-id="29849-132">After it is secured, the database can be restored by using the correct certificate.</span></span> <span data-ttu-id="29849-133">証明書の詳細については、「 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="29849-133">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

 <span data-ttu-id="29849-134">TDE を有効にしたら、証明書とそれに関連付けられた秘密キーを直ちにバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-134">When enabling TDE, you should immediately back up the certificate and the private key associated with the certificate.</span></span> <span data-ttu-id="29849-135">証明書が使用できなくなった場合、またはデータベースを別のサーバーに復元またはアタッチする必要がある場合に、証明書と秘密キーの両方のバックアップが必要です。これらのバックアップがない場合は、データベースを開けません。</span><span class="sxs-lookup"><span data-stu-id="29849-135">If the certificate ever becomes unavailable or if you must restore or attach the database on another server, you must have backups of both the certificate and the private key or you will not be able to open the database.</span></span> <span data-ttu-id="29849-136">暗号化証明書は、データベースで TDE を無効にした場合でも保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-136">The encrypting certificate should be retained even if TDE is no longer enabled on the database.</span></span> <span data-ttu-id="29849-137">データベースが暗号化されていない場合でも、トランザクション ログの一部はまだ保護されたままである場合があるため、データベースの完全バックアップが実行されるまでは、一部の操作では証明書が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="29849-137">Even though the database is not encrypted, parts of the transaction log may still remain protected, and the certificate may be needed for some operations until the full backup of the database is performed.</span></span> <span data-ttu-id="29849-138">有効期限の日付を過ぎた証明書であっても、TDE によりデータを暗号化および暗号化解除できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="29849-138">A certificate that has exceeded its expiration date can still be used to encrypt and decrypt data with TDE.</span></span>

 <span data-ttu-id="29849-139">**暗号化階層**</span><span class="sxs-lookup"><span data-stu-id="29849-139">**Encryption Hierarchy**</span></span>

 <span data-ttu-id="29849-140">TDE 暗号化のアーキテクチャを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="29849-140">The following illustration shows the architecture of TDE encryption.</span></span> <span data-ttu-id="29849-141">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]で TDE を使用する場合に、ユーザーによって構成可能なのは、データベース レベルの項目 (データベース暗号化キーと ALTER DATABASE の部分) のみです。</span><span class="sxs-lookup"><span data-stu-id="29849-141">Only the database level items (the database encryption key and ALTER DATABASE portions are user-configurable when using TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="29849-142">![トピックで説明された階層を表示します。](../../../database-engine/media/tde-architecture.gif "トピックで説明された階層を表示します。")</span><span class="sxs-lookup"><span data-stu-id="29849-142">![Displays the hierarchy described in the topic.](../../../database-engine/media/tde-architecture.gif "Displays the hierarchy described in the topic.")</span></span>

## <a name="using-transparent-data-encryption"></a><span data-ttu-id="29849-143">Transparent Data Encryption の使用</span><span class="sxs-lookup"><span data-stu-id="29849-143">Using Transparent Data Encryption</span></span>
 <span data-ttu-id="29849-144">TDE を使用するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="29849-144">To use TDE, follow these steps.</span></span>

||
|-|
|<span data-ttu-id="29849-145">**適用対象**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29849-145">**Applies to**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|

-   <span data-ttu-id="29849-146">マスター キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="29849-146">Create a master key</span></span>

-   <span data-ttu-id="29849-147">マスター キーで保護された証明書を作成または取得します。</span><span class="sxs-lookup"><span data-stu-id="29849-147">Create or obtain a certificate protected by the master key</span></span>

-   <span data-ttu-id="29849-148">データベース暗号化キーを作成し、証明書で保護します。</span><span class="sxs-lookup"><span data-stu-id="29849-148">Create a database encryption key and protect it by the certificate</span></span>

-   <span data-ttu-id="29849-149">暗号化を使用するようにデータベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="29849-149">Set the database to use encryption</span></span>

 <span data-ttu-id="29849-150">次の例では、 `AdventureWorks2012` という名前のサーバーにインストールされた証明書を使用して、 `MyServerCert`データベースを暗号化および暗号化解除しています。</span><span class="sxs-lookup"><span data-stu-id="29849-150">The following example illustrates encrypting and decrypting the `AdventureWorks2012` database using a certificate installed on the server named `MyServerCert`.</span></span>

```
USE master;
GO
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';
go
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';
go
USE AdventureWorks2012;
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_128
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;
GO
ALTER DATABASE AdventureWorks2012
SET ENCRYPTION ON;
GO
```

 <span data-ttu-id="29849-151">暗号化および暗号化解除の操作は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によってバックグラウンド スレッドでスケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="29849-151">The encryption and decryption operations are scheduled on background threads by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29849-152">これらの操作の状態は、この後の一覧に示すカタログ ビューおよび動的管理ビューを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="29849-152">You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.</span></span>

> [!CAUTION]
>  <span data-ttu-id="29849-153">TDE が有効になっているデータベースのバックアップ ファイルも、データベース暗号化キーを使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-153">Backup files of databases that have TDE enabled are also encrypted by using the database encryption key.</span></span> <span data-ttu-id="29849-154">このため、このバックアップを復元するときには、データベース暗号化キーを保護している証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="29849-154">As a result, when you restore these backups, the certificate protecting the database encryption key must be available.</span></span> <span data-ttu-id="29849-155">つまり、データの損失を防ぐには、データベースをバックアップするだけでなく、サーバー証明書のバックアップも確実に保守する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-155">This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss.</span></span> <span data-ttu-id="29849-156">証明書が使用できなくなると、データの損失が発生します。</span><span class="sxs-lookup"><span data-stu-id="29849-156">Data loss will result if the certificate is no longer available.</span></span> <span data-ttu-id="29849-157">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="29849-157">For more information, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

## <a name="commands-and-functions"></a><span data-ttu-id="29849-158">コマンドと関数</span><span class="sxs-lookup"><span data-stu-id="29849-158">Commands and Functions</span></span>
 <span data-ttu-id="29849-159">TDE の証明書を次に示すステートメントで処理できるようにするには、この証明書をデータベース マスター キーで暗号化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-159">The TDE certificates must be encrypted by the database master key to be accepted by the following statements.</span></span> <span data-ttu-id="29849-160">パスワードだけで暗号化された証明書は、ステートメントで暗号化機能として受け付けられません。</span><span class="sxs-lookup"><span data-stu-id="29849-160">If they are encrypted by password only, the statements will reject them as encryptors.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="29849-161">TDE で使用された証明書をパスワードで保護するように変更すると、再起動後にデータベースにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="29849-161">Altering the certificates to be password-protected after they are used by TDE will cause the database to become inaccessible after a restart.</span></span>

 <span data-ttu-id="29849-162">次の表に、TDE のコマンドと関数の説明とリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="29849-162">The following table provides links and explanations of TDE commands and functions.</span></span>

|<span data-ttu-id="29849-163">コマンドまたは関数</span><span class="sxs-lookup"><span data-stu-id="29849-163">Command or function</span></span>|<span data-ttu-id="29849-164">目的</span><span class="sxs-lookup"><span data-stu-id="29849-164">Purpose</span></span>|
|-------------------------|-------------|
|[<span data-ttu-id="29849-165">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-165">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)|<span data-ttu-id="29849-166">データベースの暗号化に使用されるキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="29849-166">Creates a key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="29849-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-encryption-key-transact-sql)|<span data-ttu-id="29849-168">データベースの暗号化に使用されるキーを変更します。</span><span class="sxs-lookup"><span data-stu-id="29849-168">Changes the key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="29849-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-transact-sql)|<span data-ttu-id="29849-170">データベースの暗号化に使用されたキーを削除します。</span><span class="sxs-lookup"><span data-stu-id="29849-170">Removes the key that was used to encrypt a database.</span></span>|
|[<span data-ttu-id="29849-171">ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-171">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)|<span data-ttu-id="29849-172">TDE を有効にするために使用される `ALTER DATABASE` オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="29849-172">Explains the `ALTER DATABASE` option that is used to enable TDE.</span></span>|

## <a name="catalog-views-and-dynamic-management-views"></a><span data-ttu-id="29849-173">カタログ ビューと動的管理ビュー</span><span class="sxs-lookup"><span data-stu-id="29849-173">Catalog Views and Dynamic Management Views</span></span>
 <span data-ttu-id="29849-174">次の表に、TDE のカタログ ビューと動的管理ビューを示します。</span><span class="sxs-lookup"><span data-stu-id="29849-174">The following table shows TDE catalog views and dynamic management views.</span></span>

|<span data-ttu-id="29849-175">カタログ ビューまたは動的管理ビュー</span><span class="sxs-lookup"><span data-stu-id="29849-175">Catalog view or dynamic management view</span></span>|<span data-ttu-id="29849-176">目的</span><span class="sxs-lookup"><span data-stu-id="29849-176">Purpose</span></span>|
|---------------------------------------------|-------------|
|[<span data-ttu-id="29849-177">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-177">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)|<span data-ttu-id="29849-178">データベース情報を表示するカタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="29849-178">Catalog view that displays database information.</span></span>|
|[<span data-ttu-id="29849-179">sys.certificates &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-179">sys.certificates &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)|<span data-ttu-id="29849-180">データベース内の証明書を表示するカタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="29849-180">Catalog view that shows the certificates in a database.</span></span>|
|[<span data-ttu-id="29849-181">sys.dm_database_encryption_keys &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29849-181">sys.dm_database_encryption_keys &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)|<span data-ttu-id="29849-182">データベースで使用されている暗号化キー、およびデータベースの暗号化の状態に関する情報を表示する動的管理ビュー</span><span class="sxs-lookup"><span data-stu-id="29849-182">Dynamic management view that provides information about the encryption keys used in a database, and the state of encryption of a database.</span></span>|

## <a name="permissions"></a><span data-ttu-id="29849-183">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="29849-183">Permissions</span></span>
 <span data-ttu-id="29849-184">TDE の各機能とコマンドには、上の表で説明されているように、個別の権限要件があります。</span><span class="sxs-lookup"><span data-stu-id="29849-184">Each TDE feature and command has individual permission requirements, described in the tables shown earlier.</span></span>

 <span data-ttu-id="29849-185">TDE に関係するメタデータを表示するには、証明書に対する VIEW DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="29849-185">Viewing the metadata involved with TDE requires the VIEW DEFINITION permission on the certificate.</span></span>

## <a name="considerations"></a><span data-ttu-id="29849-186">考慮事項</span><span class="sxs-lookup"><span data-stu-id="29849-186">Considerations</span></span>
 <span data-ttu-id="29849-187">データベース暗号化操作の再暗号化スキャンが実行されている間は、データベースに対するメンテナンス操作が無効になります。</span><span class="sxs-lookup"><span data-stu-id="29849-187">While a re-encryption scan for a database encryption operation is in progress, maintenance operations to the database are disabled.</span></span> <span data-ttu-id="29849-188">メンテナンス操作を実行するには、データベースに対してシングル ユーザー モード設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="29849-188">You can use the single user mode setting for the database to perform the maintenance operation.</span></span> <span data-ttu-id="29849-189">詳細については、「 [データベースをシングル ユーザー モードに設定する](../../databases/set-a-database-to-single-user-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-189">For more information, see [Set a Database to Single-user Mode](../../databases/set-a-database-to-single-user-mode.md).</span></span>

 <span data-ttu-id="29849-190">データベースの暗号化の状態を確認するには、sys.dm_database_encryption_keys 動的管理ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="29849-190">You can find the state of the database encryption using the sys.dm_database_encryption_keys dynamic management view.</span></span> <span data-ttu-id="29849-191">詳細については、このトピックの「カタログ ビューと動的管理ビュー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-191">For more information, see the "Catalog Views and Dynamic Management Views"section earlier in this topic).</span></span>

 <span data-ttu-id="29849-192">TDE では、データベース内のすべてのファイルとファイル グループが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-192">In TDE, all files and filegroups in the database are encrypted.</span></span> <span data-ttu-id="29849-193">データベースに READ ONLY とマークされているファイル グループがあると、データベースの暗号化操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="29849-193">If any filegroups in a database are marked READ ONLY, the database encryption operation will fail.</span></span>

 <span data-ttu-id="29849-194">データベースがデータベース ミラーリングまたはログ配布で使用されている場合は、両方のデータベースが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-194">If a database is being used in database mirroring or log shipping, both databases will be encrypted.</span></span> <span data-ttu-id="29849-195">トランザクション ログは、2 つのデータベースの間で送信されるときに暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-195">The log transactions will be encrypted when sent between them.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="29849-196">データベースを暗号化の対象として設定すると、新しいフルテキスト インデックスが暗号化されるようになります。</span><span class="sxs-lookup"><span data-stu-id="29849-196">Any new full-text indexes will be encrypted when a database is set for encryption.</span></span> <span data-ttu-id="29849-197">以前に作成されたフルテキスト インデックスは、アップグレード時にインポートされ、データが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に読み込まれると TDE で暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-197">Previously-created full-text indexes will be imported during upgrade and they will be in TDE after the data is loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29849-198">列でフルテキスト インデックスを有効にすると、フルテキスト インデックス スキャンの実行時に、その列のデータがプレーンテキストでディスクに書き込まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29849-198">Enabling a full-text index on a column can cause that column's data to be written in plain text onto the disk during a full-text indexing scan.</span></span> <span data-ttu-id="29849-199">暗号化された機密データにはフルテキスト インデックスを作成しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="29849-199">We recommend that you do not create a full-text index on sensitive encrypted data.</span></span>

 <span data-ttu-id="29849-200">暗号化されたデータは、暗号化されていない同等のデータより、圧縮比率が大幅に下がります。</span><span class="sxs-lookup"><span data-stu-id="29849-200">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="29849-201">TDE を使用してデータベースを暗号化した場合、バックアップの圧縮によってバックアップ ストレージが大幅に圧縮されることはありません。</span><span class="sxs-lookup"><span data-stu-id="29849-201">If TDE is used to encrypt a database, backup compression will not be able to significantly compress the backup storage.</span></span> <span data-ttu-id="29849-202">したがって、TDE とバックアップの圧縮を併用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="29849-202">Therefore, using TDE and backup compression together is not recommended.</span></span>

### <a name="restrictions"></a><span data-ttu-id="29849-203">制限</span><span class="sxs-lookup"><span data-stu-id="29849-203">Restrictions</span></span>
 <span data-ttu-id="29849-204">最初のデータベース暗号化、キー変更、またはデータベースの暗号化解除の実行中は、次の操作を実行できません。</span><span class="sxs-lookup"><span data-stu-id="29849-204">The following operations are not allowed during initial database encryption, key change, or database decryption:</span></span>

-   <span data-ttu-id="29849-205">データベース内のファイル グループからのファイルの削除</span><span class="sxs-lookup"><span data-stu-id="29849-205">Dropping a file from a filegroup in the database</span></span>

-   <span data-ttu-id="29849-206">データベースの削除</span><span class="sxs-lookup"><span data-stu-id="29849-206">Dropping the database</span></span>

-   <span data-ttu-id="29849-207">データベースのオフライン化</span><span class="sxs-lookup"><span data-stu-id="29849-207">Taking the database offline</span></span>

-   <span data-ttu-id="29849-208">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="29849-208">Detaching a database</span></span>

-   <span data-ttu-id="29849-209">データベースまたはファイル グループの READ ONLY 状態への移行</span><span class="sxs-lookup"><span data-stu-id="29849-209">Transitioning a database or filegroup into a READ ONLY state</span></span>

 <span data-ttu-id="29849-210">CREATE DATABASE ENCRYPTION KEY、ALTER DATABASE ENCRYPTION KEY、DROP DATABASE ENCRYPTION KEY、または ALTER DATABASE...SET ENCRYPTION の各ステートメントの実行中は、次の操作を実行できません。</span><span class="sxs-lookup"><span data-stu-id="29849-210">The following operations are not allowed during the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="29849-211">データベース内のファイル グループからのファイルの削除</span><span class="sxs-lookup"><span data-stu-id="29849-211">Dropping a file from a filegroup in the database.</span></span>

-   <span data-ttu-id="29849-212">データベースの削除。</span><span class="sxs-lookup"><span data-stu-id="29849-212">Dropping the database.</span></span>

-   <span data-ttu-id="29849-213">データベースのオフライン化</span><span class="sxs-lookup"><span data-stu-id="29849-213">Taking the database offline.</span></span>

-   <span data-ttu-id="29849-214">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="29849-214">Detaching a database.</span></span>

-   <span data-ttu-id="29849-215">データベースまたはファイル グループの READ ONLY 状態への移行</span><span class="sxs-lookup"><span data-stu-id="29849-215">Transitioning a database or filegroup into a READ ONLY state.</span></span>

-   <span data-ttu-id="29849-216">ALTER DATABASE コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="29849-216">Using an ALTER DATABASE command.</span></span>

-   <span data-ttu-id="29849-217">データベースまたはデータベース ファイルのバックアップの開始</span><span class="sxs-lookup"><span data-stu-id="29849-217">Starting a database or database file backup.</span></span>

-   <span data-ttu-id="29849-218">データベースまたはデータベース ファイルの復元の開始</span><span class="sxs-lookup"><span data-stu-id="29849-218">Starting a database or database file restore.</span></span>

-   <span data-ttu-id="29849-219">スナップショットの作成</span><span class="sxs-lookup"><span data-stu-id="29849-219">Creating a snapshot.</span></span>

 <span data-ttu-id="29849-220">次の操作または状況が発生すると、CREATE DATABASE ENCRYPTION KEY、ALTER DATABASE ENCRYPTION KEY、DROP DATABASE ENCRYPTION KEY、または ALTER DATABASE...SET ENCRYPTION の各ステートメントを実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="29849-220">The following operations or conditions will prevent the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="29849-221">データベースが読み取り専用であるか、読み取り専用のファイル グループを含んでいる。</span><span class="sxs-lookup"><span data-stu-id="29849-221">The database is read-only or has any read-only file groups.</span></span>

-   <span data-ttu-id="29849-222">ALTER DATABASE コマンドが実行されている。</span><span class="sxs-lookup"><span data-stu-id="29849-222">An ALTER DATABASE command is executing.</span></span>

-   <span data-ttu-id="29849-223">データ バックアップが実行されている。</span><span class="sxs-lookup"><span data-stu-id="29849-223">Any data backup is running.</span></span>

-   <span data-ttu-id="29849-224">データベースがオフラインまたは復元中である。</span><span class="sxs-lookup"><span data-stu-id="29849-224">The database is in an offline or restore condition.</span></span>

-   <span data-ttu-id="29849-225">スナップショットが実行されている。</span><span class="sxs-lookup"><span data-stu-id="29849-225">A snapshot is in progress.</span></span>

-   <span data-ttu-id="29849-226">データベース メンテナンス タスク。</span><span class="sxs-lookup"><span data-stu-id="29849-226">Database maintenance tasks.</span></span>

 <span data-ttu-id="29849-227">データベース ファイルを作成する際には、TDE が有効になっているとファイルの瞬時初期化を使用できません。</span><span class="sxs-lookup"><span data-stu-id="29849-227">When creating database files, instant file initialization is not available when TDE is enabled.</span></span>

 <span data-ttu-id="29849-228">非対称キーでデータベース暗号化キーを暗号化するには、非対称キーが拡張キー管理プロバイダーに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-228">In order to encrypt the database encryption key with an asymmetric key, the asymmetric key must reside on an extensible key management provider.</span></span>

### <a name="transparent-data-encryption-and-transaction-logs"></a><span data-ttu-id="29849-229">Transparent Data Encryption とトランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="29849-229">Transparent Data Encryption and Transaction Logs</span></span>
 <span data-ttu-id="29849-230">データベースで TDE の使用を有効にすると、仮想トランザクション ログの残りの部分が "ゼロ設定" され、強制的に次の仮想トランザクション ログに移行します。</span><span class="sxs-lookup"><span data-stu-id="29849-230">Enabling a database to use TDE has the effect of "zeroing out" the remaining part of the virtual transaction log to force the next virtual transaction log.</span></span> <span data-ttu-id="29849-231">これにより、データベースが暗号化対象として設定された後にトランザクション ログにクリア テキストが残らないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="29849-231">This guarantees that no clear text is left in the transaction logs after the database is set for encryption.</span></span> <span data-ttu-id="29849-232">ログ ファイルの暗号化の状態を確認するには、次の例のように `encryption_state` ビュー内の `sys.dm_database_encryption_keys` 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="29849-232">You can find the status of the log file encryption by viewing the `encryption_state` column in the `sys.dm_database_encryption_keys` view, as in this example:</span></span>

```
USE AdventureWorks2012;
GO
/* The value 3 represents an encrypted state 
   on the database and transaction logs. */
SELECT *
FROM sys.dm_database_encryption_keys
WHERE encryption_state = 3;
GO
```

 <span data-ttu-id="29849-233">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログ ファイル アーキテクチャの詳細については、「[トランザクション ログ &#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-233">For more information about the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] log file architecture, see [The Transaction Log &#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md).</span></span>

 <span data-ttu-id="29849-234">データベース暗号化キーを変更する前にトランザクション ログに書き込まれたデータは、以前のデータベース暗号化キーで暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-234">All data written to the transaction log before a change in the database encryption key will be encrypted by using the previous database encryption key.</span></span>

 <span data-ttu-id="29849-235">データベース暗号化キーを 2 回変更した後は、データベース暗号化キーを再度変更する前に、ログ バックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-235">After a database encryption key has been modified twice, a log backup must be performed before the database encryption key can be modified again.</span></span>

### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a><span data-ttu-id="29849-236">Transparent Data Encryption と tempdb システム データベース</span><span class="sxs-lookup"><span data-stu-id="29849-236">Transparent Data Encryption and the tempdb System Database</span></span>
 <span data-ttu-id="29849-237">tempdb システム データベースは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス上の他のデータベースが TDE を使用して暗号化されると暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-237">The tempdb system database will be encrypted if any other database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is encrypted by using TDE.</span></span> <span data-ttu-id="29849-238">この場合、同じ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス上にある暗号化されないデータベースのパフォーマンスに影響が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="29849-238">This might have a performance effect for unencrypted databases on the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29849-239">tempdb システム データベースの詳細については、「[tempdb データベース](../../databases/tempdb-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-239">For more information about the tempdb system database, see [tempdb Database](../../databases/tempdb-database.md).</span></span>

### <a name="transparent-data-encryption-and-replication"></a><span data-ttu-id="29849-240">Transparent Data Encryption とレプリケーション</span><span class="sxs-lookup"><span data-stu-id="29849-240">Transparent Data Encryption and Replication</span></span>
 <span data-ttu-id="29849-241">レプリケーションでは、TDE が有効になっているデータベースのデータが暗号化された形式で自動的にレプリケートされることはありません。</span><span class="sxs-lookup"><span data-stu-id="29849-241">Replication does not automatically replicate data from a TDE-enabled database in an encrypted form.</span></span> <span data-ttu-id="29849-242">ディストリビューション データベースとサブスクライバー データベースを保護する場合は、TDE を個別に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-242">You must separately enable TDE if you want to protect the distribution and subscriber databases.</span></span> <span data-ttu-id="29849-243">スナップショット レプリケーションでは、トランザクション レプリケーションとマージ レプリケーションへの最初のデータ ディストリビューションと同様に、暗号化されていない中間ファイル (bcp ファイルなど) にデータを格納できます。</span><span class="sxs-lookup"><span data-stu-id="29849-243">Snapshot replication, as well as the initial distribution of data for transactional and merge replication, can store data in unencrypted intermediate files; for example, the bcp files.</span></span>  <span data-ttu-id="29849-244">トランザクション レプリケーションまたはマージ レプリケーション時に、暗号化を有効にして通信チャネルを保護することができます。</span><span class="sxs-lookup"><span data-stu-id="29849-244">During transactional or merge replication, encryption can be enabled to protect the communication channel.</span></span> <span data-ttu-id="29849-245">詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29849-245">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>

### <a name="transparent-data-encryption-and-filestream-data"></a><span data-ttu-id="29849-246">Transparent Data Encryption と FILESTREAM データ</span><span class="sxs-lookup"><span data-stu-id="29849-246">Transparent Data Encryption and FILESTREAM DATA</span></span>
 <span data-ttu-id="29849-247">FILESTREAM データは TDE が有効になっている場合でも暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="29849-247">FILESTREAM data is not encrypted even when TDE is enabled.</span></span>

### <a name="transparent-data-encryption-and-buffer-pool-extension"></a><span data-ttu-id="29849-248">Transparent Data Encryption とバッファー プール拡張機能</span><span class="sxs-lookup"><span data-stu-id="29849-248">Transparent Data Encryption and Buffer Pool Extension</span></span>
 <span data-ttu-id="29849-249">バッファー プール拡張機能 (BPE) に関連するファイルは、データベースが TDE を使用して暗号化される場合でも暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="29849-249">Files related to buffer pool extension (BPE) are not encrypted when database is encrypted using TDE.</span></span> <span data-ttu-id="29849-250">BPE 関連のファイルについては、Bitlocker や EFS などのファイル システム レベルの暗号化ツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29849-250">You must use file system level encryption tools like Bitlocker or EFS for BPE related files.</span></span>

## <a name="transparent-data-encryption-and-in-memory-oltp"></a><span data-ttu-id="29849-251">Transparent Data Encryption とインメモリ OLTP</span><span class="sxs-lookup"><span data-stu-id="29849-251">Transparent Data Encryption and In-Memory OLTP</span></span>
 <span data-ttu-id="29849-252">TDE は、インメモリ OLTP オブジェクトを含むデータベースで有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="29849-252">TDE can be enabled on a database that has In-Memory OLTP objects.</span></span> <span data-ttu-id="29849-253">TDE が有効な場合、インメモリ OLTP ログ レコードが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="29849-253">In-Memory OLTP log records are encrypted if TDE is enabled.</span></span> <span data-ttu-id="29849-254">MEMORY_OPTIMIZED_DATA ファイル グループのデータは、TDE が有効な場合は暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="29849-254">Data in a MEMORY_OPTIMIZED_DATA filegroup is not encrypted if TDE is enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="29849-255">参照</span><span class="sxs-lookup"><span data-stu-id="29849-255">See Also</span></span>
 <span data-ttu-id="29849-256">[Tde で保護されたデータベースを別の SQL Server に移動](move-a-tde-protected-database-to-another-sql-server.md)します。 EKM [Transparent Data Encryption と Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server 暗号化](sql-server-encryption.md) [SQL Server およびデータベース暗号化キー](sql-server-and-database-encryption-keys-database-engine.md)を[使用して tde を有効に](enable-tde-on-sql-server-using-ekm.md)し &#40;データベースエンジン&#41;[と Security Center](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM SQL Server](../../blob/filestream-sql-server.md)データベースエンジンを Azure SQL Database &#40;</span><span class="sxs-lookup"><span data-stu-id="29849-256">[Move a TDE Protected Database to Another SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server Encryption](sql-server-encryption.md) [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) [Security Center for SQL Server Database Engine and Azure SQL Database](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)</span></span>


