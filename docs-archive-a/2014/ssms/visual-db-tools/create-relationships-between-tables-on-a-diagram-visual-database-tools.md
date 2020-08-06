---
title: ダイアグラムのテーブル間のリレーションシップの作成 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7d627a37f84dcb66b2129bb9c7dbc5890ccd46c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740678"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a><span data-ttu-id="744e2-102">ダイアグラムでテーブル間のリレーションシップを作成する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="744e2-102">Create Relationships Between Tables on a Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="744e2-103">ダイアグラム デザイナーでは、テーブル間で列をドラッグすることにより、異なるテーブルの列の間にリレーションシップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="744e2-103">You can create relationships between columns in different tables in the Diagram Designer by dragging columns between tables.</span></span>  
  
### <a name="to-create-a-relationship-graphically"></a><span data-ttu-id="744e2-104">リレーションシップをグラフィカルに作成するには</span><span class="sxs-lookup"><span data-stu-id="744e2-104">To create a relationship graphically</span></span>  
  
1.  <span data-ttu-id="744e2-105">データベース デザイナーで、別のテーブル内の列に関連付ける 1 つ以上のデータベース列の行セレクターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="744e2-105">In Database Designer, click the row selector for one or more database columns that you want to relate to a column in another table.</span></span>  
  
2.  <span data-ttu-id="744e2-106">選択した列を関連テーブルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="744e2-106">Drag the selected column(s) to the related table.</span></span>  
  
3.  <span data-ttu-id="744e2-107">**[外部キーのリレーションシップ]** ダイアログ ボックスと **[テーブルと列]** ダイアログ ボックスが表示されます。後者のダイアログ ボックスが手前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="744e2-107">Two dialog boxes appear: **Foreign Key Relationship** and **Tables and Columns**, with the latter appearing in the foreground.</span></span>  
  
4.  <span data-ttu-id="744e2-108">**[リレーションシップ名]** には、FK_*localtable*_*foreigntable*という形式の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="744e2-108">**Relationship name** has a system-provided name in the format FK_*localtable*_*foreigntable*.</span></span> <span data-ttu-id="744e2-109">この値は変更できます。</span><span class="sxs-lookup"><span data-stu-id="744e2-109">You may change this value.</span></span>  
  
5.  <span data-ttu-id="744e2-110">**[主キー テーブル]** に適切なテーブルが指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="744e2-110">Verify that **Primary key table** specifies the correct table.</span></span>  
  
6.  <span data-ttu-id="744e2-111">グリッドには、ローカル列とそれに対応する外部列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="744e2-111">The grid lists the local columns and their matching foreign columns.</span></span> <span data-ttu-id="744e2-112">テーブル列の追加や削除またはマッピングの変更が可能です。</span><span class="sxs-lookup"><span data-stu-id="744e2-112">You can add or remove table columns or change mappings.</span></span>  
  
7.  <span data-ttu-id="744e2-113">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="744e2-113">Choose **OK**.</span></span>  
  
     <span data-ttu-id="744e2-114">**[外部キーのリレーションシップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="744e2-114">The **Foreign Key Relationship** dialog box appears.</span></span> <span data-ttu-id="744e2-115">**[選択されたリレーションシップ]** には、作成したリレーションシップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="744e2-115">**Selected Relationship** shows the relationship you have created.</span></span>  
  
8.  <span data-ttu-id="744e2-116">グリッド内のリレーションシップのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="744e2-116">Change properties for the relationship in the grid.</span></span>  
  
9. <span data-ttu-id="744e2-117">**[OK]** をクリックしてリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="744e2-117">Choose **OK** to create the relationship.</span></span>  
  
     <span data-ttu-id="744e2-118">データベース デザイナーでは、選択した列間のリレーションシップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="744e2-118">Database Designer shows a relationship between the columns you chose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744e2-119">参照</span><span class="sxs-lookup"><span data-stu-id="744e2-119">See Also</span></span>  
 <span data-ttu-id="744e2-120">[[テーブルと列] ダイアログボックス &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="744e2-120">[Tables and Columns Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="744e2-121">[Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="744e2-121">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="744e2-122">データベース ダイアグラムでのテーブルの使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="744e2-122">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
