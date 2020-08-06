---
title: その他の注釈 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: rothja
ms.author: jroth
ms.openlocfilehash: b654568c93df0a0c3e08cf6eaa615b7026a9c18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640850"
---
# <a name="other-annotations-sqlxml-40"></a><span data-ttu-id="3d992-102">その他の注釈 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3d992-102">Other Annotations (SQLXML 4.0)</span></span>
  <span data-ttu-id="3d992-103">前のトピックで説明した注釈に加えて、XML 一括読み込みでは、その他の注釈が次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="3d992-103">In addition to the annotations discussed in the previous topics in this section, XML Bulk Load interprets these other annotations, as follows:</span></span>  
  
 `sql:id-prefix`  
 <span data-ttu-id="3d992-104">スキーマで XML データのプレフィックスを指定した場合、XML 一括読み込みでは Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのデータの送信前にプレフィックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3d992-104">If the schema specifies prefixes to the XML data, XML Bulk Load removes the prefixes before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:use-cdata`  
 <span data-ttu-id="3d992-105">XML 一括読み込みでは、CDATA セクションに格納されているテキストが読み取られ、それが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。</span><span class="sxs-lookup"><span data-stu-id="3d992-105">XML Bulk Load reads the text that is stored in the CDATA sections and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:url-encode`  
 <span data-ttu-id="3d992-106">XML 一括読み込みでは、この注釈はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3d992-106">XML Bulk Load does not support this annotation.</span></span> <span data-ttu-id="3d992-107">たとえば、XML データ入力に URL を指定することはできません。また、XML 一括読み込みで、指定した場所からデータを読み込んでデータベースに格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="3d992-107">For example, you cannot specify a URL in the XML data input and expect XML Bulk Load to read data from that location to store it in the database.</span></span>  
  
 `sql:is-mapping-schema`  
 <span data-ttu-id="3d992-108">XML 一括読み込みではこの注釈はサポートされず、`sql:id` もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3d992-108">XML Bulk Load does not support this annotation, nor does it support `sql:id`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d992-109">XML 一括読み込みでは、インライン マッピング スキーマはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3d992-109">XML Bulk Load does not support inline mapping schemas.</span></span>  
  
 `sql:key-fields`  
 <span data-ttu-id="3d992-110">XML 一括読み込みでは、この注釈は常に無視されます。</span><span class="sxs-lookup"><span data-stu-id="3d992-110">XML Bulk Load always ignores this annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d992-111">参照</span><span class="sxs-lookup"><span data-stu-id="3d992-111">See Also</span></span>  
 [<span data-ttu-id="3d992-112">SQLXML 4.0 &#40;の注釈の解釈&#41;</span><span class="sxs-lookup"><span data-stu-id="3d992-112">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
  
  
