---
title: 'チュートリアル: データベース ダイアグラムの追加と変更 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], about database diagrams
- database diagrams [SQL Server], designing
- database diagrams [SQL Server], creating
ms.assetid: 228caa0d-8f24-46ab-86d1-b6d8631322bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: c35eb3674c817e98a25a74cd0309fc7376fe2f58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632254"
---
# <a name="walkthrough-adding-and-changing-a-database-diagram"></a><span data-ttu-id="2f089-102">チュートリアル: データベース ダイアグラムの追加と変更</span><span class="sxs-lookup"><span data-stu-id="2f089-102">Walkthrough: Adding and Changing a Database Diagram</span></span>
  <span data-ttu-id="2f089-103">このチュートリアルでは、データベース ダイアグラムを作成および変更する方法と、データベース ダイアグラム コンポーネントを使用してデータベースを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f089-103">This walkthrough illustrates how to create and modify a database diagram and make changes to the database through the database diagrams component.</span></span> <span data-ttu-id="2f089-104">ダイアグラムにテーブルを追加する方法、テーブル間のリレーションシップを作成する方法、列に制約とインデックスを作成する方法、およびテーブルごとに表示する情報のレベルを変更する方法を記載しています。</span><span class="sxs-lookup"><span data-stu-id="2f089-104">You will see how to add tables to diagrams, create relationships between tables, create constraints and indexes on columns, and change the level of information you see for each table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f089-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="2f089-105">Prerequisites</span></span>  
 <span data-ttu-id="2f089-106">このチュートリアルを完了するには、以下が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f089-106">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="2f089-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースへのアクセス権</span><span class="sxs-lookup"><span data-stu-id="2f089-107">Access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database</span></span>  
  
-   <span data-ttu-id="2f089-108">データベース所有者 (`dbo`) 特権のあるアカウント</span><span class="sxs-lookup"><span data-stu-id="2f089-108">An account with database owner `dbo` privileges</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f089-109">十分な特権がないアカウントを使用してテーブルを変更しようとすると、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-109">If you attempt to make changes when using an account without sufficient privileges to make changes to tables, then an error message appears.</span></span>  
  
## <a name="creating-a-diagram"></a><span data-ttu-id="2f089-110">ダイアグラムの作成</span><span class="sxs-lookup"><span data-stu-id="2f089-110">Creating a Diagram</span></span>  
  
#### <a name="to-create-a-new-database-diagram"></a><span data-ttu-id="2f089-111">新しいデータベース ダイアグラムを作成するには</span><span class="sxs-lookup"><span data-stu-id="2f089-111">To create a new database diagram</span></span>  
  
1.  <span data-ttu-id="2f089-112">**[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-112">On the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="2f089-113">[データベース] ノードを展開し、[ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2f089-113">Open the Databases node and then open the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] node.</span></span>  
  
