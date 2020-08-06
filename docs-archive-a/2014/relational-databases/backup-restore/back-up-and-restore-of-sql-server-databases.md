---
title: SQL Server データベースのバックアップと復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], see restoring [SQL Server]
- backups [SQL Server]
- restoring databases [SQL Server]
- backup [SQL Server], see backing up [SQL Server]
- databases [SQL Server], restoring
- backing up databases [SQL Server]
- restore [SQL Server], see restoring [SQL Server]
- disaster recovery [SQL Server], see backing up [SQL Server]
- backing up [SQL Server]
- Database Engine [SQL Server], backups
- databases [SQL Server], backups
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec2104219d98ed3cb97bfbb8993a3c28d45841c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645699"
---
# <a name="back-up-and-restore-of-sql-server-databases"></a><span data-ttu-id="cd94e-102">SQL Server データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="cd94e-102">Back Up and Restore of SQL Server Databases</span></span>
  <span data-ttu-id="cd94e-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをバックアップする利点、バックアップと復元に関する基本的な用語、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップと復元の方法を紹介します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップと復元のセキュリティに関する考慮事項についても取り上げます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-103">This topic describes the benefits of backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, basic backup and restore terms, and introduces backup and restore strategies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and security considerations for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore.</span></span>  
  
 <span data-ttu-id="cd94e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップと復元コンポーネントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納されている大切なデータを保護するうえで不可欠な保護対策を提供します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore component provides an essential safeguard for protecting critical data stored in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="cd94e-105">致命的なデータ損失のリスクを最小限に抑えるには、データベースを定期的にバックアップして、データの変更を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-105">To minimize the risk of catastrophic data loss, you need to back up your databases to preserve modifications to your data on a regular basis.</span></span> <span data-ttu-id="cd94e-106">十分に計画されたバックアップおよび復元戦略は、さまざまな障害が原因で発生するデータ損失からデータベースを保護します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-106">A well-planned backup and restore strategy helps protect databases against data loss caused by a variety of failures.</span></span> <span data-ttu-id="cd94e-107">一連のバックアップの復元とデータベースの回復を実行することでご自分の戦略をテストして、災害に効率的に対応するための準備を整えてください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-107">Test your strategy by restoring a set of backups and then recovering your database to prepare you to respond effectively to a disaster.</span></span>  
  
 <span data-ttu-id="cd94e-108">バックアップを格納するローカル ストレージに加えて、SQL Server では、バックアップおよび Azure Blob Storage サービスからの復元がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-108">In addition to local storage for storing the backups, SQL Server also supports backup to and restore from the Azure Blob Storage Service.</span></span> <span data-ttu-id="cd94e-109">詳細については、「 [Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-109">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  

  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="cd94e-110">利点</span><span class="sxs-lookup"><span data-stu-id="cd94e-110">Benefits</span></span>  
  
-   <span data-ttu-id="cd94e-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをバックアップしたり、既存のバックアップの復元テストを実行したりできるほか、離れた安全な場所にバックアップのコピーを保管することによって、致命的な損失からデータを保護することができます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-111">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, running test restores procedures on your backups, and storing copies of backups in a safe, off-site location protects you from potentially catastrophic data loss.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cd94e-112">これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータを確実に保護する唯一の手段です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-112">This is the only way to reliably protect your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data.</span></span>  
  
     <span data-ttu-id="cd94e-113">データベースの有効なバックアップがあれば、次に示したようなさまざまな障害からデータを復旧することができます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-113">With valid backups of a database, you can recover your data from many failures, such as:</span></span>  
  
    -   <span data-ttu-id="cd94e-114">メディアの障害</span><span class="sxs-lookup"><span data-stu-id="cd94e-114">Media failure.</span></span>  
  
    -   <span data-ttu-id="cd94e-115">ユーザー エラー (テーブルの誤削除など)</span><span class="sxs-lookup"><span data-stu-id="cd94e-115">User errors, for example, dropping a table by mistake.</span></span>  
  
    -   <span data-ttu-id="cd94e-116">ハードウェア障害 (ディスク ドライブの損傷や、復旧の可能性のないサーバー障害など)</span><span class="sxs-lookup"><span data-stu-id="cd94e-116">Hardware failures, for example, a damaged disk drive or permanent loss of a server.</span></span>  
  
    -   <span data-ttu-id="cd94e-117">自然災害。</span><span class="sxs-lookup"><span data-stu-id="cd94e-117">Natural disasters.</span></span> <span data-ttu-id="cd94e-118">Azure Blob Storage サービスへの SQL Server バックアップを使用すると、オンプレミスの場所に影響する自然災害が発生した場合に使用できるように、オンプレミスの場所とは異なるリージョンにオフサイト バックアップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-118">By using SQL Server Backup to Azure Blob storage service, you can create an off-site backup in a different region than your on-premises location, to use in the event of a natural disaster affecting your on-premises location.</span></span>  
  
