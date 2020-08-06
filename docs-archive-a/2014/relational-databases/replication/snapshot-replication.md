---
title: スナップショット レプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], about snapshot replication
- snapshot replication [SQL Server]
ms.assetid: 5d745f22-9c6b-4e11-8c62-bc50e9a8bf38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6192c196e31c4c5772099074c79b3c6c4ca7aeed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743225"
---
# <a name="snapshot-replication"></a><span data-ttu-id="edf2d-102">スナップショット レプリケーション</span><span class="sxs-lookup"><span data-stu-id="edf2d-102">Snapshot Replication</span></span>
  <span data-ttu-id="edf2d-103">スナップショット レプリケーションでは、特定の時間に表示されていた状態のデータを配信します。データに対する更新は監視されません。</span><span class="sxs-lookup"><span data-stu-id="edf2d-103">Snapshot replication distributes data exactly as it appears at a specific moment in time and does not monitor for updates to the data.</span></span> <span data-ttu-id="edf2d-104">同期が発生するとデータ全体のスナップショットが作成され、サブスクライバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-104">When synchronization occurs, the entire snapshot is generated and sent to Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edf2d-105">スナップショット レプリケーションを単独で使用することもできますが、スナップショット処理 (パブリケーションで指定されたすべてのオブジェクトとデータのコピーを作成する処理) を使用して、トランザクション パブリケーションとマージ パブリケーション用にデータおよびデータベース オブジェクトの初期セットを提供することも一般的です。</span><span class="sxs-lookup"><span data-stu-id="edf2d-105">Snapshot replication can be used by itself, but the snapshot process (which creates a copy of all of the objects and data specified by a publication) is also commonly used to provide the initial set of data and database objects for transactional and merge publications.</span></span>  
  
 <span data-ttu-id="edf2d-106">次の条件に 1 つ以上当てはまる場合は、スナップショット レプリケーションを単独で使用する方法が最適です。</span><span class="sxs-lookup"><span data-stu-id="edf2d-106">Using snapshot replication by itself is most appropriate when one or more of the following is true:</span></span>  
  
-   <span data-ttu-id="edf2d-107">データの変更頻度が低い。</span><span class="sxs-lookup"><span data-stu-id="edf2d-107">Data changes infrequently.</span></span>  
  
-   <span data-ttu-id="edf2d-108">パブリッシャーで期限切れになったデータのコピーが一定の期間存在していても問題がない。</span><span class="sxs-lookup"><span data-stu-id="edf2d-108">It is acceptable to have copies of data that are out of date with respect to the Publisher for a period of time.</span></span>  
  
-   <span data-ttu-id="edf2d-109">レプリケートするデータの量が少ない。</span><span class="sxs-lookup"><span data-stu-id="edf2d-109">Replicating small volumes of data.</span></span>  
  
