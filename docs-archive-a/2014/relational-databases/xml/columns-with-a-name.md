---
title: 名前のある列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: c994e089-4cfc-4e9b-b7fc-e74f6014b51a
author: rothja
ms.author: jroth
ms.openlocfilehash: 32cfe617b80ed216374249961b85eae401011a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712849"
---
# <a name="columns-with-a-name"></a><span data-ttu-id="a0384-102">名前のある列</span><span class="sxs-lookup"><span data-stu-id="a0384-102">Columns with a Name</span></span>
  <span data-ttu-id="a0384-103">行セット内の名前のある列が、大文字と小文字を区別して結果の XML にマップされる条件を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-103">The following are the specific conditions in which rowset columns with a name are mapped, case-sensitive, to the resulting XML:</span></span>  
  
-   <span data-ttu-id="a0384-104">列名がアット マーク (\@) で始まる場合。</span><span class="sxs-lookup"><span data-stu-id="a0384-104">The column name starts with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="a0384-105">列名がアット マーク (\@) で始まらない場合。</span><span class="sxs-lookup"><span data-stu-id="a0384-105">The column name does not start with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="a0384-106">列名がアット マーク (\@) で始まらず、スラッシュ (/) を含む場合。</span><span class="sxs-lookup"><span data-stu-id="a0384-106">The column name does not start with an at sign\@ and contains a slash mark (/).</span></span>  
  
-   <span data-ttu-id="a0384-107">複数の列に同一のプレフィックスがある場合</span><span class="sxs-lookup"><span data-stu-id="a0384-107">Several columns share the same prefix.</span></span>  
  
-   <span data-ttu-id="a0384-108">名前の異なる列がある場合</span><span class="sxs-lookup"><span data-stu-id="a0384-108">One column has a different name.</span></span>  
  
## <a name="column-name-starts-with-an-at-sign-"></a><span data-ttu-id="a0384-109">列名がアット マーク (\@) で始まる場合</span><span class="sxs-lookup"><span data-stu-id="a0384-109">Column Name Starts with an At Sign (\@)</span></span>  
 <span data-ttu-id="a0384-110">列名がアットマーク () で始まり、 \@ スラッシュ (/) が含まれていない場合は、 `row` 対応する列の値を持つ <> 要素の属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-110">If the column name starts with an at sign (\@) and does not contain a slash mark (/), an attribute of the <`row`> element that has the corresponding column value is created.</span></span> <span data-ttu-id="a0384-111">たとえば、次のクエリは 2 列 (\@PmId、Name) の行セットを返します。</span><span class="sxs-lookup"><span data-stu-id="a0384-111">For example, the following query returns a two-column (\@PmId, Name) rowset.</span></span> <span data-ttu-id="a0384-112">結果の XML では、対応する <`row`> 要素に **PmId** 属性が追加され、この属性に ProductModelID の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-112">In the resulting XML, a **PmId** attribute is added to the corresponding <`row`> element and a value of ProductModelID is assigned to it.</span></span>  
  
```  
  
SELECT ProductModelID as "@PmId",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
  
```  
  
 <span data-ttu-id="a0384-113">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-113">This is the result:</span></span>  
  
```  
<row PmId="7">  
  <Name>HL Touring Frame</Name>  
</row>  
```  
  
 <span data-ttu-id="a0384-114">属性は、同一レベルでは要素ノード、テキスト ノードなどの他の種類のノードよりも前に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0384-114">Note that attributes must come before any other node types, such as element nodes and text nodes, in the same level.</span></span> <span data-ttu-id="a0384-115">次のクエリはエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="a0384-115">The following query will return an error:</span></span>  
  
```  
SELECT Name,  
       ProductModelID as "@PmId"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign-"></a><span data-ttu-id="a0384-116">列名がアット マーク (\@) で始まらない場合</span><span class="sxs-lookup"><span data-stu-id="a0384-116">Column Name Does Not Start with an At Sign (\@)</span></span>  
 <span data-ttu-id="a0384-117">列名がアットマーク () で始まらず、 \@ XPath ノードテストの1つでもなく、スラッシュ (/) も含まない場合は、行 <要素のサブ要素である XML 要素が `row` 既定で> 作成されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-117">If the column name does not start with an at sign (\@), is not one of the XPath node tests, and does not contain a slash mark (/), an XML element that is a subelement of the row element, <`row`> by default, is created.</span></span>  
  
 <span data-ttu-id="a0384-118">次のクエリでは列名 result が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a0384-118">The following query specifies the column name, the result.</span></span> <span data-ttu-id="a0384-119">したがって、<`row`> 要素には、<`result`> 子要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-119">Therefore, a <`result`> element child is added to the <`row`> element.</span></span>  
  
```  
SELECT 2+2 as result  
for xml PATH  
```  
  
 <span data-ttu-id="a0384-120">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-120">This is the result:</span></span>  
  
```  
<row>  
  <result>4</result>  
