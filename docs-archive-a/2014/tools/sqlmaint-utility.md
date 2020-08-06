---
title: sqlmaint Utility |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- database maintenance plans [SQL Server]
- sqlmaint utility
- maintaining databases [SQL Server]
- backups [SQL Server], sqlmaint utility
- command prompt utilities [SQL Server], sqlmaint
- maintenance plans [SQL Server], command prompt
- backing up [SQL Server], sqlmaint utility
ms.assetid: 937a9932-4aed-464b-b97a-a5acfe6a50de
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80e60b75305ee91e8b62a201d9c86af301326789
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711214"
---
# <a name="sqlmaint-utility"></a><span data-ttu-id="e0ecc-102">sqlmaint ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="e0ecc-102">sqlmaint Utility</span></span>
  <span data-ttu-id="e0ecc-103">**sqlmaint** ユーティリティは、1 つまたは複数のデータベース上で、指定された一連のメンテナンス操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-103">The**sqlmaint** utility performs a specified set of maintenance operations on one or more databases.</span></span> <span data-ttu-id="e0ecc-104">**sqlmaint** を使用して、DBCC チェックの実行、データベースとデータベース トランザクション ログのバックアップ、統計の更新、およびインデックスの再構築を行います。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-104">Use **sqlmaint** to run DBCC checks, back up a database and its transaction log, update statistics, and rebuild indexes.</span></span> <span data-ttu-id="e0ecc-105">すべてのデータベース メンテナンス操作では、指定されたテキスト ファイル、HTML ファイル、または電子メール アカウントに送信できるレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-105">All database maintenance activities generate a report that can be sent to a designated text file, HTML file, or e-mail account.</span></span> <span data-ttu-id="e0ecc-106">**sqlmaint** は、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]で作成されたデータベース メンテナンス プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-106">**sqlmaint** executes database maintenance plans created with previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0ecc-107">コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] メンテナンス プランを実行するには、 [dtexec](../integration-services/packages/dtexec-utility.md)ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-107">To run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plans from the command prompt, use the [dtexec Utility](../integration-services/packages/dtexec-utility.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../includes/ssnotedepnextavoid-md.md)] <span data-ttu-id="e0ecc-108">代わりに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] メンテナンス プラン機能を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-108">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plan feature instead.</span></span> <span data-ttu-id="e0ecc-109">メンテナンス プランの詳細については、「 [メンテナンス プラン](../relational-databases/maintenance-plans/maintenance-plans.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-109">For more information on maintenance plans, see [Maintenance Plans](../relational-databases/maintenance-plans/maintenance-plans.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ecc-110">構文</span><span class="sxs-lookup"><span data-stu-id="e0ecc-110">Syntax</span></span>  
  
```  
  
      sqlmaint   
[-?] |  
[  
     [-Sserver_name[\instance_name]]  
     [-Ulogin_ID [-Ppassword]]  
     {  
          [-Ddatabase_name | -PlanNamename | -PlanIDguid ]  
          [-Rpttext_file]  
          [-Tooperator_name]  
          [-HtmlRpthtml_file [-DelHtmlRpt <time_period>] ]  
          [-RmUnusedSpacethreshold_percentfree_percent]  
          [-CkDB | -CkDBNoIdx]  
          [-CkAl | -CkAlNoIdx]  
          [-CkCat]  
          [-UpdOptiStatssample_percent]  
          [-RebldIdxfree_space]  
          [-SupportComputedColumn]  
          [-WriteHistory]  
          [  
               {-BkUpDB [backup_path] | -BkUpLog [backup_path] }  
               {-BkUpMedia  
                    {DISK [  
                           [-DelBkUps<time_period>]   
                           [-CrBkSubDir ]   
                           [-UseDefDir ]   
                          ]  
                     | TAPE   
                    }  
               }  
               [-BkUpOnlyIfClean]  
               [-VrfyBackup]  
          ]  
     }  
]  
<time_period> ::=  
number[minutes | hours | days | weeks | months]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e0ecc-111">引数</span><span class="sxs-lookup"><span data-stu-id="e0ecc-111">Arguments</span></span>  
 <span data-ttu-id="e0ecc-112">パラメーターとその値は、空白で区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-112">The parameters and their values must be separated by a space.</span></span> <span data-ttu-id="e0ecc-113">たとえば、 **-S** と *server_name*の間には空白が必要です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-113">For example, there must be a space between **-S** and *server_name*.</span></span>  
  
 <span data-ttu-id="e0ecc-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-114">**-?**</span></span>  
 <span data-ttu-id="e0ecc-115">**sqlmaint** の構文ダイアグラムが返されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-115">Specifies that the syntax diagram for **sqlmaint** be returned.</span></span> <span data-ttu-id="e0ecc-116">このパラメーターは単独で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-116">This parameter must be used alone.</span></span>  
  
 <span data-ttu-id="e0ecc-117">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="e0ecc-117">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="e0ecc-118">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のターゲット インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-118">Specifies the target instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0ecc-119">サーバー上の *の既定のインスタンスに接続するには、* server_name [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-119">Specify *server_name* to connect to the default instance of [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on that server.</span></span> <span data-ttu-id="e0ecc-120">サーバー上のの名前付きインスタンスに接続するには、 *server_name **_\\_** instance_name*を指定し [!INCLUDE[ssDE](../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-120">Specify *server_name\*\*_\\_*\* instance_name\* to connect to a named instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="e0ecc-121">サーバーを指定しない場合、 **sqlmaint** は、ローカル コンピューター上にある [!INCLUDE[ssDE](../includes/ssde-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-121">If no server is specified, **sqlmaint** connects to the default instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="e0ecc-122">**-U** _login_ID_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-122">**-U** _login_ID_</span></span>  
 <span data-ttu-id="e0ecc-123">サーバーに接続するときに使用するログイン ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-123">Specifies the login ID to use when connecting to the server.</span></span> <span data-ttu-id="e0ecc-124">指定しない場合、 **sqlmaint** は [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 認証の使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-124">If not supplied, **sqlmaint** attempts to use [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="e0ecc-125">*login_ID* に特殊文字が含まれる場合、特殊文字を二重引用符 (") で囲む必要があります。特殊文字が含まれない場合は、二重引用符は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-125">If *login_ID* contains special characters, it must be enclosed in double quotation marks ("); otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e0ecc-126">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-126">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="e0ecc-127">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-127">**-P** _password_</span></span>  
 <span data-ttu-id="e0ecc-128">ログイン ID のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-128">Specifies the password for the login ID.</span></span> <span data-ttu-id="e0ecc-129">**-U** パラメーターも指定されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-129">Only valid if the **-U** parameter is also supplied.</span></span> <span data-ttu-id="e0ecc-130">*password* に特殊文字が含まれる場合、特殊文字を二重引用符で囲む必要があります。特殊文字が含まれない場合は、二重引用符は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-130">If *password* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e0ecc-131">パスワードはマスクされません。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-131">The password is not masked.</span></span> <span data-ttu-id="e0ecc-132">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="e0ecc-133">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-133">**-D** _database_name_</span></span>  
 <span data-ttu-id="e0ecc-134">メンテナンス操作の実行対象となるデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-134">Specifies the name of the database in which to perform the maintenance operation.</span></span> <span data-ttu-id="e0ecc-135">*database_name* に特殊文字が含まれる場合、特殊文字を二重引用符で囲む必要があります。特殊文字が含まれない場合は、二重引用符は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-135">If *database_name* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
 <span data-ttu-id="e0ecc-136">**-PlanName** _name_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-136">**-PlanName** _name_</span></span>  
 <span data-ttu-id="e0ecc-137">データベース メンテナンス プラン ウィザードを使用して定義される、データベース メンテナンス プランの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-137">Specifies the name of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="e0ecc-138">**sqlmaint** が使用するプランの情報は、プラン内のデータベースのリストのみです。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-138">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="e0ecc-139">他の **sqlmaint** パラメーターに指定するすべてのメンテナンス操作は、このデータベースのリストに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-139">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span>  
  
 <span data-ttu-id="e0ecc-140">**-PlanID** _guid_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-140">**-PlanID** _guid_</span></span>  
 <span data-ttu-id="e0ecc-141">データベース メンテナンス プラン ウィザードを使用して定義される、データベース メンテナンス プランのグローバル一意識別子 (GUID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-141">Specifies the globally unique identifier (GUID) of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="e0ecc-142">**sqlmaint** が使用するプランの情報は、プラン内のデータベースのリストのみです。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-142">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="e0ecc-143">他の **sqlmaint** パラメーターに指定するすべてのメンテナンス操作は、このデータベースのリストに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-143">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span> <span data-ttu-id="e0ecc-144">このパラメーターの値は、msdb.dbo.sysdbmaintplans の plan_id 値に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-144">This must match a plan_id value in msdb.dbo.sysdbmaintplans.</span></span>  
  
 <span data-ttu-id="e0ecc-145">**-Rpt** _text_file_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-145">**-Rpt** _text_file_</span></span>  
 <span data-ttu-id="e0ecc-146">レポートの生成先となるファイルの完全なパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-146">Specifies the full path and name of the file into which the report is to be generated.</span></span> <span data-ttu-id="e0ecc-147">レポートは画面上にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-147">The report is also generated on the screen.</span></span> <span data-ttu-id="e0ecc-148">レポートによってファイル名に日時が追加され、バージョン情報が維持されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-148">The report maintains version information by adding a date to the file name.</span></span> <span data-ttu-id="e0ecc-149">日時は、_*yyyyMMddhhmm*の形式で、ファイル名の最後 (ピリオドの前) に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-149">The date is generated as follows: at the end of the file name but before the period, in the form _*yyyyMMddhhmm*.</span></span> <span data-ttu-id="e0ecc-150">*yyyy* = 年、 *MM* = 月、 *dd* = 日、 *hh* = 時間、 *mm* = 分。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-150">*yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, *mm* = minute.</span></span>  
  
 <span data-ttu-id="e0ecc-151">1996 年 12 月 1 日午前 10:23 に</span><span class="sxs-lookup"><span data-stu-id="e0ecc-151">If you run the utility at 10:23 A.M.</span></span> <span data-ttu-id="e0ecc-152">ユーティリティを実行し、 *text_file* 値が次のようになるとします。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-152">on December 1, 1996, and this is the *text_file* value:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.rpt  
```  
  
 <span data-ttu-id="e0ecc-153">生成されるファイル名は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-153">The generated file name is:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint_199612011023.rpt  
```  
  
 <span data-ttu-id="e0ecc-154">*sqlmaint* がリモート サーバーにアクセスする場合、 **text_file** には、完全な汎用名前付け規則 (UNC) のファイル名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-154">The full Universal Naming Convention (UNC) file name is required for *text_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="e0ecc-155">**-** _Operator_name_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-155">**-To** _operator_name_</span></span>  
 <span data-ttu-id="e0ecc-156">生成されたレポートが SQL Mail を使用して送信される場合の、送信先となるオペレーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-156">Specifies the operator to whom the generated report is sent through SQL Mail.</span></span>  
  
 <span data-ttu-id="e0ecc-157">**-HtmlRpt** _html_file_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-157">**-HtmlRpt** _html_file_</span></span>  
 <span data-ttu-id="e0ecc-158">HTML レポートの生成先となるファイルの完全パスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-158">Specifies the full path and name of the file into which an HTML report is to be generated.</span></span> <span data-ttu-id="e0ecc-159">**sqlmaint** は、 *-Rpt* パラメーターの場合と同じように、ファイル名に _ **yyyyMMddhhmm** 形式の文字列を追加してファイル名を生成します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-159">**sqlmaint** generates the file name by appending a string of the format _*yyyyMMddhhmm* to the file name, just as it does for the **-Rpt** parameter.</span></span>  
  
 <span data-ttu-id="e0ecc-160">*sqlmaint* がリモート サーバーにアクセスする場合、 **html_file** には、完全な UNC ファイル名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-160">The full UNC file name is required for *html_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="e0ecc-161">**-DelHtmlRpt** \<*time_period*></span><span class="sxs-lookup"><span data-stu-id="e0ecc-161">**-DelHtmlRpt** \<*time_period*></span></span>  
 <span data-ttu-id="e0ecc-162">レポート ファイル作成後の期間が \<*time_period*> を超える場合、レポート ディレクトリ内にあるすべての HTML レポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-162">Specifies that any HTML report in the report directory be deleted if the time interval after the creation of the report file exceeds \<*time_period*>.</span></span> <span data-ttu-id="e0ecc-163">**-DelHtmlRpt** は、*html_file* パラメーターを基に生成されたパターンに適合する名前を持つファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-163">**-DelHtmlRpt** looks for files whose name fits the pattern generated from the *html_file* parameter.</span></span> <span data-ttu-id="e0ecc-164">*html_file* が C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm の場合、 **-DelHtmlRpt** を指定した **sqlmaint** によって、名前が C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm というパターンに一致し、指定した \<*time_period*> よりも古いすべてのファイルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-164">If *html_file* is c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm, then **-DelHtmlRpt** causes **sqlmaint** to delete any files whose names match the pattern C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm and that are older than the specified \<*time_period*>.</span></span>  
  
 <span data-ttu-id="e0ecc-165">**-RmUnusedSpace** _threshold_percent free_percent_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-165">**-RmUnusedSpace** _threshold_percent free_percent_</span></span>  
 <span data-ttu-id="e0ecc-166">**-D**に指定されたデータベースから使用されていない領域を削除します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-166">Specifies that unused space be removed from the database specified in **-D**.</span></span> <span data-ttu-id="e0ecc-167">このオプションは、自動拡張が定義されているデータベースに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-167">This option is only useful for databases that are defined to grow automatically.</span></span> <span data-ttu-id="e0ecc-168">*Threshold_percent* は、 **sqlmaint** が使用されていないデータ領域を削除する基準となるデータベースのサイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-168">*Threshold_percent* specifies in megabytes the size that the database must reach before **sqlmaint** attempts to remove unused data space.</span></span> <span data-ttu-id="e0ecc-169">データベースが *threshold_percent*より小さい場合、何も行われません。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-169">If the database is smaller than the *threshold_percent*, no action is taken.</span></span> <span data-ttu-id="e0ecc-170">*Free_percent* は、データベースに残す必要がある使用されていない領域の量を、データベースの最終的なサイズに対する割合として指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-170">*Free_percent* specifies how much unused space must remain in the database, specified as a percentage of the final size of the database.</span></span> <span data-ttu-id="e0ecc-171">たとえば、200 MB のデータベースに 100 MB のデータを取り込む場合、 *free_percent* に 10 を指定すると、最終的なデータベース サイズは 110 MB になります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-171">For example, if a 200-MB database contains 100 MB of data, specifying 10 for *free_percent* results in the final database size being 110 MB.</span></span> <span data-ttu-id="e0ecc-172">データベースが *free_percent* とデータベースのデータ量の合計より小さい場合、データベースは拡張されないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-172">Note that a database is not expanded if it is smaller than *free_percent* plus the amount of data in the database.</span></span> <span data-ttu-id="e0ecc-173">たとえば、108 MB のデータベースが 100 MB のデータを持つ場合、 *free_percent* に 10 を指定してもデータベースは 110 MB に拡張されず、108 MB のままです。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-173">For example, if a 108-MB database has 100 MB of data, specifying 10 for *free_percent* does not expand the database to 110 MB; it remains at 108 MB.</span></span>  
  
 <span data-ttu-id="e0ecc-174">**-CkDB** |  **-CkDBNoIdx**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-174">**-CkDB** | **-CkDBNoIdx**</span></span>  
 <span data-ttu-id="e0ecc-175">**-D**に指定されたデータベースで、DBCC CHECKDB ステートメント、または NOINDEX オプションを含んだ DBCC CHECKDB ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-175">Specifies that a DBCC CHECKDB statement or a DBCC CHECKDB statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="e0ecc-176">詳細については、「DBCC CHECKDB」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-176">For more information, see DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="e0ecc-177">*sqlmaint* を実行するときにデータベースが使用中の場合、 **text_file** に警告が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-177">A warning is written to *text_file* if the database is in use when **sqlmaint** runs.</span></span>  
  
 <span data-ttu-id="e0ecc-178">**-CkAl** |  **-CkAlNoIdx**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-178">**-CkAl** | **-CkAlNoIdx**</span></span>  
 <span data-ttu-id="e0ecc-179">**-D**に指定されたデータベースで、NOINDEX オプションを含んだ DBCC CHECKALLOC ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-179">Specifies that a DBCC CHECKALLOC statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="e0ecc-180">詳細については、「[DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-180">For more information, see [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql).</span></span>  
  
 <span data-ttu-id="e0ecc-181">**-CkCat**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-181">**-CkCat**</span></span>  
 <span data-ttu-id="e0ecc-182">**-D** に指定されたデータベースで、DBCC CHECKCATALOG (Transact-SQL) ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-182">Specifies that a DBCC CHECKCATALOG (Transact-SQL) statement be run in the database specified in **-D**.</span></span> <span data-ttu-id="e0ecc-183">詳細については、「[DBCC CHECKCATALOG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-183">For more information, see [DBCC CHECKCATALOG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql).</span></span>  
  
 <span data-ttu-id="e0ecc-184">**-UpdOptiStats** _sample_percent_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-184">**-UpdOptiStats** _sample_percent_</span></span>  
 <span data-ttu-id="e0ecc-185">データベースの各テーブルで、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-185">Specifies that the following statement be run on each table in the database:</span></span>  
  
```  
UPDATE STATISTICS table WITH SAMPLE sample_percent PERCENT;  
```  
  
 <span data-ttu-id="e0ecc-186">テーブルが計算列を含む場合、 **-UpdOptiStats** を使用するときに **-SupportedComputedColumn**引数も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-186">If the tables contain computed columns, you must also specify the **-SupportedComputedColumn** argument when you use **-UpdOptiStats**.</span></span>  
  
 <span data-ttu-id="e0ecc-187">詳細については、「 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)で作成されたデータベース メンテナンス プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-187">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
 <span data-ttu-id="e0ecc-188">**-RebldIdx** _free_space_</span><span class="sxs-lookup"><span data-stu-id="e0ecc-188">**-RebldIdx** _free_space_</span></span>  
 <span data-ttu-id="e0ecc-189">FILL FACTOR とは逆の関係になる値として *free_space* の割合の値を使用し、対象データベースのテーブルのインデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-189">Specifies that indexes on tables in the target database should be rebuilt by using the *free_space* percent value as the inverse of the fill factor.</span></span> <span data-ttu-id="e0ecc-190">たとえば、 *free_space* の割合が 30 の場合、使用される FILL FACTOR は 70 になります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-190">For example, if *free_space* percentage is 30, then the fill factor used is 70.</span></span> <span data-ttu-id="e0ecc-191">*free_space* の割合の値に 100 が指定された場合は、最初の FILL FACTOR 値を使用してインデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-191">If a *free_space* percentage value of 100 is specified, then the indexes are rebuilt with the original fill factor value.</span></span>  
  
 <span data-ttu-id="e0ecc-192">インデックスが計算列にある場合、 **-RebldIdx** を使用するときに **-SupportComputedColumn**引数も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-192">If the indexes are on computed columns, you must also specify the **-SupportComputedColumn** argument when you use **-RebldIdx**.</span></span>  
  
 <span data-ttu-id="e0ecc-193">**-RebldIdx**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-193">**-SupportComputedColumn**</span></span>  
 <span data-ttu-id="e0ecc-194">計算列に対して **sqlmaint** の DBCC メンテナンス コマンドを実行する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-194">Must be specified to run DBCC maintenance commands with **sqlmaint** on computed columns.</span></span>  
  
 <span data-ttu-id="e0ecc-195">**-WriteHistory**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-195">**-WriteHistory**</span></span>  
 <span data-ttu-id="e0ecc-196">**sqlmaint**によって実行される各メンテナンス操作に対して、msdb.dbo.sysdbmaintplan_history にエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-196">Specifies that an entry be made in msdb.dbo.sysdbmaintplan_history for each maintenance action performed by **sqlmaint**.</span></span> <span data-ttu-id="e0ecc-197">**-PlanName** または **-PlanID** が指定された場合、sysdbmaintplan_history のエントリには指定されたプランの ID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-197">If **-PlanName** or **-PlanID** is specified, the entries in sysdbmaintplan_history use the ID of the specified plan.</span></span> <span data-ttu-id="e0ecc-198">**-D** が指定された場合、sysdbmaintplan_history のエントリはプラン ID にゼロ値を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-198">If **-D** is specified, the entries in sysdbmaintplan_history are made with zeroes for the plan ID.</span></span>  
  
 <span data-ttu-id="e0ecc-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span><span class="sxs-lookup"><span data-stu-id="e0ecc-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span></span>  
 <span data-ttu-id="e0ecc-200">バックアップ操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-200">Specifies a backup action.</span></span> <span data-ttu-id="e0ecc-201">**-BkUpDb** はデータベース全体をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-201">**-BkUpDb** backs up the entire database.</span></span> <span data-ttu-id="e0ecc-202">**-BkUpLog** はトランザクション ログのみをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-202">**-BkUpLog** backs up only the transaction log.</span></span>  
  
 <span data-ttu-id="e0ecc-203">*backup_path* には、バックアップを格納するディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-203">*backup_path* specifies the directory for the backup.</span></span> <span data-ttu-id="e0ecc-204">*backup_path* は、 **-UseDefDir** も指定されている場合は必要ありません。ただし両方が指定されている場合は、 **-UseDefDir** によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-204">*backup_path* is not needed if **-UseDefDir** is also specified, and is overridden by **-UseDefDir** if both are specified.</span></span> <span data-ttu-id="e0ecc-205">バックアップは、ディレクトリまたはテープ デバイス アドレス ( \\\\.\TAPE0 など) に格納することができます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-205">The backup can be placed in a directory or a tape device address (for example, \\\\.\TAPE0).</span></span> <span data-ttu-id="e0ecc-206">データベース バックアップのファイル名は、次のように自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-206">The file name for a database backup is generated automatically as follows:</span></span>  
  
```  
dbname_db_yyyyMMddhhmm.BAK  
  
```  
  
 <span data-ttu-id="e0ecc-207">where</span><span class="sxs-lookup"><span data-stu-id="e0ecc-207">where</span></span>  
  
-   <span data-ttu-id="e0ecc-208">*dbname* はバックアップするデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-208">*dbname* is the name of the database being backed up.</span></span>  
  
-   <span data-ttu-id="e0ecc-209">*yyyyMMddhhmm* はバックアップ操作の日時です ( *yyyy* = 年、 *MM* = 月、 *dd* = 日、 *hh* = 時間、 *mm* = 分)。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-209">*yyyyMMddhhmm* is the time of the backup operation with *yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, and *mm* = minute.</span></span>  
  
 <span data-ttu-id="e0ecc-210">トランザクション バックアップ用のファイル名は、次のように同じ形式を使用して自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-210">The file name for a transaction backup is generated automatically with a similar format:</span></span>  
  
```  
dbname_log_yyyymmddhhmm.BAK  
  
```  
  
 <span data-ttu-id="e0ecc-211">**-BkUpDB** パラメーターを使用する場合は、 **-BkUpMedia** パラメーターを使用してメディアを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-211">If you use the **-BkUpDB** parameter, you must also specify the media by using the **-BkUpMedia** parameter.</span></span>  
  
 <span data-ttu-id="e0ecc-212">**-BkUpMedia**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-212">**-BkUpMedia**</span></span>  
 <span data-ttu-id="e0ecc-213">バックアップのメディアの種類 (DISK または TAPE) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-213">Specifies the media type of the backup, either DISK or TAPE.</span></span>  
  
 <span data-ttu-id="e0ecc-214">**DISK**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-214">**DISK**</span></span>  
 <span data-ttu-id="e0ecc-215">バックアップ メディアがディスクであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-215">Specifies that the backup medium is disk.</span></span>  
  
 <span data-ttu-id="e0ecc-216">**-DelBkUps**\< *time_period* ></span><span class="sxs-lookup"><span data-stu-id="e0ecc-216">**-DelBkUps**\< *time_period* ></span></span>  
 <span data-ttu-id="e0ecc-217">ディスク バックアップの場合で、バックアップ作成後の期間が \<*time_period*> を超える場合、バックアップ ディレクトリ内にあるすべてのバックアップ ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-217">For disk backups, specifies that any backup file in the backup directory be deleted if the time interval after the creation of the backup exceeds the \<*time_period*>.</span></span>  
  
 <span data-ttu-id="e0ecc-218">**-CrBkSubDir**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-218">**-CrBkSubDir**</span></span>  
 <span data-ttu-id="e0ecc-219">ディスク バックアップの場合で、[*backup_path*] ディレクトリ内、または **-UseDefDir** が指定されている場合は、既定のバックアップ ディレクトリ内にサブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-219">For disk backups, specifies that a subdirectory be created in the [*backup_path*] directory or in the default backup directory if **-UseDefDir** is also specified.</span></span> <span data-ttu-id="e0ecc-220">サブディレクトリの名前は、 **-D**に指定されるデータベース名を基に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-220">The name of the subdirectory is generated from the database name specified in **-D**.</span></span> <span data-ttu-id="e0ecc-221">**-CrBkSubDir** を使用すると、 *backup_path* パラメーターを変更せずに、異なるデータベースのすべてのバックアップを、個別のサブディレクトリに簡単に格納することができます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-221">**-CrBkSubDir** offers an easy way to put all the backups for different databases into separate subdirectories without having to change the *backup_path* parameter.</span></span>  
  
 <span data-ttu-id="e0ecc-222">**-UseDefDir**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-222">**-UseDefDir**</span></span>  
 <span data-ttu-id="e0ecc-223">ディスク バックアップの場合、既定のバックアップ ディレクトリにバックアップ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-223">For disk backups, specifies that the backup file be created in the default backup directory.</span></span> <span data-ttu-id="e0ecc-224">**UseDefDir** は、*backup_path* をオーバーライドします (両方が指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-224">**UseDefDir** overrides *backup_path* if both are specified.</span></span> <span data-ttu-id="e0ecc-225">既定の [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップでは、既定のバックアップ ディレクトリは C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-225">With a default [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup, the default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="e0ecc-226">**TAPE**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-226">**TAPE**</span></span>  
 <span data-ttu-id="e0ecc-227">バックアップ メディアがテープであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-227">Specifies that the backup medium is tape.</span></span>  
  
 <span data-ttu-id="e0ecc-228">**-BkUpOnlyIfClean**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-228">**-BkUpOnlyIfClean**</span></span>  
 <span data-ttu-id="e0ecc-229">指定されたすべての **-Ck** チェックでデータに問題が検出されなかった場合のみ、バックアップを行います。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-229">Specifies that the backup occur only if any specified **-Ck** checks did not find problems with the data.</span></span> <span data-ttu-id="e0ecc-230">メンテナンス操作は、コマンド プロンプトでの指定と同じ順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-230">Maintenance actions run in the same sequence as they appear in the command prompt.</span></span> <span data-ttu-id="e0ecc-231">**-BkUpOnlyIfClean**を指定する場合、またはチェックで問題がレポートされるかどうかに関係なくバックアップが発生する場合は、 **-BkUpDB**-BkUpLog **パラメーターの前に**-CkDB **、** -CkDBNoIdx **、** -CkAl **、** -CkAlNoIdx **、** / **-CkTxtAl** 、または **-CkCat**のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-231">Specify the parameters **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** before the **-BkUpDB**/**-BkUpLog** parameter(s) if you are also going to specify **-BkUpOnlyIfClean**, or the backup occurs whether or not the check reports problems.</span></span>  
  
 <span data-ttu-id="e0ecc-232">**-VrfyBackup**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-232">**-VrfyBackup**</span></span>  
 <span data-ttu-id="e0ecc-233">バックアップの完了時、バックアップに対して RESTORE VERIFYONLY を実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-233">Specifies that RESTORE VERIFYONLY be run on the backup when it completes.</span></span>  
  
 <span data-ttu-id="e0ecc-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span><span class="sxs-lookup"><span data-stu-id="e0ecc-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span></span>  
 <span data-ttu-id="e0ecc-235">レポートまたはバックアップ ファイルを削除する時期であるかどうかを判断するための期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-235">Specifies the time interval used to determine if a report or backup file is old enough to be deleted.</span></span> <span data-ttu-id="e0ecc-236">*number* は整数値で、続けてスペースを含めずに時間単位を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-236">*number* is an integer followed (without a space) by a unit of time.</span></span> <span data-ttu-id="e0ecc-237">次は有効な例です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-237">Valid examples:</span></span>  
  
-   <span data-ttu-id="e0ecc-238">**12weeks**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-238">**12weeks**</span></span>  
  
-   <span data-ttu-id="e0ecc-239">**3months**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-239">**3months**</span></span>  
  
-   <span data-ttu-id="e0ecc-240">**15days**</span><span class="sxs-lookup"><span data-stu-id="e0ecc-240">**15days**</span></span>  
  
 <span data-ttu-id="e0ecc-241">*number* だけを指定する場合、既定では、 **weeks**と見なされます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-241">If only *number* is specified, the default date part is **weeks**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0ecc-242">解説</span><span class="sxs-lookup"><span data-stu-id="e0ecc-242">Remarks</span></span>  
 <span data-ttu-id="e0ecc-243">**sqlmaint** ユーティリティは、1 つまたは複数のデータベースでメンテナンス操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-243">The **sqlmaint** utility performs maintenance operations on one or more databases.</span></span> <span data-ttu-id="e0ecc-244">**-D** を指定する場合、残りのスイッチで指定する操作は指定したデータベースでのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-244">If **-D** is specified, the operations specified in the remaining switches are performed only on the specified database.</span></span> <span data-ttu-id="e0ecc-245">**-PlanName** または **-PlanID** が指定された場合、指定されたメンテナンス プランから **sqlmaint** が取得する情報は、プラン内のデータベースのリストのみです。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-245">If **-PlanName** or **-PlanID** are specified, the only information **sqlmaint** retrieves from the specified maintenance plan is the list of databases in the plan.</span></span> <span data-ttu-id="e0ecc-246">その他の **sqlmaint** パラメーターに指定されるすべての操作は、プランから取得されたリスト内の各データベースに対して適用されます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-246">All operations specified in the remaining **sqlmaint** parameters are applied against each database in the list obtained from the plan.</span></span> <span data-ttu-id="e0ecc-247">**sqlmaint** ユーティリティでは、プラン自体に定義されているメンテナンス操作は適用されません。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-247">The **sqlmaint** utility does not apply any of the maintenance activities defined in the plan itself.</span></span>  
  
 <span data-ttu-id="e0ecc-248">**sqlmaint** ユーティリティは、実行が成功した場合には 0 を、実行が失敗した場合には 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-248">The **sqlmaint** utility returns 0 if it runs successfully or 1 if it fails.</span></span> <span data-ttu-id="e0ecc-249">失敗は次の場合にレポートされます。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-249">Failure is reported:</span></span>  
  
-   <span data-ttu-id="e0ecc-250">メンテナンス作業のすべてが失敗した場合。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-250">If any of the maintenance actions fail.</span></span>  
  
-   <span data-ttu-id="e0ecc-251">**-CkDB**、 **-CkDBNoIdx**、 **-CkAl**、 **-CkAlNoIdx**、 **-CkTxtAl**、または **-CkCat** のチェックでデータの問題が検出された場合。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-251">If **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** checks find problems with the data.</span></span>  
  
-   <span data-ttu-id="e0ecc-252">一般エラーが発生した場合。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-252">If a general failure is encountered.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="e0ecc-253">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="e0ecc-253">Permissions</span></span>  
 <span data-ttu-id="e0ecc-254">**に対して** 読み取りおよび実行 **権限のある Windows ユーザーが、** sqlmaint `sqlmaint.exe`ユーティリティを実行できます。このファイルは、既定では `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` フォルダーに格納されています。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-254">The **sqlmaint** utility can be executed by any Windows user with **Read and Execute** permission on `sqlmaint.exe`, which by default is stored in the `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` folder.</span></span> <span data-ttu-id="e0ecc-255">さらに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -login_ID **で指定される** ログインは、指定の操作を実行するのに必要な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-255">Additionally, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login specified with **-login_ID** must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span> <span data-ttu-id="e0ecc-256">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] への接続で Windows 認証を使用する場合、認証される Windows ユーザーにマップされている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインが指定の操作を実行するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-256">If the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses Windows Authentication, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login mapped to the authenticated Windows user must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span>  
  
 <span data-ttu-id="e0ecc-257">たとえば、 **-BkUpDB** を使用するには、BACKUP ステートメントを実行するための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-257">For example, using the **-BkUpDB** requires permission to execute the BACKUP statement.</span></span> <span data-ttu-id="e0ecc-258">また、 **-UpdOptiStats** 引数を使用するには、UPDATE STATISTICS ステートメントを実行するための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-258">And using the **-UpdOptiStats** argument requires permission to execute the UPDATE STATISTICS statement.</span></span> <span data-ttu-id="e0ecc-259">詳細については、オンライン ブックの該当トピックで「権限」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0ecc-259">For more information, see the "Permissions" sections of the corresponding topics in Books Online.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e0ecc-260">例</span><span class="sxs-lookup"><span data-stu-id="e0ecc-260">Examples</span></span>  
  
### <a name="a-performing-dbcc-checks-on-a-database"></a><span data-ttu-id="e0ecc-261">A.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-261">A.</span></span> <span data-ttu-id="e0ecc-262">データベースで DBCC チェックを実行する</span><span class="sxs-lookup"><span data-stu-id="e0ecc-262">Performing DBCC checks on a database</span></span>  
  
```  
sqlmaint -S MyServer -D AdventureWorks2012 -CkDB -CkAl -CkCat -Rpt C:\MyReports\AdvWks_chk.rpt  
```  
  
### <a name="b-updating-statistics-using-a-15-sample-in-all-databases-in-a-plan-also-shrink-any-of-the-database-that-have-reached-110-mb-to-having-only-10-free-space"></a><span data-ttu-id="e0ecc-263">B.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-263">B.</span></span> <span data-ttu-id="e0ecc-264">プラン内にあるすべてのデータベースから 15% のサンプルを使用して統計を更新し、</span><span class="sxs-lookup"><span data-stu-id="e0ecc-264">Updating statistics using a 15% sample in all databases in a plan.</span></span> <span data-ttu-id="e0ecc-265">110 MB に達したすべてのデータベースを圧縮して、10% の未使用領域を確保する</span><span class="sxs-lookup"><span data-stu-id="e0ecc-265">Also, shrink any of the database that have reached 110 MB to having only 10% free space</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -UpdOptiStats 15 -RmUnusedSpace 110 10  
```  
  
### <a name="c-backing-up-all-the-databases-in-a-plan-to-their-individual-subdirectories-in-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory-also-delete-any-backups-older-than-2-weeks"></a><span data-ttu-id="e0ecc-266">C.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-266">C.</span></span> <span data-ttu-id="e0ecc-267">既定の x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup ディレクトリ内にある個別のサブディレクトリに、プラン内のすべてのデータベースをバックアップし、</span><span class="sxs-lookup"><span data-stu-id="e0ecc-267">Backing up all the databases in a plan to their individual subdirectories in the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span> <span data-ttu-id="e0ecc-268">2 週間を経過したバックアップはすべて削除する</span><span class="sxs-lookup"><span data-stu-id="e0ecc-268">Also, delete any backups older than 2 weeks</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -BkUpDB -BkUpMedia DISK -UseDefDir -CrBkSubDir -DelBkUps 2weeks  
```  
  
### <a name="d-backing-up-a-database-to-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory"></a><span data-ttu-id="e0ecc-269">D.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-269">D.</span></span> <span data-ttu-id="e0ecc-270">既定の x:\Program にデータベースをバックアップする Server\MSSQL12.MSSQLSERVER\MSSQL\Backup ディレクトリ。 </span><span class="sxs-lookup"><span data-stu-id="e0ecc-270">Backing up a database to the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span>\  
  
```  
sqlmaint -S MyServer -BkUpDB -BkUpMedia DISK -UseDefDir  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0ecc-271">参照</span><span class="sxs-lookup"><span data-stu-id="e0ecc-271">See Also</span></span>  
 <span data-ttu-id="e0ecc-272">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0ecc-272">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="e0ecc-273">UPDATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e0ecc-273">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
