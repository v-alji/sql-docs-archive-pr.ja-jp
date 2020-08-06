---
title: XML データ型の変数と列の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
author: rothja
ms.author: jroth
ms.openlocfilehash: 08b79888eb47634deaccc910b2ea3c93800b7c78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738071"
---
# <a name="create-xml-data-type-variables-and-columns"></a><span data-ttu-id="085c4-102">XML データ型の変数と列の作成</span><span class="sxs-lookup"><span data-stu-id="085c4-102">Create XML Data Type Variables and Columns</span></span>
  <span data-ttu-id="085c4-103">`xml`データ型は、の組み込みデータ型で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] やなどの他の組み込み型と似てい `int` `varchar` ます。</span><span class="sxs-lookup"><span data-stu-id="085c4-103">The `xml` data type is a built-in data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is somewhat similar to other built-in types such as `int` and `varchar`.</span></span> <span data-ttu-id="085c4-104">他の組み込み型と同様に、変数の型 `xml` 、パラメーターの型、関数の戻り値の型、または[CAST および CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)としてテーブルを作成するときに、列の型としてデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-104">As with other built-in types, you can use the `xml` data type as a column type when you create a table as a variable type, a parameter type, a function-return type, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
## <a name="creating-columns-and-variables"></a><span data-ttu-id="085c4-105">列と変数の作成</span><span class="sxs-lookup"><span data-stu-id="085c4-105">Creating Columns and Variables</span></span>  
 <span data-ttu-id="085c4-106">テーブルの一部として `xml` 型の列を作成するには、 `CREATE TABLE` ステートメントを使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="085c4-106">To create an `xml` type column as part of a table, use a `CREATE TABLE` statement, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 <span data-ttu-id="085c4-107">`DECLARE statement` を使用して `xml` 型の変数を作成できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="085c4-107">You can use a `DECLARE statement` to create a variable of `xml` type, as the following example shows.</span></span>  
  
```  
DECLARE @x xml   
```  
  
 <span data-ttu-id="085c4-108">XML スキーマ コレクションを指定して、型指定された `xml` 変数を作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="085c4-108">Create a typed `xml` variable by specifying an XML schema collection, as shown in the following example.</span></span>  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 <span data-ttu-id="085c4-109">`xml` 型のパラメーターをストアド プロシージャに渡すには、 `CREATE PROCEDURE` ステートメントを使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="085c4-109">To pass an `xml` type parameter to a stored procedure, use a `CREATE PROCEDURE` statement, as shown in the following example.</span></span>  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 <span data-ttu-id="085c4-110">XQuery を使用して、列、パラメーター、または変数に格納されている XML インスタンスにクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-110">You can use XQuery to query XML instances stored in columns, parameters, or variables.</span></span> <span data-ttu-id="085c4-111">また、XML DML (データ操作言語) を使用して、XML インスタンスに更新を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="085c4-111">You can also use the XML Data Manipulation Language (XML DML) to apply updates to the XML instances.</span></span> <span data-ttu-id="085c4-112">開発時点では XQuery 標準に XQuery DML が定められていなかったので、XQuery については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML DML (XML データ変更言語) [拡張機能が](/sql/t-sql/xml/xml-data-modification-language-xml-dml) に実装されています。</span><span class="sxs-lookup"><span data-stu-id="085c4-112">Because the XQuery standard did not define XQuery DML at the time of development, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] introduces [XML Data Modification Language](/sql/t-sql/xml/xml-data-modification-language-xml-dml) extensions to XQuery.</span></span> <span data-ttu-id="085c4-113">この拡張機能を使用して、挿入、更新、および削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-113">These extensions allow you to perform insert, update, and delete operations.</span></span>  
  
## <a name="assigning-defaults"></a><span data-ttu-id="085c4-114">既定の XML の割り当て</span><span class="sxs-lookup"><span data-stu-id="085c4-114">Assigning Defaults</span></span>  
 <span data-ttu-id="085c4-115">テーブル内で、`xml` 型の列に、既定の XML インスタンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="085c4-115">In a table, you can assign a default XML instance to a column of `xml` type.</span></span> <span data-ttu-id="085c4-116">既定の XML を割り当てるには、XML 定数を使用する方法と、`xml` 型への明示的なキャストを使用する方法の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="085c4-116">You can provide the default XML in one of two ways: by using an XML constant, or by using an explicit cast to the `xml` type.</span></span>  
  
 <span data-ttu-id="085c4-117">既定の XML を XML 定数として割り当てるには、次の例の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="085c4-117">To provide the default XML as an XML constant, use syntax as shown in the following example.</span></span> <span data-ttu-id="085c4-118">文字列は暗黙的に `xml` 型にキャストされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="085c4-118">Note that the string is implicitly CAST to `xml` type.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 <span data-ttu-id="085c4-119">既定の XML を `CAST` への明示的な `xml`として割り当てるには、次の例の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="085c4-119">To provide the default XML as an explicit `CAST` to `xml`, use syntax as shown in the following example.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="085c4-120">では、`xml` 型の列に対する NULL 制約および NOT NULL 制約もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="085c4-120">also supports NULL and NOT NULL constraints on columns of `xml` type.</span></span> <span data-ttu-id="085c4-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="085c4-121">For example:</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a><span data-ttu-id="085c4-122">制約の指定</span><span class="sxs-lookup"><span data-stu-id="085c4-122">Specifying Constraints</span></span>  
 <span data-ttu-id="085c4-123">`xml` 型の列を作成するときには、列レベルまたはテーブル レベルの制約を定義できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-123">When you create columns of `xml` type, you can define column-level or table-level constraints.</span></span> <span data-ttu-id="085c4-124">制約は、次のような場合に使用してください。</span><span class="sxs-lookup"><span data-stu-id="085c4-124">Use constraints in the following situations:</span></span>  
  
