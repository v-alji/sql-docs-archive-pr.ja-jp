---
title: 変換先の選択 (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf9b717ef9de20d84d32c18eb3caa4c54cad87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642908"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="5415c-102">[変換先の選択] (SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="5415c-102">Choose a Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="5415c-103">[**変換先の選択**] ページを使用すると、コピーするデータの保存先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5415c-103">Use the **Choose a Destination** page to specify the destination of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="5415c-104">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="5415c-105">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="5415c-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="5415c-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="5415c-107">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="5415c-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="5415c-108">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="5415c-109">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="5415c-110">静的オプション</span><span class="sxs-lookup"><span data-stu-id="5415c-110">Static Options</span></span>  
 <span data-ttu-id="5415c-111">**宛先**</span><span class="sxs-lookup"><span data-stu-id="5415c-111">**Destination**</span></span>  
 <span data-ttu-id="5415c-112">変換先の保存形式に対応したデータ プロバイダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-112">Choose the data provider that matches the data storage format of the destination.</span></span> <span data-ttu-id="5415c-113">データ ソースに使用できるプロバイダーが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5415c-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="5415c-114">たとえば、では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、SQL Server の .NET Framework Data Provider、または SQL Server 用の Microsoft OLE DB プロバイダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5415c-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5415c-115">データを ODBC 変換先に保存するには、.NET Framework Data Provider for ODBC を選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-115">To save data to an ODBC destination, select the .NET Framework Data Provider for ODBC.</span></span>  
  
 <span data-ttu-id="5415c-116">[**データソース**] プロパティには、コンピューターにインストールされているプロバイダーに応じて変化するさまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="5415c-116">The **Data Source** property has a variable number of options, which change depending on the providers installed on the computer.</span></span> <span data-ttu-id="5415c-117">次の表に、一般的に使用される変換先に対応するオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="5415c-117">The following tables list the options for some commonly used destinations.</span></span> <span data-ttu-id="5415c-118">他のプロバイダーについては、プロバイダー固有のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-118">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="5415c-119">動的オプション</span><span class="sxs-lookup"><span data-stu-id="5415c-119">Dynamic Options</span></span>  
 <span data-ttu-id="5415c-120">以下では、いくつかのデータ ソースで利用可能なオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="5415c-120">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="5415c-121">[変換先] ドロップダウン リストに表示される変換先をすべて示しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5415c-121">Not all the destinations that are available in the Destination drop-down are listed here.</span></span>  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="5415c-122">[変換先] = [SQL Server Native Client] または [Microsoft OLE DB Provider for SQL Server]</span><span class="sxs-lookup"><span data-stu-id="5415c-122">Destination = SQL Server Native Client or Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="5415c-123">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="5415c-123">**Server name**</span></span>  
 <span data-ttu-id="5415c-124">データを受け取るサーバーの名前を入力するか、一覧からサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-124">Type the name of the server to receive the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="5415c-125">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="5415c-125">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="5415c-126">パッケージで Microsoft Windows 認証を使用してデータベースにログインするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-126">Specify whether the package should use Microsoft Windows Authentication to log in to the database.</span></span> <span data-ttu-id="5415c-127">より高いセキュリティのためには Windows 認証をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5415c-127">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="5415c-128">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="5415c-128">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="5415c-129">データベースへのログインに、パッケージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-129">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="5415c-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5415c-130">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="5415c-131">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="5415c-131">**User name**</span></span>  
 <span data-ttu-id="5415c-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-132">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="5415c-133">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="5415c-133">**Password**</span></span>  
 <span data-ttu-id="5415c-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-134">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="5415c-135">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="5415c-135">**Database**</span></span>  
 <span data-ttu-id="5415c-136">指定したインスタンス上のデータベースの一覧から選択するか、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **新規**作成] をクリックして新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="5415c-136">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or create a new database by clicking **New**.</span></span>  
  
 <span data-ttu-id="5415c-137">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="5415c-137">**Refresh**</span></span>  
 <span data-ttu-id="5415c-138">**[更新]** をクリックして、利用可能なデータベースの一覧を復元します。</span><span class="sxs-lookup"><span data-stu-id="5415c-138">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
 <span data-ttu-id="5415c-139">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="5415c-139">**New**</span></span>  
 <span data-ttu-id="5415c-140">[**データベースの作成**] ダイアログボックスを使用して、新しい変換先データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="5415c-140">Create a new destination database by using the **Create Database** dialog box.</span></span>  
  
