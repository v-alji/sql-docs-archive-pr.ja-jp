---
title: マージ アーティクルのパラメーター化された行フィルターの定義および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], defining
- parameterized filters [SQL Server replication], modifying
- merge replication [SQL Server replication], dynamic filters
- merge replication parameterized filters [SQL Server replication]
- filters [SQL Server replication], parameterized
- modifying filters, parameterized row
- dynamic filters [SQL Server replication]
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d80ad53661aced22795220507398e2fcc510edd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721285"
---
# <a name="define-and-modify-a-parameterized-row-filter-for-a-merge-article"></a><span data-ttu-id="31e9d-102">マージ アーティクルのパラメーター化された行フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="31e9d-102">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>
  <span data-ttu-id="31e9d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パラメーター化された行フィルターを定義および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-103">This topic describes how to define and modify a parameterized row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="31e9d-104">テーブル アーティクルを作成する際には、パラメーター化された行フィルターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-104">When creating table articles, you can use parameterized row filters.</span></span> <span data-ttu-id="31e9d-105">このフィルターでは [WHERE](/sql/t-sql/queries/where-transact-sql) 句を使用して、パブリッシュする適切なデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-105">These filters use a [WHERE](/sql/t-sql/queries/where-transact-sql) clause to select the appropriate data to be published.</span></span> <span data-ttu-id="31e9d-106">静的行フィルターのようにこの句でリテラル値を指定するのではなく、システム関数[SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) および [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) のいずれかまたは両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-106">Rather than specifying a literal value in the clause (as you do with a static row filter), you specify one or both of the following system functions: [SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) and [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql).</span></span> <span data-ttu-id="31e9d-107">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="31e9d-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="31e9d-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="31e9d-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="31e9d-109">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="31e9d-110">パブリケーションに対するサブスクリプションが初期化された後に、パラメーター化された行フィルターを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31e9d-110">If you add, modify, or delete a parameterized row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="31e9d-111">プロパティ変更の要件の詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-111">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="31e9d-112">推奨事項</span><span class="sxs-lookup"><span data-stu-id="31e9d-112">Recommendations</span></span>  
  
