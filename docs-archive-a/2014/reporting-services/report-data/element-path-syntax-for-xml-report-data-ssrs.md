---
title: XML レポート データの要素パス構文 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ElementPath syntax
- XML [Reporting Services], data retrieval
ms.assetid: 07bd7a4e-fd7a-4a72-9344-3258f7c286d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d66b39761dc278abff25a3b22ccd18ca74272b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742881"
---
# <a name="element-path-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="e4d00-102">XML レポート データの要素パス構文 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e4d00-102">Element Path Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="e4d00-103">レポート デザイナーでは、大文字と小文字が区別される要素パスを定義して、レポートに使用するデータを XML データ ソースから指定します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-103">In Report Designer, you specify the data to use for a report from an XML data source by defining a case-sensitive element path.</span></span> <span data-ttu-id="e4d00-104">要素パスとは、XML データ ソースにおける XML 階層のノードとその属性の走査方法を指定するものです。</span><span class="sxs-lookup"><span data-stu-id="e4d00-104">An element path indicates how to traverse the XML hierarchical nodes and their attributes in the XML data source.</span></span> <span data-ttu-id="e4d00-105">データセット クエリを空にするか、XML `ElementPath` の XML `Query` を空にした場合、既定の要素パスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-105">To use the default element path, leave the dataset query or the XML `ElementPath` of the XML `Query` empty.</span></span> <span data-ttu-id="e4d00-106">XML データ ソースからデータが取得されると、テキスト値を持つ要素ノードおよび要素ノードの属性が、結果セットにおける列になります。</span><span class="sxs-lookup"><span data-stu-id="e4d00-106">When data is retrieved from the XML data source, element nodes that have text values and element node attributes become columns in the result set.</span></span> <span data-ttu-id="e4d00-107">クエリを実行すると、これらのノードと属性の値が、行データになります。</span><span class="sxs-lookup"><span data-stu-id="e4d00-107">The values of the nodes and attributes become the row data when you run the query.</span></span> <span data-ttu-id="e4d00-108">[レポート データ] ペインでは、列がデータセット フィールド コレクションとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-108">The columns appear as the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="e4d00-109">このトピックでは、要素パス構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-109">This topic describes the element path syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4d00-110">要素パス構文は、名前空間に依存しません。</span><span class="sxs-lookup"><span data-stu-id="e4d00-110">Element path syntax is namespace-independent.</span></span> <span data-ttu-id="e4d00-111">要素パスで名前空間を使用するには、xml クエリ構文で説明されている xml 要素を含む xml クエリ構文を使用して、xml `ElementPath` [レポートデータ &#40;SSRS&#41;](report-data-ssrs.md)に記述します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-111">To use namespaces in an element path, use the XML query syntax that includes an XML `ElementPath` element described in [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="e4d00-112">次の表に、要素パスを定義する際の表記規則を示します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-112">The following table describes conventions used to define an element path.</span></span>  
  
|<span data-ttu-id="e4d00-113">表記</span><span class="sxs-lookup"><span data-stu-id="e4d00-113">Convention</span></span>|<span data-ttu-id="e4d00-114">使用目的</span><span class="sxs-lookup"><span data-stu-id="e4d00-114">Used for</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e4d00-115">**太字**</span><span class="sxs-lookup"><span data-stu-id="e4d00-115">**bold**</span></span>|<span data-ttu-id="e4d00-116">記載されているとおりに入力する必要があるテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-116">Text that must be typed exactly as shown.</span></span>|  
|<span data-ttu-id="e4d00-117">&#124; (垂直線)</span><span class="sxs-lookup"><span data-stu-id="e4d00-117">&#124; (vertical bar)</span></span>|<span data-ttu-id="e4d00-118">構文項目に複数の選択肢があることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-118">Separates syntax items.</span></span> <span data-ttu-id="e4d00-119">選択できる項目は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="e4d00-119">You can choose only one of the items.</span></span>|  
|`[ ] (brackets)`|<span data-ttu-id="e4d00-120">省略可能な構文項目。</span><span class="sxs-lookup"><span data-stu-id="e4d00-120">Optional syntax items.</span></span> <span data-ttu-id="e4d00-121">角かっこは入力しません。</span><span class="sxs-lookup"><span data-stu-id="e4d00-121">Do not type the brackets.</span></span>|  
|<span data-ttu-id="e4d00-122">**{}** (中かっこ)</span><span class="sxs-lookup"><span data-stu-id="e4d00-122">**{ }** (braces)</span></span>|<span data-ttu-id="e4d00-123">構文項目のパラメーターを区切ります。</span><span class="sxs-lookup"><span data-stu-id="e4d00-123">Delimits parameters of syntax items.</span></span>|  
|<span data-ttu-id="e4d00-124">[ **,** ...*n*]</span><span class="sxs-lookup"><span data-stu-id="e4d00-124">[**,**...*n*]</span></span>|<span data-ttu-id="e4d00-125">先行する項目を *n* 回繰り返せることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-125">Indicates the preceding item can be repeated *n* number of times.</span></span> <span data-ttu-id="e4d00-126">出現箇所は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-126">The occurrences are separated by commas.</span></span>|  
  
