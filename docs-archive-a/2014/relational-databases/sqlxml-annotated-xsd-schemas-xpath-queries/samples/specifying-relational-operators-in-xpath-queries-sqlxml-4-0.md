---
title: XPath クエリでの関係演算子の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], relational operators
- relational operators [SQLXML]
- XPath operators [SQLXML]
- operators [SQLXML]
ms.assetid: 177a0eb2-11ef-4459-a317-485a433ee769
author: rothja
ms.author: jroth
ms.openlocfilehash: 50d59ebd3a776386c61f4c3a8a1e892d30981d1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631736"
---
# <a name="specifying-relational-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="03289-102">XPath クエリ内での関係演算子の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="03289-102">Specifying Relational Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="03289-103">以下の例では、XPath クエリに関係演算子を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="03289-103">The following examples show how relational operators are specified in XPath queries.</span></span> <span data-ttu-id="03289-104">これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="03289-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="03289-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03289-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="03289-106">例</span><span class="sxs-lookup"><span data-stu-id="03289-106">Examples</span></span>  
  
### <a name="a-specify-relational-operator"></a><span data-ttu-id="03289-107">A.</span><span class="sxs-lookup"><span data-stu-id="03289-107">A.</span></span> <span data-ttu-id="03289-108">関係演算子を指定する</span><span class="sxs-lookup"><span data-stu-id="03289-108">Specify relational operator</span></span>  
 <span data-ttu-id="03289-109">この XPath クエリで **\<Customer>** は、 **CustomerID**属性値が "1" で、 **\<Order>** 値が **\<OrderDetail>** 3 より大きい**OrderQty**属性を持つ子要素を含む要素の子要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="03289-109">This XPath query returns the child elements of the **\<Customer>** element where the **CustomerID** attribute value is "1" and where any child **\<Order>** elements contain an **\<OrderDetail>** child with a **OrderQty** attribute with a value greater than 3:</span></span>  
  
```  
/child::Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
 <span data-ttu-id="03289-110">角かっこで指定された述語は、要素をフィルター処理し **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="03289-110">The predicate specified in the brackets filters the **\<Customer>** elements.</span></span> <span data-ttu-id="03289-111">**\<Customer>** OrderQty 属性値が3を超える孫を1つ以上含む要素のみ **\<OrderDetail>** が返されます。</span><span class="sxs-lookup"><span data-stu-id="03289-111">Only the **\<Customer>** elements that have at least one **\<OrderDetail>** grandchild with a OrderQty attribute value greater than 3 are returned.</span></span>  
  
 <span data-ttu-id="03289-112">`child` 軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="03289-112">The `child` axis is the default.</span></span> <span data-ttu-id="03289-113">そのため、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="03289-113">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="03289-114">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="03289-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="03289-115">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="03289-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="03289-116">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="03289-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="03289-117">次のテンプレート (SpecifyRelationalA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="03289-117">Create the following template (SpecifyRelationalA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="03289-118">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="03289-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="03289-119">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="03289-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="03289-120">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="03289-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="03289-121">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03289-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="03289-122">このテンプレートを実行した場合の結果セットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="03289-122">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-760" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-766" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-757" UnitPrice="1049.7528" OrderQty="4" UnitPriceDiscount="0" />   
</ROOT>  
```  
  
### <a name="b-specify-relational-operator-in-the-xpath-query-and-use-boolean-function-to-compare-the-result"></a><span data-ttu-id="03289-123">B.</span><span class="sxs-lookup"><span data-stu-id="03289-123">B.</span></span> <span data-ttu-id="03289-124">XPath クエリに関係演算子を指定し、論理関数を使用して結果を比較する</span><span class="sxs-lookup"><span data-stu-id="03289-124">Specify relational operator in the XPath query and use Boolean function to compare the result</span></span>  
 <span data-ttu-id="03289-125">このクエリ **\<Order>** は、 **SalesPersonID**属性値が270未満であるコンテキストノードのすべての子要素を返します。</span><span class="sxs-lookup"><span data-stu-id="03289-125">This query returns all the **\<Order>** element children of the context node that have an **SalesPersonID** attribute value that is less than 270:</span></span>  
  
```  
/child::Customer/child::Order[(attribute::SalesPersonID < 270)=true()]  
```  
  
 <span data-ttu-id="03289-126">軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。</span><span class="sxs-lookup"><span data-stu-id="03289-126">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer/Order[(@SalesPersonID < 270)=true()]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="03289-127">このクエリがテンプレートで指定されている場合、< 文字は XML ドキュメント内で特別な意味を持つため、< 文字はエンティティエンコードされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="03289-127">When this query is specified in a template, the < character must be entity encoded because the < character has special meaning in an XML document.</span></span> <span data-ttu-id="03289-128">テンプレートで、を使用し `<` て < 文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="03289-128">In a template, use `<` to specify the < character.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="03289-129">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="03289-129">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="03289-130">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="03289-130">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="03289-131">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="03289-131">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="03289-132">次のテンプレート (SpecifyRelationalB.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="03289-132">Create the following template (SpecifyRelationalB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="SampleSchema1.xml">  
            /Customer/Order[(@SalesPersonID<270)=true()]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="03289-133">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="03289-133">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="03289-134">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="03289-134">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="03289-135">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="03289-135">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="03289-136">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03289-136">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="03289-137">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="03289-137">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-46613" SalesPersonID="268"   
         OrderDate="2002-07-01T00:00:00"   
         DueDate="2002-07-13T00:00:00"   
         ShipDate="2002-07-08T00:00:00">  
    <OrderDetail ProductID="Prod-739" UnitPrice="917.9363"   
                 OrderQty="2" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-779" UnitPrice="1491.4221"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-825" UnitPrice="242.1391"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  <Order SalesOrderID="Ord-71919" SalesPersonID="268"  
         OrderDate="2004-06-01T00:00:00"   
         DueDate="2004-06-13T00:00:00"   
         ShipDate="2004-06-08T00:00:00">  
    <OrderDetail ProductID="Prod-961" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-965" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-966" UnitPrice="1716.5304"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  ...  
</ROOT>  
```  
  
  