-   <span data-ttu-id="31e9d-113">パラメーター化された行フィルター句では列名に関数を適用しないことをお勧めします。これは、 `LEFT([MyColumn]) = SUSER_SNAME()`のように指定すると、パフォーマンスに問題が生じるためです。</span><span class="sxs-lookup"><span data-stu-id="31e9d-113">For performance reasons, we recommend that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="31e9d-114">フィルター句で HOST_NAME を使用していて、HOST_NAME 値をオーバーライドする場合は、CONVERT を使用するデータ型の変換が必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="31e9d-114">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="31e9d-115">このようなケースの推奨事項の詳細については、「[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」の「HOST_NAME() 値のオーバーライド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-115">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="31e9d-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="31e9d-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="31e9d-117">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、パラメーター化された行フィルターを定義、変更、または削除します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-117">Define, modify, and delete parameterized row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="31e9d-118">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-118">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter"></a><span data-ttu-id="31e9d-119">パラメーター化された行フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="31e9d-119">To define a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="31e9d-120">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[追加]** をクリックし、次に **[フィルターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31e9d-120">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="31e9d-121">**[フィルターの追加]** ダイアログ ボックスで、ドロップダウン リスト ボックスからフィルター選択するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-121">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="31e9d-122">**[フィルター ステートメント]** テキスト ボックスで、フィルター ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-122">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="31e9d-123">テキスト領域に直接入力することも、 **[列]** ボックスから列をドラッグ アンド ドロップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-123">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    -   <span data-ttu-id="31e9d-124">**[フィルター ステートメント]** テキスト領域には、次の形式の既定のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-124">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="31e9d-125">既定のテキストは変更できません。標準の SQL 構文を使用して WHERE キーワードの後にフィルター句を入力してください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-125">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="31e9d-126">パラメーター化されたフィルターには、システム関数 `HOST_NAME()` および `SUSER_SNAME()` の呼び出し、あるいは、これらの関数のいずれかまたは両方を参照するユーザー定義関数の呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="31e9d-126">A parameterized filter includes a call to the system function `HOST_NAME()` and/or `SUSER_SNAME()`, or a user-defined function that references one or both of these functions.</span></span> <span data-ttu-id="31e9d-127">パラメーター化された行フィルターの完全なフィルター句の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-127">The following is an example of a complete filter clause for a parameterized row filter:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="31e9d-128">WHERE 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="31e9d-128">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="31e9d-129">複数のサブスクライバー間でのデータの共有方法に一致するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-129">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="31e9d-130">**[このテーブルの 1 行を複数のサブスクリプションに移動する]**</span><span class="sxs-lookup"><span data-stu-id="31e9d-130">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="31e9d-131">**[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**</span><span class="sxs-lookup"><span data-stu-id="31e9d-131">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="31e9d-132">**[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** を選択すると、マージ レプリケーションは、格納および処理するメタデータを減らすことにより、パフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-132">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="31e9d-133">ただし、データのパーティション分割によって、1 つの行が複数のサブスクライバーにレプリケートされないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31e9d-133">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="31e9d-134">詳細については、「 [パラメーター化された行フィルター](../merge/parameterized-filters-parameterized-row-filters.md)」トピックの「[パーティションのオプション] の設定」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-134">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="31e9d-135">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-135">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-parameterized-row-filter"></a><span data-ttu-id="31e9d-136">パラメーター化された行フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="31e9d-136">To modify a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="31e9d-137">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31e9d-137">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="31e9d-138">**[フィルターの編集]** ダイアログ ボックスで、フィルターを変更します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-138">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-parameterized-row-filter"></a><span data-ttu-id="31e9d-139">パラメーター化された行フィルターを削除するには</span><span class="sxs-lookup"><span data-stu-id="31e9d-139">To delete a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="31e9d-140">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31e9d-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="31e9d-141">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="31e9d-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="31e9d-142">パラメーター化された行フィルターは、レプリケーション ストアド プロシージャを使用してプログラムから作成し、変更できます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-142">Parameterized row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="31e9d-143">マージ パブリケーション内のアーティクルにパラメーター化された行フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="31e9d-143">To define a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="31e9d-144">パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-144">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="31e9d-145">を指定し、アーティクルの名前をに、 **@publication** **@article** パブリッシュするテーブルを、にパラメーター化された **@source_object** フィルターを定義する where 句 **@subset_filterclause** (は含めない) を指定し `WHERE` 、に次のいずれかの値を指定します **@partition_options** 。これは、パラメーター化された行フィルターの結果として得られるパーティション分割の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-145">Specify **@publication**, a name for the article for **@article**, the table being published for **@source_object**, the WHERE clause that defines the parameterized filter for **@subset_filterclause** (not including `WHERE`), and one of the following values for **@partition_options**, which describes the type of partitioning that will result from the parameterized row filter:</span></span>  
  
    -   <span data-ttu-id="31e9d-146">**0** - アーティクルのフィルター選択が静的であるか、各パーティションに対して一意なデータのサブセットは生成されません ("重複する" パーティション)。</span><span class="sxs-lookup"><span data-stu-id="31e9d-146">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="31e9d-147">**1** - 生成されるパーティションは重複しており、サブスクライバーでの更新によって行が属しているパーティションを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="31e9d-147">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="31e9d-148">**2** - アーティクルのフィルター選択によって重複しないパーティションが生成されますが、複数のサブスクライバーが同じパーティションを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-148">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="31e9d-149">**3** - アーティクルのフィルター選択によって、各サブスクリプションで一意な重複しないパーティションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-149">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
#### <a name="to-change-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="31e9d-150">マージ パブリケーション内のアーティクルに適用するパラメーター化された行フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="31e9d-150">To change a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="31e9d-151">パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-151">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="31e9d-152">**@publication**、 **@article** 、の値をに指定し `subset_filterclause` **@property** ます。のパラメーター化されたフィルターを定義する式 **@value** (は含めません `WHERE` ) と、との両方に**1** **@force_invalidate_snapshot** **@force_reinit_subscription** を指定します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-152">Specify **@publication**, **@article**, a value of `subset_filterclause` for **@property**, the expression that defines the parameterized filter for **@value** (not including `WHERE`), and a value of **1** for both **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="31e9d-153">この変更によって別のパーティション分割が発生した場合、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) を再び実行します。</span><span class="sxs-lookup"><span data-stu-id="31e9d-153">If this change results in different partitioning behavior, then execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="31e9d-154">、、にの値を指定し、に最適 **@publication** **@article** `partition_options` **@property** なパーティション分割オプションを指定し **@value** ます。これは、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="31e9d-154">Specify **@publication**, **@article**, a value of `partition_options` for **@property**, and the most appropriate partitioning option for **@value**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="31e9d-155">**0** - アーティクルのフィルター選択が静的であるか、各パーティションに対して一意なデータのサブセットは生成されません ("重複する" パーティション)。</span><span class="sxs-lookup"><span data-stu-id="31e9d-155">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="31e9d-156">**1** - 生成されるパーティションは重複しており、サブスクライバーでの更新によって行が属しているパーティションを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="31e9d-156">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="31e9d-157">**2** - アーティクルのフィルター選択によって重複しないパーティションが生成されますが、複数のサブスクライバーが同じパーティションを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-157">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="31e9d-158">**3** - アーティクルのフィルター選択によって、各サブスクリプションで一意な重複しないパーティションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-158">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="31e9d-159">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="31e9d-159">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="31e9d-160">次の例では、 `Employee` テーブルに対して一連の結合フィルターを使用してアーティクルがフィルター選択されるマージ パブリケーションで、アーティクルのグループを定義します。このテーブル自体はパラメーター化された行フィルターを **LoginID** 列に使用してフィルター選択されています。</span><span class="sxs-lookup"><span data-stu-id="31e9d-160">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the **LoginID** column.</span></span> <span data-ttu-id="31e9d-161">同期の間、[HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) 関数により返される値はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="31e9d-161">During synchronization, the value returned by the [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) function is overridden.</span></span> <span data-ttu-id="31e9d-162">詳細については、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」の「HOST_NAME() 値のオーバーライド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31e9d-162">For more information, see Overriding the HOST_NAME() Value in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
  
## <a name="see-also"></a><span data-ttu-id="31e9d-163">参照</span><span class="sxs-lookup"><span data-stu-id="31e9d-163">See Also</span></span>  
 <span data-ttu-id="31e9d-164">[マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="31e9d-164">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="31e9d-165">[パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="31e9d-165">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="31e9d-166">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="31e9d-166">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="31e9d-167">パラメーター化された行フィルター</span><span class="sxs-lookup"><span data-stu-id="31e9d-167">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
