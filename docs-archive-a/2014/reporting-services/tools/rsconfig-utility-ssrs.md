---
title: rsconfig ユーティリティ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721038"
---
# <a name="rsconfig-utility-ssrs"></a><span data-ttu-id="bf764-102">rsconfig ユーティリティ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="bf764-102">rsconfig Utility (SSRS)</span></span>
  <span data-ttu-id="bf764-103">**rsconfig.exe** ユーティリティは、接続値とアカウント値を RSReportServer.config ファイルへ暗号化して格納します。</span><span class="sxs-lookup"><span data-stu-id="bf764-103">The **rsconfig.exe** utility encrypts and stores connection and account values in the RSReportServer.config file.</span></span> <span data-ttu-id="bf764-104">暗号化される値は、自動レポート処理に使用される、レポート サーバー データベースの接続情報とアカウント値です。</span><span class="sxs-lookup"><span data-stu-id="bf764-104">Encrypted values include report server database connection information and account values used for unattended report processing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf764-105">構文</span><span class="sxs-lookup"><span data-stu-id="bf764-105">Syntax</span></span>  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf764-106">引数</span><span class="sxs-lookup"><span data-stu-id="bf764-106">Arguments</span></span>  
  
|<span data-ttu-id="bf764-107">期間</span><span class="sxs-lookup"><span data-stu-id="bf764-107">Term</span></span>|<span data-ttu-id="bf764-108">省略可/必須</span><span class="sxs-lookup"><span data-stu-id="bf764-108">Optional/Required</span></span>|<span data-ttu-id="bf764-109">定義</span><span class="sxs-lookup"><span data-stu-id="bf764-109">Definition</span></span>|  
|----------|------------------------|----------------|  
|<span data-ttu-id="bf764-110">**-?**</span><span class="sxs-lookup"><span data-stu-id="bf764-110">**-?**</span></span>|<span data-ttu-id="bf764-111">省略可能。</span><span class="sxs-lookup"><span data-stu-id="bf764-111">Optional.</span></span>|<span data-ttu-id="bf764-112">Rsconfig.exe の引数の構文を表示します。</span><span class="sxs-lookup"><span data-stu-id="bf764-112">Displays the syntax of Rsconfig.exe arguments.</span></span>|  
|`-c`|<span data-ttu-id="bf764-113">`-e` 引数を使用しない場合は必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-113">Required if `-e` argument is not used.</span></span>|<span data-ttu-id="bf764-114">レポート サーバーをレポート サーバー データベースに接続するために使用する、接続文字列、資格情報、データ ソース値を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-114">Specifies the connection string, credentials, and data source values used to connect a report server to the report server database.</span></span><br /><br /> <span data-ttu-id="bf764-115">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="bf764-115">This argument does not take a value.</span></span> <span data-ttu-id="bf764-116">ただし、必須の接続値をすべて指定する場合は、この引数と共に追加の引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf764-116">However, additional arguments must be specified with it to provide all of the required connection values.</span></span><br /><br /> <span data-ttu-id="bf764-117">で指定できる引数には `-c` `-m` 、 **-s**、、、、、、およびがあり `-i` `-d` `-a` `-u` `-p` `-t` ます。</span><span class="sxs-lookup"><span data-stu-id="bf764-117">Arguments that you can specify with `-c` include `-m`, **-s**, `-i`,`-d`,`-a`,`-u`,`-p`, and`-t`.</span></span>|  
|`-e`|<span data-ttu-id="bf764-118">`-c` 引数を使用しない場合は必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-118">Required if `-c` argument is not used.</span></span>|<span data-ttu-id="bf764-119">自動的にレポートを実行する場合のアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-119">Specifies the unattended report execution account.</span></span><br /><br /> <span data-ttu-id="bf764-120">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="bf764-120">This argument does not take a value.</span></span> <span data-ttu-id="bf764-121">ただし、構成ファイルで暗号化されている値を指定する場合は、コマンド ラインに追加の引数を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf764-121">However, you must include additional arguments on the command line to specify that values that are encrypted in the configuration file.</span></span><br /><br /> <span data-ttu-id="bf764-122">`-e` と共に指定する引数には、`-u` および `-p` があります。</span><span class="sxs-lookup"><span data-stu-id="bf764-122">Arguments that you can specify with `-e` include `-u` and `-p`.</span></span> <span data-ttu-id="bf764-123">`-t` を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bf764-123">You can also set `-t`.</span></span>|  
|<span data-ttu-id="bf764-124">`-m`  *コンピューター名*</span><span class="sxs-lookup"><span data-stu-id="bf764-124">`-m`  *computername*</span></span>|<span data-ttu-id="bf764-125">リモート レポート サーバー インスタンスを構成する場合は必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-125">Required if you are configuring a remote report server instance.</span></span>|<span data-ttu-id="bf764-126">レポート サーバーをホストするコンピューターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-126">Specifies the name of the computer that is hosting the report server.</span></span> <span data-ttu-id="bf764-127">この引数が省略された場合、既定は `localhost` です。</span><span class="sxs-lookup"><span data-stu-id="bf764-127">If this argument is omitted, the default is `localhost`.</span></span>|  
|<span data-ttu-id="bf764-128">**-s**  *servername*</span><span class="sxs-lookup"><span data-stu-id="bf764-128">**-s**  *servername*</span></span>|<span data-ttu-id="bf764-129">必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-129">Required.</span></span>|<span data-ttu-id="bf764-130">レポート サーバー データベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-130">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span>|  
|<span data-ttu-id="bf764-131">`-i`  *instancename*</span><span class="sxs-lookup"><span data-stu-id="bf764-131">`-i`  *instancename*</span></span>|<span data-ttu-id="bf764-132">名前付きインスタンスを使用する場合は必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-132">Required if you are using named instances.</span></span>|<span data-ttu-id="bf764-133">名前付き [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用してレポート サーバー データベースをホストする場合、この値には名前付きインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-133">If you used a named [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the report server database, this value specifies the named instance.</span></span>|  
|<span data-ttu-id="bf764-134">`-d`  *databasename*</span><span class="sxs-lookup"><span data-stu-id="bf764-134">`-d`  *databasename*</span></span>|<span data-ttu-id="bf764-135">必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-135">Required.</span></span>|<span data-ttu-id="bf764-136">レポート サーバー データベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-136">Specifies the name of the report server database.</span></span>|  
|<span data-ttu-id="bf764-137">`-a`  *authmethod*</span><span class="sxs-lookup"><span data-stu-id="bf764-137">`-a`  *authmethod*</span></span>|<span data-ttu-id="bf764-138">必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-138">Required.</span></span>|<span data-ttu-id="bf764-139">レポート サーバーがレポート サーバー データベースへの接続に使用する認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-139">Specifies the authentication method that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="bf764-140">有効な値は、`Windows` または `SQL` です (この引数は大文字と小文字を区別しません)。</span><span class="sxs-lookup"><span data-stu-id="bf764-140">Valid values are `Windows` or `SQL` (this argument is not case-sensitive).</span></span><br /><br /> <span data-ttu-id="bf764-141">`Windows` は、レポート サーバーが Windows 認証を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-141">`Windows` specifies that the report server use Windows Authentication.</span></span><br /><br /> <span data-ttu-id="bf764-142">`SQL` は、レポート サーバーが SQL Server 認証を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-142">`SQL` specifies that the report server use SQL Server Authentication.</span></span>|  
|<span data-ttu-id="bf764-143">`-u`  *[ドメイン \\ ]ユーザー名*</span><span class="sxs-lookup"><span data-stu-id="bf764-143">`-u`  *[domain\\]username*</span></span>|<span data-ttu-id="bf764-144">`-e` の場合は必須。`-c` の場合は省略可。</span><span class="sxs-lookup"><span data-stu-id="bf764-144">Required with `-e` Optional with `-c`.</span></span>|<span data-ttu-id="bf764-145">レポート サーバー データベース接続または自動アカウントのためのユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-145">Specifies a user account for the report server database connection or for the unattended account.</span></span><br /><br /> <span data-ttu-id="bf764-146">**rsconfig -e**では、この引数は必須です。</span><span class="sxs-lookup"><span data-stu-id="bf764-146">For **rsconfig -e**, this argument is required.</span></span> <span data-ttu-id="bf764-147">ドメイン ユーザー アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf764-147">It must be a domain user account.</span></span><br /><br /> <span data-ttu-id="bf764-148">**Rsconfig-c**およびの場合 `-a SQL` 、この引数にはログインを指定する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bf764-148">For **rsconfig -c** and `-a SQL`, this argument must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span><br /><br /> <span data-ttu-id="bf764-149">**Rsconfig-c**およびの場合 `-a Windows` 、この引数には、ドメインユーザー、組み込みアカウント、またはサービスアカウント資格情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bf764-149">For **rsconfig -c** and `-a Windows`, this argument may specify a domain user, a built-in account, or service account credentials.</span></span> <span data-ttu-id="bf764-150">ドメイン アカウントを指定している場合は、 *domain* と *username* を *domain\username*の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-150">If you are specifying a domain account, specify *domain* and *username* in the format *domain\username*.</span></span> <span data-ttu-id="bf764-151">組み込みアカウントを使用する場合、この引数は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bf764-151">If you are using a built-in account, this argument is optional.</span></span> <span data-ttu-id="bf764-152">サービス アカウント資格情報を使用する場合、この引数は省略してください。</span><span class="sxs-lookup"><span data-stu-id="bf764-152">If you want to use service account credentials, omit this argument.</span></span>|  
|<span data-ttu-id="bf764-153">`-p`  *password*</span><span class="sxs-lookup"><span data-stu-id="bf764-153">`-p`  *password*</span></span>|<span data-ttu-id="bf764-154">`-u` を指定した場合は必須。</span><span class="sxs-lookup"><span data-stu-id="bf764-154">Required if `-u` is specified.</span></span>|<span data-ttu-id="bf764-155">*username* 引数と共に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf764-155">Specifies the password to use with the *username* argument.</span></span> <span data-ttu-id="bf764-156">アカウントがパスワードを必要としない場合、この引数を空白に設定できます。</span><span class="sxs-lookup"><span data-stu-id="bf764-156">You can set this argument to a blank value if the account does not require a password.</span></span> <span data-ttu-id="bf764-157">この値は、ドメイン アカウントの大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="bf764-157">This value is case-sensitive for domain accounts.</span></span>|  
|`-t`|<span data-ttu-id="bf764-158">省略可能。</span><span class="sxs-lookup"><span data-stu-id="bf764-158">Optional.</span></span>|<span data-ttu-id="bf764-159">エラー メッセージをトレース ログに出力します。</span><span class="sxs-lookup"><span data-stu-id="bf764-159">Outputs error messages to the trace log.</span></span> <span data-ttu-id="bf764-160">この引数は値を取りません。</span><span class="sxs-lookup"><span data-stu-id="bf764-160">This argument does not take a value.</span></span> <span data-ttu-id="bf764-161">詳細については、「 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf764-161">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="bf764-162">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="bf764-162">Permissions</span></span>  
 <span data-ttu-id="bf764-163">構成中のレポート サーバーをホストするコンピューターのローカル管理者であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf764-163">You must be a local administrator on the computer that hosts the report server you are configuring.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="bf764-164">ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="bf764-164">File Location</span></span>  
 <span data-ttu-id="bf764-165">rsconfig.exe は **\Program Files\Microsoft SQL Server\110\Tools\Binn**にあります。</span><span class="sxs-lookup"><span data-stu-id="bf764-165">Rsconfig.exe is located in **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="bf764-166">このユーティリティは、ファイル システム上の任意のフォルダーから実行できます。</span><span class="sxs-lookup"><span data-stu-id="bf764-166">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf764-167">解説</span><span class="sxs-lookup"><span data-stu-id="bf764-167">Remarks</span></span>  
 <span data-ttu-id="bf764-168">Rsconfig.exe は次の 2 つの目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="bf764-168">Rsconfig.exe is used for two purposes:</span></span>  
  
-   <span data-ttu-id="bf764-169">レポート サーバー データベースへの接続でレポート サーバーが使用する接続情報の修正。</span><span class="sxs-lookup"><span data-stu-id="bf764-169">To modify the connection information that a report server uses to connect to a report server database.</span></span>  
  
-   <span data-ttu-id="bf764-170">他の資格情報が利用できない場合に、リモート データベース サーバーへのログオンでレポート サーバーが使用する特別なアカウントの構成。</span><span class="sxs-lookup"><span data-stu-id="bf764-170">To configure a special account that the report server uses to log on to a remote database server when other credentials are not available.</span></span>  
  
 <span data-ttu-id="bf764-171">**rsconfig** ユーティリティは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のローカル インスタンスまたはリモート インスタンスで実行できます。</span><span class="sxs-lookup"><span data-stu-id="bf764-171">You can run the**rsconfig** utility on a local or remote instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="bf764-172">**rsconfig** ユーティリティは、既に設定されている値の暗号化解除または参照に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf764-172">You cannot use the **rsconfig** utility to decrypt and view values that are already set.</span></span>  
  
 <span data-ttu-id="bf764-173">このユーティリティを実行する前に、構成中のコンピューターに、Windows Management Instrumentation (WMI) をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf764-173">Before you can run this utility, Windows Management Instrumentation (WMI) must be installed on the computer that you are configuring.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bf764-174">例</span><span class="sxs-lookup"><span data-stu-id="bf764-174">Examples</span></span>  
 <span data-ttu-id="bf764-175">次の例は、 **rsconfig**の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bf764-175">The following examples illustrate ways of using **rsconfig**.</span></span>  
  
#### <a name="specifying-a-domain-user-account"></a><span data-ttu-id="bf764-176">ドメイン ユーザー アカウントの指定</span><span class="sxs-lookup"><span data-stu-id="bf764-176">Specifying a Domain User Account</span></span>  
 <span data-ttu-id="bf764-177">次の例では、ローカルのレポート サーバー データベースに接続する場合に、ドメイン ユーザー アカウントを使用するようにレポート サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="bf764-177">This example shows how to configure a report server to use a domain user account when connecting to a local report server database.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a><span data-ttu-id="bf764-178">SQL Server データベース ユーザー アカウントの指定</span><span class="sxs-lookup"><span data-stu-id="bf764-178">Specifying a SQL Server Database User Account</span></span>  
 <span data-ttu-id="bf764-179">次の例では、リモートのレポート サーバー データベースに接続する場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用するようにレポート サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="bf764-179">This example shows how to configure a report server to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to connect to a remote report server database.</span></span>  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a><span data-ttu-id="bf764-180">組み込みアカウントの指定</span><span class="sxs-lookup"><span data-stu-id="bf764-180">Specifying a Built-in Account</span></span>  
 <span data-ttu-id="bf764-181">次の例では、ローカルのレポート サーバー データベースに接続する場合に、組み込みアカウントを使用するようにレポート サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="bf764-181">This example shows how to configure a report server to use a built-in account when connecting to a local report server database.</span></span> <span data-ttu-id="bf764-182">`-u` は使用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bf764-182">Notice that `-u` is not used.</span></span> <span data-ttu-id="bf764-183">サポートされているビルトインアカウント値の例としては、ローカルシステムの NT AUTHORITY\SYSTEM とネットワークサービスの NT AUTHORITY\NETWORKSERVICE (のみ) などがあり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bf764-183">Examples of supported built-in account values include NT AUTHORITY\SYSTEM for Local System and NT AUTHORITY\NETWORKSERVICE for Network Service ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] only).</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a><span data-ttu-id="bf764-184">サービス アカウントの指定</span><span class="sxs-lookup"><span data-stu-id="bf764-184">Specifying a Service Account</span></span>  
 <span data-ttu-id="bf764-185">次の例では、ローカルのレポート サーバー データベースに接続する場合に、レポート サーバー Windows サービス アカウントと Web サービス アカウントを使用するようにレポート サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="bf764-185">This example shows how to configure a report server to use the Report Server Windows service account and Web service account when connecting to a local report server database.</span></span> <span data-ttu-id="bf764-186">`-u` は使用されず、アカウント情報が指定されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bf764-186">Notice that `-u` is not used and that no account information is specified.</span></span> <span data-ttu-id="bf764-187">コマンドでアカウント値を指定しなかった場合、 **rsconfig** ユーティリティは、各サービスの実行に使用する統合セキュリティおよびサービス アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf764-187">When you eliminate account values from the command, the **rsconfig** utility uses integrated security and the service account that each service runs under.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a><span data-ttu-id="bf764-188">ローカル サーバーの自動アカウントの指定</span><span class="sxs-lookup"><span data-stu-id="bf764-188">Specifying the Unattended Account on a Local Server</span></span>  
 <span data-ttu-id="bf764-189">次の例では、外部データ ソースに資格情報を渡すことのできないレポートに対して、自動的にレポートを実行する場合に使用されるアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="bf764-189">This example shows how to configure the account used for unattended report execution for reports that do not pass credentials to the external data source.</span></span> <span data-ttu-id="bf764-190">アカウントは Windows ドメイン アカウントであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf764-190">The account must be a Windows domain account.</span></span> <span data-ttu-id="bf764-191">ユーザー名とパスワードに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf764-191">You cannot specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for the user name and password.</span></span> <span data-ttu-id="bf764-192">アカウントは、ローカルのレポート サーバー インスタンス上に構成されます。</span><span class="sxs-lookup"><span data-stu-id="bf764-192">The account is configured on a local report server instance.</span></span> <span data-ttu-id="bf764-193">エラー メッセージは、ReportingServices\LogFiles フォルダーのトレース ログにキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="bf764-193">Error messages are captured in the trace logs in the ReportingServices\LogFiles folder.</span></span>  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a><span data-ttu-id="bf764-194">リモート サーバーの自動アカウントの指定</span><span class="sxs-lookup"><span data-stu-id="bf764-194">Specifying the Unattended Account on a Remote Server</span></span>  
 <span data-ttu-id="bf764-195">次の例では、リモートのレポート サーバー インスタンス上にアカウントを構成します。このインスタンスは、Rsconfig.exe と同じバージョンになっています (レポート サーバーと Rsconfig.exe が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 バージョンの場合など)。</span><span class="sxs-lookup"><span data-stu-id="bf764-195">This example shows how to configure the account on a remote report server instance that is the same version as Rsconfig.exe (for example, the report server and Rsconfig.exe are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 version).</span></span> <span data-ttu-id="bf764-196">エラー メッセージ情報は、リモート サーバーのトレース ログにキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="bf764-196">Error message information is captured in the trace logs on the remote server.</span></span>  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf764-197">参照</span><span class="sxs-lookup"><span data-stu-id="bf764-197">See Also</span></span>  
 <span data-ttu-id="bf764-198">[SSRS Configuration Manager &#40;レポートサーバーデータベース接続の構成&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="bf764-198">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="bf764-199">[SSRS Configuration Manager &#40;自動実行アカウントを構成&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="bf764-199">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="bf764-200">[Reporting Services レポート サーバー (ネイティブ モード)](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="bf764-200">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="bf764-201">[暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="bf764-201">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 <span data-ttu-id="bf764-202">[Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="bf764-202">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="bf764-203">[SSRS&#41;&#40;レポートサーバーのコマンドプロンプトユーティリティ](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bf764-203">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="bf764-204">RSReportServer 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="bf764-204">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
