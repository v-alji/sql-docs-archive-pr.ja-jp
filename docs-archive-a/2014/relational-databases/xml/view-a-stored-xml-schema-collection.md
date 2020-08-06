---
title: 格納されている XML スキーマ コレクションの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6383fb17183a991d2f83325044663cc9671e9442
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633006"
---
# <a name="view-a-stored-xml-schema-collection"></a><span data-ttu-id="19787-102">格納されている XML スキーマ コレクションの表示</span><span class="sxs-lookup"><span data-stu-id="19787-102">View a Stored XML Schema Collection</span></span>
  <span data-ttu-id="19787-103">[CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)を使用して XML スキーマ コレクションをインポートすると、メタデータにスキーマ コンポーネントが格納されます。</span><span class="sxs-lookup"><span data-stu-id="19787-103">After you import an XML schema collection by using [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql), the schema components are stored in the metadata.</span></span> <span data-ttu-id="19787-104">固有の関数 [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)を使用して、XML スキーマ コレクションを再構築できます。</span><span class="sxs-lookup"><span data-stu-id="19787-104">You can use the [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)intrinsic function to reconstruct the XML schema collection.</span></span> <span data-ttu-id="19787-105">この関数は、`xml` データ型のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="19787-105">This function returns an `xml` data type instance.</span></span>  
  
 <span data-ttu-id="19787-106">たとえば、次のクエリでは、`ProductDescriptionSchemaCollection`データベースの実稼働リレーショナル スキーマから XML スキーマ コレクション ( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ) が取得されます。</span><span class="sxs-lookup"><span data-stu-id="19787-106">For example, the following query retrieves an XML schema collection (`ProductDescriptionSchemaCollection`) from the production relational schema in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 <span data-ttu-id="19787-107">XML スキーマ コレクションに含まれるスキーマを 1 つだけ表示する場合は、`xml_schema_namespace` によって返された `xml` 型の結果に対して、XQuery を指定できます。</span><span class="sxs-lookup"><span data-stu-id="19787-107">If you want to see only one schema from the XML schema collection, you can specify XQuery against the `xml` type result that is returned by `xml_schema_namespace`.</span></span>  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 <span data-ttu-id="19787-108">たとえば、次のクエリでは、 `ProductDescriptionSchemaCollection` XML スキーマ コレクションに含まれる、製品保証書とメンテナンスの XML スキーマ情報を取得しています。</span><span class="sxs-lookup"><span data-stu-id="19787-108">For example, the following query retrieves product warranty and maintenance XML schema information from the `ProductDescriptionSchemaCollection` XML schema collection.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 <span data-ttu-id="19787-109">次のクエリに示すように、省略可能な対象名前空間を 3 番目のパラメーターとして `xml_schema_namespace` 関数に渡すことにより、特定のスキーマをコレクションから取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="19787-109">You can also pass the optional target namespace as the third parameter to the `xml_schema_namespace` function to retrieve specific schema from the collection, as shown in the following query:</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 <span data-ttu-id="19787-110">CREATE XML SCHEMA COLLECTION を使用してデータベースに XML スキーマ コレクションを作成すると、スキーマ コンポーネントがメタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="19787-110">When you create an XML schema collection by using CREATE XML SCHEMA COLLECTION in the database, the statement stores the schema components in the metadata.</span></span> <span data-ttu-id="19787-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が理解したスキーマ コンポーネントのみが格納されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="19787-111">Note that only the schema components that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understands are stored.</span></span> <span data-ttu-id="19787-112">コメント、注釈、または XSD 以外の属性は格納されません。</span><span class="sxs-lookup"><span data-stu-id="19787-112">Any comments, annotations, or non-XSD attributes are not stored.</span></span> <span data-ttu-id="19787-113">したがって、 **xml_schema_namespace** によって再構築されたスキーマは、機能的には元のスキーマと同じですが、同じように見えるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="19787-113">Therefore, the schema reconstructed by **xml_schema_namespace** is functionally equivalent to the original schema, but it will not necessarily look the same.</span></span> <span data-ttu-id="19787-114">たとえば、元のスキーマにあったものと同じプレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="19787-114">For example, you will not see the same prefixes you had in the original schema.</span></span> <span data-ttu-id="19787-115">**xml_schema_namespace** によって返されるスキーマでは、対象名前空間のプレフィックスとして **t** が使用され、他の名前空間には **ns1**、 **ns2**などが使用されています。</span><span class="sxs-lookup"><span data-stu-id="19787-115">The schema returned by **xml_schema_namespace** uses **t** as the prefix for the target namespace and **ns1**, **ns2**, and so on, for other namespaces.</span></span>  
  
 <span data-ttu-id="19787-116">XML スキーマの同一のコピーを保持するには、ファイルまたはデータベース テーブルの `xml` 型の列に XML スキーマを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19787-116">If you want to retain an identical copy of the XML schemas, you should save your XML schema in a file or in a database table in an `xml` type column.</span></span>  
  
 <span data-ttu-id="19787-117">[sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) カタログ ビューでも、XML スキーマ コレクションに関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="19787-117">The [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) catalog view also returns information about XML schema collections.</span></span> <span data-ttu-id="19787-118">この情報には、コレクションの名前、作成日、およびコレクションの所有者が含まれます。</span><span class="sxs-lookup"><span data-stu-id="19787-118">This information includes the name of the collection, the creation date, and the owner of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19787-119">参照</span><span class="sxs-lookup"><span data-stu-id="19787-119">See Also</span></span>  
 [<span data-ttu-id="19787-120">XML スキーマ コレクション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="19787-120">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
