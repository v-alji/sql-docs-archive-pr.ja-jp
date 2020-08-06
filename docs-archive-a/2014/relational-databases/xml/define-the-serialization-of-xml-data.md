---
title: XML データのシリアル化の定義 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- entitization rules [XML in SQL Server]
- serialization
- reparsing serialized XML structures
- encoding [XML in SQL Server]
- XML [SQL Server], serialization
- xml data type [SQL Server], serialization
- typed XML
ms.assetid: 42b0b5a4-bdd6-4a60-b451-c87f14758d4b
author: rothja
ms.author: jroth
ms.openlocfilehash: df87dddd9fd4cf067125314c9d798eaa42523576
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645418"
---
# <a name="define-the-serialization-of-xml-data"></a><span data-ttu-id="19178-102">XML データのシリアル化の定義</span><span class="sxs-lookup"><span data-stu-id="19178-102">Define the Serialization of XML Data</span></span>
  <span data-ttu-id="19178-103">XML データ型を SQL 文字列型やバイナリ型に明示的または暗黙にキャストすると、XML データ型のコンテンツはこのトピックで説明する規則に従ってシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-103">When casting the xml data type explicitly or implicitly to a SQL string or binary type, the content of the xml data type will be serialized according to the rules outlined in this topic.</span></span>  
  
## <a name="serialization-encoding"></a><span data-ttu-id="19178-104">シリアル化のエンコード</span><span class="sxs-lookup"><span data-stu-id="19178-104">Serialization Encoding</span></span>  
 <span data-ttu-id="19178-105">SQL の対象型が VARBINARY の場合、結果は UTF-16 バイト順マークを前に付け、XML 宣言を付けずに、UTF-16 でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-105">If the SQL target type is VARBINARY, the result is serialized in UTF-16 with a UTF-16-byte order mark in front, but without an XML declaration.</span></span> <span data-ttu-id="19178-106">対象型が小さすぎる場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="19178-106">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="19178-107">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-107">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARBINARY(MAX))  
```  
  
 <span data-ttu-id="19178-108">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19178-108">This is the result:</span></span>  
  
```  
0xFFFE3C0094032F003E00  
```  
  
 <span data-ttu-id="19178-109">SQL の対象型が NVARCHAR または NCHAR の場合、結果はバイト順マークを前に付けず、XML 宣言を付けずに、UTF-16 でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-109">If the SQL target type is NVARCHAR or NCHAR, the result is serialized in UTF-16 without the byte order mark in front and without an XML declaration.</span></span> <span data-ttu-id="19178-110">対象型が小さすぎる場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="19178-110">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="19178-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-111">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as NVARCHAR(MAX))  
```  
  
 <span data-ttu-id="19178-112">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19178-112">This is the result:</span></span>  
  
```  
<Δ/>  
```  
  
 <span data-ttu-id="19178-113">SQL の対象型が VARCHAR または NCHAR の場合、結果はバイト順マークまたは XML 宣言を付けずに、データベースの照合順序のコード ページに対応するエンコードでシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-113">If the SQL target type is VARCHAR or NCHAR, the result is serialized in the encoding that corresponds to the database's collation code page without a byte order mark or XML declaration.</span></span> <span data-ttu-id="19178-114">対象型が小さすぎるか、または対象の照合順序のコード ページに値をマップできない場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="19178-114">If the target type is too small or the value cannot be mapped to the target collation code page, an error is raised.</span></span>  
  
 <span data-ttu-id="19178-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-115">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARCHAR(MAX))  
