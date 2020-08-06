---
title: .NET 環境での SQLXML 機能へのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], accessing SQLXML functionality
- SQLXML Managed Classes, accessing SQLXML functionality
- DiffGrams [SQLXML], accessing SQLXML functionality
- .NET Framework [SQLXML], accessing SQLXML functionality
ms.assetid: 74744535-2945-414d-9a5b-7e8cc363953a
author: rothja
ms.author: jroth
ms.openlocfilehash: a2ba0a54310833c0a1a1315aa94d78fe5650d480
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641552"
---
# <a name="accessing-sqlxml-functionality-in-the-net-environment"></a><span data-ttu-id="18847-102">.NET 環境での SQLXML 機能へのアクセス</span><span class="sxs-lookup"><span data-stu-id="18847-102">Accessing SQLXML Functionality in the .NET Environment</span></span>
  <span data-ttu-id="18847-103">この例では、以下が示されています。</span><span class="sxs-lookup"><span data-stu-id="18847-103">This example shows:</span></span>  
  
-   <span data-ttu-id="18847-104">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]SQLXML マネージクラス (microsoft. Data. sqlxml) を使用し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] て、.NET Framework 環境で microsoft にアクセスする方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="18847-104">How to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML Managed Classes (Microsoft.Data.SqlXml) to access Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment.</span></span>  
  
-   <span data-ttu-id="18847-105">.NET Framework 環境で生成された DiffGram を使って [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルにデータ更新を適用する方法</span><span class="sxs-lookup"><span data-stu-id="18847-105">How DiffGrams that are generated in the .NET Framework environment can apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="18847-106">このアプリケーションでは、XSD スキーマに対して XPath クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="18847-106">In this application, an XPath query is executed against an XSD schema.</span></span> <span data-ttu-id="18847-107">XPath クエリを実行すると、連絡先データ (**FirstName**、 **LastName**) で構成される XML ドキュメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="18847-107">The execution of the XPath query returns an XML document that consists of contact data (**FirstName**, **LastName**).</span></span> <span data-ttu-id="18847-108">アプリケーションでは、.NET Framework 環境でこの XML ドキュメントをデータセットに読み込み、</span><span class="sxs-lookup"><span data-stu-id="18847-108">The application loads the XML document in the dataset in the .NET Framework environment.</span></span> <span data-ttu-id="18847-109">データセットの最初の連絡先の名前を "Susan" に変更します。</span><span class="sxs-lookup"><span data-stu-id="18847-109">The data in the dataset is modified: the contact's first name is changed to "Susan" for the first contact in the dataset.</span></span> <span data-ttu-id="18847-110">このデータセットから DiffGram を生成し、この DiffGram で指定されている更新 (従業員の名前の変更) を、Person.Contact テーブルに適用します。</span><span class="sxs-lookup"><span data-stu-id="18847-110">The DiffGram is generated from the dataset, and the update that is specified in the DiffGram (the change in the employee's first name) is then applied to the Person.Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18847-111">コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="18847-111">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      DataRow row;  
      SqlXmlAdapter ad;  
      //need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandText = "Con";  
      cmd.CommandType = SqlXmlCommandType.XPath;  
      cmd.SchemaPath = "MySchema.xml";  
      //load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      row = ds.Tables["Con"].Rows[0];  
      row["FName"] = "Susan";  
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
  
 <span data-ttu-id="18847-112">**この例をテストするには**</span><span class="sxs-lookup"><span data-stu-id="18847-112">**To test the example:**</span></span>  
  
 <span data-ttu-id="18847-113">この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="18847-113">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
1.  <span data-ttu-id="18847-114">この XSD スキーマ (MySchema.xml) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="18847-114">Save this XSD schema (MySchema.xml) in a folder:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Con" sql:relation="Person.Contact" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="FName"    
                         sql:field="FirstName"   
                         type="xsd:string" />   
            <xsd:element name="LName"    
                         sql:field="LastName"    
                         type="xsd:string" />  
         </xsd:sequence>  
         <xsd:attribute name="ContactID" type="xsd:integer" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
2.  <span data-ttu-id="18847-115">この例で提供される C# コード (DocSample.cs) を、スキーマと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="18847-115">Save the C# code (DocSample.cs) provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="18847-116">ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18847-116">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="18847-117">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="18847-117">Compile the code.</span></span> <span data-ttu-id="18847-118">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="18847-118">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="18847-119">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="18847-119">This creates an executable (DocSample.exe).</span></span>  
  
 <span data-ttu-id="18847-120">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="18847-120">At the command prompt, execute DocSample.exe.</span></span>  
  
  
