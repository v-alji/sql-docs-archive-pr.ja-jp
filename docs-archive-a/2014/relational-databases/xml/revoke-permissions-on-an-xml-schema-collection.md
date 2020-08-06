---
title: XML スキーマ コレクションに対する権限の取り消し | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- revoking permissions [SQL Server]
ms.assetid: 4e542b70-2d56-4a65-8a39-96a1ed477ca6
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ab37c915f14207376e0c4a9582611bf8e65e0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713909"
---
# <a name="revoke-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="fd0dc-102">XML スキーマ コレクションに対する権限の取り消し</span><span class="sxs-lookup"><span data-stu-id="fd0dc-102">Revoke Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="fd0dc-103">XML スキーマ コレクションを作成する権限は、次のいずれかの方法で取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-103">The permission to create an XML schema collection can be revoked by using one of the following:</span></span>  
  
-   <span data-ttu-id="fd0dc-104">リレーショナル スキーマの ALTER 権限を取り消します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-104">Revoke the ALTER permission for the relational schema.</span></span> <span data-ttu-id="fd0dc-105">その結果、プリンシパルはリレーショナル スキーマで XML スキーマ コレクションを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-105">Then, the principal cannot create an XML schema collection in the relational schema.</span></span> <span data-ttu-id="fd0dc-106">ただし、同じデータベースの他のリレーショナル スキーマでは作成できます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-106">However, the principal can still do so in other relational schemas in the same database.</span></span>  
  
-   <span data-ttu-id="fd0dc-107">プリンシパルのデータベースの ALTER ANY SCHEMA 権限を取り消します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-107">Revoke the ALTER ANY SCHEMA permission on the database for the principal.</span></span> <span data-ttu-id="fd0dc-108">その結果、プリンシパルはデータベースのどこでも XML スキーマ コレクションを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-108">Then, the principal cannot create an XML schema collection anywhere in the database.</span></span>  
  
-   <span data-ttu-id="fd0dc-109">プリンシパルのデータベースの CREATE XML SCHEMA COLLECTION 権限または ALTER XML SCHEMA COLLECTION 権限を取り消します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-109">Revoke the CREATE XML SCHEMA COLLECTION or ALTER XML SCHEMA COLLECTION permission on the database for the principal.</span></span> <span data-ttu-id="fd0dc-110">これにより、プリンシパルはデータベース内に XML スキーマ コレクションをインポートできなくなります。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-110">This prevents the principal from importing an XML schema collection within the database.</span></span> <span data-ttu-id="fd0dc-111">データベースの ALTER 権限または CONTROL 権限を取り消しても、同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-111">Revoking the ALTER or CONTROL permission on the database has the same effect.</span></span>  
  
