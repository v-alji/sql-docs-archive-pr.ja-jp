---
title: クエリのプロパティ (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69636
- vdt.ppg.querydesigner.query
ms.assetid: 07495669-6ed5-4004-904e-aae1230be5e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3c8adfb50e15113228afe8b48218f341f19084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713681"
---
# <a name="query-properties-visual-database-tools"></a><span data-ttu-id="8e360-102">クエリのプロパティ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8e360-102">Query Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="8e360-103">クエリおよびビュー デザイナーでクエリを開くと、これらのプロパティが [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-103">These properties appear in the Properties window when you have a query open in Query and View Designer.</span></span> <span data-ttu-id="8e360-104">特に断りのない限り、このプロパティを [プロパティ] ウィンドウで編集できます。</span><span class="sxs-lookup"><span data-stu-id="8e360-104">Unless otherwise noted, you can edit these properties in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e360-105">このトピックでは、アルファベット順ではなくカテゴリ別にプロパティが示されています。</span><span class="sxs-lookup"><span data-stu-id="8e360-105">The properties in this topic are ordered by category, rather than alphabetically.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e360-106">オプション</span><span class="sxs-lookup"><span data-stu-id="8e360-106">Options</span></span>  
 <span data-ttu-id="8e360-107">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="8e360-107">**Identity Category**</span></span>  
 <span data-ttu-id="8e360-108">展開して **[オブジェクト名]** プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="8e360-108">Expand to show the **Name** property.</span></span>  
  
 <span data-ttu-id="8e360-109">**Name**</span><span class="sxs-lookup"><span data-stu-id="8e360-109">**Name**</span></span>  
 <span data-ttu-id="8e360-110">現在のクエリの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="8e360-110">Shows the name of the current query.</span></span> <span data-ttu-id="8e360-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]では変更できません。</span><span class="sxs-lookup"><span data-stu-id="8e360-111">Cannot be changed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="8e360-112">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="8e360-112">**Database Name**</span></span>  
 <span data-ttu-id="8e360-113">選択したテーブルのデータ ソースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-113">Shows the name of the data source for the selected table.</span></span>  
  
 <span data-ttu-id="8e360-114">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="8e360-114">**Server Name**</span></span>  
 <span data-ttu-id="8e360-115">データ ソースのサーバーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="8e360-115">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="8e360-116">**[クエリ デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="8e360-116">**Query Designer Category**</span></span>  
 <span data-ttu-id="8e360-117">展開すると、その他のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-117">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="8e360-118">**ターゲット テーブル**</span><span class="sxs-lookup"><span data-stu-id="8e360-118">**Destination table**</span></span>  
 <span data-ttu-id="8e360-119">データを挿入するテーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-119">Specify the name of the table into which you are inserting data.</span></span> <span data-ttu-id="8e360-120">この一覧は、INSERT クエリまたは MAKE TABLE クエリを作成する場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-120">This list appears if you are creating an INSERT query or MAKE TABLE query.</span></span> <span data-ttu-id="8e360-121">INSERT クエリの場合は、一覧でテーブル名を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e360-121">For an INSERT query, select a table name from the list.</span></span>  
  
 <span data-ttu-id="8e360-122">MAKE TABLE クエリの場合は、新しいテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8e360-122">For a MAKE TABLE query, type the name of the new table.</span></span> <span data-ttu-id="8e360-123">テーブルを別のデータ ソースに作成する場合は、データ ソースの名前、所有者 (必要な場合)、テーブルの名前を含めた、完全修飾テーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-123">To create a destination table in another data source, specify a fully qualified table name, including the name of the target data source, the owner (if required), and the name of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e360-124">クエリ デザイナーは、名前が既に使用されているか、テーブルを作成する権限があるかなどの確認はしません。</span><span class="sxs-lookup"><span data-stu-id="8e360-124">Query Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
 <span data-ttu-id="8e360-125">**[一意の値]**</span><span class="sxs-lookup"><span data-stu-id="8e360-125">**Distinct values**</span></span>  
 <span data-ttu-id="8e360-126">クエリが結果セットから重複した値を取り除くように指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-126">Specify that the query will filter out duplicates in the result set.</span></span> <span data-ttu-id="8e360-127">このオプションは、テーブルの一部の列だけを使用するときに、使用する列に重複した値が含まれる可能性のある場合、または 2 つ以上のテーブルを結合するプロセスによって結果セットに重複した行が生成される場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8e360-127">This option is useful when you are using only some of the columns from the table or tables and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="8e360-128">このオプションを選択することは、SQL ペインでステートメントに DISTINCT という単語を挿入することと同じです。</span><span class="sxs-lookup"><span data-stu-id="8e360-128">Choosing this option is equivalent to inserting the word DISTINCT into the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="8e360-129">**[GROUP BY 拡張子]**</span><span class="sxs-lookup"><span data-stu-id="8e360-129">**GROUP BY Extension**</span></span>  
 <span data-ttu-id="8e360-130">集計クエリに基づくクエリの追加オプションが使用できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-130">Specify that additional options for queries based on aggregate queries are available.</span></span> <span data-ttu-id="8e360-131">( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="8e360-131">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="8e360-132">**[すべての列を出力]**</span><span class="sxs-lookup"><span data-stu-id="8e360-132">**Output All Columns**</span></span>  
 <span data-ttu-id="8e360-133">現在のクエリのすべてのテーブルからすべての列を結果セットに含めるように指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-133">Specify that all columns from all tables in the current query will be in the result set.</span></span> <span data-ttu-id="8e360-134">このオプションを選択することは、SQL ステートメントの SELECT キーワードの後でそれぞれの列名の代わりにアスタリスク (\*) を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="8e360-134">Choosing this option is equivalent to specifying an asterisk (\*) in place of individual column names after the SELECT keyword in the SQL statement.</span></span>  
  
 <span data-ttu-id="8e360-135">**[パラメーター リストのクエリ]**</span><span class="sxs-lookup"><span data-stu-id="8e360-135">**Query Parameter List**</span></span>  
 <span data-ttu-id="8e360-136">クエリ パラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="8e360-136">Shows query parameters.</span></span> <span data-ttu-id="8e360-137">パラメーターを編集するには、プロパティをクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e360-137">To edit the parameters click the property and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="8e360-138">汎用 OLE DB だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-138">(Applies only to generic OLE DB.)</span></span>  
  
 <span data-ttu-id="8e360-139">**[SQL コメント]**</span><span class="sxs-lookup"><span data-stu-id="8e360-139">**SQL Comment**</span></span>  
 <span data-ttu-id="8e360-140">SQL ステートメントの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="8e360-140">Shows a description of the SQL statements.</span></span> <span data-ttu-id="8e360-141">説明全体を表示したり、説明を編集したりするには、説明をクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e360-141">To see the entire description or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="8e360-142">クエリの使用者やクエリをいつ使用するかなどの情報をコメントに含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="8e360-142">Your comments can include information such as who uses the query and when they use it.</span></span> <span data-ttu-id="8e360-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降のデータベースだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-143">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 databases or later.)</span></span>  
  
 <span data-ttu-id="8e360-144">**[Top の指定] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="8e360-144">**Top Specification Category**</span></span>  
 <span data-ttu-id="8e360-145">展開すると、 **[Top]** 、 **[パーセント]** 、 **[式]** 、および **[With Ties]** の各プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-145">Expand to show properties for the **Top**, **Percent**, **Expression**, and **With Ties** properties.</span></span>  
  
 <span data-ttu-id="8e360-146">**[(Top)]**</span><span class="sxs-lookup"><span data-stu-id="8e360-146">**(Top)**</span></span>  
 <span data-ttu-id="8e360-147">クエリに TOP 句が含まれるように指定します。この場合、最初の *n* 行または最初の *n* % の行だけが結果セットに返されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-147">Specify hat the query will include a TOP clause, which returns only the first *n* rows or first *n* percentage of rows in the result set.</span></span> <span data-ttu-id="8e360-148">既定では、クエリは最初の 10 行を結果セットに返します。</span><span class="sxs-lookup"><span data-stu-id="8e360-148">The default is that the query returns the first 10 rows in the result set.</span></span>  
  
 <span data-ttu-id="8e360-149">このボックスは、返される行数を変更するか、異なるパーセントを指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="8e360-149">Use this box to change the number of rows to return or to specify a different percentage.</span></span> <span data-ttu-id="8e360-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以降だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-150">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or later.)</span></span>  
  
 <span data-ttu-id="8e360-151">**[式]**</span><span class="sxs-lookup"><span data-stu-id="8e360-151">**Expression**</span></span>  
 <span data-ttu-id="8e360-152">クエリが返す行の数または割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-152">Specify the number or percentage of rows that the query will return.</span></span> <span data-ttu-id="8e360-153">**[パーセント]** を [はい] に設定すると、この数値はクエリが返す行の割合を表し、 **[パーセント]** を [いいえ] に設定すると、この数値はクエリが返す行の数を表します。</span><span class="sxs-lookup"><span data-stu-id="8e360-153">If you set **Percent** to Yes, this number is the percentage of rows the query will return; if you set **Percent** to No, it represents the number of rows to return.</span></span> <span data-ttu-id="8e360-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-154">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
 <span data-ttu-id="8e360-155">**[パーセント]**</span><span class="sxs-lookup"><span data-stu-id="8e360-155">**Percent**</span></span>  
 <span data-ttu-id="8e360-156">クエリが最初の *n* % の行だけを結果セットに返すように指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-156">Specify that the query will return only the first *n* percent of rows in the result set.</span></span> <span data-ttu-id="8e360-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-157">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
 <span data-ttu-id="8e360-158">**[With Ties]**</span><span class="sxs-lookup"><span data-stu-id="8e360-158">**With Ties**</span></span>  
 <span data-ttu-id="8e360-159">ビューに WITH TIES 句を含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="8e360-159">Specify that the view will include a WITH TIES clause.</span></span> <span data-ttu-id="8e360-160">WITH TIES は、ビューに ORDER BY 句とパーセンテージに基づく TOP 句が含まれる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8e360-160">WITH TIES is useful if a view includes an ORDER BY clause and a TOP clause based on percentage.</span></span> <span data-ttu-id="8e360-161">このオプションを設定すると、ORDER BY 句の列で同一の値を持つ行がセットになり、セットの一部の行がパーセンテージによる制限で切り捨てられてしまう場合は、すべての行が含まれるように、クエリで指定されるパーセンテージが増やされます。</span><span class="sxs-lookup"><span data-stu-id="8e360-161">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the ORDER BY clause, the view is extended to include all such rows.</span></span> <span data-ttu-id="8e360-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降だけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8e360-162">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e360-163">参照</span><span class="sxs-lookup"><span data-stu-id="8e360-163">See Also</span></span>  
 <span data-ttu-id="8e360-164">[Visual Database Tools &#40;パラメーターを使用したクエリ&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8e360-164">[Query with Parameters &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8e360-165">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8e360-165">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
