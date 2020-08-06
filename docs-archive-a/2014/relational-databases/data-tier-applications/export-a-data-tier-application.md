---
title: データ層アプリケーションのエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportdac.settings.f1
- sql12.swb. exportdac.settings.f1
- sql12.swb.exportdac.welcome.f1
- sql12.swb. exportdac.summary.f1
- sql12.swb.exportdac.progress.f1
- sql12.swb.exportdac.summary.f1
- sql12.swb.exportdac.results.f1
- sql12.swb. exportdac.results.f1
helpviewer_keywords:
- How to [DAC], export
- wizard [DAC], export
- export DAC
- data-tier application [SQL Server], export
ms.assetid: 61915bc5-0f5f-45ac-8cfe-3452bc185558
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5e1bbfc5c38dee5e7f29598086d87b680880641
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643950"
---
# <a name="export-a-data-tier-application"></a><span data-ttu-id="39acf-102">データ層アプリケーションのエクスポート</span><span class="sxs-lookup"><span data-stu-id="39acf-102">Export a Data-tier Application</span></span>
  <span data-ttu-id="39acf-103">配置されているデータ層アプリケーション (DAC) またはデータベースをエクスポートすると、エクスポート ファイルが作成されます。このファイルには、データベース内のオブジェクトの定義に加え、テーブルに格納されているすべてのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39acf-103">Exporting a deployed data-tier application (DAC) or database creates an export file that includes both the definitions of the objects in the database and all of the data contained in the tables.</span></span> <span data-ttu-id="39acf-104">さらに、このエクスポート ファイルを [!INCLUDE[ssDE](../../includes/ssde-md.md)]の別のインスタンスまたは [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]にインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="39acf-104">The export file can then be imported to another instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="39acf-105">エクスポートとインポートという操作を組み合わせることで、DAC をインスタンス間で移行したり論理バックアップを作成したりすることが可能です。または、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] に配置されているデータベースの社内用コピーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="39acf-105">The export-import operations can be combined to migrate a DAC between instances, to create a logical backup, or to create an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="39acf-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="39acf-106">Before You Begin</span></span>  
 <span data-ttu-id="39acf-107">エクスポート プロセスでは、2 つの段階を経て DAC エクスポート ファイルが構築されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-107">The export process builds a DAC export file in two stages.</span></span>  
  
1.  <span data-ttu-id="39acf-108">エクスポートではエクスポート ファイル (BACPAC ファイル) に DAC 定義が構築されます。DAC の抽出時には DAC パッケージ ファイルに DAC 定義が構築されますが、これと同様の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="39acf-108">The export builds a DAC definition in the export file - BACPAC file - in the same way a DAC extract builds a DAC definition in a DAC package file.</span></span> <span data-ttu-id="39acf-109">エクスポートされた DAC 定義には、現在のデータベース内のすべてのオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="39acf-109">The exported DAC definition includes all of the objects in the current database.</span></span> <span data-ttu-id="39acf-110">もともと DAC から配置され、その後直接変更が加えられたデータベースに対してエクスポート プロセスが実行された場合、エクスポートされる定義は、データベース内のオブジェクト セットと一致し、元の DAC に定義されている内容とは一致しません。</span><span class="sxs-lookup"><span data-stu-id="39acf-110">If the export process is run against a database that was originally deployed from a DAC, and changes were made directly to the database after deployment, the exported definition matches the object set in the database, not what was defined in the original DAC.</span></span>  
  
2.  <span data-ttu-id="39acf-111">データベース内のすべてのテーブルからデータが一括コピーされて、エクスポート ファイルに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="39acf-111">The export bulk copies out the data from all of the tables in the database and incorporates the data into the export file.</span></span>  
  
 <span data-ttu-id="39acf-112">エクスポート プロセスでは、DAC バージョンが 1.0.0.0 に設定され、エクスポート ファイル内の DAC の説明は空の文字列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-112">The export process sets the DAC version to 1.0.0.0 and the DAC description in the export file to an empty string.</span></span> <span data-ttu-id="39acf-113">データベースが DAC から配置された場合、エクスポート ファイル内の DAC 定義には、元の DAC に割り当てられた名前が格納されます。それ以外の場合、DAC 名はデータベース名に設定されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-113">If the database was deployed from a DAC, the DAC definition in the export file contains the name given to the original DAC, otherwise the DAC name is set to the database name.</span></span>  
  

