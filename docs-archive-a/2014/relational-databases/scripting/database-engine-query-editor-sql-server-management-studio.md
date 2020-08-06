---
title: データベース エンジン クエリ エディター
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.tsqlquery.f1
dev_langs:
- TSQL
helpviewer_keywords:
- Query Editor [Database Engine]
- Transact-SQL Editor See Query Editor [Database Engine]
- Database Engine Query Editor See Query Editor [Database Engine]
- Query Editor [Database Engine], Toolbar
- editors [SQL Server Management Studio], Database Engine Query Editor
- Query Editor [Database Engine], Features
- SQL Server Management Studio [SQL Server], Database Engine Query Editor
ms.assetid: 05cfae9b-96d5-4a35-a098-0bc3a548bcfc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dcb4298ec55181ea3c979228e8decf681483f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630884"
---
# <a name="database-engine-query-editor-sql-server-management-studio"></a><span data-ttu-id="27830-102">データベース エンジン クエリ エディター (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="27830-102">Database Engine Query Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="27830-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含んだスクリプトの作成と実行を行います。</span><span class="sxs-lookup"><span data-stu-id="27830-103">Use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to create and run scripts containing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="27830-104">**sqlcmd** コマンドを含んだスクリプトの実行もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="27830-104">The editor also supports running scripts that contain **sqlcmd** commands.</span></span>  
  
## <a name="transact-sql-f1-help"></a><span data-ttu-id="27830-105">Transact-SQL F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="27830-105">Transact-SQL F1 Help</span></span>  
 <span data-ttu-id="27830-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターは F1 ヘルプをサポートしており、特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントから、関連するリファレンス トピックに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="27830-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports linking you to the reference topic for a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement when you select F1.</span></span> <span data-ttu-id="27830-107">それには、Transact-SQL ステートメントの名前を強調表示し、F1 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="27830-107">To do so, highlight the name of a Transact-SQL statement and then select F1.</span></span> <span data-ttu-id="27830-108">強調表示した文字列と一致する F1 ヘルプ属性を持ったトピックが、ヘルプの検索エンジンによって検索されます。</span><span class="sxs-lookup"><span data-stu-id="27830-108">The help search engine will then search for a topic that has an F1 help attribute that matches the string you highlighted.</span></span>  
  
 <span data-ttu-id="27830-109">強調表示した文字列と完全に一致する F1 ヘルプ キーワードに該当するトピックが見つからなかった場合は、このトピックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="27830-109">If the help search engine does not find a topic with an F1 help keyword that exactly matches the string you highlighted, then this topic is displayed.</span></span> <span data-ttu-id="27830-110">その場合は、次の 2 つの方法で、目的のヘルプを探すことができます。</span><span class="sxs-lookup"><span data-stu-id="27830-110">In that case, there are two approaches to finding the help you are looking for:</span></span>  
  
-   <span data-ttu-id="27830-111">強調表示した文字列をエディターからコピーし、SQL Server オンライン ブックの検索タブに貼り付けて検索を実行します。</span><span class="sxs-lookup"><span data-stu-id="27830-111">Copy and paste the editor string you highlighted into the search tab of SQL Server Books Online and do a search.</span></span>  
  