</row>  
```  
  
 <span data-ttu-id="a0384-121">次のクエリでは、**xml** 型の Instructions 列に対して指定した XQuery から返される XML に対応する列の名前として、ManuWorkCenterInformation を指定しています。</span><span class="sxs-lookup"><span data-stu-id="a0384-121">The following query specifies the column name, ManuWorkCenterInformation, for the XML returned by the XQuery specified against Instructions column of **xml** type.</span></span> <span data-ttu-id="a0384-122">したがって、<`row`> 要素の子要素として、<`ManuWorkCenterInformation`> 要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-122">Therefore, a <`ManuWorkCenterInformation`> element is added as a child of the <`row`> element.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') as ManuWorkCenterInformation  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
 <span data-ttu-id="a0384-123">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-123">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>7</ProductModelID>  
  <Name>HL Touring Frame</Name>  
  <ManuWorkCenterInformation>  
    <MI:Location ...LocationID="10" ...></MI:Location>  
    <MI:Location ...LocationID="20" ...></MI:Location>  
     ...  
  </ManuWorkCenterInformation>  
</row>  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign--and-contains-a-slash-mark-"></a><span data-ttu-id="a0384-124">列名がアット マーク (\@) で始まらず、スラッシュ (/) を含む場合</span><span class="sxs-lookup"><span data-stu-id="a0384-124">Column Name Does Not Start with an At Sign (\@) and Contains a Slash Mark (/)</span></span>  
 <span data-ttu-id="a0384-125">列名がアット マーク (\@) で始まらず、スラッシュ (/) を含んでいる場合、列名は XML 階層を示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-125">If the column name does not start with an at sign (\@), but contains a slash mark (/), the column name indicates an XML hierarchy.</span></span> <span data-ttu-id="a0384-126">たとえば、列名を "Name1/Name2/Name3.../Name***n*** " とすると、Name***i*** は、i = 1 の場合は現在の行要素の入れ子である要素を表し、それ以外の場合は Name***i-1***要素の下にある要素を表します。</span><span class="sxs-lookup"><span data-stu-id="a0384-126">For example, if the column name is "Name1/Name2/Name3.../Name***n*** ", each Name***i*** represents an element name that is nested in the current row element (for i=1) or that is under the element that has the name Name***i-1***.</span></span> <span data-ttu-id="a0384-127">Name***n*** が '\@' で始まる場合は、Name***n-1*** 要素の属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a0384-127">If Name***n*** starts with '\@', it is mapped to an attribute of Name***n-1*** element.</span></span>  
  
 <span data-ttu-id="a0384-128">たとえば次のクエリは、従業員の ID と名前を返します。従業員名は、First、Middle、および Last から構成される複合型の要素 EmpName で表現されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-128">For example, the following query returns an employee ID and name that are represented as a complex element EmpName that contains a First, Middle, and Last name.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="a0384-129">PATH モードでは、列名は XML を作成する際のパスとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-129">The column names are used as a path in constructing XML in the PATH mode.</span></span> <span data-ttu-id="a0384-130">従業員 ID の値を含む列名は、' ' で始まり \@ ます。したがって、属性**EmpID**が <> 要素に追加され `row` ます。</span><span class="sxs-lookup"><span data-stu-id="a0384-130">The column name that contains employee ID values, starts with '\@'.Therefore, an attribute, **EmpID**, is added to the <`row`> element.</span></span> <span data-ttu-id="a0384-131">それ以外のすべての列の列名には、階層を示すスラッシュ ('/') が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0384-131">All other columns include a slash mark ('/') in the column name that indicates hierarchy.</span></span> <span data-ttu-id="a0384-132">結果の XML では、<`row`> 要素の下に <`EmpName`> 子要素があり、<`EmpName`> の下に子要素 <`First`>、<`Middle`>、および <`Last`> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-132">The resulting XML will have the <`EmpName`> child under the <`row`> element, and the <`EmpName`> child will have <`First`>, <`Middle`> and <`Last`> element children.</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="a0384-133">この従業員のミドル ネームは NULL です。既定では、要素や属性がない状態に NULL 値がマップされます。</span><span class="sxs-lookup"><span data-stu-id="a0384-133">The employee middle name is null and, by default, the null value maps to the absence of the element or attribute.</span></span> <span data-ttu-id="a0384-134">値が NULL であっても要素を生成するには、次のクエリのように XSINIL を指定した ELEMENTS ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0384-134">If you want elements generated for the NULL values, you can specify the ELEMENTS directive with XSINIL as shown in this query.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="a0384-135">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-135">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
      EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="a0384-136">PATH モードの既定では要素中心の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-136">By default, the PATH mode generates element-centric XML.</span></span> <span data-ttu-id="a0384-137">したがって、PATH モードのクエリで ELEMENTS ディレクティブを指定しても効力はありません。</span><span class="sxs-lookup"><span data-stu-id="a0384-137">Therefore, specifying the ELEMENTS directive in a PATH mode query has no effect.</span></span> <span data-ttu-id="a0384-138">ただし、前のクエリで示したように、ELEMENTS ディレクティブを XSINIL と組み合わせると、NULL 値に対して要素を生成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a0384-138">However, as shown in the previous example, the ELEMENTS directive is useful with XSINIL to generate elements for null values.</span></span>  
  
 <span data-ttu-id="a0384-139">次のクエリでは従業員の ID と名前以外に住所を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0384-139">Besides the ID and name, the following query retrieves an employee address.</span></span> <span data-ttu-id="a0384-140">住所列の列名のパスにより、<`row`> 要素に <`Address`> 子要素が追加され、<`Address`> 要素の子要素として詳しい住所が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-140">As per the path in the column names for address columns, an <`Address`> element child is added to the <`row`> element and the address details are added as element children of the <`Address`> element.</span></span>  
  
```  
SELECT EmployeeID   "@EmpID",   
       FirstName    "EmpName/First",   
       MiddleName   "EmpName/Middle",   
       LastName     "EmpName/Last",  
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City         "Address/City"  
FROM   HumanResources.Employee E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="a0384-141">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-141">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
</row>  
```  
  
## <a name="several-columns-share-the-same-path-prefix"></a><span data-ttu-id="a0384-142">複数の列に同一のパス プレフィックスがある場合</span><span class="sxs-lookup"><span data-stu-id="a0384-142">Several Columns Share the Same Path Prefix</span></span>  
 <span data-ttu-id="a0384-143">連続した複数の列に同一のパス プレフィックスがある場合、これらの列は 1 つの名前でグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-143">If several subsequent columns share the same path prefix, they are grouped together under the same name.</span></span> <span data-ttu-id="a0384-144">異なる名前空間プレフィックスが使用されている場合は、同一の名前空間にバインドされていても、パスは異なるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="a0384-144">If different namespace prefixes are being used even if they are bound to the same namespace, a path is considered different.</span></span> <span data-ttu-id="a0384-145">上のクエリで、FirstName 列、MiddleName 列、および LastName 列にはいずれも EmpName プレフィックスがあるので、これらは <`EmpName`> 要素の子として追加されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-145">In the previous query, the FirstName, MiddleName, and LastName columns share the same EmpName prefix.Therefore, they are added as children of the <`EmpName`> element.</span></span> <span data-ttu-id="a0384-146">このことは、上記の例の <`Address`> 要素の生成にも該当します。</span><span class="sxs-lookup"><span data-stu-id="a0384-146">This is also the case when you were creating the <`Address`> element in the previous example.</span></span>  
  
## <a name="one-column-has-a-different-name"></a><span data-ttu-id="a0384-147">名前の異なる列がある場合</span><span class="sxs-lookup"><span data-stu-id="a0384-147">One Column Has a Different Name</span></span>  
 <span data-ttu-id="a0384-148">変更を加えた次のクエリに示すように、異なる名前の列が間にある場合、グループは分割されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-148">If a column with a different name appears in between, it will break the grouping, as shown in the following modified query.</span></span> <span data-ttu-id="a0384-149">上のクエリで示した FirstName、MiddleName、および LastName から構成されるグループは、FirstName 列と MiddleName 列の間に住所列を追加すると分割されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-149">The query breaks the grouping of FirstName, MiddleName, and LastName, as specified in the previous query, by adding address columns in between the FirstName and MiddleName columns.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName "EmpName/First",   
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City "Address/City",  
       MiddleName "EmpName/Middle",   
       LastName "EmpName/Last"  
FROM   HumanResources.EmployeeAddress E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="a0384-150">このクエリの結果、<`EmpName`> 要素が 2 つ作成されます。</span><span class="sxs-lookup"><span data-stu-id="a0384-150">As a result, the query creates two <`EmpName`> elements.</span></span> <span data-ttu-id="a0384-151">最初の <`EmpName`> 要素には <`FirstName`> 子要素が、2 番目の <`EmpName`> 要素には <`MiddleName`> 子要素と <`LastName`> 子要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a0384-151">The first <`EmpName`> element has the <`FirstName`> element child and the second <`EmpName`> element has the <`MiddleName`> and <`LastName`> element children.</span></span>  
  
 <span data-ttu-id="a0384-152">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a0384-152">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
  <EmpName>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0384-153">参照</span><span class="sxs-lookup"><span data-stu-id="a0384-153">See Also</span></span>  
 [<span data-ttu-id="a0384-154">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="a0384-154">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
