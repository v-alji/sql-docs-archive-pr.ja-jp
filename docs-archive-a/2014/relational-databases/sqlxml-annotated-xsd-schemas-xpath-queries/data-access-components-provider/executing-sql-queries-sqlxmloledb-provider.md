---
title: SQL クエリの実行 (SQLXMLOLEDB Provider) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXMLOLEDB Provider
- xml root property [SQLXML]
- SQLXMLOLEDB Provider, executing SQL queries
- SQL queries [SQLXML]
ms.assetid: 50334cf5-9c87-4c00-9beb-e08577c4fa82
author: rothja
ms.author: jroth
ms.openlocfilehash: a1e2cc87f90700e3b81a5a2ec3dd80f219a9b1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642712"
---
# <a name="executing-sql-queries-sqlxmloledb-provider"></a><span data-ttu-id="552a9-102">SQL クエリの実行 (SQLXMLOLEDB プロバイダー)</span><span class="sxs-lookup"><span data-stu-id="552a9-102">Executing SQL Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="552a9-103">この例では、次の SQLXMLOLEDB プロバイダー固有のプロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="552a9-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="552a9-104">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="552a9-104">ClientSideXML</span></span>  
  
-   <span data-ttu-id="552a9-105">xml root</span><span class="sxs-lookup"><span data-stu-id="552a9-105">xml root</span></span>  
  
 <span data-ttu-id="552a9-106">このクライアント側の ADO サンプル アプリケーションでは、クライアントで単純な SQL クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="552a9-106">In this client-side ADO sample application, a simple SQL query is executed on the client.</span></span> <span data-ttu-id="552a9-107">ClientSideXML プロパティが True に設定されているため、FOR XML 句を指定せずに SELECT ステートメントがサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="552a9-107">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="552a9-108">サーバーではクエリが実行され、クライアントに行セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="552a9-108">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="552a9-109">次にクライアントではその行セットに FOR XML 変換が適用され、XML ドキュメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="552a9-109">The client then applies the FOR XML transformation to the rowset and produces an XML document.</span></span>  
  
 <span data-ttu-id="552a9-110">Xml ルートプロパティは、生成される XML ドキュメントの最上位レベルのルート要素を1つ提供します。</span><span class="sxs-lookup"><span data-stu-id="552a9-110">The xml root property provides the single top-level root element for the XML document that is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="552a9-111">コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="552a9-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="552a9-112">また、この例ではデータ プロバイダーとして [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) を使用するよう指定していますが、これには追加ネットワーク クライアントがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="552a9-112">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="552a9-113">詳細については、「 [SQL Server Native Client のシステム要件](../../native-client/system-requirements-for-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="552a9-113">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI ;"  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = "SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO"  
oTestStream.Open  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("xml root") = "root"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
