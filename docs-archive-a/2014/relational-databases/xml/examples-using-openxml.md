---
title: '例 : OPENXML の使用 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ColPattern [XML in SQL Server]
- XML [SQL Server], mapping data
- OPENXML statement, about OPENXML statement
- overflow in XML document [SQL Server]
- mapping XML data [SQL Server]
- combining attribute-centric and element centric mapping
- unconsumed data
- attribute-centric mapping
- column patterns [XML in SQL Server]
- XML [SQL Server], overflow handling
- row patterns [XML in SQL Server]
- rowpattern [XML in SQL Server]
- flags parameter
- element-centric mapping [SQL Server]
- edge tables
ms.assetid: 689297f3-adb0-4d8d-bf62-cfda26210164
author: rothja
ms.author: jroth
ms.openlocfilehash: 09fc6ad073b12df2f9fbd8ebc6a59149f6154ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743113"
---
# <a name="examples-using-openxml"></a><span data-ttu-id="90b0c-102">例 :OPENXML の使用</span><span class="sxs-lookup"><span data-stu-id="90b0c-102">Examples: Using OPENXML</span></span>
  <span data-ttu-id="90b0c-103">このトピックの例では、OPENXML を使用して XML ドキュメントの行セット ビューを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-103">The examples in this topic show how OPENXML is used to create a rowset view of an XML document.</span></span> <span data-ttu-id="90b0c-104">OPENXML の構文の詳細については、「 [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90b0c-104">For information about the syntax of OPENXML, see [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql).</span></span> <span data-ttu-id="90b0c-105">ここに示す例では、OPENXML でのメタプロパティの指定を除く OPENXML のすべての側面を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-105">The examples show all aspects of OPENXML, but do not specify metaproperties in OPENXML.</span></span> <span data-ttu-id="90b0c-106">OPENXML のメタプロパティの指定方法の詳細については、「 [OPENXML 内でのメタプロパティの指定](specify-metaproperties-in-openxml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90b0c-106">For more information about how to specify metaproperties in OPENXML, see [Specify Metaproperties in OPENXML](specify-metaproperties-in-openxml.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="90b0c-107">例</span><span class="sxs-lookup"><span data-stu-id="90b0c-107">Examples</span></span>  
 <span data-ttu-id="90b0c-108">データを取得する際に、 *rowpattern* を使用して、XML ドキュメント内の行を決定するノードを識別します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-108">In retrieving the data, *rowpattern* is used to identify the nodes in the XML document that determine the rows.</span></span> <span data-ttu-id="90b0c-109">また、 *rowpattern* は、MSXML XPath の実装で使用される XPath パターン言語で表現されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-109">Additionally, *rowpattern* is expressed in the XPath pattern language that is used in the MSXML XPath implementation.</span></span> <span data-ttu-id="90b0c-110">たとえば、パターンが要素や属性になる場合、 *rowpattern*で選択される要素や属性のノードごとに行が作成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-110">For example, if the pattern ends in an element or an attribute, a row is created for each element or attribute node that is selected by *rowpattern*.</span></span>  
  
 <span data-ttu-id="90b0c-111">*flags* 値は、既定のマッピングを指定します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-111">The *flags* value provides default mapping.</span></span> <span data-ttu-id="90b0c-112">*SchemaDeclaration* で *ColPattern*が指定されていない場合、 *flags* で指定されたマッピングが想定されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-112">If no *ColPattern* is specified in the *SchemaDeclaration*, the mapping specified in *flags* is assumed.</span></span> <span data-ttu-id="90b0c-113">*SchemaDeclaration* で *ColPattern* が指定されている場合、 *flags*の値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-113">The *flags* value is ignored if *ColPattern* is specified in *SchemaDeclaration*.</span></span> <span data-ttu-id="90b0c-114">指定された *ColPattern* により、マッピング、属性中心か要素中心か、さらにオーバーフロー データと未使用データを処理するときの動作が決まります。</span><span class="sxs-lookup"><span data-stu-id="90b0c-114">The specified *ColPattern* determines the mapping, attribute-centric or element-centric, and also the behavior in dealing with overflow and unconsumed data.</span></span>  
  
### <a name="a-executing-a-simple-select-statement-with-openxml"></a><span data-ttu-id="90b0c-115">A.</span><span class="sxs-lookup"><span data-stu-id="90b0c-115">A.</span></span> <span data-ttu-id="90b0c-116">OPENXML を使用した単純な SELECT ステートメントの実行</span><span class="sxs-lookup"><span data-stu-id="90b0c-116">Executing a simple SELECT statement with OPENXML</span></span>  
 <span data-ttu-id="90b0c-117">この例の XML ドキュメントは、<`Customer`> 要素、<`Order`> 要素、および <`OrderDetail`> 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-117">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="90b0c-118">OPENXML ステートメントでは、XML ドキュメントから顧客情報が 2 列の行セット ( **CustomerID** と **ContactName**) で取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-118">The OPENXML statement retrieves customer information in a two-column rowset, **CustomerID** and **ContactName**, from the XML document.</span></span>  
  
 <span data-ttu-id="90b0c-119">最初に、 **sp_xml_preparedocument** ストアド プロシージャを呼び出してドキュメント ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-119">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="90b0c-120">このドキュメント ハンドルを OPENXML に渡します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-120">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="90b0c-121">この OPENXML ステートメントは、次のことを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-121">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-122">*rowpattern* (/ROOT/Customer) により、処理する <`Customer`> ノードが識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-122">*rowpattern* (/ROOT/Customer) identifies the <`Customer`> nodes to process.</span></span>  
  
-   <span data-ttu-id="90b0c-123">*flags* パラメーター値を **1** に設定し、属性中心のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-123">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="90b0c-124">その結果、XML 属性は *SchemaDeclaration*で定義される行セットの列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-124">As a result, the XML attributes map to the columns in the rowset defined in *SchemaDeclaration*.</span></span>  
  
-   <span data-ttu-id="90b0c-125">WITH 句の *SchemaDeclaration*では、指定された *ColName* 値は対応する XML 属性の名前と一致します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-125">In *SchemaDeclaration*, in the WITH clause, the specified *ColName* values match the corresponding XML attribute names.</span></span> <span data-ttu-id="90b0c-126">したがって、 *SchemaDeclaration* では *ColPattern*パラメーターが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-126">Therefore, the *ColPattern* parameter is not specified in *SchemaDeclaration*.</span></span>  
  
 <span data-ttu-id="90b0c-127">次に、SELECT ステートメントにより、OPENXML で提供される行セット内のすべての列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-127">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @DocHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
          OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
          OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @DocHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@DocHandle, '/ROOT/Customer',1)  
      WITH (CustomerID  varchar(10),  
            ContactName varchar(20))  
