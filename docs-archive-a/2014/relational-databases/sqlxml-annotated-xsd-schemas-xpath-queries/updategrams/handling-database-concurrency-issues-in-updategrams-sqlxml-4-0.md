---
title: アップデートグラムでのデータベースの同時実行に関する問題の処理 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <before> block
- low concurrency protection
- database concurrency [SQLXML]
- timestamp column [SQLXML]
- updategrams [SQLXML], database concurrency
- high concurrency protection [SQLXML]
- optimistic concurrency control
- concurrency [SQLXML]
- intermediate concurrency protection [SQLXML]
ms.assetid: d4b908d1-b25b-4ad9-8478-9cd882e8c44e
author: rothja
ms.author: jroth
ms.openlocfilehash: dd808b2688e8bf05149a5454bee91123878fb2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642709"
---
# <a name="handling-database-concurrency-issues-in-updategrams-sqlxml-40"></a><span data-ttu-id="0dfde-102">アップデートグラムでのデータベース コンカレンシーに関する問題への対応 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0dfde-102">Handling Database Concurrency Issues in Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="0dfde-103">アップデートグラムは、他のデータベースの更新メカニズムと同様に、マルチサーバー環境での同時実行更新に対応しています。</span><span class="sxs-lookup"><span data-stu-id="0dfde-103">Like other database update mechanisms, updategrams must deal with concurrent updates to data in a multiuser environment.</span></span> <span data-ttu-id="0dfde-104">アップデートグラムではオプティミスティック コンカレンシーが使用されます。この機能では、更新するデータがデータベースからの読み取り後に他のユーザー アプリケーションによって変更され邸内事を確認するために、選択フィールド データの比較がスナップショットとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-104">Updategrams use the Optimistic Concurrency Control, which uses comparison of select field data as snapshots to ensure that the data to be updated has not been altered by another user application since it was read from the database.</span></span> <span data-ttu-id="0dfde-105">アップデートグラムには、これらのスナップショット値が **\<before>** アップデートグラムのブロックに含まれています。</span><span class="sxs-lookup"><span data-stu-id="0dfde-105">Updategrams include these snapshot values in the **\<before>** block of the updategrams.</span></span> <span data-ttu-id="0dfde-106">更新プログラムが有効であることを確認するには、データベースを更新する前に、ブロックに指定されている値がデータベース内の現在の値と照合されることを確認し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-106">Before updating the database, the updategram checks the values that are specified in the **\<before>** block against the values currently in the database to ensure that the update is valid.</span></span>  
  
 <span data-ttu-id="0dfde-107">アップデートグラムでは、オプティミスティック コンカレンシーによる保護を低 (なし)、中、高の 3 レベルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-107">The Optimistic Concurrency Control offers three levels of protection in an updategram: low (none), intermediate, and high.</span></span> <span data-ttu-id="0dfde-108">必要な保護レベルを適用するには、アップデートグラムで適切に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0dfde-108">You can decide what level of protection you need by specifying the updategram accordingly.</span></span>  
  
