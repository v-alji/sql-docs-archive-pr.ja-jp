---
title: XPath クエリでのブール関数の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
author: rothja
ms.author: jroth
ms.openlocfilehash: d230c7cd8792066732085b9ce501c0794687d17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631745"
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="043fc-102">XPath クエリ内での論理関数の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="043fc-102">Specifying Boolean Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="043fc-103">以下の例では、XPath クエリに論理関数を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="043fc-103">The following examples show how Boolean functions are specified in XPath queries.</span></span> <span data-ttu-id="043fc-104">これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="043fc-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="043fc-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="043fc-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="043fc-106">例</span><span class="sxs-lookup"><span data-stu-id="043fc-106">Examples</span></span>  
  
## <a name="a-specify-the-not-boolean-function"></a><span data-ttu-id="043fc-107">A.</span><span class="sxs-lookup"><span data-stu-id="043fc-107">A.</span></span> <span data-ttu-id="043fc-108">not() 論理関数を指定する</span><span class="sxs-lookup"><span data-stu-id="043fc-108">Specify the not() Boolean function</span></span>  
 <span data-ttu-id="043fc-109">このクエリでは、 **\<Customer>** 子要素を持たないコンテキストノードのすべての子要素が返され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="043fc-109">This query returns all the **\<Customer>** child elements of the context node that do not have **\<Order>** child elements:</span></span>  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 <span data-ttu-id="043fc-110">`child` 軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="043fc-110">The `child` axis is the default.</span></span> <span data-ttu-id="043fc-111">そのため、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="043fc-111">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="043fc-112">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="043fc-112">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="043fc-113">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="043fc-113">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="043fc-114">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="043fc-114">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="043fc-115">次のテンプレート (BooleanFunctionsA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="043fc-115">Create the following template (BooleanFunctionsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="043fc-116">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="043fc-116">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="043fc-117">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="043fc-117">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="043fc-118">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="043fc-118">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="043fc-119">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="043fc-119">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="043fc-120">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="043fc-120">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a><span data-ttu-id="043fc-121">B.</span><span class="sxs-lookup"><span data-stu-id="043fc-121">B.</span></span> <span data-ttu-id="043fc-122">true() 論理関数と false() 論理関数を指定する</span><span class="sxs-lookup"><span data-stu-id="043fc-122">Specify the true() and false() Boolean functions</span></span>  
 <span data-ttu-id="043fc-123">このクエリは **\<Customer>** 、子要素を持たないコンテキストノードのすべての子要素を返し **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="043fc-123">This query returns all **\<Customer>** element children of the context node that do not have **\<Order>** child elements.</span></span> <span data-ttu-id="043fc-124">具体的には、このクエリでは、発注していないすべての顧客が返されます。</span><span class="sxs-lookup"><span data-stu-id="043fc-124">In relational terms, this query returns all customers who have not placed any orders.</span></span>  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 <span data-ttu-id="043fc-125">`child` 軸は既定の軸です。</span><span class="sxs-lookup"><span data-stu-id="043fc-125">The `child` axis is the default.</span></span> <span data-ttu-id="043fc-126">そのため、クエリは次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="043fc-126">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order=false()]  
```  
  
 <span data-ttu-id="043fc-127">このクエリは、次の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="043fc-127">This query is equivalent to the following:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
 <span data-ttu-id="043fc-128">次のクエリでは、少なくとも 1 回発注したすべての顧客が返されます。</span><span class="sxs-lookup"><span data-stu-id="043fc-128">The following query returns all the customers who have placed at least one order:</span></span>  
  
```  
/Customer[Order=true()]  
```  
  
 <span data-ttu-id="043fc-129">このクエリは、次の指定と同じです。</span><span class="sxs-lookup"><span data-stu-id="043fc-129">This query is equivalent to this one:</span></span>  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="043fc-130">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="043fc-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="043fc-131">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="043fc-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="043fc-132">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="043fc-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="043fc-133">次のテンプレート (BooleanFunctionsB.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="043fc-133">Create the following template (BooleanFunctionsB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="043fc-134">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="043fc-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="043fc-135">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="043fc-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="043fc-136">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="043fc-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="043fc-137">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="043fc-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="043fc-138">テンプレートを実行して得られる結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="043fc-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  
