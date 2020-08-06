---
title: クライアント側での XML の処理 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: fb90f7c5c823c750b64f47d0c9df9551b9f857b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631759"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a><span data-ttu-id="3ebc6-102">クライアント側での XML の処理 (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="3ebc6-102">Processing XML on the Client Side (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="3ebc6-103">この例は、ClientSideXml プロパティの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-103">This example illustrates the use of the ClientSideXml property.</span></span> <span data-ttu-id="3ebc6-104">サーバーで、アプリケーションによってストアド プロシージャが実行されると、</span><span class="sxs-lookup"><span data-stu-id="3ebc6-104">The application executes a stored procedure on the server.</span></span> <span data-ttu-id="3ebc6-105">クライアント側でその結果 (2 列の行セット) が処理され、XML ドキュメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-105">The result of the stored procedure (a two-column rowset) is processed on the client side to produce an XML document.</span></span>  
  
 <span data-ttu-id="3ebc6-106">次の GetContacts ストアドプロシージャは、AdventureWorks データベースの Person. Contact テーブルにある従業員の**FirstName**と**LastName**を返します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-106">The following GetContacts stored procedure returns **FirstName** and **LastName** of employees in the Person.Contact table in the AdventureWorks database.</span></span>  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 <span data-ttu-id="3ebc6-107">この C# アプリケーションは、ストアドプロシージャを実行し、CommandText 値を指定するために FOR XML AUTO オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-107">This C# application executes the stored procedure and specifies the FOR XML AUTO option in specifying the CommandText value.</span></span> <span data-ttu-id="3ebc6-108">アプリケーションでは、SqlXmlCommand オブジェクトの ClientSideXml プロパティが true に設定されています。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-108">In the application, the ClientSideXml property of the SqlXmlCommand object is set to true.</span></span> <span data-ttu-id="3ebc6-109">これにより、前から存在するストアド プロシージャを実行して行セットを返すことができ、クライアント側で XML 変換を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-109">This allows you to execute preexisting stored procedures that return a rowset and apply an XML transformation to it on the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ebc6-110">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
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
  
 <span data-ttu-id="3ebc6-111">この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-111">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="3ebc6-112">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="3ebc6-112">To test the application</span></span>  
  
1.  <span data-ttu-id="3ebc6-113">ストアドプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-113">Create the stored procedure.</span></span>  
  
2.  <span data-ttu-id="3ebc6-114">この例で提供される C# コード (DocSample.cs) をフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-114">Save the C# code (DocSample.cs) that is provided in this example in a folder.</span></span> <span data-ttu-id="3ebc6-115">コードを編集し、適切なログインおよびパスワード情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-115">Edit the code to specify appropriate login and password information.</span></span>  
  
3.  <span data-ttu-id="3ebc6-116">コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-116">Compile the code.</span></span> <span data-ttu-id="3ebc6-117">コマンド プロンプトでコードをコンパイルするには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-117">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="3ebc6-118">これにより、実行可能ファイル (DocSample.exe) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-118">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="3ebc6-119">コマンド プロンプトで、DocSample.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="3ebc6-119">At the command prompt, execute DocSample.exe.</span></span>  
  
  
