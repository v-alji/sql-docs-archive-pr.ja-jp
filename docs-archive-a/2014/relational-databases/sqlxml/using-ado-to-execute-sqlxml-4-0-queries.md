---
title: ADO を使用した、SQLXML 4.0 クエリの実行
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- query testers [SQLXML]
- test scripts
- ADO [SQLXML]
- queries [SQLXML], ADO
- SQLXML, ADO
ms.assetid: 3d54e3bb-7c5f-427e-82f8-1403a54c4f53
author: rothja
ms.author: jroth
ms.openlocfilehash: 169d20b4192e4a5b8e7b32839f2da255fc58d89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713026"
---
# <a name="using-ado-to-execute-sqlxml-40-queries"></a><span data-ttu-id="239e5-102">ADO を使用した、SQLXML 4.0 クエリの実行</span><span class="sxs-lookup"><span data-stu-id="239e5-102">Using ADO to Execute SQLXML 4.0 Queries</span></span>
  <span data-ttu-id="239e5-103">以前のバージョンの SQLXML では、SQLXML IIS 仮想ディレクトリと SQLXML ISAPI フィルターを使用して、HTTP ベースのクエリを実行することができました。</span><span class="sxs-lookup"><span data-stu-id="239e5-103">In previous versions of SQLXML, HTTP-based query execution was supported using SQLXML IIS virtual directories and the SQLXML ISAPI filter.</span></span> <span data-ttu-id="239e5-104">SQLXML 4.0 では、重複する類似の機能が [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のネイティブ XML Web サービスに付属しているため、これらのコンポーネントが削除されました。</span><span class="sxs-lookup"><span data-stu-id="239e5-104">In SQLXML 4.0, these components have been removed as similar and overlapping functionality is provided with native XML Web services beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="239e5-105">SQLXML 4.0 では、代わりに Microsoft Data Access Components (MDAC) 2.6 以降で最初に導入された ADO (ActiveX Data Objects) への SQLXML 拡張を使用して、COM ベースのアプリケーションで SQLXML 4.0 を使用してクエリを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="239e5-105">As an alternative, you can execute queries and use SQLXML 4.0 with your COM-based applications, by leveraging the SQLXML extensions to ActiveX Data Objects (ADO) that were first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="239e5-106">ここでは、Visual Basic Scripting Edition (VBScript) アプリケーション (ファイル拡張子が .vbs のスクリプト) の一部として、SQLXML と ADO を使用する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="239e5-106">This topic demonstrates using SQLXML and ADO as part of a Visual Basic Scripting Edition (VBScript) application (a script with the .vbs file extension).</span></span> <span data-ttu-id="239e5-107">SQLXML 4.0 のドキュメントにあるサンプル クエリを作成しテストするときには、ここで紹介する最初の設定手順を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="239e5-107">It provides initial setup procedures to help you recreate and test query samples in the SQLXML 4.0 documentation.</span></span>  
  
## <a name="creating-the-sqlxml-40-test-script"></a><span data-ttu-id="239e5-108">SQLXML 4.0 テスト スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="239e5-108">Creating the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="239e5-109">ここでは、VBScript (.vbs) ファイル Sqlxml4test.vbs を作成します。このファイルを使用すると、ADO 2.6 以降の SQLXML ADO 拡張を使用して SQLXML クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="239e5-109">In this procedure, you create a VBScript (.vbs) file, Sqlxml4test.vbs, which can be used to execute SQLXML queries by leveraging the SQLXML ADO extensions in ADO 2.6 and later.</span></span>  
  
#### <a name="to-create-the-sqlxml-40-query-tester-using-ado-vbscript"></a><span data-ttu-id="239e5-110">ADO を使用した SQLXML 4.0 クエリのテスト スクリプト (VBScript) を作成するには</span><span class="sxs-lookup"><span data-stu-id="239e5-110">To create the SQLXML 4.0 query tester using ADO (VBScript).</span></span>  
  
1.  <span data-ttu-id="239e5-111">次の VBScript コードをコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="239e5-111">Copy the VBScript code below, and paste it into a text file.</span></span> <span data-ttu-id="239e5-112">Sqlxml4test.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="239e5-112">Save the file as Sqlxml4test.vbs.</span></span>  
  
    ```vb
    WScript.Echo "Query process may take a few seconds to complete. Please be patient."  
  
    ' Note that for SQL Server Native Client to be used as the data provider,  
    ' it needs to be installed on the client computer first. Also, SQLXML extensions   
    ' for ADO are used and available in MDAC 2.6 or later.  
  
    'Set script variables.  
    inputFile = "@@FILE_NAME@@"  
    strServer = "@@SERVER_NAME@@"  
    strDatabase = "@@DATABASE_NAME@@"  
    dbGuid = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
    ' Establish ADO connection to SQL Server and   
    ' create an instance of the ADO Command object.  
    Set conn = CreateObject("ADODB.Connection")  
    Set cmd = CreateObject("ADODB.Command")  
    conn.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Server=" & strServer & _  
              ";Database=" & strDatabase & ";Integrated Security=SSPI"  
    Set cmd.ActiveConnection = conn  
  
    ' Create the input stream as an instance of the ADO Stream object.  
    Set inStream = CreateObject("ADODB.Stream")  
    inStream.Open  
    inStream.Charset = "utf-8"  
    inStream.LoadFromFile inputFile  
  
    ' Set ADO Command instance to use input stream.  
    Set cmd.CommandStream = inStream  
  
    ' Set the command dialect.  
    cmd.Dialect = dbGuid  
  
    ' Set a second ADO Stream instance for use as a results stream.   
    Set outStream = CreateObject("ADODB.Stream")  
    outStream.Open  
  
    ' Set dynamic properties used by the SQLXML ADO command instance.   
    cmd.Properties("XML Root").Value = "ROOT"  
    cmd.Properties("Output Encoding").Value = "UTF-8"  
  
    ' Connect the results stream to the command instance and execute the command.  
    cmd.Properties("Output Stream").Value = outStream  
    cmd.Execute , , 1024  
  
    ' Echo cropped/partial results to console.  
    WScript.Echo Left(outStream.ReadText, 1023)  
  
    inStream.Close  
    outStream.Close  
    ```  
  
2.  <span data-ttu-id="239e5-113">テストするサンプルとテスト環境に合わせて、次のスクリプト値を更新します。</span><span class="sxs-lookup"><span data-stu-id="239e5-113">Update the following script values for the sample you are trying to test and your test environment.</span></span>  
  
    -   <span data-ttu-id="239e5-114">"`@@FILE_NAME@@`" をテンプレート ファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="239e5-114">Find "`@@FILE_NAME@@`" and replace it with the name of your template file.</span></span>  
  
    -   <span data-ttu-id="239e5-115">"`@@SERVER_NAME@@`" を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をローカルで実行している場合は "`(local)`" など) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="239e5-115">Find "`@@SERVER_NAME@@`" and replace it with the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (for example, "`(local)`" if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running locally).</span></span>  
  
    -   <span data-ttu-id="239e5-116">"`@@DATABASE_NAME@@`" をデータベースの名前 ("`AdventureWorks2012`" や "`tempdb`" など) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="239e5-116">Find "`@@DATABASE_NAME@@`" and replace it with the name of the database (for example, either "`AdventureWorks2012`" or "`tempdb`").</span></span>  
  
     <span data-ttu-id="239e5-117">ローカル コンピューターに作成するサンプル用の具体的な指示に従って、必要であれば他の値も更新します。</span><span class="sxs-lookup"><span data-stu-id="239e5-117">Update any other values if mentioned in the specific instructions for the example you are attempting to recreate locally on your computer.</span></span>  
  
