---
title: BACPAC ファイルのインポートによる新しいユーザー データベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.importdac.progress.f1
- sql12.swb. importdac.settings.f1
- sql12.swb.importdac.storagebrowser.f1
- sql12.swb. importdac.summary.f1
- sql12.swb.importdac.results.f1
- sql12.swb. importdac.progress.f1
- sql12.swb.importdac.welcome.f1
- sql12.swb.importdac.settings.f1
- sql12.swb. importdac.results.f1
- sql12.swb.importdac.summary.f1
helpviewer_keywords:
- Data-tier application
- SQL Server DAC
- Migrate database
- DAC
ms.assetid: 736d8d9a-39f1-4bf8-b81f-2e56c134d12e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66e71453f38fe15f295fceaf63b5edba5ab5ff43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643405"
---
# <a name="import-a-bacpac-file-to-create-a-new-user-database"></a><span data-ttu-id="c3ef6-102">BACPAC ファイルのインポートによる新しいユーザー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="c3ef6-102">Import a BACPAC File to Create a New User Database</span></span>
  <span data-ttu-id="c3ef6-103">データ層アプリケーション (DAC) ファイル (.bacpac ファイル) をインポートすると、データを含んだ元のデータベースのコピーを、[!INCLUDE[ssDE](../../includes/ssde-md.md)] の新しいインスタンス上または [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-103">Import a data-tier application (DAC) file - a .bacpac file - to create a copy of the original database, with the data, on a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="c3ef6-104">エクスポートとインポートという操作を組み合わせることで、DAC またはデータベースをインスタンス間で移行したり論理バックアップを作成したりすることが可能です。たとえば、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]に配置されているデータベースの社内用コピーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-104">Export-import operations can be combined to migrate a DAC or database between instances, or to create a logical backup, such as creating an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="c3ef6-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="c3ef6-105">Before You Begin</span></span>  
 <span data-ttu-id="c3ef6-106">インポート プロセスでは、2 つの段階を経て新しい DAC が構築されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-106">The import process builds a new DAC in two stages.</span></span>  
  
1.  <span data-ttu-id="c3ef6-107">エクスポート ファイルに格納されている DAC 定義を使用して、新しい DAC および関連するデータベースを作成します。DAC の配置時には、DAC パッケージ ファイル内の定義から新しい DAC が作成されますが、その場合と同じ方法で作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-107">The import creates a new DAC and associated database using the DAC definition stored in the export file, the same way a DAC deploy creates a new DAC from the definition in a DAC package file.</span></span>  
  
2.  <span data-ttu-id="c3ef6-108">エクスポート ファイルからデータを一括コピーします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-108">The import bulk copies in the data from the export file.</span></span>  
  
 
## <a name="sql-server-utility"></a><span data-ttu-id="c3ef6-109">SQL Server ユーティリティ (SQL Server Utility)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-109">SQL Server Utility</span></span>  
 <span data-ttu-id="c3ef6-110">データベース エンジンのマネージド インスタンスに DAC をインポートした場合、そのインポートした DAC は、次回ユーティリティ コレクション セットがインスタンスからユーティリティ コントロール ポイントへと送信されるときに SQL Server ユーティリティに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-110">If you import a DAC to a managed instance of the Database Engine, the imported DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="c3ef6-111">その後、DAC は  **の**ユーティリティ エクスプローラー[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の **[配置済みのデータ層アプリケーション]** ノードに現れるようになり、 **[配置済みのデータ層アプリケーション]** の詳細ページで報告されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-111">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
## <a name="database-options-and-settings"></a><span data-ttu-id="c3ef6-112">データベースのオプションと設定</span><span class="sxs-lookup"><span data-stu-id="c3ef6-112">Database Options and Settings</span></span>  
 <span data-ttu-id="c3ef6-113">既定では、インポート時に作成されたデータベースには、CREATE DATABASE ステートメントによる既定の設定がすべて適用されます。ただし、データベースの照合順序および互換性レベルは、DAC のエクスポート ファイルで定義された値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-113">By default, the database created during the import will have all of the default settings from the CREATE DATABASE statement, except that the database collation and compatibility level are set to the values defined in the DAC export file.</span></span> <span data-ttu-id="c3ef6-114">DAC のエクスポート ファイルには、元のデータベースに基づく値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-114">A DAC export file uses the values from the original database.</span></span>  
  
 <span data-ttu-id="c3ef6-115">TRUSTWORTHY、DB_CHAINING、HONOR_BROKER_PRIORITY など、データベース オプションによっては、インポート作業中の調整はできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-115">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the import process.</span></span> <span data-ttu-id="c3ef6-116">ファイル グループの数、ファイルの数やサイズなどの物理プロパティは、インポート作業中に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-116">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the import process.</span></span> <span data-ttu-id="c3ef6-117">インポートが完了すれば、ALTER DATABASE ステートメント、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell を使用して、データベースを調整できます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-117">After the import completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span> <span data-ttu-id="c3ef6-118">詳細については、「 [Databases](../databases/databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-118">For more information, see [Databases](../databases/databases.md).</span></span>  
  
## <a name="limitations-and-restrictions"></a><span data-ttu-id="c3ef6-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c3ef6-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c3ef6-120">DAC は、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]にインポートできるほか、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 4 (SP4) 以降を実行する [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] のインスタンスにインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-120">A DAC can be imported to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="c3ef6-121">新しいバージョンから DAC をエクスポートした場合、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ではサポートされないオブジェクトが DAC に含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-121">If you export a DAC from a higher version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="c3ef6-122">このような DAC を [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]のインスタンスに配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-122">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c3ef6-123">前提条件</span><span class="sxs-lookup"><span data-stu-id="c3ef6-123">Prerequisites</span></span>  
 <span data-ttu-id="c3ef6-124">ソースが不明または信頼されていない DAC エクスポート ファイルはインポートしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-124">We recommend that you do not import a DAC export file from unknown or untrusted sources.</span></span> <span data-ttu-id="c3ef6-125">こうしたファイルには、意図しない Transact-SQL コードを実行したり、スキーマを変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-125">Such files could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="c3ef6-126">エクスポート ファイルのソースが不明または信頼されていない場合は、使用する前に、DAC をアンパックして、ストアド プロシージャやその他のユーザー定義コードなどのコードも確認してください。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-126">Before you use an export file from an unknown or untrusted source, unpack the DAC and examine the code, like stored procedures and other user-defined code.</span></span> <span data-ttu-id="c3ef6-127">これらのチェックの実行方法の詳細については、「 [Validate a DAC Package](validate-a-dac-package.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-127">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="c3ef6-128">Security</span><span class="sxs-lookup"><span data-stu-id="c3ef6-128">Security</span></span>  
 <span data-ttu-id="c3ef6-129">セキュリティを強化するために、SQL Server 認証のログインは、パスワードなしで DAC エクスポート ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-129">To improve security, SQL Server Authentication logins are stored in a DAC export file without a password.</span></span> <span data-ttu-id="c3ef6-130">ファイルがインポートされると、ログインは、生成されたパスワードを伴う無効なログインとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-130">When the file is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="c3ef6-131">ログインを有効にするには、ALTER ANY LOGIN 権限を持つユーザーとしてログインし、ALTER LOGIN を使用してログインを有効にします。さらに、新しいパスワードを割り当て、そのパスワードを該当ユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-131">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="c3ef6-132">Windows 認証ログインの場合、ログインのパスワードは SQL Server で管理されていないため、この操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-132">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c3ef6-133">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="c3ef6-133">Permissions</span></span>  
 <span data-ttu-id="c3ef6-134">DAC をインポートできるのは、 **sysadmin** または **serveradmin** 固定サーバー ロールのメンバーか、 **dbcreator** 固定サーバー ロールに存在する ALTER ANY LOGIN 権限を持つログインのみです。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-134">A DAC can only be imported by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="c3ef6-135">あらかじめ登録された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウント ( **sa** ) も DAC をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-135">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="c3ef6-136">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれる DAC をインポートするには、loginmanager ロールまたは serveradmin ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-136">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="c3ef6-137">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] へのログインが含まれない DAC をインポートするには、dbmanager ロールまたは serveradmin ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-137">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
## <a name="using-the-import-data-tier-application-wizard"></a><span data-ttu-id="c3ef6-138">データ層アプリケーションのインポート ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="c3ef6-138">Using the Import Data-tier Application Wizard</span></span>  
 <span data-ttu-id="c3ef6-139">**ウィザードを起動するには、次の手順を実行します。**</span><span class="sxs-lookup"><span data-stu-id="c3ef6-139">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="c3ef6-140">内部設置型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内で、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-140">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3ef6-141">**オブジェクト エクスプローラー**で、 **[データベース]** を右クリックしてから、 **[データ層アプリケーションのインポート]** メニュー項目を選択してウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-141">In **Object Explorer**, right-click on **Databases**, and then select the **Import Data-tier Application** menu item to launch the wizard.</span></span>  
  
3.  <span data-ttu-id="c3ef6-142">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-142">Complete the wizard dialogs:</span></span>  
  
    -   <span data-ttu-id="c3ef6-143">[[説明] ページ](#Introduction)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-143">[Introduction Page](#Introduction)</span></span>  
  
    -   <span data-ttu-id="c3ef6-144">[[インポートの設定] ページ](#Import_settings)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-144">[Import Settings Page](#Import_settings)</span></span>  
  
    -   <span data-ttu-id="c3ef6-145">[[データベースの設定] ページ](#Database_settings)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-145">[Database Settings Page](#Database_settings)</span></span>  
  
    -   <span data-ttu-id="c3ef6-146">[[概要] ページ](#Summary)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-146">[Summary Page](#Summary)</span></span>  
  
    -   <span data-ttu-id="c3ef6-147">[[進行状況] ページ](#Progress)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-147">[Progress Page](#Progress)</span></span>  
  
    -   <span data-ttu-id="c3ef6-148">[[結果] ページ](#Results)</span><span class="sxs-lookup"><span data-stu-id="c3ef6-148">[Results Page](#Results)</span></span>  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="c3ef6-149">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-149">Introduction Page</span></span>  
 <span data-ttu-id="c3ef6-150">このページには、データ層アプリケーションのインポート ウィザードの手順が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-150">This page describes the steps for the Data-tier Application Import Wizard.</span></span>  
  
 <span data-ttu-id="c3ef6-151">**[オプション]**</span><span class="sxs-lookup"><span data-stu-id="c3ef6-151">**Options**</span></span>  
  
-   <span data-ttu-id="c3ef6-152">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="c3ef6-152">**Do not show this page again.**</span></span> <span data-ttu-id="c3ef6-153">: 今後 [説明] ページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="c3ef6-154">**[次へ]** : **[インポートの設定]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-154">**Next** - Proceeds to the **Import Settings** page.</span></span>  
  
-   <span data-ttu-id="c3ef6-155">**[キャンセル]** : 操作を取り消し、ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-155">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
###  <a name="import-settings-page"></a><a name="Import_settings"></a> <span data-ttu-id="c3ef6-156">[インポートの設定] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-156">Import Settings Page</span></span>  
 <span data-ttu-id="c3ef6-157">このページを使用して、インポートする .bacpac ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-157">Use this page to specify the location of the .bacpac file to import.</span></span>  
  
-   <span data-ttu-id="c3ef6-158">**[ローカル ディスクからインポート]** : **[参照]** をクリックしてローカル コンピューター内を参照するか、用意されている領域にパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-158">**Import from local disk** - Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="c3ef6-159">パス名には、ファイル名および .bacpac 拡張子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-159">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="c3ef6-160">**Azure からインポート**-BACPAC ファイルを azure コンテナーからインポートします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-160">**Import from Azure** - Imports a BACPAC file from an Azure container.</span></span> <span data-ttu-id="c3ef6-161">このオプションを検証するためには、Azure コンテナーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-161">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="c3ef6-162">このオプションでは、一時ファイル用のローカル ディレクトリを指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-162">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="c3ef6-163">一時ファイルは、指定した場所に作成され、操作の完了後も残ります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-163">The temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
     <span data-ttu-id="c3ef6-164">Azure を参照するときに、1 つのアカウント内のコンテナーを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-164">When browsing Azure, you will be able to switch between containers within a single account.</span></span> <span data-ttu-id="c3ef6-165">インポート操作を続行するには、1 つの .bacpac ファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-165">You must specify a single .bacpac file to continue the import operation.</span></span> <span data-ttu-id="c3ef6-166">列は、 **名前**、 **サイズ**、または **更新日時**で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-166">Note that you can sort columns by **Name**, **Size**, or **Date Modified**.</span></span>  
  
     <span data-ttu-id="c3ef6-167">続行するには、インポートする .bacpac ファイルを指定し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-167">To continue, specify the .bacpac file to import, and then click **Open**.</span></span>  
  
###  <a name="database-settings-page"></a><a name="Database_settings"></a> <span data-ttu-id="c3ef6-168">[データベースの設定] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-168">Database Settings Page</span></span>  
 <span data-ttu-id="c3ef6-169">このページを使用すると、作成されるデータベースの詳細を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-169">Use this page to specify details for the database that will be created.</span></span>  
  
 <span data-ttu-id="c3ef6-170">**SQLServer のローカル インスタンスの場合**</span><span class="sxs-lookup"><span data-stu-id="c3ef6-170">**For a local instance of SQL Server:**</span></span>  
  
-   <span data-ttu-id="c3ef6-171">**[新しいデータベース名]** : インポートするデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-171">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="c3ef6-172">**[データ ファイルのパス]** : データ ファイル用のローカル ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-172">**Data file path** - Provide a local directory for data files.</span></span> <span data-ttu-id="c3ef6-173">**[参照]** をクリックしてローカル コンピューター内を参照するか、用意されている領域にパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-173">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
-   <span data-ttu-id="c3ef6-174">**[ログ ファイルのパス]** : ログ ファイル用のローカル ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-174">**Log file path** - Provide a local directory for log files.</span></span> <span data-ttu-id="c3ef6-175">**[参照]** をクリックしてローカル コンピューター内を参照するか、用意されている領域にパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-175">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
 <span data-ttu-id="c3ef6-176">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-176">To continue, click **Next**.</span></span>  
  
 <span data-ttu-id="c3ef6-177">**SQL データベースの場合:**</span><span class="sxs-lookup"><span data-stu-id="c3ef6-177">**For a SQL Database:**</span></span>  
  
-   <span data-ttu-id="c3ef6-178">[**新しいデータベース名**-インポートされたデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-178">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="c3ef6-179">**の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] エディション**- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business または Web を指定し [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-179">**Edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** - Specify [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Web.</span></span> <span data-ttu-id="c3ef6-180">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]のエディションの詳細については、Web サイト「 [SQL データベース](https://www.windowsazure.com/home/tour/database/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-180">For more information about editions of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see this [SQL Database](https://www.windowsazure.com/home/tour/database/) web site.</span></span>  
  
-   <span data-ttu-id="c3ef6-181">[**データベースの最大サイズ (GB)** ]: ドロップダウンメニューを使用して、データベースの最大サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-181">**Maximum database size (GB)** - Use the drop-down menu to specify the maximum size for your database.</span></span>  
  
 <span data-ttu-id="c3ef6-182">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-182">To continue, click **Next**.</span></span>  
  
### <a name="validation-page"></a><span data-ttu-id="c3ef6-183">[検証] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-183">Validation Page</span></span>  
 <span data-ttu-id="c3ef6-184">このページを使用して、操作の妨げとなる問題を確認します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-184">Use this page to review any issues that block the operation.</span></span> <span data-ttu-id="c3ef6-185">続行するには、妨げとなる問題を解決し、 **[検証の再実行]** をクリックして、検証が成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-185">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="c3ef6-186">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-186">To continue, click **Next**.</span></span>  
  
###  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="c3ef6-187">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-187">Summary Page</span></span>  
 <span data-ttu-id="c3ef6-188">このページを使用すると、操作の指定ソースとターゲットの設定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-188">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="c3ef6-189">指定した設定でインポート操作を実行するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-189">To complete the import operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="c3ef6-190">インポート操作をキャンセルしてウィザードを終了するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-190">To cancel the import operation and exit the wizard, click **Cancel**.</span></span>  
  
###  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="c3ef6-191">[進行状況] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-191">Progress Page</span></span>  
 <span data-ttu-id="c3ef6-192">このページには、操作の進行状況を示す進行状況バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-192">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="c3ef6-193">詳細な状態を表示するには、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-193">To view detailed status, click the **View details** option.</span></span>  
  
 <span data-ttu-id="c3ef6-194">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-194">To continue, click **Next**.</span></span>  
  
###  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="c3ef6-195">[結果] ページ</span><span class="sxs-lookup"><span data-stu-id="c3ef6-195">Results Page</span></span>  
 <span data-ttu-id="c3ef6-196">このページでは、データベースのインポートや作成操作の成功と失敗が報告され、各アクションの成功または失敗が示されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-196">This page reports the success or failure of the import and create database operations, showing the success or failure of each action.</span></span> <span data-ttu-id="c3ef6-197">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-197">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="c3ef6-198">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-198">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="c3ef6-199">**[閉じる]** をクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c3ef6-199">Click **Close** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ef6-200">参照</span><span class="sxs-lookup"><span data-stu-id="c3ef6-200">See Also</span></span>  
 <span data-ttu-id="c3ef6-201">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c3ef6-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="c3ef6-202">データ層アプリケーションのエクスポート</span><span class="sxs-lookup"><span data-stu-id="c3ef6-202">Export a Data-tier Application</span></span>](export-a-data-tier-application.md)  
  