```  
  
 <span data-ttu-id="19178-116">現在の照合順序のコードページが Unicode 文字 & # x10300; を表すことができない場合、または特定のエンコードで表現される場合、エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19178-116">This may result in an error, if the current collation's code page cannot represent the Unicode character &#x10300;, or it will represent it in the specific encoding.</span></span>  
  
 <span data-ttu-id="19178-117">XML の結果がクライアント側に返されるときは、UTF-16 エンコードでデータが送信されます。</span><span class="sxs-lookup"><span data-stu-id="19178-117">When returning XML results to the client side, the data will be sent in UTF-16 encoding.</span></span> <span data-ttu-id="19178-118">クライアント側のプロバイダーでは、API の規則に従ってデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="19178-118">The client-side provider will then expose the data according to its API rules.</span></span>  
  
## <a name="serialization-of-the-xml-structures"></a><span data-ttu-id="19178-119">XML 構造のシリアル化</span><span class="sxs-lookup"><span data-stu-id="19178-119">Serialization of the XML Structures</span></span>  
 <span data-ttu-id="19178-120">**xml** データ型のコンテンツは、通常の方法でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-120">The content of an **xml** data type is serialized in the usual way.</span></span> <span data-ttu-id="19178-121">具体的には、要素ノードは要素マークアップにマップされ、テキスト ノードはテキスト コンテンツにマップされます。</span><span class="sxs-lookup"><span data-stu-id="19178-121">Specifically, element nodes are mapped to element markup, and text nodes are mapped to text content.</span></span> <span data-ttu-id="19178-122">ただし、文字がエンティティに変換される状況、および型指定されたアトミック値がシリアル化される方法については、次に説明します。</span><span class="sxs-lookup"><span data-stu-id="19178-122">However, the circumstances under which characters are entitized and how typed atomic values are serialized are described in the following sections.</span></span>  
  
## <a name="entitization-of-xml-characters-during-serialization"></a><span data-ttu-id="19178-123">シリアル化中の XML 文字のエンティティ変換</span><span class="sxs-lookup"><span data-stu-id="19178-123">Entitization of XML Characters During Serialization</span></span>  
 <span data-ttu-id="19178-124">シリアル化されたすべての XML 構造は再解析が可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="19178-124">Every serialized XML structure should be capable of being reparsed.</span></span> <span data-ttu-id="19178-125">したがって、XML パーサーの正規化フェーズ中に引き続き文字を互いにやり取りできるようにするには、一部の文字をエンティティに変換する方法でシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19178-125">Therefore, some characters have to be serialized in an entitized way to preserve the round-trip capability of the characters through the XML parser's normalization phase .</span></span> <span data-ttu-id="19178-126">ただし、一部の文字をエンティティに変換する場合は、ドキュメントが整形式になり、解析可能になるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="19178-126">However, some characters have to be entitized so that the document is well-formed and, therefore, able to be parsed.</span></span> <span data-ttu-id="19178-127">次に、シリアル化中に適用されるエンティティ変換の規則を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-127">Following are the entitization rules that apply during serialization:</span></span>  
  
-   <span data-ttu-id="19178-128">&、\<, and > の文字が属性値や要素のコンテンツ内に出現する場合、常に、それぞれ &amp;、&lt;、&gt; にエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-128">The characters &, \<, and > are always entitized to &amp;, &lt;, and &gt; respectively, if they occur inside an attribute value or element content.</span></span>  
  
-   <span data-ttu-id="19178-129">SQL Server では属性値を囲むために引用符 (U+0022) が使用されるので、属性値の引用符は &quot;にエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-129">Because SQL Server uses a quotation mark (U+0022) for enclosing attribute values, the quotation mark in attribute values is entitized as &quot;.</span></span>  
  
-   <span data-ttu-id="19178-130">サーバーのみでキャストする場合は、サロゲート ペアが 1 つの数字参照としてエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-130">A surrogate pair is entitized as a single numeric character reference, when casting on the server only.</span></span> <span data-ttu-id="19178-131">たとえば、サロゲート ペア U+D800 U+DF00 は、数字参照 &\#x00010300; にエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-131">For example the surrogate pair U+D800 U+DF00 is entitized to the numeric character reference &\#x00010300;.</span></span>  
  
-   <span data-ttu-id="19178-132">タブ (TAB, U+0009) とラインフィード (LF, U+000A) は、解析時に正規化されないように、属性値の内部でそれぞれ数字参照 &\#x9; および &\#xA; にエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-132">To protect a TAB (U+0009) and a linefeed (LF, U+000A) from being normalized during parsing, they are entitized to their numeric character references &\#x9; and &\#xA; respectively, inside attribute values.</span></span>  
  
-   <span data-ttu-id="19178-133">キャリッジ リターン (CR, U+000D) は、解析時に正規化されないように、属性値と要素のコンテンツの両方の内部で数字参照 &\#xD; にエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-133">To prevent a carriage return (CR, U+000D) from being normalized during parsing, it is entitized to its numeric character reference, &\#xD; inside both attribute values and element content.</span></span>  
  
-   <span data-ttu-id="19178-134">空白文字だけが含まれているテキスト ノードを保護するために、空白文字の 1 つ (通常は最後の空白文字) が数字参照としてエンティティ変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-134">To protect text nodes that only contain white space, one of the white-space characters, generally the last one, is entitized as its numeric character reference.</span></span> <span data-ttu-id="19178-135">このようにすると、解析時の空白文字の処理の設定とは無関係に、再解析時に空白文字のテキスト ノードが保持されます。</span><span class="sxs-lookup"><span data-stu-id="19178-135">In this way, reparsing preserves the white-space text node, regardless of the setting of the white-space handling during parsing.</span></span>  
  
 <span data-ttu-id="19178-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-136">For example:</span></span>  
  
```sql
declare @u NVARCHAR(50)  
set @u = N'<a a="  
    '+NCHAR(0xD800)+NCHAR(0xDF00)+N'>">   '+NCHAR(0xA)+N'</a>'  
