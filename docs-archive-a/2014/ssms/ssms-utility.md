---
title: Ssms ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0cfc9469e49e6ce3839d02a61477b8957fbc13e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644775"
---
# <a name="ssms-utility"></a><span data-ttu-id="32ef8-102">Ssms ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="32ef8-102">Ssms Utility</span></span>
  <span data-ttu-id="32ef8-103">**Ssms**ユーティリティが [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-103">The **Ssms**utility opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="32ef8-104">指定すると、 **Ssms** はサーバーへの接続を確立し、クエリ、スクリプト、ファイル、プロジェクト、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-104">If specified, **Ssms** also establishes a connection to a server, and opens queries, scripts, files, projects, and solutions.</span></span>  
  
 <span data-ttu-id="32ef8-105">クエリ、プロジェクト、またはソリューションを含んだファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-105">You can specify files that contain queries, projects, or solutions.</span></span> <span data-ttu-id="32ef8-106">接続情報が指定され、ファイルの種類とサーバーの種類が対応している場合、クエリを含んだファイルは自動的にサーバーに接続されます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-106">Files that contain queries are automatically connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="32ef8-107">たとえば、.sql ファイルならば、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の SQL クエリ エディター ウィンドウが開き、.mdx ファイルならば [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の MDX クエリ エディター ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-107">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="32ef8-108">**SQL Server のソリューションと SQL Server のプロジェクト** は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-108">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32ef8-109">**Ssms** ユーティリティはクエリを実行しません。</span><span class="sxs-lookup"><span data-stu-id="32ef8-109">The **Ssms** utility does not run queries.</span></span> <span data-ttu-id="32ef8-110">コマンド ラインからクエリを実行するには、 **sqlcmd** ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-110">To run queries from the command line, use the **sqlcmd** utility.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ef8-111">構文</span><span class="sxs-lookup"><span data-stu-id="32ef8-111">Syntax</span></span>  
  
```  
  
      Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-Sservername] [-ddatabasename] [-Uusername] [-Ppassword]   
    [-E] [-nosplash] [-log[filename]?] [-?]  
```  
  
## <a name="arguments"></a><span data-ttu-id="32ef8-112">引数</span><span class="sxs-lookup"><span data-stu-id="32ef8-112">Arguments</span></span>  
 <span data-ttu-id="32ef8-113">*scriptfile*</span><span class="sxs-lookup"><span data-stu-id="32ef8-113">*scriptfile*</span></span>  
 <span data-ttu-id="32ef8-114">開くスクリプト ファイルを 1 つ以上指定します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-114">Specifies one or more script files to open.</span></span> <span data-ttu-id="32ef8-115">パラメーターには、ファイルへの完全パスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ef8-115">The parameter must contain the full path to the files.</span></span>  
  
 <span data-ttu-id="32ef8-116">*projectfile*</span><span class="sxs-lookup"><span data-stu-id="32ef8-116">*projectfile*</span></span>  
 <span data-ttu-id="32ef8-117">開くスクリプトのプロジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-117">Specifies a script project to open.</span></span> <span data-ttu-id="32ef8-118">パラメーターには、スクリプト プロジェクト ファイルへの完全パスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ef8-118">The parameter must contain the full path to the script project file.</span></span>  
  
 <span data-ttu-id="32ef8-119">*solutionfile*</span><span class="sxs-lookup"><span data-stu-id="32ef8-119">*solutionfile*</span></span>  
 <span data-ttu-id="32ef8-120">開くソリューションを指定します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-120">Specifies a solution to open.</span></span> <span data-ttu-id="32ef8-121">パラメーターには、ソリューション ファイルへの完全パスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ef8-121">The parameter must contain the full path to the solution file.</span></span>  
  
 <span data-ttu-id="32ef8-122">[**-S** _servername_]</span><span class="sxs-lookup"><span data-stu-id="32ef8-122">[**-S** _servername_]</span></span>  
 <span data-ttu-id="32ef8-123">サーバー名</span><span class="sxs-lookup"><span data-stu-id="32ef8-123">Server name</span></span>  
  
 <span data-ttu-id="32ef8-124">[**-d** _databasename_]</span><span class="sxs-lookup"><span data-stu-id="32ef8-124">[**-d** _databasename_]</span></span>  
 <span data-ttu-id="32ef8-125">データベース名</span><span class="sxs-lookup"><span data-stu-id="32ef8-125">Database name</span></span>  
  
 <span data-ttu-id="32ef8-126">[**-U** _username_]</span><span class="sxs-lookup"><span data-stu-id="32ef8-126">[**-U** _username_]</span></span>  
 <span data-ttu-id="32ef8-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用して接続するときのユーザー名です。</span><span class="sxs-lookup"><span data-stu-id="32ef8-127">User name when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="32ef8-128">[**-P** _パスワード_]</span><span class="sxs-lookup"><span data-stu-id="32ef8-128">[**-P** _password_]</span></span>  
 <span data-ttu-id="32ef8-129">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用して接続するときのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="32ef8-129">Password when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="32ef8-130">[**-E**]</span><span class="sxs-lookup"><span data-stu-id="32ef8-130">[**-E**]</span></span>  
 <span data-ttu-id="32ef8-131">Windows 認証を使用した接続</span><span class="sxs-lookup"><span data-stu-id="32ef8-131">Connect using Windows Authentication</span></span>  
  
 <span data-ttu-id="32ef8-132">[**-nosplash**]</span><span class="sxs-lookup"><span data-stu-id="32ef8-132">[**-nosplash**]</span></span>  
 <span data-ttu-id="32ef8-133">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開くとき、スプラッシュ スクリーンのグラフィックを表示しません。</span><span class="sxs-lookup"><span data-stu-id="32ef8-133">Prevents [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from displaying the splash screen graphic while opening.</span></span> <span data-ttu-id="32ef8-134">限られた帯域幅を使用した接続では、ターミナル サービスを使用して [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を起動しているコンピューターへ接続する場合に、このオプションを使用してください。</span><span class="sxs-lookup"><span data-stu-id="32ef8-134">Use this option when connecting to the computer running [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by means of Terminal Services over a connection with a limited bandwidth.</span></span> <span data-ttu-id="32ef8-135">この引数では、大文字と小文字は区別されず、他の引数の前後どちらにも指定できます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-135">This argument is not case-sensitive and may appear before or after other arguments</span></span>  
  
 <span data-ttu-id="32ef8-136">[**-ログ**_[ファイル名]?_]</span><span class="sxs-lookup"><span data-stu-id="32ef8-136">[**-log**_[filename]?_]</span></span>  
 <span data-ttu-id="32ef8-137">トラブルシューティング用に指定したファイルに [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のアクティビティを記録します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-137">Logs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] activity to the specified file for troubleshooting</span></span>  
  
 <span data-ttu-id="32ef8-138">[**-?**]</span><span class="sxs-lookup"><span data-stu-id="32ef8-138">[**-?**]</span></span>  
 <span data-ttu-id="32ef8-139">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-139">Displays command line help</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ef8-140">解説</span><span class="sxs-lookup"><span data-stu-id="32ef8-140">Remarks</span></span>  
 <span data-ttu-id="32ef8-141">すべてのスイッチは省略可能で、コンマで区切られるファイル以外は、空白で区切られます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-141">All of the switches are optional and separated by a space except files which are separated by commas.</span></span> <span data-ttu-id="32ef8-142">スイッチを指定していない場合、 **Ssms** は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [ツール] **メニューの** [オプション] **設定で指定されているとおりに** を開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-142">If you do not specify any switches, **Ssms** opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as specified in the **Options** settings on the **Tools** menu.</span></span> <span data-ttu-id="32ef8-143">たとえば、 **[環境/全般]** の **[スタートアップ時]** オプションで、 **[新しいクエリ ウィンドウを開く]** を指定すると、 **Ssms** は空白のクエリ エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-143">For example, if the **Environment/General** page **At startup** option specifies **Open new query window**, **Ssms** will open with a blank Query Editor.</span></span>  
  
 <span data-ttu-id="32ef8-144">**-log** スイッチは、他のすべてのスイッチの後の、コマンド ラインの末尾に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ef8-144">The **-log** switch must appear at the end of the command line, after all other switches.</span></span> <span data-ttu-id="32ef8-145">ファイル名引数は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ef8-145">The filename argument is optional.</span></span> <span data-ttu-id="32ef8-146">ファイル名が指定され、そのファイルが存在しない場合は、ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-146">If a filename is specified, and the file does not exist, the file is created.</span></span> <span data-ttu-id="32ef8-147">ファイルを作成できない場合 (書き込みアクセスが不十分な場合など)、ログはローカライズされていない APPDATA の場所 (下記を参照) に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-147">If the file cannot be created - for example, due to insufficient write access, the log is written to the nonlocalized APPDATA location instead (See below).</span></span> <span data-ttu-id="32ef8-148">ファイル名引数を指定しない場合、2 つのファイルは、現在のユーザーのローカライズされていないアプリケーション データ フォルダーに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-148">If the filename argument is not specified, two files are written to the current user's nonlocalized application data folder.</span></span> <span data-ttu-id="32ef8-149">SQL Server のローカライズされていないアプリケーション データ フォルダーは APPDATA 環境変数から確認できます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-149">The nonlocalized application data folder for SQL Server can be found from the APPDATA environment variable.</span></span> <span data-ttu-id="32ef8-150">たとえば、SQL Server 2012 の場合、フォルダーは \<system drive> \ Users \\<username \> \appdata\roaming\microsoft\appenv\10.0 ですとなり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-150">For example, for SQL Server 2012, the folder is \<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\\.</span></span> <span data-ttu-id="32ef8-151">2 つのファイルは、既定では ActivityLog.xml および ActivityLog.xsl という名前になります。</span><span class="sxs-lookup"><span data-stu-id="32ef8-151">The two files are, by default, named ActivityLog.xml and ActivityLog.xsl.</span></span> <span data-ttu-id="32ef8-152">ActivityLog.xml にはアクティビティ ログ データが含まれ、ActivityLog.xsl は XML スタイル シートで、XML ファイルを簡単に表示できます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-152">The former contains the activity log data and the latter is an XML style sheet which provides a more convenient way to view the XML file.</span></span> <span data-ttu-id="32ef8-153">Internet Explorer などの既定の XML ビューアーでログファイルを表示するには、次の手順に従います。 [スタート] ボタンをクリックし、[ファイル名を指定して実行] をクリックします。次に、表示 \<system drive> されたフィールドに「: \ Users \\<ユーザー名 \>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-153">Use the following steps to view the log file in your default XML viewer, like Internet Explorer:  Click Start, then click Run...", then type "\<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml" into the field provided, and then press Enter.</span></span>  
  
 <span data-ttu-id="32ef8-154">接続情報が指定され、ファイルの種類とサーバーの種類が対応している場合、クエリを含んだファイルはサーバーへの接続を要求します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-154">Files that contain queries will prompt to be connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="32ef8-155">たとえば、.sql ファイルならば、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の SQL クエリ エディター ウィンドウが開き、.mdx ファイルならば [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の MDX クエリ エディター ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-155">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="32ef8-156">**SQL Server のソリューションと SQL Server のプロジェクト** は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-156">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="32ef8-157">次の表では、ファイルの拡張子に対応するサーバーの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="32ef8-157">The following table maps server types to file extensions.</span></span>  
  
|<span data-ttu-id="32ef8-158">サーバーの種類</span><span class="sxs-lookup"><span data-stu-id="32ef8-158">Server type</span></span>|<span data-ttu-id="32ef8-159">拡張子</span><span class="sxs-lookup"><span data-stu-id="32ef8-159">Extension</span></span>|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|<span data-ttu-id="32ef8-160">.sql</span><span class="sxs-lookup"><span data-stu-id="32ef8-160">.sql</span></span>|  
|<span data-ttu-id="32ef8-161">SQL Server Analysis Services</span><span class="sxs-lookup"><span data-stu-id="32ef8-161">SQL Server Analysis Services</span></span>|<span data-ttu-id="32ef8-162">.mdx</span><span class="sxs-lookup"><span data-stu-id="32ef8-162">.mdx</span></span><br /><br /> <span data-ttu-id="32ef8-163">.xmla</span><span class="sxs-lookup"><span data-stu-id="32ef8-163">.xmla</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="32ef8-164">例</span><span class="sxs-lookup"><span data-stu-id="32ef8-164">Examples</span></span>  
 <span data-ttu-id="32ef8-165">次のスクリプトは、既定の設定でコマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-165">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt with the default settings:</span></span>  
  
```  
Ssms  
  
```  
  
 <span data-ttu-id="32ef8-166">次のスクリプトは、コマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開きます。接続には Windows 認証を使用し、サーバー `ACCTG and the database AdventureWorks2012,` に対して設定されているコード エディターを使用します。また、スプラッシュ スクリーンは表示されません。</span><span class="sxs-lookup"><span data-stu-id="32ef8-166">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, with Windows Authentication, with the Code Editor set to the server `ACCTG and the database AdventureWorks2012,` without showing the splash screen:</span></span>  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 <span data-ttu-id="32ef8-167">次のスクリプトは、コマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、MonthEndQuery スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-167">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthEndQuery script.</span></span>  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 <span data-ttu-id="32ef8-168">次のスクリプトは、コマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 `developer`という名前のコンピューター上にある NewReportsProject プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-168">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the NewReportsProject project on the computer named `developer`:</span></span>  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 <span data-ttu-id="32ef8-169">次のスクリプトは、コマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、MonthlyReports ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="32ef8-169">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthlyReports solution:</span></span>  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="32ef8-170">参照</span><span class="sxs-lookup"><span data-stu-id="32ef8-170">See Also</span></span>  
 <span data-ttu-id="32ef8-171">[SQL Server Management Studio の使用 [SQL Server]](../database-engine/use-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="32ef8-171">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)</span></span>  
  
  
