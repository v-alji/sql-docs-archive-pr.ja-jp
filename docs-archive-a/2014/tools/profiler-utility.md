---
title: プロファイラーユーティリティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], profiler90 utility
- profiler90 utility
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: e91c30a9-0d29-4f84-bcb8-e8fb62afadda
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8df3e8557bb52839d17291bae0c5ba507d0a671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711290"
---
# <a name="profiler-utility"></a><span data-ttu-id="b0a42-102">profiler ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="b0a42-102">Profiler Utility</span></span>
  <span data-ttu-id="b0a42-103">**profiler** ユーティリティにより [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] ツールが起動されます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-103">The **profiler** utility launches the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tool.</span></span> <span data-ttu-id="b0a42-104">このトピックの後半で説明する省略可能な引数を使用して、アプリケーションの起動を制御できます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-104">The optional arguments listed later in this topic allow you to control how the application starts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0a42-105">**profiler** ユーティリティは、トレースのスクリプティングを目的とするものではありません。</span><span class="sxs-lookup"><span data-stu-id="b0a42-105">The **profiler** utility is not intended for scripting traces.</span></span> <span data-ttu-id="b0a42-106">詳細については、「 [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0a42-106">For more information, see [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a42-107">構文</span><span class="sxs-lookup"><span data-stu-id="b0a42-107">Syntax</span></span>  
  
```  
  
      profiler  
          [ /? ] |  
[  
{  
{ /U login_id [ /P password ] }  
| /E  
}  
{[ /S sql_server_name ] | [ /A analysis_services_server_name ] }  
[ /D database ]  
[ /T "template_name" ]  
[ /B { "trace_table_name" } ]  
{ [/F "filename" ] | [ /O "filename" ] }  
[ /L locale_ID ]  
[ /M "MM-DD-YY hh:mm:ss" ]  
[ /R ]  
[ /Z file_size ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0a42-108">引数</span><span class="sxs-lookup"><span data-stu-id="b0a42-108">Arguments</span></span>  
 <span data-ttu-id="b0a42-109">**/?**</span><span class="sxs-lookup"><span data-stu-id="b0a42-109">**/?**</span></span>  
 <span data-ttu-id="b0a42-110">**profiler** の引数に関する構文の概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-110">Displays the syntax summary of **profiler** arguments.</span></span>  
  
 <span data-ttu-id="b0a42-111">**/U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="b0a42-111">**/U** *login_id*</span></span>  
 <span data-ttu-id="b0a42-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証に使用するユーザー ログイン ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-112">Is the user login ID for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="b0a42-113">ログイン ID では大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-113">Login IDs are case sensitive.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]<span data-ttu-id="b0a42-114">.</span><span class="sxs-lookup"><span data-stu-id="b0a42-114">.</span></span>  
  
 <span data-ttu-id="b0a42-115">**/P** *password*</span><span class="sxs-lookup"><span data-stu-id="b0a42-115">**/P** *password*</span></span>  
 <span data-ttu-id="b0a42-116">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で必要なユーザーのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-116">Specifies a user-specified password for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="b0a42-117">**/E**</span><span class="sxs-lookup"><span data-stu-id="b0a42-117">**/E**</span></span>  
 <span data-ttu-id="b0a42-118">現在のユーザーの資格情報に基づいて、Windows 認証による接続を行います。</span><span class="sxs-lookup"><span data-stu-id="b0a42-118">Specifies connecting with Windows Authentication with the current user's credentials.</span></span>  
  
 <span data-ttu-id="b0a42-119">**/S**  *sql_server_name*</span><span class="sxs-lookup"><span data-stu-id="b0a42-119">**/S**  *sql_server_name*</span></span>  
 <span data-ttu-id="b0a42-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-120">Specifies an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b0a42-121">**/U** スイッチと **/P** スイッチ、または **/E** スイッチで指定した認証情報を使用して、Profiler は指定されたサーバーに自動的に接続します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-121">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="b0a42-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の名前付きインスタンスに接続するには、 **/S** *sql_server_name*\\*instance_name* を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-122">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use **/S** *sql_server_name*\\*instance_name*.</span></span>  
  
 <span data-ttu-id="b0a42-123">**/A**  *analysis_services_server_name*</span><span class="sxs-lookup"><span data-stu-id="b0a42-123">**/A**  *analysis_services_server_name*</span></span>  
 <span data-ttu-id="b0a42-124">Analysis Services のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-124">Specifies an instance of Analysis Services.</span></span> <span data-ttu-id="b0a42-125">**/U** スイッチと **/P** スイッチ、または **/E** スイッチで指定した認証情報を使用して、Profiler は指定されたサーバーに自動的に接続します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-125">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="b0a42-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の名前付きインスタンスに接続するには、 **/A** *analysis_services_server_name\instance_name* を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-126">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] use **/A** *analysis_services_server_name\instance_name*.</span></span>  
  
 <span data-ttu-id="b0a42-127">**/D** *database*</span><span class="sxs-lookup"><span data-stu-id="b0a42-127">**/D** *database*</span></span>  
 <span data-ttu-id="b0a42-128">接続に使用するデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-128">Specifies the name of the database to be used with the connection.</span></span> <span data-ttu-id="b0a42-129">データベースを指定しないと、指定したユーザーに対して既定のデータベースが選択されます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-129">This option will select the default database for the specified user if no database is specified.</span></span>  
  
 <span data-ttu-id="b0a42-130">**/B "** *trace_table_name* **"**</span><span class="sxs-lookup"><span data-stu-id="b0a42-130">**/B "** *trace_table_name* **"**</span></span>  
 <span data-ttu-id="b0a42-131">Profiler を起動するときに読み込むトレース テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-131">Specifies a trace table to load when the profiler is launched.</span></span> <span data-ttu-id="b0a42-132">データベース、ユーザーやスキーマ、およびテーブルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-132">You must specify the database, the user or schema, and the table.</span></span>  
  
 <span data-ttu-id="b0a42-133">**/T"** *template_name* **"**</span><span class="sxs-lookup"><span data-stu-id="b0a42-133">**/T"** *template_name* **"**</span></span>  
 <span data-ttu-id="b0a42-134">トレースを構成するために読み込まれるテンプレートを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-134">Specifies the template that will be loaded to configure the trace.</span></span> <span data-ttu-id="b0a42-135">テンプレート名は引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-135">The template name must be in quotes.</span></span> <span data-ttu-id="b0a42-136">テンプレートは、システム テンプレート ディレクトリまたはユーザー テンプレート ディレクトリに格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-136">The template name must be in either the system template directory or the user template directory.</span></span> <span data-ttu-id="b0a42-137">同じ名前のテンプレートが両方のディレクトリにある場合は、システム ディレクトリのテンプレートが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-137">If two templates with the same name exist in both directories, the template from the system directory will be loaded.</span></span> <span data-ttu-id="b0a42-138">指定した名前のテンプレートが存在しない場合は、標準テンプレートが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-138">If no template with the specified name exists, the standard template will be loaded.</span></span> <span data-ttu-id="b0a42-139">テンプレートのファイル拡張子 (.tdf) は、 *template_name*の一部として指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="b0a42-139">Note that the file extension for the template (.tdf) should not be specified as part of the *template_name*.</span></span> <span data-ttu-id="b0a42-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-140">For example:</span></span>  
  
```  
/T "standard"  
```  
  
 <span data-ttu-id="b0a42-141">**/F"** *filename* **"**</span><span class="sxs-lookup"><span data-stu-id="b0a42-141">**/F"** *filename* **"**</span></span>  
 <span data-ttu-id="b0a42-142">Profiler を起動するときに読み込むトレース ファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-142">Specifies the path and filename of a trace file to load when profiler is launched.</span></span> <span data-ttu-id="b0a42-143">パスとファイル名はすべて引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-143">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="b0a42-144">このオプションを **/O**と同時に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b0a42-144">This option cannot be used with **/O**.</span></span>  
  
 <span data-ttu-id="b0a42-145">**/O "** *filename*  **"**</span><span class="sxs-lookup"><span data-stu-id="b0a42-145">**/O "** *filename*  **"**</span></span>  
 <span data-ttu-id="b0a42-146">トレース結果を書き込むファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-146">Specifies the path and filename of a file to which trace results should be written.</span></span> <span data-ttu-id="b0a42-147">パスとファイル名はすべて引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-147">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="b0a42-148">このオプションを **/F**と同時に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b0a42-148">This option cannot be used with **/F.**</span></span>  
  
 <span data-ttu-id="b0a42-149">**/L** *locale_ID*</span><span class="sxs-lookup"><span data-stu-id="b0a42-149">**/L** *locale_ID*</span></span>  
 <span data-ttu-id="b0a42-150">使用できません。</span><span class="sxs-lookup"><span data-stu-id="b0a42-150">Not available.</span></span>  
  
 <span data-ttu-id="b0a42-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span><span class="sxs-lookup"><span data-stu-id="b0a42-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span></span>  
 <span data-ttu-id="b0a42-152">トレースが停止する日と時刻を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-152">Specifies the date and time for the trace to stop.</span></span> <span data-ttu-id="b0a42-153">停止時刻は引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-153">The stop time must be in quotes.</span></span> <span data-ttu-id="b0a42-154">次の表に示すパラメーターに従って停止時刻を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-154">Specify the stop time according to the parameters in the table below:</span></span>  
  
|<span data-ttu-id="b0a42-155">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0a42-155">Parameter</span></span>|<span data-ttu-id="b0a42-156">定義</span><span class="sxs-lookup"><span data-stu-id="b0a42-156">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="b0a42-157">mm</span><span class="sxs-lookup"><span data-stu-id="b0a42-157">MM</span></span>|<span data-ttu-id="b0a42-158">月を表す 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-158">Two-digit month</span></span>|  
|<span data-ttu-id="b0a42-159">DD</span><span class="sxs-lookup"><span data-stu-id="b0a42-159">DD</span></span>|<span data-ttu-id="b0a42-160">日を表す 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-160">Two-digit day</span></span>|  
|<span data-ttu-id="b0a42-161">YY</span><span class="sxs-lookup"><span data-stu-id="b0a42-161">YY</span></span>|<span data-ttu-id="b0a42-162">年を表す 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-162">Two-digit year</span></span>|  
|<span data-ttu-id="b0a42-163">hh</span><span class="sxs-lookup"><span data-stu-id="b0a42-163">hh</span></span>|<span data-ttu-id="b0a42-164">時刻を表す 24 時間形式の 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-164">Two-digit hour on a 24-hour clock</span></span>|  
|<span data-ttu-id="b0a42-165">mm</span><span class="sxs-lookup"><span data-stu-id="b0a42-165">mm</span></span>|<span data-ttu-id="b0a42-166">分を表す 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-166">Two-digit minute</span></span>|  
|<span data-ttu-id="b0a42-167">ss</span><span class="sxs-lookup"><span data-stu-id="b0a42-167">ss</span></span>|<span data-ttu-id="b0a42-168">秒を表す 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-168">Two-digit second</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b0a42-169">"MM-DD-YY hh:mm:ss" 形式は、 **で** [日時の値の表示に地域別設定を使用する] [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]オプションが有効になっている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-169">The "MM-DD-YY hh:mm:ss" format can only be used if the **Use regional settings to display date and time values** option is enabled in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="b0a42-170">このオプションが無効になっている場合は、"YYYY-MM-DD hh:mm:ss" の日付/時刻形式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a42-170">If this option is not enabled, you must use the "YYYY-MM-DD hh:mm:ss" date and time format.</span></span>  
  
 <span data-ttu-id="b0a42-171">**/R**</span><span class="sxs-lookup"><span data-stu-id="b0a42-171">**/R**</span></span>  
 <span data-ttu-id="b0a42-172">トレース ファイルのロールオーバーを可能にします。</span><span class="sxs-lookup"><span data-stu-id="b0a42-172">Enables trace file rollover.</span></span>  
  
 <span data-ttu-id="b0a42-173">**/Z**  *file_size*</span><span class="sxs-lookup"><span data-stu-id="b0a42-173">**/Z**  *file_size*</span></span>  
 <span data-ttu-id="b0a42-174">トレース ファイルのサイズをメガバイト (MB) 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-174">Specifies the size of the trace file in megabytes (MB).</span></span> <span data-ttu-id="b0a42-175">既定値は 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="b0a42-175">The default size is 5 MB.</span></span> <span data-ttu-id="b0a42-176">ロールオーバーが可能な場合は、すべてのロールオーバー ファイルはこの引数で指定した値に制限されます。</span><span class="sxs-lookup"><span data-stu-id="b0a42-176">If rollover is enabled, all rollover files will be limited to the value specified in this argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0a42-177">解説</span><span class="sxs-lookup"><span data-stu-id="b0a42-177">Remarks</span></span>  
 <span data-ttu-id="b0a42-178">特定のテンプレートでトレースを開始する場合は、 **/S** オプションと **/T** オプションを同時に使用します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-178">To start a trace with a specific template, use the **/S** and **/T** options together.</span></span> <span data-ttu-id="b0a42-179">たとえば、MyServer\MyInstance で Standard テンプレートを使用してトレースを開始する場合は、コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="b0a42-179">For example, to start a trace using the Standard template on MyServer\MyInstance, enter the following at the command prompt:</span></span>  
  
```  
profiler /S MyServer\MyInstance /T "Standard"  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0a42-180">参照</span><span class="sxs-lookup"><span data-stu-id="b0a42-180">See Also</span></span>  
 [<span data-ttu-id="b0a42-181">コマンド プロンプト ユーティリティ リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="b0a42-181">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