-   <span data-ttu-id="085c4-125">ビジネス ルールが XML スキーマでは表現できない場合。</span><span class="sxs-lookup"><span data-stu-id="085c4-125">Your business rules cannot be expressed in XML schemas.</span></span> <span data-ttu-id="085c4-126">たとえば、花屋の配達可能地域が店舗から 80 km 以内に限られている場合などです。</span><span class="sxs-lookup"><span data-stu-id="085c4-126">For example, the delivery address of a flower shop must be within 50 miles of its business location.</span></span> <span data-ttu-id="085c4-127">このルールは XML 列の制約として記述できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-127">This can be written as a constraint on the XML column.</span></span> <span data-ttu-id="085c4-128">この制約には、`xml` データ型のメソッドが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="085c4-128">The constraint may involve `xml` data type methods.</span></span>  
  
-   <span data-ttu-id="085c4-129">制約が、テーブル内の他の XML 列または XML 以外の列に関係している場合。</span><span class="sxs-lookup"><span data-stu-id="085c4-129">Your constraint involves other XML or non-XML columns in the table.</span></span> <span data-ttu-id="085c4-130">たとえば、XML インスタンスに現れる Customer の ID (`/Customer/@CustId`) が、CustomerID リレーショナル列の値と一致する必要がある場合などです。</span><span class="sxs-lookup"><span data-stu-id="085c4-130">An example is the enforcement of the ID of a Customer (`/Customer/@CustId`) found in an XML instance to match the value in a relational CustomerID column.</span></span>  
  
 <span data-ttu-id="085c4-131">制約は、型指定された `xml` データ型の列にも、型指定されていない  データ型の列にも指定できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-131">You can specify constraints for typed or untyped `xml` data type columns.</span></span> <span data-ttu-id="085c4-132">ただし、制約を指定するとき、 [XML データ型のメソッド](/sql/t-sql/xml/xml-data-type-methods) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="085c4-132">However, you cannot use the [XML data type methods](/sql/t-sql/xml/xml-data-type-methods) when you specify constraints.</span></span> <span data-ttu-id="085c4-133">また、`xml` データ型では次の列およびテーブルの制約はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="085c4-133">Also, note that the `xml` data type does not support the following column and table constraints:</span></span>  
  
-   <span data-ttu-id="085c4-134">PRIMARY KEY/ FOREIGN KEY</span><span class="sxs-lookup"><span data-stu-id="085c4-134">PRIMARY KEY/ FOREIGN KEY</span></span>  
  
-   <span data-ttu-id="085c4-135">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="085c4-135">UNIQUE</span></span>  
  
-   <span data-ttu-id="085c4-136">COLLATE</span><span class="sxs-lookup"><span data-stu-id="085c4-136">COLLATE</span></span>  
  
     <span data-ttu-id="085c4-137">XML では、独自のエンコードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="085c4-137">XML provides its own encoding.</span></span> <span data-ttu-id="085c4-138">照合順序は、文字列型にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="085c4-138">Collations apply to string types only.</span></span> <span data-ttu-id="085c4-139">`xml` データ型は文字列型ではありません。</span><span class="sxs-lookup"><span data-stu-id="085c4-139">The `xml` data type is not a string type.</span></span> <span data-ttu-id="085c4-140">ただし、文字列で表記され、文字列データ型との相互のキャストが可能です。</span><span class="sxs-lookup"><span data-stu-id="085c4-140">However, it does have string representation and allows casting to and from string data types.</span></span>  
  
