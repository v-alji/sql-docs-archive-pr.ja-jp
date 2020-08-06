---
title: osql ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- operating systems [SQL Server], commands
- osql utility [SQL Server]
- stored procedures [SQL Server], command prompt
- scripts [SQL Server], command prompt
- RESET command
- GO command
- command prompt utilities [SQL Server], osql
- CTRL+C command
ms.assetid: cf530d9e-0609-4528-8975-ab8e08e40b9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95782afe0de8567781316e3478d04a090f968ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711297"
---
# <a name="osql-utility"></a><span data-ttu-id="966eb-102">osql ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="966eb-102">osql Utility</span></span>
  <span data-ttu-id="966eb-103">**osql** ユーティリティを使用すると、 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルを入力できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-103">The **osql** utility allows you to enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files.</span></span> <span data-ttu-id="966eb-104">また、このユーティリティは ODBC を使用してサーバーと通信します。</span><span class="sxs-lookup"><span data-stu-id="966eb-104">This utility uses ODBC to communicate with the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="966eb-105">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の将来のバージョンで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="966eb-105">This feature will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="966eb-106">新しい開発作業では、この機能を使用しないでください。また、現在この機能を使用しているアプリケーションの変更を計画してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-106">Avoid using this feature in new development work, and plan to modify applications that currently use the feature.</span></span> <span data-ttu-id="966eb-107">代わりに **sqlcmd** を使用します。</span><span class="sxs-lookup"><span data-stu-id="966eb-107">Use **sqlcmd** instead.</span></span> <span data-ttu-id="966eb-108">詳細については、「 [sqlcmd Utility](sqlcmd-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-108">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966eb-109">構文</span><span class="sxs-lookup"><span data-stu-id="966eb-109">Syntax</span></span>  
  
```  
  
      osql  
[-?] |  
[-L] |  
[  
  {  
     {-Ulogin_id [-Ppassword]} | -E }  
     [-Sserver_name[\instance_name]] [-Hwksta_name] [-ddb_name]  
     [-ltime_out] [-ttime_out] [-hheaders]  
     [-scol_separator] [-wcolumn_width] [-apacket_size]  
     [-e] [-I] [-D data_source_name]  
     [-ccmd_end] [-q "query"] [-Q"query"]  
     [-n] [-merror_level] [-r {0 | 1}]  
     [-iinput_file] [-ooutput_file] [-p]  
     [-b] [-u] [-R] [-O]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="966eb-110">引数</span><span class="sxs-lookup"><span data-stu-id="966eb-110">Arguments</span></span>  
 <span data-ttu-id="966eb-111">**-?**</span><span class="sxs-lookup"><span data-stu-id="966eb-111">**-?**</span></span>  
 <span data-ttu-id="966eb-112">**osql** のスイッチに関する構文の概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="966eb-112">Displays the syntax summary of **osql** switches.</span></span>  
  
 <span data-ttu-id="966eb-113">**-L**</span><span class="sxs-lookup"><span data-stu-id="966eb-113">**-L**</span></span>  
 <span data-ttu-id="966eb-114">ローカルに構成されたサーバーと、ネットワーク上でブロードキャストしているサーバー名の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="966eb-114">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-115">ネットワーク上のブロードキャストの特性によっては、 **osql** は、一部のサーバーからタイムリーな応答を受信できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="966eb-115">Due to the nature of broadcasting on networks, **osql** may not receive a timely response from all servers.</span></span> <span data-ttu-id="966eb-116">そのため、返されるサーバーのリストは、このオプションの実行ごとに異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="966eb-116">Therefore the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="966eb-117">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="966eb-117">**-U** _login_id_</span></span>  
 <span data-ttu-id="966eb-118">ユーザーのログイン ID です。</span><span class="sxs-lookup"><span data-stu-id="966eb-118">Is the user login ID.</span></span> <span data-ttu-id="966eb-119">ログイン ID では大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-119">Login IDs are case-sensitive.</span></span>  
  
 <span data-ttu-id="966eb-120">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="966eb-120">**-P** _password_</span></span>  
 <span data-ttu-id="966eb-121">ユーザーが指定するパスワードです。</span><span class="sxs-lookup"><span data-stu-id="966eb-121">Is a user-specified password.</span></span> <span data-ttu-id="966eb-122">**-P** オプションを使用しない場合は、 **osql** ではパスワードの入力が要求されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-122">If the **-P** option is not used, **osql** prompts for a password.</span></span> <span data-ttu-id="966eb-123">**-P** オプションをコマンド プロンプトの最後にパスワードなしで使用すると、 **osql** ではデフォルトのパスワード (NULL) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-123">If the **-P** option is used at the end of the command prompt without any password, **osql** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="966eb-124">空白のパスワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="966eb-124">Do not use a blank password.</span></span> <span data-ttu-id="966eb-125">強力なパスワードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-125">Use a strong password.</span></span> <span data-ttu-id="966eb-126">詳細については、「 [Strong Passwords](../relational-databases/security/strong-passwords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-126">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="966eb-127">パスワードでは大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-127">Passwords are case-sensitive.</span></span>  
  
 <span data-ttu-id="966eb-128">OSQLPASSWORD 環境変数を使用して、現在のセッションの既定のパスワードを設定できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-128">The OSQLPASSWORD environment variable allows you to set a default password for the current session.</span></span> <span data-ttu-id="966eb-129">したがって、バッチ ファイルにパスワードを書き込む必要がありません。</span><span class="sxs-lookup"><span data-stu-id="966eb-129">Therefore, you do not have to hard code a password into batch files.</span></span>  
  
 <span data-ttu-id="966eb-130">**-P** オプションを使用してパスワードを指定しないと、 **osql** では最初に OSQLPASSWORD 変数が確認されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-130">If you do not specify a password with the **-P** option, **osql** first checks for the OSQLPASSWORD variable.</span></span> <span data-ttu-id="966eb-131">値が設定されていないと、 **osql** では既定のパスワード (NULL) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-131">If no value is set, **osql** uses the default password, NULL.</span></span> <span data-ttu-id="966eb-132">次の例では、コマンド プロンプトで OSQLPASSWORD 変数を設定してから **osql** ユーティリティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="966eb-132">The following example sets the OSQLPASSWORD variable at a command prompt and then accesses the **osql** utility:</span></span>  
  
```  
C:\>SET OSQLPASSWORD=abracadabra  
C:\>osql   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="966eb-133">パスワードをマスクする場合は、 **-P** オプションを **-U** オプションと共に指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="966eb-133">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="966eb-134">**osql** を **-U** オプションおよび他のスイッチと共に指定した後 ( **-P**は指定しない)、Enter キーを押すと、 **osql** によってパスワードが要求されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-134">Instead, after specifying **osql** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and **osql** will prompt you for a password.</span></span> <span data-ttu-id="966eb-135">この方法を使用すると、入力時にパスワードが確実にマスクされます。</span><span class="sxs-lookup"><span data-stu-id="966eb-135">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="966eb-136">**-E**</span><span class="sxs-lookup"><span data-stu-id="966eb-136">**-E**</span></span>  
 <span data-ttu-id="966eb-137">パスワードを要求せずに、セキュリティ接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="966eb-137">Uses a trusted connection instead of requesting a password.</span></span>  
  
 <span data-ttu-id="966eb-138">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="966eb-138">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="966eb-139">接続先となる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-139">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="966eb-140">サーバー上の *の既定のインスタンスに接続するには、* server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-140">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="966eb-141">_server_name_ **\\** サーバー上のの名前付きインスタンスに接続するには、server_name_instance_name_を指定し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="966eb-141">Specify _server_name_**\\**_instance_name_ to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="966eb-142">サーバーを指定しない場合、 **osql** は、ローカル コンピューター上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="966eb-142">If no server is specified, **osql** connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="966eb-143">ネットワーク上のリモート コンピューターから **osql** を実行するときは、このオプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="966eb-143">This option is required when executing **osql** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="966eb-144">**-H** _wksta_name_</span><span class="sxs-lookup"><span data-stu-id="966eb-144">**-H** _wksta_name_</span></span>  
 <span data-ttu-id="966eb-145">ワークステーション名を指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-145">Is a workstation name.</span></span> <span data-ttu-id="966eb-146">ワークステーション名は **sysprocesses.hostname** に格納され、 **sp_who**により表示されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-146">The workstation name is stored in **sysprocesses.hostname** and is displayed by **sp_who**.</span></span> <span data-ttu-id="966eb-147">このオプションが指定されていない場合は、現在のコンピューター名であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="966eb-147">If this option is not specified, the current computer name is assumed.</span></span>  
  
 <span data-ttu-id="966eb-148">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="966eb-148">**-d** _db_name_</span></span>  
 <span data-ttu-id="966eb-149">*osql* の開始時に USE **db_name**ステートメントを発行します。</span><span class="sxs-lookup"><span data-stu-id="966eb-149">Issues a USE *db_name* statement when **osql**is started.</span></span>  
  
 <span data-ttu-id="966eb-150">**-l** _time_out_</span><span class="sxs-lookup"><span data-stu-id="966eb-150">**-l** _time_out_</span></span>  
 <span data-ttu-id="966eb-151">**osql** がログイン タイムアウトになる時間を秒単位で指定します。**osql** でのログインに関する既定のタイムアウトは 8 秒です。</span><span class="sxs-lookup"><span data-stu-id="966eb-151">Specifies the number of seconds before an **osql** login times out. The default time-out for login to **osql** is eight seconds.</span></span>  
  
 <span data-ttu-id="966eb-152">**-t** _time_out_</span><span class="sxs-lookup"><span data-stu-id="966eb-152">**-t** _time_out_</span></span>  
 <span data-ttu-id="966eb-153">コマンドの実行待ち時間を秒単位で指定します。*time_out* 値を指定しないと、コマンドはタイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="966eb-153">Specifies the number of seconds before a command times out. If a *time_out* value is not specified, commands do not time out.</span></span>  
  
 <span data-ttu-id="966eb-154">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="966eb-154">**-h** _headers_</span></span>  
 <span data-ttu-id="966eb-155">列ヘッダーの間に出力する行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-155">Specifies the number of rows to print between column headings.</span></span> <span data-ttu-id="966eb-156">既定では、各クエリの結果に対して、ヘッダーは 1 つだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-156">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="966eb-157">ヘッダーを出力しない場合は、-1 を指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-157">Use -1 to specify that no headers will be printed.</span></span> <span data-ttu-id="966eb-158">-1 を使用する場合、パラメーターと設定値の間には空白を入れないでください ( **-h -1** ではなく **-h-1**)。</span><span class="sxs-lookup"><span data-stu-id="966eb-158">If -1 is used, there must be no space between the parameter and the setting (**-h-1**, not **-h -1**).</span></span>  
  
 <span data-ttu-id="966eb-159">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="966eb-159">**-s** _col_separator_</span></span>  
 <span data-ttu-id="966eb-160">列の区切り文字を指定します。既定値は空白文字です。</span><span class="sxs-lookup"><span data-stu-id="966eb-160">Specifies the column-separator character, which is a blank space by default.</span></span> <span data-ttu-id="966eb-161">オペレーティングシステムに特別な意味を持つ文字 (たとえば、|; &) を使用するには、 \< > 文字を二重引用符 (") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="966eb-161">To use characters that have special meaning to the operating system (for example, | ; & \< >), enclose the character in double quotation marks (").</span></span>  
  
 <span data-ttu-id="966eb-162">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="966eb-162">**-w** _column_width_</span></span>  
 <span data-ttu-id="966eb-163">出力用の画面幅を設定できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-163">Allows the user to set the screen width for output.</span></span> <span data-ttu-id="966eb-164">既定値は 80 文字です。</span><span class="sxs-lookup"><span data-stu-id="966eb-164">The default is 80 characters.</span></span> <span data-ttu-id="966eb-165">出力行が画面幅の最大値を超えると、複数の行に分けて出力されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-165">When an output line has reached its maximum screen width, it is broken into multiple lines.</span></span>  
  
 <span data-ttu-id="966eb-166">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="966eb-166">**-a** _packet_size_</span></span>  
 <span data-ttu-id="966eb-167">サイズの異なるパケットが要求できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-167">Allows you to request a different-sized packet.</span></span> <span data-ttu-id="966eb-168">*packet_size* の有効値は 512 ～ 65535 です。</span><span class="sxs-lookup"><span data-stu-id="966eb-168">The valid values for *packet_size* are 512 through 65535.</span></span> <span data-ttu-id="966eb-169">既定値 **osql** はサーバーの既定値です。</span><span class="sxs-lookup"><span data-stu-id="966eb-169">The default value **osql** is the server default.</span></span> <span data-ttu-id="966eb-170">パケット サイズを大きくすると、各 GO コマンドの間に多くの SQL ステートメントが含まれているサイズの大きいスクリプトを実行する場合に、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="966eb-170">Increased packet size can enhance performance on larger script execution where the amount of SQL statements between GO commands is substantial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="966eb-171">のテストでは、一括コピーが最も速くなる設定値は 8,192 という結果が出ています。</span><span class="sxs-lookup"><span data-stu-id="966eb-171">testing indicates that 8192 is typically the fastest setting for bulk copy operations.</span></span> <span data-ttu-id="966eb-172">大きなパケット サイズを要求することもできますが、要求が認められない場合は、サーバーでの既定値が **osql** での既定値になります。</span><span class="sxs-lookup"><span data-stu-id="966eb-172">A larger packet size can be requested, but **osql** defaults to the server default if the request cannot be granted.</span></span>  
  
 <span data-ttu-id="966eb-173">**-e**</span><span class="sxs-lookup"><span data-stu-id="966eb-173">**-e**</span></span>  
 <span data-ttu-id="966eb-174">入力のエコーを返します。</span><span class="sxs-lookup"><span data-stu-id="966eb-174">Echoes input.</span></span>  
  
 <span data-ttu-id="966eb-175">**-I**</span><span class="sxs-lookup"><span data-stu-id="966eb-175">**-I**</span></span>  
 <span data-ttu-id="966eb-176">QUOTED_IDENTIFIER 接続オプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="966eb-176">Sets the QUOTED_IDENTIFIER connection option on.</span></span>  
  
 <span data-ttu-id="966eb-177">**-D** _data_source_name_</span><span class="sxs-lookup"><span data-stu-id="966eb-177">**-D** _data_source_name_</span></span>  
 <span data-ttu-id="966eb-178">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]用の ODBC ドライバーを使用して定義された ODBC データ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="966eb-178">Connects to an ODBC data source that is defined using the ODBC driver for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="966eb-179">**osql** 接続では、データ ソースで指定されたオプションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-179">The **osql** connection uses the options specified in the data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-180">このオプションは、他のドライバー用に定義されたデータ ソースでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="966eb-180">This option does not work with data sources defined for other drivers.</span></span>  
  
 <span data-ttu-id="966eb-181">**-c** _cmd_end_</span><span class="sxs-lookup"><span data-stu-id="966eb-181">**-c** _cmd_end_</span></span>  
 <span data-ttu-id="966eb-182">コマンド ターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-182">Specifies the command terminator.</span></span> <span data-ttu-id="966eb-183">既定では、GO だけが入力されている行があると、コマンドが終了したと見なされ、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に送られます。</span><span class="sxs-lookup"><span data-stu-id="966eb-183">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by entering GO on a line by itself.</span></span> <span data-ttu-id="966eb-184">コマンド ターミネータをリセットする場合、 [!INCLUDE[tsql](../includes/tsql-md.md)] の予約語やオペレーティング システムで特別な意味を持つ文字は、先頭に円記号が付いているかどうかに関係なく、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="966eb-184">When you reset the command terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved words or characters that have special meaning to the operating system, whether preceded by a backslash or not.</span></span>  
  
 <span data-ttu-id="966eb-185">**-q "** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="966eb-185">**-q "** _query_ **"**</span></span>  
 <span data-ttu-id="966eb-186">**osql** の起動時にクエリを実行しますが、クエリが完了しても **osql** を終了しません。</span><span class="sxs-lookup"><span data-stu-id="966eb-186">Executes a query when **osql** starts, but does not exit **osql** when the query completes.</span></span> <span data-ttu-id="966eb-187">クエリ ステートメントには GO を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="966eb-187">(Note that the query statement should not include GO).</span></span> <span data-ttu-id="966eb-188">バッチ ファイルからクエリを実行する場合は、% 変数 (環境変数 %variable%) も使用できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-188">If you issue a query from a batch file, use %variables, or environment %variables%.</span></span> <span data-ttu-id="966eb-189">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="966eb-189">For example:</span></span>  
  