-   <span data-ttu-id="cd94e-119">また、データベースのバックアップは、サーバー間でのデータベースのコピー、 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] やデータベース ミラーリングのセットアップ、およびアーカイブなど、日常的な管理作業を行ううえでも便利です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-119">Additionally, backups of a database are useful for routine administrative purposes, such as copying a database from one server to another, setting up [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring, and archiving.</span></span>  
  

  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="cd94e-120">コンポーネントおよび概念</span><span class="sxs-lookup"><span data-stu-id="cd94e-120">Components and Concepts</span></span>  
 <span data-ttu-id="cd94e-121">バックアップ (back up) (動詞)</span><span class="sxs-lookup"><span data-stu-id="cd94e-121">back up [verb]</span></span>  
 <span data-ttu-id="cd94e-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースまたはそのトランザクション ログからバックアップ デバイス (ディスクなど) にデータまたはログ レコードをコピーすることによって、データ バックアップまたはログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-122">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="cd94e-123">バックアップ (backup) (名詞)</span><span class="sxs-lookup"><span data-stu-id="cd94e-123">backup [noun]</span></span>  
 <span data-ttu-id="cd94e-124">障害の発生後、データの復元と復旧に使用できるデータのコピー。</span><span class="sxs-lookup"><span data-stu-id="cd94e-124">A copy of data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="cd94e-125">データベースのバックアップを使用して、コピー (データベース) を新しい場所に復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-125">Backups of a database can also be used to restore a copy the database to a new location.</span></span>  
  
 <span data-ttu-id="cd94e-126">バックアップ デバイス (backup device)</span><span class="sxs-lookup"><span data-stu-id="cd94e-126">backup device</span></span>  
 <span data-ttu-id="cd94e-127">SQL Server のバックアップの書き込みと復元に使用されるディスクまたはテープ デバイス。</span><span class="sxs-lookup"><span data-stu-id="cd94e-127">A disk or tape device to which SQL Server backups are written and from which they can be restored.</span></span> <span data-ttu-id="cd94e-128">SQL Server のバックアップは、Azure Blob Storage サービスに書き込むこともできます。バックアップ先とバックアップ ファイルの名前を指定するには **URL** 形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-128">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="cd94e-129">詳細については、「 [Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-129">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="cd94e-130">バックアップ メディア (backup media)</span><span class="sxs-lookup"><span data-stu-id="cd94e-130">backup media</span></span>  
 <span data-ttu-id="cd94e-131">バックアップの書き込み先となる 1 つまたは複数のテープまたはディスク ファイル。</span><span class="sxs-lookup"><span data-stu-id="cd94e-131">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 <span data-ttu-id="cd94e-132">データ バックアップ (data backup)</span><span class="sxs-lookup"><span data-stu-id="cd94e-132">data backup</span></span>  
 <span data-ttu-id="cd94e-133">データのバックアップ。データベース全体 (データ バックアップ)、データベースの一部 (部分バックアップ)、または一連のデータ ファイルやファイル グループ (ファイル バックアップ) の形式で存在します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-133">A backup of data in a complete database (a database backup), a partial database ( a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 <span data-ttu-id="cd94e-134">データベース バックアップ (database backup)</span><span class="sxs-lookup"><span data-stu-id="cd94e-134">database backup</span></span>  
 <span data-ttu-id="cd94e-135">データベースのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="cd94e-135">A backup of a database.</span></span> <span data-ttu-id="cd94e-136">データベースの完全バックアップは、バックアップが完了した時点のデータベース全体を表します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-136">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="cd94e-137">差分データベース バックアップには、最新の完全バックアップ以降に行われたデータベースへの変更のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-137">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 <span data-ttu-id="cd94e-138">差分バックアップ (differential backup)</span><span class="sxs-lookup"><span data-stu-id="cd94e-138">differential backup</span></span>  
 <span data-ttu-id="cd94e-139">データベース全体、データベースの一部、または一連のデータ ファイル (またはファイル グループ) の最新の完全バックアップ (差分ベース) をベースとし、その差分ベース以後に変更されたデータのみを含んだデータ バックアップ。</span><span class="sxs-lookup"><span data-stu-id="cd94e-139">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the differential base) and that contains only the data that has changed since that base.</span></span>  
  
 <span data-ttu-id="cd94e-140">完全バックアップ (full backup)</span><span class="sxs-lookup"><span data-stu-id="cd94e-140">full backup</span></span>  
 <span data-ttu-id="cd94e-141">特定のデータベース (または一連のファイルやファイル グループ) 内のデータがすべて含まれ、さらに、データを復旧するために必要なログも含んだデータ バックアップ。</span><span class="sxs-lookup"><span data-stu-id="cd94e-141">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 <span data-ttu-id="cd94e-142">ログ バックアップ (log backup)</span><span class="sxs-lookup"><span data-stu-id="cd94e-142">log backup</span></span>  
 <span data-ttu-id="cd94e-143">前回のログ バックアップでバックアップされなかったすべてのログ レコードを含むトランザクション ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="cd94e-143">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="cd94e-144">(完全復旧モデル)。</span><span class="sxs-lookup"><span data-stu-id="cd94e-144">(full recovery model)</span></span>  
  
 <span data-ttu-id="cd94e-145">recover</span><span class="sxs-lookup"><span data-stu-id="cd94e-145">recover</span></span>  
 <span data-ttu-id="cd94e-146">安定し一貫した状態にデータベースを戻すこと。</span><span class="sxs-lookup"><span data-stu-id="cd94e-146">To return a database to a stable and consistent state.</span></span>  
  
 <span data-ttu-id="cd94e-147">復旧 (recovery)</span><span class="sxs-lookup"><span data-stu-id="cd94e-147">recovery</span></span>  
 <span data-ttu-id="cd94e-148">データベースをトランザクションの一貫性が保たれた状態にする、データベース起動時または RESTORE WITH RECOVERY 時のフェーズ。</span><span class="sxs-lookup"><span data-stu-id="cd94e-148">A phase of database startup or of a restore with recovery that brings the database into a transaction-consistent state.</span></span>  
  
 <span data-ttu-id="cd94e-149">復旧モデル (recovery model)</span><span class="sxs-lookup"><span data-stu-id="cd94e-149">recovery model</span></span>  
 <span data-ttu-id="cd94e-150">データベースのトランザクション ログのメンテナンスを制御するデータベース プロパティ。</span><span class="sxs-lookup"><span data-stu-id="cd94e-150">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="cd94e-151">復旧モデルの種類は、単純、完全、および一括ログの 3 種類です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-151">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="cd94e-152">データベースのバックアップと復元の要件は、その復旧モデルによって決まります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-152">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 <span data-ttu-id="cd94e-153">復元</span><span class="sxs-lookup"><span data-stu-id="cd94e-153">restore</span></span>  
 <span data-ttu-id="cd94e-154">データを直近の状態まで戻す複数フェーズから成る処理。指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップからすべてのデータおよびログ ページを指定されたデータベースにコピーするフェーズと、バックアップにログとして記録されているすべてのトランザクションをロールフォワード (ログに記録されている変更を適用) するフェーズとで構成されます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-154">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  

  
