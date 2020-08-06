---
title: XML フォーマット ファイル (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], XML format files
- bulk importing [SQL Server], format files
- XML format files [SQL Server]
ms.assetid: 69024aad-eeea-4187-8fea-b49bc2359849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cc1e8de30fa582898ef8516b9767dec14c4fa81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643839"
---
# <a name="xml-format-files-sql-server"></a><span data-ttu-id="63977-102">XML フォーマット ファイル (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63977-102">XML Format Files (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="63977-103">には、 *のテーブルにデータを一括インポートする目的で使用する* XML フォーマット ファイル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を記述するための構文を定義した XML スキーマが用意されています。</span><span class="sxs-lookup"><span data-stu-id="63977-103">provides an XML schema that defines syntax for writing *XML format files* to use for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="63977-104">このスキーマは XML Schema Definition Language (XSDL) で定義されています。XML フォーマット ファイルはこのスキーマに準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-104">XML format files must adhere to this schema, which is defined in the XML Schema Definition Language (XSDL).</span></span> <span data-ttu-id="63977-105">XML フォーマット ファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ツールが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client と共にインストールされている場合のみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="63977-105">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="63977-106">XML フォーマット ファイルは、**bcp** コマンド、BULK INSERT ステートメント、または INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントのいずれかを使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="63977-106">You can use an XML format file with a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="63977-107">**bcp** コマンドを使用して、あるテーブルに対する XML フォーマット ファイルを自動的に生成できます。詳細については、「 [bcp Utility](../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-107">The **bcp** command allows you to automatically generate an XML format file for a table; for more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63977-108">一括エクスポートおよび一括インポート用に 2 種類のフォーマット ファイルがサポートされています。 *XML 以外のフォーマット ファイル* と *XML フォーマット ファイル*です。</span><span class="sxs-lookup"><span data-stu-id="63977-108">Two types of format files are supported for bulk exporting and importing: *non-XML format files* and *XML format files*.</span></span> <span data-ttu-id="63977-109">XML フォーマット ファイルは XML 以外のフォーマット ファイルに比べ、柔軟かつ強力です。</span><span class="sxs-lookup"><span data-stu-id="63977-109">XML format files provide a flexible and powerful alternative to non-XML format files.</span></span> <span data-ttu-id="63977-110">XML 以外のフォーマット ファイルの詳細については、「 [XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-110">For information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="benefits-of-xml-format-files"></a><a name="BenefitsOfXmlFFs"></a> <span data-ttu-id="63977-111">XML フォーマット ファイルの利点</span><span class="sxs-lookup"><span data-stu-id="63977-111">Benefits of XML Format Files</span></span>  
  
-   <span data-ttu-id="63977-112">XML フォーマット ファイルは、自己記述型を特徴とし、見やすく簡単に作成、拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="63977-112">XML format files are self-describing, making them easy to read, create, and extend.</span></span> <span data-ttu-id="63977-113">人間に読みやすいように書かれているので、一括操作でのデータの解釈方法を容易に理解できます。</span><span class="sxs-lookup"><span data-stu-id="63977-113">They are human readable, making it easy to understand how data is interpreted during bulk operations.</span></span>  
  
-   <span data-ttu-id="63977-114">XML フォーマット ファイルには、ターゲット列のデータ型が格納されています。</span><span class="sxs-lookup"><span data-stu-id="63977-114">XML format files contain the data types of target columns.</span></span>  <span data-ttu-id="63977-115">XML エンコーディングでは、データ ファイルのデータ型およびデータ要素だけでなく、データ要素とテーブル列の間のマッピングを明確に記述できます。</span><span class="sxs-lookup"><span data-stu-id="63977-115">The XML encoding clearly describes the data types and data elements of the data file and also the mapping between data elements and table columns.</span></span>  
  
     <span data-ttu-id="63977-116">これにより、データ ファイルでのデータの表記方法と、ファイル内の各フィールドに関連付けられるデータ型を切り離すことができます。</span><span class="sxs-lookup"><span data-stu-id="63977-116">This enables separation between how data is represented in the data file and what data type is associated with each field in the file.</span></span> <span data-ttu-id="63977-117">たとえば、データ ファイルにデータの文字表記が含まれている場合、対応する SQL 列の型が失われます。</span><span class="sxs-lookup"><span data-stu-id="63977-117">For example, if a data file contains a character representation of the data, the corresponding SQL column type is lost.</span></span>  
  
-   <span data-ttu-id="63977-118">XML フォーマット ファイルがあることで、データ ファイルから、単一のラージ オブジェクト (LOB) データ型を格納するフィールドを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="63977-118">An XML format file allows for loading of a field that contains a single large object (LOB) data type from a data file.</span></span>  
  
-   <span data-ttu-id="63977-119">XML フォーマット ファイルは機能を拡張できますが、以前のバージョンとの互換性も保たれます。</span><span class="sxs-lookup"><span data-stu-id="63977-119">An XML format file can be enhanced yet remain compatible with its earlier versions.</span></span> <span data-ttu-id="63977-120">さらに XML エンコーディングは明確なので、特定のデータ ファイルに対して複数のフォーマット ファイルを容易に作成できます。</span><span class="sxs-lookup"><span data-stu-id="63977-120">Furthermore, the clarity of XML encoding facilitates the creation of multiple format files for a given data file.</span></span> <span data-ttu-id="63977-121">この特性は、データ フィールドの全体または一部を、さまざまなテーブルまたはビューの列にマップする必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="63977-121">This is useful if you have to map all or some of the data fields to columns in different tables or views.</span></span>  
  
-   <span data-ttu-id="63977-122">XML の構文は、操作の方向とは関係がありません。つまり、一括エクスポートでも一括インポートでも構文は同じです。</span><span class="sxs-lookup"><span data-stu-id="63977-122">The XML syntax is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span>  
  
-   <span data-ttu-id="63977-123">XML フォーマット ファイルを使用すると、テーブルまたは非パーティション ビューにデータの一括インポートを行ったり、データの一括エクスポートを行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="63977-123">You can use XML format files to bulk import data into tables or non-partitioned views and to bulk export data.</span></span>  
  
-   <span data-ttu-id="63977-124">OPENROWSET(BULK...) 関数では、対象テーブルの指定は省略できます。</span><span class="sxs-lookup"><span data-stu-id="63977-124">For the OPENROWSET(BULK...) function specifying a target table is optional.</span></span> <span data-ttu-id="63977-125">これは、この関数が XML フォーマット ファイルを使用してデータ ファイルからデータを読み取るためです。</span><span class="sxs-lookup"><span data-stu-id="63977-125">This is because the function relies on the XML format file to read data from a data file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63977-126">対象テーブル列を使用して型変換を行う **bcp** コマンドと BULK INSERT ステートメントでは、対象テーブルが必要となります。</span><span class="sxs-lookup"><span data-stu-id="63977-126">A target table is necessary with the **bcp** command and the BULK INSERT statement, which uses the target table columns to do the type conversion.</span></span>  
  
##  <a name="structure-of-xml-format-files"></a><a name="StructureOfXmlFFs"></a> <span data-ttu-id="63977-127">XML フォーマット ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="63977-127">Structure of XML Format Files</span></span>  
 <span data-ttu-id="63977-128">XML 以外のフォーマット ファイルと同様に、XML フォーマット ファイルでもデータ ファイル内のデータ フィールドの形式および構造を定義し、定義したデータ フィールドを 1 つのマップ先テーブル内の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="63977-128">Like a non-XML format file, an XML format file defines the format and structure of the data fields in a data file and maps those data fields to columns in a single target table.</span></span>  
  
 <span data-ttu-id="63977-129">XML フォーマット ファイルには、\<RECORD> と \<ROW> という 2 つの主要なコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="63977-129">An XML format file possesses two main components, \<RECORD> and \<ROW>:</span></span>  
  
