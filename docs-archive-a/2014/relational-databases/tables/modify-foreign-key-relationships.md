---
title: 外部キー リレーションシップの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65538
- vdt.ppg.relationships
helpviewer_keywords:
- foreign keys [SQL Server], modifying
- modifying foreign keys
ms.assetid: 0c9ca80d-d79b-44c4-a21e-0fce39c398ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: ba9010b0d634a174dd35391c870d5003aa78efa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632298"
---
# <a name="modify-foreign-key-relationships"></a><span data-ttu-id="7e3a6-102">外部キー リレーションシップの変更</span><span class="sxs-lookup"><span data-stu-id="7e3a6-102">Modify Foreign Key Relationships</span></span>
  <span data-ttu-id="7e3a6-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、リレーションシップの外部キー側を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-103">You can modify the foreign key side of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7e3a6-104">テーブルの外部キーを変更すると、主キー テーブルの列に関連付けられる列が変更されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-104">Modifying a table's foreign key changes which columns are related to columns in the primary key table.</span></span>  
  
 <span data-ttu-id="7e3a6-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7e3a6-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7e3a6-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7e3a6-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7e3a6-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7e3a6-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7e3a6-109">**以下を使用して外部キーを変更するには:**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-109">**To modify a foreign key using:**</span></span>  
  
     [<span data-ttu-id="7e3a6-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7e3a6-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7e3a6-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7e3a6-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7e3a6-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="7e3a6-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7e3a6-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7e3a6-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7e3a6-114">新しい外部キー列は、関連付けられる主キー列のデータ型およびサイズと一致する必要があります。ただし、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-114">The new foreign key column must match the data type and size of the primary key column to which it relates, with these exceptions:</span></span>  
  
-   <span data-ttu-id="7e3a6-115">`char` 列または `sysname` 列は、`varchar` 列と関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-115">A `char` column or `sysname` column can relate to a `varchar` column.</span></span>  
  
-   <span data-ttu-id="7e3a6-116">`binary` 列は、`varbinary` 列と関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-116">A `binary` column can relate to a `varbinary` column.</span></span>  
  
-   <span data-ttu-id="7e3a6-117">alias データ型は、その基本型に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-117">An alias data type can relate to its base type.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7e3a6-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7e3a6-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7e3a6-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="7e3a6-119">Permissions</span></span>  
 <span data-ttu-id="7e3a6-120">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-120">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7e3a6-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7e3a6-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-foreign-key"></a><span data-ttu-id="7e3a6-122">外部キーを変更するには</span><span class="sxs-lookup"><span data-stu-id="7e3a6-122">To modify a foreign key</span></span>  
  
1.  <span data-ttu-id="7e3a6-123">**オブジェクト エクスプローラー**で、外部キーが含まれているテーブルを展開し、 **[キー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-123">In **Object Explorer**, expand the table with the foreign key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="7e3a6-124">変更する外部キーを右クリックし、 **[変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-124">Right-click the foreign key to be modified and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="7e3a6-125">**[外部キー リレーションシップ]** ダイアログ ボックスでは、次の変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-125">In the **Foreign Key Relationships** dialog box, you can make the following modifications.</span></span>  
  
     <span data-ttu-id="7e3a6-126">**[選択されたリレーションシップ]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-126">**Selected Relationship**</span></span>  
     <span data-ttu-id="7e3a6-127">既存のリレーションシップを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-127">Lists existing relationships.</span></span> <span data-ttu-id="7e3a6-128">右側のグリッドにプロパティを表示するリレーションシップを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-128">Select a relationship to show its properties in the grid to the right.</span></span> <span data-ttu-id="7e3a6-129">この一覧が空の場合、テーブルにはリレーションシップがまったく定義されていません。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-129">If the list is empty, no relationships have been defined for the table.</span></span>  
  
     <span data-ttu-id="7e3a6-130">**追加**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-130">**Add**</span></span>  
     <span data-ttu-id="7e3a6-131">新しいリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-131">Create a new relationship.</span></span> <span data-ttu-id="7e3a6-132">リレーションシップを有効にする前に、 **[テーブルと列の指定]** を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-132">The **Tables and Columns Specifications** must be set before the relationship will be valid.</span></span>  
  
     <span data-ttu-id="7e3a6-133">**削除**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-133">**Delete**</span></span>  
     <span data-ttu-id="7e3a6-134">**[選択されたリレーションシップ]** ボックスの一覧で選択したリレーションシップを削除します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-134">Delete the relationship selected in the **Selected Relationships** list.</span></span> <span data-ttu-id="7e3a6-135">追加したリレーションシップを取り消すには、このボタンを使用してリレーションシップを削除します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-135">To cancel the addition of a relationship, use this button to remove the relationship.</span></span>  
  
     <span data-ttu-id="7e3a6-136">**[全般] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-136">**General Category**</span></span>  
     <span data-ttu-id="7e3a6-137">展開して **[作成時または再度有効化するときに既存データを確認]** および **[テーブルと列の指定]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-137">Expand to show **Check Existing Data on Creation or RE-Enabling** and **Tables and Columns Specifications**.</span></span>  
  
     <span data-ttu-id="7e3a6-138">**Check Existing Data on Creation or Re-Enabling**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-138">**Check Existing Data on Creation or Re-Enabling**</span></span>  
     <span data-ttu-id="7e3a6-139">制約を作成した時点、または制約を再度有効にした時点よりも前からテーブルに存在しているすべてのデータについて、その制約に対して検証します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-139">Verify all existing data in the table before the constraint was created or re-enabled, against the constraint.</span></span>  
  
     <span data-ttu-id="7e3a6-140">**[テーブルと列の指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-140">**Tables and Columns Specifications Category**</span></span>  
     <span data-ttu-id="7e3a6-141">展開すると、リレーションシップの外部キーおよび主キー (一意キー) として、どのテーブルのどの列が機能しているかわかります。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-141">Expand to show which columns from which tables act as the foreign key and primary (or unique) key in the relationship.</span></span> <span data-ttu-id="7e3a6-142">これらの値を編集または定義するには、プロパティ フィールドの右にある省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-142">To edit or define these values, click the ellipsis button (**...**) to the right of the property field.</span></span>  
  
     <span data-ttu-id="7e3a6-143">**[外部キーの基本テーブル]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-143">**Foreign Key Base Table**</span></span>  
     <span data-ttu-id="7e3a6-144">選択したリレーションシップで、どのテーブルが外部キーとして機能する列を含んでいるかを示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-144">Shows which table contains the column acting as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="7e3a6-145">**[外部キー列]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-145">**Foreign Key Columns**</span></span>  
     <span data-ttu-id="7e3a6-146">選択したリレーションシップで、どの列が外部キーとして機能しているかを示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-146">Shows which column acts as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="7e3a6-147">**[主/一意キーの基本テーブル]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-147">**Primary/Unique Key Base Table**</span></span>  
     <span data-ttu-id="7e3a6-148">選択したリレーションシップで、どのテーブルが主キー (一意キー) として機能する列を含んでいるかを示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-148">Shows which table contains the column acting as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="7e3a6-149">**[主/一意キー列]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-149">**Primary/Unique Key Columns**</span></span>  
     <span data-ttu-id="7e3a6-150">選択したリレーションシップで、どの列が主キー (一意キー) として機能しているかを示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-150">Shows which column acts as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="7e3a6-151">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-151">**Identity Category**</span></span>  
     <span data-ttu-id="7e3a6-152">展開して **[オブジェクト名]** および **[説明]** のプロパティ フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-152">Expand to show the property fields for **Name** and **Description**.</span></span>  
  
     <span data-ttu-id="7e3a6-153">**Name**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-153">**Name**</span></span>  
     <span data-ttu-id="7e3a6-154">リレーションシップの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-154">Shows the name of the relationship.</span></span> <span data-ttu-id="7e3a6-155">新しいリレーションシップを作成した場合、このプロパティには、 **テーブル デザイナー**のアクティブ ウィンドウのテーブルに基づいて、既定の名前が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-155">When a new relationship is created, it is given a default name based on the table in the active window in **Table Designer**.</span></span> <span data-ttu-id="7e3a6-156">名前はいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-156">You can change the name at any time.</span></span>  
  
     <span data-ttu-id="7e3a6-157">**説明**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-157">**Description**</span></span>  
     <span data-ttu-id="7e3a6-158">リレーションシップの説明です。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-158">Describe the relationship.</span></span> <span data-ttu-id="7e3a6-159">より詳細な説明を記述する場合は、 **[説明]** をクリックしてから、プロパティ フィールドの右に表示される省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-159">To write a more detailed description, click **Description** and then click the ellipsis **(...)** that appears to the right of the property field.</span></span> <span data-ttu-id="7e3a6-160">これにより、テキストを書くことができる領域が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-160">This provides a larger area in which to write text.</span></span>  
  
     <span data-ttu-id="7e3a6-161">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-161">**Table Designer Category**</span></span>  
     <span data-ttu-id="7e3a6-162">展開して **[作成時または再度有効化するときに既存データを確認]** および **[レプリケーションに対して適用]** に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-162">Expand to show information for **Check Existing Data on Creation or Re-Enabling** and **Enforce for Replication**.</span></span>  
  
     <span data-ttu-id="7e3a6-163">**[レプリケーションに対して適用]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-163">**Enforce For Replication**</span></span>  
     <span data-ttu-id="7e3a6-164">レプリケーション エージェントがこのテーブルに対して挿入、更新、または削除操作を行うときに制約を適用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-164">Indicates whether to enforce the constraint when a replication agent performs an insert, update, or delete on this table.</span></span>  
  
     <span data-ttu-id="7e3a6-165">**[外部キーの制約を適用]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-165">**Enforce Foreign Key Constraint**</span></span>  
     <span data-ttu-id="7e3a6-166">リレーションシップの列のデータに対する変更が、外部キー リレーションシップの整合性に違反しているときに、その変更を許可するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-166">Specify whether changes are allowed to the data of the columns in the relationship if those changes would invalidate the integrity of the foreign key relationship.</span></span> <span data-ttu-id="7e3a6-167">このような変更を許可する場合には **[はい]** を、許可しない場合には **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-167">Choose **Yes** if you do not want to allow such changes, and choose **No** if you do want to allow them.</span></span>  
  
     <span data-ttu-id="7e3a6-168">**[INSERT および UPDATE の指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-168">**INSERT and UPDATE Specification Category**</span></span>  
     <span data-ttu-id="7e3a6-169">展開して、そのリレーションシップの **[DeleteRule の設定]** および **[UpdateRule の設定]** に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-169">Expand to show information for the **Delete Rule** and the **Update Rule** for the relationship.</span></span>  
  
     <span data-ttu-id="7e3a6-170">**[DeleteRule の設定]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-170">**Delete Rule**</span></span>  
     <span data-ttu-id="7e3a6-171">外部キー リレーションシップに関連するデータを持つ行をユーザーが削除しようとした場合の処理を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-171">Specify what happens if a user tries to delete a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="7e3a6-172">**[動作なし]** &#xA0;&#xA0;&#xA0;削除操作が許可されていないことをユーザーに通知するエラー メッセージが出力され、DELETE がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-172">**No Action** An error message tells the user that the deletion is not allowed and the DELETE is rolled back.</span></span>  
  
    -   <span data-ttu-id="7e3a6-173">**[重ねて表示]** &#xA0;&#xA0;&#xA0;外部キー リレーションシップに関係するデータを含む行がすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-173">**Cascade** Deletes all rows containing data involved in the foreign key relationship.</span></span> <span data-ttu-id="7e3a6-174">論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-174">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="7e3a6-175">**[Null に設定]** テーブルのすべての外部キー列が null 値を使用できる場合、null 値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-175">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="7e3a6-176">**[既定値の設定]** テーブルのすべての外部キー列に既定値が定義されている場合、既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-176">**Set Default** Sets the value to the default value defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
     <span data-ttu-id="7e3a6-177">**[UpdateRule の設定]**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-177">**Update Rule**</span></span>  
     <span data-ttu-id="7e3a6-178">外部キー リレーションシップに関連するデータを持つ行をユーザーが更新しようとした場合の処理を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-178">Specify what occurs if a user tries to update a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="7e3a6-179">**[動作なし]** &#xA0;&#xA0;&#xA0;更新操作が許可されていないことをユーザーに通知するエラー メッセージを出力し、UPDATE がロールバックします。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-179">**No Action** An error message tells the user that the update is not allowed and the UPDATE is rolled back.</span></span>  
  
    -   <span data-ttu-id="7e3a6-180">**[重ねて表示]** &#xA0;&#xA0;&#xA0;外部キー リレーションシップに関係するデータを含む行がすべて更新されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-180">**Cascade** Updates all rows that contain data involved in the foreign key relationship.</span></span> <span data-ttu-id="7e3a6-181">論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-181">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="7e3a6-182">**[Null に設定]** テーブルのすべての外部キー列が null 値を使用できる場合、null 値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-182">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="7e3a6-183">**[既定値の設定]** &#xA0;&#xA0;テーブルのすべての外部キー列に既定値が定義されている場合、その列に定義されている既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-183">**Set Default** Sets the value to the default value that is defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
4.  <span data-ttu-id="7e3a6-184">**[ファイル]** メニューの **[ _<テーブル名>_ を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-184">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7e3a6-185">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7e3a6-185">Using Transact-SQL</span></span>  
 <span data-ttu-id="7e3a6-186">**外部キーを変更するには**</span><span class="sxs-lookup"><span data-stu-id="7e3a6-186">**To modify a foreign key**</span></span>  
  
 <span data-ttu-id="7e3a6-187">Transact-SQL を使用して FOREIGN KEY 制約を変更するには、まず既存の FOREIGN KEY 制約を削除してから、新しい定義を使用して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-187">To modify a FOREIGN KEY constraint by using Transact-SQL, you must first delete the existing FOREIGN KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="7e3a6-188">詳細については、「 [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) 」および「 [Create Foreign Key Relationships](create-foreign-key-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e3a6-188">For more information, see [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) and [Create Foreign Key Relationships](create-foreign-key-relationships.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
