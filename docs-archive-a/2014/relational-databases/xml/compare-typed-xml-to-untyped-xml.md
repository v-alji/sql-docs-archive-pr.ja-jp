---
title: 型指定された XML と型指定されていない XML の比較 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- parameters [XML in SQL Server]
- facets [XML in SQL Server]
- xml data type [SQL Server], columns
- untyped XML
- xml data type [SQL Server], typed xml
- XML [SQL Server], typed
- variables [XML in SQL Server], creating
- xml data type [SQL Server], untyped xml
- columns [XML in SQL Server], creating
- typed XML
- document mode processing [SQL Server]
- XML [SQL Server], untyped
- xml data type [SQL Server], parameters
ms.assetid: 4bc50af9-2f7d-49df-bb01-854d080c72c7
author: rothja
ms.author: jroth
ms.openlocfilehash: fae9ca930bd8741a1332b61c8272f2133590483e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713937"
---
# <a name="compare-typed-xml-to-untyped-xml"></a><span data-ttu-id="d37ca-102">型指定された XML と型指定されていない XML の比較</span><span class="sxs-lookup"><span data-stu-id="d37ca-102">Compare Typed XML to Untyped XML</span></span>
  <span data-ttu-id="d37ca-103">`xml` 型の変数、パラメーター、および列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-103">You can create variables, parameters, and columns of the `xml` type.</span></span> <span data-ttu-id="d37ca-104">必要に応じて、XML スキーマのコレクションを、`xml` 型の変数、パラメーター、または列に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-104">You can optionally associate a collection of XML schemas with a variable, parameter, or column of `xml` type.</span></span> <span data-ttu-id="d37ca-105">この場合、 `xml` データ型のインスタンスは*型指定*されています。</span><span class="sxs-lookup"><span data-stu-id="d37ca-105">In this case, the `xml` data type instance is called *typed*.</span></span> <span data-ttu-id="d37ca-106">それ以外の場合は、XML インスタンスを *型指定されていない*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-106">Otherwise, the XML instance is called *untyped*.</span></span>  
  
## <a name="well-formed-xml-and-the-xml-data-type"></a><span data-ttu-id="d37ca-107">適切な形式の XML と xml データ型</span><span class="sxs-lookup"><span data-stu-id="d37ca-107">Well-formed XML and the xml Data Type</span></span>  
 <span data-ttu-id="d37ca-108">`xml` データ型には、ISO 標準の `xml` データ型が実装されています。</span><span class="sxs-lookup"><span data-stu-id="d37ca-108">The `xml` data type implements the ISO standard `xml` data type.</span></span> <span data-ttu-id="d37ca-109">したがって、型指定されていない XML 列には、適切な形式の XML Version 1.0 ドキュメントを保存できるほか、テキスト ノードや任意の数の最上位要素が含まれた、いわゆる XML コンテンツ フラグメントを保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-109">Therefore, it can store well-formed XML version 1.0 documents and also so-called XML content fragments with text nodes and an arbitrary number of top-level elements in an untyped XML column.</span></span> <span data-ttu-id="d37ca-110">システムにより、データが適切な形式であることが確認されます。このとき XML スキーマに列をバインドする必要はなく、広義の適切な形式でないデータは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-110">The system checks that the data is well-formed, does not require the column to be bound to XML schemas, and rejects data that is not well-formed in the extended sense.</span></span> <span data-ttu-id="d37ca-111">このことは、型指定されていない XML の変数やパラメーターにも該当します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-111">This is true also of untyped XML variables and parameters.</span></span>  
  
## <a name="xml-schemas"></a><span data-ttu-id="d37ca-112">XML スキーマ</span><span class="sxs-lookup"><span data-stu-id="d37ca-112">XML Schemas</span></span>  
 <span data-ttu-id="d37ca-113">XML スキーマでは、次のものが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-113">An XML schema provides the following:</span></span>  
  
