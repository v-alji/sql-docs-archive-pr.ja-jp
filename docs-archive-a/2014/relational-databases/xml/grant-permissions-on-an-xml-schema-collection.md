---
title: XML スキーマ コレクションに対する権限の許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- granting permissions [SQL Server], XML schema collections
- ALTER permission
ms.assetid: ffbb829c-3b8f-4e5d-97d9-ab4059aab0db
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dc6384acb2f079245c80923e683ebe2c03d2562
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712842"
---
# <a name="grant-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="b9cf7-102">XML スキーマ コレクションに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-102">Grant Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="b9cf7-103">XML スキーマ コレクションを作成する権限、および XML スキーマ コレクション オブジェクトに対する権限を許可できます。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-103">You can grant permissions to create an XML schema collection and also grant permissions on an XML schema collection object.</span></span>  
  
## <a name="granting-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="b9cf7-104">XML スキーマ コレクションを作成する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-104">Granting Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="b9cf7-105">XML スキーマ コレクションを作成するには、次の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-105">To create an XML schema collection, the following permissions are required:</span></span>  
  
-   <span data-ttu-id="b9cf7-106">プリンシパルは、データベースレベルの CREATE XML SCHEMA COLLECTION 権限を必要とします。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-106">The principal requires CREATE XML SCHEMA COLLECTION permission at the database-level.</span></span>  
  
-   <span data-ttu-id="b9cf7-107">XML スキーマ コレクションはリレーショナル スキーマ スコープなので、プリンシパルはリレーショナル スキーマに対する ALTER 権限も必要とします。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-107">Because the XML schema collections are relational schema-scoped, the principal must also have ALTER permission on the relational schema.</span></span>  
  
 <span data-ttu-id="b9cf7-108">次の権限があると、プリンシパルはサーバー上のデータベース内のリレーショナル スキーマに XML スキーマ コレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-108">The following permissions let a principal create an XML schema collection in a relational schema in a database on a server:</span></span>  
  
-   <span data-ttu-id="b9cf7-109">サーバーに対する CONTROL 権限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-109">CONTROL permission on the server</span></span>  
  
-   <span data-ttu-id="b9cf7-110">サーバーに対する ALTER ANY DATABASE 権限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-110">ALTER ANY DATABASE permission on the server</span></span>  
  
-   <span data-ttu-id="b9cf7-111">データベースに対する ALTER 権限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-111">ALTER permission on the database</span></span>  
  
-   <span data-ttu-id="b9cf7-112">データベースに対する CONTROL 権限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-112">CONTROL permission in the database</span></span>  
  
-   <span data-ttu-id="b9cf7-113">データベースに対する ALTER ANY SCHEMA 権限と CREATE XML SCHEMA COLLECTION 権限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-113">ALTER ANY SCHEMA permission and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
-   <span data-ttu-id="b9cf7-114">リレーショナル スキーマに対する ALTER 権限または CONTROL 権限と、データベースに対する CREATE XML SCHEMA COLLECTION 権限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-114">ALTER or CONTROL permission on the relational schema and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
 <span data-ttu-id="b9cf7-115">上に示した最後の方法を次の例で使用します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-115">This last method of permissions is used in the following example.</span></span>  
  
 <span data-ttu-id="b9cf7-116">リレーショナル スキーマの所有者は、そのスキーマで作成される XML スキーマ コレクションの所有者になります。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-116">The owner of the relational schema becomes the owner of the XML schema collection created in that schema.</span></span> <span data-ttu-id="b9cf7-117">その結果、この所有者には XML スキーマ コレクションに対するフル コントロール権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-117">This owner then has full control over the XML schema collection.</span></span> <span data-ttu-id="b9cf7-118">したがって、この所有者は XML スキーマ コレクションの変更も、xml 列の型指定も、XML スキーマ コレクションの削除も行えます。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-118">Therefore, this owner can modify the XML schema collection, type an xml column, or drop the XML schema collection.</span></span>  
  
## <a name="granting-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="b9cf7-119">XML スキーマ コレクション オブジェクトの権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-119">Granting Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="b9cf7-120">XML スキーマ コレクションに対して許可できる権限は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-120">The following permissions are allowed on the XML schema collection:</span></span>  
  
