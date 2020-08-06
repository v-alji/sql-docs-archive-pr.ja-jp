---
title: XML スキーマ コレクションに対する権限の拒否 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- denying permissions [SQL Server], XML server collections
ms.assetid: e2b300b0-e734-4c43-a4da-c78e6e5d4fba
author: rothja
ms.author: jroth
ms.openlocfilehash: 0791a9bd9c7f6b323886a38bed27bea84940770d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631689"
---
# <a name="deny-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="275e0-102">XML スキーマ コレクションに対する権限の拒否</span><span class="sxs-lookup"><span data-stu-id="275e0-102">Deny Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="275e0-103">新しい XML スキーマ コレクションを作成したり、既存の XML スキーマ コレクションを使用する権限を拒否できます。</span><span class="sxs-lookup"><span data-stu-id="275e0-103">Permission can be denied to either create a new XML schema collection or use an existing one.</span></span>  
  
## <a name="denying-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="275e0-104">XML スキーマ コレクションを作成する権限の拒否</span><span class="sxs-lookup"><span data-stu-id="275e0-104">Denying Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="275e0-105">次の方法で、XML スキーマ コレクションを作成する権限を拒否できます。</span><span class="sxs-lookup"><span data-stu-id="275e0-105">You can deny permission to create an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="275e0-106">リレーショナル スキーマに対する ALTER 権限を拒否します。</span><span class="sxs-lookup"><span data-stu-id="275e0-106">Deny ALTER permission on the relational schema.</span></span>  
  
-   <span data-ttu-id="275e0-107">リレーショナル スキーマやスキーマに含まれるすべてのオブジェクトに対するすべての権限を拒否するには、リレーショナル スキーマに対する CONTROL 権限を拒否します。</span><span class="sxs-lookup"><span data-stu-id="275e0-107">Deny CONTROL on the relational schema to deny all permissions on the relational schema and on all the contained objects.</span></span>  
  
-   <span data-ttu-id="275e0-108">データベースに対する ALTER ANY SCHEMA を拒否します。</span><span class="sxs-lookup"><span data-stu-id="275e0-108">Deny ALTER ANY SCHEMA on the database.</span></span> <span data-ttu-id="275e0-109">この場合、プリンシパルはデータベースのどこにも XML スキーマ コレクションを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="275e0-109">In this case, the principal cannot create an XML schema collection anywhere in the database.</span></span> <span data-ttu-id="275e0-110">データベースに対する ALTER 権限または CONTROL 権限を拒否すると、データベース内のすべてのオブジェクトに対するすべての権限を拒否することになるので注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="275e0-110">Note also that denying ALTER or CONTROL permission on the database denies all permissions on all objects in the database.</span></span>  
  
## <a name="denying-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="275e0-111">XML スキーマ コレクション オブジェクトの権限の拒否</span><span class="sxs-lookup"><span data-stu-id="275e0-111">Denying Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="275e0-112">既存の XML スキーマ コレクションで拒否可能な権限とその結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="275e0-112">Following are the permission that can be denied on an existing XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="275e0-113">ALTER 権限を拒否すると、XML スキーマ コレクションの内容を変更するプリンシパルの権限を拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-113">Denying the ALTER permission denies the principal the ability to modify the contents of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="275e0-114">CONTROL 権限を拒否すると、XML スキーマ コレクションで操作を実行するプリンシパルの権限を拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-114">Denying the CONTROL permission denies the principal the ability to perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="275e0-115">REFERENCES 権限を拒否すると、XML スキーマ コレクションを使用して xml 型の列やパラメーターを型指定または制約するプリンシパルの権限を拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-115">Denying the REFERENCES permission denies the principal the ability to type or constrain xml type columns and parameters using the XML schema collection.</span></span> <span data-ttu-id="275e0-116">また、他の XML スキーマ コレクションからこの XML スキーマ コレクションを参照するプリンシパルの権限も拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-116">It also denies the principal the ability to refer to this XML schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="275e0-117">VIEW DEFINITION 権限を拒否すると、XML スキーマ コレクションのコンテンツを表示するプリンシパルの権限を拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-117">Denying the VIEW DEFINITION permission denies the principal the ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="275e0-118">EXECUTE 権限を拒否すると、XML スキーマ コレクションによって型指定または制約された列、変数、およびパラメーターの値を挿入または更新するプリンシパルの権限を拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-118">Denying the EXECUTE permission denies the principal the ability to insert or update the values in columns, variables, and parameters that are typed or constrained by the XML schema collection.</span></span> <span data-ttu-id="275e0-119">また、同じ xml 型の列や変数の値のクエリを実行するプリンシパルの権限も拒否することになります。</span><span class="sxs-lookup"><span data-stu-id="275e0-119">It also denies the principal the ability to query the values in those same xml type columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="275e0-120">例</span><span class="sxs-lookup"><span data-stu-id="275e0-120">Examples</span></span>  
 <span data-ttu-id="275e0-121">次の例のシナリオでは、XML スキーマ権限の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="275e0-121">The scenarios in the following examples show how XML schema permissions work.</span></span> <span data-ttu-id="275e0-122">各例では、必要なテスト データベース、リレーショナル スキーマ、およびログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="275e0-122">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="275e0-123">それらのログインには、必要な XML スキーマ コレクション権限が許可されています。</span><span class="sxs-lookup"><span data-stu-id="275e0-123">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="275e0-124">最後に必要なクリーンアップを行います。</span><span class="sxs-lookup"><span data-stu-id="275e0-124">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-preventing-a-user-from-creating-an-xml-schema-collection"></a><span data-ttu-id="275e0-125">A.</span><span class="sxs-lookup"><span data-stu-id="275e0-125">A.</span></span> <span data-ttu-id="275e0-126">ユーザーによる XML スキーマ コレクションの作成を防止する</span><span class="sxs-lookup"><span data-stu-id="275e0-126">Preventing a user from creating an XML schema collection</span></span>  
 <span data-ttu-id="275e0-127">ユーザーが XML スキーマ コレクションを作成できないようにする方法の 1 つは、リレーショナル スキーマの ALTER 権限を拒否することです。</span><span class="sxs-lookup"><span data-stu-id="275e0-127">One of the ways to prevent a user from creating an XML schema collection is by denying the ALTER permission on a relational schema.</span></span> <span data-ttu-id="275e0-128">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="275e0-128">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="275e0-129">この例では、ユーザー `TestLogin1`とデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="275e0-129">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="275e0-130">このデータベースには、 `dbo` スキーマに加えてリレーショナル スキーマも作成します。</span><span class="sxs-lookup"><span data-stu-id="275e0-130">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="275e0-131">まず、 `CREATE XML SCHEMA` 権限によって、データベース内の任意の場所にスキーマ コレクションを作成する権限をユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="275e0-131">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span> <span data-ttu-id="275e0-132">次に、リレーショナル スキーマの 1 つに対して、そのユーザーの `ALTER` 権限を拒否します。</span><span class="sxs-lookup"><span data-stu-id="275e0-132">The example then denies `ALTER` permission to the user on one of the relational schemas.</span></span> <span data-ttu-id="275e0-133">これにより、ユーザーはこのリレーショナル スキーマで XML スキーマ コレクションを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="275e0-133">This prevents the user from creating an XML schema collection in that relational schema.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