## <a name="syntax"></a><span data-ttu-id="e4d00-127">構文</span><span class="sxs-lookup"><span data-stu-id="e4d00-127">Syntax</span></span>  
  
```  
  
Element path ::=  
    ElementNode[/Element path]  
ElementNode ::=  
    XMLName[(Encoding)][{[FieldList]}]  
XMLName ::=  
    [NamespacePrefix:]XMLLocalName  
Encoding ::=  
        HTMLEncoded | Base64Encoded  
FieldList ::=  
    Field[,FieldList]  
Field ::=  
    Attribute | Value | Element | ElementNode  
Attribute ::=  
        @XMLName[(Type)]  
Value ::=  
        @[(Type)]  
Element ::=  
    XMLName[(Type)]  
Type ::=  
        String | Integer | Boolean | Float | Decimal | Date | XML   
NamespacePrefix ::=  
    Identifier that specifies the namespace.  
XMLLocalName :: =  
    Identifier in the XML tag.   
```  
  
## <a name="remarks"></a><span data-ttu-id="e4d00-128">解説</span><span class="sxs-lookup"><span data-stu-id="e4d00-128">Remarks</span></span>  
 <span data-ttu-id="e4d00-129">次の表は、要素パス関連の用語をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="e4d00-129">The following table summarizes element path terms.</span></span> <span data-ttu-id="e4d00-130">サンプル XML ドキュメントである Customers.xml (このトピックの「例」を参照) を使って説明しています。</span><span class="sxs-lookup"><span data-stu-id="e4d00-130">Examples in the table refer to the example XML document Customers.xml, which is included in the Examples section of this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4d00-131">XML タグでは大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-131">XML tags are case-sensitive.</span></span> <span data-ttu-id="e4d00-132">要素パスに ElementNode を指定する場合は、データ ソース内の XML タグと完全に一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4d00-132">When you specify an ElementNode in the element path, you must exactly match the XML tags in the data source.</span></span>  
  