EXEC sp_xml_removedocument @DocHandle  
```  
  
 <span data-ttu-id="90b0c-128">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-128">This is the result:</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="90b0c-129">*flags* を要素中心のマッピングを示す **2** に設定して同じ SELECT ステートメントを実行すると、<`Customer`> 要素にはサブ要素がないので、両方の顧客の **CustomerID** と **ContactName** の値が NULL として返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-129">Because the <`Customer`> elements do not have any subelements, if the same SELECT statement is executed with *flags* set to **2** to indicate element-centric mapping, the values of **CustomerID** and **ContactName** for both the customers are returned as NULL.</span></span>  
  
 <span data-ttu-id="90b0c-130">また、@xmlDocument を **xml** 型や **(n)varchar(max)** 型にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-130">The @xmlDocument can also be of **xml** type or of **(n)varchar(max)** type.</span></span>  
  
 <span data-ttu-id="90b0c-131">XML ドキュメント内で <`CustomerID`> と <`ContactName`> がサブ要素の場合は、要素中心のマッピングにより値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-131">If <`CustomerID`> and <`ContactName`> in the XML document are subelements, the element-centric mapping retrieves the values.</span></span>  
  
```  
DECLARE @XmlDocumentHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer>  
   <CustomerID>VINET</CustomerID>  
   <ContactName>Paul Henriot</ContactName>  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer>     
   <CustomerID>LILAS</CustomerID>  
   <ContactName>Carlos Gonzlez</ContactName>  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @XmlDocumentHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT    *  
FROM      OPENXML (@XmlDocumentHandle, '/ROOT/Customer',2)  
           WITH (CustomerID  varchar(10),  
                 ContactName varchar(20))  
EXEC sp_xml_removedocument @XmlDocumentHandle  
```  
  
 <span data-ttu-id="90b0c-132">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-132">This is the result:</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="90b0c-133">**sp_xml_preparedocument** から返されたドキュメント ハンドルは、セッション内ではなく、バッチが実行されている間は有効であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="90b0c-133">Note that the document handle returned by **sp_xml_preparedocument** is valid for the duration of the batch and not the session.</span></span>  
  
### <a name="b-specifying-colpattern-for-mapping-between-rowset-columns-and-the-xml-attributes-and-elements"></a><span data-ttu-id="90b0c-134">B.</span><span class="sxs-lookup"><span data-stu-id="90b0c-134">B.</span></span> <span data-ttu-id="90b0c-135">行セットの列と XML の属性や要素の間でマッピングを行うための ColPattern の指定</span><span class="sxs-lookup"><span data-stu-id="90b0c-135">Specifying ColPattern for mapping between rowset columns and the XML attributes and elements</span></span>  
 <span data-ttu-id="90b0c-136">この例では、省略可能な *ColPattern* パラメーターに XPath パターンを指定して、行セットの列と XML の属性や要素の間でマッピングを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-136">This example shows how the XPath pattern is specified in the optional *ColPattern* parameter to provide mapping between rowset columns and the XML attributes and elements.</span></span>  
  
 <span data-ttu-id="90b0c-137">この例の XML ドキュメントは、<`Customer`> 要素、<`Order`> 要素、および <`OrderDetail`> 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-137">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="90b0c-138">OPENXML ステートメントにより、XML ドキュメントから顧客情報と注文情報が 1 つの行セット (**CustomerID**、 **OrderDate**、 **ProdID**、および **Qty**) として取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-138">The OPENXML statement retrieves customer and order information as a rowset (**CustomerID**, **OrderDate**, **ProdID**, and **Qty**) from the XML document.</span></span>  
  
 <span data-ttu-id="90b0c-139">最初に、 **sp_xml_preparedocument** ストアド プロシージャを呼び出してドキュメント ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-139">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="90b0c-140">このドキュメント ハンドルを OPENXML に渡します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-140">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="90b0c-141">この OPENXML ステートメントは、次のことを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-141">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-142">*rowpattern* (/ROOT/Customer/Order/OrderDetail) により、処理する <`OrderDetail`> ノードが識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-142">*rowpattern* (/ROOT/Customer/Order/OrderDetail) identifies the <`OrderDetail`> nodes to process.</span></span>  
  
 <span data-ttu-id="90b0c-143">ここでは説明のために、 *flags* パラメーター値を **2** に設定して、要素中心のマッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-143">For illustration, the *flags* parameter value is set to **2** and indicates element-centric mapping.</span></span> <span data-ttu-id="90b0c-144">ただし、このマッピングは *ColPattern* に指定したマッピングによって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-144">However, the mapping specified in *ColPattern* overwrites this mapping.</span></span> <span data-ttu-id="90b0c-145">つまり、 *ColPattern* に指定した XPath パターンにより、行セットの列が属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-145">That is, the XPath pattern specified in *ColPattern* maps the columns in the rowset to attributes.</span></span> <span data-ttu-id="90b0c-146">この結果、属性中心のマッピングになります。</span><span class="sxs-lookup"><span data-stu-id="90b0c-146">This results in attribute-centric mapping.</span></span>  
  
 <span data-ttu-id="90b0c-147">WITH 句の *SchemaDeclaration*では、 *ColName* パラメーターと *ColType* パラメーターを使用して *ColPattern* も指定されています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-147">In *SchemaDeclaration*, in the WITH clause, *ColPattern* is also specified with the *ColName* and *ColType* parameters.</span></span> <span data-ttu-id="90b0c-148">省略可能な *ColPattern* は指定された XPath パターンで、次のことを示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-148">The optional *ColPattern* is the XPath pattern specified and indicates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-149">行セットの **OrderID** 列、**CustomerID** 列、および **OrderDate** 列は *rowpattern* によって識別されたノードの親の属性にマップされ、*rowpattern* によって <`OrderDetail`> ノードが識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-149">The **OrderID**, **CustomerID**, and **OrderDate** columns in the rowset map to the attributes of the parent of the nodes identified by *rowpattern*, and *rowpattern* identifies the <`OrderDetail`> nodes.</span></span> <span data-ttu-id="90b0c-150">したがって、**CustomerID** 列と **OrderDate** 列は <`Order`> 要素の **CustomerID** 属性と **OrderDate** 属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-150">Therefore, the **CustomerID** and **OrderDate** columns map to **CustomerID** and **OrderDate** attributes of the <`Order`> element.</span></span>  
  
-   <span data-ttu-id="90b0c-151">行セットの **ProdID** 列と **Qty** 列は、 **rowpattern** で識別されたノードの **ProductID** 属性と *Quantity*属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-151">The **ProdID** and **Qty** columns in the rowset map to the **ProductID** and **Quantity** attributes of the nodes identified in *rowpattern*.</span></span>  
  
 <span data-ttu-id="90b0c-152">次に、SELECT ステートメントにより、OPENXML で提供される行セット内のすべての列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-152">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @XmlDocumentHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @XmlDocumentHandle OUTPUT, @XmlDocument  
-- Execute a SELECT stmt using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@XmlDocumentHandle, '/ROOT/Customer/Order/OrderDetail',2)  
WITH (OrderID     int         '../@OrderID',  
      CustomerID  varchar(10) '../@CustomerID',  
      OrderDate   datetime    '../@OrderDate',  
      ProdID      int         '@ProductID',  
      Qty         int         '@Quantity')  
EXEC sp_xml_removedocument @XmlDocumentHandle  
```  
  
 <span data-ttu-id="90b0c-153">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-153">This is the result:</span></span>  
  
