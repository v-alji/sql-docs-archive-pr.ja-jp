---
title: 'Sql: limit-field および sql: limit-value を使用した値のフィルター処理 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, filtering values
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: c0f7ae92-eeec-430e-a66a-f22c3ae64a5e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7886a9a6f51c76ed693576ca6f4659f4051d1f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741674"
---
# <a name="filtering-values-using-sqllimit-field-and-sqllimit-value-sqlxml-40"></a><span data-ttu-id="c9f69-102">sql:limit-field および sql:limit-value を使用した、値のフィルター選択 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c9f69-102">Filtering Values Using sql:limit-field and sql:limit-value (SQLXML 4.0)</span></span>
  <span data-ttu-id="c9f69-103">データベース クエリから返される行を、一定の制限値に基づいて制限することができます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-103">You can limit rows that are returned from a database query on the basis of some limiting value.</span></span> <span data-ttu-id="c9f69-104">制限の対象となるデータベース列を識別し、返されるデータのフィルター選択に使用する制限値を指定するには、`sql:limit-field` 注釈と `sql:limit-value` 注釈を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-104">The `sql:limit-field` and `sql:limit-value` annotations are used to identify the database column that contains limiting values and to specify a specific limiting value to be used to filter the data returned.</span></span>  
  
 <span data-ttu-id="c9f69-105">`sql:limit-field` 注釈では、制限の対象となる列を指定します。この注釈は、マップされる要素または属性ごとに使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-105">The `sql:limit-field` annotation is used to identify a column that contains a limiting value; it is allowed on each mapped element or attribute.</span></span>  
  
 <span data-ttu-id="c9f69-106">`sql:limit-value` 注釈では、`sql:limit-field` 注釈で指定された列に適用する制限値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-106">The `sql:limit-value` annotation is used to specify the limited value in the column that is specified in the `sql:limit-field` annotation.</span></span> <span data-ttu-id="c9f69-107">`sql:limit-value` 注釈は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c9f69-107">The `sql:limit-value` annotation is optional.</span></span> <span data-ttu-id="c9f69-108">`sql:limit-value`を指定しない場合は、NULL 値が想定されます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-108">If `sql:limit-value` is not specified, a NULL value is assumed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9f69-109">マップされる SQL 列が `sql:limit-field` 型の場合に `real` を指定すると、SQLXML 4.0 では XML スキーマで指定されているとおり、`sql:limit-value` 指定値として `nvarchar` が変換されます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-109">When working with a `sql:limit-field` where the mapped SQL column is of type `real`, SQLXML 4.0 performs conversion on the `sql:limit-value` as specified in XML schemas as an `nvarchar` specified value.</span></span> <span data-ttu-id="c9f69-110">ここで、10 進数の制限値を完全な科学的表記法で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9f69-110">This requires that decimal limit values be specified using full scientific notation.</span></span> <span data-ttu-id="c9f69-111">詳細については、後の例 B を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9f69-111">For more information, see Example B below.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c9f69-112">例</span><span class="sxs-lookup"><span data-stu-id="c9f69-112">Examples</span></span>  
 <span data-ttu-id="c9f69-113">次の例を使用して実際のサンプルを作成するには、次がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9f69-113">To create working samples using these examples, you need to have the following installed:</span></span>  
  
-   <span data-ttu-id="c9f69-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="c9f69-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="c9f69-115">MDAC 2.6 以降</span><span class="sxs-lookup"><span data-stu-id="c9f69-115">MDAC 2.6 or later</span></span>  
  
 <span data-ttu-id="c9f69-116">これらの例では、テンプレートを使用して、マッピング XSD スキーマに対する XPath クエリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-116">In these examples, templates are used to specify XPath queries against the mapping XSD schema.</span></span>  
  
