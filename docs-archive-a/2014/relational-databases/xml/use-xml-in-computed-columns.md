---
title: 計算列での XML の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
author: rothja
ms.author: jroth
ms.openlocfilehash: 33a7549823dc3e4a23cecfa97d7345a6421cb1b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711766"
---
# <a name="use-xml-in-computed-columns"></a><span data-ttu-id="895d2-102">計算列での XML の使用</span><span class="sxs-lookup"><span data-stu-id="895d2-102">Use XML in Computed Columns</span></span>
  <span data-ttu-id="895d2-103">XML インスタンスは、計算列のソースとして、または計算列の一種として使用できます。</span><span class="sxs-lookup"><span data-stu-id="895d2-103">XML instances can appear as a source for a computed column, or as a type of computed column.</span></span> <span data-ttu-id="895d2-104">このトピックでは、計算列で XML を使用する方法を示す例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="895d2-104">The examples in this topic show how to use XML with computed columns.</span></span>  
  
## <a name="creating-computed-columns-from-xml-columns"></a><span data-ttu-id="895d2-105">XML 列から計算列を作成する</span><span class="sxs-lookup"><span data-stu-id="895d2-105">Creating Computed Columns from XML Columns</span></span>  
 <span data-ttu-id="895d2-106">次の `CREATE TABLE` ステートメントでは、 `xml` から`col2`型の列 ( `col1`) を計算しています。</span><span class="sxs-lookup"><span data-stu-id="895d2-106">In the following `CREATE TABLE` statement, an `xml` type column (`col2`) is computed from `col1`:</span></span>  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 <span data-ttu-id="895d2-107">次の `xml` ステートメントで示すように、 `CREATE TABLE` データ型は計算列を作成するときのソースとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="895d2-107">The `xml` data type can also appear as a source in creating a computed column, as shown in the following `CREATE TABLE` statement:</span></span>  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 <span data-ttu-id="895d2-108">次の例に示すように、 `xml` 型の列から値を抽出して計算列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="895d2-108">You can create a computed column by extracting a value from an `xml` type column as shown in the following example.</span></span> <span data-ttu-id="895d2-109">計算列を作成するときは `xml` データ型のメソッドを直接使用できません。そのため、この例では XML インスタンスの値を返す関数 (`my_udf`) をまず定義しています。</span><span class="sxs-lookup"><span data-stu-id="895d2-109">Because the `xml` data type methods cannot be used directly in creating computed columns, the example first defines a function (`my_udf`) that returns a value from an XML instance.</span></span> <span data-ttu-id="895d2-110">この関数には、 `value()` 型の `xml` メソッドがラップされています。</span><span class="sxs-lookup"><span data-stu-id="895d2-110">The function wraps the `value()` method of the `xml` type.</span></span> <span data-ttu-id="895d2-111">`CREATE TABLE` ステートメントで、この関数名が計算列の代わりに指定されています。</span><span class="sxs-lookup"><span data-stu-id="895d2-111">The function name is then specified in the `CREATE TABLE` statement for the computed column.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 <span data-ttu-id="895d2-112">上記の例と同様に、次の例では計算列用に `xml` 型のインスタンスを返す関数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="895d2-112">As in the previous example, the following example defines a function to return an `xml` type instance for a computed column.</span></span> <span data-ttu-id="895d2-113">関数内では、 `query()` データ型の `xml` メソッドにより `xml` 型のパラメーターの値を取得しています。</span><span class="sxs-lookup"><span data-stu-id="895d2-113">Inside the function, the `query()` method of the `xml` data type retrieves a value from an `xml` type parameter.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 <span data-ttu-id="895d2-114">次の `CREATE TABLE` ステートメントの `Col2` は、関数が返した XML データ (`<Features>` 要素) を使用する計算列です。</span><span class="sxs-lookup"><span data-stu-id="895d2-114">In the following `CREATE TABLE` statement, `Col2` is a computed column that uses the XML data (`<Features>` element) that is returned by the function:</span></span>  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a><span data-ttu-id="895d2-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="895d2-115">In This Section</span></span>  
  
|<span data-ttu-id="895d2-116">トピック</span><span class="sxs-lookup"><span data-stu-id="895d2-116">Topic</span></span>|<span data-ttu-id="895d2-117">説明</span><span class="sxs-lookup"><span data-stu-id="895d2-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="895d2-118">計算列を使用した使用頻度の高い XML 値の昇格</span><span class="sxs-lookup"><span data-stu-id="895d2-118">Promote Frequently Used XML Values with Computed Columns</span></span>](promote-frequently-used-xml-values-with-computed-columns.md)|<span data-ttu-id="895d2-119">計算列やプロパティ テーブルでプロパティの昇格を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="895d2-119">Describes how to use property promotion with computed columns and property tables.</span></span>|  
  
  
