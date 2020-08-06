---
title: '[テーブルの追加] ダイアログ ボックス (データベース デザイナー) (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ae9d3763ef66c0a7580cc516169c2f273f36528
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634213"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a><span data-ttu-id="d804a-102">[テーブルの追加] ダイアログ ボックス (データベース デザイナー) (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d804a-102">Add Table Dialog Box (Database Designer) (Visual Database Tools)</span></span>
  <span data-ttu-id="d804a-103">データベース デザイナーでテーブルを追加するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="d804a-103">Lets you add tables in Database Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d804a-104">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d804a-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="d804a-105">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="d804a-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="d804a-106">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d804a-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d804a-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="d804a-107">UI element list</span></span>  
 <span data-ttu-id="d804a-108">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="d804a-108">**Refresh**</span></span>  
 <span data-ttu-id="d804a-109">テーブルの一覧を更新し、現在のデータベースの状態を反映させます。</span><span class="sxs-lookup"><span data-stu-id="d804a-109">Refreshed the list of tables to match the current state of the database.</span></span>  
  
 <span data-ttu-id="d804a-110">**追加**</span><span class="sxs-lookup"><span data-stu-id="d804a-110">**Add**</span></span>  
 <span data-ttu-id="d804a-111">選択したテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d804a-111">Adds the selected table or tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d804a-112">複数のテーブルをダイアグラムに追加する場合は、それらをすべて選択してから **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d804a-112">If you want to add several tables to the diagram, you can select them all before clicking **Add**.</span></span> <span data-ttu-id="d804a-113">または追加する各テーブルをダブルクリックします。すべてダブルクリックしたら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d804a-113">Alternatively, you can double-click each table you want to add, then click **Close** when you are finished.</span></span>  
  
 <span data-ttu-id="d804a-114">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="d804a-114">**Close**</span></span>  
 <span data-ttu-id="d804a-115">テーブルをそれ以上追加せずにダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d804a-115">Closes the dialog box without adding further tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d804a-116">参照</span><span class="sxs-lookup"><span data-stu-id="d804a-116">See Also</span></span>  
 [<span data-ttu-id="d804a-117">ダイアグラムへのテーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d804a-117">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
