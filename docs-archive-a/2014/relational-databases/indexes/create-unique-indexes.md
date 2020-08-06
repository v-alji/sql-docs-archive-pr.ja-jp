---
title: Unique インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- unique indexes
- designing indexes [SQL Server], unique
- clustered indexes, unique
- indexes [SQL Server], unique
- nonclustered indexes [SQL Server], unique
- unique indexes, design guidelines
ms.assetid: 56b5982e-cb94-46c0-8fbb-772fc275354a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c96c4e17a8ce0863452db171302d650f6114919
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740942"
---
# <a name="create-unique-indexes"></a><span data-ttu-id="a2407-102">一意のインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="a2407-102">Create Unique Indexes</span></span>
  <span data-ttu-id="a2407-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、テーブルに一意のインデックスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2407-103">This topic describes how to create a unique index on a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a2407-104">一意インデックスを使用すると、インデックス キーの値が重複することがないので、テーブルのすべての行を一意にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a2407-104">A unique index guarantees that the index key contains no duplicate values and therefore every row in the table is in some way unique.</span></span> <span data-ttu-id="a2407-105">UNIQUE 制約を作成することと、制約に依存しない一意インデックスを作成することの間に大きな違いはありません。</span><span class="sxs-lookup"><span data-stu-id="a2407-105">There are no significant differences between creating a UNIQUE constraint and creating a unique index that is independent of a constraint.</span></span> <span data-ttu-id="a2407-106">データ検証動作も同じ方式で行われます。また、クエリ オプティマイザーでは、制約によって作成された一意インデックスと手動で作成された一意インデックスは区別されません。</span><span class="sxs-lookup"><span data-stu-id="a2407-106">Data validation occurs in the same manner, and the query optimizer does not differentiate between a unique index created by a constraint or manually created.</span></span> <span data-ttu-id="a2407-107">ただし、列に UNIQUE 制約を作成すると、インデックスの目的が明確になります。</span><span class="sxs-lookup"><span data-stu-id="a2407-107">However, creating a UNIQUE constraint on the column makes the objective of the index clear.</span></span> <span data-ttu-id="a2407-108">UNIQUE 制約の詳細については、「 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2407-108">For more information on UNIQUE constraints, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="a2407-109">一意のインデックスを作成するとき、重複するキーを無視するオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a2407-109">When you create a unique index, you can set an option to ignore duplicate keys.</span></span> <span data-ttu-id="a2407-110">このオプションを **[はい]** に設定して、複数行に影響するデータを INSERT ステートメントによって追加して重複キーを作成しようとすると、重複を含む行は追加されません。</span><span class="sxs-lookup"><span data-stu-id="a2407-110">If this option is set to **Yes** and you attempt to create duplicate keys by adding data that affects multiple rows (with the INSERT statement), the row containing a duplicate is not added.</span></span> <span data-ttu-id="a2407-111">**[いいえ]** に設定すると、この挿入操作全体が失敗となり、データはすべてロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="a2407-111">If it is set to **No**, the entire insert operation fails and all the data is rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2407-112">1 つの列の複数行に NULL がある場合は、その列には一意のインデックスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="a2407-112">You cannot create a unique index on a single column if that column contains NULL in more than one row.</span></span> <span data-ttu-id="a2407-113">同様に、複数の列の複数行に NULL がある場合は、その列の組み合わせに一意のインデックスを作成することもできません。</span><span class="sxs-lookup"><span data-stu-id="a2407-113">Similarly, you cannot create a unique index on multiple columns if the combination of columns contains NULL in more than one row.</span></span> <span data-ttu-id="a2407-114">インデックスを作成する場合、これらの NULL は重複した値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="a2407-114">These are treated as duplicate values for indexing purposes.</span></span>  
  
 <span data-ttu-id="a2407-115">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a2407-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2407-116">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a2407-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a2407-117">一意インデックスの利点</span><span class="sxs-lookup"><span data-stu-id="a2407-117">Benefits of a Unique Index</span></span>](#Benefits)  
  
     [<span data-ttu-id="a2407-118">一般的な実装</span><span class="sxs-lookup"><span data-stu-id="a2407-118">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="a2407-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2407-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a2407-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2407-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a2407-121">**以下を使用してテーブルに一意のインデックスを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="a2407-121">**To create a unique index on a table, using:**</span></span>  
  
     [<span data-ttu-id="a2407-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2407-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a2407-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2407-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2407-124">はじめに</span><span class="sxs-lookup"><span data-stu-id="a2407-124">Before You Begin</span></span>  
  
###  <a name="benefits-of-a-unique-index"></a><a name="Benefits"></a> <span data-ttu-id="a2407-125">一意インデックスの利点</span><span class="sxs-lookup"><span data-stu-id="a2407-125">Benefits of a Unique Index</span></span>  
  
-   <span data-ttu-id="a2407-126">複数列の一意なインデックスにより、インデックス キーのそれぞれの値の組み合わせが一意であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-126">Multicolumn unique indexes guarantee that each combination of values in the index key is unique.</span></span> <span data-ttu-id="a2407-127">たとえば、 **LastName**列、 **FirstName**列、および **MiddleName** 列の組み合わせに一意インデックスを作成した場合、テーブル内の 2 つの行がこれらの列に対して同じ値の組み合わせを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="a2407-127">For example, if a unique index is created on a combination of **LastName**, **FirstName**, and **MiddleName** columns, no two rows in the table could have the same combination of values for these columns.</span></span>  
  
-   <span data-ttu-id="a2407-128">列のデータが一意である場合、1 つのテーブルに 1 つの一意クラスター化インデックスと、複数の一意非クラスター化インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a2407-128">Provided that the data in each column is unique, you can create both a unique clustered index and multiple unique nonclustered indexes on the same table.</span></span>  
  
-   <span data-ttu-id="a2407-129">一意インデックスにより、定義された列のデータ整合性が保証されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-129">Unique indexes ensure the data integrity of the defined columns.</span></span>  
  
-   <span data-ttu-id="a2407-130">一意インデックスにより、より効率的な実行プランを生成できるクエリ オプティマイザーの役に立つ追加情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-130">Unique indexes provide additional information helpful to the query optimizer that can produce more efficient execution plans.</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="a2407-131">一般的な実装</span><span class="sxs-lookup"><span data-stu-id="a2407-131">Typical Implementations</span></span>  
 <span data-ttu-id="a2407-132">一意インデックスは、次のように実装されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-132">Unique indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="a2407-133">**PRIMARY KEY 制約または UNIQUE 制約**</span><span class="sxs-lookup"><span data-stu-id="a2407-133">**PRIMARY KEY or UNIQUE constraint**</span></span>  
  
     <span data-ttu-id="a2407-134">PRIMARY KEY 制約を作成すると、テーブルにクラスター化インデックスが存在せず、一意の非クラスター化インデックスを指定しなかった場合、列に一意のクラスター化インデックスが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-134">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="a2407-135">主キー列には NULL 値を指定できません。</span><span class="sxs-lookup"><span data-stu-id="a2407-135">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="a2407-136">UNIQUE 制約を作成すると、既定では、一意な非クラスター化インデックスが作成され、UNIQUE 制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-136">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="a2407-137">テーブルにクラスター化インデックスが存在しない場合は、一意なクラスター化インデックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2407-137">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="a2407-138">詳細については、「 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) 」および「 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2407-138">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) and [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).</span></span>  
  
-   <span data-ttu-id="a2407-139">**制約に依存しないインデックス**</span><span class="sxs-lookup"><span data-stu-id="a2407-139">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="a2407-140">テーブルでは、一意の非クラスター化インデックスを複数定義できます。</span><span class="sxs-lookup"><span data-stu-id="a2407-140">Multiple unique nonclustered indexes can be defined on a table.</span></span>  
  
     <span data-ttu-id="a2407-141">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2407-141">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="a2407-142">**インデックス付きビュー**</span><span class="sxs-lookup"><span data-stu-id="a2407-142">**Indexed view**</span></span>  
  
     <span data-ttu-id="a2407-143">インデックス付きビューを作成するには、1 つ以上のビュー列で一意のクラスター化インデックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="a2407-143">To create an indexed view, a unique clustered index is defined on one or more view columns.</span></span> <span data-ttu-id="a2407-144">このビューを実行すると、テーブル データがクラスター化インデックスに格納されるときと同じ方法で、結果セットがインデックスのリーフ レベルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a2407-144">The view is executed and the result set is stored in the leaf level of the index in the same way table data is stored in a clustered index.</span></span> <span data-ttu-id="a2407-145">詳細については、「 [インデックス付きビューの作成](../views/views.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2407-145">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a2407-146">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2407-146">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a2407-147">重複するキー値がデータに存在する場合は、一意インデックス、UNIQUE 制約、または PRIMARY KEY 制約を作成できません。</span><span class="sxs-lookup"><span data-stu-id="a2407-147">A unique index, UNIQUE constraint, or PRIMARY KEY constraint cannot be created if duplicate key values exist in the data.</span></span>  
  
-   <span data-ttu-id="a2407-148">一意非クラスター化インデックスには、付加非キー列を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a2407-148">A unique nonclustered index can contain included nonkey columns.</span></span> <span data-ttu-id="a2407-149">詳細については、「 [付加列インデックスの作成](create-indexes-with-included-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2407-149">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a2407-150">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2407-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a2407-151">Permissions</span><span class="sxs-lookup"><span data-stu-id="a2407-151">Permissions</span></span>  
 <span data-ttu-id="a2407-152">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2407-152">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="a2407-153">実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2407-153">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a2407-154">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a2407-154">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-index-by-using-the-table-designer"></a><span data-ttu-id="a2407-155">テーブル デザイナーを使用して一意のインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="a2407-155">To create a unique index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="a2407-156">オブジェクト エクスプローラーで、一意のインデックスを作成するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2407-156">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="a2407-157">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2407-157">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="a2407-158">一意のインデックスを作成するテーブルを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-158">Right-click the table on which you want to create a unique index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="a2407-159">**[テーブル デザイナー]** メニューの **[インデックス/キー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-159">On the **Table Designer** menu, select **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="a2407-160">**[インデックス/キー]** ダイアログ ボックスで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-160">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="a2407-161">**[Selected Primary/Unique Key or Index (選択された主/一意キーまたはインデックス)]** ボックスで、新しいインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-161">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="a2407-162">メイン グリッドの **[(全般)]** で、 **[種類]** を選択し、一覧から **[インデックス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-162">In the main grid, under **(General)**, select **Type** and then choose **Index** from the list.</span></span>  
  
8.  <span data-ttu-id="a2407-163">**[列]** を選択し、省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-163">Select **Columns**, and then click the ellipsis **(...)**.</span></span>  
  
9. <span data-ttu-id="a2407-164">**[インデックスの列]** ダイアログ ボックスの **[列名]** で、インデックスを作成する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-164">In the **Index Columns** dialog box, under **Column Name**, select the columns you want to index.</span></span> <span data-ttu-id="a2407-165">16 列まで選択できます。</span><span class="sxs-lookup"><span data-stu-id="a2407-165">You can select up to 16 columns.</span></span> <span data-ttu-id="a2407-166">ただし、最適なパフォーマンスを得るには、1 つのインデックスにつき 1 列または 2 列に抑えます。</span><span class="sxs-lookup"><span data-stu-id="a2407-166">For optimal performance, select only one or two columns per index.</span></span> <span data-ttu-id="a2407-167">選択した各列の値の並べ方を昇順または降順のどちらかに指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2407-167">For each column you select, indicate whether the index arranges values of this column in ascending or descending order.</span></span>  
  
10. <span data-ttu-id="a2407-168">インデックスを作成するすべての列を選択したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-168">When all columns for the index are selected, click **OK**.</span></span>  
  
11. <span data-ttu-id="a2407-169">グリッドの **[(全般)]** で、 **[一意である]** を選択し、一覧から **[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-169">In the grid, under **(General)**, select **Is Unique** and then choose **Yes** from the list.</span></span>  
  
12. <span data-ttu-id="a2407-170">省略可能: メイン グリッドの **[テーブル デザイナー]** で、select **[重複するキーを無視]** を選択し、一覧から **[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-170">Optional: In the main grid, under **Table Designer**, select **Ignore Duplicate Keys** and then choose **Yes** from the list.</span></span> <span data-ttu-id="a2407-171">この操作は、一意のインデックスに重複キーが作成される可能性のあるデータを追加する操作を無視する場合に実行します。</span><span class="sxs-lookup"><span data-stu-id="a2407-171">Do this if you want to ignore attempts to add data that would create a duplicate key in the unique index.</span></span>  
  
13. <span data-ttu-id="a2407-172">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-172">Click **Close**.</span></span>  
  
14. <span data-ttu-id="a2407-173">**[ファイル]** メニューの **テーブル名**_の保存]_ をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-173">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="create-a-unique-index-by-using-object-explorer"></a><span data-ttu-id="a2407-174">オブジェクト エクスプ ローラーを使用して一意のインデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="a2407-174">Create a unique index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="a2407-175">オブジェクト エクスプローラーで、一意のインデックスを作成するテーブルが格納されているデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2407-175">In Object Explorer, expand the database that contains the table on which you want to create a unique index.</span></span>  
  
2.  <span data-ttu-id="a2407-176">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2407-176">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="a2407-177">一意のインデックスを作成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2407-177">Expand the table on which you want to create a unique index.</span></span>  
  
4.  <span data-ttu-id="a2407-178">**[インデックス]** フォルダーを右クリックし、 **[新しいインデックス]** をポイントし、 **[非クラスター化インデックス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2407-178">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="a2407-179">**[新しいインデックス]** ダイアログ ボックスの **[全般]** ページで、 **[インデックス名]** ボックスに新しいインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a2407-179">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="a2407-180">**[一意]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a2407-180">Select the **Unique** check box.</span></span>  
  
7.  <span data-ttu-id="a2407-181">**[インデックス キー列]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-181">Under **Index key columns**, click **Add...**.</span></span>  
  
8.  <span data-ttu-id="a2407-182">[Table_name**から列を選択**_table_name_ ] ダイアログボックスで、一意のインデックスに追加するテーブル列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a2407-182">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
9. <span data-ttu-id="a2407-183">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-183">Click **OK**.</span></span>  
  
10. <span data-ttu-id="a2407-184">**[新しいインデックス]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-184">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a2407-185">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a2407-185">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-index-on-a-table"></a><span data-ttu-id="a2407-186">テーブルに一意のインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="a2407-186">To create a unique index on a table</span></span>  
  
1.  <span data-ttu-id="a2407-187">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a2407-187">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a2407-188">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-188">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a2407-189">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2407-189">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named AK_UnitMeasure_Name and delete it if found  
    IF EXISTS (SELECT name from sys.indexes  
               WHERE name = N'AK_UnitMeasure_Name')   
       DROP INDEX AK_UnitMeasure_Name ON Production.UnitMeasure;   
    GO  
    -- Create a unique index called AK_UnitMeasure_Name  
    -- on the Production.UnitMeasure table using the Name column.  
    CREATE UNIQUE INDEX AK_UnitMeasure_Name   
       ON Production.UnitMeasure (Name);   
    GO  
    ```  
  
 <span data-ttu-id="a2407-190">詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2407-190">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