```  
OrderID CustomerID        OrderDate          ProdID    Qty  
-------------------------------------------------------------  
10248    VINET     1996-07-04 00:00:00.000     11       12  
10248    VINET     1996-07-04 00:00:00.000     42       10  
10283    LILAS     1996-08-16 00:00:00.000     72        3  
```  
  
 <span data-ttu-id="90b0c-154">*ColPattern* として指定した XPath パターンを、行セットの列に XML 要素をマップするために指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-154">The XPath pattern specified as *ColPattern* can also be specified to map the XML elements to the rowset columns.</span></span> <span data-ttu-id="90b0c-155">この結果、要素中心のマッピングになります。</span><span class="sxs-lookup"><span data-stu-id="90b0c-155">This results in element-centric mapping.</span></span> <span data-ttu-id="90b0c-156">次の例では、XML ドキュメントの <`CustomerID`> と <`OrderDate`> は、<`Orders`> 要素のサブ要素です。</span><span class="sxs-lookup"><span data-stu-id="90b0c-156">In the following example, the XML document <`CustomerID`> and <`OrderDate`> are subelements of the <`Orders`> element.</span></span> <span data-ttu-id="90b0c-157">*ColPattern* により *flags* パラメーターに指定されたマッピングが上書きされるので、OPENXML では *flags* パラメーターを指定しません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-157">Because *ColPattern* overwrites the mapping specified in the *flags* parameter, the *flags* parameter is not specified in OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order EmployeeID="5" >  
      <OrderID>10248</OrderID>  
      <CustomerID>VINET</CustomerID>  
      <OrderDate>1996-07-04T00:00:00</OrderDate>  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order  EmployeeID="3" >  
      <OrderID>10283</OrderID>  
      <CustomerID>LILAS</CustomerID>  
      <OrderDate>1996-08-16T00:00:00</OrderDate>  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer/Order/OrderDetail')  
WITH (CustomerID  varchar(10)   '../CustomerID',  
      OrderDate   datetime      '../OrderDate',  
      ProdID      int           '@ProductID',  
      Qty         int           '@Quantity')  
