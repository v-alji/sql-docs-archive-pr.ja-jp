---
title: '[インデックスのプロパティ] の F1 ヘルプ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.storage.f1
- sql12.swb.indexproperties.columns.f1
- sql12.swb.indexproperties.partitions.f1
- sql12.swb.indexproperties.general.f1
- sql12.swb.indexproperties.filter.f1
- sql12.swb.indexproperties.options.f1
- sql12.swb.indexproperties.spatial.f1
ms.assetid: 45efd81a-3796-4b04-b0cc-f3deec94c733
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 390a63d21dc72e052017f2d30b061d71de863bc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742042"
---
# <a name="index-properties-f1-help"></a><span data-ttu-id="130c6-102">[インデックスのプロパティ] の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="130c6-102">Index Properties F1 Help</span></span>
  <span data-ttu-id="130c6-103">このトピックのセクションでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のダイアログを使用して取得できる各種のインデックス プロパティを参照しています。</span><span class="sxs-lookup"><span data-stu-id="130c6-103">The sections in this topic refer to various index properties that are available by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialogs.</span></span>  
  
 <span data-ttu-id="130c6-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="130c6-104">**In This Topic:**</span></span>  
  
 <span data-ttu-id="130c6-105">[[インデックスのプロパティ] の [全般] ページ](#General)</span><span class="sxs-lookup"><span data-stu-id="130c6-105">[Index Properties General Page](#General)</span></span>  
  
 [<span data-ttu-id="130c6-106">から (インデックス) 列を選択 ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="130c6-106">Select (Index) Columns Dialog Box</span></span>](#Columns)  
  
 <span data-ttu-id="130c6-107">[[インデックスのプロパティ] の [ストレージ] ページ](#Storage)</span><span class="sxs-lookup"><span data-stu-id="130c6-107">[Index Properties Storage Page](#Storage)</span></span>  
  
 <span data-ttu-id="130c6-108">[[インデックスのプロパティ] の [空間] ページ](#Spatial)</span><span class="sxs-lookup"><span data-stu-id="130c6-108">[Index Properties Spatial Page](#Spatial)</span></span>  
  
 <span data-ttu-id="130c6-109">[[インデックスのプロパティ] の [フィルター] ページ](#Filter)</span><span class="sxs-lookup"><span data-stu-id="130c6-109">[Index Properties Filter Page](#Filter)</span></span>  
  
##  <a name="index-properties-general-page"></a><a name="General"></a> <span data-ttu-id="130c6-110">[インデックスのプロパティ] の [全般] ページ</span><span class="sxs-lookup"><span data-stu-id="130c6-110">Index Properties General Page</span></span>  
 <span data-ttu-id="130c6-111">[全般] ページを使用すると、選択されているテーブルまたはビューのインデックスのプロパティを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-111">Use the General page to view or modify index properties for the selected table or view.</span></span> <span data-ttu-id="130c6-112">各ページのオプションは、選択されたインデックスの種類に応じて異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="130c6-112">The options for each page may change based on the type of index selected.</span></span>  
  
 <span data-ttu-id="130c6-113">**[テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="130c6-113">**Table name**</span></span>  
 <span data-ttu-id="130c6-114">インデックスが作成されているテーブルまたはビューの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-114">Displays the name of the table or view that the index was created on.</span></span> <span data-ttu-id="130c6-115">このフィールドは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="130c6-115">This field is read-only.</span></span> <span data-ttu-id="130c6-116">別のテーブルを選択するには、[インデックスのプロパティ] ページを閉じてから適切なテーブルを選択し、再び [インデックスのプロパティ] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="130c6-116">To select a different table, close the Index Properties page, select the correct table, and then open the Index Properties page again.</span></span>  
  
 <span data-ttu-id="130c6-117">インデックス付きビューに対して空間インデックスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="130c6-117">Spatial indexes cannot be specified on indexed views.</span></span> <span data-ttu-id="130c6-118">空間インデックスは、主キーがあるテーブルでしか定義できません。</span><span class="sxs-lookup"><span data-stu-id="130c6-118">Spatial indexes can be defined only for a table that has a primary key.</span></span> <span data-ttu-id="130c6-119">テーブルの主キー列の最大数は 15 です。</span><span class="sxs-lookup"><span data-stu-id="130c6-119">The maximum number of primary key columns on the table is 15.</span></span> <span data-ttu-id="130c6-120">主キー列の組み合わされた行あたりのサイズは、最大 895 バイトに制限されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-120">The combined per-row size of the primary-key columns is limited to a maximum of 895 bytes.</span></span>  
  
 <span data-ttu-id="130c6-121">**[インデックス名]**</span><span class="sxs-lookup"><span data-stu-id="130c6-121">**Index name**</span></span>  
 <span data-ttu-id="130c6-122">インデックスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-122">Displays the name of the index.</span></span> <span data-ttu-id="130c6-123">このフィールドは、既存のインデックスに関しては読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="130c6-123">This field is read-only for an existing index.</span></span> <span data-ttu-id="130c6-124">新しいインデックスを作成する場合は、インデックスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="130c6-124">When creating a new index, type the name of the index.</span></span>  
  
 <span data-ttu-id="130c6-125">**[インデックスの種類]**</span><span class="sxs-lookup"><span data-stu-id="130c6-125">**Index type**</span></span>  
 <span data-ttu-id="130c6-126">インデックスの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-126">Indicates the type of index.</span></span> <span data-ttu-id="130c6-127">新しいインデックスの場合は、ダイアログ ボックスを開いたときに選択されたインデックスの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-127">For new indexes, indicates the type of index selected when opening the dialog box.</span></span> <span data-ttu-id="130c6-128">インデックスは、 **[クラスター化]** 、 **[非クラスター化]** 、 **[プライマリ XML]** 、 **[セカンダリ XML]** 、 **[空間]** 、 **[クラスター化列ストア]** 、 **[非クラスター化列ストア]** にすることができます。</span><span class="sxs-lookup"><span data-stu-id="130c6-128">Indexes can be: **Clustered**, **Nonclustered**, **Primary XML**, **Secondary XML**, **Spatial**, **Clustered columnstore**, or **Nonclustered Columnstore**.</span></span>  
  
 <span data-ttu-id="130c6-129">**メモ** クラスター化インデックスは、各テーブルに 1 つだけ許可されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-129">**Note** Only one clustered index is allowed for each table.</span></span> <span data-ttu-id="130c6-130">xVelocity メモリ最適化列ストア インデックスは、各テーブルに 1 つだけ許可されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-130">Only one xVelocity memory optimized columnstore index is allowed for each table.</span></span>  
  
 <span data-ttu-id="130c6-131">**[一意]**</span><span class="sxs-lookup"><span data-stu-id="130c6-131">**Unique**</span></span>  
 <span data-ttu-id="130c6-132">このチェック ボックスをオンにすると、インデックスは一意になります。</span><span class="sxs-lookup"><span data-stu-id="130c6-132">Selecting this check box makes the index unique.</span></span> <span data-ttu-id="130c6-133">2 つの行が同じインデックス値を持つことは許されません。</span><span class="sxs-lookup"><span data-stu-id="130c6-133">No two rows are permitted to have the same index value.</span></span> <span data-ttu-id="130c6-134">既定では、このチェック ボックスはオフに設定されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-134">By default, this check box is cleared.</span></span> <span data-ttu-id="130c6-135">既存のインデックスを変更するときに 2 つの行が同じ値を持つ場合、インデックスの作成は失敗します。</span><span class="sxs-lookup"><span data-stu-id="130c6-135">When modifying an existing index, index creation will fail if two rows have the same value.</span></span> <span data-ttu-id="130c6-136">NULL が許容される列の場合、一意なインデックスとして 1 つの NULL 値が許容されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-136">For columns where NULL is permitted, a unique index permits one NULL value.</span></span>  
  
 <span data-ttu-id="130c6-137">**[インデックスの種類]** フィールドで **[空間]** を選択すると、 **[一意]** チェック ボックスは淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="130c6-137">If you select **Spatial** in the **Index type** field, the **Unique** check box is dimmed.</span></span>  
  
 <span data-ttu-id="130c6-138">**[インデックス キー列]**</span><span class="sxs-lookup"><span data-stu-id="130c6-138">**Index key columns**</span></span>  
 <span data-ttu-id="130c6-139">目的の列を **[インデックス キー列]** グリッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="130c6-139">Add the desired columns to the **Index key columns** grid.</span></span> <span data-ttu-id="130c6-140">複数の列を追加する場合は、適切な順序で列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="130c6-140">When more than one column is added, the columns must be listed in the order desired.</span></span> <span data-ttu-id="130c6-141">インデックス内の列の順序は、インデックスのパフォーマンスに大きな影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="130c6-141">The column order in an index can have a great impact on the index performance.</span></span>  
  
 <span data-ttu-id="130c6-142">1 つの複合インデックスを構成できる列は最大で 16 個です。</span><span class="sxs-lookup"><span data-stu-id="130c6-142">No more than 16 columns can participate in a single composite index.</span></span> <span data-ttu-id="130c6-143">列が 16 より多い場合については、このトピックの最後にある付加列の説明をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="130c6-143">For greater than 16 columns, see included columns at the end of this topic.</span></span>  
  
 <span data-ttu-id="130c6-144">空間インデックスを定義できるのは、空間データ型を含む単一の列 ( *空間列*) だけです。</span><span class="sxs-lookup"><span data-stu-id="130c6-144">A spatial index can be defined only on a single column that contains a spatial data type (a *spatial column*).</span></span>  
  
 <span data-ttu-id="130c6-145">**名前**</span><span class="sxs-lookup"><span data-stu-id="130c6-145">**Name**</span></span>  
 <span data-ttu-id="130c6-146">インデックス キーを構成する列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-146">Displays the name of the column that participates in the index key.</span></span>  
  
 <span data-ttu-id="130c6-147">**[並べ替え順序]**</span><span class="sxs-lookup"><span data-stu-id="130c6-147">**Sort Order**</span></span>  
 <span data-ttu-id="130c6-148">選択されているインデックス列の並べ替え方向として、 **[昇順]** または **[降順]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-148">Specifies the sort direction of the selected index column, either **Ascending** or **Descending**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="130c6-149">インデックスの種類が **[プライマリ XML]** または **[空間]** の場合、この列はテーブルに表示されません。</span><span class="sxs-lookup"><span data-stu-id="130c6-149">If the index type is **Primary XML** or **Spatial**, this column does not appear in the table.</span></span>  
  
 <span data-ttu-id="130c6-150">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="130c6-150">**Data Type**</span></span>  
 <span data-ttu-id="130c6-151">データ型情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-151">Displays the data type information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="130c6-152">テーブル列が計算列の場合、 **[データ型]** に "計算列" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-152">If the table column is a computed column, **Data type** displays "computed column."</span></span>  
  
 <span data-ttu-id="130c6-153">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="130c6-153">**Size**</span></span>  
 <span data-ttu-id="130c6-154">列データ型を格納するために必要な最大バイト数を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-154">Displays the maximum number of bytes required to store the column data type.</span></span> <span data-ttu-id="130c6-155">空間列または XML 列の場合は、ゼロ (0) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-155">Displays zero (0) for a spatial or XML column.</span></span>  
  
 <span data-ttu-id="130c6-156">**ID**</span><span class="sxs-lookup"><span data-stu-id="130c6-156">**Identity**</span></span>  
 <span data-ttu-id="130c6-157">インデックス キーを構成する列が ID 列であるかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-157">Displays whether the column participating in the index key is an identity column.</span></span>  
  
 <span data-ttu-id="130c6-158">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="130c6-158">**Allow NULLs**</span></span>  
 <span data-ttu-id="130c6-159">NULL 値をテーブルまたはビュー列に格納することがインデックス キーを構成する列で許容されるかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-159">Displays whether the column participating in the index key allows NULL values to be stored in the table or view column.</span></span>  
  
 <span data-ttu-id="130c6-160">**追加**</span><span class="sxs-lookup"><span data-stu-id="130c6-160">**Add**</span></span>  
 <span data-ttu-id="130c6-161">列をインデックス キーに追加します。</span><span class="sxs-lookup"><span data-stu-id="130c6-161">Adds a column to the index key.</span></span> <span data-ttu-id="130c6-162">**[追加]** をクリックすると表示される [ *\<table name>* **から列を選択**] ダイアログ ボックスからテーブル列を選択します。</span><span class="sxs-lookup"><span data-stu-id="130c6-162">Select table columns from the **Select Columns from** *\<table name>* dialog box that appears when you click **Add**.</span></span> <span data-ttu-id="130c6-163">空間インデックスの場合は、1 つの列を選択した後、このボタンが淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="130c6-163">For a spatial index, after you select one column, this button is dimmed.</span></span>  
  
 <span data-ttu-id="130c6-164">**Remove**</span><span class="sxs-lookup"><span data-stu-id="130c6-164">**Remove**</span></span>  
 <span data-ttu-id="130c6-165">選択されている列をインデックス キーから削除します。</span><span class="sxs-lookup"><span data-stu-id="130c6-165">Removes the selected column from participation in the index key.</span></span>  
  
 <span data-ttu-id="130c6-166">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="130c6-166">**Move Up**</span></span>  
 <span data-ttu-id="130c6-167">選択されている列をインデックス キー グリッド内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="130c6-167">Moves the selected column up in the index key grid.</span></span>  
  
 <span data-ttu-id="130c6-168">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="130c6-168">**Move Down**</span></span>  
 <span data-ttu-id="130c6-169">選択されている列をインデックス キー グリッド内で下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="130c6-169">Moves the selected column down in the index key grid.</span></span>  
  
 <span data-ttu-id="130c6-170">**[列ストア列]**</span><span class="sxs-lookup"><span data-stu-id="130c6-170">**Columnstore columns**</span></span>  
 <span data-ttu-id="130c6-171">列ストア インデックスの列を選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="130c6-171">Click **Add** to select columns for the columnstore index.</span></span> <span data-ttu-id="130c6-172">列ストア インデックスに関する制限事項は、「[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-172">For limitations on a columnstore index, see [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>  
  
 <span data-ttu-id="130c6-173">**[付加列]**</span><span class="sxs-lookup"><span data-stu-id="130c6-173">**Included columns**</span></span>  
 <span data-ttu-id="130c6-174">非キー列を非クラスター化インデックスに含めます。</span><span class="sxs-lookup"><span data-stu-id="130c6-174">Include nonkey columns in the nonclustered index.</span></span> <span data-ttu-id="130c6-175">このオプションを選択すると、列を非キー列として非クラスター化インデックスのリーフ レベルに追加することにより、インデックス キーの合計サイズに対する現在のインデックス制限、およびインデックス キーを構成する列の最大数の制限を無視できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-175">This option allows you to bypass the current index limits on the total size of an index key and the maximum number of columns participating in an index key by adding columns as nonkey columns in the leaf level of the nonclustered index.</span></span> <span data-ttu-id="130c6-176">詳細については、「 [付加列インデックスの作成](create-indexes-with-included-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-176">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md)</span></span>  
  
##  <a name="select-index-columns-dialog-box"></a><a name="Columns"></a> <span data-ttu-id="130c6-177">[<table name> から (インデックス) 列を選択] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="130c6-177">Select (Index) Columns Dialog Box</span></span>  
 <span data-ttu-id="130c6-178">このページを使用すると、インデックスを作成または変更するときに **[インデックスのプロパティ]\([全般] ページ)** に列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-178">Use this page to add columns to the **Index Properties General** page when creating or modifying an index.</span></span>  
  
 <span data-ttu-id="130c6-179">**チェック ボックス**</span><span class="sxs-lookup"><span data-stu-id="130c6-179">**Check box**</span></span>  
 <span data-ttu-id="130c6-180">列を選択する場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="130c6-180">Select to add columns.</span></span>  
  
 <span data-ttu-id="130c6-181">**名前**</span><span class="sxs-lookup"><span data-stu-id="130c6-181">**Name**</span></span>  
 <span data-ttu-id="130c6-182">列の名前です。</span><span class="sxs-lookup"><span data-stu-id="130c6-182">Name of the column.</span></span>  
  
 <span data-ttu-id="130c6-183">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="130c6-183">**Data Type**</span></span>  
 <span data-ttu-id="130c6-184">列のデータ型。</span><span class="sxs-lookup"><span data-stu-id="130c6-184">The data type of the column.</span></span>  
  
 <span data-ttu-id="130c6-185">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="130c6-185">**Bytes**</span></span>  
 <span data-ttu-id="130c6-186">列のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="130c6-186">The size of the column in bytes.</span></span>  
  
 <span data-ttu-id="130c6-187">**ID**</span><span class="sxs-lookup"><span data-stu-id="130c6-187">**Identity**</span></span>  
 <span data-ttu-id="130c6-188">列が ID 列の場合は **[はい]** が表示され、列が ID 列でない場合は **[いいえ]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-188">Displays **Yes** for identity columns, and **No** when the column is not an identity column.</span></span>  
  
 <span data-ttu-id="130c6-189">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="130c6-189">**Allow Nulls**</span></span>  
 <span data-ttu-id="130c6-190">テーブル定義において列の NULL 値が許容される場合は **[はい]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-190">Displays **Yes** when the table definition allows null values for the column.</span></span> <span data-ttu-id="130c6-191">テーブル定義において列の NULL 値が許容されない場合は **[いいえ]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-191">Displays **No** when the table definition does not allow nulls for the column.</span></span>  
  
##  <a name="storage-page-options"></a><a name="Storage"></a> <span data-ttu-id="130c6-192">[ストレージ] ページのオプション</span><span class="sxs-lookup"><span data-stu-id="130c6-192">Storage Page Options</span></span>  
 <span data-ttu-id="130c6-193">このページを使用すると、選択したインデックスのファイル グループ プロパティやパーティション構成プロパティを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-193">Use this page to view or modify filegroup or partition scheme properties for the selected index.</span></span> <span data-ttu-id="130c6-194">インデックスの種類に関連するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-194">Only shows options related to the type of index.</span></span>  
  
 <span data-ttu-id="130c6-195">**[ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="130c6-195">**Filegroup**</span></span>  
 <span data-ttu-id="130c6-196">指定したファイル グループのインデックスを格納します。</span><span class="sxs-lookup"><span data-stu-id="130c6-196">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="130c6-197">一覧には、標準 (ROW) ファイル グループのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-197">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="130c6-198">既定で選択されているのは、データベースのプライマリ ファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="130c6-198">The default list selection is the PRIMARY filegroup of the database.</span></span> <span data-ttu-id="130c6-199">詳細については、「 [Database Files and Filegroups](../databases/database-files-and-filegroups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-199">For more information, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
 <span data-ttu-id="130c6-200">**[Filestream ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="130c6-200">**Filestream filegroup**</span></span>  
 <span data-ttu-id="130c6-201">FILESTREAM データのファイル グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-201">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="130c6-202">この一覧には FILESTREAM ファイル グループのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-202">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="130c6-203">既定で選択されているのは、PRIMARY FILESTREAM ファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="130c6-203">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span> <span data-ttu-id="130c6-204">詳細については、「[FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="130c6-204">For more information, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="130c6-205">**[パーティション構成]**</span><span class="sxs-lookup"><span data-stu-id="130c6-205">**Partition scheme**</span></span>  
 <span data-ttu-id="130c6-206">パーティション構成のインデックスを格納します。</span><span class="sxs-lookup"><span data-stu-id="130c6-206">Stores the index in a partition scheme.</span></span> <span data-ttu-id="130c6-207">**[パーティション構成]** をクリックすると、下のグリッドが有効になります。</span><span class="sxs-lookup"><span data-stu-id="130c6-207">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="130c6-208">既定で選択されているのは、テーブルのデータを格納するために使用されるパーティション構成です。</span><span class="sxs-lookup"><span data-stu-id="130c6-208">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="130c6-209">一覧にある他のパーティション構成を選択すると、グリッドに表示される情報が更新されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-209">When you select a different partition scheme in the list, the information in the grid is updated.</span></span> <span data-ttu-id="130c6-210">詳細については、「 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-210">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="130c6-211">この [パーティション構成] オプションは、データベースにパーティション構成がなければ使用できません。</span><span class="sxs-lookup"><span data-stu-id="130c6-211">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="130c6-212">**[FileStream パーティション構成]**</span><span class="sxs-lookup"><span data-stu-id="130c6-212">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="130c6-213">FILESTREAM データのパーティション構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-213">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="130c6-214">パーティション構成は、 **[パーティション構成]** オプションで指定した構成と対称である必要があります。</span><span class="sxs-lookup"><span data-stu-id="130c6-214">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="130c6-215">テーブルがパーティション分割されていない場合、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="130c6-215">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="130c6-216">**[パーティション構成パラメーター]**</span><span class="sxs-lookup"><span data-stu-id="130c6-216">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="130c6-217">パーティション構成に使用される列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-217">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="130c6-218">**[テーブル列]**</span><span class="sxs-lookup"><span data-stu-id="130c6-218">**Table Column**</span></span>  
 <span data-ttu-id="130c6-219">パーティション構成にマップされるテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="130c6-219">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="130c6-220">**[列データ型]**</span><span class="sxs-lookup"><span data-stu-id="130c6-220">**Column Data Type**</span></span>  
 <span data-ttu-id="130c6-221">列のデータ型情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-221">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="130c6-222">テーブルの列が計算列の場合、 **[列データ型]** には "計算列" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-222">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="130c6-223">**[インデックスの移動中に DML ステートメントのオンライン処理を許可する]**</span><span class="sxs-lookup"><span data-stu-id="130c6-223">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="130c6-224">インデックス操作中に、基本となるテーブルやクラスター化インデックス データ、および関連する非クラスター化インデックスにユーザーがアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="130c6-224">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span> <span data-ttu-id="130c6-225">詳しくは、「 [Perform Index Operations Online](perform-index-operations-online.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="130c6-225">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="130c6-226">XML インデックスの場合、またはインデックスが無効なクラスター化インデックスの場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="130c6-226">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="130c6-227">**[並列処理の最大限度の設定]**</span><span class="sxs-lookup"><span data-stu-id="130c6-227">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="130c6-228">並列実行プランの実行中に使用されるプロセッサ数を制限します。</span><span class="sxs-lookup"><span data-stu-id="130c6-228">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="130c6-229">既定値は 0 です。0 の場合、実際に使用可能な CPU 数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-229">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="130c6-230">値を 1 に設定すると、並列実行プランが生成されなくなります。値を 1 よりも大きな数値に設定すると、1 つのクエリ実行で使用されるプロセッサの最大数が限定されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-230">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="130c6-231">このオプションは、ダイアログ ボックスが **再構築** または **再作成** 状態のときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-231">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span> <span data-ttu-id="130c6-232">詳しくは、「 [最適なパフォーマンスを実現するための max degree of parallelism オプションの設定](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="130c6-232">For more information, see [Set the Max Degree of Parallelism Option for Optimal Performance](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="130c6-233">使用可能な CPU 数よりも多い値を指定すると、実際に使用可能な CPU 数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-233">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="spatial-page-index-options"></a><a name="Spatial"></a> <span data-ttu-id="130c6-234">[空間] ページのインデックス オプション</span><span class="sxs-lookup"><span data-stu-id="130c6-234">Spatial Page Index Options</span></span>  
 <span data-ttu-id="130c6-235">**[空間]** ページを使用して、空間プロパティの値を表示または指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-235">Use the **Spatial** page to view or specify the values of the spatial properties.</span></span> <span data-ttu-id="130c6-236">詳細については、「[空間データ &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-236">For more information, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
### <a name="bounding-box"></a><span data-ttu-id="130c6-237">[境界ボックス]</span><span class="sxs-lookup"><span data-stu-id="130c6-237">Bounding Box</span></span>  
 <span data-ttu-id="130c6-238">*境界ボックス* は、幾何平面の最上位レベルのグリッドの境界です。</span><span class="sxs-lookup"><span data-stu-id="130c6-238">The *bounding box* is the perimeter of the top-level grid of a geometric plane.</span></span> <span data-ttu-id="130c6-239">境界ボックスのパラメーターは、ジオメトリ グリッド テセレーションにのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="130c6-239">The bounding-box parameters exist only in the geometry grid tessellation.</span></span> <span data-ttu-id="130c6-240">**[テセレーション スキーム]** が **[地理グリッド]** である場合、これらのパラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="130c6-240">These parameters are unavailable if the **Tessellation Scheme** is **Geography grid**.</span></span>  
  
 <span data-ttu-id="130c6-241">パネルには、境界ボックスの座標 **( *`X-min`* , *`Y-min`* )** と **( *`X-max`* , *`Y-max`* )** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-241">The panel displays the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="130c6-242">座標の既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="130c6-242">There are no default coordinate values.</span></span> <span data-ttu-id="130c6-243">そのため、`geometry` 型の列に新しい空間インデックスを作成する場合は、座標の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="130c6-243">Therefore, when you are creating a new spatial index on a `geometry` type column, you must specify the coordinate values.</span></span>  
  
 `X-min`  
 <span data-ttu-id="130c6-244">境界ボックスの左下隅の X 座標。</span><span class="sxs-lookup"><span data-stu-id="130c6-244">The X-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `Y-min`  
 <span data-ttu-id="130c6-245">境界ボックスの左下隅の Y 座標。</span><span class="sxs-lookup"><span data-stu-id="130c6-245">The Y-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `X-max`  
 <span data-ttu-id="130c6-246">境界ボックスの右上隅の X 座標。</span><span class="sxs-lookup"><span data-stu-id="130c6-246">The X-coordinate of the upper-right corner of the bounding box.</span></span>  
  
 `Y-max`  
 <span data-ttu-id="130c6-247">境界ボックスの右上隅の Y 座標。</span><span class="sxs-lookup"><span data-stu-id="130c6-247">The Y-coordinate of upper-right corner of the bounding box.</span></span>  
  
### <a name="general"></a><span data-ttu-id="130c6-248">全般</span><span class="sxs-lookup"><span data-stu-id="130c6-248">General</span></span>  
 <span data-ttu-id="130c6-249">**[テセレーション スキーム]**</span><span class="sxs-lookup"><span data-stu-id="130c6-249">**Tessellation Scheme**</span></span>  
 <span data-ttu-id="130c6-250">インデックスのテセレーション スキームを示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-250">Indicates the tessellation scheme of the index.</span></span> <span data-ttu-id="130c6-251">サポートされているテセレーション スキームは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="130c6-251">The supported tessellation schemes are as follows.</span></span>  
  
 <span data-ttu-id="130c6-252">**[ジオメトリ グリッド]**</span><span class="sxs-lookup"><span data-stu-id="130c6-252">**Geometry grid**</span></span>  
 <span data-ttu-id="130c6-253">`geometry` データ型の列に適用される、ジオメトリ グリッド テセレーション スキームを指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-253">Specifies the geometry grid tessellation scheme, which applies to a column of the `geometry` data type.</span></span>  
  
 <span data-ttu-id="130c6-254">**[ジオメトリ自動グリッド]**</span><span class="sxs-lookup"><span data-stu-id="130c6-254">**Geometry Auto grid**</span></span>  
 <span data-ttu-id="130c6-255">このオプションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、データベース互換性レベルが 110 以上に設定されている場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-255">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="130c6-256">**[地理グリッド]**</span><span class="sxs-lookup"><span data-stu-id="130c6-256">**Geography grid**</span></span>  
 <span data-ttu-id="130c6-257">**geography** データ型の列に適用される、地理グリッド テセレーション スキームを指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-257">Specifies the geography grid tessellation scheme, which applies to a column of the **geography** data type.</span></span>  
  
 <span data-ttu-id="130c6-258">**[地理自動グリッド]**</span><span class="sxs-lookup"><span data-stu-id="130c6-258">**Geography Auto grid**</span></span>  
 <span data-ttu-id="130c6-259">このオプションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、データベース互換性レベルが 110 以上に設定されている場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-259">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="130c6-260">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がテセレーションを実装するしくみについては、「[空間データ &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-260">For information about how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implements tessellation, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="130c6-261">**[オブジェクトごとのセル数]**</span><span class="sxs-lookup"><span data-stu-id="130c6-261">**Cells Per Object**</span></span>  
 <span data-ttu-id="130c6-262">インデックスの単一の空間オブジェクトに使用できるオブジェクトごとのテセレーション セル数を示します。</span><span class="sxs-lookup"><span data-stu-id="130c6-262">Indicates the number of tessellation cells-per-object that can be used for a single spatial object in the index.</span></span> <span data-ttu-id="130c6-263">1 ～ 8192 の整数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="130c6-263">This number can be any integer between 1 and 8192, inclusive.</span></span> <span data-ttu-id="130c6-264">既定値は 16 ですが、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でデータベース互換性レベルが 110 以上に設定されている場合、既定値は 8 です。</span><span class="sxs-lookup"><span data-stu-id="130c6-264">The default is 16, and 8 for earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="130c6-265">オブジェクトがセルで指定された数よりについて説明している場合は、最上位レベルに *n*、数のセルに応じて使用して完全な最上位レベルのテセレーションを提供する、インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="130c6-265">At the top level, if an object covers more cells than specified by *n*, the indexing uses as many cells as necessary to provide a complete top-level tessellation.</span></span> <span data-ttu-id="130c6-266">その場合、オブジェクトには指定されたセル数よりも多くのセルが割り当てられることがあります。</span><span class="sxs-lookup"><span data-stu-id="130c6-266">In such cases, an object might receive more than the specified number of cells.</span></span> <span data-ttu-id="130c6-267">このとき、最大数は、 **[レベル 1]** の密度に応じて最上位レベルのグリッドで生成されたセルの数となります。</span><span class="sxs-lookup"><span data-stu-id="130c6-267">In this case, the maximum number is the number of cells generated by the top-level grid, which depends on the **Level 1** density.</span></span>  
  
### <a name="grids"></a><span data-ttu-id="130c6-268">グリッド</span><span class="sxs-lookup"><span data-stu-id="130c6-268">Grids</span></span>  
 <span data-ttu-id="130c6-269">このパネルには、テセレーション スキームの各レベルにおけるグリッド密度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-269">This panel shows the density of the grid at each level of the tessellation scheme.</span></span> <span data-ttu-id="130c6-270">密度は、 **[低]** 、 **[中]** 、または **[高]** で指定されます。</span><span class="sxs-lookup"><span data-stu-id="130c6-270">Density is specified as **Low**, **Medium**, or **High**.</span></span> <span data-ttu-id="130c6-271">既定値は **[中]** です。</span><span class="sxs-lookup"><span data-stu-id="130c6-271">The default is **Medium**.</span></span> <span data-ttu-id="130c6-272">**[低]** は 4 × 4 のグリッド (16 個のセル)、 **[中]** は 8 × 8 のグリッド (64 個のセル)、 **[高]** は 16 × 16 のグリッド (256 個のセル) を表します。</span><span class="sxs-lookup"><span data-stu-id="130c6-272">**Low** represents a 4x4 grid (16 cells), **Medium** represents an 8x8 grid (64 cells), and **High** represents a 16x16 grid (256 cells).</span></span> <span data-ttu-id="130c6-273">これらのオプションは、 **[ジオメトリ自動グリッド]** または **[地理自動グリッド]** テセレーション オプションが選択されている場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="130c6-273">These options are not available when the **Geometry Auto grid** or **Geography Auto grid** tessellation options are chosen.</span></span>  
  
 <span data-ttu-id="130c6-274">**Level 1 (レベル 1)**</span><span class="sxs-lookup"><span data-stu-id="130c6-274">**Level 1**</span></span>  
 <span data-ttu-id="130c6-275">第 1 レベル (最上位) グリッドの密度です。</span><span class="sxs-lookup"><span data-stu-id="130c6-275">The density of the first-level (top) grid.</span></span>  
  
 <span data-ttu-id="130c6-276">**Level 2 (レベル 2)**</span><span class="sxs-lookup"><span data-stu-id="130c6-276">**Level 2**</span></span>  
 <span data-ttu-id="130c6-277">第 2 レベルのグリッドの密度です。</span><span class="sxs-lookup"><span data-stu-id="130c6-277">The density of the second-level grid.</span></span>  
  
 <span data-ttu-id="130c6-278">**Level 3 (レベル 3)**</span><span class="sxs-lookup"><span data-stu-id="130c6-278">**Level 3**</span></span>  
 <span data-ttu-id="130c6-279">第 3 レベルのグリッドの密度です。</span><span class="sxs-lookup"><span data-stu-id="130c6-279">The density of the third-level grid.</span></span>  
  
 <span data-ttu-id="130c6-280">**[レベル 4]**</span><span class="sxs-lookup"><span data-stu-id="130c6-280">**Level 4**</span></span>  
 <span data-ttu-id="130c6-281">第 4 レベルのグリッドの密度です。</span><span class="sxs-lookup"><span data-stu-id="130c6-281">The density of the fourth-level grid.</span></span>  
  
##  <a name="filter-page"></a><a name="Filter"></a> <span data-ttu-id="130c6-282">[フィルター] ページ</span><span class="sxs-lookup"><span data-stu-id="130c6-282">Filter Page</span></span>  
 <span data-ttu-id="130c6-283">このページを使用して、フィルター選択されたインデックスのフィルター述語を入力します。</span><span class="sxs-lookup"><span data-stu-id="130c6-283">Use this page to enter the filter predicate for a filtered index.</span></span> <span data-ttu-id="130c6-284">詳細については、「 [Create Filtered Indexes](create-filtered-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130c6-284">For more information, see [Create Filtered Indexes](create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="130c6-285">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="130c6-285">**Filter Expression**</span></span>  
 <span data-ttu-id="130c6-286">フィルター処理されたインデックスにどのデータ行を含めるかを定義します。</span><span class="sxs-lookup"><span data-stu-id="130c6-286">Defines which data rows to include in the filtered index.</span></span> <span data-ttu-id="130c6-287">たとえば、`StartDate > '20000101' AND EndDate IS NOT NULL'.` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="130c6-287">For example, `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130c6-288">参照</span><span class="sxs-lookup"><span data-stu-id="130c6-288">See Also</span></span>  
 <span data-ttu-id="130c6-289">[インデックス オプションの設定](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="130c6-289">[Set Index Options](set-index-options.md) </span></span>  
 <span data-ttu-id="130c6-290">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="130c6-290">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 [<span data-ttu-id="130c6-291">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="130c6-291">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
