---
title: ローカル パッケージの出力の読み込み | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6799e593ab9d5ae1a9358bf54f4927838991ebd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740141"
---
# <a name="loading-the-output-of-a-local-package"></a><span data-ttu-id="8b849-102">ローカル パッケージの出力の読み込み</span><span class="sxs-lookup"><span data-stu-id="8b849-102">Loading the Output of a Local Package</span></span>
  <span data-ttu-id="8b849-103">クライアント アプリケーションは、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先に出力が保存された場合、または **System.IO** 名前空間のクラスを使用してフラット ファイル変換先に出力が保存された場合に、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの出力を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8b849-103">Client applications can read the output of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages when the output is saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinations by using [!INCLUDE[vstecado](../../includes/vstecado-md.md)], or when the output is saved to a flat file destination by using the classes in the **System.IO** namespace.</span></span> <span data-ttu-id="8b849-104">ただし、メモリから直接、パッケージの出力を読み取ることもできます。その際、データを保持するための中間手段を必要としません。</span><span class="sxs-lookup"><span data-stu-id="8b849-104">However, a client application can also read the output of a package directly from memory, without the need for an intermediate step to persist the data.</span></span> <span data-ttu-id="8b849-105">このソリューションの重要な鍵は、 `Microsoft.SqlServer.Dts.DtsClient` `IDbConnection` `IDbCommand` **ある**名前空間からの、、 **System.Data**およびの各インターフェイスの特殊な実装を含む名前空間です。</span><span class="sxs-lookup"><span data-stu-id="8b849-105">The key to this solution is the `Microsoft.SqlServer.Dts.DtsClient` namespace, which contains specialized implementations of the `IDbConnection`, `IDbCommand`, and **IDbDataParameter** interfaces from the **System.Data** namespace.</span></span> <span data-ttu-id="8b849-106">既定では、アセンブリ Microsoft.SqlServer.Dts.DtsClient.dll は、 **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn** にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="8b849-106">The assembly Microsoft.SqlServer.Dts.DtsClient.dll is installed by default in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

> [!NOTE]
>  <span data-ttu-id="8b849-107">このトピックで説明されている手順では、データ フロー タスクおよび親オブジェクトの DelayValidation プロパティが既定値の **False** に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b849-107">The procedure described in this topic requires that the DelayValidation property of the Data Flow task and of any parent objects be set to its default value of **False**.</span></span>

## <a name="description"></a><span data-ttu-id="8b849-108">[説明]</span><span class="sxs-lookup"><span data-stu-id="8b849-108">Description</span></span>
 <span data-ttu-id="8b849-109">この手順では、マネージド コードを使用して、DataReader 変換先でパッケージの出力をメモリから直接読み込むクライアント アプリケーションを開発する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8b849-109">This procedure demonstrates how to develop a client application in managed code that loads the output of a package with a DataReader destination directly from memory.</span></span> <span data-ttu-id="8b849-110">ここにまとめた手順は、後のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="8b849-110">The steps summarized here are demonstrated in the code sample that follows.</span></span>

#### <a name="to-load-data-package-output-into-a-client-application"></a><span data-ttu-id="8b849-111">クライアント アプリケーションにパッケージ出力を読み込むには</span><span class="sxs-lookup"><span data-stu-id="8b849-111">To load data package output into a client application</span></span>

1.  <span data-ttu-id="8b849-112">パッケージで、クライアント アプリケーションに読み込む出力を受信するように DataReader 変換先を構成します。</span><span class="sxs-lookup"><span data-stu-id="8b849-112">In the package, configure a DataReader destination to receive the output that you want to read into the client application.</span></span> <span data-ttu-id="8b849-113">DataReader 変換先にはわかりやすい名前を付けます。この名前は後からクライアント アプリケーションで使用します。</span><span class="sxs-lookup"><span data-stu-id="8b849-113">Give the DataReader destination a descriptive name, since you will use this name later in your client application.</span></span> <span data-ttu-id="8b849-114">DataReader 変換先の名前はメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="8b849-114">Make a note of the name of the DataReader destination.</span></span>

