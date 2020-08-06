---
title: 注釈の解釈 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: rothja
ms.author: jroth
ms.openlocfilehash: c31d56f7dd577b4b5a5b582eb0e3b1db312109a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642717"
---
# <a name="annotation-interpretation-sqlxml-40"></a><span data-ttu-id="71a34-102">注釈の解釈 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="71a34-102">Annotation Interpretation (SQLXML 4.0)</span></span>
  <span data-ttu-id="71a34-103">ここでは、XML 一括読み込みで XSD スキーマの注釈がどのように解釈されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="71a34-103">The topics in this section describe how XML Bulk Load interprets annotations in the XSD schema.</span></span> <span data-ttu-id="71a34-104">ここで説明する動作は、XDR スキーマの注釈にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="71a34-104">The behavior described here also applies to the annotations in the XDR schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a34-105">ここで提供する情報は、XML 一括読み込みの処理で使用される注釈に関するものだけです。</span><span class="sxs-lookup"><span data-stu-id="71a34-105">The information in these topics describes only the annotations used by XML Bulk Load in its processing.</span></span> <span data-ttu-id="71a34-106">SQLXML 4.0 でサポートされている XSD スキーマの注釈の完全な一覧については、「 [Xsd スキーマでの注釈の使用 &#40;sqlxml 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71a34-106">For a complete list of annotations for the XSD schema that are supported by SQLXML 4.0, see [Using Annotations in XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="71a34-107">XDR スキーマでサポートされている注釈の一覧については、「 [SQLXML 4.0&#41;では、注釈付き Xdr スキーマ &#40;非推奨](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71a34-107">For a list of supported annotations for XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71a34-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="71a34-108">In This Section</span></span>  
 [<span data-ttu-id="71a34-109">sql: リレーションシップとキーの順序付け規則 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="71a34-109">sql:relationship and the Key Ordering Rule &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 <span data-ttu-id="71a34-110">XML 一括読み込みで `sql:relationship` 注釈がどのように解釈されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="71a34-110">Describes how the `sql:relationship` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="71a34-111">sql: &#40;SQLXML 4.0&#41;にマップされています</span><span class="sxs-lookup"><span data-stu-id="71a34-111">sql:mapped &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-mapped.md)  
 <span data-ttu-id="71a34-112">XML 一括読み込みで `sql:mapped` 注釈がどのように解釈されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="71a34-112">Describes how the `sql:mapped` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="71a34-113">sql: limit-field および sql: limit-value &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="71a34-113">sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="71a34-114">XML 一括読み込みで `sql:limit-field` 注釈と `sql:limit-value` 注釈がどのように解釈されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="71a34-114">Describes how the `sql:limit-field` and `sql:limit-value` annotations are interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="71a34-115">sql: overflow フィールド &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="71a34-115">sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="71a34-116">XML 一括読み込みで `sql:overflow` 注釈がどのように解釈されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="71a34-116">Describes how the `sql:overflow` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="71a34-117">SQLXML 4.0 &#40;その他の注釈&#41;</span><span class="sxs-lookup"><span data-stu-id="71a34-117">Other Annotations &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-other-annotations.md)  
 <span data-ttu-id="71a34-118">XML 一括読み込みで `sql:id-prefix`、`sql:use-cdata`、`sql:url-encode`、`sql:is-mapping-schema`、`sql:key-fields` の各注釈がどのように解釈されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="71a34-118">Describes how the following annotations are interpreted in XML Bulk Load: `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.</span></span>  
  
  