-   <span data-ttu-id="b9cf7-121">ALTER 権限。ALTER XML SCHEMA COLLECTION ステートメントを使用して既存の XML スキーマ コレクションのコンテンツを変更する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-121">The ALTER permission is required when modifying contents of an existing XML schema collection by using the ALTER XML SCHEMA COLLECTION statement.</span></span>  
  
-   <span data-ttu-id="b9cf7-122">CONTROL 権限。許可されると、ユーザーは XML スキーマ コレクションに任意の操作を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-122">The CONTROL permission lets a user perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="b9cf7-123">TAKE OWNERSHIP 権限。XML スキーマ コレクションの所有者権を特定のプリンシパルから別のプリンシパルに転送するために必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-123">The TAKE OWNERSHIP permission is required to transfer ownership of the XML schema collection from one principal to another.</span></span>  
  
-   <span data-ttu-id="b9cf7-124">REFERENCES 権限。許可されたプリンシパルは、XML スキーマ コレクションを使用してテーブル、ビュー、およびパラメーター内の `xml` 型の列に対して型指定や制約を行えます。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-124">The REFERENCES permission authorizes the principal to use the XML schema collection to type or constrain `xml` type columns, in tables and views and parameters.</span></span> <span data-ttu-id="b9cf7-125">また、REFERENCES 権限は、ある XML スキーマ コレクションで別の XML スキーマ コレクションを参照する場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-125">The REFERENCES permission is also required when one XML schema collection refers to another.</span></span>  
  
-   <span data-ttu-id="b9cf7-126">VIEW DEFINITION 権限。このコレクションに対する ALTER 権限、REFERENCES 権限、または CONTROL 権限のいずれかがあれば、XML_SCHEMA_NAMESPACE またはカタログ ビューのどちらかを使用して XML スキーマ コレクションの内容に対してクエリ実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-126">The VIEW DEFINITION permission allows the principal to query the contents of an XML schema collection either through XML_SCHEMA_NAMESPACE or through the catalog views, provided this principal also has one of the ALTER, REFERENCES, or CONTROL permissions on the collection.</span></span>  
  
-   <span data-ttu-id="b9cf7-127">EXECUTE 権限。`xml` 型の列、変数、およびパラメーターの型指定または制約を定義している XML スキーマ コレクションに対して、プリンシパルが挿入または更新した値を検証するために必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-127">The EXECUTE permission is required to validate values inserted or updated by the principal against the XML schema collection that is typing or constraining the `xml` type columns, variables, and parameters.</span></span> <span data-ttu-id="b9cf7-128">また、これらの列や変数に格納されている XML に対してクエリを実行する場合にも必要な権限です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-128">You also need this permission when you are querying the XML stored in these columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b9cf7-129">例</span><span class="sxs-lookup"><span data-stu-id="b9cf7-129">Examples</span></span>  
 <span data-ttu-id="b9cf7-130">次の例に示すシナリオでは、XML スキーマ権限のしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-130">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="b9cf7-131">各例では、必要なテスト データベース、リレーショナル スキーマ、およびログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-131">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="b9cf7-132">それらのログインには、必要な XML スキーマ コレクション権限が許可されています。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-132">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="b9cf7-133">各例の最後には、必要なクリーン アップを行います。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-133">Each example does the necessary clean up at the end.</span></span>  
  
### <a name="a-granting-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="b9cf7-134">A.</span><span class="sxs-lookup"><span data-stu-id="b9cf7-134">A.</span></span> <span data-ttu-id="b9cf7-135">XML スキーマ コレクションを作成する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-135">Granting permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="b9cf7-136">次の例では、権限を許可することにより、プリンシパルが XML スキーマ コレクションを作成できるようにする方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-136">The following example shows how to grant permissions so that a principal can create an XML schema collection.</span></span> <span data-ttu-id="b9cf7-137">この例では、サンプル データベースとテスト ユーザー `TestLogin1`を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-137">The example creates a sample database and a test user, `TestLogin1`.</span></span> <span data-ttu-id="b9cf7-138">`TestLogin1` に、リレーショナル スキーマに対する `ALTER` 権限と、データベースに対する `CREATE XML SCHEMA COLLECTION` 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-138">`TestLogin1` is then given `ALTER` permission on the relational schema and given `CREATE XML SCHEMA COLLECTION` permission on the database.</span></span> <span data-ttu-id="b9cf7-139">これらの権限を使用して、 `TestLogin1` はサンプルの XML スキーマ コレクションを正常に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-139">With these permissions, `TestLogin1` succeeds in creating a sample XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Execute CREATE XML SCHEMA COLLECTION.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="root" type="xsd:byte"/>  
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
  
