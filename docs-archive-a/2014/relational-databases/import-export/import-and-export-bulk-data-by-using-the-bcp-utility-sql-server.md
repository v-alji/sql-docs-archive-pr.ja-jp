---
title: bcp ユーティリティを使用した一括データのインポートとエクスポート (SQL Server) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7d1892b26f3c638a696d8ed15e739f56ac2e682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643341"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a><span data-ttu-id="70464-102">bcp ユーティリティを使用した一括データのインポートとエクスポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70464-102">Import and Export Bulk Data by Using the bcp Utility (SQL Server)</span></span>

<span data-ttu-id="70464-103">このトピックでは、 [bcp ユーティリティ](../../tools/bcp-utility.md) を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内の SELECT ステートメントで指定できる任意の場所 (パーティション ビューを含む) からデータをエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70464-103">This topic provides an overview for using the [bcp utility](../../tools/bcp-utility.md) to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database where a SELECT statement works, including partitioned views.</span></span>  
  
 <span data-ttu-id="70464-104">bcp ユーティリティ (Bcp.exe) は、一括コピー プログラム (BCP) API を使用するコマンド ライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="70464-104">The bcp utility (Bcp.exe) is a command-line tool that uses the Bulk Copy Program (BCP) API.</span></span> <span data-ttu-id="70464-105">bcp ユーティリティは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="70464-105">The bcp utility performs the following tasks:</span></span>  
  
-   <span data-ttu-id="70464-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからデータ ファイルへのデータの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="70464-106">Bulk exports data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into a data file.</span></span>  
  
-   <span data-ttu-id="70464-107">クエリからのデータの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="70464-107">Bulk exports data from a query.</span></span>  
  
-   <span data-ttu-id="70464-108">データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルへのデータの一括インポート</span><span class="sxs-lookup"><span data-stu-id="70464-108">Bulk imports data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
-   <span data-ttu-id="70464-109">フォーマット ファイルの生成</span><span class="sxs-lookup"><span data-stu-id="70464-109">Generates format files.</span></span>  
  
 <span data-ttu-id="70464-110">bcp ユーティリティには、 **bcp** コマンドを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="70464-110">The bcp utility is accessed by the **bcp** command.</span></span> <span data-ttu-id="70464-111">**bcp** コマンドを使用してデータを一括インポートするには、テーブルのスキーマとテーブル列のデータ型を理解しておく必要があります (既存のフォーマット ファイルを使用する場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="70464-111">To use the **bcp** command to bulk import data, you must understand the schema of the table and the data types of its columns, unless you are using a pre-existing format file.</span></span>  
  
 <span data-ttu-id="70464-112">bcp ユーティリティでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルのデータを他のプログラムで使用できるようにデータ ファイルにエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="70464-112">The bcp utility can export data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file for use in other programs.</span></span> <span data-ttu-id="70464-113">このユーティリティでは、別のデータベース管理システム (DBMS) など、別のプログラムのデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="70464-113">The utility can also import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from another program, usually another database management system (DBMS).</span></span> <span data-ttu-id="70464-114">データは、まずエクスポート元プログラムからデータ ファイルにエクスポートされ、その後に別の操作として、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="70464-114">The data is first exported from the source program to a data file and then, in a separate operation, copied from the data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="70464-115">**bcp** コマンドには、データ ファイルのデータ型やその他の情報を指定するためのスイッチがあります。</span><span class="sxs-lookup"><span data-stu-id="70464-115">The **bcp** command provides switches that you use to specify the data type of the data file and other information.</span></span> <span data-ttu-id="70464-116">これらのスイッチを指定しなかった場合は、データ ファイルに含まれているデータ フィールドの型などのフォーマット情報を要求されます。</span><span class="sxs-lookup"><span data-stu-id="70464-116">If these switches are not specified, the command prompts for formatting information, such as the type of data fields in a data file.</span></span> <span data-ttu-id="70464-117">その後、対話型の応答内容を含んだフォーマット ファイルを作成するかどうかをたずねるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70464-117">The command then asks whether you want to create a format file that contains your interactive responses.</span></span> <span data-ttu-id="70464-118">一括インポート操作や一括エクスポート操作を後で行う場合は、フォーマット ファイルを使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="70464-118">If you want flexibility for future bulk-import or bulk-export operations, a format file is often useful.</span></span> <span data-ttu-id="70464-119">フォーマット ファイルは、同等のデータ ファイルに対して **bcp** コマンドを後で実行するときに指定できます。</span><span class="sxs-lookup"><span data-stu-id="70464-119">You can specify the format file on later **bcp** commands for equivalent data files.</span></span> <span data-ttu-id="70464-120">詳細については、「[bcp を使用した互換性のためのデータ形式の指定 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70464-120">For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70464-121">bcp ユーティリティは ODBC 一括コピーを使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="70464-121">The bcp utility is written by using the ODBC bulk-copy</span></span>  
  
 <span data-ttu-id="70464-122">**bcp** コマンドの構文の説明については、「 [bcp Utility](../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70464-122">For a description of the **bcp** command syntax, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="70464-123">例</span><span class="sxs-lookup"><span data-stu-id="70464-123">Examples</span></span>

 <span data-ttu-id="70464-124">**bcp** の例については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70464-124">For **bcp** examples, see:</span></span>  
  
-   [<span data-ttu-id="70464-125">bcp ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="70464-125">bcp Utility</span></span>](../../tools/bcp-utility.md)  
  
-   [<span data-ttu-id="70464-126">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-126">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="70464-127">XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-127">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="70464-128">データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-128">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="70464-129">一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-129">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="70464-130">フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-130">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="70464-131">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-131">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="70464-132">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="70464-133">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-133">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="70464-134">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="70464-135">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70464-135">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a><span data-ttu-id="70464-136">参照</span><span class="sxs-lookup"><span data-stu-id="70464-136">See Also</span></span>

<span data-ttu-id="70464-137">[Transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql) 
 の挿入 &#40;[SELECT 句 &#40;transact-sql&#41;](/sql/t-sql/queries/select-clause-transact-sql) 
[Bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="70464-137">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)
[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql)
[bcp Utility](../../tools/bcp-utility.md) </span></span>  
<span data-ttu-id="70464-138">[データ &#40;SQL Server の一括インポートの準備&#41;](prepare-to-bulk-import-data-sql-server.md) 
[BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
[データ &#40;SQL Server&#41;の一括インポートと一括エクスポート](bulk-import-and-export-of-data-sql-server.md) 
[OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) 
[フォーマットファイル &#40;SQL Server を作成し&#41;](create-a-format-file-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="70464-138">[Prepare to Bulk Import Data &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md)
[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)
[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)
[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)
[Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md)</span></span>