---
title: XML スキーマ コレクション (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- xml_schema_namespace function
- XML schema collections [SQL Server], about XML schema collections
- metadata [SQL Server], XML schema collections
- queries [XML in SQL Server], XML schema collections
- schema collections [SQL Server]
- schemas [SQL Server], XML
- XML [SQL Server], schema collections
- XML schema collections [SQL Server]
- schema collections [SQL Server], about XML schema collections
ms.assetid: 659d41aa-ccec-4554-804a-722a96ef25c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee4757f1353278447ee55e97c8d4ba23aa2d649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642637"
---
# <a name="xml-schema-collections-sql-server"></a><span data-ttu-id="04e6f-102">XML スキーマ コレクション (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="04e6f-102">XML Schema Collections (SQL Server)</span></span>
  <span data-ttu-id="04e6f-103">「 [Xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)」で説明したように、SQL Server は、データ型を使用して xml データのネイティブストレージを提供し `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-103">As described in the topic, [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql), SQL Server provides native storage of XML data through the `xml` data type.</span></span> <span data-ttu-id="04e6f-104">必要に応じて、 `xml` XML スキーマコレクションを使用して、XSD スキーマを型の変数または列に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-104">You can optionally associate XSD schemas with a variable or a column of `xml` type through an XML schema collection.</span></span> <span data-ttu-id="04e6f-105">XML スキーマ コレクションにはインポートした XML スキーマが格納され、その後このコレクションを次の操作に使用します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-105">The XML schema collection stores the imported XML schemas and is then used to do the following:</span></span>  
  
-   <span data-ttu-id="04e6f-106">XML インスタンスの検証</span><span class="sxs-lookup"><span data-stu-id="04e6f-106">Validate XML instances</span></span>  
  
-   <span data-ttu-id="04e6f-107">XML データをデータベースに格納するときの型指定</span><span class="sxs-lookup"><span data-stu-id="04e6f-107">Type the XML data as it is stored in the database</span></span>  
  
 <span data-ttu-id="04e6f-108">XML スキーマ コレクションは、データベース内のテーブルに似たメタデータ エンティティです。</span><span class="sxs-lookup"><span data-stu-id="04e6f-108">Note that the XML schema collection is a metadata entity like a table in the database.</span></span> <span data-ttu-id="04e6f-109">XML スキーマ コレクションは作成、変更、削除できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-109">You can create, modify, and drop them.</span></span> <span data-ttu-id="04e6f-110">[CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) ステートメントで指定されたスキーマが、新しく作成される XML スキーマ コレクション オブジェクトに自動的にインポートされます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-110">Schemas specified in a [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) statement are automatically imported into the newly created XML schema collection object.</span></span> <span data-ttu-id="04e6f-111">[ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) ステートメントを使用して、追加のスキーマやスキーマ コンポーネントをデータベース内の既存のコレクション オブジェクトにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-111">You can import additional schemas or schema components into an existing collection object in the database by using the [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="04e6f-112">「[型指定された XML と型指定されていない XML](../xml/compare-typed-xml-to-untyped-xml.md)」で説明したように、スキーマが関連付けられる列や変数に格納されている XML を、**型指定された** XML と呼びます。これは、インスタンス データに必要なデータ型情報をスキーマが提供しているためです。</span><span class="sxs-lookup"><span data-stu-id="04e6f-112">As described in the topic, [Typed vs. Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md), the XML stored in a column or variable that a schema is associated with is referred to as **typed** XML, because the schema provides the necessary data type information for the instance data.</span></span> <span data-ttu-id="04e6f-113">SQL Server ではこの型情報を使用して、データ ストレージを最適化します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-113">SQL Server uses this type information to optimize data storage.</span></span>  
  
 <span data-ttu-id="04e6f-114">クエリ処理エンジンでも、型の確認、クエリの最適化、およびデータの変更にスキーマが使用されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-114">The query-processing engine also uses the schema for type checking and to optimize queries and data modification.</span></span>  
  
 <span data-ttu-id="04e6f-115">また、SQL Server では、 `xml` xml インスタンスを検証するために、型指定されたの場合に、関連付けられた xml スキーマコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-115">Also, SQL Server uses the associated XML schema collection, in the case of typed `xml`, to validate the XML instance.</span></span> <span data-ttu-id="04e6f-116">XML インスタンスがスキーマを使ってコンパイルされると、そのデータベースはインスタンスを型情報と共にシステムに格納できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-116">If the XML instance complies with the schema, the database allows the instance to be stored in the system with their type information.</span></span> <span data-ttu-id="04e6f-117">それ以外の場合は、インスタンスを拒否します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-117">Otherwise, it rejects the instance.</span></span>  
  
 <span data-ttu-id="04e6f-118">固有の関数 XML_SCHEMA_NAMESPACE を使用して、データベースに格納されているスキーマ コレクションを取得できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-118">You can use the intrinsic function XML_SCHEMA_NAMESPACE to retrieve the schema collection that is stored in the database.</span></span> <span data-ttu-id="04e6f-119">詳細については、「 [格納されている XML スキーマ コレクションの表示](../xml/view-a-stored-xml-schema-collection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04e6f-119">For more information, see [View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md).</span></span>  
  
 <span data-ttu-id="04e6f-120">また、XML スキーマ コレクションは、XML 変数、パラメーター、および列の型指定にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-120">You can also use the XML schema collection to type XML variables, parameters, and columns.</span></span>  
  
##  <a name="ddl-for-managing-schema-collections"></a><a name="ddl"></a> <span data-ttu-id="04e6f-121">スキーマ コレクションを管理するための DDL</span><span class="sxs-lookup"><span data-stu-id="04e6f-121">DDL for Managing Schema Collections</span></span>  
 <span data-ttu-id="04e6f-122">データベースに XML スキーマ コレクションを作成し、`xml` 型の変数や列に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-122">You can create XML schema collections in the database and associate them with variables and columns of `xml` type.</span></span> <span data-ttu-id="04e6f-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、データベースでスキーマ コレクションを管理するために、次の DDL ステートメントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-123">To manage schema collections in the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following DDL statements:</span></span>  
  
-   <span data-ttu-id="04e6f-124">[CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql): データベースにスキーマ コンポーネントをインポートします。</span><span class="sxs-lookup"><span data-stu-id="04e6f-124">[CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) Imports schema components into a database.</span></span>  
  
-   <span data-ttu-id="04e6f-125">[ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql): 既存の XML スキーマ コレクションのスキーマ コンポーネントを変更します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-125">[ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) Modifies the schema components in an existing XML schema collection.</span></span>  
  
-   <span data-ttu-id="04e6f-126">[ DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql): XML スキーマ コレクション全体とそのすべてのコンポーネントを削除します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-126">[DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) Deletes a complete XML schema collection and all its components.</span></span>  
  
 <span data-ttu-id="04e6f-127">XML スキーマ コレクションとそのコレクションに含まれるスキーマを使用するには、まず CREATE XML SCHEMA COLLECTION ステートメントを使用して、コレクションとスキーマを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-127">To use an XML schema collection and the schemas it contains, you must first create the collection and the schemas by using the CREATE XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="04e6f-128">スキーマ コレクションを作成したら、`xml` 型の変数および列を作成し、スキーマ コレクションに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-128">After the schema collection is created, you can then create variables and columns of `xml` type and associate the schema collection with them.</span></span> <span data-ttu-id="04e6f-129">スキーマ コレクションを作成すると、さまざまなスキーマ コンポーネントがメタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-129">Note that after a schema collection is created, various schema components are stored in the metadata.</span></span> <span data-ttu-id="04e6f-130">ALTER XML SCHEMA COLLECTION ステートメントを使用して、既存のスキーマにコンポーネントを追加したり、既存のスキーマ コレクションに新しいスキーマを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-130">You can also use the ALTER XML SCHEMA COLLECTION to add more components to the existing schemas or add new schemas to an existing collection.</span></span>  
  
 <span data-ttu-id="04e6f-131">スキーマ コレクションを削除するには、DROP XML SCHEMA COLLECTION ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-131">To drop the schema collection, use the DROP XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="04e6f-132">このステートメントを実行すると、スキーマ コレクションに含まれているすべてのスキーマが削除され、コレクション オブジェクトが削除されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-132">This drops all schemas that are contained in the collection and removes the collection object.</span></span> <span data-ttu-id="04e6f-133">スキーマ コレクションを削除する前に、「[DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)」に記載されている条件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="04e6f-133">Note that before you can drop a schema collection, the conditions described in [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)must be met.</span></span>  
  
##  <a name="understanding-schema-components"></a><a name="components"></a> <span data-ttu-id="04e6f-134">スキーマ コンポーネントについて</span><span class="sxs-lookup"><span data-stu-id="04e6f-134">Understanding Schema Components</span></span>  
 <span data-ttu-id="04e6f-135">CREATE XML SCHEMA COLLECTION ステートメントを使用すると、さまざまなスキーマ コンポーネントがデータベースにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-135">When you use the CREATE XML SCHEMA COLLECTION statement, various schema components are imported into the database.</span></span> <span data-ttu-id="04e6f-136">スキーマ コンポーネントには、スキーマの要素、属性、および型の定義などがあります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-136">Schema components include schema elements, attributes, and type definitions.</span></span> <span data-ttu-id="04e6f-137">DROP XML SCHEMA COLLECTION ステートメントを使用すると、コレクション全体が削除されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-137">When you use the DROP XML SCHEMA COLLECTION statement, you remove the complete collection.</span></span>  
  
 <span data-ttu-id="04e6f-138">CREATE XML SCHEMA COLLECTION ステートメントを使用すると、さまざまなシステム テーブルにスキーマ コンポーネントが保存されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-138">CREATE XML SCHEMA COLLECTION saves the schema components into various system tables.</span></span>  
  
 <span data-ttu-id="04e6f-139">たとえば、次のスキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-139">For example, consider the following schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            targetNamespace="uri:Cust_Orders2"  
            xmlns="uri:Cust_Orders2" >  
  <xsd:attribute name="SomeAttribute" type="xsd:int" />  
  <xsd:complexType name="SomeType" />  
  <xsd:complexType name="OrderType" >  
    <xsd:sequence>  
      <xsd:element name="OrderDate" type="xsd:date" />  
      <xsd:element name="RequiredDate" type="xsd:date" />  
      <xsd:element name="ShippedDate" type="xsd:date" />  
    </xsd:sequence>  
    <xsd:attribute name="OrderID" type="xsd:ID" />  
    <xsd:attribute name="CustomerID"  />  
    <xsd:attribute name="EmployeeID"  />  
  </xsd:complexType>  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order" type="OrderType"  
                     maxOccurs="unbounded" />  
       </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
      <xsd:attribute name="OrderIDList" type="xsd:IDREFS" />  
  </xsd:complexType>  
  <xsd:element name="Customer" type="CustomerType" />  
</xsd:schema>  
```  
  
 <span data-ttu-id="04e6f-140">上記のスキーマは、データベースに格納できる、異なる型のコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-140">The previous schema shows the different types of components that can be stored in the database.</span></span> <span data-ttu-id="04e6f-141">これには、 `SomeAttribute`、 `SomeType`、 `OrderType`、 `CustomerType`、 `Customer`、 `Order`、 `CustomerID`、 `OrderID`、 `OrderDate`、 `RequiredDate`、および `ShippedDate`があります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-141">These include `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`, and `ShippedDate`.</span></span>  
  
### <a name="component-categories"></a><span data-ttu-id="04e6f-142">コンポーネントのカテゴリ</span><span class="sxs-lookup"><span data-stu-id="04e6f-142">Component Categories</span></span>  
 <span data-ttu-id="04e6f-143">データベースに格納されるスキーマ コンポーネントは、次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-143">The Schema components stored in the database fall into the following categories:</span></span>  
  
-   <span data-ttu-id="04e6f-144">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="04e6f-144">ELEMENT</span></span>  
  
-   <span data-ttu-id="04e6f-145">ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="04e6f-145">ATTRIBUTE</span></span>  
  
-   <span data-ttu-id="04e6f-146">TYPE (単純型用または複合型用)</span><span class="sxs-lookup"><span data-stu-id="04e6f-146">TYPE (for simple or complex types)</span></span>  
  
-   <span data-ttu-id="04e6f-147">ATTRIBUTEGROUP</span><span class="sxs-lookup"><span data-stu-id="04e6f-147">ATTRIBUTEGROUP</span></span>  
  
-   <span data-ttu-id="04e6f-148">MODELGROUP</span><span class="sxs-lookup"><span data-stu-id="04e6f-148">MODELGROUP</span></span>  
  
 <span data-ttu-id="04e6f-149">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-149">For example:</span></span>  
  
-   <span data-ttu-id="04e6f-150">**SomeAttribute** は、ATTRIBUTE コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="04e6f-150">**SomeAttribute** is an ATTRIBUTE component.</span></span>  
  
-   <span data-ttu-id="04e6f-151">**SomeType**、 **OrderType**、および **CustomerType** は、TYPE コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="04e6f-151">**SomeType**, **OrderType**, and **CustomerType** are TYPE components.</span></span>  
  
-   <span data-ttu-id="04e6f-152">**Customer** は、ELEMENT コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="04e6f-152">**Customer** is an ELEMENT component.</span></span>  
  
 <span data-ttu-id="04e6f-153">スキーマをデータベースにインポートするとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではスキーマ自体は格納されません。</span><span class="sxs-lookup"><span data-stu-id="04e6f-153">When you import a schema into the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not store the schema itself.</span></span> <span data-ttu-id="04e6f-154">代わりに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって個々のさまざまなコンポーネントが格納されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-154">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stores the various individual components.</span></span> <span data-ttu-id="04e6f-155">つまり、\<Schema> タグは格納されず、定義されているコンポーネントのみが保持されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-155">That is, the \<Schema> tag is not stored, only the components that are defined within it are preserved.</span></span> <span data-ttu-id="04e6f-156">すべてのスキーマの要素は保持されません。</span><span class="sxs-lookup"><span data-stu-id="04e6f-156">All schema elements are not preserved.</span></span> <span data-ttu-id="04e6f-157">\<Schema> タグにそのコンポーネントの既定の動作を指定する属性が含まれている場合、次の表に示すように、そのような属性はインポート処理中にスキーマ コンポーネントに移動されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-157">If the \<Schema> tag contains attributes that specify default behavior of its components, these attributes are moved to the schema components within it during the import process, as shown in the following table.</span></span>  
  
|<span data-ttu-id="04e6f-158">属性名</span><span class="sxs-lookup"><span data-stu-id="04e6f-158">Attribute name</span></span>|<span data-ttu-id="04e6f-159">動作</span><span class="sxs-lookup"><span data-stu-id="04e6f-159">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="04e6f-160">**attributeFormDefault**</span><span class="sxs-lookup"><span data-stu-id="04e6f-160">**attributeFormDefault**</span></span>|<span data-ttu-id="04e6f-161">**form** 属性が存在しないスキーマ内のすべての属性の宣言に適用され、値は **attributeFormDefault** 属性の値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-161">The **form** attribute applied to all attribute declarations in the schema where it is not already present and the value is set to the value of the **attributeFormDefault** attribute.</span></span>|  
|<span data-ttu-id="04e6f-162">**elementFormDefault**</span><span class="sxs-lookup"><span data-stu-id="04e6f-162">**elementFormDefault**</span></span>|<span data-ttu-id="04e6f-163">**form** 属性が存在しないスキーマ内のすべての要素の宣言に適用され、値は **elementFormDefault** 属性の値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-163">The **form** attribute applied to all element declarations in the schema where it is not already present and the value is set to the value of the **elementFormDefault** attribute.</span></span>|  
|<span data-ttu-id="04e6f-164">**blockDefault**</span><span class="sxs-lookup"><span data-stu-id="04e6f-164">**blockDefault**</span></span>|<span data-ttu-id="04e6f-165">**block** 属性が存在しないすべての要素の宣言と型定義に適用され、値は **blockDefault** 属性の値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-165">The **block** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **blockDefault** attribute.</span></span>|  
|<span data-ttu-id="04e6f-166">**finalDefault**</span><span class="sxs-lookup"><span data-stu-id="04e6f-166">**finalDefault**</span></span>|<span data-ttu-id="04e6f-167">**final** 属性が存在しないすべての要素の宣言と型定義に適用され、値は **finalDefault** 属性の値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-167">The **final** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **finalDefault** attribute.</span></span>|  
|<span data-ttu-id="04e6f-168">**targetNamespace**</span><span class="sxs-lookup"><span data-stu-id="04e6f-168">**targetNamespace**</span></span>|<span data-ttu-id="04e6f-169">対象の名前空間に属するコンポーネントに関する情報がメタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-169">Information about the components that belong to the target namespace is stored in the metadata.</span></span>|  
  
##  <a name="permissions-on-an-xml-schema-collection"></a><a name="perms"></a> <span data-ttu-id="04e6f-170">XML スキーマ コレクションに対する権限</span><span class="sxs-lookup"><span data-stu-id="04e6f-170">Permissions on an XML Schema Collection</span></span>  
 <span data-ttu-id="04e6f-171">次の操作を行うためには必要な権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-171">You must have the necessary permissions to do the following:</span></span>  
  
-   <span data-ttu-id="04e6f-172">XML スキーマ コレクションを作成する、または読み込む</span><span class="sxs-lookup"><span data-stu-id="04e6f-172">Create/load the XML schema collection</span></span>  
  
-   <span data-ttu-id="04e6f-173">XML スキーマ コレクションを変更する</span><span class="sxs-lookup"><span data-stu-id="04e6f-173">Modify the XML schema collection</span></span>  
  
-   <span data-ttu-id="04e6f-174">XML スキーマ コレクションを削除する</span><span class="sxs-lookup"><span data-stu-id="04e6f-174">Drop the XML schema collection</span></span>  
  
-   <span data-ttu-id="04e6f-175">XML スキーマコレクションを使用して型 `xml` の列、変数、およびパラメーターを入力するか、テーブルまたは列の制約で使用します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-175">Use the XML schema collection to type `xml` type columns, variables, and parameters, or use it in table or column constraints</span></span>  
  
 <span data-ttu-id="04e6f-176">SQL Server セキュリティ モデルでは、すべてのオブジェクトで CONTROL 権限が許可されています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-176">The SQL Server security model allows CONTROL permission on every object.</span></span> <span data-ttu-id="04e6f-177">この権限が許可されたユーザーは、オブジェクトに対する他のすべての権限を取得したことになります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-177">The grantee of this permission obtains all other permissions on the object.</span></span> <span data-ttu-id="04e6f-178">オブジェクトの所有者も、オブジェクトに対するすべての権限を持っています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-178">The owner of the object also has all the permissions on the object.</span></span>  
  
 <span data-ttu-id="04e6f-179">オブジェクトの所有者とオブジェクトの CONTROL 権限があるユーザーは、オブジェクトに対する任意の権限を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-179">The owner and the grantee of the CONTROL permission on an object can grant any permission on the object.</span></span> <span data-ttu-id="04e6f-180">オブジェクトの所有者でなく、CONTROL 権限を持っていないユーザーでも、WITH GRANT OPTION が指定されていれば、オブジェクトに対する権限を許可できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-180">A user who is not the owner and does not have CONTROL permission can still grant permission on an object when WITH GRANT OPTION is specified.</span></span> <span data-ttu-id="04e6f-181">たとえば、ユーザー A は、WITH GRANT OPTION により、XML スキーマ コレクション S に対して REFERENCES 権限を持っていますが、S に対する他の権限は持っていないとします。ユーザー A は、スキーマ コレクション S に対する REFERENCES 権限をユーザー B に許可することができます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-181">For example, assume User A has REFERENCES permission on XML schema collection S, through WITH GRANT OPTION, but no other permissions on S. User A could grant User B REFERENCES permission on schema collection S.</span></span>  
  
 <span data-ttu-id="04e6f-182">セキュリティ モデルでは、XML スキーマ コレクションを作成および使用する権限を許可したり、あるユーザーから他のユーザーに所有権を転送することが許可されています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-182">The security model also allows permissions to create and use XML schema collections or transfer ownership from one user to another.</span></span> <span data-ttu-id="04e6f-183">次のトピックでは、XML スキーマ コレクションの権限について説明しています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-183">The following topics describe the XML schema collection permissions.</span></span>  
  
-   [<span data-ttu-id="04e6f-184">XML スキーマ コレクションに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="04e6f-184">Grant Permissions on an XML Schema Collection</span></span>](../xml/grant-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="04e6f-185">XML スキーマ コレクションを作成する権限を許可する方法、および XML スキーマ コレクション オブジェクトに対する権限を許可する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-185">This topic discussess how to grant permissions to create an XML schema collection and how to grant permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="04e6f-186">XML スキーマ コレクションに対する権限の取り消し</span><span class="sxs-lookup"><span data-stu-id="04e6f-186">Revoke Permissions on an XML Schema Collection</span></span>](../xml/revoke-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="04e6f-187">権限の取り消しを使用して XML スキーマ コレクションの作成を回避する方法、および XML スキーマ コレクション オブジェクトに対する権限を取り消す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-187">This topic discusses how revoking permissions can be used to prevent the creation of an XML schema collection and how to revoke permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="04e6f-188">XML スキーマ コレクションに対する権限の拒否</span><span class="sxs-lookup"><span data-stu-id="04e6f-188">Deny Permissions on an XML Schema Collection</span></span>](../xml/deny-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="04e6f-189">XML スキーマ コレクションを作成する権限を拒否する方法、および XML スキーマ コレクション オブジェクトに対する権限を拒否する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-189">This topic discusses how to deny permissions to create an XML schema collection and deny permission on an XML schema collection object.</span></span>  
  
##  <a name="getting-information-about-xml-schemas-and-schema-collections"></a><a name="info"></a> <span data-ttu-id="04e6f-190">XML スキーマおよびスキーマ コレクションに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="04e6f-190">Getting Information about XML Schemas and Schema Collections</span></span>  
 <span data-ttu-id="04e6f-191">カタログ ビュー sys.xml_schema_collections には XML スキーマ コレクションが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-191">XML schema collections are enumerated in the catalog view, sys.xml_schema_collections.</span></span> <span data-ttu-id="04e6f-192">XML スキーマ コレクション "sys" がシステムにより定義されています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-192">The XML schema collection "sys" is defined by the system.</span></span> <span data-ttu-id="04e6f-193">このコレクションには、すべてのユーザー定義 XML スキーマ コレクションで明示的に読み込むことなく使用できる定義済みの名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-193">It contains the predefined namespaces that can be used in all user-defined XML schema collections without having to load them explicitly.</span></span> <span data-ttu-id="04e6f-194">一覧には xml、xs、xsi、fn、および xdt 用の名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="04e6f-194">This list contains the namespaces for xml, xs, xsi, fn, and xdt.</span></span> <span data-ttu-id="04e6f-195">この他に、各 XML スキーマ コレクションのすべての名前空間を列挙する sys.xml_schema_namespaces、および各 XML スキーマのすべての XML スキーマ コンポーネントを列挙する sys.xml_components の 2 つのカタログ ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-195">Two other catalog views are sys.xml_schema_namespaces, which enumerates all namespaces within each XML schema collection, and sys.xml_components, which enumerates all XML schema components within each XML schema.</span></span>  
  
 <span data-ttu-id="04e6f-196">組み込み関数**XML_SCHEMA_NAMESPACE**、 *schemaName、XmlSchemacollectionName、名前空間 uri*は、 `xml` データ型のインスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-196">The built-in function **XML_SCHEMA_NAMESPACE**, *schemaName, XmlSchemacollectionName, namespace-uri*, yields an `xml` data type instance..</span></span> <span data-ttu-id="04e6f-197">このインスタンスには、XML スキーマ コレクションに含まれるスキーマ (定義済みの XML スキーマを除く) の XML スキーマ フラグメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-197">This instance contains XML schema fragments for schemas that are contained in an XML schema collection, except the predefined XML schemas.</span></span>  
  
 <span data-ttu-id="04e6f-198">XML スキーマ コレクションのコンテンツは、次のようにして列挙できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-198">You can enumerate the contents of an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="04e6f-199">XML スキーマ コレクションのカタログ ビューに対する Transact-SQL クエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-199">Write Transact-SQL queries on the appropriate catalog views for XML schema collections.</span></span>  
  
-   <span data-ttu-id="04e6f-200">組み込み関数 **XML_SCHEMA_NAMESPACE()** を使用します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-200">Use the built-in function **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="04e6f-201">`xml`この関数の出力には、データ型のメソッドを適用できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-201">You can apply `xml` data type methods on the output of this function.</span></span> <span data-ttu-id="04e6f-202">ただし、基になる XML スキーマは変更できません。</span><span class="sxs-lookup"><span data-stu-id="04e6f-202">However, you cannot modify the underlying XML schemas.</span></span>  
  
 <span data-ttu-id="04e6f-203">このことを次の例で説明します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-203">These are illustrated in the following examples.</span></span>  
  
### <a name="example-enumerate-the-xml-namespaces-in-an-xml-schema-collection"></a><span data-ttu-id="04e6f-204">例:XML スキーマ コレクションでの XML 名前空間の列挙</span><span class="sxs-lookup"><span data-stu-id="04e6f-204">Example: Enumerate the XML Namespaces in an XML Schema Collection</span></span>  
 <span data-ttu-id="04e6f-205">XML スキーマ コレクション "myCollection" に次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-205">Use the following query for the XML schema collection "myCollection":</span></span>  
  
```  
SELECT XSN.name  
FROM    sys.xml_schema_collections XSC JOIN sys.xml_schema_namespaces XSN  
    ON (XSC.xml_collection_id = XSN.xml_collection_id)  
WHERE    XSC.name = 'myCollection'     
```  
  
### <a name="example-enumerate-the-contents-of-an-xml-schema-collection"></a><span data-ttu-id="04e6f-206">例:XML スキーマ コレクションのコンテンツの列挙</span><span class="sxs-lookup"><span data-stu-id="04e6f-206">Example: Enumerate the Contents of an XML Schema Collection</span></span>  
 <span data-ttu-id="04e6f-207">次のステートメントは、リレーショナル スキーマ dbo 内の XML スキーマ コレクション "myCollection" のコンテンツを列挙します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-207">The following statement enumerates the contents of the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection')  
```  
  
 <span data-ttu-id="04e6f-208">コレクション内の個々の XML スキーマは `xml` 、ターゲットの名前空間を**XML_SCHEMA_NAMESPACE ()** の3番目の引数として指定することで、データ型のインスタンスとして取得できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-208">Individual XML schemas within the collection can be obtained as `xml` data type instances by specifying the target namespace as the third argument to **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="04e6f-209">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04e6f-209">This is shown in the following example.</span></span>  
  
### <a name="example-output-a-specified-schema-from-an-xml-schema-collection"></a><span data-ttu-id="04e6f-210">例:XML スキーマ コレクションからの指定したスキーマの出力</span><span class="sxs-lookup"><span data-stu-id="04e6f-210">Example: Output a Specified Schema from an XML Schema Collection</span></span>  
 <span data-ttu-id="04e6f-211">次のステートメントを実行すると、リレーショナル スキーマ dbo の XML スキーマ コレクション "myCollection" から、対象になる名前空間が "<https://www.microsoft.com/books>" である XML スキーマが出力されます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-211">The following statement outputs the XML schema with the target namespace "<https://www.microsoft.com/books>" from the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection',   
N'https://www.microsoft.com/books')  
```  
  
### <a name="querying-xml-schemas"></a><span data-ttu-id="04e6f-212">XML スキーマへのクエリ</span><span class="sxs-lookup"><span data-stu-id="04e6f-212">Querying XML Schemas</span></span>  
 <span data-ttu-id="04e6f-213">XML スキーマ コレクションに読み込んだ XML スキーマには、次のようにしてクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-213">You can query XML schemas that you have loaded into XML schema collections in the following ways:</span></span>  
  
-   <span data-ttu-id="04e6f-214">XML スキーマ名前空間のカタログ ビューに対する Transact-SQL クエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="04e6f-214">Write Transact-SQL queries on catalog views for XML schema namespaces.</span></span>  
  
-   <span data-ttu-id="04e6f-215">`xml` データ型の列を含むテーブルを作成し、その列に XML スキーマを保存して XML 型のシステムに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-215">Create a table that contains an `xml` data type column to store your XML schemas and also load them into the XML type system.</span></span> <span data-ttu-id="04e6f-216">その後、`xml` データ型のメソッドを使用して XML 列にクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-216">You can query the XML column by using the `xml` data type methods.</span></span> <span data-ttu-id="04e6f-217">また、この列に XML インデックスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="04e6f-217">Also, you can build an XML index on this column.</span></span> <span data-ttu-id="04e6f-218">ただしこの方法を使用する場合は、XML 列に保存されている XML スキーマと XML 型のシステムとの整合性をアプリケーションで保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-218">However, with this approach, the application must maintain consistency between the XML schemas stored in the XML column and the XML type system.</span></span> <span data-ttu-id="04e6f-219">たとえば、XML 型のシステムから XML スキーマ名前空間を削除する場合、整合性を保つためにテーブルからもその名前空間を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04e6f-219">For example, if you drop the XML schema namespace from the XML type system, you also have to drop it from the table in order to preserve consistency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e6f-220">参照</span><span class="sxs-lookup"><span data-stu-id="04e6f-220">See Also</span></span>  
 <span data-ttu-id="04e6f-221">[格納されている XML スキーマ コレクションの表示](../xml/view-a-stored-xml-schema-collection.md) </span><span class="sxs-lookup"><span data-stu-id="04e6f-221">[View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md) </span></span>  
 <span data-ttu-id="04e6f-222">[含まれているスキーマをマージするためのスキーマの前処理](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="04e6f-222">[Preprocess a Schema to Merge Included Schemas](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span></span>  
 [<span data-ttu-id="04e6f-223">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="04e6f-223">Requirements and Limitations for XML Schema Collections on the Server</span></span>](../xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
