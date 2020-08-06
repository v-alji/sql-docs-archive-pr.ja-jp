---
title: XML データの読み込む | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], loading
- loading XML data
ms.assetid: d1741e8d-f44e-49ec-9f14-10208b5468a7
author: rothja
ms.author: jroth
ms.openlocfilehash: c48d1d6feccb7df9fec9801ee56abcab99884754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717546"
---
# <a name="load-xml-data"></a><span data-ttu-id="da050-102">XML データの読み込み</span><span class="sxs-lookup"><span data-stu-id="da050-102">Load XML Data</span></span>
  <span data-ttu-id="da050-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へは、いくつかの方法で XML データを転送できます。</span><span class="sxs-lookup"><span data-stu-id="da050-103">You can transfer XML data into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in several ways.</span></span> <span data-ttu-id="da050-104">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="da050-104">For example:</span></span>  
  
-   <span data-ttu-id="da050-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの [n]text 型または image 型の列にデータが含まれている場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を使用してテーブルをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="da050-105">If you have your data in an [n]text or image column in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you can import the table by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="da050-106">ALTER TABLE ステートメントを使用して列の型を XML に変更します。</span><span class="sxs-lookup"><span data-stu-id="da050-106">Change the column type to XML by using the ALTER TABLE statement.</span></span>  
  
-   <span data-ttu-id="da050-107">bcp out を使用して別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからデータの一括コピーを実行し、bcp in を使用して新しいバージョンのデータベースにそのデータの一括挿入を実行できます。</span><span class="sxs-lookup"><span data-stu-id="da050-107">You can bulk copy your data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using bcp out, and then bulk insert the data into the later version database by using bcp in.</span></span>  
  
-   <span data-ttu-id="da050-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのリレーショナル列にデータが含まれている場合、新しいテーブルを作成し、[n]text 型の列や行 ID を保存する主キー列 (任意) を含めます。</span><span class="sxs-lookup"><span data-stu-id="da050-108">If you have data in relational columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, create a new table with an [n]text column and, optionally, a primary key column for a row identifier.</span></span> <span data-ttu-id="da050-109">クライアント側プログラミングを使用して、FOR XML によりサーバーで生成された XML を取得し、`[n]text` 型の列に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="da050-109">Use client-side programming to retrieve the XML that is generated at the server with FOR XML and write it into the `[n]text` column.</span></span> <span data-ttu-id="da050-110">その後で、既に説明した技法により、新しいバージョンのデータベースにデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="da050-110">Then, use the previously mentioned techniques to transfer data to a later version database.</span></span> <span data-ttu-id="da050-111">XML を新しいバージョンのデータベースの XML 列に直接書き込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="da050-111">You can choose to write the XML into an XML column in the later version database directly.</span></span>  
  
## <a name="bulk-loading-xml-data"></a><span data-ttu-id="da050-112">XML データの一括読み込み</span><span class="sxs-lookup"><span data-stu-id="da050-112">Bulk loading XML data</span></span>  
 <span data-ttu-id="da050-113">bcp など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の一括読み込み機能によって XML データをサーバーに一括で読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="da050-113">You can bulk load XML data into the server by using the bulk loading capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as bcp.</span></span> <span data-ttu-id="da050-114">OPENROWSET を使用すると、ファイルから XML 列にデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="da050-114">OPENROWSET allows you to load data into an XML column from files.</span></span> <span data-ttu-id="da050-115">この点について、次の例で説明します。</span><span class="sxs-lookup"><span data-stu-id="da050-115">The following example illustrates this point.</span></span>  
  
##### <a name="example-loading-xml-from-files"></a><span data-ttu-id="da050-116">例: ファイルからの XML の読み込み</span><span class="sxs-lookup"><span data-stu-id="da050-116">Example: Loading XML from Files</span></span>  
 <span data-ttu-id="da050-117">この例では、テーブル T に行を挿入する方法を示します。C:\MyFile\xmlfile.xml から CLOB として XML 列の値を読み込み、整数型の列に値 10 を保存します。</span><span class="sxs-lookup"><span data-stu-id="da050-117">This example shows how to insert a row in table T. The value of the XML column is loaded from file C:\MyFile\xmlfile.xml as CLOB, and the integer column is supplied the value 10.</span></span>  
  
```  
INSERT INTO T  
SELECT 10, xCol  
FROM    (SELECT *      
    FROM OPENROWSET (BULK 'C:\MyFile\xmlfile.xml', SINGLE_CLOB)   
 AS xCol) AS R(xCol)  
```  
  
## <a name="text-encoding"></a><span data-ttu-id="da050-118">テキストのエンコード</span><span class="sxs-lookup"><span data-stu-id="da050-118">Text Encoding</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="da050-119">では XML データを Unicode (UTF-16) で保存します。</span><span class="sxs-lookup"><span data-stu-id="da050-119">stores XML data in Unicode (UTF-16).</span></span> <span data-ttu-id="da050-120">サーバーから取得する XML データは UTF-16 エンコードで出力されます。</span><span class="sxs-lookup"><span data-stu-id="da050-120">XML data retrieved from the server comes out in UTF-16 encoding.</span></span> <span data-ttu-id="da050-121">それ以外のエンコードが必要な場合、取得したデータに必要な変換を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="da050-121">If you want a different encoding, you have to perform the required conversion on the retrieved data.</span></span> <span data-ttu-id="da050-122">変換した XML データのエンコードが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="da050-122">Sometimes, the XML data may be in a different encoding.</span></span> <span data-ttu-id="da050-123">その場合は、注意してデータを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="da050-123">If it is, you have to use care during data loading.</span></span> <span data-ttu-id="da050-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="da050-124">For example:</span></span>  
  
