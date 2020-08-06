---
title: XPath クエリでの算術演算子の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- arithmetic operators
- XPath operators [SQLXML]
- XPath queries [SQLXML], arithmetic operators
- operators [SQLXML]
ms.assetid: fdfbc87d-759f-4abc-acf5-a21de01f78d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 904f3b920029d45d1b72641a19e2ac07befd4def
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631748"
---
# <a name="specifying-arithmetic-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="22cbe-102">XPath クエリ内での算術演算子の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="22cbe-102">Specifying Arithmetic Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="22cbe-103">以下の例では、XPath クエリに算術演算子を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="22cbe-103">The following example shows how arithmetic operators are specified in XPath queries.</span></span> <span data-ttu-id="22cbe-104">この例の XPath クエリは、SampleSchema1.xml に格納されているマッピング スキーマに対して指定されます。</span><span class="sxs-lookup"><span data-stu-id="22cbe-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="22cbe-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22cbe-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="22cbe-106">例</span><span class="sxs-lookup"><span data-stu-id="22cbe-106">Examples</span></span>  
  
### <a name="a-specify-the--arithmetic-operator"></a><span data-ttu-id="22cbe-107">A.</span><span class="sxs-lookup"><span data-stu-id="22cbe-107">A.</span></span> <span data-ttu-id="22cbe-108">\* 算術演算子を指定する</span><span class="sxs-lookup"><span data-stu-id="22cbe-108">Specify the \* arithmetic operator</span></span>  
 <span data-ttu-id="22cbe-109">この XPath クエリ **\<OrderDetail>** は、指定された述語を満たす要素を返します。</span><span class="sxs-lookup"><span data-stu-id="22cbe-109">This XPath query returns **\<OrderDetail>** elements that satisfy the predicate specified:</span></span>  
  
```  
/child::OrderDetail[@UnitPrice * @Quantity = 12.350]  
```  
  
 <span data-ttu-id="22cbe-110">このクエリでは、は軸で、は `child` `OrderDetail` ノードテストです。これは、 **OrderDetail** **\<element node>** **\<element>** ノードが軸のプライマリノードであるため、ORDERDETAIL がの場合は TRUE です `child` 。</span><span class="sxs-lookup"><span data-stu-id="22cbe-110">In the query, `child` is the axis and `OrderDetail` is the node test (TRUE if **OrderDetail** is an **\<element node>**, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="22cbe-111">すべての要素ノードについて、 **\<OrderDetail>** 述語内のテストが適用され、条件を満たすノードだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="22cbe-111">For all the **\<OrderDetail>** element nodes, the test in the predicate is applied, and only those nodes that satisfy the condition are returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22cbe-112">XPath の数値は倍精度浮動小数点数であり、例のように浮動小数点数を比較する場合は丸めが実行されます。</span><span class="sxs-lookup"><span data-stu-id="22cbe-112">The numbers in XPath are double-precision floating-point numbers, and comparing floating-point numbers as in the example causes rounding.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="22cbe-113">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="22cbe-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="22cbe-114">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="22cbe-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="22cbe-115">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="22cbe-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="22cbe-116">次のテンプレート (ArithmeticOperatorA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="22cbe-116">Create the following template (ArithmeticOperatorA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /OrderDetail[@UnitPrice * @OrderQty = 12.350]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="22cbe-117">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="22cbe-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="22cbe-118">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="22cbe-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="22cbe-119">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="22cbe-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="22cbe-120">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22cbe-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
```  
Here is the partial result set of the template execution:    
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-710" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
   ...  
</ROOT>  
```  
  
  