select CAST(CONVERT(XML,@u,1) as NVARCHAR(50))  
```  
  
 <span data-ttu-id="19178-137">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19178-137">This is the result:</span></span>  
  
```  
<a a="  
    𐌀>">     
</a>  
```  
  
 <span data-ttu-id="19178-138">最後の空白文字の保護規則を適用しない場合は、 **xml** から文字列型またはバイナリ型にキャストするときに、CONVERT オプションを明示的に 1 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="19178-138">If you do not want to apply the last white-space protection rule, you can use the explicit CONVERT option 1 when casting from **xml** to a string or binary type.</span></span> <span data-ttu-id="19178-139">たとえば、エンティティ変換が行われないように、次のように設定できます。</span><span class="sxs-lookup"><span data-stu-id="19178-139">For example, to avoid entitization, you can do the following:</span></span>  
  
```sql
select CONVERT(NVARCHAR(50), CONVERT(XML, '<a>   </a>', 1), 1)  
```  
  
 <span data-ttu-id="19178-140">[query() メソッド (XML データ型)](/sql/t-sql/xml/query-method-xml-data-type) の結果は、XML データ型のインスタンスになることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="19178-140">Note that, the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) results in an xml data type instance.</span></span> <span data-ttu-id="19178-141">したがって、文字列型またはバイナリ型にキャストされる **query()** メソッドの結果は、上記の規則に従ってエンティティに変換されます。</span><span class="sxs-lookup"><span data-stu-id="19178-141">Therefore, any result of the **query()** method that is cast to a string or binary type is entitized according to the previously described rules.</span></span> <span data-ttu-id="19178-142">エンティティに変換されていない文字列値を取得する場合は、代わりに [value() メソッド (XML データ型)](/sql/t-sql/xml/value-method-xml-data-type) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19178-142">If you want to obtain the string values that are not entitized, you should use the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) instead.</span></span> <span data-ttu-id="19178-143">次に、 **query()** メソッドを使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-143">Following is an example of using the **query()** method:</span></span>  
  
```sql
declare @x xml  
set @x = N'<a>This example contains an entitized char: <.</a>'  
select @x.query('/a/text()')  
```  
  
 <span data-ttu-id="19178-144">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19178-144">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
 <span data-ttu-id="19178-145">次に、 **value()** メソッドを使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="19178-145">Following is an example of using the **value()** method:</span></span>  
  
```sql
select @x.value('(/a/text())[1]', 'nvarchar(100)')  
```  
  
 <span data-ttu-id="19178-146">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19178-146">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
## <a name="serializing-a-typed-xml-data-type"></a><span data-ttu-id="19178-147">型指定された XML データ型のシリアル化</span><span class="sxs-lookup"><span data-stu-id="19178-147">Serializing a Typed xml Data Type</span></span>  
 <span data-ttu-id="19178-148">型指定された **xml** データ型のインスタンスには、XML スキーマ型に従って型指定される値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="19178-148">A typed **xml** data type instance contains values that are typed according to their XML schema types.</span></span> <span data-ttu-id="19178-149">このような値は、XQuery が xs:string にキャストするのと同じ形式で、XML スキーマ型に従ってシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-149">These values are serialized according to their XML schema type in the same format as the XQuery cast to xs:string produces.</span></span> <span data-ttu-id="19178-150">詳細については、「 [XQuery での型キャストの規則](/sql/xquery/type-casting-rules-in-xquery)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19178-150">For more information, see [Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery).</span></span>  
  
 <span data-ttu-id="19178-151">たとえば、次の例で示すように、xs:double の値 1.34e1 は 13.4 にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="19178-151">For example, the xs:double value 1.34e1 is serialized to 13.4 as shown in the following example:</span></span>  
  
```sql
declare @x xml  
set @x =''  
select CAST(@x.query('1.34e1') as nvarchar(50))  
```  
  
 <span data-ttu-id="19178-152">これは、文字列値 13.4 を返します。</span><span class="sxs-lookup"><span data-stu-id="19178-152">This returns the string value 13.4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19178-153">参照</span><span class="sxs-lookup"><span data-stu-id="19178-153">See Also</span></span>  
 <span data-ttu-id="19178-154">[XQuery での型キャストの規則](/sql/xquery/type-casting-rules-in-xquery) </span><span class="sxs-lookup"><span data-stu-id="19178-154">[Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery) </span></span>  
 [<span data-ttu-id="19178-155">CAST および CONVERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19178-155">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
