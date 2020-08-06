---
title: Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: a5393c1a-cc37-491a-a260-7aad84dbff68
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51de779b6869d80245302741035e6169aa750c83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639586"
---
# <a name="loop-through-excel-files-and-tables-by-using-a-foreach-loop-container"></a><span data-ttu-id="5856b-102">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="5856b-102">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>
  <span data-ttu-id="5856b-103">このトピックの手順では、Foreach ループ コンテナーと適切な列挙子を使用して、フォルダー内の Excel ブックまたは Excel ブック内のテーブルをループ処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5856b-103">The procedures in this topic describe how to loop through the Excel workbooks in a folder, or through the tables in an Excel workbook, by using the Foreach Loop container with the appropriate enumerator.</span></span>  
  
### <a name="to-loop-through-excel-files-by-using-the-foreach-file-enumerator"></a><span data-ttu-id="5856b-104">Foreach File 列挙子を使用して Excel ファイルをループ処理するには</span><span class="sxs-lookup"><span data-stu-id="5856b-104">To loop through Excel files by using the Foreach File enumerator</span></span>  
  
1.  <span data-ttu-id="5856b-105">ループの反復ごとに現在の Excel のパスとファイル名を受け取る文字列変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5856b-105">Create a string variable that will receive the current Excel path and file name on each iteration of the loop.</span></span> <span data-ttu-id="5856b-106">検証で問題が発生しないようにするには、変数の初期値として Excel の有効なパスとファイル名を割り当てます</span><span class="sxs-lookup"><span data-stu-id="5856b-106">To avoid validation issues, assign a valid Excel path and file name as the initial value of the variable.</span></span> <span data-ttu-id="5856b-107">(この手順の後半で示すサンプル式では、 `ExcelFile`という変数名を使用します)。</span><span class="sxs-lookup"><span data-stu-id="5856b-107">(The sample expression shown later in this procedure uses the variable name, `ExcelFile`.)</span></span>  
  
2.  <span data-ttu-id="5856b-108">必要に応じて、Excel 接続文字列の Extended Properties 引数の値を保持する別の文字列変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5856b-108">Optionally, create another string variable that will hold the value for the Extended Properties argument of the Excel connection string.</span></span> <span data-ttu-id="5856b-109">この引数には、Excel のバージョンを指定したり、最初の行に列名が含まれているかどうか、およびインポート モードが使用されるかどうかを判断する一連の値が格納されます</span><span class="sxs-lookup"><span data-stu-id="5856b-109">This argument contains a series of values that specify the Excel version and determine whether the first row contains column names, and whether import mode is used.</span></span> <span data-ttu-id="5856b-110">(この手順の後半で示すサンプル式では、初期値が " `ExtProperties`" である`Excel 8.0;HDR=Yes`という名前の変数を使用しています)。</span><span class="sxs-lookup"><span data-stu-id="5856b-110">(The sample expression shown later in this procedure uses the variable name `ExtProperties`, with an initial value of "`Excel 8.0;HDR=Yes`".)</span></span>  
  
     <span data-ttu-id="5856b-111">Extended Properties 引数の値を格納している変数を使用しない場合は、接続文字列を含む式に引数の値を手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5856b-111">If you do not use a variable for the Extended Properties argument, then you must add it manually to the expression that contains the connection string.</span></span>  
  