GO  
-- Now deny permission from TestLogin1 to alter myOtherDBSchema.  
setuser  
GO  
DENY ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
GO  
-- Now TestLogin1 cannot create xml schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
### <a name="b-denying-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="275e0-134">B.</span><span class="sxs-lookup"><span data-stu-id="275e0-134">B.</span></span> <span data-ttu-id="275e0-135">XML スキーマ コレクションに対する権限の拒否</span><span class="sxs-lookup"><span data-stu-id="275e0-135">Denying permissions on an XML schema collection</span></span>  
 <span data-ttu-id="275e0-136">次の例では、既存の XML スキーマ コレクションに対するログインの特定の権限を拒否する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="275e0-136">The following example shows how a specific permission on an existing XML schema collection can be denied to a login.</span></span> <span data-ttu-id="275e0-137">この例では、テスト ログインは既存の XML スキーマ コレクションに対する REFERENCES 権限を拒否します。</span><span class="sxs-lookup"><span data-stu-id="275e0-137">In this example, a test login is denied REFERENCES permission on an existing XML schema collection.</span></span>  
  
 <span data-ttu-id="275e0-138">この例では、ユーザー `TestLogin1`とデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="275e0-138">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="275e0-139">このデータベースには、 `dbo` スキーマに加えてリレーショナル スキーマも作成します。</span><span class="sxs-lookup"><span data-stu-id="275e0-139">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="275e0-140">まず、 `CREATE XML SCHEMA` 権限によって、データベース内の任意の場所にスキーマ コレクションを作成する権限をユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="275e0-140">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span>  
  
 <span data-ttu-id="275e0-141">`REFERENCES` に XML スキーマ コレクションに対する `TestLogin1` 権限があれば、テーブルに型指定された `xml` 列を作成するときにスキーマを使用できます。</span><span class="sxs-lookup"><span data-stu-id="275e0-141">The `REFERENCES` permission on the XML schema collection lets `TestLogin1` use the schema in creating a typed `xml` column in a table.</span></span> <span data-ttu-id="275e0-142">XML スキーマ コレクションに対する `REFERENCES` 権限が拒否された場合、 `TestLogin1` は XML スキーマ コレクションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="275e0-142">If the `REFERENCES` permission on the XML schema collection is denied, it prevents the `TestLogin1` from using the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, the following  
-- permission is required.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant permission to TestLogin1 to create a table and reference the XML schema collection.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also needs REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on the schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection   
TO TestLogin1  
GO  
  
--TestLogin1 can use the schema.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
-- Drop the table.  
DROP TABLE T  
GO  
-- Now deny REFERENCES permission to TestLogin1 on the schema created previously.  
SETUSER  
GO  
DENY REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection TO TestLogin1  
  
GO  
-- Now TestLogin1 cannot create xml schema collection  
SETUSER 'TestLogin1'  
GO  
-- Following statement fails. TestLogin1 does not have REFERENCES   
-- permission on the XML schema collection.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="275e0-143">参照</span><span class="sxs-lookup"><span data-stu-id="275e0-143">See Also</span></span>  
 <span data-ttu-id="275e0-144">[型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="275e0-144">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="275e0-145">[XML スキーマ コレクション &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="275e0-145">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 <span data-ttu-id="275e0-146">[サーバー上の XML スキーマ コレクションの要件と制限](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span><span class="sxs-lookup"><span data-stu-id="275e0-146">[Requirements and Limitations for XML Schema Collections on the Server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span></span>  
 <span data-ttu-id="275e0-147">[DENY (オブジェクトの権限の拒否) &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="275e0-147">[DENY Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="275e0-148">[GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="275e0-148">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="275e0-149">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="275e0-149">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
