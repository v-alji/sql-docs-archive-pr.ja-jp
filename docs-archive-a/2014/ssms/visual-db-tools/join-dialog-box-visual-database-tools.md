---
title: '[結合] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7fbd2b61a080a681b5d15a4b69c466fae76e04e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711445"
---
# <a name="join-dialog-box-visual-database-tools"></a><span data-ttu-id="19cb5-102">[結合] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="19cb5-102">Join Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="19cb5-103">このダイアログ ボックスを使用すると、テーブルを結合するオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-103">Use this dialog box to specify options for joining tables.</span></span> <span data-ttu-id="19cb5-104">このダイアログにアクセスするには、 **[デザイン]** ペインで結合線を選択します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-104">To access this dialog, in the **Design** pane select a join line.</span></span> <span data-ttu-id="19cb5-105">次に、 **[プロパティ]** ウィンドウの **[結合条件と種類]** をクリックして、プロパティの右側に表示される省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19cb5-105">Then in the **Properties** window click **Join Condition And Type**, and click the ellipses **(...)** that appear to the right of the property.</span></span>  
  
 <span data-ttu-id="19cb5-106">既定では、関連するテーブルは内部結合によって結合されます。この場合、結合列に一致した情報を含んでいる行に基づいて、結果セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-106">By default, related tables are joined using an inner join that creates a result set based on rows containing matching information in the join columns.</span></span> <span data-ttu-id="19cb5-107">**[結合]** ダイアログ ボックスのオプションを設定することにより、別の演算子に基づいて結合を指定したり、外部結合を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-107">By setting options in the **Join** dialog box, you can specify a join based on a different operator, and you can specify an outer join.</span></span>  
  
 <span data-ttu-id="19cb5-108">テーブルの結合の詳細については、「 [結合を使用したクエリ (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19cb5-108">For more information about joining tables, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="19cb5-109">オプション</span><span class="sxs-lookup"><span data-stu-id="19cb5-109">Options</span></span>  
  
|<span data-ttu-id="19cb5-110">**用語**</span><span class="sxs-lookup"><span data-stu-id="19cb5-110">**Term**</span></span>|<span data-ttu-id="19cb5-111">**[定義]**</span><span class="sxs-lookup"><span data-stu-id="19cb5-111">**Definition**</span></span>|  
|--------------|--------------------|  
|<span data-ttu-id="19cb5-112">**Table**</span><span class="sxs-lookup"><span data-stu-id="19cb5-112">**Table**</span></span>|<span data-ttu-id="19cb5-113">結合するテーブルまたはテーブル値オブジェクトの名前です。</span><span class="sxs-lookup"><span data-stu-id="19cb5-113">The names of the tables or table-valued objects involved in the join.</span></span> <span data-ttu-id="19cb5-114">ここではテーブルの名前は変更できません。この情報は参照用としてのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-114">You cannot change the names of the tables here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="19cb5-115">**列**</span><span class="sxs-lookup"><span data-stu-id="19cb5-115">**Column**</span></span>|<span data-ttu-id="19cb5-116">テーブルの結合に使用する列の名前です。</span><span class="sxs-lookup"><span data-stu-id="19cb5-116">The names of the columns used for joining the tables.</span></span> <span data-ttu-id="19cb5-117">演算子一覧の演算子によって、列のデータ間の関係を指定します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-117">The operator in the operator list specifies the relationship between the data in the columns.</span></span> <span data-ttu-id="19cb5-118">ここでは列の名前は変更できません。この情報は参照用としてのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-118">You cannot change the names of the columns here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="19cb5-119">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="19cb5-119">**Operator**</span></span>|<span data-ttu-id="19cb5-120">結合列を関連付けるために使用する演算子を指定します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-120">Specify the operator used to relate the join columns.</span></span> <span data-ttu-id="19cb5-121">等号 (=) 以外の演算子を指定する場合は、一覧で選択します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-121">To specify an operator other than equal (=), select it from the list.</span></span> <span data-ttu-id="19cb5-122">プロパティ ページを閉じると、選択した演算子が結合線の菱形記号の中に次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-122">When you close the property page, the operator you selected will appear in the diamond graphic of the join line, as in the following:</span></span><br /><br /> <span data-ttu-id="19cb5-123">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbii.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="19cb5-123">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|  
|<span data-ttu-id="19cb5-124">**次のすべての行: \<table1>**</span><span class="sxs-lookup"><span data-stu-id="19cb5-124">**All rows from \<table1>**</span></span>|<span data-ttu-id="19cb5-125">右側のテーブルに対応する一致がない場合でも、左側のテーブルのすべての行を出力に含めるように指定します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-125">Specify that all the rows from the left table appear in the output, even if there are no corresponding matches in the right table.</span></span> <span data-ttu-id="19cb5-126">右側のテーブルに一致するデータのない列は、NULL として出力されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-126">Columns with no matching data in the right table appear as null.</span></span> <span data-ttu-id="19cb5-127">このオプションを選択することは、SQL ステートメントで LEFT OUTER JOIN を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="19cb5-127">Choosing this option is equivalent to specifying LEFT OUTER JOIN in the SQL statement.</span></span>|  
|<span data-ttu-id="19cb5-128">**次のすべての行: \<table2>**</span><span class="sxs-lookup"><span data-stu-id="19cb5-128">**All rows from \<table2>**</span></span>|<span data-ttu-id="19cb5-129">左側のテーブルに対応する一致がない場合でも、右側のテーブルのすべての行を出力に含めるように指定します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-129">Specify that all the rows from the right table appear in the output, even if there are no corresponding matches in the left table.</span></span> <span data-ttu-id="19cb5-130">左側のテーブルに一致するデータのない列は、NULL として出力されます。</span><span class="sxs-lookup"><span data-stu-id="19cb5-130">Columns with no matching data in the left table appear as null.</span></span> <span data-ttu-id="19cb5-131">このオプションを選択することは、SQL ステートメントで RIGHT OUTER JOIN を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="19cb5-131">Choosing this option is equivalent to specifying RIGHT OUTER JOIN in the SQL statement.</span></span>|  
  
 <span data-ttu-id="19cb5-132">**[\<table1> のすべての行]** と **[\<table2> のすべての行]** の両方を選択することは、SQL ステートメントで FULL OUTER JOIN を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="19cb5-132">Selecting both All **rows from \<table1>** and **All rows from \<table2>** is equivalent to specifying FULL OUTER JOIN in the SQL statement.</span></span>  
  
 <span data-ttu-id="19cb5-133">外部結合を作成するためにオプションを選択すると、結合線中の菱形記号が変化して、結合が LEFT OUTER、RIGHT OUTER、FULL OUTER のいずれであるかを示します。</span><span class="sxs-lookup"><span data-stu-id="19cb5-133">When you select an option to create an outer join, the diamond graphic in the join line changes to indicate that the join is a left outer, right outer, or full outer join.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19cb5-134">この "LEFT" や "RIGHT" という単語は、必ずしも [ダイアグラム] ペイン内のテーブルの位置に対応しません。</span><span class="sxs-lookup"><span data-stu-id="19cb5-134">The words "left" and "right" do not necessarily correspond to the position of tables in the Diagram pane.</span></span> <span data-ttu-id="19cb5-135">"LEFT" とは、SQL ステートメントでキーワード JOIN の左側に名前が記述されるテーブルを示し、"RIGHT" とは、SQL ステートメントでキーワード JOIN の右側に名前が記述されるテーブルを示しています。</span><span class="sxs-lookup"><span data-stu-id="19cb5-135">"Left" refers to the table whose name appears to the left of the keyword JOIN in the SQL statement, and "right" refers to the table whose name appears to the right of the JOIN keyword.</span></span> <span data-ttu-id="19cb5-136">**[ダイアグラム]** ペイン内でテーブルを移動しても、この意味でのテーブルの左右が入れ替わることはありません。</span><span class="sxs-lookup"><span data-stu-id="19cb5-136">If you move tables in the **Diagram** pane, you do not change which table is considered left or right.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cb5-137">参照</span><span class="sxs-lookup"><span data-stu-id="19cb5-137">See Also</span></span>  
 <span data-ttu-id="19cb5-138">[Visual Database Tools &#40;Join を使用したクエリ&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="19cb5-138">[Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="19cb5-139">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="19cb5-139">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
