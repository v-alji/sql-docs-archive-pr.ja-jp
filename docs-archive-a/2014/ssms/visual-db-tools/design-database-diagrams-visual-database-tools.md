---
title: データベース ダイアグラムのデザイン (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65536
- vdt.DatabaseDesigner
helpviewer_keywords:
- Database Diagram Designer
- Visual Database Tools [SQL Server], database diagrams
- database diagrams [SQL Server], designing
- diagrams [SQL Server], designing
ms.assetid: 6d2c14e1-3d73-4d10-ae5b-7f2b5d6c4ea8
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb4cbc518b6878ed8fb6e9f7d5d2d00803ab4d62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713694"
---
# <a name="design-database-diagrams-visual-database-tools"></a><span data-ttu-id="81471-102">データベース ダイアグラムのデザイン (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-102">Design Database Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="81471-103">データベース デザイナーは、接続先のデータベースをデザインしたりビジュアル化したりできるビジュアル ツールです。</span><span class="sxs-lookup"><span data-stu-id="81471-103">The Database Designer is a visual tool that allows you to design and visualize a database to which you are connected.</span></span> <span data-ttu-id="81471-104">データベースをデザインするときは、データベース デザイナーを使用して、テーブル、列、キー、インデックス、リレーションシップ、および制約の作成、編集、または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="81471-104">When designing a database, you can use Database Designer to create, edit, or delete tables, columns, keys, indexes, relationships, and constraints.</span></span> <span data-ttu-id="81471-105">データベースをビジュアル化するには、データベースに含まれるテーブル、列、キー、およびリレーションシップの一部または全部を表すダイアグラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="81471-105">To visualize a database, you can create one or more diagrams illustrating some or all of the tables, columns, keys, and relationships in it.</span></span>  
  
 <span data-ttu-id="81471-106">![テーブル リレーションシップを説明するデータベース ダイアグラム](../../database-engine/media//dv3w7c1.gif "テーブル リレーションシップを説明するデータベース ダイアグラム")</span><span class="sxs-lookup"><span data-stu-id="81471-106">![Database diagram illustrating table relationships](../../database-engine/media//dv3w7c1.gif "Database diagram illustrating table relationships")</span></span>  
  
 <span data-ttu-id="81471-107">1 つのデータベースから、いくつでもデータベース ダイアグラムを作成できます。また、1 つのデータベース テーブルは、複数のダイアグラムに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="81471-107">For any database, you can create as many database diagrams as you like; each database table can appear on any number of diagrams.</span></span> <span data-ttu-id="81471-108">したがって、異なるダイアグラムを作成し、データベースの異なる部分をビジュアル化したり、デザインの異なる面を強調したりできます。</span><span class="sxs-lookup"><span data-stu-id="81471-108">Thus, you can create different diagrams to visualize different portions of the database, or to accentuate different aspects of the design.</span></span> <span data-ttu-id="81471-109">たとえば、大きなダイアグラムを作成した場合はすべてのテーブルと列を表示することができ、小さいダイアグラムの場合は列を表示しないですべてのテーブルだけを表示するようにできます。</span><span class="sxs-lookup"><span data-stu-id="81471-109">For example, you can create a large diagram showing all tables and columns, and you can create a smaller diagram showing all tables without showing the columns.</span></span>  
  
 <span data-ttu-id="81471-110">作成したデータベース ダイアグラムは、関連するデータベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="81471-110">Each database diagram you create is stored in the associated database.</span></span>  
  
## <a name="tables-and-columns-in-a-database-diagram"></a><span data-ttu-id="81471-111">データベース ダイアグラムに表示されるテーブルと列</span><span class="sxs-lookup"><span data-stu-id="81471-111">Tables and Columns in a Database Diagram</span></span>  
 <span data-ttu-id="81471-112">データベース ダイアグラムの中では、テーブルは、タイトル バー、行セレクター、一連のプロパティ列という 3 つの異なる機能で表示されます。</span><span class="sxs-lookup"><span data-stu-id="81471-112">Within a database diagram, each table can appear with three distinct features: a title bar, a row selector, and a set of property columns.</span></span>  
  
 <span data-ttu-id="81471-113">**タイトル バー** タイトル バーにはテーブルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81471-113">**Title Bar** The title bar shows the name of the table</span></span>  
  
 <span data-ttu-id="81471-114">テーブルを変更し、まだ保存していない場合は、保存されていない変更があることを示すアスタリスク (\*) がテーブル名の最後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="81471-114">If you have modified a table and have not yet saved it, an asterisk (\*) appears at the end of the table name to indicate unsaved changes.</span></span> <span data-ttu-id="81471-115">変更したテーブルおよびダイアグラムの保存については、「 [データベース ダイアグラムの使用 (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="81471-115">For information about saving modified tables and diagrams, see [Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md)</span></span>  
  
 <span data-ttu-id="81471-116">**行セレクター** 行セレクターをクリックすると、テーブルの中のデータベース列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="81471-116">**Row Selector** You can click the row selector to select a database column in the table.</span></span> <span data-ttu-id="81471-117">列がテーブルの主キーに含まれる場合は、行セレクターに鍵の記号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81471-117">The row selector displays a key symbol if the column is in the table's primary key.</span></span> <span data-ttu-id="81471-118">主キーの詳細については、「 [Primary Key 制約と Foreign Key 制約](../../relational-databases/tables/primary-and-foreign-key-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81471-118">For information about primary keys, see [Primary and Foreign Key Constraints](../../relational-databases/tables/primary-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="81471-119">**プロパティ列** プロパティ列は、テーブルの特定のビューにだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="81471-119">**Property Columns** The set of property columns is visible only in the certain views of your table.</span></span> <span data-ttu-id="81471-120">テーブルは、5 種類のいずれのビューでも表示できるので、ダイアグラムのサイズとレイアウトを管理するときの参考になります。</span><span class="sxs-lookup"><span data-stu-id="81471-120">You can view a table in any of five different views to help you manage the size and layout of your diagram.</span></span>  
  
 <span data-ttu-id="81471-121">テーブル ビューの詳細については、「[ダイアグラムに表示される情報の量のカスタマイズ (Visual Database Tools)](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81471-121">For more information about table views, see [Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md).</span></span>  
  
## <a name="relationships-in-a-database-diagram"></a><span data-ttu-id="81471-122">データベース ダイアグラムにおけるリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="81471-122">Relationships in a Database Diagram</span></span>  
 <span data-ttu-id="81471-123">データベース ダイアグラムでは、各リレーションシップの機能が、端点、線のスタイル、および関連テーブルという 3 つの異なる機能によって示されます。</span><span class="sxs-lookup"><span data-stu-id="81471-123">Within a database diagram, each relationship can appear with three distinct features: endpoints, a line style, and related tables.</span></span>  
  
 <span data-ttu-id="81471-124">**端点** 線の端点は、リレーションシップが一対一なのか一対多なのかを示しています。</span><span class="sxs-lookup"><span data-stu-id="81471-124">**Endpoints** The endpoints of the line indicate whether the relationship is one-to-one or one-to-many.</span></span> <span data-ttu-id="81471-125">リレーションシップの一方の端点には鍵が、もう一方の端点には数字の 8 に似た記号が表示されている場合は、一対多のリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="81471-125">If a relationship has a key at one endpoint and a figure-eight at the other, it is a one-to-many relationship.</span></span> <span data-ttu-id="81471-126">リレーションシップの両方の端点に鍵が表示されている場合は、一対一のリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="81471-126">If a relationship has a key at each endpoint, it is a one-to-one relationship.</span></span>  
  
 <span data-ttu-id="81471-127">**線のスタイル** 端点ではなく線自体は、新しいデータを外部キー テーブルに追加するときに、データベース管理システム (DBMS) がリレーションシップに対して参照整合性を適用するかどうかを示しています。</span><span class="sxs-lookup"><span data-stu-id="81471-127">**Line Style** The line itself (not its endpoints) indicates whether the Database Management System (DBMS) enforces referential integrity for the relationship when new data is added to the foreign-key table.</span></span> <span data-ttu-id="81471-128">線が実線の場合は、外部キー テーブルの行を追加または変更すると、リレーションシップに対する参照整合性が DBMS により適用されます。</span><span class="sxs-lookup"><span data-stu-id="81471-128">If the line appears solid, the DBMS enforces referential integrity for the relationship when rows are added or modified in the foreign-key table.</span></span> <span data-ttu-id="81471-129">線が点線の場合は、外部キー テーブルの行を追加または変更しても、リレーションシップに対する参照整合性は適用されません。</span><span class="sxs-lookup"><span data-stu-id="81471-129">If the line appears dotted, the DBMS does not enforce referential integrity for the relationship when rows are added or modified in the foreign-key table.</span></span>  
  
 <span data-ttu-id="81471-130">**関連テーブル** リレーションシップの線は、あるテーブルと別のテーブルの間に外部キー テーブルのリレーションシップが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="81471-130">**Related Tables** The relationship line indicates that a foreign-key relationship exists between one table and another.</span></span> <span data-ttu-id="81471-131">一対多のリレーションシップの場合は、線に数字の 8 に似た記号が付いている側のテーブルが外部キー テーブルです。</span><span class="sxs-lookup"><span data-stu-id="81471-131">For a one-to-many relationship, the foreign-key table is the table near the line's figure-eight symbol.</span></span> <span data-ttu-id="81471-132">線の両方の端点が同じテーブルに接続している場合、そのリレーションシップは再帰リレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="81471-132">If both endpoints of the line attach to the same table, the relationship is a reflexive relationship.</span></span> <span data-ttu-id="81471-133">詳細については、「[再帰リレーションシップの作成 (Visual Database Tools)](draw-reflexive-relationships-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81471-133">For more information, see [Draw Reflexive Relationships &#40;Visual Database Tools&#41;](draw-reflexive-relationships-visual-database-tools.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81471-134">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="81471-134">In this Section</span></span>  
 [<span data-ttu-id="81471-135">データベース ダイアグラムの所有権について (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-135">Understand Database Diagram Ownership &#40;Visual Database Tools&#41;</span></span>](understand-database-diagram-ownership-visual-database-tools.md)  
  
 [<span data-ttu-id="81471-136">データベース ダイアグラム デザイナー内でのナビゲーション (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-136">Navigate in Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](navigate-in-database-diagram-designer-visual-database-tools.md)  
  
 [<span data-ttu-id="81471-137">データベース ダイアグラム デザイナーの設定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-137">Set Up Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](set-up-database-diagram-designer-visual-database-tools.md)  
  
 [<span data-ttu-id="81471-138">旧エディションのデータベース ダイアグラムのアップグレード (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-138">Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;</span></span>](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
  
 [<span data-ttu-id="81471-139">データベース ダイアグラム デザイナーを開く (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-139">Open Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](open-database-diagram-designer-visual-database-tools.md)  
  
## <a name="see-also"></a><span data-ttu-id="81471-140">参照</span><span class="sxs-lookup"><span data-stu-id="81471-140">See Also</span></span>  
 <span data-ttu-id="81471-141">[データベースダイアグラムの使用 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="81471-141">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="81471-142">[データベースダイアグラムでのテーブルの操作 &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="81471-142">[Work with Tables in Database Diagram &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="81471-143">ダイアグラムのレイアウトの操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81471-143">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
