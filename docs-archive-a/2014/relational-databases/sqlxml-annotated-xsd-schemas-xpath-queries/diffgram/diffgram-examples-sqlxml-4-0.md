---
title: DiffGram の例 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], examples
- examples [SQLXML], DiffGram
- diffgr:parentID
- parentID annotation
ms.assetid: fc148583-dfd3-4efb-a413-f47b150b0975
author: rothja
ms.author: jroth
ms.openlocfilehash: 04fb355af01f9853149a84af72471375d9135468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641563"
---
# <a name="diffgram-examples-sqlxml-40"></a><span data-ttu-id="94cb0-102">DiffGram の例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="94cb0-102">DiffGram Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="94cb0-103">ここでは、データベースに対して挿入、変更、および削除の各操作を実行する DiffGram の例を示します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-103">The examples in this topic consist of DiffGrams that perform insert, update, and delete operations to the database.</span></span> <span data-ttu-id="94cb0-104">例を使用する前に、次のことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-104">Before using the examples, note the following:</span></span>  
  
-   <span data-ttu-id="94cb0-105">例では、2 つのテーブル (Cust と Ord) を使用します。したがって、DiffGram の例をテストするにはこれらを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94cb0-105">The examples use two tables (Cust and Ord) that must be created if you want to test the DiffGram examples:</span></span>  
  
    ```  
    Cust(CustomerID, CompanyName, ContactName)  
    Ord(OrderID, CustomerID)  
    ```  
  