### <a name="a-limiting-the-customer-addresses-returned-to-a-specific-address-type"></a><span data-ttu-id="c9f69-117">A.</span><span class="sxs-lookup"><span data-stu-id="c9f69-117">A.</span></span> <span data-ttu-id="c9f69-118">返される顧客の住所を特定の住所タイプに制限する</span><span class="sxs-lookup"><span data-stu-id="c9f69-118">Limiting the customer addresses returned to a specific address type</span></span>  
 <span data-ttu-id="c9f69-119">この例では、データベースに次の 2 つのテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9f69-119">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="c9f69-120">Customer (CustomerID, CompanyName)</span><span class="sxs-lookup"><span data-stu-id="c9f69-120">Customer (CustomerID, CompanyName)</span></span>  
  
-   <span data-ttu-id="c9f69-121">Addresses (CustomerID, AddressType, StreetAddress)</span><span class="sxs-lookup"><span data-stu-id="c9f69-121">Addresses (CustomerID, AddressType, StreetAddress)</span></span>  
  
 <span data-ttu-id="c9f69-122">顧客には、発送先住所と請求先住所のいずれかまたは両方が設定されています。</span><span class="sxs-lookup"><span data-stu-id="c9f69-122">A customer can have a shipping address and/or a billing address.</span></span> <span data-ttu-id="c9f69-123">AddressType 列の値は Shipping と Billing です。</span><span class="sxs-lookup"><span data-stu-id="c9f69-123">The AddressType column values are Shipping and Billing.</span></span>  
  
 <span data-ttu-id="c9f69-124">これは、 **ShipTo** schema 属性が Addresses 関係の StreetAddress 列にマップされるマッピングスキーマです。</span><span class="sxs-lookup"><span data-stu-id="c9f69-124">This is the mapping schema in which the **ShipTo** schema attribute maps to the StreetAddress column in the Addresses relation.</span></span> <span data-ttu-id="c9f69-125">この属性に対して返される値は、注釈と注釈を指定することによって、出荷先住所に限定され `sql:limit-field` `sql:limit-value` ます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-125">The values that are returned for this attribute are limited to only shipping addresses by specifying the `sql:limit-field` and `sql:limit-value` annotations.</span></span> <span data-ttu-id="c9f69-126">同様に、 **BillTo** schema 属性では、顧客の請求先住所のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-126">Similarly, the **BillTo** schema attribute returns only the billing address of a customer.</span></span>  
  
 <span data-ttu-id="c9f69-127">スキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c9f69-127">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Addresses"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:sequence>  
        <xsd:element name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        <xsd:element name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="c9f69-128">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c9f69-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="c9f69-129">**Tempdb**データベースに2つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-129">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (CustomerID int primary key,   
                           CompanyName varchar(30))  
    CREATE TABLE Addresses(CustomerID int,   
                           StreetAddress varchar(50),  
                           AddressType varchar(10))  
    ```  
  
2.  <span data-ttu-id="c9f69-130">サンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-130">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Customer values (1, 'Company A')  
    INSERT INTO Customer values (2, 'Company B')  
  
    INSERT INTO Addresses values  
               (1, 'Obere Str. 57 Berlin', 'billing')  
    INSERT INTO Addresses values  
               (1, 'Avda. de la Constituci??n 2222 M??xico D.F.', 'shipping')  
    INSERT INTO Addresses values  
               (2, '120 Hanover Sq., London', 'billing')  
    INSERT INTO Addresses values  
               (2, 'Forsterstr. 57, Mannheim', 'shipping')  
    ```  
  
3.  <span data-ttu-id="c9f69-131">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="c9f69-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="c9f69-132">LimitFieldValue.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-132">Save the file as LimitFieldValue.xml.</span></span>  
  
