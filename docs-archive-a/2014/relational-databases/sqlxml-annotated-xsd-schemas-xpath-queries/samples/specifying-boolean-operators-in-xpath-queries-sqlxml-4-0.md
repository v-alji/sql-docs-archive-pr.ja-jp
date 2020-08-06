---
title: XPath クエリでのブール演算子の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dd6e1f120b53382ce984684ea352b36d34b768
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631744"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="fb478-102">XPath クエリ内での論理演算子の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="fb478-102">Specifying Boolean Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="fb478-103">以下の例では、XPath クエリに論理演算子を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fb478-103">The following example shows how Boolean operators are specified in XPath queries.</span></span> <span data-ttu-id="fb478-104">この例の XPath クエリは、SampleSchema1.xml に格納されているマッピング スキーマに対して指定されます。</span><span class="sxs-lookup"><span data-stu-id="fb478-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="fb478-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb478-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fb478-106">例</span><span class="sxs-lookup"><span data-stu-id="fb478-106">Examples</span></span>  
  
### <a name="a-specify-the-or-boolean-operator"></a><span data-ttu-id="fb478-107">A.</span><span class="sxs-lookup"><span data-stu-id="fb478-107">A.</span></span> <span data-ttu-id="fb478-108">OR 論理演算子を指定する</span><span class="sxs-lookup"><span data-stu-id="fb478-108">Specify the OR Boolean operator</span></span>  
 <span data-ttu-id="fb478-109">この XPath クエリでは、 **\<Customer>** **CustomerID**属性値が13または31のコンテキストノードの子要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="fb478-109">This XPath query returns the **\<Customer>** element children of the context node with the **CustomerID** attribute value of 13 or 31:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 <span data-ttu-id="fb478-110">`attribute` 軸は省略形 (@) で指定できます。また、`child` 軸は既定の軸なので省略できます。</span><span class="sxs-lookup"><span data-stu-id="fb478-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted:</span></span>  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 <span data-ttu-id="fb478-111">述語では、 `attribute` は軸で、 `CustomerID` はノードテストです。これは**CustomerID** 、 **\<attribute>** **\<attribute>** ノードが軸のプライマリノードであるため、CUSTOMERID がノードの場合は TRUE に `attribute` なります。</span><span class="sxs-lookup"><span data-stu-id="fb478-111">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an **\<attribute>** node, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span> <span data-ttu-id="fb478-112">述語は、要素をフィルター処理 **\<Customer>** し、述語に指定された条件を満たす要素のみを返します。</span><span class="sxs-lookup"><span data-stu-id="fb478-112">The predicate filters the **\<Customer>** elements and returns only those that satisfy the condition specified in the predicate.</span></span>  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a><span data-ttu-id="fb478-113">マッピングスキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="fb478-113">To test the XPath queries against the mapping schema</span></span>  
  
1.  <span data-ttu-id="fb478-114">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="fb478-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="fb478-115">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="fb478-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="fb478-116">次のテンプレート (BooleanOperatorsA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="fb478-116">Create the following template (BooleanOperatorsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="fb478-117">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="fb478-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="fb478-118">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="fb478-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="fb478-119">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb478-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fb478-120">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb478-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fb478-121">このテンプレートを実行した場合の結果セットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fb478-121">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