##  <a name="introduction-to-backup-and-restore-strategies"></a><a name="BnrStrategies"></a><span data-ttu-id="cd94e-155">バックアップと復元の方法の概要</span><span class="sxs-lookup"><span data-stu-id="cd94e-155">Introduction to Backup and Restore Strategies</span></span>  
 <span data-ttu-id="cd94e-156">データのバックアップと復元は、特定の環境向けにカスタマイズし、使用可能なリソースと連動させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-156">Backing up and restoring data must be customized to a particular environment and must work with the available resources.</span></span> <span data-ttu-id="cd94e-157">したがって、信頼性が確保された状態でバックアップと復元を使用して復旧するには、バックアップと復元のストラテジが必要です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-157">Therefore, a reliable use of backup and restore for recovery requires a backup and restore strategy.</span></span> <span data-ttu-id="cd94e-158">バックアップと復元のストラテジ設計が良ければ、特定のビジネス要件を考慮しながら、データの可用性を最大にし、データ損失を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-158">A well-designed backup and restore strategy maximizes data availability and minimizes data loss, while considering your particular business requirements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cd94e-159">データベースとバックアップは異なるデバイスに置いてください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-159">Place the database and backups on separate devices.</span></span> <span data-ttu-id="cd94e-160">そうしないと、データベースを置いているデバイスに障害が発生した場合、バックアップも使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-160">Otherwise, if the device containing the database fails, your backups will be unavailable.</span></span> <span data-ttu-id="cd94e-161">データとバックアップを異なるデバイスに置くと、バックアップの書き込みでもデータベースの運用でも I/O パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-161">Placing the data and backups on separate devices also enhances the I/O performance for both writing backups and the production use of the database.</span></span>  
  
 <span data-ttu-id="cd94e-162">バックアップと復元のストラテジには、バックアップに関する部分と復元に関する部分があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-162">A backup and restore strategy contains a backup portion and a restore portion.</span></span> <span data-ttu-id="cd94e-163">ストラテジで扱うバックアップ部分では、バックアップの種類と頻度、バックアップに必要なハードウェアの性質と速度、バックアップのテスト方法、およびバックアップ メディアの保管場所と保管方法 (セキュリティ上の考慮事項も含む) を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-163">The backup part of the strategy defines the type and frequency of backups, the nature and speed of the hardware that is required for them, how backups are to be tested, and where and how backup media is to be stored (including security considerations).</span></span> <span data-ttu-id="cd94e-164">ストラテジで扱う復元部分では、復元の実行責任者と、データベースの可用性とデータ損失の最小化という目標を達成するためにどのように復元を実行するのかを定義します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-164">The restore part of the strategy defines who is responsible for performing restores and how restores should be performed to meet your goals for availability of the database and for minimizing data loss.</span></span> <span data-ttu-id="cd94e-165">バックアップと復元の手順をドキュメント化し、そのドキュメントを運用手順書に含めて保管することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd94e-165">We recommend that you document your backup and restore procedures and keep a copy of the documentation in your run book.</span></span>  
  
 <span data-ttu-id="cd94e-166">バックアップと復元について効果的なストラテジをデザインするには、慎重に計画、実装、およびテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-166">Designing an effective backup and restore strategy requires careful planning, implementation, and testing.</span></span> <span data-ttu-id="cd94e-167">テストは必ず行ってください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-167">Testing is required.</span></span> <span data-ttu-id="cd94e-168">復元ストラテジに含まれるすべての組み合わせでバックアップを正常に復元できるようになって初めて、バックアップ ストラテジは完成します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-168">You do not have a backup strategy until you have successfully restored backups in all the combinations that are included in your restore strategy.</span></span> <span data-ttu-id="cd94e-169">さまざまな要因を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-169">You must consider a variety of factors.</span></span> <span data-ttu-id="cd94e-170">コーディネートは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cd94e-170">These include the following:</span></span>  
  