3.  <span data-ttu-id="2f089-114">[データベース ダイアグラム] ノードを右クリックし、 **[新しいデータベース ダイアグラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-114">Right-click the Database Diagrams node and choose **New Database Diagram**.</span></span>  
  
     <span data-ttu-id="2f089-115">ダイアグラムの作成に必要なオブジェクトがデータベースに含まれていない場合、" **このデータベースには、データベース ダイアグラムの作成を使用するために必要な 1 つ以上のサポート オブジェクトが含まれていません。サポート オブジェクトを作成しますか?** " というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-115">If the database does not have objects necessary to create diagrams, the following message appears: **This database does not have one or more of the support objects required to use database diagramming. Do you wish to create them?**</span></span> <span data-ttu-id="2f089-116">**[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f089-116">Choose **Yes**.</span></span>  
  
     <span data-ttu-id="2f089-117">**[テーブルの追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-117">The **Add Table** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="2f089-118">**[AddressType (Person)]** と **[Address (Person)]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-118">Select **AddressType (Person)** and **Address (Person)** and click **Add**.</span></span>  
  
     <span data-ttu-id="2f089-119">2 つのテーブルがダイアグラムに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-119">Two tables are added to the diagram.</span></span>  
  
5.  <span data-ttu-id="2f089-120">**[テーブルの追加]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2f089-120">Close the **Add Table** dialog box.</span></span>  
  
#### <a name="to-view-different-column-data"></a><span data-ttu-id="2f089-121">異なる列データを表示するには</span><span class="sxs-lookup"><span data-stu-id="2f089-121">To view different column data</span></span>  
  
1.  <span data-ttu-id="2f089-122">`Address` テーブルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-122">Right-click the `Address` table.</span></span> <span data-ttu-id="2f089-123">ショートカット メニューの **[テーブル ビュー]** をポイントし、 **[標準]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-123">On the shortcut menu, point to **Table View**, and then click **Standard**.</span></span>  
  
     <span data-ttu-id="2f089-124">テーブル グリッドに **[列名]** 、 **[データ型]** 、および **[Null を許容]** という 3 つの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-124">The table grid shows three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
2.  <span data-ttu-id="2f089-125">`Address` テーブルを右クリックし、 **[テーブル ビュー]** をクリックして、 **[キー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f089-125">Right-click the `Address` table, click **Table View** and select **Keys**.</span></span>  
  
     <span data-ttu-id="2f089-126">テーブル グリッドに、テーブルの列名が列挙された 1 つの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-126">The table grid shows one column, with the table-column names.</span></span> <span data-ttu-id="2f089-127">表示されるのは、インデックスとして使用されている列のみです。</span><span class="sxs-lookup"><span data-stu-id="2f089-127">Only those columns participating in indexes appear.</span></span>  
  
## <a name="creating-new-tables"></a><span data-ttu-id="2f089-128">新しいテーブルの作成</span><span class="sxs-lookup"><span data-stu-id="2f089-128">Creating New Tables</span></span>  
  
#### <a name="to-create-tables-within-diagram-designer"></a><span data-ttu-id="2f089-129">ダイアグラム デザイナー内でテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="2f089-129">To create tables within Diagram Designer</span></span>  
  
1.  <span data-ttu-id="2f089-130">ダイアグラム デザイナーで、既存のテーブル以外の場所を右クリックし、 **[新しいテーブル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-130">Right-click the Diagram Designer outside the existing tables and choose **New Table**.</span></span>  
  
2.  <span data-ttu-id="2f089-131">[**名前の選択**] ダイアログボックスで、[ **OK** ] をクリックして既定の名前をそのまま使用し `Table1` ます。</span><span class="sxs-lookup"><span data-stu-id="2f089-131">In the **Choose Name** dialog box, click **OK** to accept the default name `Table1`.</span></span>  
  
     <span data-ttu-id="2f089-132">新しいテーブル グリッドに **[列名]** 、 **[データ型]** 、および **[Null を許容]** という 3 つの列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-132">A new table grid appears with three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
3.  <span data-ttu-id="2f089-133">に次の情報を追加し `Table1` ます。</span><span class="sxs-lookup"><span data-stu-id="2f089-133">Add the following information to `Table1`:</span></span>  
  
    |<span data-ttu-id="2f089-134">**列名**</span><span class="sxs-lookup"><span data-stu-id="2f089-134">**Column Name**</span></span>|<span data-ttu-id="2f089-135">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="2f089-135">**Data Type**</span></span>|<span data-ttu-id="2f089-136">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="2f089-136">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T1col1`|`int`|<span data-ttu-id="2f089-137">checked</span><span class="sxs-lookup"><span data-stu-id="2f089-137">checked</span></span>|  
    |`T1col2`|`varchar(50)`|<span data-ttu-id="2f089-138">checked</span><span class="sxs-lookup"><span data-stu-id="2f089-138">checked</span></span>|  
    |`T1col3`|`float`|<span data-ttu-id="2f089-139">チェック</span><span class="sxs-lookup"><span data-stu-id="2f089-139">checked</span></span>|  
  
4.  <span data-ttu-id="2f089-140">[ `T1col1` ] を右クリックし、 **[主キーの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-140">Right-click `T1col1` and select **Set Primary Key**.</span></span>  
  
     <span data-ttu-id="2f089-141">列名の隣に鍵のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-141">A key icon will appear beside the column name.</span></span>  
  
5.  <span data-ttu-id="2f089-142">**[ファイル]** メニューの **[Diagram1 を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-142">From the **File** menu, click **Save Diagram1**.</span></span>  
  
6.  <span data-ttu-id="2f089-143">[**名前の選択**] ダイアログボックスで、[ **OK** ] をクリックして既定の名前をそのまま使用し `Diagram1` ます。</span><span class="sxs-lookup"><span data-stu-id="2f089-143">In the **Choose Name** dialog box, click **OK** to accept the default name `Diagram1`.</span></span>  
  
7.  <span data-ttu-id="2f089-144">**[上書き保存]** ダイアログ ボックスに、 `Table1` がデータベースに保存されることを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-144">The **Save** dialog box appears with a message that `Table1` will be saved to the database.</span></span> <span data-ttu-id="2f089-145">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-145">Click **Yes**.</span></span>  
  
## <a name="modifying-table-structure"></a><span data-ttu-id="2f089-146">テーブル構造の変更</span><span class="sxs-lookup"><span data-stu-id="2f089-146">Modifying Table Structure</span></span>  
 <span data-ttu-id="2f089-147">ダイアグラム デザイナーで CHECK 制約を追加し、テーブル間のリレーションシップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2f089-147">You can add check constraints and make relationships between tables in Diagram Designer.</span></span>  
  
#### <a name="to-create-check-constraints"></a><span data-ttu-id="2f089-148">CHECK 制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="2f089-148">To create check constraints</span></span>  
  
1.  <span data-ttu-id="2f089-149">`Table1`で、[ `T1col3` ] 行を右クリックし、 **[CHECK 制約]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-149">In `Table1`, right-click the `T1col3` row and choose **Check Constraints**.</span></span>  
  
     <span data-ttu-id="2f089-150">**[CHECK 制約]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-150">The **Check Constraints** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="2f089-151">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-151">Click **Add**.</span></span>  
  
     <span data-ttu-id="2f089-152">**[制約された制約のチェック]** の一覧に、既定の `CK_Table1`という名前を持つ新しい制約が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-152">A new constraint appears in the **Selected Check Constraint** list, with the default name `CK_Table1`.</span></span>  
  
3.  <span data-ttu-id="2f089-153">グリッド内の **[式]** 行をクリックし、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-153">Select the **Expression** row in the grid and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="2f089-154">**[選択された制約のチェック]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-154">The **Check Constraint Expression** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="2f089-155">「 `T1col3 > 5` 」と入力して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-155">Type `T1col3 > 5` and click **OK**.</span></span>  
  
     <span data-ttu-id="2f089-156">`Table1` これで `T1col3` に入力されるすべての値が 5 よりも大きくなければならないという制約が追加されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-156">`Table1` now has a constraint that all values entered into `T1col3` must be greater than 5.</span></span>  
  
5.  <span data-ttu-id="2f089-157">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-157">Click **Close**.</span></span>  
  
#### <a name="to-create-relationships-between-tables"></a><span data-ttu-id="2f089-158">テーブル間のリレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="2f089-158">To create relationships between tables</span></span>  
  
1.  <span data-ttu-id="2f089-159">ダイアグラム デザイナーで、 `Table2` という新しいテーブルを作成し、次の列を追加します。</span><span class="sxs-lookup"><span data-stu-id="2f089-159">Create a new table in Diagram designer named `Table2` with the following columns:</span></span>  
  
    |<span data-ttu-id="2f089-160">**列名**</span><span class="sxs-lookup"><span data-stu-id="2f089-160">**Column Name**</span></span>|<span data-ttu-id="2f089-161">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="2f089-161">**Data Type**</span></span>|<span data-ttu-id="2f089-162">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="2f089-162">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T2col1`|`int`|<span data-ttu-id="2f089-163">オフ</span><span class="sxs-lookup"><span data-stu-id="2f089-163">not checked</span></span>|  
    |`T2col2`|`varchar(50)`|<span data-ttu-id="2f089-164">checked</span><span class="sxs-lookup"><span data-stu-id="2f089-164">checked</span></span>|  
    |`T2col3`|`xml`|<span data-ttu-id="2f089-165">checked</span><span class="sxs-lookup"><span data-stu-id="2f089-165">checked</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f089-166">外部キー リレーションシップの主キー側の列は、主キーまたは UNIQUE 制約に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f089-166">The columns on the primary key side of a foreign key relationship must participate in either a Primary Key or a Unique Constraint.</span></span>  
  
2.  <span data-ttu-id="2f089-167">`T2col1` を `T1col1`にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2f089-167">Drag `T2col1` to `T1col1`.</span></span>  
  
     <span data-ttu-id="2f089-168">**[外部キーのリレーションシップ]** ダイアログ ボックスと **[テーブルと列]** ダイアログ ボックスが表示されます。[テーブルと列] ダイアログ ボックスが手前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-168">Two dialog boxes appear: **Foreign Key Relationship** in the background and **Tables and Columns** in the foreground.</span></span>  
  
3.  <span data-ttu-id="2f089-169">**[OK]** をクリックして、新しいリレーションシップを保存します。</span><span class="sxs-lookup"><span data-stu-id="2f089-169">Click **OK** to save the new relationship.</span></span>  
  
4.  <span data-ttu-id="2f089-170">もう一度 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-170">Click **OK** again.</span></span>  
  
## <a name="creating-indexes"></a><span data-ttu-id="2f089-171">インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="2f089-171">Creating Indexes</span></span>  
 <span data-ttu-id="2f089-172">XML を含めて、ほとんどの種類のデータにインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2f089-172">You can create indexes on most types of data, including XML.</span></span>  
  
#### <a name="to-create-a-standard-index"></a><span data-ttu-id="2f089-173">標準のインデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="2f089-173">To create a standard index</span></span>  
  
1.  <span data-ttu-id="2f089-174">`Table1` を右クリックし、 **[インデックス/キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-174">Right-click `Table1` and choose **Indexes/Keys**.</span></span>  
  
     <span data-ttu-id="2f089-175">**[インデックス/キー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-175">The **Indexes/Keys** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="2f089-176">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-176">Click **Add**.</span></span>  
  
     <span data-ttu-id="2f089-177">**[選択された主/一意キーまたはインデックス]** の一覧に、既定の `IX_Table1`という名前を持つ新しいインデックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-177">A new index appears in the **Selected Primary/Unique Key or Index** list, with a default name similar to `IX_Table1`.</span></span>  
  
3.  <span data-ttu-id="2f089-178">**[列]** 行を選択し、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-178">Select the **Columns** row and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="2f089-179">**[インデックスの列]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-179">The **Index Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="2f089-180">**[列名]** の下にあるドロップダウン リストの下矢印をクリックして、[ `T1col2`] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-180">Click the drop-down arrow under **Column Name** and select `T1col2`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f089-181">`T1col2` の下にあるセルを選択し、別の列名を選択することにより、このインデックスに列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2f089-181">You may add additional columns to this index by selecting the cell below `T1col2` and choosing another column name.</span></span>  
  
5.  <span data-ttu-id="2f089-182">**[OK]** をクリックしてこのインデックスを保存します。</span><span class="sxs-lookup"><span data-stu-id="2f089-182">Click **OK** to save this index.</span></span>  
  
6.  <span data-ttu-id="2f089-183">**[インデックス/キー]** ダイアログ ボックスで **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-183">Click **Close** in the **Indexes/Keys** dialog box.</span></span>  
  
#### <a name="to-create-an-xml-index"></a><span data-ttu-id="2f089-184">XML インデックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="2f089-184">To create an XML index</span></span>  
  
1.  <span data-ttu-id="2f089-185">[ `T2col1` ] を右クリックし、 **[主キーの設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f089-185">Right-click `T2col1` and choose **Set Primary Key**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f089-186">XML インデックスを追加するには、テーブル内にある別の列がクラスター化主キーに設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f089-186">Adding an XML index requires that another column in the table be set as a clustered primary key.</span></span>  
  
2.  <span data-ttu-id="2f089-187">`T2col3` の [ `Table2` ] 行を右クリックし、 **[XML インデックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-187">Right-click the `T2col3` row in `Table2` and select **XML Indexes**.</span></span>  
  
     <span data-ttu-id="2f089-188">**[XML インデックス]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-188">The **XML Indexes** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="2f089-189">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-189">Click **Add**.</span></span>  
  
     <span data-ttu-id="2f089-190">XML インデックスが **[選択された XML インデックス]** の一覧に既定の名前で追加されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-190">An XML index with default values will be added to the **Selected XML Index** list.</span></span>  
  
4.  <span data-ttu-id="2f089-191">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-191">Click **Close**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f089-192">XML インデックスは列単位に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-192">XML indexes are created per-column.</span></span> <span data-ttu-id="2f089-193">最初の XML インデックスがプライマリ インデックス、その他のインデックスがセカンダリ インデックスになります。</span><span class="sxs-lookup"><span data-stu-id="2f089-193">The first XML index is primary; any additional indexes are secondary.</span></span>  
  
## <a name="saving-the-diagram"></a><span data-ttu-id="2f089-194">ダイアグラムの保存</span><span class="sxs-lookup"><span data-stu-id="2f089-194">Saving the Diagram</span></span>  
 <span data-ttu-id="2f089-195">ダイアグラムに加えた変更は、そのダイアグラムを保存するまでデータベースに送信されません。</span><span class="sxs-lookup"><span data-stu-id="2f089-195">All of the changes you make to a diagram are not posted to the database until you save it.</span></span> <span data-ttu-id="2f089-196">問題や競合が発生した場合、ダイアログ ボックスにその詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-196">If there are problems or conflicts, a dialog box appears with more information.</span></span>  
  
#### <a name="to-save-a-database-diagram"></a><span data-ttu-id="2f089-197">データベース ダイアグラムを保存するには</span><span class="sxs-lookup"><span data-stu-id="2f089-197">To save a database diagram</span></span>  
  
1.  <span data-ttu-id="2f089-198">**[ファイル]** メニューの **[Diagram1 の保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f089-198">On the **File** menu, select **Save Diagram1**.</span></span>  
  
     <span data-ttu-id="2f089-199">**[上書き保存]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-199">The **Save** dialog box appears.</span></span> <span data-ttu-id="2f089-200">**[該当テーブルに関する警告]** チェック ボックスがオンになっている場合、新しいテーブルや変更されるテーブルの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-200">If **Warn about Tables Affected** is selected, information about new or changed tables is listed.</span></span>  
  
2.  <span data-ttu-id="2f089-201">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f089-201">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="2f089-202">エラーが発生した場合は、 **[保存前の通知]** ダイアログ ボックスにそれらのエラーと原因が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f089-202">If any errors occurred, the **Post-Save Notifications** dialog box appears with the errors and their causes.</span></span> <span data-ttu-id="2f089-203">エラーを修正し、再度ダイアグラムを保存します。</span><span class="sxs-lookup"><span data-stu-id="2f089-203">Fix the errors and save the diagram again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f089-204">次の手順</span><span class="sxs-lookup"><span data-stu-id="2f089-204">Next Steps</span></span>  
 <span data-ttu-id="2f089-205">ここで作成したダイアグラムは、既存のテーブルと新しいテーブルを 2 つずつ使用しただけの基本的なものですが、既存のデータベースのダイアグラムを作成したり、視覚的に新しいスキーマを作成したりできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="2f089-205">This is a basic diagram with just two existing and two new tables, but it illustrates the potential for diagramming an existing database or creating a new schema visually.</span></span> <span data-ttu-id="2f089-206">さらに理解を深めるには、次の操作を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2f089-206">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="2f089-207">関連テーブルのグループを含む新しいダイアグラムの作成</span><span class="sxs-lookup"><span data-stu-id="2f089-207">Create new diagrams containing groups of related tables</span></span>  
  
-   <span data-ttu-id="2f089-208">テーブルごとに表示される情報量のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="2f089-208">Customize the amount of information shown for each table</span></span>  
  
-   <span data-ttu-id="2f089-209">レイアウトの変更と注釈の追加</span><span class="sxs-lookup"><span data-stu-id="2f089-209">Change the layout and add annotations</span></span>  
  
-   <span data-ttu-id="2f089-210">ビットマップへのダイアグラムのコピー</span><span class="sxs-lookup"><span data-stu-id="2f089-210">Copy the diagram to a bitmap</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f089-211">参照</span><span class="sxs-lookup"><span data-stu-id="2f089-211">See Also</span></span>  
 <span data-ttu-id="2f089-212">[Visual Database Tools &#40;ダイアグラムに表示される情報の量をカスタマイズ&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2f089-212">[Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="2f089-213">[データベースダイアグラムデザイナー &#40;Visual Database Tools&#41;を設定する](set-up-database-diagram-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2f089-213">[Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span></span>  
 <span data-ttu-id="2f089-214">[Visual Database Tools &#40;ダイアグラムにテーブルを追加する&#41;](add-tables-to-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2f089-214">[Add Tables to Diagrams &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="2f089-215">[ダイアグラムのテーブル間のリレーションシップの作成 &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2f089-215">[Create Relationships Between Tables on a Diagram &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span></span>  
 <span data-ttu-id="2f089-216">[XML インデックスの作成](../../relational-databases/xml/create-xml-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="2f089-216">[Create XML Indexes](../../relational-databases/xml/create-xml-indexes.md) </span></span>  
 <span data-ttu-id="2f089-217">[データベースダイアグラムのイメージをクリップボードにコピーし &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2f089-217">[Copy an Image of a Database Diagram to the Clipboard &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2f089-218">ダイアグラムのレイアウトの操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2f089-218">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
