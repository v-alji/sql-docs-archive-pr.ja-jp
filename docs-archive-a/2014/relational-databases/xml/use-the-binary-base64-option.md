---
title: BINARY BASE64 オプションの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: rothja
ms.author: jroth
ms.openlocfilehash: 090d6a91ee56707a4eb1d545aa5a05bc25999fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738035"
---
# <a name="use-the-binary-base64-option"></a><span data-ttu-id="41ea5-102">BINARY BASE64 オプションの使用</span><span class="sxs-lookup"><span data-stu-id="41ea5-102">Use the BINARY BASE64 Option</span></span>
  <span data-ttu-id="41ea5-103">クエリに BINARY BASE64 オプションを指定すると、バイナリ データが base64 エンコード形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="41ea5-103">If the BINARY BASE64 option is specified in the query, the binary data is returned in base64 encoding format.</span></span> <span data-ttu-id="41ea5-104">AUTO モードでは、BINARY BASE64 オプションを指定しないと、既定でバイナリ データの URL エンコードがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="41ea5-104">By default, if the BINARY BASE64 option is not specified, AUTO mode supports URL encoding of binary data.</span></span> <span data-ttu-id="41ea5-105">つまり、バイナリ データではなく、クエリが実行されたデータベースの仮想ルートからの相対 URL への参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="41ea5-105">That is, instead of binary data, a reference to a relative URL to the virtual root of the database where the query was executed is returned.</span></span> <span data-ttu-id="41ea5-106">この参照は、それ以降の操作で SQLXML ISAPI dbobject クエリを使用して実際のバイナリ データにアクセスするときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="41ea5-106">This reference can be used to access the actual binary data in subsequent operations by using the SQLXML ISAPI dbobject query.</span></span> <span data-ttu-id="41ea5-107">クエリで画像を識別するには、主キー列など、十分な情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41ea5-107">The query must provide enough information, such as primary key columns, to identify the image.</span></span>  
  
 <span data-ttu-id="41ea5-108">クエリを指定するときに、ビューのバイナリ列に別名を使用すると、その別名がバイナリ データの URL エンコードで返されます。</span><span class="sxs-lookup"><span data-stu-id="41ea5-108">In specifying a query, if an alias is used for the binary column of the view, the alias is returned in the URL encoding of the binary data.</span></span> <span data-ttu-id="41ea5-109">それ以降の操作では別名は無意味になり、URL エンコードを使用して画像を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="41ea5-109">In subsequent operations, the alias is meaningless, and the URL encoding cannot be used to retrieve the image.</span></span> <span data-ttu-id="41ea5-110">したがって、FOR XML AUTO モードを使用してビューのクエリを実行するときは、別名を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="41ea5-110">Therefore, do not use aliases when querying a view using FOR XML AUTO mode.</span></span>  
  
 <span data-ttu-id="41ea5-111">たとえば、SELECT クエリで、BLOB (バイナリ ラージ オブジェクト) に任意の列をキャストした場合、列は一時エンティティになります (関連するテーブル名と列名が失われます)。</span><span class="sxs-lookup"><span data-stu-id="41ea5-111">For example, in a SELECT query, casting any column to a binary large object (BLOB) makes it a temporary entity in that it loses its associated table name and column name.</span></span> <span data-ttu-id="41ea5-112">これにより、AUTO モードのクエリでエラーが発生します。これは XML 階層内でのこの値の配置場所がわからないためです。</span><span class="sxs-lookup"><span data-stu-id="41ea5-112">This causes AUTO mode queries to generate an error, because it does not know where to put this value in the XML hierarchy.</span></span> <span data-ttu-id="41ea5-113">例:</span><span class="sxs-lookup"><span data-stu-id="41ea5-113">For example:</span></span>  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 <span data-ttu-id="41ea5-114">次のクエリでは、BLOB (バイナリ ラージ オブジェクト) へのキャストによるエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="41ea5-114">This query produces an error, because of the casting to a binary large object (BLOB):</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 <span data-ttu-id="41ea5-115">これを解決するには、BINARY BASE64 オプションを FOR XML 句に追加します。</span><span class="sxs-lookup"><span data-stu-id="41ea5-115">The solution is to add the BINARY BASE64 option to the FOR XML clause.</span></span> <span data-ttu-id="41ea5-116">キャストを削除すると、クエリは予想どおりの結果を作成します。</span><span class="sxs-lookup"><span data-stu-id="41ea5-116">If you remove the casting, the query produces the results as expected:</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 <span data-ttu-id="41ea5-117">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="41ea5-117">This is the result:</span></span>  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="41ea5-118">参照</span><span class="sxs-lookup"><span data-stu-id="41ea5-118">See Also</span></span>  
 [<span data-ttu-id="41ea5-119">FOR XML での AUTO モードの使用</span><span class="sxs-lookup"><span data-stu-id="41ea5-119">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