-   <span data-ttu-id="cd94e-171">組織がそのデータベースに求める生産目標。特に、可用性とデータ損失からの保護に関する要件。</span><span class="sxs-lookup"><span data-stu-id="cd94e-171">The production goals of your organization for the databases, especially the requirements for availability and protection of data from loss.</span></span>  
  
-   <span data-ttu-id="cd94e-172">各データベースの性質。サイズ、使用パターン、内容の性質、保持しているデータの要件など。</span><span class="sxs-lookup"><span data-stu-id="cd94e-172">The nature of each of your databases: its size, its usage patterns, the nature of its content, the requirements for its data, and so on.</span></span>  
  
-   <span data-ttu-id="cd94e-173">リソースについての制約。ハードウェア、スタッフ、バックアップ メディアを保管する場所、保管されたメディアの物理的なセキュリティなど。</span><span class="sxs-lookup"><span data-stu-id="cd94e-173">Constraints on resources, such as: hardware, personnel, space for storing backup media, the physical security of the stored media, and so on.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd94e-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク上のストレージ形式は、64 ビット環境でも 32 ビット環境でも同じです。</span><span class="sxs-lookup"><span data-stu-id="cd94e-174">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="cd94e-175">このため、バックアップと復元は 32 ビット環境と 64 ビット環境の間でも機能します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-175">Therefore, backup and restore work across 32-bit and 64-bit environments.</span></span> <span data-ttu-id="cd94e-176">一方の環境で実行中のサーバー インスタンスで作成したバックアップは、他方の環境で実行中のサーバー インスタンスで復元できます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-176">A backup created on a server instance running in one environment can be restored on a server instance that runs in the other environment.</span></span>  
  

  
### <a name="impact-of-the-recovery-model-on-backup-and-restore"></a><span data-ttu-id="cd94e-177">バックアップおよび復元に対する復旧モデルの影響</span><span class="sxs-lookup"><span data-stu-id="cd94e-177">Impact of the Recovery Model on Backup and Restore</span></span>  
 <span data-ttu-id="cd94e-178">バックアップ操作および復元操作は、復旧モデルのコンテキストで発生します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-178">Backup and restore operations occur within the context of a recovery model.</span></span> <span data-ttu-id="cd94e-179">復旧モデルは、トランザクション ログの管理方法を制御するデータベース プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cd94e-179">A recovery model is a database property that controls how the transaction log is managed.</span></span> <span data-ttu-id="cd94e-180">また、データベースの復旧モデルでは、そのデータベースでサポートされるバックアップの種類および復元シナリオが判断されます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-180">Also, the recovery model of a database determines what types of backups and what restore scenarios are supported for the database.</span></span> <span data-ttu-id="cd94e-181">通常、データベースは単純復旧モデルまたは完全復旧モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-181">Typically a database uses either the simple recovery model or the full recovery model.</span></span> <span data-ttu-id="cd94e-182">完全復旧モデルを補完するには、一括操作を行う前に一括ログ復旧モデルに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-182">The full recovery model can be supplemented by switching to the bulk-logged recovery model before bulk operations.</span></span> <span data-ttu-id="cd94e-183">これらの復旧モデルの概要とトランザクション ログの管理への影響については、「[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-183">For an introduction to these recovery models and how they affect transaction log management, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="cd94e-184">データベースに対する復旧モデルの最善の選択は、ビジネス要件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-184">The best choice of recovery model for the database depends on your business requirements.</span></span> <span data-ttu-id="cd94e-185">トランザクション ログの管理を不要にし、バックアップと復元を簡単にするには、単純復旧モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-185">To avoid transaction log management and simplify backup and restore, use the simple recovery model.</span></span> <span data-ttu-id="cd94e-186">作業損失の可能性を最小に抑えるには、管理のオーバーヘッドが発生するという犠牲を払っても、完全復旧モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-186">To minimize work-loss exposure, at the cost of administrative overhead, use the full recovery model.</span></span> <span data-ttu-id="cd94e-187">バックアップおよび復元に対する復旧モデルの影響については、「 [バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-187">For information about the effect of recovery models on backup and restore, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