|<span data-ttu-id="e4d00-133">期間</span><span class="sxs-lookup"><span data-stu-id="e4d00-133">Term</span></span>|<span data-ttu-id="e4d00-134">定義</span><span class="sxs-lookup"><span data-stu-id="e4d00-134">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="e4d00-135">Element path</span><span class="sxs-lookup"><span data-stu-id="e4d00-135">Element path</span></span>|<span data-ttu-id="e4d00-136">XML ドキュメント内のノードのシーケンス、つまり、どのようにノードをたどっていけば、XML データ ソースからデータセットのフィールド データを取得できるかを定義します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-136">Defines the sequence of nodes to traverse within the XML document in order to retrieve field data for a dataset with an XML data source.</span></span>|  
|`ElementNode`|<span data-ttu-id="e4d00-137">XML ドキュメント内の XML ノードです。</span><span class="sxs-lookup"><span data-stu-id="e4d00-137">The XML node in the XML document.</span></span> <span data-ttu-id="e4d00-138">各ノードは他のノードと階層的な関係にあり、タグによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-138">Nodes are designated by tags and exist in a hierarchical relationship with other nodes.</span></span> <span data-ttu-id="e4d00-139">たとえば、 \<Customers> はルート要素ノードです。</span><span class="sxs-lookup"><span data-stu-id="e4d00-139">For example, \<Customers> is the root element node.</span></span> <span data-ttu-id="e4d00-140">\<Customer>はのサブ要素です \<Customers> 。</span><span class="sxs-lookup"><span data-stu-id="e4d00-140">\<Customer> is a subelement of \<Customers>.</span></span>|  
|`XMLName`|<span data-ttu-id="e4d00-141">ノード名。</span><span class="sxs-lookup"><span data-stu-id="e4d00-141">The name of the node.</span></span> <span data-ttu-id="e4d00-142">たとえば、Customers ノードの名前は Customers です。</span><span class="sxs-lookup"><span data-stu-id="e4d00-142">For example, the name of the Customers node is Customers.</span></span> <span data-ttu-id="e4d00-143">すべてのノード名を一意に識別できるように、`XMLName` の先頭には名前空間識別子を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-143">An `XMLName` can be prefixed with a namespace identifier to uniquely name every node.</span></span>|  
|`Encoding`|<span data-ttu-id="e4d00-144">この要素の `Value` はエンコードされた XML であり、この要素のサブ要素としてデコードおよび追加する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-144">Indicates that the `Value` for this element is encoded XML and needs to be decoded and included as a subelement of this element.</span></span>|  
|`FieldList`|<span data-ttu-id="e4d00-145">データの取得に使用する一連の要素と属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-145">Defines the set of elements and attributes to use to retrieve data.</span></span><br /><br /> <span data-ttu-id="e4d00-146">指定しなかった場合は、すべての属性およびサブ要素がフィールドとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-146">If not specified, all attributes and subelements are used as fields.</span></span> <span data-ttu-id="e4d00-147">空のフィールドリストが指定されている場合 ( **{}** )、このノードのフィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e4d00-147">If the empty field list is specified (**{}**), no fields from this node are used.</span></span><br /><br /> <span data-ttu-id="e4d00-148">`FieldList` には、`Value` や `Element`、`ElementNode` は含まれません。</span><span class="sxs-lookup"><span data-stu-id="e4d00-148">A `FieldList` may not contain both a `Value` and an `Element` or `ElementNode`.</span></span>|  
|`Field`|<span data-ttu-id="e4d00-149">データセットのフィールドとして取得するデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-149">Specifies the data that is retrieved as a dataset field.</span></span>|  
|`Attribute`|<span data-ttu-id="e4d00-150">`ElementNode` 内に指定される名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="e4d00-150">A name-value pair within the `ElementNode`.</span></span> <span data-ttu-id="e4d00-151">たとえば、要素ノードでは、 \<Customer ID="1"> `ID` は属性で、 `@ID(Integer)` 対応するデータフィールドの整数型として "1" を返し `ID` ます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-151">For example, in the element node \<Customer ID="1">, `ID` is an attribute and `@ID(Integer)` returns "1" as an integer type in the corresponding data field `ID`.</span></span>|  
|`Value`|<span data-ttu-id="e4d00-152">要素の値。</span><span class="sxs-lookup"><span data-stu-id="e4d00-152">The value of the element.</span></span> <span data-ttu-id="e4d00-153">`Value` は、要素パス内で最後の `ElementNode` でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-153">`Value` can only be used on the last `ElementNode` in the element path.</span></span> <span data-ttu-id="e4d00-154">たとえば、はリーフノードであるため、 \<Return> これを要素パスの最後に含めると、の値 `Return {@}` はに `Chair` なります。</span><span class="sxs-lookup"><span data-stu-id="e4d00-154">For example, because \<Return> is a leaf node, if you include it at the end of an element path, the value of `Return {@}` is `Chair`.</span></span>|  
|`Element`|<span data-ttu-id="e4d00-155">指定されたサブ要素の値です。</span><span class="sxs-lookup"><span data-stu-id="e4d00-155">The value of the named subelement.</span></span> <span data-ttu-id="e4d00-156">たとえば、Customers {}/Customer {}/LastName とすると、LastName 要素についてのみ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-156">For example, Customers {}/Customer {}/LastName retrieves values for only the LastName element.</span></span>|  
|`Type`|<span data-ttu-id="e4d00-157">この要素から作成されたフィールドに使用するデータ型 (省略可) です。</span><span class="sxs-lookup"><span data-stu-id="e4d00-157">The optional data type to use for the field created from this element.</span></span>|  
|`NamespacePrefix`|<span data-ttu-id="e4d00-158">`NamespacePrefix` は XML Query 要素で定義されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-158">`NamespacePrefix` is defined in the XML Query element.</span></span> <span data-ttu-id="e4d00-159">XML Query 要素が存在しない場合、XML `ElementPath` の名前空間は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-159">If no XML Query element exists, namespaces in the XML `ElementPath` are ignored.</span></span> <span data-ttu-id="e4d00-160">XML Query 要素が存在する場合は、XML `ElementPath` に属性 `IgnoreNamespaces` を使用できます (省略可)。</span><span class="sxs-lookup"><span data-stu-id="e4d00-160">If there is an XML Query element, the XML `ElementPath` has an optional attribute `IgnoreNamespaces`.</span></span> <span data-ttu-id="e4d00-161">IgnoreNamespaces がの場合 `true` 、xml および xml ドキュメント内の名前空間 `ElementPath` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-161">If IgnoreNamespaces is `true`, namespaces in the XML `ElementPath` and the XML document are ignored.</span></span> <span data-ttu-id="e4d00-162">詳細については、「[XML レポート データの XML クエリ構文 &#40;SSRS&#41;](report-data-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4d00-162">For more information, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>|  
  
