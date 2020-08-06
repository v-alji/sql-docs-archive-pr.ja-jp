---
title: XML インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- indexes [XML in SQL Server]
- XML indexes [SQL Server], creating
ms.assetid: 6ecac598-355d-4408-baf7-1b2e8d4cf7c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e7800193222b8c9060fee1b247cc5585654cde4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738059"
---
# <a name="create-xml-indexes"></a><span data-ttu-id="e59f6-102">XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="e59f6-102">Create XML Indexes</span></span>
  <span data-ttu-id="e59f6-103">このトピックでは、プライマリ XML インデックスとセカンダリ XML インデックスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-103">This topic describes how to create primary and secondary XML indexes.</span></span>  
  
## <a name="creating-a-primary-xml-index"></a><span data-ttu-id="e59f6-104">プライマリ XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="e59f6-104">Creating a Primary XML Index</span></span>  
 <span data-ttu-id="e59f6-105">プライマリ XML インデックスを作成するには、[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-105">To create a primary XML index, use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement.</span></span> <span data-ttu-id="e59f6-106">XML インデックスでは、XML 以外のインデックスで使用できるオプションの一部しかサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-106">Not all options available for non-XML indexes are supported on XML indexes.</span></span>  
  
 <span data-ttu-id="e59f6-107">XML インデックスの作成時には、次の事項に注意します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-107">Note the following when you are creating an XML index:</span></span>  
  
-   <span data-ttu-id="e59f6-108">プライマリ XML インデックスを作成するには、インデックスが作成される XML 列を含んだベース テーブルと呼ばれるテーブルの主キーに、クラスター化インデックスが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-108">To create a primary XML index, the table that contains the XML column being indexed, called the base table, must have a clustered index on the primary key.</span></span> <span data-ttu-id="e59f6-109">これにより、ベース テーブルをパーティション分割した場合に、同じパーティション構成とパーティション関数を使用してプライマリ XML インデックスがパーティション分割されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-109">This makes sure that if the base table is partitioned, the primary XML index can be partitioned by using the same partitioning scheme and partitioning function.</span></span>  
  
-   <span data-ttu-id="e59f6-110">XML インデックスが存在する場合は、テーブルのクラスター化主キーを変更できません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-110">If an XML index exists, the clustered, primary key of the table cannot be modified.</span></span> <span data-ttu-id="e59f6-111">主キーを変更する前に、テーブルのすべての XML インデックスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-111">You will have to drop all XML indexes on the table before modifying the primary key.</span></span>  
  
-   <span data-ttu-id="e59f6-112">プライマリ XML インデックスは、1 つの `xml` 型の列に作成できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-112">A primary XML index can be created on a single `xml` type column.</span></span> <span data-ttu-id="e59f6-113">キー列の XML 型の列には他の型のインデックスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-113">You cannot create any other type of index with the XML type column as a key column.</span></span> <span data-ttu-id="e59f6-114">ただし、XML 以外のインデックスに `xml` 型の列を含めることはできます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-114">However, you can include the `xml` L type column in a non-XML index.</span></span> <span data-ttu-id="e59f6-115">テーブル内の各 `xml` 型列には、それぞれ独自のプライマリ XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-115">Each `xml` type column in a table can have its own primary XML index.</span></span> <span data-ttu-id="e59f6-116">ただし、各 `xml` 型列に作成できるプライマリ XML インデックスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="e59f6-116">However, only one primary XML index per `xml` type column is permitted.</span></span>  
  
-   <span data-ttu-id="e59f6-117">XML インデックスは、XML 以外のインデックスと同じ名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-117">XML indexes exist in the same namespace as non-XML indexes.</span></span> <span data-ttu-id="e59f6-118">したがって、同じテーブルでは、XML インデックスと XML 以外のインデックスを同じ名前で作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-118">Therefore, you cannot have an XML index and a non-XML index on the same table with the same name.</span></span>  
  
-   <span data-ttu-id="e59f6-119">IGNORE_DUP_KEY オプションと ONLINE オプションは、XML インデックスでは常に OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-119">IGNORE_DUP_KEY and ONLINE options of are always set to OFF for XML indexes.</span></span> <span data-ttu-id="e59f6-120">これらのオプションを値 OFF で指定できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-120">You can specify these options with a value of OFF.</span></span>  
  
-   <span data-ttu-id="e59f6-121">ユーザー テーブルのファイル グループ情報またはパーティション分割情報が XML インデックスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-121">The filegroup or partitioning information of the user table is applied to the XML index.</span></span> <span data-ttu-id="e59f6-122">ユーザーは、これらの情報を XML インデックスで別々に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-122">Users cannot specify these separately on an XML index.</span></span>  
  
-   <span data-ttu-id="e59f6-123">DROP_EXISTING インデックス オプションを使用すると、プライマリ XML インデックスを削除して新しい XML インデックスを作成することや、セカンダリ XML インデックスを削除して新しいセカンダリ XML インデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-123">The DROP_EXISTING index option can drop a primary XML index and create a new primary XML index, or drop a secondary XML index and create a new secondary XML index.</span></span> <span data-ttu-id="e59f6-124">ただし、このインデックス オプションを使用して、セカンダリ XML インデックスを削除して新しいプライマリ XML インデックスを作成することや、プライマリ XML インデックスを削除して新しいセカンダリ XML インデックスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-124">However, this option cannot drop a secondary XML index to create a new primary XML index or vice versa.</span></span>  
  
-   <span data-ttu-id="e59f6-125">プライマリ XML インデックスの名前にはビュー名と同じ制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-125">Primary XML index names have the same restrictions as view names.</span></span>  
  
 <span data-ttu-id="e59f6-126">ビューの型の列、型の `xml` 列を持つ**テーブル**値変数 `xml` 、または型の変数に XML インデックスを作成することはできません `xml` 。</span><span class="sxs-lookup"><span data-stu-id="e59f6-126">You cannot create an XML index on an `xml` type column in a view, on a **table** valued variable with `xml` type columns, or `xml` type variables.</span></span>  
  
-   <span data-ttu-id="e59f6-127">ALTER TABLE ALTER COLUMN オプションを使用して、`xml` 型の列を型指定されていない XML から型指定された XML に変更する場合、またはその逆の変更を行う場合は、その列に XML インデックスが存在してはいけません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-127">To change an `xml` type column from untyped to typed XML, or vice versa, by using the ALTER TABLE ALTER COLUMN option, no XML index on the column should exist.</span></span> <span data-ttu-id="e59f6-128">XML インデックスが存在する場合は、列の型を変更する前にその XML インデックスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-128">If one does exist, it must be dropped before the column type change is tried.</span></span>  
  
-   <span data-ttu-id="e59f6-129">XML インデックスを作成する場合は、ARITHABORT オプションが ON に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-129">The option ARITHABORT must be set to ON when an XML index is created.</span></span> <span data-ttu-id="e59f6-130">XML データ型メソッドを使用して XML 列内の値のクエリ、挿入、削除、または更新を行うには、同じオプションがその接続に設定される必要があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-130">To query, insert, delete, or update values in the XML column using XML data type methods, the same option must be set on the connection.</span></span> <span data-ttu-id="e59f6-131">異なるオプションが設定された場合、XML データ型のメソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-131">If it is not, the XML data type methods will fail.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e59f6-132">XML インデックスについての情報は、カタログ ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-132">Information about an XML index can be found in catalog views.</span></span> <span data-ttu-id="e59f6-133">ただし、 **sp_helpindex** はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e59f6-133">However, **sp_helpindex** is not supported.</span></span> <span data-ttu-id="e59f6-134">このトピックの後半に示す例では、カタログ ビューにクエリを実行して XML インデックスの情報を参照する方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="e59f6-134">Examples provided later in this topic show how to query the catalog views to find XML index information.</span></span>  
  
 <span data-ttu-id="e59f6-135">**以降のバージョンでは、プライマリ XML インデックスを作成または再作成する XML データ型の列に、XML スキーマ型** xs:date **または** xs:dateTime [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (またはこれらのサブタイプ) で 1 未満の年の値が含まれていると、インデックスの作成が失敗します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-135">When creating or recreating a primary XML index on an XML data type column that contains values of the XML Schema types **xs:date** or **xs:dateTime** (or any subtypes of these types) that have a year of less than 1, the index creation will fail in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="e59f6-136">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ではこれらの値が許可されていたため、この問題は、生成されたデータベースでインデックスを作成する際に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-136">allowed these values, so this problem can occur when creating indexes in a database generated in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e59f6-137">詳細については、「 [型指定された XML と型指定されていない XML の比較](../xml/compare-typed-xml-to-untyped-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e59f6-137">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
### <a name="example-creating-a-primary-xml-index"></a><span data-ttu-id="e59f6-138">例:プライマリ XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="e59f6-138">Example: Creating a Primary XML Index</span></span>  
 <span data-ttu-id="e59f6-139">ここからはほとんどの例で、型指定されていない XML 列を含んだテーブル T (pk INT PRIMARY KEY, xCol XML) を使用します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-139">Table T (pk INT PRIMARY KEY, xCol XML) with an untyped XML column is used in most of the examples.</span></span> <span data-ttu-id="e59f6-140">XML 列は、型指定された XML に簡単に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-140">These can be extended to typed XML in a straightforward way.</span></span> <span data-ttu-id="e59f6-141">説明を簡単にするため、次に示す XML データ インスタンスに対するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-141">For simplicity, queries are described for XML data instances as shown in the following:</span></span>  
  
```  
<book genre="security" publicationdate="2002" ISBN="0-7356-1588-2">  
   <title>Writing Secure Code</title>  
   <author>  
      <first-name>Michael</first-name>  
      <last-name>Howard</last-name>  
   </author>  
   <author>  
      <first-name>David</first-name>  
      <last-name>LeBlanc</last-name>  
   </author>  
   <price>39.99</price>  
</book>  
```  
  
 <span data-ttu-id="e59f6-142">次のステートメントを実行すると、テーブル T の XML 列 xCol に idx_xCol という XML インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-142">The following statement creates an XML index, called idx_xCol, on the XML column xCol of table T:</span></span>  
  
```  
CREATE PRIMARY XML INDEX idx_xCol on T (xCol)  
```  
  
## <a name="creating-a-secondary-xml-index"></a><span data-ttu-id="e59f6-143">セカンダリ XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="e59f6-143">Creating a Secondary XML Index</span></span>  
 <span data-ttu-id="e59f6-144">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL ステートメントを使用して、セカンダリ XML インデックスを作成したり、必要なセカンダリ XML インデックスの種類を指定したりします。</span><span class="sxs-lookup"><span data-stu-id="e59f6-144">Use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement to create secondary XML indexes and specify the type of the secondary XML index that you want.</span></span>  
  
 <span data-ttu-id="e59f6-145">セカンダリ XML インデックスの作成時には、次の事項に注意します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-145">Note the following when you are creating secondary XML indexes:</span></span>  
  
-   <span data-ttu-id="e59f6-146">IGNORE_DUP_KEY と ONLINE を除き、非クラスター化インデックスに適用されるすべてのオプションをセカンダリ XML インデックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-146">All indexing options that apply to a nonclustered index, except IGNORE_DUP_KEY and ONLINE, are permitted on secondary XML indexes.</span></span> <span data-ttu-id="e59f6-147">例外の 2 つのオプションは、セカンダリ XML インデックスでは常に OFF に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e59f6-147">The two options must always be set to OFF for secondary XML indexes.</span></span>  
  
-   <span data-ttu-id="e59f6-148">セカンダリ XML インデックスは、プライマリ XML インデックスと同様にパーティション分割されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-148">The secondary indexes are partitioned just like the primary XML index.</span></span>  
  
-   <span data-ttu-id="e59f6-149">DROP_EXISTING を使用すると、ユーザー テーブルのセカンダリ XML インデックスを削除し、そのユーザー テーブルに別のセカンダリ XML インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-149">DROP_EXISTING can drop a secondary index on the user table and create another secondary index on the user table.</span></span>  
  
 <span data-ttu-id="e59f6-150">**sys.xml_indexes** カタログ ビューにクエリを実行して XML インデックス情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-150">You can query the **sys.xml_indexes** catalog view to retrieve XML index information.</span></span> <span data-ttu-id="e59f6-151">**sys.xml_indexes** カタログ ビューの **secondary_type_desc** 列には、セカンダリ インデックスの種類が示されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-151">Note that the **secondary_type_desc** column in the **sys.xml_indexes** catalog view provides the type of secondary index:</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="e59f6-152">**secondary_type_desc** 列に返される値は、NULL、PATH、VALUE、または PROPERTY です。</span><span class="sxs-lookup"><span data-stu-id="e59f6-152">The values returned in the **secondary_type_desc** column can be NULL, PATH, VALUE, or PROPERTY.</span></span> <span data-ttu-id="e59f6-153">プライマリ XML インデックスの場合、返される値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="e59f6-153">For the primary XML index, the value returned is NULL.</span></span>  
  
### <a name="example-creating-secondary-xml-indexes"></a><span data-ttu-id="e59f6-154">例: セカンダリ XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="e59f6-154">Example: Creating Secondary XML Indexes</span></span>  
 <span data-ttu-id="e59f6-155">次の例では、セカンダリ XML インデックスの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-155">The following example illustrates how secondary XML indexes are created.</span></span> <span data-ttu-id="e59f6-156">また、作成した XML インデックスに関する情報も示します。</span><span class="sxs-lookup"><span data-stu-id="e59f6-156">The example also shows information about the XML indexes that you created.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML);  
GO  
-- Create primary index.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol);  
GO  
-- Create secondary indexes (PATH, VALUE, PROPERTY).  
CREATE XML INDEX PIdx_T_XmlCol_PATH ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PATH;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_VALUE ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR VALUE;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_PROPERTY ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PROPERTY;  
GO  
```  
  
 <span data-ttu-id="e59f6-157">`sys.xml_indexes` に対するクエリを実行して XML インデックス情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-157">You can query the `sys.xml_indexes` to retrieve XML indexes information.</span></span> <span data-ttu-id="e59f6-158">`secondary_type_desc` 列からは、セカンダリ インデックスの種類が提供されます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-158">The `secondary_type_desc` column provides the secondary index type.</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="e59f6-159">次のように、カタログ ビューに対するクエリを実行してインデックス情報を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-159">You can also query the catalog view for index information.</span></span>  
  
```  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T');  
```  
  
 <span data-ttu-id="e59f6-160">次のように、サンプル データを追加した後で、XML インデックス情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e59f6-160">You can add sample data and then review the XML index information.</span></span>  
  
```  
INSERT INTO T VALUES (1,  
'<doc id="123">  
<sections>  
<section num="2">  
<heading>Background</heading>  
</section>  
<section num="3">  
<heading>Sort</heading>  
</section>  
<section num="4">  
<heading>Search</heading>  
</section>  
</sections>  
</doc>');  
GO  
-- Check XML index information.  
SELECT *  
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, NULL, 'DETAILED');  
GO  
-- Space usage of primary XML index  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id  
FROM    sys.xml_indexes i   
WHERE   i.name = 'PIdx_T_XmlCol' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
--- Space usage of secondary XML index (for example PATH secondary index)  PIdx_T_XmlCol_PATH  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id   
FROM    sys.xml_indexes i   
WHERE  i.name = 'PIdx_T_XmlCol_PATH' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
  
-- Space usage of all secondary XML indexes for a particular table  
SELECT i.name, object_name(i.object_id), stats.*   
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, DEFAULT, 'DETAILED') stats  
JOIN sys.xml_indexes i ON (stats.object_id = i.object_id and stats.index_id = i.index_id)  
WHERE secondary_type is not null;  
-- Drop secondary indexes.  
DROP INDEX PIdx_T_XmlCol_PATH ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_VALUE ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_PROPERTY ON T;  
GO  
-- Drop primary index.  
DROP INDEX PIdx_T_XmlCol ON T;  
-- Drop table T.  
DROP TABLE T;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="e59f6-161">参照</span><span class="sxs-lookup"><span data-stu-id="e59f6-161">See Also</span></span>  
 <span data-ttu-id="e59f6-162">[XML インデックス &#40;SQL Server&#41;](xml-indexes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e59f6-162">[XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md) </span></span>  
 [<span data-ttu-id="e59f6-163">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e59f6-163">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