### <a name="design-the-backup-strategy"></a><span data-ttu-id="cd94e-188">バックアップ ストラテジの設計</span><span class="sxs-lookup"><span data-stu-id="cd94e-188">Design the Backup Strategy</span></span>  
 <span data-ttu-id="cd94e-189">特定のデータベースに対するビジネス要件を満たす復旧モデルを選択した後、対応するバックアップ ストラテジを計画して実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-189">After you have selected a recovery model that meets your business requirements for a specific database, you have to plan and implement a corresponding backup strategy.</span></span> <span data-ttu-id="cd94e-190">最適なバックアップ ストラテジはさまざまな要因に依存しますが、その中でも以下の要因が特に重要です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-190">The optimal backup strategy depends on a variety of factors, of which the following are especially significant:</span></span>  
  
-   <span data-ttu-id="cd94e-191">アプリケーションがデータベースにアクセスする必要があるのは 1 日に何時間か。</span><span class="sxs-lookup"><span data-stu-id="cd94e-191">How many hours a day do applications have to access the database?</span></span>  
  
     <span data-ttu-id="cd94e-192">オフピーク時間が予測できる場合は、その時間にデータベースの完全バックアップをスケジュールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd94e-192">If there is a predictable off-peak period, we recommend that you schedule full database backups for that period.</span></span>  
  