-   <span data-ttu-id="085c4-141">RULE</span><span class="sxs-lookup"><span data-stu-id="085c4-141">RULE</span></span>  
  
 <span data-ttu-id="085c4-142">制約を使用する代わりに、次の例に示すように、`xml` データ型のメソッドをラップするためのラッパーと呼ばれるユーザー定義関数を作成し、ユーザー定義関数を CHECK 制約を適用して指定します。</span><span class="sxs-lookup"><span data-stu-id="085c4-142">An alternative to using constraints is to create a wrapper, user-defined function to wrap the `xml` data type method and specify user-defined function in the check constraint as shown in the following example.</span></span>  
  
 <span data-ttu-id="085c4-143">次の例では、 `Col2` 列に対して、保存する各 XML インスタンスには `<ProductDescription>` 属性を持つ `ProductID` 要素が必要であるという制約を指定します。</span><span class="sxs-lookup"><span data-stu-id="085c4-143">In the following example, the constraint on `Col2` specifies that each XML instance stored in this column must have a `<ProductDescription>` element that contains a `ProductID` attribute.</span></span> <span data-ttu-id="085c4-144">この制約は、次のユーザー定義関数によって適用されます。</span><span class="sxs-lookup"><span data-stu-id="085c4-144">This constraint is enforced by this user-defined function:</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 <span data-ttu-id="085c4-145">インスタンスの `exist()` 要素に `xml` 属性が含まれる場合、 `1` データ型の `<ProductDescription>` メソッドは `ProductID` を返します。</span><span class="sxs-lookup"><span data-stu-id="085c4-145">Note that the `exist()` method of the `xml` data type returns `1` if the `<ProductDescription>` element in the instance contains the `ProductID` attribute.</span></span> <span data-ttu-id="085c4-146">それ以外の場合は `0`を返します。</span><span class="sxs-lookup"><span data-stu-id="085c4-146">Otherwise, it returns `0`.</span></span>  
  
 <span data-ttu-id="085c4-147">ここで、次のようにして列レベルの制約を定義したテーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-147">Now, you can create a table with a column-level constraint as follows:</span></span>  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 <span data-ttu-id="085c4-148">次の挿入操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="085c4-148">The following insert succeeds:</span></span>  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 <span data-ttu-id="085c4-149">次の挿入操作は制約に違反するため失敗します。</span><span class="sxs-lookup"><span data-stu-id="085c4-149">Because of the constraint, the following insert fails:</span></span>  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a><span data-ttu-id="085c4-150">同じテーブルと別のテーブル</span><span class="sxs-lookup"><span data-stu-id="085c4-150">Same or Different Table</span></span>  
 <span data-ttu-id="085c4-151">`xml`データ型の列は、他のリレーショナル列を含むテーブル、またはメインテーブルとの外部キーリレーションシップを持つ別のテーブルに作成できます。</span><span class="sxs-lookup"><span data-stu-id="085c4-151">An `xml` data type column can be created in a table that contains other relational columns, or in a separate table with a foreign key relationship to a main table.</span></span>  
  
 <span data-ttu-id="085c4-152">`xml`次のいずれかの条件に該当する場合は、同じテーブルにデータ型の列を作成します。</span><span class="sxs-lookup"><span data-stu-id="085c4-152">Create an `xml` data type column in the same table when one of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="085c4-153">XML 列のデータを取得するが、その列に XML インデックスは不要な場合。</span><span class="sxs-lookup"><span data-stu-id="085c4-153">Your application performs data retrieval on the XML column and does not require an XML index on the XML column.</span></span>  
  
-   <span data-ttu-id="085c4-154">`xml` データ型の列に XML インデックスを作成するときに、メイン テーブルの主キーがクラスター化キーと同一である場合。</span><span class="sxs-lookup"><span data-stu-id="085c4-154">You want to build an XML index on the `xml` data type column and the primary key of the main table is the same as its clustering key.</span></span> <span data-ttu-id="085c4-155">詳細については、「[XML インデックス &#40;SQL Server&#41;](xml-indexes-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="085c4-155">For more information, see [XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md).</span></span>  
  
 <span data-ttu-id="085c4-156">次の条件に該当する場合は、別のテーブルに `xml` データ型の列を作成してください。</span><span class="sxs-lookup"><span data-stu-id="085c4-156">Create the `xml` data type column in a separate table if the following conditions are true:</span></span>  
  
-   <span data-ttu-id="085c4-157">`xml` データ型の列に XML インデックスを作成するときに、メイン テーブルの主キーがクラスター化キーと異なる場合、メイン テーブルに主キーがない場合、またはメイン テーブルがヒープである (クラスター化キーがない) 場合。</span><span class="sxs-lookup"><span data-stu-id="085c4-157">You want to build an XML index on the `xml` data type column, but the primary key of the main table is different from its clustering key, or the main table does not have a primary key, or the main table is a heap (no clustering key).</span></span> <span data-ttu-id="085c4-158">メイン テーブルが既に存在する場合、これに該当している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="085c4-158">This may be true if the main table already exists.</span></span>  
  
-   <span data-ttu-id="085c4-159">テーブルに XML 列が存在することでテーブル スキャンが遅くなるのを避ける場合。</span><span class="sxs-lookup"><span data-stu-id="085c4-159">You do not want table scans to slow down because of the presence of the XML column in the table.</span></span> <span data-ttu-id="085c4-160">テーブル スキャンは、XML が行内に保存されていても行外に保存されていても領域を消費します。</span><span class="sxs-lookup"><span data-stu-id="085c4-160">This uses space whether it is stored in-row or out-of-row.</span></span>  
  
  