-   <span data-ttu-id="94cb0-106">ほとんどの例では、次の XSD スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-106">Most of the examples in this topic use the following XSD Schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
    <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
    <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
    </xsd:element>  
  
    </xsd:schema>     
    ```  
  
     <span data-ttu-id="94cb0-107">このスキーマを、例で使用する他のファイルと同じフォルダーに DiffGramSchema.xml として保存してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-107">Save this schema as DiffGramSchema.xml in the same folder where you save other files used in the examples.</span></span>  
  
## <a name="a-deleting-a-record-by-using-a-diffgram"></a><span data-ttu-id="94cb0-108">A.</span><span class="sxs-lookup"><span data-stu-id="94cb0-108">A.</span></span> <span data-ttu-id="94cb0-109">DiffGram を使用してレコードを削除する</span><span class="sxs-lookup"><span data-stu-id="94cb0-109">Deleting a record by using a DiffGram</span></span>  
 <span data-ttu-id="94cb0-110">この例の DiffGram では、CustomerID が ALFKI の顧客レコードを Cust テーブルから削除し、OrderID が 1 の、対応する注文レコードを Ord テーブルから削除します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-110">The DiffGram in this example deletes a customer (whose CustomerID is ALFKI) record from the Cust table and deletes the corresponding order record (whose OrderID is 1) from the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance/>  
  
    <diffgr:before>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI"   
               OrderID="1"/>  
        <Customer diffgr:id="Customer1"   
                  msdata:rowOrder="0"   
                  CustomerID="ALFKI">  
           <CompanyName>Alfreds Futterkiste</CompanyName>  
           <ContactName>Maria Anders</ContactName>  
        </Customer>  
    </diffgr:before>  
    <msdata:errors/>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="94cb0-111">ブロックに **\<before>** は、 **\<Order>** 要素 (**Order1: Id = ""**) と **\<Customer>** 要素 (**"Customer1"** という) があります。</span><span class="sxs-lookup"><span data-stu-id="94cb0-111">In the **\<before>** block, there is an **\<Order>** element (**diffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="94cb0-112">これらの要素はデータベースの既存のレコードを表します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-112">These elements represent existing records in the database.</span></span> <span data-ttu-id="94cb0-113">要素には、 **\<DataInstance>** 対応するレコードがありません (同一の場合 **: id**)。</span><span class="sxs-lookup"><span data-stu-id="94cb0-113">The **\<DataInstance>** element does not have the corresponding records (with the same **diffgr:id**).</span></span> <span data-ttu-id="94cb0-114">これは削除操作を表します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-114">This indicates a delete operation.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="94cb0-115">DiffGram をテストするには</span><span class="sxs-lookup"><span data-stu-id="94cb0-115">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="94cb0-116">これらのテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-116">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="94cb0-117">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-117">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="94cb0-118">上の DiffGram をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-118">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="94cb0-119">前の手順と同じフォルダーに MyDiffGram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-119">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="94cb0-120">前で提供されている DiffGramSchema をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-120">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="94cb0-121">DiffGramSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-121">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="94cb0-122">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用して DiffGram を実行します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-122">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="94cb0-123">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-123">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="b-inserting-a-record-by-using-a-diffgram"></a><span data-ttu-id="94cb0-124">B.</span><span class="sxs-lookup"><span data-stu-id="94cb0-124">B.</span></span> <span data-ttu-id="94cb0-125">DiffGram を使用してレコードを挿入する</span><span class="sxs-lookup"><span data-stu-id="94cb0-125">Inserting a record by using a DiffGram</span></span>  
 <span data-ttu-id="94cb0-126">この例の DiffGram では、Cust テーブルと Ord テーブルにレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-126">In this example, the DiffGram inserts a record in the Cust table and a record in the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"   
      sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
          xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
          xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
       <Customer diffgr:id="Customer1" msdata:rowOrder="0"    
                 diffgr:hasChanges="inserted" CustomerID="ALFKI">  
        <CompanyName>C3Company</CompanyName>  
        <ContactName>C3Contact</ContactName>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"  
               diffgr:hasChanges="inserted"   
               CustomerID="ALFKI" OrderID="1"/>  
      </Customer>  
    </DataInstance>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="94cb0-127">この DiffGram で **\<before>** は、ブロックが指定されていません (既存のデータベースレコードが指定されていません)。</span><span class="sxs-lookup"><span data-stu-id="94cb0-127">In this DiffGram the **\<before>** block is not specified (no existing database records identified).</span></span> <span data-ttu-id="94cb0-128">**\<Customer>** **\<Order>** **\<DataInstance>** Cust テーブルと Ord テーブルにマップされる2つのレコードインスタンス (ブロック内の要素と要素によって識別される) があります。</span><span class="sxs-lookup"><span data-stu-id="94cb0-128">There are two record instances (identified by the **\<Customer>** and **\<Order>** elements in the **\<DataInstance>** block) that map to Cust and Ord tables, respectively.</span></span> <span data-ttu-id="94cb0-129">これらの要素はどちらも **、** "属性の変更" 属性 (**haschanges = "inserted"**) を指定します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-129">Both of these elements specify the **diffgr:hasChanges** attribute (**hasChanges="inserted"**).</span></span> <span data-ttu-id="94cb0-130">これは挿入操作を表します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-130">This indicates an insert operation.</span></span> <span data-ttu-id="94cb0-131">この DiffGram では、 **Haschanges = "modified"** を指定した場合、存在しないレコードを変更しようとするとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="94cb0-131">In this DiffGram, if you specify **hasChanges="modified"**, you are indicating that you want to modify a record that does not exist, which results in an error.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="94cb0-132">DiffGram をテストするには</span><span class="sxs-lookup"><span data-stu-id="94cb0-132">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="94cb0-133">これらのテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-133">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="94cb0-134">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-134">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="94cb0-135">上の DiffGram をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-135">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="94cb0-136">前の手順と同じフォルダーに MyDiffGram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-136">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="94cb0-137">前で提供されている DiffGramSchema をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-137">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="94cb0-138">DiffGramSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-138">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="94cb0-139">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用して DiffGram を実行します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-139">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="94cb0-140">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-140">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="c-updating-an-existing-record-by-using-a-diffgram"></a><span data-ttu-id="94cb0-141">C.</span><span class="sxs-lookup"><span data-stu-id="94cb0-141">C.</span></span> <span data-ttu-id="94cb0-142">DiffGram を使用して既存のレコードを更新する</span><span class="sxs-lookup"><span data-stu-id="94cb0-142">Updating an existing record by using a DiffGram</span></span>  
 <span data-ttu-id="94cb0-143">この例では、DiffGram で顧客 ALFKI の顧客情報 (CompanyName と ContactName) を更新します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-143">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="94cb0-144">ブロックには **\<before>** 要素が含まれてい **\<Customer>** ます (**diffgram: Id = "Customer1"**)。</span><span class="sxs-lookup"><span data-stu-id="94cb0-144">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="94cb0-145">ブロックには、 **\<DataInstance>** **\<Customer>** 同じ**id**を持つ対応する要素が含まれています。**\<customer>** また、の要素は、 **\<NewDataSet>** **"変更前" と "変更**された" というように指定します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-145">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="94cb0-146">これは更新操作であることを示し、 **Cust**テーブルの顧客レコードがそれに応じて更新されます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-146">This indicates an update operation, and the customer record in the **Cust** table is updated accordingly.</span></span> <span data-ttu-id="94cb0-147">DiffGram **: hasChanges**属性が指定されていない場合、diffgram 処理ロジックはこの要素を無視し、更新は実行されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-147">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="94cb0-148">DiffGram をテストするには</span><span class="sxs-lookup"><span data-stu-id="94cb0-148">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="94cb0-149">これらのテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-149">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="94cb0-150">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-150">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="94cb0-151">上の DiffGram をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-151">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="94cb0-152">前の手順と同じフォルダーに MyDiffGram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-152">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="94cb0-153">前で提供されている DiffGramSchema をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-153">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="94cb0-154">DiffGramSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-154">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="94cb0-155">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用して DiffGram を実行します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-155">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="94cb0-156">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-156">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="d-inserting-updating-and-deleting-records-by-using-a-diffgram"></a><span data-ttu-id="94cb0-157">D.</span><span class="sxs-lookup"><span data-stu-id="94cb0-157">D.</span></span> <span data-ttu-id="94cb0-158">DiffGram を使用して、レコードの挿入、更新、および削除を実行する</span><span class="sxs-lookup"><span data-stu-id="94cb0-158">Inserting, updating, and deleting records by using a DiffGram</span></span>  
 <span data-ttu-id="94cb0-159">この例では、比較的複雑な DiffGram を使用して、挿入、更新、および削除操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-159">In this example, a relatively complex DiffGram is used to perform insert, update, and delete operations.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                diffgr:hasChanges="modified"   
                CustomerID="ANATR">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Elizabeth Lincoln</ContactName>  
          <Order diffgr:id="Order2" msdata:rowOrder="1"   
               msdata:hiddenCustomerID="ANATR"   
               CustomerID="ANATR" OrderID="2"/>  
      </Customer>  
  
      <Customer diffgr:id="Customer3" msdata:rowOrder="2"   
                CustomerID="ANTON">  
         <CompanyName>Chop-suey Chinese</CompanyName>  
         <ContactName>Yang Wang</ContactName>  
         <Order diffgr:id="Order3" msdata:rowOrder="2"   
               msdata:hiddenCustomerID="ANTON"   
               CustomerID="ANTON" OrderID="3"/>  
      </Customer>  
      <Customer diffgr:id="Customer4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                CustomerID="AROUT">  
         <CompanyName>Around the Horn</CompanyName>  
         <ContactName>Thomas Hardy</ContactName>  
         <Order diffgr:id="Order4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                msdata:hiddenCustomerID="AROUT"   
               CustomerID="AROUT" OrderID="4"/>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
      <Order diffgr:id="Order1" msdata:rowOrder="0"   
             msdata:hiddenCustomerID="ALFKI"   
             CustomerID="ALFKI" OrderID="1"/>  
      <Customer diffgr:id="Customer1" msdata:rowOrder="0"   
                CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                CustomerID="ANATR">  
        <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
        <ContactName>Ana Trujillo</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="94cb0-160">この DiffGram は、DiffGram のロジックにより次のように処理されます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-160">The DiffGram logic processes this DiffGram as follows:</span></span>  
  
-   <span data-ttu-id="94cb0-161">DiffGram 処理ロジックに従って、ブロック内の最上位レベルのすべての要素は、 **\<before>** マッピングスキーマで説明されているように、対応するテーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-161">In accordance with DiffGram processing logic, all the top-level elements in the **\<before>** block map to corresponding tables, as described in the mapping schema.</span></span>  
  
-   <span data-ttu-id="94cb0-162">**\<before>** ブロックには、 **\<Order>** 要素 (**dffgr: Id = "Order1"**) と、( **\<Customer>** 同じ id を持つ) ブロック内に対応する要素が存在しない要素 (**: id = "Customer1"**) があり **\<DataInstance>** ます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-162">The **\<before>** block has an **\<Order>** element (**dffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**) for which there is no corresponding element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="94cb0-163">これは削除操作を表し、レコードは Cust テーブルと Ord テーブルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-163">This indicates a delete operation, and the records are deleted from the Cust and Ord tables.</span></span>  
  
-   <span data-ttu-id="94cb0-164">ブロックには、 **\<before>** **\<Customer>** (同じ id を持つ) ブロック内に対応する要素が存在する要素 (**diffgram gr: Id = "Customer2"**) があり **\<Customer>** **\<DataInstance>** ます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-164">The **\<before>** block has a **\<Customer>** element (**diffgr:id="Customer2"**) for which there is a corresponding **\<Customer>** element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="94cb0-165">ブロック内の要素は、次のように指定されて **\<DataInstance>** います **: haschanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="94cb0-165">The element in the **\<DataInstance>** block specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="94cb0-166">これは更新操作であり、顧客 ANATR に対して、ブロックで指定された値を使用して、Cust テーブルの CompanyName および担当する情報が更新されます **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="94cb0-166">This is an update operation in which for customer ANATR, the CompanyName and ContactName information is updated in the Cust table using values that are specified in the **\<DataInstance>** block.</span></span>  
  
-   <span data-ttu-id="94cb0-167">**\<DataInstance>** ブロックには **\<Customer>** 要素 (**diffgram: Id = "Customer3"**) と **\<Order>** 要素 (**Order3: id = ""**) があります。</span><span class="sxs-lookup"><span data-stu-id="94cb0-167">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer3"**) and an **\<Order>** element (**diffgr:id="Order3"**).</span></span> <span data-ttu-id="94cb0-168">これらの要素のどちらにも、 **diffgram: hasChanges**属性が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="94cb0-168">Neither of these elements specify the **diffgr:hasChanges** attribute.</span></span> <span data-ttu-id="94cb0-169">このため、DiffGram の処理ロジックで、これらの要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-169">Therefore, the DiffGram processing logic ignores these elements.</span></span>  
  
-   <span data-ttu-id="94cb0-170">**\<DataInstance>** ブロックには、 **\<Customer>** 要素 (Order4 **: Id = "Customer4"**) と、 **\<Order>** 対応する要素がブロック内に存在しない要素 (**: id = ""**) があり \<before> ます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-170">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer4"**) and an **\<Order>** element (**diffgr:id="Order4"**) for which there are no corresponding elements in the \<before> block.</span></span> <span data-ttu-id="94cb0-171">ブロック内のこれらの要素は、次のように **\<DataInstance>** 指定します。 **haschanges = "inserted"**。</span><span class="sxs-lookup"><span data-stu-id="94cb0-171">These elements in the **\<DataInstance>** block specify **diffgr:hasChanges="inserted"**.</span></span> <span data-ttu-id="94cb0-172">このため、新しいレコードが Cust テーブルと Ord テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-172">Therefore, a new record is added in the Cust table and in the Ord table.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="94cb0-173">DiffGram をテストするには</span><span class="sxs-lookup"><span data-stu-id="94cb0-173">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="94cb0-174">次のテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-174">Create the following tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="94cb0-175">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-175">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="94cb0-176">上の DiffGram をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-176">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="94cb0-177">前の手順と同じフォルダーに MyDiffGram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-177">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="94cb0-178">前で提供されている DiffGramSchema をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="94cb0-178">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="94cb0-179">DiffGramSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-179">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="94cb0-180">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用して DiffGram を実行します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-180">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="94cb0-181">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94cb0-181">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="e-applying-updates-by-using-a-diffgram-with-the-diffgrparentid-annotation"></a><span data-ttu-id="94cb0-182">E.</span><span class="sxs-lookup"><span data-stu-id="94cb0-182">E.</span></span> <span data-ttu-id="94cb0-183">DiffGram で diffgr:parentID 注釈を指定して更新を適用する</span><span class="sxs-lookup"><span data-stu-id="94cb0-183">Applying updates by using a DiffGram with the diffgr:parentID annotation</span></span>  
 <span data-ttu-id="94cb0-184">この例では、DiffGram のブロックで指定されている**parentID**注釈を使用して更新プログラムを適用する方法を示し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-184">This example illustrates how the **parentID** annotation that is specified in the **\<before>** block of the DiffGram is used in applying the updates.</span></span>  
  
```  
<NewDataSet />  
<diffgr:before>  
   <Order diffgr:id="Order1" msdata:rowOrder="0" OrderID="2" />  
   <Order diffgr:id="Order3" msdata:rowOrder="2" OrderID="4" />  
  
   <OrderDetail diffgr:id="OrderDetail1"   
                diffgr:parentId="Order1"   
                msdata:rowOrder="0"   
                ProductID="13"   
                OrderID="2" />  
   <OrderDetail diffgr:id="OrderDetail3"   
                diffgr:parentId="Order3"  
                ProductID="77"  
                OrderID="4"/>  
</diffgr:before>  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="94cb0-185">この DiffGram は、ブロックが1つしかないため、削除操作を指定し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-185">This DiffGram specifies a delete operation because there is only a **\<before>** block.</span></span> <span data-ttu-id="94cb0-186">DiffGram では、 **parentID**注釈を使用して、注文と注文の詳細の間に親子リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="94cb0-186">In the DiffGram, the **parentID** annotation is used to specify a parent-child relationship between the orders and order details.</span></span> <span data-ttu-id="94cb0-187">SQLXML でレコードが削除されるときには、このリレーションシップで指定された子テーブルからレコードが削除された後、対応する親テーブルからレコードが削除されます。</span><span class="sxs-lookup"><span data-stu-id="94cb0-187">When SQLXML deletes the records, it deletes records from the child table that is identified by this relationship and then deletes the records from the corresponding parent table.</span></span>  
  
  
