---
title: データベース スナップショット (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- static database views
- snapshots [SQL Server database snapshots]
- source databases [SQL Server]
- snapshots [SQL Server database snapshots], about database snapshots
- database snapshots [SQL Server]
- read-only database views
- database snapshots [SQL Server], about database snapshots
ms.assetid: 00179314-f23e-47cb-a35c-da6f180f86d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a0fa9b6cee2287d4e6060d4cb39f34d909e7db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742214"
---
# <a name="database-snapshots-sql-server"></a><span data-ttu-id="a4829-102">データベース スナップショット (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a4829-102">Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="a4829-103">データベース スナップショットは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース ( *ソース データベース*) の読み取り専用の静的ビューです。</span><span class="sxs-lookup"><span data-stu-id="a4829-103">A database snapshot is a read-only, static view of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database (the *source database*).</span></span> <span data-ttu-id="a4829-104">データベース スナップショットには、そのスナップショットを作成した時点でのソース データベースに対するトランザクションが反映されています。</span><span class="sxs-lookup"><span data-stu-id="a4829-104">The database snapshot is transactionally consistent with the source database as of the moment of the snapshot's creation.</span></span> <span data-ttu-id="a4829-105">データベース スナップショットは、常にそのソース データベースと同じサーバー インスタンス上に存在します。</span><span class="sxs-lookup"><span data-stu-id="a4829-105">A database snapshot always resides on the same server instance as its source database.</span></span> <span data-ttu-id="a4829-106">ソース データベースが更新されると、データベース スナップショットが更新されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-106">As the source database is updated, the database snapshot is updated.</span></span> <span data-ttu-id="a4829-107">したがって、データベース スナップショットが長期間にわたって存在するほど、使用可能なディスク領域が使い尽くされる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a4829-107">Therefore, the longer a database snapshot exists, the more likely it is to use up its available disk space.</span></span>  
  
 <span data-ttu-id="a4829-108">1 つのソース データベースには複数のスナップショットが存在できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-108">Multiple snapshots can exist on a given source database.</span></span> <span data-ttu-id="a4829-109">各データベース スナップショットは、データベースの所有者によって明示的に削除されるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-109">Each database snapshot persists until it is explicitly dropped by the database owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4829-110">データベース スナップショットは、スナップショットのバックアップ、トランザクションのスナップショット分離、およびスナップショット レプリケーションとは無関係の機能です。</span><span class="sxs-lookup"><span data-stu-id="a4829-110">Database snapshots are unrelated to snapshot backups, snapshot isolation of transactions, or snapshot replication.</span></span>  
  
 <span data-ttu-id="a4829-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a4829-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="a4829-112">機能の概要</span><span class="sxs-lookup"><span data-stu-id="a4829-112">Feature Overview</span></span>](#FeatureOverview)  
  
-   [<span data-ttu-id="a4829-113">データベース スナップショットの利点</span><span class="sxs-lookup"><span data-stu-id="a4829-113">Benefits of Database Snapshots</span></span>](#Benefits)  
  
-   [<span data-ttu-id="a4829-114">用語と定義</span><span class="sxs-lookup"><span data-stu-id="a4829-114">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="a4829-115">データベース スナップショットの前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="a4829-115">Prerequisites for and Limitations on Database Snapshots</span></span>](#LimitationsRequirements)  
  
-   [<span data-ttu-id="a4829-116">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a4829-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="feature-overview"></a><a name="FeatureOverview"></a> <span data-ttu-id="a4829-117">機能の概要</span><span class="sxs-lookup"><span data-stu-id="a4829-117">Feature Overview</span></span>  
 <span data-ttu-id="a4829-118">データベース スナップショットは、データページ レベルで動作します。</span><span class="sxs-lookup"><span data-stu-id="a4829-118">Database snapshots operate at the data-page level.</span></span> <span data-ttu-id="a4829-119">ソース データベースのページをユーザーが初めて変更する前に、元のページがソース データベースからスナップショットにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a4829-119">Before a page of the source database is modified for the first time, the original page is copied from the source database to the snapshot.</span></span> <span data-ttu-id="a4829-120">スナップショットには元のページが格納され、スナップショットの作成時点におけるデータ レコードの状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-120">The snapshot stores the original page, preserving the data records as they existed when the snapshot was created.</span></span> <span data-ttu-id="a4829-121">初めて変更する各ページについて、同様の処理が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-121">The same process is repeated for every page that is being modified for the first time.</span></span> <span data-ttu-id="a4829-122">データベース スナップショットに対する読み取り操作では、その格納場所にかかわらず、常に元のデータ ページにアクセスすることになります。したがって、データベース スナップショットはユーザーには不変なものとして映ります。</span><span class="sxs-lookup"><span data-stu-id="a4829-122">To the user, a database snapshot appears never to change, because read operations on a database snapshot always access the original data pages, regardless of where they reside.</span></span>  
  
 <span data-ttu-id="a4829-123">コピーされた元のページを格納するために、スナップショットでは *スパース ファイル*が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-123">To store the copied original pages, the snapshot uses one or more *sparse files*.</span></span> <span data-ttu-id="a4829-124">スパース ファイルの最初の状態は、ユーザー データを一切含まず、ユーザー データ用のディスク領域も割り当てられていない空のファイルです。</span><span class="sxs-lookup"><span data-stu-id="a4829-124">Initially, a sparse file is an essentially empty file that contains no user data and has not yet been allocated disk space for user data.</span></span> <span data-ttu-id="a4829-125">スパース ファイルのサイズは、ソース データベースで更新されるページ数が増えるにつれて大きくなります。</span><span class="sxs-lookup"><span data-stu-id="a4829-125">As more and more pages are updated in the source database, the size of the file grows.</span></span> <span data-ttu-id="a4829-126">次の図は、2 つの対照的な更新パターンがスナップショットのサイズにどのような影響を与えるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a4829-126">The following figure illustrates the effects of two contrasting update patterns on the size of a snapshot.</span></span> <span data-ttu-id="a4829-127">更新パターン A は、スナップショットの有効期間に元のページの 30% しか更新されない環境を反映し、</span><span class="sxs-lookup"><span data-stu-id="a4829-127">Update pattern A reflects an environment in which only 30 percent of the original pages are updated during the life of the snapshot.</span></span> <span data-ttu-id="a4829-128">更新パターン B は、スナップショットの有効期間に元のページの 80% が更新される環境を反映しています。</span><span class="sxs-lookup"><span data-stu-id="a4829-128">Update pattern B reflects an environment in which 80 percent of the original pages are updated during the life of the snapshot.</span></span>  
  
 <span data-ttu-id="a4829-129">![更新の代替パターンとスナップショットのサイズ](../../database-engine/media/dbview-04.gif "更新の代替パターンとスナップショットのサイズ")</span><span class="sxs-lookup"><span data-stu-id="a4829-129">![Alternative update patterns and snapshot size](../../database-engine/media/dbview-04.gif "Alternative update patterns and snapshot size")</span></span>  
  
##  <a name="benefits-of-database-snapshots"></a><a name="Benefits"></a> <span data-ttu-id="a4829-130">データベース スナップショットの利点</span><span class="sxs-lookup"><span data-stu-id="a4829-130">Benefits of Database Snapshots</span></span>  
  
-   <span data-ttu-id="a4829-131">スナップショットはレポート生成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-131">Snapshots can be used for reporting purposes.</span></span>  
  
     <span data-ttu-id="a4829-132">クライアントは、データベース スナップショットをクエリできます。したがって、スナップショットを作成した時点のデータに基づいてレポートを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-132">Clients can query a database snapshot, which makes it useful for writing reports based on the data at the time of snapshot creation.</span></span>  
  
-   <span data-ttu-id="a4829-133">レポートの生成に関する履歴データを維持できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-133">Maintaining historical data for report generation.</span></span>  
  
     <span data-ttu-id="a4829-134">スナップショットを使用すると、データへのユーザー アクセスを特定の時点から延長することができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-134">A snapshot can extend user access to data from a particular point in time.</span></span> <span data-ttu-id="a4829-135">たとえば、特定の期間 (営業年度の四半期など) の終了時にデータベース スナップショットを作成しておけば、</span><span class="sxs-lookup"><span data-stu-id="a4829-135">For example, you can create a database snapshot at the end of a given time period (such as a financial quarter) for later reporting.</span></span> <span data-ttu-id="a4829-136">その後、これらのスナップショットに基づいて期間末レポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-136">You can then run end-of-period reports on the snapshot.</span></span> <span data-ttu-id="a4829-137">ディスク領域が十分にある場合は、期間末スナップショットを無期限に維持することも可能です。それによって、これらの期間の結果をクエリして、組織の業績を調べたりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a4829-137">If disk space permits, you can also maintain end-of-period snapshots indefinitely, allowing queries against the results from these periods; for example, to investigate organizational performance.</span></span>  
  
-   <span data-ttu-id="a4829-138">可用性の目的で維持しているミラー データベースを使用して、レポート作成に伴う負担を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-138">Using a mirror database that you are maintaining for availability purposes to offload reporting.</span></span>  
  
     <span data-ttu-id="a4829-139">データベース スナップショットをデータベース ミラーリングと共に使用すると、ミラー サーバー上のデータをレポートに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a4829-139">Using database snapshots with database mirroring permits you to make the data on the mirror server accessible for reporting.</span></span> <span data-ttu-id="a4829-140">また、ミラー データベースに対してクエリを実行すると、プリンシパル サーバー上のリソースを解放することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4829-140">Additionally, running queries on the mirror database can free up resources on the principal.</span></span> <span data-ttu-id="a4829-141">詳細については、「 [データベース ミラーリングとデータベース スナップショット &#40;SQL Server&#41;](database-snapshots-sql-server.md)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-141">For more information, see [Database Mirroring and Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a4829-142">管理者によるエラーからデータを保護できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-142">Safeguarding data against administrative error.</span></span>  
  
-   <span data-ttu-id="a4829-143">ソース データベースでユーザー エラーが発生したときは、特定のデータベース スナップショットの作成時の状態にソース データベースを戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-143">In the event of a user error on a source database, you can revert the source database to the state it was in when a given database snapshot was created.</span></span> <span data-ttu-id="a4829-144">失われるデータは、スナップショットの作成時点よりも後に行ったデータベースへの更新内容だけです。</span><span class="sxs-lookup"><span data-stu-id="a4829-144">Data loss is confined to updates to the database since the snapshot's creation.</span></span>  
  
     <span data-ttu-id="a4829-145">たとえば、一括更新やスキーマの変更などの大がかりな更新を実行する場合は、事前にデータベース スナップショットを作成しておくと、データを保護することができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-145">For example, before doing major updates, such as a bulk update or a schema change, create a database snapshot on the database protects data.</span></span> <span data-ttu-id="a4829-146">スナップショットを使用すると、更新を間違えた場合でも、データベースをスナップショットに戻すことによってデータを復旧できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-146">If you make a mistake, you can use the snapshot to recover by reverting the database to the snapshot.</span></span> <span data-ttu-id="a4829-147">この場合、データベースを元の状態に戻す方がバックアップから復元するよりも短時間で済みますが、後でロールフォワードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a4829-147">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a4829-148">オフラインのデータベースや破損したデータベースは元に戻せません。</span><span class="sxs-lookup"><span data-stu-id="a4829-148">Reverting does not work in an offline or corrupted database.</span></span> <span data-ttu-id="a4829-149">このため、データベースの保護には、定期的なバックアップと復元プランのテストが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4829-149">Therefore, taking regular backups and testing your restore plan are necessary to protect a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4829-150">データベース スナップショットはソース データベースに依存します。</span><span class="sxs-lookup"><span data-stu-id="a4829-150">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="a4829-151">したがって、データベース スナップショットを使用してデータベースを以前の状態に戻す方法は、バックアップおよび復元の代替にはなりません。</span><span class="sxs-lookup"><span data-stu-id="a4829-151">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="a4829-152">定期的なバックアップを毎回行うことが必要なことに変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="a4829-152">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="a4829-153">データベース スナップショットを作成した時点の状態にソース データベースを復元する必要がある場合は、そのためのバックアップ ポリシーを実装してください。</span><span class="sxs-lookup"><span data-stu-id="a4829-153">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="a4829-154">ユーザーによるエラーからデータを保護できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-154">Safeguarding data against user error.</span></span>  
  
     <span data-ttu-id="a4829-155">データベース スナップショットを定期的に作成すると、テーブルの削除など、ユーザーが重大な間違いを犯した場合にその影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-155">By creating database snapshots on a regular basis, you can mitigate the impact of a major user error, such as a dropped table.</span></span> <span data-ttu-id="a4829-156">ユーザーによる大半のエラーを認識し、それに対応できるよう、十分な長さの期間をカバーした一連のデータベース スナップショットを作成しておくと、データの保護レベルを高めることができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-156">For a high level of protection, you can create a series of database snapshots spanning enough time to recognize and respond to most user errors.</span></span> <span data-ttu-id="a4829-157">たとえば、ディスク リソースに応じて、24 時間間隔で作成されるスナップショットを 6 ～ 12 個維持しておき、</span><span class="sxs-lookup"><span data-stu-id="a4829-157">For instance, you might maintain 6 to 12 rolling snapshots spanning a 24-hour interval, depending on your disk resources.</span></span> <span data-ttu-id="a4829-158">新しいスナップショットが作成されるたびに、最も古いスナップショットが削除されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-158">Then, each time a new snapshot is created, the earliest snapshot can be deleted.</span></span>  
  
    -   <span data-ttu-id="a4829-159">ユーザー エラーが発生する直前のスナップショットにデータベースを戻すと、エラーから復旧することができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-159">To recover from a user error, you can revert the database to the snapshot immediately before the error.</span></span> <span data-ttu-id="a4829-160">この場合、データベースを元の状態に戻す方がバックアップから復元するよりも短時間で済みますが、後でロールフォワードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a4829-160">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    -   <span data-ttu-id="a4829-161">あるいは、スナップショットの情報を使用すると、削除されたテーブルやその他の紛失データを手動で再構築できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a4829-161">Alternatively, you may be able to manually reconstruct a dropped table or other lost data from the information in a snapshot.</span></span> <span data-ttu-id="a4829-162">たとえば、スナップショットのデータをデータベースに一括コピーして、データベースにデータを手動でマージすることができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-162">For instance, you could bulk copy the data out of the snapshot into the database and manually merge the data back into the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4829-163">データベースごとに必要な同時実行スナップショットの数、新規スナップショットを作成する頻度、およびスナップショットを保持する期間は、データベース スナップショットをどのような理由で使用するかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="a4829-163">Your reasons for using database snapshots determine how many concurrent snapshots you need on a database, how frequently to create a new snapshot, and how long to keep it.</span></span>  
  
-   <span data-ttu-id="a4829-164">テスト データベースの管理</span><span class="sxs-lookup"><span data-stu-id="a4829-164">Managing a test database</span></span>  
  
     <span data-ttu-id="a4829-165">テスト環境でテスト プロトコルを繰り返し実行する場合は、各テスト ラウンドを開始する際に同一のデータをデータベースに格納しておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="a4829-165">In a testing environment, it can be useful when repeatedly running a test protocol for the database to contain identical data at the start of each round of testing.</span></span> <span data-ttu-id="a4829-166">アプリケーション開発者やテスターは、最初のラウンドを実行する前に、テスト データベースのデータベース スナップショットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-166">Before running the first round, an application developer or tester can create a database snapshot on the test database.</span></span> <span data-ttu-id="a4829-167">各テストの実行が完了したら、データベース スナップショットを戻すことにより、データベースを元の状態にすばやく戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="a4829-167">After each test run, the database can be quickly returned to its prior state by reverting the database snapshot.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="a4829-168">用語と定義</span><span class="sxs-lookup"><span data-stu-id="a4829-168">Terms and Definitions</span></span>  
 <span data-ttu-id="a4829-169">データベース スナップショット (database snapshot)</span><span class="sxs-lookup"><span data-stu-id="a4829-169">database snapshot</span></span>  
 <span data-ttu-id="a4829-170">データベース (ソース データベース) の読み取り専用の静的なビュー。トランザクションの一貫性が確保されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-170">A transactionally consistent, read-only, static view of a database (the source database).</span></span>  
  
 <span data-ttu-id="a4829-171">ソース データベース</span><span class="sxs-lookup"><span data-stu-id="a4829-171">source database</span></span>  
 <span data-ttu-id="a4829-172">データベース スナップショットの場合、スナップショットの作成元となったデータベース。</span><span class="sxs-lookup"><span data-stu-id="a4829-172">For a database snapshot, the database on which the snapshot was created.</span></span> <span data-ttu-id="a4829-173">データベース スナップショットはソース データベースに依存します。</span><span class="sxs-lookup"><span data-stu-id="a4829-173">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="a4829-174">データベースのスナップショットは、データベースと同じサーバー インスタンス上に格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-174">The snapshots of a database must be on the same server instance as the database.</span></span> <span data-ttu-id="a4829-175">さらに、データベースがなんらかの理由で使用できなくなった場合、データベース スナップショットもすべて使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a4829-175">Furthermore, if that database becomes unavailable for any reason, all of its database snapshots also become unavailable.</span></span>  
  
 <span data-ttu-id="a4829-176">スパース ファイル (sparse file)</span><span class="sxs-lookup"><span data-stu-id="a4829-176">sparse file</span></span>  
 <span data-ttu-id="a4829-177">NTFS ファイル システムによって実現される、本来よりもはるかに少ないディスク領域しか必要としないファイル。</span><span class="sxs-lookup"><span data-stu-id="a4829-177">A file provided by the NTFS file system that requires much less disk space than would otherwise be needed.</span></span> <span data-ttu-id="a4829-178">スパース ファイルは、データベース スナップショットにコピーされたページを保存する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-178">A sparse file is used to store pages copied to a database snapshot.</span></span> <span data-ttu-id="a4829-179">作成したばかりのスパース ファイルは、ディスク領域をほとんど使用しません。</span><span class="sxs-lookup"><span data-stu-id="a4829-179">When first created, a sparse file takes up little disk space.</span></span> <span data-ttu-id="a4829-180">データがデータベース スナップショットに書き込まれるにつれて、NTFS によって、対応するスパース ファイルにディスク領域が徐々に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a4829-180">As data is written to a database snapshot, NTFS allocates disk space gradually to the corresponding sparse file.</span></span>  
  
##  <a name="prerequisites-for-and-limitations-on-database-snapshots"></a><a name="LimitationsRequirements"></a> <span data-ttu-id="a4829-181">データベース スナップショットの前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="a4829-181">Prerequisites for and Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="a4829-182">**このセクションの内容**</span><span class="sxs-lookup"><span data-stu-id="a4829-182">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="a4829-183">前提条件</span><span class="sxs-lookup"><span data-stu-id="a4829-183">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="a4829-184">ソース データベースへの制限</span><span class="sxs-lookup"><span data-stu-id="a4829-184">Limitations on the Source Database</span></span>](#LimitsOnSourceDb)  
  
-   [<span data-ttu-id="a4829-185">データベース スナップショットへの制限</span><span class="sxs-lookup"><span data-stu-id="a4829-185">Limitations on Database Snapshots</span></span>](#LimitsOnDbSS)  
  
-   [<span data-ttu-id="a4829-186">必要なディスク領域</span><span class="sxs-lookup"><span data-stu-id="a4829-186">Disk Space Requirements</span></span>](#DiskSpace)  
  
-   [<span data-ttu-id="a4829-187">オフライン ファイル グループを含むデータベース スナップショット</span><span class="sxs-lookup"><span data-stu-id="a4829-187">Database Snapshots with Offline Filegroups</span></span>](#OfflineFGs)  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a4829-188">前提条件</span><span class="sxs-lookup"><span data-stu-id="a4829-188">Prerequisites</span></span>  
 <span data-ttu-id="a4829-189">任意の復旧モデルを使用できるソース データベースは、次の前提条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-189">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="a4829-190">データベース スナップショットをサポートする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エディションでサーバー インスタンスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-190">The server instance must be running on an edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that supports database snapshots.</span></span> <span data-ttu-id="a4829-191">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a4829-191">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="a4829-192">ソース データベースは、データベース ミラーリング セッション内のミラー データベースである場合を除き、オンラインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-192">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="a4829-193">データベース スナップショットは、可用性グループ内の任意のプライマリ データベースまたはセカンダリ データベースに作成できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-193">You can create a database snapshot on any primary or secondary database in an availability group.</span></span> <span data-ttu-id="a4829-194">レプリカのロールは "プライマリ" または "セカンダリ" とし、"解決中" 状態でないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4829-194">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
     <span data-ttu-id="a4829-195">データベース スナップショットの作成は、データベースの同期状態が "同期中" または "同期済み" であるときに実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4829-195">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="a4829-196">ただし、データベースの同期状態が "同期されていません" であっても、データベース スナップショットを作成することはできます。</span><span class="sxs-lookup"><span data-stu-id="a4829-196">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
     <span data-ttu-id="a4829-197">詳細については、「[AlwaysOn 可用性グループを含むデータベース スナップショット &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4829-197">For more information, see [Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a4829-198">ミラー データベースにデータベース スナップショットを作成するには、データベースは "同期済み" のミラーリング状態になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-198">To create a database snapshot on a mirror database, the database must be in the SYNCHRONIZED mirroring state.</span></span>  
  
-   <span data-ttu-id="a4829-199">ソース データベースは、スケーラブルな共有データベースとして構成できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-199">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4829-200">すべての復旧モデルがデータベース スナップショットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a4829-200">All recovery models support database snapshots.</span></span>  
  
###  <a name="limitations-on-the-source-database"></a><a name="LimitsOnSourceDb"></a> <span data-ttu-id="a4829-201">ソース データベースへの制限</span><span class="sxs-lookup"><span data-stu-id="a4829-201">Limitations on the Source Database</span></span>  
 <span data-ttu-id="a4829-202">データベース スナップショットが存在する限り、スナップショットのソース データベースには次の制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-202">As long as a database snapshot exists, the following limitations exist on the snapshot's source database:</span></span>  
  
-   <span data-ttu-id="a4829-203">データベースは削除、デタッチ、または復元できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-203">The database cannot be dropped, detached, or restored.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4829-204">ソース データベースのバックアップは正常に実行されます。この動作はデータベース スナップショットの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="a4829-204">Backing up the source database works normally; it is unaffected by database snapshots.</span></span>  
  
-   <span data-ttu-id="a4829-205">ソース データベースでの I/O が増加することによって、パフォーマンスが低下します。これは、ページが更新されるたびにスナップショットに対して copy-on-write (書き込まれるたびにコピーする) 操作が実行されることが原因です。</span><span class="sxs-lookup"><span data-stu-id="a4829-205">Performance is reduced, due to increased I/O on the source database resulting from a copy-on-write operation to the snapshot every time a page is updated.</span></span>  
  
-   <span data-ttu-id="a4829-206">ソース データベースまたはスナップショットからはファイルを削除できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-206">Files cannot be dropped from the source database or from any snapshots.</span></span>  
  
###  <a name="limitations-on-database-snapshots"></a><a name="LimitsOnDbSS"></a> <span data-ttu-id="a4829-207">データベース スナップショットへの制限</span><span class="sxs-lookup"><span data-stu-id="a4829-207">Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="a4829-208">データベース スナップショットには、次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-208">The following limitations apply to database snapshots:</span></span>  
  
-   <span data-ttu-id="a4829-209">データベース スナップショットは、ソース データベースと同じサーバー インスタンスに作成および保持される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-209">A database snapshot must be created and remain on the same server instance as the source database.</span></span>  
  
-   <span data-ttu-id="a4829-210">データベース スナップショットは、常にデータベース全体に対して機能します。</span><span class="sxs-lookup"><span data-stu-id="a4829-210">Database snapshots always work on an entire database.</span></span>  
  
-   <span data-ttu-id="a4829-211">データベース スナップショットはソース データベースに依存するものであり、冗長ストレージではありません。</span><span class="sxs-lookup"><span data-stu-id="a4829-211">Database snapshots are dependent on the source database and are not redundant storage.</span></span> <span data-ttu-id="a4829-212">ディスク エラーやその他の種類の破損からは保護されません。</span><span class="sxs-lookup"><span data-stu-id="a4829-212">They do not protect against disk errors or other types of corruption.</span></span> <span data-ttu-id="a4829-213">したがって、データベース スナップショットを使用してデータベースを以前の状態に戻す方法は、バックアップおよび復元の代替にはなりません。</span><span class="sxs-lookup"><span data-stu-id="a4829-213">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="a4829-214">定期的なバックアップを毎回行うことが必要なことに変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="a4829-214">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="a4829-215">データベース スナップショットを作成した時点の状態にソース データベースを復元する必要がある場合は、そのためのバックアップ ポリシーを実装してください。</span><span class="sxs-lookup"><span data-stu-id="a4829-215">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="a4829-216">ソース データベースで更新されているページがスナップショットにプッシュされたときに、そのスナップショットによりディスク領域不足やその他のエラーが発生すると、そのスナップショットは問題ありに設定されるので、削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-216">When a page getting updated on the source database is pushed to a snapshot, if the snapshot runs out of disk space or encounters some other error, the snapshot becomes suspect and must be deleted.</span></span>  
  
-   <span data-ttu-id="a4829-217">スナップショットは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="a4829-217">Snapshots are read-only.</span></span> <span data-ttu-id="a4829-218">読み取り専用であるため、アップグレードできません。</span><span class="sxs-lookup"><span data-stu-id="a4829-218">Since they are read only, they cannot be upgraded.</span></span> <span data-ttu-id="a4829-219">したがって、データベース スナップショットはアップグレード後は利用不可と想定されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-219">Therefore, database snapshots are not expected to be viable after an upgrade.</span></span>  
  
-   <span data-ttu-id="a4829-220">**model**、 **master**、および **tempdb** の各データベースのスナップショットは禁止されています。</span><span class="sxs-lookup"><span data-stu-id="a4829-220">Snapshots of the **model**, **master**, and **tempdb** databases are prohibited.</span></span>  
  
-   <span data-ttu-id="a4829-221">データベース スナップショット ファイルの仕様は変更できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-221">You cannot change any of the specifications of the database snapshot files.</span></span>  
  
-   <span data-ttu-id="a4829-222">データベース スナップショットからはファイルを削除できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-222">You cannot drop files from a database snapshot.</span></span>  
  
-   <span data-ttu-id="a4829-223">データベース スナップショットはバックアップまたは復元できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-223">You cannot back up or restore database snapshots.</span></span>  
  
-   <span data-ttu-id="a4829-224">データベース スナップショットはアタッチまたはデタッチできません。</span><span class="sxs-lookup"><span data-stu-id="a4829-224">You cannot attach or detach database snapshots.</span></span>  
  
-   <span data-ttu-id="a4829-225">FAT32 ファイル システムまたは未処理のパーティションにはデータベース スナップショットを作成できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-225">You cannot create database snapshots on FAT32 file system or RAW partitions.</span></span> <span data-ttu-id="a4829-226">データベース スナップショットで使用されるスパース ファイルは NTFS ファイル システムによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-226">The sparse files used by database snapshots are provided by the NTFS file system.</span></span>  
  
-   <span data-ttu-id="a4829-227">データベース スナップショットではフルテキスト インデックスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a4829-227">Full-text indexing is not supported on database snapshots.</span></span> <span data-ttu-id="a4829-228">フルテキスト カタログはソース データベースから反映されません。</span><span class="sxs-lookup"><span data-stu-id="a4829-228">Full-text catalogs are not propagated from the source database.</span></span>  
  
-   <span data-ttu-id="a4829-229">データベース スナップショットでは、スナップショットの作成時にソース データベースのセキュリティ制約が継承されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-229">A database snapshot inherits the security constraints of its source database at the time of snapshot creation.</span></span> <span data-ttu-id="a4829-230">スナップショットは読み取り専用なので、継承された権限は変更できません。また、ソース データベースに加えられた権限の変更は、既存のスナップショットには反映されません。</span><span class="sxs-lookup"><span data-stu-id="a4829-230">Because snapshots are read-only, inherited permissions cannot be changed and permission changes made to the source will not be reflected in existing snapshots.</span></span>  
  
-   <span data-ttu-id="a4829-231">スナップショットには、常にスナップショットの作成時にファイル グループの状態が反映されます。オンライン ファイル グループはオンラインのまま、オフライン ファイル グループはオフラインのまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-231">A snapshot always reflects the state of filegroups at the time of snapshot creation: online filegroups remain online, and offline filegroups remain offline.</span></span> <span data-ttu-id="a4829-232">詳細については、このトピックの後半に記載されている「オフライン ファイル グループを含むデータベース スナップショット」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4829-232">For more information, see "Database Snapshots with Offline Filegroups" later in this topic.</span></span>  
  
-   <span data-ttu-id="a4829-233">ソース データベースが RECOVERY_PENDING になった場合、データベース スナップショットにアクセスできなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-233">If a source database becomes RECOVERY_PENDING, its database snapshots may become inaccessible.</span></span> <span data-ttu-id="a4829-234">ただし、ソース データベースの問題を解決した後は、スナップショットを再度利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a4829-234">After the issue on the source database is resolved, however, its snapshots should become available again.</span></span>  
  
-   <span data-ttu-id="a4829-235">元に戻す操作は、読み取り専用のファイル グループと圧縮されたファイル グループではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a4829-235">Reverting is unsupported for read-only filegroups and for compressed filegroups.</span></span> <span data-ttu-id="a4829-236">これらのいずれかの種類のファイル グループを含むデータベースを元に戻す操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="a4829-236">Attempts to revert a database containing either of these types of filegroups fail.</span></span>  
  
-   <span data-ttu-id="a4829-237">ログ配布構成では、データベース スナップショットを作成できるのはプライマリ データベースだけです。セカンダリ データベースでは作成できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-237">In a log shipping configuration, database snapshots can be created only on the primary database, not on a secondary database.</span></span> <span data-ttu-id="a4829-238">プライマリ サーバー インスタンスとセカンダリ サーバー インスタンスの役割を交代させる場合は、プライマリ データベースをセカンダリ データベースとしてセットアップする前にすべてのデータベース スナップショットを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-238">If you switch roles between the primary server instance and a secondary server instance, you must drop all the database snapshots before you can set the primary database up as a secondary database.</span></span>  
  
-   <span data-ttu-id="a4829-239">データベース スナップショットは、スケーラブルな共有データベースとして構成できません。</span><span class="sxs-lookup"><span data-stu-id="a4829-239">A database snapshot cannot be configured as a scalable shared database.</span></span>  
  
-   <span data-ttu-id="a4829-240">FILESTREAM ファイル グループは、データベース スナップショットではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a4829-240">FILESTREAM filegroups are not supported by database snapshots.</span></span> <span data-ttu-id="a4829-241">FILESTREAM ファイル グループがソース データベース内にある場合、それらはデータベース スナップショット内でオフラインとしてマークされ、データベースを元に戻す操作でデータベース スナップショットを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a4829-241">If FILESTREAM filegroups exist in a source database, they are marked as offline in its database snapshots, and the database snapshots cannot be used for reverting the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4829-242">データベース スナップショットで実行する SELECT ステートメントには、FILESTREAM 列を指定しないようにする必要があります。FILESTREAM 列が含まれていると、次のようなエラー メッセージが返されます。 `Could not continue scan with NOLOCK due to data movement.`</span><span class="sxs-lookup"><span data-stu-id="a4829-242">A SELECT statement that is executed on a database snapshot must not specify a FILESTREAM column; otherwise, the following error message will be returned: `Could not continue scan with NOLOCK due to data movement.`</span></span>  
  
-   <span data-ttu-id="a4829-243">読み取り専用スナップショットに関する統計が欠落しているか、古くなっている場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、tempdb に一時的な統計を作成して維持します。</span><span class="sxs-lookup"><span data-stu-id="a4829-243">When statistics on a read-only snapshot are missing or stale, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] creates and maintains temporary statistics in tempdb.</span></span> <span data-ttu-id="a4829-244">詳細については、[統計](../statistics/statistics.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4829-244">For more information, see [Statistics](../statistics/statistics.md).</span></span>  
  
###  <a name="disk-space-requirements"></a><a name="DiskSpace"></a> <span data-ttu-id="a4829-245">必要なディスク領域</span><span class="sxs-lookup"><span data-stu-id="a4829-245">Disk Space Requirements</span></span>  
 <span data-ttu-id="a4829-246">データベース スナップショットはディスク領域を消費します。</span><span class="sxs-lookup"><span data-stu-id="a4829-246">Database snapshots consume disk space.</span></span> <span data-ttu-id="a4829-247">データベース スナップショットによってディスク領域が足りなくなった場合、そのデータベース スナップショットは問題ありに設定されるので、削除する必要があります</span><span class="sxs-lookup"><span data-stu-id="a4829-247">If a database snapshot runs out of disk space, it is marked as suspect and must be dropped.</span></span> <span data-ttu-id="a4829-248">(ただし、ソース データベースは影響を受けず、操作は正常に続行されます)。しかし、データベースの完全なコピーと比較すると、スナップショットでは領域が非常に効率的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4829-248">(The source database, however, is not affected; actions on it continue normally.) Compared to a full copy of a database, however, snapshots are highly space efficient.</span></span> <span data-ttu-id="a4829-249">スナップショットにとって必要なのは、有効期間中に変化するページを格納する領域だけです。</span><span class="sxs-lookup"><span data-stu-id="a4829-249">A snapshot requires only enough storage for the pages that change during its lifetime.</span></span> <span data-ttu-id="a4829-250">通常はスナップショットが保持されている時間は限られているので、サイズはそれほど大きな問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="a4829-250">Generally, snapshots are kept for a limited time, so their size is not a major concern.</span></span>  
  
 <span data-ttu-id="a4829-251">ただし、スナップショットを保持する時間が長くなると、空き領域が消費される可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a4829-251">The longer you keep a snapshot, however, the more likely it is to use up available space.</span></span> <span data-ttu-id="a4829-252">スパース ファイルを拡張できる最大サイズは、スナップショットの作成時の対応するソース データベース ファイルのサイズです。</span><span class="sxs-lookup"><span data-stu-id="a4829-252">The maximum size to which a sparse file can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span>  
  
 <span data-ttu-id="a4829-253">データベース スナップショットによってディスク領域が足りなくなった場合は、データベース スナップショットを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-253">If a database snapshot runs out of disk space, it must be deleted (dropped).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4829-254">ファイル領域を除いて、データベース スナップショットはデータベースとほぼ同じくらいのリソースを消費します。</span><span class="sxs-lookup"><span data-stu-id="a4829-254">Except for file space, a database snapshot consumes roughly as many resources as a database.</span></span>  
  
###  <a name="database-snapshots-with-offline-filegroups"></a><a name="OfflineFGs"></a> <span data-ttu-id="a4829-255">オフライン ファイル グループを含むデータベース スナップショット</span><span class="sxs-lookup"><span data-stu-id="a4829-255">Database Snapshots with Offline Filegroups</span></span>  
 <span data-ttu-id="a4829-256">ソース データベース内のオフライン ファイル グループは、次の操作を実行しようとすると、データベース スナップショットに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="a4829-256">Offline filegroups in the source database affect database snapshots when you try to do any of the following:</span></span>  
  
-   <span data-ttu-id="a4829-257">スナップショットの作成</span><span class="sxs-lookup"><span data-stu-id="a4829-257">Create a snapshot</span></span>  
  
     <span data-ttu-id="a4829-258">ソース データベースに 1 つ以上のオフライン ファイル グループが含まれている場合、ファイル グループがオフラインのときは、スナップショットを正常に作成できます。</span><span class="sxs-lookup"><span data-stu-id="a4829-258">When a source database has one or more offline filegroups, snapshot creation succeeds with the filegroups offline.</span></span> <span data-ttu-id="a4829-259">オフライン ファイル グループの場合、スパース ファイルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="a4829-259">Sparse files are not created for the offline filegroups.</span></span>  
  
-   <span data-ttu-id="a4829-260">ファイル グループをオフラインにする</span><span class="sxs-lookup"><span data-stu-id="a4829-260">Take a filegroup offline</span></span>  
  
     <span data-ttu-id="a4829-261">ソース データベースのファイルはオフラインにできます。</span><span class="sxs-lookup"><span data-stu-id="a4829-261">You can take a file offline in the source database.</span></span> <span data-ttu-id="a4829-262">ただし、データベース スナップショットの作成時にオンラインだったファイル グループは、データベース スナップショットでもオンラインです。</span><span class="sxs-lookup"><span data-stu-id="a4829-262">However, the filegroup remains online in database snapshots if it was online when the snapshot was created.</span></span> <span data-ttu-id="a4829-263">クエリされたデータがスナップショットの作成時以降に変更された場合、スナップショットから元のデータ ページにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a4829-263">If the queried data has changed since snapshot creation, the original data page will be accessible in the snapshot.</span></span> <span data-ttu-id="a4829-264">ただし、ファイル グループ内の変更されていないデータへのアクセスにスナップショットを使用するクエリは、入出力 (I/O) エラーで失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-264">However, queries that use the snapshot to access unmodified data in the filegroup are likely to fail with input/output (I/O) errors.</span></span>  
  
-   <span data-ttu-id="a4829-265">ファイル グループをオンラインにする</span><span class="sxs-lookup"><span data-stu-id="a4829-265">Bring a filegroup online</span></span>  
  
     <span data-ttu-id="a4829-266">データベース スナップショットが存在するデータベースでファイル グループをオンラインにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a4829-266">You cannot bring a filegroup online in a database that has any database snapshots.</span></span> <span data-ttu-id="a4829-267">スナップショットの作成時にオフラインだったファイル グループや、データベース スナップショットが存在している間にオフラインにしたファイル グループは、オフラインのままになります。</span><span class="sxs-lookup"><span data-stu-id="a4829-267">If a filegroup is offline at the time of snapshot creation or is taken offline while a database snapshot exists, the filegroup remains offline.</span></span> <span data-ttu-id="a4829-268">これは、ファイルをオンラインに戻す際にファイルの復元が行われるためです。データベースにデータベース スナップショットが存在している場合、ファイルを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4829-268">This is because bringing a file back online involves restoring it, which is not possible if a database snapshot exists on the database.</span></span>  
  
-   <span data-ttu-id="a4829-269">ソース データベースをスナップショットに戻す</span><span class="sxs-lookup"><span data-stu-id="a4829-269">Revert the source database to the snapshot</span></span>  
  
     <span data-ttu-id="a4829-270">ソース データベースをデータベース スナップショットに戻すには、スナップショットの作成時にオフラインだったファイル グループを除くすべてのファイル グループがオンラインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4829-270">Reverting a source database to a database snapshot requires that all of the filegroups are online except for filegroups that were offline when the snapshot was created.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a4829-271">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a4829-271">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a4829-272">データベース スナップショットの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4829-272">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="a4829-273">データベース スナップショットの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4829-273">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="a4829-274">データベース スナップショットのスパース ファイルのサイズを表示する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4829-274">View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;</span></span>](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="a4829-275">データベースをデータベース スナップショットに戻す</span><span class="sxs-lookup"><span data-stu-id="a4829-275">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="a4829-276">データベース スナップショットの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4829-276">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4829-277">参照</span><span class="sxs-lookup"><span data-stu-id="a4829-277">See Also</span></span>  
 [<span data-ttu-id="a4829-278">データベース ミラーリングとデータベース スナップショット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4829-278">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
