---
title: XPath クエリでのブール値述語の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- nested predicates
- successive predicates
- predicates [SQLXML]
- top-level predicates
- Boolean-valued predicates
- multiple predicates
ms.assetid: 5f6e7219-6911-4bca-a54b-56b95e0b43dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 56f2f94ec895c5b76382d5103ca9d518b78cc899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631743"
---
# <a name="specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="c1dc3-102">XPath クエリでのブール値述語の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c1dc3-102">Specifying Boolean-Valued Predicates in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="c1dc3-103">以下の例では、XPath クエリにブール値述語を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-103">The following examples show how Boolean-valued predicates are specified in XPath queries.</span></span> <span data-ttu-id="c1dc3-104">これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="c1dc3-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c1dc3-106">例</span><span class="sxs-lookup"><span data-stu-id="c1dc3-106">Examples</span></span>  
  
### <a name="a-specify-multiple-predicates"></a><span data-ttu-id="c1dc3-107">A.</span><span class="sxs-lookup"><span data-stu-id="c1dc3-107">A.</span></span> <span data-ttu-id="c1dc3-108">複数の述語を指定する</span><span class="sxs-lookup"><span data-stu-id="c1dc3-108">Specify multiple predicates</span></span>  
 <span data-ttu-id="c1dc3-109">次の XPath クエリでは、複数の述語を使用して、任意の注文 ID と顧客 ID の注文情報を検索します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-109">The following XPath query uses multiple predicates to find order information for a given order ID and a customer ID:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]/child::Order[attribute::OrderID="Ord-43860"]  
```  
  
 <span data-ttu-id="c1dc3-110">軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c1dc3-111">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c1dc3-111">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c1dc3-112">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-112">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c1dc3-113">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-113">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c1dc3-114">次のテンプレート (BooleanValuedPredicatesA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-114">Create the following template (BooleanValuedPredicatesA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c1dc3-115">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-115">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c1dc3-116">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-116">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c1dc3-117">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-117">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c1dc3-118">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-118">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
     <span data-ttu-id="c1dc3-119">以下に結果を示します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-119">Here is the result:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
        <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-761" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-762" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-765" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-768" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-770" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
      </Order>  
    </ROOT>  
    ```  
  
### <a name="b-specify-successive-and-nested-predicates"></a><span data-ttu-id="c1dc3-120">B.</span><span class="sxs-lookup"><span data-stu-id="c1dc3-120">B.</span></span> <span data-ttu-id="c1dc3-121">連続する述語を入れ子で指定する</span><span class="sxs-lookup"><span data-stu-id="c1dc3-121">Specify successive and nested predicates</span></span>  
 <span data-ttu-id="c1dc3-122">次のクエリでは、述語を連続して使用しています。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-122">The following query shows using successive predicates.</span></span> <span data-ttu-id="c1dc3-123">このクエリでは、 **\<Customer>** **SalesPersonID**属性の値が277で、 **TerritoryID**属性の値が3であるコンテキストノードのすべての子要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-123">The query returns all the **\<Customer>** child elements of the context node that have both a **SalesPersonID** attribute with a value of 277 and a **TerritoryID** attribute with a value of 3:</span></span>  
  
```  
/child::Customer[attribute::SalesPersonID="277"][attribute::TerritoryID="3"]  
```  
  
 <span data-ttu-id="c1dc3-124">このクエリは、 **\<Customer>** 述語で指定された両方の条件を満たす要素を返します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-124">The query returns the **\<Customer>** elements that satisfy both the conditions specified in the predicates.</span></span>  
  
 <span data-ttu-id="c1dc3-125">軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-125">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@SalesPersonID="277"][@TerritoryID="3"]  
