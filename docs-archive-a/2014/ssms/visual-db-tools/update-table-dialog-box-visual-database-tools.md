---
title: '[テーブルの更新] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 426c842b85d6404ba101b57a9b572107dbc76bb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642452"
---
# <a name="update-table-dialog-box-visual-database-tools"></a><span data-ttu-id="4786d-102">[テーブルの更新] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4786d-102">Update Table Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="4786d-103">このダイアログ ボックスを使用すると、更新するテーブルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4786d-103">This dialog box allows you to specify the table to be updated.</span></span>  
  
 <span data-ttu-id="4786d-104">クエリの種類を UPDATE クエリに変更するときに、ダイアグラム ペインに複数のテーブルが表示される場合、このダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4786d-104">This dialog box appears if more than one table is displayed in the Diagram pane when you change a query's type to be an Update query.</span></span>  
  
 <span data-ttu-id="4786d-105">更新するテーブルを選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4786d-105">Select the table to update, and then choose **OK**.\</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4786d-106">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4786d-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="4786d-107">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="4786d-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="4786d-108">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="4786d-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4786d-109">参照</span><span class="sxs-lookup"><span data-stu-id="4786d-109">See Also</span></span>  
 [<span data-ttu-id="4786d-110">更新クエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4786d-110">Create Update Queries &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