-   <span data-ttu-id="d37ca-114">**検証制約。**</span><span class="sxs-lookup"><span data-stu-id="d37ca-114">**Validation constraints.**</span></span> <span data-ttu-id="d37ca-115">型指定された xml インスタンスが割り当てまたは変更されるときは、常に、SQL Server によってそのインスタンスが検証されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-115">Whenever a typed xml instance is assigned to or modified, SQL Server validates the instance.</span></span>  
  
-   <span data-ttu-id="d37ca-116">**データ型情報。**</span><span class="sxs-lookup"><span data-stu-id="d37ca-116">**Data type information.**</span></span> <span data-ttu-id="d37ca-117">スキーマでは、`xml` データ型のインスタンス内の属性と要素の型に関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-117">Schemas provide information about the types of attributes and elements in the `xml` data type instance.</span></span> <span data-ttu-id="d37ca-118">この型情報により、インスタンスに含まれている値には、型指定されていない `xml` より正確な演算のセマンティクスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-118">The type information provides more precise operational semantics to the values contained in the instance than is possible with untyped `xml`.</span></span> <span data-ttu-id="d37ca-119">たとえば、10 進数の算術演算は 10 進数値では実行できますが、文字列値では実行できません。</span><span class="sxs-lookup"><span data-stu-id="d37ca-119">For example, decimal arithmetic operations can be performed on a decimal value, but not on a string value.</span></span> <span data-ttu-id="d37ca-120">スキーマで型情報が指定されるので、型指定された XML ストレージは、型指定されていない XML よりも大幅に小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-120">Because of this, typed XML storage can be made significantly more compact than untyped XML.</span></span>  
  
## <a name="choosing-typed-or-untyped-xml"></a><span data-ttu-id="d37ca-121">型指定された XML と型指定されていない XML の選択</span><span class="sxs-lookup"><span data-stu-id="d37ca-121">Choosing Typed or Untyped XML</span></span>  
 <span data-ttu-id="d37ca-122">次の条件に該当する場合は、型指定されていない `xml` データ型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d37ca-122">Use untyped `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="d37ca-123">XML データに対応するスキーマがない場合。</span><span class="sxs-lookup"><span data-stu-id="d37ca-123">You do not have a schema for your XML data.</span></span>  
  
-   <span data-ttu-id="d37ca-124">スキーマはあるが、サーバーでデータを検証しない場合。</span><span class="sxs-lookup"><span data-stu-id="d37ca-124">You have schemas, but you do not want the server to validate the data.</span></span> <span data-ttu-id="d37ca-125">サーバーにデータを保存する前にクライアント側で検証を行う場合、スキーマに従っていない無効な XML データを一時的に保存する場合、サーバーでサポートされていないスキーマ コンポーネントを使用する場合などが該当します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-125">This is sometimes the case when an application performs client-side validation before storing the data at the server, or temporarily stores XML data that is invalid according to the schema, or uses schema components that are not supported at the server.</span></span>  
  
 <span data-ttu-id="d37ca-126">`xml`次の状況では、型指定されたデータ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-126">Use typed `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="d37ca-127">使用する XML データのスキーマがあり、その XML スキーマに従ってサーバーで XML データを検証する場合。</span><span class="sxs-lookup"><span data-stu-id="d37ca-127">You have schemas for your XML data and you want the server to validate your XML data according to the XML schemas.</span></span>  
  
-   <span data-ttu-id="d37ca-128">型情報を基にしたストレージやクエリの最適化を行う場合。</span><span class="sxs-lookup"><span data-stu-id="d37ca-128">You want to take advantage of storage and query optimizations based on type information.</span></span>  
  