3.  <span data-ttu-id="239e5-118">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="239e5-118">Save the file and close it.</span></span>  
  
4.  <span data-ttu-id="239e5-119">ローカル コンピューターに作成するサンプル ファイルの一部として、XML テンプレートやスキーマなどの必要な追加ファイルが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="239e5-119">Verify that you have created any additional files, such as XML templates or schemas that are part of the sample you are attempting to recreate locally on your computer.</span></span> <span data-ttu-id="239e5-120">これらのファイルは、テスト スクリプト ファイル (Sqlxml4test.vbs) を保存したディレクトリに置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="239e5-120">These files should be located in the same directory where you have saved the test script file (Sqlxml4test.vbs).</span></span>  
  
5.  <span data-ttu-id="239e5-121">次に、SQLXML 4.0 テスト スクリプトの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="239e5-121">Follow the instructions in the next section for how to use the SQLXML 4.0 test script.</span></span>  
  
## <a name="using-the-sqlxml-40-test-script"></a><span data-ttu-id="239e5-122">SQLXML 4.0 テスト スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="239e5-122">Using the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="239e5-123">Sqlxml4test.vbs ファイルを使用して、このドキュメントで提供されるサンプル クエリをテストするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="239e5-123">The following procedure describes how to use the Sqlxml4test.vbs files to test the example queries provided in this documentation.</span></span>  
  