-   <span data-ttu-id="63977-130">\<RECORD> にはデータ ファイルに保存するデータをそのまま記述します。</span><span class="sxs-lookup"><span data-stu-id="63977-130">\<RECORD> describes the data as it is stored in the data file.</span></span>  
  
     <span data-ttu-id="63977-131">各 \<RECORD> 要素は、1 つ以上の \<FIELD> 要素のセットを格納します。</span><span class="sxs-lookup"><span data-stu-id="63977-131">Each \<RECORD> element contains a set of one or more \<FIELD> elements.</span></span> <span data-ttu-id="63977-132">それらの要素はデータ ファイル内のフィールドに対応します。</span><span class="sxs-lookup"><span data-stu-id="63977-132">These elements correspond to fields in the data file.</span></span> <span data-ttu-id="63977-133">基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="63977-133">The basic syntax is as follows:</span></span>  
  
     \<RECORD>  
  
     <span data-ttu-id="63977-134">\<FIELD .../> [ ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="63977-134">\<FIELD .../> [ ...*n* ]</span></span>  
  
     \</RECORD>  
  
     <span data-ttu-id="63977-135">各 \<FIELD> 要素には、特定のデータ フィールドの内容を記述します。</span><span class="sxs-lookup"><span data-stu-id="63977-135">Each \<FIELD> element describes the contents of a specific data field.</span></span> <span data-ttu-id="63977-136">個々のフィールドは、テーブル内の 1 つの列にのみマップできます。</span><span class="sxs-lookup"><span data-stu-id="63977-136">A field can only be mapped to one column in the table.</span></span> <span data-ttu-id="63977-137">すべてのフィールドを列にマップする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="63977-137">Not all fields need to be mapped to columns.</span></span>  
  
     <span data-ttu-id="63977-138">データ ファイルのフィールドは、固定/可変長にすることも、任意の文字で区切ることもできます。</span><span class="sxs-lookup"><span data-stu-id="63977-138">A field in a data file can be either of fixed/variable length or character terminated.</span></span> <span data-ttu-id="63977-139">*フィールドの値* は、半角文字 (1 バイト表現を使用)、全角文字 (Unicode の 2 バイト表現を使用)、ネイティブ データベース形式、またはファイル名で表現できます。</span><span class="sxs-lookup"><span data-stu-id="63977-139">A *field value* can be represented as: a character (using single-byte representation), a wide character (using Unicode two-byte representation), native database format, or a file name.</span></span> <span data-ttu-id="63977-140">フィールドの値をファイル名で表現する場合、対象になるテーブルの BLOB 列の値を含むファイルをそのファイル名で指すようにします。</span><span class="sxs-lookup"><span data-stu-id="63977-140">If a field value is represented as a file name, the file name points to the file that contains the value of a BLOB column in the target table.</span></span>  
  
-   <span data-ttu-id="63977-141">\<ROW> には、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータをインポートするときのデータ行の構成方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="63977-141">\<ROW> describes how to construct data rows from a data file when the data from the file is imported into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
     <span data-ttu-id="63977-142">\<ROW> 要素は、\<COLUMN> 要素のセットを格納します。</span><span class="sxs-lookup"><span data-stu-id="63977-142">A \<ROW> element contains a set of \<COLUMN> elements.</span></span> <span data-ttu-id="63977-143">それらの要素はテーブル列に対応します。</span><span class="sxs-lookup"><span data-stu-id="63977-143">These elements correspond to table columns.</span></span> <span data-ttu-id="63977-144">基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="63977-144">The basic syntax is as follows:</span></span>  
  
     \<ROW>  
  
     <span data-ttu-id="63977-145">\<COLUMN .../> [ ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="63977-145">\<COLUMN .../> [ ...*n* ]</span></span>  
  
     \</ROW>  
  
     <span data-ttu-id="63977-146">個々の \<COLUMN> 要素は、データ ファイル内の 1 つのフィールドにのみマップできます。</span><span class="sxs-lookup"><span data-stu-id="63977-146">Each \<COLUMN> element can be mapped to only one field in the data file.</span></span> <span data-ttu-id="63977-147">\<ROW> 要素内の \<COLUMN> 要素の順序により、一括操作で返される順序が決定されます。</span><span class="sxs-lookup"><span data-stu-id="63977-147">The order of the \<COLUMN> elements in the \<ROW> element defines the order in which they are returned by the bulk operation.</span></span> <span data-ttu-id="63977-148">XML フォーマット ファイルでは、一括インポート操作の対象になるテーブルの列とのリレーションシップがない各 \<COLUMN> 要素にローカル名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="63977-148">The XML format file assigns each \<COLUMN> element a local name that has no relationship to the column in the target table of a bulk import operation.</span></span>  
  
##  <a name="schema-syntax-for-xml-format-files"></a><a name="SchemaSyntax"></a> <span data-ttu-id="63977-149">XML フォーマット ファイルのスキーマ構文</span><span class="sxs-lookup"><span data-stu-id="63977-149">Schema Syntax for XML Format Files</span></span>  
 <span data-ttu-id="63977-150">このセクションでは、XML フォーマット ファイルに対する XML スキーマの要素および属性について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-150">This section contains a summary of the elements and attributes of the XML schema for XML format files.</span></span> <span data-ttu-id="63977-151">フォーマット ファイルの構文は、操作の方向とは関係がありません。つまり、一括エクスポートでも一括インポートでも構文は同じです。</span><span class="sxs-lookup"><span data-stu-id="63977-151">The syntax of a format file is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span> <span data-ttu-id="63977-152">また、一括インポートで \<ROW> 要素と \<COLUMN> 要素を使用する方法、および要素の xsi:type 値をデータ セットに格納する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-152">This section also considers how bulk import uses the \<ROW> and \<COLUMN> elements and how to put the xsi:type value of an element into a data set.</span></span>  
  
 <span data-ttu-id="63977-153">構文が実際の XML フォーマット ファイルとどのように対応しているかについては、このトピックの「 [XML フォーマット ファイルのサンプル](#SampleXmlFFs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-153">To see how the syntax corresponds to actual XML format files, see [Sample XML Format Files](#SampleXmlFFs), later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63977-154">フォーマット ファイルを変更して、フィールドの数や順序がテーブル列とは異なるデータ ファイルから一括インポートできます。</span><span class="sxs-lookup"><span data-stu-id="63977-154">You can modify a format file to let you bulk import from a data file in which the number and/or order of the fields differ from the number and/or order of table columns.</span></span> <span data-ttu-id="63977-155">詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-155">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
  
  
###  <a name="basic-syntax-of-the-xml-schema"></a><a name="BasicSyntax"></a> <span data-ttu-id="63977-156">XML スキーマの基本構文</span><span class="sxs-lookup"><span data-stu-id="63977-156">Basic Syntax of the XML Schema</span></span>  
 <span data-ttu-id="63977-157">この基本構文のステートメントでは、要素 (\<BCPFORMAT>、\<RECORD>、\<FIELD>、\<ROW>、\<COLUMN>) とその基本属性のみを示します。</span><span class="sxs-lookup"><span data-stu-id="63977-157">This syntax statements show only the elements (\<BCPFORMAT>, \<RECORD>, \<FIELD>, \<ROW>, and \<COLUMN>) and their basic attributes.</span></span>  
  
 \<BCPFORMAT ...>  
  
 \<RECORD>  
  
 <span data-ttu-id="63977-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span><span class="sxs-lookup"><span data-stu-id="63977-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span></span>  
  
 />  
  
 \</RECORD>  
  
 \<ROW>  
  
 <span data-ttu-id="63977-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span><span class="sxs-lookup"><span data-stu-id="63977-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span></span>  
  
 />  
  
 \</ROW>  
  
 \</BCPFORMAT>  
  
> [!NOTE]  
>  <span data-ttu-id="63977-160">\<FIELD> 要素または \<COLUMN> 要素の xsi:type の値と関連付けられている他の属性については、このトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-160">Additional attributes that are associated with the value of the xsi:type in a \<FIELD> or \<COLUMN> element are described later in this topic.</span></span>  
  

  
####  <a name="schema-elements"></a><a name="SchemaElements"></a> <span data-ttu-id="63977-161">Schema 要素</span><span class="sxs-lookup"><span data-stu-id="63977-161">Schema Elements</span></span>  
 <span data-ttu-id="63977-162">ここでは、XML スキーマで XML フォーマット ファイル用に定義している各要素の目的を説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-162">This section summarizes the purpose of each element that the XML schema defines for XML format files.</span></span> <span data-ttu-id="63977-163">各要素の属性については、このトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-163">The attributes are described in separate sections later in this topic.</span></span>  
  
 \<BCPFORMAT>  
 <span data-ttu-id="63977-164">特定のデータ ファイルのレコード構造とテーブル内の対応するテーブル行の列を定義するフォーマット ファイル要素です。</span><span class="sxs-lookup"><span data-stu-id="63977-164">Is the format-file element that defines the record structure of a given data file and its correspondence to the columns of a table row in the table.</span></span>  
  
 \<RECORD .../>  
 <span data-ttu-id="63977-165">1 つ以上の \<FIELD> 要素を含む複合要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-165">Defines a complex element containing one or more \<FIELD> elements.</span></span> <span data-ttu-id="63977-166">フォーマット ファイルでフィールドが宣言される順序は、データ ファイルでフィールドが表示される順序と同じです。</span><span class="sxs-lookup"><span data-stu-id="63977-166">The order in which the fields are declared in the format file is the order in which those fields appear in the data file.</span></span>  
  
 \<FIELD .../>  
 <span data-ttu-id="63977-167">データを含むデータ ファイル内のフィールドを定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-167">Defines a field in data file, which contains data.</span></span>  
  
 <span data-ttu-id="63977-168">この要素の属性については、このトピックの「[\<FIELD> 要素の属性](#AttrOfFieldElement)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-168">The attributes of this element are discussed in [Attributes of the \<FIELD> Element](#AttrOfFieldElement), later in this topic.</span></span>  
  
 \<ROW .../>  
 <span data-ttu-id="63977-169">1 つ以上の \<COLUMN> 要素を含む複合要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-169">Defines a complex element containing one or more \<COLUMN> elements.</span></span> <span data-ttu-id="63977-170">\<COLUMN> 要素の順序は、RECORD 定義の \<FIELD> 要素の順序とは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="63977-170">The order of the \<COLUMN> elements is independent of the order of \<FIELD> elements in a RECORD definition.</span></span> <span data-ttu-id="63977-171">結果行セットの列の順序は、フォーマット ファイルの \<COLUMN> 要素の順序で決まります。</span><span class="sxs-lookup"><span data-stu-id="63977-171">Rather, the order of the \<COLUMN> elements in a format file determines the column order of the resultant rowset.</span></span> <span data-ttu-id="63977-172">データ フィールドは、対応する \<COLUMN> 要素が \<COLUMN> 要素内で宣言されている順序で読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="63977-172">Data fields are loaded in the order in which the corresponding \<COLUMN> elements are declared in the \<COLUMN> element.</span></span>  
  
 <span data-ttu-id="63977-173">詳細については、このトピックの「[一括インポートで \<ROW> 要素を使用する方法](#HowUsesROW)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-173">For more information, see [How Bulk Import Uses the \<ROW> Element](#HowUsesROW), later in this topic.</span></span>  
  
 \<COLUMN>  
 <span data-ttu-id="63977-174">列を要素 (\<COLUMN>) として定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-174">Defines a column as an element (\<COLUMN>).</span></span> <span data-ttu-id="63977-175">各 \<COLUMN> 要素は、\<FIELD> 要素に対応しています (この要素の ID は、\<COLUMN> 要素の SOURCE 属性で指定されます)。</span><span class="sxs-lookup"><span data-stu-id="63977-175">Each \<COLUMN> element corresponds to a \<FIELD> element (whose ID is specified in the SOURCE attribute of the \<COLUMN> element).</span></span>  
  
 <span data-ttu-id="63977-176">この要素の属性については、このトピックの「[\<COLUMN> 要素の属性](#AttrOfColumnElement)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-176">The attributes of this element are discussed in [Attributes of the \<COLUMN> Element](#AttrOfColumnElement), later in this topic.</span></span> <span data-ttu-id="63977-177">また、このトピックの「[一括インポートで \<COLUMN> 要素を使用する方法](#HowUsesColumn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-177">Also see, [How Bulk Import Uses the \<COLUMN> Element](#HowUsesColumn), later in this topic.</span></span>  
  
 \</BCPFORMAT>  
 <span data-ttu-id="63977-178">フォーマット ファイルを終了するために必要なフォーマット ファイル要素です。</span><span class="sxs-lookup"><span data-stu-id="63977-178">Required to end the format file.</span></span>  
  
####  <a name="attributes-of-the-field-element"></a><a name="AttrOfFieldElement"></a> <span data-ttu-id="63977-179">\<FIELD> 要素の属性</span><span class="sxs-lookup"><span data-stu-id="63977-179">Attributes of the \<FIELD> Element</span></span>  
 <span data-ttu-id="63977-180">ここでは、次のスキーマ構文に示す \<FIELD> 要素の属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-180">This section describes the attributes of the \<FIELD> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="63977-181"><FIELD</span><span class="sxs-lookup"><span data-stu-id="63977-181"><FIELD</span></span>  
  
 <span data-ttu-id="63977-182">ID **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-182">ID **="*`fieldID`*"**</span></span>  
  
 <span data-ttu-id="63977-183">xsi **:** type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-183">xsi **:** type **="*`fieldType`*"**</span></span>  
  
 <span data-ttu-id="63977-184">[ LENGTH **="*`n`*"** ]</span><span class="sxs-lookup"><span data-stu-id="63977-184">[ LENGTH **="*`n`*"** ]</span></span>  
  
 <span data-ttu-id="63977-185">[PREFIX_LENGTH **= " *`p`* "** ]</span><span class="sxs-lookup"><span data-stu-id="63977-185">[ PREFIX_LENGTH **="*`p`*"** ]</span></span>  
  
 <span data-ttu-id="63977-186">[MAX_LENGTH **= " *`m`* "** ]</span><span class="sxs-lookup"><span data-stu-id="63977-186">[ MAX_LENGTH **="*`m`*"** ]</span></span>  
  
 <span data-ttu-id="63977-187">[COLLATION **= " *`collationName`* "** ]</span><span class="sxs-lookup"><span data-stu-id="63977-187">[ COLLATION **="*`collationName`*"** ]</span></span>  
  
 <span data-ttu-id="63977-188">[ターミネータ **= " *`terminator`* "** ]</span><span class="sxs-lookup"><span data-stu-id="63977-188">[ TERMINATOR **="*`terminator`*"** ]</span></span>  
  
 />  
  
 <span data-ttu-id="63977-189">それぞれの \<FIELD> 要素は、他の要素から独立しています。</span><span class="sxs-lookup"><span data-stu-id="63977-189">Each \<FIELD> element is independent of the others.</span></span> <span data-ttu-id="63977-190">フィールドは、次の属性を使用して表現されます。</span><span class="sxs-lookup"><span data-stu-id="63977-190">A field is described in terms of the following attributes:</span></span>  
  
|<span data-ttu-id="63977-191">FIELD 要素の属性</span><span class="sxs-lookup"><span data-stu-id="63977-191">FIELD Attribute</span></span>|<span data-ttu-id="63977-192">説明</span><span class="sxs-lookup"><span data-stu-id="63977-192">Description</span></span>|<span data-ttu-id="63977-193">省略可能 /</span><span class="sxs-lookup"><span data-stu-id="63977-193">Optional /</span></span><br /><br /> <span data-ttu-id="63977-194">必須</span><span class="sxs-lookup"><span data-stu-id="63977-194">Required</span></span>|  
|---------------------|-----------------|------------------------------|  
|<span data-ttu-id="63977-195">ID **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-195">ID **="*`fieldID`*"**</span></span>|<span data-ttu-id="63977-196">データ ファイル内のフィールドの論理名を指定します。</span><span class="sxs-lookup"><span data-stu-id="63977-196">Specifies the logical name of the field in the data file.</span></span> <span data-ttu-id="63977-197">フィールドの ID は、フィールドを参照する際に使用するキーになります。</span><span class="sxs-lookup"><span data-stu-id="63977-197">The ID of a field is the key used to refer to the field.</span></span><br /><br /> <span data-ttu-id="63977-198"><フィールド ID **= " *`fieldID`* "**/> は <COLUMN SOURCE **= " *`fieldID`* "** にマップされる/></span><span class="sxs-lookup"><span data-stu-id="63977-198"><FIELD ID **="*`fieldID`*"**/> maps to <COLUMN SOURCE **="*`fieldID`*"**/></span></span>|<span data-ttu-id="63977-199">必須</span><span class="sxs-lookup"><span data-stu-id="63977-199">Required</span></span>|  
|<span data-ttu-id="63977-200">xsi: type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-200">xsi:type **="*`fieldType`*"**</span></span>|<span data-ttu-id="63977-201">要素のインスタンスの種類を特定する XML コンストラクトです (これは属性のように使用します)。</span><span class="sxs-lookup"><span data-stu-id="63977-201">This is an XML construct (used like an attribute) that identifies the type of the instance of the element.</span></span> <span data-ttu-id="63977-202">*fieldType* の値により、要素のインスタンスで必要なオプションの属性 (下記参照) が決まります。</span><span class="sxs-lookup"><span data-stu-id="63977-202">The value of *fieldType* determines which of the optional attributes (below) you need in a given instance.</span></span>|<span data-ttu-id="63977-203">必須 (データ型により異なる)</span><span class="sxs-lookup"><span data-stu-id="63977-203">Required (depending on the data type)</span></span>|  
|<span data-ttu-id="63977-204">長さ **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-204">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="63977-205">固定長データ型のインスタンスの長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-205">This attribute defines the length for an instance of a fixed-length data type.</span></span><br /><br /> <span data-ttu-id="63977-206">*n* の値は、正の整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-206">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="63977-207">省略可能 (xsi:type 値で必要な場合は必須)。</span><span class="sxs-lookup"><span data-stu-id="63977-207">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="63977-208">PREFIX_LENGTH **= " *`p`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-208">PREFIX_LENGTH **="*`p`*"**</span></span>|<span data-ttu-id="63977-209">バイナリ データ表現のプレフィックス長を定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-209">This attribute defines the prefix length for a binary data representation.</span></span> <span data-ttu-id="63977-210">PREFIX_LENGTH 値の *p* は、1、2、4、または 8 のいずれかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-210">The PREFIX_LENGTH value, *p*, must be one of the following: 1, 2, 4, or 8.</span></span>|<span data-ttu-id="63977-211">省略可能 (xsi:type 値で必要な場合は必須)。</span><span class="sxs-lookup"><span data-stu-id="63977-211">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="63977-212">MAX_LENGTH **= " *`m`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-212">MAX_LENGTH **="*`m`*"**</span></span>|<span data-ttu-id="63977-213">指定したフィールドに格納できる最大バイト数を定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-213">This attribute is the maximum number of bytes that can be stored in a given field.</span></span> <span data-ttu-id="63977-214">対象のテーブルがない場合、列の最大長を決めることはできません。</span><span class="sxs-lookup"><span data-stu-id="63977-214">Without a target table, the column max-length is not known.</span></span> <span data-ttu-id="63977-215">MAX_LENGTH 属性では、出力先の文字列型の列の最大長を制限し、列の値に割り当てる領域を制限しています。</span><span class="sxs-lookup"><span data-stu-id="63977-215">The MAX_LENGTH attribute restricts the maximum length of an output character column, limiting the storage allocated for the column value.</span></span> <span data-ttu-id="63977-216">この属性は、SELECT FROM 句で OPENROWSET 関数の BULK オプションを使用している場合に特に有益です。</span><span class="sxs-lookup"><span data-stu-id="63977-216">This is especially convenient when using the OPENROWSET function's BULK option in a SELECT FROM clause.</span></span><br /><br /> <span data-ttu-id="63977-217">*m* の値は、正の整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-217">The value of *m* must be a positive integer.</span></span> <span data-ttu-id="63977-218">既定では、 **char** 列の最大長は 8,000 文字で、 **nchar** 列の最大長は 4,000 文字です。</span><span class="sxs-lookup"><span data-stu-id="63977-218">By default, the maximum length is 8000 characters for a **char** column and 4000 characters for an **nchar** column.</span></span>|<span data-ttu-id="63977-219">省略可能</span><span class="sxs-lookup"><span data-stu-id="63977-219">Optional</span></span>|  
|<span data-ttu-id="63977-220">COLLATION **= " *`collationName`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-220">COLLATION **="*`collationName`*"**</span></span>|<span data-ttu-id="63977-221">COLLATION は、文字列型のフィールドでのみ使用できる属性です。</span><span class="sxs-lookup"><span data-stu-id="63977-221">COLLATION is only allowed for character fields.</span></span> <span data-ttu-id="63977-222">SQL 照合順序名の一覧については、「[SQL Server の照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-222">For a list of the SQL collation names, see [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).</span></span>|<span data-ttu-id="63977-223">省略可能</span><span class="sxs-lookup"><span data-stu-id="63977-223">Optional</span></span>|  
|<span data-ttu-id="63977-224">ターミネータ **= " *`terminator`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-224">TERMINATOR **= "*`terminator`*"**</span></span>|<span data-ttu-id="63977-225">データ フィールドのターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="63977-225">This attribute specifies the terminator of a data field.</span></span> <span data-ttu-id="63977-226">ターミネータには、任意の文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="63977-226">The terminator can be any character.</span></span> <span data-ttu-id="63977-227">ただし、ターミネータには、データに含まれていない一意な文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-227">The terminator must be a unique character that is not part of the data.</span></span><br /><br /> <span data-ttu-id="63977-228">既定では、フィールド ターミネータはタブ文字 (\t) です。</span><span class="sxs-lookup"><span data-stu-id="63977-228">By default, the field terminator is the tab character (represented as \t).</span></span> <span data-ttu-id="63977-229">段落記号を表すには、\r\n を使用します。</span><span class="sxs-lookup"><span data-stu-id="63977-229">To represent a paragraph mark, use \r\n.</span></span>|<span data-ttu-id="63977-230">この属性が必要な文字型データの xsi:type でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="63977-230">Used only with an xsi:type of character data, which requires this attribute</span></span>|  
  
#####  <a name="xsitype-values-of-the-field-element"></a><a name="XsiTypeValuesOfFIELD"></a> <span data-ttu-id="63977-231">\<FIELD> 要素の Xsi:type 値</span><span class="sxs-lookup"><span data-stu-id="63977-231">Xsi:type values of the \<FIELD> Element</span></span>  
 <span data-ttu-id="63977-232">xsi:type 値は、要素のインスタンスのデータ型を特定する XML コンストラクトです (これは属性のように使用します)。</span><span class="sxs-lookup"><span data-stu-id="63977-232">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="63977-233">詳細については、このトピックの「xsi:type 値のデータセットへの格納」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-233">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="63977-234">\<FIELD> 要素の xsi:type 値では、次のデータ型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="63977-234">The xsi:type value of the \<FIELD> element supports the following data types.</span></span>  
  
|<span data-ttu-id="63977-235">\<FIELD> の xsi:type 値</span><span class="sxs-lookup"><span data-stu-id="63977-235">\<FIELD> xsi:type values</span></span>|<span data-ttu-id="63977-236">必要な XML</span><span class="sxs-lookup"><span data-stu-id="63977-236">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="63977-237">属性</span><span class="sxs-lookup"><span data-stu-id="63977-237">for Data Type</span></span>|<span data-ttu-id="63977-238">データ型に関する省略可能な XML</span><span class="sxs-lookup"><span data-stu-id="63977-238">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="63977-239">属性</span><span class="sxs-lookup"><span data-stu-id="63977-239">for Data Type</span></span>|  
|-------------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="63977-240">**NativeFixed**</span><span class="sxs-lookup"><span data-stu-id="63977-240">**NativeFixed**</span></span>|`LENGTH`|<span data-ttu-id="63977-241">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-241">None.</span></span>|  
|<span data-ttu-id="63977-242">**NativePrefix**</span><span class="sxs-lookup"><span data-stu-id="63977-242">**NativePrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="63977-243">MAX_LENGTH</span><span class="sxs-lookup"><span data-stu-id="63977-243">MAX_LENGTH</span></span>|  
|<span data-ttu-id="63977-244">**CharFixed**</span><span class="sxs-lookup"><span data-stu-id="63977-244">**CharFixed**</span></span>|`LENGTH`|<span data-ttu-id="63977-245">COLLATION</span><span class="sxs-lookup"><span data-stu-id="63977-245">COLLATION</span></span>|  
|<span data-ttu-id="63977-246">**NCharFixed**</span><span class="sxs-lookup"><span data-stu-id="63977-246">**NCharFixed**</span></span>|`LENGTH`|<span data-ttu-id="63977-247">COLLATION</span><span class="sxs-lookup"><span data-stu-id="63977-247">COLLATION</span></span>|  
|<span data-ttu-id="63977-248">**CharPrefix**</span><span class="sxs-lookup"><span data-stu-id="63977-248">**CharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="63977-249">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="63977-249">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="63977-250">**NCharPrefix**</span><span class="sxs-lookup"><span data-stu-id="63977-250">**NCharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="63977-251">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="63977-251">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="63977-252">**CharTerm**</span><span class="sxs-lookup"><span data-stu-id="63977-252">**CharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="63977-253">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="63977-253">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="63977-254">**NCharTerm**</span><span class="sxs-lookup"><span data-stu-id="63977-254">**NCharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="63977-255">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="63977-255">MAX_LENGTH, COLLATION</span></span>|  
  
 <span data-ttu-id="63977-256">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型について詳しくは、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="63977-256">For more information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
####  <a name="attributes-of-the-column-element"></a><a name="AttrOfColumnElement"></a> <span data-ttu-id="63977-257">\<COLUMN> 要素の属性</span><span class="sxs-lookup"><span data-stu-id="63977-257">Attributes of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="63977-258">ここでは、次のスキーマ構文に示す \<COLUMN> 要素の属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-258">This section describes the attributes of the \<COLUMN> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="63977-259">\<要素の xsi:type 値</span><span class="sxs-lookup"><span data-stu-id="63977-259">\<COLUMN</span></span>  
  
 <span data-ttu-id="63977-260">SOURCE = "*fieldID*"</span><span class="sxs-lookup"><span data-stu-id="63977-260">SOURCE = "*fieldID*"</span></span>  
  
 <span data-ttu-id="63977-261">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="63977-261">NAME = "*columnName*"</span></span>  
  
 <span data-ttu-id="63977-262">xsi:type = "*columnType*"</span><span class="sxs-lookup"><span data-stu-id="63977-262">xsi:type = "*columnType*"</span></span>  
  
 <span data-ttu-id="63977-263">[ LENGTH = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="63977-263">[ LENGTH = "*n*" ]</span></span>  
  
 <span data-ttu-id="63977-264">[ PRECISION = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="63977-264">[ PRECISION = "*n*" ]</span></span>  
  
 <span data-ttu-id="63977-265">[ SCALE = "*value*" ]</span><span class="sxs-lookup"><span data-stu-id="63977-265">[ SCALE = "*value*" ]</span></span>  
  
 <span data-ttu-id="63977-266">[ NULLABLE = { "YES"</span><span class="sxs-lookup"><span data-stu-id="63977-266">[ NULLABLE = { "YES"</span></span>  
  
 <span data-ttu-id="63977-267">"NO" } ]</span><span class="sxs-lookup"><span data-stu-id="63977-267">"NO" } ]</span></span>  
  
 />  
  
 <span data-ttu-id="63977-268">フィールドは、次の属性を使用して、対象となるテーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="63977-268">A field is mapped to a column in the target table using the following attributes:</span></span>  
  
|<span data-ttu-id="63977-269">COLUMN 要素の属性</span><span class="sxs-lookup"><span data-stu-id="63977-269">COLUMN Attribute</span></span>|<span data-ttu-id="63977-270">説明</span><span class="sxs-lookup"><span data-stu-id="63977-270">Description</span></span>|<span data-ttu-id="63977-271">省略可能 /</span><span class="sxs-lookup"><span data-stu-id="63977-271">Optional /</span></span><br /><br /> <span data-ttu-id="63977-272">必須</span><span class="sxs-lookup"><span data-stu-id="63977-272">Required</span></span>|  
|----------------------|-----------------|------------------------------|  
|<span data-ttu-id="63977-273">SOURCE **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-273">SOURCE **="*`fieldID`*"**</span></span>|<span data-ttu-id="63977-274">列にマップされているフィールドの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="63977-274">Specifies the ID of the field being mapped to the column.</span></span><br /><br /> <span data-ttu-id="63977-275"><COLUMN SOURCE **= " *`fieldID`* "**/> は <フィールド ID **= " *`fieldID`* "** にマップされる/></span><span class="sxs-lookup"><span data-stu-id="63977-275"><COLUMN SOURCE **="*`fieldID`*"**/> maps to <FIELD ID **="*`fieldID`*"**/></span></span>|<span data-ttu-id="63977-276">必須</span><span class="sxs-lookup"><span data-stu-id="63977-276">Required</span></span>|  
|<span data-ttu-id="63977-277">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="63977-277">NAME = "*columnName*"</span></span>|<span data-ttu-id="63977-278">フォーマット ファイルで表している行セットの列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="63977-278">Specifies the name of the column in the row set represented by the format file.</span></span> <span data-ttu-id="63977-279">この列名は、結果セット内で列名を特定する際に使用されるので、対象のテーブルで使用されている列名に対応する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="63977-279">This column name is used to identify the column in the result set, and it need not correspond to the column name used in the target table.</span></span>|<span data-ttu-id="63977-280">必須</span><span class="sxs-lookup"><span data-stu-id="63977-280">Required</span></span>|  
|<span data-ttu-id="63977-281">xsi **:** type **= " *`ColumnType`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-281">xsi **:** type **="*`ColumnType`*"**</span></span>|<span data-ttu-id="63977-282">要素のインスタンスのデータ型を特定する XML コンストラクトです (これは属性のように使用します)。</span><span class="sxs-lookup"><span data-stu-id="63977-282">This is an XML construct (used like an attribute) that identifies the data type of the instance of the element.</span></span> <span data-ttu-id="63977-283">*ColumnType* の値により、要素のインスタンスで必要なオプションの属性 (下記参照) が決まります。</span><span class="sxs-lookup"><span data-stu-id="63977-283">The value of *ColumnType* determines which of the optional attributes (below) you need in a given instance.</span></span><br /><br /> <span data-ttu-id="63977-284">注: *ColumnType*とそれらに関連付けられている属性の有効な値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="63977-284">Note: The possible values of *ColumnType* and their associated attributes are listed in the next table.</span></span>|<span data-ttu-id="63977-285">省略可能</span><span class="sxs-lookup"><span data-stu-id="63977-285">Optional</span></span>|  
|<span data-ttu-id="63977-286">長さ **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-286">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="63977-287">固定長データ型のインスタンスの長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="63977-287">Defines the length for an instance of a fixed-length data type.</span></span> <span data-ttu-id="63977-288">LENGTH 属性は、xsi:type が文字列データ型の場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="63977-288">LENGTH is used only when the xsi:type is a string data type.</span></span><br /><br /> <span data-ttu-id="63977-289">*n* の値は、正の整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-289">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="63977-290">省略可能 (xsi:type が文字列データ型の場合にのみ使用可能)</span><span class="sxs-lookup"><span data-stu-id="63977-290">Optional (available only if the xsi:type is a string data type)</span></span>|  
|<span data-ttu-id="63977-291">PRECISION **="*`n`*"**</span><span class="sxs-lookup"><span data-stu-id="63977-291">PRECISION **="*`n`*"**</span></span>|<span data-ttu-id="63977-292">数値全体の桁数を示します。</span><span class="sxs-lookup"><span data-stu-id="63977-292">Indicates the number of digits in a number.</span></span> <span data-ttu-id="63977-293">たとえば、数字 123.45 の有効桁数は 5 桁です。</span><span class="sxs-lookup"><span data-stu-id="63977-293">For example, the number 123.45 has a precision of 5.</span></span><br /><br /> <span data-ttu-id="63977-294">この値は、正の整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-294">The value must be a positive integer.</span></span>|<span data-ttu-id="63977-295">省略可能 (xsi:type が可変数値のデータ型の場合にのみ使用可能)</span><span class="sxs-lookup"><span data-stu-id="63977-295">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="63977-296">SCALE **= " *`int`* "**</span><span class="sxs-lookup"><span data-stu-id="63977-296">SCALE **="*`int`*"**</span></span>|<span data-ttu-id="63977-297">数値の中で小数点より右側の桁数を示します。</span><span class="sxs-lookup"><span data-stu-id="63977-297">Indicates the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="63977-298">たとえば、数字 123.45 の小数点以下桁数は 2 桁です。</span><span class="sxs-lookup"><span data-stu-id="63977-298">For example, the number 123.45 has a scale of 2.</span></span><br /><br /> <span data-ttu-id="63977-299">この値は、整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63977-299">The value must be an integer.</span></span>|<span data-ttu-id="63977-300">省略可能 (xsi:type が可変数値のデータ型の場合にのみ使用可能)</span><span class="sxs-lookup"><span data-stu-id="63977-300">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="63977-301">NULLABLE **=** { **"** YES **"**</span><span class="sxs-lookup"><span data-stu-id="63977-301">NULLABLE **=** { **"** YES **"**</span></span><br /><br /> <span data-ttu-id="63977-302">**"** NO **"** }</span><span class="sxs-lookup"><span data-stu-id="63977-302">**"** NO **"** }</span></span>|<span data-ttu-id="63977-303">列で NULL 値を使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="63977-303">Indicates whether a column can assume NULL values.</span></span> <span data-ttu-id="63977-304">この属性は、FIELDS 要素から完全に独立しています。</span><span class="sxs-lookup"><span data-stu-id="63977-304">This attribute is completely independent of FIELDS.</span></span> <span data-ttu-id="63977-305">ただし、列が NULLABLE ではない場合に、フィールドで NULL が指定された (何も値が指定されない) 場合、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="63977-305">However, if a column is not NULLABLE and field specifies NULL (by not specifying any value), a run-time error results.</span></span><br /><br /> <span data-ttu-id="63977-306">NULLABLE 属性は、単純な SELECT FROM OPENROWSET(BULK...) ステートメントを実行する場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="63977-306">The NULLABLE attribute is used only if you do a plain SELECT FROM OPENROWSET(BULK...) statement.</span></span>|<span data-ttu-id="63977-307">省略可能 (任意のデータ型で使用可能)</span><span class="sxs-lookup"><span data-stu-id="63977-307">Optional (available for any data type)</span></span>|  
  
#####  <a name="xsitype-values-of-the-column-element"></a><a name="XsiTypeValuesOfCOLUMN"></a> <span data-ttu-id="63977-308">\<COLUMN> 要素の Xsi:type 値</span><span class="sxs-lookup"><span data-stu-id="63977-308">Xsi:type values of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="63977-309">xsi:type 値は、要素のインスタンスのデータ型を特定する XML コンストラクトです (これは属性のように使用します)。</span><span class="sxs-lookup"><span data-stu-id="63977-309">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="63977-310">詳細については、このトピックの「xsi:type 値のデータセットへの格納」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-310">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="63977-311">次の表に示すように、\<COLUMN> 要素ではネイティブな SQL データ型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="63977-311">The \<COLUMN> element supports native SQL data types, as follows:</span></span>  
  
|<span data-ttu-id="63977-312">データ型</span><span class="sxs-lookup"><span data-stu-id="63977-312">Type Category</span></span>|<span data-ttu-id="63977-313">\<COLUMN> データ型</span><span class="sxs-lookup"><span data-stu-id="63977-313">\<COLUMN> Data Types</span></span>|<span data-ttu-id="63977-314">必要な XML</span><span class="sxs-lookup"><span data-stu-id="63977-314">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="63977-315">属性</span><span class="sxs-lookup"><span data-stu-id="63977-315">for Data Type</span></span>|<span data-ttu-id="63977-316">データ型に関する省略可能な XML</span><span class="sxs-lookup"><span data-stu-id="63977-316">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="63977-317">属性</span><span class="sxs-lookup"><span data-stu-id="63977-317">for Data Type</span></span>|  
|-------------------|---------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="63977-318">固定</span><span class="sxs-lookup"><span data-stu-id="63977-318">Fixed</span></span>|<span data-ttu-id="63977-319">`SQLBIT`、`SQLTINYINT`、`SQLSMALLINT`、`SQLINT`、`SQLBIGINT`、`SQLFLT4`、`SQLFLT8`、`SQLDATETIME`、`SQLDATETIM4``SQLDATETIM8`、`SQLMONEY`、`SQLMONEY4`、`SQLVARIANT``SQLUNIQUEID`</span><span class="sxs-lookup"><span data-stu-id="63977-319">`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT`, and `SQLUNIQUEID`</span></span>|<span data-ttu-id="63977-320">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-320">None.</span></span>|<span data-ttu-id="63977-321">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="63977-321">NULLABLE</span></span>|  
|<span data-ttu-id="63977-322">可変数値</span><span class="sxs-lookup"><span data-stu-id="63977-322">Variable Number</span></span>|<span data-ttu-id="63977-323">`SQLDECIMAL` および `SQLNUMERIC`</span><span class="sxs-lookup"><span data-stu-id="63977-323">`SQLDECIMAL` and `SQLNUMERIC`</span></span>|<span data-ttu-id="63977-324">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-324">None.</span></span>|<span data-ttu-id="63977-325">NULLABLE、PRECISION、SCALE</span><span class="sxs-lookup"><span data-stu-id="63977-325">NULLABLE, PRECISION, SCALE</span></span>|  
|<span data-ttu-id="63977-326">LOB</span><span class="sxs-lookup"><span data-stu-id="63977-326">LOB</span></span>|<span data-ttu-id="63977-327">`SQLIMAGE`、`CharLOB`、`SQLTEXT`、および `SQLUDT`</span><span class="sxs-lookup"><span data-stu-id="63977-327">`SQLIMAGE`, `CharLOB`, `SQLTEXT`, and `SQLUDT`</span></span>|<span data-ttu-id="63977-328">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-328">None.</span></span>|<span data-ttu-id="63977-329">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="63977-329">NULLABLE</span></span>|  
|<span data-ttu-id="63977-330">CLOB</span><span class="sxs-lookup"><span data-stu-id="63977-330">Character LOB</span></span>|`SQLNTEXT`|<span data-ttu-id="63977-331">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-331">None.</span></span>|<span data-ttu-id="63977-332">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="63977-332">NULLABLE</span></span>|  
|<span data-ttu-id="63977-333">バイナリ文字列</span><span class="sxs-lookup"><span data-stu-id="63977-333">Binary string</span></span>|<span data-ttu-id="63977-334">`SQLBINARY` および `SQLVARYBIN`</span><span class="sxs-lookup"><span data-stu-id="63977-334">`SQLBINARY` and `SQLVARYBIN`</span></span>|<span data-ttu-id="63977-335">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-335">None.</span></span>|<span data-ttu-id="63977-336">NULLABLE、LENGTH</span><span class="sxs-lookup"><span data-stu-id="63977-336">NULLABLE, LENGTH</span></span>|  
|<span data-ttu-id="63977-337">文字列</span><span class="sxs-lookup"><span data-stu-id="63977-337">Character string</span></span>|<span data-ttu-id="63977-338">`SQLCHAR`、`SQLVARYCHAR`、`SQLNCHAR`、および `SQLNVARCHAR`</span><span class="sxs-lookup"><span data-stu-id="63977-338">`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR`, and `SQLNVARCHAR`</span></span>|<span data-ttu-id="63977-339">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-339">None.</span></span>|<span data-ttu-id="63977-340">NULLABLE、LENGTH</span><span class="sxs-lookup"><span data-stu-id="63977-340">NULLABLE, LENGTH</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63977-341">SQLXML データを一括エクスポートまたは一括インポートするには、フォーマット ファイルで次のいずれかのデータ型を使用します。SQLCHAR または SQLVARYCHAR (データはクライアント コード ページまたは照合順序で暗黙的に指定されるコード ページで送られます)、SQLNCHAR または SQLNVARCHAR (データは Unicode として送られます)、SQLBINARY または SQLVARYBIN (データは変換なしで送られます)。</span><span class="sxs-lookup"><span data-stu-id="63977-341">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
 <span data-ttu-id="63977-342">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型の詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-342">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
###  <a name="how-bulk-import-uses-the-row-element"></a><a name="HowUsesROW"></a> <span data-ttu-id="63977-343">一括インポートで \<ROW> 要素を使用する方法</span><span class="sxs-lookup"><span data-stu-id="63977-343">How Bulk Import Uses the \<ROW> Element</span></span>  
 <span data-ttu-id="63977-344">\<ROW> 要素は、一部のコンテキストでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="63977-344">The \<ROW> element is ignored in some contexts.</span></span> <span data-ttu-id="63977-345">\<ROW> 要素が、一括インポート操作に影響を与えるかどうかは、一括インポート操作がどのように実行されるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="63977-345">Whether the \<ROW> element affects a bulk-import operation depends on how the operation is performed:</span></span>  
  
-   <span data-ttu-id="63977-346">**bcp** コマンド</span><span class="sxs-lookup"><span data-stu-id="63977-346">the **bcp** command</span></span>  
  
     <span data-ttu-id="63977-347">データがインポート先のテーブルに読み込まれるときに、**bcp** コマンドでは \<ROW> コンポーネントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="63977-347">When data is loaded into a target table, **bcp** ignores the \<ROW> component.</span></span> <span data-ttu-id="63977-348">代わりに、 **bcp** コマンドでは、インポート先テーブルの列の型に基づいてデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="63977-348">Instead, **bcp** loads the data based on the column types of the target table.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="63977-349">ステートメント (BULK INSERT および OPENROWSET の一括行セット プロバイダー)</span><span class="sxs-lookup"><span data-stu-id="63977-349">statements (BULK INSERT and OPENROWSET's Bulk rowset provider)</span></span>  
  
     <span data-ttu-id="63977-350">テーブルにデータを一括インポートする際、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、\<ROW> コンポーネントを使用して入力行セットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="63977-350">When bulk importing data into a table, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements use the \<ROW> component to generate the input rowset.</span></span> <span data-ttu-id="63977-351">また、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、\<ROW> で指定されている列の型とインポート先のテーブルの対応する列に基づいて、適切な型変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="63977-351">Also, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements perform appropriate type conversions based on the column types specified under \<ROW> and the corresponding column in the target table.</span></span> <span data-ttu-id="63977-352">フォーマット ファイルで指定されている列の型とインポート先のテーブルの列の型が一致しない場合、追加の型変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="63977-352">If a mismatch exists between column types as specified in the format file and in the target table, an extra type conversion occurs.</span></span> <span data-ttu-id="63977-353">この追加の型変換によって、 **bcp**コマンドと比べたときの BULK INSERT または OPENROWSET の一括行セット プロバイダーの動作に矛盾が生じる (精度が低下する) ことがあります。</span><span class="sxs-lookup"><span data-stu-id="63977-353">This extra type conversion may lead to some discrepancy (that is, a loss of precision) in behavior in BULK INSERT or OPENROWSET's Bulk rowset provider as compared to **bcp**.</span></span>  
  
     <span data-ttu-id="63977-354">\<ROW> 要素の情報に基づいて行が構築されるので、追加の情報は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="63977-354">The information in the \<ROW> element allows a row to be constructed without requiring any additional information.</span></span> <span data-ttu-id="63977-355">このため、SELECT ステートメント (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*) を使用して行セットを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="63977-355">For this reason, you can generate a rowset using a SELECT statement (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63977-356">OPENROWSET BULK 句では、フォーマット ファイルが必要です (フィールドのデータ型から列のデータ型に変換する処理には、XML フォーマット ファイルが必要であることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="63977-356">The OPENROWSET BULK clause requires a format file (note that converting from the data type of the field to the data type of a column is available only with an XML format file).</span></span>  
  
###  <a name="how-bulk-import-uses-the-column-element"></a><a name="HowUsesColumn"></a> <span data-ttu-id="63977-357">一括インポートで \<COLUMN> 要素を使用する方法</span><span class="sxs-lookup"><span data-stu-id="63977-357">How Bulk Import Uses the \<COLUMN> Element</span></span>  
 <span data-ttu-id="63977-358">データをテーブルに一括インポートする際、フォーマット ファイル内の \<COLUMN> 要素により、次のことが指定され、データ ファイルのフィールドがテーブルの列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="63977-358">For bulk importing data into a table, the \<COLUMN> elements in a format file map a data-file field to table columns by specifying:</span></span>  
  
-   <span data-ttu-id="63977-359">データ ファイルの行内における各フィールドの位置。</span><span class="sxs-lookup"><span data-stu-id="63977-359">The position of each field within a row in the data file.</span></span>  
  
-   <span data-ttu-id="63977-360">列の型 (この型はフィールドのデータ型を適切な列のデータ型に変換する際に使用します)。</span><span class="sxs-lookup"><span data-stu-id="63977-360">The column type, which is used to convert the field data type to the desired column data type.</span></span>  
  
 <span data-ttu-id="63977-361">フィールドに列がマップされていない場合、フィールドは生成された行にコピーされません。</span><span class="sxs-lookup"><span data-stu-id="63977-361">If no column is mapped to a field, the field is not copied into the generated row(s).</span></span> <span data-ttu-id="63977-362">この動作により、データ ファイルでは、(異なるテーブルの) 異なる列を持つ行を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="63977-362">This behavior allows a data file to generate rows with different columns (in different tables).</span></span>  
  
 <span data-ttu-id="63977-363">同様に、データをテーブルから一括エクスポートする際、フォーマット ファイルの各 \<COLUMN> 要素により、エクスポート元のテーブル行の列が出力先データ ファイルの対応するフィールドにマップされます。</span><span class="sxs-lookup"><span data-stu-id="63977-363">Similarly, for bulk exporting data from a table, each \<COLUMN> in the format file maps the column from the input table row to its corresponding field in the output data file.</span></span>  
  
###  <a name="putting-the-xsitype-value-into-a-data-set"></a><a name="PutXsiTypeValueIntoDataSet"></a> <span data-ttu-id="63977-364">xsi:type 値のデータセットへの格納</span><span class="sxs-lookup"><span data-stu-id="63977-364">Putting the xsi:type Value into a Data Set</span></span>  
 <span data-ttu-id="63977-365">XML ドキュメントが XML Schema Definition (XSD) 言語で検証されると、xsi:type 値はデータセットに格納されません。</span><span class="sxs-lookup"><span data-stu-id="63977-365">When an XML document is validated through the XML Schema Definition (XSD) language, the xsi:type value is not put into the data set.</span></span> <span data-ttu-id="63977-366">ただし、次のコードに示すように、XML フォーマット ファイルを XML ドキュメント (たとえば、 `myDoc`) に読み込んで、xsi:type の情報をデータセットに格納することができます。</span><span class="sxs-lookup"><span data-stu-id="63977-366">However, you can put the xsi:type information into the data set by loading the XML format file into an XML document (for example, `myDoc`), as illustrated in the following code snippet:</span></span>  
  
```  
...;  
myDoc.LoadXml(xmlFormat);  
XmlNodeList ColumnList = myDoc.GetElementsByTagName("COLUMN");  
for(int i=0;i<ColumnList.Count;i++)  
{  
   Console.Write("COLUMN: xsi:type=" +ColumnList[i].Attributes["type",  
      "http://www.w3.org/2001/XMLSchema-instance"].Value+"\n");  
}  
```  
  
##  <a name="sample-xml-format-files"></a><a name="SampleXmlFFs"></a> <span data-ttu-id="63977-367">XML フォーマット ファイルのサンプル</span><span class="sxs-lookup"><span data-stu-id="63977-367">Sample XML Format Files</span></span>  
 <span data-ttu-id="63977-368">ここでは、 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] の例を基に、さまざまな状況で XML フォーマット ファイルを使用するときの情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-368">This section contains information on using XML format files in a variety of cases, including an [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63977-369">下記の例で示すデータ ファイルでは、 `<tab>` がデータ ファイル内のタブ文字、 `<return>` が復帰を表します。</span><span class="sxs-lookup"><span data-stu-id="63977-369">In the data files shown in the following examples, `<tab>` indicates a tab character in a data file, and `<return>` indicates a carriage return.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="63977-370">フォーマット ファイルの作成方法については、「 [フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-370">For information about how to create format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="a-ordering-character-data-fields-the-same-as-table-columns"></a><a name="OrderCharFieldsSameAsCols"></a> <span data-ttu-id="63977-371">A.</span><span class="sxs-lookup"><span data-stu-id="63977-371">A.</span></span> <span data-ttu-id="63977-372">文字データ フィールドの順序とテーブル列の順序が同じ場合</span><span class="sxs-lookup"><span data-stu-id="63977-372">Ordering character-data fields the same as table columns</span></span>  
 <span data-ttu-id="63977-373">次の例は、文字データのフィールドを 3 つ含んだデータ ファイルを記述する XML フォーマット ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="63977-373">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="63977-374">フォーマット ファイルによって、このデータ ファイルを 3 列のテーブルにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="63977-374">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="63977-375">データ フィールドは、テーブルの列と一対一に対応します。</span><span class="sxs-lookup"><span data-stu-id="63977-375">The data fields correspond one-to-one with the columns of the table.</span></span>  
  
 <span data-ttu-id="63977-376">**テーブル (行):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="63977-376">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="63977-377">**データ ファイル (レコード):** Age\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="63977-377">**Data file (record):** Age\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="63977-378">次の XML フォーマット ファイルはデータ ファイルのデータをテーブルに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="63977-378">The following XML format file reads from the data file to the table.</span></span>  
  
 <span data-ttu-id="63977-379">`<RECORD>` 要素では、3 つのフィールドすべてのデータ値が文字データとして表現されています。</span><span class="sxs-lookup"><span data-stu-id="63977-379">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span> <span data-ttu-id="63977-380">各フィールドの `TERMINATOR` 属性は、データ値の後のターミネータを示します。</span><span class="sxs-lookup"><span data-stu-id="63977-380">For each field, the `TERMINATOR` attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="63977-381">データ フィールドは、テーブルの列と一対一に対応します。</span><span class="sxs-lookup"><span data-stu-id="63977-381">The data fields correspond one-to-one with the columns of the table.</span></span> <span data-ttu-id="63977-382">`<ROW>` 要素で、列 `Age` を 1 番目のフィールドに、列 `FirstName` を 2 番目のフィールドに、列 `LastName` を 3 番目のフィールドにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="63977-382">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the second field, and the column `LastName` to the third field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>   
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="2" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="3" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="63977-383">[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] を使用した同様の例については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-383">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="b-ordering-data-fields-and-table-columns-differently"></a><a name="OrderFieldsAndColsDifferently"></a> <span data-ttu-id="63977-384">B.</span><span class="sxs-lookup"><span data-stu-id="63977-384">B.</span></span> <span data-ttu-id="63977-385">データ フィールドの順序とテーブル列の順序が異なる場合</span><span class="sxs-lookup"><span data-stu-id="63977-385">Ordering data fields and table columns differently</span></span>  
 <span data-ttu-id="63977-386">次の例は、文字データのフィールドを 3 つ含んだデータ ファイルを記述する XML フォーマット ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="63977-386">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="63977-387">フォーマット ファイルによって、データ ファイルを 3 列のテーブルにマッピングします。ここでは、データ ファイルのフィールドの順序とマッピング先のテーブルの列の順序は異なるものとします。</span><span class="sxs-lookup"><span data-stu-id="63977-387">The format file maps the data file to a table that contains three columns that are ordered differently from the fields of the data file.</span></span>  
  
 <span data-ttu-id="63977-388">**テーブル (行):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="63977-388">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="63977-389">**データ ファイル** (レコード): Age\<tab>Lastname\<tab>Firstname\<return></span><span class="sxs-lookup"><span data-stu-id="63977-389">**Data file** (record): Age\<tab>Lastname\<tab>Firstname\<return></span></span>  
  
 <span data-ttu-id="63977-390">`<RECORD>` 要素では、3 つのフィールドすべてのデータ値が文字データとして表現されています。</span><span class="sxs-lookup"><span data-stu-id="63977-390">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span>  
  
 <span data-ttu-id="63977-391">`<ROW>` 要素で、列 `Age` を 1 番目のフィールドに、列 `FirstName` を 3 番目のフィールドに、列 `LastName` を 2 番目のフィールドにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="63977-391">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the second field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="2" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="63977-392">[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] を使用した同様の例については、「[フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-392">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md).</span></span>  
  
### <a name="c-omitting-a-data-field"></a><span data-ttu-id="63977-393">C.</span><span class="sxs-lookup"><span data-stu-id="63977-393">C.</span></span> <span data-ttu-id="63977-394">データ フィールドをスキップする場合</span><span class="sxs-lookup"><span data-stu-id="63977-394">Omitting a data field</span></span>  
 <span data-ttu-id="63977-395">次の例は、文字データのフィールドを 4 つ含んだデータ ファイルを記述する XML フォーマット ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="63977-395">The following example shows an XML format file that describes a data file containing four fields of character data.</span></span> <span data-ttu-id="63977-396">フォーマット ファイルによって、このデータ ファイルを 3 列のテーブルにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="63977-396">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="63977-397">2 番目のデータ フィールドは対応するテーブル列がありません。</span><span class="sxs-lookup"><span data-stu-id="63977-397">The second data field does not correspond to any table column.</span></span>  
  
 <span data-ttu-id="63977-398">**テーブル (行):** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span><span class="sxs-lookup"><span data-stu-id="63977-398">**Table (row):** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span></span>  
  
 <span data-ttu-id="63977-399">**データ ファイル (レコード):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="63977-399">**Data file (record):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="63977-400">`<RECORD>` 要素では、4 つのフィールドすべてのデータ値が文字データとして表現されています。</span><span class="sxs-lookup"><span data-stu-id="63977-400">In the `<RECORD>` element, the format file represents the data values in all four fields as character data.</span></span> <span data-ttu-id="63977-401">各フィールドの TERMINATOR 属性は、データ値の後のターミネータを示します。</span><span class="sxs-lookup"><span data-stu-id="63977-401">For each field, the TERMINATOR attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="63977-402">`<ROW>` 要素で、列 `Age` を 1 番目のフィールドに、列 `FirstName` を 3 番目のフィールドに、列 `LastName` を 4 番目のフィールドにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="63977-402">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the fourth field.</span></span>  
  
```  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="10"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="4" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="63977-403">[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] を使用した同様の例については、「[フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-403">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md).</span></span>  
  
###  <a name="d-mapping-field-xsitype-to-column-xsitype"></a><a name="MapXSItype"></a> <span data-ttu-id="63977-404">D.</span><span class="sxs-lookup"><span data-stu-id="63977-404">D.</span></span> <span data-ttu-id="63977-405">\<FIELD> xsi: type を \<COLUMN> xsi: type にマッピングする場合</span><span class="sxs-lookup"><span data-stu-id="63977-405">Mapping \<FIELD> xsi:type to \<COLUMN> xsi:type</span></span>  
 <span data-ttu-id="63977-406">次の例では、さまざまな型のフィールド、および列への各フィールドのマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="63977-406">The following example shows different types of fields and their mappings to columns.</span></span>  
  
```  
<?xml version = "1.0"?>  
<BCPFORMAT  
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <RECORD>  
      <FIELD xsi:type="CharTerm" ID="C1" TERMINATOR="\t"   
            MAX_LENGTH="4"/>  
      <FIELD xsi:type="CharFixed" ID="C2" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="CharPrefix" ID="C3" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharTerm" ID="C4" TERMINATOR="\t"   
         MAX_LENGTH="4"/>  
      <FIELD xsi:type="NCharFixed" ID="C5" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharPrefix" ID="C6" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NativeFixed" ID="C7" LENGTH="4"/>  
   </RECORD>  
   <ROW>  
      <COLUMN SOURCE="C1" NAME="Age" xsi:type="SQLTINYINT"/>  
      <COLUMN SOURCE="C2" NAME="FirstName" xsi:type="SQLVARYCHAR"   
      LENGTH="16" NULLABLE="NO"/>  
      <COLUMN SOURCE="C3" NAME="LastName" />  
      <COLUMN SOURCE="C4" NAME="Salary" xsi:type="SQLMONEY"/>  
      <COLUMN SOURCE="C5" NAME="Picture" xsi:type="SQLIMAGE"/>  
      <COLUMN SOURCE="C6" NAME="Bio" xsi:type="SQLTEXT"/>  
      <COLUMN SOURCE="C7" NAME="Interest"xsi:type="SQLDECIMAL"   
      PRECISION="5" SCALE="3"/>  
   </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="e-mapping-xml-data-to-a-table"></a><a name="MapXMLDataToTbl"></a> <span data-ttu-id="63977-407">E.</span><span class="sxs-lookup"><span data-stu-id="63977-407">E.</span></span> <span data-ttu-id="63977-408">XML データをテーブルにマッピングする場合</span><span class="sxs-lookup"><span data-stu-id="63977-408">Mapping XML data to a table</span></span>  
 <span data-ttu-id="63977-409">次の例では、2 列の空テーブル (`t_xml`) を作成し、1 番目の列を `int` データ型に、2 番目の列を `xml` データ型にマッピングしています。</span><span class="sxs-lookup"><span data-stu-id="63977-409">The following example creates an empty two-column table (`t_xml`), in which the first column maps to the `int` data type and the second column maps to the `xml` data type.</span></span>  
  
```  
CREATE TABLE t_xml (c1 int, c2 xml)  
```  
  
 <span data-ttu-id="63977-410">次の XML フォーマット ファイルを使用すると、テーブル `t_xml`にデータ ファイルが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="63977-410">The following XML format file would load a data file into table `t_xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" PREFIX_LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLINT"/>  
  <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLNCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="f-importing-fixed-length-or-fixed-width-fields"></a><a name="ImportFixedFields"></a> <span data-ttu-id="63977-411">F.</span><span class="sxs-lookup"><span data-stu-id="63977-411">F.</span></span> <span data-ttu-id="63977-412">固定長フィールドまたは固定幅フィールドをインポートする場合</span><span class="sxs-lookup"><span data-stu-id="63977-412">Importing fixed-length or fixed-width fields</span></span>  
 <span data-ttu-id="63977-413">次の例では、長さと幅がそれぞれ `10` 文字または `6` 文字に固定されたフィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="63977-413">The following example describes fixed fields of `10` or `6` characters each.</span></span> <span data-ttu-id="63977-414">これらのフィールドの長さと幅は `LENGTH="10"` および `LENGTH="6"`としてそれぞれ表現されています。</span><span class="sxs-lookup"><span data-stu-id="63977-414">The format file represents these field lengths/widths as `LENGTH="10"` and `LENGTH="6"`, respectively.</span></span> <span data-ttu-id="63977-415">データ ファイルのすべての行の末尾には、復帰と改行の組み合わせ ({CR}{LF}) が記述されます。フォーマット ファイルでは `TERMINATOR="\r\n"`として表現されています。</span><span class="sxs-lookup"><span data-stu-id="63977-415">Every row of the data files ends with a carriage return-line feed combination, {CR}{LF}, which the format file represents as `TERMINATOR="\r\n"`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT  
       xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"  
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharFixed" LENGTH="10"/>  
    <FIELD ID="2" xsi:type="CharFixed" LENGTH="6"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="C1" xsi:type="SQLINT" />  
    <COLUMN SOURCE="2" NAME="C2" xsi:type="SQLINT" />  
  </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="additional-examples"></a><a name="AdditionalExamples"></a> <span data-ttu-id="63977-416">その他の例</span><span class="sxs-lookup"><span data-stu-id="63977-416">Additional Examples</span></span>  
 <span data-ttu-id="63977-417">XML 以外のフォーマット ファイルと XML フォーマット ファイルに関するその他の例については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="63977-417">For additional examples of both non-XML format files and XML format files, see the following topics:</span></span>  
  
-   [<span data-ttu-id="63977-418">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-418">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="63977-419">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-419">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="63977-420">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-420">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="63977-421">関連タスク</span><span class="sxs-lookup"><span data-stu-id="63977-421">Related Tasks</span></span>  
  
-   [<span data-ttu-id="63977-422">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-422">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="63977-423">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-423">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="63977-424">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-424">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="63977-425">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-425">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="63977-426">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-426">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="63977-427">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="63977-427">Related Content</span></span>  
 <span data-ttu-id="63977-428">[なし] :</span><span class="sxs-lookup"><span data-stu-id="63977-428">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63977-429">参照</span><span class="sxs-lookup"><span data-stu-id="63977-429">See Also</span></span>  
 <span data-ttu-id="63977-430">[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63977-430">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="63977-431">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63977-431">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="63977-432">[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63977-432">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="63977-433">データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="63977-433">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