-   <span data-ttu-id="d37ca-129">クエリをコンパイルするときに型情報を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="d37ca-129">You want to take better advantage of type information during compilation of your queries.</span></span>  
  
 <span data-ttu-id="d37ca-130">型指定された XML の列、パラメーター、および変数には、XML ドキュメントまたは XML コンテンツを保存できます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-130">Typed XML columns, parameters, and variables can store XML documents or content.</span></span> <span data-ttu-id="d37ca-131">ただし、宣言のときに保存の対象がドキュメントなのかコンテンツなのかをフラグで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d37ca-131">However, you have to specify with a flag whether you are storing a document or content at the time of declaration.</span></span> <span data-ttu-id="d37ca-132">また、XML スキーマのコレクションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d37ca-132">Additionally, you have to provide the collection of XML schemas.</span></span> <span data-ttu-id="d37ca-133">各 XML インスタンスの最上位要素が 1 つだけの場合、DOCUMENT を指定します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-133">Specify DOCUMENT if each XML instance has exactly one top-level element.</span></span> <span data-ttu-id="d37ca-134">それ以外の場合は CONTENT を指定します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-134">Otherwise, use CONTENT.</span></span> <span data-ttu-id="d37ca-135">クエリのコンパイルで型を確認するとき、クエリ コンパイラにより DOCUMENT フラグが使用され、シングルトンの最上位要素が推測されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-135">The query compiler uses the DOCUMENT flag in type checks during query compilation to infer singleton top-level elements.</span></span>  
  
