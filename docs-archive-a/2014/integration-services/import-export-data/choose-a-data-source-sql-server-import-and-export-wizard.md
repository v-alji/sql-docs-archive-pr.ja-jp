---
title: '[データ ソースの選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 246c3b03bfefad83cbfc1d0110e1fd4cf0cedf7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642914"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a><span data-ttu-id="52872-102">[データ ソースの選択] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="52872-102">Choose a Data Source (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="52872-103">[**データソースの選択**] ページを使用すると、コピーするデータのソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="52872-103">Use the **Choose a Data Source** page to specify the source of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="52872-104">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="52872-105">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-105">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="52872-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="52872-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="52872-107">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="52872-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="52872-108">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="52872-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="52872-109">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="52872-110">Options</span><span class="sxs-lookup"><span data-stu-id="52872-110">Options</span></span>  
 <span data-ttu-id="52872-111">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="52872-111">**Data Source**</span></span>  
 <span data-ttu-id="52872-112">ソースのデータ保存形式に対応したデータ プロバイダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-112">Choose the data provider that matches the data storage format of the source.</span></span> <span data-ttu-id="52872-113">データ ソースに使用できるプロバイダーが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52872-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="52872-114">たとえば、では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、SQL Server の .NET Framework Data Provider、または SQL Server 用の Microsoft OLE DB プロバイダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="52872-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
 <span data-ttu-id="52872-115">**データソース**プロパティには、コンピューターにインストールされているプロバイダーに応じて、さまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="52872-115">The **Data Source** property has a variable number of options, which depend on the providers installed on the computer.</span></span> <span data-ttu-id="52872-116">次の表に、使用頻度の高いプロバイダーのオプションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="52872-116">The following tables list the options for some frequently used destinations.</span></span> <span data-ttu-id="52872-117">他のプロバイダーについては、プロバイダー固有のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-117">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="52872-118">動的オプション</span><span class="sxs-lookup"><span data-stu-id="52872-118">Dynamic Options</span></span>  
 <span data-ttu-id="52872-119">以下では、いくつかのデータ ソースで利用可能なオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="52872-119">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="52872-120">[データ ソース] のドロップダウンで利用可能なすべてのデータ ソースが、ここに一覧表示されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52872-120">Not all the data sources that are available in the Data Source drop-down are listed here.</span></span>  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="52872-121">[データ ソース] = [SQL Server Native Client] および [Microsoft OLE DB Provider for SQL Server]</span><span class="sxs-lookup"><span data-stu-id="52872-121">Data Source = SQL Server Native Client and Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="52872-122">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="52872-122">**Server name**</span></span>  
 <span data-ttu-id="52872-123">データが格納されているサーバーの名前を入力するか、一覧からサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-123">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="52872-124">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="52872-124">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="52872-125">データベースへのログインに、パッケージが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-125">Specify whether the package should use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication to log in to the database.</span></span> <span data-ttu-id="52872-126">より高いセキュリティのためには Windows 認証をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52872-126">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="52872-127">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="52872-127">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="52872-128">データベースへのログインに、パッケージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-128">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="52872-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52872-129">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="52872-130">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="52872-130">**User name**</span></span>  
 <span data-ttu-id="52872-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-131">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="52872-132">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="52872-132">**Password**</span></span>  
 <span data-ttu-id="52872-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-133">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="52872-134">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="52872-134">**Database**</span></span>  
 <span data-ttu-id="52872-135">指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベースの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-135">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="52872-136">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="52872-136">**Refresh**</span></span>  
 <span data-ttu-id="52872-137">**[更新]** をクリックして、利用可能なデータベースの一覧を復元します。</span><span class="sxs-lookup"><span data-stu-id="52872-137">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a><span data-ttu-id="52872-138">[データ ソース] = [.Net Framework Data Provider for SQL Server]</span><span class="sxs-lookup"><span data-stu-id="52872-138">Data Source = .NET Framework Data Provider for SQL Server</span></span>  
 <span data-ttu-id="52872-139">このページでは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ プロバイダーのオプションがアルファベット順で一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="52872-139">This page presents an alphabetical list of options for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52872-140">最も重要なオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="52872-140">The most important options are listed in the following table.</span></span>  
  
 <span data-ttu-id="52872-141">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="52872-141">**Data Source**</span></span>  
 <span data-ttu-id="52872-142">データが格納されているサーバーの名前を入力するか、一覧からサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-142">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="52872-143">**初期カタログ**</span><span class="sxs-lookup"><span data-stu-id="52872-143">**Initial Catalog**</span></span>  
 <span data-ttu-id="52872-144">ソース データベース名を入力します。</span><span class="sxs-lookup"><span data-stu-id="52872-144">Type the name of the source database.</span></span>  
  
 <span data-ttu-id="52872-145">**統合セキュリティ**</span><span class="sxs-lookup"><span data-stu-id="52872-145">**Integrated Security**</span></span>  
 <span data-ttu-id="52872-146">`True` を指定して Windows 統合認証を使用して接続するか (推奨)、`False` を指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="52872-146">Specify `True` to connect by using Windows integrated authentication, which is recommended, or `False` to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="52872-147">`False` を指定した場合は、ユーザー ID とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52872-147">If you specify `False`, you must enter a user ID and password.</span></span> <span data-ttu-id="52872-148">既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="52872-148">The default value is `False`.</span></span>  
  
 <span data-ttu-id="52872-149">**[ユーザー ID]**</span><span class="sxs-lookup"><span data-stu-id="52872-149">**User ID**</span></span>  
 <span data-ttu-id="52872-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-150">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="52872-151">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="52872-151">**Password**</span></span>  
 <span data-ttu-id="52872-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-152">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="52872-153">このプロバイダーを選択したときに一覧表示される追加オプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のソース データベースに正しく接続するために必須というわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52872-153">The additional options that are listed when you select this provider are not required to connect successfully to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source database.</span></span> <span data-ttu-id="52872-154">これらの追加オプションの説明については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ソフトウェア開発キットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Provider for [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-154">For a description of these additional options, see the documentation for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit.</span></span>  
  
