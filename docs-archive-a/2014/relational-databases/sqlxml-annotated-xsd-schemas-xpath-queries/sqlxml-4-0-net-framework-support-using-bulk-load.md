---
title: .NET 環境での SQLXML 一括読み込みの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bd1c44a8b56bc5129aeb9843ed9ba814d45742a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738173"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a><span data-ttu-id="06d07-102">.NET 環境での SQLXML 一括読み込みの使用</span><span class="sxs-lookup"><span data-stu-id="06d07-102">Using SQLXML Bulk Load in the .NET Environment</span></span>
  <span data-ttu-id="06d07-103">ここでは、XML 一括読み込み機能を .NET 環境で使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06d07-103">This topic explains how the XML Bulk Load functionality can be used in the .NET environment.</span></span> <span data-ttu-id="06d07-104">XML 一括読み込みの詳細については、「 [Xml データの一括読み込みの実行 &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06d07-104">For detailed information about XML Bulk Load, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="06d07-105">マネージド環境から SQLXML 一括読み込み COM オブジェクトを使用するには、このオブジェクトにプロジェクト参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06d07-105">To use the SQLXML Bulk Load COM object from a managed environment, you need to add a project reference to this object.</span></span> <span data-ttu-id="06d07-106">これによって、一括読み込み COM オブジェクトのマネージド ラッパー インターフェイスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="06d07-106">This generates a managed wrapper interface around the Bulk Load COM object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06d07-107">マネージド XML 一括読み込みはマネージド ストリームでは動作せず、ネイティブ ストリームのラッパーが必要です。</span><span class="sxs-lookup"><span data-stu-id="06d07-107">Managed XML Bulk load does not work with managed streams and requires a wrapper around native streams.</span></span> <span data-ttu-id="06d07-108">SQLXML 一括読み込みコンポーネントはマルチスレッド環境 ('[MTAThread]' 属性) では動作しません。</span><span class="sxs-lookup"><span data-stu-id="06d07-108">The SQLXML Bulk Load component will not run in a multi-threaded environment ('[MTAThread]' attribute).</span></span> <span data-ttu-id="06d07-109">マルチスレッド環境で一括読み込みコンポーネントを実行しようとすると、InvalidCastException 例外が発生し、次の追加情報が表示されます。 "インターフェイス SQLXMLBULKLOADLib. がの QueryInterface に失敗しました。"</span><span class="sxs-lookup"><span data-stu-id="06d07-109">If you attempt to run the Bulk Load component in a multi-thread environment, you get an InvalidCastException exception with the following additional information: "QueryInterface for interface SQLXMLBULKLOADLib.ISQLXMLBulkLoad failed."</span></span> <span data-ttu-id="06d07-110">これを回避するには、一括読み込みオブジェクトを含むオブジェクトをシングルスレッドにアクセスできるようにします (たとえば、サンプルに示すように、[を使用する **]** を使用します)。</span><span class="sxs-lookup"><span data-stu-id="06d07-110">The workaround is to make the object that contains the Bulk Load object single-thread accessible (for example, by using the **[STAThread]** attribute as shown in the sample).</span></span>  
  
 <span data-ttu-id="06d07-111">ここでは、データベースに XML データの一括読み込みを行う、実際の C# サンプル アプリケーションを紹介します。</span><span class="sxs-lookup"><span data-stu-id="06d07-111">This topic provides a working C# sample application to bulk load XML data in the database.</span></span> <span data-ttu-id="06d07-112">実際のサンプルを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="06d07-112">To create a working sample, follow these steps:</span></span>  
  
1.  <span data-ttu-id="06d07-113">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="06d07-113">Create the following tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  <span data-ttu-id="06d07-114">次のスキーマをファイル schema.xml に保存します。</span><span class="sxs-lookup"><span data-stu-id="06d07-114">Save the following schema in a file (schema.xml):</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="06d07-115">次のサンプル XML ドキュメントをファイル data.xml に保存します。</span><span class="sxs-lookup"><span data-stu-id="06d07-115">Save the following sample XML document in a file (data.xml):</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="06d07-116">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="06d07-116">Start Visual Studio.</span></span>  
  
5.  <span data-ttu-id="06d07-117">C# コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="06d07-117">Create a C# console application.</span></span>  
  
6.  <span data-ttu-id="06d07-118">[**プロジェクト**] メニューの [**参照の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06d07-118">From the **Project** menu, select **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="06d07-119">[ **COM** ] タブで、[ **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll)] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06d07-119">In the **COM** tab, select **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll) and click **OK**.</span></span> <span data-ttu-id="06d07-120">プロジェクトで作成された**Interop. SQLXMLBULKLOADLib**アセンブリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="06d07-120">You will see the **Interop.SQLXMLBULKLOADLib** assembly created in the project.</span></span>  
  
8.  <span data-ttu-id="06d07-121">Main() メソッドを次のコードに置き換え、</span><span class="sxs-lookup"><span data-stu-id="06d07-121">Replace the Main() method with the following code.</span></span> <span data-ttu-id="06d07-122">**ConnectionString**プロパティと、スキーマファイルとデータファイルへのファイルパスを更新します。</span><span class="sxs-lookup"><span data-stu-id="06d07-122">Update the **ConnectionString** property and the file path to the schema and data files.</span></span>  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. <span data-ttu-id="06d07-123">作成したテーブルに XML を読み込むには、プロジェクトをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="06d07-123">To load the XML in the table you created, build and run the project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="06d07-124">.NET Framework で提供される tlbimp.exe ツールを使用して、一括読み込みコンポーネント (xblkld4.dll) への参照を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="06d07-124">The reference to the Bulk Load component (xblkld4.dll) can also be added using the tlbimp.exe tool, which is available as part of .NET framework.</span></span> <span data-ttu-id="06d07-125">このツールでは、ネイティブ DLL (xblkld4.dll) のマネージド ラッパーが作成され、任意の .NET プロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="06d07-125">This tool creates a managed wrapper for the native DLL (xblkld4.dll), which can then be used in any .NET project.</span></span> <span data-ttu-id="06d07-126">例:</span><span class="sxs-lookup"><span data-stu-id="06d07-126">For example:</span></span>  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     <span data-ttu-id="06d07-127">この例では、.NET Framework プロジェクトで使用できるマネージド ラッパー DLL (SQLXMLBULKLOADLib.dll) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="06d07-127">This creates the managed wrapper DLL (SQLXMLBULKLOADLib.dll) that you can use in the .NET Framework project.</span></span> <span data-ttu-id="06d07-128">新しく作成した DLL へのプロジェクト参照を、.NET Framework で追加します。</span><span class="sxs-lookup"><span data-stu-id="06d07-128">In the .NET Framework, you add project reference to the newly created DLL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d07-129">参照</span><span class="sxs-lookup"><span data-stu-id="06d07-129">See Also</span></span>  
 [<span data-ttu-id="06d07-130">XML データの一括読み込みの実行 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="06d07-130">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
