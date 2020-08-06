---
title: SSIS を使用する Excel からのインポートまたは Excel へのエクスポート | Microsoft Docs
description: 前提条件、既知の問題、制限事項と共に、SQL Server Integration Services (SSIS) を使用して Excel データをインポートまたはエクスポートする方法について説明します。
ms.date: 04/10/2018
ms.prod: sql-server-2014
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58b0165925e73d0eb72b118113bc354338741a0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641070"
---
# <a name="import-data-from-excel-or-export-data-to-excel-with-sql-server-integration-services-ssis"></a><span data-ttu-id="aecfc-103">SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="aecfc-103">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>

<span data-ttu-id="aecfc-104">この記事では、SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-104">This article describes how to import data from Excel or export data to Excel with SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="aecfc-105">また、前提条件、制限事項、および既知の問題についても説明します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-105">The article also describes prerequisites, limitations, and known issues.</span></span>

<span data-ttu-id="aecfc-106">Excel からデータをインポートする、または Excel にデータをエクスポートするには、SSIS パッケージを作成し、Excel 接続マネージャーと Excel ソースまたは Excel 変換先を使用することで行えます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-106">You can import data from Excel or export data to Excel by creating an SSIS package and using the Excel Connection Manager and the Excel Source or the Excel Destination.</span></span> <span data-ttu-id="aecfc-107">SSIS に組み込まれている SQL Server インポートおよびエクスポート ウィザードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-107">You can also use the SQL Server Import and Export Wizard, which is built on SSIS.</span></span>