EXEC sp_xml_removedocument @docHandle  
```  
  
### <a name="c-combining-attribute-centric-and-element-centric-mapping"></a><span data-ttu-id="90b0c-158">C.</span><span class="sxs-lookup"><span data-stu-id="90b0c-158">C.</span></span> <span data-ttu-id="90b0c-159">属性中心のマッピングと要素中心のマッピングの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="90b0c-159">Combining attribute-centric and element-centric mapping</span></span>  
 <span data-ttu-id="90b0c-160">この例では、 *flags* パラメーターを **3** に設定し、属性中心のマッピングと要素中心のマッピングの両方が適用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-160">In this example, the *flags* parameter is set to **3** and indicates that both attribute-centric and element-centric mapping will be applied.</span></span> <span data-ttu-id="90b0c-161">この場合、まだ処理されていないすべての列に対して、まず属性中心のマッピングが適用されてから、次に要素中心のマッピングが適用されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-161">In this case, the attribute-centric mapping is applied first, and then element-centric mapping is applied for all the columns not yet dealt with.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument =N'<ROOT>  
<Customer CustomerID="VINET"  >  
     <ContactName>Paul Henriot</ContactName>  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
          OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" >   
     <ContactName>Carlos Gonzlez</ContactName>  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
          OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @XmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer',3)  
      WITH (CustomerID  varchar(10),  
            ContactName varchar(20))  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="90b0c-162">結果</span><span class="sxs-lookup"><span data-stu-id="90b0c-162">This is the result</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="90b0c-163">**CustomerID**に属性中心のマッピングが適用されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-163">The attribute-centric mapping is applied for **CustomerID**.</span></span> <span data-ttu-id="90b0c-164"><`Customer`> 要素には **ConzｘtactName** 属性がありません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-164">There is no **ContactName** attribute in the <`Customer`> element.</span></span> <span data-ttu-id="90b0c-165">そのため、要素中心のマッピングが適用されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-165">Therefore, element-centric mapping is applied.</span></span>  
  
### <a name="d-specifying-the-text-xpath-function-as-colpattern"></a><span data-ttu-id="90b0c-166">D.</span><span class="sxs-lookup"><span data-stu-id="90b0c-166">D.</span></span> <span data-ttu-id="90b0c-167">ColPattern としての text() XPath 関数の指定</span><span class="sxs-lookup"><span data-stu-id="90b0c-167">Specifying the text() XPath function as ColPattern</span></span>  
 <span data-ttu-id="90b0c-168">この例の XML ドキュメントは、<`Customer`> 要素および <`Order`> 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-168">The XML document in this example is made up of the <`Customer`> and <`Order`> elements.</span></span> <span data-ttu-id="90b0c-169">OPENXML ステートメントにより、<`Order`> 要素の **oid** 属性、*rowpattern* で識別されるノードの親の ID、および要素のコンテンツのリーフ値の文字列で構成される行セットが取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-169">The OPENXML statement retrieves a rowset that is made up of the **oid** attribute from the <`Order`> element, the ID of the parent of the node identified by *rowpattern*, and the leaf-value string of the element content.</span></span>  
  
 <span data-ttu-id="90b0c-170">最初に、 **sp_xml_preparedocument** ストアド プロシージャを呼び出してドキュメント ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-170">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="90b0c-171">このドキュメント ハンドルを OPENXML に渡します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-171">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="90b0c-172">この OPENXML ステートメントは、次のことを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-172">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-173">*rowpattern* (/root/Customer/Order) により、処理する <`Order`> ノードが識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-173">*rowpattern* (/root/Customer/Order) identifies the <`Order`> nodes to process.</span></span>  
  
-   <span data-ttu-id="90b0c-174">*flags* パラメーター値を **1** に設定し、属性中心のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-174">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="90b0c-175">その結果、XML 属性は *SchemaDeclaration*で定義される行セットの列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-175">As a result, the XML attributes map to the rowset columns defined in *SchemaDeclaration*.</span></span>  
  
-   <span data-ttu-id="90b0c-176">WITH 句の *SchemaDeclaration* では、行セットの列名である **oid** と **amount** が対応する XML 属性の名前と一致します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-176">In *SchemaDeclaration* in the WITH clause, the **oid** and **amount** rowset column names match the corresponding XML attribute names.</span></span> <span data-ttu-id="90b0c-177">したがって、 *ColPattern* パラメーターは指定されません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-177">Therefore, the *ColPattern* parameter is not specified.</span></span> <span data-ttu-id="90b0c-178">行セット内の **comment** 列では、XPath 関数 **text()** が *ColPattern*に指定されています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-178">For the **comment** column in the rowset, the XPath function, **text()**, is specified as *ColPattern*.</span></span> <span data-ttu-id="90b0c-179">これにより、 *flags*に指定された属性中心のマッピングが上書きされ、列には要素コンテンツのリーフ値の文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-179">This overwrites the attribute-centric mapping specified in *flags*, and the column contains the leaf-value string of the element content.</span></span>  
  
 <span data-ttu-id="90b0c-180">次に、SELECT ステートメントにより、OPENXML で提供される行セット内のすべての列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-180">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
--sample XML document  
SET @xmlDocument =N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied  
      </Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
            <Urgency>Important</Urgency>  
            Happy Customer.  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/root/Customer/Order', 1)  
     WITH (oid     char(5),   
           amount  float,   
           comment ntext 'text()')  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="90b0c-181">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-181">This is the result:</span></span>  
  
```  
oid   amount        comment  
----- -----------   -----------------------------  
O1    3.5           NULL  
O2    13.4          Customer was very satisfied  
O3    100.0         Happy Customer.  
O4    10000.0       NULL  
```  
  
### <a name="e-specifying-tablename-in-the-with-clause"></a><span data-ttu-id="90b0c-182">E.</span><span class="sxs-lookup"><span data-stu-id="90b0c-182">E.</span></span> <span data-ttu-id="90b0c-183">WITH 句での TableName の指定</span><span class="sxs-lookup"><span data-stu-id="90b0c-183">Specifying TableName in the WITH clause</span></span>  
 <span data-ttu-id="90b0c-184">この例では、WITH 句に *SchemaDeclaration* ではなく *TableName*を指定します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-184">This example specifies *TableName* in the WITH clause instead of *SchemaDeclaration*.</span></span> <span data-ttu-id="90b0c-185">この指定は、目的の構造のテーブルがあり、列パターンの *ColPattern* パラメーターが必要ない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-185">This is useful if you have a table that has the structure you want and no column patterns, *ColPattern* parameter, are required.</span></span>  
  
 <span data-ttu-id="90b0c-186">この例の XML ドキュメントは、<`Customer`> 要素および <`Order`> 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-186">The XML document in this example is made up of the <`Customer`> and <`Order`> elements.</span></span> <span data-ttu-id="90b0c-187">OPENXML ステートメントでは、XML ドキュメントから注文情報が 3 列の行セット (**oid**、 **date**、および **amount**) に取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-187">The OPENXML statement retrieves order information in a three-column rowset (**oid**, **date**, and **amount**) from the XML document.</span></span>  
  
 <span data-ttu-id="90b0c-188">最初に、 **sp_xml_preparedocument** ストアド プロシージャを呼び出してドキュメント ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-188">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="90b0c-189">このドキュメント ハンドルを OPENXML に渡します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-189">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="90b0c-190">この OPENXML ステートメントは、次のことを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-190">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-191">*rowpattern* (/root/Customer/Order) により、処理する <`Order`> ノードが識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-191">*rowpattern* (/root/Customer/Order) identifies the <`Order`> nodes to process.</span></span>  
  
-   <span data-ttu-id="90b0c-192">WITH 句には *SchemaDeclaration* がありません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-192">There is no *SchemaDeclaration* in the WITH clause.</span></span> <span data-ttu-id="90b0c-193">代わりに、テーブル名が指定されています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-193">Instead, a table name is specified.</span></span> <span data-ttu-id="90b0c-194">そのため、行セット スキーマとしてテーブル スキーマが使用されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-194">Therefore, the table schema is used as the rowset schema.</span></span>  
  
-   <span data-ttu-id="90b0c-195">*flags* パラメーター値を **1** に設定し、属性中心のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-195">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="90b0c-196">したがって、 *rowpattern*で識別される要素の属性は、同じ名前の行セット列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-196">Therefore, attributes of the elements, identified by *rowpattern*, map to the rowset columns with the same name.</span></span>  
  
 <span data-ttu-id="90b0c-197">次に、SELECT ステートメントにより、OPENXML で提供される行セット内のすべての列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-197">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
-- Create a test table. This table schema is used by OPENXML as the  
-- rowset schema.  
CREATE TABLE T1(oid char(5), date datetime, amount float)  
GO  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
-- Sample XML document  
SET @xmlDocument =N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very   
             satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/root/Customer/Order', 1)  
     WITH T1  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="90b0c-198">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-198">This is the result:</span></span>  
  
```  
oid   date                        amount  
----- --------------------------- ----------  
O1    1996-01-20 00:00:00.000     3.5  
O2    1997-04-30 00:00:00.000     13.4  
O3    1999-07-14 00:00:00.000     100.0  
O4    1996-01-20 00:00:00.000     10000.0  
```  
  
### <a name="f-obtaining-the-result-in-an-edge-table-format"></a><span data-ttu-id="90b0c-199">F.</span><span class="sxs-lookup"><span data-stu-id="90b0c-199">F.</span></span> <span data-ttu-id="90b0c-200">エッジ テーブル形式での結果の取得</span><span class="sxs-lookup"><span data-stu-id="90b0c-200">Obtaining the result in an edge table format</span></span>  
 <span data-ttu-id="90b0c-201">この例では、OPENXML ステートメントに WITH 句が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-201">In this example, the WITH clause is not specified in the OPENXML statement.</span></span> <span data-ttu-id="90b0c-202">その結果、OPENXML で生成される行セットがエッジ テーブル形式になります。</span><span class="sxs-lookup"><span data-stu-id="90b0c-202">As a result, the rowset generated by OPENXML has an edge table format.</span></span> <span data-ttu-id="90b0c-203">SELECT ステートメントにより、エッジ テーブル内のすべての列が返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-203">The SELECT statement returns all the columns in the edge table.</span></span>  
  
 <span data-ttu-id="90b0c-204">この例のサンプル XML ドキュメントは、<`Customer`> 要素、<`Order`> 要素、および <`OrderDetail`> 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-204">The sample XML document in the example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span>  
  
 <span data-ttu-id="90b0c-205">最初に、 **sp_xml_preparedocument** ストアド プロシージャを呼び出してドキュメント ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-205">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="90b0c-206">このドキュメント ハンドルを OPENXML に渡します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-206">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="90b0c-207">この OPENXML ステートメントは、次のことを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-207">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-208">*rowpattern* (/ROOT/Customer) により、処理する <`Customer`> ノードが識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-208">*rowpattern* (/ROOT/Customer) identifies the <`Customer`> nodes to process.</span></span>  
  
-   <span data-ttu-id="90b0c-209">WITH 句は指定されていません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-209">The WITH clause is not provided.</span></span> <span data-ttu-id="90b0c-210">したがって、OPENXML により、行セットがエッジ テーブル形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-210">Therefore, OPENXML returns the rowset in an edge table format.</span></span>  
  
 <span data-ttu-id="90b0c-211">次に、SELECT ステートメントにより、エッジ テーブル内のすべての列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-211">The SELECT statement then retrieves all the columns in the edge table.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
SET @xmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer')  
  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="90b0c-212">結果はエッジ テーブルとして返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-212">The result is returned as an edge table.</span></span> <span data-ttu-id="90b0c-213">エッジ テーブルに対するクエリを作成して、情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-213">You can write queries against the edge table to obtain information.</span></span> <span data-ttu-id="90b0c-214">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-214">For example:</span></span>  
  
-   <span data-ttu-id="90b0c-215">次のクエリにより、ドキュメント内の **Customer** ノードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-215">The following query returns the number of **Customer** nodes in the document.</span></span> <span data-ttu-id="90b0c-216">WITH 句が指定されていないので、OPENXML からエッジ テーブルが返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-216">Because the WITH clause is not specified, OPENXML returns an edge table.</span></span> <span data-ttu-id="90b0c-217">SELECT ステートメントにより、エッジ テーブルへのクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-217">The SELECT statement queries the edge table.</span></span>  
  
    ```  
    SELECT count(*)  
    FROM OPENXML(@docHandle, '/')  
    WHERE localname = 'Customer'  
    ```  
  
-   <span data-ttu-id="90b0c-218">次のクエリにより、要素型の XML ノードのローカル名が返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-218">The following query returns the local names of XML nodes of element type.</span></span>  
  
    ```  
    SELECT distinct localname   
    FROM OPENXML(@docHandle, '/')   
    WHERE nodetype = 1   
    ORDER BY localname  
    ```  
  
### <a name="g-specifying-rowpattern-ending-with-an-attribute"></a><span data-ttu-id="90b0c-219">G.</span><span class="sxs-lookup"><span data-stu-id="90b0c-219">G.</span></span> <span data-ttu-id="90b0c-220">属性で終了する rowpattern の指定</span><span class="sxs-lookup"><span data-stu-id="90b0c-220">Specifying rowpattern ending with an attribute</span></span>  
 <span data-ttu-id="90b0c-221">この例の XML ドキュメントは、<`Customer`> 要素、<`Order`> 要素、および <`OrderDetail`> 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-221">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="90b0c-222">OPENXML ステートメントにより、XML ドキュメントから注文明細の情報が 3 列の行セット (**ProductID**、 **Quantity**、および **OrderID**) で取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-222">The OPENXML statement retrieves information about the order details in a three-column rowset (**ProductID**, **Quantity**, and **OrderID**) from the XML document.</span></span>  
  
 <span data-ttu-id="90b0c-223">最初に、 **sp_xml_preparedocument** を呼び出してドキュメント ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-223">First, the **sp_xml_preparedocument** is called to obtain a document handle.</span></span> <span data-ttu-id="90b0c-224">このドキュメント ハンドルを OPENXML に渡します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-224">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="90b0c-225">この OPENXML ステートメントは、次のことを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-225">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="90b0c-226">*rowpattern* (/ROOT/Customer/Order/OrderDetail/\@ProductID) は、XML 属性 **ProductID** で終了します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-226">*rowpattern* (/ROOT/Customer/Order/OrderDetail/\@ProductID) ends with an XML attribute, **ProductID**.</span></span> <span data-ttu-id="90b0c-227">結果の行セットでは、XML ドキュメント内で選択した属性ノードごとに行が作成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-227">In the resulting rowset, a row is created for each attribute node selected in the XML document.</span></span>  
  
-   <span data-ttu-id="90b0c-228">この例では、 *flags* パラメーターは指定されていません。</span><span class="sxs-lookup"><span data-stu-id="90b0c-228">In this example, the *flags* parameter is not specified.</span></span> <span data-ttu-id="90b0c-229">代わりに、 *ColPattern* パラメーターによってマッピングを指定します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-229">Instead, the mappings are specified by the *ColPattern* parameter.</span></span>  
  
 <span data-ttu-id="90b0c-230">WITH 句の *SchemaDeclaration* では、 *ColName* パラメーターと *ColType* パラメーターを使用して *ColPattern* も指定されています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-230">In *SchemaDeclaration* in the WITH clause, *ColPattern* is also specified with the *ColName* and *ColType* parameters.</span></span> <span data-ttu-id="90b0c-231">省略可能な *ColPattern* は、次のことを示すために指定する XPath パターンです。</span><span class="sxs-lookup"><span data-stu-id="90b0c-231">The optional *ColPattern* is the XPath pattern specified to indicate the following:</span></span>  
  
-   <span data-ttu-id="90b0c-232">行セット内の**ProdID**列の *ColPattern* に指定された XPath パターン ( **.** ) により、コンテキスト ノード (現在のノード) が識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-232">The XPath pattern (**.**) specified as *ColPattern* for the **ProdID** column in the rowset identifies the context node, current node.</span></span> <span data-ttu-id="90b0c-233">指定された *rowpattern* によって、これは、<`OrderDetail`> 要素の **ProductID** 属性となります。</span><span class="sxs-lookup"><span data-stu-id="90b0c-233">As per the *rowpattern* specified, it is the **ProductID** attribute of the <`OrderDetail`> element.</span></span>  
  
-   <span data-ttu-id="90b0c-234">行セット内の **Qty** 列に指定された *ColPattern* である **../\@Quantity** により、コンテキスト ノード \<ProductID> の親ノードである <`OrderDetail`> の **Quantity** 属性が識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-234">The *ColPattern*, **../\@Quantity**, specified for the **Qty** column in the rowset identifies the **Quantity** attribute of the parent, <`OrderDetail`>, node of the context node, \<ProductID>.</span></span>  
  
-   <span data-ttu-id="90b0c-235">同様に、行セット内の **OID** 列に指定された *ColPattern* である **../../\@OrderID** により、コンテキスト ノードの親ノードの親である <`Order`> の **OrderID** 属性が識別されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-235">Similarly, the *ColPattern*, **../../\@OrderID**, specified for the **OID** column in the rowset identifies the **OrderID** attribute of the parent, <`Order`>, of the parent node of the context node.</span></span> <span data-ttu-id="90b0c-236">親ノードは <`OrderDetail`> で、コンテキスト ノードは <`ProductID`> です。</span><span class="sxs-lookup"><span data-stu-id="90b0c-236">The parent node is <`OrderDetail`>, and the context node is <`ProductID`>.</span></span>  
  
 <span data-ttu-id="90b0c-237">次に、SELECT ステートメントにより、OPENXML で提供される行セット内のすべての列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-237">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
--Sample XML document  
SET @xmlDocument =N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer/Order/OrderDetail/@ProductID')  
       WITH ( ProdID  int '.',  
              Qty     int '../@Quantity',  
              OID     int '../../@OrderID')  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="90b0c-238">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-238">This is the result:</span></span>  
  
```  
ProdID      Qty         OID  
----------- ----------- -------   
11          12          10248  
42          10          10248  
72          3           10283  
```  
  
### <a name="h-specifying-an-xml-document-that-has-multiple-text-nodes"></a><span data-ttu-id="90b0c-239">H.</span><span class="sxs-lookup"><span data-stu-id="90b0c-239">H.</span></span> <span data-ttu-id="90b0c-240">複数のテキスト ノードを含む XML ドキュメントの指定</span><span class="sxs-lookup"><span data-stu-id="90b0c-240">Specifying an XML document that has multiple text nodes</span></span>  
 <span data-ttu-id="90b0c-241">XML ドキュメント内に複数のテキスト ノードがある場合、 *ColPattern*である **text()** が指定された SELECT ステートメントにより、すべてのテキスト ノードではなく最初のテキスト ノードだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-241">If you have multiple text nodes in an XML document, a SELECT statement with a *ColPattern*, **text()**, returns only the first text node, instead of all of them.</span></span> <span data-ttu-id="90b0c-242">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-242">For example:</span></span>  
  
```  
DECLARE @h int  
EXEC sp_xml_preparedocument @h OUTPUT,  
         N'<root xmlns:a="urn:1">  
           <a:Elem abar="asdf">  
             T<a>a</a>U  
           </a:Elem>  
         </root>',  
         '<ns xmlns:b="urn:1" />'  
  