## <a name="example---no-namespaces"></a><span data-ttu-id="e4d00-163">例 - 名前空間なし</span><span class="sxs-lookup"><span data-stu-id="e4d00-163">Example - No Namespaces</span></span>  
 <span data-ttu-id="e4d00-164">データ ソースとして、XML ドキュメント (Customers.xml) を使用した例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-164">The following examples use the XML document Customers.xml.</span></span> <span data-ttu-id="e4d00-165">要素パスの構文を示しながら、データセットを定義するクエリでその要素パスを使用した場合にどのような結果が得られるかを説明しています。</span><span class="sxs-lookup"><span data-stu-id="e4d00-165">This table shows examples of element path syntax and the results of using the element path in a query that defines a dataset, based on the XML document as a data source.</span></span>  
  
 <span data-ttu-id="e4d00-166">要素パスが空の場合、クエリは既定の要素パス (リーフノードコレクションへの最初のパス) を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e4d00-166">Note that when the element path is empty, the query uses the default element path: the first path to a leaf node collection.</span></span> <span data-ttu-id="e4d00-167">1 つ目は要素パスを空にする例です。/Customers/Customer/Orders/Order という要素パスを指定した場合と同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="e4d00-167">In the first example, leaving the element path empty is equivalent to specifying the element path /Customers/Customer/Orders/Order.</span></span> <span data-ttu-id="e4d00-168">このパス上に存在するすべてのノードの値と属性が結果セットに返され、ノード名と属性名がデータセットのフィールドとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-168">All node value and attributes along the path are returned in the result set, and the node names and attributes names appear as dataset fields.</span></span>  
  