#### <a name="to-use-the-sqlxml-40-query-tester"></a><span data-ttu-id="239e5-124">SQLXML 4.0 クエリのテスト スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="239e5-124">To use the SQLXML 4.0 query tester</span></span>  
  
1.  <span data-ttu-id="239e5-125">次の方法で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client がインストールされていること確認します。</span><span class="sxs-lookup"><span data-stu-id="239e5-125">Verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed, as follows:</span></span>  
  
    1.  <span data-ttu-id="239e5-126">[**スタート**] メニューの [**設定**] をポイントし、[**コントロールパネル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="239e5-126">From the **Start** menu, point to **Settings**, and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="239e5-127">コントロールパネルで、[**プログラムの追加と削除**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="239e5-127">In Control Panel, open **Add or Remove Programs**</span></span>  
  
    3.  <span data-ttu-id="239e5-128">現在インストールされているプログラムの一覧で、[ **Microsoft SQL Server Native Client** ] が一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="239e5-128">In the list of currently installed programs, verify that **Microsoft SQL Server Native Client** appears in the list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="239e5-129">Native Client をインストールする必要がある場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server Native Client のインストール](../native-client/applications/installing-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="239e5-129">If you need to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
2.  <span data-ttu-id="239e5-130">クライアント コンピューターにインストールされている MDAC のバージョンが 2.6 以降であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="239e5-130">Verify that the version of MDAC installed for the client computer is 2.6 or later.</span></span> <span data-ttu-id="239e5-131">MDAC のバージョン情報を確認する必要がある場合は、MDAC コンポーネントチェッカーツールを使用できます。このツールは、Microsoft Web サイトから無料でダウンロードでき [https://www.microsoft.com/](https://www.microsoft.com/) ます。</span><span class="sxs-lookup"><span data-stu-id="239e5-131">If you need to verify MDAC version information, you can use the MDAC Component Checker tool, which is provided as free download from the Microsoft Web site [https://www.microsoft.com/](https://www.microsoft.com/).</span></span> <span data-ttu-id="239e5-132">詳細については、Microsoft Web サイトの「MDAC Component Checker」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="239e5-132">For more information, search on "MDAC Component Checker" on the Microsoft Web site.</span></span>  
  
3.  <span data-ttu-id="239e5-133">スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="239e5-133">Execute the script.</span></span>  
  
     <span data-ttu-id="239e5-134">VBScript ファイルを実行するには、コマンド ラインで Cscript.exe を指定するか、Sqlxml4test.vbs ファイルをダブルクリックして Windows Script Host (WScript.exe) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="239e5-134">You can execute the VBScript file either at the command line using Cscript.exe or by double-clicking Sqlxml4test.vbs file to invoke the Windows Script Host (WScript.exe).</span></span>  
  
     <span data-ttu-id="239e5-135">スクリプトを実行すると、警告メッセージが表示され、返されたクエリの結果を出力として表示するまでには時間がかかる場合があることが示されます。</span><span class="sxs-lookup"><span data-stu-id="239e5-135">When executed, the script should display a message to alert you that the script might take a few moments to execute before returning and displaying query results as script output.</span></span> <span data-ttu-id="239e5-136">出力が表示されたら、サンプルの結果例と内容を比較します。</span><span class="sxs-lookup"><span data-stu-id="239e5-136">When the output appears, compare its contents to the expected results for the sample.</span></span>  
  
  
