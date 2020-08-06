---
title: 列フィルターの定義および変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a655976f925f83d8c9446cab99016f32ab14887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645518"
---
# <a name="define-and-modify-a-column-filter"></a><span data-ttu-id="5e279-102">列フィルターの定義および変更</span><span class="sxs-lookup"><span data-stu-id="5e279-102">Define and Modify a Column Filter</span></span>
  <span data-ttu-id="5e279-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、列フィルターを定義および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e279-103">This topic describes how to define and modify a column filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5e279-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5e279-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5e279-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5e279-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5e279-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5e279-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="5e279-107">**列フィルターを定義または変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="5e279-107">**To define and modify a column filter, using:**</span></span>  
  
     [<span data-ttu-id="5e279-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5e279-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5e279-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5e279-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5e279-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="5e279-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5e279-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5e279-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5e279-112">一部の列はフィルター選択できません。詳細については、「[Filter Published Data](filter-published-data.md)」(パブリッシュされたデータのフィルター処理) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-112">Some columns cannot be filtered; for more information, see [Filter Published Data](filter-published-data.md).</span></span> <span data-ttu-id="5e279-113">サブスクリプションを初期化した後で列フィルターを変更する場合には、列フィルターの変更後、新規スナップショットを生成してすべてのサブスクリプションを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e279-113">If you modify a column filter after subscriptions have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="5e279-114">プロパティ変更の要件の詳細については、「[Change Publication and Article Properties](change-publication-and-article-properties.md)」(パブリケーションとアーティクルのプロパティの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5e279-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5e279-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5e279-116">パブリケーションの新規作成ウィザードの **[アーティクル]** ページで列フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e279-116">Define column filters on the **Articles** page of the New Publication Wizard.</span></span> <span data-ttu-id="5e279-117">パブリケーションの新規作成ウィザードの詳細については、「[Create a Publication](create-a-publication.md)」(パブリケーションの作成) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-117">For more information about using the New Publication Wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="5e279-118">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、列フィルターの定義および変更を行います。</span><span class="sxs-lookup"><span data-stu-id="5e279-118">Define and modify column filters on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="5e279-119">パブリケーションとアーティクルのプロパティの詳細については、「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」(パブリケーション プロパティの表示と変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-119">For more information about publication and article properties, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-column-filter"></a><span data-ttu-id="5e279-120">列フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="5e279-120">To define a column filter</span></span>  
  
1.  <span data-ttu-id="5e279-121">パブリケーションの新規作成ウィザードの **[アーティクル]** ページにある **[パブリッシュするオブジェクト]** ペインで、フィルター選択するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="5e279-121">On the **Articles** page of the New Publication Wizard, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="5e279-122">フィルター選択する列の隣にあるチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5e279-122">Clear the check box next to each column you want to filter.</span></span>  
  
#### <a name="to-modify-column-filtering"></a><span data-ttu-id="5e279-123">列フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="5e279-123">To modify column filtering</span></span>  
  
1.  <span data-ttu-id="5e279-124">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページにある **[パブリッシュするオブジェクト]** ペインで、フィルター選択するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="5e279-124">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="5e279-125">フィルター選択する列の隣にあるチェック ボックスをオフにして、アーティクルに含める列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5e279-125">Clear the check box next to each column you want to filter, and ensure that the check box is selected for each column that should be included in the article.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5e279-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5e279-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="5e279-127">テーブル アーティクルを作成するときに、アーティクルにどの列を含めるかを定義したり、アーティクルを定義した後で列を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="5e279-127">When creating table articles, you can define which columns to include in the article and change the columns after the article has been defined.</span></span> <span data-ttu-id="5e279-128">レプリケーション ストアド プロシージャを使用して、フィルターが適用された列をプログラムで作成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="5e279-128">You can create and modify filtered columns programmatically using replication stored procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e279-129">次の手順は、基になるテーブルが変更されていないことが前提となっています。</span><span class="sxs-lookup"><span data-stu-id="5e279-129">The following procedures assume that the underlying table has not changed.</span></span> <span data-ttu-id="5e279-130">パブリッシュされたテーブルにデータ定義言語 (DDL) の変更をレプリケートする方法の詳細については、「[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md)」(パブリケーション データベースでのスキーマの変更) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-130">For information on replicating data definition language (DDL) changes to published tables, see [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="5e279-131">スナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされたアーティクルの列フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="5e279-131">To define a column filter for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="5e279-132">フィルターを適用するアーティクルを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e279-132">Define the article to filter.</span></span> <span data-ttu-id="5e279-133">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-133">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="5e279-134">パブリッシャー側のパブリケーション データベースで、 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-134">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="5e279-135">これにより、アーティクルに含める列、またはアーティクルから削除する列を定義します。</span><span class="sxs-lookup"><span data-stu-id="5e279-135">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="5e279-136">多数の列を含むテーブルから少数の列をパブリッシュする場合は、追加する各列に対して [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) を一度実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-136">If publishing only a few columns from a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="5e279-137">**\@column** に列名を指定し、 **\@operation** に **add** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-137">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="5e279-138">多数の列を含むテーブルの列の多くをパブリッシュする場合は、[sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) を実行します。その場合、 **\@column** に **null** を指定し、 **\@operation** に **add** を指定してすべての列を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e279-138">If publishing most of the columns in a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="5e279-139">次に、除外する各列に [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) を一度ずつ実行します。その場合、 **\@operation** に **drop** を指定し、 **\@column** に除外する列名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-139">Then execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
3.  <span data-ttu-id="5e279-140">パブリッシャー側のパブリケーション データベースで、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-140">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="5e279-141">**\@publication** にパブリケーション名を指定し、 **\@article** にフィルターを適用するアーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-141">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="5e279-142">これにより、フィルターを適用するアーティクルの同期オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5e279-142">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="5e279-143">スナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされたアーティクルに対して、追加列を含めるための列フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="5e279-143">To change a column filter to include additional columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="5e279-144">パブリッシャー側のパブリケーション データベースで、追加する各列に対して [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) を一度ずつ実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-144">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="5e279-145">**\@column** に列名を指定し、 **\@operation** に **add** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-145">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="5e279-146">パブリッシャー側のパブリケーション データベースで、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-146">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="5e279-147">**\@publication** にパブリケーション名を指定し、 **\@article** にフィルターを適用するアーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-147">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="5e279-148">パブリケーションに既存のサブスクリプションが存在する場合は、 **\@change_active** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-148">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="5e279-149">これにより、フィルターを適用するアーティクルの同期オブジェクトが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="5e279-149">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="5e279-150">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="5e279-150">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="5e279-151">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="5e279-151">Reinitialize subscriptions.</span></span> <span data-ttu-id="5e279-152">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e279-152">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="5e279-153">スナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされたアーティクルに対して、列を削除するための列フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="5e279-153">To change a column filter to remove columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="5e279-154">パブリッシャー側のパブリケーション データベースで、削除する各列に対して [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) を一度実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-154">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="5e279-155">**\@column** に列名を指定し、 **\@operation** に **drop** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-155">Specify the column name for **\@column** and a value of **drop** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="5e279-156">パブリッシャー側のパブリケーション データベースで、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-156">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="5e279-157">**\@publication** にパブリケーション名を指定し、 **\@article** にフィルターを適用するアーティクルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-157">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="5e279-158">パブリケーションに既存のサブスクリプションが存在する場合は、 **\@change_active** に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-158">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="5e279-159">これにより、フィルターを適用するアーティクルの同期オブジェクトが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="5e279-159">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="5e279-160">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="5e279-160">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="5e279-161">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="5e279-161">Reinitialize subscriptions.</span></span> <span data-ttu-id="5e279-162">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e279-162">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="5e279-163">スナップショットまたはマージ パブリケーションでパブリッシュされたアーティクルの列フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="5e279-163">To define a column filter for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="5e279-164">フィルターを適用するアーティクルを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e279-164">Define the article to filter.</span></span> <span data-ttu-id="5e279-165">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e279-165">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="5e279-166">パブリッシャー側のパブリケーション データベースで、 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-166">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql).</span></span> <span data-ttu-id="5e279-167">これにより、アーティクルに含める列、またはアーティクルから削除する列を定義します。</span><span class="sxs-lookup"><span data-stu-id="5e279-167">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="5e279-168">多数の列を含むテーブルから少数の列のみをパブリッシュする場合は、追加する各列に対して [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を一度ずつ実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-168">If publishing only a few columns from a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="5e279-169">**\@column** に列名を指定し、 **\@operation** に **add** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-169">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="5e279-170">多数の列を含むテーブルの多くの列をパブリッシュする場合は、[sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を実行します。この場合、 **\@column** に **null** を指定し、 **\@operation** に **add** を指定してすべての列を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e279-170">If publishing most of the columns in a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="5e279-171">次に、除外する各列に対して [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を一度ずつ実行します。この場合、 **\@operation** に **drop** を指定し、 **\@column** に除外する列名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-171">Then execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="5e279-172">マージ パブリケーションでパブリッシュされたアーティクルに対して、追加列を含めるための列フィルターを定義するには</span><span class="sxs-lookup"><span data-stu-id="5e279-172">To change a column filter to include additional columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="5e279-173">パブリッシャー側のパブリケーション データベースで、追加する各列に対して [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を一度ずつ実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-173">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="5e279-174">**\@column** に列名を、 **\@operation** に **add**、 **\@force_invalidate_snapshot** と **\@force_reinit_subscription** の両方に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-174">Specify the column name for **\@column**, a value of **add** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="5e279-175">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="5e279-175">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="5e279-176">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="5e279-176">Reinitialize subscriptions.</span></span> <span data-ttu-id="5e279-177">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e279-177">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="5e279-178">マージ パブリケーションでパブリッシュされたアーティクルに対して、列を削除するための列フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="5e279-178">To change a column filter to remove columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="5e279-179">パブリッシャー側のパブリケーション データベースで、削除する各列に対して [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を一度ずつ実行します。</span><span class="sxs-lookup"><span data-stu-id="5e279-179">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="5e279-180">**\@column** に列名を、 **\@operation** に **drop** を、 **\@force_invalidate_snapshot** と **\@force_reinit_subscription** の両方に **1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e279-180">Specify the column name for **\@column**, a value of **drop** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="5e279-181">パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="5e279-181">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="5e279-182">サブスクリプションを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="5e279-182">Reinitialize subscriptions.</span></span> <span data-ttu-id="5e279-183">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e279-183">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="5e279-184">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5e279-184">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="5e279-185">次のトランザクション レプリケーション例では、 `DaysToManufacture` テーブルに基づく `Product` 列がアーティクルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="5e279-185">In this transactional replication example, the `DaysToManufacture` column is removed from an article based on the `Product` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="5e279-186">次のマージ レプリケーション例では、 `CreditCardApprovalCode` テーブルに基づく `SalesOrderHeader` 列がアーティクルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="5e279-186">In this merge replication example, the `CreditCardApprovalCode` column is removed from an article based on the `SalesOrderHeader` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="5e279-187">参照</span><span class="sxs-lookup"><span data-stu-id="5e279-187">See Also</span></span>  
 <span data-ttu-id="5e279-188">[パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5e279-188">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="5e279-189">[パブリッシュされたデータのフィルター処理](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="5e279-189">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="5e279-190">マージ レプリケーション用にパブリッシュされたデータのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="5e279-190">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