### <a name="data-source--microsoft-excel"></a><span data-ttu-id="52872-155">[データ ソース] = [Microsoft Excel]</span><span class="sxs-lookup"><span data-stu-id="52872-155">Data Source = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52872-156">Excel 2003 以前を使用しているデータソースに接続する場合にのみ、[ **Microsoft Excel** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-156">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="52872-157">Excel 2007 を使用するデータソースに接続するには、[ **Microsoft Office 12.0 Access データベースエンジン OLE DB プロバイダー**] を選択し、[**プロパティ**] をクリックします。次に、[**データリンクプロパティ**] ダイアログボックスの [**すべて**] タブで、 `Excel 12.0` **拡張プロパティ**の値として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="52872-157">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, enter `Excel 12.0` as the value for **Extended Properties**.</span></span>  
  
 <span data-ttu-id="52872-158">**[Excel ファイル パス]**</span><span class="sxs-lookup"><span data-stu-id="52872-158">**Excel file path**</span></span>  
 <span data-ttu-id="52872-159">データをインポートするスプレッドシートのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-159">Specify the path and file name for the spreadsheet from which to import the data.</span></span> <span data-ttu-id="52872-160">たとえば、 **C:\MyData.xls、 \\\Sales\Database\Northwind.xls**です。</span><span class="sxs-lookup"><span data-stu-id="52872-160">For example, **C:\MyData.xls, \\\Sales\Database\Northwind.xls**.</span></span> <span data-ttu-id="52872-161">または、**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52872-161">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="52872-162">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="52872-162">**Browse**</span></span>  
 <span data-ttu-id="52872-163">**[ファイルを開く]** ダイアログ ボックスを使用して、ワークシートを検索します。</span><span class="sxs-lookup"><span data-stu-id="52872-163">Locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="52872-164">**Excel のバージョン**</span><span class="sxs-lookup"><span data-stu-id="52872-164">**Excel version**</span></span>  
 <span data-ttu-id="52872-165">ソース データが格納されている Excel のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-165">Select the version of Excel that the source data is stored in.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52872-166">ウィザードでは、データを [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ソースからインポートするときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel ソース コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="52872-166">When you import data from a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] source, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Source component.</span></span> <span data-ttu-id="52872-167">使用に関する注意点と既知の問題については、「[Excel ソース](../data-flow/excel-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-167">For information about usage considerations and known issues, see [Excel Source](../data-flow/excel-source.md).</span></span>  
  
### <a name="data-source--microsoft-access"></a><span data-ttu-id="52872-168">[データ ソース] = [Microsoft Access]</span><span class="sxs-lookup"><span data-stu-id="52872-168">Data Source = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52872-169">Access 2003 以前を使用しているデータベースに接続する場合にのみ、[ **Microsoft access** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-169">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="52872-170">Access 2007 を使用するデータベースに接続するには、代わりに [ **Microsoft Office 12.0 access データベースエンジン OLE DB プロバイダー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52872-170">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider** instead.</span></span>  
  
 <span data-ttu-id="52872-171">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="52872-171">**File name**</span></span>  
 <span data-ttu-id="52872-172">データをインポートするデータベース ファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-172">Specify the path and file name for the database file from which to import the data.</span></span> <span data-ttu-id="52872-173">たとえば、**C:\MyData.mdb、\\\Sales\Database\Northwind.mdb** などです。</span><span class="sxs-lookup"><span data-stu-id="52872-173">For example, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**.</span></span> <span data-ttu-id="52872-174">または、**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52872-174">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="52872-175">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="52872-175">**Browse**</span></span>  
 <span data-ttu-id="52872-176">**[ファイルを開く]** ダイアログ ボックスを使用して、データベース ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="52872-176">Locate the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="52872-177">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="52872-177">**User name**</span></span>  
 <span data-ttu-id="52872-178">ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のために有効なユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-178">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="52872-179">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="52872-179">**Password**</span></span>  
 <span data-ttu-id="52872-180">ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のためにユーザーのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="52872-180">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="52872-181">ただし、データベースがすべてのユーザーに対して1つのパスワードで保護されている場合は、[**データリンクプロパティ**] ダイアログボックスでこの値を指定する必要があります。このダイアログボックスにアクセスするには、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52872-181">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed by clicking **Advanced**.</span></span>  
  
 <span data-ttu-id="52872-182">**詳細**</span><span class="sxs-lookup"><span data-stu-id="52872-182">**Advanced**</span></span>  
 <span data-ttu-id="52872-183">[**データリンクプロパティ**] ダイアログボックスを使用して、データベースパスワードや既定以外のワークグループ情報ファイルなどの詳細オプションを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="52872-183">You may want to specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="52872-184">OLE DB プロバイダーのプロパティの詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/?linkid=62553)の「データアクセス」セクションを検索してください。</span><span class="sxs-lookup"><span data-stu-id="52872-184">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
### <a name="data-source--flat-file-source"></a><span data-ttu-id="52872-185">[データ ソース] = [フラット ファイル ソース]</span><span class="sxs-lookup"><span data-stu-id="52872-185">Data Source = Flat File Source</span></span>  
 <span data-ttu-id="52872-186">フラット ファイル ソースのオプションの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52872-186">See the following topics for information about the options for a flat file data source.</span></span>  
  
 <span data-ttu-id="52872-187">[[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="52872-187">[Flat File Connection Manager Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
 <span data-ttu-id="52872-188">[[フラット ファイル接続マネージャー エディター] &#40;[列] ページ&#41;](../flat-file-connection-manager-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="52872-188">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../flat-file-connection-manager-editor-columns-page.md)</span></span>  
  
 <span data-ttu-id="52872-189">[[フラット ファイル接続マネージャー エディター] &#40;[詳細設定] ページ&#41;](../flat-file-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="52872-189">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="52872-190">[[フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)](../flat-file-connection-manager-editor-preview-page.md)</span><span class="sxs-lookup"><span data-stu-id="52872-190">[Flat File Connection Manager Editor &#40;Preview Page&#41;](../flat-file-connection-manager-editor-preview-page.md)</span></span>  
  
  
