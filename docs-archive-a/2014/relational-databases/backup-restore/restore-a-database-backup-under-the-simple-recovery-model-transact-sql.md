---
title: 単純復旧モデルでのデータベース バックアップの復元 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e264dd380c3dff40dacc4eb576d34af5195dec01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714441"
---
# <a name="restore-a-database-backup-under-the-simple-recovery-model-transact-sql"></a><span data-ttu-id="80f13-102">単純復旧モデルでのデータベース バックアップの復元 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="80f13-102">Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="80f13-103">このトピックでは、データベースの完全バックアップを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80f13-103">This topic explains how to restore a full database backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="80f13-104">データベースの完全バックアップの復元中は、復元作業を実行するシステム管理者以外は、復元中のデータベースを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="80f13-104">The system administrator restoring the full database backup must be the only person currently using the database to be restored.</span></span>  
  
## <a name="prerequisites-and-recommendations"></a><span data-ttu-id="80f13-105">前提条件と推奨事項</span><span class="sxs-lookup"><span data-stu-id="80f13-105">Prerequisites and Recommendations</span></span>  
  
-   <span data-ttu-id="80f13-106">暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="80f13-106">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="80f13-107">証明書または非対称キーがないと、データベースは復元できません。</span><span class="sxs-lookup"><span data-stu-id="80f13-107">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="80f13-108">このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="80f13-108">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="80f13-109">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80f13-109">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="80f13-110">セキュリティを確保するため、不明なソースや信頼されていないソースからのデータベースは、アタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="80f13-110">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="80f13-111">こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80f13-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="80f13-112">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="80f13-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="80f13-113">アップグレード後のデータベース互換性レベル</span><span class="sxs-lookup"><span data-stu-id="80f13-113">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="80f13-114">**tempdb**、 **model**、 **msdb** 、および **Resource** データベースの互換性レベルは、アップグレード後に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の互換性レベルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="80f13-114">The compatibility levels of the **tempdb**, **model**, **msdb** and **Resource** databases are set to the compatibility level of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after upgrade.</span></span> <span data-ttu-id="80f13-115">**master** システム データベースは、互換性レベルが 100 を下回っている場合を除いて、アップグレード前の互換性レベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="80f13-115">The **master** system database retains the compatibility level it had before upgrade, unless that level was less than 100.</span></span> <span data-ttu-id="80f13-116">アップグレード前の **master** の互換性レベルが 100 を下回っている場合は、アップグレード後、100 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="80f13-116">If the compatibility level of **master** was less than 100 before upgrade, it is set to 100 after upgrade.</span></span>  
  
 <span data-ttu-id="80f13-117">アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。</span><span class="sxs-lookup"><span data-stu-id="80f13-117">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="80f13-118">アップグレード前の互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でサポートされている下限の互換性レベルです。</span><span class="sxs-lookup"><span data-stu-id="80f13-118">If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80f13-119">新しいユーザー データベースには、 **model** データベースの互換性レベルが継承されます。</span><span class="sxs-lookup"><span data-stu-id="80f13-119">New user databases will inherit the compatibility level of the **model** database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="80f13-120">手順</span><span class="sxs-lookup"><span data-stu-id="80f13-120">Procedures</span></span>  
  
#### <a name="to-restore-a-full-database-backup"></a><span data-ttu-id="80f13-121">データベースの完全バックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="80f13-121">To restore a full database backup</span></span>  
  
1.  <span data-ttu-id="80f13-122">次の項目を指定した RESTORE DATABASE ステートメントを実行し、データベースの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="80f13-122">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="80f13-123">復元するデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="80f13-123">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="80f13-124">データベースの完全バックアップの復元元バックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="80f13-124">The backup device from where the full database backup is restored.</span></span>  
  
    -   <span data-ttu-id="80f13-125">NORECOVERY 句。データベースの完全バックアップを復元した後に適用するトランザクション ログまたはデータベースの差分バックアップがある場合に指定します。</span><span class="sxs-lookup"><span data-stu-id="80f13-125">The NORECOVERY clause if you have a transaction log or differential database backup to apply after restoring the full database backup.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="80f13-126">暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。</span><span class="sxs-lookup"><span data-stu-id="80f13-126">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="80f13-127">証明書または非対称キーがないと、データベースは復元できません。</span><span class="sxs-lookup"><span data-stu-id="80f13-127">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="80f13-128">このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="80f13-128">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="80f13-129">詳細については、「 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80f13-129">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="80f13-130">必要に応じて、以下も指定します。</span><span class="sxs-lookup"><span data-stu-id="80f13-130">Optionally, specify:</span></span>  
  
    -   <span data-ttu-id="80f13-131">FILE 句。バックアップ デバイス上の復元するバックアップ セットを識別するとき指定します。</span><span class="sxs-lookup"><span data-stu-id="80f13-131">The FILE clause to identify the backup set on the backup device to restore.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80f13-132">以前のバージョンのデータベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]に復元すると、データベースが自動的にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="80f13-132">If you restore an earlier version database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="80f13-133">通常、データベースは直ちに使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="80f13-133">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="80f13-134">ただし、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、  **upgrade_option** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。</span><span class="sxs-lookup"><span data-stu-id="80f13-134">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="80f13-135">アップグレード オプションがインポート (**upgrade_option** = 2) または再構築 (**upgrade_option** = 0) に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="80f13-135">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="80f13-136">インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="80f13-136">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="80f13-137">また、アップグレード オプションがインポートに設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="80f13-137">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="80f13-138">**upgrade_option** サーバー プロパティの設定を変更するには、 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="80f13-138">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80f13-139">例</span><span class="sxs-lookup"><span data-stu-id="80f13-139">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="80f13-140">説明</span><span class="sxs-lookup"><span data-stu-id="80f13-140">Description</span></span>  
 <span data-ttu-id="80f13-141">この例では、テープから [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] の完全データベース バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="80f13-141">This example restores the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] full database backup from tape.</span></span>  
  
### <a name="example"></a><span data-ttu-id="80f13-142">例</span><span class="sxs-lookup"><span data-stu-id="80f13-142">Example</span></span>  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="80f13-143">参照</span><span class="sxs-lookup"><span data-stu-id="80f13-143">See Also</span></span>  
 <span data-ttu-id="80f13-144">[データベースの全体復元 &#40;完全復旧モデル&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="80f13-144">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="80f13-145">[データベースの全体復元 &#40;単純復旧モデル&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="80f13-145">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="80f13-146">[データベースの完全バックアップ &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80f13-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="80f13-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="80f13-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="80f13-148">[バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80f13-148">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 [<span data-ttu-id="80f13-149">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="80f13-149">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
