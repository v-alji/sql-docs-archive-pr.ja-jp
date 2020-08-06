---
title: '[テーブルと列] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28e0c52b74413a3a5a4122412c6028b34e974b09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644259"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="fd544-102">[テーブルと列] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fd544-102">Tables and Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="fd544-103">このダイアログ ボックスを使用すると、あるテーブルの主キーを別のテーブルの外部キーに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="fd544-103">Use this dialog box to map a primary key in one table to a foreign key in another.</span></span> <span data-ttu-id="fd544-104">このダイアログ ボックスにアクセスするには、 **[テーブル デザイナー]** メニューの **[リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd544-104">To access this dialog box, from the **Table Designer** menu, click **Relationships**.</span></span> <span data-ttu-id="fd544-105">**[外部キーのリレーションシップ]** ダイアログ ボックスの **[テーブルと列の指定]** フィールドをクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd544-105">In the **Foreign Key Relationships** dialog box, click the **Tables and Columns Specification** field, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd544-106">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd544-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="fd544-107">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="fd544-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="fd544-108">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="fd544-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd544-109">Options</span><span class="sxs-lookup"><span data-stu-id="fd544-109">Options</span></span>  
 <span data-ttu-id="fd544-110">**[リレーションシップ名]**</span><span class="sxs-lookup"><span data-stu-id="fd544-110">**Relationship name**</span></span>  
 <span data-ttu-id="fd544-111">リレーションシップの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="fd544-111">Shows the name of the relationship.</span></span>  
  
 <span data-ttu-id="fd544-112">**[主キー テーブル]**</span><span class="sxs-lookup"><span data-stu-id="fd544-112">**Primary Key Table**</span></span>  
 <span data-ttu-id="fd544-113">データベース内のテーブルの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="fd544-113">Lists the tables in the database.</span></span> <span data-ttu-id="fd544-114">リレーションシップの主キー側になるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="fd544-114">Choose the table that will be on the primary-key side of the relationship.</span></span>  
  
 <span data-ttu-id="fd544-115">**[外部キーのテーブル]**</span><span class="sxs-lookup"><span data-stu-id="fd544-115">**Foreign Key Table**</span></span>  
 <span data-ttu-id="fd544-116">リレーションシップの外部キー側のテーブルを表示します。</span><span class="sxs-lookup"><span data-stu-id="fd544-116">Shows the table on the foreign key side of the relationship.</span></span> <span data-ttu-id="fd544-117">これは、テーブル デザイナーで現在選択されているテーブルです。</span><span class="sxs-lookup"><span data-stu-id="fd544-117">This is the table currently selected in Table Designer.</span></span>  
  
 <span data-ttu-id="fd544-118">**[主キー テーブル] の下のグリッド**</span><span class="sxs-lookup"><span data-stu-id="fd544-118">**Grid beneath Primary Key Table**</span></span>  
 <span data-ttu-id="fd544-119">**[主キー テーブル]** ボックスで選択されているテーブルの列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fd544-119">List the columns of the table selected in the **Primary Key Table** list.</span></span> <span data-ttu-id="fd544-120">そのテーブルの主キーになる列を入力します。</span><span class="sxs-lookup"><span data-stu-id="fd544-120">Enter the columns contributing to that table's primary key.</span></span>  
  
 <span data-ttu-id="fd544-121">**[外部キーのテーブル] の下のグリッド**</span><span class="sxs-lookup"><span data-stu-id="fd544-121">**Grid beneath Foreign Key Table**</span></span>  
 <span data-ttu-id="fd544-122">**[外部キーのテーブル]** ボックスで選択されているテーブルの列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fd544-122">List the columns of the table selected in the **Foreign Key Table** list.</span></span> <span data-ttu-id="fd544-123">主キー列に対応する外部キーのテーブルの外部キー列を入力します。</span><span class="sxs-lookup"><span data-stu-id="fd544-123">Enter the foreign-key column of the foreign-key table that corresponds to the primary key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd544-124">外部キーに選択した列は、対応する主キー列と同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd544-124">The columns you choose for the foreign key must have the same data type of the primary columns they correspond to.</span></span> <span data-ttu-id="fd544-125">各キーには同じ数の列が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd544-125">There must be an equal number of columns in each of the keys.</span></span> <span data-ttu-id="fd544-126">たとえば、リレーションシップの主キー側になるテーブルの主キーが 2 列で構成されている場合、この各列がリレーションシップの外部キー側になるテーブルの列と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd544-126">For example, if the primary key of the table on the primary side of the relationship is made up of two columns, you will need to match each of those columns with a column in the table for the foreign key side of the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd544-127">参照</span><span class="sxs-lookup"><span data-stu-id="fd544-127">See Also</span></span>  
 [<span data-ttu-id="fd544-128">外部キーのリレーションシップの作成</span><span class="sxs-lookup"><span data-stu-id="fd544-128">Create Foreign Key Relationships</span></span>](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