-   <span data-ttu-id="cd94e-193">変更や更新はどの程度の頻度で行われるか。</span><span class="sxs-lookup"><span data-stu-id="cd94e-193">How frequently are changes and updates likely to occur?</span></span>  
  
     <span data-ttu-id="cd94e-194">変更が頻繁に行われる場合は、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-194">If changes are frequent, consider the following:</span></span>  
  
    -   <span data-ttu-id="cd94e-195">単純復旧モデルでは、データベースの完全バックアップの合間に差分バックアップをスケジュールすることを検討します。</span><span class="sxs-lookup"><span data-stu-id="cd94e-195">Under the simple recovery model, consider scheduling differential backups between full database backups.</span></span> <span data-ttu-id="cd94e-196">差分バックアップは、データベースの最後の完全バックアップ以降の変更だけをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="cd94e-196">A differential backup captures only the changes since the last full database backup.</span></span>  
  
    -   <span data-ttu-id="cd94e-197">完全復旧モデルでは、ログ バックアップを頻繁に行うようスケジュールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-197">Under the full recovery model, you should schedule frequent log backups.</span></span> <span data-ttu-id="cd94e-198">完全バックアップの合間に差分バックアップを行うようにスケジュールすると、データを復元した後で復元する必要のあるログ バックアップの数が減るので、復元時間を短縮することができます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-198">Scheduling differential backups between full backups can reduce restore time by reducing the number of log backups you have to restore after restoring the data.</span></span>  
  
