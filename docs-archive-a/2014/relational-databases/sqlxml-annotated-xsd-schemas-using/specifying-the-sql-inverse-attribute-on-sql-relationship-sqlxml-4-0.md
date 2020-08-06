---
title: 'Sql: relationship での sql: 逆属性の指定 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b0781102371b98cced72a5a0edee70c9567c372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640862"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a><span data-ttu-id="a1419-102">sql:relationship での sql:inverse 属性の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a1419-102">Specifying the sql:inverse Attribute on sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="a1419-103">`sql:inverse` 属性は、一括読み込みまたはアップデートグラムで XSD スキーマが使用される場合にのみ便利です。</span><span class="sxs-lookup"><span data-stu-id="a1419-103">The `sql:inverse` attribute is useful only when the XSD schema is used for either bulk load or by an updategram.</span></span> <span data-ttu-id="a1419-104">属性は、 `sql:inverse` 要素で指定でき **\<sql:relationship>** ます。</span><span class="sxs-lookup"><span data-stu-id="a1419-104">The `sql:inverse` attribute can be specified on the **\<sql:relationship>** element.</span></span> <span data-ttu-id="a1419-105">アップデートグラムでは、アップデートグラム ロジックによってスキーマが解釈され、アップデートグラム操作で更新されるテーブルと列が決定されます。</span><span class="sxs-lookup"><span data-stu-id="a1419-105">In updategrams, the updategram logic interprets the schema in determining the tables and columns that are updated by the updategram operation.</span></span> <span data-ttu-id="a1419-106">また、スキーマで指定される親子リレーションシップによって、レコードが変更、挿入、または削除される順序が決定されます。</span><span class="sxs-lookup"><span data-stu-id="a1419-106">The parent-child relationships that are specified in the schema determine the order in which the records are modified (inserted or deleted).</span></span>  
  
 <span data-ttu-id="a1419-107">XSD スキーマを使用しており、そこで指定されている親子リレーションシップが、対応するデータベース列間の主キー/外部キー リレーションシップの逆順である場合は、アップデートグラムで挿入または削除操作を実行すると、主キー/外部キー違反で失敗します。</span><span class="sxs-lookup"><span data-stu-id="a1419-107">If you have an XSD schema in which the parent-child relationship is specified in the inverse order of the primary-key/foreign-key relationship between the corresponding database columns, the insert or delete updategram operation will fail because of the primary-key/foreign-key violation.</span></span> <span data-ttu-id="a1419-108">このような場合、 `sql:inverse` 要素で属性が指定され `sql:inverse="true"` **\<sql:relationship>** ています。また、アップデートグラムのロジックは、スキーマで指定されている親子リレーションシップの解釈を逆します。</span><span class="sxs-lookup"><span data-stu-id="a1419-108">In such cases, the `sql:inverse` attribute is specified (`sql:inverse="true"`) in the **\<sql:relationship>** element, and the updategram logic inverses its interpretation of the parent-child relationship specified in the schema.</span></span>  
  
 <span data-ttu-id="a1419-109">`sql:inverse` 属性はブール値 (0 = false、1=true) をとります。</span><span class="sxs-lookup"><span data-stu-id="a1419-109">The `sql:inverse` attribute takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="a1419-110">指定できる値は 0、1、true、false です。</span><span class="sxs-lookup"><span data-stu-id="a1419-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="a1419-111">注釈を使用した実際のサンプルについ `sql:inverse` ては、「[アップデートグラムでの注釈付きマッピングスキーマの指定](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1419-111">For a working sample using the `sql:inverse` annotation, see [Specifying an Annotated Mapping Schema in an Updategram](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1419-112">参照</span><span class="sxs-lookup"><span data-stu-id="a1419-112">See Also</span></span>  
 [<span data-ttu-id="a1419-113">Sql: relationship を使用したリレーションシップの指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a1419-113">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