2.  <span data-ttu-id="8b849-115">開発プロジェクトで、アセンブリMicrosoft.SqlServer.Dts.DtsClient.dllを検索して、名前空間への参照を設定 `Microsoft.SqlServer.Dts.DtsClient` します。 \*\* \*\*</span><span class="sxs-lookup"><span data-stu-id="8b849-115">In the development project, set a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by locating the assembly **Microsoft.SqlServer.Dts.DtsClient.dll**.</span></span> <span data-ttu-id="8b849-116">既定では、このアセンブリは **C:\Program Files\Microsoft SQL Server\100\DTS\Binn** にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8b849-116">By default, this assembly is installed in **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**.</span></span> <span data-ttu-id="8b849-117">C# またはステートメントを使用して、コードに名前空間をインポートし `Using` [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` ます。</span><span class="sxs-lookup"><span data-stu-id="8b849-117">Import the namespace into your code by using the C# `Using` or the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` statement.</span></span>

3.  <span data-ttu-id="8b849-118">コードで、 `DtsClient.DtsConnection` パッケージを実行する**dtexec.exe**に必要なコマンドラインパラメーターを含む接続文字列を使用して、型のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b849-118">In your code, create an object of type `DtsClient.DtsConnection` with a connection string that contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="8b849-119">詳細については、「[dtexec ユーティリティ](../packages/dtexec-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b849-119">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span> <span data-ttu-id="8b849-120">次に、この接続文字列を使用して接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="8b849-120">Then open the connection with this connection string.</span></span> <span data-ttu-id="8b849-121">**dtexecui** ユーティリティを使用して、必要な接続文字列を視覚的に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b849-121">You can also use the **dtexecui** utility to create the required connection string visually.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="8b849-122">このサンプル コードは、`/FILE <path and filename>` 構文を使用してファイル システムからパッケージを読み込む方法を示していますが、</span><span class="sxs-lookup"><span data-stu-id="8b849-122">The sample code demonstrates loading the package from the file system by using the `/FILE <path and filename>` syntax.</span></span> <span data-ttu-id="8b849-123">`/SQL <package name>` 構文を使用して MSDB データベースからパッケージを読み込んだり、`/DTS \<folder name>\<package name>` 構文を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ストアからパッケージを読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="8b849-123">However you can also load the package from the MSDB database by using the `/SQL <package name>` syntax, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by using the `/DTS \<folder name>\<package name>` syntax.</span></span>

4.  <span data-ttu-id="8b849-124">前に作成した `DtsClient.DtsCommand` を使用する `DtsConnection` という種類のオブジェクトを作成し、その `CommandText` プロパティに、パッケージ内の DataReader 変換先の名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="8b849-124">Create an object of type `DtsClient.DtsCommand` that uses the previously created `DtsConnection` and set its `CommandText` property to the name of the DataReader destination in the package.</span></span> <span data-ttu-id="8b849-125">次に、コマンド オブジェクトの `ExecuteReader` メソッドを呼び出して、パッケージの結果を新しい DataReader に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8b849-125">Then call the `ExecuteReader` method of the command object to load the package results into a new DataReader.</span></span>

