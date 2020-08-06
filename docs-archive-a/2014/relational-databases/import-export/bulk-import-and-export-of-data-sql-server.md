---
title: データの一括インポートと一括エクスポート (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b4e7611270135735cf3f7aada808a0a27ba927c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639961"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a><span data-ttu-id="90605-102">データの一括インポートと一括エクスポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="90605-102">Bulk Import and Export of Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90605-103">では、*テーブルからのデータの一括エクスポート (* 一括データのエクスポート [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはパーティション分割されていないビューへの一括データのインポートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90605-103">supports exporting data in bulk (*bulk data*) from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and importing bulk data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="90605-104">一括インポートと一括エクスポートは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と異種データ ソースとの間で効率的にデータを転送するための重要な機能です。</span><span class="sxs-lookup"><span data-stu-id="90605-104">Bulk importing and bulk exporting are essential to efficient transfer data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and heterogeneous data sources.</span></span> <span data-ttu-id="90605-105">*一括エクスポート* とは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルから特定のデータ ファイルにデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="90605-105">*Bulk exporting* refers to copying data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file.</span></span> <span data-ttu-id="90605-106">*一括インポート* は、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータを読み込むことを指します。</span><span class="sxs-lookup"><span data-stu-id="90605-106">*Bulk importing* refers to loading data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="90605-107">たとえば、データを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel アプリケーションから特定のデータ ファイルにエクスポートした後、そのデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに一括インポートできます。</span><span class="sxs-lookup"><span data-stu-id="90605-107">For example, you can export data from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel application to a data file and then bulk import that data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="90605-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="90605-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="90605-109">一括インポート操作と一括エクスポート操作の概要</span><span class="sxs-lookup"><span data-stu-id="90605-109">Introduction to Bulk Import and Bulk Export Operations</span></span>](#Intro)  
  
-   [<span data-ttu-id="90605-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="90605-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bulk-import-and-bulk-export-overview"></a><a name="Intro"></a><span data-ttu-id="90605-111">一括インポートと一括エクスポートの概要</span><span class="sxs-lookup"><span data-stu-id="90605-111">Bulk Import and Bulk Export Overview</span></span>  
 <span data-ttu-id="90605-112">このセクションでは、データを一括でインポートおよびエクスポートするために使用できるさまざまな方法を示し、それらを簡単に比較します。</span><span class="sxs-lookup"><span data-stu-id="90605-112">This section lists and briefly compares the various methods that are available for bulk importing and exporting data.</span></span> <span data-ttu-id="90605-113">また、フォーマット ファイルについても説明します。</span><span class="sxs-lookup"><span data-stu-id="90605-113">The section also introduces format files.</span></span>  
  
 <span data-ttu-id="90605-114">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="90605-114">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="90605-115">データの一括インポートと一括エクスポートの方法</span><span class="sxs-lookup"><span data-stu-id="90605-115">Methods for Bulk Importing and Exporting Data</span></span>](#MethodsForBuliIE)  
  
-   [<span data-ttu-id="90605-116">フォーマットファイル</span><span class="sxs-lookup"><span data-stu-id="90605-116">Format Files</span></span>](#FFs)  
  
###  <a name="methods-for-bulk-importing-and-exporting-data"></a><a name="MethodsForBuliIE"></a><span data-ttu-id="90605-117">データの一括インポートと一括エクスポートの方法</span><span class="sxs-lookup"><span data-stu-id="90605-117">Methods for Bulk Importing and Exporting Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90605-118">では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからのデータの一括エクスポート、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはパーティション分割されていないビューへのデータの一括インポートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90605-118">supports bulk exporting data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or nonpartitioned view.</span></span> <span data-ttu-id="90605-119">使用できる基本的な方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90605-119">The following basic methods are available.</span></span>  
  
|<span data-ttu-id="90605-120">Method</span><span class="sxs-lookup"><span data-stu-id="90605-120">Method</span></span>|<span data-ttu-id="90605-121">説明</span><span class="sxs-lookup"><span data-stu-id="90605-121">Description</span></span>|<span data-ttu-id="90605-122">データのインポート</span><span class="sxs-lookup"><span data-stu-id="90605-122">Imports data</span></span>|<span data-ttu-id="90605-123">データのエクスポート</span><span class="sxs-lookup"><span data-stu-id="90605-123">Exports data</span></span>|  
|------------|-----------------|------------------|------------------|  
|[<span data-ttu-id="90605-124">bcp ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="90605-124">bcp utility</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|<span data-ttu-id="90605-125">データの一括エクスポートと一括インポート、およびフォーマット ファイルの生成を行うコマンド ライン ユーティリティ (Bcp.exe)。</span><span class="sxs-lookup"><span data-stu-id="90605-125">A command-line utility (Bcp.exe) that bulk exports and bulk imports data and generates format files.</span></span>|<span data-ttu-id="90605-126">はい</span><span class="sxs-lookup"><span data-stu-id="90605-126">Yes</span></span>|<span data-ttu-id="90605-127">はい</span><span class="sxs-lookup"><span data-stu-id="90605-127">Yes</span></span>|  
|[<span data-ttu-id="90605-128">BULK INSERT ステートメント</span><span class="sxs-lookup"><span data-stu-id="90605-128">BULK INSERT statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="90605-129">データ ファイルのデータをデータベース テーブルまたはパーティション分割されていないビューに直接インポートする [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント。</span><span class="sxs-lookup"><span data-stu-id="90605-129">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that imports data directly from a data file into a database table or nonpartitioned view.</span></span>|<span data-ttu-id="90605-130">はい</span><span class="sxs-lookup"><span data-stu-id="90605-130">Yes</span></span>|<span data-ttu-id="90605-131">いいえ</span><span class="sxs-lookup"><span data-stu-id="90605-131">No</span></span>|  
|[<span data-ttu-id="90605-132">INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメント</span><span class="sxs-lookup"><span data-stu-id="90605-132">INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|<span data-ttu-id="90605-133">INSERT ステートメントでデータを選択するために OPENROWSET(BULK...) 関数を指定することによって、OPENROWSET 一括行セット プロバイダーを使用してデータを [!INCLUDE[tsql](../../includes/tsql-md.md)] テーブルに一括インポートする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメント。</span><span class="sxs-lookup"><span data-stu-id="90605-133">A [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that uses the OPENROWSET bulk rowset provider to bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table by specifying the OPENROWSET(BULK...) function to select data in an INSERT statement.</span></span>|<span data-ttu-id="90605-134">はい</span><span class="sxs-lookup"><span data-stu-id="90605-134">Yes</span></span>|<span data-ttu-id="90605-135">いいえ</span><span class="sxs-lookup"><span data-stu-id="90605-135">No</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90605-136">SQL Server の一括インポート操作では、コンマ区切り (CSV) ファイルがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="90605-136">Comma-separated value (CSV) files are not supported by SQL Server bulk-import operations.</span></span> <span data-ttu-id="90605-137">ただし、場合によっては、SQL Server に対してデータを一括インポートする際、CSV ファイルをデータ ファイルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="90605-137">However, in some cases, a CSV file can be used as the data file for a bulk import of data into SQL Server.</span></span> <span data-ttu-id="90605-138">CSV ファイルのフィールド ターミネータは必ずしもコンマである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="90605-138">Note that the field terminator of a CSV file does not have to be a comma.</span></span> <span data-ttu-id="90605-139">詳細については、「[一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90605-139">For more information, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
###  <a name="format-files"></a><a name="FFs"></a><span data-ttu-id="90605-140">フォーマットファイル</span><span class="sxs-lookup"><span data-stu-id="90605-140">Format Files</span></span>  
 <span data-ttu-id="90605-141">**Bcp**ユーティリティ、BULK INSERT、および挿入...SELECT \* FROM OPENROWSET (BULK...) では、データファイル内の各フィールドの書式情報を格納する特殊な*フォーマットファイル*の使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90605-141">The **bcp** utility, BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) all support the use of a specialized *format file* that stores format information for each field in a data file.</span></span> <span data-ttu-id="90605-142">また、フォーマット ファイルには、対応する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに関する情報が含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="90605-142">A format file might also contain information about the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="90605-143">フォーマット ファイルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスからデータを一括エクスポートしたり、このインスタンスにデータを一括インポートしたりするのに必要なすべてのフォーマット情報を指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="90605-143">The format file can be used to provide all the format information that is required to bulk export data from and bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="90605-144">フォーマット ファイルを使用すると、インポートの際にデータ ファイルの形式に従ってデータを解釈したり、エクスポートの際にデータ ファイル内のデータに形式を適用する処理を柔軟に行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="90605-144">Format files provide a flexible way to interpret data as it is in the data file during import, and also to format data in the data file during export.</span></span> <span data-ttu-id="90605-145">これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または外部アプリケーションの特定の必要性に応じてデータの解釈や再フォーマットを行うことだけを目的としたプログラムを作成する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="90605-145">This flexibility eliminates the need to write special-purpose code to interpret the data or reformat the data to the specific requirements of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the external application.</span></span> <span data-ttu-id="90605-146">たとえば、コンマ区切り値が必要なアプリケーションに読み込まれるデータを一括インポートする場合、フォーマット ファイルを使用すると、エクスポートされたデータにフィールド ターミネータとしてコンマを挿入できます。</span><span class="sxs-lookup"><span data-stu-id="90605-146">For example, if you are bulk exporting data to be loaded into an application that requires comma-separated values, you can use a format file to insert commas as field terminators in the exported data.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90605-147">では、次の 2 種類のフォーマット ファイルがサポートされます:XML フォーマット ファイルと XML 以外のフォーマット ファイル。</span><span class="sxs-lookup"><span data-stu-id="90605-147">supports two kinds of format files: XML format files and non-XML format files.</span></span>  
  
 <span data-ttu-id="90605-148">フォーマットファイルを生成できるツールは、 **bcp**ユーティリティだけです。</span><span class="sxs-lookup"><span data-stu-id="90605-148">The **bcp** utility is the only tool that can generate a format file.</span></span> <span data-ttu-id="90605-149">詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90605-149">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="90605-150">フォーマット ファイルの使用方法の詳細は、「[データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90605-150">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90605-151">一括エクスポート操作または一括インポート操作でフォーマット ファイルが正しく提供されなかった場合に備えて、ユーザーはコマンド ラインで既定の形式をオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90605-151">In cases when a format file is not supplied during a bulk export or import operations, you can override the default formatting at the command line.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="90605-152">関連タスク</span><span class="sxs-lookup"><span data-stu-id="90605-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="90605-153">bcp ユーティリティを使用した一括データのインポートとエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-153">Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;</span></span>](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [<span data-ttu-id="90605-154">BULK INSERT または OPENROWSET&#40;BULK...&#41; を使用した一括データのインポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-154">Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;</span></span>](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [<span data-ttu-id="90605-155">データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-155">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="90605-156">一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-156">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="90605-157">一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-157">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="90605-158">**フォーマット ファイルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="90605-158">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="90605-159">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-159">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="90605-160">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-160">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="90605-161">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-161">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="90605-162">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-162">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="90605-163">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-163">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="90605-164">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="90605-164">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="90605-165">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="90605-165">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="90605-166">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-166">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="90605-167">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-167">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="90605-168">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-168">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="90605-169">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-169">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="90605-170">**bcp を使用した互換性のためのデータ形式を指定するには**</span><span class="sxs-lookup"><span data-stu-id="90605-170">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="90605-171">フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-171">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="90605-172">bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-172">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="90605-173">bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-173">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="90605-174">参照</span><span class="sxs-lookup"><span data-stu-id="90605-174">See Also</span></span>  
 <span data-ttu-id="90605-175">[一括インポートで最小ログ記録を行うための前提条件](prerequisites-for-minimal-logging-in-bulk-import.md) </span><span class="sxs-lookup"><span data-stu-id="90605-175">[Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md) </span></span>  
 <span data-ttu-id="90605-176">[データ &#40;SQL Server のインポートまたはエクスポート用のフォーマットファイル&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90605-176">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 <span data-ttu-id="90605-177">[XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90605-177">[Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md) </span></span>  
 <span data-ttu-id="90605-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="90605-178">[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md) </span></span>  
 <span data-ttu-id="90605-179">[他のサーバーへのデータベースのコピー](../databases/copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="90605-179">[Copy Databases to Other Servers](../databases/copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="90605-180">[XML データの一括読み込みを実行する &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="90605-180">[Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="90605-181">[一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md) </span><span class="sxs-lookup"><span data-stu-id="90605-181">[Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md) </span></span>  
 <span data-ttu-id="90605-182">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="90605-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="90605-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90605-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="90605-184">[データ &#40;SQL Server のインポートまたはエクスポート用のフォーマットファイル&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90605-184">[Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md) </span></span>  
 [<span data-ttu-id="90605-185">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90605-185">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
