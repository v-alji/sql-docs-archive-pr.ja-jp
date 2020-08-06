---
title: バックアップからのトランザクションサブスクリプションの初期化 (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632336"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a><span data-ttu-id="f1919-102">トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="f1919-102">Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="f1919-103">トランザクション パブリケーションのサブスクリプションは通常、スナップショットを使用して初期化されますが、レプリケーション ストアド プロシージャを使用して、バックアップからサブスクリプションを初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1919-103">Although a subscription to a transactional publication is typically initialized with a snapshot, a subscription can be initialized from a backup using replication stored procedures.</span></span> <span data-ttu-id="f1919-104">詳細については、「 [スナップショットを使用しないトランザクション サブスクリプションの初期化](initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1919-104">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a><span data-ttu-id="f1919-105">トランザクション サブスクライバーをバックアップから初期化するには</span><span class="sxs-lookup"><span data-stu-id="f1919-105">To initialize a transactional subscriber from a backup</span></span>  
  
1.  <span data-ttu-id="f1919-106">既存のパブリケーションの場合は、パブリッシャーのパブリケーション データベースで [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) を実行して、バックアップから初期化する機能をパブリケーションがサポートしているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1919-106">For an existing publication, ensure that the publication supports the ability to initialize from backup by executing [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="f1919-107">結果セットの **allow_initialize_from_backup** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="f1919-107">Note the value of **allow_initialize_from_backup** in the result set.</span></span>  
  
    -   <span data-ttu-id="f1919-108">この値が **1**の場合、パブリケーションはこの機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f1919-108">If the value is **1**, the publication supports this functionality.</span></span>  
  
    -   <span data-ttu-id="f1919-109">この値が **0** の場合、パブリッシャー側のパブリケーション データベースに対して [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f1919-109">If the value is **0**, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="f1919-110">値には、 \*\* \@ プロパティ**に**allow_initialize_from_backup**を指定し、値にはを指定し `true` ます** \@ \*\*。</span><span class="sxs-lookup"><span data-stu-id="f1919-110">Specify a value of **allow_initialize_from_backup** for **\@property** and a value of `true` for **\@value**.</span></span>  
  
2.  <span data-ttu-id="f1919-111">新しいパブリケーションの場合、パブリッシャー側のパブリケーション データベースに対して [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f1919-111">For a new publication, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="f1919-112">Allow_initialize_from_backup には、の値を指定し `true` ます。 **allow_initialize_from_backup**</span><span class="sxs-lookup"><span data-stu-id="f1919-112">Specify a value of `true` for **allow_initialize_from_backup**.</span></span> <span data-ttu-id="f1919-113">詳しくは、「 [パブリケーションを作成](publish/create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f1919-113">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="f1919-114">サブスクライバー データの欠落を回避するために、 **sp_addpublication** で `@allow_initialize_from_backup = N'true'`を使用する場合は、常に `@immediate_sync = N'true'`を使用します。</span><span class="sxs-lookup"><span data-stu-id="f1919-114">To avoid missing subscriber data, when using **sp_addpublication** with `@allow_initialize_from_backup = N'true'`, always use `@immediate_sync = N'true'`.</span></span>  
  
3.  <span data-ttu-id="f1919-115">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) ステートメントを使用して、パブリケーション データベースのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1919-115">Create a backup of the publication database using the [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
4.  <span data-ttu-id="f1919-116">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを使用し、サブスクライバー上でバックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="f1919-116">Restore the backup on the Subscriber using the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
5.  <span data-ttu-id="f1919-117">パブリッシャー側のパブリケーション データベースに対して、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f1919-117">At the Publisher on the publication database, execute the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="f1919-118">次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1919-118">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="f1919-119">\*\* \@ sync_type\*\* - **backup を使用した初期化**の値。</span><span class="sxs-lookup"><span data-stu-id="f1919-119">**\@sync_type** - a value of **initialize with backup**.</span></span>  
  
    -   <span data-ttu-id="f1919-120">\*\* \@ backupdevicetype\*\* -バックアップデバイスの種類 (**論理**(既定)、**ディスク**、または**テープ**)。</span><span class="sxs-lookup"><span data-stu-id="f1919-120">**\@backupdevicetype** - the type of backup device: **logical** (default), **disk**, or **tape**.</span></span>  
  
    -   <span data-ttu-id="f1919-121">\*\* \@ backupdevicename\*\* -復元に使用する論理バックアップデバイスまたは物理バックアップデバイス。</span><span class="sxs-lookup"><span data-stu-id="f1919-121">**\@backupdevicename** - the logical or physical backup device to use for the restore.</span></span>  
  
         <span data-ttu-id="f1919-122">論理デバイスの場合は、 **sp_addumpdevice** を使ってデバイスを作成する際に指定したバックアップ デバイスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1919-122">For a logical device, specify the name of the backup device specified when **sp_addumpdevice** was used to create the device.</span></span>  
  
         <span data-ttu-id="f1919-123">物理デバイスの場合は、「 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` 」または「 `TAPE = '\\.\TAPE0'`」のように、完全なパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1919-123">For a physical device, specify a complete path and file name, such as `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` or `TAPE = '\\.\TAPE0'`.</span></span>  
  
    -   <span data-ttu-id="f1919-124">Optional\*\* \@ パスワード\*\*-バックアップセットの作成時に指定されたパスワード。</span><span class="sxs-lookup"><span data-stu-id="f1919-124">(Optional) **\@password** - a password that was provided when the backup set was created.</span></span>  
  
    -   <span data-ttu-id="f1919-125">Optional\*\* \@ mediapassword\*\* -メディアセットのフォーマット時に指定されたパスワード。</span><span class="sxs-lookup"><span data-stu-id="f1919-125">(Optional) **\@mediapassword** - a password that was provided when the media set was formatted.</span></span>  
  
    -   <span data-ttu-id="f1919-126">Optional\*\* \@ fileidhint\*\* -復元するバックアップセットの識別子。</span><span class="sxs-lookup"><span data-stu-id="f1919-126">(Optional) **\@fileidhint** - identifier for the backup set to be restored.</span></span> <span data-ttu-id="f1919-127">たとえば、 **1** はバックアップ メディアの 1 番目のバックアップ セットを示し、 **2** は 2 番目のバックアップ セットを示します。</span><span class="sxs-lookup"><span data-stu-id="f1919-127">For example, specifying **1** indicates the first backup set on the backup medium and **2** indicates the second backup set.</span></span>  
  
    -   <span data-ttu-id="f1919-128">(テープデバイスの場合は省略可能)\*\* \@ unload\*\* -復元が完了した後にテープをドライブからアンロードする場合は**1** (既定値) を、アンロードしない場合は**0**を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1919-128">(Optional for tape devices) **\@unload** - specify a value of **1** (default) if the tape should be unloaded from the drive after the restore is complete and **0** if it should not be unloaded.</span></span>  
  
6.  <span data-ttu-id="f1919-129">(省略可能) プル サブスクリプションの場合は、サブスクライバーのサブスクリプション データベースで [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) と [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f1919-129">(Optional) For a pull subscription, execute [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) and [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="f1919-130">詳細については、「 [プル サブスクリプションの作成](create-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f1919-130">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
7.  <span data-ttu-id="f1919-131">(省略可) ディストリビューション エージェントを起動します。</span><span class="sxs-lookup"><span data-stu-id="f1919-131">(Optional) Start the Distribution Agent.</span></span> <span data-ttu-id="f1919-132">詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) 」または「 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1919-132">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) or [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1919-133">参照</span><span class="sxs-lookup"><span data-stu-id="f1919-133">See Also</span></span>  
 <span data-ttu-id="f1919-134">[バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="f1919-134">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="f1919-135">SQL Server データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="f1919-135">Back Up and Restore of SQL Server Databases</span></span>](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
