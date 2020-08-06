---
title: XPath クエリでの軸の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- context node [SQLXML]
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- axes [SQLXML]
ms.assetid: d17b8278-da58-4576-95b4-7a92772566d8
author: rothja
ms.author: jroth
ms.openlocfilehash: f6f17404ea109bb0e687f9116b61025bbc411008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631747"
---
# <a name="specifying-axes-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="4572a-102">XPath クエリ内での軸の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4572a-102">Specifying Axes in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="4572a-103">以下の例では、XPath クエリに軸を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4572a-103">The following examples show how axes are specified in XPath queries.</span></span>  
  
 <span data-ttu-id="4572a-104">これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="4572a-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="4572a-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4572a-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4572a-106">例</span><span class="sxs-lookup"><span data-stu-id="4572a-106">Examples</span></span>  
  
### <a name="a-retrieve-child-elements-of-the-context-node"></a><span data-ttu-id="4572a-107">A.</span><span class="sxs-lookup"><span data-stu-id="4572a-107">A.</span></span> <span data-ttu-id="4572a-108">コンテキスト ノードの子要素を取得する</span><span class="sxs-lookup"><span data-stu-id="4572a-108">Retrieve child elements of the context node</span></span>  
 <span data-ttu-id="4572a-109">次の XPath クエリでは、 **\<Contact>** コンテキストノードのすべての子要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="4572a-109">The following XPath query selects all the **\<Contact>** child elements of the context node:</span></span>  
  
```  
/child::Contact  
```  
  
 <span data-ttu-id="4572a-110">このクエリでは、は軸で、は `child` `Contact` ノードテストです (がノードの場合は TRUE `Contact` **\<element>** \<element> 。は軸に関連付けられているプライマリノード型であるためです `child` )。</span><span class="sxs-lookup"><span data-stu-id="4572a-110">In the query, `child` is the axis and `Contact` is the node test (TRUE if `Contact` is an **\<element>** node, because \<element> is the primary node type associated with the `child` axis).</span></span>  
  
 <span data-ttu-id="4572a-111">`child` 軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="4572a-111">The `child` axis is the default.</span></span> <span data-ttu-id="4572a-112">したがって、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="4572a-112">Therefore, the query can be written as:</span></span>  
  
```  
/Contact  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4572a-113">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="4572a-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4572a-114">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4572a-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4572a-115">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4572a-116">次のテンプレート (XPathAxesSampleA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-116">Create the following template (XPathAxesSampleA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4572a-117">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="4572a-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4572a-118">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4572a-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4572a-119">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4572a-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4572a-120">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4572a-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4572a-121">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4572a-121">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Contact ContactID="1" LastName="Achong" FirstName="Gustavo" Title="Mr." />   
  <Contact ContactID="2" LastName="Abel" FirstName="Catherine" Title="Ms." />   
  <Contact ContactID="3" LastName="Abercrombie" FirstName="Kim" Title="Ms." />   
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />  
  ...  
</ROOT>  
```  
  
### <a name="b-retrieve-grandchildren-of-the-context-node"></a><span data-ttu-id="4572a-122">B.</span><span class="sxs-lookup"><span data-stu-id="4572a-122">B.</span></span> <span data-ttu-id="4572a-123">コンテキスト ノードの孫を取得する</span><span class="sxs-lookup"><span data-stu-id="4572a-123">Retrieve grandchildren of the context node</span></span>  
 <span data-ttu-id="4572a-124">次の XPath クエリでは、 **\<Order>** コンテキストノードの子要素のすべての子要素を選択し **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="4572a-124">The following XPath query selects all the **\<Order>** element children of the **\<Customer>** element children of the context node:</span></span>  
  