### <a name="b-granting-permission-to-use-an-existing-xml-schema-collection"></a><span data-ttu-id="b9cf7-140">B.</span><span class="sxs-lookup"><span data-stu-id="b9cf7-140">B.</span></span> <span data-ttu-id="b9cf7-141">既存の XML スキーマ コレクションを使用する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-141">Granting permission to use an existing XML schema collection</span></span>  
 <span data-ttu-id="b9cf7-142">次の例では、XML スキーマ コレクションの権限モデルを詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-142">The following example further shows the permission model for the XML schema collection.</span></span> <span data-ttu-id="b9cf7-143">XML スキーマ コレクションの作成と使用には、各種の権限が必要であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-143">The example shows how different permissions are required to create and use the XML schema collection.</span></span>  
  
 <span data-ttu-id="b9cf7-144">この例では、テスト データベースとログイン `TestLogin1`を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-144">The example creates a test database and a login, `TestLogin1`.</span></span> <span data-ttu-id="b9cf7-145">`TestLogin1` で、データベースに XML スキーマ コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-145">`TestLogin1` creates an XML schema collection in the database.</span></span> <span data-ttu-id="b9cf7-146">次に、テーブルを作成し、XML スキーマ コレクションを使用して、型指定された xml 列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-146">The login then creates a table and uses the XML schema collection to create a typed xml column.</span></span> <span data-ttu-id="b9cf7-147">その後、データを挿入し、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-147">The user then inserts data and queries it.</span></span> <span data-ttu-id="b9cf7-148">次のコードに示すように、これらのどの手順でも正しいスキーマ権限を必要とします。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-148">All these steps require the necessary schema permissions, as shown in the code.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Create a table by using the collection to type an XML column.   
