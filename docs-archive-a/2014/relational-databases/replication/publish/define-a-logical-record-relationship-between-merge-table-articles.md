---
title: マージ テーブル アーティクル間に論理レコード リレーションシップを定義する | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60c92a237562704e5bc5d43717f863aa78a14b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741786"
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a><span data-ttu-id="577ed-102">マージ テーブル アーティクル間に論理レコード リレーションシップを定義する</span><span class="sxs-lookup"><span data-stu-id="577ed-102">Define a Logical Record Relationship Between Merge Table Articles</span></span>
  <span data-ttu-id="577ed-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、マージ テーブル アーティクル間に論理レコード リレーションシップを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="577ed-103">This topic describes how to define a logical record relationship between merge table articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="577ed-104">マージ レプリケーションでは、さまざまなテーブルの関連する行の間にリレーションシップを定義できます。</span><span class="sxs-lookup"><span data-stu-id="577ed-104">Merge replication allows you to define a relationship between related rows in different tables.</span></span> <span data-ttu-id="577ed-105">これらの行は、同期の際にトランザクション単位として処理できます。</span><span class="sxs-lookup"><span data-stu-id="577ed-105">These rows can then be processed as a transactional unit during synchronization.</span></span> <span data-ttu-id="577ed-106">論理レコードは、2 つのアーティクルの間に定義できます。結合フィルター リレーションシップの有無は関係ありません。</span><span class="sxs-lookup"><span data-stu-id="577ed-106">A logical record can be defined between two articles whether or not they have a join filter relationship.</span></span> <span data-ttu-id="577ed-107">詳細については、「[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577ed-107">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="577ed-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="577ed-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="577ed-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="577ed-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="577ed-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="577ed-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="577ed-111">**マージ テーブル アーティクル間に論理レコード リレーションシップを定義するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="577ed-111">**To define a logical record relationship between merge table articles, using:**</span></span>  
  
     [<span data-ttu-id="577ed-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="577ed-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="577ed-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="577ed-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="577ed-114">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="577ed-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="577ed-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="577ed-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="577ed-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="577ed-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="577ed-117">パブリケーションに対するサブスクリプションが初期化された後に、論理レコードを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="577ed-117">If you add, modify, or delete a logical record after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="577ed-118">プロパティ変更の要件の詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="577ed-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="577ed-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="577ed-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="577ed-120">**[結合の追加]** ダイアログ ボックスで論理レコードを定義します。このダイアログ ボックスは、パブリケーションの新規作成ウィザードと **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="577ed-120">Define logical records in the **Add Join** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="577ed-121">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577ed-121">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="577ed-122">**[結合の追加]** ダイアログ ボックスで論理レコードを定義できるのは、マージ パブリケーションの結合フィルターに論理レコードが適用されている場合だけです。また、パブリケーションが、事前計算済みパーティションを使用するための要件を満たしている必要もあります。</span><span class="sxs-lookup"><span data-stu-id="577ed-122">Logical records can be defined in the **Add Join** dialog box only if they are applied to a join filter in a merge publication, and the publication follows the requirements for using precomputed partitions.</span></span> <span data-ttu-id="577ed-123">結合フィルターに適用されていない論理レコードを定義して、論理レコード レベルでの競合の検出と解決を設定するには、ストアド プロシージャを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="577ed-123">To define logical records that are not applied to join filters and to set conflict detection and resolution at the logical record level, you must use stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship"></a><span data-ttu-id="577ed-124">論理レコード リレーションシップを定義するには</span><span class="sxs-lookup"><span data-stu-id="577ed-124">To define a logical record relationship</span></span>  
  
1.  <span data-ttu-id="577ed-125">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内の行フィルターを選択します。</span><span class="sxs-lookup"><span data-stu-id="577ed-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a row filter in the **Filtered Tables** pane.</span></span>  
  
     <span data-ttu-id="577ed-126">論理レコード リレーションシップは、行フィルターを拡張する結合フィルターに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="577ed-126">A logical record relationship is associated with a join filter, which extends a row filter.</span></span> <span data-ttu-id="577ed-127">したがって、先に行フィルターが定義されていないと、行フィルターを結合で拡張して論理レコード リレーションシップを適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="577ed-127">Therefore you must define a row filter before you can extend the filter with a join and apply a logical record relationship.</span></span> <span data-ttu-id="577ed-128">1 つの結合フィルターが定義されると、この結合フィルターを別の結合フィルターを使用して拡張できます。</span><span class="sxs-lookup"><span data-stu-id="577ed-128">After one join filter is defined, you can extend this join filter with another join filter.</span></span> <span data-ttu-id="577ed-129">結合フィルターの定義の詳細については、「 [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577ed-129">For more information about defining join filters, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
2.  <span data-ttu-id="577ed-130">**[追加]** をクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="577ed-130">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="577ed-131">**[結合の追加]** ダイアログ ボックスで結合フィルターを定義してから、 **[論理レコード]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="577ed-131">Define a join filter in the **Add Join** dialog box, and then select the check box **Logical Record**.</span></span>  
  
4.  <span data-ttu-id="577ed-132">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="577ed-132">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-delete-a-logical-record-relationship"></a><span data-ttu-id="577ed-133">論理レコード リレーションシップを削除するには</span><span class="sxs-lookup"><span data-stu-id="577ed-133">To delete a logical record relationship</span></span>  
  
-   <span data-ttu-id="577ed-134">論理レコード リレーションシップのみを削除するか、または論理レコード リレーションシップとそれに関連付けられている結合フィルターを削除します。</span><span class="sxs-lookup"><span data-stu-id="577ed-134">Delete only the logical record relationship or delete the logical record relationship and the join filter associated with it.</span></span>  
  
     <span data-ttu-id="577ed-135">論理レコード リレーションシップのみを削除するには</span><span class="sxs-lookup"><span data-stu-id="577ed-135">To delete only the logical record relationship:</span></span>  
  
    1.  <span data-ttu-id="577ed-136">パブリケーションの新規作成ウィザードの **[行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内の論理レコード リレーションシップに関連付けられている結合フィルターを選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="577ed-136">On the **Filter Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select the join filter associated with the logical record relationship in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="577ed-137">**[結合の編集]** ダイアログ ボックスで、 **[論理レコード]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="577ed-137">In the **Edit Join** dialog box, clear the check box **Logical Record**.</span></span>  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="577ed-138">論理レコード リレーションシップとそれに関連付けられている結合フィルターを削除するには</span><span class="sxs-lookup"><span data-stu-id="577ed-138">To delete the logical record relationship and join filter associated with it:</span></span>  
  
    -   <span data-ttu-id="577ed-139">パブリケーションの新規作成ウィザードの **[行のフィルター選択]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="577ed-139">On the **Filter Rows** page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="577ed-140">削除する結合フィルター自体が他の結合によって拡張されている場合は、それらの結合も削除されます。</span><span class="sxs-lookup"><span data-stu-id="577ed-140">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="577ed-141">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="577ed-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="577ed-142">プログラムでレプリケーション ストアド プロシージャを使用して、アーティクル間に論理レコード リレーションシップを指定できます。</span><span class="sxs-lookup"><span data-stu-id="577ed-142">You can programmatically specify logical record relationships between articles using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="577ed-143">関連する結合フィルターを使用せずに論理レコード リレーションシップを定義するには</span><span class="sxs-lookup"><span data-stu-id="577ed-143">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="577ed-144">フィルター選択されたアーティクルがパブリケーションに含まれている場合、 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)を実行して、結果セットの **use_partition_groups** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="577ed-144">If the publication contains any articles that are filtered, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), and note the value of **use_partition_groups** in the result set.</span></span>  
  
    -   <span data-ttu-id="577ed-145">値が **1**の場合、事前計算済みパーティションが既に使用されています。</span><span class="sxs-lookup"><span data-stu-id="577ed-145">If the value is **1**, then precomputed partitions are already being used.</span></span>  
  
    -   <span data-ttu-id="577ed-146">値が **0**の場合、パブリッシャー側のパブリケーション データベースに対して [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-146">If the value is **0**, then execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="577ed-147">**@property** に **use_partition_groups** を指定し、**@value** に **true** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-147">Specify a value of **use_partition_groups** for **@property** and a value of **true** for **@value**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="577ed-148">パブリケーションで事前計算済みパーティションがサポートされない場合、論理レコードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="577ed-148">If the publication does not support precomputed partitions, then logical records cannot be used.</span></span> <span data-ttu-id="577ed-149">詳細については、[事前計算済みパーティションによるパラメーター化されたフィルター パフォーマンスの最適化](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)に関するページで、事前計算済みパーティションを使用するための要件をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="577ed-149">For more information, see Requirements for Using Precomputed Partitions in the topic [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="577ed-150">この値が NULL の場合、パブリケーションの初期スナップショットを生成するためにスナップショット エージェントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="577ed-150">If the value is NULL, then the Snapshot Agent needs to be run to generate the initial snapshot for the publication.</span></span>  
  
2.  <span data-ttu-id="577ed-151">論理レコードを構成するアーティクルが存在しない場合は、パブリッシャー側のパブリケーション データベースに対して [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-151">If the articles that will comprise the logical record do not exist, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="577ed-152">論理レコードの競合の検出と解決に関するオプションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-152">Specify one of the following conflict detection and resolution options for the logical record:</span></span>  
  
    -   <span data-ttu-id="577ed-153">論理レコードの関連する行で発生する競合を検出し、解決するには、 **@value** には **@logical_record_level_conflict_detection** 」および「 **@logical_record_level_conflict_resolution**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="577ed-153">To detect and resolve conflicts that occur within related rows in the logic record, specify a value of **true** for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**.</span></span>  
  
    -   <span data-ttu-id="577ed-154">標準の行レベルまたは列レベルの競合の検出と解決を使用するには、との値を指定し `false` **@logical_record_level_conflict_detection** **@logical_record_level_conflict_resolution** ます。これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="577ed-154">To use the standard row- or column-level conflict detection and resolution, specify a value of `false` for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**, which is the default.</span></span>  
  
3.  <span data-ttu-id="577ed-155">論理レコードを構成する各アーティクルに対して、手順 2. を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-155">Repeat step 2 for each article that will comprise the logical record.</span></span> <span data-ttu-id="577ed-156">論理レコード内の各アーティクルに使用する競合の検出および解決のオプションは、すべて同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="577ed-156">You must use the same conflict detection and resolution option for each article in the logical record.</span></span> <span data-ttu-id="577ed-157">詳しくは、「 [論理レコードの競合の検出および解決](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="577ed-157">For more information, see [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
4.  <span data-ttu-id="577ed-158">パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-158">At the publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="577ed-159">を指定し、リレーションシップ内の1つのアーティクルの名前をに、に2番目のアーティクルの名前を、にリレーションシップの名前を、に **@publication** **@article** **@join_articlename** **@filtername** 2 つのアーティクル間のリレーションシップを定義する句、に **@join_filterclause** 結合の種類を、に次のいずれかの **@join_unique_key** 値 **@filter_type** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-159">Specify **@publication**, the name of one article in the relationship for **@article**, the name of the second article for **@join_articlename**, a name for the relationship for **@filtername**, a clause that defines the relationship between the two articles for **@join_filterclause**, the type of join for **@join_unique_key** and one of the following values for **@filter_type**:</span></span>  
  
    -   <span data-ttu-id="577ed-160">**2** - 論理リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="577ed-160">**2** - Defines a logical relationship.</span></span>  
  
    -   <span data-ttu-id="577ed-161">**3** - 結合フィルターを使用した論理リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="577ed-161">**3** - Defines a logical relationship with a join filter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="577ed-162">結合フィルターを使用しない場合、2 つのアーティクル間のリレーションシップの方向はあまり重要でなくなります。</span><span class="sxs-lookup"><span data-stu-id="577ed-162">If a join filter is not used, the direction of the relationship between the two articles is not important.</span></span>  
  
5.  <span data-ttu-id="577ed-163">パブリケーションの他の論理レコード リレーションシップについても、手順 2. をそれぞれ実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-163">Repeat step 2 for each remaining logical record relationship in the publication.</span></span>  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a><span data-ttu-id="577ed-164">論理レコードにおける競合の検出と解決の方法を変更するには</span><span class="sxs-lookup"><span data-stu-id="577ed-164">To change conflict detection and resolution for logical records</span></span>  
  
1.  <span data-ttu-id="577ed-165">論理レコードの関連する行で発生する競合を検出し、解決するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-165">To detect and resolve conflicts that occur within related rows in the logical record:</span></span>  
  
    -   <span data-ttu-id="577ed-166">パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-166">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="577ed-167">**@property** に **logical_record_level_conflict_detection** を指定し、**@value** に **true** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-167">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="577ed-168">**@force_invalidate_snapshot** と **@force_reinit_subscription** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-168">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="577ed-169">パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-169">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="577ed-170">**@property** に **logical_record_level_conflict_resolution** を指定し、**@value** に **true** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-170">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="577ed-171">**@force_invalidate_snapshot** と **@force_reinit_subscription** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-171">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="577ed-172">標準の行レベルまたは列レベルの競合の検出と解決を使用するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-172">To use the standard row-level or column-level conflict detection and resolution:</span></span>  
  
    -   <span data-ttu-id="577ed-173">パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-173">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="577ed-174">に**logical_record_level_conflict_detection**の値を指定し、に値を指定し **@property** `false` **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="577ed-174">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="577ed-175">**@force_invalidate_snapshot** と **@force_reinit_subscription** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-175">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="577ed-176">パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-176">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="577ed-177">に**logical_record_level_conflict_resolution**の値を指定し、に値を指定し **@property** `false` **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="577ed-177">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="577ed-178">**@force_invalidate_snapshot** と **@force_reinit_subscription** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-178">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
#### <a name="to-remove-a-logical-record-relationship"></a><span data-ttu-id="577ed-179">論理レコード リレーションシップを削除するには</span><span class="sxs-lookup"><span data-stu-id="577ed-179">To remove a logical record relationship</span></span>  
  
1.  <span data-ttu-id="577ed-180">パブリッシャー側のパブリケーション データベースに対して次のクエリを実行し、指定されたパブリケーションに対して定義されているすべての論理レコード リレーションシップに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="577ed-180">At the Publisher on the publication database, execute the following query to return information about all logical record relationships defined for the specified publication:</span></span>  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_returnmergelogicalrecords)]  
  
     <span data-ttu-id="577ed-181">結果セット内の `filtername` 列で削除されている論理レコード リレーションシップの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="577ed-181">Note the name of the logical record relationship being removed in the `filtername` column in the result set.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="577ed-182">このクエリは、 [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql)と同じ情報を返します。ただし、このシステム ストアド プロシージャは、結合フィルターでもある論理レコード リレーションシップに関する情報のみ返します。</span><span class="sxs-lookup"><span data-stu-id="577ed-182">This query returns the same information as [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql); however, this system stored procedure only returns information about logical record relationships that are also join filters.</span></span>  
  
2.  <span data-ttu-id="577ed-183">パブリッシャー側のパブリケーション データベースに対して、 [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-183">At the Publisher on the publication database, execute [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql).</span></span> <span data-ttu-id="577ed-184">を指定し、 **@publication** リレーションシップ内のいずれかのアーティクルの名前をに指定し、 **@article** 手順 1. のリレーションシップの名前をに指定し **@filtername** ます。</span><span class="sxs-lookup"><span data-stu-id="577ed-184">Specify **@publication**, the name of one of the articles in the relationship for **@article**, and the name of the relationship from step 1 for **@filtername**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="577ed-185">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="577ed-185">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="577ed-186">この例では、既存のパブリケーションで事前計算済みパーティションを有効にし、 `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルの 2 つの新しいアーティクルを含む論理レコードを作成しています。</span><span class="sxs-lookup"><span data-stu-id="577ed-186">This example enables precomputed partitions on an existing publication, and creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_addmergelogicalrecord)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="577ed-187">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="577ed-187">Using Replication Management Objects (RMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="577ed-188">マージ レプリケーションを使用して、論理レコード レベルで追跡および解決する競合を指定できますが、これらのオプションは RMO を使用して設定できません。</span><span class="sxs-lookup"><span data-stu-id="577ed-188">Merge replication allows you to specify that conflicts be tracked and resolved at the logical record level, but these options cannot be set using RMO.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="577ed-189">関連する結合フィルターを使用せずに論理レコード リレーションシップを定義するには</span><span class="sxs-lookup"><span data-stu-id="577ed-189">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="577ed-190"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="577ed-190">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="577ed-191"><xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成し、パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティと <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定して、手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-191">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="577ed-192"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="577ed-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="577ed-193">このメソッドが `false` を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。</span><span class="sxs-lookup"><span data-stu-id="577ed-193">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="577ed-194"><xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> プロパティが <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>に設定されている場合、これを <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>に設定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-194">If the <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> property is set to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, set it to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.</span></span>  
  
5.  <span data-ttu-id="577ed-195">論理レコードを構成するアーティクルが存在しない場合は、 <xref:Microsoft.SqlServer.Replication.MergeArticle> クラスのインスタンスを作成し、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-195">If the articles that are to comprise the logical record do not exist, create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="577ed-196"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>にアーティクル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-196">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="577ed-197"><xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>にパブリケーション名を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-197">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="577ed-198">(省略可) アーティクルが行方向にフィルター選択される場合、 <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> プロパティに行フィルター句を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-198">(Optional) If the article is horizontally filtered, specify the row filter clause for the <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> property.</span></span> <span data-ttu-id="577ed-199">このプロパティを使用して、静的行フィルターまたはパラメーター化された行フィルターを指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-199">Use this property to specify a static or parameterized row filter.</span></span> <span data-ttu-id="577ed-200">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="577ed-200">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="577ed-201">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="577ed-201">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
6.  <span data-ttu-id="577ed-202"><xref:Microsoft.SqlServer.Replication.Article.Create%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="577ed-202">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span>  
  
7.  <span data-ttu-id="577ed-203">論理レコードを構成するアーティクルごとに、手順 5. と 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="577ed-203">Repeat steps 5 and 6 for each article comprising the logical record.</span></span>  
  
8.  <span data-ttu-id="577ed-204"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter> クラスのインスタンスを作成して、アーティクル間の論理レコード リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="577ed-204">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> class to define the logical record relationship between articles.</span></span> <span data-ttu-id="577ed-205">その後、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-205">Then, set the following properties:</span></span>  
  
    -   <span data-ttu-id="577ed-206"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> プロパティに論理レコード リレーションシップの子アーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-206">The name of the child article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="577ed-207"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> プロパティに論理レコード リレーションシップの既存の親アーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-207">The name of the existing, parent article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="577ed-208"><xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> プロパティに論理レコード リレーションシップの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-208">A name for the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> property.</span></span>  
  
    -   <span data-ttu-id="577ed-209">リレーションシップを定義する式を <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> プロパティに指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-209">The expression that defines the relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> property.</span></span>  
  
    -   <span data-ttu-id="577ed-210"><xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> の値を <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> プロパティに指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-210">A value of <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> property.</span></span> <span data-ttu-id="577ed-211">論理レコード リレーションシップが結合フィルターでもある場合は、このプロパティに <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="577ed-211">If the logical record relationship is also a join filter, specify a value of <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> for this property.</span></span> <span data-ttu-id="577ed-212">詳細については、「[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577ed-212">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
9. <span data-ttu-id="577ed-213">リレーションシップ内の子アーティクルを表すオブジェクトに対して <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="577ed-213">Call the <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> method on the object that represents the child article in the relationship.</span></span> <span data-ttu-id="577ed-214">手順 8. の <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> オブジェクトを渡して、リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="577ed-214">Pass the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> object from step 8 to define the relationship.</span></span>  
  
10. <span data-ttu-id="577ed-215">パブリケーションの他の論理レコード リレーションシップについても、手順 8. と 9. をそれぞれ実行します。</span><span class="sxs-lookup"><span data-stu-id="577ed-215">Repeat steps 8 and 9 for each remaining logical record relationship in the publication.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="577ed-216">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="577ed-216">Example (RMO)</span></span>  
 <span data-ttu-id="577ed-217">この例では、 `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルの 2 つの新しいアーティクルを含む論理レコードを作成しています。</span><span class="sxs-lookup"><span data-stu-id="577ed-217">This example creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a><span data-ttu-id="577ed-218">参照</span><span class="sxs-lookup"><span data-stu-id="577ed-218">See Also</span></span>  
 <span data-ttu-id="577ed-219">[マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="577ed-219">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="577ed-220">[マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="577ed-220">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="577ed-221">[静的行フィルターの定義と変更](define-and-modify-a-static-row-filter.md) </span><span class="sxs-lookup"><span data-stu-id="577ed-221">[Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) </span></span>  
 <span data-ttu-id="577ed-222">[論理レコードによる関連行への変更のグループ化](../merge/group-changes-to-related-rows-with-logical-records.md) </span><span class="sxs-lookup"><span data-stu-id="577ed-222">[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md) </span></span>  
 <span data-ttu-id="577ed-223">[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="577ed-223">[Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span></span>  
 [<span data-ttu-id="577ed-224">論理レコードによる関連行への変更のグループ化</span><span class="sxs-lookup"><span data-stu-id="577ed-224">Group Changes to Related Rows with Logical Records</span></span>](../merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