-   <span data-ttu-id="edf2d-110">短時間に大量の変更が発生する。</span><span class="sxs-lookup"><span data-stu-id="edf2d-110">A large volume of changes occurs over a short period of time.</span></span>  
  
 <span data-ttu-id="edf2d-111">データの変更が大量であるが頻度が低い場合は、スナップショット レプリケーションが最適です。</span><span class="sxs-lookup"><span data-stu-id="edf2d-111">Snapshot replication is most appropriate when data changes are substantial but infrequent.</span></span> <span data-ttu-id="edf2d-112">たとえば、販売組織が製品価格の一覧を保持しており、全価格が一年に一度か二度まとめて更新される場合、データ変更後に全体のスナップショットをレプリケートすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="edf2d-112">For example, if a sales organization maintains a product price list and the prices are all updated at the same time once or twice each year, replicating the entire snapshot of data after it has changed is recommended.</span></span> <span data-ttu-id="edf2d-113">特定の種類のデータのスナップショットが頻繁に発生する場合にも適しています。</span><span class="sxs-lookup"><span data-stu-id="edf2d-113">Given certain types of data, more frequent snapshots may also be appropriate.</span></span> <span data-ttu-id="edf2d-114">たとえば、比較的小さいテーブルが日中パブリッシャーで更新され、その更新を即時に反映しなくても問題ない場合に、変更を夜間にスナップショットとして配信することもできます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-114">For example, if a relatively small table is updated at the Publisher during the day, but some latency is acceptable, changes can be delivered nightly as a snapshot.</span></span>  
  
 <span data-ttu-id="edf2d-115">スナップショット レプリケーションでは、増分変更を追跡しないので、トランザクション レプリケーションと比べてパブリッシャー上で連続して発生するオーバーヘッドは小さくなります。</span><span class="sxs-lookup"><span data-stu-id="edf2d-115">Snapshot replication has a lower continuous overhead on the Publisher than transactional replication, because incremental changes are not tracked.</span></span> <span data-ttu-id="edf2d-116">ただし、レプリケートされるデータセットが大きい場合、スナップショットを生成して適用するために多くのリソースが必要となります。</span><span class="sxs-lookup"><span data-stu-id="edf2d-116">However, if the dataset set being replicated is very large, it will require substantial resources to generate and apply the snapshot.</span></span> <span data-ttu-id="edf2d-117">スナップショット レプリケーションの利用を検討する場合には、データセット全体のサイズとデータの変更頻度を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="edf2d-117">Consider the size of the entire data set and the frequency of changes to the data when evaluating whether to utilize snapshot replication.</span></span>  
  
 <span data-ttu-id="edf2d-118">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="edf2d-118">**In this topic**</span></span>  
  
 [<span data-ttu-id="edf2d-119">スナップショット レプリケーションの動作方法</span><span class="sxs-lookup"><span data-stu-id="edf2d-119">How Snapshot Replication Works</span></span>](#HowWorks)  
  
 [<span data-ttu-id="edf2d-120">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="edf2d-120">Snapshot Agent</span></span>](#SnapshotAgent)  
  
 [<span data-ttu-id="edf2d-121">ディストリビューション エージェントとマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="edf2d-121">Distribution and Merge Agents</span></span>](#DistAgent)  
  
##  <a name="how-snapshot-replication-works"></a><a name="HowWorks"></a> <span data-ttu-id="edf2d-122">スナップショット レプリケーションの動作方法</span><span class="sxs-lookup"><span data-stu-id="edf2d-122">How Snapshot Replication Works</span></span>  
 <span data-ttu-id="edf2d-123">既定では、3 種類のレプリケーションすべてでスナップショットを使用してサブスクライバーが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-123">By default, all three types of replication use a snapshot to initialize Subscribers.</span></span> <span data-ttu-id="edf2d-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スナップショット エージェントは、必ずスナップショット ファイルを生成しますが、ファイルを配信するエージェントは、使用するレプリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="edf2d-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Snapshot Agent always generates the snapshot files, but the agent that delivers the files differs depending on the type of replication being used.</span></span> <span data-ttu-id="edf2d-125">スナップショット レプリケーションとトランザクション レプリケーションでは、ディストリビューション エージェントを使用してファイルが配信されますが、マージ レプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] マージ エージェントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-125">Snapshot replication and transactional replication use the Distribution Agent to deliver the files, whereas merge replication uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Merge Agent.</span></span> <span data-ttu-id="edf2d-126">スナップショット エージェントはディストリビューター側で実行されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-126">The Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="edf2d-127">ディストリビューション エージェントとマージ エージェントは、プッシュ サブスクリプションの場合はディストリビューター側で、プル サブスクリプションの場合はサブスクライバー側で実行されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-127">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, or at Subscribers for pull subscriptions.</span></span>  
  
 <span data-ttu-id="edf2d-128">スナップショットは、サブスクリプションの作成直後、またはパブリケーションの作成時に設定したスケジュールに従って生成および適用できます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-128">Snapshots can be generated and applied either immediately after the subscription is created or according to a schedule set at the time the publication is created.</span></span> <span data-ttu-id="edf2d-129">スナップショット エージェントは、パブリッシュされたテーブルやデータベース オブジェクトのスキーマとデータを含むスナップショット ファイルを作成し、ファイルをパブリッシャーのスナップショット フォルダーに格納して、追跡情報をディストリビューターのディストリビューション データベースに記録します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-129">The Snapshot Agent prepares snapshot files containing the schema and data of published tables and database objects, stores the files in the snapshot folder for the Publisher, and records tracking information in the distribution database on the Distributor.</span></span> <span data-ttu-id="edf2d-130">ディストリビューターを構成する際に既定のスナップショットフォルダーを指定しますが、既定のフォルダーを代替または追加する場所として、パブリケーションに対して代替位置を指定できます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-130">You specify a default snapshot folder when you configure a Distributor, but you can specify an alternate location for a publication instead of or in addition to the default.</span></span>  
  
 <span data-ttu-id="edf2d-131">このトピックで説明する標準のスナップショット処理の他に、パラメーター化されたフィルターを使用したマージ パブリケーションでは、2 段階のスナップショット処理が使用されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-131">In addition to the standard snapshot process described in this topic, a two-part snapshot process is used for merge publications with parameterized filters.</span></span>  
  
 <span data-ttu-id="edf2d-132">次の図に、スナップショット レプリケーションの主要なコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-132">The following illustration shows the principal components of snapshot replication.</span></span>  
  
 <span data-ttu-id="edf2d-133">![スナップショット レプリケーション コンポーネントとデータ フロー](media/snapshot.gif "スナップショット レプリケーション コンポーネントとデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="edf2d-133">![Snapshot replication components and data flow](media/snapshot.gif "Snapshot replication components and data flow")</span></span>  
  
##  <a name="snapshot-agent"></a><a name="SnapshotAgent"></a> <span data-ttu-id="edf2d-134">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="edf2d-134">Snapshot Agent</span></span>  
 <span data-ttu-id="edf2d-135">マージ レプリケーションの場合は、スナップショット エージェントが起動するたびにスナップショットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-135">For merge replication, a snapshot is generated every time the Snapshot Agent runs.</span></span> <span data-ttu-id="edf2d-136">トランザクション レプリケーションでは、スナップショットの生成はパブリケーション プロパティ **immediate_sync**の設定で決まります。</span><span class="sxs-lookup"><span data-stu-id="edf2d-136">For transactional replication, snapshot generation depends on the setting of the publication property **immediate_sync**.</span></span> <span data-ttu-id="edf2d-137">プロパティが TRUE に設定されていると (パブリケーションの新規作成ウィザードを使用する際の既定の設定)、スナップショット エージェントを実行するたびにスナップショットが生成され、いつでもスナップショットをサブスクライバーに適用できます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-137">If the property is set to TRUE (the default when using the New Publication Wizard), a snapshot is generated every time the Snapshot Agent runs, and it can be applied to a Subscriber at any time.</span></span> <span data-ttu-id="edf2d-138">プロパティが FALSE に設定されていると ( **sp_addpublication**を使用する場合の既定の設定)、最後にスナップショット エージェントを実行してから新しいサブスクリプションが追加された場合にのみスナップショットが生成されます。サブスクライバーは、スナップショット エージェントが完了するまで同期することはできません。</span><span class="sxs-lookup"><span data-stu-id="edf2d-138">If the property is set to FALSE (the default when using **sp_addpublication**), the snapshot is generated only if a new subscription has been added since the last Snapshot Agent run; Subscribers must wait for the Snapshot Agent to complete before they can synchronize.</span></span>  
  
 <span data-ttu-id="edf2d-139">スナップショット エージェントは以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-139">The Snapshot Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="edf2d-140">ディストリビューターからパブリッシャーへの接続を確立し、必要に応じてパブリッシュされたテーブルのロックを設定します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-140">Establishes a connection from the Distributor to the Publisher, and then takes locks on published tables if necessary:</span></span>  
  
    -   <span data-ttu-id="edf2d-141">マージ パブリケーションの場合、スナップショット エージェントはロックを設定しません。</span><span class="sxs-lookup"><span data-stu-id="edf2d-141">For merge publications, the Snapshot Agent does not take any locks.</span></span>  
  
    -   <span data-ttu-id="edf2d-142">トランザクション パブリケーションの場合、既定では、スナップショット生成の初期フェーズの間だけロックを設定します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-142">For transactional publications, by default the Snapshot Agent take locks only during the initial phase of snapshot generation.</span></span>  
  
    -   <span data-ttu-id="edf2d-143">スナップショット パブリケーションの場合は、スナップショット生成処理の間中ロックが保持されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-143">For snapshot publications, locks are held during the entire snapshot generation process.</span></span>  
  
2.  <span data-ttu-id="edf2d-144">各アーティクルに対するテーブル スキーマのコピーを .sch ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-144">Writes a copy of the table schema for each article to a .sch file.</span></span> <span data-ttu-id="edf2d-145">インデックス、制約、ストアド プロシージャ、ビュー、ユーザー定義関数などの他のデータベース オブジェクトがパブリッシュされている場合は、追加のスクリプト ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-145">If other database objects are published, such as indexes, constraints, stored procedures, views, user-defined functions, and so on, additional script files are generated.</span></span>  
  
3.  <span data-ttu-id="edf2d-146">パブリッシュされたテーブルのデータをパブリッシャーでコピーし、スナップショット フォルダーにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-146">Copies the data from the published table at the Publisher and writes the data to the snapshot folder.</span></span> <span data-ttu-id="edf2d-147">スナップショットは、一連の一括コピー プログラム (BCP) ファイルとして生成されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-147">The snapshot is generated as a set of bulk copy program (BCP) files.</span></span>  
  
4.  <span data-ttu-id="edf2d-148">スナップショット パブリケーションとトランザクション パブリケーションの場合、ディストリビューション データベース内の **MSrepl_commands** テーブルと **MSrepl_transactions** テーブルに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-148">For snapshot and transactional publications, the Snapshot Agent appends rows to the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database.</span></span> <span data-ttu-id="edf2d-149">**MSrepl_commands** テーブル中のエントリは、.sch ファイルと .bcp ファイル、その他のスナップショット ファイルの場所を示すコマンドと、スナップショットの作成前後に実行するスクリプトへの参照です。</span><span class="sxs-lookup"><span data-stu-id="edf2d-149">The entries in the **MSrepl_commands** table are commands indicating the location of .sch and .bcp files, any other snapshot files, and references to any pre- or post-snapshot scripts.</span></span> <span data-ttu-id="edf2d-150">**MSrepl_transactions** テーブル内のエントリは、サブスクライバーの同期に関連するコマンドです。</span><span class="sxs-lookup"><span data-stu-id="edf2d-150">The entries in the **MSrepl_transactions** table are commands relevant to synchronizing the Subscriber.</span></span>  
  
     <span data-ttu-id="edf2d-151">マージ パブリケーションの場合は、スナップショット エージェントで実行する手順が追加されます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-151">For merge publications, the Snapshot Agent performs additional steps.</span></span>  
  
5.  <span data-ttu-id="edf2d-152">パブリッシュされたテーブルのすべてのロックを解放します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-152">Releases any locks on published tables.</span></span>  
  
 <span data-ttu-id="edf2d-153">スナップショットの生成中に、パブリッシュされたテーブルのスキーマを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="edf2d-153">During snapshot generation, you cannot make schema changes on published tables.</span></span> <span data-ttu-id="edf2d-154">スナップショット ファイルが生成されると、Windows エクスプローラーを使用して、スナップショット フォルダーにあるそれらのファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="edf2d-154">After the snapshot files are generated, you can view them in the snapshot folder using Windows Explorer.</span></span>  
  
##  <a name="distribution-agent-and-merge-agent"></a><a name="DistAgent"></a> <span data-ttu-id="edf2d-155">ディストリビューション エージェントとマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="edf2d-155">Distribution Agent and Merge Agent</span></span>  
 <span data-ttu-id="edf2d-156">スナップショット パブリケーションの場合、そのパブリケーションに対してディストリビューション エージェントが起動するたびに、まだ同期されておらず、再初期化のマークが付いているか新しいアーティクルを含む各サブスクライバーへ、新しいスナップショットを移動します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-156">For snapshot publications, each time the Distribution Agent runs for the publication, it moves a new snapshot to each Subscriber that has not yet been synchronized, has been marked for reinitialization, or includes new articles.</span></span>  
  
 <span data-ttu-id="edf2d-157">スナップショット レプリケーションとトランザクション レプリケーションの場合、ディストリビューション エージェントは以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-157">For snapshot and transactional replication, the Distribution Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="edf2d-158">ディストリビューターへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-158">Establishes a connection to the Distributor.</span></span>  
  
2.  <span data-ttu-id="edf2d-159">ディストリビューターのディストリビューション データベースにある **MSrepl_commands** テーブルと **MSrepl_transactions** テーブルを調査します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-159">Examines the **MSrepl_commands** and **MSrepl_transactions** tables in the distribution database on the Distributor.</span></span> <span data-ttu-id="edf2d-160">最初のテーブルからスナップショット ファイルの位置を読み取り、両方のテーブルからサブスクライバー同期コマンドを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="edf2d-160">The agent reads the location of the snapshot files from the first table and Subscriber synchronization commands from both tables.</span></span>  
  
3.  <span data-ttu-id="edf2d-161">スキーマとコマンドをサブスクリプション データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-161">Applies the schema and commands to the subscription database.</span></span>  
  
 <span data-ttu-id="edf2d-162">フィルター選択されていないマージ レプリケーション パブリケーションの場合、マージ エージェントは以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-162">For an unfiltered merge replication publication, the Merge Agent performs the following steps:</span></span>  
  
1.  <span data-ttu-id="edf2d-163">パブリッシャーへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-163">Establishes a connection to the Publisher.</span></span>  
  
2.  <span data-ttu-id="edf2d-164">パブリッシャー上の **sysmergeschemachange** テーブルを調べ、サブスクライバーで適用する必要のある新しいスナップショットがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-164">Examines the **sysmergeschemachange** table on the Publisher and determines whether there is a new snapshot that should be applied at the Subscriber.</span></span>  
  
3.  <span data-ttu-id="edf2d-165">新しいスナップショットを利用できる場合、 **sysmergeschemachange**で指定された位置のスナップショット ファイルをサブスクリプション データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="edf2d-165">If a new snapshot is available, the Merge Agent applies to the subscription database the snapshot files from the location specified in **sysmergeschemachange**.</span></span>  
  
  
