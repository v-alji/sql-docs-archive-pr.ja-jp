---
title: XML データのインスタンスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: rothja
ms.author: jroth
ms.openlocfilehash: c857b9ebbe559de34fdac925642f9270d9cbf936
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743114"
---
# <a name="create-instances-of-xml-data"></a><span data-ttu-id="d9c2f-102">XML データのインスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="d9c2f-102">Create Instances of XML Data</span></span>
  <span data-ttu-id="d9c2f-103">このトピックでは、XML インスタンスを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-103">This topic describes how to generate XML instances.</span></span>  
  
 <span data-ttu-id="d9c2f-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、次の方法で XML インスタンスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can generate XML instances in the following ways:</span></span>  
  
-   <span data-ttu-id="d9c2f-105">文字列インスタンスの型をキャストする。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-105">Type casting string instances.</span></span>  
  
-   <span data-ttu-id="d9c2f-106">FOR XML 句を指定した SELECT ステートメントを使用する。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-106">Using the SELECT statement with the FOR XML clause.</span></span>  
  
-   <span data-ttu-id="d9c2f-107">定数の代入を使用する。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-107">Using constant assignments.</span></span>  
  
-   <span data-ttu-id="d9c2f-108">一括読み込みを使用する。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-108">Using bulk load.</span></span>  
  