3.  <span data-ttu-id="5856b-112">[**制御フロー** ] タブに Foreach ループコンテナーを追加します。Foreach ループコンテナーの構成方法については、「 [Foreach ループコンテナーを構成](foreach-loop-container.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5856b-112">Add a Foreach Loop container to the **Control Flow** tab. For information about how to configure the Foreach Loop Container, see [Configure a Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
4.  <span data-ttu-id="5856b-113">**[Foreach ループ エディター]** の **[コレクション]** ページで [Foreach File 列挙子] を選択し、Excel ブックが存在するフォルダーを指定して、ファイル フィルター (通常は \*.xls) を指定します。</span><span class="sxs-lookup"><span data-stu-id="5856b-113">On the **Collection** page of the **Foreach Loop Editor**, select the Foreach File enumerator, specify the folder in which the Excel workbooks are located, and specify the file filter (ordinarily \*.xls).</span></span>  
  
5.  <span data-ttu-id="5856b-114">**[変数のマッピング]** ページで、ループの反復ごとに現在の Excel のパスとファイル名を受け取るユーザー定義文字列変数に、インデックス 0 をマップします。</span><span class="sxs-lookup"><span data-stu-id="5856b-114">On the **Variable Mapping** page, map Index 0 to a user-defined string variable that will receive the current Excel path and file name on each iteration of the loop.</span></span> <span data-ttu-id="5856b-115">(この手順の後半で示すサンプル式では、 `ExcelFile`という変数名を使用します)。</span><span class="sxs-lookup"><span data-stu-id="5856b-115">(The sample expression shown later in this procedure uses the variable name `ExcelFile`.)</span></span>  
  
6.  <span data-ttu-id="5856b-116">**[Foreach ループ エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="5856b-116">Close the **Foreach Loop Editor**.</span></span>  
  
7.  <span data-ttu-id="5856b-117">「 [パッケージの接続マネージャーを追加、削除、または共有する](../add-delete-or-share-a-connection-manager-in-a-package.md)」(パッケージでの接続マネージャーの追加、削除、または共有) の説明に従って、Excel 接続マネージャーをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="5856b-117">Add an Excel connection manager to the package as described in [Add, Delete, or Share a Connection Manager in a Package](../add-delete-or-share-a-connection-manager-in-a-package.md).</span></span> <span data-ttu-id="5856b-118">接続時に検証エラーが発生しないように、既存の Excel ブック ファイルを選択してください。</span><span class="sxs-lookup"><span data-stu-id="5856b-118">Select an existing Excel workbook file for the connection to avoid validation errors.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5856b-119">この Excel 接続マネージャーを使用するデータ フロー コンポーネントとタスクを構成する際、検証エラーが発生しないようにするには、 **[Excel 接続マネージャー]** で既存の Excel ブックを選択します。</span><span class="sxs-lookup"><span data-stu-id="5856b-119">To avoid validation errors as you configure tasks and data flow components that use this Excel connection manager, select an existing Excel workbook in the **Excel Connection Manager Editor**.</span></span> <span data-ttu-id="5856b-120">以下の手順に従って `ConnectionString` プロパティ用の式を構成した後は、接続マネージャーは実行時にこのブックを使用しなくなります。</span><span class="sxs-lookup"><span data-stu-id="5856b-120">The connection manager will not use this workbook at run time after you configure an expression for the `ConnectionString` property as described in the following steps.</span></span> <span data-ttu-id="5856b-121">パッケージを作成して構成したら、[プロパティ] ウィンドウで `ConnectionString` プロパティの値を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="5856b-121">After you create and configure the package, you can clear the value of the `ConnectionString` property in the Properties window.</span></span> <span data-ttu-id="5856b-122">ただし、この値を削除すると、Excel 接続マネージャーの接続文字列プロパティは Foreach ループが実行されるまで無効になります。</span><span class="sxs-lookup"><span data-stu-id="5856b-122">However, if you clear this value, the connection string property of the Excel connection manager is no longer valid until the Foreach Loop runs.</span></span> <span data-ttu-id="5856b-123">したがって、接続マネージャーを使用するタスクまたはパッケージでは、検証エラーが発生しないように、`DelayValidation` プロパティを `True` に設定してください。</span><span class="sxs-lookup"><span data-stu-id="5856b-123">Therefore you must set the `DelayValidation` property to `True` on the tasks in which the connection manager is used, or on the package, to avoid validation errors.</span></span>  
    >   
    >  <span data-ttu-id="5856b-124">また、Excel 接続マネージャーの `False` プロパティでは既定値の `RetainSameConnection` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5856b-124">You must also use the default value of `False` for the `RetainSameConnection` property of the Excel connection manager.</span></span> <span data-ttu-id="5856b-125">この値を `True` に変更すると、ループの各反復処理で最初の Excel ブックが繰り返し開かれるようになります。</span><span class="sxs-lookup"><span data-stu-id="5856b-125">If you change this value to `True`, each iteration of the loop will continue to open the first Excel workbook.</span></span>  
  
8.  <span data-ttu-id="5856b-126">新しい Excel 接続マネージャーを選択し、[プロパティ] ウィンドウで **[式]** プロパティをクリックして、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5856b-126">Select the new Excel connection manager, click the **Expressions** property in the Properties window, and then click the ellipsis.</span></span>  
  
9. <span data-ttu-id="5856b-127">[**プロパティ式エディター**] で、プロパティを選択し、 `ConnectionString` 省略記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5856b-127">In the **Property Expressions Editor**, select the `ConnectionString` property, and then click the ellipsis.</span></span>  
  
10. <span data-ttu-id="5856b-128">式ビルダーで、次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="5856b-128">In the Expression Builder, enter the following expression:</span></span>  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=\"" + @[User::ExtProperties] + "\""  
    ```  
  
     <span data-ttu-id="5856b-129">拡張プロパティ引数の値の前後に必要な内側の引用符をエスケープするために、エスケープ文字 "\\" を使用していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5856b-129">Note the use of the escape character "\\" to escape the inner quotation marks required around the value of the Extended Properties argument.</span></span>  
  
     <span data-ttu-id="5856b-130">Extended Properties 引数は省略できません。</span><span class="sxs-lookup"><span data-stu-id="5856b-130">The Extended Properties argument is not optional.</span></span> <span data-ttu-id="5856b-131">引数の値を格納している変数を使用しない場合は、Excel 2003 ファイルの次の例に示すように、式に引数の値を手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5856b-131">If you do not use a variable to contain its value, then you must add it manually to the expression, as in the following example for an Excel 2003 file:</span></span>  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=Excel 8.0"  
    ```  
  
11. <span data-ttu-id="5856b-132">Foreach ループ コンテナー内で、Excel 接続マネージャーを使用して、指定したファイルの場所とパターンに一致した各 Excel ブックに対して同じ操作を実行するタスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="5856b-132">Create tasks in the Foreach Loop container that use the Excel connection manager to perform the same operations on each Excel workbook that matches the specified file location and pattern.</span></span>  
  
### <a name="to-loop-through-excel-tables-by-using-the-foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="5856b-133">Foreach ADO.NET Schema Rowset 列挙子を使用して Excel テーブルをループ処理するには</span><span class="sxs-lookup"><span data-stu-id="5856b-133">To loop through Excel tables by using the Foreach ADO.NET Schema Rowset enumerator</span></span>  
  
1.  <span data-ttu-id="5856b-134">Microsoft Jet OLE DB Provider を使用して Excel ブックに接続する ADO.NET 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5856b-134">Create an ADO.NET connection manager that uses the Microsoft Jet OLE DB Provider to connect to an Excel workbook.</span></span> <span data-ttu-id="5856b-135">**[接続マネージャー]** ダイアログ ボックスの [すべて] ページで、Extended Properties プロパティの値として「Excel 8.0」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5856b-135">On the All page of the **Connection Manager** dialog box, make sure that you enter Excel 8.0 as the value of the Extended Properties property.</span></span> <span data-ttu-id="5856b-136">詳細については、「 [パッケージでの接続マネージャーの追加、削除、または共有](../add-delete-or-share-a-connection-manager-in-a-package.md)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5856b-136">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
2.  <span data-ttu-id="5856b-137">ループの反復ごとに現在のテーブルの名前を受け取る文字列変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5856b-137">Create a string variable that will receive the name of the current table on each iteration of the loop.</span></span>  
  
3.  <span data-ttu-id="5856b-138">[**制御フロー** ] タブに Foreach ループコンテナーを追加します。Foreach ループコンテナーの構成方法については、「 [Foreach ループコンテナーを構成](foreach-loop-container.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5856b-138">Add a Foreach Loop container to the **Control Flow** tab. For information about how to configure the Foreach Loop container, see [Configure a Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
4.  <span data-ttu-id="5856b-139">**[Foreach ループ エディター]** の **[コレクション]** ページで、Foreach ADO.NET Schema Rowset 列挙子を選択します。</span><span class="sxs-lookup"><span data-stu-id="5856b-139">On the **Collection** page of the **Foreach Loop Editor**, select the Foreach ADO.NET Schema Rowset enumerator.</span></span>  
  
5.  <span data-ttu-id="5856b-140">**[コレクション]** の値として、以前に作成した ADO.NET 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="5856b-140">As the value of **Connection**, select the ADO.NET connection manager that you created previously.</span></span>  
  
6.  <span data-ttu-id="5856b-141">**[スキーマ]** の値として、[テーブル] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5856b-141">As the value of **Schema**, select Tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5856b-142">Excel ブック内のテーブルの一覧には、ワークシート ($ サフィックスが付きます) と名前付き範囲が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5856b-142">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="5856b-143">ワークシートのみ、または名前付き範囲のみを一覧からフィルター選択する場合は、そのためのカスタム コードをスクリプト タスクで記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5856b-143">If you have to filter the list for only worksheets or only named ranges, you may have to write custom code in a Script task for this purpose.</span></span> <span data-ttu-id="5856b-144">詳しくは、「 [スクリプト タスクを使用した Excel ファイルの操作](script-task.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5856b-144">For more information, see [Working with Excel Files with the Script Task](script-task.md).</span></span>  
  
7.  <span data-ttu-id="5856b-145">**[変数のマッピング]** ページで、以前に作成した文字列変数にインデックス 2 をマップし、現在のテーブルの名前を保持します。</span><span class="sxs-lookup"><span data-stu-id="5856b-145">On the **Variable Mappings** page, map Index 2 to the string variable created earlier to hold the name of the current table.</span></span>  
  
8.  <span data-ttu-id="5856b-146">**[Foreach ループ エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="5856b-146">Close the **Foreach Loop Editor**.</span></span>  
  
9. <span data-ttu-id="5856b-147">Foreach ループ コンテナー内で、Excel 接続マネージャーを使用して、指定したブック内の各 Excel テーブルに対して同じ操作を実行するタスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="5856b-147">Create tasks in the Foreach Loop container that use the Excel connection manager to perform the same operations on each Excel table in the specified workbook.</span></span> <span data-ttu-id="5856b-148">スクリプト タスクを使用して、列挙されるテーブル名を調べたり各テーブルを操作したりする場合、スクリプト タスクの ReadOnlyVariables プロパティに文字列変数を追加することを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="5856b-148">If you use a Script Task to examine the enumerated table name or to work with each table, remember to add the string variable to the ReadOnlyVariables property of the Script task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5856b-149">参照</span><span class="sxs-lookup"><span data-stu-id="5856b-149">See Also</span></span>  
 <span data-ttu-id="5856b-150">[SQL Server Integration Services (SSIS) を使用した excel からのデータのインポートまたは excel へのデータのエクスポート](../load-data-to-from-excel-with-ssis.md) [Foreach ループコンテナーの構成](foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="5856b-150">[Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md) [Configure a Foreach Loop Container](foreach-loop-container.md) </span></span>  
 <span data-ttu-id="5856b-151">[プロパティ式を追加または変更する](../expressions/add-or-change-a-property-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5856b-151">[Add or Change a Property Expression](../expressions/add-or-change-a-property-expression.md) </span></span>  
 <span data-ttu-id="5856b-152">[Excel 接続マネージャー](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5856b-152">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 <span data-ttu-id="5856b-153">[Excel ソース](../data-flow/excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="5856b-153">[Excel Source](../data-flow/excel-source.md) </span></span>  
 <span data-ttu-id="5856b-154">[Excel 変換先](../data-flow/excel-destination.md) </span><span class="sxs-lookup"><span data-stu-id="5856b-154">[Excel Destination](../data-flow/excel-destination.md) </span></span>  
 [<span data-ttu-id="5856b-155">スクリプト タスクを使用した Excel ファイルの操作</span><span class="sxs-lookup"><span data-stu-id="5856b-155">Working with Excel Files with the Script Task</span></span>](script-task.md)  
  
  
