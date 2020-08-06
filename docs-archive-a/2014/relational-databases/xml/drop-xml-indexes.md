---
title: XML インデックスの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- dropping indexes
- XML indexes [SQL Server], dropping
ms.assetid: 7591ebea-34af-4925-8553-b2adb5b487c2
author: rothja
ms.author: jroth
ms.openlocfilehash: b7d4621cf2182b4587b12665a1cfe10ddbe0db3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631690"
---
# <a name="drop-xml-indexes"></a><span data-ttu-id="4cf56-102">XML インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="4cf56-102">Drop XML Indexes</span></span>
  <span data-ttu-id="4cf56-103">[DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用すると、XML インデックスと XML 以外のインデックスの両方を含め、既存のプライマリ インデックスまたはセカンダリ インデックスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="4cf56-103">The [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be used to drop existing primary or secondary XML and non-XML indexes.</span></span> <span data-ttu-id="4cf56-104">ただし、DROP INDEX のオプションは XML インデックスに適用されません。</span><span class="sxs-lookup"><span data-stu-id="4cf56-104">However, no options of DROP INDEX apply to XML indexes.</span></span> <span data-ttu-id="4cf56-105">プライマリ XML インデックスを削除すると、存在するセカンダリ XML インデックスもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="4cf56-105">If you drop the primary XML index, any secondary indexes that are present are also deleted.</span></span>  
  
 <span data-ttu-id="4cf56-106">*TableName.IndexName* を指定する DROP 構文は廃止されるので、XML インデックスではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="4cf56-106">The DROP syntax with *TableName.IndexName* is being phased out and is not supported for XML indexes.</span></span>  
  
## <a name="example-creating-and-dropping-a-primary-xml-index"></a><span data-ttu-id="4cf56-107">例: プライマリ XML インデックスの作成とドロップ</span><span class="sxs-lookup"><span data-stu-id="4cf56-107">Example: Creating and Dropping a Primary XML Index</span></span>  
 <span data-ttu-id="4cf56-108">次の例では、`xml` 型の列に XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cf56-108">In the following example, an XML index is created on an `xml` type column.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create Primary XML index   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Verify the index creation.   
-- Note index type is 3 for xml indexes.  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'   
-- Drop the index.  
DROP INDEX PIdx_T_XmlCol ON T  
```  
  
 <span data-ttu-id="4cf56-109">テーブルを削除すると、テーブルのすべての XML インデックスも自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="4cf56-109">When a table is dropped, all the XML indexes on it are also automatically dropped.</span></span> <span data-ttu-id="4cf56-110">ただし、XML 列に XML インデックスが存在する場合、その XML 列はテーブルから削除できません。</span><span class="sxs-lookup"><span data-stu-id="4cf56-110">However, an XML column cannot be dropped from a table if an XML index exists on the column.</span></span>  
  
 <span data-ttu-id="4cf56-111">次の例では、`xml` 型の列に XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cf56-111">In the following example, an XML index is created on an `xml` type column.</span></span> <span data-ttu-id="4cf56-112">詳細については、「 [型指定された XML と型指定されていない XML の比較](../xml/compare-typed-xml-to-untyped-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cf56-112">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
```  
CREATE TABLE TestTable(  
 Col1 int primary key,   
 Col2 xml (Production.ProductDescriptionSchemaCollection))   
GO  
```  
  
 <span data-ttu-id="4cf56-113">これで次のように、 `Co12`にプライマリ XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4cf56-113">Now, you can create a primary XML index on `Co12`.</span></span>  
  
```  
CREATE PRIMARY XML INDEX PIdx_TestTable_Col2   
ON TestTable(Col2)  
GO  
```  
  
## <a name="example-creating-an-xml-index-by-using-the-drop_existing-index-option"></a><span data-ttu-id="4cf56-114">例: DROP_EXISTING インデックス オプションを使用した XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="4cf56-114">Example: Creating an XML Index by Using the DROP_EXISTING Index Option</span></span>  
 <span data-ttu-id="4cf56-115">次の例では、列 (`XmlColx`) に XML インデックスを作成しています。</span><span class="sxs-lookup"><span data-stu-id="4cf56-115">In the following example, an XML index is created on a column (`XmlColx`).</span></span> <span data-ttu-id="4cf56-116">次に、同じ名前を使用して異なる列 (`XmlColy`) に別の XML インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cf56-116">Then, another XML index with the same name is created on a different column, (`XmlColy`).</span></span> <span data-ttu-id="4cf56-117">`DROP_EXISTING` を指定しているので、列 (`XmlColx)` の既存の XML インデックスが削除されて、列 (`XmlColy`) に新しい XML インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4cf56-117">Because the `DROP_EXISTING` option is specified, the existing XML index on (`XmlColx)` is dropped and a new XML index on (`XmlColy`) is created.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T(Col1 int primary key, XmlColx xml, XmlColy xml)  
GO  
-- Create XML index on XmlColx.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColx)  
GO  
-- Create same name XML index on XmlColy.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColy)   
WITH (DROP_EXISTING = ON)  
-- Verify the index is created on XmlColy.d.  
SELECT sc.name   
FROM   sys.xml_indexes si inner join sys.index_columns sic   
ON     sic.object_id=si.object_id and sic.index_id=si.index_id  
INNER  join sys.columns sc on sc.object_id=sic.object_id   
AND    sc.column_id=sic.column_id  
WHERE  si.name='PIdx_T_XmlCol'   
AND    si.object_id=object_id('T')  
```  
  
 <span data-ttu-id="4cf56-118">このクエリからは、指定した XML インデックスを作成する対象の列名が返されます。</span><span class="sxs-lookup"><span data-stu-id="4cf56-118">This query returns the column name on which the specified XML index is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf56-119">参照</span><span class="sxs-lookup"><span data-stu-id="4cf56-119">See Also</span></span>  
 [<span data-ttu-id="4cf56-120">XML インデックス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf56-120">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
