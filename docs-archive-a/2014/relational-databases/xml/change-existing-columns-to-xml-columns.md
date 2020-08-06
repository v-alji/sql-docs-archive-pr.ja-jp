---
title: 既存の列を XML 列に変更する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 32447851fcfe2a54143a028a94539532bba6708d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631701"
---
# <a name="change-existing-columns-to-xml-columns"></a><span data-ttu-id="8fa32-102">既存の列を XML 列に変更する方法</span><span class="sxs-lookup"><span data-stu-id="8fa32-102">Change Existing Columns to XML Columns</span></span>
  <span data-ttu-id="8fa32-103">`xml` データ型は ALTER TABLE ステートメントでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8fa32-103">The ALTER TABLE statement supports the `xml` data type.</span></span> <span data-ttu-id="8fa32-104">たとえば、文字列型の列を `xml` データ型に変更できます。</span><span class="sxs-lookup"><span data-stu-id="8fa32-104">For example, you can alter any string type column to the `xml` data type.</span></span> <span data-ttu-id="8fa32-105">このような場合、列に格納されるドキュメントは正しい形式でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8fa32-105">Note that in these cases, the documents contained in the column must be well formed.</span></span> <span data-ttu-id="8fa32-106">また、列の型を文字列から型指定された xml に変更する場合、列内のドキュメントは指定した XSD スキーマに対して検証されます。</span><span class="sxs-lookup"><span data-stu-id="8fa32-106">Also, if you are changing the type of the column from string to typed xml, the documents in the column are validated against the specified XSD schemas.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max))  
GO  
INSERT INTO T   
VALUES (1, '<Root><Product ProductID="1"/></Root>')  
GO  
ALTER TABLE T   
ALTER COLUMN Col2 xml  
GO  
```  
  
 <span data-ttu-id="8fa32-107">`xml` 型の列は、型指定されていない XML から型指定された XML に変更できます。</span><span class="sxs-lookup"><span data-stu-id="8fa32-107">You can change an `xml` type column from untyped XML to typed XML.</span></span> <span data-ttu-id="8fa32-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8fa32-108">For example:</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T   
values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>')  
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection)  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8fa32-109">このスクリプトは [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに対して実行されます。これは、XML スキーマ コレクション `Production.ProductDescriptionSchemaCollection`が [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの一部として作成されるからです。</span><span class="sxs-lookup"><span data-stu-id="8fa32-109">The script will run against [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, because the XML schema collection, `Production.ProductDescriptionSchemaCollection`, is created as part of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="8fa32-110">上記の例では、列に保存されているすべてのインスタンスは指定したコレクションの XSD スキーマで検証と型指定が行われます。</span><span class="sxs-lookup"><span data-stu-id="8fa32-110">In the previous example, all the instances stored in the column are validated and typed against the XSD schemas in the specified collection.</span></span> <span data-ttu-id="8fa32-111">指定したスキーマに適合しない XML インスタンスが列に含まれている場合、 `ALTER TABLE` ステートメントは失敗するので、型指定されていない XML 列を型指定された XML に変更することができません。</span><span class="sxs-lookup"><span data-stu-id="8fa32-111">If the column contains one or more XML instances that are invalid with regard to the specified schema, the `ALTER TABLE` statement will fail and you will not be able to change your untyped XML column into typed XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8fa32-112">大きなテーブルの場合、`xml` 型の列を変更すると処理の負担が大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="8fa32-112">If a table is large, modifying an `xml` type column can be costly.</span></span> <span data-ttu-id="8fa32-113">これは、各ドキュメントについて、形式が正しいか、型指定された XML であるかどうかを検証する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="8fa32-113">This is because each document must be checked for being well formed and, for typed XML, must also be validated.</span></span>  
  
 <span data-ttu-id="8fa32-114">型指定された XML に関する詳細については、「 [型指定された XML と型指定されていない XML の比較](compare-typed-xml-to-untyped-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fa32-114">For more information about typed XML, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
  
