---
title: CommandText プロパティ | を使用したテンプレートファイルの実行Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- executing template files [SQLXML]
- CommandText property
ms.assetid: f1b1278d-252d-4a06-836e-4ef77f338ef9
author: rothja
ms.author: jroth
ms.openlocfilehash: f5507e84daf57ca4646fae3efe78c6105af35700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630869"
---
# <a name="executing-template-files-by-using-the-commandtext-property"></a><span data-ttu-id="51935-102">CommandText プロパティを使用した、テンプレート ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="51935-102">Executing Template Files by Using the CommandText Property</span></span>
  <span data-ttu-id="51935-103">この例では、SQL または XPath クエリで構成されるテンプレートファイルを CommandTextproperty を使用して指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51935-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandTextproperty.</span></span> <span data-ttu-id="51935-104">CommandText の値として SQL または XPath クエリを指定する代わりに、ファイル名を値として指定できます。</span><span class="sxs-lookup"><span data-stu-id="51935-104">Instead of specifying the SQL or XPath query as the value of CommandText, you can specify a file name as the value.</span></span> <span data-ttu-id="51935-105">次の例では、CommandType プロパティが SqlXmlCommandType として指定されています。</span><span class="sxs-lookup"><span data-stu-id="51935-105">In the following example, the CommandType property is specified as SqlXmlCommandType.TemplateFile.</span></span>  
  
 <span data-ttu-id="51935-106">サンプル アプリケーションでは、次のテンプレートが実行されます。</span><span class="sxs-lookup"><span data-stu-id="51935-106">The sample application executes this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="51935-107">これは C# サンプル アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="51935-107">This is the C# sample application.</span></span> <span data-ttu-id="51935-108">このアプリケーションをテストするには、テンプレート (TemplateFile.xml) を保存した後、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="51935-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51935-109">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="51935-109">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandType = SqlXmlCommandType.TemplateFile;  
         cmd.CommandText = "TemplateFile.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="51935-110">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="51935-110">To test the application</span></span>  
  
1.  <span data-ttu-id="51935-111">コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="51935-111">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="51935-112">この例で提供される XML テンプレート (TemplateFile.xml) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="51935-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="51935-113">この例で提供されている C# コード (DocSample.cs) を、スキーマが格納されているのと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="51935-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="51935-114">ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51935-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="51935-115">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="51935-115">Compile the code.</span></span> <span data-ttu-id="51935-116">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="51935-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="51935-117">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="51935-117">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="51935-118">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="51935-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="51935-119">テンプレートにパラメーターを渡す場合、パラメーター名はアットマーク (@) で始める必要があります。たとえば、p.Name = "" のように指定し @ContactID ます。ここで、p は SqlXmlParameter オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="51935-119">If you pass a parameter to a template, the parameter name must begin with at sign (@); for example, p.Name="@ContactID", where p is a SqlXmlParameter object.</span></span>  
  
 <span data-ttu-id="51935-120">次は、1 つのパラメーターをとるように変更したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="51935-120">This is the updated template which takes one parameter.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='ContactID'>1</sql:param>    
  </sql:header>  
  <sql:query>  
    SELECT ContactID, FirstName, LastName  
    FROM   Person.Contact  
    WHERE  ContactID=@ContactID  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="51935-121">次は、テンプレートを実行するパラメーターを渡すように変更したコードです。</span><span class="sxs-lookup"><span data-stu-id="51935-121">This is the updated code in which a parameter is passed in to execute the template.</span></span>  
  
```  
public static int testParams()  
{  
  
   Stream strm;  
   SqlXmlParameter p;  
  
   SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
   cmd.CommandType = SqlXmlCommandType.TemplateFile;  
   cmd.CommandText = "TemplateFile.xml";  
   p = cmd.CreateParameter();  
   p.Name="@ContactID";  
   p.Value = "1";  
   strm = cmd.ExecuteStream();  
   StreamReader sw = new StreamReader(strm);  
   Console.WriteLine(sw.ReadToEnd());  
   return 0;        
}  
```  
  
  