```  
SET table=sys.objects  
osql -E -q "select name, object_id from %table%"  
```  
  
 <span data-ttu-id="966eb-190">クエリは二重引用符で、クエリに埋め込まれたものは単一引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="966eb-190">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="966eb-191">**-Q"** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="966eb-191">**-Q"** _query_ **"**</span></span>  
 <span data-ttu-id="966eb-192">クエリの実行後、直ちに **osql**を終了します。</span><span class="sxs-lookup"><span data-stu-id="966eb-192">Executes a query and immediately exits **osql**.</span></span> <span data-ttu-id="966eb-193">クエリは二重引用符で、クエリに埋め込まれたものは単一引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="966eb-193">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="966eb-194">**-n**</span><span class="sxs-lookup"><span data-stu-id="966eb-194">**-n**</span></span>  
 <span data-ttu-id="966eb-195">入力行から行番号とプロンプト記号 (>) を削除します。</span><span class="sxs-lookup"><span data-stu-id="966eb-195">Removes numbering and the prompt symbol (>) from input lines.</span></span>  
  
 <span data-ttu-id="966eb-196">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="966eb-196">**-m** _error_level_</span></span>  
 <span data-ttu-id="966eb-197">エラー メッセージの表示をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="966eb-197">Customizes the display of error messages.</span></span> <span data-ttu-id="966eb-198">指定した重大度レベル以上のエラーが発生すると、メッセージ番号、状況、エラー レベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-198">The message number, state, and error level are displayed for errors of the specified severity level or higher.</span></span> <span data-ttu-id="966eb-199">指定した重大度レベルより低いレベルのエラーの場合は、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="966eb-199">Nothing is displayed for errors of levels lower than the specified level.</span></span> <span data-ttu-id="966eb-200">**-1** を指定すると、単なる情報メッセージであっても、すべてのヘッダーがメッセージと共に返されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-200">Use **-1** to specify that all headers are returned with messages, even informational messages.</span></span> <span data-ttu-id="966eb-201">**-1**を使用する場合、パラメーターと設定値の間には空白を入れないでください ( **-m -1**ではなく、 **-m-1**を使用)。</span><span class="sxs-lookup"><span data-stu-id="966eb-201">If using **-1**, there must be no space between the parameter and the setting (**-m-1**, not **-m -1**).</span></span>  
  
 <span data-ttu-id="966eb-202">**-r** { **0**| **1**}</span><span class="sxs-lookup"><span data-stu-id="966eb-202">**-r** { **0**| **1**}</span></span>  
 <span data-ttu-id="966eb-203">メッセージ出力を画面にリダイレクトします (**stderr**)。</span><span class="sxs-lookup"><span data-stu-id="966eb-203">Redirects message output to the screen (**stderr**).</span></span> <span data-ttu-id="966eb-204">パラメーターを指定しない場合や、 **0**を指定した場合は、重大度レベル 11 以上のエラー メッセージだけがリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="966eb-204">If you do not specify a parameter, or if you specify **0**, only error messages with a severity level 11 or higher are redirected.</span></span> <span data-ttu-id="966eb-205">**1**を指定した場合は、"print" を含むすべてのメッセージ出力がリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="966eb-205">If you specify **1**, all message output (including "print") is redirected.</span></span>  
  
 <span data-ttu-id="966eb-206">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="966eb-206">**-i** _input_file_</span></span>  
 <span data-ttu-id="966eb-207">SQL ステートメントまたはストアド プロシージャのバッチを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-207">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="966eb-208">**\<** -i **の代わりに、未満を示す比較演算子 (** ) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="966eb-208">The less than (**\<**) comparison operator can be used in place of **-i**.</span></span>  
  
 <span data-ttu-id="966eb-209">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="966eb-209">**-o** _output_file_</span></span>  
 <span data-ttu-id="966eb-210">**osql**からの出力を受信するファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-210">Identifies the file that receives output from **osql**.</span></span> <span data-ttu-id="966eb-211">**>** -o **の代わりに、より大きい (** ) 比較演算子を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="966eb-211">The greater than (**>**) comparison operator can be used in place of **-o**.</span></span>  
  
 <span data-ttu-id="966eb-212">*input_file* が Unicode ではなく、 **-u** が指定されていない場合、 *output_file* は OEM 形式で格納されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-212">If *input_file* is not Unicode and **-u** is not specified, *output_file* is stored in OEM format.</span></span> <span data-ttu-id="966eb-213">*input_file* が Unicode であるか、 **-u** が指定されている場合、 *output_file* は Unicode 形式で格納されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-213">If *input_file* is Unicode or **-u** is specified, *output_file* is stored in Unicode format.</span></span>  
  
 <span data-ttu-id="966eb-214">**-p**</span><span class="sxs-lookup"><span data-stu-id="966eb-214">**-p**</span></span>  
 <span data-ttu-id="966eb-215">パフォーマンス統計を出力します。</span><span class="sxs-lookup"><span data-stu-id="966eb-215">Prints performance statistics.</span></span>  
  
 <span data-ttu-id="966eb-216">**-b**</span><span class="sxs-lookup"><span data-stu-id="966eb-216">**-b**</span></span>  
 <span data-ttu-id="966eb-217">エラーが発生したときに、 **osql** を終了し、DOS ERRORLEVEL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="966eb-217">Specifies that **osql** exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="966eb-218">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエラー メッセージの重大度が 11 以上の場合は、DOS ERRORLEVEL 変数に返される値は 1 です。それ以外の場合は、値 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-218">The value returned to the DOS ERRORLEVEL variable is 1 when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity of 11 or greater; otherwise, the value returned is 0.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="966eb-219">MS-DOS バッチ ファイルにより、DOS ERRORLEVEL の値をテストすることができ、エラーを適切に処理できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-219">MS-DOS batch files can test the value of DOS ERRORLEVEL and handle the error appropriately.</span></span>  
  
 <span data-ttu-id="966eb-220">**-u**</span><span class="sxs-lookup"><span data-stu-id="966eb-220">**-u**</span></span>  
 <span data-ttu-id="966eb-221">*input_file* の形式に関係なく、 *output_file*を Unicode 形式で格納するように指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-221">Specifies that *output_file* is stored in Unicode format, regardless of the format of the *input_file*.</span></span>  
  
 <span data-ttu-id="966eb-222">**-R**</span><span class="sxs-lookup"><span data-stu-id="966eb-222">**-R**</span></span>  
 <span data-ttu-id="966eb-223">通貨、日付、および時刻データを文字データに変換するときに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC ドライバーでクライアントの設定を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-223">Specifies that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver use client settings when converting currency, date, and time data to character data.</span></span>  
  
 <span data-ttu-id="966eb-224">**-O**</span><span class="sxs-lookup"><span data-stu-id="966eb-224">**-O**</span></span>  
 <span data-ttu-id="966eb-225">**isql** の先行バージョンの動作と一致するように、 **osql**の一部の機能を使用不能にします。</span><span class="sxs-lookup"><span data-stu-id="966eb-225">Specifies that certain **osql** features be deactivated to match the behavior of earlier versions of **isql**.</span></span> <span data-ttu-id="966eb-226">このオプションを指定すると、次の機能は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="966eb-226">These features are deactivated:</span></span>  
  
