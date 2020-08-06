---
title: '[テーブルの追加] ダイアログボックス (クエリデザイナーおよびビューデザイナー) (Visual Database Tools) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d7bf30cbdd37927735c36f184208a1ded957763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634212"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a><span data-ttu-id="8a354-102">[テーブルの追加] ダイアログ ボックス (クエリ デザイナーおよびビュー デザイナー) (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8a354-102">Add Table Dialog Box (Query and View Designers) (Visual Database Tools)</span></span>
  <span data-ttu-id="8a354-103">このダイアログ ボックスを使用すると、クエリまたはビューに、テーブル、ビュー、ユーザー定義関数、またはシノニムを追加できます。</span><span class="sxs-lookup"><span data-stu-id="8a354-103">This dialog box lets you add tables, views, user-defined functions, or synonyms to a query or view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a354-104">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a354-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="8a354-105">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="8a354-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="8a354-106">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="8a354-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8a354-107">オプション</span><span class="sxs-lookup"><span data-stu-id="8a354-107">Options</span></span>  
 <span data-ttu-id="8a354-108">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="8a354-108">**Tables**</span></span>  
 <span data-ttu-id="8a354-109">**[ダイアグラム]** ペインに追加できるテーブルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8a354-109">Lists the tables you can add to the **Diagram** pane.</span></span> <span data-ttu-id="8a354-110">テーブルを追加するには、テーブルを選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-110">To add a table, select it and click **Add**.</span></span> <span data-ttu-id="8a354-111">複数のテーブルを一度に追加するには、それらのテーブルを選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-111">To add several tables at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="8a354-112">**ビュー**</span><span class="sxs-lookup"><span data-stu-id="8a354-112">**Views**</span></span>  
 <span data-ttu-id="8a354-113">**[ダイアグラム]** ペインに追加できるビューを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8a354-113">Lists the views you can add to the **Diagram** pane.</span></span> <span data-ttu-id="8a354-114">ビューを追加するには、ビューを選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-114">To add a view, select it and click **Add**.</span></span> <span data-ttu-id="8a354-115">複数のビューを一度に追加するには、それらのビューを選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-115">To add several views at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="8a354-116">**関数**</span><span class="sxs-lookup"><span data-stu-id="8a354-116">**Functions**</span></span>  
 <span data-ttu-id="8a354-117">**[ダイアグラム]** ペインに追加できるユーザー定義関数を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8a354-117">Lists the user-defined functions you can add to the **Diagram** pane.</span></span> <span data-ttu-id="8a354-118">関数を追加するには、関数を選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-118">To add a function, select it and click **Add**.</span></span> <span data-ttu-id="8a354-119">複数の関数を一度に追加するには、それらの関数を選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-119">To add several functions at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="8a354-120">**シノニム**</span><span class="sxs-lookup"><span data-stu-id="8a354-120">**Synonyms**</span></span>  
 <span data-ttu-id="8a354-121">**[ダイアグラム]** ペインに追加できるシノニムを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8a354-121">Lists the synonyms you can add to the **Diagram** pane.</span></span> <span data-ttu-id="8a354-122">シノニムを追加するには、シノニムを選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-122">To add a synonym, select it and click **Add**.</span></span> <span data-ttu-id="8a354-123">複数のシノニムを一度に追加するには、それらのシノニムを選択して **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a354-123">To add several synonyms at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="8a354-124">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="8a354-124">**Refresh**</span></span>  
 <span data-ttu-id="8a354-125">一覧を更新します。最後の一覧取得以降にデータベースに対して行われた変更が掲載されます。</span><span class="sxs-lookup"><span data-stu-id="8a354-125">Update the list to include any changes made to the database since the list was last retrieved.</span></span>  
  
 <span data-ttu-id="8a354-126">**追加**</span><span class="sxs-lookup"><span data-stu-id="8a354-126">**Add**</span></span>  
 <span data-ttu-id="8a354-127">選択した項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="8a354-127">Add the selected item or items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a354-128">参照</span><span class="sxs-lookup"><span data-stu-id="8a354-128">See Also</span></span>  
 [<span data-ttu-id="8a354-129">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8a354-129">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