-   <span data-ttu-id="e4d00-169">*空*</span><span class="sxs-lookup"><span data-stu-id="e4d00-169">*Empty*</span></span>  
  
    |<span data-ttu-id="e4d00-170">Order</span><span class="sxs-lookup"><span data-stu-id="e4d00-170">Order</span></span>|<span data-ttu-id="e4d00-171">数量</span><span class="sxs-lookup"><span data-stu-id="e4d00-171">Qty</span></span>|<span data-ttu-id="e4d00-172">id</span><span class="sxs-lookup"><span data-stu-id="e4d00-172">ID</span></span>|<span data-ttu-id="e4d00-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="e4d00-173">FirstName</span></span>|<span data-ttu-id="e4d00-174">LastName</span><span class="sxs-lookup"><span data-stu-id="e4d00-174">LastName</span></span>|<span data-ttu-id="e4d00-175">Customer.ID</span><span class="sxs-lookup"><span data-stu-id="e4d00-175">Customer.ID</span></span>|<span data-ttu-id="e4d00-176">xmlns</span><span class="sxs-lookup"><span data-stu-id="e4d00-176">xmlns</span></span>|  
    |-----------|---------|--------|---------------|--------------|-----------------|-----------|  
    |<span data-ttu-id="e4d00-177">Chair</span><span class="sxs-lookup"><span data-stu-id="e4d00-177">Chair</span></span>|<span data-ttu-id="e4d00-178">6</span><span class="sxs-lookup"><span data-stu-id="e4d00-178">6</span></span>|<span data-ttu-id="e4d00-179">1</span><span class="sxs-lookup"><span data-stu-id="e4d00-179">1</span></span>|<span data-ttu-id="e4d00-180">Bobby</span><span class="sxs-lookup"><span data-stu-id="e4d00-180">Bobby</span></span>|<span data-ttu-id="e4d00-181">Moore</span><span class="sxs-lookup"><span data-stu-id="e4d00-181">Moore</span></span>|<span data-ttu-id="e4d00-182">11</span><span class="sxs-lookup"><span data-stu-id="e4d00-182">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="e4d00-183">テーブル</span><span class="sxs-lookup"><span data-stu-id="e4d00-183">Table</span></span>|<span data-ttu-id="e4d00-184">1</span><span class="sxs-lookup"><span data-stu-id="e4d00-184">1</span></span>|<span data-ttu-id="e4d00-185">2</span><span class="sxs-lookup"><span data-stu-id="e4d00-185">2</span></span>|<span data-ttu-id="e4d00-186">Bobby</span><span class="sxs-lookup"><span data-stu-id="e4d00-186">Bobby</span></span>|<span data-ttu-id="e4d00-187">Moore</span><span class="sxs-lookup"><span data-stu-id="e4d00-187">Moore</span></span>|<span data-ttu-id="e4d00-188">11</span><span class="sxs-lookup"><span data-stu-id="e4d00-188">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="e4d00-189">Sofa</span><span class="sxs-lookup"><span data-stu-id="e4d00-189">Sofa</span></span>|<span data-ttu-id="e4d00-190">2</span><span class="sxs-lookup"><span data-stu-id="e4d00-190">2</span></span>|<span data-ttu-id="e4d00-191">8</span><span class="sxs-lookup"><span data-stu-id="e4d00-191">8</span></span>|<span data-ttu-id="e4d00-192">Crystal</span><span class="sxs-lookup"><span data-stu-id="e4d00-192">Crystal</span></span>|<span data-ttu-id="e4d00-193">Hu</span><span class="sxs-lookup"><span data-stu-id="e4d00-193">Hu</span></span>|<span data-ttu-id="e4d00-194">20</span><span class="sxs-lookup"><span data-stu-id="e4d00-194">20</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="e4d00-195">EndTables</span><span class="sxs-lookup"><span data-stu-id="e4d00-195">EndTables</span></span>|<span data-ttu-id="e4d00-196">2</span><span class="sxs-lookup"><span data-stu-id="e4d00-196">2</span></span>|<span data-ttu-id="e4d00-197">15</span><span class="sxs-lookup"><span data-stu-id="e4d00-197">15</span></span>|<span data-ttu-id="e4d00-198">Wyatt</span><span class="sxs-lookup"><span data-stu-id="e4d00-198">Wyatt</span></span>|<span data-ttu-id="e4d00-199">Diaz</span><span class="sxs-lookup"><span data-stu-id="e4d00-199">Diaz</span></span>|<span data-ttu-id="e4d00-200">33</span><span class="sxs-lookup"><span data-stu-id="e4d00-200">33</span></span>|http://www.adventure-works.com|  
  
