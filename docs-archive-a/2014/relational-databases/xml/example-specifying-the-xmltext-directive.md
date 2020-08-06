---
title: '例: XMLTEXT ディレクティブの指定 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XMLTEXT directive
ms.assetid: e78008ec-51e8-4fd1-b86f-1058a781de17
author: rothja
ms.author: jroth
ms.openlocfilehash: d14299ad3e989c6600434b857a650fbbddd7a590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644349"
---
# <a name="example-specifying-the-xmltext-directive"></a><span data-ttu-id="5c483-102">例:XMLTEXT ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="5c483-102">Example: Specifying the XMLTEXT Directive</span></span>
  <span data-ttu-id="5c483-103">この例では、EXPLICIT モードを使用した `SELECT` ステートメントで、`XMLTEXT` ディレクティブによりオーバーフロー列のデータを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5c483-103">This example illustrates how data in the overflow column is addressed by using the `XMLTEXT` directive in a `SELECT` statement using EXPLICIT mode.</span></span>  
  
 <span data-ttu-id="5c483-104">`Person` テーブルについて考えます。</span><span class="sxs-lookup"><span data-stu-id="5c483-104">Consider the `Person` table.</span></span> <span data-ttu-id="5c483-105">このテーブルには、XML ドキュメントの未使用部分を格納している `Overflow` 列があります。</span><span class="sxs-lookup"><span data-stu-id="5c483-105">This table has an `Overflow` column that stores the unconsumed part of the XML document.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE TABLE Person(PersonID varchar(5), PersonName varchar(20), Overflow nvarchar(200));  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
   ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P">content</SomeTag>');  
```  
  
 <span data-ttu-id="5c483-106">このクエリでは、 `Person` テーブルから列を取得します。</span><span class="sxs-lookup"><span data-stu-id="5c483-106">This query retrieves columns from the `Person` table.</span></span> <span data-ttu-id="5c483-107">`Overflow` 列には *AttributeName* が指定されていませんが、ユニバーサル テーブルの列名の一部として、  *ディレクティブ*`XMLTEXT` が設定されています。</span><span class="sxs-lookup"><span data-stu-id="5c483-107">For the `Overflow` column, *AttributeName* is not specified, but *directive* is set to `XMLTEXT` as part of providing a universal table column name.</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEST] -- No AttributeName; XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="5c483-108">結果の XML ドキュメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5c483-108">In the resulting XML document:</span></span>  
  
-   <span data-ttu-id="5c483-109">`Overflow` 列には *AttributeName* が指定されていませんが、`xmltext` ディレクティブが指定されているので、<`overflow`> 要素の属性は、囲み要素である <`Parent`> の属性リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-109">Because *AttributeName* is not specified for the `Overflow` column and the `xmltext` directive is specified, the attributes in the <`overflow`> element are appended to the attribute list of the enclosing <`Parent`> element.</span></span>  
  
-   <span data-ttu-id="5c483-110"><`xmltext`> 要素の `PersonID` 属性は、同じ要素レベルで取得される `PersonID` 属性と競合するので、<`xmltext`> 要素の属性は無視されます。これは、`PersonID` 属性の値が NULL であっても同じです。</span><span class="sxs-lookup"><span data-stu-id="5c483-110">Because the `PersonID`attribute in the <`xmltext`> element conflicts with the `PersonID` attribute retrieved on the same element level, the attribute in the <`xmltext`> element is ignored, even if `PersonID` is NULL.</span></span> <span data-ttu-id="5c483-111">一般的に、属性はオーバーフローに含まれる同じ名前の属性をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5c483-111">Generally, an attribute overrides an attribute of the same name in the overflow.</span></span>  
  
 <span data-ttu-id="5c483-112">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5c483-112">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">content</Parent>`  
  
 <span data-ttu-id="5c483-113">オーバーフロー データにサブ要素がある場合に同じクエリを指定すると、`Overflow` 列内のサブ要素は、囲み要素である <`Parent`> のサブ要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-113">If the overflow data has subelements and the same query is specified, the subelements in the `Overflow` column are added as the subelements of the enclosing <`Parent`> element.</span></span>  
  
 <span data-ttu-id="5c483-114">たとえば、次のように `Person` テーブルのデータを変更したとします。`Overflow` 列にサブ要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c483-114">For example, change the data in the `Person` table so that the `Overflow` column now has subelements.</span></span>  
  
