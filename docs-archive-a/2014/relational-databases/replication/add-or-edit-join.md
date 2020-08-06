---
title: 結合の追加と編集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.addeditjoin.f1
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3e17b084a232375734601b515821273d482fcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632420"
---
# <a name="add-or-edit-join"></a><span data-ttu-id="5e0b6-102">結合の追加と編集</span><span class="sxs-lookup"><span data-stu-id="5e0b6-102">Add or Edit Join</span></span>
  <span data-ttu-id="5e0b6-103">**[結合の追加]** ダイアログ ボックスおよび **[結合の編集]** ダイアログ ボックスでは、マージ パブリケーションに使用する結合フィルターの追加と編集を行えます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-103">The **Add Join** and **Edit Join** dialog boxes allow you to add and edit join filters for merge publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e0b6-104">既存のパブリケーション内のフィルターを編集するには、パブリケーション用の新しいスナップショットが必要です。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-104">Editing a filter in an existing publication requires a new snapshot for the publication.</span></span> <span data-ttu-id="5e0b6-105">パブリケーションにサブスクリプションがある場合は、サブスクリプションを再度初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-105">If a publication has subscriptions, the subscriptions must be reinitialized.</span></span> <span data-ttu-id="5e0b6-106">プロパティ変更の詳細については、「[パブリケーションおよびアーティクルのプロパティの変更](publish/change-publication-and-article-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-106">For more information about property changes, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="5e0b6-107">結合フィルターを使用すると、パブリケーションにおける関連するテーブルのフィルター方法に基づいて、テーブルにフィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-107">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="5e0b6-108">一般的に、親テーブルにはパラメーター化された行フィルターが適用されます。次に、テーブル間の結合を定義するときとほぼ同じ方法で、1 つ以上の結合フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-108">Typically a parent table is filtered using a parameterized row filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="5e0b6-109">この結合フィルターにより、関連するテーブル内のデータが結合フィルター句と一致する場合にのみレプリケートされるように、行フィルターが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-109">The join filters extend the row filter so that the data in the related tables is replicated only if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="5e0b6-110">通常、結合フィルターは適用先のテーブルに定義されている主キー/外部キーのリレーションシップに従いますが、これに厳密に限定されてはいません。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-110">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="5e0b6-111">結合フィルターは、2 つのアーティクル テーブル内の関連するデータを比較する、任意のロジックに基づくことができます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-111">The join filter can be based on any logic that compares related data in two article tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5e0b6-112">結合フィルターに使用できるテーブルの数に制限はありませんが、多数のテーブルをフィルターに使用すると、マージ処理中のパフォーマンスに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-112">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can impact performance during merge processing.</span></span> <span data-ttu-id="5e0b6-113">テーブルが 5 つ以上の結合フィルターを生成する場合は、小さなテーブル、変更されないテーブル、プライマリ参照テーブルはフィルター選択しないという別の解決策を検討してください。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-113">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="5e0b6-114">サブスクライバーの間で分割する必要があるテーブル間にのみ、結合フィルターを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-114">Use join filters only between tables that must be partitioned among Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e0b6-115">Options</span><span class="sxs-lookup"><span data-stu-id="5e0b6-115">Options</span></span>  
 <span data-ttu-id="5e0b6-116">このダイアログ ボックスでは、3 つの手順で 2 つのテーブル間の結合フィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-116">This dialog box involves a three-step process to create a join filter between two tables.</span></span> <span data-ttu-id="5e0b6-117">結合フィルターを複数作成するには、このダイアログ ボックスの手順を複数回繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-117">Creating more than one join filter requires more than one pass through the dialog box.</span></span>  
  
1.  <span data-ttu-id="5e0b6-118">**[フィルター選択されたテーブルを確認し、結合テーブルを選択します]**</span><span class="sxs-lookup"><span data-stu-id="5e0b6-118">**Verify filtered table and select the joined table**</span></span>  
  
    -   <span data-ttu-id="5e0b6-119">新しい結合を追加する場合、 **[フィルター選択されたテーブル]** テキスト ボックス内のテーブルが適切かどうか確認します。適切でない場合には **[キャンセル]** をクリックし、 **[テーブル行のフィルター選択]** ページで正しいテーブルを選択して、 **[結合の追加]** をクリックし、このダイアログ ボックスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-119">If you are adding a new join, verify that the table in the **Filtered table** text box is correct (if it is not correct, click **Cancel**, select the correct table on the **Filter Table Rows** page, and click **Add Join** to return to this dialog box).</span></span> <span data-ttu-id="5e0b6-120">次に、 **[結合テーブル]** ドロップダウン リスト ボックスでテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-120">Then select a table from the **Joined table** drop-down list box.</span></span>  
  
    -   <span data-ttu-id="5e0b6-121">既存の結合を編集する場合、テーブル名は既に指定されており、変更できません。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-121">If you are editing an existing join, the table names will be specified already and cannot be changed.</span></span> <span data-ttu-id="5e0b6-122">結合に使用されるテーブルを変更するには、 **[テーブル行のフィルター選択]** ページで既存の結合フィルターを削除して、別のテーブルの間に新しい結合を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-122">To change the tables involved in the join, you must delete the existing join filter on the **Filter Table Rows** page and create a new join between different tables.</span></span>  
  
2.  <span data-ttu-id="5e0b6-123">**[JOIN ステートメントを作成します]**</span><span class="sxs-lookup"><span data-stu-id="5e0b6-123">**Create the join statement**</span></span>  
  
    -   <span data-ttu-id="5e0b6-124">新しい結合を追加する場合、 **[ビルダーを使用してステートメントを作成する]** または **[JOIN ステートメントを手動で作成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-124">If you are adding a new join, select either **Use the builder to create the statement** or **Write the join statement manually**.</span></span> <span data-ttu-id="5e0b6-125">結合を手動で作成する場合、ビルダーは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-125">If you begin writing the join manually, you cannot use the builder.</span></span>  
  
         <span data-ttu-id="5e0b6-126">ビルダーの使用を選択した場合、グリッド内の列 ( **[結合]** 、 **[フィルター選択されたテーブルの列]** 、 **[演算子]** 、 **[結合テーブルの列]** ) を使用して JOIN ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-126">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span> <span data-ttu-id="5e0b6-127">グリッド内の各列にはドロップダウン リスト ボックスがあり、これを使用して 2 つの列と 1 つの演算子 ( **=** 、 **<>** 、 **<=** 、 **\<**, **>=** 、 **>** 、 **[like]** ) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-127">Each column in the grid contains a drop-down list box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, **like**).</span></span> <span data-ttu-id="5e0b6-128">結果は **[プレビュー]** テキスト領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-128">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="5e0b6-129">結合に列が 2 組以上使用される場合には、 **[結合]** 列で結合 ( **[AND]** または **[OR]** ) を選択し、2 つの列と別の演算子を入力します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-129">If the join involves more than one pair of columns, select a conjunction (**AND** or **OR**) from the **Conjunction** column, and then enter two more columns and another operator.</span></span>  
  
         <span data-ttu-id="5e0b6-130">ステートメントを手動で作成する場合、 **[JOIN ステートメント]** テキスト領域に JOIN ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-130">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="5e0b6-131">**[フィルター選択されたテーブルの列]** リスト ボックスと **[結合テーブルの列]** リスト ボックスを使用して、列を **[結合テーブルの列]** テキスト領域にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-131">Use the **Filtered table columns** list box and **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="5e0b6-132">既存の結合を編集する場合、手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-132">If you are editing an existing join, you must make edits manually.</span></span>  
  
3.  <span data-ttu-id="5e0b6-133">**[結合オプションを指定します]**</span><span class="sxs-lookup"><span data-stu-id="5e0b6-133">**Specify join options**</span></span>  
  
    -   <span data-ttu-id="5e0b6-134">フィルター選択するテーブル内で結合する列が一意な場合、 **[一意キー : フィルター選択されたテーブルの 1 つの行に関連する結合テーブル内の行 (一対一または一対多の関係)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-134">If the column on which you join in the filtered table is unique, select **Unique key**.</span></span> <span data-ttu-id="5e0b6-135">列が一意の場合、特別なパフォーマンスの最適化機能をマージ処理で利用できます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-135">The merge process has special performance optimizations available if the column is unique.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="5e0b6-136">このオプションを選択すると、結合フィルターにおける子テーブルと親テーブルのリレーションシップが一対一または一対多となるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-136">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="5e0b6-137">親テーブル内の結合する列に一意性を保証する制約がある場合にのみ、このオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-137">Only select this option if you have a constraint on the joining column in the parent table that guarantees uniqueness.</span></span> <span data-ttu-id="5e0b6-138">このオプションを適切に設定しなかった場合、データを収束できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-138">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="5e0b6-139">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-139">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="5e0b6-140">既定で、マージ レプリケーションでは同期中に行ごとに変化が処理されます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-140">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="5e0b6-141">関連する変更をまとめて処理するには、 **[論理レコード : フィルター選択されたテーブルと結合テーブルの関連する変更を同期時にトランザクションとして扱う]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-141">To have related changes processed as a unit, select **Logical record**.</span></span> <span data-ttu-id="5e0b6-142">このオプションは、論理レコードを使用するために必要なアーティクルとパブリケーションの要件が満たされている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-142">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="5e0b6-143">詳細については、「[論理レコードによる関連行への変更のグループ化](merge/group-changes-to-related-rows-with-logical-records.md)」の「Considerations for Using Logical Records」 (論理レコードの使用についての注意点) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-143">For more information, see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
 <span data-ttu-id="5e0b6-144">フィルターを追加または編集した後に、 **[OK]** をクリックして変更を保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-144">After you have added or edited a filter, click **OK** to save changes and close the dialog box.</span></span> <span data-ttu-id="5e0b6-145">指定したフィルターは、SELECT 句のテーブルに対して解析され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-145">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="5e0b6-146">フィルター ステートメントに構文エラーなどの問題がある場合には通知され、フィルター ステートメントを編集することができます。</span><span class="sxs-lookup"><span data-stu-id="5e0b6-146">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0b6-147">参照</span><span class="sxs-lookup"><span data-stu-id="5e0b6-147">See Also</span></span>  
 <span data-ttu-id="5e0b6-148">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="5e0b6-148">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="5e0b6-149">[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5e0b6-149">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="5e0b6-150">[パブリッシュされたデータのフィルター処理](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="5e0b6-150">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="5e0b6-151">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="5e0b6-151">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="5e0b6-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="5e0b6-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="5e0b6-153">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="5e0b6-153">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  