## <a name="type-casting-string-and-binary-instances"></a><span data-ttu-id="d9c2f-109">文字列インスタンスとバイナリ インスタンスの型キャスト</span><span class="sxs-lookup"><span data-stu-id="d9c2f-109">Type Casting String and Binary Instances</span></span>  
 <span data-ttu-id="d9c2f-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][**N**] [**var**]**char**、 **[n] text**、 **varbinary**、 **image**などの文字列データ型は、データ型 `xml` へのキャスト (CAST) または変換 (変換) によってデータ型に解析でき `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-110">You can parse any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] string data types, such as [**n**][**var**]**char**, **[n]text**, **varbinary**,and **image**, into the `xml` data type by casting (CAST) or converting (CONVERT) the string to the `xml` data type.</span></span> <span data-ttu-id="d9c2f-111">型指定されていない XML は、正しい形式かどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-111">Untyped XML is checked to confirm that it is well formed.</span></span> <span data-ttu-id="d9c2f-112">型に関連付けられているスキーマがある場合は `xml` 、検証も実行されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-112">If there is a schema associated with the `xml` type, validation is also performed.</span></span> <span data-ttu-id="d9c2f-113">詳細については、「 [型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-113">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
 <span data-ttu-id="d9c2f-114">XML ドキュメントは、UTF-8、UTF-16、windows-1252 など、さまざまなエンコードを使用してエンコードできます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-114">XML documents can be encoded with different encodings (for example, UTF-8, UTF-16, windows-1252).</span></span> <span data-ttu-id="d9c2f-115">ここでは、文字列およびバイナリの元のデータ型と XML ドキュメントのエンコード間の相互作用における規則、およびパーサーの動作に関する規則を概説します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-115">The following outlines the rules on how the string and binary source types interact with the XML document encoding and how the parser behaves.</span></span>  
  
 <span data-ttu-id="d9c2f-116">**nvarchar** 型は UTF-16 や UCS-2 などの 2 バイト Unicode エンコードを想定しているので、XML パーサーは文字列値を 2 バイト Unicode でエンコードされた XML ドキュメントまたは XML フラグメントとして処理します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-116">Since **nvarchar** assumes a two-byte unicode encoding such as UTF-16 or UCS-2, the XML parser will treat the string value as a two-byte Unicode encoded XML document or fragment.</span></span> <span data-ttu-id="d9c2f-117">つまり、XML ドキュメントには、元のデータ型との互換性だけでなく、2 バイト Unicode エンコードでのエンコードも必要であるということになります。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-117">This means that the XML document needs to be encoded in a two-byte Unicode encoding as well to be compatible with the source data type.</span></span> <span data-ttu-id="d9c2f-118">UTF-16 でエンコードされた XML ドキュメントでは、UTF-16 バイト順マーク (BOM) を指定できますが、指定する必要はありません。これは、変換元データ型のコンテキストにより、2 バイト Unicode でエンコードされたドキュメントに限定されることが明確であるためです。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-118">A UTF-16 encoded XML document can have a UTF-16 byte order mark (BOM), but it does not need to, since the context of the source type makes it clear that it can only be a two-byte Unicode encoded document.</span></span>  
  
 <span data-ttu-id="d9c2f-119">**varchar** 文字列の内容は、XML パーサーによって、1 バイトでエンコードされた XML ドキュメントまたは XML フラグメントとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-119">The content of a **varchar** string is treated as a one-byte encoded XML document/fragment by the XML parser.</span></span> <span data-ttu-id="d9c2f-120">**varchar** の変換元文字列にはコード ページが関連付けられているので、明示的なエンコード方法が XML 自体に指定されていない場合、XML パーサーはそのコード ページを使用してエンコードを行います。XML インスタンスに BOM またはエンコード宣言がある場合、このコード ページとの一貫性が必要になります。そうでない場合、XML パーサーからエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-120">Since the **varchar** source string has a code page associated, the parser will use that code page for the encoding if no explicit encoding is specified in the XML itself If an XML instance has a BOM or an encoding declaration, the BOM or declaration needs to be consistent with the code page, otherwise the parser will report an error.</span></span>  
  
 <span data-ttu-id="d9c2f-121">**varbinary** の内容は、XML パーサーに直接渡されるコードポイント ストリームとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-121">The content of **varbinary** is treated as a codepoint stream that is passed directly to the XML parser.</span></span> <span data-ttu-id="d9c2f-122">このため、XML ドキュメントまたは XML フラグメントに、BOM またはその他のエンコード情報をインラインで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-122">Thus, the XML document or fragment needs to provide the BOM or other encoding information inline.</span></span> <span data-ttu-id="d9c2f-123">XML パーサーは、ストリームからのみエンコード方法を判断します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-123">The parser will only look at the stream to determine the encoding.</span></span> <span data-ttu-id="d9c2f-124">つまり、UTF-16 でエンコードされた XML には UTF-16 BOM を指定する必要があり、BOM やエンコード宣言のない XML インスタンスは UTF-8 として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-124">This means that UTF-16 encoded XML needs to provide the UTF-16 BOM and an instance without BOM and without a declaration encoding will be interpreted as UTF-8.</span></span>  
  
 <span data-ttu-id="d9c2f-125">XML ドキュメントのエンコードが事前にわからないために、XML にキャストする前に XML データではなく文字列データまたはバイナリ データとしてデータが渡される場合は、そのデータを **varbinary**として処理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-125">If the encoding of the XML document is not known in advance and the data is passed as string or binary data instead of XML data before casting to XML, it is recommended to treat the data as **varbinary**.</span></span> <span data-ttu-id="d9c2f-126">たとえば、OpenRowset() を使用して XML ファイルからデータを読み取る場合、次のように、そのデータを **varbinary(max)** 値として読み取るように指定してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-126">For example, when reading data from an XML file using OpenRowset(), one should specify the data to be read as a **varbinary(max)** value:</span></span>  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d9c2f-127">内部では、UTF-16 エンコードを使用した効率のよいバイナリ表記で XML が表現されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-127">internally represents XML in an efficient binary representation that uses UTF-16 encoding.</span></span> <span data-ttu-id="d9c2f-128">ユーザーが指定したエンコードは保持されませんが、解析処理時に考慮されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-128">User-provided encoding is not preserved, but is considered during the parse process.</span></span>  
  
### <a name="type-casting-clr-user-defined-types"></a><span data-ttu-id="d9c2f-129">CLR ユーザー定義型の型キャスト</span><span class="sxs-lookup"><span data-stu-id="d9c2f-129">Type Casting CLR user-defined types</span></span>  
 <span data-ttu-id="d9c2f-130">CLR ユーザー定義型で XML シリアル化を指定している場合は、その型のインスタンスを XML データ型に明示的にキャストすることができます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-130">If a CLR user-defined type has an XML Serialization, instances of that type can be explicitly cast to an XML datatype.</span></span> <span data-ttu-id="d9c2f-131">CLR ユーザー定義型の XML シリアル化の詳細については、「 [XML Serialization from CLR Database Objects](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-131">For more details about the XML serialization of a CLR user-defined typed, see [XML Serialization from CLR Database Objects](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).</span></span>  
  
### <a name="white-space-handling-in-typed-xml"></a><span data-ttu-id="d9c2f-132">型指定された XML の空白文字の処理</span><span class="sxs-lookup"><span data-stu-id="d9c2f-132">White Space Handling in Typed XML</span></span>  
 <span data-ttu-id="d9c2f-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で、要素の内容に含まれる空白文字は、開始タグや終了タグなどのマークアップで区切られた空白文字だけのシーケンス内に出現し、エンティティに変換されていない場合、重要でないと見なされます</span><span class="sxs-lookup"><span data-stu-id="d9c2f-133">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], white space inside element content is considered insignificant if it occurs inside a sequence of white-space-only character data delimited by markup, such as begin or end tags, and is not entitized.</span></span> <span data-ttu-id="d9c2f-134">(CDATA セクションは無視されます)。この空白文字の処理は、W3C (World Wide Web Consortium) から公開されている XML 1.0 仕様の空白文字に関する記述とは異なります。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-134">(CDATA sections are ignored.) This handling of white space handling is different from how white space is described in the XML 1.0 specification published by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="d9c2f-135">これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の XML パーサーが XML 1.0 の定義に従って、限定された数の DTD サブセットしか認識しないためです。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-135">This is because the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recognizes only a limited number of DTD subsets, as defined in XML 1.0.</span></span> <span data-ttu-id="d9c2f-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされる限定された DTD サブセット数の詳細については、「[CAST および CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-136">For more information about the limited DTD subsets supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
 <span data-ttu-id="d9c2f-137">XML パーサーは、既定では、文字列データを XML に変換するときに、次のいずれかの条件に当てはまる場合は、重要ではない空白文字を破棄します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-137">By default, the XML parser discards insignificant white space when it converts string data to XML if either of the following is true:</span></span>  
  
-   <span data-ttu-id="d9c2f-138">`The xml:space` 要素またはその先祖の要素に属性が定義されていない。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-138">`The xml:space` attribute is not defined on an element or its ancestor elements.</span></span>  
  
-   <span data-ttu-id="d9c2f-139">要素またはその先祖の要素の 1 つで有効になっている `xml:space` 属性に既定値が設定されている。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-139">The `xml:space` attribute in effect on an element, or one of its ancestor elements, has the value of default.</span></span>  
  
 <span data-ttu-id="d9c2f-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-140">For example:</span></span>  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 <span data-ttu-id="d9c2f-141">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-141">This is the result:</span></span>  
  
```  
<root><child/></root>  
```  
  
 <span data-ttu-id="d9c2f-142">ただし、この動作は変更できます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-142">However, you can change this behavior.</span></span> <span data-ttu-id="d9c2f-143">xml DT インスタンスの空白文字を保持するには、CONVERT 演算子を使用し、省略可能な *style* パラメーターを値 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-143">To preserve white space for an xml DT instance, use the CONVERT operator and its optional *style* parameter set to a value of 1.</span></span> <span data-ttu-id="d9c2f-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-144">For example:</span></span>  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 <span data-ttu-id="d9c2f-145">*style* パラメーターが使用されていないか、この値が 0 に設定されていると、xml DT インスタンスの変換では重要でない空白文字は保持されません。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-145">If the *style* parameter is either not used or its value is set to 0, insignificant white space is not preserved for the conversion of the xml DT instance.</span></span> <span data-ttu-id="d9c2f-146">文字列データを xml DT インスタンスに変換するときの、CONVERT 演算子と *style* パラメーターの使用方法の詳細については、「[CAST および CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-146">For more information about how to use the CONVERT operator and its *style* parameter when converting string data to xml DT instances, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a><span data-ttu-id="d9c2f-147">例: 型指定された xml に文字列値をキャストし、列に割り当てる</span><span class="sxs-lookup"><span data-stu-id="d9c2f-147">Example: Cast a string value to typed xml and assign it to a column</span></span>  
 <span data-ttu-id="d9c2f-148">次の例では、XML フラグメントを含む文字列変数を `xml` データ型にキャストし、型の列に格納し `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-148">The following example casts a string variable that contains an XML fragment to the `xml` data type and then stores it in the `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 <span data-ttu-id="d9c2f-149">次の挿入操作では、文字列から型に暗黙的に変換され `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-149">The following insert operation implicitly converts from a string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 <span data-ttu-id="d9c2f-150">() 文字列を型に明示的にキャストすることができ `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-150">You can explicitly cast() the string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 <span data-ttu-id="d9c2f-151">または、次に示すように convert() を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-151">Or you can use convert(), as shown in the following:</span></span>  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a><span data-ttu-id="d9c2f-152">例: 型指定された xml に文字列を変換し、変数に割り当てる</span><span class="sxs-lookup"><span data-stu-id="d9c2f-152">Example: Convert a string to typed xml and assign it to a variable</span></span>  
 <span data-ttu-id="d9c2f-153">次の例では、文字列は型に変換され、 `xml` データ型の変数に割り当てられ `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-153">In the following example, a string is converted to `xml` type and assigned to a variable of the `xml` data type:</span></span>  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a><span data-ttu-id="d9c2f-154">FOR XML 句を指定した SELECT ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="d9c2f-154">Using the SELECT Statement with a FOR XML Clause</span></span>  
 <span data-ttu-id="d9c2f-155">SELECT ステートメントに FOR XML 句を使用すると、結果を XML として返すことができます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-155">You can use the FOR XML clause in a SELECT statement to return results as XML.</span></span> <span data-ttu-id="d9c2f-156">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-156">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 <span data-ttu-id="d9c2f-157">SELECT ステートメントは、テキスト形式の XML フラグメントを返します。このフラグメントは、データ型の変数への割り当て時に解析され `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-157">The SELECT statement returns a textual XML fragment that is then parsed during the assignment to the `xml` data type variable.</span></span>  
  
 <span data-ttu-id="d9c2f-158">For xml 句の[type ディレクティブ](type-directive-in-for-xml-queries.md)を使用して、for xml クエリの結果を型として直接返すこともでき `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-158">You can also use the [TYPE directive](type-directive-in-for-xml-queries.md) in the FOR XML clause that directly returns a FOR XML query result as `xml` type:</span></span>  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 <span data-ttu-id="d9c2f-159">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-159">This is the result:</span></span>  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 <span data-ttu-id="d9c2f-160">次の例で `xml` は、FOR XML クエリの型指定された結果が型の列に挿入され `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-160">In the following example, the typed `xml` result of a FOR XML query is inserted into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 <span data-ttu-id="d9c2f-161">FOR XML の詳細については、「[FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-161">For more information about FOR XML, see [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d9c2f-162">は、TYPE ディレクティブを使用する FOR XML クエリや、`xml` データ型を使用して SQL 列、変数、および出力パラメーターから XML を返す FOR XML クエリなど、異なるサーバー構成の結果として、`xml` データ型インスタンスをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-162">returns `xml` data type instances to the client as a result of different server constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML from SQL columns, variables, and output parameters.</span></span> <span data-ttu-id="d9c2f-163">クライアント アプリケーションのコードでは、ADO.NET プロバイダーがこの `xml` データ型情報をサーバーからバイナリ エンコード形式で送信するよう要求します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-163">In client application code, the ADO.NET provider requests that this `xml` data type information be sent in a binary encoding from the server.</span></span> <span data-ttu-id="d9c2f-164">ただし、TYPE ディレクティブを指定しないで FOR XML を使用した場合、XML データは文字列型のデータとして返されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-164">However, if you are using FOR XML without the TYPE directive, the XML data returns as a string type.</span></span> <span data-ttu-id="d9c2f-165">どんな場合でも、クライアント プロバイダーは常にいずれかの形式の XML を処理できます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-165">In any case, the client provider will always be able to handle either form of XML.</span></span>  
  
## <a name="using-constant-assignments"></a><span data-ttu-id="d9c2f-166">定数の代入の使用</span><span class="sxs-lookup"><span data-stu-id="d9c2f-166">Using Constant Assignments</span></span>  
 <span data-ttu-id="d9c2f-167">データ型のインスタンスが必要な場合は、文字列定数を使用でき `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-167">A string constant can be used where an instance of the `xml` data type is expected.</span></span> <span data-ttu-id="d9c2f-168">これは、文字列から XML への暗黙の CAST と同じです。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-168">This is the same as an implied CAST of string to XML.</span></span> <span data-ttu-id="d9c2f-169">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-169">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 <span data-ttu-id="d9c2f-170">前の例では、文字列をデータ型に暗黙的に変換 `xml` し、型変数に代入して `xml` います。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-170">The previous example implicitly converts the string to the `xml` data type and assigns it to an `xml` type variable.</span></span>  
  
 <span data-ttu-id="d9c2f-171">次の例では、型の列に定数文字列を挿入し `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-171">The following example inserts a constant string into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  <span data-ttu-id="d9c2f-172">型指定された XML では、指定したスキーマに対して XML が検証されます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-172">For typed XML, the XML is validated against the specified schema.</span></span> <span data-ttu-id="d9c2f-173">詳細については、「 [型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-173">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
## <a name="using-bulk-load"></a><span data-ttu-id="d9c2f-174">一括読み込みの使用</span><span class="sxs-lookup"><span data-stu-id="d9c2f-174">Using Bulk Load</span></span>  
 <span data-ttu-id="d9c2f-175">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) 機能が強化され、データベースに XML ドキュメントを一括読み込みできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-175">The enhanced [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) functionality allows you to bulk load XML documents in the database.</span></span> <span data-ttu-id="d9c2f-176">XML インスタンスは、ファイルから `xml` データベース内の型の列に一括読み込みできます。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-176">You can bulk load XML instances from files into the `xml` type columns in the database.</span></span> <span data-ttu-id="d9c2f-177">作業用サンプルについては、「[XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-177">For working samples, see [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md).</span></span> <span data-ttu-id="d9c2f-178">XML ドキュメントの読み込みの詳細については、「 [XML データの読み込み](load-xml-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-178">For more information about loading XML documents, see [Load XML Data](load-xml-data.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9c2f-179">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d9c2f-179">In This Section</span></span>  
  
|<span data-ttu-id="d9c2f-180">トピック</span><span class="sxs-lookup"><span data-stu-id="d9c2f-180">Topic</span></span>|<span data-ttu-id="d9c2f-181">説明</span><span class="sxs-lookup"><span data-stu-id="d9c2f-181">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d9c2f-182">XML データの取得および XML データに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="d9c2f-182">Retrieve and Query XML Data</span></span>](retrieve-and-query-xml-data.md)|<span data-ttu-id="d9c2f-183">XML インスタンスをデータベースに格納するときに保持されない部分について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9c2f-183">Describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9c2f-184">参照</span><span class="sxs-lookup"><span data-stu-id="d9c2f-184">See Also</span></span>  
 <span data-ttu-id="d9c2f-185">[型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="d9c2f-185">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="d9c2f-186">[xml データ型メソッド](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="d9c2f-186">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="d9c2f-187">[XML データ変更言語 &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="d9c2f-187">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="d9c2f-188">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d9c2f-188">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