```  
USE tempdb;  
GO  
TRUNCATE TABLE Person;  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
    ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P"><name>PersonName</name></SomeTag>');  
```  
  
 <span data-ttu-id="5c483-115">同じクエリを実行すると、<`xmltext`> 要素のサブ要素は、囲み要素である <`Parent`> のサブ要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-115">If the same query is executed, the subelements in the <`xmltext`> element are added as subelements of the enclosing <`Parent`> element:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEXT] -- no AttributeName, XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="5c483-116">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5c483-116">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `</Parent>`  
  
 <span data-ttu-id="5c483-117">*AttributeName* と `xmltext` ディレクティブの両方を指定した場合、<`overflow`> 要素の属性は、囲み要素である <`Parent`> のサブ要素の属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-117">If *AttributeName* is specified with the `xmltext` directive, the attributes of the <`overflow`> element are added as attributes of the subelements of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="5c483-118">*AttributeName*に指定された名前がサブ要素の名前になります。</span><span class="sxs-lookup"><span data-stu-id="5c483-118">The name specified for *AttributeName* becomes the name of the subelement.</span></span>  
  
 <span data-ttu-id="5c483-119">このクエリでは、 *AttributeName*、<`overflow`> がディレクティブと共に指定されてい `xmltext` ます。</span><span class="sxs-lookup"><span data-stu-id="5c483-119">In this query, *AttributeName*, <`overflow`>, is specified together with the `xmltext` directive:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!overflow!XMLTEXT] -- Overflow is AttributeName  
                      -- XMLTEXT is a directive  
FROM Person  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="5c483-120">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5c483-120">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe">`  
  
 `<overflow attr1="data">content</overflow>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe">`  
  
 `<overflow attr2="data" />`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe">`  
  
 `<overflow attr3="data" PersonID="P">`  
  
 `<name>PersonName</name>`  
  
 `</overflow>`  
  
 `</Parent>`  
  
 <span data-ttu-id="5c483-121">このクエリでは、`PersonName` 属性に *element* ディレクティブを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c483-121">In this query element, *directive* is specified for `PersonName` attribute.</span></span> <span data-ttu-id="5c483-122">これにより、`PersonName` 属性は、囲み要素である <`Parent`> 要素のサブ要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-122">This results in `PersonName` being added as a subelement of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="5c483-123"><`xmltext`> の属性も、依然として、囲み要素 <`Parent`> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-123">The attributes of the <`xmltext`> are still appended to the enclosing <`Parent`> element.</span></span> <span data-ttu-id="5c483-124"><`overflow`> 要素の内容 (サブ要素) は、囲み要素である <`Parent`> 要素の他のサブ要素の前に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c483-124">The contents of the <`overflow`> element, subelements, are prepended to the other subelements of the enclosing <`Parent`> elements.</span></span>  
  
```  
SELECT 1      AS Tag, NULL as parent,  
       PersonID   AS [Parent!1!PersonID],  
       PersonName AS [Parent!1!PersonName!element], -- element directive  
       Overflow   AS [Parent!1!!XMLTEXT]  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="5c483-125">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5c483-125">This is the result:</span></span>  
  
 `<Parent PersonID="P1" attr1="data">content<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" attr2="data">`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 <span data-ttu-id="5c483-126">`XMLTEXT` 列のデータにルート要素の属性が含まれている場合、これらの属性は XML データ スキーマに反映されません。結果の XML ドキュメントのその部分に関して、MSXML パーサーによる検証は行われません。</span><span class="sxs-lookup"><span data-stu-id="5c483-126">If the `XMLTEXT` column data contains attributes on the root element, these attributes are not shown in the XML data schema and the MSXML parser does not validate the resulting XML document fragment.</span></span> <span data-ttu-id="5c483-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5c483-127">For example:</span></span>  
  
```  
SELECT 1 AS Tag,  
       0 ASParent,  
       N'<overflow a="1"/>' AS 'overflow!1!!xmltext'  
FOR XML EXPLICIT, xmldata;  
```  
  
 <span data-ttu-id="5c483-128">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5c483-128">This is the result.</span></span> <span data-ttu-id="5c483-129">返されたスキーマでは、オーバーフロー要素の属性 `a` が欠落している点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="5c483-129">Note that in the returned schema, the overflow attribute `a` is missing from the schema:</span></span>  
  
 `<Schema name="Schema2"`  
  
 `xmlns="urn:schemas-microsoft-com:xml-data"`  
  
 `xmlns:dt="urn:schemas-microsoft-com:datatypes">`  
  
 `<ElementType name="overflow" content="mixed" model="open">`  
  
 `</ElementType>`  
  
 `</Schema>`  
  
 `<overflow xmlns="x-schema:#Schema2" a="1">`  
  
 `</overflow>`  
  
## <a name="see-also"></a><span data-ttu-id="5c483-130">参照</span><span class="sxs-lookup"><span data-stu-id="5c483-130">See Also</span></span>  
 [<span data-ttu-id="5c483-131">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="5c483-131">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