## <a name="lowest-level-of-protection"></a><span data-ttu-id="0dfde-109">最低レベルの保護</span><span class="sxs-lookup"><span data-stu-id="0dfde-109">Lowest Level of Protection</span></span>  
 <span data-ttu-id="0dfde-110">このレベルでは、最後のデータベースの読み取り後に行われたその他の更新を無視して更新操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-110">This level is a blind update, in which the update is processed without reference to other updates that have been made since the database was last read.</span></span> <span data-ttu-id="0dfde-111">このような場合、レコードを識別するためにブロック内の主キー列のみを指定 **\<before>** し、ブロック内の更新された情報を指定し **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-111">In such a case, you specify only the primary key column(s) in the **\<before>** block to identify the record, and you specify the updated information in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="0dfde-112">たとえば次のアップデートグラムでは、以前の電話番号に関係なく、新しい連絡先の電話番号として正しい番号を設定できます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-112">For example, the new contact phone number in the following updategram is correct, regardless of what the phone number was previously.</span></span> <span data-ttu-id="0dfde-113">**\<before>** ブロックで主キー列 (ContactID) のみが指定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0dfde-113">Notice how the **\<before>** block specifies only the primary key column (ContactID).</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="intermediate-level-of-protection"></a><span data-ttu-id="0dfde-114">中レベルの保護</span><span class="sxs-lookup"><span data-stu-id="0dfde-114">Intermediate Level of Protection</span></span>  
 <span data-ttu-id="0dfde-115">この保護レベルでは、トランザクションで読み取ったレコードが他のトランザクションによって変更されていないことを確認するため、アップデートグラムにおいて、更新するデータの現在の値とデータベース列の値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-115">In this level of protection, the updategram compares the current value(s) of the data being updated with the value(s) in the database column(s) to ensure that the values have not been changed by some other transaction since the record was read by your transaction.</span></span>  
  
 <span data-ttu-id="0dfde-116">このレベルの保護を実現するには、ブロックで更新する主キー列と列を指定します (複数可) **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="0dfde-116">You can get this level of protection by specifying the primary key column(s) and the column(s) that you are updating in the **\<before>** block.</span></span>  
  
 <span data-ttu-id="0dfde-117">たとえば、このアップデートグラムでは、Person.Contact テーブルで、ContactID が 1 となっている連絡先の Phone 列の値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-117">For example, this updategram changes the value in the Phone column of the Person.Contact table for the contact with ContactID of 1.</span></span> <span data-ttu-id="0dfde-118">ブロックでは、 **\<before>** 更新された値を適用する前に、この属性値がデータベース内の対応する列の値と一致するように、 **Phone**属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-118">The **\<before>** block specifies the **Phone** attribute to ensure that this attribute value matches the value in the corresponding column in the database before applying the updated value.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" Phone="398-555-0132" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="high-level-of-protection"></a><span data-ttu-id="0dfde-119">高レベルの保護</span><span class="sxs-lookup"><span data-stu-id="0dfde-119">High Level of Protection</span></span>  
 <span data-ttu-id="0dfde-120">高レベルの保護では、アプリケーションで最後に読み取ったレコードが変化していない (他のトランザクションによって変更されていない) ことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-120">A high level of protection ensures that the record remains the same since your application last read that record (that is, since your application has read the record, it has not been changed by any other transaction).</span></span>  
  
 <span data-ttu-id="0dfde-121">同時実行更新に高レベルの保護を適用するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="0dfde-121">There are two ways you can get this high level of protection against concurrent updates:</span></span>  
  
-   <span data-ttu-id="0dfde-122">ブロック内のテーブルに追加の列を指定し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-122">Specify additional columns in the table in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="0dfde-123">ブロックに追加の列を指定した場合 **\<before>** 、アップデートグラムでは、更新プログラムを適用する前に、これらの列に指定されている値と、データベース内の値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-123">If you specify additional columns in the **\<before>** block, the updategram compares the values that are specified for these columns with the values that were in the database before applying the update.</span></span> <span data-ttu-id="0dfde-124">トランザクションで読み取ったレコード列のいずれかが変更されている場合、アップデートグラムで更新は実行されません。</span><span class="sxs-lookup"><span data-stu-id="0dfde-124">If any of the record columns has changed since your transaction read the record, the updategram does not perform the update.</span></span>  
  
     <span data-ttu-id="0dfde-125">たとえば、次のアップデートグラムでは、シフト名を更新しますが、ブロック内に追加の列 (StartTime、EndTime) を指定するため、 **\<before>** 同時更新に対するより高いレベルの保護が要求されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-125">For example, the following updategram updates the shift name, but specifies additional columns (StartTime,EndTime) in the **\<before>** block, thereby requesting a higher level of protection against concurrent updates.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1"   
                 Name="Day"   
                 StartTime="1900-01-01 07:00:00.000"   
                 EndTime="1900-01-01 15:00:00.000" />  
    </updg:before>  
    <updg:after>  
       <HumanResources.Shift Name="Morning" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0dfde-126">この例では、ブロック内のレコードのすべての列の値を指定することによって、最も高いレベルの保護を指定し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-126">This example specifies the highest level of protection by specifying all column values for the record in the **\<before>** block.</span></span>  
  
