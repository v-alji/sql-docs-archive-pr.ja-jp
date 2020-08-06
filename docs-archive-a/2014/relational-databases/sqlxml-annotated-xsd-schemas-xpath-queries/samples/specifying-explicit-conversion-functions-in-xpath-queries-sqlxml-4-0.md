---
title: XPath クエリでの明示的な変換関数の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b4b9bd5f5665c8cb86cb74c1397e2bd06e113fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631740"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="c92df-102">XPath クエリでの明示変換関数の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c92df-102">Specifying Explicit Conversion Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="c92df-103">次の例では、XPath クエリに明示変換関数を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c92df-103">The following examples show how explicit conversion functions are specified in XPath queries.</span></span> <span data-ttu-id="c92df-104">これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="c92df-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="c92df-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92df-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c92df-106">例</span><span class="sxs-lookup"><span data-stu-id="c92df-106">Examples</span></span>  
  
### <a name="a-use-the-number-explicit-conversion-function"></a><span data-ttu-id="c92df-107">A.</span><span class="sxs-lookup"><span data-stu-id="c92df-107">A.</span></span> <span data-ttu-id="c92df-108">number() 明示変換関数を使用する</span><span class="sxs-lookup"><span data-stu-id="c92df-108">Use the number() explicit conversion function</span></span>  
 <span data-ttu-id="c92df-109">`number()` 関数は、引数を数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="c92df-109">The `number()` function converts an argument to a number.</span></span>  
  
 <span data-ttu-id="c92df-110">**ContactID**の値が数値以外の場合、次のクエリは**ContactID**を数値に変換し、値4と比較します。</span><span class="sxs-lookup"><span data-stu-id="c92df-110">Assuming the value of **ContactID** is nonnumeric, the following query converts **ContactID** to a number and compares it with the value 4.</span></span> <span data-ttu-id="c92df-111">次に、クエリは **\<Employee>** コンテキストノードのすべての子要素を返します。 **ContactID**属性の数値は4です。</span><span class="sxs-lookup"><span data-stu-id="c92df-111">The query then returns all **\<Employee>** element children of the context node with the **ContactID** attribute that has a numeric value of 4:</span></span>  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 <span data-ttu-id="c92df-112">軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。</span><span class="sxs-lookup"><span data-stu-id="c92df-112">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 <span data-ttu-id="c92df-113">関係用語では、クエリは**ContactID**が4の従業員を返します。</span><span class="sxs-lookup"><span data-stu-id="c92df-113">In relational terms, the query returns an employee with a **ContactID** of 4.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c92df-114">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c92df-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c92df-115">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c92df-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c92df-116">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="c92df-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c92df-117">次のテンプレート (ExplicitConversionA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c92df-117">Create the following template (ExplicitConversionA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c92df-118">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c92df-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c92df-119">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c92df-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c92df-120">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c92df-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c92df-121">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92df-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c92df-122">このテンプレート実行の結果セットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c92df-122">The result set for this template execution is:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a><span data-ttu-id="c92df-123">B.</span><span class="sxs-lookup"><span data-stu-id="c92df-123">B.</span></span> <span data-ttu-id="c92df-124">string() 明示変換関数を使用する</span><span class="sxs-lookup"><span data-stu-id="c92df-124">Use the string() explicit conversion function</span></span>  
 <span data-ttu-id="c92df-125">`string()` 関数は、引数を文字列に変換します。</span><span class="sxs-lookup"><span data-stu-id="c92df-125">The `string()` function converts an argument to a string.</span></span>  
  
 <span data-ttu-id="c92df-126">次のクエリでは、 **ContactID**を文字列に変換し、文字列値 "4" と比較します。</span><span class="sxs-lookup"><span data-stu-id="c92df-126">The following query converts **ContactID** to a string and compares it with the string value "4".</span></span> <span data-ttu-id="c92df-127">このクエリは、 **\<Employee>** コンテキストノードのすべての子要素を返します。文字列値が "4" の**ContactID**が返されます。</span><span class="sxs-lookup"><span data-stu-id="c92df-127">The query returns all **\<Employee>** element children of the context node with a **ContactID** with a string value of "4":</span></span>  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 <span data-ttu-id="c92df-128">軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。</span><span class="sxs-lookup"><span data-stu-id="c92df-128">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 <span data-ttu-id="c92df-129">機能的には、このクエリでは上の例のクエリと同じ結果が返されます。ただし、評価は数値 (4) ではなく文字列に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="c92df-129">Functionally, this query returns the same results as the previous example query, though the evaluation is done against a string value and not the numeric value (that is, the number 4).</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c92df-130">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c92df-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c92df-131">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c92df-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c92df-132">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="c92df-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c92df-133">次のテンプレート (ExplicitConversionB.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c92df-133">Create the following template (ExplicitConversionB.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c92df-134">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c92df-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c92df-135">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c92df-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c92df-136">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c92df-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c92df-137">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c92df-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c92df-138">このテンプレートを実行した場合の結果セットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c92df-138">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
