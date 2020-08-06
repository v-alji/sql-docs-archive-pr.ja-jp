---
title: SQLXML マネージクラスを使用した DiffGram の実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: rothja
ms.author: jroth
ms.openlocfilehash: f36127c37eea73a2872d4bf0aef7172a88e430a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641555"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a><span data-ttu-id="ff72e-102">SQLXML マネージド クラスを使用した、DiffGram の実行</span><span class="sxs-lookup"><span data-stu-id="ff72e-102">Executing a DiffGram by Using SQLXML Managed Classes</span></span>
  <span data-ttu-id="ff72e-103">この例では、.NET Framework 環境で DiffGram ファイルを実行し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] て、SQLXML マネージクラス (Microsoft. Data. SQLXML) を使用してテーブルにデータ更新を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-103">This example shows how to execute a DiffGram file in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment to apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables using SQLXML Managed Classes (Microsoft.Data.SqlXml).</span></span>  
  
 <span data-ttu-id="ff72e-104">この例では、DiffGram で顧客 ALFKI の顧客情報 (CompanyName と ContactName) を更新します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-104">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
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
  
 <span data-ttu-id="ff72e-105">ブロックには **\<before>** 要素が含まれてい **\<Customer>** ます (**diffgram: Id = "Customer1"**)。</span><span class="sxs-lookup"><span data-stu-id="ff72e-105">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="ff72e-106">ブロックには、 **\<DataInstance>** **\<Customer>** 同じ**id**を持つ対応する要素が含まれています。**\<customer>** また、の要素は、 **\<NewDataSet>** **"変更前" と "変更**された" というように指定します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-106">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="ff72e-107">これは更新操作であることを示し、Cust テーブルの顧客レコードは指定に従って更新されます。</span><span class="sxs-lookup"><span data-stu-id="ff72e-107">This indicates an update operation, and the customer record in the Cust table is updated accordingly.</span></span> <span data-ttu-id="ff72e-108">DiffGram **: hasChanges**属性が指定されていない場合、diffgram 処理ロジックはこの要素を無視し、更新は実行されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff72e-108">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
 <span data-ttu-id="ff72e-109">次に示すのは、SQLXML マネージクラスを使用して上記の DiffGram を実行し、2つのテーブル (Cust、Ord) を更新して**tempdb**データベースに作成する方法を示す C# チュートリアルアプリケーションのコードです。</span><span class="sxs-lookup"><span data-stu-id="ff72e-109">The following is code for a C# tutorial application that shows how to use the SQLXML Managed Classes to execute the above DiffGram and update two tables (Cust, Ord) you will also create in the **tempdb** database.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="ff72e-110">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="ff72e-110">To test the application</span></span>  
  
1.  <span data-ttu-id="ff72e-111">.NET Framework がコンピューターにインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-111">Ensure that the .NET Framework is installed on your computer.</span></span>  
  
2.  <span data-ttu-id="ff72e-112">次の XSD スキーマ (DiffGramSchema.xml) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-112">Save the following XSD schema (DiffGramSchema.xml) in a folder:</span></span>  
  
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
  
3.  <span data-ttu-id="ff72e-113">これらのテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-113">Create these tables in the **tempdb** database.</span></span>  
  
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
  
4.  <span data-ttu-id="ff72e-114">次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-114">Add this sample data:</span></span>  
  
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
  
5.  <span data-ttu-id="ff72e-115">上の DiffGram をコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="ff72e-115">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="ff72e-116">手順 1. と同じフォルダーに MyDiffGram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-116">Save the file as MyDiffGram.xml in the same folder used in step 1.</span></span>  
  
6.  <span data-ttu-id="ff72e-117">上の C# コード (DiffgramSample.cs) を、上の手順で DiffGramSchema.xml と MyDiffGram.xml を保存したフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-117">Save the C# code (DiffgramSample.cs) that is provided above in the same folder in which the DiffGramSchema.xml and MyDiffGram.xml were stored in previous steps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ff72e-118">接続文字列の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前は、'`MyServer`' の部分を、インストールされている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの実際の名前に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff72e-118">You will need to update the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the connection string from '`MyServer`' to the actual name of your installed instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="ff72e-119">ファイルを別のフォルダーに保存する場合は、コードを編集し、マッピングスキーマの適切なディレクトリパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff72e-119">If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.</span></span>  
  
7.  <span data-ttu-id="ff72e-120">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ff72e-120">Compile the code.</span></span> <span data-ttu-id="ff72e-121">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-121">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     <span data-ttu-id="ff72e-122">これにより、実行可能ファイル (DiffgramSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff72e-122">This creates an executable (DiffgramSample.exe).</span></span>  
  
8.  <span data-ttu-id="ff72e-123">コマンド プロンプトで、DiffgramSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="ff72e-123">At the command prompt, execute DiffgramSample.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff72e-124">参照</span><span class="sxs-lookup"><span data-stu-id="ff72e-124">See Also</span></span>  
 [<span data-ttu-id="ff72e-125">&#40;SQLXML 4.0&#41;の DiffGram の例</span><span class="sxs-lookup"><span data-stu-id="ff72e-125">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
  
  
