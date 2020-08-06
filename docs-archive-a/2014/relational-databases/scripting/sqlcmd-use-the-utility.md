---
title: sqlcmd ユーティリティの使用
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL statements, executing
- command prompt utilities [SQL Server], sqlcmd
- statements [SQL Server], executing
- sqlcmd utility, about sqlcmd utility
ms.assetid: 3ec89119-7314-43ef-9e91-12e72bb63d62
author: rothja
ms.author: jroth
ms.openlocfilehash: 922f9915272fb2d7fc63487ec135ce44ee91e88b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643224"
---
# <a name="use-the-sqlcmd-utility"></a><span data-ttu-id="67d60-102">sqlcmd ユーティリティの使用</span><span class="sxs-lookup"><span data-stu-id="67d60-102">Use the sqlcmd Utility</span></span>
  <span data-ttu-id="67d60-103">`sqlcmd` ユーティリティは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントおよびスクリプトを対話形式でアドホック実行したり、[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト タスクを自動化したりするためのコマンドライン ユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="67d60-103">The `sqlcmd` utility is a command-line utility for ad hoc, interactive execution of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and scripts and for automating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripting tasks.</span></span> <span data-ttu-id="67d60-104">`sqlcmd` を対話形式で使用したり、`sqlcmd` を使用して実行できるスクリプト ファイルを作成したりするには、ユーザーが [!INCLUDE[tsql](../../includes/tsql-md.md)] を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="67d60-104">To use `sqlcmd` interactively, or to build script files to be run using `sqlcmd`, users must understand [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="67d60-105">`sqlcmd` ユーティリティは一般的に次のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-105">The `sqlcmd` utility is typically used in the following ways:</span></span>  
  
-   <span data-ttu-id="67d60-106">コマンド プロンプトでの操作と同様、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを対話形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-106">Users interactively enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a manner similar to working at the command prompt.</span></span> <span data-ttu-id="67d60-107">結果はコマンド プロンプトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-107">The results are displayed at the command prompt.</span></span> <span data-ttu-id="67d60-108">コマンド プロンプト ウィンドウを開くには、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をポイントします。次に **[アクセサリ]** をポイントし、 **[コマンド プロンプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67d60-108">To open a Command Prompt window, click **Start**, click **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span> <span data-ttu-id="67d60-109">コマンド プロンプトで「`sqlcmd`」と入力し、その後に必要なオプションのリストを入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-109">At the command prompt, type `sqlcmd` followed by a list of options that you want.</span></span> <span data-ttu-id="67d60-110">でサポートされているオプションの完全な一覧につい `sqlcmd` ては、「 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67d60-110">For a complete list of the options that are supported by `sqlcmd`, see [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="67d60-111">実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つ指定するか、実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの入ったテキスト ファイルをユーティリティに指定して、`sqlcmd` ジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-111">Users submit a `sqlcmd` job either by specifying a single [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute, or by pointing the utility to a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to execute.</span></span> <span data-ttu-id="67d60-112">出力先はコマンド プロンプトにすることもできますが、通常はテキスト ファイルに出力されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-112">The output is usually directed to a text file, but it can also be displayed at the command prompt.</span></span>  
  
-   <span data-ttu-id="67d60-113">[クエリ エディターの](edit-sqlcmd-scripts-with-query-editor.md) SQLCMD モード [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d60-113">[SQLCMD mode](edit-sqlcmd-scripts-with-query-editor.md) in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="67d60-114">SQL Server 管理オブジェクト (SMO)</span><span class="sxs-lookup"><span data-stu-id="67d60-114">SQL Server Management Objects (SMO)</span></span>  
  
-   <span data-ttu-id="67d60-115">SQL Server エージェントの CmdExec ジョブ</span><span class="sxs-lookup"><span data-stu-id="67d60-115">SQL Server Agent CmdExec jobs.</span></span>  
  
## <a name="typically-used-sqlcmd-options"></a><span data-ttu-id="67d60-116">一般的な sqlcmd オプション</span><span class="sxs-lookup"><span data-stu-id="67d60-116">Typically Used sqlcmd Options</span></span>  
 <span data-ttu-id="67d60-117">最もよく使用されるオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-117">The following options are used most frequently:</span></span>  
  
-   <span data-ttu-id="67d60-118">接続先ののインスタンスを識別するサーバーオプション (**-S**) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="67d60-118">The server option (**-S**) that identifies the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to which `sqlcmd` connects.</span></span>  
  
-   <span data-ttu-id="67d60-119">認証オプション (**-E**、 **-U**、 **-P**) `sqlcmd` 。のインスタンスへの接続に使用する資格情報を指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="67d60-119">Authentication options (**-E**, **-U**, and **-P**) that specify the credentials that `sqlcmd` uses to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d60-120">**-E** オプションは既定値なので、指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="67d60-120">The **-E** option is the default and does not have to be specified.</span></span>  
  
-   <span data-ttu-id="67d60-121">入力の場所を示す入力オプション (**-q**、 **-q**、 **-i**) `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="67d60-121">Input options (**-Q**, **-q**, and **-i**) that identify the location of the input to `sqlcmd`.</span></span>  
  
-   <span data-ttu-id="67d60-122">出力オプション (**-o**)。出力先となるファイルを指定し `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="67d60-122">The output option (**-o**) that specifies the file in which `sqlcmd` is to put its output.</span></span>  
  
## <a name="connecting-to-the-sqlcmd-utility"></a><span data-ttu-id="67d60-123">sqlcmd ユーティリティへの接続</span><span class="sxs-lookup"><span data-stu-id="67d60-123">Connecting to the sqlcmd Utility</span></span>  
 <span data-ttu-id="67d60-124">次に、`sqlcmd` ユーティリティの一般的な使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-124">The following are common uses of the `sqlcmd` utility:</span></span>  
  
-   <span data-ttu-id="67d60-125">Windows 認証を使用して既定のインスタンスに接続し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを対話的に実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-125">Connecting to a default instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d60-126">前の例では、 **-E**は既定値であり、 `sqlcmd` Windows 認証を使用して既定のインスタンスに接続するため、指定されていません。</span><span class="sxs-lookup"><span data-stu-id="67d60-126">In the previous example, **-E** is not specified because it is the default and `sqlcmd` connects to the default instance by using Windows Authentication.</span></span>  
  
-   <span data-ttu-id="67d60-127">Windows 認証を使用して名前付きインスタンスに接続し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを対話的に実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-127">Connecting to a named instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName>  
    ```  
  
     <span data-ttu-id="67d60-128">or</span><span class="sxs-lookup"><span data-stu-id="67d60-128">or</span></span>  
  
    ```  
    sqlcmd -S .\<InstanceName>  
    ```  
  
-   <span data-ttu-id="67d60-129">Windows 認証を使用して名前付きインスタンスに接続し、入出力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="67d60-129">Connecting to a named instance by using Windows Authentication and specifying input and output files:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName> -i <MyScript.sql> -o <MyOutput.rpt>  
    ```  
  
-   <span data-ttu-id="67d60-130">Windows 認証を使用してローカル コンピューター上の既定のインスタンスに接続し、クエリを実行して、クエリの完了後も `sqlcmd` を実行状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="67d60-130">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, and having `sqlcmd` remain running after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -q "SELECT * FROM AdventureWorks2012.Person.Person"  
    ```  
  
-   <span data-ttu-id="67d60-131">Windows 認証を使用してローカル コンピューター上の既定のインスタンスに接続し、クエリを実行して、ファイルへの出力を指定し、クエリの完了後に `sqlcmd` を終了します。</span><span class="sxs-lookup"><span data-stu-id="67d60-131">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, directing the output to a file, and having `sqlcmd` exit after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -Q "SELECT * FROM AdventureWorks2012.Person.Person" -o MyOutput.txt  
    ```  
  
-   <span data-ttu-id="67d60-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して名前付きインスタンスに接続し、`sqlcmd` からパスワードの入力を求めて [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを対話的に実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-132">Connecting to a named instance using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, with `sqlcmd` prompting for a password:</span></span>  
  
    ```  
    sqlcmd -U MyLogin -S <ComputerName>\<InstanceName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d60-133">`sqlcmd` ユーティリティでサポートされているオプションの一覧を表示するには、`sqlcmd -?` を実行してください。</span><span class="sxs-lookup"><span data-stu-id="67d60-133">To see a list of the options that are supported by the `sqlcmd` utility run: `sqlcmd -?`.</span></span>  
  
## <a name="running-transact-sql-statements-interactively-by-using-sqlcmd"></a><span data-ttu-id="67d60-134">sqlcmd を使用した Transact-SQL ステートメントの対話的な実行</span><span class="sxs-lookup"><span data-stu-id="67d60-134">Running Transact-SQL Statements Interactively by Using sqlcmd</span></span>  
 <span data-ttu-id="67d60-135">コマンド プロンプト ウィンドウでは、`sqlcmd` ユーティリティを対話的に使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-135">You can use the `sqlcmd` utility interactively to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a Command Prompt window.</span></span> <span data-ttu-id="67d60-136">を使用してステートメントを対話的に実行するには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] `sqlcmd` **-q**、 **-q**、 **-Z**、または **-i**オプションを使用せずに、入力ファイルまたはクエリを指定するために、ユーティリティを実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-136">To interactively execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using `sqlcmd`, run the utility without using the **-Q**, **-q**, **-Z**, or **-i** options to specify any input files or queries.</span></span> <span data-ttu-id="67d60-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-137">For example:</span></span>  
  
 `sqlcmd -S <ComputerName>\<InstanceName>`  
  
 <span data-ttu-id="67d60-138">入力ファイルやクエリを指定せずにこのコマンドを実行すると、`sqlcmd` は指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続した後、新しい行に `1>` と表示し、その隣でアンダースコアを点滅させます。これを `sqlcmd` プロンプトと呼びます。</span><span class="sxs-lookup"><span data-stu-id="67d60-138">When the command is executed without input files or queries, `sqlcmd` connects to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then displays a new line with a `1>` followed by a blinking underscore that is named the `sqlcmd` prompt.</span></span> <span data-ttu-id="67d60-139">`1` は、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの最初の行であることを示します。この `sqlcmd` プロンプトが [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの入力開始位置になります。</span><span class="sxs-lookup"><span data-stu-id="67d60-139">The `1` signifies that this is the first line of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, and the `sqlcmd` prompt is the point at which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will start when you type it in.</span></span>  
  
 <span data-ttu-id="67d60-140">`sqlcmd` プロンプトでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと、`sqlcmd` や `GO` などの `EXIT` コマンドの両方を入力できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-140">At the `sqlcmd` prompt, you can type both [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands, such as `GO` and `EXIT`.</span></span> <span data-ttu-id="67d60-141">各 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、ステートメント キャッシュと呼ばれるバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-141">Each [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is put in a buffer called the statement cache.</span></span> <span data-ttu-id="67d60-142">`GO` コマンドを入力し、Enter キーを押すと、これらのステートメントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-142">These statements are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] after you type the `GO` command and press ENTER.</span></span> <span data-ttu-id="67d60-143">を終了するに `sqlcmd` `EXIT` は、 `QUIT` 新しい行の先頭に「」または「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-143">To exit `sqlcmd`, type `EXIT` or `QUIT` at the start of a new line.</span></span>  
  
 <span data-ttu-id="67d60-144">ステートメント キャッシュをクリアするには、「`:RESET`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-144">To clear the statement cache, type `:RESET`.</span></span> <span data-ttu-id="67d60-145">「」 `^C` と入力 `sqlcmd` すると、が終了します。</span><span class="sxs-lookup"><span data-stu-id="67d60-145">Typing `^C` causes `sqlcmd` to exit.</span></span> <span data-ttu-id="67d60-146">`^C` は、`GO` コマンドが実行された後に、ステートメント キャッシュの実行を停止するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-146">`^C` can also be used to stop the execution of the statement cache after a `GO` command has been issued.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="67d60-147">対話型セッションで入力されたステートメントは、 **: ED**コマンドとプロンプトを入力することによって編集できます `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="67d60-147">statements that are entered in an interactive session can edited by entering the **:ED** command and the `sqlcmd` prompt.</span></span> <span data-ttu-id="67d60-148">起動したエディターで [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを編集して、エディターを終了すると、変更された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがコマンド ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-148">The editor will open and, after editing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement and closing the editor, the revised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will appear in the command window.</span></span> <span data-ttu-id="67d60-149">を入力して `GO` 、実行するステートメントを実行 [!INCLUDE[tsql](../../includes/tsql-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="67d60-149">Enter `GO` to run therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="quoted-strings"></a><span data-ttu-id="67d60-150">引用符で囲まれた文字列</span><span class="sxs-lookup"><span data-stu-id="67d60-150">Quoted Strings</span></span>  
 <span data-ttu-id="67d60-151">引用符で囲まれた文字列は、前処理がまったく行われずそのまま使用されます。ただし、例外として、2 つの連続する引用符を入力することで、引用符自体を文字列に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-151">Characters that are enclosed in quotation marks are used without any additional preprocessing, except that quotations marks can be inserted into a string by entering two consecutive quotation marks.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="67d60-152">は、この文字の並びを 1 つの引用符として扱います</span><span class="sxs-lookup"><span data-stu-id="67d60-152">treats this character sequence as one quotation mark.</span></span> <span data-ttu-id="67d60-153">(ただし、この変換はサーバーで行われます)。スクリプト変数が文字列内に存在する場合は展開されません。</span><span class="sxs-lookup"><span data-stu-id="67d60-153">(However, the translation occurs in the server.) Scripting variables will not be expanded when they appear within a string.</span></span>  
  
 <span data-ttu-id="67d60-154">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-154">For example:</span></span>  
  
 `sqlcmd`  
  
 `PRINT "Length: 5"" 7'";`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Length: 5" 7'`  
  
## <a name="strings-that-span-multiple-lines"></a><span data-ttu-id="67d60-155">複数行の文字列</span><span class="sxs-lookup"><span data-stu-id="67d60-155">Strings That Span Multiple Lines</span></span>  
 <span data-ttu-id="67d60-156">`sqlcmd` では、複数行の文字列になるスクリプトがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="67d60-156">`sqlcmd` supports scripts that have strings that span multiple lines.</span></span> <span data-ttu-id="67d60-157">たとえば、次の `SELECT` ステートメントは複数行にわたって記述されていますが、「 `GO`」と入力して &lt;localizedText&gt;Enter&lt;/localizedText&gt; キーを押すと、1 つの文字列として実行されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-157">For example, the following `SELECT` statement spans multiple lines but is a single string executed when you press the ENTER key after typing `GO`.</span></span>  
  
 `SELECT First line`  
  
 `FROM Second line`  
  
 `WHERE Third line;`  
  
 `GO`  
  
## <a name="interactive-sqlcmd-example"></a><span data-ttu-id="67d60-158">対話的な sqlcmd の例</span><span class="sxs-lookup"><span data-stu-id="67d60-158">Interactive sqlcmd Example</span></span>  
 <span data-ttu-id="67d60-159">`sqlcmd` を対話的に実行する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-159">This is an example of what you see when you run `sqlcmd` interactively.</span></span>  
  
 <span data-ttu-id="67d60-160">コマンド プロンプト ウィンドウを開くと、次のような行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-160">When you open a Command Prompt window, there is one line similar to:</span></span>  
  
 `C:\> _`  
  
 <span data-ttu-id="67d60-161">これは、フォルダー `C:\` が現在のフォルダーであり、ファイル名を指定すると Windows によってそのフォルダー内のファイルが検索されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="67d60-161">This means the folder `C:\` is the current folder, and if you specify a file name, Windows will look for the file in that folder.</span></span>  
  
 <span data-ttu-id="67d60-162">「`sqlcmd`」と入力して、ローカル コンピューターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。コマンド プロンプト ウィンドウの内容は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="67d60-162">Type `sqlcmd` to connect to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer, and the contents of the Command Prompt window will be:</span></span>  
  
 `C:\>sqlcmd`  
  
 `1> _`  
  
 <span data-ttu-id="67d60-163">これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続が確立され、 `sqlcmd` で [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと `sqlcmd` コマンドを実行できるようになったことを示しています。</span><span class="sxs-lookup"><span data-stu-id="67d60-163">This means you have connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and `sqlcmd` is now ready to accept [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands.</span></span> <span data-ttu-id="67d60-164">`1>` の隣で点滅しているアンダースコアは、入力したステートメントやコマンドが表示される位置を示す `sqlcmd` プロンプトです。</span><span class="sxs-lookup"><span data-stu-id="67d60-164">The flashing underscore after the `1>` is the `sqlcmd` prompt that marks the location at which the statements and commands you type will be displayed.</span></span> <span data-ttu-id="67d60-165">ここで、「」と入力し、enter キーを押して、「」と入力し、enter `USE AdventureWorks2012` `GO` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="67d60-165">Now, type `USE AdventureWorks2012` and press ENTER, and then type `GO` and press ENTER.</span></span> <span data-ttu-id="67d60-166">コマンド プロンプト ウィンドウの内容は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="67d60-166">The contents of the Command Prompt window will be:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `1> _`  
  
 <span data-ttu-id="67d60-167">「 `USE AdventureWorks2012` 」と入力した後で &lt;localizedText&gt;Enter&lt;/localizedText&gt; キーを押すことにより、新しい行を開始するよう `sqlcmd` に要求します。</span><span class="sxs-lookup"><span data-stu-id="67d60-167">Pressing ENTER after entering `USE AdventureWorks2012` signaled `sqlcmd` to start a new line.</span></span> <span data-ttu-id="67d60-168">「 `GO,` 」と入力してから Enter キーを押すことにより、 `sqlcmd` ステートメントを `USE AdventureWorks2012` のインスタンスに送信するよう [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に指示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-168">Pressing ENTER, after you type `GO,` signaled `sqlcmd` to send the `USE AdventureWorks2012` statement to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67d60-169">`sqlcmd` により、 `USE` ステートメントが正常に完了したことを示すメッセージが返されます。その後、 `1>` プロンプトが表示され、新しいステートメントやコマンドを入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="67d60-169">`sqlcmd` then returned a message to indicate that the `USE` statement completed successfully and displayed a new `1>` prompt as a signal to enter a new statement or command.</span></span>  
  
 <span data-ttu-id="67d60-170">次の例では、 `SELECT` ステートメント、 `GO` を実行するための `SELECT`、および `EXIT` を終了するための `sqlcmd`を入力した場合に、コマンド プロンプト ウィンドウに表示される内容を示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-170">The following example shows what the Command Prompt window contains if you type a `SELECT` statement, a `GO` to execute the `SELECT`, and an `EXIT` to exit `sqlcmd`:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `BusinessEntityID   FirstName                 LastName`  
  
 `----------- -------------------------------- -----------`  
  
 `1           Syed                             Abbas`  
  
 `2           Catherine                        Abel`  
  
 `3           Kim                              Abercrombie`  
  
 `(3 rows affected)`  
  
 `1> EXIT`  
  
 `C:\>`  
  
 <span data-ttu-id="67d60-171">行 `3> GO` の後の行は、 `SELECT` ステートメントの出力です。</span><span class="sxs-lookup"><span data-stu-id="67d60-171">The lines after line `3> GO` are the output of a `SELECT` statement.</span></span> <span data-ttu-id="67d60-172">出力の生成後、 `sqlcmd` により `sqlcmd` プロンプトがリセットされ、 `1>`が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-172">After you generate output, `sqlcmd` resets the `sqlcmd` prompt and displays `1>`.</span></span> <span data-ttu-id="67d60-173">行 `EXIT` で「 `1>`」と入力すると、最初にコマンド プロンプト ウィンドウを開いたときと同じ行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-173">After entering `EXIT` at line `1>`, the Command Prompt window displays the same line it did when you first opened it.</span></span> <span data-ttu-id="67d60-174">これは、 `sqlcmd` のセッションを終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="67d60-174">This indicates that `sqlcmd` has exited its session.</span></span> <span data-ttu-id="67d60-175">その状態で再度 `EXIT` コマンドを入力すると、コマンド プロンプト ウィンドウを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="67d60-175">You can now close the Command Prompt window by typing another `EXIT` command.</span></span>  
  
## <a name="running-transact-sql-script-files-by-using-sqlcmd"></a><span data-ttu-id="67d60-176">sqlcmd を使用した Transact-SQL スクリプト ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="67d60-176">Running Transact-SQL Script Files by Using sqlcmd</span></span>  
 <span data-ttu-id="67d60-177">`sqlcmd` を使用してデータベース スクリプト ファイルを実行できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-177">You can use `sqlcmd` to execute database script files.</span></span> <span data-ttu-id="67d60-178">スクリプトファイルは [!INCLUDE[tsql](../../includes/tsql-md.md)] 、ステートメント、 `sqlcmd` コマンド、およびスクリプト変数が混在したテキストファイルです。</span><span class="sxs-lookup"><span data-stu-id="67d60-178">Script files are text files that contain a mix of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span> <span data-ttu-id="67d60-179">変数をスクリプト化する方法の詳細については、「 [sqlcmd でのスクリプト変数の使用](sqlcmd-use-with-scripting-variables.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67d60-179">For more information about how to script variables, see [Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md).</span></span> <span data-ttu-id="67d60-180">スクリプト ファイル内のステートメント、コマンド、およびスクリプト変数に対して `sqlcmd` で行われる処理は、対話的に入力したステートメントやコマンドの処理と似ています。</span><span class="sxs-lookup"><span data-stu-id="67d60-180">`sqlcmd` works with the statements, commands, and scripting variables in a script file in a manner similar to how it works with statements and commands that are entered interactively.</span></span> <span data-ttu-id="67d60-181">`sqlcmd` が対話入力の場合と大きく異なる点は、ユーザーがステートメント、コマンド、およびスクリプト変数を入力するまで待機するのではなく、入力ファイルを最後まで中断することなく読み取るという点です。</span><span class="sxs-lookup"><span data-stu-id="67d60-181">The main difference is that `sqlcmd` reads through the input file without pause instead of waiting for a user to enter the statements, commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="67d60-182">データベース スクリプト ファイルの作成方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="67d60-182">There are different ways to create database script files:</span></span>  
  
-   <span data-ttu-id="67d60-183">[!INCLUDE[tsql](../../includes/tsql-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ステートメントのセットを対話的に作成およびデバッグして、クエリ ウィンドウの内容をスクリプト ファイルとして保存する。</span><span class="sxs-lookup"><span data-stu-id="67d60-183">You can interactively build and debug a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then save the contents of the Query window as a script file.</span></span>  
  
-   <span data-ttu-id="67d60-184">メモ帳などのテキスト エディターを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含んだテキスト ファイルを作成する。</span><span class="sxs-lookup"><span data-stu-id="67d60-184">You can create a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using a text editor, such as Notepad.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="67d60-185">例</span><span class="sxs-lookup"><span data-stu-id="67d60-185">Examples</span></span>  
  
### <a name="a-running-a-script-by-using-sqlcmd"></a><span data-ttu-id="67d60-186">A.</span><span class="sxs-lookup"><span data-stu-id="67d60-186">A.</span></span> <span data-ttu-id="67d60-187">sqlcmd を使用したスクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="67d60-187">Running a script by using sqlcmd</span></span>  
 <span data-ttu-id="67d60-188">メモ帳を起動し、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-188">Start Notepad, and type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="67d60-189">`MyFolder` というフォルダーを作成し、スクリプトを `MyScript.sql` ファイルとして `C:\MyFolder`フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="67d60-189">Create a folder named `MyFolder` and then save the script as the file `MyScript.sql` in the folder `C:\MyFolder`.</span></span> <span data-ttu-id="67d60-190">コマンド プロンプトで、次のコマンドを入力してスクリプトを実行し、結果を `MyOutput.txt` の `MyFolder`に出力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-190">Enter the following at the command prompt to run the script and put the output in `MyOutput.txt` in `MyFolder`:</span></span>  
  
 `sqlcmd -i C:\MyFolder\MyScript.sql -o C:\MyFolder\MyOutput.txt`  
  
 <span data-ttu-id="67d60-191">メモ帳で `MyOutput.txt` を開くと、次のような内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-191">When you view the contents of `MyOutput.txt` in Notepad, you will see the following:</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `BusinessEntityID FirstName   LastName`  
  
 `---------------- ----------- -----------`  
  
 `1                Syed        Abbas`  
  
 `2                Catherine   Abel`  
  
 `3                Kim         Abercrombie`  
  
 `(3 rows affected)`  
  
### <a name="b-using-sqlcmd-with-a-dedicated-administrative-connection"></a><span data-ttu-id="67d60-192">B.</span><span class="sxs-lookup"><span data-stu-id="67d60-192">B.</span></span> <span data-ttu-id="67d60-193">sqlcmd と専用管理者接続の併用</span><span class="sxs-lookup"><span data-stu-id="67d60-193">Using sqlcmd with a dedicated administrative connection</span></span>  
 <span data-ttu-id="67d60-194">次の例では、 `sqlcmd` を使用して、ブロッキングの問題が発生しているサーバーに専用管理者接続 (DAC) で接続します。</span><span class="sxs-lookup"><span data-stu-id="67d60-194">In the following example, `sqlcmd` is used to connect to a server that has a blocking problem by using the dedicated administrator connection (DAC).</span></span>  
  
 `C:\>sqlcmd -S ServerName -A`  
  
 `1> SELECT blocked FROM sys.dm_exec_requests WHERE blocked <> 0;`  
  
 `2> GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `spid   blocked`  
  
 `------ -------`  
  
 `62       64`  
  
 `(1 rows affected)`  
  
 <span data-ttu-id="67d60-195">`sqlcmd` を使用してブロック中のプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="67d60-195">Use `sqlcmd` to end the blocking process.</span></span>  
  
 `1> KILL 64;`  
  
 `2> GO`  
  
### <a name="c-using-sqlcmd-to-execute-a-stored-procedure"></a><span data-ttu-id="67d60-196">C.</span><span class="sxs-lookup"><span data-stu-id="67d60-196">C.</span></span> <span data-ttu-id="67d60-197">sqlcmd を使用したストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="67d60-197">Using sqlcmd to execute a stored procedure</span></span>  
 <span data-ttu-id="67d60-198">次の例では、 `sqlcmd`を使用してストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-198">The following example shows how to execute a stored procedure by using `sqlcmd`.</span></span> <span data-ttu-id="67d60-199">次のストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="67d60-199">Create the following stored procedure.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `IF OBJECT_ID ( ' dbo.ContactEmailAddress, 'P' ) IS NOT NULL`  
  
 `DROP PROCEDURE dbo.ContactEmailAddress;`  
  
 `GO`  
  
 `CREATE PROCEDURE dbo.ContactEmailAddress`  
  
 `(`  
  
 `@FirstName nvarchar(50)`  
  
 `,@LastName nvarchar(50)`  
  
 `)`  
  
 `AS`  
  
 `SET NOCOUNT ON`  
  
 `SELECT EmailAddress`  
  
 `FROM Person.Person`  
  
 `WHERE FirstName = @FirstName`  
  
 `AND LastName = @LastName;`  
  
 `SET NOCOUNT OFF`  
  
 <span data-ttu-id="67d60-200">`sqlcmd` プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-200">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\sqlcmd`  
  
 `1> :Setvar FirstName Gustavo`  
  
 `1> :Setvar LastName Achong`  
  
 `1> EXEC dbo.ContactEmailAddress $(Gustavo),$(Achong)`  
  
 `2> GO`  
  
 `EmailAddress`  
  
 `-----------------------------`  
  
 `gustavo0@adventure-works.com`  
  
### <a name="d-using-sqlcmd-for-database-maintenance"></a><span data-ttu-id="67d60-201">D.</span><span class="sxs-lookup"><span data-stu-id="67d60-201">D.</span></span> <span data-ttu-id="67d60-202">sqlcmd を使用したデータベースのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="67d60-202">Using sqlcmd for database maintenance</span></span>  
 <span data-ttu-id="67d60-203">次の例では、 `sqlcmd` を使用してデータベースのメンテナンス タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-203">The following example shows how to use `sqlcmd` for a database maintenance task.</span></span> <span data-ttu-id="67d60-204">次のコードを使用して `C:\BackupTemplate.sql` を作成します。</span><span class="sxs-lookup"><span data-stu-id="67d60-204">Create `C:\BackupTemplate.sql` with the following code.</span></span>  
  
 `USE master;`  
  
 `BACKUP DATABASE [$(db)] TO DISK='$(bakfile)';`  
  
 <span data-ttu-id="67d60-205">`sqlcmd` プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="67d60-205">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\ >sqlcmd`  
  
 `1> :connect <server>`  
  
 `Sqlcmd: Successfully connected to server <server>.`  
  
 `1> :setvar db msdb`  
  
 `1> :setvar bakfile c:\msdb.bak`  
  
 `1> :r c:\BackupTemplate.sql`  
  
 `2> GO`  
  
 `Changed database context to 'master'.`  
  
 `Processed 688 pages for database 'msdb', file 'MSDBData' on file 2.`  
  
 `Processed 5 pages for database 'msdb', file 'MSDBLog' on file 2.`  
  
 `BACKUP DATABASE successfully processed 693 pages in 0.725 seconds (7.830 MB/sec)`  
  
### <a name="e-using-sqlcmd-to-execute-code-on-multiple-instances"></a><span data-ttu-id="67d60-206">E.</span><span class="sxs-lookup"><span data-stu-id="67d60-206">E.</span></span> <span data-ttu-id="67d60-207">sqlcmd を使用した複数のインスタンスでのコードの実行</span><span class="sxs-lookup"><span data-stu-id="67d60-207">Using sqlcmd to execute code on multiple instances</span></span>  
 <span data-ttu-id="67d60-208">ファイル内の次のコードは、2 つのインスタンスに接続するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="67d60-208">The following code in a file shows a script that connects to two instances.</span></span> <span data-ttu-id="67d60-209">2 番目のインスタンスへの接続の前に `GO` が記述されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="67d60-209">Notice the `GO` before the connection to the second instance.</span></span>  
  
 `:CONNECT <server>\,<instance1>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
 `:CONNECT <server>\,<instance2>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
### <a name="e-returning-xml-output"></a><span data-ttu-id="67d60-210">E.</span><span class="sxs-lookup"><span data-stu-id="67d60-210">E.</span></span> <span data-ttu-id="67d60-211">XML 出力の取得</span><span class="sxs-lookup"><span data-stu-id="67d60-211">Returning XML output</span></span>  
 <span data-ttu-id="67d60-212">次の例では、XML 出力が、連続するストリームでフォーマットされずに返されます。</span><span class="sxs-lookup"><span data-stu-id="67d60-212">The following example shows how XML output is returned unformatted, in a continuous stream.</span></span>  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> :XML ON`  
  
 `1> SELECT TOP 3 FirstName + ' ' + LastName + ', '`  
  
 `2> FROM Person.Person`  
  
 `3> GO`  
  
 `Syed Abbas, Catherine Abel, Kim Abercrombie,`  
  
### <a name="f-using-sqlcmd-in-a-windows-script-file"></a><span data-ttu-id="67d60-213">F.</span><span class="sxs-lookup"><span data-stu-id="67d60-213">F.</span></span> <span data-ttu-id="67d60-214">Windows スクリプト ファイルでの sqlcmd の使用</span><span class="sxs-lookup"><span data-stu-id="67d60-214">Using sqlcmd in a Windows script file</span></span>  
 <span data-ttu-id="67d60-215">などのコマンドは、 `sqlcmd` `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` .bat ファイルで VBScript と共に実行できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-215">A `sqlcmd`command such as `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` can be executed in a .bat file together with VBScript.</span></span> <span data-ttu-id="67d60-216">この場合、対話型のオプションは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="67d60-216">In this case, do not use interactive options.</span></span> <span data-ttu-id="67d60-217">また、.bat ファイルを実行するコンピューターには `sqlcmd` がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="67d60-217">`sqlcmd` must be installed on the computer that is executing the .bat file.</span></span>  
  
 <span data-ttu-id="67d60-218">最初に、次の 4 つのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="67d60-218">First, create the following four files:</span></span>  
  
-   <span data-ttu-id="67d60-219">C:\badscript.sql</span><span class="sxs-lookup"><span data-stu-id="67d60-219">C:\badscript.sql</span></span>  
  
    ```  
    SELECT batch_1_this_is_an_error  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="67d60-220">C:\goodscript.sql</span><span class="sxs-lookup"><span data-stu-id="67d60-220">C:\goodscript.sql</span></span>  
  
    ```  
    SELECT 'batch #1'  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="67d60-221">C:\returnvalue.sql</span><span class="sxs-lookup"><span data-stu-id="67d60-221">C:\returnvalue.sql</span></span>  
  
    ```  
    :exit(select 100)  
    @echo off  
    C:\windowsscript.bat  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
-   <span data-ttu-id="67d60-222">C:\windowsscript.bat</span><span class="sxs-lookup"><span data-stu-id="67d60-222">C:\windowsscript.bat</span></span>  
  
    ```  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
 <span data-ttu-id="67d60-223">その後、コマンド プロンプトで次のように `C:\windowsscript.bat`を実行します。</span><span class="sxs-lookup"><span data-stu-id="67d60-223">Then, at the command prompt, run `C:\windowsscript.bat`:</span></span>  
  
 `C:\>windowsscript.bat`  
  
 `Running badscript.sql`  
  
 `== An error occurred`  
  
 `Running goodscript.sql`  
  
 `Running returnvalue.sql`  
  
 `SQLCMD returned 100 to the command shell`  
  
### <a name="g-using-sqlcmd-to-set-encryption-on-azure-sql-database"></a><span data-ttu-id="67d60-224">G.</span><span class="sxs-lookup"><span data-stu-id="67d60-224">G.</span></span> <span data-ttu-id="67d60-225">sqlcmd を使用した Azure SQL Database での暗号化の設定</span><span class="sxs-lookup"><span data-stu-id="67d60-225">Using sqlcmd to set encryption on Azure SQL Database</span></span>  
 <span data-ttu-id="67d60-226">`sqlcmd`データへの接続でを実行して、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 暗号化と証明書の信頼を指定できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-226">A `sqlcmd`can be executed on a connection to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data on to specify encryption and certificate trust.</span></span> <span data-ttu-id="67d60-227">次の2つの ' sqlcmd ' ' オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="67d60-227">Two \`sqlcmd\`\`\`options are available:</span></span>  
  
-   <span data-ttu-id="67d60-228">暗号化された接続を要求するには、クライアント側で -N スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="67d60-228">The -N switch is used by the client to request an encrypted connection.</span></span> <span data-ttu-id="67d60-229">このオプションは、ADO.net オプションの `ENCRYPT = true`と同等です。</span><span class="sxs-lookup"><span data-stu-id="67d60-229">This option is equivalent to the ADO.net option `ENCRYPT = true`.</span></span>  
  
-   <span data-ttu-id="67d60-230">サーバーの証明書を信頼し、その有効性を検証しないように設定するには、クライアント側で -C スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="67d60-230">The -C switch is used by the client to configure it to implicitly the trust server certificate and not validate it.</span></span> <span data-ttu-id="67d60-231">このオプションは、ADO.net オプションの `TRUSTSERVERCERTIFICATE = true`と同等です。</span><span class="sxs-lookup"><span data-stu-id="67d60-231">This option is equivalent to the ADO.net option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="67d60-232">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サービスは、SQL Server インスタンスで使用できるすべての `SET` オプションをサポートするわけではありません。</span><span class="sxs-lookup"><span data-stu-id="67d60-232">The [!INCLUDE[ssSDS](../../includes/sssds-md.md)] service does not support all the `SET` options available on a SQL Server instance.</span></span> <span data-ttu-id="67d60-233">次の `SET` オプションを `ON` または `OFF`に設定すると、エラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="67d60-233">The following options throw an error when the corresponding `SET` option is set to `ON` or `OFF`:</span></span>  
  
-   <span data-ttu-id="67d60-234">[SET ANSI_DEFAULTS]</span><span class="sxs-lookup"><span data-stu-id="67d60-234">SET ANSI_DEFAULTS</span></span>  
  
-   <span data-ttu-id="67d60-235">[SET ANSI_NULLS]</span><span class="sxs-lookup"><span data-stu-id="67d60-235">SET ANSI_NULLS</span></span>  
  
-   <span data-ttu-id="67d60-236">SET REMOTE_PROC_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="67d60-236">SET REMOTE_PROC_TRANSACTIONS</span></span>  
  
-   <span data-ttu-id="67d60-237">SET ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="67d60-237">SET ANSI_NULL_DEFAULT</span></span>  
  
 <span data-ttu-id="67d60-238">次の SET オプションは例外をスローしませんが、使用できません。</span><span class="sxs-lookup"><span data-stu-id="67d60-238">The following SET options do not throw exceptions but cannot be used.</span></span> <span data-ttu-id="67d60-239">これらのオプションは非推奨とされます：</span><span class="sxs-lookup"><span data-stu-id="67d60-239">They are deprecated:</span></span>  
  
-   <span data-ttu-id="67d60-240">[SET CONCAT_NULL_YIELDS_NULL]</span><span class="sxs-lookup"><span data-stu-id="67d60-240">SET CONCAT_NULL_YIELDS_NULL</span></span>  
  
-   <span data-ttu-id="67d60-241">[SET ANSI_PADDING]</span><span class="sxs-lookup"><span data-stu-id="67d60-241">SET ANSI_PADDING</span></span>  
  
-   <span data-ttu-id="67d60-242">[SET QUERY_GOVERNOR_COST_LIMIT]</span><span class="sxs-lookup"><span data-stu-id="67d60-242">SET QUERY_GOVERNOR_COST_LIMIT</span></span>  
  
#### <a name="syntax"></a><span data-ttu-id="67d60-243">構文</span><span class="sxs-lookup"><span data-stu-id="67d60-243">Syntax</span></span>  
 <span data-ttu-id="67d60-244">次の構文の例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider の設定に `ForceProtocolEncryption = False`、 `Trust Server Certificate = No`</span><span class="sxs-lookup"><span data-stu-id="67d60-244">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span></span>  
  
 <span data-ttu-id="67d60-245">Windows 資格情報を使用して接続し、通信を暗号化する:</span><span class="sxs-lookup"><span data-stu-id="67d60-245">Connect using Windows credentials and encrypt communication:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="67d60-246">Windows 資格情報を使用して接続し、サーバーの証明書を信頼する:</span><span class="sxs-lookup"><span data-stu-id="67d60-246">Connect using Windows credentials and trust server certificate:</span></span>  
  
```  
SQLCMD -E -C  
  
```  
  
 <span data-ttu-id="67d60-247">Windows 資格情報を使用して接続し、通信を暗号化して、サーバーの証明書を信頼する:</span><span class="sxs-lookup"><span data-stu-id="67d60-247">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="67d60-248">次の構文の例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider の設定に `ForceProtocolEncryption = True`と `TrustServerCertificate = Yes`が含まれる場合を示しています。</span><span class="sxs-lookup"><span data-stu-id="67d60-248">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.</span></span>  
  
 <span data-ttu-id="67d60-249">Windows 資格情報を使用して接続し、通信を暗号化して、サーバーの証明書を信頼する:</span><span class="sxs-lookup"><span data-stu-id="67d60-249">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E  
  
```  
  
 <span data-ttu-id="67d60-250">Windows 資格情報を使用して接続し、通信を暗号化して、サーバーの証明書を信頼する:</span><span class="sxs-lookup"><span data-stu-id="67d60-250">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="67d60-251">Windows 資格情報を使用して接続し、通信を暗号化して、サーバーの証明書を信頼する:</span><span class="sxs-lookup"><span data-stu-id="67d60-251">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -T  
  
```  
  
 <span data-ttu-id="67d60-252">Windows 資格情報を使用して接続し、通信を暗号化して、サーバーの証明書を信頼する:</span><span class="sxs-lookup"><span data-stu-id="67d60-252">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="67d60-253">プロバイダーで `ForceProtocolEncryption = True` が指定されている場合、接続文字列で `Encrypt=No` が設定されていても暗号化が有効になります。</span><span class="sxs-lookup"><span data-stu-id="67d60-253">If the provider specifies `ForceProtocolEncryption = True` then encryption is enabled even if `Encrypt=No` in the connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d60-254">参照</span><span class="sxs-lookup"><span data-stu-id="67d60-254">See Also</span></span>  
 <span data-ttu-id="67d60-255">[sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="67d60-255">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="67d60-256">[sqlcmd でのスクリプト変数の使用](sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="67d60-256">[Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="67d60-257">[クエリ エディターによる SQLCMD スクリプトの編集](edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="67d60-257">[Edit SQLCMD Scripts with Query Editor](edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="67d60-258">[ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="67d60-258">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="67d60-259">CmdExec ジョブ ステップの作成</span><span class="sxs-lookup"><span data-stu-id="67d60-259">Create a CmdExec Job Step</span></span>](../../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