-   <span data-ttu-id="cd94e-199">変更は、データベースの一部分でのみ行われるか、データベースの大部分で行われるか。</span><span class="sxs-lookup"><span data-stu-id="cd94e-199">Are changes likely to occur in only a small part of the database or in a large part of the database?</span></span>  
  
     <span data-ttu-id="cd94e-200">ファイルまたはファイル グループの一部分に変更が集中する大規模なデータベースでは、部分バックアップまたはファイル バックアップが有効です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-200">For a large database in which changes are concentrated in a part of the files or filegroups, partial backups and or file backups can be useful.</span></span> <span data-ttu-id="cd94e-201">詳細については、「[部分バックアップ &#40;SQL Server&#41;](partial-backups-sql-server.md)」と「[完全バックアップ &#40;SQL Server&#41;](full-file-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-201">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md) and [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="cd94e-202">データベースの完全バックアップにはどの程度のディスク領域が必要か。</span><span class="sxs-lookup"><span data-stu-id="cd94e-202">How much disk space will a full database backup require?</span></span>  
  
     <span data-ttu-id="cd94e-203">詳細については、このセクションの「[データベースの完全バックアップのサイズの推計](#EstimateDbBuSize)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-203">For more information, see [Estimating the Size of a Full Database Backup](#EstimateDbBuSize), later in this section.</span></span>  
  
####  <a name="estimate-the-size-of-a-full-database-backup"></a><a name="EstimateDbBuSize"></a><span data-ttu-id="cd94e-204">データベースの完全バックアップのサイズの見積もり</span><span class="sxs-lookup"><span data-stu-id="cd94e-204">Estimate the Size of a Full Database Backup</span></span>  
 <span data-ttu-id="cd94e-205">バックアップと復元のストラテジを実装する前に、データベースの完全バックアップで使用するディスク領域を推計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-205">Before you implement a backup and restore strategy, you should estimate how much disk space a full database backup will use.</span></span> <span data-ttu-id="cd94e-206">バックアップ操作では、データベース内のデータをバックアップ ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cd94e-206">The backup operation copies the data in the database to the backup file.</span></span> <span data-ttu-id="cd94e-207">バックアップにはデータベース内の実際のデータだけが入っており、未使用の領域は入っていません。</span><span class="sxs-lookup"><span data-stu-id="cd94e-207">The backup contains only the actual data in the database and not any unused space.</span></span> <span data-ttu-id="cd94e-208">そのため、通常、バックアップはデータベースそのものよりも小さくなります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-208">Therefore, the backup is usually smaller than the database itself.</span></span> <span data-ttu-id="cd94e-209">データベースの完全バックアップのサイズは、 **sp_spaceused** システム ストアド プロシージャを使用して推計することができます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-209">You can estimate the size of a full database backup by using the **sp_spaceused** system stored procedure.</span></span> <span data-ttu-id="cd94e-210">詳細については、「[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-210">For more information, see [sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql).</span></span>  
  
### <a name="schedule-backups"></a><span data-ttu-id="cd94e-211">バックアップのスケジュール</span><span class="sxs-lookup"><span data-stu-id="cd94e-211">Schedule Backups</span></span>  
 <span data-ttu-id="cd94e-212">バックアップの実行によって、実行中のトランザクションが受ける影響はわずかです。したがってバックアップは、通常の運用時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-212">Performing a backup operation has minimal effect on transactions that are running; therefore, backup operations can be run during regular operations.</span></span> <span data-ttu-id="cd94e-213">実稼働ワークロードへの影響は最小限にとどめて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-213">You can perform a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup with minimal effect on production workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd94e-214">バックアップ中のコンカレンシーの制限については、「[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-214">For information about concurrency restrictions during backup, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="cd94e-215">必要なバックアップの種類、および各種類のバックアップを実行する必要のある頻度を決定した後、データベースに対するデータベース メンテナンス プランの一部として、定期的なバックアップをスケジュールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd94e-215">After you decide what types of backups you require and how frequently you have to perform each type, we recommend that you schedule regular backups as part of a database maintenance plan for the database.</span></span> <span data-ttu-id="cd94e-216">メンテナンス プランと、データベース バックアップおよびログ バックアップ用のメンテナンス プランの作成方法については、「 [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd94e-216">For information about maintenance plans and how to create them for database backups and log backups, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
### <a name="test-your-backups"></a><span data-ttu-id="cd94e-217">バックアップのテスト</span><span class="sxs-lookup"><span data-stu-id="cd94e-217">Test Your Backups</span></span>  
 <span data-ttu-id="cd94e-218">バックアップをテストするまでは、復元ストラテジが完成したことにはなりません。</span><span class="sxs-lookup"><span data-stu-id="cd94e-218">You do not have a restore strategy until you have tested your backups.</span></span> <span data-ttu-id="cd94e-219">データベースのコピーをテスト システムに復元することで、各データベースに対するバックアップ ストラテジを十分にテストすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="cd94e-219">It is very important to thoroughly test your backup strategy for each of your databases by restoring a copy of the database onto a test system.</span></span> <span data-ttu-id="cd94e-220">使用するすべての種類のバックアップの復元をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-220">You must test restoring every type of backup that you intend to use.</span></span>  
  
 <span data-ttu-id="cd94e-221">データベースごとに操作マニュアルを用意しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd94e-221">We recommend that you maintain an operations manual for each database.</span></span> <span data-ttu-id="cd94e-222">この操作マニュアルには、バックアップの場所、バックアップ デバイス名 (ある場合)、およびテスト バックアップの復元に必要な時間を記載しておきます。</span><span class="sxs-lookup"><span data-stu-id="cd94e-222">This operations manual should document the location of the backups, backup device names (if any), and the amount of time that is required to restore the test backups.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cd94e-223">関連タスク</span><span class="sxs-lookup"><span data-stu-id="cd94e-223">Related Tasks</span></span>  
  
### <a name="scheduling-backup-jobs"></a><span data-ttu-id="cd94e-224">バックアップ ジョブのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="cd94e-224">Scheduling Backup Jobs</span></span>  
  
-   [<span data-ttu-id="cd94e-225">メンテナンス プランの作成</span><span class="sxs-lookup"><span data-stu-id="cd94e-225">Create a Maintenance Plan</span></span>](../maintenance-plans/create-a-maintenance-plan.md)  
  
-   [<span data-ttu-id="cd94e-226">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="cd94e-226">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="cd94e-227">ジョブのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="cd94e-227">Schedule a Job</span></span>](../../ssms/agent/schedule-a-job.md)  
  
### <a name="working-with-backup-devices-and-backup-media"></a><span data-ttu-id="cd94e-228">バックアップ デバイスとバックアップ メディアの操作</span><span class="sxs-lookup"><span data-stu-id="cd94e-228">Working with Backup Devices and Backup Media</span></span>  
  
-   [<span data-ttu-id="cd94e-229">ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-229">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-230">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-230">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-231">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-231">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-232">バックアップ デバイスの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-232">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-233">バックアップの有効期限の設定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-233">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-234">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-234">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-235">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-236">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-236">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-237">デバイスからのバックアップ復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-237">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
### <a name="creating-backups"></a><span data-ttu-id="cd94e-238">バックアップの作成</span><span class="sxs-lookup"><span data-stu-id="cd94e-238">Creating Backups</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd94e-239">部分バックアップまたはコピーのみのバックアップでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントにそれぞれ PARTIAL オプションまたは COPY_ONLY オプションを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd94e-239">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
 <span data-ttu-id="cd94e-240">**SQL Server Management Studio の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-240">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="cd94e-241">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-241">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-242">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-242">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-243">ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-243">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-244">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-244">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="cd94e-245">**Transact-SQL の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-245">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="cd94e-246">リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-246">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="cd94e-247">データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-247">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-248">バックアップ中または復元中にバックアップ チェックサムを有効または無効にする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-248">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-249">バックアップまたは復元の操作をエラー発生後に続行するか停止するかを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-249">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  

  
### <a name="restoring-data-backups"></a><span data-ttu-id="cd94e-250">データ バックアップの復元</span><span class="sxs-lookup"><span data-stu-id="cd94e-250">Restoring Data Backups</span></span>  
 <span data-ttu-id="cd94e-251">**SQL Server Management Studio の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-251">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="cd94e-252">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="cd94e-253">データベースを新しい場所に復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-253">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-254">データベースの差分バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-254">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-255">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-255">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
 <span data-ttu-id="cd94e-256">**Transact-SQL の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-256">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="cd94e-257">単純復旧モデルでのデータベース バックアップの復元 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-257">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="cd94e-258">完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-258">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="cd94e-259">既存のファイルにファイルとファイル グループを復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-259">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-260">新しい場所へのファイルの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-260">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-261">master データベースの復元 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-261">Restore the master Database &#40;Transact-SQL&#41;</span></span>](restore-the-master-database-transact-sql.md)  
  

  
### <a name="restoring-transaction-logs-full-recovery-model"></a><span data-ttu-id="cd94e-262">トランザクション ログを復元する (完全復旧モデル)</span><span class="sxs-lookup"><span data-stu-id="cd94e-262">Restoring Transaction Logs (Full Recovery Model)</span></span>  
 <span data-ttu-id="cd94e-263">**SQL Server Management Studio の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-263">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="cd94e-264">マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-264">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cd94e-265">トランザクション ログ バックアップの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-265">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="cd94e-266">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-266">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
 <span data-ttu-id="cd94e-267">**Transact-SQL の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-267">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="cd94e-268">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-268">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  

  
### <a name="additional-restore-tasks"></a><span data-ttu-id="cd94e-269">その他の復元タスク</span><span class="sxs-lookup"><span data-stu-id="cd94e-269">Additional Restore Tasks</span></span>  
 <span data-ttu-id="cd94e-270">**Transact-SQL の使用**</span><span class="sxs-lookup"><span data-stu-id="cd94e-270">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="cd94e-271">中断された復元操作の再開 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-271">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](restart-an-interrupted-restore-operation-transact-sql.md)  
  
-   [<span data-ttu-id="cd94e-272">データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-272">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="cd94e-273">参照</span><span class="sxs-lookup"><span data-stu-id="cd94e-273">See Also</span></span>  
 <span data-ttu-id="cd94e-274">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd94e-274">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="cd94e-275">[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd94e-275">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="cd94e-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd94e-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="cd94e-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd94e-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="cd94e-278">[Analysis Services データベースのバックアップと復元](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span><span class="sxs-lookup"><span data-stu-id="cd94e-278">[Backup and Restore of Analysis Services Databases](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span></span>  
 <span data-ttu-id="cd94e-279">[フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="cd94e-279">[Back Up and Restore Full-Text Catalogs and Indexes](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span></span>  
 <span data-ttu-id="cd94e-280">[レプリケートされたデータベースのバックアップと復元](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="cd94e-280">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="cd94e-281">[トランザクション ログ &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd94e-281">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="cd94e-282">[復旧モデル &#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd94e-282">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 [<span data-ttu-id="cd94e-283">メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd94e-283">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