```  
  
 <span data-ttu-id="c1dc3-126">次の XPath クエリでは、述語を入れ子にして使用しています。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-126">The following XPath query illustrates the use of nested predicates.</span></span> <span data-ttu-id="c1dc3-127">このクエリでは、 **\<Customer>** **\<Order>** **\<Order>** **SalesPersonID**属性の値が2である1つ以上の要素を含む子要素を含むコンテキストノードのすべての子要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-127">The query returns all the **\<Customer>** child elements of the context node that include **\<Order>** child elements with at least one **\<Order>** element that has a **SalesPersonID** attribute value of 2.</span></span>  
  
```  
/Customer[Order[@SalesPersonID=2]]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c1dc3-128">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c1dc3-128">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c1dc3-129">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-129">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c1dc3-130">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-130">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c1dc3-131">次のテンプレート (nestedSuccessive.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-131">Create the following template (nestedSuccessive.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
             /Customer[@SalesPersonID="277"][@TerritoryID="3"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c1dc3-132">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-132">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c1dc3-133">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c1dc3-134">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c1dc3-135">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c1dc3-136">次は結果の一部です。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-136">The following is a partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="22" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="22" CustomerType="S"   
            Orders="Ord-43874 Ord-44519 Ord-46989 Ord-48013 Ord-49130 Ord-50274 Ord-51807 Ord-57113 Ord-63162 Ord-69495">  
    <Order SalesOrderID="Ord-43874" SalesPersonID="277"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
                   OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    ...  
  </Customer>  
  <Customer CustomerID="39" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="39" CustomerType="S"   
            Orders="Ord-47428 Ord-48367 Ord-49529 Ord-50742 Ord-53591 Ord-59051 Ord-65301 Ord-71912">    <Order SalesOrderID="Ord-47428" SalesPersonID="277"   
           OrderDate="2002-09-01T00:00:00"   
           DueDate="2002-09-13T00:00:00"   
           ShipDate="2002-09-08T00:00:00">  
      <OrderDetail ProductID="Prod-759" UnitPrice="563.7528" OrderQty="2" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-769" UnitPrice="563.7528" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
### <a name="c-specify-a-top-level-predicate"></a><span data-ttu-id="c1dc3-137">C.</span><span class="sxs-lookup"><span data-stu-id="c1dc3-137">C.</span></span> <span data-ttu-id="c1dc3-138">最上位の述語を指定する</span><span class="sxs-lookup"><span data-stu-id="c1dc3-138">Specify a top-level predicate</span></span>  
 <span data-ttu-id="c1dc3-139">次のクエリでは、子 **\<Customer>** 要素を持つコンテキストノードの子要素ノードが返され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-139">The following query returns the **\<Customer>** child element nodes of the context node that have **\<Order>** element children.</span></span> <span data-ttu-id="c1dc3-140">このクエリでは、ロケーション パスを最上位の述語としてテストします。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-140">The query tests the location path as the top-level predicate:</span></span>  
  
```  
/child::Customer[child::Order]  
```  
  
 <span data-ttu-id="c1dc3-141">`child` 軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-141">The `child` axis is the default.</span></span> <span data-ttu-id="c1dc3-142">そのため、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-142">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c1dc3-143">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c1dc3-143">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c1dc3-144">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-144">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c1dc3-145">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-145">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c1dc3-146">次のテンプレート (TopLevelPredicate.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-146">Create the following template (TopLevelPredicate.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c1dc3-147">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-147">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c1dc3-148">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c1dc3-149">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c1dc3-150">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c1dc3-151">次に結果の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="c1dc3-151">Here is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280" TerritoryID="1" AccountNumber="1" CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    <Order SalesOrderID="Ord-44501" SalesPersonID="280" OrderDate="2001-11-01T00:00:00" DueDate="2001-11-13T00:00:00" ShipDate="2001-11-08T00:00:00">  
      <OrderDetail ProductID="Prod-725" UnitPrice="226.8571" OrderQty="3" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-726" UnitPrice="226.8571" OrderQty="2" UnitPriceDiscount="0" />   
      ...  
    </Order>    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
  