```  
/child::Customer/child::Order  
```  
  
 <span data-ttu-id="4572a-125">このクエリで `child` は、は軸で、は `Customer` `Order` ノードテストです ( **\<element>** ノードが軸のプライマリノードであるため、Customer と Order がノードである場合、これらのノードテストは TRUE に **\<element>** `child` なります)。</span><span class="sxs-lookup"><span data-stu-id="4572a-125">In the query, `child` is the axis and `Customer` and `Order` are the node tests (these node tests are TRUE if Customer and Order are **\<element>** nodes, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="4572a-126">一致するノードごとに **\<Customer>** 、一致 **\<Orders>** するノードが結果に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4572a-126">For each node matching **\<Customer>**, the nodes matching **\<Orders>** are added to the result.</span></span> <span data-ttu-id="4572a-127">**\<Order>** 結果セットにのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="4572a-127">Only **\<Order>** is returned in the result set.</span></span>  
  
 <span data-ttu-id="4572a-128">`child` 軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="4572a-128">The `child` axis is the default.</span></span> <span data-ttu-id="4572a-129">そのため、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="4572a-129">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4572a-130">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="4572a-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4572a-131">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4572a-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4572a-132">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4572a-133">次のテンプレート (XPathAxesSampleB.xml) を作成し、ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-133">Create the following template (XPathAxesSampleB.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4572a-134">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="4572a-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4572a-135">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4572a-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4572a-136">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4572a-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4572a-137">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4572a-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4572a-138">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4572a-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</ROOT>  
```  
  
 <span data-ttu-id="4572a-139">XPath クエリがとして指定されている場合 `Customer/Order/OrderDetail` 、クエリは一致する各ノードから **\<Customer>** その要素に移動し **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="4572a-139">If the XPath query is specified as `Customer/Order/OrderDetail`, from each node matching **\<Customer>** the query navigates to its **\<Order>** elements.</span></span> <span data-ttu-id="4572a-140">また、一致するノードごとに **\<Order>** 、クエリによってノードが結果に追加され **\<OrderDetail>** ます。</span><span class="sxs-lookup"><span data-stu-id="4572a-140">And for each node matching **\<Order>**, the query adds the nodes **\<OrderDetail>** to the result.</span></span> <span data-ttu-id="4572a-141">**\<OrderDetail>** 結果セットにのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="4572a-141">Only **\<OrderDetail>** is returned in the result set.</span></span>  
  
### <a name="c-use--to-specify-the-parent-axis"></a><span data-ttu-id="4572a-142">C.</span><span class="sxs-lookup"><span data-stu-id="4572a-142">C.</span></span> <span data-ttu-id="4572a-143">.. を使用して </span><span class="sxs-lookup"><span data-stu-id="4572a-143">Use ..</span></span> <span data-ttu-id="4572a-144">parent 軸を指定する</span><span class="sxs-lookup"><span data-stu-id="4572a-144">to specify the parent axis</span></span>  
 <span data-ttu-id="4572a-145">次のクエリでは、 **\<Order>** **\<Customer>** **CustomerID**属性値が1である親要素を持つすべての要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="4572a-145">The following query retrieves all the **\<Order>** elements with a parent **\<Customer>** element with a **CustomerID** attribute value of 1.</span></span> <span data-ttu-id="4572a-146">このクエリでは、述語の軸を使用して、 `child` 要素の親を検索し **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="4572a-146">The query uses the `child` axis in the predicate to find the parent of the **\<Order>** element.</span></span>  
  
```  
/child::Customer/child::Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="4572a-147">`child`軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="4572a-147">The `child` axis is the default axis.</span></span> <span data-ttu-id="4572a-148">そのため、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="4572a-148">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="4572a-149">この XPath クエリは、次の指定と同じです。</span><span class="sxs-lookup"><span data-stu-id="4572a-149">The XPath query is equivalent to:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4572a-150">`/Order[../@CustomerID="1"]`の親が存在しないため、XPath クエリからエラーが返され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="4572a-150">The XPath query `/Order[../@CustomerID="1"]` will return an error because there is no parent of **\<Order>**.</span></span> <span data-ttu-id="4572a-151">が含まれるマッピングスキーマには要素が存在する場合があり **\<Order>** ますが、XPath はいずれの要素からも開始されませんでした。したがって、 **\<Order>** はドキュメントの最上位要素型と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4572a-151">Although there may be elements in the mapping schema that contain **\<Order>**, the XPath did not begin at any of them; consequently, **\<Order>** is considered to be the top-level element type in the document.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4572a-152">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="4572a-152">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4572a-153">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4572a-153">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4572a-154">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-154">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4572a-155">次のテンプレート (XPathAxesSampleC.xml) を作成し、ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-155">Create the following template (XPathAxesSampleC.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order[../@CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4572a-156">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="4572a-156">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4572a-157">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4572a-157">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4572a-158">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4572a-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4572a-159">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4572a-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4572a-160">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4572a-160">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</Order>  
</ROOT>  
```  
  
### <a name="d-specify-the-attribute-axis"></a><span data-ttu-id="4572a-161">D.</span><span class="sxs-lookup"><span data-stu-id="4572a-161">D.</span></span> <span data-ttu-id="4572a-162">attribute 軸を指定する</span><span class="sxs-lookup"><span data-stu-id="4572a-162">Specify the attribute axis</span></span>  
 <span data-ttu-id="4572a-163">次の XPath クエリでは、 **\<Customer>** **CustomerID**属性値が1のコンテキストノードのすべての子要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="4572a-163">The following XPath query selects all the **\<Customer>** child elements of the context node with a **CustomerID** attribute value of 1:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]  
```  
  
 <span data-ttu-id="4572a-164">述語で `attribute::CustomerID` は、 `attribute` は軸で、は `CustomerID` ノードテストです (が属性の場合、ノードは `CustomerID` 軸のプライマリノードであるため、ノードテストは TRUE になり **\<attribute>** `attribute` ます)。</span><span class="sxs-lookup"><span data-stu-id="4572a-164">In the predicate `attribute::CustomerID`, `attribute` is the axis and `CustomerID` is the node test (if `CustomerID` is an attribute the node test is TRUE, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span>  
  
 <span data-ttu-id="4572a-165">`attribute` 軸は省略形 (@) で指定できます。また、`child` 軸は既定の軸なので、クエリから省略できます。</span><span class="sxs-lookup"><span data-stu-id="4572a-165">A shortcut to the `attribute` axis (@) can be specified, and because `child` is the default axis, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4572a-166">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="4572a-166">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4572a-167">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4572a-167">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4572a-168">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-168">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4572a-169">次のテンプレート (XPathAxesSampleD.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="4572a-169">Create the following template (XPathAxesSampleD.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        child::Customer[attribute::CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4572a-170">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="4572a-170">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4572a-171">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4572a-171">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4572a-172">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="4572a-172">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4572a-173">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4572a-173">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4572a-174">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4572a-174">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280"   
            TerritoryID="1" AccountNumber="1"   
            CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
       <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
                    OrderQty="1" UnitPriceDiscount="0" />   
      ...   
    </Order>  
   ...  
  </Customer>  
</ROOT>  
```  
  
  
