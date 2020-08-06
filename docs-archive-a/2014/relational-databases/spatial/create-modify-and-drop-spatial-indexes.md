---
title: 空間インデックスの作成、変更、および削除 | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], creating
- spatial indexes [SQL Server], dropping
- spatial indexes [SQL Server], creating
- indexes [SQL Server], dropping
- indexes [SQL Server], modifying
- spatial indexes [SQL Server], modifying
ms.assetid: 00c1b927-8ec5-44cf-87c2-c8de59745735
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 88de17e8c487d9a965f2e236edac064dc2fe4c7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632316"
---
# <a name="create-modify-and-drop-spatial-indexes"></a><span data-ttu-id="3e770-102">空間インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3e770-102">Create, Modify, and Drop Spatial Indexes</span></span>
  <span data-ttu-id="3e770-103">空間インデックスは、 `geometry` `geography` データ型またはデータ型の列 (*空間列*) に対して、特定の操作をより効率的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e770-103">A spatial index can more efficiently perform certain operations on a column of the `geometry` or `geography` data type (a *spatial column*).</span></span> <span data-ttu-id="3e770-104">1 つの空間列に対して複数の空間インデックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e770-104">More than one spatial index can be specified on a spatial column.</span></span> <span data-ttu-id="3e770-105">たとえば、1 つの列の異なるテセレーション パラメーターのインデックスを作成する場合などに便利です。</span><span class="sxs-lookup"><span data-stu-id="3e770-105">This is useful, for example, for indexing different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="3e770-106">空間インデックスの作成にはいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="3e770-106">There are a number of restrictions on creating spatial indexes.</span></span> <span data-ttu-id="3e770-107">詳細については、このトピックの「 [空間インデックスに関する制限](#restrictions) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e770-107">For more information, see [Restrictions on Spatial Indexes](#restrictions) in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e770-108">空間インデックスとパーティションやファイル グループとの関係については、「 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)」の「解説」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3e770-108">For information about the relationship of spatial indexes to partition and to filegroups, see the "Remarks" section in [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
##  <a name="creating-modifying-and-dropping-spatial-indexes"></a><a name="creating"></a> <span data-ttu-id="3e770-109">空間インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3e770-109">Creating, Modifying, and Dropping Spatial Indexes</span></span>  
  
###  <a name="to-create-a-spatial-index"></a><a name="create"></a> <span data-ttu-id="3e770-110">空間インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="3e770-110">To create a spatial index</span></span>  
 <span data-ttu-id="3e770-111">**Transact-SQL を使用して空間インデックスを作成するには**</span><span class="sxs-lookup"><span data-stu-id="3e770-111">**To create a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="3e770-112">CREATE SPATIAL INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3e770-112">CREATE SPATIAL INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-spatial-index-transact-sql)  
  
 <span data-ttu-id="3e770-113">**Management Studio の [新しいインデックス] ダイアログ ボックスを使用して空間インデックスを作成するには**</span><span class="sxs-lookup"><span data-stu-id="3e770-113">**To create a spatial index by using the New Index dialog box in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-management-studio"></a><span data-ttu-id="3e770-114">Management Studio で空間インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="3e770-114">To create a spatial index in Management Studio</span></span>  
  
1.  <span data-ttu-id="3e770-115">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="3e770-115">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3e770-116">**[データベース]** を展開し、指定されたインデックスを含むテーブルが格納されたデータベースを展開して、 **[テーブル]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3e770-116">Expand **Databases**, expand the database that contains the table with the specified index, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="3e770-117">インデックスを作成するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="3e770-117">Expand the table for which you want to create the index.</span></span>  
  
4.  <span data-ttu-id="3e770-118">**[インデックス]** を右クリックして **[新しいインデックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-118">Right-click **Indexes** and select **New Index**.</span></span>  
  
5.  <span data-ttu-id="3e770-119">**[インデックス名]** フィールドにインデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3e770-119">In the **Index name** field, enter a name for the index.</span></span>  
  
6.  <span data-ttu-id="3e770-120">**[インデックスの種類]** ボックスの一覧の **[空間]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-120">In the **Index type** drop-down list, select **Spatial**.</span></span>  
  
7.  <span data-ttu-id="3e770-121">インデックスを作成する空間列を指定するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-121">To specify the spatial column that you want to index, click **Add**.</span></span>  
  
8.  <span data-ttu-id="3e770-122">**[から列を選択** *\<table name>* ] ダイアログボックスで、型または型の列を選択し `geometry` `geography` ます。対応するチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3e770-122">In the **Select Columns from** *\<table name>* dialog box, select a column of type `geometry` or `geography` by selecting the corresponding check box.</span></span> <span data-ttu-id="3e770-123">その他の空間列は編集できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3e770-123">Any other spatial columns then become uneditable.</span></span> <span data-ttu-id="3e770-124">別の空間列を選択するには、先に現在選択されている列の選択を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e770-124">If you want to select a different spatial column, you must first clear the currently selected column.</span></span> <span data-ttu-id="3e770-125">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-125">When finished, click **OK**.</span></span>  
  
9. <span data-ttu-id="3e770-126">**[インデックス キー列]** グリッドで、選択した列を確認します。</span><span class="sxs-lookup"><span data-stu-id="3e770-126">Verify your column selection in the **Index key columns** grid.</span></span>  
  
10. <span data-ttu-id="3e770-127">**[インデックスのプロパティ]** ダイアログ ボックスの **[ページの選択]** ペインで、 **[空間]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-127">In the **Select a page** pane of the **Index Properties** dialog box, click **Spatial**.</span></span>  
  
11. <span data-ttu-id="3e770-128">**[空間]** ページで、インデックスの空間プロパティに対して使用する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3e770-128">On the **Spatial** page, specify the values that you want to use for the spatial properties of the index.</span></span>  
  
     <span data-ttu-id="3e770-129">型の列にインデックスを作成する場合は、 `geometry` 境界ボックスの座標 **( *`X-min`* , *`Y-min`* )** と **( *`X-max`* , *`Y-max`* )** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e770-129">When creating an index on a `geometry` type column, you must specify the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="3e770-130">型の列のインデックスの場合、地理グリッドテセレーション `geography` スキームを指定した後、境界ボックスフィールド**Geography grid**は読み取り専用になります。これは、geography grid テセレーションでは境界ボックスが使用されないためです。</span><span class="sxs-lookup"><span data-stu-id="3e770-130">For an index on a `geography` type column, the bounding-box fields become read-only after you specify the **Geography grid** tessellation scheme, because geography grid tessellation does not use a bounding box.</span></span>  
  
     <span data-ttu-id="3e770-131">また、 **[オブジェクトごとのセル数]** フィールドに既定以外の値を指定したり、テセレーション スキームの任意のレベルのグリッド密度を指定したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3e770-131">Optionally, you can specify nondefault values for the **Cells Per Object** field and for the grid density at any level of the tessellation scheme.</span></span> <span data-ttu-id="3e770-132">オブジェクトごとのセル数の既定値は、 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] では 16、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降では 8 で、 **のグリッド密度の既定値は** [中] [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3e770-132">The default number of cells per object is 16 for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or 8 for [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] or higher, and the default grid density is **Medium** for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span>  
  
     <span data-ttu-id="3e770-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、テセレーション スキームに GEOMETRY_AUTO_GRID または GEOGRAPHY_AUTO_GRID を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="3e770-133">You can select GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID for tessellation scheme in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3e770-134">GEOMETRY_AUTO_GRID または GEOGRAPHY_AUTO_GRID を選択すると、レベル 1、レベル 2、レベル 3、およびレベル 4 のグリッド密度のオプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="3e770-134">When GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID is selected, then Level 1, Level 2, Level 3, and Level 4 grid density options are disabled.</span></span>  
  
     <span data-ttu-id="3e770-135">これらのプロパティの詳細については、「 [[インデックスのプロパティ] の F1 ヘルプ](../indexes/index-properties-f1-help.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3e770-135">For more information about these properties, see [Index Properties F1 Help](../indexes/index-properties-f1-help.md).</span></span>  
  
12. <span data-ttu-id="3e770-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-136">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e770-137">同じ空間列または異なる空間列に別の空間インデックスを作成するには、上の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3e770-137">To create another spatial index on the same or a different spatial column, repeat the preceding steps.</span></span>  
  
  
 <span data-ttu-id="3e770-138">**Management Studio のテーブル デザイナーを使用して空間インデックスを作成するには**</span><span class="sxs-lookup"><span data-stu-id="3e770-138">**To create a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-table-designer"></a><span data-ttu-id="3e770-139">テーブル デザイナーで空間インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="3e770-139">To create a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="3e770-140">オブジェクト エクスプローラーで、空間インデックスを作成するテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-140">In Object Explorer, right-click the table for which you want to create a spatial index, and then click **Design**.</span></span>  
  
     <span data-ttu-id="3e770-141">テーブル デザイナーにテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e770-141">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="3e770-142">インデックスを作成する `geometry` 列または `geography` 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e770-142">Select a `geometry` or `geography` column for the index.</span></span>  
  
3.  <span data-ttu-id="3e770-143">**[テーブル デザイナー]** メニューの **[空間インデックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-143">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
4.  <span data-ttu-id="3e770-144">**[空間インデックス]** ダイアログ ボックスの **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-144">In the **Spatial Indexes** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="3e770-145">**[選択された空間インデックス]** ボックスの一覧で新しいインデックスを選択し、右側のグリッドで空間インデックスのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="3e770-145">Select the new index in the **Selected Spatial Index** list, and in the grid to the right, set the properties for the spatial index.</span></span> <span data-ttu-id="3e770-146">プロパティの詳細については、「[[空間インデックス] ダイアログ ボックス &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3e770-146">For information about the properties, see [Spatial Indexes Dialog Box &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
  
###  <a name="to-alter-a-spatial-index"></a><a name="alter"></a> <span data-ttu-id="3e770-147">空間インデックスを変更するには</span><span class="sxs-lookup"><span data-stu-id="3e770-147">To alter a spatial index</span></span>  
  
-   [<span data-ttu-id="3e770-148">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3e770-148">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3e770-149">BOUNDING_BOX や GRID など、空間インデックス固有のオプションを変更するには、DROP_EXISTING = ON を指定する CREATE SPATIAL INDEX ステートメントを使用するか、空間インデックスを削除して新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="3e770-149">To change options that are specific to a spatial index, such as BOUNDING_BOX or GRID, you can either use a CREATE SPATIAL INDEX statement that specifies DROP_EXISTING = ON, or drop the spatial index and create a new one.</span></span> <span data-ttu-id="3e770-150">例については、「 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)」の「解説」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3e770-150">For an example, see [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
-   [<span data-ttu-id="3e770-151">インデックスの変更</span><span class="sxs-lookup"><span data-stu-id="3e770-151">Modify an Index</span></span>](../indexes/modify-an-index.md)  
  
-   [<span data-ttu-id="3e770-152">既存のインデックスの別のファイル グループへの移動</span><span class="sxs-lookup"><span data-stu-id="3e770-152">Move an Existing Index to a Different Filegroup</span></span>](../indexes/move-an-existing-index-to-a-different-filegroup.md)  
  
  
###  <a name="to-drop-a-spatial-index"></a><a name="drop"></a> <span data-ttu-id="3e770-153">空間インデックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="3e770-153">To drop a spatial index</span></span>  
 <span data-ttu-id="3e770-154">**Transact-SQL を使用して空間インデックスを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3e770-154">**To drop a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="3e770-155">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3e770-155">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 <span data-ttu-id="3e770-156">**Management Studio を使用してインデックスを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3e770-156">**To drop an index by using Management Studio**</span></span>  
 [<span data-ttu-id="3e770-157">インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="3e770-157">Delete an Index</span></span>](../indexes/delete-an-index.md)  
  
 <span data-ttu-id="3e770-158">**Management Studio のテーブル デザイナーを使用して空間インデックスを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3e770-158">**To drop a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-drop-a-spatial-index-in-table-designer"></a><span data-ttu-id="3e770-159">テーブル デザイナーで空間インデックスを削除するには</span><span class="sxs-lookup"><span data-stu-id="3e770-159">To drop a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="3e770-160">オブジェクト エクスプローラーで、削除する空間インデックスが含まれているテーブルを右クリックし、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-160">In Object Explorer, right-click the table with the spatial index you want to delete and click **Design**.</span></span>  
  
     <span data-ttu-id="3e770-161">テーブル デザイナーにテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e770-161">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="3e770-162">**[テーブル デザイナー]** メニューの **[空間インデックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-162">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
     <span data-ttu-id="3e770-163">**[空間インデックス]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e770-163">The **Spatial Index** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3e770-164">**[選択された空間インデックス]** 列で削除するインデックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-164">Click the index you want to delete in the **Selected Spatial Index** column.</span></span>  
  
4.  <span data-ttu-id="3e770-165">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e770-165">Click **Delete**.</span></span>  
  
  
##  <a name="restrictions-on-spatial-indexes"></a><a name="restrictions"></a> <span data-ttu-id="3e770-166">空間インデックスに関する制限</span><span class="sxs-lookup"><span data-stu-id="3e770-166">Restrictions on Spatial Indexes</span></span>  
 <span data-ttu-id="3e770-167">空間インデックスを作成できるのは、`geometry` 型か `geography` 型の列だけです。</span><span class="sxs-lookup"><span data-stu-id="3e770-167">A spatial index can be created only on a column of type `geometry` or `geography`.</span></span>  
  
### <a name="table-and-view-restrictions"></a><span data-ttu-id="3e770-168">テーブルおよびビューの制限</span><span class="sxs-lookup"><span data-stu-id="3e770-168">Table and View Restrictions</span></span>  
 <span data-ttu-id="3e770-169">空間インデックスは、主キーがあるテーブルでしか定義できません。</span><span class="sxs-lookup"><span data-stu-id="3e770-169">Spatial indexes can be defined only on a table that has a primary key.</span></span> <span data-ttu-id="3e770-170">テーブルの主キー列の最大数は 15 です。</span><span class="sxs-lookup"><span data-stu-id="3e770-170">The maximum number of primary key columns on the table is 15.</span></span>  
  
 <span data-ttu-id="3e770-171">インデックス キー レコードの最大サイズは 895 バイトです。</span><span class="sxs-lookup"><span data-stu-id="3e770-171">The maximum size of index key records is 895 bytes.</span></span> <span data-ttu-id="3e770-172">このサイズを超えるとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3e770-172">Larger sizes raise an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e770-173">主キーのメタデータは、テーブルに空間インデックスが定義されていると変更できません。</span><span class="sxs-lookup"><span data-stu-id="3e770-173">Primary key metadata cannot be changed while a spatial index is defined on a table.</span></span>  
  
 <span data-ttu-id="3e770-174">インデックス付きビューに対して空間インデックスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3e770-174">Spatial indexes cannot be specified on indexed views.</span></span>  
  
### <a name="multiple-spatial-index-restrictions"></a><span data-ttu-id="3e770-175">複数の空間インデックスに関する制限</span><span class="sxs-lookup"><span data-stu-id="3e770-175">Multiple Spatial Index Restrictions</span></span>  
 <span data-ttu-id="3e770-176">空間インデックスは、サポートされているテーブルの任意の空間列に 249 個まで作成できます。</span><span class="sxs-lookup"><span data-stu-id="3e770-176">You can create up to 249 spatial indexes on any of the spatial columns in a supported table.</span></span> <span data-ttu-id="3e770-177">同じ空間列に複数の空間インデックスを作成すると、1 つの列の異なるテセレーション パラメーターのインデックスを作成する場合などに便利です。</span><span class="sxs-lookup"><span data-stu-id="3e770-177">Creating more than one spatial index on the same spatial column can be useful, for example, to index different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="3e770-178">一度に作成できる空間インデックスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="3e770-178">You can create only one spatial index at a time.</span></span>  
  
### <a name="spatial-indexes-and-process-parallelism"></a><span data-ttu-id="3e770-179">空間インデックスとプロセスの並列処理</span><span class="sxs-lookup"><span data-stu-id="3e770-179">Spatial Indexes and Process Parallelism</span></span>  
 <span data-ttu-id="3e770-180">インデックスの構築では、プロセスの並列処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e770-180">An index build can use available process parallelism.</span></span>  
  
### <a name="version-restrictions"></a><span data-ttu-id="3e770-181">バージョンの制限事項</span><span class="sxs-lookup"><span data-stu-id="3e770-181">Version Restrictions</span></span>  
 <span data-ttu-id="3e770-182">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] で導入された空間テセレーションは、 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] または [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]にレプリケートできません。</span><span class="sxs-lookup"><span data-stu-id="3e770-182">Spatial tessellations introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] cannot be replicated to [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="3e770-183">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] または [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] のデータベースとの下位互換性が必要条件である場合は、空間インデックスで [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] または [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 空間テセレーションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e770-183">You must use [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] spatial tessellations for spatial indexes when backward compatibility with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] databases is a requirement.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="3e770-184">参照</span><span class="sxs-lookup"><span data-stu-id="3e770-184">See Also</span></span>  
 [<span data-ttu-id="3e770-185">空間インデックスの概要</span><span class="sxs-lookup"><span data-stu-id="3e770-185">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
  
  
