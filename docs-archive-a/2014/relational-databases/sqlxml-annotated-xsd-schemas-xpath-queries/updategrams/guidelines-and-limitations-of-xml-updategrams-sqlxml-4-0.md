---
title: XML アップデートグラムのガイドラインと制限事項 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e01e366edc2889691862de639f69220ac4bb439
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716137"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a><span data-ttu-id="e067e-102">XML アップデートグラムのガイドラインと制限 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e067e-102">Guidelines and Limitations of XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="e067e-103">XML アップデートグラムを使用する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="e067e-103">Remember the following when using XML updategrams:</span></span>  
  
-   <span data-ttu-id="e067e-104">とブロックのペアが1つだけである挿入操作にアップデートグラムを使用している場合は、 **\<before>** **\<after>** ブロックを **\<before>** 省略できます。</span><span class="sxs-lookup"><span data-stu-id="e067e-104">If you are using an updategram for an insert operation with only a single pair of **\<before>** and **\<after>** blocks, the **\<before>** block can be omitted.</span></span> <span data-ttu-id="e067e-105">逆に、削除操作の場合は、 **\<after>** ブロックを省略できます。</span><span class="sxs-lookup"><span data-stu-id="e067e-105">Conversely, in case of a delete operation, the **\<after>** block can be omitted.</span></span>  
  
-   <span data-ttu-id="e067e-106">タグに複数のおよびブロックを含むアップデートグラムを使用している場合は、 **\<before>** **\<after>** との **\<sync>** **\<before>** **\<after>** ペアを形成するために、ブロックとブロックの両方を指定する必要があり **\<before>** **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="e067e-106">If you are using an updategram with multiple **\<before>** and **\<after>** blocks in the **\<sync>** tag, both **\<before>** blocks and **\<after>** blocks must be specified to form **\<before>** and **\<after>** pairs.</span></span>  
  
-   <span data-ttu-id="e067e-107">アップデートグラムの更新は、XML スキーマで提供される XML ビューに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e067e-107">The updates in an updategram are applied to the XML view that is provided by the XML schema.</span></span> <span data-ttu-id="e067e-108">したがって、既定のマッピングが正しく行われるようにするには、アップデートグラムでスキーマ ファイル名を指定するか、ファイル名を指定しない場合は、要素名と属性名がデータベースのテーブル名と列名に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e067e-108">Therefore, for the default mapping to succeed either you must specify the schema file name in the updategram or, if the file name is not provided, the element and attribute names must match the table and column names in the database.</span></span>  
  
