---
title: SQL Server インポートおよびエクスポートウィザードを実行する |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 008c541b1f1a295057b0ee7cc384982627b9689a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642879"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="8159f-102">SQL Server インポートおよびエクスポート ウィザードを実行する</span><span class="sxs-lookup"><span data-stu-id="8159f-102">Run the SQL Server Import and Export Wizard</span></span>
  <span data-ttu-id="8159f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを使用すると、最も簡単な方法でデータ ソース間でデータをコピーしたり、基本パッケージを構築したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8159f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard provides the simplest method of copying data between data sources and of constructing basic packages.</span></span> <span data-ttu-id="8159f-104">ウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8159f-104">For more information about the wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="8159f-105">SQL Server のインポートおよびエクスポートウィザードを使用して、SQL Server データベースから Microsoft Excel スプレッドシートにデータをエクスポートするパッケージを作成する方法を示すビデオについては、「 [SQL Server データを excel にエクスポートする (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=131024)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8159f-105">For a video that demonstrates how to use the SQL Server Import and Export Wizard to create a package that exports data from a SQL Server database to a Microsoft Excel spreadsheet, see [Exporting SQL Server Data to Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131024).</span></span>  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="8159f-106">SQL Server インポートおよびエクスポート ウィザードを起動するには</span><span class="sxs-lookup"><span data-stu-id="8159f-106">To start the SQL Server Import and Export Wizard</span></span>  
  
-   <span data-ttu-id="8159f-107">[**スタート**] ボタンをクリックし、[**すべてのプログラム**]、[**Microsoft SQL Server** ] の順にポイントして、[**データのインポートおよびエクスポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8159f-107">On the **Start** menu, point to **All Programs**, point to**Microsoft SQL Server** , and then click **Import and Export Data**.</span></span>  
  
     <span data-ttu-id="8159f-108">または</span><span class="sxs-lookup"><span data-stu-id="8159f-108">-or-</span></span>  
  
     <span data-ttu-id="8159f-109">で、[ [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **SSIS パッケージ**] フォルダーを右クリックし、[ **SSISImport and Export Wizard**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8159f-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **SSIS Packages** folder, and then click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="8159f-110">または</span><span class="sxs-lookup"><span data-stu-id="8159f-110">-or-</span></span>  
  
     <span data-ttu-id="8159f-111">で、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] [**プロジェクト**] メニューの [ **SSISImport and Export Wizard**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8159f-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="8159f-112">または</span><span class="sxs-lookup"><span data-stu-id="8159f-112">-or-</span></span>  
  
     <span data-ttu-id="8159f-113">で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーの種類に接続し、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [データベース] を展開します。データベースを右クリックして [**タスク**] をポイントし、[**データのインポート**] または [**データのエクスポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8159f-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] server type, expand Databases, right-click a database, point to **Tasks**, and then click **Import Data** or **Export data**.</span></span>  
  
     <span data-ttu-id="8159f-114">または</span><span class="sxs-lookup"><span data-stu-id="8159f-114">-or-</span></span>  
  
     <span data-ttu-id="8159f-115">コマンド プロンプト ウィンドウで、C:\Program Files\Microsoft SQL Server\100\DTS\Binn にある DTSWizard.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="8159f-115">In a command prompt window, run DTSWizard.exe, located in C:\Program Files\Microsoft SQL Server\100\DTS\Binn.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8159f-116">64 ビット コンピューターには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって 64 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード (DTSWizard.exe) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8159f-116">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs the 64-bit version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard (DTSWizard.exe).</span></span> <span data-ttu-id="8159f-117">ただし、Access や Excel など、一部のデータ ソースは、32 ビット プロバイダーでしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="8159f-117">However, some data sources, such as Access or Excel, only have a 32-bit provider available.</span></span> <span data-ttu-id="8159f-118">これらのデータ ソースを操作するには、32 ビット版のウィザードをインストールして実行することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8159f-118">To work with these data sources, you might have to install and run the 32-bit version of the wizard.</span></span> <span data-ttu-id="8159f-119">32 ビット版のウィザードをインストールするには、セットアップ中に [クライアント ツール] または [[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8159f-119">To install the 32-bit version of the wizard, select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="8159f-120">SQL Server インポートおよびエクスポート ウィザードを使用してデータをインポートまたはエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="8159f-120">To import or export data by using the SQL Server Import and Export Wizard</span></span>  
  
1.  <span data-ttu-id="8159f-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="8159f-121">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span>  
  
2.  <span data-ttu-id="8159f-122">対応するウィザード ページで、データの変換元とデータの変換先を選択します。</span><span class="sxs-lookup"><span data-stu-id="8159f-122">On the corresponding wizard pages, select a data source and a data destination.</span></span>  
  
     <span data-ttu-id="8159f-123">利用できるデータの変換元は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー、OLE DB プロバイダー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client プロバイダー、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダー、Microsoft Office Excel、Microsoft Office Access およびフラット ファイル ソースです。</span><span class="sxs-lookup"><span data-stu-id="8159f-123">The available data sources include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers, [!INCLUDE[vstecado](../../includes/vstecado-md.md)] providers, Microsoft Office Excel, Microsoft Office Access, and the Flat File source.</span></span> <span data-ttu-id="8159f-124">変換元に応じて、認証モード、サーバー名、データベース名、ファイル形式などのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-124">Depending on the source, you set options such as the authentication mode, server name, database name, and file format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8159f-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle では、Oracle BLOB、CLOB、NCLOB、BFILE、および UROWID のデータ型はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8159f-125">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle does not support the Oracle BLOB, CLOB, NCLOB, BFILE, and UROWID data types.</span></span> <span data-ttu-id="8159f-126">したがって、OLE DB ソースで、これらのデータ型を使用する列が含まれるテーブルからデータを抽出することはできません。</span><span class="sxs-lookup"><span data-stu-id="8159f-126">Therefore, the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
     <span data-ttu-id="8159f-127">利用できるデータの変換先は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー、OLE DB プロバイダー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、Excel、Access およびフラット ファイル変換先です。</span><span class="sxs-lookup"><span data-stu-id="8159f-127">The available data destinations include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access, and the Flat File destination.</span></span>  
  
3.  <span data-ttu-id="8159f-128">選択した変換先の種類に対応するオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-128">Set the options for the type of destination that you selected.</span></span>  
  
     <span data-ttu-id="8159f-129">変換先が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの場合、次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-129">If the destination is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database you can specify the following:</span></span>  
  
    -   <span data-ttu-id="8159f-130">新しいデータベースを作成してデータベース プロパティを設定するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-130">Indicate whether to create a new database and set the database properties.</span></span> <span data-ttu-id="8159f-131">次のプロパティは構成できません。ウィザードは指定の既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="8159f-131">The following properties cannot be configured and the wizard uses the specified default values:</span></span>  
  
        |<span data-ttu-id="8159f-132">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8159f-132">Property</span></span>|<span data-ttu-id="8159f-133">値</span><span class="sxs-lookup"><span data-stu-id="8159f-133">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="8159f-134">照合順序</span><span class="sxs-lookup"><span data-stu-id="8159f-134">Collation</span></span>|<span data-ttu-id="8159f-135">Latin1_General_CS_AS_KS_WS</span><span class="sxs-lookup"><span data-stu-id="8159f-135">Latin1_General_CS_AS_KS_WS</span></span>|  
        |<span data-ttu-id="8159f-136">復旧モデル</span><span class="sxs-lookup"><span data-stu-id="8159f-136">Recovery model</span></span>|<span data-ttu-id="8159f-137">[完全]</span><span class="sxs-lookup"><span data-stu-id="8159f-137">Full</span></span>|  
        |<span data-ttu-id="8159f-138">フルテキスト インデックスを使用する</span><span class="sxs-lookup"><span data-stu-id="8159f-138">Use full-text indexing</span></span>|<span data-ttu-id="8159f-139">正しい</span><span class="sxs-lookup"><span data-stu-id="8159f-139">True</span></span>|  
  
    -   <span data-ttu-id="8159f-140">テーブルまたはビューのデータをコピーするか、またはクエリ結果をコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="8159f-140">Select whether to copy data from tables or views, or to copy query results.</span></span>  
  
         <span data-ttu-id="8159f-141">変換元のデータに対してクエリを実行し、その結果をコピーするには、Transact-SQL クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-141">If you want to query the source data and copy the results, you can construct a Transact-SQL query.</span></span> <span data-ttu-id="8159f-142">Transact-SQL クエリは、手動で入力するか、またはファイルに保存されたクエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-142">You can enter the Transact-SQL query manually or use a query saved to a file.</span></span> <span data-ttu-id="8159f-143">ウィザードにはファイルを探す参照機能があり、ファイルを選択すると、ウィザードは自動的にファイルを開き、その内容をウィザード ページに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8159f-143">The wizard includes a browse feature for locating the file, and the wizard automatically opens the file and pastes its content into the wizard page when you select the file.</span></span>  
  
         <span data-ttu-id="8159f-144">変換元が [!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーの場合は、DBCommand 文字列をクエリとして提供し、クエリ結果をコピーするオプションも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-144">If the source is an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider you can also use the option to copy query results, providing the DBCommand string as the query.</span></span>  
  
         <span data-ttu-id="8159f-145">変換元のデータがビューの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードでは、変換先でビューがテーブルに自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8159f-145">If the source data is a view, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically converts the view to a table in the destination.</span></span>  
  
    -   <span data-ttu-id="8159f-146">変換先テーブルを削除して再作成するかどうか、および ID 挿入を許可するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8159f-146">Indicate whether the destination table is dropped and then re-created, and whether to enable identity inserts.</span></span>  
  
    -   <span data-ttu-id="8159f-147">既存の変換先テーブルの行を削除するか、または行を追加するかを示します。</span><span class="sxs-lookup"><span data-stu-id="8159f-147">Indicate whether to delete rows or append rows in an existing destination table.</span></span> <span data-ttu-id="8159f-148">テーブルが存在しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは自動的にテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8159f-148">If the table does not exist, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically creates it.</span></span>  
  
     <span data-ttu-id="8159f-149">変換先がフラット ファイル変換先の場合、次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-149">If the destination is a Flat File destination you can specify the following:</span></span>  
  
    -   <span data-ttu-id="8159f-150">変換先ファイルの行区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-150">Specify the row delimiter in the destination file.</span></span>  
  
    -   <span data-ttu-id="8159f-151">変換先ファイルの列区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-151">Specify the column delimiter in the destination file.</span></span>  
  
4.  <span data-ttu-id="8159f-152">(省略可) テーブルを 1 つ選択して変換元列と変換先列間のマッピングを変更するか、または変換先列のメタデータを変更します。</span><span class="sxs-lookup"><span data-stu-id="8159f-152">(Optional) Select one table and change the mappings between source and destination columns, or change the metadata of destination columns:</span></span>  
  
    -   <span data-ttu-id="8159f-153">変換元列を別の変換先列にマップします。</span><span class="sxs-lookup"><span data-stu-id="8159f-153">Map source columns to different destination columns.</span></span>  
  
    -   <span data-ttu-id="8159f-154">変換先列のデータ型を変更します。</span><span class="sxs-lookup"><span data-stu-id="8159f-154">Change the data type in the destination column.</span></span>  
  
    -   <span data-ttu-id="8159f-155">文字データ型の列の長さを設定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-155">Set the length of columns with character data types.</span></span>  
  
    -   <span data-ttu-id="8159f-156">数値データ型の列の有効桁数と小数点以下桁数を設定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-156">Set the precision and scale of columns with numeric data types.</span></span>  
  
    -   <span data-ttu-id="8159f-157">列に null 値を含めることができるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-157">Specify whether the column can contain null values.</span></span>  
  
5.  <span data-ttu-id="8159f-158">(省略可) 複数のテーブルを選択して、これらのテーブルに適用されるメタデータおよびオプションを更新します。</span><span class="sxs-lookup"><span data-stu-id="8159f-158">(Optional) Select multiple tables, and update the metadata and options to apply to those tables:</span></span>  
  
    -   <span data-ttu-id="8159f-159">既存の変換先スキーマを選択するか、テーブルを割り当てる新しいスキーマを提供します。</span><span class="sxs-lookup"><span data-stu-id="8159f-159">Select an existing destination schema or provide a new schema to which to assign tables.</span></span>  
  
    -   <span data-ttu-id="8159f-160">変換先テーブルの ID 挿入を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-160">Specify whether to enable identity inserts in destination tables.</span></span>  
  
    -   <span data-ttu-id="8159f-161">変換先テーブルを削除して再作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-161">Specify whether to drop and re-create destination tables.</span></span>  
  
    -   <span data-ttu-id="8159f-162">既存の変換先テーブルを切り捨てるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8159f-162">Specify whether to truncate existing destination tables.</span></span>  
  
6.  <span data-ttu-id="8159f-163">パッケージを保存して実行します。</span><span class="sxs-lookup"><span data-stu-id="8159f-163">Save and run a package.</span></span>  
  
     <span data-ttu-id="8159f-164">ウィザードを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから起動した場合、パッケージはすぐに実行されます。</span><span class="sxs-lookup"><span data-stu-id="8159f-164">If the wizard is started from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the command prompt, the package can run immediately.</span></span> <span data-ttu-id="8159f-165">必要に応じて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**データベースまたはファイルシステムにパッケージを保存できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-165">You can optionally save the package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database or to the file system.</span></span> <span data-ttu-id="8159f-166">**Msdb**データベースの詳細については、「 [Package Management &#40;SSIS サービス&#41;](../service/package-management-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8159f-166">For more information about the **msdb** database, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
     <span data-ttu-id="8159f-167">パッケージを保存する際に、パッケージの保護レベルを設定し、パスワードを使用する保護レベルの場合はパスワードを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-167">When you save the package you can set the package protection level, and if the protection level uses a password, provide the password.</span></span> <span data-ttu-id="8159f-168">パッケージ保護レベルの詳細については、「[パッケージ内の機微なデータの Access Control](../security/access-control-for-sensitive-data-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8159f-168">For more information about package protection levels, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
     <span data-ttu-id="8159f-169">ウィザードを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトから起動した場合、ウィザードからパッケージを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="8159f-169">If the wizard is started from an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you cannot run the package from the wizard.</span></span> <span data-ttu-id="8159f-170">代わりに、ウィザードを起動した [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトにパッケージが追加されます。</span><span class="sxs-lookup"><span data-stu-id="8159f-170">Instead, the package is added to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project from which you started the wizard.</span></span> <span data-ttu-id="8159f-171">パッケージは、その後、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で実行できます。</span><span class="sxs-lookup"><span data-stu-id="8159f-171">You can then run the package in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8159f-172">では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ウィザードによって作成されたパッケージを保存するオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="8159f-172">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8159f-173">参照</span><span class="sxs-lookup"><span data-stu-id="8159f-173">See Also</span></span>  
 <span data-ttu-id="8159f-174">[SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="8159f-174">[SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span></span>  
 [<span data-ttu-id="8159f-175">SQL Server データ ツールでのパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="8159f-175">Create Packages in SQL Server Data Tools</span></span>](../create-packages-in-sql-server-data-tools.md)  
  
  