5.  <span data-ttu-id="8b849-126">必要に応じて、`DtsDataParameter` オブジェクトで `DtsCommand` オブジェクトのコレクションを使用して、パッケージに定義された変数に値を渡すことによって、パッケージの出力を間接的にパラメーター化できます。</span><span class="sxs-lookup"><span data-stu-id="8b849-126">Optionally, you can indirectly parameterize the output of the package by using the collection of `DtsDataParameter` objects on the `DtsCommand` object to pass values to variables defined in the package.</span></span> <span data-ttu-id="8b849-127">パッケージ内では、これらの変数をクエリ パラメーターとして、または式で使用して、DataReader 変換先に返される結果に影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="8b849-127">Within the package, you can use these variables as query parameters or in expressions to affect the results returned to the DataReader destination.</span></span> <span data-ttu-id="8b849-128">クライアントアプリケーションからオブジェクトと共に使用するには、 **dtsclient**名前空間のパッケージでこれらの変数を定義する必要があり `DtsDataParameter` ます。</span><span class="sxs-lookup"><span data-stu-id="8b849-128">You must define these variables in the package in the **DtsClient** namespace before you can use them with the `DtsDataParameter` object from a client application.</span></span> <span data-ttu-id="8b849-129">([**変数**] ウィンドウの [**変数列の選択**] ツールバーボタンをクリックして、[**名前空間**] 列を表示する必要がある場合があります)。クライアントコードで、をのコレクションに追加する場合は、 `DtsDataParameter` `Parameters` `DtsCommand` 変数名から dtsclient 名前空間参照を省略します。</span><span class="sxs-lookup"><span data-stu-id="8b849-129">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.) In your client code, when you add a `DtsDataParameter` to the `Parameters` collection of the `DtsCommand`, omit the DtsClient namespace reference from the variable name.</span></span> <span data-ttu-id="8b849-130">例:</span><span class="sxs-lookup"><span data-stu-id="8b849-130">For example:</span></span>

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  <span data-ttu-id="8b849-131">出力データの行をループするのに必要なだけ、DataReader の `Read` メソッドを繰り返し呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b849-131">Call the `Read` method of the DataReader repeatedly as needed to loop through the rows of output data.</span></span> <span data-ttu-id="8b849-132">クライアント アプリケーションで、データを使用するか、または後で使用するために保存します。</span><span class="sxs-lookup"><span data-stu-id="8b849-132">Use the data, or save the data for later use, in the client application.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="8b849-133">DataReader のこの実装の `Read` メソッドは、データの最後の行が読み取られた後にもう一度 `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="8b849-133">The `Read` method of this implementation of the DataReader returns `true` one more time after the last row of data has been read.</span></span> <span data-ttu-id="8b849-134">このため、`Read` が `true` を返している間、DataReader をループする通常のコードを使用することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="8b849-134">This makes it difficult to use the usual code that loops through the DataReader while `Read` returns `true`.</span></span> <span data-ttu-id="8b849-135">予定した行数を読み取った後に `Read` メソッドの追加の最終呼び出しがないと、コードで DataReader または接続を閉じようとした場合に、ハンドルされていない例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="8b849-135">If your code attempts to close the DataReader or the connection after reading the expected number of rows, without an additional, final call to the `Read` method, the code will raise an unhandled exception.</span></span> <span data-ttu-id="8b849-136">しかし、コードがこのループの最後の反復でデータを読み取ろうとした場合、`Read` がまだ `true` を返しているのに最後の行に到達すると、ハンドルされていない `ApplicationException` が発生し、"SSIS IDataReader は結果セットの末尾に到達しました。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b849-136">However, if your code attempts to read data on this final iteration through a loop, when `Read` still returns `true` but the last row has been passed, the code will raise an unhandled `ApplicationException` with the message, "The SSIS IDataReader is past the end of the resultset."</span></span> <span data-ttu-id="8b849-137">この動作は、その他の DataReader 実装の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="8b849-137">This behavior is different from that of other DataReader implementations.</span></span> <span data-ttu-id="8b849-138">したがって、`Read` が `true` を返している間にループを使用して DataReader 内の行を最後まで読み取るようにするには、最後の `ApplicationException` メソッドの正常な呼び出しで予想されるこの `Read` をキャッチ、テスト、および破棄するコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b849-138">Therefore, when using a loop to read through the rows in the DataReader while `Read` returns `true`, you need to write code to catch, test, and discard this anticipated `ApplicationException` on the last successful call to the `Read` method.</span></span> <span data-ttu-id="8b849-139">あるいは、予定の行数があらかじめわかっている場合は、行を処理してから、DataReader および接続を閉じる前にもう一度 `Read` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b849-139">Or, if you know in advance the number of rows expected, you can process the rows, and then call the `Read` method one more time before closing the DataReader and the connection.</span></span>

7.  <span data-ttu-id="8b849-140">`Dispose` オブジェクトの `DtsCommand` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b849-140">Call the `Dispose` method of the `DtsCommand` object.</span></span> <span data-ttu-id="8b849-141">`DtsDataParameter` オブジェクトを使用している場合、これは特に重要です。</span><span class="sxs-lookup"><span data-stu-id="8b849-141">This is particularly important if you have used any `DtsDataParameter` objects.</span></span>

