---
title: パラメーター化された行フィルターの最適化 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1c6448d8e2dba7a68fab441d4d08fd4a4a1db4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740818"
---
# <a name="optimize-parameterized-row-filters"></a><span data-ttu-id="c4eba-102">パラメーター化された行フィルターの最適化</span><span class="sxs-lookup"><span data-stu-id="c4eba-102">Optimize Parameterized Row Filters</span></span>
  <span data-ttu-id="c4eba-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パラメーター化された行フィルターを最適化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-103">This topic describes how to optimize parameterized row filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c4eba-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c4eba-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c4eba-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c4eba-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c4eba-106">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="c4eba-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="c4eba-107">**パラメーター化された行フィルターを最適化するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="c4eba-107">**To optimize parameterized row filters, using:**</span></span>  
  
     [<span data-ttu-id="c4eba-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4eba-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c4eba-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4eba-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4eba-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="c4eba-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c4eba-111">推奨事項</span><span class="sxs-lookup"><span data-stu-id="c4eba-111">Recommendations</span></span>  
  
-   <span data-ttu-id="c4eba-112">パラメーター化されたフィルターを使用する場合、パブリケーションを作成する際に **\@use_partition_groups** オプションまたは **\@keep_partition_changes** オプションを指定して、マージ レプリケーションでのフィルターの処理方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-112">When you use parameterized filters, you can control how the filters are processed by merge replication by specifying either the **use partition groups** option or the **keep partition changes** option when you create a publication.</span></span> <span data-ttu-id="c4eba-113">この 2 つのオプションを使用し、パブリケーション データベースに追加のメタデータを格納することで、アーティクルをフィルター選択し、パブリケーションの同期パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-113">These options improve the synchronization performance for publications with filtered articles by storing additional metadata in the publication database.</span></span> <span data-ttu-id="c4eba-114">アーティクルを作成する際に **\@partition_options** を設定することで、サブスクライバー間でデータを共有する方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-114">You can control how the data is shared among Subscribers by setting **partition options** when you create an article.</span></span> <span data-ttu-id="c4eba-115">これらの要件の詳細については、「 [パラメーター化された行フィルター](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-115">For more information about these requirements, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="c4eba-116">[!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact サブスクライバーを使用して、keep_partition_changes を true に設定し、削除を正しく反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4eba-116">With [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact subscribers, keep_partition_changes must be set to true to ensure that deletes are correctly propagated.</span></span> <span data-ttu-id="c4eba-117">false に設定すると、サブスクライバーに予想よりも多くの行が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c4eba-117">When set to false, the subscriber might have more rows than expected.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c4eba-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c4eba-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c4eba-119">次の設定を使用して、パラメーター化された行フィルターを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-119">The following settings can be used to optimize parameterized row filters:</span></span>  
  
 <span data-ttu-id="c4eba-120">**Partition Options**</span><span class="sxs-lookup"><span data-stu-id="c4eba-120">**Partition Options**</span></span>  
 <span data-ttu-id="c4eba-121">このオプションは、 **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** ページ、または **[フィルターの追加]** ダイアログ ボックスで設定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-121">Set this option on the **Properties** page of the **Article Properties - \<Article>** dialog box, or in the **Add Filter** dialog box.</span></span> <span data-ttu-id="c4eba-122">どちらのダイアログ ボックスも、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-122">Both dialog boxes are available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="c4eba-123">**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスでは、 **[フィルターの追加]** ダイアログ ボックスでは使用できない、このオプションに対する追加の値も指定できます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-123">The **Article Properties - \<Article>** dialog box allows you to specify additional values for this option that are not available in the **Add Filter** dialog box.</span></span>  
  
 <span data-ttu-id="c4eba-124">**[パーティションの事前計算]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-124">**Precompute Partitions**</span></span>  
 <span data-ttu-id="c4eba-125">このオプションは、パブリケーションのアーティクルが一連の要件を満たしている場合に、既定で **[True]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="c4eba-125">This option is set to **True** by default if the articles in your publication adhere to a set of requirements.</span></span> <span data-ttu-id="c4eba-126">これらの要件の詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-126">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="c4eba-127">このオプションは、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで変更します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-127">Modify this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="c4eba-128">**[同期の最適化]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-128">**Optimize Synchronization**</span></span>  
 <span data-ttu-id="c4eba-129">このオプションは、 **[パーティションの事前計算]** が **[False]** に設定されている場合にのみ、 **[True]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="c4eba-129">This option should be set to **True** only if **Precompute Partitions** is set to **False**.</span></span> <span data-ttu-id="c4eba-130">このオプションは、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで設定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-130">Set this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="c4eba-131">パブリケーションの新規作成ウィザードの使用および **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」 (パブリケーションの作成) および「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-131">For more information about using the New Publication Wizard and accessing the **Publication Properties - \<Publication>** dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a><span data-ttu-id="c4eba-132">[フィルターの追加] または [フィルターの編集] ダイアログ ボックスでパーティションのオプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="c4eba-132">To set Partition options in the Add Filter or Edit Filter dialog box</span></span>  
  
1.  <span data-ttu-id="c4eba-133">パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、 **[追加]** をクリックし、 **[フィルターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4eba-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="c4eba-134">パラメーター化されたフィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-134">Create a parameterized filter.</span></span> <span data-ttu-id="c4eba-135">詳しくは、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-135">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="c4eba-136">複数のサブスクライバー間でのデータの共有方法に一致するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-136">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="c4eba-137">**[このテーブルの 1 行を複数のサブスクリプションに移動する]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-137">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="c4eba-138">**[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-138">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="c4eba-139">**[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** を選択すると、マージ レプリケーションは、格納および処理するメタデータを減らすことにより、パフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-139">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="c4eba-140">ただし、データのパーティション分割によって、1 つの行が複数のサブスクライバーにレプリケートされないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4eba-140">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="c4eba-141">詳細については、「 [パラメーター化された行フィルター](../merge/parameterized-filters-parameterized-row-filters.md)」トピックの「[パーティションのオプション] の設定」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-141">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="c4eba-142">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-142">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a><span data-ttu-id="c4eba-143">[アーティクルのプロパティ - \<Article>] ダイアログ ボックスで [パーティションのオプション] を設定するには</span><span class="sxs-lookup"><span data-stu-id="c4eba-143">To set Partition Options in the Article Properties - \<Article> dialog box</span></span>  
  
1.  <span data-ttu-id="c4eba-144">パブリケーションの新規作成ウィザードの **[アーティクル]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスでテーブルを選択し、 **[アーティクルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4eba-144">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="c4eba-145">**[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4eba-145">Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.</span></span>  
  
3.  <span data-ttu-id="c4eba-146">**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** タブの **[対象オブジェクト]** セクションで、 **[パーティションのオプション]** に対して以下のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-146">In the **Destination Object** section of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify one of the following values for **Partition Options**:</span></span>  
  
    -   <span data-ttu-id="c4eba-147">**[重複する]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-147">**Overlapping**</span></span>  
  
    -   <span data-ttu-id="c4eba-148">**[重複する (パーティション外のデータ変更を禁止)]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-148">**Overlapping, disallow out-of-partition data changes**</span></span>  
  
    -   <span data-ttu-id="c4eba-149">**[重複しない (単一のサブスクリプション)]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-149">**Nonoverlapping, single subscription**</span></span>  
  
    -   <span data-ttu-id="c4eba-150">**[重複しない (複数のサブスクリプションで共有)]**</span><span class="sxs-lookup"><span data-stu-id="c4eba-150">**Nonoverlapping, shared between subscriptions**</span></span>  
  
     <span data-ttu-id="c4eba-151">これらのオプションの詳細、および **[フィルターの追加]** および **[フィルターの編集]** ダイアログ ボックスで使用できるオプションとこれらのオプションを関連付ける方法の詳細については、「 [パラメーター化された行フィルター](../merge/parameterized-filters-parameterized-row-filters.md)」の「[パーティションのオプション] の設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-151">For more information about these options and how they relate to the options available in the **Add Filter** and **Edit Filter** dialog boxes, see the "Setting 'partition options'" section of [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="c4eba-152">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-152">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-precompute-partitions"></a><span data-ttu-id="c4eba-153">[パーティションの事前計算] を設定するには</span><span class="sxs-lookup"><span data-stu-id="c4eba-153">To set Precompute Partitions</span></span>  
  
1.  <span data-ttu-id="c4eba-154">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、 **[パーティションの事前計算]** オプションに対する値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-154">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value for the **Precompute Partitions** option.</span></span> <span data-ttu-id="c4eba-155">このプロパティは、以下の場合に読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="c4eba-155">The property is read-only if:</span></span>  
  
    -   <span data-ttu-id="c4eba-156">パブリケーションが、事前計算済みパーティションの要件を満たさない場合。</span><span class="sxs-lookup"><span data-stu-id="c4eba-156">The publication does not meet the requirements for precomputed partitions.</span></span>  
  
    -   <span data-ttu-id="c4eba-157">スナップショットが、パブリケーションに対して生成されていない場合。</span><span class="sxs-lookup"><span data-stu-id="c4eba-157">A snapshot has not yet been generated for the publication.</span></span> <span data-ttu-id="c4eba-158">この場合、 **[スナップショットの作成時に自動的に設定する]** の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-158">In this case, the option displays a value of **Set automatically when a snapshot is created**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a><span data-ttu-id="c4eba-159">[同期の最適化] を設定するには</span><span class="sxs-lookup"><span data-stu-id="c4eba-159">To set Optimize Synchronization</span></span>  
  
1.  <span data-ttu-id="c4eba-160">[**パブリケーションのプロパティ \<Publication> -** ] ダイアログボックスの [**サブスクリプションオプション**] ページで、[**同期の最適化**] オプションの値として [ **True** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-160">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Optimize Synchronization** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c4eba-161">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c4eba-161">Using Transact-SQL</span></span>  
 <span data-ttu-id="c4eba-162">\*\* \@ Keep_partition_changes**および** \@ use_partition_groups\*\*のフィルター選択オプションの定義については、「 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-162">For definitions of the filtering options for **\@keep_partition_changes** and **\@use_partition_groups**, see [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a><span data-ttu-id="c4eba-163">新しいパブリケーションを作成するときにマージ フィルターの最適化を指定するには</span><span class="sxs-lookup"><span data-stu-id="c4eba-163">To specify merge filter optimizations when creating a new publication</span></span>  
  
1.  <span data-ttu-id="c4eba-164">パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-164">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="c4eba-165">次のいずれかのパラメーターに、 \*\* \@ publication\*\*との値を指定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-165">Specify **\@publication** and a value of `true` for one the following parameters:</span></span>  
  
    -   <span data-ttu-id="c4eba-166">\*\* \@ use_partition_groups\*\*: 事前計算済みパーティションの要件にアーティクルが準拠していれば、最高のパフォーマンス最適化。</span><span class="sxs-lookup"><span data-stu-id="c4eba-166">**\@use_partition_groups**: - the highest performance optimization, provided that the articles conform to the requirements for precomputed partitions.</span></span> <span data-ttu-id="c4eba-167">詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-167">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="c4eba-168">\*\* \@ keep_partition_changes\*\* -事前計算済みパーティションを使用できない場合は、この最適化を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-168">**\@keep_partition_changes** - use this optimization if precomputed partitions cannot be used.</span></span>  
  
2.  <span data-ttu-id="c4eba-169">パブリケーション用のスナップショット ジョブを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-169">Add a snapshot job for the publication.</span></span> <span data-ttu-id="c4eba-170">詳細については、「[Publisher で文書を作成するには](create-a-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-170">For more information see [Create a Publication](create-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="c4eba-171">パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), specifying the following parameters:</span></span>  
  
    -   <span data-ttu-id="c4eba-172">\*\* \@ publication\*\* -手順 1. のパブリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="c4eba-172">**\@publication** - the name of the publication from step 1.</span></span>  
  
    -   <span data-ttu-id="c4eba-173">\*\* \@ article\*\* -アーティクルの名前</span><span class="sxs-lookup"><span data-stu-id="c4eba-173">**\@article** - a name for the article</span></span>  
  
    -   <span data-ttu-id="c4eba-174">\*\* \@ source_object\*\* -パブリッシュされるデータベースオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c4eba-174">**\@source_object** - the database object being published.</span></span>  
  
    -   <span data-ttu-id="c4eba-175">\*\* \@ subset_filterclause\*\* -アーティクルを行方向にフィルター選択するために使用する、省略可能なパラメーター化されたフィルター句。</span><span class="sxs-lookup"><span data-stu-id="c4eba-175">**\@subset_filterclause** - the optional parameterized filter clause used to horizontally filter the article.</span></span>  
  
    -   <span data-ttu-id="c4eba-176">\*\* \@ partition_options\*\* -フィルター選択されたアーティクルのパーティションオプション。</span><span class="sxs-lookup"><span data-stu-id="c4eba-176">**\@partition_options** - the partition options for the filtered article.</span></span>  
  
4.  <span data-ttu-id="c4eba-177">パブリケーションの各アーティクルに対し、手順 3. を実行します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-177">Repeat step 3 for each article in the publication.</span></span>  
  
5.  <span data-ttu-id="c4eba-178">(省略可) パブリッシャー側のパブリケーション データベースに対して [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) を実行し、2 つのアーティクル間に結合フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-178">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="c4eba-179">詳しくは、「 [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-179">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a><span data-ttu-id="c4eba-180">既存のパブリケーションに対するマージ フィルターの動作を表示して変更するには</span><span class="sxs-lookup"><span data-stu-id="c4eba-180">To view and modify merge filter behaviors for an existing publication</span></span>  
  
1.  <span data-ttu-id="c4eba-181">Optionalパブリッシャー側のパブリケーションデータベースに対して[sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)を実行し、 \*\* \@ パブリケーション\*\*を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-181">(Optional) At the Publisher on the publication database, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication**.</span></span> <span data-ttu-id="c4eba-182">結果セットの **keep_partition_changes** および **use_partition_groups** の値を調べます。</span><span class="sxs-lookup"><span data-stu-id="c4eba-182">Note the value of **keep_partition_changes** and **use_partition_groups** in the result set.</span></span>  
  
2.  <span data-ttu-id="c4eba-183">(省略可) パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-183">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="c4eba-184">\*\* \@ プロパティ**には**use_partition_groups**の値を指定し `true` 、 `false` \*\* \@ value**にはまたはのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-184">Specify a value of **use_partition_groups** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
3.  <span data-ttu-id="c4eba-185">(省略可) パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-185">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="c4eba-186">\*\* \@ プロパティ**には**keep_partition_changes**の値を指定し `true` 、 `false` \*\* \@ value**にはまたはのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-186">Specify a value of **keep_partition_changes** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4eba-187">**Keep_partition_changes**を有効にする場合は、まず**use_partition_groups**を無効にし、 \*\* \@ force_reinit_subscription**に**1\*\*を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4eba-187">When enabling **keep_partition_changes**, you must first disable **use_partition_groups** and specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
4.  <span data-ttu-id="c4eba-188">(省略可) パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-188">(Optional) At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="c4eba-189">[ \*\* \@ プロパティ**] に**partition_options**の値を指定し、[ \*\* \@ 値**] に適切な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4eba-189">Specify a value of **partition_options** for **\@property** and the appropriate value for **\@value**.</span></span> <span data-ttu-id="c4eba-190">このフィルター選択オプションの定義については、「 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-190">See [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) for definitions of these filtering options.</span></span>  
  
5.  <span data-ttu-id="c4eba-191">(省略可) 必要に応じてスナップショット エージェントを開始し、スナップショットを再生成してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-191">(Optional) Start the Snapshot Agent to regenerate the snapshot if necessary.</span></span> <span data-ttu-id="c4eba-192">新しいスナップショットの生成が必要な変更の詳細については、「[変更パブリケーションとアーティクルのプロパティ](change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4eba-192">For information about which changes require a new snapshot to be generated, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4eba-193">参照</span><span class="sxs-lookup"><span data-stu-id="c4eba-193">See Also</span></span>  
 <span data-ttu-id="c4eba-194">[マージ アーティクル間の一連の結合フィルターを自動的に生成する &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="c4eba-194">[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span></span>  
 <span data-ttu-id="c4eba-195">[マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="c4eba-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 [<span data-ttu-id="c4eba-196">パラメーター化された行フィルター</span><span class="sxs-lookup"><span data-stu-id="c4eba-196">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