-   <span data-ttu-id="da050-125">Unicode (UCS-2、UTF-16) のテキスト XML は、問題なく XML 列、変数、またはパラメーターに代入できます。</span><span class="sxs-lookup"><span data-stu-id="da050-125">If your text XML is in Unicode (UCS-2, UTF-16), you can assign it to an XML column, variable, or parameter  without any problems.</span></span>  
  
-   <span data-ttu-id="da050-126">基になるコード ページの都合で Unicode ではなく、かつ暗黙のエンコードの場合、データベースの文字列のコード ページは読み込むコード ポイントと同一か、互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="da050-126">If the encoding is not Unicode and is implicit, because of the source code page, the string code page in the database should be the same as or compatible with the code points that you want to load.</span></span> <span data-ttu-id="da050-127">必要であれば COLLATE を使用します。</span><span class="sxs-lookup"><span data-stu-id="da050-127">If required, use COLLATE.</span></span> <span data-ttu-id="da050-128">サーバーにそのようなコード ページが存在しない場合、エンコードを修正する明示的な XML 宣言を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da050-128">If no such server code page exists, you have to add an explicit XML declaration with the correct encoding.</span></span>  
  
-   <span data-ttu-id="da050-129">明示的なエンコードを使用するには、コード ページに連動しない `varbinary()` 型を使用するか、適切なコード ページの文字列型を使用します。</span><span class="sxs-lookup"><span data-stu-id="da050-129">To use an explicit encoding, use either the `varbinary()` type, which has no interaction with code pages, or use a string type of the appropriate code page.</span></span> <span data-ttu-id="da050-130">次に、データを XML の列、変数、またはパラメーターに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="da050-130">Then, assign the data to an XML column, variable, or parameter.</span></span>  
  
### <a name="example-explicitly-specifying-an-encoding"></a><span data-ttu-id="da050-131">例: エンコードの明示的な指定</span><span class="sxs-lookup"><span data-stu-id="da050-131">Example: Explicitly Specifying an Encoding</span></span>  
 <span data-ttu-id="da050-132">明示的な XML 宣言が行われていない XML ドキュメント vcdoc を `varchar(max)` として保存しているとします。</span><span class="sxs-lookup"><span data-stu-id="da050-132">Assume that you have an XML document, vcdoc, stored as `varchar(max)` that does not have an explicit XML declaration.</span></span> <span data-ttu-id="da050-133">次のステートメントは、エンコード "iso8859-1" を指定した XML 宣言を追加し、この XML ドキュメントを宣言に連結します。バイト表現を保持するために結果を `varbinary(max)` にキャストし、最終的にその結果を XML にキャストします。</span><span class="sxs-lookup"><span data-stu-id="da050-133">The following statement adds an XML declaration with the encoding "iso8859-1", concatenates the XML document, casts the result to `varbinary(max)` so that the byte representation is preserved, and then finally casts it to XML.</span></span> <span data-ttu-id="da050-134">その結果、XML プロセッサで、指定したエンコード "iso8859-1" に従ってデータを解析し、対応する文字列値の UTF-16 表現を生成できます。</span><span class="sxs-lookup"><span data-stu-id="da050-134">This enables the XML processor to parse the data according to the specified encoding "iso8859-1" and generate the corresponding UTF-16 representation for string values.</span></span>  
  
```  
SELECT CAST(   
CAST (('<?xml version="1.0" encoding="iso8859-1"?>'+ vcdoc) AS VARBINARY (MAX))   
 AS XML)  
```  
  
### <a name="string-encoding-incompatibilities"></a><span data-ttu-id="da050-135">文字列エンコードの非互換性</span><span class="sxs-lookup"><span data-stu-id="da050-135">String Encoding Incompatibilities</span></span>  
 <span data-ttu-id="da050-136">XML をコピーし、文字列リテラルとして [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のクエリ エディター ウィンドウに貼り付けると、[N]VARCHAR 文字列エンコードの非互換性の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="da050-136">If you copy and paste XML as a string literal into the Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you might experience [N]VARCHAR string encoding incompatibilities.</span></span> <span data-ttu-id="da050-137">この問題が発生するかどうかは、XML インスタンスのエンコードによって決まります。</span><span class="sxs-lookup"><span data-stu-id="da050-137">This will depend on the encoding of your XML instance.</span></span> <span data-ttu-id="da050-138">多くの場合、XML 宣言の削除が必要になります。</span><span class="sxs-lookup"><span data-stu-id="da050-138">In many cases, you may want to remove the XML declaration.</span></span> <span data-ttu-id="da050-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="da050-139">For example:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
  <xsd:schema ...  
```  
  
 <span data-ttu-id="da050-140">続いて、N を指定し、XML インスタンスを Unicode 形式のインスタンスにします。</span><span class="sxs-lookup"><span data-stu-id="da050-140">You should then include an N to make the XML instance an instance of Unicode.</span></span> <span data-ttu-id="da050-141">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="da050-141">For example:</span></span>  
  
```  
-- Assign XML instance to a variable.  
DECLARE @X XML  
SET @X = N'...'  
-- Insert XML instance into an xml type column.  
INSERT INTO T VALUES (N'...')  
-- Create an XML schema collection  
CREATE XML SCHEMA COLLECTION XMLCOLL1 AS N'<xsd:schema ... '  
```  
  
## <a name="see-also"></a><span data-ttu-id="da050-142">参照</span><span class="sxs-lookup"><span data-stu-id="da050-142">See Also</span></span>  
 [<span data-ttu-id="da050-143">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="da050-143">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
