---
title: '[制約のチェック] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraint
ms.assetid: ad0bbf7f-b0de-406a-bd0a-cb779816b101
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7244984b869a1c68e597984a1cd03e16e53d0306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630750"
---
# <a name="check-constraint-dialog-box-visual-database-tools"></a><span data-ttu-id="98e71-102">[制約のチェック] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="98e71-102">Check Constraint Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="98e71-103">このダイアログ ボックスは、テーブル デザイナーのテーブル定義グリッドを右クリックし、 **[制約のチェック]** をクリックすると表示されます。</span><span class="sxs-lookup"><span data-stu-id="98e71-103">This dialog box appears when you right-click a table definition grid in Table Designer and click **Check Constraints**.</span></span> <span data-ttu-id="98e71-104">このダイアログ ボックスには、データベースのテーブルに関連付けられた、一意でない制約のプロパティ セットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="98e71-104">The dialog box contains a set of properties for non-unique constraints attached to the tables in your database.</span></span> <span data-ttu-id="98e71-105">UNIQUE 制約に適用されるプロパティは、 **[インデックス/キー]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="98e71-105">Properties applying to unique constraints appear in the **Indexes/Keys** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98e71-106">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98e71-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="98e71-107">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="98e71-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="98e71-108">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="98e71-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98e71-109">オプション</span><span class="sxs-lookup"><span data-stu-id="98e71-109">Options</span></span>  
 <span data-ttu-id="98e71-110">**[選択された制約のチェック]**</span><span class="sxs-lookup"><span data-stu-id="98e71-110">**Selected Check Constraints**</span></span>  
 <span data-ttu-id="98e71-111">使用できる CHECK 制約を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-111">Lists available check constraints.</span></span> <span data-ttu-id="98e71-112">制約のプロパティを表示するには、一覧の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="98e71-112">To view the properties of a constraint, select it in the list.</span></span>  
  
 <span data-ttu-id="98e71-113">**追加**</span><span class="sxs-lookup"><span data-stu-id="98e71-113">**Add**</span></span>  
 <span data-ttu-id="98e71-114">選択したデータベース テーブルの制約を新しく作成し、その制約に既定の名前と他の値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="98e71-114">Create a new constraint for the selected database table and provide a default name and other values for the constraint.</span></span> <span data-ttu-id="98e71-115">制約は、その制約用の式を入力するまで、有効にできません。</span><span class="sxs-lookup"><span data-stu-id="98e71-115">The constraint will not become valid until an expression is entered for the constraint.</span></span>  
  
 <span data-ttu-id="98e71-116">**削除**</span><span class="sxs-lookup"><span data-stu-id="98e71-116">**Delete**</span></span>  
 <span data-ttu-id="98e71-117">選択した制約をテーブルから削除します。</span><span class="sxs-lookup"><span data-stu-id="98e71-117">Remove the selected constraint from the table.</span></span> <span data-ttu-id="98e71-118">追加した CHECK 制約を取り消すには、このボタンを使用して制約を削除します。</span><span class="sxs-lookup"><span data-stu-id="98e71-118">To cancel the addition of a check constraint, use this button to remove the constraint.</span></span>  
  
 <span data-ttu-id="98e71-119">**[全般] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="98e71-119">**General Category**</span></span>  
 <span data-ttu-id="98e71-120">展開して **[式]** のプロパティ フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-120">Expand to show the **Expression** property field.</span></span>  
  
 <span data-ttu-id="98e71-121">**[式]**</span><span class="sxs-lookup"><span data-stu-id="98e71-121">**Expression**</span></span>  
 <span data-ttu-id="98e71-122">選択した CHECK 制約の式を表示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-122">Displays the expression for the selected check constraint.</span></span> <span data-ttu-id="98e71-123">新しい制約の場合は、このボックスを終了する前に式を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98e71-123">For new constraints, you must enter the expression before exiting this box.</span></span> <span data-ttu-id="98e71-124">既存の CHECK 制約を編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="98e71-124">You can also edit existing check constraints.</span></span> <span data-ttu-id="98e71-125">詳細については、「 [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98e71-125">For more information, see [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="98e71-126">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="98e71-126">**Identity Category**</span></span>  
 <span data-ttu-id="98e71-127">展開して **[名前]** と **[説明]** のプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-127">Expand to show properties for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="98e71-128">**Name**</span><span class="sxs-lookup"><span data-stu-id="98e71-128">**Name**</span></span>  
 <span data-ttu-id="98e71-129">選択した CHECK 制約の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-129">Shows the name of the selected check constraint.</span></span> <span data-ttu-id="98e71-130">この制約の名前を変更するには、プロパティ フィールドに直接テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="98e71-130">To change the name of this constraint, type the text directly in the property field.</span></span>  
  
 <span data-ttu-id="98e71-131">**説明**</span><span class="sxs-lookup"><span data-stu-id="98e71-131">**Description**</span></span>  
 <span data-ttu-id="98e71-132">この CHECK 制約の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="98e71-132">Describing this check constraint.</span></span> <span data-ttu-id="98e71-133">プロパティ フィールドに入力することで説明を編集できます。またプロパティ フィールドの右側に表示されている省略記号ボタン ( **[...]** ) をクリックすると、 **[説明のプロパティ]** ダイアログ ボックスで説明を編集できます。</span><span class="sxs-lookup"><span data-stu-id="98e71-133">You can edit the description by typing into the property field or you can click the ellipsis button (**...**) that appears to the right of the property field and edit the description in the **Description Property** dialog box.</span></span>  
  
 <span data-ttu-id="98e71-134">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="98e71-134">**Table Designer Category**</span></span>  
 <span data-ttu-id="98e71-135">展開して **[作成時または再度有効化するときに既存データを確認]** 、 **[INSERTs および UPDATEs に適用]** 、および **[レプリケーションに対して適用]** の各プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-135">Expand to show properties for **Check Existing Data on Creation or Re-enabling**, **Enforce For Inserts And Updates**, and **Enforce Replication**.</span></span>  
  
 <span data-ttu-id="98e71-136">**Check Existing Data On Creation or Re-Enabling**</span><span class="sxs-lookup"><span data-stu-id="98e71-136">**Check Existing Data On Creation or Re-Enabling**</span></span>  
 <span data-ttu-id="98e71-137">既存のすべてのデータ (制約を作成する前からテーブルに存在しているデータ) を制約で検証するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="98e71-137">Specify whether all pre-existing data (data existing in the table before the constraint is created) is verified against the constraint.</span></span>  
  
 <span data-ttu-id="98e71-138">**[INSERTs および UPDATEs に適用]**</span><span class="sxs-lookup"><span data-stu-id="98e71-138">**Enforce For Inserts And Updates**</span></span>  
 <span data-ttu-id="98e71-139">テーブルにデータを挿入するときやテーブルのデータを更新するときに、制約を適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="98e71-139">Specify whether the constraint is enforced when data is inserted into or updated in the table.</span></span>  
  
 <span data-ttu-id="98e71-140">**[レプリケーションに対して適用]**</span><span class="sxs-lookup"><span data-stu-id="98e71-140">**Enforce For Replication**</span></span>  
 <span data-ttu-id="98e71-141">レプリケーション エージェントがこのテーブルに対して挿入または更新を行うときに制約を適用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="98e71-141">Indicates whether to enforce the constraint when a replication agent performs an insert or update on this table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e71-142">参照</span><span class="sxs-lookup"><span data-stu-id="98e71-142">See Also</span></span>  
 <span data-ttu-id="98e71-143">[Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="98e71-143">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 <span data-ttu-id="98e71-144">[[インデックスとキー] ダイアログボックス &#40;Visual Database Tools&#41;](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="98e71-144">[Indexes and Keys Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
  