## <a name="creating-typed-xml"></a><span data-ttu-id="d37ca-136">型指定された XML の作成</span><span class="sxs-lookup"><span data-stu-id="d37ca-136">Creating Typed XML</span></span>  
 <span data-ttu-id="d37ca-137">型指定された `xml` 変数、パラメーター、または列を作成するには、まず、 [CREATE XML schema Collection &#40;transact-sql&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)を使用して xml スキーマコレクションを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d37ca-137">Before you can create typed `xml` variables, parameters, or columns, you must first register the XML schema collection by using [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span> <span data-ttu-id="d37ca-138">その後、XML スキーマ コレクションを `xml` データ型の変数、パラメーター、または列に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-138">You can then associate the XML schema collection with variables, parameters, or columns of the `xml` data type.</span></span>  
  
 <span data-ttu-id="d37ca-139">次の例では、XML スキーマ コレクション名を指定する際に、2 つの要素で構成された名前付け規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-139">In the following examples, a two-part naming convention is used for specifying the XML schema collection name.</span></span> <span data-ttu-id="d37ca-140">最初の要素はスキーマ名で、2 番目の要素は XML スキーマ コレクション名です。</span><span class="sxs-lookup"><span data-stu-id="d37ca-140">The first part is the schema name, and the second part is the XML schema collection name.</span></span>  
  
### <a name="example-associating-a-schema-collection-with-an-xml-type-variable"></a><span data-ttu-id="d37ca-141">例: スキーマ コレクションと xml 型の変数の関連付け</span><span class="sxs-lookup"><span data-stu-id="d37ca-141">Example: Associating a Schema Collection with an xml Type Variable</span></span>  
 <span data-ttu-id="d37ca-142">次の例では、型の変数を作成 `xml` し、それにスキーマコレクションを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-142">The following example creates an`xml` type variable and associates a schema collection with it.</span></span> <span data-ttu-id="d37ca-143">例で指定されているスキーマ コレクションは、 **AdventureWorks** のデータベースに既にインポートされています。</span><span class="sxs-lookup"><span data-stu-id="d37ca-143">The schema collection specified in the example is already imported in the **AdventureWorks** database.</span></span>  
  
```  
DECLARE @x xml (Production.ProductDescriptionSchemaCollection);   
```  
  
### <a name="example-specifying-a-schema-for-an-xml-type-column"></a><span data-ttu-id="d37ca-144">例: xml 型の列のスキーマの指定</span><span class="sxs-lookup"><span data-stu-id="d37ca-144">Example: Specifying a Schema for an xml Type Column</span></span>  
 <span data-ttu-id="d37ca-145">次の例では、`xml` 型の列を持つテーブルを作成し、列のスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-145">The following example creates a table with an `xml` type column and specifies a schema for the column:</span></span>  
  
```  
CREATE TABLE T1(  
 Col1 int,   
 Col2 xml (Production.ProductDescriptionSchemaCollection)) ;  
```  
  
### <a name="example-passing-an-xml-type-parameter-to-a-stored-procedure"></a><span data-ttu-id="d37ca-146">例: xml 型のパラメーターのストアド プロシージャへの受け渡し</span><span class="sxs-lookup"><span data-stu-id="d37ca-146">Example: Passing an xml Type Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="d37ca-147">次の例では、`xml` 型のパラメーターをストアド プロシージャに渡し、変数にスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-147">The following example passes an `xml` type parameter to a stored procedure and specifies a schema for the variable:</span></span>  
  
```  
CREATE PROCEDURE SampleProc   
  @ProdDescription xml (Production.ProductDescriptionSchemaCollection)   
AS   
...  
```  
  
 <span data-ttu-id="d37ca-148">XML スキーマ コレクションに関して次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d37ca-148">Note the following about the XML schema collection:</span></span>  
  
-   <span data-ttu-id="d37ca-149">XML スキーマ コレクションは、「 [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)」を使用して登録されたデータベースでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-149">An XML schema collection is available only in the database in which it was registered by using [Creating an XML Schema Collection](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span>  
  
-   <span data-ttu-id="d37ca-150">文字列から型指定された `xml` データ型にキャストする場合、指定したコレクションの XML スキーマの名前空間に基づいて、解析時に検証と型指定も行われます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-150">If you cast from a string to a typed `xml` data type, the parsing also performs validation and typing, based on the XML schema namespaces in the collection specified.</span></span>  
  
-   <span data-ttu-id="d37ca-151">型指定された `xml` データ型から、型指定されていない `xml` データ型にキャストできます。その逆も可能です。</span><span class="sxs-lookup"><span data-stu-id="d37ca-151">You can cast from a typed `xml` data type to an untyped `xml` data type, and vice versa.</span></span>  
  
 <span data-ttu-id="d37ca-152">SQL Server で XML を生成するその他の方法の詳細については、「 [XML データのインスタンスの作成](create-instances-of-xml-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d37ca-152">For more information about other ways to generate XML in SQL Server, see [Create Instances of XML Data](create-instances-of-xml-data.md).</span></span> <span data-ttu-id="d37ca-153">XML を生成後、それを `xml` データ型の変数に代入できます。また、その後の処理のために `xml` 型の列に格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-153">After XML is generated, it can be assigned either to an `xml` data type variable or stored in `xml` type columns for additional processing.</span></span>  
  
 <span data-ttu-id="d37ca-154">データ型の階層では、`xml` データ型は `sql_variant` やユーザー定義型の下、組み込み型の上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-154">In the data type hierarchy, the `xml` data type appears below `sql_variant` and user-defined types, but above any of the built-in types.</span></span>  
  
### <a name="example-specifying-facets-to-constrain-a-typed-xml-column"></a><span data-ttu-id="d37ca-155">例: 型指定された xml 列を制約するためのファセットの指定</span><span class="sxs-lookup"><span data-stu-id="d37ca-155">Example: Specifying Facets to Constrain a Typed xml Column</span></span>  
 <span data-ttu-id="d37ca-156">型指定された `xml` 列では、格納されているインスタンスごとに、最上位要素を 1 つだけ許可するように、列を制約できます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-156">For typed `xml` columns, you can constrain the column to allow only single, top-level elements for each instance stored in it.</span></span> <span data-ttu-id="d37ca-157">これを行うには、次の例で示すように、テーブルを作成するときに、オプションの `DOCUMENT` ファセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-157">You do this by specifying the optional `DOCUMENT` facet when a table is created, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml   
   (DOCUMENT Production.ProductDescriptionSchemaCollection));  
GO  
DROP TABLE T;  
GO  
```  
  
 <span data-ttu-id="d37ca-158">既定では、型指定された `xml` 列に格納されるインスタンスは、XML ドキュメントではなく、XML コンテンツとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-158">By default, instances stored in the typed `xml` column are stored as XML content and not as XML documents.</span></span> <span data-ttu-id="d37ca-159">これにより、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d37ca-159">This allows for the following:</span></span>  
  
-   <span data-ttu-id="d37ca-160">ゼロ (0) 個以上の最上位要素</span><span class="sxs-lookup"><span data-stu-id="d37ca-160">Zero or many top-level elements</span></span>  
  
-   <span data-ttu-id="d37ca-161">最上位要素のテキスト ノード</span><span class="sxs-lookup"><span data-stu-id="d37ca-161">Text nodes in top-level elements</span></span>  
  
 <span data-ttu-id="d37ca-162">また、次の例に示すように、 `CONTENT` ファセットを追加することにより、この動作を明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-162">You can also explicitly specify this behavior by adding `CONTENT` facet, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml(CONTENT Production.ProductDescriptionSchemaCollection));  
GO -- Default  
```  
  
 <span data-ttu-id="d37ca-163">`xml` 型 (型指定された xml) を定義する場所ならどこでも、オプションの DOCUMENT/CONTENT ファセットを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-163">Note that you can specify the optional DOCUMENT/CONTENT facets anywhere you define `xml` type (typed xml).</span></span> <span data-ttu-id="d37ca-164">たとえば、型指定された `xml` 変数を作成するときに、次に示すように DOCUMENT/CONTENT ファセットを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-164">For example, when you create a typed `xml` variable, you can add the DOCUMENT/CONTENT facet, as shown in the following:</span></span>  
  
```  
declare @x xml (DOCUMENT Production.ProductDescriptionSchemaCollection);  
```  
  
## <a name="document-type-definition-dtd"></a><span data-ttu-id="d37ca-165">DTD (文書型定義)</span><span class="sxs-lookup"><span data-stu-id="d37ca-165">Document Type Definition (DTD)</span></span>  
 <span data-ttu-id="d37ca-166">`xml` データ型の列、変数、およびパラメーターは XML スキーマを使用して型指定できますが、DTD では型指定できません。</span><span class="sxs-lookup"><span data-stu-id="d37ca-166">The `xml` data type columns, variables, and parameters can be typed by using XML schema, but not by using DTD.</span></span> <span data-ttu-id="d37ca-167">ただしインライン DTD は型指定された XML にも型指定されていない XML にも使用できるので、それを使用して既定値を指定したり、エンティティ参照を展開した形に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-167">However, inline DTD can be used for both untyped and typed XML to supply default values and to replace entity references with their expanded form.</span></span>  
  
 <span data-ttu-id="d37ca-168">サード パーティのツールを使用すると、DTD を XML スキーマ ドキュメントに変換できます。変換した XML スキーマはデータベースに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-168">You can convert DTDs to XML schema documents by using third-party tools, and load the XML schemas into the database.</span></span>  
  
## <a name="upgrading-typed-xml-from-sql-server-2005"></a><span data-ttu-id="d37ca-169">型指定された XML の SQL Server 2005 からのアップグレード</span><span class="sxs-lookup"><span data-stu-id="d37ca-169">Upgrading Typed XML from SQL Server 2005</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="d37ca-170">では、lax 検証のサポート、 **xs:date**、 **xs:time** 、および **xs:dateTime** のインスタンス データの処理の強化、list 型と union 型のサポートの追加など、XML スキーマのサポートがいくつかの点で拡張されています。</span><span class="sxs-lookup"><span data-stu-id="d37ca-170">made several extensions to the XML Schema support, including support for lax validation, improved handling of **xs:date**, **xs:time** and **xs:dateTime** instance data, and added support for list and union types.</span></span> <span data-ttu-id="d37ca-171">ほとんどの場合は、アップグレードの際にこれらの変更を意識する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d37ca-171">In most cases the changes do not affect the upgrade experience.</span></span> <span data-ttu-id="d37ca-172">ただし、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で、 **xs:date**型、 **xs:time**型、または **xs:dateTime** 型 (またはこれらのサブタイプ) の値を許可する XML スキーマ コレクションを使用していた場合は、その [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以降のバージョンにアタッチすると、以下のアップグレード手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-172">However if you used an XML Schema collection in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] that allowed values of type **xs:date**, **xs:time**, or **xs:dateTime** (or any subtype) then the following upgrade steps occur when you attach your [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database to a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="d37ca-173">XML スキーマ コレクションに **xs:anyType**、 **xs:anySimpleType**、 **xs:date** (またはそのサブタイプ)、 **xs:time** (またはそのサブタイプ)、または **xs:dateTime** (またはそのサブタイプ) として型指定されている要素や属性、あるいはこれらの型を含む union 型または list 型の要素や属性が含まれる場合、その XML スキーマ コレクションで型指定されているすべての XML 列で、次の状況が発生します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-173">For every XML column, that is typed with an XML Schema Collection that contains elements or attributes that are typed as either **xs:anyType**, **xs:anySimpleType**, **xs:date** or any of its subtypes, **xs:time** or any subtype thereof, or **xs:dateTime** or any of its subtypes, or are union or list types containing any of these types the following occurs:</span></span>  
  
    1.  <span data-ttu-id="d37ca-174">列のすべての XML インデックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="d37ca-174">All XML indices on the column will be disabled.</span></span>  
  
    2.  <span data-ttu-id="d37ca-175">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] の値はすべて Z タイムゾーンで正規化されているため、引き続き Z タイムゾーンで表されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-175">All [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] values will continue to be represented in the Z timezone, because they have been normalized to the Z timezone.</span></span>  
  
    3.  <span data-ttu-id="d37ca-176">1 年 1 月 1 日より小さい **xs:date** 値や **xs:dateTime** 値があると、インデックスが再構築されるときや、その値を含む XML データ型に対して XQuery ステートメントや XML-DML ステートメントが実行されるときに、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d37ca-176">Any **xs:date** or **xs:dateTime** values that are smaller than January 1st of year 1 will lead to a runtime error when the index gets rebuild or an XQuery or XML-DML statements gets executed against the XML data type containing that value.</span></span>  
  
