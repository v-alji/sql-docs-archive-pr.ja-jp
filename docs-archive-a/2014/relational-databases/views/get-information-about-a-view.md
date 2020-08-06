---
title: ビューに関する情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.viewproperties.general.f1
helpviewer_keywords:
- views [SQL Server], status information
- metadata [SQL Server], views
- dependencies [SQL Server], views
- displaying view information
- views [SQL Server], metadata
- viewing view information
- status information [SQL Server], views
- view dependencies
ms.assetid: 05a73e33-8f85-4fb6-80c1-1b659e753403
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4277aad4c1de0140606575c7ba437408518b3c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631721"
---
# <a name="get-information-about-a-view"></a><span data-ttu-id="281f2-102">ビューに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="281f2-102">Get Information About a View</span></span>
  <span data-ttu-id="281f2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のビューの定義またはプロパティに関する情報は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="281f2-103">You can gain information about a view's definition or properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="281f2-104">ビューのデータが元のテーブルからどのように抽出されているのかを理解したり、ビューで定義されているデータを確認するために、ビューの定義を調べたい場合があります。</span><span class="sxs-lookup"><span data-stu-id="281f2-104">You may need to see the definition of the view to understand how its data is derived from the source tables or to see the data defined by the view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="281f2-105">ビューから参照しているオブジェクトの名前を変更する場合は、ビューのテキストに新しいオブジェクト名が反映されるようにビューを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="281f2-105">If you change the name of an object referenced by a view, you must modify the view so that its text reflects the new name.</span></span> <span data-ttu-id="281f2-106">オブジェクト名を変更する前には、まずオブジェクトの依存関係を表示して、その変更により影響を受けるビューがないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="281f2-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any views are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="281f2-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="281f2-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="281f2-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="281f2-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="281f2-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="281f2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="281f2-110">**以下を使用してビューに関する情報を取得するには:**</span><span class="sxs-lookup"><span data-stu-id="281f2-110">**To get information about a view, using:**</span></span>  
  
     [<span data-ttu-id="281f2-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="281f2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="281f2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="281f2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="281f2-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="281f2-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="281f2-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="281f2-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="281f2-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="281f2-115">Permissions</span></span>  
 <span data-ttu-id="281f2-116">`sp_helptext` を使用してビューの定義を返すには、 **public** ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="281f2-116">Using `sp_helptext` to return the definition of a view requires membership in the **public** role.</span></span> <span data-ttu-id="281f2-117">`sys.sql_expression_dependencies` を使用してビューのすべての依存関係を見つけるには、データベースに対する VIEW DEFINITION 権限とデータベースの `sys.sql_expression_dependencies` に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="281f2-117">Using `sys.sql_expression_dependencies` to find all the dependencies on a view requires VIEW DEFINITION permission on the database and SELECT permission on `sys.sql_expression_dependencies` for the database.</span></span> <span data-ttu-id="281f2-118">SELECT OBJECT_DEFINITION で返されるようなシステム オブジェクトの定義は公開されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-118">System object definitions, like the ones returned in SELECT OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="281f2-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="281f2-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="get-view-properties-by-using-object-explorer"></a><span data-ttu-id="281f2-120">オブジェクト エクスプローラーを使用してビューのプロパティを取得する</span><span class="sxs-lookup"><span data-stu-id="281f2-120">Get view properties by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="281f2-121">**オブジェクト エクスプローラー**で、プロパティを表示するビューを含むデータベースの横にあるプラス記号をクリックします。次に、プラス記号をクリックして **[ビュー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="281f2-121">In **Object Explorer**, click the plus sign next to the database that contains the view to which you want to view the properties, and then click the plus sign to expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="281f2-122">プロパティを表示するビューを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="281f2-122">Right-click the view of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="281f2-123">**[ビューのプロパティ]** ダイアログ ボックスに次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-123">The following properties show in the **View Properties** dialog box.</span></span>  
  
     <span data-ttu-id="281f2-124">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="281f2-124">**Database**</span></span>  
     <span data-ttu-id="281f2-125">このビューを含むデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-125">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="281f2-126">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="281f2-126">**Server**</span></span>  
     <span data-ttu-id="281f2-127">現在のサーバー インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-127">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="281f2-128">**User**</span><span class="sxs-lookup"><span data-stu-id="281f2-128">**User**</span></span>  
     <span data-ttu-id="281f2-129">この接続のユーザーの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-129">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="281f2-130">**[作成日]**</span><span class="sxs-lookup"><span data-stu-id="281f2-130">**Created date**</span></span>  
     <span data-ttu-id="281f2-131">ビューが作成された日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="281f2-131">Displays the date the view was created.</span></span>  
  
     <span data-ttu-id="281f2-132">**Name**</span><span class="sxs-lookup"><span data-stu-id="281f2-132">**Name**</span></span>  
     <span data-ttu-id="281f2-133">現在のビューの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-133">The name of the current view.</span></span>  
  
     <span data-ttu-id="281f2-134">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="281f2-134">**Schema**</span></span>  
     <span data-ttu-id="281f2-135">ビューを所有するスキーマを表示します。</span><span class="sxs-lookup"><span data-stu-id="281f2-135">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="281f2-136">**[システム オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="281f2-136">**System object**</span></span>  
     <span data-ttu-id="281f2-137">ビューがシステム オブジェクトかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-137">Indicates whether the view is a system object.</span></span> <span data-ttu-id="281f2-138">値は True と False です。</span><span class="sxs-lookup"><span data-stu-id="281f2-138">Values are True and False.</span></span>  
  
     <span data-ttu-id="281f2-139">**[ANSI NULL]**</span><span class="sxs-lookup"><span data-stu-id="281f2-139">**ANSI NULLs**</span></span>  
     <span data-ttu-id="281f2-140">オブジェクトが ANSI NULL オプションで作成されたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-140">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="281f2-141">**Encrypted**</span><span class="sxs-lookup"><span data-stu-id="281f2-141">**Encrypted**</span></span>  
     <span data-ttu-id="281f2-142">ビューが暗号化されているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-142">Indicates whether the view is encrypted.</span></span> <span data-ttu-id="281f2-143">値は True と False です。</span><span class="sxs-lookup"><span data-stu-id="281f2-143">Values are True and False.</span></span>  
  
     <span data-ttu-id="281f2-144">**[引用符で囲まれた識別子]**</span><span class="sxs-lookup"><span data-stu-id="281f2-144">**Quoted identifier**</span></span>  
     <span data-ttu-id="281f2-145">オブジェクトが引用符で囲まれた識別子オプションで作成されたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-145">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="281f2-146">**[スキーマ バインド]**</span><span class="sxs-lookup"><span data-stu-id="281f2-146">**Schema bound**</span></span>  
     <span data-ttu-id="281f2-147">ビューがスキーマ バインドされているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-147">Indicates whether the view is schema-bound.</span></span> <span data-ttu-id="281f2-148">値は True と False です。</span><span class="sxs-lookup"><span data-stu-id="281f2-148">Values are True and False.</span></span> <span data-ttu-id="281f2-149">スキーマ バインド ビューの詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)」の SCHEMABINDING のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="281f2-149">For information about schema-bound views, see the SCHEMABINDING portion of [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
#### <a name="getting-view-properties-by-using-the-view-designer-tool"></a><span data-ttu-id="281f2-150">ビュー デザイナー ツールを使用したビューのプロパティの取得</span><span class="sxs-lookup"><span data-stu-id="281f2-150">Getting view properties by using the View Designer tool</span></span>  
  
1.  <span data-ttu-id="281f2-151">**オブジェクト エクスプローラー**で、プロパティを表示するビューを含むデータベースを展開します。次に、 **[ビュー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="281f2-151">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="281f2-152">プロパティを表示するビューを右クリックし、 **[デザイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="281f2-152">Right-click the view of which you want to view the properties and select **Design**.</span></span>  
  
3.  <span data-ttu-id="281f2-153">ダイアグラム ペインの空白領域を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281f2-153">Right-click in the blank space of the Diagram pane and click **Properties**.</span></span>  
  
     <span data-ttu-id="281f2-154">**[プロパティ]** ウィンドウに次のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-154">The following properties show in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="281f2-155">**[(名前)]**</span><span class="sxs-lookup"><span data-stu-id="281f2-155">**(Name)**</span></span>  
     <span data-ttu-id="281f2-156">現在のビューの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-156">The name of the current view.</span></span>  
  
     <span data-ttu-id="281f2-157">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="281f2-157">**Database Name**</span></span>  
     <span data-ttu-id="281f2-158">このビューを含むデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-158">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="281f2-159">**説明**</span><span class="sxs-lookup"><span data-stu-id="281f2-159">**Description**</span></span>  
     <span data-ttu-id="281f2-160">現在のビューの簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="281f2-160">A brief description of the current view.</span></span>  
  
     <span data-ttu-id="281f2-161">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="281f2-161">**Schema**</span></span>  
     <span data-ttu-id="281f2-162">ビューを所有するスキーマを表示します。</span><span class="sxs-lookup"><span data-stu-id="281f2-162">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="281f2-163">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="281f2-163">**Server Name**</span></span>  
     <span data-ttu-id="281f2-164">現在のサーバー インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="281f2-164">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="281f2-165">**[スキーマにバインド]**</span><span class="sxs-lookup"><span data-stu-id="281f2-165">**Bind to Schema**</span></span>  
     <span data-ttu-id="281f2-166">このビューに関連する既定のオブジェクトをユーザーが変更した結果ビュー定義が無効化されるのを防止します。</span><span class="sxs-lookup"><span data-stu-id="281f2-166">Prevents users from modifying the underlying objects that contribute to this view in any way that would invalidate the view definition.</span></span>  
  
     <span data-ttu-id="281f2-167">**決定的**</span><span class="sxs-lookup"><span data-stu-id="281f2-167">**Deterministic**</span></span>  
     <span data-ttu-id="281f2-168">選択した列のデータ型を明確に決定できるかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-168">Shows whether the data type of the selected column can be determined with certainty</span></span>  
  
     <span data-ttu-id="281f2-169">**[DISTINCT 値]**</span><span class="sxs-lookup"><span data-stu-id="281f2-169">**Distinct Values**</span></span>  
     <span data-ttu-id="281f2-170">クエリでビューの重複する値を除外することを指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-170">Specifies that the query will filter out duplicates in the view.</span></span> <span data-ttu-id="281f2-171">このオプションは、テーブルの一部の列だけを使用するときに、使用する列に重複した値が含まれる可能性のある場合、または 2 つ以上のテーブルを結合するプロセスによって結果セットに重複した行が生成される場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="281f2-171">This option is useful when you are using only some of the columns from a table and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="281f2-172">このオプションを選択することは、SQL ペインでステートメントに DISTINCT という単語を挿入することと同じです。</span><span class="sxs-lookup"><span data-stu-id="281f2-172">Choosing this option is equivalent to inserting the keyword DISTINCT into the statement in the SQL pane.</span></span>  
  
     <span data-ttu-id="281f2-173">**[GROUP BY 拡張子]**</span><span class="sxs-lookup"><span data-stu-id="281f2-173">**GROUP BY Extension**</span></span>  
     <span data-ttu-id="281f2-174">集計クエリに基づくビューの追加オプションが使用できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-174">Specifies that additional options for views based on aggregate queries are available.</span></span>  
  
     <span data-ttu-id="281f2-175">**[すべての列を出力]**</span><span class="sxs-lookup"><span data-stu-id="281f2-175">**Output All Columns**</span></span>  
     <span data-ttu-id="281f2-176">選択したビューによってすべての列が返されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="281f2-176">Shows whether all columns are returned by the selected view.</span></span> <span data-ttu-id="281f2-177">これは、ビューの作成時に設定されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-177">This is set at the time the view is created.</span></span>  
  
     <span data-ttu-id="281f2-178">**[SQL コメント]**</span><span class="sxs-lookup"><span data-stu-id="281f2-178">**SQL Comment**</span></span>  
     <span data-ttu-id="281f2-179">SQL ステートメントの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="281f2-179">Shows a description of the SQL statements.</span></span> <span data-ttu-id="281f2-180">説明全体を表示したり、説明を編集したりするには、説明をクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281f2-180">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="281f2-181">ビューの使用者やビューをいつ使用するかなどの情報をコメントに含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="281f2-181">Your comments might include information such as who uses the view and when they use it.</span></span>  
  
     <span data-ttu-id="281f2-182">**[TOP の指定]**</span><span class="sxs-lookup"><span data-stu-id="281f2-182">**Top Specification**</span></span>  
     <span data-ttu-id="281f2-183">展開すると、 **[TOP]** 、 **[式]** 、 **[パーセント]** 、および **[With Ties]** の各プロパティのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-183">Expands to show properties for the **Top**, **Expression**, **Percent**, and **With Ties** properties.</span></span>  
  
     <span data-ttu-id="281f2-184">**[(Top)]**</span><span class="sxs-lookup"><span data-stu-id="281f2-184">**(Top)**</span></span>  
     <span data-ttu-id="281f2-185">ビューに TOP 句が含まれるように指定します。この場合、最初の n 行または最初の n% の行だけが結果セットに返されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-185">Specifies that the view will include a TOP clause, which returns only the first n rows or first n percentage of rows in the result set.</span></span> <span data-ttu-id="281f2-186">既定では、ビューは最初の 10 行を結果セットに返します。</span><span class="sxs-lookup"><span data-stu-id="281f2-186">The default is that the view returns the first 10 rows in the result set.</span></span> <span data-ttu-id="281f2-187">返される行数を変更するか、異なるパーセントを指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="281f2-187">Use this to change the number of rows to return or to specify a different percentage</span></span>  
  
     <span data-ttu-id="281f2-188">**[式]**</span><span class="sxs-lookup"><span data-stu-id="281f2-188">**Expression**</span></span>  
     <span data-ttu-id="281f2-189">ビューによって返されるパーセント ( **[パーセント]** が **[はい]** に設定されている場合) またはレコード数 ( **[パーセント]** が **[いいえ]** に設定されている場合) を示します。</span><span class="sxs-lookup"><span data-stu-id="281f2-189">Shows what percent (if **Percent** is set to **Yes**) or records (if **Percent** is set to **No**) that the view will return.</span></span>  
  
     <span data-ttu-id="281f2-190">**[パーセント]**</span><span class="sxs-lookup"><span data-stu-id="281f2-190">**Percent**</span></span>  
     <span data-ttu-id="281f2-191">クエリに **TOP** 句が含まれるように指定します。この場合、最初の n% の行だけが結果セットに返されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-191">Specifies that the query will include a **TOP** clause, returning only the first n percentage of rows in the result set</span></span>  
  
     <span data-ttu-id="281f2-192">**[With Ties]**</span><span class="sxs-lookup"><span data-stu-id="281f2-192">**With Ties**</span></span>  
     <span data-ttu-id="281f2-193">ビューに **WITH TIES** 句が含まれるように指定します。</span><span class="sxs-lookup"><span data-stu-id="281f2-193">Specifies that the view will include a **WITH TIES** clause.</span></span> <span data-ttu-id="281f2-194">**WITH TIES** は、ビューに **ORDER BY** 句とパーセンテージに基づく **TOP** 句が含まれる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="281f2-194">**WITH TIES** is useful if a view includes an **ORDER BY** clause and a **TOP** clause based on percentage.</span></span> <span data-ttu-id="281f2-195">このオプションを設定すると、 **ORDER BY** 句の列で同一の値を持つ行がセットになり、セットの一部の行がパーセンテージによる制限で切り捨てられてしまう場合は、すべての行が含まれるように、ビューで指定されるパーセンテージが増やされます。</span><span class="sxs-lookup"><span data-stu-id="281f2-195">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the **ORDER BY** clause, the view is extended to include all such rows.</span></span>  
  
     <span data-ttu-id="281f2-196">**[更新の指定]**</span><span class="sxs-lookup"><span data-stu-id="281f2-196">**Update Specification**</span></span>  
     <span data-ttu-id="281f2-197">展開すると、 **[表示ルールを使用して更新]** プロパティと **[オプションのチェック]** プロパティのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-197">Expands to show properties for the **Update Using View Rules** and **Check Option** properties.</span></span>  
  
     <span data-ttu-id="281f2-198">**(表示ルールを使用して更新)**</span><span class="sxs-lookup"><span data-stu-id="281f2-198">**(Update Using View Rules)**</span></span>  
     <span data-ttu-id="281f2-199">Microsoft Data Access Components (MDAC) によって、すべての更新およびビューへの挿入は、ビューのベース テーブルを直接参照する SQL ステートメントではなく、ビューを参照する SQL ステートメントに変換されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-199">Indicates that all updates and insertions to the view will be translated by Microsoft Data Access Components (MDAC) into SQL statements that refer to the view, rather than into SQL statements that refer directly to the view's base tables.</span></span>  
  
     <span data-ttu-id="281f2-200">MDAC マニフェストは、更新およびビューの挿入操作を、ビューの基になるベース テーブルに対する更新および挿入操作として見なす場合があります。</span><span class="sxs-lookup"><span data-stu-id="281f2-200">In some cases, MDAC manifests view update and view insert operations as updates and inserts against the view's underlying base tables.</span></span> <span data-ttu-id="281f2-201">**[表示ルールを使用して更新]** を選択することにより、MDAC がビュー自体に対する更新および挿入操作を生成することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-201">By selecting **Update Using View Rules**, you can ensure that MDAC generates update and insert operations against the view itself.</span></span>  
  
     <span data-ttu-id="281f2-202">**[オプションのチェック]**</span><span class="sxs-lookup"><span data-stu-id="281f2-202">**Check Option**</span></span>  
     <span data-ttu-id="281f2-203">このビューを開き、 **[結果]** ウィンドウを変更すると、データ ソースによって、追加または変更されたデータがビュー定義の **WHERE** 句を満たすかどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="281f2-203">Indicates that when you open this view and modify the **Results** pane, the data source checks whether the added or modified data satisfies the **WHERE** clause of the view definition.</span></span> <span data-ttu-id="281f2-204">変更内容が **WHERE** 句を満たさない場合、エラーが詳細情報と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="281f2-204">If your modification do not satisfy the **WHERE** clause, you will see an error with more information.</span></span>  
  
#### <a name="to-get-dependencies-on-the-view"></a><span data-ttu-id="281f2-205">ビューの依存関係を取得するには</span><span class="sxs-lookup"><span data-stu-id="281f2-205">To get dependencies on the view</span></span>  
  
1.  <span data-ttu-id="281f2-206">**オブジェクト エクスプローラー**で、プロパティを表示するビューを含むデータベースを展開します。次に、 **[ビュー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="281f2-206">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="281f2-207">プロパティを表示するビューを右クリックし、 **[依存関係の表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="281f2-207">Right-click the view of which you want to view the properties and select **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="281f2-208">ビューを参照するオブジェクトを表示するには、 **[[ビュー名] に依存するオブジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="281f2-208">Select **Objects that depend on [view name]** to display the objects that refer to the view.</span></span>  
  
4.  <span data-ttu-id="281f2-209">ビューによって参照されるオブジェクトを表示するには、 **[[ビュー名] が依存するオブジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="281f2-209">Select **Objects on which [view name] depends** to display the objects that are referenced by the view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="281f2-210">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="281f2-210">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-view"></a><span data-ttu-id="281f2-211">ビューの定義およびプロパティを取得するには</span><span class="sxs-lookup"><span data-stu-id="281f2-211">To get the definition and properties of a view</span></span>  
  
1.  <span data-ttu-id="281f2-212">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="281f2-212">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="281f2-213">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281f2-213">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="281f2-214">次のいずれかの例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281f2-214">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition, uses_ansi_nulls, uses_quoted_identifier, is_schema_bound  
    FROM sys.sql_modules  
    WHERE object_id = OBJECT_ID('HumanResources.vEmployee');   
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID('HumanResources.vEmployee')) AS ObjectDefinition;   
    GO  
    ```  
  
    ```  
    EXEC sp_helptext 'HumanResources.vEmployee';  
    ```  
  
 <span data-ttu-id="281f2-215">詳細については、「[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)」、「[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)」、および「[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="281f2-215">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql), [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) and [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-view"></a><span data-ttu-id="281f2-216">ビューの依存関係を取得するには</span><span class="sxs-lookup"><span data-stu-id="281f2-216">To get the dependencies of a view</span></span>  
  
1.  <span data-ttu-id="281f2-217">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="281f2-217">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="281f2-218">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281f2-218">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="281f2-219">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="281f2-219">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');  
    GO  
    ```  
  
 <span data-ttu-id="281f2-220">詳細については、「[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)」および「[sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="281f2-220">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