## <a name="revoking-permissions-on-an-existing-xml-schema-collection-object"></a><span data-ttu-id="fd0dc-112">既存の XML スキーマ コレクション オブジェクトに対する権限の取り消し</span><span class="sxs-lookup"><span data-stu-id="fd0dc-112">Revoking Permissions on an Existing XML Schema Collection Object</span></span>  
 <span data-ttu-id="fd0dc-113">次に、XML スキーマ コレクションで取り消し可能な権限と権限を取り消した結果を示します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-113">Following are the permissions that can be revoked on an XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="fd0dc-114">ALTER 権限を取り消すと、XML スキーマ コレクションのコンテンツを変更するプリンシパルの権限が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-114">Revoking the ALTER permission revokes a principal's ability to modify the content of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="fd0dc-115">TAKE OWNERSHIP 権限を取り消すと、XML スキーマ コレクションの所有権を転送するプリンシパルの権限が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-115">Revoking the TAKE OWNERSHIP permission revokes a principal's ability to transfer ownership of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="fd0dc-116">REFERENCES 権限を取り消すと、テーブルやビュー内の xml 型の列やパラメーターを、型指定または制約するために XML スキーマ コレクションを使用するプリンシパルの権限が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-116">Revoking the REFERENCES permission revokes a principal's ability to use the XML schema collection for typing or constraining xml type columns, in tables and views, and parameters.</span></span> <span data-ttu-id="fd0dc-117">また、他の XML スキーマ コレクションからこのスキーマ コレクションを参照する権限も取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-117">It also revokes the permission to refer to this schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="fd0dc-118">VIEW DEFINITION 権限を取り消すと、XML スキーマ コレクションのコンテンツを表示するプリンシパルの権限が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-118">Revoking the VIEW DEFINITION permission revokes a principal's ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="fd0dc-119">EXECUTE 権限を取り消すと、XML コレクションによって型指定または制約された列、変数、およびパラメーターの値を挿入または更新するプリンシパルの権限が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-119">Revoking the EXECUTE permission revokes a principal's ability to insert or update values in columns, variables, and parameters that are typed or constrained by the XML collection.</span></span> <span data-ttu-id="fd0dc-120">これにより、そのような **xml** 型の列、変数、またはパラメーターにクエリする権限も取り消されます。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-120">It also revokes the ability to query such **xml** type columns, variables, or parameters.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fd0dc-121">例</span><span class="sxs-lookup"><span data-stu-id="fd0dc-121">Examples</span></span>  
 <span data-ttu-id="fd0dc-122">次の例に示すシナリオでは、XML スキーマ権限のしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-122">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="fd0dc-123">各例では、必要なテスト データベース、リレーショナル スキーマ、およびログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-123">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="fd0dc-124">それらのログインには、必要な XML スキーマ コレクション権限が許可されています。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-124">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="fd0dc-125">最後に必要なクリーンアップを行います。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-125">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-revoking-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="fd0dc-126">A.</span><span class="sxs-lookup"><span data-stu-id="fd0dc-126">A.</span></span> <span data-ttu-id="fd0dc-127">XML スキーマ コレクションを作成するための権限の取り消し</span><span class="sxs-lookup"><span data-stu-id="fd0dc-127">Revoking permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="fd0dc-128">この例では、ログインとサンプル データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-128">This example creates a login and a sample database.</span></span> <span data-ttu-id="fd0dc-129">データベースにはリレーショナル スキーマも追加します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-129">It also adds a relational schema in the database.</span></span> <span data-ttu-id="fd0dc-130">最初に、ログインに両方のリレーショナル スキーマの ALTER 権限を許可し、XML スキーマ コレクションを作成するのに必要なその他の権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-130">Initially, the login is granted ALTER permission on both relational schemas and other necessary permissions to create XML schema collections.</span></span> <span data-ttu-id="fd0dc-131">次に、データベースのリレーショナル スキーマのいずれかの ALTER 権限を取り消します。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-131">The example then revokes the ALTER permission on one of the relational schemas in the database.</span></span> <span data-ttu-id="fd0dc-132">これにより、このログインは XML スキーマ コレクションを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fd0dc-132">This prevents the login from creating an XML schema collection.</span></span>  
  
```  
setuser  
go  
create login TestLogin1 with password='SQLSvrPwd1'  
go  
create database SampleDBForSchemaPermissions  
go  
use SampleDBForSchemaPermissions  
go  
-- Create another relational schema in the db (in addition to dbo schema)  
CREATE SCHEMA myOtherDBSchema  
go  
CREATE USER TestLogin1  
go  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed  
-- CREATE XML SCHEMA is a database level permission  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
go  
-- Now TestLogin1 can import an XML schema collection in both relational schemas.  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- TestLogin1 can create XML schema collection in myOtherDBSchema relational schema  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- Let us drop XML schema collections from both relational schemas  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
go  
DROP XML SCHEMA COLLECTION dbo.myTestSchemaCollection  
go  
-- now REVOKE permission from TestLogin1 to alter myOtherDBSchema  
setuser  
go  
REVOKE ALTER ON SCHEMA::myOtherDBSchema FROM TestLogin1  
go  
-- now TestLogin1 cannot create xml schema collection in myOtherDBSchema  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- TestLogin1 can still create XML schema collections in dbo  
-- It cannot create XML schema collections anywhere in the database  
-- if we REVOKE CREATE XML SCHEMA COLLECTION permission  
SETUSER  
go  
REVOKE CREATE XML SCHEMA COLLECTION FROM TestLogin1  
go  
  
setuser 'TestLogin1'  
go  
-- the following now should fail  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- Final cleanup  
SETUSER  
go  
USE master  
go  
DROP DATABASE SampleDBForSchemaPermissions  
go  
DROP LOGIN TestLogin1  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd0dc-133">参照</span><span class="sxs-lookup"><span data-stu-id="fd0dc-133">See Also</span></span>  
 <span data-ttu-id="fd0dc-134">[XML データ &#40;SQL Server&#41;](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd0dc-134">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="fd0dc-135">[型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="fd0dc-135">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="fd0dc-136">[XML スキーマ コレクション &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd0dc-136">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="fd0dc-137">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="fd0dc-137">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