-   <span data-ttu-id="27830-112">Transact-SQL ステートメントで、トピックに適用されている F1 ヘルプ キーワードと一致しそうな部分を強調表示してから再度 F1 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="27830-112">Highlight only the part of the Transact-SQL statement likely to match an F1 help keyword applied to a topic and select F1 again.</span></span> <span data-ttu-id="27830-113">トピックに割り当てられている F1 ヘルプ キーワードと強調表示した文字列とが完全に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="27830-113">The search engine requires an exact match between the string you highlighted and an F1 help keyword assigned to a topic.</span></span> <span data-ttu-id="27830-114">強調表示した文字列に、列名やパラメーター名など、特定の環境にしか存在しないような要素が含まれていると、検索エンジンが一致を見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="27830-114">If the string you highlighted contains elements unique to your environment, such as column or parameter names, the search engine will not get a match.</span></span> <span data-ttu-id="27830-115">強調表示する文字列の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="27830-115">Examples of the strings to highlight include:</span></span>  
  
    -   <span data-ttu-id="27830-116">Transact-SQL ステートメントの名前 (SELECT、CREATE DATABASE、BEGIN TRANSACTION など)。</span><span class="sxs-lookup"><span data-stu-id="27830-116">The name of a Transact-SQL statement, such as SELECT, CREATE DATABASE or BEGIN TRANSACTION.</span></span>  
  
    -   <span data-ttu-id="27830-117">組み込み関数の名前 (SERVERPROPERTY、@@VERSION など)。</span><span class="sxs-lookup"><span data-stu-id="27830-117">The name of a built-in function, such as SERVERPROPERTY, or @@VERSION.</span></span>  
  
    -   <span data-ttu-id="27830-118">システム ストアド プロシージャのテーブル名やビュー名 (sys.data_spaces、sp_tableoption など)。</span><span class="sxs-lookup"><span data-stu-id="27830-118">The name of a system stored procedure table, or view, such as sys.data_spaces or sp_tableoption.</span></span>  
  
