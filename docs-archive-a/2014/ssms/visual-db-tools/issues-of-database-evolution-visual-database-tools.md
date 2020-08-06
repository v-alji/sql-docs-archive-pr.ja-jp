---
title: 運用されているデータベースを変更するときの問題 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80daa694cd015a83657368902b07da254e6196ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740657"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a><span data-ttu-id="facf9-102">運用されているデータベースを変更するときの問題 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="facf9-102">Issues of Database Evolution (Visual Database Tools)</span></span>
  <span data-ttu-id="facf9-103">配置されているデータベースの構成を変更する場合は、既存のデータおよびデータベース構成との互換性を保って変更を行うよう、特別な注意を払う必要があります。</span><span class="sxs-lookup"><span data-stu-id="facf9-103">If you change the structure of a deployed database, you must take special care that your alteration is compatible with the existing data and database structure.</span></span> <span data-ttu-id="facf9-104">次の変更を行うときは、特別な手順が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="facf9-104">You might need to take special steps when you make the following modifications:</span></span>  
  
-   <span data-ttu-id="facf9-105">**制約の追加** 制約を追加する場合、その制約を満たさないデータがデータベースに既に存在している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="facf9-105">**Adding a Constraint** If you add a constraint, the database might already contain data that does not satisfy it.</span></span> <span data-ttu-id="facf9-106">新しい制約を保存しようとすると、[[保存前の通知] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md) が表示されて、データベース サーバーが新しい制約を作成できないことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="facf9-106">When you try to save the new constraint, the [Post-Save Notifications Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) informs you that the database server could not create the constraint.</span></span> <span data-ttu-id="facf9-107">新しい制約をデータベースに強制的に設定するには、 **[作成時に既存データを確認する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="facf9-107">To force the database to accept the new constraint, you can clear the **Check existing data on creation** check box.</span></span>  
  
-   <span data-ttu-id="facf9-108">**リレーションシップの追加** リレーションシップを作成する場合、主キー テーブルの行に対応していない外部キー テーブルの行が既に存在している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="facf9-108">**Adding a Relationship** If you add a relationship, the database might already contain rows of the foreign-key table that do not have corresponding rows in the primary-key table.</span></span> <span data-ttu-id="facf9-109">つまり、既存のデータが参照整合性を満たしていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="facf9-109">That is, the existing data might not satisfy referential integrity.</span></span> <span data-ttu-id="facf9-110">新しいリレーションシップを保存しようとすると、[[保存前の通知] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md) が表示されて、データベース サーバーが変更された外部キー テーブルを作成できないことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="facf9-110">When you try to save the new relationship, the[Post-Save Notifications Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) informs you that the database server could not save the revised foreign-key table.</span></span> <span data-ttu-id="facf9-111">変更をデータベースに強制的に保存するには、 **[作成時に既存データを確認する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="facf9-111">To force the database to accept the modification, you can clear the **Check existing data on creation** check box.</span></span>  
  
-   <span data-ttu-id="facf9-112">**インデックス付きビューに含まれるテーブルの変更** Microsoft SQL Server のインデックス付きビューに含まれるテーブルを変更すると、ビューのインデックスが失われます。</span><span class="sxs-lookup"><span data-stu-id="facf9-112">**Modifying a Table Contributing to an Indexed View** If you modify a table that contributes to a Microsoft SQL Server indexed view, the indexes on the view will be lost.</span></span> <span data-ttu-id="facf9-113">インデックスの作成方法については、『SQL Server オンライン ブック』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="facf9-113">See the SQL Server Books Online for information on recreating indexes.</span></span>  
  
-   <span data-ttu-id="facf9-114">**オブジェクトの削除** 列、テーブル、またはビューなどのオブジェクトを削除する場合は、まずデータベース内の他のオブジェクトがそのオブジェクトを参照していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="facf9-114">**Deleting an Object** If you delete an object, such as a column, table, or view, check first to be sure that the object is not referenced by another object in the database.</span></span>  
  
 <span data-ttu-id="facf9-115">データベースのデザインを変更する場合は常に、変更の履歴を残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="facf9-115">No matter how you alter the database design, you should retain a history of the alterations.</span></span> <span data-ttu-id="facf9-116">1 つの方法として、実行時用データベースに対して行ったすべての変更について、SQL スクリプトを残しておくことができます。</span><span class="sxs-lookup"><span data-stu-id="facf9-116">One approach is to retain SQL scripts for all modifications that you ever make to your production database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facf9-117">参照</span><span class="sxs-lookup"><span data-stu-id="facf9-117">See Also</span></span>  
 <span data-ttu-id="facf9-118">[Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="facf9-118">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="facf9-119">マルチユーザー環境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="facf9-119">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