SELECT * FROM openxml(@h, '/root/b:Elem')  
      WITH (Col1 varchar(20) 'text()')  
EXEC sp_xml_removedocument @h  
```  
  
 <span data-ttu-id="90b0c-243">SELECT ステートメントでは、結果として **TaU** ではなく **T**が返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-243">The SELECT statement returns **T** as the result, and not **TaU**.</span></span>  
  
### <a name="i-specifying-the-xml-data-type-in-the-with-clause"></a><span data-ttu-id="90b0c-244">I.</span><span class="sxs-lookup"><span data-stu-id="90b0c-244">I.</span></span> <span data-ttu-id="90b0c-245">WITH 句での xml データ型の指定</span><span class="sxs-lookup"><span data-stu-id="90b0c-245">Specifying the xml data type in the WITH clause</span></span>  
 <span data-ttu-id="90b0c-246">WITH 句では、 **xml** データ型の列にマップされる列パターンが型指定されているかどうかにかかわらず、この列パターンから、空のシーケンスまたは要素のシーケンス、処理命令、テキスト ノード、およびコメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-246">In the WITH clause, a column pattern that is mapped to the **xml** data type column, whether typed or untyped, must return either an empty sequence or a sequence of elements, processing instructions, text nodes, and comments.</span></span> <span data-ttu-id="90b0c-247">データは **xml** データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-247">The data is cast to an **xml** data type.</span></span>  
  
 <span data-ttu-id="90b0c-248">次の例では、WITH 句のテーブル スキーマ宣言に **xml** 型の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-248">In the following example, the table schema declaration in the WITH clause includes **xml** type columns.</span></span>  
  
```  
DECLARE @h int  
DECLARE @x xml  
set @x = '<Root>  
  <row id="1"><lname>Duffy</lname>  
   <Address>  
            <Street>111 Maple</Street>  
            <City>Seattle</City>  
   </Address>  
  </row>  
  <row id="2"><lname>Wang</lname>  
   <Address>  
            <Street>222 Pine</Street>  
            <City>Bothell</City>  
   </Address>  
  </row>  