-   `Customers {}/Customer`  
  
    |<span data-ttu-id="e4d00-201">FirstName</span><span class="sxs-lookup"><span data-stu-id="e4d00-201">FirstName</span></span>|<span data-ttu-id="e4d00-202">LastName</span><span class="sxs-lookup"><span data-stu-id="e4d00-202">LastName</span></span>|<span data-ttu-id="e4d00-203">id</span><span class="sxs-lookup"><span data-stu-id="e4d00-203">ID</span></span>|  
    |---------------|--------------|--------|  
    |<span data-ttu-id="e4d00-204">Bobby</span><span class="sxs-lookup"><span data-stu-id="e4d00-204">Bobby</span></span>|<span data-ttu-id="e4d00-205">Moore</span><span class="sxs-lookup"><span data-stu-id="e4d00-205">Moore</span></span>|<span data-ttu-id="e4d00-206">11</span><span class="sxs-lookup"><span data-stu-id="e4d00-206">11</span></span>|  
    |<span data-ttu-id="e4d00-207">Crystal</span><span class="sxs-lookup"><span data-stu-id="e4d00-207">Crystal</span></span>|<span data-ttu-id="e4d00-208">Hu</span><span class="sxs-lookup"><span data-stu-id="e4d00-208">Hu</span></span>|<span data-ttu-id="e4d00-209">20</span><span class="sxs-lookup"><span data-stu-id="e4d00-209">20</span></span>|  
    |<span data-ttu-id="e4d00-210">Wyatt</span><span class="sxs-lookup"><span data-stu-id="e4d00-210">Wyatt</span></span>|<span data-ttu-id="e4d00-211">Diaz</span><span class="sxs-lookup"><span data-stu-id="e4d00-211">Diaz</span></span>|<span data-ttu-id="e4d00-212">33</span><span class="sxs-lookup"><span data-stu-id="e4d00-212">33</span></span>|  
  
-   `Customers {}/Customer {}/LastName`  
  
    |<span data-ttu-id="e4d00-213">LastName</span><span class="sxs-lookup"><span data-stu-id="e4d00-213">LastName</span></span>|  
    |--------------|  
    |<span data-ttu-id="e4d00-214">Moore</span><span class="sxs-lookup"><span data-stu-id="e4d00-214">Moore</span></span>|  
    |<span data-ttu-id="e4d00-215">Hu</span><span class="sxs-lookup"><span data-stu-id="e4d00-215">Hu</span></span>|  
    |<span data-ttu-id="e4d00-216">Diaz</span><span class="sxs-lookup"><span data-stu-id="e4d00-216">Diaz</span></span>|  
  
-   `Customers {}/Customer {}/Orders/Order {@,@Qty}`  
  
    |<span data-ttu-id="e4d00-217">Order</span><span class="sxs-lookup"><span data-stu-id="e4d00-217">Order</span></span>|<span data-ttu-id="e4d00-218">数量</span><span class="sxs-lookup"><span data-stu-id="e4d00-218">Qty</span></span>|  
    |-----------|---------|  
    |<span data-ttu-id="e4d00-219">Chair</span><span class="sxs-lookup"><span data-stu-id="e4d00-219">Chair</span></span>|<span data-ttu-id="e4d00-220">6</span><span class="sxs-lookup"><span data-stu-id="e4d00-220">6</span></span>|  
    |<span data-ttu-id="e4d00-221">テーブル</span><span class="sxs-lookup"><span data-stu-id="e4d00-221">Table</span></span>|<span data-ttu-id="e4d00-222">1</span><span class="sxs-lookup"><span data-stu-id="e4d00-222">1</span></span>|  
    |<span data-ttu-id="e4d00-223">Sofa</span><span class="sxs-lookup"><span data-stu-id="e4d00-223">Sofa</span></span>|<span data-ttu-id="e4d00-224">2</span><span class="sxs-lookup"><span data-stu-id="e4d00-224">2</span></span>|  
    |<span data-ttu-id="e4d00-225">EndTables</span><span class="sxs-lookup"><span data-stu-id="e4d00-225">EndTables</span></span>|<span data-ttu-id="e4d00-226">2</span><span class="sxs-lookup"><span data-stu-id="e4d00-226">2</span></span>|  
  
