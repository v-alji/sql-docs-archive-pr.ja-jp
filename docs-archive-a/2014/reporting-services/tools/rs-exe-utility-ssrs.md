---
title: RS.exe ユーティリティ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf21a1bf2453d2bd1f0644e31ca46f3f94e6884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721026"
---
# <a name="rsexe-utility-ssrs"></a><span data-ttu-id="30187-102">RS.exe Utility (SSRS)</span><span class="sxs-lookup"><span data-stu-id="30187-102">RS.exe Utility (SSRS)</span></span>
  <span data-ttu-id="30187-103">rs.exe ユーティリティは入力ファイル内に指定したスクリプトを処理します。</span><span class="sxs-lookup"><span data-stu-id="30187-103">The rs.exe utility processes script that you provide in an input file.</span></span> <span data-ttu-id="30187-104">このユーティリティを使用して、レポート サーバーの配置と管理タスクを自動化します。</span><span class="sxs-lookup"><span data-stu-id="30187-104">Use this utility to automate report server deployment and administration tasks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30187-105">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、 **rs** ユーティリティは、SharePoint 統合モード用に構成されているレポート サーバー、およびネイティブ モードで構成されているレポート サーバーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="30187-105">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], the **rs** utility is supported against report servers that are configured for SharePoint integrated mode as well as servers configured in native mode.</span></span> <span data-ttu-id="30187-106">以前のバージョンでは、ネイティブ モードの構成のみがサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="30187-106">Previous versions only supported native mode configurations.</span></span>  
  
 <span data-ttu-id="30187-107">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="30187-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="30187-108">ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="30187-108">File Location</span></span>](#bkmk_filelocation)  
  
