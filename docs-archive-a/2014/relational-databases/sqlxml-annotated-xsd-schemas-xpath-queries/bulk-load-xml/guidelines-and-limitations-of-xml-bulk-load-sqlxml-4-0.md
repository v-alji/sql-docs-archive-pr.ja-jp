---
title: XML 一括読み込みのガイドラインと制限 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: rothja
ms.author: jroth
ms.openlocfilehash: 08c0020ac7b28702f5a573c6158ec9d50c735b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642715"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="d20a6-102">XML 一括読み込みのガイドラインと制限 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d20a6-102">Guidelines and Limitations of XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="d20a6-103">XML 一括読み込みを使用する場合は、次のガイドラインと制限に留意してください。</span><span class="sxs-lookup"><span data-stu-id="d20a6-103">When you use XML Bulk Load, you should be familiar with the following guidelines and limitations:</span></span>  
  
-   <span data-ttu-id="d20a6-104">インライン スキーマはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-104">Inline schemas are not supported.</span></span>  
  
     <span data-ttu-id="d20a6-105">インライン スキーマがソース XML ドキュメントにある場合、XML 一括読み込みでそのスキーマは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-105">If you have an inline schema in the source XML document, XML Bulk Load ignores that schema.</span></span> <span data-ttu-id="d20a6-106">XML 一括読み込みには、XML データの外部にあるマッピング スキーマを指定してください。</span><span class="sxs-lookup"><span data-stu-id="d20a6-106">You specify the mapping schema for XML Bulk Load external to the XML data.</span></span> <span data-ttu-id="d20a6-107">ノードでは、 **xmlns = "x:schema"** 属性を使用してマッピングスキーマを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-107">You cannot specify the mapping schema at a node by using the **xmlns="x:schema"** attribute.</span></span>  
  
-   <span data-ttu-id="d20a6-108">XML ドキュメントが適切な形式であるかどうかはチェックされますが、検証は行われません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-108">An XML document is checked for being well-formed, but it is not validated.</span></span>  
  
     <span data-ttu-id="d20a6-109">Xml 一括読み込みでは、xml ドキュメントが適切な形式であるかどうかを確認し、xml が World Wide Web コンソーシアムの XML 1.0 勧告の構文要件に準拠しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d20a6-109">XML Bulk Load checks the XML document to determine whether it is well-formed-that is, to ensure that the XML conforms to the syntax requirements of the World Wide Web Consortium's XML 1.0 recommendation.</span></span> <span data-ttu-id="d20a6-110">ドキュメントが適切な形式でない場合、XML 一括読み込みの処理は取り消され、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-110">If the document is not well-formed, XML Bulk Load cancels processing and returns an error.</span></span> <span data-ttu-id="d20a6-111">ただし、ドキュメントがフラグメントの場合 (ドキュメントに単一のルート要素がない場合) だけは、XML 一括読み込みでドキュメントが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-111">The only exception to this is when the document is a fragment (for example, the document has no single root element), in which case XML Bulk Load will load the document.</span></span>  
  
     <span data-ttu-id="d20a6-112">XML 一括読み込みでは、XML データ ファイル内で定義または参照されている XML-Data または DTD スキーマに関して、ドキュメントの検証は行われません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-112">XML Bulk Load does not validate the document with respect to any XML-Data or DTD schema that is defined or referenced within the XML data file.</span></span> <span data-ttu-id="d20a6-113">さらに、XML 一括読み込みでは、指定されるマッピング スキーマに対して XML データ ファイルは検証されません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-113">In addition, XML Bulk Load does not validate the XML data file against the mapping schema supplied.</span></span>  
  
-   <span data-ttu-id="d20a6-114">XML prolog 情報は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-114">Any XML prolog information is ignored.</span></span>  
  
     <span data-ttu-id="d20a6-115">Xml 一括読み込みでは、XML ドキュメント内の要素の前後にあるすべての情報が無視さ \<root> れます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-115">XML Bulk Load ignores all the information before and after the \<root> element in the XML document.</span></span> <span data-ttu-id="d20a6-116">たとえば、XML 宣言、内部 DTD 定義、外部 DTD 参照、コメントなどは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-116">For example, XML Bulk Load ignores any XML declarations, internal DTD definitions, external DTD references, comments, and so on.</span></span>  
  