### <a name="destination--flat-file-destination"></a><span data-ttu-id="5415c-141">[変換先] = [フラット ファイル変換先]</span><span class="sxs-lookup"><span data-stu-id="5415c-141">Destination = Flat File Destination</span></span>  
 <span data-ttu-id="5415c-142">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="5415c-142">**File name**</span></span>  
 <span data-ttu-id="5415c-143">データを格納するファイルのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-143">Specify the path and file name for the file in which to store the data.</span></span> <span data-ttu-id="5415c-144">または、 **[参照]** をクリックしてファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="5415c-144">Or, click **Browse** to locate a file.</span></span>  
  
 <span data-ttu-id="5415c-145">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="5415c-145">**Browse**</span></span>  
 <span data-ttu-id="5415c-146">**[開く]** ダイアログ ボックスを使用して、ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="5415c-146">Locate a file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="5415c-147">**ロケール**</span><span class="sxs-lookup"><span data-stu-id="5415c-147">**Locale**</span></span>  
 <span data-ttu-id="5415c-148">文字の並べ替え順と日時の形式を定義するロケールの ID (LCID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-148">Specify the locale ID (LCID) that defines character sort orders and date and time formatting.</span></span>  
  
 <span data-ttu-id="5415c-149">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="5415c-149">**Unicode**</span></span>  
 <span data-ttu-id="5415c-150">Unicode を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5415c-150">Indicate whether to use Unicode.</span></span> <span data-ttu-id="5415c-151">Unicode を使用する場合、コード ページを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5415c-151">If you use Unicode, you do not have to specify a code page.</span></span>  
  
 <span data-ttu-id="5415c-152">**コード ページ**</span><span class="sxs-lookup"><span data-stu-id="5415c-152">**Code page**</span></span>  
 <span data-ttu-id="5415c-153">使用する言語のコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-153">Specify the code page for the language you want to use.</span></span>  
  
 <span data-ttu-id="5415c-154">**形式**</span><span class="sxs-lookup"><span data-stu-id="5415c-154">**Format**</span></span>  
 <span data-ttu-id="5415c-155">区切り形式、固定幅形式、または幅合わせしない形式を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5415c-155">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="5415c-156">値</span><span class="sxs-lookup"><span data-stu-id="5415c-156">Value</span></span>|<span data-ttu-id="5415c-157">説明</span><span class="sxs-lookup"><span data-stu-id="5415c-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5415c-158">区切り記号</span><span class="sxs-lookup"><span data-stu-id="5415c-158">Delimited</span></span>|<span data-ttu-id="5415c-159">列は、 **[列]** ページで指定した区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="5415c-159">Columns are separated by a delimiter, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="5415c-160">固定幅ファイル</span><span class="sxs-lookup"><span data-stu-id="5415c-160">Fixed width</span></span>|<span data-ttu-id="5415c-161">列は固定幅を持ちます。</span><span class="sxs-lookup"><span data-stu-id="5415c-161">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="5415c-162">[幅合わせしない]</span><span class="sxs-lookup"><span data-stu-id="5415c-162">Ragged right</span></span>|<span data-ttu-id="5415c-163">幅合わせしないファイルとは、最後の列以外のすべての列が固定幅を持つファイルです。最後の列は、行区切り記号で区切られます。</span><span class="sxs-lookup"><span data-stu-id="5415c-163">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="5415c-164">**テキスト修飾子**</span><span class="sxs-lookup"><span data-stu-id="5415c-164">**Text qualifier**</span></span>  
 <span data-ttu-id="5415c-165">使用するテキスト修飾子を入力します。</span><span class="sxs-lookup"><span data-stu-id="5415c-165">Type the text qualifier to use.</span></span> <span data-ttu-id="5415c-166">たとえば、各テキスト列を引用符で囲むように指定できます。</span><span class="sxs-lookup"><span data-stu-id="5415c-166">For example, you can specify that each text column be surrounded with quotation marks.</span></span>  
  
 <span data-ttu-id="5415c-167">**[先頭データ行を列名として使用する]**</span><span class="sxs-lookup"><span data-stu-id="5415c-167">**Column names in first data row**</span></span>  
 <span data-ttu-id="5415c-168">先頭のデータ行に列名を表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-168">Indicate whether you want to display column names in the first data row.</span></span>  
  
### <a name="destination--microsoft-excel"></a><span data-ttu-id="5415c-169">[変換先] = [Microsoft Excel]</span><span class="sxs-lookup"><span data-stu-id="5415c-169">Destination = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5415c-170">Excel 2003 以前を使用しているデータソースに接続する場合にのみ、[ **Microsoft Excel** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-170">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="5415c-171">Excel 2007 を使用するデータソースに接続するには、[ **Microsoft Office 12.0 Access データベースエンジン OLE DB プロバイダー**] を選択し、[**プロパティ**] をクリックします。次に、[**データリンクプロパティ**] ダイアログボックスの [**すべて**] タブで、[**拡張プロパティ**] に「」と入力し `Excel 12.0` ます。</span><span class="sxs-lookup"><span data-stu-id="5415c-171">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, for **Extended Properties**, enter `Excel 12.0`.</span></span>  
  
 <span data-ttu-id="5415c-172">**[Excel ファイル パス]**</span><span class="sxs-lookup"><span data-stu-id="5415c-172">**Excel file path**</span></span>  
 <span data-ttu-id="5415c-173">データを格納するブックのパスとファイル名を指定します (たとえば、C:\MyData.xls、 \\\Sales\Database\Northwind.xls)。</span><span class="sxs-lookup"><span data-stu-id="5415c-173">Specify the path and file name for the workbook in which to store the data (for example, C:\MyData.xls, \\\Sales\Database\Northwind.xls).</span></span> <span data-ttu-id="5415c-174">または、 **[参照]** をクリックしてブックを探します。</span><span class="sxs-lookup"><span data-stu-id="5415c-174">Or, click **Browse** to locate a workbook.</span></span>  
  
 <span data-ttu-id="5415c-175">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="5415c-175">**Browse**</span></span>  
 <span data-ttu-id="5415c-176">[**開く**] ダイアログボックスを使用して、Excel ブックを検索します。</span><span class="sxs-lookup"><span data-stu-id="5415c-176">Locate an Excel workbook by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="5415c-177">**Excel のバージョン**</span><span class="sxs-lookup"><span data-stu-id="5415c-177">**Excel version**</span></span>  
 <span data-ttu-id="5415c-178">変換先のブックで使用される Excel のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-178">Select the version of Excel that is used by the destination workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5415c-179">データを変換先の [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] にエクスポートする場合、ウィザードでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 変換先コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5415c-179">When you export data to a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] destination, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Destination component.</span></span> <span data-ttu-id="5415c-180">使用に関する考慮事項と既知の問題の詳細については、「 [Excel 変換先](../data-flow/excel-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-180">For information on some usage considerations and known issues, see [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
### <a name="destination--microsoft-access"></a><span data-ttu-id="5415c-181">[変換先] = [Microsoft Access]</span><span class="sxs-lookup"><span data-stu-id="5415c-181">Destination = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5415c-182">Access 2003 以前を使用しているデータベースに接続する場合にのみ、[ **Microsoft access** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-182">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="5415c-183">Access 2007 を使用するデータベースに接続するには、[ **Microsoft Office 12.0 access データベースエンジン OLE DB プロバイダー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5415c-183">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.</span></span>  
  
 <span data-ttu-id="5415c-184">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="5415c-184">**File name**</span></span>  
 <span data-ttu-id="5415c-185">データを格納するデータベースファイルのパスとファイル名を指定します (たとえば、C:\MyData.mdb、 \\ \Sales\Database\Northwind.mdb)。</span><span class="sxs-lookup"><span data-stu-id="5415c-185">Specify the path and file name for the database file in which to store the data (for example, C:\MyData.mdb, \\\Sales\Database\Northwind.mdb).</span></span> <span data-ttu-id="5415c-186">または、 **[参照]** をクリックしてデータベース ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="5415c-186">Or, click **Browse** to locate a database file.</span></span>  
  
 <span data-ttu-id="5415c-187">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="5415c-187">**Browse**</span></span>  
 <span data-ttu-id="5415c-188">[**開く**] ダイアログボックスを使用して、データベースファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="5415c-188">Browse to the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="5415c-189">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="5415c-189">**User name**</span></span>  
 <span data-ttu-id="5415c-190">ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のために有効なユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-190">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="5415c-191">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="5415c-191">**Password**</span></span>  
 <span data-ttu-id="5415c-192">ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のためにユーザーのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-192">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="5415c-193">ただし、データベースがすべてのユーザーに対して 1 つのパスワードで保護されている場合、 **[データ リンク プロパティ]** ダイアログ ボックスでもこの値を入力する必要があります。このダイアログ ボックスを表示するには **[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5415c-193">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed from the **Advanced** button.</span></span>  
  
 <span data-ttu-id="5415c-194">**詳細**</span><span class="sxs-lookup"><span data-stu-id="5415c-194">**Advanced**</span></span>  
 <span data-ttu-id="5415c-195">**[データ リンク プロパティ]** ダイアログ ボックスで、データベースのパスワードや既定以外のワークグループ情報ファイルなどの詳細なオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5415c-195">Specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="5415c-196">OLE DB プロバイダーのプロパティの詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink/?linkid=62553)の「データ アクセス」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="5415c-196">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
  