8.  <span data-ttu-id="8b849-142">DataReader と接続オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="8b849-142">Close the DataReader and the connection objects.</span></span>

## <a name="example"></a><span data-ttu-id="8b849-143">例</span><span class="sxs-lookup"><span data-stu-id="8b849-143">Example</span></span>
 <span data-ttu-id="8b849-144">次の例では、1 つの集計値を計算してその値を DataReader 変換先に保存するパッケージを実行します。次に、この値を DataReader から読み取って、Windows フォーム上のテキスト ボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="8b849-144">The following example runs a package that calculates a single aggregate value and saves the value to a DataReader destination, and then reads this value from the DataReader and displays the value in a text box on a Windows Form.</span></span>

 <span data-ttu-id="8b849-145">パッケージの出力をクライアント アプリケーションに読み込む場合は、パラメーターを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8b849-145">The use of parameters is not required when loading the output of a package into a client application.</span></span> <span data-ttu-id="8b849-146">パラメーターを使用しない場合は、 **Dtsclient**名前空間の変数の使用を省略し、そのオブジェクトを使用するコードを省略でき `DtsDataParameter` ます。</span><span class="sxs-lookup"><span data-stu-id="8b849-146">If you do not want to use a parameter, you can omit the use of the variable in the **DtsClient** namespace, and omit the code that uses the `DtsDataParameter` object.</span></span>

#### <a name="to-create-the-test-package"></a><span data-ttu-id="8b849-147">テスト パッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="8b849-147">To create the test package</span></span>

1.  <span data-ttu-id="8b849-148">新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b849-148">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="8b849-149">サンプル コードでは、パッケージの名前として "DtsClientWParamPkg.dtsx" が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8b849-149">The sample code uses "DtsClientWParamPkg.dtsx" as the name of the package.</span></span>

2.  <span data-ttu-id="8b849-150">DtsClient 名前空間に文字列型の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="8b849-150">Add a variable of type String in the DtsClient namespace.</span></span> <span data-ttu-id="8b849-151">サンプル コードでは、変数の名前として Country が使用されています </span><span class="sxs-lookup"><span data-stu-id="8b849-151">The sample code use Country as the name of the variable.</span></span> <span data-ttu-id="8b849-152">(**[名前空間]** 列を表示するには、**[変数]** ウィンドウの **[変数列の選択]** ツール バー ボタンをクリックする必要がある場合があります)。</span><span class="sxs-lookup"><span data-stu-id="8b849-152">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.)</span></span>