-   <span data-ttu-id="e067e-109">SQLXML 4.0 を使用する場合、アップデートグラムのすべての列値は、子要素の XML ビューを構成するために提供される XDR スキーマまたは XSD スキーマで明示的にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e067e-109">SQLXML 4.0 requires that all column values in an updategram must be explicitly mapped in the schema (either XDR or XSD) provided to compose the XML view for its child elements.</span></span> <span data-ttu-id="e067e-110">この動作は以前のバージョンの SQLXML とは異なります。以前のバージョンでは、`sql:relationship` 注釈で列の値が外部キーの一部として暗黙的に指定されていれば、スキーマでマップされない列値も許可されていました。</span><span class="sxs-lookup"><span data-stu-id="e067e-110">This behavior differs from earlier versions of SQLXML, which allowed a value for a column not mapped in the schema if it was implied as part of the foreign Key in a `sql:relationship` annotation.</span></span> <span data-ttu-id="e067e-111">この変更は、子要素への主キー値の割り当てには影響しません。SQLXML 4.0 では、子要素に対して明示的に値が指定されていない場合でも、値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e067e-111">(Note that this change does not affect propagation of primary key values to child elements, which still occurs for SQLXML 4.0 if no value is explicitly specified for the child element.</span></span>  
  
-   <span data-ttu-id="e067e-112">アップデートグラムを使用してバイナリ列 (データ型など) のデータを変更する場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型 (など `sql:datatype="image"` ) と XML データ型 (たとえば、や) を指定するマッピングスキーマを指定する必要があり `dt:type="binhex"` `dt:type="binbase64` ます。</span><span class="sxs-lookup"><span data-stu-id="e067e-112">If you are using an updategram to modify data in a binary column (such as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` data type), you must provide a mapping schema in which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (for example, `sql:datatype="image"`) and the XML data type (for example, `dt:type="binhex"` or `dt:type="binbase64`) must be specified.</span></span> <span data-ttu-id="e067e-113">バイナリ列のデータは、アップデートグラム内に指定する必要があります。マッピング スキーマで指定される `sql:url-encode` 注釈は、アップデートグラムでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e067e-113">The data for the binary column must be specified in the updategram; the `sql:url-encode` annotation that is specified in the mapping schema is ignored by the updategram.</span></span>  
  
-   <span data-ttu-id="e067e-114">XSD スキーマを記述するときに、`sql:relation` 注釈または `sql:field` 注釈に指定する値に特殊文字が含まれる場合、たとえば、スペースを含むテーブル名 "Order Details" を指定する場合などは、値を "[Order Details]" のように角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="e067e-114">When you are writing an XSD schema, if the value you specify for the `sql:relation` or `sql:field` annotation includes a special character, such as a space character (for example, in the "Order Details" table name), this value must be enclosed in brackets (for example, "[Order Details]").</span></span>  
  
-   <span data-ttu-id="e067e-115">アップデートグラムの使用で、チェーン リレーションシップはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e067e-115">When using updategrams, chain relationships are not supported.</span></span> <span data-ttu-id="e067e-116">たとえば、テーブル A とテーブル C が、テーブル B を使用するチェーン リレーションシップで関連付けられている場合は、アップデートグラムの実行時に次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e067e-116">For example, if tables A and C are related through a chain relationship that uses table B, the following error will occur when attempting to run and execute the updategram:</span></span>  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     <span data-ttu-id="e067e-117">スキーマとアップデートグラムの両方が正しく、有効な形式であっても、チェーン リレーションシップが存在すると、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e067e-117">Even if both schema and updategram are otherwise correct and validly formed, this error will occur if a chain relationship is present.</span></span>  
  
-   <span data-ttu-id="e067e-118">アップデートグラムでは、更新中に `image` 型データをパラメーターとして引き渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e067e-118">Updategrams do not permit the passing of `image` type data as parameters during updates.</span></span>  
  
-   <span data-ttu-id="e067e-119">や image のようなバイナリラージオブジェクト (BLOB) 型は、 `text/ntext` updategrams を使用するときにのブロックでは使用しない **\<before>** でください。これには、同時実行制御で使用するためのものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e067e-119">Binary large object (BLOB) types like `text/ntext` and images should not be used in the **\<before>** block in when working with updategrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="e067e-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e067e-120">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="e067e-121">たとえば、`text` データ型の列を比較するには WHERE 句で LIKE キーワードを使用しますが、データ サイズが 8 KB を超える BLOB 型の場合、この比較は失敗します。</span><span class="sxs-lookup"><span data-stu-id="e067e-121">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="e067e-122">`ntext` データで特殊文字を使用すると、BLOB 型の比較の制限によって、SQLXML 4.0 で問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e067e-122">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="e067e-123">たとえば、アップデートグラムのブロックで "[Serializable]" を使用 **\<before>** すると、型の列に対する同時実行制御チェックに `ntext` 失敗し、次の SQLOLEDB エラー説明が返されます。</span><span class="sxs-lookup"><span data-stu-id="e067e-123">For example, the use of "[Serializable]" in the **\<before>** block of an updategrams when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e067e-124">参照</span><span class="sxs-lookup"><span data-stu-id="e067e-124">See Also</span></span>  
 [<span data-ttu-id="e067e-125">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e067e-125">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
