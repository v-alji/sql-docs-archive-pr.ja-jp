---
title: 名前空間を使用した XPath クエリの実行 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: rothja
ms.author: jroth
ms.openlocfilehash: a2d726de95929709c1ae958ee22388df3195bc84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630867"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a><span data-ttu-id="13d42-102">名前空間を使用した XPath クエリの実行 (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="13d42-102">Executing XPath Queries with Namespaces (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="13d42-103">XPath クエリには名前空間を使用できます。</span><span class="sxs-lookup"><span data-stu-id="13d42-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="13d42-104">スキーマ要素に対象名前空間の修飾子が付けられている場合、そのスキーマに対する XPath クエリでは、名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d42-104">If the schema elements are namespace-qualified (use a target namespace), the XPath queries against the schema must specify the namespace.</span></span>  
  
 <span data-ttu-id="13d42-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 ではワイルドカード文字 (\*) がサポートされないため、XPath クエリは、名前空間プレフィックスを使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d42-105">Because the wildcard character (\*) is not supported in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="13d42-106">プレフィックスを解決するには、名前空間プロパティを使用して名前空間のバインドを指定します。</span><span class="sxs-lookup"><span data-stu-id="13d42-106">To resolve the prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="13d42-107">次の例では、XPath クエリは、ワイルドカード文字 ( \* ) およびローカル名 () および名前空間 uri () の xpath 関数を使用して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13d42-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="13d42-108">この XPath クエリでは、ローカル名が `Employee`、名前空間 URI が `urn:myschema:Contacts` のすべての要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="13d42-108">This XPath query returns all the elements where the local name is `Employee` and the namespace URI is `urn:myschema:Contacts`:</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="13d42-109">SQLXML 4.0 では、この XPath クエリを名前空間プレフィックスと共に指定します。</span><span class="sxs-lookup"><span data-stu-id="13d42-109">In SQLXML 4.0, specify this XPath query with a namespace prefix.</span></span> <span data-ttu-id="13d42-110">たとえば、`x:Contact` と指定します。ここで、`x` は名前空間プレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="13d42-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="13d42-111">次の XSD スキーマについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="13d42-111">Consider the following XSD schema:</span></span>  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 <span data-ttu-id="13d42-112">このスキーマでは対象の名前空間が定義されているため、このスキーマに対する XPath クエリ ("Employee" など) には名前空間を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d42-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against this schema must include the namespace.</span></span>  
  
 <span data-ttu-id="13d42-113">次の C# サンプル アプリケーションでは、前の XSD スキーマ (MySchema.xml) に対する XPath クエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="13d42-113">The following C# sample application executes an XPath query against the preceding XSD schema (MySchema.xml).</span></span> <span data-ttu-id="13d42-114">プレフィックスを解決するには、SqlXmlCommand オブジェクトの namespace プロパティを使用して名前空間のバインドを指定します。</span><span class="sxs-lookup"><span data-stu-id="13d42-114">To resolve the prefix, specify the namespace binding by using the Namespaces property of the SqlXmlCommand object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13d42-115">コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d42-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
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
  
 <span data-ttu-id="13d42-116">この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d42-116">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="13d42-117">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="13d42-117">To test the application</span></span>  
  
1.  <span data-ttu-id="13d42-118">この例で提供される XSD スキーマ (MySchema.xml) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="13d42-118">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="13d42-119">この例で提供されている C# コード (DocSample.cs) を、スキーマが格納されているのと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="13d42-119">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="13d42-120">ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d42-120">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="13d42-121">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="13d42-121">Compile the code.</span></span> <span data-ttu-id="13d42-122">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="13d42-122">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="13d42-123">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="13d42-123">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="13d42-124">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="13d42-124">At the command prompt, execute DocSample.exe.</span></span>  
  
  
