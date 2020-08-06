---
title: 計算列を使用した使用頻度の高い XML 値の昇格 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- promoting properties [XML in SQL Server]
- property promotion [XML in SQL Server]
ms.assetid: f5111896-c2fd-4209-b500-f2baa45489ad
author: rothja
ms.author: jroth
ms.openlocfilehash: bfb83b7772ffd92eab7087db11e4c3ffd96afa47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717541"
---
# <a name="promote-frequently-used-xml-values-with-computed-columns"></a><span data-ttu-id="5fa87-102">計算列を使用した使用頻度の高い XML 値の昇格</span><span class="sxs-lookup"><span data-stu-id="5fa87-102">Promote Frequently Used XML Values with Computed Columns</span></span>
  <span data-ttu-id="5fa87-103">クエリが主に少数の要素や属性の値に対して行われる場合、対象になる値をリレーショナル列に昇格できます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-103">If queries are made principally on a small number of element and attribute values, you may want to promote those quantities into relational columns.</span></span> <span data-ttu-id="5fa87-104">XML インスタンス全体を取得する一方で、XML データの一部に対してクエリを実行する場合に昇格が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-104">This is helpful when queries are issued on a small part of the XML data while the whole XML instance is retrieved.</span></span> <span data-ttu-id="5fa87-105">XML 列に XML インデックスを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5fa87-105">Creating an XML index on the XML column is not required.</span></span> <span data-ttu-id="5fa87-106">代わりに、昇格した列にインデックスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-106">Instead, the promoted column can be indexed.</span></span> <span data-ttu-id="5fa87-107">クエリは昇格した列を使用するように記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fa87-107">Queries must be written to use the promoted column.</span></span> <span data-ttu-id="5fa87-108">クエリ オプティマイザーは、クエリの対象を XML 列から、昇格した列に振り替えないためです。</span><span class="sxs-lookup"><span data-stu-id="5fa87-108">That is, the query optimizer does not target again the queries on the XML column to the promoted column.</span></span>  
  
 <span data-ttu-id="5fa87-109">昇格した列は、同一のテーブルで計算列にすることができます。また、任意のテーブルでユーザーが管理する独立した列にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-109">The promoted column can be a computed column in the same table or it can be a separate, user-maintained column in a table.</span></span> <span data-ttu-id="5fa87-110">これは、各 XML インスタンスから単一の値を昇格するときには十分です。</span><span class="sxs-lookup"><span data-stu-id="5fa87-110">This is sufficient when singleton values are promoted from each XML instance.</span></span> <span data-ttu-id="5fa87-111">しかし、複数の値から構成されるプロパティの場合、個々のプロパティ用に個別のテーブルを作成する必要があります。詳細については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa87-111">However, for multi-valued properties, you have to create a separate table for the property, as described in the following section.</span></span>  
  
## <a name="computed-column-based-on-the-xml-data-type"></a><span data-ttu-id="5fa87-112">xml データ型を基にした計算列</span><span class="sxs-lookup"><span data-stu-id="5fa87-112">Computed Column Based on the xml Data Type</span></span>  
 <span data-ttu-id="5fa87-113">データ型のメソッドを呼び出すユーザー定義関数を使用して、計算列を作成でき `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-113">A computed column can be created by using a user-defined function that invokes `xml` data type methods.</span></span> <span data-ttu-id="5fa87-114">計算列の型は、XML を含めどの SQL 型でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5fa87-114">The type of the computed column can be any SQL type, including XML.</span></span> <span data-ttu-id="5fa87-115">この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-115">This is illustrated in the following example.</span></span>  
  
### <a name="example-computed-column-based-on-the-xml-data-type-method"></a><span data-ttu-id="5fa87-116">例: xml データ型のメソッドを基にした計算列</span><span class="sxs-lookup"><span data-stu-id="5fa87-116">Example: Computed Column Based on the xml Data Type Method</span></span>  
 <span data-ttu-id="5fa87-117">書籍の ISBN 番号を取得するユーザー定義関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-117">Create the user-defined function for a book ISBN number:</span></span>  
  
```  
CREATE FUNCTION udf_get_book_ISBN (@xData xml)  
RETURNS varchar(20)  
BEGIN  
   DECLARE @ISBN   varchar(20)  
   SELECT @ISBN = @xData.value('/book[1]/@ISBN', 'varchar(20)')  
   RETURN @ISBN   
