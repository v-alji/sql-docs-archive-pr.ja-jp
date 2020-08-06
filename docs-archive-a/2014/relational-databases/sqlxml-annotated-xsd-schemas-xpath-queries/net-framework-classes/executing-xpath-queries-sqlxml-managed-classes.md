---
title: XPath クエリの実行 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- Managed Classes [SQLXML], executing XPath queries
- mapping schema [SQLXML], XPath queries
- SQLXML Managed Classes, executing XPath queries
ms.assetid: 8bef4c4d-bf0e-4236-a875-fd7d3e058396
author: rothja
ms.author: jroth
ms.openlocfilehash: d8f5fd2612a0992f18e0b7f32c749c352d29d2b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630868"
---
# <a name="executing-xpath-queries-sqlxml-managed-classes"></a><span data-ttu-id="0d0ba-102">XPath クエリの実行 (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="0d0ba-102">Executing XPath Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="0d0ba-103">この例では、マッピング スキーマに対する XPath クエリの実行方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-103">This example illustrates how XPath queries are executed against a mapping schema.</span></span>  
  
 <span data-ttu-id="0d0ba-104">次のスキーマについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-104">Consider this schema:</span></span>  
  
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
  
 <span data-ttu-id="0d0ba-105">この C# アプリケーションでは、このスキーマ (MySchema.xml) に対して XPath クエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-105">This C# application executes an XPath query against this schema (MySchema.xml).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d0ba-106">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-106">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
  
      public static int testXPath()  
      {  
         Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "Con";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.SchemaPath = "MySchema.xml";  
         strm = cmd.ExecuteStream();  
         using (StreamReader sr = new StreamReader(strm)){  
            Console.WriteLine(sr.ReadToEnd());  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="0d0ba-107">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="0d0ba-107">To test the application</span></span>  
  
1.  <span data-ttu-id="0d0ba-108">コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-108">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="0d0ba-109">この例で提供される XSD スキーマ (MySchema.xml) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-109">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="0d0ba-110">この例で提供されている C# コード (DocSample.cs) を、スキーマが格納されているのと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-110">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="0d0ba-111">ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-111">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="0d0ba-112">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-112">Compile the code.</span></span> <span data-ttu-id="0d0ba-113">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-113">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="0d0ba-114">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-114">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="0d0ba-115">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="0d0ba-115">At the command prompt, execute DocSample.exe.</span></span>  
  
  
