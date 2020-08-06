---
title: bcp を使用した互換性のためのデータ形式の指定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d12456760f32ddbd8cc434d474aebb0e0ecf141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738424"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a><span data-ttu-id="6f939-102">bcp を使用した互換性のためのデータ形式の指定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6f939-102">Specify Data Formats for Compatibility when Using bcp (SQL Server)</span></span>
  <span data-ttu-id="6f939-103">このトピックでは、データ形式属性、フィールド固有のプロンプト、およびコマンドの xml 以外のフォーマットファイルでのフィールドごとのデータの格納について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp` ます。</span><span class="sxs-lookup"><span data-stu-id="6f939-103">This topic describes the data-format attributes, field-specific prompts, and storing field-by-field data in a non-xml format file of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`bcp` command.</span></span> <span data-ttu-id="6f939-104">このトピックの内容は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを一括エクポートして別のプログラム (別のデータベース プログラムなど) に一括インポートする場合に有用です。</span><span class="sxs-lookup"><span data-stu-id="6f939-104">Understanding these can be helpful when you bulk export [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data for bulk import into another program, such as another database program.</span></span> <span data-ttu-id="6f939-105">ソース テーブルの既定のデータ形式 (ネイティブ、文字、または Unicode) が、他のプログラムで想定されているデータ レイアウトと互換性がない場合があります。互換性がない場合はデータをエクスポートするときに、データ レイアウトを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f939-105">The default data formats (native, character, or Unicode) in the source table might be incompatible with the data layout expected by the other program If an incompatibility exists, when you export the data, you must describe the data layout.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f939-106">データをインポートまたはエクスポートするためのデータ形式に精通していない場合は、「 [一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-106">If you are unfamiliar with data formats for importing or exporting data, see [Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md).</span></span>  
  
 <span data-ttu-id="6f939-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6f939-107">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="6f939-108">bcp データ形式の属性</span><span class="sxs-lookup"><span data-stu-id="6f939-108">bcp Data-Format Attributes</span></span>](#bcpDataFormatAttr)  
  
-   [<span data-ttu-id="6f939-109">フィールド固有のプロンプトの概要</span><span class="sxs-lookup"><span data-stu-id="6f939-109">Overview of the Field-Specific Prompts</span></span>](#FieldSpecificPrompts)  
  
-   [<span data-ttu-id="6f939-110">XML 以外のフォーマットファイルでのフィールドごとのデータの格納</span><span class="sxs-lookup"><span data-stu-id="6f939-110">Storing Field-by-Field Data in a Non-XML Format File</span></span>](#FieldByFieldNonXmlFF)  
  
-   [<span data-ttu-id="6f939-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6f939-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bcp-data-format-attributes"></a><a name="bcpDataFormatAttr"></a> <span data-ttu-id="6f939-112">bcp データ形式の属性</span><span class="sxs-lookup"><span data-stu-id="6f939-112">bcp Data-Format Attributes</span></span>  
 <span data-ttu-id="6f939-113">`bcp` コマンドにより、次のデータ形式属性に関して、データ ファイル内の各フィールドの構造を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6f939-113">The `bcp` command allows you to specify the structure of each field in a data file in terms of the following data-format attributes:</span></span>  
  
-   <span data-ttu-id="6f939-114">ファイル ストレージ型</span><span class="sxs-lookup"><span data-stu-id="6f939-114">File storage type</span></span>  
  
     <span data-ttu-id="6f939-115">*ファイル ストレージ型* は、データ ファイルへのデータの格納方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="6f939-115">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="6f939-116">データ ファイルには、データベース テーブルの型 (ネイティブ形式)、文字表現 (文字形式)、または暗黙的な型変換がサポートされているデータ型のいずれかでデータをエクスポートできます。暗黙的な型変換では、たとえば、`smallint` は `int` としてコピーされます。</span><span class="sxs-lookup"><span data-stu-id="6f939-116">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="6f939-117">ユーザー定義のデータ型は、基本データ型としてエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="6f939-117">User-defined data types are exported as their base types.</span></span> <span data-ttu-id="6f939-118">詳細については、「 [bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-118">For more information, see [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6f939-119">プレフィックス長</span><span class="sxs-lookup"><span data-stu-id="6f939-119">Prefix length</span></span>  
  
     <span data-ttu-id="6f939-120">`bcp` コマンドでは、ネイティブ形式のデータをデータ ファイルに一括エクスポートするためのファイル ストレージが最も少なくなるように、各フィールドの前にそのフィールドの長さを 1 文字以上の文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="6f939-120">To provide the most compact file storage for the bulk export of data in native format to a data file, the `bcp` command precedes each field with one or more characters that indicates the length of the field.</span></span> <span data-ttu-id="6f939-121">このような文字列を、 *プレフィックス長文字列*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="6f939-121">These characters are called *length prefix characters*.</span></span> <span data-ttu-id="6f939-122">詳細については、「 [bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-122">For more information, see [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6f939-123">フィールド長</span><span class="sxs-lookup"><span data-stu-id="6f939-123">Field length</span></span>  
  
     <span data-ttu-id="6f939-124">フィールド長は、文字形式でデータを表現するために必要な文字の最大数を示します。</span><span class="sxs-lookup"><span data-stu-id="6f939-124">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="6f939-125">データがネイティブ形式で格納される場合、フィールド長は既にわかっています。</span><span class="sxs-lookup"><span data-stu-id="6f939-125">The field length is already known if the data is stored in the native format.</span></span> <span data-ttu-id="6f939-126">詳細については、「 [bcp を使用したフィールド長の指定 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-126">For more information, see [Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6f939-127">フィールド ターミネータ</span><span class="sxs-lookup"><span data-stu-id="6f939-127">Field terminator</span></span>  
  
     <span data-ttu-id="6f939-128">文字列データ フィールドでは、省略可能なターミネータ文字を使用して、データ ファイルの各フィールドの末尾 ( *フィールド ターミネータ*を使用) と各行の末尾 ( *行ターミネータ*を使用) を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="6f939-128">For character data fields, optional terminating characters allow you to mark the end of each field in a data file (using a *field terminator*) and the end of each row (using a *row terminator*).</span></span> <span data-ttu-id="6f939-129">ターミネータ文字は、フィールドや行の終了位置と次のフィールドや行の開始位置を、データ ファイルを読み取るプログラムに示す方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6f939-129">Terminating characters are one way to indicate to programs reading the data file where one field or row ends and another begins.</span></span> <span data-ttu-id="6f939-130">詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-130">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
##  <a name="overview-of-the-field-specific-prompts"></a><a name="FieldSpecificPrompts"></a> <span data-ttu-id="6f939-131">フィールド固有のプロンプトの概要</span><span class="sxs-lookup"><span data-stu-id="6f939-131">Overview of the Field-Specific Prompts</span></span>  
 <span data-ttu-id="6f939-132">対話型コマンドに `bcp` **in**または**out**オプションが含まれていても、フォーマットファイルスイッチ (**-f**) またはデータ形式スイッチ (**-n**、 **-c**、 **-w**、または **-n**) のいずれも含まれていない場合は、ソーステーブルまたはターゲットテーブルの各列に対して、上記の各属性の入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="6f939-132">If an interactive `bcp` command contains the **in** or **out** option but does not also contain either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**),  each column in the source or target table, the command prompts for each of the preceding attributes, in turn.</span></span> <span data-ttu-id="6f939-133">問い合わせが行われる際は、`bcp` コマンドにより、テーブル列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に基づいてそれぞれ既定値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f939-133">In each prompt, the `bcp` command provides a default value based on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the table column.</span></span> <span data-ttu-id="6f939-134">すべての問い合わせに対して既定値を受け入れることは、コマンド ラインでネイティブ形式 ( **-n**) を指定するのと同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="6f939-134">Accepting the default value for all of the prompts produces the same result as specifying native format (**-n**) on the command line.</span></span> <span data-ttu-id="6f939-135">各プロンプトには、[*default*] のように既定値が角かっこ付きで表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f939-135">Each prompt displays a default value in brackets: [*default*].</span></span> <span data-ttu-id="6f939-136">表示される既定値を受け入れるには、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6f939-136">Pressing ENTER accepts the displayed default.</span></span> <span data-ttu-id="6f939-137">既定値以外を指定するには、プロンプトで新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="6f939-137">To specify a value other than the default, enter the new value at the prompt.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f939-138">例</span><span class="sxs-lookup"><span data-stu-id="6f939-138">Example</span></span>  
 <span data-ttu-id="6f939-139">次の例では、`bcp` コマンドを使用して、`HumanResources.myTeam` テーブルから `myTeam.txt` ファイルに、データを対話的に一括エクスポートします。</span><span class="sxs-lookup"><span data-stu-id="6f939-139">The following example uses the `bcp` command to bulk export data from the `HumanResources.myTeam` table interactively to the `myTeam.txt` file.</span></span> <span data-ttu-id="6f939-140">このテーブルを作成しないと、例を実行できません。</span><span class="sxs-lookup"><span data-stu-id="6f939-140">Before you can run the example, you must create this table.</span></span> <span data-ttu-id="6f939-141">テーブルの詳細とテーブルを作成する方法については、「[HumanResources.myTeam サンプル テーブル &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-141">For information about the table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
 <span data-ttu-id="6f939-142">コマンドでフォーマット ファイルもデータ型も指定しないと、`bcp` からデータ形式情報が要求されます。</span><span class="sxs-lookup"><span data-stu-id="6f939-142">The command specifies neither a format file nor a data type, causing `bcp` to prompt for data-format information.</span></span> <span data-ttu-id="6f939-143">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="6f939-143">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 <span data-ttu-id="6f939-144">列ごとに、bcp からフィールド固有の値が要求されます。</span><span class="sxs-lookup"><span data-stu-id="6f939-144">For each column, bcp prompts for field-specific values.</span></span> <span data-ttu-id="6f939-145">次の例は、テーブルの `EmployeeID` 列と `Name` 列のフィールド固有のプロンプトを示しています。また、各列の既定のファイル保存形式 (ネイティブ形式) も示しています。</span><span class="sxs-lookup"><span data-stu-id="6f939-145">The following example shows the field-specific prompts for the `EmployeeID` and `Name` columns of the table, and suggests the default file storage type (the native format) for each column.</span></span> <span data-ttu-id="6f939-146">`EmployeeID` 列と `Name` 列のプレフィックス長は、それぞれ 0 と 2 です。</span><span class="sxs-lookup"><span data-stu-id="6f939-146">The prefix lengths of the `EmployeeID` and `Name` column are 0 and 2, respectively.</span></span> <span data-ttu-id="6f939-147">ここでは、各フィールドのターミネータとして、ユーザーがコンマ (`,`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f939-147">The user specifies a comma (`,`) as the terminator of each field.</span></span>  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 <span data-ttu-id="6f939-148">テーブルの列ごとに、列の順番に従って、同等のプロンプトが (必要に応じて) 表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f939-148">Equivalent prompts (as needed) are displayed for each of the table columns in order.</span></span>  
  
##  <a name="storing-field-by-field-data-in-a-non-xml-format-file"></a><a name="FieldByFieldNonXmlFF"></a> <span data-ttu-id="6f939-149">XML 以外のフォーマット ファイルでのフィールドごとのデータの格納</span><span class="sxs-lookup"><span data-stu-id="6f939-149">Storing Field-by-Field Data in a Non-XML Format File</span></span>  
 <span data-ttu-id="6f939-150">すべてのテーブル列の情報を指定すると、`bcp` コマンドから XML 以外のフォーマット ファイルを生成することを求められます。この生成は省略可能です。このフォーマット ファイルには、プロンプトに応じて指定したフィールドごとの情報が格納されます (上記の例を参照)。</span><span class="sxs-lookup"><span data-stu-id="6f939-150">After all of the table columns are specified, the `bcp` command prompts you to optionally generate a non-XML format file that stores the field-by-field information just supplied (see the preceding example).</span></span> <span data-ttu-id="6f939-151">フォーマット ファイルを生成することを選択すると、いつでも、そのテーブルからデータをエクスポートしたり、同じような構造のデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="6f939-151">If you choose to generate a format file, you can whenever you export data out of that table or import like-structured data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f939-152">フォーマット ファイルを使用して、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータを一括インポートできます。また、形式を再度指定しないで、そのテーブルからデータを一括エクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="6f939-152">You can use the format file to bulk import data from the data file into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to bulk export data from the table, without needing to respecify the format.</span></span> <span data-ttu-id="6f939-153">詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f939-153">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="6f939-154">次の例では、 `myFormatFile.fmt`という名前の XML 以外のフォーマット ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f939-154">The following example creates a non-XML format file named `myFormatFile.fmt`:</span></span>  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 <span data-ttu-id="6f939-155">フォーマット ファイルの既定の名前は bcp.fmt ですが、必要に応じて別のファイル名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6f939-155">The default name for the format file is bcp.fmt, but you can specify a different file name if you choose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f939-156">文字形式やネイティブ形式など、ファイル保存形式に 1 つのデータ形式を使用するデータ ファイルの場合は、 **format** オプションを使用することで、データをエクスポートまたはインポートしなくても、フォーマット ファイルをすばやく作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f939-156">For a data file that uses a single data format for its file-storage type, such as character or native format, you can quickly create a format file without exporting or importing data by using the **format** option.</span></span> <span data-ttu-id="6f939-157">この方法は簡単で、XML フォーマット ファイルと XML 以外のフォーマット ファイルのどちらも作成できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="6f939-157">This approach has the advantages of being easy and of allowing you to create either an XML format file or a non-XML format file.</span></span> <span data-ttu-id="6f939-158">詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6f939-158">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6f939-159">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6f939-159">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6f939-160">bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6f939-160">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="6f939-161">bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6f939-161">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="6f939-162">bcp を使用したフィールド長の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6f939-162">Specify Field Length by Using bcp &#40;SQL Server&#41;</span></span>](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="6f939-163">フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6f939-163">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="6f939-164">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6f939-164">Related Content</span></span>  
 <span data-ttu-id="6f939-165">[なし] :</span><span class="sxs-lookup"><span data-stu-id="6f939-165">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f939-166">参照</span><span class="sxs-lookup"><span data-stu-id="6f939-166">See Also</span></span>  
 <span data-ttu-id="6f939-167">[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6f939-167">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="6f939-168">[一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6f939-168">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 <span data-ttu-id="6f939-169">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="6f939-169">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="6f939-170">データ型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6f939-170">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