<span data-ttu-id="aecfc-108">この記事には、SSIS から Excel を正常に使用するため、または一般的な問題を理解して解決するために必要な 3 つの情報セットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aecfc-108">This article contains the three sets of information you need to use Excel successfully from SSIS or to understand and troubleshoot common problems:</span></span>
1.  <span data-ttu-id="aecfc-109">[必要なファイル](#files-you-need)。</span><span class="sxs-lookup"><span data-stu-id="aecfc-109">[The files you need](#files-you-need).</span></span>
2.  <span data-ttu-id="aecfc-110">Excel から、または Excel へのデータの読み込み時に指定する必要がある情報。</span><span class="sxs-lookup"><span data-stu-id="aecfc-110">The information you have to provide when you load data from or to Excel.</span></span>
    -   <span data-ttu-id="aecfc-111">データ ソースとして [Excel を指定](#specify-excel)します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-111">[Specify Excel](#specify-excel) as your data source.</span></span>
    -   <span data-ttu-id="aecfc-112">[Excel ファイル名とパス](#excel-file)を指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-112">Provide the [Excel file name and path](#excel-file).</span></span>
    -   <span data-ttu-id="aecfc-113">[Excel のバージョン](#excel-version)を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-113">Select the [Excel version](#excel-version).</span></span>
    -   <span data-ttu-id="aecfc-114">[最初の行に列名が含まれる](#first-row)かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-114">Specify whether the [first row contains column names](#first-row).</span></span>
    -   <span data-ttu-id="aecfc-115">[データを含むワークシートまたは範囲](#sheets-ranges)を指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-115">Provide the [worksheet or range that contains the data](#sheets-ranges).</span></span>
3.  <span data-ttu-id="aecfc-116">既知の問題と制限事項。</span><span class="sxs-lookup"><span data-stu-id="aecfc-116">Known issues and limitations.</span></span>
    -   <span data-ttu-id="aecfc-117">[データ型](#issues-types)に関する問題</span><span class="sxs-lookup"><span data-stu-id="aecfc-117">Issues with [data types](#issues-types).</span></span>
    -   <span data-ttu-id="aecfc-118">[インポート](#issues-importing)に関する問題。</span><span class="sxs-lookup"><span data-stu-id="aecfc-118">Issues with [importing](#issues-importing).</span></span>
    -   <span data-ttu-id="aecfc-119">[エクスポート](#issues-exporting)に関する問題。</span><span class="sxs-lookup"><span data-stu-id="aecfc-119">Issues with [exporting](#issues-exporting).</span></span>

## <a name="get-the-files-you-need-to-connect-to-excel"></a><a name="files-you-need"></a> <span data-ttu-id="aecfc-120">Excel に接続するために必要なファイルを取得する</span><span class="sxs-lookup"><span data-stu-id="aecfc-120">Get the files you need to connect to Excel</span></span>

<span data-ttu-id="aecfc-121">Excel からデータをインポートしたり、データを Excel にエクスポートするには、事前に Excel の接続コンポーネントをダウンロードする必要があります (まだインストールされていない場合)。</span><span class="sxs-lookup"><span data-stu-id="aecfc-121">Before you can import data from Excel or export data to Excel, you may have to download the connectivity components for Excel if they're not already installed.</span></span> <span data-ttu-id="aecfc-122">Excel の接続コンポーネントは、既定ではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-122">The connectivity components for Excel are not installed by default.</span></span>

<span data-ttu-id="aecfc-123">[Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)で、Excel の接続コンポーネントの最新バージョンをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="aecfc-123">Download the latest version of the connectivity components for Excel here: [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).</span></span>
  
<span data-ttu-id="aecfc-124">以前のバージョンの Excel で作成したファイルは、最新バージョンのコンポーネントで開くことができます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-124">The latest version of the components can open files created by earlier versions of Excel.</span></span>

<span data-ttu-id="aecfc-125">Microsoft Access 2016 *ランタイム*ではなく、必ず Access データベース エンジン 2016 *再頒布可能パッケージ*をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="aecfc-125">Make sure that you download the Access Database Engine 2016 *Redistributable* and not the Microsoft Access 2016 *Runtime*.</span></span>

<span data-ttu-id="aecfc-126">32 ビット バージョンの Office を既にインストールしている場合は、32 ビット バージョンのコンポーネントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-126">If the computer already has a 32-bit version of Office, then you have to install the 32-bit version of the components.</span></span> <span data-ttu-id="aecfc-127">また、SSIS パッケージを 32 ビット モードで実行していること、またはインポートおよびエクスポート ウィザードの 32 ビット バージョンを実行していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-127">You also have to ensure that you run the SSIS package in 32-bit mode, or run the 32-bit version of the Import and Export Wizard.</span></span>

<span data-ttu-id="aecfc-128">Office 365 サブスクリプションをお持ちの場合は、インストーラーを実行するときにエラー メッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-128">If you have an Office 365 subscription, you may see an error message when you run the installer.</span></span> <span data-ttu-id="aecfc-129">このエラーは、ダウンロードを Office のクイック実行コンポーネントとサイド バイ サイドでインストールできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-129">The error indicates that you can't install the download side by side with Office click-to-run components.</span></span> <span data-ttu-id="aecfc-130">このエラー メッセージを回避するには、コマンド プロンプト ウィンドウを開き、`/quiet` スイッチを使用してダウンロードした .EXE ファイルを実行して、Quiet モードでインストールを実行します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-130">To bypass this error message, run the installation in quiet mode by opening a Command Prompt window and running the .EXE file that you downloaded with the `/quiet` switch.</span></span> <span data-ttu-id="aecfc-131">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-131">For example:</span></span>

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

<span data-ttu-id="aecfc-132">2016 再頒布可能パッケージのインストールに問題がある場合は、代わりに [Microsoft Access データベース エンジン 2010 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=13255)から 2010 再頒布可能パッケージをインストールします</span><span class="sxs-lookup"><span data-stu-id="aecfc-132">If you have trouble installing the 2016 redistributable, install the 2010 redistributable instead from here: [Microsoft Access Database Engine 2010 Redistributable](https://www.microsoft.com/download/details.aspx?id=13255).</span></span> <span data-ttu-id="aecfc-133">(Excel 2013 用の再頒布可能パッケージはありません)。</span><span class="sxs-lookup"><span data-stu-id="aecfc-133">(There is no redistributable for Excel 2013.)</span></span>

## <a name="specify-excel"></a><a name="specify-excel"></a> <span data-ttu-id="aecfc-134">Excel を指定する</span><span class="sxs-lookup"><span data-stu-id="aecfc-134">Specify Excel</span></span>

<span data-ttu-id="aecfc-135">最初の手順は、Excel に接続することを指定することです。</span><span class="sxs-lookup"><span data-stu-id="aecfc-135">The first step is to indicate that you want to connect to Excel.</span></span>

### <a name="in-ssis"></a><span data-ttu-id="aecfc-136">SSIS</span><span class="sxs-lookup"><span data-stu-id="aecfc-136">In SSIS</span></span>
<span data-ttu-id="aecfc-137">SSIS で、Excel ソースまたは変換先ファイルに接続するための Excel 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-137">In SSIS, create an Excel Connection Manager to connect to the Excel source or destination file.</span></span> <span data-ttu-id="aecfc-138">接続マネージャーを作成するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-138">There are several ways to create the connection manager:</span></span>

-   <span data-ttu-id="aecfc-139">**[接続マネージャー]** 領域内を右クリックし、 **[新しい接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-139">In the **Connection Managers** area, right-click and select **New connection**.</span></span> <span data-ttu-id="aecfc-140">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[EXCEL]** 、 **[追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-140">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>
 
-   <span data-ttu-id="aecfc-141">**[SSIS]** メニューで **[新しい接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-141">On the **SSIS** menu, select **New connection**.</span></span> <span data-ttu-id="aecfc-142">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[EXCEL]** 、 **[追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-142">In the **Add SSIS Connection Manager** dialog box, select **EXCEL** and then **Add**.</span></span>

-   <span data-ttu-id="aecfc-143">**Excel ソース エディター**または **Excel 変換先エディター**の **[接続マネージャー]** ページで、**Excel ソース**または **Excel 変換先**を構成するときに、同時に接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-143">Create the connection manager at the same time that you configure the **Excel Source** or the **Excel Destination** on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**.</span></span>

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="aecfc-144">SQL Server インポートおよびエクスポート ウィザード</span><span class="sxs-lookup"><span data-stu-id="aecfc-144">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="aecfc-145">インポートおよびエクスポート ウィザードの **[データ ソースの選択]** または **[変換先の選択]** ページで、 **[データ ソース]** リストから **[Microsoft Excel]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-145">In the Import and Export Wizard, on the **Choose a Data Source** or **Choose a Destination** page, select **Microsoft Excel** in the **Data source** list.</span></span>

<span data-ttu-id="aecfc-146">データ ソースのリストに Excel が表示されない場合は、32 ビットのウィザードを実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="aecfc-146">If you don't see Excel in the list of data sources, make sure you're running the 32-bit wizard.</span></span> <span data-ttu-id="aecfc-147">Excel 接続コンポーネントは、通常、32 ビット ファイルで、64 ビットのウィザードでは表示されません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-147">The Excel connectivity components are typically 32-bit files and aren't visible in the 64-bit wizard.</span></span>

## <a name="excel-file-and-file-path"></a><a name="excel-file"></a> <span data-ttu-id="aecfc-148">Excel ファイルとファイル パス</span><span class="sxs-lookup"><span data-stu-id="aecfc-148">Excel file and file path</span></span>

<span data-ttu-id="aecfc-149">最初に指定する情報は、Excel ファイルのパスとファイル名です。</span><span class="sxs-lookup"><span data-stu-id="aecfc-149">The first piece of info to provide is the path and file name for the Excel file.</span></span> <span data-ttu-id="aecfc-150">この情報は、SSIS パッケージの **Excel 接続マネージャー エディター**、またはインポートとエクスポート ウィザードの **[データ ソースの選択]** または **[変換先の選択]** のページで指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-150">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="aecfc-151">次の形式でパスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-151">Enter the path and file name in the following format:</span></span>

-   <span data-ttu-id="aecfc-152">ローカル コンピューター上のファイルの場合、**C:\\TestData.xlsx** です。</span><span class="sxs-lookup"><span data-stu-id="aecfc-152">For a file on the local computer, **C:\\TestData.xlsx**.</span></span>

-   <span data-ttu-id="aecfc-153">ネットワーク共有上のファイルの場合、 **\\\\Sales\\Data\\TestData.xlsx** です。</span><span class="sxs-lookup"><span data-stu-id="aecfc-153">For a file on a network share, **\\\\Sales\\Data\\TestData.xlsx**.</span></span>

<span data-ttu-id="aecfc-154">または、 **[参照]** をクリックして、 **[ファイルを開く]** ダイアログ ボックスを使用してワークシートを検索します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-154">Or, click **Browse** to locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aecfc-155">パスワードで保護された Excel ファイルには接続できません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-155">You can't connect to a password-protected Excel file.</span></span>

## <a name="excel-version"></a><a name="excel-version"></a> <span data-ttu-id="aecfc-156">Excel バージョン</span><span class="sxs-lookup"><span data-stu-id="aecfc-156">Excel version</span></span>

<span data-ttu-id="aecfc-157">2 番目に指定する情報は、Excel ファイルのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="aecfc-157">The second piece of info to provide is the version of the Excel file.</span></span> <span data-ttu-id="aecfc-158">この情報は、SSIS パッケージの **Excel 接続マネージャー エディター**、またはインポートとエクスポート ウィザードの **[データ ソースの選択]** または **[変換先の選択]** のページで指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-158">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** or **Choose a Destination** page of the Import and Export Wizard.</span></span>

<span data-ttu-id="aecfc-159">ファイルを作成するために使用した Microsoft Excel のバージョンか、別の互換性のあるバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-159">Select the version of Microsoft Excel that was used to create the file, or another compatible version.</span></span> <span data-ttu-id="aecfc-160">たとえば、2016 接続コンポーネントのインストールに問題がある場合、2010 コンポーネントをインストールして、このリストで **[Microsoft Excel 2007-2010]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-160">For example, if you had trouble installing the 2016 connectivity components, you can install the 2010 components and select **Microsoft Excel 2007-2010** in this list.</span></span>

<span data-ttu-id="aecfc-161">古いバージョンの接続コンポーネントしかインストールされていない場合は、それより新しいバージョンの Excel をリストで選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-161">You may not be able to select newer Excel versions in the list if you only have older versions of the connectivity components installed.</span></span> <span data-ttu-id="aecfc-162">**Excel バージョン** リストには、SSIS によってサポートされている Excel のすべてのバージョンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aecfc-162">The **Excel version** list includes all the versions of Excel supported by SSIS.</span></span> <span data-ttu-id="aecfc-163">このリスト内に項目があっても、必要な接続コンポーネントがインストールされているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-163">The presence of items in this list does not indicate that the required connectivity components are installed.</span></span> <span data-ttu-id="aecfc-164">たとえば、2016 接続コンポーネントをインストールしていなくても、リストには **Microsoft Excel 2016** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-164">For example, **Microsoft Excel 2016** appears in the list even if you have not installed the 2016 connectivity components.</span></span>

## <a name="first-row-has-column-names"></a><a name="first-row"></a> <span data-ttu-id="aecfc-165">先頭行に列名を含める</span><span class="sxs-lookup"><span data-stu-id="aecfc-165">First row has column names</span></span>

<span data-ttu-id="aecfc-166">Excel からデータをインポートしている場合、次の手順は、データの最初の行に列の名前が含まれているかどうかを示すことです。</span><span class="sxs-lookup"><span data-stu-id="aecfc-166">If you're importing data from Excel, the next step is to indicate whether the first row of the data contains column names.</span></span> <span data-ttu-id="aecfc-167">この情報は、SSIS パッケージの **Excel 接続マネージャー エディター**、またはインポートとエクスポート ウィザードの **[データ ソースの選択]** ページで指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-167">You provide this info in the **Excel Connection Manager Editor** in an SSIS package, or on the **Choose a Data Source** page of the Import and Export Wizard.</span></span>

-   <span data-ttu-id="aecfc-168">ソース データに列名が含まれていないため、このオプションを無効にすると、ウィザードでは F1、F2 などが列見出しとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-168">If you disable this option because the source data doesn't contain column names, the wizard uses F1, F2, and so forth, as column headings.</span></span>
-   <span data-ttu-id="aecfc-169">データに列名が含まれているのにこのオプションを無効にすると、ウィザードでは列名がデータの最初の行としてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-169">If the data contains column names, but you disable this option, the wizard imports the column names as the first row of data.</span></span>
-   <span data-ttu-id="aecfc-170">データに列名が含まれていないのにこのオプションを有効にすると、ウィザードではソース データの最初の行が列名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-170">If the data does not contain column names, but you enable this option, the wizard uses the first row of source data as the column names.</span></span> <span data-ttu-id="aecfc-171">この場合、ソース データの最初の行は、データ自体には含まれなくなります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-171">In this case, the first row of source data is no longer included in the data itself.</span></span>

<span data-ttu-id="aecfc-172">Excel からデータをエクスポートする場合にこのオプションを有効にすると、エクスポートされたデータの最初の行に列名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-172">If you're exporting data from Excel, and you enable this option, the first row of exported data includes the column names.</span></span>

## <a name="worksheets-and-ranges"></a><a name="sheets-ranges"></a> <span data-ttu-id="aecfc-173">ワークシートと範囲</span><span class="sxs-lookup"><span data-stu-id="aecfc-173">Worksheets and ranges</span></span>

<span data-ttu-id="aecfc-174">データのソースまたは変換先として使用できる Excel オブジェクトには、ワークシート、名前付き範囲、またはそのアドレスを使って指定する名前のない範囲のセルの 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-174">There are three types of Excel objects that you can use as the source or destination for your data: a worksheet, a named range, or an unnamed range of cells that you specify with its address.</span></span>

-   <span data-ttu-id="aecfc-175">**ワークシート。**</span><span class="sxs-lookup"><span data-stu-id="aecfc-175">**Worksheet.**</span></span> <span data-ttu-id="aecfc-176">ワークシートを指定するには、シート名の末尾に `$` 文字を付加し、文字列を区切り文字で囲みます (例: **[Sheet1$]** )。</span><span class="sxs-lookup"><span data-stu-id="aecfc-176">To specify a worksheet, append the `$` character to the end of the sheet name and add delimiters around the string - for example, **[Sheet1$]**.</span></span> <span data-ttu-id="aecfc-177">または、リスト内の既存のテーブルとビューから `$` 文字で終わる名前を探します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-177">Or, look for a name that ends with the `$` character in the list of existing tables and views.</span></span>

-   <span data-ttu-id="aecfc-178">**名前付き範囲。**</span><span class="sxs-lookup"><span data-stu-id="aecfc-178">**Named range.**</span></span> <span data-ttu-id="aecfc-179">名前付き範囲を指定するには、範囲名を指定します (例: **MyDataRange**)。</span><span class="sxs-lookup"><span data-stu-id="aecfc-179">To specify a named range, provide the range name - for example, **MyDataRange**.</span></span> <span data-ttu-id="aecfc-180">または、リスト内の既存のテーブルとビューから `$` 以外の文字で終わる名前を探します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-180">Or, look for a name that does not end with the `$` character in the list of existing tables and views.</span></span>
    
-   <span data-ttu-id="aecfc-181">**名前のない範囲。**</span><span class="sxs-lookup"><span data-stu-id="aecfc-181">**Unnamed range.**</span></span> <span data-ttu-id="aecfc-182">名前のないセルの範囲を指定するには、シート名の末尾に $ 文字を付加し、範囲の指定を追加し、文字列を区切り文字で囲みます (例: **[Sheet1$A1:B4]** )。</span><span class="sxs-lookup"><span data-stu-id="aecfc-182">To specify a range of cells that you haven't named, append the $ character to the end of the sheet name, add the range specification, and add delimiters around the string - for example, **[Sheet1$A1:B4]**.</span></span>

<span data-ttu-id="aecfc-183">データのソースまたは変換先として使用する Excel オブジェクトの種類を選択または指定するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="aecfc-183">To select or specify the type of Excel object that you want to use as the source or destination for your data, do one of the following things:</span></span>

### <a name="in-ssis"></a><span data-ttu-id="aecfc-184">SSIS</span><span class="sxs-lookup"><span data-stu-id="aecfc-184">In SSIS</span></span>

<span data-ttu-id="aecfc-185">SSIS で、**Excel ソース エディター**または **Excel 変換先エディター**の **[接続マネージャー]** ページで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="aecfc-185">In SSIS, on the **Connection manager** page of the **Excel Source Editor** or of the **Excel Destination Editor**, do one of the following things:</span></span>

-   <span data-ttu-id="aecfc-186">**ワークシート**または**名前付き範囲**を使用するには、 **[データ アクセス モード]** に **[テーブルまたはビュー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-186">To use a **worksheet** or a **named range**, select **Table or view** as the **Data access mode**.</span></span> <span data-ttu-id="aecfc-187">次に、 **[Excel シートの名前]** リストで、ワークシートまたは名前付き範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-187">Then, in the **Name of the Excel sheet** list, select the worksheet or named range.</span></span>

-   <span data-ttu-id="aecfc-188">そのアドレスを使用して指定する**名前のない範囲**を使用するには、 **[データ アクセス モード]** に **[SQL コマンド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-188">To use an **unnamed range** that you specify with its address, select **SQL command** as the **Data access mode**.</span></span> <span data-ttu-id="aecfc-189">次に、 **[SQL コマンド テキスト]** フィールドに、次の例のようなクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-189">Then, in the **SQL command text** field, enter a query like the following example:</span></span>

    ```sql
    SELECT * FROM [Sheet1$A1:B5]
    ```

### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="aecfc-190">SQL Server インポートおよびエクスポート ウィザード</span><span class="sxs-lookup"><span data-stu-id="aecfc-190">In the SQL Server Import and Export Wizard</span></span>
<span data-ttu-id="aecfc-191">インポートおよびエクスポート ウィザードで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="aecfc-191">In the Import and Export Wizard, do one of the following things:</span></span>

-   <span data-ttu-id="aecfc-192">Excel から**インポートする**場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="aecfc-192">When you're **importing** from Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="aecfc-193">**ワークシート**または**名前付き範囲**を使用するには、 **[テーブルのコピーまたはクエリの指定]** ページで、 **[1 つ以上のテーブルまたはビューからデータをコピーする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-193">To use a **worksheet** or a **named range**, on the **Specify table copy or query** page, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="aecfc-194">次に、 **[コピー元のテーブルおよびビューを選択]** ページの **[ソース]** 列で、ソースのワークシートと名前付き範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-194">Then, on the **Select Source Tables and Views** page, in the **Source** column, select the source worksheets and named ranges.</span></span>

    -   <span data-ttu-id="aecfc-195">そのアドレスを使用して指定する**名前のない範囲**を使用するには、 **[テーブルのコピーまたはクエリの指定]** ページで、 **[転送するデータを指定するためのクエリを記述する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-195">To use an **unnamed range** that you specify with its address, on the **Specify table copy or query** page, select **Write a query to specify the data to transfer**.</span></span> <span data-ttu-id="aecfc-196">次に、 **[基になるクエリの指定]** ページで、次の例のようなクエリを指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-196">Then, on the **Provide a Source Query** page, provide a query similar to the following example:</span></span>

        ```sql
        SELECT * FROM [Sheet1$A1:B5]
        ```

-   <span data-ttu-id="aecfc-197">Excel に**エクスポートする**場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="aecfc-197">When you're **exporting** to Excel, do one of the following things:</span></span>

    -   <span data-ttu-id="aecfc-198">**ワークシート**または**名前付き範囲**を使用するには、 **[コピー元のテーブルおよびビューを選択]** ページの **[変換先]** 列で、エクスポート先のワークシートおよび名前付き範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-198">To use a **worksheet** or a **named range**, on the **Select Source Tables and Views** page, in the **Destination** column, select the destination worksheets and named ranges.</span></span>

    -   <span data-ttu-id="aecfc-199">そのアドレスを使用して指定する**名前のない範囲**を使用するには、 **[コピー元のテーブルおよびビューを選択]** ページの **[変換先]** 列で、区切り記号は使わずに、`Sheet1$A1:B5` の形式で範囲を入力します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-199">To use an **unnamed range** that you specify with its address, on the **Select Source Tables and Views** page, in the **Destination** column, enter the range in the following format without delimiters: `Sheet1$A1:B5`.</span></span> <span data-ttu-id="aecfc-200">区切り記号はウィザードによって追加されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-200">The wizard adds the delimiters.</span></span>

<span data-ttu-id="aecfc-201">インポートまたはエクスポートする Excel オブジェクトを選択または入力すると、ウィザードの **[コピー元のテーブルおよびビューを選択]** ページで次の操作も行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-201">After you select or enter the Excel objects to import or export, you can also do the following things on the **Select Source Tables and Views** page of the wizard:</span></span>

-   <span data-ttu-id="aecfc-202">**[マッピングの編集]** を選択して、変換元と変換先の間の列マッピングを確認する。</span><span class="sxs-lookup"><span data-stu-id="aecfc-202">Review column mappings between source and destination by selecting **Edit Mappings**.</span></span>

-   <span data-ttu-id="aecfc-203">**[プレビュー]** を選択して、サンプル データが期待どおりになっていることをプレビューで確認する。</span><span class="sxs-lookup"><span data-stu-id="aecfc-203">Preview sample data to make sure it's what you expect by selecting **Preview**.</span></span>

## <a name="issues-with-data-types"></a><a name="issues-types"></a> <span data-ttu-id="aecfc-204">データ型に関する問題</span><span class="sxs-lookup"><span data-stu-id="aecfc-204">Issues with data types</span></span>

### <a name="data-types"></a><span data-ttu-id="aecfc-205">データ型</span><span class="sxs-lookup"><span data-stu-id="aecfc-205">Data types</span></span>

<span data-ttu-id="aecfc-206">Excel ドライバーでは、データ型の限定されたセットのみを認識します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-206">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="aecfc-207">たとえば、すべての数値列は倍精度浮動小数点型 (DT_R8) として解釈され、すべての文字列の列 (メモ列以外) は 255 文字の Unicode 文字列 (DT_WSTR) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-207">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> <span data-ttu-id="aecfc-208">SSIS では、Excel データ型を次のようにマップします。</span><span class="sxs-lookup"><span data-stu-id="aecfc-208">SSIS maps the Excel data types as follows:</span></span>

-   <span data-ttu-id="aecfc-209">Numeric - 倍精度浮動小数点数 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="aecfc-209">Numeric - double-precision float (DT_R8)</span></span>

-   <span data-ttu-id="aecfc-210">Currency - 通貨 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="aecfc-210">Currency - currency (DT_CY)</span></span>

-   <span data-ttu-id="aecfc-211">Boolean - ブール (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="aecfc-211">Boolean - Boolean (DT_BOOL)</span></span>

-   <span data-ttu-id="aecfc-212">Date/time - 日時 (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="aecfc-212">Date/time - datetime (DT_DATE)</span></span>

-   <span data-ttu-id="aecfc-213">String - Unicode 文字列、長さ 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="aecfc-213">String - Unicode string, length 255 (DT_WSTR)</span></span>

-   <span data-ttu-id="aecfc-214">Memo - Unicode テキスト ストリーム (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="aecfc-214">Memo - Unicode text stream (DT_NTEXT)</span></span>

### <a name="data-type-and-length-conversions"></a><span data-ttu-id="aecfc-215">データ型と長さの変換</span><span class="sxs-lookup"><span data-stu-id="aecfc-215">Data type and length conversions</span></span>

<span data-ttu-id="aecfc-216">SSIS では、データ型の暗黙的な変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-216">SSIS does not implicitly convert data types.</span></span> <span data-ttu-id="aecfc-217">したがって、派生列変換またはデータ変換の変換を使用して、Excel データを明示的に変換してから Excel 以外の変換先に読み込むか、Excel 以外のソースからデータを変換してから Excel 変換先に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-217">As a result, you may have to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a destination other than Excel, or to convert data from a source other than Excel before loading it into an Excel destination.</span></span>

<span data-ttu-id="aecfc-218">必要な変換の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-218">Here are some examples of the conversions that may be required:</span></span>  
  
-   <span data-ttu-id="aecfc-219">特定のコードページを使用した Unicode Excel 文字列の列と Unicode 以外の文字列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="aecfc-219">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepage.</span></span>
  
-   <span data-ttu-id="aecfc-220">255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="aecfc-220">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>
  
-   <span data-ttu-id="aecfc-221">倍精度の Excel 数値列と他の型の数値列の列間の変換</span><span class="sxs-lookup"><span data-stu-id="aecfc-221">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>

> [!TIP]
> <span data-ttu-id="aecfc-222">インポートおよびエクスポート ウィザードを使用していて、データにこれらの変換がいくつか必要な場合は、ウィザードによって必要な変換が構成されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-222">If you're using the Import and Export Wizard, and your data requires some of these conversions, the wizard configures the necessary conversions for you.</span></span> <span data-ttu-id="aecfc-223">そのため、SSIS パッケージを使用する場合でも、インポートおよびエクスポート ウィザードを使用して初期パッケージを作成しておくと役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-223">As a result, even when you want to use an SSIS package, it may be useful to create the initial package by using the Import and Export Wizard.</span></span> <span data-ttu-id="aecfc-224">ウィザードを使用すると、接続マネージャー、ソース、変換、および変換先を作成および構成できます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-224">Let the wizard create and configure connection managers, sources, transformations, and destinations for you.</span></span>

## <a name="issues-with-importing"></a><a name="issues-importing"></a> <span data-ttu-id="aecfc-225">インポートに関する問題</span><span class="sxs-lookup"><span data-stu-id="aecfc-225">Issues with importing</span></span>

### <a name="empty-rows"></a><span data-ttu-id="aecfc-226">空の行</span><span class="sxs-lookup"><span data-stu-id="aecfc-226">Empty rows</span></span>

<span data-ttu-id="aecfc-227">ソースとしてワークシートまたは名前付き範囲を指定すると、ドライバーは、ワークシートまたは範囲の左上の空でない最初のセルから、*連続した*セルのブロックを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-227">When you specify a worksheet or a named range as the source, the driver reads the *contiguous* block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="aecfc-228">そのため、データ行は行 1 で開始する必要はありませんが、ソース データで空の行を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-228">As a result, your data doesn't have to start in row 1, but you can't have empty rows in the source data.</span></span> <span data-ttu-id="aecfc-229">たとえば、列ヘッダーとデータ行の間に空の行を入れたり、ワークシートの上部のタイトルの後に空の行を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-229">For example, you can't have an empty row between the column headers and the data rows, or a title followed by empty rows at the top of the worksheet.</span></span>

<span data-ttu-id="aecfc-230">データの上に空の行がある場合は、ワークシートとしてデータにクエリを実行できません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-230">If there are empty rows above your data, you can't query the data as a worksheet.</span></span> <span data-ttu-id="aecfc-231">Excel では、データの範囲を選択し、その範囲に名前を割り当ててから、ワークシートではなく名前付き範囲に対してクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-231">In Excel, you have to select your range of data and assign a name to the range, and then query the named range instead of the worksheet.</span></span>

### <a name="missing-values"></a><span data-ttu-id="aecfc-232">不足している値</span><span class="sxs-lookup"><span data-stu-id="aecfc-232">Missing values</span></span>

<span data-ttu-id="aecfc-233">Excel ドライバーは、指定した変換元の特定の行数 (既定では 8 行) を読み取り、各列のデータ型を推測します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-233">The Excel driver reads a certain number of rows (by default, eight rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="aecfc-234">1 つの列に複数のデータ型が混在している可能性がある場合、特に数値データとテキスト データが混合している場合に、Excel ドライバーは数が多い方のデータ型を優先して判定し、それ以外のデータ型のデータが含まれるセルについては NULL 値を返します</span><span class="sxs-lookup"><span data-stu-id="aecfc-234">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="aecfc-235">(同数の場合は、数値型が優先されます)。Excel ワークシートでのセル書式のほとんどのオプションは、このデータ型の判定に影響しません。</span><span class="sxs-lookup"><span data-stu-id="aecfc-235">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span>

<span data-ttu-id="aecfc-236">Excel ドライバーのこの動作を変更するには、すべての値をテキストとしてインポートするようにインポート モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-236">You can modify this behavior of the Excel driver by specifying Import Mode to import all values as text.</span></span> <span data-ttu-id="aecfc-237">インポート モードを指定するには、[プロパティ] ウィンドウで、Excel 接続マネージャーの接続文字列内の**拡張プロパティ**の値に `IMEX=1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-237">To specify Import Mode, add `IMEX=1` to the value of **Extended Properties** in the connection string of the Excel connection manager in the Properties window.</span></span> 

### <a name="truncated-text"></a><span data-ttu-id="aecfc-238">切り捨てられたテキスト</span><span class="sxs-lookup"><span data-stu-id="aecfc-238">Truncated text</span></span>

<span data-ttu-id="aecfc-239">Excel の列にテキスト データが含まているとドライバーが判定した場合、ドライバーはサンプリングした最も長い値に基づいて、データ型 (文字列またはメモ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-239">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="aecfc-240">ドライバーがサンプリングした行で 255 文字より長い値が検出されなかった場合、その列はメモ列ではなく、255 文字の文字列の列として扱われます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-240">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="aecfc-241">このため、255 文字より長い値があると、切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-241">Therefore, values longer than 255 characters may be truncated.</span></span>

<span data-ttu-id="aecfc-242">データを切り捨てずにメモ列からインポートするには、2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-242">To import data from a memo column without truncation, you have two options:</span></span>

-   <span data-ttu-id="aecfc-243">サンプリングされた行の少なくとも 1 つのメモ列に、255 文字より長い値が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-243">Make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters</span></span>

-   <span data-ttu-id="aecfc-244">このような行を含めるには、ドライバーによってサンプリングされる行数を増やします。</span><span class="sxs-lookup"><span data-stu-id="aecfc-244">Increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="aecfc-245">サンプリングする行数を増やすには、次のレジストリ キーの下で **TypeGuessRows** の値を増やします。</span><span class="sxs-lookup"><span data-stu-id="aecfc-245">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the following registry key:</span></span>

| <span data-ttu-id="aecfc-246">再配布可能なコンポーネントのバージョン</span><span class="sxs-lookup"><span data-stu-id="aecfc-246">Redistributable components version</span></span> | <span data-ttu-id="aecfc-247">レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="aecfc-247">Registry key</span></span> |
|---|---|
| <span data-ttu-id="aecfc-248">Excel 2016</span><span class="sxs-lookup"><span data-stu-id="aecfc-248">Excel 2016</span></span> | <span data-ttu-id="aecfc-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="aecfc-249">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel</span></span> |
| <span data-ttu-id="aecfc-250">Excel 2010</span><span class="sxs-lookup"><span data-stu-id="aecfc-250">Excel 2010</span></span> | <span data-ttu-id="aecfc-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span><span class="sxs-lookup"><span data-stu-id="aecfc-251">HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel</span></span> |
| | |

## <a name="issues-with-exporting"></a><a name="issues-exporting"></a> <span data-ttu-id="aecfc-252">エクスポートに関する問題</span><span class="sxs-lookup"><span data-stu-id="aecfc-252">Issues with exporting</span></span>

### <a name="create-a-new-destination-file"></a><span data-ttu-id="aecfc-253">新しいエクスポート先ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="aecfc-253">Create a new destination file</span></span>

#### <a name="in-ssis"></a><span data-ttu-id="aecfc-254">SSIS</span><span class="sxs-lookup"><span data-stu-id="aecfc-254">In SSIS</span></span>

<span data-ttu-id="aecfc-255">作成する新しい Excel ファイルのパスとファイル名を使用して、Excel 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-255">Create an Excel Connection Manager with the path and file name of the new Excel file that you want to create.</span></span> <span data-ttu-id="aecfc-256">次に、**Excel 変換先エディター**で、 **[Excel シートの名前]** に **[新規]** を選択して、エクスポート先のワークシートを作成します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-256">Then, in the **Excel Destination Editor**, for **Name of the Excel sheet**, select **New** to create the destination worksheet.</span></span> <span data-ttu-id="aecfc-257">この時点で、SSIS によって指定したワークシートを持つ新しい Excel ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-257">At this point, SSIS creates the new Excel file with the specified worksheet.</span></span>

#### <a name="in-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="aecfc-258">SQL Server インポートおよびエクスポート ウィザード</span><span class="sxs-lookup"><span data-stu-id="aecfc-258">In the SQL Server Import and Export Wizard</span></span>

<span data-ttu-id="aecfc-259">**[変換先の選択]** ページで、 **[参照]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-259">On the **Choose a Destination** page, select **Browse**.</span></span> <span data-ttu-id="aecfc-260">**[ファイルを開く]** ダイアログ ボックスで、新しい Excel ファイルを作成するフォルダーに移動し、新しいファイルの名前を指定してから、 **[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-260">In the **Open** dialog box, navigate to the folder where you want the new Excel file to be created, provide a name for the new file, and then select **Open**.</span></span>

### <a name="export-to-a-large-enough-range"></a><span data-ttu-id="aecfc-261">十分な大きさの範囲をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="aecfc-261">Export to a large enough range</span></span>

<span data-ttu-id="aecfc-262">変換先として範囲を指定するときに、範囲の "*列数*" がソース データより少ないと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-262">When you specify a range as the destination, an error occurs if the range has fewer *columns* than the source data.</span></span> <span data-ttu-id="aecfc-263">一方、指定した範囲がソース データより "*行数*" が少ない場合、エラーは発生せず、ウィザードでは行の記述が続行され、新しい行数に合わせて行の定義が拡張されます。</span><span class="sxs-lookup"><span data-stu-id="aecfc-263">However, if the range that you specify has fewer *rows* than the source data, the wizard continues writing rows without error and extends the range definition to match the new number of rows.</span></span>

### <a name="export-long-text-values"></a><span data-ttu-id="aecfc-264">長いテキストの値をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="aecfc-264">Export long text values</span></span>

<span data-ttu-id="aecfc-265">255 文字を超える文字列を Excel 列に正常に保存するには、変換先の列のデータ型を **文字列型** ではなく **メモ型**としてドライバーが認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-265">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span>

-   <span data-ttu-id="aecfc-266">既存の変換先のテーブルに既にデータ行が含まれている場合、ドライバーによってサンプリングされた先頭の数行のメモ列に、255 文字を超える値のインスタンスが 1 つ以上含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-266">If an existing destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span>

-   <span data-ttu-id="aecfc-267">新しい変換先のテーブルがパッケージの設計時または実行時に作成される場合、またはインポートおよびエクスポート ウィザードによって作成される場合は、`CREATE TABLE` ステートメントで LONGTEXT (またはそのいずれかのシノニム) を変換先のメモ列のデータ型として使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aecfc-267">If a new destination table is created during package design or at run time or by the Import and Export Wizard, then the `CREATE TABLE` statement must use LONGTEXT (or one of its synonyms) as the data type of the destination memo column.</span></span> <span data-ttu-id="aecfc-268">ウィザードで、**[列マッピング]** ページの **[変換先テーブルの作成]** オプションの横にある **[SQL の編集]** をクリックし、`CREATE TABLE` ステートメントを調べて、必要であれば修正します。</span><span class="sxs-lookup"><span data-stu-id="aecfc-268">In the wizard, check the `CREATE TABLE` statement and revise it, if necessary, by clicking **Edit SQL** next to the **Create destination table** option on the **Column Mappings** page.</span></span>

## <a name="related-content"></a><span data-ttu-id="aecfc-269">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="aecfc-269">Related content</span></span>

<span data-ttu-id="aecfc-270">この記事で説明した手順とコンポーネントに関する詳細は、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aecfc-270">For more information about the components and procedures described in this article, see the following articles:</span></span>

### <a name="about-ssis"></a><span data-ttu-id="aecfc-271">SSIS について</span><span class="sxs-lookup"><span data-stu-id="aecfc-271">About SSIS</span></span>
[<span data-ttu-id="aecfc-272">Excel 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="aecfc-272">Excel Connection Manager</span></span>](connection-manager/excel-connection-manager.md)  
[<span data-ttu-id="aecfc-273">Excel ソース</span><span class="sxs-lookup"><span data-stu-id="aecfc-273">Excel Source</span></span>](data-flow/excel-source.md)  
[<span data-ttu-id="aecfc-274">Excel 変換先</span><span class="sxs-lookup"><span data-stu-id="aecfc-274">Excel Destination</span></span>](data-flow/excel-destination.md)  
[<span data-ttu-id="aecfc-275">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="aecfc-275">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
[<span data-ttu-id="aecfc-276">スクリプト タスクを使用した Excel ファイルの操作</span><span class="sxs-lookup"><span data-stu-id="aecfc-276">Working with Excel Files with the Script Task</span></span>](extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)

### <a name="about-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="aecfc-277">SQL Server インポートおよびエクスポート ウィザードについて</span><span class="sxs-lookup"><span data-stu-id="aecfc-277">About the SQL Server Import and Export Wizard</span></span>
[<span data-ttu-id="aecfc-278">Excel データ ソースに接続する</span><span class="sxs-lookup"><span data-stu-id="aecfc-278">Connect to an Excel Data Source</span></span>](/sql/integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard)  
[<span data-ttu-id="aecfc-279">簡単な例によるインポートおよびエクスポート ウィザードの概要</span><span class="sxs-lookup"><span data-stu-id="aecfc-279">Get started with this simple example of the Import and Export Wizard</span></span>](/sql/integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard)

### <a name="other-articles"></a><span data-ttu-id="aecfc-280">その他の記事</span><span class="sxs-lookup"><span data-stu-id="aecfc-280">Other articles</span></span>
[<span data-ttu-id="aecfc-281">Excel から SQL Server または Azure SQL Database にデータをインポートする</span><span class="sxs-lookup"><span data-stu-id="aecfc-281">Import data from Excel to SQL Server or Azure SQL Database</span></span>](/sql/relational-databases/import-export/import-data-from-excel-to-sql)  

