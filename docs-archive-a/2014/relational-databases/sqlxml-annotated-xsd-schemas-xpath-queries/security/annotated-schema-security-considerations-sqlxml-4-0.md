---
title: 注釈付きスキーマのセキュリティに関する考慮事項 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
author: rothja
ms.author: jroth
ms.openlocfilehash: 098f554410a846ed0223d17117b51025dfcf7897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631730"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a><span data-ttu-id="0b8d3-102">注釈付きスキーマのセキュリティに関する注意点 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0b8d3-102">Annotated Schema Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="0b8d3-103">次に、注釈付きスキーマを使用する場合のセキュリティに関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-103">The following are security guidelines for using annotated schemas:</span></span>  
  
-   <span data-ttu-id="0b8d3-104">マッピング スキーマでは既定のマッピングを使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-104">Avoid using default mapping in the mapping schemas.</span></span> <span data-ttu-id="0b8d3-105">既定のマッピングでは、要素名がテーブル名にマップされ、属性名が列名にマップされるため、結果の XML ドキュメントではデータベース情報 (テーブル名と列名) が公開されることになります。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-105">The default mapping exposes the database information (table and column names) in the resulting XML document because, by default, the element names map to table names and attribute names map to column names.</span></span> <span data-ttu-id="0b8d3-106">データベースのテーブルと列の情報には XML ドキュメントを表示できるユーザーであればだれでもアクセスできるので、これにより、セキュリティが脅かされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-106">Therefore, any user who sees the XML document has access to the table and column information in the database, presenting a potential security risk.</span></span> <span data-ttu-id="0b8d3-107">この危険を避けるため、スキーマで任意の要素名と属性名を指定し、注釈を使用してそれらを明示的にテーブルと列にマップするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-107">To avoid this risk, specify arbitrary element and attribute names in the schema and use annotations to explicitly map them to the tables and columns.</span></span> <span data-ttu-id="0b8d3-108">XSD スキーマを作成するときの既定のマッピングの使用方法の詳細については、「 [&#40;SQLXML 4.0&#41;のテーブルおよび列への Xsd 要素と属性の既定のマッピング](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-108">For more information about using default mapping when you create XSD schemas, see [Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="0b8d3-109">注釈を使用して指定する明示的なマッピングでは、データベース情報 (テーブル名、列名など) が公開されます。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-109">The explicit mapping specified using the annotations exposes the database information (such as table names and column names).</span></span> <span data-ttu-id="0b8d3-110">このため、これらのスキーマはだれもがアクセスできる場所に置かないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-110">Therefore, you may not want to make these schemas available publicly.</span></span>  
  
-   <span data-ttu-id="0b8d3-111">`max-depth` 注釈が大きな値に設定されており、再帰が行われるマッピング スキーマに対するクエリなど、実行に時間がかかるクエリがあります。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-111">Certain queries such as those specified against mapping schema with recursion (specified using `max-depth` annotation set to a higher value) may take longer to execute.</span></span> <span data-ttu-id="0b8d3-112">必要に応じて、[コマンドタイムアウト] プロパティを (秒単位で) 設定して、タイムアウトの制限を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-112">You can optionally specify a time-out limit by setting the Command Time Out property (in seconds).</span></span> <span data-ttu-id="0b8d3-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0b8d3-113">For example:</span></span>  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0b8d3-114">参照</span><span class="sxs-lookup"><span data-stu-id="0b8d3-114">See Also</span></span>  
 [<span data-ttu-id="0b8d3-115">SQLXML 4.0 における注釈付き XSD スキーマ</span><span class="sxs-lookup"><span data-stu-id="0b8d3-115">Annotated XSD Schemas in SQLXML 4.0</span></span>](../../sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
