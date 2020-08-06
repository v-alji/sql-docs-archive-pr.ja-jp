---
title: マージ アーティクル間の結合フィルターの定義および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- merge replication join filters [SQL Server replication]
- modifying filters, join
- join filters
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0770a17ce4c50c9c0e3b8728db85c0f9e80b555b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645517"
---
# <a name="define-and-modify-a-join-filter-between-merge-articles"></a><span data-ttu-id="eab60-102">マージ アーティクル間の結合フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="eab60-102">Define and Modify a Join Filter Between Merge Articles</span></span>
  <span data-ttu-id="eab60-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクル間の結合フィルターを定義および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eab60-103">This topic describes how to define and modify a join filter between merge articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="eab60-104">マージ レプリケーションでは結合フィルターがサポートされています。結合フィルターは、通常、テーブル分割を他の関連するテーブル アーティクルに拡張するために、パラメーター化されたフィルターと組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-104">Merge replication supports join filters, which are typically used in conjunction with parameterized filters to extend table partitioning to other related table articles.</span></span>  
  
 <span data-ttu-id="eab60-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="eab60-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eab60-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="eab60-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eab60-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eab60-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eab60-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="eab60-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="eab60-109">**マージ アーティクル間の結合フィルターを定義および変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="eab60-109">**To define and modify a join filter between merge articles, using:**</span></span>  
  
     [<span data-ttu-id="eab60-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eab60-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eab60-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eab60-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eab60-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="eab60-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eab60-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eab60-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eab60-114">結合フィルターを作成するには、パブリケーションに少なくとも 2 つの関連テーブルを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="eab60-114">To create a join filter, a publication must contain at least two related tables.</span></span> <span data-ttu-id="eab60-115">結合フィルターは、行フィルターを拡張したものです。そのため、結合を使用して行フィルターを別のテーブルに拡張するには、先に 1 つのテーブルの行フィルターを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eab60-115">A join filter extends a row filter; therefore you must define a row filter on one table before you can extend the filter with a join to another table.</span></span> <span data-ttu-id="eab60-116">結合フィルターを 1 つ定義すると、パブリケーションに追加の関連テーブルが含まれている場合、この結合フィルターは別の結合フィルターを使用して拡張できます。</span><span class="sxs-lookup"><span data-stu-id="eab60-116">After one join filter is defined, you can extend this join filter with another join filter if the publication contains additional related tables.</span></span>  
  
-   <span data-ttu-id="eab60-117">パブリケーションに対するサブスクリプションが初期化された後に、結合フィルターを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eab60-117">If you add, modify, or delete a join filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="eab60-118">プロパティ変更の要件の詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab60-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="eab60-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="eab60-119">Recommendations</span></span>  
  
-   <span data-ttu-id="eab60-120">結合フィルターは、一連のテーブルに対して手動で作成できます。また、テーブルに定義された外部キーと主キーのリレーションシップに基づいて、レプリケーションによって自動的に生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="eab60-120">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the relationships between foreign keys and primary keys defined on the tables.</span></span> <span data-ttu-id="eab60-121">一連の結合フィルターを自動的に生成する方法の詳細については、「[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)」(マージ アーティクル間で一連の結合フィルターを自動的に生成する (SQL Server Management Studio)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab60-121">For more information on generating a set of join filters automatically, see [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eab60-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="eab60-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="eab60-123">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、結合フィルターを定義、変更、または削除します。</span><span class="sxs-lookup"><span data-stu-id="eab60-123">Define, modify, and delete join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="eab60-124">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eab60-124">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-join-filter"></a><span data-ttu-id="eab60-125">結合フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="eab60-125">To define a join filter</span></span>  
  
1.  <span data-ttu-id="eab60-126">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内の既存の行フィルターまたは結合フィルターを選択します。</span><span class="sxs-lookup"><span data-stu-id="eab60-126">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select an existing row filter or join filter in the **Filtered Tables** pane.</span></span>  
  
2.  <span data-ttu-id="eab60-127">**[追加]** をクリックし、 **[選択したフィルターを拡張するために結合を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab60-127">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="eab60-128">JOIN ステートメントを作成します。 **[ビルダーを使用してステートメントを作成する]** または **[JOIN ステートメントを手動で作成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eab60-128">Create the join statement: select either **Use the builder to create the statement** or **Write the join the statement manually**.</span></span>  
  
    -   <span data-ttu-id="eab60-129">ビルダーの使用を選択した場合、グリッド内の列 ( **[結合]** 、 **[フィルター選択されたテーブルの列]** 、 **[演算子]** 、 **[結合テーブルの列]** ) を使用して JOIN ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="eab60-129">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span>  
  
         <span data-ttu-id="eab60-130">グリッド内の各列には、ドロップダウン コンボ ボックスが含まれており、2 つの列と 1 つの演算子 ( **=** 、 **<>** 、 **<=** 、 **\<**, **>=** 、 **>** 、 **[like]** ) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="eab60-130">Each column in the grid contains a drop-down combo box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, and **like**).</span></span> <span data-ttu-id="eab60-131">結果は **[プレビュー]** テキスト領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-131">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="eab60-132">結合に列のペアを複数個含める場合は、 **[結合]** 列から結合 (AND または OR) を選択し、さらに 2 つの列と 1 つの演算子を入力します。</span><span class="sxs-lookup"><span data-stu-id="eab60-132">If the join involves more than one pair of columns, select a conjunction (AND or OR) from the **Conjunction** column, and then enter two more columns and an operator.</span></span>  
  
    -   <span data-ttu-id="eab60-133">ステートメントを手動で作成する場合、 **[JOIN ステートメント]** テキスト領域に JOIN ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="eab60-133">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="eab60-134">**[フィルター選択されたテーブルの列]** ボックスと **[結合テーブルの列]** ボックスを使用して、 **[JOIN ステートメント]** テキスト領域に列をドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="eab60-134">Use the **Filtered table columns** list box and the **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="eab60-135">完成した JOIN ステートメントは、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-135">The complete join statement would appear like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         <span data-ttu-id="eab60-136">JOIN 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="eab60-136">The JOIN clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="eab60-137">結合オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="eab60-137">Specify join options:</span></span>  
  
    -   <span data-ttu-id="eab60-138">フィルター選択されたテーブル (親テーブル) 内での結合先の列が一意である場合は、 **[一意キー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eab60-138">If the column on which you join in the filtered table (the parent table) is unique, select **Unique key**.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="eab60-139">このオプションを選択すると、結合フィルターにおける子テーブルと親テーブルのリレーションシップが一対一または一対多となるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-139">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="eab60-140">子テーブル内で結合する列に制約があり、一意性が保証される場合にのみ、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="eab60-140">Only select this option if you have a constraint on the joining column in the child table that guarantees uniqueness.</span></span> <span data-ttu-id="eab60-141">このオプションを適切に設定しなかった場合、データを収束できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eab60-141">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="eab60-142">既定で、マージ レプリケーションでは同期中に行ごとに変化が処理されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-142">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="eab60-143">フィルター選択されたテーブルと結合されたテーブルの両方の行内の関連する変更を 1 つの単位として処理するには、 **[論理レコード]** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンのみ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="eab60-143">To have related changes in rows of both the filtered table and the joined table processed as a unit, select **Logical record** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions only).</span></span> <span data-ttu-id="eab60-144">このオプションは、論理レコードを使用するために必要なアーティクルとパブリケーションの要件が満たされている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="eab60-144">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="eab60-145">詳細については、「[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md)」(論理レコードによる関連行への変更のグループ化) の「Considerations for Using Logical Records」(論理レコードの使用についての注意点) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab60-145">For more information see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="eab60-146">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="eab60-146">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-join-filter"></a><span data-ttu-id="eab60-147">結合フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="eab60-147">To modify a join filter</span></span>  
  
1.  <span data-ttu-id="eab60-148">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab60-148">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="eab60-149">**[結合の編集]** ダイアログ ボックスで、フィルターを変更します。</span><span class="sxs-lookup"><span data-stu-id="eab60-149">In the **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-join-filter"></a><span data-ttu-id="eab60-150">結合フィルターを削除するには</span><span class="sxs-lookup"><span data-stu-id="eab60-150">To delete a join filter</span></span>  
  
1.  <span data-ttu-id="eab60-151">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eab60-151">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="eab60-152">削除する結合フィルター自体が他の結合によって拡張されている場合は、それらの結合も削除されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-152">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eab60-153">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="eab60-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="eab60-154">この手順では、親アーティクルのパラメーター化されたフィルターと、親アーティクルと子アーティクルの結合フィルターを組み合わせて使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eab60-154">These procedures show a parameterized filter on a parent article with join filters between this article and related child articles.</span></span> <span data-ttu-id="eab60-155">結合フィルターは、レプリケーションのストアド プロシージャを使用してプログラムから定義したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="eab60-155">Join filters can be defined and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-join-filter-to-extend-an-article-filter-to-related-articles-in-a-merge-publication"></a><span data-ttu-id="eab60-156">アーティクル フィルターをマージ パブリケーションの関連アーティクルに拡張する結合フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="eab60-156">To define a join filter to extend an article filter to related articles in a merge publication</span></span>  
  
1.  <span data-ttu-id="eab60-157">結合先アーティクル (親アーティクル) のフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="eab60-157">Define the filtering for the article being joined to, which is also known as the parent article.</span></span>  
  
    -   <span data-ttu-id="eab60-158">パラメーター化された行フィルターを使ったアーティクルのフィルター選択については、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eab60-158">For an article filtered using a parameterized row filter, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="eab60-159">静的行フィルターを使ったアーティクルのフィルター選択については、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eab60-159">For an article filtered using a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
2.  <span data-ttu-id="eab60-160">パブリッシャーのパブリケーション データベースで [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行し、関連アーティクル (パブリケーションの子アーティクル) を少なくとも 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="eab60-160">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define one or more related articles, which are also known as child articles, for the publication.</span></span> <span data-ttu-id="eab60-161">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab60-161">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="eab60-162">パブリッシャー側のパブリケーション データベースに対して、[sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="eab60-162">At the Publisher on the publication database, execute [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="eab60-163">を指定し **@publication** 、このフィルターの一意の名前をに、 **@filtername** 手順 2. で作成した子アーティクルの名前をに、結合先の親アーティクルの名前を、に次のいずれかの値を指定し **@article** **@join_articlename** **@join_unique_key** ます。</span><span class="sxs-lookup"><span data-stu-id="eab60-163">Specify **@publication**, a unique name for this filter for **@filtername**, the name of the child article created in step 2 for **@article**, the name of the parent article being joined to for **@join_articlename**, and one of the following values for **@join_unique_key**:</span></span>  
  
    -   <span data-ttu-id="eab60-164">**0** - 親アーティクルと子アーティクル間の多対一または多対多の結合を示します。</span><span class="sxs-lookup"><span data-stu-id="eab60-164">**0** - indicates a many-to-one or many-to-many join between the parent and child articles.</span></span>  
  
    -   <span data-ttu-id="eab60-165">**1** - 親アーティクルと子アーティクル間の一対一または一対多の結合を示します。</span><span class="sxs-lookup"><span data-stu-id="eab60-165">**1** - indicates a one-to-one or one-to-many join between the parent and child articles.</span></span>  
  
     <span data-ttu-id="eab60-166">これにより、2 つのアーティクル間の結合フィルターが定義されます。</span><span class="sxs-lookup"><span data-stu-id="eab60-166">This defines a join filter between the two articles.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="eab60-167">一意性を **@join_unique_key** 保証する親アーティクルの基になるテーブルの結合する列に制約がある場合にのみ、を**1**に設定します。</span><span class="sxs-lookup"><span data-stu-id="eab60-167">Only set **@join_unique_key** to **1** if you have a constraint on the joining column in the underlying table for the parent article that guarantees uniqueness.</span></span> <span data-ttu-id="eab60-168">**@join_unique_key**が**1**に設定されていない場合は、データの非収束が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eab60-168">If **@join_unique_key** is set to **1** incorrectly, non-convergence of data may occur.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="eab60-169">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="eab60-169">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="eab60-170">次の例では、マージ パブリケーションのアーティクルを定義しています。 `SalesOrderDetail` テーブルのアーティクルが、 `SalesOrderHeader` テーブルと比較されてフィルター選択されます (このテーブル自体が静的行フィルターを使ってフィルター選択されています)。</span><span class="sxs-lookup"><span data-stu-id="eab60-170">This example defines an article for a merge publication, where the `SalesOrderDetail` table article is filtered against the `SalesOrderHeader` table that is itself filtered using a static row filter.</span></span> <span data-ttu-id="eab60-171">詳しくは、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab60-171">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
 <span data-ttu-id="eab60-172">次の例では、マージ パブリケーションでアーティクル グループを定義しています。アーティクルは、 `Employee` テーブルと比較されて、一連の結合フィルターを使ってフィルター選択されます (このテーブル自体が、 [LoginID](/sql/t-sql/functions/host-name-transact-sql) 列の **HOST_NAME** の値に対するパラメーター化された行フィルターを使ってフィルター選択されています)。</span><span class="sxs-lookup"><span data-stu-id="eab60-172">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the value of [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) in the **LoginID** column.</span></span> <span data-ttu-id="eab60-173">詳しくは、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eab60-173">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
## <a name="see-also"></a><span data-ttu-id="eab60-174">参照</span><span class="sxs-lookup"><span data-stu-id="eab60-174">See Also</span></span>  
 <span data-ttu-id="eab60-175">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="eab60-175">[Join Filters](../merge/join-filters.md) </span></span>  
 <span data-ttu-id="eab60-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="eab60-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 <span data-ttu-id="eab60-177">[パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="eab60-177">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="eab60-178">[マージ レプリケーション用にパブリッシュされたデータのフィルター処理](../merge/filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="eab60-178">[Filter Published Data for Merge Replication](../merge/filter-published-data-for-merge-replication.md) </span></span>  
 <span data-ttu-id="eab60-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="eab60-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="eab60-180">[Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) </span><span class="sxs-lookup"><span data-stu-id="eab60-180">[Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) </span></span>  
 [<span data-ttu-id="eab60-181">マージ アーティクルのパラメーター化された行フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="eab60-181">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  
