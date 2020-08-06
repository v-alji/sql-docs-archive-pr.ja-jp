---
title: XPath クエリでの XPath 変数の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], XPath variables
- XPath variables [SQLXML]
ms.assetid: c11ab816-11b8-4131-8b77-c03fe500fa10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5045831f627722f7dbb9a9189be5c48d830f2add
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631733"
---
# <a name="specifying-xpath-variables-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="49673-102">XPath クエリ内での XPath 変数の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="49673-102">Specifying XPath Variables in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="49673-103">次の例では、XPath クエリに XPath 変数を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="49673-103">The following examples show how XPath variables are passed in XPath queries.</span></span> <span data-ttu-id="49673-104">これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。</span><span class="sxs-lookup"><span data-stu-id="49673-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="49673-105">このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49673-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="49673-106">例</span><span class="sxs-lookup"><span data-stu-id="49673-106">Examples</span></span>  
  
### <a name="a-use-the-xpath-variables"></a><span data-ttu-id="49673-107">A.</span><span class="sxs-lookup"><span data-stu-id="49673-107">A.</span></span> <span data-ttu-id="49673-108">XPath 変数を使用する</span><span class="sxs-lookup"><span data-stu-id="49673-108">Use the XPath variables</span></span>  
 <span data-ttu-id="49673-109">サンプル テンプレートは、2 つの XPath クエリで構成されており、</span><span class="sxs-lookup"><span data-stu-id="49673-109">A sample template consists of two XPath queries.</span></span> <span data-ttu-id="49673-110">各 XPath クエリは 1 つのパラメーターをとります。</span><span class="sxs-lookup"><span data-stu-id="49673-110">Each of the XPath queries takes one parameter.</span></span> <span data-ttu-id="49673-111">テンプレートでは、これらのパラメーターの既定値も指定しています。</span><span class="sxs-lookup"><span data-stu-id="49673-111">The template also specifies default values for these parameters.</span></span> <span data-ttu-id="49673-112">パラメーター値が指定されない場合は、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="49673-112">The default values are used if parameter values are not specified.</span></span> <span data-ttu-id="49673-113">では、既定値を持つ2つのパラメーターが指定されてい **\<sql:header>** ます。</span><span class="sxs-lookup"><span data-stu-id="49673-113">Two parameters with default values are specified in **\<sql:header>**.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='CustomerID'>1</sql:param>  
     <sql:param name='ContactID'>1</sql:param>   
  </sql:header>  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
    Customer[@CustomerID=$CustomerID]   
  </sql:xpath-query >  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
   Contact[@ContactID=$ContactID]   
  </sql:xpath-query>  
</ROOT>  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="49673-114">マッピング スキーマに対して XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="49673-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="49673-115">[サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="49673-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="49673-116">SampleSchema1.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="49673-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="49673-117">次のテンプレート (XPathVariables.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="49673-117">Create the following template (XPathVariables.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:header>  
         <sql:param name='CustomerID'>1</sql:param>  
         <sql:param name='ContactID'>1</sql:param>   
      </sql:header>  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[@CustomerID=$CustomerID]   
      </sql:xpath-query >  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
       Contact[@ContactID=$ContactID]   
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="49673-118">マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="49673-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="49673-119">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="49673-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="49673-120">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="49673-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="49673-121">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49673-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49673-122">この例では、パラメーターは渡されていません。</span><span class="sxs-lookup"><span data-stu-id="49673-122">In this example, no parameters are passed.</span></span> <span data-ttu-id="49673-123">このため、パラメーターの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="49673-123">Therefore, the default parameter values are used.</span></span>  
  
  