-   <span data-ttu-id="d20a6-117">マッピング スキーマで、2 つのテーブル (たとえば Customer と CustOrder) 間の主キー/外部キーのリレーションシップを定義する場合は、主キーがあるテーブルを先に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-117">If you have a mapping schema that defines a primary key/foreign key relationship between two tables (such as between Customer and CustOrder), the table with the primary key must be described first in the schema.</span></span> <span data-ttu-id="d20a6-118">外部キー列があるテーブルは、後に記述します。</span><span class="sxs-lookup"><span data-stu-id="d20a6-118">The table with the foreign key column must appear later in the schema.</span></span> <span data-ttu-id="d20a6-119">その理由は、スキーマ内でテーブルが識別される順序が、データベースに読み込まれる順序と同じであるためです。たとえば、次の XDR スキーマでは、要素が要素の前に記述されているため、XML 一括読み込みで使用されるとエラーが発生し **\<Order>** **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-119">The reason for this is that the order in which the tables are identified in the schema is the order that is used to load them into the database.For example, the following XDR schema will produce an error when it is used in XML Bulk Load because the **\<Order>** element is described before the **\<Customer>** element.</span></span> <span data-ttu-id="d20a6-120">CustOrder の CustomerID 列は、Cust テーブル内の CustomerID 主キー列を参照する外部キー列です。</span><span class="sxs-lookup"><span data-stu-id="d20a6-120">The CustomerID column in CustOrder is a foreign key column that refers to the CustomerID primary key column in the Cust table.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   <span data-ttu-id="d20a6-121">スキーマで `sql:overflow-field` 注釈によりオーバーフロー列が指定されていない場合、XML 一括読み込みでは、XML ドキュメントに存在していてもマッピング スキーマに記述されていないデータは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-121">If the schema does not specify overflow columns by using the `sql:overflow-field` annotation, XML Bulk Load ignores any data that is present in the XML document but is not described in the mapping schema.</span></span>  
  
     <span data-ttu-id="d20a6-122">XML 一括読み込みでは、XML データ ストリーム内に既知のタグが検出されると常に、指定のマッピング スキーマが適用されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-122">XML Bulk Load applies the mapping schema that you have specified whenever it encounters known tags in the XML data stream.</span></span> <span data-ttu-id="d20a6-123">XML ドキュメントに存在していてもスキーマに記述されていないデータは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-123">It ignores data that is present in the XML document but is not described in the schema.</span></span> <span data-ttu-id="d20a6-124">たとえば、要素を記述するマッピングスキーマがあるとし **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-124">For example, assume you have a mapping schema that describes a **\<Customer>** element.</span></span> <span data-ttu-id="d20a6-125">XML データファイルには、 **\<AllCustomers>** すべての要素を囲むルートタグ (スキーマでは説明されていません) があり **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-125">The XML data file has an **\<AllCustomers>** root tag (which is not described in the schema) that encloses all the **\<Customer>** elements:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="d20a6-126">この場合、XML 一括読み込みでは要素が無視され、 **\<AllCustomers>** 要素でマッピングが開始さ **\<Customer>** れます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-126">In this case, XML Bulk Load ignores the **\<AllCustomers>** element and begins mapping at the **\<Customer>** element.</span></span> <span data-ttu-id="d20a6-127">XML ドキュメントに存在していてもスキーマに記述されていない要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-127">XML Bulk Load ignores the elements that are not described in the schema but are present in the XML document.</span></span>  
  
     <span data-ttu-id="d20a6-128">要素を含む別の XML ソースデータファイルについて考えてみ **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-128">Consider another XML source data file that contains **\<Order>** elements.</span></span> <span data-ttu-id="d20a6-129">この要素はマッピング スキーマには記述されていません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-129">These elements are not described in the mapping schema:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="d20a6-130">XML 一括読み込みでは、これらの要素は無視さ **\<Order>** れます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-130">XML Bulk Load ignores these **\<Order>** elements.</span></span> <span data-ttu-id="d20a6-131">ただし `sql:overflow-field` 、スキーマで注釈を使用して列をオーバーフロー列として識別すると、XML 一括読み込みではこの列にすべての未使用データが格納されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-131">But if you use the `sql:overflow-field`annotation in the schema to identify a column as an overflow column, XML Bulk Load stores all unconsumed data in this column.</span></span>  
  
