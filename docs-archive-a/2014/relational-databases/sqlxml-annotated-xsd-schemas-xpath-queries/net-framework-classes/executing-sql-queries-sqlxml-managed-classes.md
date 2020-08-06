---
title: SQL クエリの実行 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
author: rothja
ms.author: jroth
ms.openlocfilehash: d869e45de359e602b2451b9f66fa3046f6823c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641534"
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a><span data-ttu-id="32e0e-102">SQL クエリの実行 (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="32e0e-102">Executing SQL Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="32e0e-103">この例では、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="32e0e-103">This example demonstrates:</span></span>  
  
-   <span data-ttu-id="32e0e-104">パラメーターの作成 (SqlXmlParameter オブジェクト)</span><span class="sxs-lookup"><span data-stu-id="32e0e-104">Creating parameters (SqlXmlParameter objects).</span></span>  
  
-   <span data-ttu-id="32e0e-105">SqlXmlParameter オブジェクトのプロパティ (名前と値) に値を代入します。</span><span class="sxs-lookup"><span data-stu-id="32e0e-105">Assigning values to the properties (Name and Value) of SqlXmlParameter objects.</span></span>  
  
 <span data-ttu-id="32e0e-106">この例では、単純な SQL クエリを実行して、従業員の姓、名、および誕生日を取得します。従業員の姓の値はパラメーターとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-106">In this example, a simple SQL query is executed to retrieve the first name, last name, and birth date of the employee whose last name value is passed as a parameter.</span></span> <span data-ttu-id="32e0e-107">パラメーター (*LastName*) を指定する場合は、Value プロパティのみが設定されます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-107">In specifying the parameter (*LastName*), only the Value property is set.</span></span> <span data-ttu-id="32e0e-108">Name プロパティが設定されていません。このクエリでは、パラメーターは位置指定であり、名前は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="32e0e-108">The Name property is not set, because in this query the parameter is positional and no name is required.</span></span>  
  
 <span data-ttu-id="32e0e-109">SqlXmlCommand オブジェクトの CommandType プロパティは、既定では**Sql**です。</span><span class="sxs-lookup"><span data-stu-id="32e0e-109">The CommandType property of the SqlXmlCommand object by default is **Sql**.</span></span> <span data-ttu-id="32e0e-110">したがって、このプロパティは明示的に設定しません。</span><span class="sxs-lookup"><span data-stu-id="32e0e-110">Therefore, the property is not explicitly set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32e0e-111">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="32e0e-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
 <span data-ttu-id="32e0e-112">この C# コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="32e0e-112">This is the C# code:</span></span>  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="32e0e-113">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="32e0e-113">To test the application</span></span>  
  
1.  <span data-ttu-id="32e0e-114">このトピックで提供される C# コード (DocSample.cs) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="32e0e-114">Save the C# code (DocSample.cs) provided in this topic in a folder.</span></span>  
  
2.  <span data-ttu-id="32e0e-115">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="32e0e-115">Compile the code.</span></span> <span data-ttu-id="32e0e-116">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="32e0e-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="32e0e-117">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-117">This creates an executable (DocSample.exe).</span></span>  
  
3.  <span data-ttu-id="32e0e-118">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="32e0e-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="32e0e-119">この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="32e0e-119">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
 <span data-ttu-id="32e0e-120">コマンド テキストとして SQL クエリを指定する代わりに、次のコード フラグメントのようなテンプレートを指定して、(同様にテンプレートとして提供されている) アップデートグラムを実行し、顧客レコードを挿入することもできます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-120">Instead of specifying SQL queries as the command text, you can specify a template (as shown in the following code fragment) that executes an updategram (which is also a template) to insert a customer record.</span></span> <span data-ttu-id="32e0e-121">テンプレートとアップデートグラムはファイル内に指定し、ファイルとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-121">You can specify templates and updategrams in files and execute files.</span></span> <span data-ttu-id="32e0e-122">詳細については、「 [CommandText プロパティを使用したテンプレートファイルの実行](executing-template-files-by-using-the-commandtext-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32e0e-122">For more information, see [Executing Template Files by Using the CommandText Property](executing-template-files-by-using-the-commandtext-property.md).</span></span>  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a><span data-ttu-id="32e0e-123">ExecuteToStream の使用</span><span class="sxs-lookup"><span data-stu-id="32e0e-123">Using ExecuteToStream</span></span>  
 <span data-ttu-id="32e0e-124">既存のストリームがある場合は、Stream オブジェクトを作成し、Execute メソッドを使用する代わりに、ExecuteToStream メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-124">If you have an existing stream, you can use the ExecuteToStream method instead of creating a Stream object and using the Execute method.</span></span> <span data-ttu-id="32e0e-125">前の例のコードは、次のように ExecuteToStream メソッドを使用するように改訂されています。</span><span class="sxs-lookup"><span data-stu-id="32e0e-125">The code from the preceding example is revised here to use the ExecuteToStream method:</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="32e0e-126">XmlReader オブジェクトを返す ExecuteXMLReadermethod を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="32e0e-126">You can also use the ExecuteXMLReadermethod that returns an XmlReader object.</span></span> <span data-ttu-id="32e0e-127">詳細については、「 [ExecuteXMLReader メソッドを使用した SQL クエリの実行](executing-sql-queries-by-using-the-executexmlreader-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32e0e-127">For more information, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
  
