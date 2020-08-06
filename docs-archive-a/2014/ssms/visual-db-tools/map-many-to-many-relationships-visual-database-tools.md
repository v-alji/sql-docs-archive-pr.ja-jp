---
title: 多対多リレーションシップの割り当て (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbcbdbdf8d8371baa2a817e43b831535723be7ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644762"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a><span data-ttu-id="16dc4-102">多対多リレーションシップの割り当て (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="16dc4-102">Map Many-to-Many Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="16dc4-103">多対多リレーションシップを使用すると、テーブルの各行を他のテーブルの複数の行と関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="16dc4-103">Many-to-many relationships let you relate each row in one table to many rows in another table, and vice versa.</span></span> <span data-ttu-id="16dc4-104">たとえば、 `authors` テーブルと `titles` テーブルとの間に多対多リレーションシップを作成し、各著者をその全著作に対応付け、各著作をすべての著者に対応付けることができます。</span><span class="sxs-lookup"><span data-stu-id="16dc4-104">For example, you could create a many-to-many relationship between the `authors` table and the `titles` table to match each author to all of his or her books and to match each book to all of its authors.</span></span> <span data-ttu-id="16dc4-105">一方のテーブルから一対多リレーションシップを作成すると、各著作には著者が 1 人しか存在しない、または各著者には 1 冊の著作しかないという情報が誤って示されることになります。</span><span class="sxs-lookup"><span data-stu-id="16dc4-105">Creating a one-to-many relationship from either table would incorrectly indicate that every book can have only one author, or that every author can write only one book.</span></span>  
  
 <span data-ttu-id="16dc4-106">テーブル間の多対多リレーションシップは、それぞれのデータベースで交差テーブルによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="16dc4-106">Many-to-many relationships between tables are accommodated in databases by means of junction tables.</span></span> <span data-ttu-id="16dc4-107">交差テーブルには、関連付ける 2 つのテーブルの各主キー列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="16dc4-107">A junction table contains the primary key columns of the two tables you want to relate.</span></span> <span data-ttu-id="16dc4-108">これを使用して、2 つのテーブルの各主キー列から、交差テーブル内の対応する列へのリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-108">You then create a relationship from the primary key columns of each of those two tables to the matching columns in the junction table.</span></span> <span data-ttu-id="16dc4-109">pubs データベースでは、 `titleauthor` テーブルが交差テーブルです。</span><span class="sxs-lookup"><span data-stu-id="16dc4-109">In the pubs database, the `titleauthor` table is a junction table.</span></span>  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a><span data-ttu-id="16dc4-110">テーブル間で多対多リレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="16dc4-110">To create a many-to-many relationship between tables</span></span>  
  
1.  <span data-ttu-id="16dc4-111">データベース ダイアグラムで、多対多リレーションシップを作成する各テーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-111">In your database diagram, add the tables that you want to create a many-to-many relationship between.</span></span>  
  
2.  <span data-ttu-id="16dc4-112">ダイアグラムを右クリックし、ショートカット メニューの **[新しいテーブル]** をクリックして 3 つ目のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-112">Create a third table by right-clicking the diagram and choosing **New Table** from the shortcut menu.</span></span> <span data-ttu-id="16dc4-113">これが交差テーブルになります。</span><span class="sxs-lookup"><span data-stu-id="16dc4-113">This will become the junction table.</span></span>  
  
3.  <span data-ttu-id="16dc4-114">**[名前の選択]** ダイアログ ボックスで、システムによって割り当てられたテーブル名を変更します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-114">In the **Choose Name** dialog box, change the system-assigned table name.</span></span> <span data-ttu-id="16dc4-115">たとえば、 `titles` テーブルと `authors` テーブルとの間の交差テーブルは、現在 `titleauthors`という名前です。</span><span class="sxs-lookup"><span data-stu-id="16dc4-115">For example, the junction table between the `titles` table and the `authors` table is now named `titleauthors`.</span></span>  
  
4.  <span data-ttu-id="16dc4-116">2 つのテーブルの各主キー列を交差テーブルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="16dc4-116">Copy the primary key columns from each of the other two tables to the junction table.</span></span> <span data-ttu-id="16dc4-117">他の列も、他のテーブルに追加するのと同様に交差テーブルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="16dc4-117">You can add other columns to this table, just as you can to any other table.</span></span>  
  
5.  <span data-ttu-id="16dc4-118">交差テーブルで、他の 2 つのテーブルの主キーをすべて含めて主キーを設定します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-118">In the junction table, set the primary key to include all the primary key columns from the other two tables.</span></span> <span data-ttu-id="16dc4-119">詳細については、「[主キーの作成](../../relational-databases/tables/create-primary-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16dc4-119">For details, see [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).</span></span>  
  
6.  <span data-ttu-id="16dc4-120">2 つの各主テーブルと交差テーブルとの間に一対多リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-120">Define a one-to-many relationship between each of the two primary tables and the junction table.</span></span> <span data-ttu-id="16dc4-121">交差テーブルは、作成するリレーションシップの "多" 側に配置します。</span><span class="sxs-lookup"><span data-stu-id="16dc4-121">The junction table should be at the "many" side of both of the relationships you create.</span></span> <span data-ttu-id="16dc4-122">詳細については、「[外部キーリレーションシップの作成](../../relational-databases/tables/create-foreign-key-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16dc4-122">For details, see [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="16dc4-123">データベース ダイアグラムで交差テーブルを作成しても、関連テーブルから交差テーブルにデータは挿入されません。</span><span class="sxs-lookup"><span data-stu-id="16dc4-123">The creation of a junction table in a database diagram does not insert data from the related tables into the junction table.</span></span> <span data-ttu-id="16dc4-124">テーブルにデータを挿入する方法については、「[方法 : 複製挿入クエリを作成する (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16dc4-124">For information about inserting data into a table, see [Create Insert Results Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16dc4-125">参照</span><span class="sxs-lookup"><span data-stu-id="16dc4-125">See Also</span></span>  
 [<span data-ttu-id="16dc4-126">データベース ダイアグラムの使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="16dc4-126">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](work-with-database-diagrams-visual-database-tools.md)  
  
  
