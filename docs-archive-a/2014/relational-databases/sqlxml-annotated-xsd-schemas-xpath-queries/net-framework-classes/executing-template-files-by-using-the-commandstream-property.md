---
title: CommandStream プロパティを使用したテンプレートファイルの実行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
author: rothja
ms.author: jroth
ms.openlocfilehash: c57a2ab2f3780a8bc75b53b0cceeee0799fcfcc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630870"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a><span data-ttu-id="cb55d-102">CommandStream プロパティを使用した、テンプレート ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="cb55d-102">Executing Template Files by Using the CommandStream Property</span></span>
  <span data-ttu-id="cb55d-103">この例は、SqlXmlCommand オブジェクトの CommandStream プロパティを使用して、SQL クエリまたは XPath クエリで構成されるテンプレートファイルを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb55d-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandStream property of the SqlXmlCommand object.</span></span> <span data-ttu-id="cb55d-104">このアプリケーションでは、コマンドファイルの FileStreamobject が開かれ、実行される CommandStream としてファイルストリームが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cb55d-104">In this application, a FileStreamobject is opened for a command file, and the file stream is assigned as the CommandStream that is executed.</span></span>  
  
 <span data-ttu-id="cb55d-105">次の例では、CommandType プロパティが (TemplateFile としてではなく) SqlXmlCommandType. Template として指定されています。</span><span class="sxs-lookup"><span data-stu-id="cb55d-105">In the following example, the CommandType property is specified as SqlXmlCommandType.Template (not as TemplateFile).</span></span>  
  
 <span data-ttu-id="cb55d-106">次はサンプル XML テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="cb55d-106">This is the sample XML template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="cb55d-107">これはサンプル C# アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="cb55d-107">This is the sample C# application.</span></span> <span data-ttu-id="cb55d-108">このアプリケーションをテストするには、テンプレート (TemplateFile.xml) を保存した後、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="cb55d-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span> <span data-ttu-id="cb55d-109">このアプリケーションでは、XML テンプレートに指定されているクエリが実行され、生成された XML ドキュメントが画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb55d-109">The application executes the query that is specified in the XML template and displays the XML document that is generated on the screen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb55d-110">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb55d-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;        
      }  
  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="cb55d-111">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="cb55d-111">To test the application</span></span>  
  
1.  <span data-ttu-id="cb55d-112">この例で提供される XML テンプレート (TemplateFile.xml) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="cb55d-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="cb55d-113">この例で提供されている C# コード (DocSample.cs) を、スキーマが格納されているのと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="cb55d-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="cb55d-114">ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb55d-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="cb55d-115">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="cb55d-115">Compile the code.</span></span> <span data-ttu-id="cb55d-116">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb55d-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="cb55d-117">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb55d-117">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="cb55d-118">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="cb55d-118">At the command prompt, execute DocSample.exe.</span></span>  
  
  