3.  <span data-ttu-id="8b849-153">[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベースに接続する OLE DB 接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="8b849-153">Add an OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>

4.  <span data-ttu-id="8b849-154">データ フロー タスクをパッケージに追加し、[データ フロー] デザイン画面に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="8b849-154">Add a data flow task to the package and switch to the Data Flow design surface.</span></span>

5.  <span data-ttu-id="8b849-155">OLE DB ソースをデータ フローに追加し、前に作成した OLE DB 接続マネージャーを使用するように構成して、次の SQL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8b849-155">Add an OLE DB source to the data flow and configure it to use the OLE DB connection manager created previously, and the following SQL command:</span></span>

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  <span data-ttu-id="8b849-156">[ `Parameters` **クエリパラメーターの設定**] ダイアログボックスで [] をクリックし、クエリの単一の入力パラメーターを Dtsclient:: Country 変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="8b849-156">Click `Parameters` and, in the **Set Query Parameters** dialog box, map the single input parameter in the query, Parameter0, to the DtsClient::Country variable.</span></span>

7.  <span data-ttu-id="8b849-157">データ フローに集計変換を追加し、OLE DB ソースの出力を変換に接続します。</span><span class="sxs-lookup"><span data-stu-id="8b849-157">Add an Aggregate transformation to the data flow, and connect the output of the OLE DB source to the transformation.</span></span> <span data-ttu-id="8b849-158">[集計変換エディター] を開き、すべての入力列 (\*) に対して "すべてカウント" 操作を実行し、"顧客カウント" という別名で集計値を出力するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8b849-158">Open the Aggregate Transformation Editor and configure it to perform a "Count all" operation on all input columns (\*) and to output the aggregated value with the alias CustomerCount.</span></span>

8.  <span data-ttu-id="8b849-159">データ フローに DataReader 変換先を追加し、集計変換の出力を DataReader 変換先に接続します。</span><span class="sxs-lookup"><span data-stu-id="8b849-159">Add a DataReader destination to the data flow and connect the output of the Aggregate transformation to the DataReader destination.</span></span> <span data-ttu-id="8b849-160">サンプル コードでは、DataReader の名前として "DataReaderDest" が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8b849-160">The sample code uses "DataReaderDest" as the name of the DataReader.</span></span> <span data-ttu-id="8b849-161">変換先に対して使用可能な単一の入力列 CustomerCount を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b849-161">Select the single available input column, CustomerCount, for the destination.</span></span>

9. <span data-ttu-id="8b849-162">パッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="8b849-162">Save the package.</span></span> <span data-ttu-id="8b849-163">次に作成されたテスト アプリケーションではパッケージが実行され、その出力がメモリから直接取得されます。</span><span class="sxs-lookup"><span data-stu-id="8b849-163">The test application created next will run the package and retrieve its output directly from memory.</span></span>

#### <a name="to-create-the-test-application"></a><span data-ttu-id="8b849-164">テスト アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="8b849-164">To create the test application</span></span>

1.  <span data-ttu-id="8b849-165">新しい Windows フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b849-165">Create a new Windows Forms application.</span></span>

2.  <span data-ttu-id="8b849-166">`Microsoft.SqlServer.Dts.DtsClient` **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**で同じ名前のアセンブリを参照して、名前空間への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="8b849-166">Add a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by browsing to the assembly of the same name in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

3.  <span data-ttu-id="8b849-167">次のサンプル コードをコピーし、フォームのコード モジュールに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8b849-167">Copy and paste the following sample code into the code module for the form.</span></span>

4.  <span data-ttu-id="8b849-168">必要に応じて変数の値を変更して、 `dtexecArgs` パッケージを実行するために**dtexec.exe**に必要なコマンドラインパラメーターが含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="8b849-168">Modify the value of the `dtexecArgs` variable as required so that it contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="8b849-169">サンプル コードは、ファイル システムからパッケージを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8b849-169">The sample code loads the package from the file system.</span></span>

5.  <span data-ttu-id="8b849-170">必要に応じて変数の値を変更して、 `dataReaderName` パッケージ内の DataReader 変換先の名前が含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="8b849-170">Modify the value of the `dataReaderName` variable as required so that it contains the name of the DataReader destination in the package.</span></span>

6.  <span data-ttu-id="8b849-171">ボタンとテキスト ボックスをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="8b849-171">Put a button and a text box on the form.</span></span> <span data-ttu-id="8b849-172">このサンプルコードでは、ボタンの名前としてを使用し、 `btnRun` テキストボックスの名前としてを使用し `txtResults` ます。</span><span class="sxs-lookup"><span data-stu-id="8b849-172">The sample code uses `btnRun` as the name of the button, and `txtResults` as the name of the text box.</span></span>

7.  <span data-ttu-id="8b849-173">アプリケーションを実行し、ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b849-173">Run the application and click the button.</span></span> <span data-ttu-id="8b849-174">パッケージの実行中に一時停止したら、パッケージによって計算された集計値 (Canada の顧客数) が、フォーム上のテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b849-174">After a brief pause while the package runs, you should see the aggregate value calculated by the package (the count of customers in Canada) displayed in the text box on the form.</span></span>

### <a name="sample-code"></a><span data-ttu-id="8b849-175">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="8b849-175">Sample Code</span></span>

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

<span data-ttu-id="8b849-176">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="8b849-176">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8b849-177">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b849-177">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8b849-178">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="8b849-178">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8b849-179">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="8b849-179">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b849-180">参照</span><span class="sxs-lookup"><span data-stu-id="8b849-180">See Also</span></span>
 <span data-ttu-id="8b849-181">ローカル[実行とリモート実行の違いについて](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)[ローカルパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)プログラムによる[リモートパッケージの読み込み](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)と実行</span><span class="sxs-lookup"><span data-stu-id="8b849-181">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) [Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)</span></span>