-   `Customers {}/Customer/Orders/Order{ @ID(Integer)}`  
  
    |<span data-ttu-id="e4d00-227">Order.ID</span><span class="sxs-lookup"><span data-stu-id="e4d00-227">Order.ID</span></span>|<span data-ttu-id="e4d00-228">FirstName</span><span class="sxs-lookup"><span data-stu-id="e4d00-228">FirstName</span></span>|<span data-ttu-id="e4d00-229">LastName</span><span class="sxs-lookup"><span data-stu-id="e4d00-229">LastName</span></span>|<span data-ttu-id="e4d00-230">id</span><span class="sxs-lookup"><span data-stu-id="e4d00-230">ID</span></span>|  
    |--------------|---------------|--------------|--------|  
    |<span data-ttu-id="e4d00-231">1</span><span class="sxs-lookup"><span data-stu-id="e4d00-231">1</span></span>|<span data-ttu-id="e4d00-232">Bobby</span><span class="sxs-lookup"><span data-stu-id="e4d00-232">Bobby</span></span>|<span data-ttu-id="e4d00-233">Moore</span><span class="sxs-lookup"><span data-stu-id="e4d00-233">Moore</span></span>|<span data-ttu-id="e4d00-234">11</span><span class="sxs-lookup"><span data-stu-id="e4d00-234">11</span></span>|  
    |<span data-ttu-id="e4d00-235">2</span><span class="sxs-lookup"><span data-stu-id="e4d00-235">2</span></span>|<span data-ttu-id="e4d00-236">Bobby</span><span class="sxs-lookup"><span data-stu-id="e4d00-236">Bobby</span></span>|<span data-ttu-id="e4d00-237">Moore</span><span class="sxs-lookup"><span data-stu-id="e4d00-237">Moore</span></span>|<span data-ttu-id="e4d00-238">11</span><span class="sxs-lookup"><span data-stu-id="e4d00-238">11</span></span>|  
    |<span data-ttu-id="e4d00-239">8</span><span class="sxs-lookup"><span data-stu-id="e4d00-239">8</span></span>|<span data-ttu-id="e4d00-240">Crystal</span><span class="sxs-lookup"><span data-stu-id="e4d00-240">Crystal</span></span>|<span data-ttu-id="e4d00-241">Hu</span><span class="sxs-lookup"><span data-stu-id="e4d00-241">Hu</span></span>|<span data-ttu-id="e4d00-242">20</span><span class="sxs-lookup"><span data-stu-id="e4d00-242">20</span></span>|  
    |<span data-ttu-id="e4d00-243">15</span><span class="sxs-lookup"><span data-stu-id="e4d00-243">15</span></span>|<span data-ttu-id="e4d00-244">Wyatt</span><span class="sxs-lookup"><span data-stu-id="e4d00-244">Wyatt</span></span>|<span data-ttu-id="e4d00-245">Diaz</span><span class="sxs-lookup"><span data-stu-id="e4d00-245">Diaz</span></span>|<span data-ttu-id="e4d00-246">33</span><span class="sxs-lookup"><span data-stu-id="e4d00-246">33</span></span>|  
  