</Root>'  
  
EXEC sp_xml_preparedocument @h output, @x  
SELECT *  
FROM   OPENXML (@h, '/Root/row', 10)  
      WITH (id int '@id',  
  
            lname    varchar(30),  
            xmlname  xml 'lname',  
            OverFlow xml '@mp:xmltext')  
EXEC sp_xml_removedocument @h  
```  
  
 <span data-ttu-id="90b0c-249">具体的には、**xml** 型の変数 (\@x) を **sp_xml_preparedocument()** 関数に渡しています。</span><span class="sxs-lookup"><span data-stu-id="90b0c-249">Specifically, you are passing an **xml** type variable (\@x) to the **sp_xml_preparedocument()** function.</span></span>  
  
 <span data-ttu-id="90b0c-250">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-250">This is the result:</span></span>  
  
```  
id  lname   xmlname                   OverFlow  
--- ------- ------------------------------ -------------------------------  
1   Duffy   <lname>Duffy</lname>  <row><Address>  
                                   <Street>111 Maple</Street>  
                                   <City>Seattle</City>  
                                  </Address></row>  
2   Wang    <lname>Wang</lname>   <row><Address>  
                                    <Street>222 Pine</Street>  
                                    <City>Bothell</City>  
                                   </Address></row>  
```  
  
 <span data-ttu-id="90b0c-251">結果では、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="90b0c-251">Note the following from the result:</span></span>  
  
-   <span data-ttu-id="90b0c-252">**varchar(30)** 型の **lname** 列の場合、この列の値が対応する <`lname`> 要素から取得されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-252">For the **lname** column of **varchar(30)** type, its value is retrieved from the corresponding <`lname`> element.</span></span>  
  
-   <span data-ttu-id="90b0c-253">**xml** 型の **xmlname** 列では、この列の値として同じ名前の要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-253">For the **xmlname** column of **xml** type, the same name element is returned as its value.</span></span>  
  
-   <span data-ttu-id="90b0c-254">フラグは 10 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-254">The flag is set to 10.</span></span> <span data-ttu-id="90b0c-255">10 は 2 + 8 を意味し、2 は要素中心のマッピングを示します。8 は未使用の XML データのみを WITH 句で定義した OverFlow 列に追加する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-255">The 10 means 2 + 8, where 2 indicates element-centric mapping and 8 indicates that only unconsumed XML data should be added to the OverFlow column defined in the WITH clause.</span></span> <span data-ttu-id="90b0c-256">フラグを 2 に設定すると、WITH 句で指定された OverFlow 列に XML ドキュメント全体がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-256">If you set the flag to 2, the whole XML document is copied to the OverFlow column that is specified in the WITH clause.</span></span>  
  
-   <span data-ttu-id="90b0c-257">WITH 句の列が型指定された XML 列で、XML インスタンスがスキーマに準拠しない場合、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-257">In case the column in the WITH clause is a typed XML column and the XML instance does not confirm to the schema, an error is returned.</span></span>  
  
### <a name="j-retrieving-individual-values-from-multivalued-attributes"></a><span data-ttu-id="90b0c-258">J.</span><span class="sxs-lookup"><span data-stu-id="90b0c-258">J.</span></span> <span data-ttu-id="90b0c-259">複数の値の属性から個別の値の取得</span><span class="sxs-lookup"><span data-stu-id="90b0c-259">Retrieving individual values from multivalued attributes</span></span>  
 <span data-ttu-id="90b0c-260">XML ドキュメントには、複数の値を指定できる属性を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-260">An XML document can have attributes that are multivalued.</span></span> <span data-ttu-id="90b0c-261">たとえば、 **IDREFS** 属性には複数の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-261">For example, the **IDREFS** attribute can be multivalued.</span></span> <span data-ttu-id="90b0c-262">XML ドキュメントでは、複数の値の属性値を、各値をスペースで区切った文字列として指定します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-262">In an XML document, the multivalued attribute values are specified as a string, with the values separated by a space.</span></span> <span data-ttu-id="90b0c-263">次の XML ドキュメントでは、\<Student> 要素の **attends** 属性と \<Class> 要素の **attendedBy** 属性に複数の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-263">In the following XML document, the **attends** attribute of the \<Student> element and the **attendedBy** attribute of \<Class> are multivalued.</span></span> <span data-ttu-id="90b0c-264">複数の値を指定できる XML 属性から値を個別に取得し、各値をデータベース内の別々の行に格納するには、新たな作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="90b0c-264">Retrieving individual values from a multivalued XML attribute and storing each value in a separate row in the database requires additional work.</span></span> <span data-ttu-id="90b0c-265">この例ではその処理を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-265">This example shows the process.</span></span>  
  
 <span data-ttu-id="90b0c-266">このサンプル XML ドキュメントは、次の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-266">This sample XML document is made up of the following elements:</span></span>  
  
-   \<Student>  
  
     <span data-ttu-id="90b0c-267">**id** (学生 ID) 属性、 **name**属性、および **attends** 属性。</span><span class="sxs-lookup"><span data-stu-id="90b0c-267">The **id** (student ID), **name**, and **attends** attributes.</span></span> <span data-ttu-id="90b0c-268">**attends** 属性には複数の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-268">The **attends** attribute is a multivalued attribute.</span></span>  
  
-   \<Class>  
  
     <span data-ttu-id="90b0c-269">**id** (クラス ID) 属性、 **name**属性、および **attendedBy** 属性。</span><span class="sxs-lookup"><span data-stu-id="90b0c-269">The **id** (class ID), **name**, and **attendedBy** attributes.</span></span> <span data-ttu-id="90b0c-270">**attendedBy** 属性には複数の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-270">The **attendedBy** attribute is a multivalued attribute.</span></span>  
  
 <span data-ttu-id="90b0c-271">\<Student> の **attends** 属性と \<Class> の **attendedBy** 属性は、Student テーブルと Class テーブル間の **m:n** リレーションシップを表します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-271">The **attends** attribute in \<Student> and the **attendedBy** attribute in \<Class> represent a **m:n** relationship between the Student and Class tables.</span></span> <span data-ttu-id="90b0c-272">学生は多くのクラスを受講でき、クラスは多くの学生を受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-272">A student can take many classes and a class can have many students.</span></span>  
  
 <span data-ttu-id="90b0c-273">次に示すように、このドキュメントを細分化し、データベースに保存するとします。</span><span class="sxs-lookup"><span data-stu-id="90b0c-273">Assume that you want to shred this document and save it in the database as shown in the following:</span></span>  
  
-   <span data-ttu-id="90b0c-274">\<Student> データは Students テーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-274">Save the \<Student> data in the Students table.</span></span>  
  
-   <span data-ttu-id="90b0c-275">\<Class> データは Courses テーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-275">Save the \<Class> data in the Courses table.</span></span>  
  
-   <span data-ttu-id="90b0c-276">Student と Class 間の **m:n** リレーションシップ データは、CourseAttendence テーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-276">Save the **m:n** relationship data, between Student and Class, in the CourseAttendence table.</span></span> <span data-ttu-id="90b0c-277">値を抽出するには、新たな作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="90b0c-277">Additional work is required to extract the values.</span></span> <span data-ttu-id="90b0c-278">この情報を取得し、テーブルに格納するには、次のストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-278">To retrieve this information and store it in the table, use these stored procedures:</span></span>  
  
    -   <span data-ttu-id="90b0c-279">**Insert_Idrefs_Values**</span><span class="sxs-lookup"><span data-stu-id="90b0c-279">**Insert_Idrefs_Values**</span></span>  
  
         <span data-ttu-id="90b0c-280">コース ID と学生 ID の値を CourseAttendence テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-280">Inserts the values of course ID and student ID in the CourseAttendence table.</span></span>  
  
    -   <span data-ttu-id="90b0c-281">**Extract_idrefs_values**</span><span class="sxs-lookup"><span data-stu-id="90b0c-281">**Extract_idrefs_values**</span></span>  
  
         <span data-ttu-id="90b0c-282">各 \<Course> 要素から個別の学生 ID を抽出します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-282">Extracts the individual student IDs from each \<Course> element.</span></span> <span data-ttu-id="90b0c-283">エッジ テーブルを使用して、これらの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-283">An edge table is used to retrieve these values.</span></span>  
  
 <span data-ttu-id="90b0c-284">次に手順を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-284">Here are the steps:</span></span>  
  
```  
-- Create these tables:  
DROP TABLE CourseAttendance  
DROP TABLE Students  
DROP TABLE Courses  
GO  
CREATE TABLE Students(  
                id   varchar(5) primary key,  
                name varchar(30)  
                )  
