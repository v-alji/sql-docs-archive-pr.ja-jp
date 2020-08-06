---
title: '[インデックスとキー] ダイアログボックス (Visual Database Tools) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68c9022f3ea7803f372e7c349e0dc75b1fc56adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630737"
---
# <a name="indexes-and-keys-dialog-box-visual-database-tools"></a><span data-ttu-id="5eeae-102">[インデックスとキー] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5eeae-102">Indexes and Keys Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="5eeae-103">このダイアログ ボックスを使用すると、インデックス、主キー、および一意キーを作成したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-103">Use this dialog box to create or modify indexes, primary keys, and unique keys.</span></span> <span data-ttu-id="5eeae-104">このダイアログ ボックスにアクセスするには、インデックスまたはキーを持つテーブルのテーブル定義を開いて、テーブル定義グリッドを右クリックし、 **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5eeae-104">To access this dialog box, open the table definition for the table with the index or key, right-click the table definition grid, and then click **Indexes/Keys**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5eeae-105">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eeae-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="5eeae-106">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="5eeae-107">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5eeae-108">オプション</span><span class="sxs-lookup"><span data-stu-id="5eeae-108">Options</span></span>  
 <span data-ttu-id="5eeae-109">**[選択された主/一意キーまたはインデックス]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-109">**Selected Primary/Unique Key or Index**</span></span>  
 <span data-ttu-id="5eeae-110">既存の主キーまたは一意キーとインデックスを示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-110">Lists existing primary or unique keys and indexes.</span></span> <span data-ttu-id="5eeae-111">右側のグリッドにプロパティを表示するキーまたはインデックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-111">Select one to show its properties in the grid to the right.</span></span> <span data-ttu-id="5eeae-112">一覧が空の場合、テーブルには何も定義されていません。</span><span class="sxs-lookup"><span data-stu-id="5eeae-112">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="5eeae-113">**追加**</span><span class="sxs-lookup"><span data-stu-id="5eeae-113">**Add**</span></span>  
 <span data-ttu-id="5eeae-114">新しい主キー、一意キー、またはインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-114">Create a new primary or unique key or index.</span></span>  
  
 <span data-ttu-id="5eeae-115">**削除**</span><span class="sxs-lookup"><span data-stu-id="5eeae-115">**Delete**</span></span>  
 <span data-ttu-id="5eeae-116">**[選択された主/一意キーまたはインデックス]** 一覧で選択したキーまたはインデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-116">Delete the key or index selected in the **Selected Primary/Unique Key or Index** list.</span></span>  
  
 <span data-ttu-id="5eeae-117">**[全般] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="5eeae-117">**General Category**</span></span>  
 <span data-ttu-id="5eeae-118">展開してプロパティ **[列]** 、 **[UNIQUE]** 、および **[型]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-118">When expanded, shows the properties **Columns**, **Is Unique**, and **Type**.</span></span>  
  
 <span data-ttu-id="5eeae-119">**[列]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-119">**Columns**</span></span>  
 <span data-ttu-id="5eeae-120">キー列またはインデックス列に対して選択されている並べ替え順を一覧表示します。またここから並べ替え順を定義できるダイアログ ボックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-120">Lists chosen sort orders for the columns in the key or index, and provides access to a dialog box where the sort orders can be defined.</span></span> <span data-ttu-id="5eeae-121">ダイアログ ボックスを表示するには、 **[列]** をクリックして、プロパティ フィールドの右に表示される省略記号ボタン ( [...] ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5eeae-121">To display the dialog box, click **Columns** and then click the ellipsis button (...) that appears to the right of the property field.</span></span>  
  
 <span data-ttu-id="5eeae-122">**[UNIQUE]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-122">**Is Unique**</span></span>  
 <span data-ttu-id="5eeae-123">インデックスまたはキーに入力するデータが一意である必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-123">Indicates whether data entered into this index or key must be unique.</span></span> <span data-ttu-id="5eeae-124">XML インデックスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5eeae-124">This is unavailable for XML Indexes.</span></span>  
  
 <span data-ttu-id="5eeae-125">**Type**</span><span class="sxs-lookup"><span data-stu-id="5eeae-125">**Type**</span></span>  
 <span data-ttu-id="5eeae-126">**[選択された主/一意キーまたはインデックス]** の一覧で選択された項目が一意のキーであるか、主キーであるか、またはインデックスであるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-126">Specify whether the item selected in the **Selected Primary/Unique Key or Index** list is a unique key, a primary key, or an index.</span></span> <span data-ttu-id="5eeae-127">主キーを選択した場合、該当するフィールドは読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="5eeae-127">For primary keys this field is read-only.</span></span>  
  
 <span data-ttu-id="5eeae-128">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="5eeae-128">**Identity Category**</span></span>  
 <span data-ttu-id="5eeae-129">展開して **[オブジェクト名]** プロパティ フィールドと **[説明]** プロパティ フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-129">When expanded, it shows the property fields for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="5eeae-130">**Name**</span><span class="sxs-lookup"><span data-stu-id="5eeae-130">**Name**</span></span>  
 <span data-ttu-id="5eeae-131">キーまたはインデックスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-131">Shows the name of the key or index.</span></span> <span data-ttu-id="5eeae-132">新しいキーまたはインデックスを作成した場合、このプロパティには、テーブル デザイナーのアクティブ ウィンドウのテーブルに基づいて、既定の名前が設定されます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-132">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="5eeae-133">名前はいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-133">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="5eeae-134">**説明**</span><span class="sxs-lookup"><span data-stu-id="5eeae-134">**Description**</span></span>  
 <span data-ttu-id="5eeae-135">キーまたはインデックスの説明を記述できます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-135">Provides a place to describe the key or index.</span></span> <span data-ttu-id="5eeae-136">より詳細な説明を記述する場合は、 **[説明]** をクリックしてから、プロパティ フィールドの右に表示される省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5eeae-136">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="5eeae-137">これにより、テキストを書くことができる領域が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="5eeae-137">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="5eeae-138">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="5eeae-138">**Table Designer Category**</span></span>  
 <span data-ttu-id="5eeae-139">展開して **[CLUSTERED として作成]** の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-139">When expanded, shows information for **Create as Clustered**.</span></span>  
  
 <span data-ttu-id="5eeae-140">**[CLUSTERED として作成]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-140">**Create as Clustered**</span></span>  
 <span data-ttu-id="5eeae-141">キーまたはインデックスをクラスター化します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-141">Make the key or index clustered.</span></span> <span data-ttu-id="5eeae-142">1 つのテーブルでクラスター化できるインデックスは、1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="5eeae-142">Only one clustered index is allowed on a table.</span></span> <span data-ttu-id="5eeae-143">テーブル内のデータは、クラスター化インデックスの順序で保存されます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-143">Data in the table is stored in the order of the clustered index.</span></span> <span data-ttu-id="5eeae-144">詳細については、「 [クラスター化インデックスの作成](../../relational-databases/indexes/indexes.md) 」と「 [非クラスター化インデックスの作成](../../relational-databases/indexes/create-nonclustered-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eeae-144">For more information, see [Create Clustered Indexes](../../relational-databases/indexes/indexes.md) and [Create Nonclustered Indexes](../../relational-databases/indexes/create-nonclustered-indexes.md).</span></span>  
  
 <span data-ttu-id="5eeae-145">**[データ スペースの指定]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-145">**Data Space Specification**</span></span>  
 <span data-ttu-id="5eeae-146">展開して **[(データ スペースの種類)]** 、 **[ファイル グループまたはパーティション スキーム名]** 、および **[パーティション列の一覧]** の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-146">When expanded, shows information for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="5eeae-147">**[(データ スペースの種類)]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-147">**(Data Space Type)**</span></span>  
 <span data-ttu-id="5eeae-148">インデックスまたはキーが、ファイル グループまたはパーティション スキームに属するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-148">Indicates whether this index or key belongs to a file group or partition scheme.</span></span>  
  
 <span data-ttu-id="5eeae-149">**[ファイル グループまたはパーティション スキーム名]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-149">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="5eeae-150">格納されているファイル グループまたはパーティション スキームの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-150">Shows the name of the file group or partition scheme on which it is stored.</span></span>  
  
 <span data-ttu-id="5eeae-151">**[パーティション列の一覧]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-151">**Partition Column List**</span></span>  
 <span data-ttu-id="5eeae-152">パーティション列関数に関係している列を、コンマ区切りで一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-152">Displays a comma-separated list of columns that participate in the partition column function.</span></span> <span data-ttu-id="5eeae-153">**[(データ スペースの種類)]** フィールドの [ファイル グループ] を選択した場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="5eeae-153">Unavailable if Filegroup is selected in the **(Data Space Type)** field.</span></span>  
  
 <span data-ttu-id="5eeae-154">**[FILL の指定]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-154">**Fill Specification**</span></span>  
 <span data-ttu-id="5eeae-155">展開して **[FILL FACTOR]** および **[インデックスの埋め込み]** の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-155">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="5eeae-156">**[FILL FACTOR]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-156">**Fill Factor**</span></span>  
 <span data-ttu-id="5eeae-157">インデックスのリーフレベル ページをシステムにより埋めることができる割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-157">Specifies what percentage of the index's leaf-level pages the system can fill.</span></span> <span data-ttu-id="5eeae-158">ページがいっぱいになり、新たなデータが追加されると、システムはそのページを分割します。これによりパフォーマンスが大きく低下します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-158">Once a page is full, the system must split the pages to add new data, impairing performance.</span></span>  
  
-   <span data-ttu-id="5eeae-159">値 100 は、ページがいっぱいになることを示しています。</span><span class="sxs-lookup"><span data-stu-id="5eeae-159">A value of 100 means the pages will be full.</span></span> <span data-ttu-id="5eeae-160">この場合、最小限の記憶領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="5eeae-160">This will require the least amount of storage space.</span></span> <span data-ttu-id="5eeae-161">この設定は、データに変更がない (たとえば読み取り専用テーブルのデータ) 場合にだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-161">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="5eeae-162">値が小さいほど、データ ページの空の領域が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="5eeae-162">A lower value leaves more empty space on the data pages.</span></span> <span data-ttu-id="5eeae-163">インデックスが増えるにつれてデータ ページを分割する必要性は低くなりますが、必要な記憶領域は大きくなります。</span><span class="sxs-lookup"><span data-stu-id="5eeae-163">This reduces the need to split data pages as indexes grow but requires more storage space.</span></span>  
  
 <span data-ttu-id="5eeae-164">**[インデックスの埋め込み]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-164">**Pad Index**</span></span>  
 <span data-ttu-id="5eeae-165">インデックスの中間ページが拡大したときに、 **[FILL FACTOR]** で指定したのと同じ割合で空き領域 (埋め込み) を用意するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-165">Indicate whether intermediate pages in this index are provided the same percentage of empty space (padding) specified in **Fill Factor** when they grow.</span></span>  
  
 <span data-ttu-id="5eeae-166">**[重複するキーを無視]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-166">**Ignore Duplicate Keys**</span></span>  
 <span data-ttu-id="5eeae-167">一括挿入操作で、既存のキー値と等しいキー値を持つ行が挿入された場合の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-167">Specify what happens when a row is inserted during a bulk insert operation whose key value equals an existing key value.</span></span> <span data-ttu-id="5eeae-168">次のうちのどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-168">If you choose:</span></span>  
  
-   <span data-ttu-id="5eeae-169">**[はい]** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は警告を表示し、不正な挿入行を無視して、残りの行の挿入を試行します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-169">**Yes** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues a warning, ignores the offending incoming row, and tries to insert the remaining rows.</span></span>  
  
-   <span data-ttu-id="5eeae-170">**[いいえ]** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はエラー メッセージを表示し、一括挿入操作全体をロールバックします。</span><span class="sxs-lookup"><span data-stu-id="5eeae-170">**No** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues an error message and rolls back the entire bulk insert operation.</span></span>  
  
 <span data-ttu-id="5eeae-171">**[インクルードされた列]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-171">**Included Columns**</span></span>  
 <span data-ttu-id="5eeae-172">インデックス キーを構成するすべての列の名前を、コンマ区切りで一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-172">Displays a comma-separated list of the names of all the columns that constitute the index key.</span></span> <span data-ttu-id="5eeae-173">サブキー列が指定できるのは、クラスター化されていないインデックスの場合だけです。</span><span class="sxs-lookup"><span data-stu-id="5eeae-173">Subkey columns can only be specified for nonclustered indexes.</span></span> <span data-ttu-id="5eeae-174">このプロパティは、XML インデックスに対して隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-174">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="5eeae-175">**[無効化]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-175">**Is Disabled**</span></span>  
 <span data-ttu-id="5eeae-176">インデックスを無効にするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-176">Indicates whether this index is disabled.</span></span> <span data-ttu-id="5eeae-177">これは、読み取り専用プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5eeae-177">This is a read-only property.</span></span> <span data-ttu-id="5eeae-178">インデックスが Visual Database Tools の外部で無効に設定されている場合、このプロパティは **[はい]** にのみ設定されます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-178">This property is only set to **Yes** if the index has been disabled outside of the Visual Database tools.</span></span>  
  
 <span data-ttu-id="5eeae-179">**[フルテキスト キー]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-179">**Is Full-Text Key**</span></span>  
 <span data-ttu-id="5eeae-180">インデックスがフルテキスト キーかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-180">Specify whether this index is a full-text key.</span></span> <span data-ttu-id="5eeae-181">フルテキスト キーの詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eeae-181">For more information on full-text keys, see SQL Server Books Online.</span></span> <span data-ttu-id="5eeae-182">このプロパティは、XML インデックスに対して隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-182">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="5eeae-183">**[ページのロックを許可]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-183">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="5eeae-184">インデックスでページレベルのロックを許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-184">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="5eeae-185">ページレベル ロックの許可、非許可はデータベースのパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-185">Allowing or disallowing page-level locking affects database performance.</span></span> <span data-ttu-id="5eeae-186">推奨設定値は **[はい]** です。</span><span class="sxs-lookup"><span data-stu-id="5eeae-186">The recommended setting is **Yes**.</span></span>  
  
 <span data-ttu-id="5eeae-187">**[統計値を再計算する]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-187">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="5eeae-188">インデックスの作成時に、基になる [!INCLUDE[ssDE](../../includes/ssde-md.md)] で統計情報を新たに計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-188">Specify whether the underlying [!INCLUDE[ssDE](../../includes/ssde-md.md)] computes new statistics when the index is created.</span></span> <span data-ttu-id="5eeae-189">統計情報の再計算により、インデックスの構築には前よりも時間がかかりますが、クエリのパフォーマンスは大幅に向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5eeae-189">Re-computing statistics slows the building of indexes but will very likely improve query performance.</span></span>  
  
 <span data-ttu-id="5eeae-190">**[行のロックを許可]**</span><span class="sxs-lookup"><span data-stu-id="5eeae-190">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="5eeae-191">該当するインデックスで行レベルのロックを許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5eeae-191">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="5eeae-192">行レベル ロックの許可、非許可はデータベースのパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="5eeae-192">Allowing or disallowing row-level locking affects database performance.</span></span> <span data-ttu-id="5eeae-193">推奨設定値は **[はい]** です。</span><span class="sxs-lookup"><span data-stu-id="5eeae-193">The recommended setting is **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eeae-194">参照</span><span class="sxs-lookup"><span data-stu-id="5eeae-194">See Also</span></span>  
 <span data-ttu-id="5eeae-195">[Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="5eeae-195">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="5eeae-196">主キー制約と外部キー制約</span><span class="sxs-lookup"><span data-stu-id="5eeae-196">Primary and Foreign Key Constraints</span></span>](../../relational-databases/tables/primary-and-foreign-key-constraints.md)  
  
  
