---
title: FOR XML での RAW モードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: rothja
ms.author: jroth
ms.openlocfilehash: b2908a98336ec8a6e12029ad471f22a33d7a4dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738065"
---
# <a name="use-raw-mode-with-for-xml"></a><span data-ttu-id="2eec9-102">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="2eec9-102">Use RAW Mode with FOR XML</span></span>
  <span data-ttu-id="2eec9-103">RAW モードでは、クエリの結果セットの各行が XML 要素に変換されます。この XML 要素は、汎用識別子 \<row> を持つか、必要に応じて要素名が付けられます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-103">RAW mode transforms each row in the query result set into an XML element that has the generic identifier \<row>, or the optionally provided element name.</span></span> <span data-ttu-id="2eec9-104">既定では、NULL 以外の行セットの各列の値が \<row> 要素の属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-104">By default, each column value in the rowset that is not NULL is mapped to an attribute of the \<row> element.</span></span> <span data-ttu-id="2eec9-105">FOR XML 句に ELEMENTS ディレクティブが追加されると、各列の値が \<row> 要素のサブ要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-105">If the ELEMENTS directive is added to the FOR XML clause, each column value is mapped to a subelement of the \<row> element.</span></span> <span data-ttu-id="2eec9-106">必要に応じて ELEMENTS ディレクティブと共に XSINIL オプションを指定して、xsi:nil=`"`true`"`の属性を持つ要素に結果セットの NULL 列値をマップできます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-106">Together with the ELEMENTS directive, you can optionally specify the XSINIL option to map NULL column values in the result set to an element that has the attribute, xsi:nil=`"`true`"`.</span></span>  
  
 <span data-ttu-id="2eec9-107">結果として生成される XML のスキーマを要求できます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-107">You can request a schema for the resulting XML.</span></span> <span data-ttu-id="2eec9-108">XMLDATA オプションを指定すると、インライン XDR スキーマが返されます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-108">Specifying the XMLDATA option returns an in-line XDR schema.</span></span> <span data-ttu-id="2eec9-109">XMLSCHEMA オプションを指定すると、インライン XSD スキーマが返されます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-109">Specifying the XMLSCHEMA option returns an in-line XSD schema.</span></span> <span data-ttu-id="2eec9-110">スキーマはデータの先頭に示されます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-110">The schema appears at the start of the data.</span></span> <span data-ttu-id="2eec9-111">その結果、トップレベルの要素ごとにスキーマの名前空間参照が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="2eec9-111">In the result, the schema namespace reference is repeated for every top-level element.</span></span>  
  
 <span data-ttu-id="2eec9-112">バイナリ データを base64 エンコード形式で返すには、BINARY BASE64 オプションを FOR XML 句に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2eec9-112">The BINARY BASE64 option must be specified in the FOR XML clause to return the binary data in base64-encoded format.</span></span> <span data-ttu-id="2eec9-113">RAW モードでは、BINARY BASE64 オプションを指定しないでバイナリ データを取得すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2eec9-113">In RAW mode, retrieving binary data without specifying the BINARY BASE64 option will result in an error.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2eec9-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2eec9-114">In This Section</span></span>  
 <span data-ttu-id="2eec9-115">このセクションには、次の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2eec9-115">This section contains the following examples:</span></span>  
  
-   [<span data-ttu-id="2eec9-116">例: XML での製品モデル情報の取得</span><span class="sxs-lookup"><span data-stu-id="2eec9-116">Example: Retrieving Product Model Information as XML</span></span>](example-retrieving-product-model-information-as-xml.md)  
  
-   [<span data-ttu-id="2eec9-117">例: ELEMENTS ディレクティブで XSINIL を指定する</span><span class="sxs-lookup"><span data-stu-id="2eec9-117">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [<span data-ttu-id="2eec9-118">例: XMLDATA オプションと XMLSCHEMA オプションを使用した結果としてのスキーマの要求</span><span class="sxs-lookup"><span data-stu-id="2eec9-118">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [<span data-ttu-id="2eec9-119">例: バイナリ データの取得</span><span class="sxs-lookup"><span data-stu-id="2eec9-119">Example: Retrieving Binary Data</span></span>](example-retrieving-binary-data.md)  
  
-   [<span data-ttu-id="2eec9-120">例: &#60;row&#62; 要素の名前を変更する</span><span class="sxs-lookup"><span data-stu-id="2eec9-120">Example: Renaming the &#60;row&#62; Element</span></span>](example-renaming-the-row-element.md)  
  
-   [<span data-ttu-id="2eec9-121">例: FOR XML で生成される XML のルート要素の指定</span><span class="sxs-lookup"><span data-stu-id="2eec9-121">Example: Specifying a Root Element for the XML Generated by FOR XML</span></span>](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [<span data-ttu-id="2eec9-122">例: XML 型の列のクエリ</span><span class="sxs-lookup"><span data-stu-id="2eec9-122">Example: Querying XMLType Columns</span></span>](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="2eec9-123">参照</span><span class="sxs-lookup"><span data-stu-id="2eec9-123">See Also</span></span>  
 <span data-ttu-id="2eec9-124">[WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="2eec9-124">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="2eec9-125">[FOR XML での AUTO モードの使用](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="2eec9-125">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="2eec9-126">[FOR XML での EXPLICIT モードの使用](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="2eec9-126">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="2eec9-127">[FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="2eec9-127">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="2eec9-128">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2eec9-128">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="2eec9-129">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2eec9-129">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
