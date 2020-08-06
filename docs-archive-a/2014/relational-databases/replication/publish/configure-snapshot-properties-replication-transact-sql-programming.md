---
title: スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c7dd645fed073f73132c6993f12925a885a8e0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721296"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a><span data-ttu-id="15452-102">スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="15452-102">Configure Snapshot Properties (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="15452-103">スナップショットのプロパティは、レプリケーションのストアド プロシージャを使用し、プログラムから定義および変更できます。使用するストアド プロシージャは、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="15452-103">Snapshot properties can be defined and modified programmatically using replication stored procedures, where the stored procedures used depend on the type of publication.</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a><span data-ttu-id="15452-104">スナップショット パブリケーションまたはトランザクション パブリケーションを作成するときにスナップショットのプロパティを構成するには</span><span class="sxs-lookup"><span data-stu-id="15452-104">To configure snapshot properties when creating a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="15452-105">パブリッシャーで [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="15452-105">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="15452-106">にパブリケーション名を指定し **@publication** ます。には**snapshot**または**continuous**のいずれかの値を指定し、次の **@repl_freq** スナップショット関連のパラメーターを1つ以上指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-106">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="15452-107">**@alt_snapshot_folder**-このパブリケーションのスナップショットが、スナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-107">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="15452-108">**@compress_snapshot**-代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル形式で圧縮する場合は、値**true**を指定し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="15452-108">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB file format.</span></span>  
  
    -   <span data-ttu-id="15452-109">**@pre_snapshot_script**-初期スナップショットが適用される前に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-109">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-110">**@post_snapshot_script**-初期スナップショットが適用された後に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-110">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-111">**@snapshot_in_defaultfolder**-スナップショットを既定以外の場所でのみ使用できる場合は、 **false**の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-111">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
     <span data-ttu-id="15452-112">パブリケーションの作成の詳細については、「 [Create a Publication](create-a-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15452-112">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a><span data-ttu-id="15452-113">マージ パブリケーションを作成するときにスナップショットのプロパティを構成するには</span><span class="sxs-lookup"><span data-stu-id="15452-113">To configure snapshot properties when creating a merge publication</span></span>  
  
1.  <span data-ttu-id="15452-114">パブリッシャーで [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="15452-114">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="15452-115">にパブリケーション名を指定し **@publication** ます。には**snapshot**または**continuous**のいずれかの値を指定し、次の **@repl_freq** スナップショット関連のパラメーターを1つ以上指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-115">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="15452-116">**@alt_snapshot_folder**-このパブリケーションのスナップショットが、スナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-116">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="15452-117">**@compress_snapshot**-代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル形式で圧縮する場合は、値**true**を指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-117">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="15452-118">**@pre_snapshot_script**-初期スナップショットが適用される前に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-118">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-119">**@post_snapshot_script**-初期スナップショットが適用された後に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-119">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-120">**@snapshot_in_defaultfolder**-スナップショットを既定以外の場所でのみ使用できる場合は、 **false**の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-120">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="15452-121">パブリケーションの作成の詳細については、「 [Create a Publication](create-a-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15452-121">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a><span data-ttu-id="15452-122">既存のスナップショット パブリケーションまたはトランザクション パブリケーションに対してスナップショットのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="15452-122">To modify snapshot properties of an existing snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="15452-123">パブリッシャー側のパブリケーション データベースに対して [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="15452-123">At the Publisher on the publication database, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="15452-124">に**1**を指定し、 **@force_invalidate_snapshot** に次のいずれかの値を指定し **@property** ます。</span><span class="sxs-lookup"><span data-stu-id="15452-124">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="15452-125">**alt_snapshot_folder** -の代替スナップショットフォルダーへの新しいパスも指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="15452-125">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="15452-126">**compress_snapshot** -代替スナップショットフォルダー内のスナップショットファイルを**false** **true** **@value** CAB ファイル形式で圧縮するかどうかを示す true または false のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-126">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="15452-127">**pre_snapshot_script** - **@value** 初期スナップショットが適用される前に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-127">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-128">**post_snapshot_script** - **@value** 初期スナップショットが適用された後に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-128">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-129">**snapshot_in_defaultfolder** - スナップショットを既定の場所に格納するかどうかを **true** または **false** で指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-129">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="15452-130">(省略可) パブリッシャーのパブリケーション データベースで [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="15452-130">(Optional) At the Publisher on the publication database, execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql).</span></span> <span data-ttu-id="15452-131">を指定し、 **@publication** 1 つまたは複数のスケジュールまたはセキュリティ資格情報のパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="15452-131">Specify **@publication** and one or more of the scheduling or security credential parameters being changed.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="15452-132">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="15452-132">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="15452-133">スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="15452-133">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
3.  <span data-ttu-id="15452-134">コマンド プロンプトから [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) を実行するか、スナップショット エージェント ジョブを起動して新しいスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="15452-134">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="15452-135">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="15452-135">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a><span data-ttu-id="15452-136">既存のマージ パブリケーションに対してスナップショットのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="15452-136">To modify snapshot properties of an existing merge publication</span></span>  
  
1.  <span data-ttu-id="15452-137">パブリッシャー側のパブリケーション データベースに対して [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="15452-137">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="15452-138">に**1**を指定し、 **@force_invalidate_snapshot** に次のいずれかの値を指定し **@property** ます。</span><span class="sxs-lookup"><span data-stu-id="15452-138">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="15452-139">**alt_snapshot_folder** -の代替スナップショットフォルダーへの新しいパスも指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="15452-139">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="15452-140">**compress_snapshot** -代替スナップショットフォルダー内のスナップショットファイルを**false** **true** **@value** CAB ファイル形式で圧縮するかどうかを示す true または false のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-140">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="15452-141">**pre_snapshot_script** - **@value** 初期スナップショットが適用される前に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-141">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-142">**post_snapshot_script** - **@value** 初期スナップショットが適用された後に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-142">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="15452-143">**snapshot_in_defaultfolder** - スナップショットを既定の場所に格納するかどうかを **true** または **false** で指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-143">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="15452-144">コマンド プロンプトから [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) を実行するか、スナップショット エージェント ジョブを起動して新しいスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="15452-144">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="15452-145">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="15452-145">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15452-146">例</span><span class="sxs-lookup"><span data-stu-id="15452-146">Example</span></span>  
 <span data-ttu-id="15452-147">次の例では、代替スナップショット フォルダーと圧縮スナップショットを使用したパブリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="15452-147">This example creates a publication that uses an alternate snapshot folder and a compressed snapshot.</span></span>  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a><span data-ttu-id="15452-148">参照</span><span class="sxs-lookup"><span data-stu-id="15452-148">See Also</span></span>  
 <span data-ttu-id="15452-149">[代替スナップショットフォルダーの場所](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="15452-149">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="15452-150">[圧縮されたスナップショット](../compressed-snapshots.md) </span><span class="sxs-lookup"><span data-stu-id="15452-150">[Compressed Snapshots](../compressed-snapshots.md) </span></span>  
 <span data-ttu-id="15452-151">[スナップショットが適用される前および後のスクリプトの実行](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span><span class="sxs-lookup"><span data-stu-id="15452-151">[Execute Scripts Before and After the Snapshot Is Applied](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span></span>  
 <span data-ttu-id="15452-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="15452-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="15452-153">[FTP によるスナップショットの転送](../transfer-snapshots-through-ftp.md) </span><span class="sxs-lookup"><span data-stu-id="15452-153">[Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md) </span></span>  
 [<span data-ttu-id="15452-154">パブリケーションおよびアーティクルのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="15452-154">Change Publication and Article Properties</span></span>](change-publication-and-article-properties.md)  
  
  