--TestLogin1 must have permission to create a table.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also must have REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- Now user can create a table and use the XML schema collection to create   
-- a typed XML column.  
SETUSER 'TestLogin1'  
GO  
CREATE TABLE MyTestTable (xmlCol xml (dbo.myTestSchemaCollection))  
GO  
-- To insert data in the table, the user needs EXECUTE permission on the XML schema collection.  
-- GRANT EXECUTE permission to TestLogin2 on the xml schema collection.  
SETUSER  
GO  
GRANT EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- TestLogin1 does not own the dbo schema. This user must have INSERT permission.  
GRANT INSERT TO TestLogin1  
GO  
-- Now the user can insert data into the table.  
SETUSER 'TestLogin1'  
GO  
INSERT INTO MyTestTable VALUES('  
<telephone xmlns="http://schemas.adventure-works.com/Additional/ContactInfo">111-1111</telephone>  
')  
GO  
-- To query the table, TestLogin1 must have permissions: SELECT on the table and EXECUTE on the XML schema collection.  
SETUSER  
GO  
GRANT SELECT TO TestLogin1  
GO  
-- TestLogin1 already has EXECUTE permission on the schema (granted before inserting a record in the table).  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
GO  
-- To show that the user must have EXECUTE permission to query, revoke the  
-- previously granted permission and return the query.  
SETUSER  
GO  
REVOKE EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection to TestLogin1  
Go  
-- Now TestLogin1 cannot execute the query.  
SETUSER 'TestLogin1'  
GO  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
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
  
### <a name="c-granting-alter-permission-on-an-xml-schema-collection"></a><span data-ttu-id="b9cf7-149">C.</span><span class="sxs-lookup"><span data-stu-id="b9cf7-149">C.</span></span> <span data-ttu-id="b9cf7-150">XML スキーマ コレクションに対する ALTER 権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-150">Granting ALTER permission on an XML schema collection</span></span>  
 <span data-ttu-id="b9cf7-151">データベース内の既存の XML スキーマ コレクションを変更するには、ユーザーに ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-151">A user must have ALTER permission to modify an existing XML schema collection in the database.</span></span> <span data-ttu-id="b9cf7-152">次の例では、 `ALTER` 権限を許可する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-152">The following example shows how to grant `ALTER` permission.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant ALTER permission to TestLogin1.  
setuser  
GO  
GRANT ALTER ON XML SCHEMA COLLECTION::myTestSchemaCollection TO TestLogin1  
GO  
-- TestLogin1 should be able to add components to the collection.  
SETUSER 'TestLogin1'  
GO  
ALTER XML SCHEMA COLLECTION myTestSchemaCollection ADD '  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns="http://schemas.adventure-works.com/Additional/ContactInfo"   
elementFormDefault="qualified">  
 <xsd:element name="pager" type="xsd:string"/>  
</xsd:schema>  
'  
Go  
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
  
### <a name="d-granting-take-ownership-permission-on-an-xml-schema-collection"></a><span data-ttu-id="b9cf7-153">D.</span><span class="sxs-lookup"><span data-stu-id="b9cf7-153">D.</span></span> <span data-ttu-id="b9cf7-154">XML スキーマ コレクションに対する TAKE OWNERSHIP 権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-154">Granting TAKE OWNERSHIP permission on an XML schema collection</span></span>  
 <span data-ttu-id="b9cf7-155">次の例では、XML スキーマの所有権を特定のユーザーから別のユーザーに移す方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-155">The following example shows how to transfer XML schema ownership from one user to another.</span></span> <span data-ttu-id="b9cf7-156">より興味深い例にするために、この例の 2 人のユーザーは異なる既定リレーショナル スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-156">To make the example more interesting, the users in this example work in different default relational schemas.</span></span>  
  
 <span data-ttu-id="b9cf7-157">この例の内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-157">This example does the following:</span></span>  
  
-   <span data-ttu-id="b9cf7-158">2 つのリレーショナル スキーマ `dbo` および `myOtherDBSchema`を備えた 1 つのデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-158">Creates a database with two relational schemas, `dbo` and `myOtherDBSchema`).</span></span>  
  
-   <span data-ttu-id="b9cf7-159">`TestLogin1` と `TestLogin2`という 2 人のユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-159">Creates two users, `TestLogin1` and `TestLogin2`.</span></span> <span data-ttu-id="b9cf7-160">`TestLogin2` を、 `myOtherDBSchema` リレーショナル スキーマの所有者にします。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-160">`TestLogin2` is made the owner of the `myOtherDBSchema` relational schema.</span></span>  
  
-   <span data-ttu-id="b9cf7-161">`TestLogin1` は、 `dbo` リレーショナル スキーマに XML スキーマ コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-161">`TestLogin1` creates an XML schema collection in the `dbo` relational schema.</span></span>  
  
-   <span data-ttu-id="b9cf7-162">`TestLogin1` はその XML スキーマ コレクションに対する `TAKE OWNERSHIP` 権限を `TestLogin2`に許可します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-162">`TestLogin1` then gives `TAKE OWNERSHIP` permission on the XML schema collection to `TestLogin2`.</span></span>  
  
-   <span data-ttu-id="b9cf7-163">`TestLogin2` は、 `myOtherDBSchema`の XML スキーマ コレクションの所有者になります。このとき、XML スキーマ コレクションのリレーショナル スキーマは変更されません。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-163">`TestLogin2` becomes the owner of the XML schema collection in `myOtherDBSchema`, without changing the relational schema of the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 with password='SQLSvrPwd1'  
GO  
CREATE LOGIN TestLogin2 with password='SQLSvrPwd2'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
-- Create users in the database. Note TestLogin2's default schema is  
-- myOtherDBSchema.  
CREATE USER TestLogin1  
GO  
CREATE USER TestLogin2 WITH DEFAULT_SCHEMA=myOtherDBSchema  
GO  
-- TestLogin2 will own myOtherDBSchema relational schema.  
ALTER AUTHORIZATION ON SCHEMA::myOtherDBSchema TO TestLogin2  
GO  
  
-- For TestLogin1 to create XML schema collection, the following  
-- permission is required.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- Now TestLogin1 can create an XML schema collection.  
setuser 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
 <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"   
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
 </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Grant TAKE OWNERSHIP to TestLogin2.  
SETUSER  
GO  
GRANT TAKE OWNERSHIP ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Verify the owner. Note the UserName and Principal_id is null.   
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections   
      JOIN sys.schemas   
      ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- TestLogin2 can take ownership now.  
setuser 'TestLogin2'  
GO  
ALTER AUTHORIZATION ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Note that although TestLogin2 is the owner,the XML schema collection   
-- is still in dbo.  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
      sys.schemas.name as RelSchemaName,*   
FROM sys.xml_schema_collections JOIN sys.schemas   
     ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
  
-- TestLogin2 moves the collection from dbo to myOtherDBSchema relational schema.  
-- TestLogin2 already has all necessary permissions.  
-- 1) TestLogin2 owns the destination relational schema so he can alter it.  
-- 2) TestLogin2 owns the XML schema collection (therefore, has CONTROL permission).  
ALTER SCHEMA myOtherDBSchema  
TRANSFER XML SCHEMA COLLECTION::dbo.myTestSchemaCollection  
GO  
  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections JOIN sys.schemas   
       ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- Final cleanup   
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
DROP LOGIN TestLogin2  
go   
```  
  
### <a name="e-granting-view-definition-permission-on-an-xml-schema-collection"></a><span data-ttu-id="b9cf7-164">E.</span><span class="sxs-lookup"><span data-stu-id="b9cf7-164">E.</span></span> <span data-ttu-id="b9cf7-165">XML スキーマ コレクションに対する VIEW DEFINITION 権限の許可</span><span class="sxs-lookup"><span data-stu-id="b9cf7-165">Granting VIEW DEFINITION permission on an XML schema collection</span></span>  
 <span data-ttu-id="b9cf7-166">次の例では、XML スキーマ コレクションに対する VIEW DEFINITION 権限を許可する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9cf7-166">The following example shows how to grant VIEW DEFINITION permissions for an XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
IF EXISTS( SELECT * FROM sysdatabases WHERE name='permissionsDB' )  
   DROP DATABASE permissionsDB  
GO  
IF EXISTS( SELECT * FROM sys.sql_logins WHERE name='schemaUser' )  
   DROP LOGIN schemaUser  
GO  
CREATE DATABASE permissionsDB  
GO  
CREATE LOGIN schemaUser WITH PASSWORD='Pass#123',DEFAULT_DATABASE=permissionsDB  
GO  
GRANT CONNECT SQL TO schemaUser  
GO  
USE permissionsDB  
GO  
CREATE USER schemaUser WITH DEFAULT_SCHEMA=dbo  
GO  
CREATE XML SCHEMA COLLECTION MySC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns"  
xmlns:ns="http://ns">  
  
   <simpleType name="ListOfIntegers">  
      <list itemType="integer"/>  
   </simpleType>  
  
   <element name="root" type="ns:ListOfIntegers"/>  
  
   <element name="gRoot" type="gMonth"/>  
  
</schema>  
'  
GO  
-- schemaUser cannot see the contents of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
  
-- Grant schemaUser VIEW DEFINITION and REFERENCES permissions  
-- on the XML schema collection.  
SETUSER  
GO  
GRANT VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
GRANT REFERENCES ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
-- Now schemaUser can see the content of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
-- Revoke schemaUser VIEW DEFINITION permissions  
-- on the XML schema collection.  
SETUSER  
GO  
REVOKE VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC FROM schemaUser  
GO  
-- Now schemaUser cannot see the contents of   
-- the collection.  
setuser 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9cf7-167">参照</span><span class="sxs-lookup"><span data-stu-id="b9cf7-167">See Also</span></span>  
 <span data-ttu-id="b9cf7-168">[XML データ &#40;SQL Server&#41;](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b9cf7-168">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="b9cf7-169">[型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b9cf7-169">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="b9cf7-170">[XML スキーマ コレクション &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b9cf7-170">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="b9cf7-171">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="b9cf7-171">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