## <a name="working-with-the-database-engine-query-editor"></a><span data-ttu-id="27830-119">データベース エンジン クエリ エディターを使用した作業</span><span class="sxs-lookup"><span data-stu-id="27830-119">Working With the Database Engine Query Editor</span></span>  
 <span data-ttu-id="27830-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に実装されている 4 つのエディターの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="27830-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is one of four editors implemented in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="27830-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターに実装されている機能の詳細と、このエディターを使用して実行できる主な作業については、「[クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27830-121">For a description of the functionality implemented in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the main tasks you can perform using the editor, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="27830-122">SQL エディター ツール バー</span><span class="sxs-lookup"><span data-stu-id="27830-122">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="27830-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターが開いているときは、次のボタンを持つ SQL エディター ツール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="27830-123">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is open, the SQL Editor toolbar appears with the following buttons.</span></span>  
  
 <span data-ttu-id="27830-124">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="27830-124">**Connect**</span></span>  
 <span data-ttu-id="27830-125">**[サーバーへの接続]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="27830-125">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="27830-126">このダイアログ ボックスを使用すると、サーバーへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="27830-126">Use this dialog box to establish a connection to a server.</span></span>  
  
 <span data-ttu-id="27830-127">**Disconnect (切断)**</span><span class="sxs-lookup"><span data-stu-id="27830-127">**Disconnect**</span></span>  
 <span data-ttu-id="27830-128">現在のクエリ エディターをサーバーから接続解除します。</span><span class="sxs-lookup"><span data-stu-id="27830-128">Disconnects the current Query Editor from the server.</span></span>  
  
 <span data-ttu-id="27830-129">**[接続の変更]**</span><span class="sxs-lookup"><span data-stu-id="27830-129">**Change Connection**</span></span>  
 <span data-ttu-id="27830-130">**[サーバーへの接続]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="27830-130">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="27830-131">このダイアログ ボックスを使用すると、別のサーバーへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="27830-131">Use this dialog box to establish a connection to a different server.</span></span>  
  
 <span data-ttu-id="27830-132">**[新しいクエリを現在の接続で実行]**</span><span class="sxs-lookup"><span data-stu-id="27830-132">**New Query with Current Connection**</span></span>  
 <span data-ttu-id="27830-133">新しいクエリ エディター ウィンドウを開き、現在のクエリ エディター ウィンドウの接続情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="27830-133">Opens a new Query Editor window and uses the connection information from the current Query Editor window.</span></span>  
  
 <span data-ttu-id="27830-134">**[使用できるデータベース]**</span><span class="sxs-lookup"><span data-stu-id="27830-134">**Available Databases**</span></span>  
 <span data-ttu-id="27830-135">接続を同じサーバー上の別のデータベースに変更します。</span><span class="sxs-lookup"><span data-stu-id="27830-135">Change the connection to a different database on the same server.</span></span>  
  
 <span data-ttu-id="27830-136">**おい**</span><span class="sxs-lookup"><span data-stu-id="27830-136">**Execute**</span></span>  
 <span data-ttu-id="27830-137">選択されているコードを実行します。コードが選択されていない場合は、クエリ エディター内のコード全体を実行します。</span><span class="sxs-lookup"><span data-stu-id="27830-137">Executes the selected code or, if no code is selected, executes all the code in the Query Editor.</span></span>  
  
 <span data-ttu-id="27830-138">**デバッグ**</span><span class="sxs-lookup"><span data-stu-id="27830-138">**Debug**</span></span>  
 <span data-ttu-id="27830-139">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="27830-139">Enables the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="27830-140">このデバッガーでは、ブレークポイントの設定、変数の監視、コードのステップ実行などのデバッグ操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="27830-140">This debugger supports debugging actions such as setting breakpoints, watching variables, and stepping through code.</span></span>  
  
 <span data-ttu-id="27830-141">**[クエリ実行のキャンセル]**</span><span class="sxs-lookup"><span data-stu-id="27830-141">**Cancel Executing Query**</span></span>  
 <span data-ttu-id="27830-142">キャンセル要求をサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="27830-142">Sends a cancellation request to the server.</span></span> <span data-ttu-id="27830-143">即座にキャンセルできないクエリもあります。そのようなクエリは、適切なキャンセル条件が整うまでキャンセルできません。</span><span class="sxs-lookup"><span data-stu-id="27830-143">Some queries cannot be canceled immediately, but must wait for a suitable cancellation condition.</span></span> <span data-ttu-id="27830-144">トランザクションが取り消されると、トランザクションがロールバックされる間に遅延が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="27830-144">When transactions are canceled, delays might occur while transactions are rolled back.</span></span>  
  
 <span data-ttu-id="27830-145">**Parse**</span><span class="sxs-lookup"><span data-stu-id="27830-145">**Parse**</span></span>  
 <span data-ttu-id="27830-146">選択されているコードの構文をチェックします。</span><span class="sxs-lookup"><span data-stu-id="27830-146">Check the syntax of the selected code.</span></span> <span data-ttu-id="27830-147">コードが選択されていない場合は、クエリ エディター ウィンドウ内のコード全体の構文をチェックします。</span><span class="sxs-lookup"><span data-stu-id="27830-147">If no code is selected, checks the syntax of the all code in the Query Editor window.</span></span>  
  
 <span data-ttu-id="27830-148">**[推定実行プランの表示]**</span><span class="sxs-lookup"><span data-stu-id="27830-148">**Display Estimated Execution Plan**</span></span>  
 <span data-ttu-id="27830-149">実際にクエリを実行することなくクエリ プロセッサからクエリ実行プランを要求し、プランを **[実行プラン]** ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="27830-149">Requests a query execution plan from the query processor without actually executing the query, and displays the plan in the **Execution plan** window.</span></span> <span data-ttu-id="27830-150">このプランでは、クエリ実行中の各部分で返される行数の推定として、インデックス統計が使用されます。</span><span class="sxs-lookup"><span data-stu-id="27830-150">This plan uses index statistics as an estimate of the number of rows that are expected to be returned during each part of the query execution.</span></span> <span data-ttu-id="27830-151">実際に使用されるクエリ プランは、推定実行プランとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="27830-151">The actual query plan that is used can be different from the estimated execution plan.</span></span> <span data-ttu-id="27830-152">この状況は、返される行数が推定値と大幅に異なり、クエリ プロセッサによってプランが効率化される場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="27830-152">This can occur if the number of rows that are returned is significantly different from the estimate, and the query processor changes the plan to be more efficient.</span></span>  
  
 <span data-ttu-id="27830-153">**[クエリ オプション]**</span><span class="sxs-lookup"><span data-stu-id="27830-153">**Query Options**</span></span>  
 <span data-ttu-id="27830-154">**[クエリ オプション]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="27830-154">Opens the **Query Options** dialog box.</span></span> <span data-ttu-id="27830-155">このダイアログ ボックスを使用すると、クエリの実行およびクエリ結果に関する既定のオプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="27830-155">Use this dialog box to configure the default options for query execution and for query results.</span></span>  
  
 <span data-ttu-id="27830-156">**[IntelliSense が有効]**</span><span class="sxs-lookup"><span data-stu-id="27830-156">**IntelliSense Enabled**</span></span>  
 <span data-ttu-id="27830-157">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターで IntelliSense 機能が使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="27830-157">Specifies whether IntelliSense functionality is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="27830-158">**[実際の実行プランを含める]**</span><span class="sxs-lookup"><span data-stu-id="27830-158">**Include Actual Execution Plan**</span></span>  
 <span data-ttu-id="27830-159">クエリを実行し、クエリ結果と、クエリに対して使用された実行プランを返します。</span><span class="sxs-lookup"><span data-stu-id="27830-159">Executes the query, returns the query results, and the execution plan that was used for the query.</span></span> <span data-ttu-id="27830-160">このクエリ結果と実行プランは、グラフィカルなクエリ プランとして **[実行プラン]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="27830-160">These appear as a graphical query plan in the **Execution plan** window.</span></span>  
  
 <span data-ttu-id="27830-161">**[クライアント統計を含める]**</span><span class="sxs-lookup"><span data-stu-id="27830-161">**Include Client Statistics**</span></span>  
 <span data-ttu-id="27830-162">クエリおよびネットワーク パケットに関する統計、およびクエリの経過時間を表示する **[クライアント統計]** ウィンドウを含めます。</span><span class="sxs-lookup"><span data-stu-id="27830-162">Includes a **Client Statistics** window that contains statistics about the query and about the network packets, and the elapsed time of the query.</span></span>  
  
 <span data-ttu-id="27830-163">**[結果をテキストで表示]**</span><span class="sxs-lookup"><span data-stu-id="27830-163">**Results to Text**</span></span>  
 <span data-ttu-id="27830-164">クエリ結果をテキストとして **[結果]** ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="27830-164">Returns the query results as text in the **Results** window.</span></span>  
  
 <span data-ttu-id="27830-165">**[結果をグリッドに表示]**</span><span class="sxs-lookup"><span data-stu-id="27830-165">**Results to Grid**</span></span>  
 <span data-ttu-id="27830-166">クエリ結果を 1 つまたは複数のグリッドとして **[結果]** ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="27830-166">Returns the query results as one or more grids in the **Results** window.</span></span>  
  
 <span data-ttu-id="27830-167">**[結果をファイルに出力]**</span><span class="sxs-lookup"><span data-stu-id="27830-167">**Results to File**</span></span>  
 <span data-ttu-id="27830-168">クエリを実行したときに、 **[結果の保存]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="27830-168">When the query executes, the **Save Results** dialog box opens.</span></span> <span data-ttu-id="27830-169">ファイルを保存するフォルダーを **[保存先]** で選択します。</span><span class="sxs-lookup"><span data-stu-id="27830-169">In **Save In**, select the folder in which you want to save the file.</span></span> <span data-ttu-id="27830-170">**[ファイル名]** にファイルの名前を入力し、 **[保存]** をクリックして、拡張子 .rpt を持つ **レポート** ファイルとしてクエリ結果を保存します。</span><span class="sxs-lookup"><span data-stu-id="27830-170">In **File name**, type the name of the file, and then click **Save** to save the query results as a **Report** file that has the .rpt extension.</span></span> <span data-ttu-id="27830-171">詳細設定オプションを指定するには、 **[保存]** ボタンの下向き矢印をクリックし、 **[エンコード付きで保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27830-171">For advanced options, click the down-arrow on the **Save** button, and then click **Save with Encoding**.</span></span>  
  
 <span data-ttu-id="27830-172">**選択範囲のコメント**</span><span class="sxs-lookup"><span data-stu-id="27830-172">**Comment Selection**</span></span>  
 <span data-ttu-id="27830-173">行の先頭にコメント演算子 (--) を追加することで、現在の行をコメントにします。</span><span class="sxs-lookup"><span data-stu-id="27830-173">Makes the current line a comment by adding a comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="27830-174">**選択範囲のコメントを解除**</span><span class="sxs-lookup"><span data-stu-id="27830-174">**Uncomment Selection**</span></span>  
 <span data-ttu-id="27830-175">行の先頭にあるコメント演算子 (--) をすべて削除することで、現在の行をアクティブなソース ステートメントにします。</span><span class="sxs-lookup"><span data-stu-id="27830-175">Makes the current line an active source statement by removing any comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="27830-176">**行インデント解除**</span><span class="sxs-lookup"><span data-stu-id="27830-176">**Decrease Line Indent**</span></span>  
 <span data-ttu-id="27830-177">行の先頭にある空白を削除することで、行のテキストを左方向へ移動します。</span><span class="sxs-lookup"><span data-stu-id="27830-177">Moves the text of the line to the left by removing blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="27830-178">**行インデント**</span><span class="sxs-lookup"><span data-stu-id="27830-178">**Increase Line Indent**</span></span>  
 <span data-ttu-id="27830-179">行の先頭に空白を追加することで、行のテキストを右方向へ移動します。</span><span class="sxs-lookup"><span data-stu-id="27830-179">Moves the text of the line to the right by adding blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="27830-180">**[テンプレート パラメーターの値の指定]**</span><span class="sxs-lookup"><span data-stu-id="27830-180">**Specify Values for Template Parameters**</span></span>  
 <span data-ttu-id="27830-181">ストアド プロシージャや関数のパラメーター値を指定するためのダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="27830-181">Opens a dialog box that you can use to specify values for parameters in stored procedures and functions.</span></span>  
  
 <span data-ttu-id="27830-182">また、 **[表示]** メニューの **[ツール バー]** を選択し、 **[SQL エディター]** を選択して、SQL エディター ツール バーを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="27830-182">You can also add the SQL Editor toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **SQL Editor**.</span></span> <span data-ttu-id="27830-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターのウィンドウが開いていない状態で SQL エディター ツール バーを追加した場合、ボタンは使用できません。</span><span class="sxs-lookup"><span data-stu-id="27830-183">If you add the SQL Editor toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="27830-184">SQL エディター ツール バー</span><span class="sxs-lookup"><span data-stu-id="27830-184">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="27830-185">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウが開いているときに、 **[表示]** メニューから **[ツール バー]**、 **[デバッグ]** の順に選択すると、[デバッグ] ツール バーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="27830-185">When a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window is open, you can add the Debug toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **Debug**.</span></span> <span data-ttu-id="27830-186">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウが開いていない状態で [デバッグ] ツール バーを追加した場合、ボタンは使用できません。</span><span class="sxs-lookup"><span data-stu-id="27830-186">If you add the Debug toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
 <span data-ttu-id="27830-187">**Continue**</span><span class="sxs-lookup"><span data-stu-id="27830-187">**Continue**</span></span>  
 <span data-ttu-id="27830-188">ブレークポイントに達するまで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウ内のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="27830-188">Runs the code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window until a breakpoint is encountered.</span></span>  
  
 <span data-ttu-id="27830-189">**[すべて中断]**</span><span class="sxs-lookup"><span data-stu-id="27830-189">**Break All**</span></span>  
 <span data-ttu-id="27830-190">中断が生じたときに、デバッガーがアタッチされているすべてのプロセスを中断するようにデバッガーを設定します。</span><span class="sxs-lookup"><span data-stu-id="27830-190">Sets the debugger to break all processes to which the debugger is attached when a break occurs.</span></span>  
  
 <span data-ttu-id="27830-191">**デバッグの停止**</span><span class="sxs-lookup"><span data-stu-id="27830-191">**Stop Debugging**</span></span>  
 <span data-ttu-id="27830-192">選択された [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウのデバッグ モードを解除して、標準の実行モードに戻します。</span><span class="sxs-lookup"><span data-stu-id="27830-192">Takes the selected [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window out of debug mode, and restores the standard execution mode.</span></span>  
  
 <span data-ttu-id="27830-193">**次のステートメントの表示**</span><span class="sxs-lookup"><span data-stu-id="27830-193">**Show Next Statement**</span></span>  
 <span data-ttu-id="27830-194">次に実行されるステートメントにカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="27830-194">Moves the cursor to the next statement to be executed.</span></span>  
  
 <span data-ttu-id="27830-195">**[ステップ イン]**</span><span class="sxs-lookup"><span data-stu-id="27830-195">**Step Into**</span></span>  
 <span data-ttu-id="27830-196">次のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="27830-196">The next statement is run.</span></span> <span data-ttu-id="27830-197">ステートメントで Transact-SQL ストアド プロシージャ、関数、またはトリガーが呼び出される場合、モジュールのコードが含まれた新しい **クエリ エディター** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="27830-197">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the debugger displays a new **Query Editor** window that contains the code of the module.</span></span> <span data-ttu-id="27830-198">ウィンドウはデバッグ モードに設定され、実行はモジュールの最初のステートメントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="27830-198">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="27830-199">その後、モジュールに対して、ブレークポイントの設定やコードのステップ実行などの操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="27830-199">You can then move through the module, for example, by setting breakpoints or stepping through the code.</span></span>  
  
 <span data-ttu-id="27830-200">**[ステップ オーバー]**</span><span class="sxs-lookup"><span data-stu-id="27830-200">**Step Over**</span></span>  
 <span data-ttu-id="27830-201">次のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="27830-201">The next statement is run.</span></span> <span data-ttu-id="27830-202">ステートメントで Transact-SQL ストアド プロシージャ、関数、またはトリガーが呼び出される場合、モジュールは完了するまで実行され、その結果が呼び出し元のコードに返されます。</span><span class="sxs-lookup"><span data-stu-id="27830-202">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the module is run until it finishes and the results are returned to the calling code.</span></span> <span data-ttu-id="27830-203">モジュールにエラーがないことがわかっている場合は、それをステップ オーバーできます。</span><span class="sxs-lookup"><span data-stu-id="27830-203">If you are sure there are no errors in the module, you can step over it.</span></span> <span data-ttu-id="27830-204">実行は、モジュールへの呼び出しに続くステートメントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="27830-204">Execution pauses on the statement that follows the call to the module.</span></span>  
  
 <span data-ttu-id="27830-205">**[ステップ アウト]**</span><span class="sxs-lookup"><span data-stu-id="27830-205">**Step Out**</span></span>  
 <span data-ttu-id="27830-206">この次に高い呼び出しレベル (関数、ストアド プロシージャ、またはトリガー) に戻ります。</span><span class="sxs-lookup"><span data-stu-id="27830-206">Step back to the next highest calling level (function, stored procedure, or trigger).</span></span> <span data-ttu-id="27830-207">実行は、ストアド プロシージャ、関数、またはトリガーの呼び出しに続くステートメントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="27830-207">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
 <span data-ttu-id="27830-208">**Windows**</span><span class="sxs-lookup"><span data-stu-id="27830-208">**Windows**</span></span>  
 <span data-ttu-id="27830-209">**[ブレークポイント]** ウィンドウまたは **[イミディエイト]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="27830-209">Opens either the **Breakpoint** window or the **Immediate** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27830-210">参照</span><span class="sxs-lookup"><span data-stu-id="27830-210">See Also</span></span>  
 [<span data-ttu-id="27830-211">SQL Server Management Studio のキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="27830-211">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
