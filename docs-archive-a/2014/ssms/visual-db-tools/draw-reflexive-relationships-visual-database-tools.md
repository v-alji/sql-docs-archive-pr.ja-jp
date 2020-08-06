---
title: 再帰リレーションシップの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e5056b1a5d0d884edbc4fc818fe8c7ef5cc8ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642458"
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a><span data-ttu-id="5c663-102">再帰リレーションシップの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5c663-102">Draw Reflexive Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="5c663-103">テーブルの 1 つ以上の列を同じテーブルの他の 1 つ以上の列にリンクするには、再帰リレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c663-103">You create a reflexive relationship to link a column or columns in a table with another column or columns in the same table.</span></span> <span data-ttu-id="5c663-104">たとえば、 `employee` テーブルに `emp_id` 列と `mgr_id` 列があるとします。</span><span class="sxs-lookup"><span data-stu-id="5c663-104">For example, suppose the `employee` table has an `emp_id` column and a `mgr_id` column.</span></span> <span data-ttu-id="5c663-105">各管理者は従業員でもあるため、テーブル内のこれらの 2 つの列をリレーションシップの線で関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5c663-105">Because each manager is also an employee, you relate these two columns by drawing a relationship line from the table to itself.</span></span> <span data-ttu-id="5c663-106">このリレーションシップによって、テーブルに追加された各管理者 ID は、既存の従業員 ID と確実に一致します。</span><span class="sxs-lookup"><span data-stu-id="5c663-106">This relationship ensures each manager ID that is added to the table matches an existing employee ID.</span></span>  
  
 <span data-ttu-id="5c663-107">リレーションシップを作成する前に、まずテーブルに主キー制約または UNIQUE 制約を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c663-107">Before you create a relationship, you must first define a primary key or unique constraint for your table.</span></span> <span data-ttu-id="5c663-108">次に、主キー列を目的の列に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5c663-108">You then relate the primary key column to a matching column.</span></span> <span data-ttu-id="5c663-109">リレーションシップを作成すると、対応する列がテーブルの外部キーになります。</span><span class="sxs-lookup"><span data-stu-id="5c663-109">Once you create the relationship, the matching column becomes a foreign key of the table.</span></span>  
  
### <a name="to-draw-a-reflexive-relationship"></a><span data-ttu-id="5c663-110">再帰リレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="5c663-110">To draw a reflexive relationship</span></span>  
  
1.  <span data-ttu-id="5c663-111">データベース ダイアグラムで、他の列と関連付けるデータベース列の行セレクターをクリックし、ポインターをテーブル外部にドラッグして線を表示させます。</span><span class="sxs-lookup"><span data-stu-id="5c663-111">In your database diagram, click the row selector for the database column that you want to relate to another column and drag the pointer outside the table until a line appears.</span></span>  
  
2.  <span data-ttu-id="5c663-112">選択したテーブルに線をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5c663-112">Drag the line back to the selected table.</span></span>  
  
3.  <span data-ttu-id="5c663-113">マウスのボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="5c663-113">Release the mouse button.</span></span> <span data-ttu-id="5c663-114">**[テーブルと列]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c663-114">The **Tables and Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="5c663-115">リレーションシップを形成する外部キー列、および主キーのテーブルと列を選択します。</span><span class="sxs-lookup"><span data-stu-id="5c663-115">Select the foreign key column and the primary key table and column with which you want form a relationship.</span></span>  
  
5.  <span data-ttu-id="5c663-116">**[OK]** を 2 回クリックしてリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c663-116">Choose **OK** twice to create the relationship.</span></span>  
  
 <span data-ttu-id="5c663-117">テーブルに対してクエリを実行するとき、再帰リレーションシップを使用して自己結合を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5c663-117">When you run queries against a table, you can use a reflexive relationship to create a self-join.</span></span> <span data-ttu-id="5c663-118">結合を含むテーブル クエリの実行の詳細については、「 [結合を使用したクエリ (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5c663-118">For information about querying tables with joins, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c663-119">参照</span><span class="sxs-lookup"><span data-stu-id="5c663-119">See Also</span></span>  
 [<span data-ttu-id="5c663-120">結合を使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5c663-120">Query with Joins &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