-   [<span data-ttu-id="30187-109">引数</span><span class="sxs-lookup"><span data-stu-id="30187-109">Arguments</span></span>](#bkmk_arguments)  
  
-   [<span data-ttu-id="30187-110">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="30187-110">Permissions</span></span>](#bkmk_permissions)  
  
-   [<span data-ttu-id="30187-111">使用例</span><span class="sxs-lookup"><span data-stu-id="30187-111">Examples</span></span>](#bkmk_examples)  
  
## <a name="syntax"></a><span data-ttu-id="30187-112">構文</span><span class="sxs-lookup"><span data-stu-id="30187-112">Syntax</span></span>  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="file-location"></a><a name="bkmk_filelocation"></a> <span data-ttu-id="30187-113">ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="30187-113">File Location</span></span>  
 <span data-ttu-id="30187-114">**RS.exe** は **\Program Files\Microsoft SQL Server\110\Tools\Binn**にあります。</span><span class="sxs-lookup"><span data-stu-id="30187-114">**RS.exe** is located at **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="30187-115">このユーティリティは、ファイル システム上の任意のフォルダーから実行できます。</span><span class="sxs-lookup"><span data-stu-id="30187-115">You can run the utility from any folder on your file system.</span></span>  
  
##  <a name="arguments"></a><a name="bkmk_arguments"></a> <span data-ttu-id="30187-116">引数</span><span class="sxs-lookup"><span data-stu-id="30187-116">Arguments</span></span>  
 <span data-ttu-id="30187-117">**-?**</span><span class="sxs-lookup"><span data-stu-id="30187-117">**-?**</span></span>  
 <span data-ttu-id="30187-118">(省略可) **rs** の引数の構文を表示します。</span><span class="sxs-lookup"><span data-stu-id="30187-118">(Optional) Displays the syntax of **rs** arguments.</span></span>  
  
 <span data-ttu-id="30187-119">`-i`*input_file*</span><span class="sxs-lookup"><span data-stu-id="30187-119">`-i` *input_file*</span></span>  
 <span data-ttu-id="30187-120">(必須) 実行する .rss ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-120">(Required) Specifies the .rss file to execute.</span></span> <span data-ttu-id="30187-121">この値は、.rss ファイルへの相対パスまたは完全修飾パスになります。</span><span class="sxs-lookup"><span data-stu-id="30187-121">This value can be a relative or fully qualified path to the .rss file.</span></span>  
  
 <span data-ttu-id="30187-122">`-s`*serverURL*</span><span class="sxs-lookup"><span data-stu-id="30187-122">`-s` *serverURL*</span></span>  
 <span data-ttu-id="30187-123">(必須) Web サーバー名とレポート サーバーの仮想ディレクトリ名を指定して、対象ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="30187-123">(Required) Specifies the Web server name and report server virtual directory name to execute the file against.</span></span> <span data-ttu-id="30187-124">レポート サーバーの URL は、 `http://examplewebserver/reportserver`のように指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-124">An example of a report server URL is `http://examplewebserver/reportserver`.</span></span> <span data-ttu-id="30187-125">サーバー名の先頭のプレフィックス http:// または https:// は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="30187-125">The prefix http:// or https:// at the beginning of the server name is optional.</span></span> <span data-ttu-id="30187-126">プレフィックスを省略した場合、レポート サーバーのスクリプト ホストは、まず https の使用を試み、https が使用できない場合は、http を使用します。</span><span class="sxs-lookup"><span data-stu-id="30187-126">If you omit the prefix, the report server script host tries to use https first, and then uses http if https does not work.</span></span>  
  
 <span data-ttu-id="30187-127">`-u`[*ドメイン* \\ ]*ユーザー名*</span><span class="sxs-lookup"><span data-stu-id="30187-127">`-u` [*domain*\\]*username*</span></span>  
 <span data-ttu-id="30187-128">(省略可) レポート サーバーへの接続に使用するユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-128">(Optional) Specifies a user account used to connect to the report server.</span></span> <span data-ttu-id="30187-129">`-u` および `-p` を省略した場合、現在の Windows ユーザー アカウントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="30187-129">If `-u` and `-p` are omitted, the current Windows user account is used.</span></span>  
  
 <span data-ttu-id="30187-130">`-p` *password*</span><span class="sxs-lookup"><span data-stu-id="30187-130">`-p` *password*</span></span>  
 <span data-ttu-id="30187-131">(`-u` を指定した場合は必須) `-u` 引数で使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-131">(Required if `-u` is specified) Specifies the password to use with the `-u` argument.</span></span> <span data-ttu-id="30187-132">この値は、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="30187-132">This value is case-sensitive.</span></span>  
  
 `-e`  
 <span data-ttu-id="30187-133">(省略可) スクリプトを実行する SOAP エンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-133">(Optional) Specifies the SOAP endpoint against which the script should run.</span></span> <span data-ttu-id="30187-134">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="30187-134">Valid values are the following:</span></span>  
  
-   <span data-ttu-id="30187-135">Mgmt2010</span><span class="sxs-lookup"><span data-stu-id="30187-135">Mgmt2010</span></span>  
  
-   <span data-ttu-id="30187-136">Mgmt2006</span><span class="sxs-lookup"><span data-stu-id="30187-136">Mgmt2006</span></span>  
  
-   <span data-ttu-id="30187-137">Mgmt2005</span><span class="sxs-lookup"><span data-stu-id="30187-137">Mgmt2005</span></span>  
  
-   <span data-ttu-id="30187-138">Exec2005</span><span class="sxs-lookup"><span data-stu-id="30187-138">Exec2005</span></span>  
  
 <span data-ttu-id="30187-139">値が指定されていない場合は、Mgmt2005 エンドポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="30187-139">If a value is not specified, the Mgmt2005 endpoint is used.</span></span> <span data-ttu-id="30187-140">SOAP エンドポイントの詳細については、「 [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-140">For more information about the SOAP endpoints, see [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).</span></span>  
  
 <span data-ttu-id="30187-141">`-l`*time_out*</span><span class="sxs-lookup"><span data-stu-id="30187-141">`-l` *time_out*</span></span>  
 <span data-ttu-id="30187-142">Optionalサーバーへの接続がタイムアウトするまでの秒数を指定します。既定値は60秒です。</span><span class="sxs-lookup"><span data-stu-id="30187-142">(Optional) Specifies the number of seconds that elapse before the connection to the server times out. The default is 60 seconds.</span></span> <span data-ttu-id="30187-143">タイムアウト値を指定しない場合、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="30187-143">If you do not specify a time-out value, the default is used.</span></span> <span data-ttu-id="30187-144">値が `0` の場合は、接続はタイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="30187-144">A value of `0` specifies that the connection never times out.</span></span>  
  
 <span data-ttu-id="30187-145">**-b**</span><span class="sxs-lookup"><span data-stu-id="30187-145">**-b**</span></span>  
 <span data-ttu-id="30187-146">(省略可) スクリプト ファイル内のコマンドをバッチで実行します。</span><span class="sxs-lookup"><span data-stu-id="30187-146">(Optional) Specifies that the commands in the script file run in a batch.</span></span> <span data-ttu-id="30187-147">いずれかのコマンドが失敗すると、バッチはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="30187-147">If any commands fail, the batch is rolled back.</span></span> <span data-ttu-id="30187-148">バッチで実行できないコマンドがありますが、それらのコマンドは通常どおり実行されます。</span><span class="sxs-lookup"><span data-stu-id="30187-148">Some commands cannot be batched, and those run as usual.</span></span> <span data-ttu-id="30187-149">スクリプト内でスローされるが処理されない例外だけが、ロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="30187-149">Only exceptions that are thrown and are not handled within the script result in a rollback.</span></span> <span data-ttu-id="30187-150">スクリプトによって例外が処理され、`Main` から正常に値が返された場合、バッチはコミットされます。</span><span class="sxs-lookup"><span data-stu-id="30187-150">If the script handles an exception and returns normally from `Main`, the batch is committed.</span></span> <span data-ttu-id="30187-151">このパラメーターを省略した場合、バッチを作成せずにコマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="30187-151">If you omit this parameter, the commands run without creating a batch.</span></span> <span data-ttu-id="30187-152">詳細については、「 [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="30187-152">For more information, see [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).</span></span>  
  
 <span data-ttu-id="30187-153">`-v` *globalvar*</span><span class="sxs-lookup"><span data-stu-id="30187-153">`-v` *globalvar*</span></span>  
 <span data-ttu-id="30187-154">(省略可) スクリプト内で使用するグローバル変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-154">(Optional) Specifies global variables that are used in the script.</span></span> <span data-ttu-id="30187-155">スクリプトでグローバル変数を使用する場合は、この引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30187-155">If the script uses global variables, you must specify this argument.</span></span> <span data-ttu-id="30187-156">.rss ファイルで定義したグローバル変数に対して有効な値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30187-156">The value that you specify must be valid for global variable defined in the .rss file.</span></span> <span data-ttu-id="30187-157">**-V**引数ごとに1つのグローバル変数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30187-157">You must specify one global variable for each **-v** argument.</span></span>  
  
 <span data-ttu-id="30187-158">`-v` 引数はコマンド ラインで指定され、ユーザーのスクリプトに定義されているグローバル変数の値を実行時に設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="30187-158">The `-v` argument is specified on the command line and is used to set the value for a global variable that is defined in your script at run time.</span></span> <span data-ttu-id="30187-159">たとえば、スクリプトに *parentFolder*という名前の変数が含まれている場合、そのフォルダーの名前をコマンド ラインで指定することができます。</span><span class="sxs-lookup"><span data-stu-id="30187-159">For example, if your script contains a variable named *parentFolder*, you can specify a name for that folder on the command line:</span></span>  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 <span data-ttu-id="30187-160">指定した値に設定された名前を使用して、グローバル変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="30187-160">Global variables are created with the names given and set to the values supplied.</span></span> <span data-ttu-id="30187-161">たとえば、 **-v a =**" `1` " **-v b =**"" を指定すると、 `2` という名前の変数に `a` 値 " `1` " と値 "" を持つ変数**b**が生成さ `2` れます。</span><span class="sxs-lookup"><span data-stu-id="30187-161">For example, **-v a=**"`1`" **-v b=**"`2`" results in a variable named `a` with a value of"`1`" and a variable **b** with a value of "`2`".</span></span>  
  
 <span data-ttu-id="30187-162">グローバル変数は、スクリプト内のすべての関数で使用できます。</span><span class="sxs-lookup"><span data-stu-id="30187-162">Global variables are available to any function in the script.</span></span> <span data-ttu-id="30187-163">円記号と引用符 (\*\* \\ "\*\*) は、二重引用符として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="30187-163">A backslash and quotation mark (**\\"**) is interpreted as a double quotation mark.</span></span> <span data-ttu-id="30187-164">引用符は、文字列にスペースが含まれている場合のみ必要です。</span><span class="sxs-lookup"><span data-stu-id="30187-164">The quotation marks are required only if the string contains a space.</span></span> <span data-ttu-id="30187-165">変数名は、に対して有効である必要があり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ます。先頭にはアルファベットまたはアンダースコアを使用し、英字、数字、またはアンダースコアを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="30187-165">Variable names must be valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]; they must start with alphabetical character or underscore and contain alphabetical characters, digits, or underscores.</span></span> <span data-ttu-id="30187-166">予約語は、変数名として使用できません。</span><span class="sxs-lookup"><span data-stu-id="30187-166">Reserved words cannot be used as variable names.</span></span> <span data-ttu-id="30187-167">グローバル変数の使用の詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-167">For more information about using global variables, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="30187-168">**-t**</span><span class="sxs-lookup"><span data-stu-id="30187-168">**-t**</span></span>  
 <span data-ttu-id="30187-169">(省略可) エラー メッセージをトレース ログに出力します。</span><span class="sxs-lookup"><span data-stu-id="30187-169">(Optional) Outputs error messages to the trace log.</span></span> <span data-ttu-id="30187-170">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="30187-170">This argument does not take a value.</span></span> <span data-ttu-id="30187-171">詳細については、「 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-171">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> <span data-ttu-id="30187-172">Permissions</span><span class="sxs-lookup"><span data-stu-id="30187-172">Permissions</span></span>  
 <span data-ttu-id="30187-173">ツールを実行するには、スクリプトの実行対象であるレポート サーバー インスタンスに接続するための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="30187-173">To run the tool, you must have permission to connect to the report server instance you are running the script against.</span></span> <span data-ttu-id="30187-174">スクリプトを実行して、ローカル コンピューターまたはリモート コンピューターに変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="30187-174">You can run scripts to make changes to the local computer or a remote computer.</span></span> <span data-ttu-id="30187-175">リモート コンピューターにインストールしたレポート サーバーを変更するには、`-s` 引数でリモート コンピューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="30187-175">To make changes to a report server installed on a remote computer, specify the remote computer in the `-s` argument.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="30187-176">使用例</span><span class="sxs-lookup"><span data-stu-id="30187-176">Examples</span></span>  
 <span data-ttu-id="30187-177">次の例では、実行する [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET スクリプト、および Web サービス メソッドを含むスクリプト ファイルの指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="30187-177">The following example illustrates how to specify the script file that contains [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET script and Web service methods that you want to execute.</span></span>  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 <span data-ttu-id="30187-178"> 詳細な例については、「 [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-178">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="30187-179">その他の例については、「 [Reporting Services スクリプト ファイルを実行する](run-a-reporting-services-script-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-179">For additional examples, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30187-180">解説</span><span class="sxs-lookup"><span data-stu-id="30187-180">Remarks</span></span>  
 <span data-ttu-id="30187-181">スクリプトを定義して、システム プロパティの設定、レポートのパブリッシュなどが行えます。</span><span class="sxs-lookup"><span data-stu-id="30187-181">You can define scripts to set system properties, publish reports, and so forth.</span></span> <span data-ttu-id="30187-182">作成したスクリプトには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API の任意のメソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="30187-182">The scripts that you create can include any methods of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="30187-183">使用可能なメソッドおよびプロパティの詳細については、「 [Report Server Web Service](../report-server-web-service/report-server-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-183">For more information about the methods and properties available to you, see [Report Server Web Service](../report-server-web-service/report-server-web-service.md).</span></span>  
  
 <span data-ttu-id="30187-184">スクリプトは、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET のコードで記述し、.rss ファイル名拡張子が付いた Unicode または UTF-8 テキスト ファイルとして保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30187-184">The script must be written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET code, and stored in a Unicode or UTF-8 text file with an .rss file name extension.</span></span> <span data-ttu-id="30187-185">**rs** ユーティリティを使用して、スクリプトをデバッグすることはできません。</span><span class="sxs-lookup"><span data-stu-id="30187-185">You cannot debug scripts with the **rs** utility.</span></span> <span data-ttu-id="30187-186">スクリプトをデバッグするには、内でコードを実行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="30187-186">To debug a script, run the code within [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="30187-187"> 詳細な例については、「 [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30187-187">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30187-188">参照</span><span class="sxs-lookup"><span data-stu-id="30187-188">See Also</span></span>  
 <span data-ttu-id="30187-189">[Reporting Services スクリプトファイルを実行する](run-a-reporting-services-script-file.md) </span><span class="sxs-lookup"><span data-stu-id="30187-189">[Run a Reporting Services Script File](run-a-reporting-services-script-file.md) </span></span>  
 <span data-ttu-id="30187-190">[配置タスクと管理タスクのスクリプトを作成する](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="30187-190">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="30187-191">[rs.exe ユーティリティと Web サービスを使用したスクリプト](script-with-the-rs-exe-utility-and-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="30187-191">[Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md) </span></span>  
 [<span data-ttu-id="30187-192">レポート サーバーのコマンド プロンプト ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="30187-192">Report Server Command Prompt Utilities &#40;SSRS&#41;</span></span>](report-server-command-prompt-utilities-ssrs.md)  
  
  
