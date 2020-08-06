---
title: XSL 変換の適用 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- applying XSL transformations [SQLXML]
- Managed Classes [SQLXML], applying XSL transformations
- SQLXML Managed Classes, applying XSL transformations
- XSL Transformations [SQLXML]
ms.assetid: 8562043b-3e9f-41a3-bb41-92b9f14363c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d3225d838db284e2a34ebd41edb109400d0b72f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641539"
---
# <a name="applying-an-xsl-transformation-sqlxml-managed-classes"></a><span data-ttu-id="825f6-102">XSL 変換の適用 (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="825f6-102">Applying an XSL Transformation (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="825f6-103">この例では、AdventureWorks データベースに対して SQL クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="825f6-103">In this example, an SQL query is executed against the AdventureWorks database.</span></span> <span data-ttu-id="825f6-104">クエリ結果には XSL 変換が適用され、従業員の名前と姓を示す 2 列のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="825f6-104">The XSL transformation is applied to the query result to generate a two-column table of the employees' first and last names.</span></span>  
  
 <span data-ttu-id="825f6-105">SqlXmlCommand オブジェクトの XslPath プロパティは、XSL ファイルとそのディレクトリパスを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="825f6-105">The XslPath property of the SqlXmlCommand object is used to specify the XSL file and its directory path.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="825f6-106">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="825f6-106">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXSL()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "SELECT TOP 20 FirstName, LastName FROM Person.Contact FOR XML AUTO";  
         cmd.XslPath = "MyXSL.xsl";  
         cmd.RootTag = "root";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
        }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXSL();     
         return 0;  
      }  
   }  
```  
  
 <span data-ttu-id="825f6-107">次は、アプリケーションのテストに使用できる XSL スタイル シートです。</span><span class="sxs-lookup"><span data-stu-id="825f6-107">This is the XSL style sheet you can use to test the application:</span></span>  
  
```  
<?xml version='1.0' encoding='UTF-8'?>  
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
    <xsl:output method="html"/>  
    <xsl:template match = '*'>  
        <xsl:apply-templates />  
    </xsl:template>  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR><TH >First name</TH><TH>Last name</TH></TR>  
           <xsl:apply-templates select = 'root' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="825f6-108">この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="825f6-108">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="825f6-109">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="825f6-109">To test the application</span></span>  
  
1.  <span data-ttu-id="825f6-110">XSL スタイル シートをファイル (MyXSL.xsl) に保存します。</span><span class="sxs-lookup"><span data-stu-id="825f6-110">Save the XSL style sheet in a file (MyXSL.xsl).</span></span>  
  
2.  <span data-ttu-id="825f6-111">この例で提供される C# コード (DocSample.cs) を、スタイル シートと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="825f6-111">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the style sheet is stored.</span></span>  
  
3.  <span data-ttu-id="825f6-112">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="825f6-112">Compile the code.</span></span> <span data-ttu-id="825f6-113">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="825f6-113">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="825f6-114">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="825f6-114">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="825f6-115">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="825f6-115">At the command prompt, execute DocSample.exe.</span></span>  
  
## <a name="applying-an-xsl-transformation-in-the-net-framework"></a><span data-ttu-id="825f6-116">.NET Framework での XSL 変換の適用</span><span class="sxs-lookup"><span data-stu-id="825f6-116">Applying an XSL Transformation in the .NET Framework</span></span>  
 <span data-ttu-id="825f6-117">前で示したように中間層で XSL 変換を適用する代わりに、クライアント側 (.NET Framework) で XSL 変換を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="825f6-117">Instead of applying an XSL transformation in the middle tier, as described previously, you can apply an XSL transformation on the client side (in the .NET Framework).</span></span> <span data-ttu-id="825f6-118">次の C# コードは、.NET Framework で XSL 変換を適用するよう変更したものです。</span><span class="sxs-lookup"><span data-stu-id="825f6-118">The following revised C# code shows how the XSL transformation is applied in the .NET Framework.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="825f6-119">コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="825f6-119">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using System.Xml;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXSL()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "SELECT TOP 20 FirstName, LastName FROM Person.Contact FOR XML AUTO";  
         cmd.RootTag = "root";  
         using (Stream strm = cmd.ExecuteStream()){  
            XmlReader reader = new XmlReader(strm);  
            XPathDocument xd = new XPathDocument(reader, XmlSpace.Preserve);  
            XslCompiledTransform xslt = new XslCompiledTransform();  
            xslt.Load("MyXSL.xsl");  
            XmlWriter writer = XmlWriter.Create("xslt_output.html");  
            xslt.Transform(xd, writer);  
            reader.Close();  
            writer.Close();  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXSL();     
         return 0;  
      }  
   }  
```  
  
  
