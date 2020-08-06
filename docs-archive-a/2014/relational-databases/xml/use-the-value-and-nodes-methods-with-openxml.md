---
title: OPENXML での value() メソッドと nodes() メソッドの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- OpenXML method [XML in SQL Server]
- value method [XML in SQL Server]
- nodes method [XML in SQL Server]
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5dccf5a7ef626d1f1a42d011d22ba77807b34eba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738029"
---
# <a name="use-the-value-and-nodes-methods-with-openxml"></a><span data-ttu-id="27efe-102">OPENXML での value() メソッドと nodes() メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="27efe-102">Use the value() and nodes() Methods with OPENXML</span></span>
  <span data-ttu-id="27efe-103">SELECT 句では、データ型に対して複数の**value ()** メソッドを使用して `xml` 、抽出された値の行セットを生成できます。 **SELECT**</span><span class="sxs-lookup"><span data-stu-id="27efe-103">You can use multiple **value()** methods on `xml` data type in a **SELECT** clause to generate a rowset of extracted values.</span></span> <span data-ttu-id="27efe-104">**nodes()** メソッドは、追加のクエリに使用するために選択した各ノードの内部参照を生成します。</span><span class="sxs-lookup"><span data-stu-id="27efe-104">The **nodes()** method yields an internal reference for each selected node that can be used for additional query.</span></span> <span data-ttu-id="27efe-105">**nodes()** メソッドと **value()** メソッドを併用すると、行セットに複数の列があるとき、および行セット生成のためのパス式が複雑なときに、効率的に行セットを生成できます。</span><span class="sxs-lookup"><span data-stu-id="27efe-105">The combination of the **nodes()** and **value()** methods can be more efficient in generating the rowset when it has several columns and, perhaps, when the path expressions used in its generation are complex.</span></span>  
  
 <span data-ttu-id="27efe-106">**Nodes ()** メソッドを使用すると、特殊な `xml` データ型のインスタンスが生成されます。それぞれのインスタンスのコンテキストは、選択した別のノードに設定されます。</span><span class="sxs-lookup"><span data-stu-id="27efe-106">The **nodes()** method yields instances of a special `xml` data type, each of which has its context set to a different selected node.</span></span> <span data-ttu-id="27efe-107">このような XML インスタンスは、**query()** メソッド、**value()** メソッド、**nodes()** メソッド、および **exist()** メソッドをサポートし、**count(\*)** 集計で使用できます。</span><span class="sxs-lookup"><span data-stu-id="27efe-107">This kind of XML instance supports **query()**, **value()**, **nodes()**, and **exist()** methods and can be used in **count(\*)** aggregations.</span></span> <span data-ttu-id="27efe-108">それ以外の使用方法ではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="27efe-108">All other uses cause an error.</span></span>  
  
## <a name="example-using-nodes"></a><span data-ttu-id="27efe-109">例:nodes() の使用</span><span class="sxs-lookup"><span data-stu-id="27efe-109">Example: Using nodes()</span></span>  
 <span data-ttu-id="27efe-110">名が "David" ではない著者の姓と名を抽出するとします。</span><span class="sxs-lookup"><span data-stu-id="27efe-110">Assume that you want to extract the first and last names of authors, and the first name is not "David".</span></span> <span data-ttu-id="27efe-111">2 つの列 FirstName および LastName から構成される行セットとしてこの情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="27efe-111">Additionally, you want to extract this information as a rowset that contains two columns, FirstName and LastName.</span></span> <span data-ttu-id="27efe-112">そのためには次に示すように、 **nodes()** メソッドと **value()** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="27efe-112">By using **nodes()** and **value()** methods, you can accomplish this as shown in the following:</span></span>  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 <span data-ttu-id="27efe-113">この例では、 `nodes('//author')` により各 XML インスタンスの `<author>` 要素への参照が格納された行セットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="27efe-113">In this example, `nodes('//author')` yields a rowset of references to `<author>` elements for each XML instance.</span></span> <span data-ttu-id="27efe-114">その参照について **value()** メソッドを評価することで、著者の姓および名を取得します。</span><span class="sxs-lookup"><span data-stu-id="27efe-114">The first and last names of authors are obtained by evaluating **value()** methods relative to those references.</span></span>  
  
 <span data-ttu-id="27efe-115">SQL Server 2000 には、 **OpenXml()** を使用して XML インスタンスから行セットを生成する機能があります。</span><span class="sxs-lookup"><span data-stu-id="27efe-115">SQL Server 2000 provides the capability for generating a rowset from an XML instance by using **OpenXml()**.</span></span> <span data-ttu-id="27efe-116">行セットにリレーショナル スキーマを指定し、その中の列に XML インスタンス内の値をどのようにマップするかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="27efe-116">You can specify the relational schema for the rowset and how values inside the XML instance map to columns in the rowset.</span></span>  
  