-   <span data-ttu-id="d20a6-132">CDATA セクションとエンティティ参照は、データベースに保存される前に、同等の文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-132">CDATA sections and entity references are translated to their string equivalents before they are stored in the database.</span></span>  
  
     <span data-ttu-id="d20a6-133">この例では、CDATA セクションによって要素の値がラップさ **\<City>** れます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-133">In this example, a CDATA section wraps the value for the **\<City>** element.</span></span> <span data-ttu-id="d20a6-134">XML 一括読み込みでは、データベースに要素を挿入する前に、文字列値 ("NY") が抽出され **\<City>** ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-134">XML Bulk Load extracts the string value ("NY") before it inserts the **\<City>** element into the database.</span></span>  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     <span data-ttu-id="d20a6-135">XML 一括読み込みでは、エンティティ参照は保持されません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-135">XML Bulk Load does not preserve entity references.</span></span>  
  
-   <span data-ttu-id="d20a6-136">マッピング スキーマで属性に既定値が指定されており、その属性が XML ソース データに含まれていない場合、XML 一括読み込みでは既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-136">If the mapping schema specifies the default value for an attribute and the XML source data does not contain that attribute, XML Bulk Load uses the default value.</span></span>  
  
     <span data-ttu-id="d20a6-137">次のサンプル XDR スキーマでは、 **HireDate**属性に既定値が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="d20a6-137">The following sample XDR schema assigns a default value to the **HireDate** attribute:</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     <span data-ttu-id="d20a6-138">この XML データでは、2番目の要素に**HireDate**属性がありません **\<Customers>** 。</span><span class="sxs-lookup"><span data-stu-id="d20a6-138">In this XML data, the **HireDate** attribute is missing from the second **\<Customers>** element.</span></span> <span data-ttu-id="d20a6-139">XML 一括読み込みで2番目の要素がデータベースに挿入されるときに、 **\<Customers>** スキーマで指定されている既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-139">When XML Bulk Load inserts the second **\<Customers>** element into the database, it uses the default value that is specified in the schema.</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   <span data-ttu-id="d20a6-140">`sql:url-encode` 注釈はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-140">The `sql:url-encode` annotation is not supported:</span></span>  
  
     <span data-ttu-id="d20a6-141">XML データ入力に URL を指定して、その場所からデータの一括読み込みを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-141">You cannot specify a URL in the XML data input and expect Bulk Load to read data from that location.</span></span>  
  
     <span data-ttu-id="d20a6-142">マッピング スキーマで指定されているテーブルは、新しく作成されます (データベースは存在する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="d20a6-142">The tables that are identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="d20a6-143">データベースに1つ以上のテーブルが既に存在する場合、SGDropTables プロパティは、これらの既存のテーブルを削除して再作成するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="d20a6-143">If one or more of the tables already exists in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
-   <span data-ttu-id="d20a6-144">SchemaGen プロパティ (たとえば、SchemaGen = true) を指定した場合、マッピングスキーマで指定されているテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-144">If you specify the SchemaGen property (for example, SchemaGen = true), the tables that are identified in the mapping schema are created.</span></span> <span data-ttu-id="d20a6-145">ただし、SchemaGen では、次の1つの例外を除き、これらのテーブルに対する制約 (主キー/外部キーの制約など) は作成されません。リレーションシップの主キーを構成する XML ノードが XML 型の ID (XSD の場合は) を持つように定義されて `type="xsd:ID"` おり、SchemaGen に対して SGUseID プロパティが True に設定されている場合、id 型のノードから作成される主キーだけでなく、マッピングスキーマリレーションシップから主キー/外部キーのリレーションシップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-145">But SchemaGen does not create any constraints (such as the PRIMARY KEY/FOREIGN KEY constraints) on these tables with one exception: If the XML nodes that constitute the primary key in a relationship are defined as having an XML type of ID (that is, `type="xsd:ID"` for XSD) AND the SGUseID property is set to True for SchemaGen, then not only are primary keys created from the ID typed nodes, but primary key/foreign key relationships are created from mapping schema relationships.</span></span>  
  
-   <span data-ttu-id="d20a6-146">SchemaGen は、リレーショナルスキーマを生成するために XSD スキーマファセットと拡張機能を使用しません [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d20a6-146">SchemaGen does not use XSD schema facets and extensions to generate the relational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schema.</span></span>  
  
-   <span data-ttu-id="d20a6-147">一括読み込みで SchemaGen プロパティ (SchemaGen = true など) を指定した場合、指定されている (共有名のビューではなく) テーブルだけが更新されます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-147">If you specify the SchemaGen property (for example, SchemaGen = true) on Bulk Load, only tables (and not views of shared name) that are specified are updated.</span></span>  
  
-   <span data-ttu-id="d20a6-148">SchemaGen は、注釈付き XSD からリレーショナルスキーマを生成するための基本的な機能のみを提供します。</span><span class="sxs-lookup"><span data-stu-id="d20a6-148">SchemaGen only provides basic functionality for generating the relational schema from annotated XSD.</span></span> <span data-ttu-id="d20a6-149">ユーザーは必要に応じて、生成されたテーブルを手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-149">The user should modify the generated tables manually, if needed.</span></span>  
  
-   <span data-ttu-id="d20a6-150">テーブル間に複数のリレーションシップが存在する場合、SchemaGen は、2つのテーブル間に含まれるすべてのキーを含む単一のリレーションシップを作成しようとします。</span><span class="sxs-lookup"><span data-stu-id="d20a6-150">Where more than relationship exists between tables,SchemaGen tries to create a single relationship that includes all the keys involved between the two tables.</span></span> <span data-ttu-id="d20a6-151">この制限は、[!INCLUDE[tsql](../../../includes/tsql-md.md)] エラーの原因となることがあります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-151">This limitation might be the cause of a [!INCLUDE[tsql](../../../includes/tsql-md.md)] error.</span></span>  
  
-   <span data-ttu-id="d20a6-152">データベースに XML データの一括読み込みを行う場合は、マッピング スキーマ内に、データベース列にマップされる属性または子要素が 1 つ以上存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-152">When you are bulk loading XML data into a database, there must be at least one attribute or child element in the mapping schema that is mapped to a database column.</span></span>  
  
-   <span data-ttu-id="d20a6-153">XML 一括読み込みを使用して日付値を挿入する場合、値は (-)CCYY-MM-DD((+-)TZ) の形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-153">If you are inserting date values by using XML Bulk Load, the values must be specified in the (-)CCYY-MM-DD((+-)TZ) format.</span></span> <span data-ttu-id="d20a6-154">これは日付の標準の XSD 形式です。</span><span class="sxs-lookup"><span data-stu-id="d20a6-154">This is the standard XSD format for the date.</span></span>  
  
-   <span data-ttu-id="d20a6-155">一部のプロパティ フラグは、他のプロパティ フラグと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-155">Some property flags are not compatible with other property flags.</span></span> <span data-ttu-id="d20a6-156">たとえば、一括読み込みでは `Ignoreduplicatekeys=true` と `Keepidentity=false` の同時使用がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-156">For example, bulk load does not support `Ignoreduplicatekeys=true` together with `Keepidentity=false`.</span></span> <span data-ttu-id="d20a6-157">`Keepidentity=false` である場合、一括読み込みではサーバーがキー値を生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-157">When `Keepidentity=false`, bulk load expects the server to generate the key values.</span></span> <span data-ttu-id="d20a6-158">各テーブルでは、キーに `IDENTITY` 制約が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d20a6-158">Tables should have an `IDENTITY` constraint on the key.</span></span> <span data-ttu-id="d20a6-159">サーバーは重複キーを生成しないため、`Ignoreduplicatekeys` を `true` に設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d20a6-159">The server will not generate duplicate keys, which means there is no need for `Ignoreduplicatekeys` to be set to `true`.</span></span> <span data-ttu-id="d20a6-160">`Ignoreduplicatekeys` を `true` に設定しなければならないのは、複数の行があるテーブルに入力データから主キー値をアップロードすることによって主キー値の競合が発生する可能性がある場合だけです。</span><span class="sxs-lookup"><span data-stu-id="d20a6-160">`Ignoreduplicatekeys` should be set to `true` only when uploading primary key values from the incoming data into a table that has rows and there is a potential for conflict of primary key values.</span></span>  
  
  
