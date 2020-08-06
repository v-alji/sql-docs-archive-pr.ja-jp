---
title: 静的行フィルターの定義および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying filters, static row
- static row filters
- filters [SQL Server replication], static row
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d13fd93b6afdcce6b55e9b181f52087fd620913c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633075"
---
# <a name="define-and-modify-a-static-row-filter"></a><span data-ttu-id="77413-102">静的行フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="77413-102">Define and Modify a Static Row Filter</span></span>
  <span data-ttu-id="77413-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、静的行フィルターを定義および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="77413-103">This topic describes how to define and modify a static row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="77413-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="77413-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="77413-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="77413-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="77413-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="77413-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="77413-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="77413-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="77413-108">**静的行フィルターを定義または変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="77413-108">**To define and modify a static row filter, using:**</span></span>  
  
     [<span data-ttu-id="77413-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="77413-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="77413-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="77413-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="77413-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="77413-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="77413-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="77413-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="77413-113">パブリケーションに対するサブスクリプションが初期化された後に、静的行フィルターを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77413-113">If you add, modify, or delete a static row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="77413-114">プロパティ変更の要件の詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
-   <span data-ttu-id="77413-115">パブリケーションでピア ツー ピア トランザクション レプリケーションが有効な場合、テーブルはフィルター選択できません。</span><span class="sxs-lookup"><span data-stu-id="77413-115">If the publication is enabled for peer-to-peer transactional replication, tables cannot be filtered.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="77413-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="77413-116">Recommendations</span></span>  
  
-   <span data-ttu-id="77413-117">フィルターが静的であるため、すべてのサブスクライバーは同じデータのサブセットを受け取ることになります。</span><span class="sxs-lookup"><span data-stu-id="77413-117">Because these filters are static, all subscribers will receive the same subset of the data.</span></span> <span data-ttu-id="77413-118">マージ パブリケーションに属しているテーブルのアーティクルから行を動的にフィルター選択して、各サブスクライバーが異なるデータ パーティションを受け取るようにする場合は、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-118">If you need to dynamically filter rows in a table article belonging to a merge publication so that each subscriber receives a different partition of the data, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span> <span data-ttu-id="77413-119">マージ レプリケーションでは、既存の行フィルターに基づいて、関連する行をフィルター選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="77413-119">Merge replication also enables you to filter related rows based on an existing row filter.</span></span> <span data-ttu-id="77413-120">詳しくは、「 [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-120">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="77413-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="77413-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="77413-122">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、静的行フィルターを定義、変更、削除します。</span><span class="sxs-lookup"><span data-stu-id="77413-122">Define, modify, and delete static row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="77413-123">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter"></a><span data-ttu-id="77413-124">静的行フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="77413-124">To define a static row filter</span></span>  
  
1.  <span data-ttu-id="77413-125">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで行う操作は、パブリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="77413-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, the action you take depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="77413-126">スナップショット パブリケーションまたはトランザクション パブリケーションの場合は、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77413-126">For a snapshot or transactional publication, click **Add**.</span></span>  
  
    -   <span data-ttu-id="77413-127">マージ パブリケーションの場合は、 **[追加]** をクリックしてから **[フィルターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77413-127">For a merge publication, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="77413-128">**[フィルターの追加]** ダイアログ ボックスで、ドロップダウン リスト ボックスからフィルター選択するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="77413-128">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="77413-129">**[フィルター ステートメント]** テキスト領域で、フィルター ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="77413-129">Create a filter statement in the **Filter statement** text area.</span></span> <span data-ttu-id="77413-130">テキスト領域に直接入力することも、 **[列]** ボックスから列をドラッグ アンド ドロップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="77413-130">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77413-131">WHERE 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="77413-131">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span> <span data-ttu-id="77413-132">パブリケーションが Oracle パブリッシャーからのものである場合、WHERE 句は Oracle の構文に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77413-132">If the publication is from an Oracle Publisher, the WHERE clause must be compliant with Oracle syntax.</span></span>  
  
    -   <span data-ttu-id="77413-133">**[フィルター ステートメント]** テキスト領域には、次の形式の既定のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77413-133">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="77413-134">既定のテキストは変更できません。標準の SQL 構文を使用して WHERE キーワードの後にフィルター句を入力してください。</span><span class="sxs-lookup"><span data-stu-id="77413-134">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="77413-135">完成したフィルター句は、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="77413-135">The complete filter clause would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   <span data-ttu-id="77413-136">静的行フィルターには、ユーザー定義関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="77413-136">A static row filter can include a user-defined function.</span></span> <span data-ttu-id="77413-137">ユーザー定義関数を指定して完成した静的行フィルターのフィルター句は、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="77413-137">The complete filter clause for a static row filter with a user-defined function would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="77413-138">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="77413-138">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-static-row-filter"></a><span data-ttu-id="77413-139">静的行フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="77413-139">To modify a static row filter</span></span>  
  
1.  <span data-ttu-id="77413-140">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77413-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="77413-141">**[フィルターの編集]** ダイアログ ボックスで、フィルターを変更します。</span><span class="sxs-lookup"><span data-stu-id="77413-141">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-static-row-filter"></a><span data-ttu-id="77413-142">静的行フィルターを削除するには</span><span class="sxs-lookup"><span data-stu-id="77413-142">To delete a static row filter</span></span>  
  
1.  <span data-ttu-id="77413-143">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77413-143">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="77413-144">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="77413-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="77413-145">テーブルのアーティクルを作成するとき、WHERE 句を定義することで、アーティクルから特定の行をフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="77413-145">When creating table articles, you can define a WHERE clause to filter rows out of an article.</span></span> <span data-ttu-id="77413-146">いったん行フィルターを定義した後で、そのフィルターを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="77413-146">You can also change a row filter after it has been defined.</span></span> <span data-ttu-id="77413-147">静的行フィルターは、レプリケーションのストアド プロシージャを使用してプログラムから作成したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="77413-147">Static row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="77413-148">スナップショット パブリケーションまたはトランザクション パブリケーションの静的行フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="77413-148">To define a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="77413-149">フィルターを適用するアーティクルを定義します。</span><span class="sxs-lookup"><span data-stu-id="77413-149">Define the article to filter.</span></span> <span data-ttu-id="77413-150">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-150">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="77413-151">パブリッシャー側のパブリケーション データベースに対して、[sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-151">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="77413-152">**\@article**、 **\@publication**、 **\@filter_name**、 **\@filter_clause** に、それぞれアーティクル名、パブリケーション名、フィルター名、フィルター句 (`WHERE` は含めない) を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-152">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the filter for **\@filter_name**, and the filtering clause for **\@filter_clause** (not including `WHERE`).</span></span>  
  
3.  <span data-ttu-id="77413-153">列フィルターも定義する必要がある場合は、「 [列フィルターの定義および変更](define-and-modify-a-column-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-153">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span> <span data-ttu-id="77413-154">それ以外の場合、[sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-154">Otherwise, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="77413-155">**\@publication** にパブリケーション名を、 **\@article** にフィルター選択の対象アーティクル名を、 **\@filter_clause** に手順 2 で指定したフィルター句を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-155">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 2 for **\@filter_clause**.</span></span> <span data-ttu-id="77413-156">これにより、フィルターを適用するアーティクルの同期オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="77413-156">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="77413-157">スナップショット パブリケーションまたはトランザクション パブリケーションの静的行フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="77413-157">To modify a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="77413-158">パブリッシャー側のパブリケーション データベースに対して、[sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-158">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="77413-159">**\@article**、 **\@publication**、 **\@filter_name**、 **\@filter_clause** に、それぞれアーティクル名、パブリケーション名、新しいフィルター名、新しいフィルター句 (`WHERE` は含めない) を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-159">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the new filter for **\@filter_name**, and the new filtering clause for **\@filter_clause** (not including `WHERE`).</span></span> <span data-ttu-id="77413-160">この変更によって既存のサブスクリプションのデータが無効になるため、 **\@force_reinit_subscription** の値に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-160">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="77413-161">パブリッシャー側のパブリケーション データベースで、[sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-161">At the Publisher on the publication database, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="77413-162">**\@publication** にパブリケーション名を、 **\@article** にフィルター選択の対象アーティクル名を、 **\@filter_clause** に手順 1 で指定したフィルター句を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-162">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 1 for **\@filter_clause**.</span></span> <span data-ttu-id="77413-163">この結果、フィルター選択の対象アーティクルを定義するビューが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="77413-163">This re-creates the view that defines the filtered article.</span></span>  
  
3.  <span data-ttu-id="77413-164">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="77413-164">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="77413-165">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-165">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
4.  <span data-ttu-id="77413-166">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="77413-166">Reinitialize subscriptions.</span></span> <span data-ttu-id="77413-167">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-167">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-delete-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="77413-168">スナップショット パブリケーションまたはトランザクション パブリケーションの静的行フィルターを削除するには</span><span class="sxs-lookup"><span data-stu-id="77413-168">To delete a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="77413-169">パブリッシャー側のパブリケーション データベースに対して、[sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-169">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="77413-170">**\@article** にアーティクル名を、 **\@publication** にパブリケーション名を、 **\@filter_name** に NULL を、 **\@filter_clause** に NULL を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-170">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a value of NULL for **\@filter_name**, and a value of NULL for **\@filter_clause**.</span></span> <span data-ttu-id="77413-171">この変更によって既存のサブスクリプションのデータが無効になるため、 **\@force_reinit_subscription** の値に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-171">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="77413-172">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="77413-172">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="77413-173">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-173">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="77413-174">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="77413-174">Reinitialize subscriptions.</span></span> <span data-ttu-id="77413-175">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="77413-176">マージ パブリケーションの静的行フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="77413-176">To define a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="77413-177">パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-177">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="77413-178">**\@subset_filterclause** にフィルター句 (`WHERE` は含めない) を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-178">Specify the filtering clause for **\@subset_filterclause** (not including `WHERE`).</span></span> <span data-ttu-id="77413-179">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-179">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="77413-180">列フィルターも定義する必要がある場合は、「 [列フィルターの定義および変更](define-and-modify-a-column-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-180">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="77413-181">マージ パブリケーションの静的行フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="77413-181">To modify a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="77413-182">パブリッシャー側のパブリケーション データベースに対して、[sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="77413-182">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="77413-183">**\@publication**、 **\@article**、 **\@property**、 **\@value** に、それぞれパブリケーション名、フィルター選択の対象アーティクル名、**subset_filterclause**、新しいフィルター選択句 (`WHERE` は含めない) を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-183">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, a value of **subset_filterclause** for **\@property**, and the new filtering clause for **\@value** (not including `WHERE`).</span></span> <span data-ttu-id="77413-184">この変更によって既存のサブスクリプションのデータが無効になるため、 **\@force_reinit_subscription** の値に 1 を指定します。</span><span class="sxs-lookup"><span data-stu-id="77413-184">Because this change will invalidate data in existing subscriptions, specify a value of 1 for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="77413-185">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="77413-185">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="77413-186">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-186">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="77413-187">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="77413-187">Reinitialize subscriptions.</span></span> <span data-ttu-id="77413-188">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77413-188">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="77413-189">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="77413-189">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="77413-190">次のトランザクション レプリケーションの例では、アーティクルを行方向でフィルター選択し、製造停止になった製品をすべて除外します。</span><span class="sxs-lookup"><span data-stu-id="77413-190">In this transactional replication example, the article is filtered horizontally to remove all discontinued products.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="77413-191">次のマージ レプリケーションの例では、アーティクルを行方向でフィルター選択して、指定した営業担当者に属する行だけを取得します。</span><span class="sxs-lookup"><span data-stu-id="77413-191">In this merge replication example, the articles are filtered horizontally to return only rows that belong to the specified salesperson.</span></span> <span data-ttu-id="77413-192">結合フィルターも使用されます。</span><span class="sxs-lookup"><span data-stu-id="77413-192">A join filter is also used.</span></span> <span data-ttu-id="77413-193">詳しくは、「 [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77413-193">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="77413-194">参照</span><span class="sxs-lookup"><span data-stu-id="77413-194">See Also</span></span>  
 <span data-ttu-id="77413-195">[マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="77413-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="77413-196">[パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="77413-196">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="77413-197">[パブリッシュされたデータのフィルター処理](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="77413-197">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="77413-198">マージ レプリケーション用にパブリッシュされたデータのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="77413-198">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
