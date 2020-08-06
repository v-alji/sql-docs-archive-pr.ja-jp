---
title: パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- partitions [SQL Server replication]
- merge replication partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], partition management
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 983b02865c0564919259f896bf09d8bdb0cd969f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631792"
---
# <a name="manage-partitions-for-a-merge-publication-with-parameterized-filters"></a><span data-ttu-id="4ee6a-102">パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理</span><span class="sxs-lookup"><span data-stu-id="4ee6a-102">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>
  <span data-ttu-id="4ee6a-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パラメーター化されたフィルターを利用し、マージ パブリケーションのパーティションを管理する方法ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-103">This topic describes how to manage partitions for a merge publication with parameterized filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="4ee6a-104">パラメーター化された行フィルターを使用して、重複しないパーティションを生成できます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-104">Parameterized row filters can be used to generate nonoverlapping partitions.</span></span> <span data-ttu-id="4ee6a-105">パーティションを制限することで、特定のパーティションを 1 つのサブスクリプションだけが受け取るようにできます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-105">These partitions can be restricted so that only one subscription receives a given partition.</span></span> <span data-ttu-id="4ee6a-106">このような場合、サブスクリプションの数が多いと多数のパーティションが生成されるため、それと同数のパーティション スナップショットが必要になります。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-106">In these cases, a large number of subscribers will result in a large number of partitions, which in turn requires an equal number of partitioned snapshots.</span></span> <span data-ttu-id="4ee6a-107">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="4ee6a-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4ee6a-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4ee6a-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4ee6a-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4ee6a-110">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="4ee6a-110">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="4ee6a-111">**パラメーター化されたフィルターによるマージ パブリケーションのパーティションを管理するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="4ee6a-111">**To manage partitions for a merge publication with parameterized filters, using:**</span></span>  
  
     [<span data-ttu-id="4ee6a-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4ee6a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4ee6a-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4ee6a-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4ee6a-114">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="4ee6a-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4ee6a-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="4ee6a-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4ee6a-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="4ee6a-116">Recommendations</span></span>  
  
-   <span data-ttu-id="4ee6a-117">レプリケーション トポロジをスクリプト化する場合 (推奨)、パブリケーション スクリプトには、データ パーティションを作成するためのストアド プロシージャの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-117">If you script a replication topology, which is recommended, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="4ee6a-118">このスクリプトによって、作成されたパーティションの参照、および必要に応じて 1 つ以上のパーティションを再作成する方法を利用できます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-118">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span> <span data-ttu-id="4ee6a-119">詳細については、「[レプリケーションのスクリプト作成](../scripting-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-119">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="4ee6a-120">パブリケーションが、重複しないパーティションを含むサブスクリプションを返すパラメーター化されたフィルターを持つ場合に、特定のサブスクリプションが失われて再作成が必要になったときは、サブスクライブされたパーティションを削除し、サブスクリプションを再作成してから、パーティションを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-120">When a publication has parameterized filters that yield subscriptions with nonoverlapping partitions, and if a particular subscription is lost and needs to be re-created, you must do the following: remove the partition that was subscribed to, re-create the subscription, and then re-create the partition.</span></span> <span data-ttu-id="4ee6a-121">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-121">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span> <span data-ttu-id="4ee6a-122">パブリケーション作成スクリプトが生成されると、レプリケーションによって既存のサブスクライバー パーティション用の作成スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-122">Replication generates creation scripts for existing Subscriber partitions when a publication creation script is generated.</span></span> <span data-ttu-id="4ee6a-123">詳細については、「[レプリケーションのスクリプト作成](../scripting-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-123">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4ee6a-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4ee6a-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4ee6a-125">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[データ パーティション]** ページでパーティションを管理します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-125">Manage partitions on the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="4ee6a-126">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-126">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="4ee6a-127">このページでは、パーティションを作成および削除する、サブスクライバーがスナップショットの生成および配信を開始できるようにする、1 つ以上のパーティションのスナップショットを生成する、スナップショットをクリーンアップするなどの操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-127">On this page you can: create and delete partitions; allow Subscribers to initiate snapshot generation and delivery; generate snapshots for one or more partitions; and clean up snapshots.</span></span>  
  
#### <a name="to-create-a-partition"></a><span data-ttu-id="4ee6a-128">パーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-128">To create a partition</span></span>  
  
1.  <span data-ttu-id="4ee6a-129">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[データ パーティション]** ページで **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-129">On the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="4ee6a-130">**[データ パーティションの追加]** ダイアログ ボックスで、作成するパーティションに関連する **HOST_NAME()** 値または **SUSER_SNAME()** 値、あるいはその両方を入力します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-130">In the **Add Data Partition** dialog box, enter a value for the **HOST_NAME()** and/or **SUSER_SNAME()** value associated with the partition you want to create.</span></span>  
  
3.  <span data-ttu-id="4ee6a-131">オプションでスナップショットの更新スケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-131">Optionally specify a schedule for refreshing snapshots:</span></span>  
  
    1.  <span data-ttu-id="4ee6a-132">**[以下のスケジュールでこのパーティションのスナップショット エージェントを実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-132">Select **Schedule the Snapshot Agent for this partition to run at the following time(s)**</span></span>  
  
    2.  <span data-ttu-id="4ee6a-133">スナップショットの既定の更新スケジュールをそのまま使用するか、または **[変更]** をクリックして別のスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-133">Accept the default schedule for refreshing snapshots, or click **Change** to specify a different schedule.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="4ee6a-134">パーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-134">To delete a partition</span></span>  
  
1.  <span data-ttu-id="4ee6a-135">**[データ パーティション]** ページのグリッドでパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-135">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="4ee6a-136">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-136">Click **Delete**.</span></span>  
  
#### <a name="to-allow-subscribers-to-initiate-snapshot-generation-and-delivery"></a><span data-ttu-id="4ee6a-137">サブスクライバーにスナップショットの生成と配信を許可するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-137">To allow Subscribers to initiate snapshot generation and delivery</span></span>  
  
1.  <span data-ttu-id="4ee6a-138">**[データ パーティション]** ページで、 **[新規サブスクライバーで同期を行うとき、パーティションを自動的に定義し、必要に応じてスナップショットを生成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-138">On the **Data Partitions** page, select **Automatically define a partition and generate a snapshot if needed when a new Subscriber tries to synchronize**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-generate-a-snapshot-for-a-partition"></a><span data-ttu-id="4ee6a-139">パーティションのスナップショットを生成するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-139">To generate a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="4ee6a-140">**[データ パーティション]** ページのグリッドでパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-140">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="4ee6a-141">**[今すぐ選択したスナップショットを生成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-141">Click **Generate the selected snapshots now**.</span></span>  
  
#### <a name="to-clean-up-a-snapshot-for-a-partition"></a><span data-ttu-id="4ee6a-142">パーティションのスナップショットをクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-142">To clean up a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="4ee6a-143">**[データ パーティション]** ページのグリッドでパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-143">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="4ee6a-144">**[既存のスナップショットをクリーンアップする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-144">Click **Clean up the existing snapshots**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4ee6a-145">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4ee6a-145">Using Transact-SQL</span></span>  
 <span data-ttu-id="4ee6a-146">パラメーター化されたフィルターを使ってパブリケーションをより詳細に管理するために、プログラムからレプリケーション ストアド プロシージャを使用して既存のパーティションを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-146">To better manage a publication with parameterized filters, you can programmatically enumerate the existing partitions using replication stored procedures.</span></span> <span data-ttu-id="4ee6a-147">既存のパーティションの作成と削除も行えます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-147">You can also create and delete existing partitions.</span></span> <span data-ttu-id="4ee6a-148">既存パーティションに関する次の情報も取得できます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-148">The following information on existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="4ee6a-149">パーティションのフィルター方法 ([SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) または [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) を使用)。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-149">How a partition is filtered (using [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) or [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)).</span></span>  
  
-   <span data-ttu-id="4ee6a-150">パーティション スナップショットを生成するジョブの名前</span><span class="sxs-lookup"><span data-stu-id="4ee6a-150">The name of the job that generates a partitioned snapshot.</span></span>  
  
-   <span data-ttu-id="4ee6a-151">パーティション スナップショット ジョブが最後に実行された時刻</span><span class="sxs-lookup"><span data-stu-id="4ee6a-151">The last time that a partitioned snapshot job ran.</span></span>  
  
 <span data-ttu-id="4ee6a-152">新しいサブスクリプションが初期化されたときに、2 つの部分から構成されるスナップショットの 2 番目の部分は要求時に生成できますが、下記の手順を実行することで、このスナップショットの生成方法を制御し、都合のよいときにこのスナップショットをあらかじめ生成できます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-152">While the second part of the two-part snapshot can be generated on-demand when a new subscription is initialized, the procedures below enable you to control how this snapshot is generated and to pre-generate this snapshot when it is most convenient.</span></span> <span data-ttu-id="4ee6a-153">詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-153">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="4ee6a-154">既存のパーティションに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-154">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="4ee6a-155">パブリッシャー側のパブリケーション データベースに対して、[sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-155">At the Publisher on the publication database, execute [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql).</span></span> <span data-ttu-id="4ee6a-156">\*\* \@ パブリケーション\*\*のパブリケーションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-156">Specify the name of the publication for **\@publication**.</span></span> <span data-ttu-id="4ee6a-157">Optional1つのフィルター条件に基づいて情報のみを返すには、 \*\* \@ suser_sname**または** \@ host_name\*\*を指定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-157">(Optional) Specify **\@suser_sname** or **\@host_name** to return only information based on a single filtering criterion.</span></span>  
  
#### <a name="to-define-a-new-partition-and-generate-a-new-partitioned-snapshot"></a><span data-ttu-id="4ee6a-158">新しいパーティションを定義して、新しいパーティション スナップショットを生成するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-158">To define a new partition and generate a new partitioned snapshot</span></span>  
  
1.  <span data-ttu-id="4ee6a-159">パブリッシャー側のパブリケーション データベースに対して、[sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-159">At the Publisher on the publication database, execute [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql).</span></span> <span data-ttu-id="4ee6a-160">\*\* \@ パブリケーション\*\*の名前と、次のいずれかのパーティションを定義するパラメーター化された値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-160">Specify the name of the publication for **\@publication**, and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="4ee6a-161">\*\* \@ suser_sname\*\* -パラメーター化されたフィルターが SUSER_SNAME によって返される値によって定義されている場合[&#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-161">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="4ee6a-162">\*\* \@ host_name\*\* -パラメーター化されたフィルターが HOST_NAME によって返される値によって定義されている場合[&#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-162">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
2.  <span data-ttu-id="4ee6a-163">この新しいパーティションのパラメーター化スナップショットを作成し、初期化します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-163">Create and initialize the parameterized snapshot for this new partition.</span></span> <span data-ttu-id="4ee6a-164">詳しくは、「 [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-164">For more information, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="4ee6a-165">パーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-165">To delete a partition</span></span>  
  
1.  <span data-ttu-id="4ee6a-166">パブリッシャー側のパブリケーション データベースに対して、[sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-166">At the Publisher on the publication database, execute [sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql).</span></span> <span data-ttu-id="4ee6a-167">\*\* \@ パブリケーション\*\*のパブリケーションの名前と、次のいずれかのパーティションを定義するパラメーター化された値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-167">Specify the name of the publication for **\@publication** and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="4ee6a-168">\*\* \@ suser_sname\*\* -パラメーター化されたフィルターが SUSER_SNAME によって返される値によって定義されている場合[&#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-168">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="4ee6a-169">\*\* \@ host_name\*\* -パラメーター化されたフィルターが HOST_NAME によって返される値によって定義されている場合[&#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-169">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
     <span data-ttu-id="4ee6a-170">これにより、そのパーティションのスナップショット ジョブおよびすべてのスナップショット ファイルも削除されます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-170">This also removes the snapshot job and any snapshot files for the partition.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4ee6a-171">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="4ee6a-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="4ee6a-172">パラメーター化されたフィルターを使ってパブリケーションをより適切に管理するために、レプリケーション管理オブジェクト (RMO) を使用して、新しいサブスクライバー パーティションの作成、既存のサブスクライバー パーティションの列挙、およびサブスクライバーの削除をプログラムで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-172">To better manage a publication with parameterized filters, you can programmatically create new Subscriber partitions, enumerate the existing Subscriber partitions, and delete Subscriber partitions by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="4ee6a-173">サブスクライバー パーティションを作成する方法の詳細については、「 [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-173">For information about how to create Subscriber partitions, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span> <span data-ttu-id="4ee6a-174">既存のパーティションに関する次の情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-174">The following information about existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="4ee6a-175">パーティションの基になる値およびフィルター関数。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-175">The value and filtering function upon which the partition is based.</span></span>  
  
-   <span data-ttu-id="4ee6a-176">サブスクライバーのパラメーター化されたスナップショットを生成するジョブの名前。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-176">The name of the job that generates a parameterized snapshot for the Subscriber.</span></span>  
  
-   <span data-ttu-id="4ee6a-177">パラメーター化されたスナップショット ジョブが最後に実行された日時。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-177">The last time that a parameterized snapshot job ran.</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="4ee6a-178">既存のパーティションに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-178">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="4ee6a-179"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-179">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4ee6a-180"><xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-180">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="4ee6a-181">パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-181">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="4ee6a-182"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4ee6a-183">このメソッドが `false` を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-183">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="4ee6a-184"><xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> メソッドを呼び出して、結果を <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトの配列に渡します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-184">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="4ee6a-185">配列内の各 <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトに対して、必要なプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-185">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, get any properties of interest.</span></span>  
  
#### <a name="to-delete-existing-partitions"></a><span data-ttu-id="4ee6a-186">既存のパーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="4ee6a-186">To delete existing partitions</span></span>  
  
1.  <span data-ttu-id="4ee6a-187"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4ee6a-188"><xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="4ee6a-189">パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-189">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="4ee6a-190"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4ee6a-191">このメソッドが `false` を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-191">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="4ee6a-192"><xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> メソッドを呼び出して、結果を <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトの配列に渡します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-192">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="4ee6a-193">配列内の各 <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトに対して、パーティションを削除するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-193">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, determine whether the partition should be deleted.</span></span> <span data-ttu-id="4ee6a-194">この決定は、通常、 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> プロパティまたは <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> プロパティの値に基づいて行います。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-194">This decision is usually based on the value of the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> property or the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> property.</span></span>  
  
6.  <span data-ttu-id="4ee6a-195">手順 2. の <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> オブジェクトで、 <xref:Microsoft.SqlServer.Replication.MergePublication> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-195">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> method on the <xref:Microsoft.SqlServer.Replication.MergePublication> object from step 2.</span></span> <span data-ttu-id="4ee6a-196">手順 5. の <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-196">Pass the <xref:Microsoft.SqlServer.Replication.MergePartition> object from step 5.</span></span>  
  
7.  <span data-ttu-id="4ee6a-197">削除する各パーティションに対して手順 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="4ee6a-197">Repeat step 6 for each partition that is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee6a-198">参照</span><span class="sxs-lookup"><span data-stu-id="4ee6a-198">See Also</span></span>  
 <span data-ttu-id="4ee6a-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="4ee6a-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="4ee6a-200">パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット</span><span class="sxs-lookup"><span data-stu-id="4ee6a-200">Snapshots for Merge Publications with Parameterized Filters</span></span>](../snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