#### <a name="xml-document-customersxml"></a><span data-ttu-id="e4d00-247">XML ドキュメント: Customers.xml</span><span class="sxs-lookup"><span data-stu-id="e4d00-247">XML document: Customers.xml</span></span>  
 <span data-ttu-id="e4d00-248">前のセクションの要素パスの例を試すには、この XML をコピーして、レポート デザイナーからアクセス可能な URL に保存した後、この XML ドキュメントを XML データ ソースとして使用します (例: `http://localhost/Customers.xml`)。</span><span class="sxs-lookup"><span data-stu-id="e4d00-248">To try out the element path examples in the previous section, you can copy this XML and save it to a URL that is accessible by Report Designer, and then use the XML document as an XML data source: for example, `http://localhost/Customers.xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<Customers xmlns="http://www.adventure-works.com">  
   <Customer ID="11">  
      <FirstName>Bobby</FirstName>  
      <LastName>Moore</LastName>  
      <Orders>  
         <Order ID="1" Qty="6">Chair</Order>  
         <Order ID="2" Qty="1">Table</Order>  
      </Orders>  
      <Returns>  
         <Return ID="1" Qty="2">Chair</Return>  
      </Returns>  
   </Customer>  
   <Customer ID="20">  
      <FirstName>Crystal</FirstName>  
      <LastName>Hu</LastName>  
      <Orders>  
         <Order ID="8" Qty="2">Sofa</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
   <Customer ID="33">  
      <FirstName>Wyatt</FirstName>  
      <LastName>Diaz</LastName>  
      <Orders>  
         <Order ID="15" Qty="2">EndTables</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
</Customers>  
```  
  
 <span data-ttu-id="e4d00-249">または、次のプロシージャを使用して、接続文字列のない XML データ ソースを作成し、クエリに Customers.XML を埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-249">Alternatively, you can create an XML data source that has no connection string and embed Customers.XML in the query, using the following procedure:</span></span>  
  
###### <a name="to-embed-customersxml-in-a-query"></a><span data-ttu-id="e4d00-250">クエリに Customers.XML を埋め込むには</span><span class="sxs-lookup"><span data-stu-id="e4d00-250">To embed Customers.XML in a query</span></span>  
  
1.  <span data-ttu-id="e4d00-251">空白の接続文字列を使用して、XML データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-251">Create an XML data source with a blank connection string.</span></span>  
  
2.  <span data-ttu-id="e4d00-252">XML データ ソースに新しいデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-252">Create a new dataset for the XML data source.</span></span>  
  
3.  <span data-ttu-id="e4d00-253">**[データセットのプロパティ]** ダイアログ ボックスの **[クエリ デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4d00-253">In the **Dataset Properties** dialog box, click **Query Designer**.</span></span> <span data-ttu-id="e4d00-254">テキスト ベースのクエリ デザイナー ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-254">The text-based query designer dialog box opens.</span></span>  
  
4.  <span data-ttu-id="e4d00-255">クエリ ペインに次の 2 行を入力します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-255">In the query pane, enter the following two lines:</span></span>  
  
     `<Query>`  
  
     `<XmlData>`  
  
5.  <span data-ttu-id="e4d00-256">Customers.XML をコピーし、クエリ ペインで、 `<XmlData>`の後にそのテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-256">Copy Customers.XML and paste the text in the query pane after `<XmlData>`.</span></span>  
  
6.  <span data-ttu-id="e4d00-257">クエリ ペインで、Customers.XML からコピーした最初の行を削除します。 `<?xml version="1.0"?>`</span><span class="sxs-lookup"><span data-stu-id="e4d00-257">In the query pane, delete the first line that you copied from Customers.XML: `<?xml version="1.0"?>`</span></span>  
  
7.  <span data-ttu-id="e4d00-258">クエリの最後に次の 2 行を追加します。</span><span class="sxs-lookup"><span data-stu-id="e4d00-258">At the end of the query, add the following two lines:</span></span>  
  
     `<XmlData>`  
  
     `<Query>`  
  
8.  <span data-ttu-id="e4d00-259">**[クエリの実行]** (!) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4d00-259">Click **Run Query** (!).</span></span>  
  
     <span data-ttu-id="e4d00-260">`xmlns`、 `Customer.ID`、 `FirstName`、 `LastName`、 `ID`、 `Qty`、 `Order`という列を含む 4 行のデータが結果セットに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4d00-260">The result set displays 4 lines of data with the following columns: `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e4d00-261">参照</span><span class="sxs-lookup"><span data-stu-id="e4d00-261">See Also</span></span>  
 <span data-ttu-id="e4d00-262">[XML 接続の種類 &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e4d00-262">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 <span data-ttu-id="e4d00-263">[SSRS&#41;&#40;チュートリアル Reporting Services](../reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e4d00-263">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="e4d00-264">レポート データ ペインでのフィールドの追加、編集、更新 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e4d00-264">Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;</span></span>](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
  