END  
```  
  
 <span data-ttu-id="5fa87-118">ISBN を保存する計算列をテーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-118">Add a computed column to the table for the ISBN:</span></span>  
  
```  
ALTER TABLE      T  
ADD   ISBN AS dbo.udf_get_book_ISBN(xCol)  
```  
  
 <span data-ttu-id="5fa87-119">計算列は、通常の方法でインデックスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-119">The computed column can be indexed in the usual way.</span></span>  
  
### <a name="example-queries-on-a-computed-column-based-on-xml-data-type-methods"></a><span data-ttu-id="5fa87-120">例: xml データ型のメソッドを基にした計算列へのクエリ</span><span class="sxs-lookup"><span data-stu-id="5fa87-120">Example: Queries on a Computed Column Based on xml Data Type Methods</span></span>  
 <span data-ttu-id="5fa87-121">ISBN が 0-7356-1588-2 の <`book`> を取得します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-121">To obtain the <`book`> whose ISBN is 0-7356-1588-2:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  xCol.exist('/book/@ISBN[. = "0-7356-1588-2"]') = 1  
```  
  
 <span data-ttu-id="5fa87-122">XML 列へのクエリを次のように書き換えると、計算列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-122">The query on the XML column can be rewritten to use the computed column as follows:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  ISBN = '0-7356-1588-2'  