-   <span data-ttu-id="0dfde-127">ブロック内のタイムスタンプ列 (使用可能な場合) を指定し **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-127">Specify the timestamp column (if available) in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="0dfde-128">> ブロック内のすべてのレコード列を指定する代わりに、 `<before` timestamp 列 (テーブルにテーブルがある場合) と、ブロック内の主キー列を指定するだけで済み **\<before>** ます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-128">Instead of specifying all the record columns in the `<before`> block, you can just specify the timestamp column (if the table has one) along with the primary key column(s) in the **\<before>** block.</span></span> <span data-ttu-id="0dfde-129">データベースでは、レコードが更新されるたびにタイムスタンプ列が一意な値に更新されます。</span><span class="sxs-lookup"><span data-stu-id="0dfde-129">The database updates the timestamp column to a unique value after each update of the record.</span></span> <span data-ttu-id="0dfde-130">この場合、アップデートグラムではタイムスタンプの値とデータベースの対応する値を比較します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-130">In this case, the updategram compares the value of the timestamp with the corresponding value in the database.</span></span> <span data-ttu-id="0dfde-131">データベースに格納されているタイムスタンプ値はバイナリ値です。</span><span class="sxs-lookup"><span data-stu-id="0dfde-131">The timestamp value stored in the database is a binary value.</span></span> <span data-ttu-id="0dfde-132">したがって、スキーマ内にタイムスタンプ列を `dt:type="bin.hex"`、`dt:type="bin.base64"`、または `sql:datatype="timestamp"` のように指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0dfde-132">Therefore, the timestamp column must be specified in the schema as `dt:type="bin.hex"`, `dt:type="bin.base64"`, or `sql:datatype="timestamp"`.</span></span> <span data-ttu-id="0dfde-133">( `xml` データ型またはデータ型のいずれかを指定でき [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます)。</span><span class="sxs-lookup"><span data-stu-id="0dfde-133">(You can specify either the `xml` data type or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.)</span></span>  
  
#### <a name="to-test-the-updategram"></a><span data-ttu-id="0dfde-134">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="0dfde-134">To test the updategram</span></span>  
  
1.  <span data-ttu-id="0dfde-135">**Tempdb**データベースに次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-135">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (  
                 CustomerID  varchar(5),  
                 ContactName varchar(20),  
                 LastUpdated timestamp)  
    ```  
  
2.  <span data-ttu-id="0dfde-136">次のサンプル レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-136">Add this sample record:</span></span>  
  
    ```  
    INSERT INTO Customer (CustomerID, ContactName) VALUES   
                         ('C1', 'Andrew Fuller')  
    ```  
  
3.  <span data-ttu-id="0dfde-137">次の XSD スキーマをコピーして、メモ帳に貼り付け、</span><span class="sxs-lookup"><span data-stu-id="0dfde-137">Copy the following XSD schema and paste it into Notepad.</span></span> <span data-ttu-id="0dfde-138">ConcurrencySampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-138">Save it as ConcurrencySampleSchema.xml:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Customer" sql:relation="Customer" >  
       <xsd:complexType>  
            <xsd:attribute name="CustomerID"    
                           sql:field="CustomerID"   
                           type="xsd:string" />   
  
            <xsd:attribute name="ContactName"    
                           sql:field="ContactName"   
                           type="xsd:string" />  
  
            <xsd:attribute name="LastUpdated"   
                           sql:field="LastUpdated"   
                           type="xsd:hexBinary"   
                 sql:datatype="timestamp" />  
  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
4.  <span data-ttu-id="0dfde-139">次のアップデートグラム コードをメモ帳にコピーして、前の手順で作成したスキーマと同じディレクトリに ConcurrencySampleTemplate.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-139">Copy the following updategram code into Notepad and save it as ConcurrencySampleTemplate.xml in the same directory where you saved the schema created in the previous step.</span></span> <span data-ttu-id="0dfde-140">次の LastUpdated のタイムスタンプ値は例の Customer テーブルとは異なるため、LastUpdated の実際の値をテーブルからコピーし、アップデートグラムに貼り付けてください。</span><span class="sxs-lookup"><span data-stu-id="0dfde-140">(Note the timestamp value below for LastUpdated will differ in your example Customer table, so copy the actual value for LastUpdated from the table and paste it into the updategram.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
    <updg:before>  
       <Customer CustomerID="C1"   
                 LastUpdated = "0x00000000000007D1" />  
    </updg:before>  
    <updg:after>  
       <Customer ContactName="Robert King" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="0dfde-141">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="0dfde-141">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0dfde-142">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dfde-142">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0dfde-143">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="0dfde-143">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="ContactName" />  
    <AttributeType name="LastUpdated"  dt:type="bin.hex"   
                                       sql:datatype="timestamp" />  
    <attribute type="CustomerID" />  
    <attribute type="ContactName" />  
    <attribute type="LastUpdated" />  
</ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dfde-144">参照</span><span class="sxs-lookup"><span data-stu-id="0dfde-144">See Also</span></span>  
 [<span data-ttu-id="0dfde-145">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="0dfde-145">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
