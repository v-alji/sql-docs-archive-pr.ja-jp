---
title: ダイアグラムへのテーブルの追加 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe5c1274ac390f4834bd8ac1088258061fc0406d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641398"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a><span data-ttu-id="f91c7-102">ダイアグラムへのテーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f91c7-102">Add Tables to Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="f91c7-103">データベース ダイアグラムにテーブルを追加すると、そのテーブルの構造の編集や、ダイアグラム内にある他のテーブルとの関連付けを行えます。</span><span class="sxs-lookup"><span data-stu-id="f91c7-103">You can add a table to your database diagram to edit its structure or relate it to other tables in your diagram.</span></span> <span data-ttu-id="f91c7-104">テーブルを追加する方法には、ダイアグラムに既存のデータベース テーブルを追加する方法と、データベースで未定義の新しいテーブルを挿入する方法があります。</span><span class="sxs-lookup"><span data-stu-id="f91c7-104">You can either add existing database tables to a diagram or insert a new table that has not yet been defined in the database.</span></span>  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a><span data-ttu-id="f91c7-105">ダイアグラムに新しいテーブルを挿入するには</span><span class="sxs-lookup"><span data-stu-id="f91c7-105">To insert a new table into a diagram</span></span>  
  
1.  <span data-ttu-id="f91c7-106">テーブルを作成するデータベースに接続していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-106">Make sure you are connected to the database in which you want to create the table.</span></span>  
  
     <span data-ttu-id="f91c7-107">現在のダイアグラムにテーブルを作成するには、ツール バーの **[新しいテーブル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91c7-107">To create a table in your current diagram, click the **New Table** button on the toolbar.</span></span>  
  
     <span data-ttu-id="f91c7-108">または</span><span class="sxs-lookup"><span data-stu-id="f91c7-108">-or-</span></span>  
  
     <span data-ttu-id="f91c7-109">ダイアグラムを右クリックし、 **[新しいテーブル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91c7-109">Right-click in the diagram and select **New Table**.</span></span>  
  
2.  <span data-ttu-id="f91c7-110">**[名前の選択]** ダイアログ ボックスで、システムによって割り当てられたテーブル名を必要に応じて変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91c7-110">Modify or accept the system-assigned table name, in the **Choose Name** dialog box, and then choose **OK**.</span></span>  
  
     <span data-ttu-id="f91c7-111">ダイアグラムに新しいテーブルが [標準] ビューで表示されます。</span><span class="sxs-lookup"><span data-stu-id="f91c7-111">A new table appears in the diagram in Standard view.</span></span>  
  
3.  <span data-ttu-id="f91c7-112">新しいテーブルの最初のセルに列名を入力します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-112">In the first cell of the new table, type a column name.</span></span> <span data-ttu-id="f91c7-113">次に、Tab キーを押して次のセルに移動します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-113">Then press the TAB key to move to the next cell.</span></span>  
  
4.  <span data-ttu-id="f91c7-114">**[データ型]** で列のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-114">Under **Data Type**, select a data type for the column.</span></span> <span data-ttu-id="f91c7-115">各列には、名前とデータ型が必要です。</span><span class="sxs-lookup"><span data-stu-id="f91c7-115">Each column must have a name and data type.</span></span>  
  
     <span data-ttu-id="f91c7-116">テーブル デザイナーで列のその他のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f91c7-116">You can set the column's other properties in Table Designer.</span></span>  
  
5.  <span data-ttu-id="f91c7-117">テーブルに列を追加するたびに、手順 3. および手順 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-117">Repeat steps 3 and 4 for each column you want to add to the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f91c7-118">データベース ダイアグラムを保存すると、データベースに新しいテーブルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="f91c7-118">When you save your database diagram, the new table will be added to your database.</span></span>  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a><span data-ttu-id="f91c7-119">ダイアグラムに既存のテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="f91c7-119">To add an existing table to a diagram</span></span>  
  
1.  <span data-ttu-id="f91c7-120">テーブルを編集するデータベースに接続していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-120">Make sure you are connected to the database whose tables you want to edit.</span></span>  
  
2.  <span data-ttu-id="f91c7-121">**[テーブル]** フォルダーでテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-121">Select a table in the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="f91c7-122">データベース ダイアグラムにテーブルをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f91c7-122">Drag the table into your database diagram.</span></span>  
  
4.  <span data-ttu-id="f91c7-123">マウスのボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-123">Release the mouse button.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f91c7-124">選択したテーブルがダイアログの他のテーブルとの間にリレーションシップを持つ場合は、自動的にリレーションシップの線が引かれます。</span><span class="sxs-lookup"><span data-stu-id="f91c7-124">If relationships exist between the selected table and other tables in your diagram, relationship lines are automatically drawn.</span></span>  
  
### <a name="to-add-related-tables-to-a-diagram"></a><span data-ttu-id="f91c7-125">ダイアグラムに関連テーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="f91c7-125">To add related tables to a diagram</span></span>  
  
1.  <span data-ttu-id="f91c7-126">データベース ダイアグラムで、外部キー制約を含む 1 つ以上のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f91c7-126">Select one or more tables with foreign key constraints in the database diagram.</span></span>  
  
2.  <span data-ttu-id="f91c7-127">選択したテーブルの 1 つを右クリックし、 **[関連テーブルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91c7-127">Right-click any of the selected tables and choose **Add Related Tables**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f91c7-128">選択したテーブルから外部キー制約によって参照されるテーブルと、選択したテーブルを外部キー制約によって参照するテーブルの両方が、ダイアグラムに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f91c7-128">Both those tables referenced by a foreign key constraint from the selected table(s) and those referencing the selected table(s) with a foreign key constraint are added to the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91c7-129">参照</span><span class="sxs-lookup"><span data-stu-id="f91c7-129">See Also</span></span>  
 <span data-ttu-id="f91c7-130">[データベースダイアグラムの使用 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f91c7-130">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f91c7-131">データベース ダイアグラムでのテーブルの使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f91c7-131">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