```  
  
 <span data-ttu-id="5fa87-123">ユーザー定義関数を使用して、ユーザー定義関数を作成し、 `xml` データ型と計算列を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-123">You can create a user-defined function to return the `xml` data type and a computed column by using the user-defined function.</span></span> <span data-ttu-id="5fa87-124">ただし、XML 計算列には XML インデックスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="5fa87-124">However, you cannot create an XML index on the computed, XML column.</span></span>  
  
## <a name="creating-property-tables"></a><span data-ttu-id="5fa87-125">プロパティ テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="5fa87-125">Creating Property Tables</span></span>  
 <span data-ttu-id="5fa87-126">XML データの中から複数の値で構成されるプロパティの一部を 1 つ以上のテーブルに昇格させ、インデックスを作成してクエリの対象をそのテーブルに振り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-126">You may want to promote some of the multivalued properties from your XML data into one or more tables, create indexes on those tables, and target again your queries to use them.</span></span> <span data-ttu-id="5fa87-127">クエリ ワークロードの大半が少数のプロパティで占められているシナリオが典型的です。</span><span class="sxs-lookup"><span data-stu-id="5fa87-127">A typical scenario is one in which a small number of properties covers most of your query workload.</span></span> <span data-ttu-id="5fa87-128">次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-128">You can do the following:</span></span>  
  
-   <span data-ttu-id="5fa87-129">複数の値から構成されるプロパティを格納するためのテーブルを 1 つ以上作成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-129">Create one or more tables to hold the multivalued properties.</span></span> <span data-ttu-id="5fa87-130">1 つのプロパティを 1 つのテーブルに保存し、プロパティ テーブルでベース テーブルの主キーを複製すると、ベース テーブルとの逆結合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5fa87-130">You may find it convenient to store one property per table and duplicate the primary key of the base table in the property tables for back joining with the base table.</span></span>  
  
-   <span data-ttu-id="5fa87-131">プロパティの相対順序を保持する場合、相対順序を保持するための列を別に設ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fa87-131">If you want to maintain the relative order of the properties, you have to introduce a separate column for the relative order.</span></span>  
  
-   <span data-ttu-id="5fa87-132">プロパティ テーブルを管理するためのトリガーを XML 列に作成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-132">Create triggers on the XML column to maintain the property tables.</span></span> <span data-ttu-id="5fa87-133">トリガー内では次のいずれかを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-133">Within the triggers, do one of the following:</span></span>  
  
    -   <span data-ttu-id="5fa87-134">`xml` **Nodes ()** 、 **value ()** などのデータ型のメソッドを使用して、プロパティテーブルの行を挿入および削除します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-134">Use `xml` data type methods, such as **nodes()** and **value()**, to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="5fa87-135">CLR (共通言語ランタイム) でストリーミング テーブル値関数を作成し、プロパティ テーブルの行を挿入および削除します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-135">Create streaming table-valued functions in the common language runtime (CLR) to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="5fa87-136">主キーを使用してテーブルどうしを結合し、プロパティ テーブルに SQL アクセスを行うクエリ、およびベース テーブルの XML 列に XML アクセスを行うクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-136">Write queries for SQL access to the property tables and for XML access to the XML column in the base table, with joins between the tables by using their primary key.</span></span>  
  
### <a name="example-create-a-property-table"></a><span data-ttu-id="5fa87-137">例: プロパティ テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="5fa87-137">Example: Create a Property Table</span></span>  
 <span data-ttu-id="5fa87-138">たとえば、著者の名 (ファースト ネーム) を昇格させるとします。</span><span class="sxs-lookup"><span data-stu-id="5fa87-138">For illustration, assume that you want to promote the first name of the authors.</span></span> <span data-ttu-id="5fa87-139">共著の場合もあるので、名は複数の値から構成されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5fa87-139">Books have one or more authors, so that first name is a multivalued property.</span></span> <span data-ttu-id="5fa87-140">それぞれの名は、プロパティ テーブルの個別の行に保存されます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-140">Each first name is stored in a separate row of a property table.</span></span> <span data-ttu-id="5fa87-141">逆結合のため、ベース テーブルの主キーをプロパティ テーブルで複製します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-141">The primary key of the base table is duplicated in the property table for back join.</span></span>  
  
```  
create table tblPropAuthor (propPK int, propAuthor varchar(max))  
```  
  
### <a name="example-create-a-user-defined-function-to-generate-a-rowset-from-an-xml-instance"></a><span data-ttu-id="5fa87-142">例: XML インスタンスから行セットを生成するユーザー定義関数の作成</span><span class="sxs-lookup"><span data-stu-id="5fa87-142">Example: Create a User-defined Function to Generate a Rowset from an XML Instance</span></span>  
 <span data-ttu-id="5fa87-143">次のテーブル値関数 udf_XML2Table は、主キーの値と XML インスタンスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5fa87-143">The following table-valued function, udf_XML2Table, accepts a primary key value and an XML instance.</span></span> <span data-ttu-id="5fa87-144"><`book`> 要素のすべての著者の名を取得し、主キーと名の組み合わせから構成される行セットを返します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-144">It retrieves the first name of all authors of the <`book`> elements and returns a rowset of primary key, first name pairs.</span></span>  
  
```  
create function udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (propPK int, propAuthor varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
      select @pk, nref.value('.', 'varchar(max)')  
      from   @xCol.nodes('/book/author/first-name') R(nref)  
      return  
end  
```  
  
### <a name="example-create-triggers-to-populate-a-property-table"></a><span data-ttu-id="5fa87-145">例: プロパティ テーブルにデータを格納するトリガーの作成</span><span class="sxs-lookup"><span data-stu-id="5fa87-145">Example: Create Triggers to Populate a Property Table</span></span>  
 <span data-ttu-id="5fa87-146">次の挿入トリガーを使用して、プロパティ テーブルに行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-146">The insert trigger inserts rows into the property table:</span></span>  
  
```  
create trigger trg_docs_INS on T for insert  
as  
      declare @wantedXML xml  
      declare @FK int  
      select @wantedXML = xCol from inserted  
      select @FK = PK from inserted  
  
   insert into tblPropAuthor  
   select * from dbo.udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="5fa87-147">次の削除トリガーを使用して、削除する行の主キーの値を基に、プロパティ テーブルから行を削除します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-147">The delete trigger deletes the rows from the property table based on the primary key value of the deleted rows:</span></span>  
  
```  
create trigger trg_docs_DEL on T for delete  
as  
   declare @FK int  
   select @FK = PK from deleted  
   delete tblPropAuthor where propPK = @FK  
```  
  
 <span data-ttu-id="5fa87-148">次の更新トリガーを使用して、更新する XML インスタンスに対応するプロパティ テーブルの既存の行を削除し、新しい行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-148">The update trigger deletes the existing rows in the property table corresponding to the updated XML instance and inserts new rows into the property table:</span></span>  
  
```  
create trigger trg_docs_UPD  
on T  
for update  
as  
if update(xCol) or update(pk)  
begin  
      declare @FK int  
      declare @wantedXML xml  
      select @FK = PK from deleted  
      delete tblPropAuthor where propPK = @FK  
  
   select @wantedXML = xCol from inserted  
   select @FK = pk from inserted  
  
   insert into tblPropAuthor   
      select * from dbo.udf_XML2Table(@FK, @wantedXML)  
end  
```  
  
### <a name="example-find-xml-instances-whose-authors-have-the-same-first-name"></a><span data-ttu-id="5fa87-149">例: 著者の名が同一の XML インスタンスの検索</span><span class="sxs-lookup"><span data-stu-id="5fa87-149">Example: Find XML Instances Whose Authors Have the Same First Name</span></span>  
 <span data-ttu-id="5fa87-150">XML 列に対するクエリも作成できますが、</span><span class="sxs-lookup"><span data-stu-id="5fa87-150">The query can be formed on the XML column.</span></span> <span data-ttu-id="5fa87-151">プロパティ テーブルで名 "David" を検索し、ベース テーブルとの逆結合を実行して XML インスタンスを返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-151">Alternatively, it can search the property table for first name "David" and perform a back join with the base table to return the XML instance.</span></span> <span data-ttu-id="5fa87-152">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-152">For example:</span></span>  
  
```  
SELECT xCol   
FROM     T JOIN tblPropAuthor ON T.pk = tblPropAuthor.propPK  
WHERE    tblPropAuthor.propAuthor = 'David'  
```  
  
### <a name="example-solution-using-the-clr-streaming-table-valued-function"></a><span data-ttu-id="5fa87-153">例: CLR ストリーミング テーブル値関数を使用したソリューション</span><span class="sxs-lookup"><span data-stu-id="5fa87-153">Example: Solution Using the CLR Streaming Table-valued Function</span></span>  
 <span data-ttu-id="5fa87-154">このソリューションは、次の手順で実行します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-154">This solution is made up of the following steps:</span></span>  
  
1.  <span data-ttu-id="5fa87-155">CLR クラス SqlReaderBase を定義します。このクラスは ISqlReader を実装し、XML インスタンスにパス式を適用することでストリーミング テーブル値出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-155">Define a CLR class, SqlReaderBase, that implements ISqlReader and generates a streaming, table-valued output by applying a path expression on an XML instance.</span></span>  
  
2.  <span data-ttu-id="5fa87-156">CLR クラスを起動するため、アセンブリおよび Transact-SQL ユーザー定義関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-156">Create an assembly and a Transact-SQL user-defined function to start the CLR class.</span></span>  
  
3.  <span data-ttu-id="5fa87-157">ユーザー定義関数を使用して、プロパティ テーブルのメンテナンスに使用する挿入トリガー、更新トリガー、および削除トリガーを定義します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-157">Define the insert, update, and delete triggers by using the user-defined function to maintain a property tables.</span></span>  
  
 <span data-ttu-id="5fa87-158">まず、ストリーミング CLR 関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-158">To do this, you first create the streaming CLR function.</span></span> <span data-ttu-id="5fa87-159">この `xml` データ型は ADO.NET でマネージクラス SqlXml として公開され、XmlReader を返す**Createreader ()** メソッドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5fa87-159">The `xml` data type is exposed as a managed class SqlXml in ADO.NET and supports the **CreateReader()** method that returns an XmlReader.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fa87-160">このセクションの例のコードでは、XPathDocument および XPathNavigator を使用しています。</span><span class="sxs-lookup"><span data-stu-id="5fa87-160">The example code in this section uses XPathDocument and XPathNavigator.</span></span> <span data-ttu-id="5fa87-161">この 2 つはすべての XML ドキュメントをメモリに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-161">These force you to load all the XML documents into memory.</span></span> <span data-ttu-id="5fa87-162">大きな XML ドキュメントを処理するためにこのサンプルと同様のコードを使用する場合、このコードにはスケーラビリティはありません。</span><span class="sxs-lookup"><span data-stu-id="5fa87-162">If you are using similar code in your application to process several large XML documents, this code is not scalable.</span></span> <span data-ttu-id="5fa87-163">代わりに、メモリの割り当てを少なく抑え、可能な限りストリーミング インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5fa87-163">Instead, keep memory allocations small and use streaming interfaces whenever possible.</span></span> <span data-ttu-id="5fa87-164">パフォーマンスの詳細については、「 [CLR 統合のアーキテクチャ](../../database-engine/dev-guide/architecture-of-clr-integration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa87-164">For more information about performance, see [Architecture of CLR Integration](../../database-engine/dev-guide/architecture-of-clr-integration.md).</span></span>  
  
```  
public class c_streaming_xml_tvf {  
   public static ISqlReader streaming_xml_tvf   
(SqlXml xmlDoc, string pathExpression) {  
      return (new TestSqlReaderBase (xmlDoc, pathExpression));  
   }  
}  
  
// Class that implements ISqlReader  
public class TestSqlReaderBase : ISqlReader {  
XPathNodeIterator m_iterator;           
   public SqlChars FirstName;  
// Metadata for current resultset  
private SqlMetaData[] m_rgSqlMetaData;        
  
   public TestSqlReaderBase (SqlXml xmlDoc, string pathExpression) {     
      // Variables for XPath navigation  
      XPathDocument xDoc;  
      XPathNavigator xNav;  
      XPathExpression xPath;  
  
      // Set sql metadata  
      m_rgSqlMetaData = new SqlMetaData[1];  
      m_rgSqlMetaData[0] = new SqlMetaData ("FirstName",    
SqlDbType.NVarChar,50);     
  
      //Set up the Navigator  
      if (!xmlDoc.IsNull)  
          xDoc = new XPathDocument (xmlDoc.CreateReader());  
      else  
          xDoc = new XPathDocument ();  
      xNav = xDoc.CreateNavigator();  
      xPath = xNav.Compile (pathExpression);  
      m_iterator = xNav.Select(xPath);  
   }  
   public bool Read() {  
      bool moreRows = true;  
      if (moreRows = m_iterator.MoveNext())  
         FirstName = new SqlChars (m_iterator.Current.Value);  
      return moreRows;  
   }  
}  
```  
  
 <span data-ttu-id="5fa87-165">次に、アセンブリ、および CLR 関数 streaming_xml_tvf に対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数 SQL_streaming_xml_tvf (ここには示していません) を作成します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-165">Next, create an assembly and a [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined function, SQL_streaming_xml_tvf (not shown), that corresponds to the CLR function, streaming_xml_tvf.</span></span> <span data-ttu-id="5fa87-166">このユーザー定義関数を使用して、行セットを生成するためのテーブル値関数 CLR_udf_XML2Table を定義します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-166">The user-defined function is used to define the table-valued function, CLR_udf_XML2Table, for rowset generation:</span></span>  
  
```  
create function CLR_udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (FK int, FirstName varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
   select @pk, FirstName   
   FROM   SQL_streaming_xml_tvf (@xCol, '/book/author/first-name')  
      return  
end  
```  
  
 <span data-ttu-id="5fa87-167">最後に、「プロパティ テーブルにデータを格納するトリガーの作成」で示したトリガーを、udf_XML2Table 関数を CLR_udf_XML2Table 関数に置き換えて定義します。</span><span class="sxs-lookup"><span data-stu-id="5fa87-167">Finally, define triggers as shown in the example, "Create triggers to populate a property table", but replace udf_XML2Table with the CLR_udf_XML2Table function.</span></span> <span data-ttu-id="5fa87-168">挿入トリガーは次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="5fa87-168">The insert trigger is shown in the following example:</span></span>  
  
```  
create trigger CLR_trg_docs_INS on T for insert  
as  
   declare @wantedXML xml  
   declare @FK int  
   select @wantedXML = xCol from inserted  
   select @FK = PK from inserted  
  
   insert into tblPropAuthor  
      select *  
   from    dbo.CLR_udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="5fa87-169">削除トリガーは CLR を使用しない場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="5fa87-169">The delete trigger is identical to the non-CLR version.</span></span> <span data-ttu-id="5fa87-170">更新トリガーは関数 udf_XML2Table() を CLR_udf_XML2Table() に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5fa87-170">However, the update trigger just replaces the function udf_XML2Table() with CLR_udf_XML2Table().</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa87-171">参照</span><span class="sxs-lookup"><span data-stu-id="5fa87-171">See Also</span></span>  
 [<span data-ttu-id="5fa87-172">計算列での XML の使用</span><span class="sxs-lookup"><span data-stu-id="5fa87-172">Use XML in Computed Columns</span></span>](use-xml-in-computed-columns.md)  
  
  