2.  <span data-ttu-id="d37ca-177">**xs:date** ファセット、 **xs:dateTime** ファセット、または XML スキーマ コレクションの既定値に負の年がある場合は、 **xs:date** 基本型または **xs:dateTime** 基本型で許可されている最も小さな値 (たとえば、 **xs:dateTime**の場合は 0001-01-01T00:00:00.0000000Z) に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-177">Any negative years in **xs:date** or **xs:dateTime** facets or default values in an XML Schema collection will automatically be updated to the smallest value allowed by the base **xs:date** or **xs:dateTime** type (e.g., 0001-01-01T00:00:00.0000000Z for **xs:dateTime**).</span></span>  
  
 <span data-ttu-id="d37ca-178">負の年が含まれていても、単純な SQL SELECT ステートメントを使用して XML データ型全体を取得することはできます。</span><span class="sxs-lookup"><span data-stu-id="d37ca-178">Note that you can still use a simple SQL select statement to retrieve the whole XML data type, even if it contains negative years.</span></span> <span data-ttu-id="d37ca-179">負の年は、新たにサポートされた範囲内の年に置き換えるか、要素や属性の型を **xs:string**に変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d37ca-179">It is recommended that you replace negative years with a year within the newly supported range or change the type of the element or attribute to **xs:string**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37ca-180">参照</span><span class="sxs-lookup"><span data-stu-id="d37ca-180">See Also</span></span>  
 <span data-ttu-id="d37ca-181">[XML データのインスタンスの作成](create-instances-of-xml-data.md) </span><span class="sxs-lookup"><span data-stu-id="d37ca-181">[Create Instances of XML Data](create-instances-of-xml-data.md) </span></span>  
 <span data-ttu-id="d37ca-182">[xml データ型メソッド](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="d37ca-182">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="d37ca-183">[XML データ変更言語 &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="d37ca-183">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="d37ca-184">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d37ca-184">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