GO  
CREATE TABLE Courses(  
               id       varchar(5) primary key,  
               name     varchar(30),  
               taughtBy varchar(5)  
)  
GO  
CREATE TABLE CourseAttendance(  
             id         varchar(5) references Courses(id),  
             attendedBy varchar(5) references Students(id),  
             constraint CourseAttendance_PK primary key (id, attendedBy)  
)  
go  
-- Create these stored procedures:  
DROP PROCEDURE f_idrefs  
GO  
CREATE PROCEDURE f_idrefs  
    @t      varchar(500),  
    @idtab  varchar(50),  
    @id     varchar(5)  
AS  
DECLARE @sp int  
DECLARE @att varchar(5)  
SET @sp = 0  
WHILE (LEN(@t) > 0)  
BEGIN   
    SET @sp = CHARINDEX(' ', @t+ ' ')  
    SET @att = LEFT(@t, @sp-1)  
    EXEC('INSERT INTO '+@idtab+' VALUES ('''+@id+''', '''+@att+''')')  
    SET @t = SUBSTRING(@t+ ' ', @sp+1, LEN(@t)+1-@sp)  
END  
Go  
  
DROP PROCEDURE fill_idrefs  
GO  
CREATE PROCEDURE fill_idrefs   
    @xmldoc     int,  
    @xpath      varchar(100),  
    @from       varchar(50),  
    @to         varchar(50),  
    @idtable    varchar(100)  
AS  
DECLARE @t varchar(500)  
DECLARE @id varchar(5)  
  
/* Temporary edge table */  
SELECT *   
INTO #TempEdge   
FROM OPENXML(@xmldoc, @xpath)  
  
DECLARE fillidrefs_cursor CURSOR FOR  
    SELECT CAST(iv.text AS nvarchar(200)) AS id,  
           CAST(av.text AS nvarchar(4000)) AS refs  
    FROM   #TempEdge c, #TempEdge i,  
           #TempEdge iv, #TempEdge a, #TempEdge av  
    WHERE  c.id = i.parentid  
    AND    UPPER(i.localname) = UPPER(@from)  
    AND    i.id = iv.parentid  
    AND    c.id = a.parentid  
    AND    UPPER(a.localname) = UPPER(@to)  
    AND    a.id = av.parentid  
  
OPEN fillidrefs_cursor  
FETCH NEXT FROM fillidrefs_cursor INTO @id, @t  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
    IF (@@FETCH_STATUS <> -2)  
    BEGIN  
        execute f_idrefs @t, @idtable, @id  
    END  
    FETCH NEXT FROM fillidrefs_cursor INTO @id, @t  
END  
CLOSE fillidrefs_cursor  
DEALLOCATE fillidrefs_cursor  
Go  
-- This is the sample document that is shredded and the data is stored in the preceding tables.  
DECLARE @h int  
EXECUTE sp_xml_preparedocument @h OUTPUT, N'<Data>  
  <Student id = "s1" name = "Student1"  attends = "c1 c3 c6"  />  
  <Student id = "s2" name = "Student2"  attends = "c2 c4" />  
  <Student id = "s3" name = "Student3"  attends = "c2 c4 c6" />  
  <Student id = "s4" name = "Student4"  attends = "c1 c3 c5" />  
  <Student id = "s5" name = "Student5"  attends = "c1 c3 c5 c6" />  
  <Student id = "s6" name = "Student6" />  
  
  <Class id = "c1" name = "Intro to Programming"   
         attendedBy = "s1 s4 s5" />  
  <Class id = "c2" name = "Databases"   
         attendedBy = "s2 s3" />  
  <Class id = "c3" name = "Operating Systems"   
         attendedBy = "s1 s4 s5" />  
  <Class id = "c4" name = "Networks" attendedBy = "s2 s3" />  
  <Class id = "c5" name = "Algorithms and Graphs"   
         attendedBy =  "s4 s5"/>  
  <Class id = "c6" name = "Power and Pragmatism"   
         attendedBy = "s1 s3 s5" />  
</Data>'  
  
INSERT INTO Students SELECT * FROM OPENXML(@h, '//Student') WITH Students  
  
INSERT INTO Courses SELECT * FROM OPENXML(@h, '//Class') WITH Courses  
/* Using the edge table */  
EXECUTE fill_idrefs @h, '//Class', 'id', 'attendedby', 'CourseAttendance'  
  
SELECT * FROM Students  
SELECT * FROM Courses  
SELECT * FROM CourseAttendance  
  
EXECUTE sp_xml_removedocument @h  
```  
  
### <a name="k-retrieving-binary-from-base64-encoded-data-in-xml"></a><span data-ttu-id="90b0c-285">K.</span><span class="sxs-lookup"><span data-stu-id="90b0c-285">K.</span></span> <span data-ttu-id="90b0c-286">XML 内の base64 エンコードされたデータからのバイナリ データの取得</span><span class="sxs-lookup"><span data-stu-id="90b0c-286">Retrieving binary from base64 encoded data in XML</span></span>  
 <span data-ttu-id="90b0c-287">多くの場合、バイナリ データは base64 エンコードを使用して XML に含められます。</span><span class="sxs-lookup"><span data-stu-id="90b0c-287">Binary data is frequently included in XML using base64 encoding.</span></span> <span data-ttu-id="90b0c-288">OPENXML を使用してこの XML を細分化するときに、base64 エンコードされたデータを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="90b0c-288">When you shred this XML by using OPENXML, you receive the base64 encoded data.</span></span> <span data-ttu-id="90b0c-289">この例では、base64 エンコードされたデータをバイナリ データに変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-289">This example shows how you can convert the base64 encoded data back to binary.</span></span>  
  
-   <span data-ttu-id="90b0c-290">サンプル バイナリ データを含むテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-290">Create a table with sample binary data.</span></span>  
  
-   <span data-ttu-id="90b0c-291">FOR XML クエリと BINARY BASE64 オプションを使用して、base64 としてエンコードされるバイナリ データを含む XML を構築します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-291">Use a FOR XML query and the BINARY BASE64 option to construct XML that has the binary data encoded as base64.</span></span>  
  
-   <span data-ttu-id="90b0c-292">OPENXML を使用して XML を細分化します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-292">Shred the XML by using OPENXML.</span></span> <span data-ttu-id="90b0c-293">OPENXML から返されるデータは base64 エンコードされたデータです。</span><span class="sxs-lookup"><span data-stu-id="90b0c-293">The data returned by OPENXML will be base64 encoded data.</span></span> <span data-ttu-id="90b0c-294">次に、.value 関数を呼び出してデータをバイナリ データに変換します。</span><span class="sxs-lookup"><span data-stu-id="90b0c-294">Next, call the .value function to convert it back to binary.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 varbinary(100))  
go  
-- Insert sample binary data  
INSERT T VALUES(1, 0x1234567890)   
go  
 -- Create test XML document that has base64 encoded binary data (use FOR XML query and specify BINARY BASE64 option)  
SELECT * FROM T  
FOR XML AUTO, BINARY BASE64  
go  
-- result  
-- <T Col1="1" Col2="EjRWeJA="/>  
  
-- Now shredd the sample XML using OPENXML.   
-- Call the .value function to convert   
-- the base64 encoded data returned by OPENXML to binary.  
DECLARE @h int ;  
EXEC sp_xml_preparedocument @h OUTPUT, '<T Col1="1" Col2="EjRWeJA="/>' ;  
SELECT Col1,   
CAST('<binary>' + Col2 + '</binary>' AS XML).value('.', 'varbinary(max)') AS BinaryCol   
FROM openxml(@h, '/T')   
WITH (Col1 integer, Col2 varchar(max)) ;  
EXEC sp_xml_removedocument @h ;  
GO  
```  
  
 結果は次のとおりです。 <span data-ttu-id="90b0c-296">返されるバイナリ データは、テーブル T 内の元のバイナリ データです。</span><span class="sxs-lookup"><span data-stu-id="90b0c-296">The binary data returned is the original binary data in table T.</span></span>  
  
```  
Col1        BinaryCol  
----------- ---------------------  
1           0x1234567890  
```  
  
## <a name="see-also"></a><span data-ttu-id="90b0c-297">参照</span><span class="sxs-lookup"><span data-stu-id="90b0c-297">See Also</span></span>  
 <span data-ttu-id="90b0c-298">[sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b0c-298">[sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql) </span></span>  
 <span data-ttu-id="90b0c-299">[sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b0c-299">[sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql) </span></span>  
 <span data-ttu-id="90b0c-300">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90b0c-300">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="90b0c-301">OPENXML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90b0c-301">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
