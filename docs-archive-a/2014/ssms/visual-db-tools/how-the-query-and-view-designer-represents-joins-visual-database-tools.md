---
title: クエリおよびビューデザイナーでの結合の表示方法 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55fdea533436f9fa7c2a902667b3166085c27e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641941"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a><span data-ttu-id="981d2-102">クエリおよびビュー デザイナーでの結合の表示方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="981d2-102">How the Query and View Designer Represents Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="981d2-103">テーブルを結合すると、 [クエリおよびビュー デザイナー](visual-database-tools.md) は、 [ダイアグラム ペイン](diagram-pane-visual-database-tools.md) にその結合をグラフィカル表示します。また、SQL 構文を使用して [SQL ペイン](sql-pane-visual-database-tools.md)にも表示します。</span><span class="sxs-lookup"><span data-stu-id="981d2-103">If tables are joined, the [Query and View Designer](visual-database-tools.md) represents the join graphically in the [Diagram pane](diagram-pane-visual-database-tools.md) and by using SQL syntax in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="diagram-pane"></a><span data-ttu-id="981d2-104">ダイアグラム ペイン</span><span class="sxs-lookup"><span data-stu-id="981d2-104">Diagram Pane</span></span>  
 <span data-ttu-id="981d2-105">ダイアグラム ペインでは、結合に関係するデータ列の間に結合線が引かれます。</span><span class="sxs-lookup"><span data-stu-id="981d2-105">In the Diagram pane the Query and View Designer displays a join line between the data columns involved in the join.</span></span> <span data-ttu-id="981d2-106">結合条件ごとに 1 本の結合線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="981d2-106">The Query and View Designer displays one join line for each join condition.</span></span> <span data-ttu-id="981d2-107">たとえば、次の図には結合された 2 つのテーブル間の結合線が示されています。</span><span class="sxs-lookup"><span data-stu-id="981d2-107">For example, the following illustration shows a join line between two tables that are joined:</span></span>  
  
 <span data-ttu-id="981d2-108">![2 つのテーブル間のリレーションシップを示す結合線](../../database-engine/media//dv3wbig.gif "2 つのテーブル間のリレーションシップを示す結合線")</span><span class="sxs-lookup"><span data-stu-id="981d2-108">![Join line shows relationship between two tables](../../database-engine/media//dv3wbig.gif "Join line shows relationship between two tables")</span></span>  
  
 <span data-ttu-id="981d2-109">複数の結合条件を使用してテーブルが結合されている場合は、次の図に示すように、複数の結合線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="981d2-109">If tables are joined using more than one join condition, the Query and View Designer displays multiple join lines, as in the following example:</span></span>  
  
 <span data-ttu-id="981d2-110">![複数の結合条件で結合されたテーブル](../../database-engine/media//dv3w9n1.gif "複数の結合条件を使用して結合されたテーブル")</span><span class="sxs-lookup"><span data-stu-id="981d2-110">![Tables joined using more than one join condition](../../database-engine/media//dv3w9n1.gif "Tables joined using more than one join condition")</span></span>  
  
 <span data-ttu-id="981d2-111">結合されたデータ列が表示されていない場合 (テーブルまたはテーブル構造オブジェクトを表す四角形が最小化されている場合や、結合に式が含まれる場合など)、クエリおよびビュー デザイナーは、テーブルまたはテーブル構造オブジェクトを表す四角形のタイトル バーに結合線を表示します。</span><span class="sxs-lookup"><span data-stu-id="981d2-111">If the joined data columns are not displayed (for example, the rectangle representing the table or table-structured object is minimized or the join involves an expression), the Query and View Designer places the join line at the title bar of the rectangle representing the table or table-structured object.</span></span>  
  
 <span data-ttu-id="981d2-112">結合線の中央に表示されるアイコンの形は、テーブルまたはテーブル構造オブジェクトの結合方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="981d2-112">The shape of the icon in the middle of the join line indicates how the tables or table-structured objects are joined.</span></span> <span data-ttu-id="981d2-113">等号 (=) 以外の演算子が結合句で使用されている場合は、その演算子が結合線のアイコンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="981d2-113">If the join clause uses an operator other than equal (=), the operator appears in the join line icon.</span></span> <span data-ttu-id="981d2-114">結合線に表示されるアイコンは、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="981d2-114">The following table lists the icons that appear in the join line.</span></span>  
  
|<span data-ttu-id="981d2-115">**結合線のアイコン**</span><span class="sxs-lookup"><span data-stu-id="981d2-115">**Join line icon**</span></span>|<span data-ttu-id="981d2-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="981d2-116">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="981d2-117">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbih.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-117">![Visual Database Tools icon](../../database-engine/media//dv3wbih.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-118">内部結合 (等号を使用して作成)。</span><span class="sxs-lookup"><span data-stu-id="981d2-118">Inner join (created using an equal sign).</span></span>|  
|<span data-ttu-id="981d2-119">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbii.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-119">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-120">"大なり" 演算子 (>) による内部結合</span><span class="sxs-lookup"><span data-stu-id="981d2-120">Inner join based on the "greater than" operator.</span></span>|  
|<span data-ttu-id="981d2-121">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbij.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-121">![Visual Database Tools icon](../../database-engine/media//dv3wbij.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-122">外部結合。右側のテーブルに一致する行があるかどうかにかかわらず、左側のテーブルのすべての行が含められます。</span><span class="sxs-lookup"><span data-stu-id="981d2-122">Outer join in which all rows from the table represented on the left will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="981d2-123">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbik.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-123">![Visual Database Tools icon](../../database-engine/media//dv3wbik.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-124">外部結合。左側のテーブルに一致する行があるかどうかにかかわらず、右側のテーブルのすべての行が含められます。</span><span class="sxs-lookup"><span data-stu-id="981d2-124">Outer join in which all rows from the table represented on the right will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="981d2-125">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbil.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-125">![Visual Database Tools icon](../../database-engine/media//dv3wbil.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-126">完全外部結合。関連テーブルに一致する行があるかどうかにかかわらず、両方のテーブルのすべての行が含められます。</span><span class="sxs-lookup"><span data-stu-id="981d2-126">Full outer join in which all rows from both tables will be included, even if they do not have matches in the related table.</span></span>|  
  
 <span data-ttu-id="981d2-127">結合線の端に表示される記号は、結合の種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="981d2-127">The symbols on the ends of the join line indicate the type of join.</span></span> <span data-ttu-id="981d2-128">結合の種類と結合線の端に表示されるアイコンは、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="981d2-128">The following table lists the types of joins and the icons displayed on the ends of the join line.</span></span>  
  
|<span data-ttu-id="981d2-129">**結合線の端のアイコン**</span><span class="sxs-lookup"><span data-stu-id="981d2-129">**Icon on ends of join line**</span></span>|<span data-ttu-id="981d2-130">**結合の種類**</span><span class="sxs-lookup"><span data-stu-id="981d2-130">**Type of join**</span></span>|  
|-----------------------------------|----------------------|  
|<span data-ttu-id="981d2-131">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbim.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-131">![Visual Database Tools icon](../../database-engine/media//dv3wbim.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-132">一対一結合。</span><span class="sxs-lookup"><span data-stu-id="981d2-132">One-to-one join.</span></span>|  
|<span data-ttu-id="981d2-133">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbin.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-133">![Visual Database Tools icon](../../database-engine/media//dv3wbin.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-134">一対多結合。</span><span class="sxs-lookup"><span data-stu-id="981d2-134">One-to-many join.</span></span>|  
|<span data-ttu-id="981d2-135">![Visual Database Tools のアイコン](../../database-engine/media//dv3wbio.gif "Visual Database Tools のアイコン")</span><span class="sxs-lookup"><span data-stu-id="981d2-135">![Visual Database Tools icon](../../database-engine/media//dv3wbio.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="981d2-136">クエリおよびビュー デザイナーが特定できない種類の結合です。</span><span class="sxs-lookup"><span data-stu-id="981d2-136">Query and View Designer cannot determine the join type.</span></span> <span data-ttu-id="981d2-137">この状態は、結合を手動で作成した場合に多く発生します。</span><span class="sxs-lookup"><span data-stu-id="981d2-137">This situation occurs most often when you have created a join manually.</span></span>|  
  
## <a name="sql-pane"></a><span data-ttu-id="981d2-138">SQL ペイン</span><span class="sxs-lookup"><span data-stu-id="981d2-138">SQL Pane</span></span>  
 <span data-ttu-id="981d2-139">SQL ステートメントでは、さまざまな方法で結合を表現できます。</span><span class="sxs-lookup"><span data-stu-id="981d2-139">A join can be expressed in a number of ways in an SQL statement.</span></span> <span data-ttu-id="981d2-140">正確な構文は、使用するデータベースおよび結合を定義する方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="981d2-140">The exact syntax depends on the database you are using and on how you have defined the join.</span></span>  
  
 <span data-ttu-id="981d2-141">テーブルの結合に使用する構文オプションは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="981d2-141">Syntax options for joining tables include:</span></span>  
  
-   <span data-ttu-id="981d2-142">**FROM 句の JOIN 修飾子**。</span><span class="sxs-lookup"><span data-stu-id="981d2-142">**JOIN qualifier for the FROM clause**.</span></span>   <span data-ttu-id="981d2-143">キーワード INNER および OUTER で結合の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="981d2-143">The keywords INNER and OUTER specify the join type.</span></span> <span data-ttu-id="981d2-144">この構文は、ANSI 92 SQL の標準です。</span><span class="sxs-lookup"><span data-stu-id="981d2-144">This syntax is standard for ANSI 92 SQL.</span></span>  
  
     <span data-ttu-id="981d2-145">たとえば、 `publishers` テーブルと `pub_info` テーブルを両方のテーブルの `pub_id` 列に基づいて結合する場合、SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="981d2-145">For example, if you join the `publishers` and `pub_info` tables based on the `pub_id` column in each table, the resulting SQL statement might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     <span data-ttu-id="981d2-146">外部結合を作成する場合は、INNER の代わりに LEFT OUTER または RIGHT OUTER というキーワードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="981d2-146">If you create an outer join, the words LEFT OUTER or RIGHT OUTER appear in place of the word INNER.</span></span>  
  
-   <span data-ttu-id="981d2-147">**WHERE 句による両テーブルの列の比較**。</span><span class="sxs-lookup"><span data-stu-id="981d2-147">**WHERE clause compares columns in both tables**.</span></span>   <span data-ttu-id="981d2-148">データベースが JOIN 構文をサポートしていない場合、またはユーザーが自分で入力した場合には、WHERE 句が使用されます。</span><span class="sxs-lookup"><span data-stu-id="981d2-148">A WHERE clause appears if the database does not support the JOIN syntax (or if you entered it yourself).</span></span> <span data-ttu-id="981d2-149">WHERE 句で結合が作成される場合は、FROM 句で両方のテーブルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="981d2-149">If the join is created in the WHERE clause, both table names appear in the FROM clause.</span></span>  
  
     <span data-ttu-id="981d2-150">たとえば、 `publishers` テーブルと `pub_info` テーブルを結合するステートメントは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="981d2-150">For example, the following statement joins the `publishers` and `pub_info` tables.</span></span>  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="981d2-151">参照</span><span class="sxs-lookup"><span data-stu-id="981d2-151">See Also</span></span>  
 <span data-ttu-id="981d2-152">[Visual Database Tools &#40;Join を使用したクエリ&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="981d2-152">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 <span data-ttu-id="981d2-153">[[結合] ダイアログ ボックス (Visual Database Tools)](join-dialog-box-visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="981d2-153">[Join Dialog Box &#40;Visual Database Tools&#41;](join-dialog-box-visual-database-tools.md)</span></span>  
  
  
