---
title: FOR XML クエリの TYPE ディレクティブ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
author: rothja
ms.author: jroth
ms.openlocfilehash: cddce90718ef5edfcf161ddc6cc52b617825a2e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645413"
---
# <a name="type-directive-in-for-xml-queries"></a><span data-ttu-id="a53ef-102">FOR XML クエリの TYPE ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="a53ef-102">TYPE Directive in FOR XML Queries</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="a53ef-103">[xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)のサポートにより、必要に応じて、type ディレクティブを指定することにより、for xml クエリの結果をデータ型として返すように要求でき `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-103">support for the [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql) enables you to optionally request that the result of a FOR XML query be returned as `xml` data type by specifying the TYPE directive.</span></span> <span data-ttu-id="a53ef-104">これにより、サーバーで FOR XML クエリの結果を処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a53ef-104">This allows you to process the result of a FOR XML query on the server.</span></span> <span data-ttu-id="a53ef-105">たとえば、XQuery を指定したり、その結果を `xml` 型の変数に割り当てたり、[入れ子になった FOR XML クエリ](use-nested-for-xml-queries.md)を記述したりできます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-105">For example, you can specify an XQuery against it, assign the result to an `xml` type variable, or write [Nested FOR XML queries](use-nested-for-xml-queries.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a53ef-106">は、TYPE ディレクティブを使用した FOR XML クエリなど、サーバーでのさまざまな構成の結果として、または SQL テーブルの列および出力パラメーターの XML インスタンス データ値を返すために `xml` データ型が使用された場合に、XML データ型のインスタンス データをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-106">returns XML data type instance data to the client as a result of different server-constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML instance data values from SQL table columns and output parameters.</span></span> <span data-ttu-id="a53ef-107">クライアント アプリケーション コードでは、ADO.NET プロバイダーが、この XML データ型の情報をサーバーからバイナリ エンコードで送信するように要求します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-107">In client application code, the ADO.NET provider requests this XML data type information to be sent in a binary encoding from the server.</span></span> <span data-ttu-id="a53ef-108">ただし、TYPE ディレクティブを指定せずに FOR XML を使用した場合、この XML データは文字列型として返されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-108">However, if you are using FOR XML without the TYPE directive, the XML data comes back as a string type.</span></span> <span data-ttu-id="a53ef-109">どんな場合でも、クライアント プロバイダーは常にいずれかの形式の XML を処理できます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-109">In any case, the client provider will always be able to handle either form of XML.</span></span> <span data-ttu-id="a53ef-110">TYPE ディレクティブを指定していない最上位レベルでの FOR XML 句は、カーソルと共に使用できません。</span><span class="sxs-lookup"><span data-stu-id="a53ef-110">Note that top-level FOR XML without the TYPE directive cannot be used with cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a53ef-111">例</span><span class="sxs-lookup"><span data-stu-id="a53ef-111">Examples</span></span>  
 <span data-ttu-id="a53ef-112">次の例は、FOR XML クエリでの TYPE ディレクトリの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a53ef-112">The following examples illustrate the use of the TYPE directive with FOR XML queries.</span></span>  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a><span data-ttu-id="a53ef-113">FOR XML クエリの結果の xml 型としての取得</span><span class="sxs-lookup"><span data-stu-id="a53ef-113">Retrieving FOR XML query results as xml type</span></span>  
 <span data-ttu-id="a53ef-114">次のクエリでは、 `Contacts` テーブルから顧客の連絡先に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-114">The following query retrieves customer contact information from the `Contacts` table.</span></span> <span data-ttu-id="a53ef-115">`TYPE` に `FOR XML` ディレクティブが指定されているので、結果は `xml` 型として返されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-115">Because the `TYPE` directive is specified in `FOR XML`, the result is returned as `xml` type.</span></span>  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="a53ef-116">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-116">This is the partial result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a><span data-ttu-id="a53ef-117">FOR XML クエリ結果の xml 型の変数への代入</span><span class="sxs-lookup"><span data-stu-id="a53ef-117">Assigning FOR XML query results to an xml type variable</span></span>  
 <span data-ttu-id="a53ef-118">次の例では、FOR XML の結果が `xml` 型の変数 `@x` に代入されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-118">In the following example, a FOR XML result is assigned to an `xml` type variable, `@x`.</span></span> <span data-ttu-id="a53ef-119">クエリでは、 `BusinessEntityID` の列から、、、 `FirstName` `LastName` 、追加の電話番号などの連絡先情報を取得し `AdditionalContactInfo` `xml``TYPE` ます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-119">The query retrieves contact information, such as the `BusinessEntityID`, `FirstName`, `LastName`, and additional telephone numbers, from the `AdditionalContactInfo` column of `xml``TYPE`.</span></span> <span data-ttu-id="a53ef-120">`FOR XML` 句に `TYPE` ディレクティブを指定するので、この XML は `xml` 型として返され、変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-120">Because the `FOR XML` clause specifies `TYPE` directive, the XML is returned as `xml` type and is assigned to a variable.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a><span data-ttu-id="a53ef-121">FOR XML クエリの結果のクエリ</span><span class="sxs-lookup"><span data-stu-id="a53ef-121">Querying results of a FOR XML query</span></span>  
 <span data-ttu-id="a53ef-122">FOR XML クエリにより、XML が返されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-122">The FOR XML queries return XML.</span></span> <span data-ttu-id="a53ef-123">したがって、FOR XML クエリにより返された XML 結果には、`xml` や `query()` などの `value()` 型のメソッドを適用できます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-123">Therefore, you can apply `xml` type methods, such as `query()` and `value()`, to the XML result returned by FOR XML queries.</span></span>  
  
 <span data-ttu-id="a53ef-124">次のクエリでは、`xml` データ型の `query()` メソッドを使用して、`FOR XML` クエリの結果にクエリします。</span><span class="sxs-lookup"><span data-stu-id="a53ef-124">In the following query, the `query()` method of the `xml` data type is used to query the result of the `FOR XML` query.</span></span> <span data-ttu-id="a53ef-125">詳細については、「[クエリ&#40;&#41; メソッド &#40;xml データ型&#41;](/sql/t-sql/xml/query-method-xml-data-type)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a53ef-125">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 <span data-ttu-id="a53ef-126">内側の `SELECT ... FOR XML` クエリにより `xml` 型の結果が返され、外側の `SELECT` によりその `xml` 型の結果に `query()` メソッドが適用されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-126">The inner `SELECT ... FOR XML` query returns an `xml` type result to which the outer `SELECT` applies the `query()` method to the `xml` type.</span></span> <span data-ttu-id="a53ef-127">`TYPE` ディレクティブが指定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a53ef-127">Note the `TYPE` directive specified.</span></span>  
  
 <span data-ttu-id="a53ef-128">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-128">This is the result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 <span data-ttu-id="a53ef-129">次のクエリでは、`xml` データ型の `value()` メソッドを使用して、`SELECT...FOR XML` クエリにより返された XML 結果から値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-129">In the following query, the `value()` method of the `xml` data type is used to retrieve a value from the XML result returned by the `SELECT...FOR XML` query.</span></span> <span data-ttu-id="a53ef-130">詳細については、「[value&#40;&#41; メソッド &#40;xml データ型&#41;](/sql/t-sql/xml/value-method-xml-data-type)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a53ef-130">For more information, see [value&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 <span data-ttu-id="a53ef-131">`value()` メソッドの XQuery パス式により、 `BusinessEntityID` が `1`の顧客の連絡先から 1 つ目の電話番号が取得されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-131">The XQuery path expression in the `value()` method retrieves the first telephone number of a customer contact whose `BusinessEntityID` is `1`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a53ef-132">TYPE ディレクティブを指定しなかった場合、この FOR XML クエリの結果は `nvarchar(max)` 型として返されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-132">If the TYPE directive is not specified, the FOR XML query result is returned as type `nvarchar(max)`.</span></span>  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a><span data-ttu-id="a53ef-133">INSERT、UPDATE、および DELETE (Transact-SQL DML) での FOR XML クエリの結果の使用</span><span class="sxs-lookup"><span data-stu-id="a53ef-133">Using FOR XML query results in INSERT, UPDATE, and DELETE (Transact-SQL DML)</span></span>  
 <span data-ttu-id="a53ef-134">次の例では、FOR XML クエリをデータ操作言語 (DML) ステートメントで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a53ef-134">The following example demonstrates how FOR XML queries can be used in Data Manipulation Language (DML) statements.</span></span> <span data-ttu-id="a53ef-135">この例では、`FOR XML` により `xml` 型のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-135">In the example, the `FOR XML` returns an instance of `xml` type.</span></span> <span data-ttu-id="a53ef-136">また、 `INSERT` ステートメントによりこの XML がテーブルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="a53ef-136">The `INSERT` statement inserts this XML into a table.</span></span>  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a53ef-137">参照</span><span class="sxs-lookup"><span data-stu-id="a53ef-137">See Also</span></span>  
 [<span data-ttu-id="a53ef-138">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a53ef-138">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