## <a name="example-using-openxml-on-the-xml-data-type"></a><span data-ttu-id="27efe-117">例:xml データ型での OpenXml() の使用</span><span class="sxs-lookup"><span data-stu-id="27efe-117">Example: Using OpenXml() on the xml Data Type</span></span>  
 <span data-ttu-id="27efe-118">上記の例のクエリは、 **OpenXml()** を使用して次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="27efe-118">The query can be rewritten from the previous example by using **OpenXml()** as shown in the following.</span></span> <span data-ttu-id="27efe-119">そのためには、各 XML インスタンスを読み取って XML 変数に代入し、OpenXML に渡すカーソルを作成します。</span><span class="sxs-lookup"><span data-stu-id="27efe-119">This is done by creating a cursor that reads each XML instance into an XML variable and then applies OpenXML to it:</span></span>  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 <span data-ttu-id="27efe-120">**OpenXml()** によりメモリ内表現が作成され、クエリ プロセッサの代わりに作業テーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="27efe-120">**OpenXml()** creates an in-memory representation and uses work tables instead of the query processor.</span></span> <span data-ttu-id="27efe-121">この関数は XQuery エンジンではなく MSXML Version 3.0 の XPath Version 1.0 プロセッサを使用します。</span><span class="sxs-lookup"><span data-stu-id="27efe-121">It relies on the XPath version 1.0 processor of MSXML version 3.0 instead of the XQuery engine.</span></span> <span data-ttu-id="27efe-122">同一の XML インスタンスであっても、 **OpenXml()** の複数の呼び出しで作業テーブルを共有することはありません。</span><span class="sxs-lookup"><span data-stu-id="27efe-122">The work tables are not shared among multiple calls to **OpenXml()**, even on the same XML instance.</span></span> <span data-ttu-id="27efe-123">このため、スケーラビリティが制限されます。</span><span class="sxs-lookup"><span data-stu-id="27efe-123">This limits its scalability.</span></span> <span data-ttu-id="27efe-124">**OpenXml()** を使用すると、WITH 句を指定しない場合に XML データのエッジ テーブル形式にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="27efe-124">**OpenXml()** allows you to access an edge table format for the XML data when the WITH clause is not specified.</span></span> <span data-ttu-id="27efe-125">また、別の "オーバーフロー" 列内の残りの XML 値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="27efe-125">Also, it allows you to use the remaining XML value in a separate, "overflow" column.</span></span>  
  
 <span data-ttu-id="27efe-126">**nodes()** 関数と **value()** 関数を組み合わせると、XML インデックスを効果的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="27efe-126">The combination of **nodes()** and **value()** functions uses XML indexes effectively.</span></span> <span data-ttu-id="27efe-127">つまり、 **OpenXml**よりもスケーラビリティに優れています。</span><span class="sxs-lookup"><span data-stu-id="27efe-127">As a result, this combination can exhibit more scalability than **OpenXml**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27efe-128">参照</span><span class="sxs-lookup"><span data-stu-id="27efe-128">See Also</span></span>  
 [<span data-ttu-id="27efe-129">OPENXML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="27efe-129">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
