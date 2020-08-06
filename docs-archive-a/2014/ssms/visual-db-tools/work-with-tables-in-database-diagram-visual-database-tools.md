---
title: データベース ダイアグラムでのテーブルの操作 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], tables
- Table Designer, database diagrams
- tables [SQL Server], database diagrams
- database diagrams [SQL Server], Table Designer
ms.assetid: ee2c5d84-22bf-4597-ac70-a27ed8cc94f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f648cd5fd08ed47c6670491ad5b7f3d75b7ead47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642453"
---
# <a name="work-with-tables-in-database-diagram-visual-database-tools"></a><span data-ttu-id="6f23f-102">データベース ダイアグラムでのテーブルの操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-102">Work with Tables in Database Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="6f23f-103">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用すると、データベース テーブルを変更および作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f23f-103">You can modify and create database tables in either Table Designer or Database Diagram Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f23f-104">テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f23f-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="6f23f-105">テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。</span><span class="sxs-lookup"><span data-stu-id="6f23f-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="6f23f-106">パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。</span><span class="sxs-lookup"><span data-stu-id="6f23f-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f23f-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6f23f-107">In This Section</span></span>  
 [<span data-ttu-id="6f23f-108">ダイアグラムへのテーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-108">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
 [<span data-ttu-id="6f23f-109">ダイアグラムへの関連テーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-109">Add Related Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-related-tables-to-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="6f23f-110">ダイアグラムで選択したテーブルの保存 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-110">Save Selected Tables on a Diagram &#40;Visual Database Tools&#41;</span></span>](save-selected-tables-on-a-diagram-visual-database-tools.md)  
  
 [<span data-ttu-id="6f23f-111">データベース ダイアグラム間でのテーブルのコピー (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-111">Copy Tables from One Database Diagrams to Another &#40;Visual Database Tools&#41;</span></span>](copy-tables-from-one-database-diagrams-to-another-visual-database-tools.md)  
  
 [<span data-ttu-id="6f23f-112">データベース ダイアグラムからのテーブルの削除 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-112">Remove Tables from Database Diagrams &#40;Visual Database Tools&#41;</span></span>](remove-tables-from-database-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="6f23f-113">多対多リレーションシップの割り当て (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-113">Map Many-to-Many Relationships &#40;Visual Database Tools&#41;</span></span>](map-many-to-many-relationships-visual-database-tools.md)  
  
 [<span data-ttu-id="6f23f-114">再帰リレーションシップの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f23f-114">Draw Reflexive Relationships &#40;Visual Database Tools&#41;</span></span>](draw-reflexive-relationships-visual-database-tools.md)  
  
## <a name="reference"></a><span data-ttu-id="6f23f-115">リファレンス</span><span class="sxs-lookup"><span data-stu-id="6f23f-115">Reference</span></span>  
 <span data-ttu-id="6f23f-116">[[テーブルの追加] ダイアログ ボックス (データベース デザイナー) (Visual Database Tools)](add-table-dialog-box-database-designer-visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="6f23f-116">[Add Table Dialog Box &#40;Database Designer&#41; &#40;Visual Database Tools&#41;](add-table-dialog-box-database-designer-visual-database-tools.md)</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f23f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f23f-117">Related Sections</span></span>  
  
