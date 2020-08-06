---
title: マージアーティクル間の一連の結合フィルターを自動的に生成する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- automatic join filter generation
- join filters
ms.assetid: 7ef419f4-c17f-42a5-9068-174a3ec08941
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bfdbf93aad134e4da873a6aade307754a2637e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630900"
---
# <a name="automatically-generate-a-set-of-join-filters-between-merge-articles-sql-server-management-studio"></a><span data-ttu-id="110a2-102">マージ アーティクル間の一連の結合フィルターを自動的に生成する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="110a2-102">Automatically Generate a Set of Join Filters Between Merge Articles (SQL Server Management Studio)</span></span>
  <span data-ttu-id="110a2-103">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、一連の結合フィルターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-103">Automatically generate a set of join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="110a2-104">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="110a2-104">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="110a2-105">パブリケーションに対するサブスクリプションを初期化した後に、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで一連の結合フィルターを自動的に生成した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="110a2-105">If you automatically generate a set of join filters in the **Publication Properties - \<Publication>** dialog box after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="110a2-106">プロパティ変更の要件の詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="110a2-106">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="110a2-107">結合フィルターは、一連のテーブルに対して手動で作成できます。また、テーブルに定義された外部キーと主キーのリレーションシップに基づいてレプリケーションによって自動的に生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="110a2-107">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the foreign key to primary key relationships defined on the tables.</span></span> <span data-ttu-id="110a2-108">手動での結合フィルターの作成の詳細については、「[マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="110a2-108">For more information about creating join filters manually, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
### <a name="to-automatically-generate-a-set-of-join-filters-between-merge-articles"></a><span data-ttu-id="110a2-109">マージ アーティクル間の一連の結合フィルターを自動的に生成するには</span><span class="sxs-lookup"><span data-stu-id="110a2-109">To automatically generate a set of join filters between merge articles</span></span>  
  
1.  <span data-ttu-id="110a2-110">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[追加]** をクリックし、次に **[フィルターを自動的に生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110a2-110">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Automatically Generate Filters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="110a2-111">フィルターを自動的に生成すると、現在パブリケーション内にある行フィルターまたは結合フィルターがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-111">Automatically generating filters deletes any existing row filters or join filters in the publication.</span></span> <span data-ttu-id="110a2-112">一連のフィルターを自動的に生成した後でフィルターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="110a2-112">You can add filters after automatically generating a set of filters.</span></span>  
  
2.  <span data-ttu-id="110a2-113">**[フィルターの生成]** ダイアログ ボックスの処理に従って行フィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="110a2-113">Follow the process in the **Generate Filters** dialog box to create a row filter.</span></span> <span data-ttu-id="110a2-114">次に、主キーと外部キーのリレーションシップによって、フィルター選択されるテーブルに関係する各テーブルに行フィルターが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-114">The row filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span>  
  
    1.  <span data-ttu-id="110a2-115">ドロップダウン リスト ボックスからフィルター選択するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="110a2-115">Select a table to filter from the drop-down list box.</span></span>  
  
    2.  <span data-ttu-id="110a2-116">**[フィルター ステートメント]** テキスト ボックスで、フィルター ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="110a2-116">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="110a2-117">テキスト領域に直接入力することも、 **[列]** ボックスから列をドラッグ アンド ドロップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="110a2-117">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
         <span data-ttu-id="110a2-118">**[フィルター ステートメント]** テキスト領域には、次の形式の既定のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-118">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
         <span data-ttu-id="110a2-119">既定のテキストは変更できません。静的行フィルターのフィルター句を入力するか、標準の SQL 構文を使用して WHERE キーワードの後にパラメーター化された行フィルターを入力してください。</span><span class="sxs-lookup"><span data-stu-id="110a2-119">The default text cannot be changed; type the filter clause for a static row filter or a parameterized row filter after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="110a2-120">パラメーター化された行フィルターの完全なフィルター句は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="110a2-120">The complete filter clause for a parameterized row filter would look like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="110a2-121">WHERE 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="110a2-121">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
    3.  <span data-ttu-id="110a2-122">フィルター オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="110a2-122">Specify filter options.</span></span>  
  
         <span data-ttu-id="110a2-123">複数のサブスクライバー間でのデータの共有方法に一致するオプションを選択します。 **[このテーブルの 1 行を複数のサブスクリプションに移動する]** または **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** 。</span><span class="sxs-lookup"><span data-stu-id="110a2-123">Select the option that matches how data will be shared among Subscribers: **A row from this table will go to multiple subscriptions** or **A row from this table will go to only one subscription**.</span></span> <span data-ttu-id="110a2-124">**[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** を選択すると、マージ レプリケーションは、格納および処理するメタデータを減らすことにより、パフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="110a2-124">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="110a2-125">ただし、データのパーティション分割によって、1 つの行が複数のサブスクライバーにレプリケートされないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="110a2-125">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="110a2-126">詳細については、「 [パラメーター化された行フィルター](../merge/parameterized-filters-parameterized-row-filters.md)」トピックの「[パーティションのオプション] の設定」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="110a2-126">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="110a2-127">指定したフィルターは、SELECT 句のテーブルに対して解析され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-127">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="110a2-128">フィルター ステートメントに構文エラーなどの問題がある場合には通知され、フィルター ステートメントを編集することができます。</span><span class="sxs-lookup"><span data-stu-id="110a2-128">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
     <span data-ttu-id="110a2-129">ステートメントの解析が終了すると、レプリケーションによって必要な結合フィルターが作成され、 **[テーブル行のフィルター選択]** ページ、または **[行のフィルター選択]** ページの **[フィルター選択されたテーブル]** ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-129">After the statement is parsed, replication creates the necessary join filters and displays them in the **Filtered Tables** pane on the **Filter Table Rows** or **Filter Rows** page.</span></span> <span data-ttu-id="110a2-130">パブリケーションの新規作成ウィザードでフィルターを生成し、このウィザードの実行対象であるパブリッシャーのディストリビューターをまだ構成していない場合は、構成するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="110a2-130">If you are generating filters from the New Publication Wizard and have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
4.  <span data-ttu-id="110a2-131">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="110a2-131">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
### <a name="to-modify-a-filter-that-was-automatically-generated"></a><span data-ttu-id="110a2-132">自動的に生成されたフィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="110a2-132">To modify a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="110a2-133">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110a2-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="110a2-134">**[フィルターの編集]** または **[結合の編集]** ダイアログ ボックスでフィルターを変更します。</span><span class="sxs-lookup"><span data-stu-id="110a2-134">In the **Edit Filter** or **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-filter-that-was-automatically-generated"></a><span data-ttu-id="110a2-135">自動的に生成されたフィルターを削除するには</span><span class="sxs-lookup"><span data-stu-id="110a2-135">To delete a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="110a2-136">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** の **[行のフィルター選択]** ページで、 **[フィルター選択されたテーブル]** ペイン内のフィルターを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110a2-136">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110a2-137">参照</span><span class="sxs-lookup"><span data-stu-id="110a2-137">See Also</span></span>  
 <span data-ttu-id="110a2-138">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="110a2-138">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="110a2-139">パラメーター化された行フィルター</span><span class="sxs-lookup"><span data-stu-id="110a2-139">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
