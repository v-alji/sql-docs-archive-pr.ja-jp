---
title: ADO を使用した DiffGram の実行 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b96db25fd46b1ecbbc15c8acd912743e5560f178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641558"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a><span data-ttu-id="30ee8-102">ADO を使用した、DiffGram の実行 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="30ee8-102">Executing a DiffGram by Using ADO (SQLXML 4.0)</span></span>
  <span data-ttu-id="30ee8-103">この [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic アプリケーションでは、ADO を使用して Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立した後、DiffGram を実行します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-103">This [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application uses ADO to establish a connection to an instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then executes a DiffGram.</span></span> <span data-ttu-id="30ee8-104">このアプリケーションでは、DiffGram と XSD スキーマは 1 つのファイルに格納されており、</span><span class="sxs-lookup"><span data-stu-id="30ee8-104">In this application, the DiffGram and the XSD schema are stored in a file.</span></span> <span data-ttu-id="30ee8-105">ファイルを指定して DiffGram を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-105">The application loads the DiffGram from the specified file.</span></span> <span data-ttu-id="30ee8-106">[Diffgram の例](diffgram-examples-sqlxml-4-0.md)に記載されている、すべての diffgram (および関連する XSD スキーマ) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-106">You can use any of the DiffGrams (and the associated XSD schema) described in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="30ee8-107">サンプルアプリケーションのプロセスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="30ee8-107">This is the process for the sample application:</span></span>  
  
-   <span data-ttu-id="30ee8-108">**Conn**オブジェクト (**ADODB接続**) 特定のサーバー上の SQL Server の実行中のインスタンスへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-108">The **conn** object (**ADODB.Connection**) establishes a connection to a running instance of SQL Server on a specific server.</span></span>  
  
-   <span data-ttu-id="30ee8-109">**Cmd**オブジェクト (**ADODB**) は、確立された接続で実行されます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-109">The **cmd** object (**ADODB.Command**) executes on the established connection.</span></span>  
  
-   <span data-ttu-id="30ee8-110">コマンド言語が DBGUID_MSSQLXML に設定されます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-110">The command dialect is set to DBGUID_MSSQLXML.</span></span>  
  
-   <span data-ttu-id="30ee8-111">DiffGram は、ファイルからコマンドストリーム (**Strmin**) にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-111">The DiffGram is copied to the command stream (**strmIn**) from a file.</span></span>  
  
-   <span data-ttu-id="30ee8-112">コマンドの出力ストリームは、 **Strmout**オブジェクト (ADODB) に設定され**ます。ストリーム**) が返されます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-112">The command's output stream is set to the **StrmOut** object (**ADODB.Stream**) to receive any returned data.</span></span>  
  
-   <span data-ttu-id="30ee8-113">SQLOLEDB プロバイダーを使用する場合、既定では Sqlxmlx.dll により Microsoft SQLXML の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-113">When you are using the SQLOLEDB Provider, by default you will get the Microsoft SQLXML functionality provided by Sqlxmlx.dll.</span></span> <span data-ttu-id="30ee8-114">SQLOLEDB プロバイダーで Sqlxml4.dll を使用するには、SQLOLEDB プロバイダー**接続**オブジェクトで**sqlxml Version**プロパティを**sqlxml. 4.0**に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30ee8-114">To use Sqlxml4.dll with the SQLOLEDB Provider, the **SQLXML Version** property must be set to **SQLXML.4.0** on the SQLOLEDB Provider **Connection** object.</span></span>  
  
-   <span data-ttu-id="30ee8-115">コマンド (DiffGram) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="30ee8-115">The command (DiffGram) is executed.</span></span>  
  
 <span data-ttu-id="30ee8-116">サンプル アプリケーションのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-116">The following code is the sample application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30ee8-117">コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="30ee8-117">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a><span data-ttu-id="30ee8-118">DiffGram をテストするには</span><span class="sxs-lookup"><span data-stu-id="30ee8-118">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="30ee8-119">コンピューター上のフォルダーには、 [diffgram の例](diffgram-examples-sqlxml-4-0.md)のいずれかの例から、いずれかの diffgram と対応する XSD スキーマをコピーします。</span><span class="sxs-lookup"><span data-stu-id="30ee8-119">To a folder on your computer, copy any one of the DiffGrams and the corresponding XSD schema from one of the examples in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="30ee8-120">Visual Basic を開き、標準 EXE プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-120">Open Visual Basic and create a Standard EXE project.</span></span>  
  
3.  <span data-ttu-id="30ee8-121">プロジェクトに次の参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-121">Add these references to the project:</span></span>  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  <span data-ttu-id="30ee8-122">ツールボックスで、[**コマンド**ボタン] をクリックし、フォームにボタンを描画します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-122">In the Toolbox, click **CommandButton**, and then draw a button on the form.</span></span>  
  
5.  <span data-ttu-id="30ee8-123">ボタンをダブルクリックしてコードを編集し、トピックで提供されるアプリケーション コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-123">Double-click the button to edit the code, and add the application code that is provided in the topic.</span></span>  
  
6.  <span data-ttu-id="30ee8-124">コードに DiffGram と XSD ファイルの名前を指定し、</span><span class="sxs-lookup"><span data-stu-id="30ee8-124">Edit the code to specify the DiffGram and XSD file names.</span></span> <span data-ttu-id="30ee8-125">接続文字列も適宜変更します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-125">Also edit the connection string as appropriate.</span></span>  
  
7.  <span data-ttu-id="30ee8-126">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="30ee8-126">Execute the application.</span></span> <span data-ttu-id="30ee8-127">実行結果は、実行する DiffGram によって変わります。</span><span class="sxs-lookup"><span data-stu-id="30ee8-127">The result of the execution depends on what DiffGram you are executing.</span></span>  
  
  