-   <span data-ttu-id="966eb-227">EOF バッチ処理</span><span class="sxs-lookup"><span data-stu-id="966eb-227">EOF batch processing</span></span>  
  
-   <span data-ttu-id="966eb-228">コンソール幅の自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="966eb-228">Automatic console width scaling</span></span>  
  
-   <span data-ttu-id="966eb-229">広範なメッセージ</span><span class="sxs-lookup"><span data-stu-id="966eb-229">Wide messages</span></span>  
  
 <span data-ttu-id="966eb-230">また、このオプションは DOS ERRORLEVEL の既定値を -1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="966eb-230">It also sets the default DOS ERRORLEVEL value to -1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-231">**-n**、 **-O** および **-D** オプションは、 **osql**ではサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="966eb-231">The **-n**, **-O** and **-D** options are no longer supported by **osql**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="966eb-232">解説</span><span class="sxs-lookup"><span data-stu-id="966eb-232">Remarks</span></span>  
 <span data-ttu-id="966eb-233">**osql** ユーティリティは、ここに記載された、大文字と小文字では異なる機能を持つオプションを使用して、オペレーティング システムから直接起動されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-233">The **osql** utility is started directly from the operating system with the case-sensitive options listed here.</span></span> <span data-ttu-id="966eb-234">起動されると、 **osql**は SQL ステートメントを受け取り、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に対話的に送ります。</span><span class="sxs-lookup"><span data-stu-id="966eb-234">After **osql**starts, it accepts SQL statements and sends them to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] interactively.</span></span> <span data-ttu-id="966eb-235">結果はフォーマットされ、画面に表示されます (**stdout**)。</span><span class="sxs-lookup"><span data-stu-id="966eb-235">The results are formatted and displayed on the screen (**stdout**).</span></span> <span data-ttu-id="966eb-236">**osql**を終了するには、QUIT または EXIT を使用します。</span><span class="sxs-lookup"><span data-stu-id="966eb-236">Use QUIT or EXIT to exit from **osql**.</span></span>  
  
 <span data-ttu-id="966eb-237">**Osql**を開始するときにユーザー名を指定しなかった場合は、に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] よって環境変数が確認され、 **osqluser = ( *`user`* )** や**osqlserver = ( *`server`* )** などのように使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-237">If you do not specify a user name when you start **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for the environment variables and uses those, for example, **osqluser=(*`user`*)** or **osqlserver=(*`server`*)**.</span></span> <span data-ttu-id="966eb-238">環境変数が設定されていない場合は、ワークステーションのユーザー名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-238">If no environment variables are set, the workstation user name is used.</span></span> <span data-ttu-id="966eb-239">サーバーを指定していない場合は、ワークステーション名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-239">If you do not specify a server, the name of the workstation is used.</span></span>  
  
 <span data-ttu-id="966eb-240">**-U** と **-P** のどちらのオプションも使用しない場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では接続時に [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 認証モードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-240">If neither the **-U** or **-P** options are used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attempts to connect using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication Mode.</span></span> <span data-ttu-id="966eb-241">認証は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] osql **を実行しているユーザーの**Windows アカウントに基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="966eb-241">Authentication is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows account of the user running **osql**.</span></span>  
  
 <span data-ttu-id="966eb-242">**osql** ユーティリティでは ODBC API が使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-242">The **osql** utility uses the ODBC API.</span></span> <span data-ttu-id="966eb-243">またこのユーティリティでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の ISO 接続オプションに対して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC ドライバーの既定の設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-243">The utility uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver default settings for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO connection options.</span></span> <span data-ttu-id="966eb-244">詳細については、「ANSI オプションの効果」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-244">For more information, see Effects of ANSI Options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-245">**osql** ユーティリティでは CLR ユーザー定義データ型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="966eb-245">The **osql** utility does not support CLR user-defined data types.</span></span> <span data-ttu-id="966eb-246">これらのデータ型を処理するには、 **sqlcmd** ユーティリティを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="966eb-246">To process these data types, you must use the **sqlcmd** utility.</span></span> <span data-ttu-id="966eb-247">詳細については、「 [sqlcmd Utility](sqlcmd-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-247">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="osql-commands"></a><span data-ttu-id="966eb-248">OSQL コマンド</span><span class="sxs-lookup"><span data-stu-id="966eb-248">OSQL Commands</span></span>  
 <span data-ttu-id="966eb-249">[!INCLUDE[tsql](../includes/tsql-md.md)] osql **では、** ステートメントの他に次のコマンドも使用できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-249">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within **osql**, these commands are also available.</span></span>  
  
|<span data-ttu-id="966eb-250">コマンド</span><span class="sxs-lookup"><span data-stu-id="966eb-250">Command</span></span>|<span data-ttu-id="966eb-251">説明</span><span class="sxs-lookup"><span data-stu-id="966eb-251">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="966eb-252">GO</span><span class="sxs-lookup"><span data-stu-id="966eb-252">GO</span></span>|<span data-ttu-id="966eb-253">最後の GO の後に入力したすべてのステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="966eb-253">Executes all statements entered after the last GO.</span></span>|  
|<span data-ttu-id="966eb-254">RESET</span><span class="sxs-lookup"><span data-stu-id="966eb-254">RESET</span></span>|<span data-ttu-id="966eb-255">入力したステートメントをすべて消去します。</span><span class="sxs-lookup"><span data-stu-id="966eb-255">Clears any statements you have entered.</span></span>|  
|<span data-ttu-id="966eb-256">QUIT または EXIT( )</span><span class="sxs-lookup"><span data-stu-id="966eb-256">QUIT or EXIT( )</span></span>|<span data-ttu-id="966eb-257">**osql**を終了します。</span><span class="sxs-lookup"><span data-stu-id="966eb-257">Exits from **osql**.</span></span>|  
|<span data-ttu-id="966eb-258">Ctrl + C</span><span class="sxs-lookup"><span data-stu-id="966eb-258">CTRL+C</span></span>|<span data-ttu-id="966eb-259">クエリを終了しますが、 **osql**は終了しません。</span><span class="sxs-lookup"><span data-stu-id="966eb-259">Ends a query without exiting from **osql**.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-260">!! コマンド</span><span class="sxs-lookup"><span data-stu-id="966eb-260">The !!</span></span> <span data-ttu-id="966eb-261">および ED コマンドは **osql**ではサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="966eb-261">and ED commands are no longer supported by **osql**.</span></span>  
  
 <span data-ttu-id="966eb-262">コマンド ターミネータ GO (既定値)、RESET、EXIT、QUIT、および Ctrl + C は、行頭の **osql** プロンプトの直後に使用した場合にだけ認識されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-262">The command terminators GO (by default), RESET EXIT, QUIT, and CTRL+C, are recognized only if they appear at the beginning of a line, immediately following the **osql** prompt.</span></span>  
  
 <span data-ttu-id="966eb-263">GO は、バッチの終わりとキャッシュされた [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの実行を知らせます。</span><span class="sxs-lookup"><span data-stu-id="966eb-263">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="966eb-264">各入力行の終わりで Enter キーを押すと、 **osql** はその行のステートメントをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="966eb-264">When you press ENTER at the end of each input line, **osql** caches the statements on that line.</span></span> <span data-ttu-id="966eb-265">GO を入力した後 Enter キーを押すと、現在キャッシュされているすべてのステートメントが一括して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に送られます。</span><span class="sxs-lookup"><span data-stu-id="966eb-265">When you press ENTER after typing GO, all of the currently cached statements are sent as a batch to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="966eb-266">現在の **osql** ユーティリティは、実行する各スクリプトの終わりに暗黙の GO があるものとして動作します。したがって、スクリプト内のすべてのステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-266">The current **osql** utility works as if there is an implied GO at the end of any script executed, therefore all statements in the script execute.</span></span>  
  
 <span data-ttu-id="966eb-267">行頭にコマンド ターミネータを入力すると、コマンドが終了します。</span><span class="sxs-lookup"><span data-stu-id="966eb-267">End a command by typing a line beginning with a command terminator.</span></span> <span data-ttu-id="966eb-268">コマンド ターミネータの後ろに整数を入力すると、コマンドの実行回数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-268">You can follow the command terminator with an integer to specify how many times the command should be run.</span></span> <span data-ttu-id="966eb-269">たとえば、コマンドを 100 回実行するには、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="966eb-269">For example, to execute this command 100 times, type:</span></span>  
  
```  
SELECT x = 1  
GO 100  
```  
  
 <span data-ttu-id="966eb-270">結果は、実行終了時に 1 回出力されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-270">The results are printed once at the end of execution.</span></span> <span data-ttu-id="966eb-271">**osql** で 1 行に入力できる文字数は、最大で 1,000 文字です。</span><span class="sxs-lookup"><span data-stu-id="966eb-271">**osql** does not accept more than 1,000 characters per line.</span></span> <span data-ttu-id="966eb-272">大きなステートメントは、複数の行に分けてください。</span><span class="sxs-lookup"><span data-stu-id="966eb-272">Large statements should be spread across multiple lines.</span></span>  
  
 <span data-ttu-id="966eb-273">Windows のコマンド再呼び出し機能を使用すると、 **osql** ステートメントの再呼び出しと修正が可能になります。</span><span class="sxs-lookup"><span data-stu-id="966eb-273">The command recall facilities of Windows can be used to recall and modify **osql** statements.</span></span> <span data-ttu-id="966eb-274">RESET を入力すると、既存のクエリ バッファーをクリアできます。</span><span class="sxs-lookup"><span data-stu-id="966eb-274">The existing query buffer can be cleared by typing RESET.</span></span>  
  
 <span data-ttu-id="966eb-275">ストアド プロシージャを実行するとき、 **osql** は同じバッチの各結果セットの間に空白行を 1 行ずつ出力します。</span><span class="sxs-lookup"><span data-stu-id="966eb-275">When running stored procedures, **osql** prints a blank line between each set of results in a batch.</span></span> <span data-ttu-id="966eb-276">また、"0 件処理されました" というメッセージは、そのメッセージが実行したステートメントに該当する場合にだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-276">In addition, the "0 rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
## <a name="using-osql-interactively"></a><span data-ttu-id="966eb-277">osql の対話的使用</span><span class="sxs-lookup"><span data-stu-id="966eb-277">Using osql Interactively</span></span>  
 <span data-ttu-id="966eb-278">**osql** を対話的に使用するには、コマンド プロンプトで **osql** コマンド (および任意のオプション) を入力します。</span><span class="sxs-lookup"><span data-stu-id="966eb-278">To use **osql** interactively, type the **osql** command (and any of the options) at a command prompt.</span></span>  
  
 <span data-ttu-id="966eb-279">次のようなコマンドを入力すると、 **osql** によって実行されるクエリ (Stores.qry など) が含まれているファイルの内容を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="966eb-279">You can read in a file containing a query (such as Stores.qry) for execution by **osql** by typing a command similar to this:</span></span>  
  
```  
osql -E -i stores.qry  
```  
  
 <span data-ttu-id="966eb-280">次のようなコマンドを入力すると、クエリ (Titles.qry など) が含まれているファイルを読み取り、結果を別のファイルに出力できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-280">You can read in a file containing a query (such as Titles.qry) and direct the results to another file by typing a command similar to this:</span></span>  
  
```  
osql -E -i titles.qry -o titles.res  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="966eb-281">可能であれば、 **-E**オプションを使用します (信頼関係接続)。</span><span class="sxs-lookup"><span data-stu-id="966eb-281">When possible, use the **-E**option (trusted connection).</span></span>  
  
 <span data-ttu-id="966eb-282">**Osql**を対話的に使用する場合、 **r**_file_name_を使用して、オペレーティングシステムファイルをコマンドバッファーに読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="966eb-282">When using **osql** interactively, you can read an operating-system file into the command buffer with **:r**_file_name_.</span></span> <span data-ttu-id="966eb-283">これにより、 *file_name* 内の SQL スクリプトが単一のバッチとして直接サーバーへ送信されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-283">This sends the SQL script in *file_name* directly to the server as a single batch.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-284">**osql**を使用するとき、GO によって SQL スクリプト ファイルに構文エラーが発生する場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は GO をバッチ区切り記号として処理しています。</span><span class="sxs-lookup"><span data-stu-id="966eb-284">When using **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] treats the batch separator GO, if it appears in a SQL script file, as a syntax error.</span></span>  
  
## <a name="inserting-comments"></a><span data-ttu-id="966eb-285">コメントの挿入</span><span class="sxs-lookup"><span data-stu-id="966eb-285">Inserting Comments</span></span>  
 <span data-ttu-id="966eb-286">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] osql **で**に送られる Transact-SQL ステートメントには、コメントを挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="966eb-286">You can include comments in a Transact-SQL statement submitted to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by **osql**.</span></span> <span data-ttu-id="966eb-287">-- (コメント) と /\*...\*/ (コメント) の 2 種類のコメント形式があります。</span><span class="sxs-lookup"><span data-stu-id="966eb-287">Two types of commenting styles are allowed: -- and /\*...\*/.</span></span>  
  
## <a name="using-exit-to-return-results-in-osql"></a><span data-ttu-id="966eb-288">EXIT によって osql から返される結果</span><span class="sxs-lookup"><span data-stu-id="966eb-288">Using EXIT to Return Results in osql</span></span>  
 <span data-ttu-id="966eb-289">**osql**からの戻り値に、SELECT ステートメントの結果を使用できます。</span><span class="sxs-lookup"><span data-stu-id="966eb-289">You can use the result of a SELECT statement as the return value from **osql**.</span></span> <span data-ttu-id="966eb-290">数値の場合、結果行の最終行の最終列は、4 バイトの (長) 整数に変換されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-290">If it is numeric, the last column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="966eb-291">MS-DOS は、下位バイトを親プロセスやオペレーティング システムのエラー レベルに渡します。</span><span class="sxs-lookup"><span data-stu-id="966eb-291">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="966eb-292">Windows では、4 バイトの整数全体を渡します。</span><span class="sxs-lookup"><span data-stu-id="966eb-292">Windows passes the entire 4-byte integer.</span></span> <span data-ttu-id="966eb-293">の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="966eb-293">The syntax is:</span></span>  
  
```  
EXIT ( < query > )  
```  
  
 <span data-ttu-id="966eb-294">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="966eb-294">For example:</span></span>  
  
```  
EXIT(SELECT @@ROWCOUNT)  
```  
  
 <span data-ttu-id="966eb-295">バッチ ファイルの一部として、EXIT パラメーターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="966eb-295">You can also include the EXIT parameter as part of a batch file.</span></span> <span data-ttu-id="966eb-296">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="966eb-296">For example:</span></span>  
  
```  
osql -E -Q "EXIT(SELECT COUNT(*) FROM '%1')"  
```  
  
 <span data-ttu-id="966eb-297">**osql** ユーティリティでは、かっこ **()** 内のすべての情報が、入力されたとおりにサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-297">The **osql** utility passes everything between the parentheses **()** to the server exactly as entered.</span></span> <span data-ttu-id="966eb-298">システム ストアド プロシージャが値セットを選択し、値を返す場合、選択した値だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-298">If a stored system procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="966eb-299">かっこ内に何も指定せずに EXIT **()** ステートメントを指定すると、バッチ内のそのステートメントよりも前にあるものすべてを実行し、戻り値を返さずに終了します。</span><span class="sxs-lookup"><span data-stu-id="966eb-299">The EXIT **()** statement with nothing between the parentheses executes everything preceding it in the batch and then exits with no return value.</span></span>  
  
 <span data-ttu-id="966eb-300">EXIT には、次の 4 つの形式があります。</span><span class="sxs-lookup"><span data-stu-id="966eb-300">There are four EXIT formats:</span></span>  
  
-   <span data-ttu-id="966eb-301">EXIT</span><span class="sxs-lookup"><span data-stu-id="966eb-301">EXIT</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-302">バッチを実行せずに直ちに終了し、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="966eb-302">Does not execute the batch; quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="966eb-303">EXIT **()**</span><span class="sxs-lookup"><span data-stu-id="966eb-303">EXIT **()**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-304">バッチを実行してから終了し、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="966eb-304">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="966eb-305">EXIT **( *`query`* )**</span><span class="sxs-lookup"><span data-stu-id="966eb-305">EXIT **(*`query`*)**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-306">クエリを含むバッチを実行し、クエリの結果を返して終了します。</span><span class="sxs-lookup"><span data-stu-id="966eb-306">Executes the batch, including the query, and then quits after returning the results of the query.</span></span>  
  
-   <span data-ttu-id="966eb-307">状態 127 の RAISERROR ステートメント</span><span class="sxs-lookup"><span data-stu-id="966eb-307">RAISERROR with a state of 127</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="966eb-308">RAISERROR を **osql** スクリプトの中で使用し、状態 127 が発生すると、 **osql** は終了し、メッセージ ID がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-308">If RAISERROR is used within an **osql** script and a state of 127 is raised, **osql** will quit and return the message ID back to the client.</span></span> <span data-ttu-id="966eb-309">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="966eb-309">For example:</span></span>  
  
```  
RAISERROR(50001, 10, 127)  
```  
  
 <span data-ttu-id="966eb-310">このエラーが発生すると、 **osql** スクリプトが終了し、メッセージ ID 50001 がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-310">This error will cause the **osql** script to end and the message ID 50001 will be returned to the client.</span></span>  
  
 <span data-ttu-id="966eb-311">戻り値 -1 ～ -99 は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]によって予約済みです。 **osql** では次のような値を定義しています。</span><span class="sxs-lookup"><span data-stu-id="966eb-311">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; **osql** defines these values:</span></span>  
  
-   <span data-ttu-id="966eb-312">-100</span><span class="sxs-lookup"><span data-stu-id="966eb-312">-100</span></span>  
  
     <span data-ttu-id="966eb-313">戻り値を選択する前に、エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="966eb-313">Error encountered prior to selecting return value.</span></span>  
  
-   <span data-ttu-id="966eb-314">-101</span><span class="sxs-lookup"><span data-stu-id="966eb-314">-101</span></span>  
  
     <span data-ttu-id="966eb-315">戻り値を選択するときに、行が見つからなかった。</span><span class="sxs-lookup"><span data-stu-id="966eb-315">No rows found when selecting return value.</span></span>  
  
-   <span data-ttu-id="966eb-316">-102</span><span class="sxs-lookup"><span data-stu-id="966eb-316">-102</span></span>  
  
     <span data-ttu-id="966eb-317">戻り値を選択するときに、変換エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="966eb-317">Conversion error occurred when selecting return value.</span></span>  
  
## <a name="displaying-money-and-smallmoney-data-types"></a><span data-ttu-id="966eb-318">money (金額) と smallmoney (短精度金額) のデータ型の表示</span><span class="sxs-lookup"><span data-stu-id="966eb-318">Displaying money and smallmoney Data Types</span></span>  
 <span data-ttu-id="966eb-319">**osql**では、データ型とデータ型が小数点以下2桁で表示されますが、では `money` `smallmoney` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 内部的に小数点以下4桁の値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="966eb-319">**osql** displays the `money` and `smallmoney` data types with two decimal places although [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the value internally with four decimal places.</span></span> <span data-ttu-id="966eb-320">次の例の結果を参照してください。</span><span class="sxs-lookup"><span data-stu-id="966eb-320">Consider the example:</span></span>  
  
```  
SELECT CAST(CAST(10.3496 AS money) AS decimal(6, 4))  
GO  
```  
  
 <span data-ttu-id="966eb-321">このステートメントの実行結果は `10.3496`で、小数点以下のすべての桁をそのままにして値を格納することを示しています。</span><span class="sxs-lookup"><span data-stu-id="966eb-321">This statement produces a result of `10.3496`, which indicates that the value is stored with all decimal places intact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966eb-322">参照</span><span class="sxs-lookup"><span data-stu-id="966eb-322">See Also</span></span>  
 <span data-ttu-id="966eb-323">[コメント &#40;MDX&#41;](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="966eb-323">[Comment &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="966eb-324">[-- &#40;コメント&#41; &#40;MDX&#41;](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="966eb-324">[-- &#40;Comment&#41; &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="966eb-325">[CAST および CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="966eb-325">[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span></span>  
 [<span data-ttu-id="966eb-326">RAISERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="966eb-326">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
