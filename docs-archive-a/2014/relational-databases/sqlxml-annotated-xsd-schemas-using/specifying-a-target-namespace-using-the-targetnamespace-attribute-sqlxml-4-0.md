---
title: TargetNamespace 属性を使用してターゲットの名前空間を指定する (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
author: rothja
ms.author: jroth
ms.openlocfilehash: 823bcbf7f4906a2e1d2ced1ff58b681c0ca41a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644387"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a><span data-ttu-id="1ded1-102">targetNamespace 属性を使用した、対象名前空間の指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1ded1-102">Specifying a Target Namespace Using the targetNamespace Attribute (SQLXML 4.0)</span></span>
  <span data-ttu-id="1ded1-103">XSD スキーマの記述では、XSD **targetNamespace**属性を使用して、ターゲットの名前空間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-103">In writing XSD schemas, you can use the XSD **targetNamespace** attribute to specify a target namespace.</span></span> <span data-ttu-id="1ded1-104">このトピックでは、XSD **targetNamespace**、 **ElementFormDefault**、および**attributeFormDefault**属性の動作、生成される XML インスタンスへの影響、および名前空間での XPath クエリの指定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-104">This topic describes how the XSD **targetNamespace**, **elementFormDefault**, and **attributeFormDefault** attributes work, how they affect the XML instance that is generated, and how XPath queries are specified with namespaces.</span></span>  
  
 <span data-ttu-id="1ded1-105">**Xsd: targetNamespace**属性を使用して、既定の名前空間の要素と属性を別の名前空間に配置できます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-105">You can use the **xsd:targetNamespace** attribute to place elements and attributes from the default namespace into a different namespace.</span></span> <span data-ttu-id="1ded1-106">また、スキーマでローカルに宣言された要素と属性を、名前空間で修飾して表示するかどうかも指定できます。名前空間は、プレフィックスを使って明示的に、または既定により暗黙的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-106">You can also specify whether the locally declared elements and attributes of the schema should appear qualified by a namespace, either explicitly by using a prefix or implicitly by default.</span></span> <span data-ttu-id="1ded1-107">要素の**elementFormDefault**属性と**attributeFormDefault**属性を使用して、 **\<xsd:schema>** ローカル要素と属性の修飾をグローバルに指定することも、 **form**属性を使用して個々の要素と属性を個別に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-107">You can use the **elementFormDefault** and **attributeFormDefault** attributes on the **\<xsd:schema>** element to globally specify the qualification of local elements and attributes, or you can use the **form** attribute to specify individual elements and attributes separately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1ded1-108">例</span><span class="sxs-lookup"><span data-stu-id="1ded1-108">Examples</span></span>  
 <span data-ttu-id="1ded1-109">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ded1-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="1ded1-110">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ded1-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-a-target-namespace"></a><span data-ttu-id="1ded1-111">A.</span><span class="sxs-lookup"><span data-stu-id="1ded1-111">A.</span></span> <span data-ttu-id="1ded1-112">対象名前空間を指定する</span><span class="sxs-lookup"><span data-stu-id="1ded1-112">Specifying a target namespace</span></span>  
 <span data-ttu-id="1ded1-113">次の XSD スキーマでは、 **xsd: targetNamespace**属性を使用してターゲットの名前空間を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1ded1-113">The following XSD schema specifies a target namespace by using the **xsd:targetNamespace** attribute.</span></span> <span data-ttu-id="1ded1-114">また、このスキーマでは、 **elementFormDefault**属性と**attributeFormDefault**属性の値が **"非修飾"** (これらの属性の既定値) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-114">The schema also sets the **elementFormDefault** and **attributeFormDefault** attribute values to **"unqualified"** (the default value for these attributes).</span></span> <span data-ttu-id="1ded1-115">これはグローバルな宣言であり、すべてのローカル要素 ( **\<Order>** スキーマ内) と属性 (スキーマ内**ContactName**の**CustomerID、CustomerID**、および**OrderID** ) に影響します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-115">This is a global declaration and affects all the local elements (**\<Order>** in the schema) and attributes (**CustomerID**, **ContactName**, and **OrderID** in the schema).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="1ded1-116">このスキーマの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1ded1-116">In the schema:</span></span>  
  
-   <span data-ttu-id="1ded1-117">**顧客型**と**ordertype**型の宣言はグローバルであるため、スキーマのターゲット名前空間に含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ded1-117">The **CustomerType** and **OrderType** type declarations are global and, therefore, are included in the schema's target namespace.</span></span> <span data-ttu-id="1ded1-118">その結果、これらの型が要素とその子要素の宣言で参照されている場合、 **\<Customer>** **\<Order>** ターゲットの名前空間に関連付けられているプレフィックスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-118">As a result, when these types are referenced in the declaration of **\<Customer>** element and its **\<Order>** child element, a prefix is specified that is associated with the target namespace.</span></span>  
  
-   <span data-ttu-id="1ded1-119">スキーマの **\<Customer>** グローバル要素であるため、スキーマのターゲット名前空間にも要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-119">The **\<Customer>** element is also included in the target namespace of the schema because it is a global element in the schema.</span></span>  
  
 <span data-ttu-id="1ded1-120">このスキーマに対して次の XPath クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-120">Execute the following XPath query against the schema:</span></span>  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 <span data-ttu-id="1ded1-121">この XPath クエリでは、次のインスタンス ドキュメントが生成されます。ここでは注文の一部のみを表示します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-121">The XPath query generates this instance document (only a few of the orders are shown):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 <span data-ttu-id="1ded1-122">このインスタンスドキュメントでは、urn: MyNamespace 名前空間を定義し、プレフィックス (y0) をそれに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-122">This instance document defines the urn:MyNamespace namespace and associates a prefix (y0) to it.</span></span> <span data-ttu-id="1ded1-123">プレフィックスは、グローバル要素にのみ適用され **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-123">The prefix is applied only to the **\<Customer>** global element.</span></span> <span data-ttu-id="1ded1-124">(要素は、スキーマ内の要素の子として宣言されているため、グローバルです **\<xsd:schema>** )。</span><span class="sxs-lookup"><span data-stu-id="1ded1-124">(The element is global because it is declared as a child of **\<xsd:schema>** element in the schema.)</span></span>  
  
 <span data-ttu-id="1ded1-125">スキーマで**elementFormDefault**属性と**attributeFormDefault**属性の値が **"非修飾"** に設定されているため、プレフィックスはローカルの要素および属性には適用されません。</span><span class="sxs-lookup"><span data-stu-id="1ded1-125">The prefix is not applied to the local elements and attributes because the value of **elementFormDefault** and **attributeFormDefault** attributes is set to **"unqualified"** in the schema.</span></span> <span data-ttu-id="1ded1-126">要素は、要素を **\<Order>** 定義する要素の子として宣言されているため、ローカルであることに注意して **\<complexType>** **\<CustomerType>** ください。</span><span class="sxs-lookup"><span data-stu-id="1ded1-126">Note that the **\<Order>** element is local because its declaration appears as a child of the **\<complexType>** element that defines the **\<CustomerType>** element.</span></span> <span data-ttu-id="1ded1-127">同様に、属性 (**CustomerID**、 **OrderID** **、および**CustomerID) はグローバルではなくローカルになります。</span><span class="sxs-lookup"><span data-stu-id="1ded1-127">Similarly, the attributes (**CustomerID**, **OrderID**, and **ContactName**) are local, not global.</span></span>  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="1ded1-128">このスキーマの実際のサンプルを作成するには</span><span class="sxs-lookup"><span data-stu-id="1ded1-128">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="1ded1-129">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="1ded1-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="1ded1-130">targetNameSpace.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-130">Save the file as targetNameSpace.xml.</span></span>  
  
2.  <span data-ttu-id="1ded1-131">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="1ded1-131">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="1ded1-132">targetNamespace.xml を保存したディレクトリに targetNameSpaceT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-132">Save the file as targetNameSpaceT.xml in the same directory where you saved targetNamespace.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="1ded1-133">このテンプレートの XPath クエリでは、 **\<Customer>** CustomerID が1の顧客の要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-133">The XPath query in the template returns the **\<Customer>** element for the customer with a CustomerID of 1.</span></span> <span data-ttu-id="1ded1-134">この XPath クエリでは、属性ではなく、クエリ内の要素の名前空間プレフィックスが指定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ded1-134">Note that the XPath query specifies the namespace prefix for the element in the query and not for the attribute.</span></span> <span data-ttu-id="1ded1-135">ローカル属性は、スキーマ内の指定と同様、修飾されません。</span><span class="sxs-lookup"><span data-stu-id="1ded1-135">(Local attributes are not qualified, as specified in the schema.)</span></span>  
  
     <span data-ttu-id="1ded1-136">マッピング スキーマ (targetNamespace.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="1ded1-136">The directory path specified for the mapping schema (targetNamespace.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="1ded1-137">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-137">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  <span data-ttu-id="1ded1-138">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-138">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="1ded1-139">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ded1-139">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="1ded1-140">スキーマで**elementFormDefault**属性と**attributeFormDefault**属性が値 **"qualified"** で指定されている場合、インスタンスドキュメントには、すべてのローカル要素と属性が修飾されます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-140">If the schema specifies **elementFormDefault** and **attributeFormDefault** attributes with value **"qualified"**, the instance document will have all of the local elements and attributes qualified.</span></span> <span data-ttu-id="1ded1-141">前のスキーマを変更してこれらの属性を要素に追加 **\<xsd:schema>** し、テンプレートを再度実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1ded1-141">You can change the previous schema to include these attributes in the **\<xsd:schema>** element and execute the template again.</span></span> <span data-ttu-id="1ded1-142">この場合は、インスタンスで属性も修飾されるので、名前空間プレフィックスを含むよう XPath クエリを変更します。</span><span class="sxs-lookup"><span data-stu-id="1ded1-142">Because the attributes are now also qualified in the instance, the XPath query will change to include the namespace prefix.</span></span>  
  
 <span data-ttu-id="1ded1-143">次は変更した XPath クエリです。</span><span class="sxs-lookup"><span data-stu-id="1ded1-143">This is the revised XPath query:</span></span>  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 <span data-ttu-id="1ded1-144">次は返される XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="1ded1-144">This is the XML document that is returned:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