4.  <span data-ttu-id="c9f69-133">次のテンプレート (LimitFieldValueT.xml) を作成し、前の手順でスキーマ (LimitFieldValue.xml) を保存した場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-133">Create the following template (LimitFieldValueT.xml), and save it in the same where you saved the schema (LimitFieldValue.xml) in the previous step:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="LimitFieldValue.xml">  
            /Customer  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c9f69-134">マッピング スキーマ (LimitFieldValue.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c9f69-134">The directory path specified for the mapping schema (LimitFieldValue.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c9f69-135">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\LimitFieldValue.xml"  
    ```  
  
5.  <span data-ttu-id="c9f69-136">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c9f69-137">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9f69-137">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c9f69-138">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-138">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1" CompanyName="Company A">   
     <BillTo>Obere Str. 57 Berlin</BillTo>   
     <ShipTo>Avda. de la Constituci??n 2222 M??xico D.F.</ShipTo>   
  </Customer>   
  <Customer CustomerID="2" CompanyName="Company B">   
     <BillTo>120 Hanover Sq., London</BillTo>   
     <ShipTo>Forsterstr. 57, Mannheim</ShipTo>   
   </Customer>   
</ROOT>  
```  
  
### <a name="b-limiting-results-based-on-a-discount-value-of-type-real-data"></a><span data-ttu-id="c9f69-139">B.</span><span class="sxs-lookup"><span data-stu-id="c9f69-139">B.</span></span> <span data-ttu-id="c9f69-140">実数型データのディスカウント値に基づいて結果を制限する</span><span class="sxs-lookup"><span data-stu-id="c9f69-140">Limiting results based on a discount value of type real data</span></span>  
 <span data-ttu-id="c9f69-141">この例では、データベースに次の 2 つのテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9f69-141">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="c9f69-142">Orders (OrderID)</span><span class="sxs-lookup"><span data-stu-id="c9f69-142">Orders (OrderID)</span></span>  
  
-   <span data-ttu-id="c9f69-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span><span class="sxs-lookup"><span data-stu-id="c9f69-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span></span>  
  
 <span data-ttu-id="c9f69-144">これは、注文の詳細の**orderid**属性が orders リレーションシップの orderid 列にマップされるマッピングスキーマです。</span><span class="sxs-lookup"><span data-stu-id="c9f69-144">This is the mapping schema in which the **OrderID** attribute on the order details maps to the OrderID column in the orders relation.</span></span> <span data-ttu-id="c9f69-145">この属性に対して返される値は、および注釈を使用して、**割引**属性に対して指定されている 2.0000000 e-001 (0.2) の値のみに制限され `sql:limit-field` `sql:limit-value` ます。</span><span class="sxs-lookup"><span data-stu-id="c9f69-145">The values that are returned for this attribute are limited to only those that have a value of 2.0000000e-001 (0.2) as specified for the **Discount** attribute using the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 <span data-ttu-id="c9f69-146">スキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c9f69-146">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
   <xsd:appinfo>  
    <sql:relationship name="OrderOrderDetails"  
        parent="Orders"  
        parent-key="OrderID"  
        child="OrderDetails"  
        child-key="OrderID" />  
   </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="root" sql:is-constant="1">  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="Order" sql:relation="Orders" >  
          <xsd:complexType>  
             <xsd:sequence>  
                <xsd:element name="orderDetail"   
                       sql:relation="OrderDetails"   
                       sql:limit-field="Discount"                       sql:limit-value="2.0000000e-001"  
                       sql:relationship="OrderOrderDetails">  
                   <xsd:complexType>  
                     <xsd:attribute name="OrderID"   />   
                     <xsd:attribute name="ProductID" />   
                     <xsd:attribute name="Discount"  />   
                     <xsd:attribute name="Quantity"  />   
                     <xsd:attribute name="UnitPrice" />   
                   </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
           <xsd:attribute name="OrderID"/>   
          </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="c9f69-147">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="c9f69-147">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="c9f69-148">**Tempdb**データベースに2つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-148">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Orders ([OrderID] int NOT NULL ) ON [PRIMARY]  
    ALTER TABLE Orders WITH NOCHECK ADD   
    CONSTRAINT [PK_Orders] PRIMARY KEY  CLUSTERED (  
       [OrderID]  
     )  ON [PRIMARY]   
    CREATE TABLE [OrderDetails] (  
       [OrderID] int NOT NULL ,  
       [ProductID] int NOT NULL ,  
       [UnitPrice] money NULL ,  
       [Quantity] smallint NOT NULL ,  
       [Discount] real NOT NULL   
    ) ON [PRIMARY]  
    ```  
  
2.  <span data-ttu-id="c9f69-149">サンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-149">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Orders ([OrderID]) values (10248)  
    INSERT INTO Orders ([OrderID]) values (10250)  
    INSERT INTO Orders ([OrderID]) values (10251)  
    INSERT INTO Orders ([OrderID]) values (10257)  
    INSERT INTO Orders ([OrderID]) values (10258)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10248,11,14,12,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10250,51,42.4,35,0.15)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10251,22,16.8,6,0.05)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10257,77,10.4,15,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10258,2,15.2,50,0.2)  
    ```  
  
3.  <span data-ttu-id="c9f69-150">スキーマ (LimitFieldValue.xml) をディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-150">Save the schema (LimitFieldValue.xml) in a directory.</span></span>  
  
4.  <span data-ttu-id="c9f69-151">次のテスト スクリプト (TestQuery.vbs) を作成し、"MyServer" を使用している SQL Server コンピューターの名前に変更して、前の手順でスキーマを保存したディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-151">Create the following test script (TestQuery.vbs), modify MyServer to the name of your SQL Server computer and save it in the same directory as you used in the previous step to save the schema:</span></span>  
  
    ```  
    Set conn = CreateObject("ADODB.Connection")  
    conn.Open "Provider=SQLOLEDB;Data Source=MyServer;Database=tempdb;Integrated Security=SSPI"  
    conn.Properties("SQLXML Version") = "sqlxml.4.0"   
    Set cmd = CreateObject("ADODB.Command")  
    Set stm = CreateObject("ADODB.Stream")  
    Set cmd.ActiveConnection = conn  
    stm.open  
    result ="none"  
    strXPathQuery="/root"  
    DBGUID_XPATH = "{EC2A4293-E898-11D2-B1B7-00C04F680C56}"  
    cmd.Dialect = DBGUID_XPATH  
    cmd.CommandText = strXPathQuery  
    cmd.Properties("Mapping schema") = "LimitFieldReal.xml"  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    WScript.Echo "executing for xml query"  
    On Error Resume Next  
    cmd.Execute , ,1024  
    if err then  
    Wscript.Echo err.description  
    Wscript.Echo err.Number  
    Wscript.Echo err.source  
    On Error GoTo 0  
    else  
    stm.Position = 0  
    result  = stm.ReadText  
    end if  
    WScript.Echo result  
    Wscript.Echo "done"  
    ```  
  
5.  <span data-ttu-id="c9f69-152">Windows エクスプローラーで TestQuery.vbs ファイルをクリックして実行します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-152">Execute the TestQuery.vbs file by clicking on it in Windows Explorer.</span></span>  
  
     <span data-ttu-id="c9f69-153">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9f69-153">This is the result:</span></span>  
  
    ```  
    <root>  
      <Order OrderID="10248"/>  
      <Order OrderID="10250"/>  
      <Order OrderID="10251"/>  
      <Order OrderID="10257"/>  
      <Order OrderID="10258">  
        <orderDetail OrderID="10258"   
                     ProductID="2"   
                     Discount="0.2"   
                     Quantity="50"/>  
      </Order>  
    </root>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c9f69-154">参照</span><span class="sxs-lookup"><span data-stu-id="c9f69-154">See Also</span></span>  
 <span data-ttu-id="c9f69-155">[Transact-sql&#41;の float 型と real 型の &#40;](/sql/t-sql/data-types/float-and-real-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9f69-155">[float and real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span></span>  
 <span data-ttu-id="c9f69-156">[nchar および nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9f69-156">[nchar and nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span></span>  
 <span data-ttu-id="c9f69-157">[SQL Server Native Client のインストール](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="c9f69-157">[Installing SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="c9f69-158">クエリでの注釈付き XSD スキーマの使用 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="c9f69-158">Using Annotated XSD Schemas in Queries &#40;SQLXML 4.0&#41;</span></span>](../../relational-databases/sqlxml/annotated-xsd-schemas/using-annotated-xsd-schemas-in-queries-sqlxml-4-0.md)  
  
  