###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="39acf-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="39acf-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="39acf-115">DAC またはデータベースをエクスポートできるのは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 以降のデータベースに限られます。</span><span class="sxs-lookup"><span data-stu-id="39acf-115">A DAC or database can only be exported from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
 <span data-ttu-id="39acf-116">DAC でサポートされていないオブジェクトまたは包含ユーザーが存在するデータベースはエクスポートできません。</span><span class="sxs-lookup"><span data-stu-id="39acf-116">You cannot export a database that has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="39acf-117">DAC でサポートされるオブジェクトの種類の詳細については、「 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39acf-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="39acf-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="39acf-118">Permissions</span></span>  
 <span data-ttu-id="39acf-119">DAC をエクスポートするには、少なくとも ALTER ANY LOGIN 権限とデータベース スコープの VIEW DEFINITION 権限、および **sys.sql_expression_dependencies**に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="39acf-119">Exporting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="39acf-120">DAC をエクスポートできるのは、DAC をエクスポートするデータベースの database_owner 固定データベース ロールのメンバーでもある、securityadmin 固定サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="39acf-120">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="39acf-121">sysadmin 固定サーバー ロールのメンバーまたは **sa** という組み込みの SQL Server システム管理者アカウントも DAC をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="39acf-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
##  <a name="using-the-export-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="39acf-122">データ層アプリケーションのエクスポートウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="39acf-122">Using the Export Data-tier Application Wizard</span></span>  
 <span data-ttu-id="39acf-123">**ウィザードを使用して DAC をエクスポートするには**</span><span class="sxs-lookup"><span data-stu-id="39acf-123">**To Export a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="39acf-124">内部設置型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内で、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="39acf-124">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="39acf-125">**オブジェクト エクスプローラー**で、DAC のエクスポート元のインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="39acf-125">In **Object Explorer**, expand the node for the instance from which you want to export the DAC.</span></span>  
  
3.  <span data-ttu-id="39acf-126">データベース名を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="39acf-126">Right-click the database name.</span></span>  
  
