---
title: クエリ エディターによる SQLCMD スクリプトの編集
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], SQLCMD scripts
- SQLCMD scripts
- modifying scripts
- Query Editor [Database Engine], SQLCMD scripts
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: f77b866d-c330-47c9-9e74-0b8d8dff4b31
author: rothja
ms.author: jroth
ms.openlocfilehash: a3466cfc15ea2f4f0c8de5da42f4a1c24c28a575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641587"
---
# <a name="edit-sqlcmd-scripts-with-query-editor"></a><span data-ttu-id="2bdcb-102">クエリ エディターによる SQLCMD スクリプトの編集</span><span class="sxs-lookup"><span data-stu-id="2bdcb-102">Edit SQLCMD Scripts with Query Editor</span></span>
  <span data-ttu-id="2bdcb-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用すると、クエリを SQLCMD スクリプトとして作成したり、編集したりできます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-103">By using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] you can write and edit queries as SQLCMD scripts.</span></span> <span data-ttu-id="2bdcb-104">Windows システムのコマンドと [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを同じスクリプトで処理する必要がある場合は、SQLCMD スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-104">You use SQLCMD scripts when you have to process Windows System commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the same script.</span></span>  
  
## <a name="sqlcmd-mode"></a><span data-ttu-id="2bdcb-105">SQLCMD モード</span><span class="sxs-lookup"><span data-stu-id="2bdcb-105">SQLCMD Mode</span></span>  
 <span data-ttu-id="2bdcb-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターで SQLCMD スクリプトの作成や編集を行うには、SQLCMD スクリプト モードを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-106">To use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to write or edit SQLCMD scripts, you must enable the SQLCMD scripting mode.</span></span> <span data-ttu-id="2bdcb-107">クエリ エディターの SQLCMD モードは、既定では有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-107">By default, SQLCMD mode is not enabled in the Query Editor.</span></span> <span data-ttu-id="2bdcb-108">スクリプト モードを有効にするには、ツール バーの **[SQLCMD モード]** アイコンをクリックするか、 **[クエリ]** メニューの **[SQLCMD モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-108">You can enable scripting mode by clicking the **SQLCMD Mode** icon in the toolbar or by selecting **SQLCMD Mode** from the **Query** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2bdcb-109">SQLCMD モードを有効にすると、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のクエリ エディターの IntelliSense および [!INCLUDE[ssDE](../../includes/ssde-md.md)] デバッガーが無効になります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-109">Enabling SQLCMD mode turns off IntelliSense and the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="2bdcb-110">クエリ エディターで SQLCMD スクリプトを操作するときには、あらゆる [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトと同じ機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-110">SQLCMD scripts in the Query Editor can use the same features that all [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts use.</span></span> <span data-ttu-id="2bdcb-111">使用できる機能には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-111">These features include the following:</span></span>  
  
-   <span data-ttu-id="2bdcb-112">コードの色分け</span><span class="sxs-lookup"><span data-stu-id="2bdcb-112">Color Coding</span></span>  
  
-   <span data-ttu-id="2bdcb-113">スクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="2bdcb-113">Executing Scripts</span></span>  
  
-   <span data-ttu-id="2bdcb-114">ソース管理</span><span class="sxs-lookup"><span data-stu-id="2bdcb-114">Source Control</span></span>  
  
-   <span data-ttu-id="2bdcb-115">スクリプトの解析</span><span class="sxs-lookup"><span data-stu-id="2bdcb-115">Parsing Scripts</span></span>  
  
-   <span data-ttu-id="2bdcb-116">Showplan</span><span class="sxs-lookup"><span data-stu-id="2bdcb-116">Showplan</span></span>  
  
## <a name="enable-sqlcmd-scripting-in-query-editor"></a><span data-ttu-id="2bdcb-117">クエリ エディターで SQLCMD スクリプト操作を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="2bdcb-117">Enable SQLCMD Scripting in Query Editor</span></span>  
 <span data-ttu-id="2bdcb-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のアクティブなクエリ エディター ウィンドウで SQLCMD スクリプト操作を有効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-118">To turn SQLCMD scripting on for an active [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, use the following procedure.</span></span>  
  
#### <a name="to-switch-a-database-engine-query-editor-window-to-sqlcmd-mode"></a><span data-ttu-id="2bdcb-119">データベース エンジンのクエリ エディター ウィンドウを SQLCMD モードに切り替えるには</span><span class="sxs-lookup"><span data-stu-id="2bdcb-119">To switch a Database Engine Query Editor window to SQLCMD mode</span></span>  
  
1.  <span data-ttu-id="2bdcb-120">オブジェクト エクスプローラーで、サーバーを右クリックして **[新しいクエリ]** をクリックし、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディター ウィンドウを新しく開きます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-120">In Object Explorer, right-click the server, and then click **New Query**, to open a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
2.  <span data-ttu-id="2bdcb-121">**[クエリ]** メニューの **[SQLCMD モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-121">On the **Query** menu, click **SQLCMD Mode**.</span></span>  
  
     <span data-ttu-id="2bdcb-122">クエリ エディター ウィンドウのコンテキストで **sqlcmd** ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-122">The Query Editor executes **sqlcmd** statements in the context of the Query Editor.</span></span>  
  
3.  <span data-ttu-id="2bdcb-123">**[SQL エディター]** ツール バーの **[使用できるデータベース]** の一覧で、[ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-123">On the **SQL Editor** toolbar, in the **Available Databases** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
4.  <span data-ttu-id="2bdcb-124">クエリ エディター ウィンドウに、次の 2 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと `!!DIR`**sqlcmd** ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-124">In the Query Editor window, type the following two [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the `!!DIR` **sqlcmd** statement:</span></span>  
  
    ```  
    SELECT DISTINCT Type FROM Sales.SpecialOffer;  
    GO  
    !!DIR  
    GO  
    SELECT ProductCategoryID, Name FROM Production.ProductCategory;  
    GO  
    ```  
  
5.  <span data-ttu-id="2bdcb-125">F5&lt;/localizedText&gt; キーを押して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと MS-DOS ステートメントが混在するセクション全体を実行します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-125">Press F5 to execute the whole section of mixed [!INCLUDE[tsql](../../includes/tsql-md.md)] and MS-DOS statements.</span></span>  
  
     <span data-ttu-id="2bdcb-126">1 番目と 3 番目のステートメントにより、2 つの SQL 結果ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-126">Notice the two SQL result panes from the first and third statements.</span></span>  
  
6.  <span data-ttu-id="2bdcb-127">**結果** ペインの **[メッセージ]** タブをクリックし、3 つのステートメントすべてから取得されたメッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-127">In the **Results** pane, click the **Messages** tab to see the messages from all three statements:</span></span>  
  
    -   <span data-ttu-id="2bdcb-128">(6 件処理されました)</span><span class="sxs-lookup"><span data-stu-id="2bdcb-128">(6 row(s) affected)</span></span>  
  
    -   \<The directory information>  
  
    -   <span data-ttu-id="2bdcb-129">(4 行処理されました)</span><span class="sxs-lookup"><span data-stu-id="2bdcb-129">(4 row(s) affected)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2bdcb-130">コマンド ラインから実行すると、 **sqlcmd** ユーティリティではオペレーティング システムとの完全な対話が可能になります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-130">When executed from the command line, the **sqlcmd** utility permits full interaction with the operating system.</span></span> <span data-ttu-id="2bdcb-131">クエリ エディターを **SQLCMD モード**で使用する場合は、対話型のステートメントを実行しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-131">When you use the Query Editor in **SQLCMD Mode**, you must be careful not to execute interactive statements.</span></span> <span data-ttu-id="2bdcb-132">クエリ エディターは、オペレーティング システムのプロンプトに応答できません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-132">The Query Editor cannot respond to operating system prompts.</span></span>  
  
 <span data-ttu-id="2bdcb-133">SQLCMD の実行方法の詳細については、「 [sqlcmd Utility](../../tools/sqlcmd-utility.md)」または SQLCMD のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-133">For more information about how to run SQLCMD, see [sqlcmd Utility](../../tools/sqlcmd-utility.md), or take the SQLCMD tutorial.</span></span>  
  
## <a name="enable-sqlcmd-scripting-by-default"></a><span data-ttu-id="2bdcb-134">SQLCMD スクリプト操作を既定で有効にする方法</span><span class="sxs-lookup"><span data-stu-id="2bdcb-134">Enable SQLCMD Scripting by Default</span></span>  
 <span data-ttu-id="2bdcb-135">SQLCMD スクリプト操作を既定でオンにするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[クエリ実行]**、 **[SQL Server]** の順に展開します。次に、 **[全般]** ページをクリックし、 **[既定で、新しいクエリを SQLCMD モードで開始する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-135">To turn SQLCMD scripting on by default, on the **Tools** menu select **Options**, expand **Query Execution**, and **SQL Server**, click the **General** page, and then check the **By default open new queries in SQLCMD Mode** box.</span></span>  
  
## <a name="writing-and-editing-sqlcmd-scripts"></a><span data-ttu-id="2bdcb-136">SQLCMD スクリプトの作成と編集</span><span class="sxs-lookup"><span data-stu-id="2bdcb-136">Writing and Editing SQLCMD Scripts</span></span>  
 <span data-ttu-id="2bdcb-137">スクリプト モードを有効にしたら、SQLCMD コマンドと [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-137">After enabling scripting mode you may write SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="2bdcb-138">次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-138">The following rules apply:</span></span>  
  
-   <span data-ttu-id="2bdcb-139">SQLCMD コマンドは行の最初のステートメントでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-139">SQLCMD commands must be the first statement on a line.</span></span>  
  
-   <span data-ttu-id="2bdcb-140">各行に 1 つの SQLCMD コマンドだけを記述できます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-140">Only one SQLCMD command is permitted on each line.</span></span>  
  
-   <span data-ttu-id="2bdcb-141">SQLCMD コマンドの前にコメントや空白文字を入れてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-141">SQLCMD commands can be preceded by comments or white space.</span></span>  
  
-   <span data-ttu-id="2bdcb-142">コメント文字の間にはさまれた SQLCMD コマンドは実行されません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-142">SQLCMD commands within comment characters are not executed.</span></span>  
  
-   <span data-ttu-id="2bdcb-143">1 行のコメント文字は 2 つのハイフン (`--)` であり、行の先頭に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-143">Single line comment characters are two hyphens (`--)` and must appear at the beginning of a line.</span></span>  
  
-   <span data-ttu-id="2bdcb-144">オペレーティング システム コマンドの前には 2 つの感嘆符 (`!!`) を置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-144">Operating system commands must be preceded by two exclamation points (`!!`).</span></span> <span data-ttu-id="2bdcb-145">2 つの感嘆符が付いたコマンドの場合は、感嘆符の後のステートメントが `cmd.exe` コマンド プロセッサによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-145">The double-exclamation points command causes the statement that follows the exclamation points to be executed using the `cmd.exe` command processor.</span></span> <span data-ttu-id="2bdcb-146">`!!` の後のテキストは、 `cmd.exe`にパラメーターとして渡されるので、最終的に実行されるコマンド ラインは、 `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`になります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-146">The text after `!!` is passed in as a parameter to `cmd.exe`, so the final command line will execute as: `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`.</span></span>  
  
-   <span data-ttu-id="2bdcb-147">SQLCMD コマンドと [!INCLUDE[tsql](../../includes/tsql-md.md)]の区別を明確にするために、すべての SQLCMD コマンドの先頭にはコロン (`:`) を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-147">To make a clear distinction between SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)], all SQLCMD commands, need to be prefixed with a colon (`:`).</span></span>  
  
-   <span data-ttu-id="2bdcb-148">`GO` コマンドは、先頭に文字を付けずに使用することも、 を付けて使用することもできます。 `!!:`</span><span class="sxs-lookup"><span data-stu-id="2bdcb-148">The `GO` command may be used without preface, or preceded by `!!:`</span></span>  
  
-   <span data-ttu-id="2bdcb-149">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターは、環境変数をサポートしており、また SQLCMD スクリプトの一部として定義されている変数もサポートしています。ただし、組み込みの SQLCMD 変数や **osql** 変数はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-149">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports environment variables and variables that are defined as part of a SQLCMD script, but does not support built-in SQLCMD or **osql** variables.</span></span> <span data-ttu-id="2bdcb-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で処理される SQLCMD では、変数の大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-150">SQLCMD processing by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is case sensitive for variables.</span></span> <span data-ttu-id="2bdcb-151">たとえば、PRINT '$(COMPUTERNAME)' では正しい結果になりますが、PRINT '$(ComputerName)' ではエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-151">For example, PRINT '$(COMPUTERNAME)' produces the correct result, but PRINT '$(ComputerName)' returns an error.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="2bdcb-152">は、標準モードと SQLCMD モードの実行に [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient を使用します。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-152">uses [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode.</span></span> <span data-ttu-id="2bdcb-153">コマンド ラインから SQLCMD を実行する場合は、OLE DB プロバイダーを使用することになります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-153">When run from the command line, SQLCMD uses the OLE DB provider.</span></span> <span data-ttu-id="2bdcb-154">同じクエリでも、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の SQLCMD モードで実行する場合と SQLCMD ユーティリティで実行する場合とでは、適用される既定のオプションが異なるので、動作も異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-154">Because different default options may apply, it is possible to get different behavior while executing the same query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD Mode, and in the SQLCMD utility.</span></span>  
  
## <a name="supported-sqlcmd-syntax"></a><span data-ttu-id="2bdcb-155">サポートされている SQLCMD 構文</span><span class="sxs-lookup"><span data-stu-id="2bdcb-155">Supported SQLCMD Syntax</span></span>  
 <span data-ttu-id="2bdcb-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターでは、以下の SQLCMD スクリプト キーワードをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-156">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following SQLCMD script keywords:</span></span>  
  
 `[!!:]GO[count]`  
  
 `!! <command>`  
  
 `:exit(statement)`  
  
 `:Quit`  
  
 `:r <filename>`  
  
 `:setvar <var> <value>`  
  
 `:connect server[\instance] [-l login_timeout] [-U user [-P password]]`  
  
 `:on error [ignore|exit]`  
  
 `:error <filename>|stderr|stdout`  
  
 `:out <filename>|stderr|stdout`  
  
> [!NOTE]  
>  <span data-ttu-id="2bdcb-157">`:error` と `:out`の場合、 `stderr` と `stdout` のどちらを指定しても、出力は [メッセージ] タブに送信されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-157">For both `:error` and `:out`, `stderr` and `stdout` send output to the messages tab.</span></span>  
  
 <span data-ttu-id="2bdcb-158">クエリ エディターでは、上記以外の SQLCMD コマンドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-158">SQLCMD commands not listed above are not supported in Query Editor.</span></span> <span data-ttu-id="2bdcb-159">サポートされていない SQLCMD キーワードを含むスクリプトが実行されると、クエリエディターは、サポートされていない各キーワードの送信先に "コマンド \* を無視します" というメッセージを送信し \<ignored command*> ます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-159">When a script containing SQLCMD keywords that are not supported is executed, the Query Editor will send an "Ignoring command \*\<ignored command*>" message to the destination for each unsupported keyword.</span></span> <span data-ttu-id="2bdcb-160">スクリプトは正常に実行されますが、サポートされていないコマンドは無視されます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-160">The script will execute successfully, but the unsupported commands will be ignored.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2bdcb-161">コマンド ラインから SQLCMD を実行する場合とは異なり、クエリ エディターの SQLCMD モードにはいくつかの制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-161">Because you are not starting SQLCMD from the command line, there are some limitations when running Query Editor in SQLCMD Mode.</span></span> <span data-ttu-id="2bdcb-162">まず、変数などのコマンド ライン パラメーターを受け渡すことができません。また、クエリ エディターはオペレーティング システムのプロンプトに応答できないため、対話型のステートメントを実行しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-162">You cannot pass in command-line parameters such as variables, and, because the Query Editor does not have the ability to respond to operating system prompts, you must be careful not to execute interactive statements.</span></span>  
  
## <a name="color-coding-in-sqlcmd-scripts"></a><span data-ttu-id="2bdcb-163">SQLCMD スクリプトのコードの色分け</span><span class="sxs-lookup"><span data-stu-id="2bdcb-163">Color Coding in SQLCMD Scripts</span></span>  
 <span data-ttu-id="2bdcb-164">SQLCMD スクリプト操作が有効になっていると、スクリプトのコードが色分けされます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-164">With SQLCMD scripting enabled, scripts will be color coded.</span></span> <span data-ttu-id="2bdcb-165">[!INCLUDE[tsql](../../includes/tsql-md.md)] キーワードの色分けは変わりません。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-165">The color coding for [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords will remain the same.</span></span> <span data-ttu-id="2bdcb-166">SQLCMD コマンドは、背景が影付きになります。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-166">SQLCMD commands are presented with a shaded background.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bdcb-167">例</span><span class="sxs-lookup"><span data-stu-id="2bdcb-167">Example</span></span>  
 <span data-ttu-id="2bdcb-168">次の例では、現在のディレクトリを出力するために、 **sqlcmd** ステートメントを使用して testoutput.txt という出力ファイルを作成し、1 つのオペレーティング システム コマンドで 2 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] の SELECT ステートメントを実行しています。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-168">The following example uses a **sqlcmd** statement to create an output file called testoutput.txt, executes two [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statements along with one operating system command (to print out the current directory).</span></span> <span data-ttu-id="2bdcb-169">結果ファイルには、 `DIR` ステートメントからのメッセージ出力に続いて、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントからの結果の出力が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2bdcb-169">The resultant file contains the message output from the `DIR` statement, followed by the results output from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
:out C:\testoutput.txt  
SELECT @@VERSION As 'Server Version'  
!!DIR  
!!:GO  
SELECT @@SERVERNAME AS 'Server Name'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bdcb-170">参照</span><span class="sxs-lookup"><span data-stu-id="2bdcb-170">See Also</span></span>  
 [<span data-ttu-id="2bdcb-171">sqlcmd Utility</span><span class="sxs-lookup"><span data-stu-id="2bdcb-171">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