4.  <span data-ttu-id="39acf-127">[**タスク**] をクリックし、[**データ層アプリケーションのエクスポート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39acf-127">Click **Tasks** and then select **Export Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="39acf-128">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="39acf-128">Complete the wizard dialogs:</span></span>  
  
    -   <span data-ttu-id="39acf-129">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="39acf-129">[Introduction Page](#Introduction)</span></span>  
  
    -   <span data-ttu-id="39acf-130">[[エクスポートの設定] ページ](#Export_settings)</span><span class="sxs-lookup"><span data-stu-id="39acf-130">[Export Settings Page](#Export_settings)</span></span>  
  
    -   <span data-ttu-id="39acf-131">[[検証] ページ](#Validation)</span><span class="sxs-lookup"><span data-stu-id="39acf-131">[Validation Page](#Validation)</span></span>  
  
    -   <span data-ttu-id="39acf-132">[[概要] ページ](#Summary)</span><span class="sxs-lookup"><span data-stu-id="39acf-132">[Summary Page](#Summary)</span></span>  
  
    -   <span data-ttu-id="39acf-133">[[進行状況] ページ](#Progress)</span><span class="sxs-lookup"><span data-stu-id="39acf-133">[Progress Page](#Progress)</span></span>  
  
    -   <span data-ttu-id="39acf-134">[[結果] ページ](#Results)</span><span class="sxs-lookup"><span data-stu-id="39acf-134">[Results Page](#Results)</span></span>  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="39acf-135">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="39acf-135">Introduction Page</span></span>  
 <span data-ttu-id="39acf-136">このページには、データ層アプリケーションのエクスポート ウィザードの手順が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-136">This page describes the steps for the Export Data-tier Application Wizard.</span></span>  
  
 <span data-ttu-id="39acf-137">**Options**</span><span class="sxs-lookup"><span data-stu-id="39acf-137">**Options**</span></span>  
  
 <span data-ttu-id="39acf-138">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="39acf-138">**Do not show this page again.**</span></span> <span data-ttu-id="39acf-139">: 今後 [説明] ページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="39acf-139">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="39acf-140">**[次へ]** : **[DAC パッケージの選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="39acf-140">**Next** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="39acf-141">**[キャンセル]** : 操作を取り消し、ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="39acf-141">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="export-settings-page"></a><a name="Export_settings"></a><span data-ttu-id="39acf-142">[設定のエクスポート] ページ</span><span class="sxs-lookup"><span data-stu-id="39acf-142">Export Settings Page</span></span>  
 <span data-ttu-id="39acf-143">このページを使用して、BACPAC ファイルを作成する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="39acf-143">Use this page to specify the location where you want the BACPAC file to be created.</span></span>  
  
-   <span data-ttu-id="39acf-144">**[ローカル ディスクに保存]** : BACPAC ファイルをローカル コンピューター上のディレクトリに作成します。</span><span class="sxs-lookup"><span data-stu-id="39acf-144">**Save to local disk** - Creates a BACPAC file in a directory on the local computer.</span></span> <span data-ttu-id="39acf-145">**[参照]** をクリックしてローカル コンピューター内を参照するか、用意されている領域にパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="39acf-145">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="39acf-146">パス名には、ファイル名および .bacpac 拡張子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="39acf-146">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="39acf-147">**[Save to Azure]\(Azure に保存\)**: BACPAC ファイルを Azure コンテナーに作成します。</span><span class="sxs-lookup"><span data-stu-id="39acf-147">**Save to Azure** - Creates a BACPAC file in an Azure container.</span></span> <span data-ttu-id="39acf-148">このオプションを検証するためには、Azure コンテナーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39acf-148">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="39acf-149">このオプションでは、一時ファイル用のローカル ディレクトリを指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="39acf-149">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="39acf-150">一時ファイルは、指定した場所に作成され、操作の完了後も残ります。</span><span class="sxs-lookup"><span data-stu-id="39acf-150">Note that the temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
 <span data-ttu-id="39acf-151">エクスポートするテーブルのサブセットを指定するには、 **[詳細]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="39acf-151">To specify a subset of tables to export, use the **Advanced** option.</span></span>  
  
##  <a name="validation-page"></a><a name="Validation"></a><span data-ttu-id="39acf-152">[検証] ページ</span><span class="sxs-lookup"><span data-stu-id="39acf-152">Validation Page</span></span>  
 <span data-ttu-id="39acf-153">[検証] ページを使用して、操作の妨げとなる問題を確認します。</span><span class="sxs-lookup"><span data-stu-id="39acf-153">Use the validation page to review any issues that block the operation.</span></span> <span data-ttu-id="39acf-154">続行するには、妨げとなる問題を解決し、 **[検証の再実行]** をクリックして、検証が成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="39acf-154">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="39acf-155">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39acf-155">To continue, click **Next**.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="39acf-156">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="39acf-156">Summary Page</span></span>  
 <span data-ttu-id="39acf-157">このページを使用すると、操作の指定ソースとターゲットの設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="39acf-157">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="39acf-158">指定した設定でエクスポート操作を実行するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39acf-158">To complete the export operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="39acf-159">エクスポート操作をキャンセルしてウィザードを終了するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39acf-159">To cancel the export operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="39acf-160">[進行状況] ページ</span><span class="sxs-lookup"><span data-stu-id="39acf-160">Progress Page</span></span>  
 <span data-ttu-id="39acf-161">このページには、操作の進行状況を示す進行状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-161">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="39acf-162">詳細な状態を表示するには、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39acf-162">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="39acf-163">[結果] ページ</span><span class="sxs-lookup"><span data-stu-id="39acf-163">Results Page</span></span>  
 <span data-ttu-id="39acf-164">このページでは、エクスポート操作の成功と失敗が報告され、各アクションの結果が示されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-164">This page reports the success or failure of the export operation, showing the results of each action.</span></span> <span data-ttu-id="39acf-165">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39acf-165">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="39acf-166">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39acf-166">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="39acf-167">[**完了**] をクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="39acf-167">Click **Finish** to close the Wizard.</span></span>  
  
##  <a name="using-a-net-framework-application"></a><a name="NetApp"></a><span data-ttu-id="39acf-168">.Net Framework アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="39acf-168">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="39acf-169">**.Net Framework アプリケーションで Export() メソッドを使用して DAC をエクスポートするには**</span><span class="sxs-lookup"><span data-stu-id="39acf-169">**To export a DAC using the Export() method in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="39acf-170">コード例を参照するには、 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)上の DAC サンプル アプリケーションをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="39acf-170">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="39acf-171">SMO サーバー オブジェクトを作成し、エクスポートする DAC が含まれたインスタンスにそれを設定します。</span><span class="sxs-lookup"><span data-stu-id="39acf-171">Create a SMO Server object and set it to the instance that contains the DAC to be exported.</span></span>  
  
2.  <span data-ttu-id="39acf-172">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="39acf-172">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="39acf-173">`Export` 型の `Microsoft.SqlServer.Management.Dac.DacStore` メソッドを使用して、DAC をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="39acf-173">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the DAC.</span></span> <span data-ttu-id="39acf-174">エクスポートする DAC の名前と、エクスポート ファイルの出力先となるフォルダーのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="39acf-174">Specify the name of the DAC to be exported, and the path to the folder where the export file is to be placed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39acf-175">参照</span><span class="sxs-lookup"><span data-stu-id="39acf-175">See Also</span></span>  
 <span data-ttu-id="39acf-176">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="39acf-176">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="39acf-177">データベースから DAC を抽出する</span><span class="sxs-lookup"><span data-stu-id="39acf-177">Extract a DAC From a Database</span></span>](extract-a-dac-from-a-database.md)  
  
  
