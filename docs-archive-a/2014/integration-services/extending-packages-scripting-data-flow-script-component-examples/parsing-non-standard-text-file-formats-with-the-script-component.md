---
title: スクリプト コンポーネントを使用した標準以外のテキスト ファイル形式の解析 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- text file reading [Integration Services]
- Script component [Integration Services], non-standard text file formats
- transformations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: 1fda034d-09e4-4647-9a9f-e8d508c2cc8f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a0ca1a0d10bdad40d39a366864a07d2b0a61d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713317"
---
# <a name="parsing-non-standard-text-file-formats-with-the-script-component"></a><span data-ttu-id="8df05-102">スクリプト コンポーネントを使用した標準以外のテキスト ファイル形式の解析</span><span class="sxs-lookup"><span data-stu-id="8df05-102">Parsing Non-Standard Text File Formats with the Script Component</span></span>
  <span data-ttu-id="8df05-103">ソース データが標準以外の形式の場合、複数の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換を連結するより、すべての解析ロジックを単一のスクリプトに統合する方がより便利で、同じ結果が得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8df05-103">When your source data is arranged in a non-standard format, you may find it more convenient to consolidate all your parsing logic in a single script than to chain together multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations to achieve the same result.</span></span>  
  
 [<span data-ttu-id="8df05-104">例 1: 行区切りのレコードの解析</span><span class="sxs-lookup"><span data-stu-id="8df05-104">Example 1: Parsing Row-Delimited Records</span></span>](#example1)  
  
 [<span data-ttu-id="8df05-105">例 2: 親レコードと子レコードの分割</span><span class="sxs-lookup"><span data-stu-id="8df05-105">Example 2: Splitting Parent and Child Records</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="8df05-106">複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、このスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="8df05-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="8df05-107">詳細については、「 [カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df05-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
##  <a name="example-1-parsing-row-delimited-records"></a><a name="example1"></a> <span data-ttu-id="8df05-108">例 1: 行区切りのレコードの解析</span><span class="sxs-lookup"><span data-stu-id="8df05-108">Example 1: Parsing Row-Delimited Records</span></span>  
 <span data-ttu-id="8df05-109">この例では、データの各列が個別の行に表示されるテキスト ファイルを取得し、スクリプト コンポーネントを使用して解析し、変換先テーブルに入れる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8df05-109">This example shows how to take a text file in which each column of data appears on a separate line and parse it into a destination table by using the Script component.</span></span>  
  
 <span data-ttu-id="8df05-110">データフローで変換として使用するスクリプトコンポーネントを構成する方法の詳細については、「[スクリプトコンポーネントによる同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)」および「[スクリプトコンポーネントによる非同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df05-110">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="8df05-111">このスクリプト コンポーネントの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="8df05-111">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="8df05-112">次のソース データを含む、**rowdelimiteddata.txt** という名前のテキスト ファイルを作成して保存します。</span><span class="sxs-lookup"><span data-stu-id="8df05-112">Create and save a text file named **rowdelimiteddata.txt** that contains the following source data:</span></span>  
  
    ```  
    FirstName: Nancy  
    LastName: Davolio  
    Title: Sales Representative  
    City: Seattle  
    StateProvince: WA  
  
    FirstName: Andrew  
    LastName: Fuller  
    Title: Vice President, Sales  
    City: Tacoma  
    StateProvince: WA  
  
    FirstName: Steven  
    LastName: Buchanan  
    Title: Sales Manager  
    City: London  
    StateProvince:  
  
    ```  
  
2.  <span data-ttu-id="8df05-113">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開き、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8df05-113">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="8df05-114">変換先データベースを選択し、新しいクエリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="8df05-114">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="8df05-115">クエリ ウィンドウで、次のスクリプトを実行して変換先テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-115">In the query window, execute the following script to create the destination table:</span></span>  
  
    ```  
    create table RowDelimitedData  
    (  
    FirstName varchar(32),  
    LastName varchar(32),  
    Title varchar(32),  
    City varchar(32),  
    StateProvince varchar(32)  
    )  
  
    ```  
  
4.  <span data-ttu-id="8df05-116">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を開き、ParseRowDelim.dtsx という名前の新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-116">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named ParseRowDelim.dtsx.</span></span>  
  
5.  <span data-ttu-id="8df05-117">フラット ファイル接続マネージャーをパッケージに追加し、RowDelimitedData という名前を付け、前の手順で作成した rowdelimiteddata.txt ファイルに接続するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-117">Add a Flat File connection manager to the package, name it RowDelimitedData, and configure it to connect to the rowdelimiteddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="8df05-118">OLE DB 接続マネージャーをパッケージに追加し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスと、変換先テーブルを作成したデータベースに接続するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-118">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination table.</span></span>  
  
7.  <span data-ttu-id="8df05-119">データ フロー タスクをパッケージに追加し、SSIS デザイナーの **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8df05-119">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="8df05-120">フラット ファイル ソースをデータ フローに追加し、RowDelimitedData 接続マネージャーを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-120">Add a Flat File Source to the data flow and configure it to use the RowDelimitedData connection manager.</span></span> <span data-ttu-id="8df05-121">**[フラット ファイル ソース エディター]** の **[列]** ページで、単一の使用可能な外部列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8df05-121">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="8df05-122">スクリプト コンポーネントをデータ フローに追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-122">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="8df05-123">フラット ファイル ソースの出力をスクリプト コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="8df05-123">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="8df05-124">スクリプト コンポーネントをダブルクリックし、 **[スクリプト変換エディター]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="8df05-124">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="8df05-125">**[スクリプト変換エディター]** の **[入力列]** ページで、単一の使用可能な入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8df05-125">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="8df05-126">[**スクリプト変換エディター**] の [**入力および出力**] ページで、[出力 0] を選択し、を [なし] に設定し `SynchronousInputID` ます。</span><span class="sxs-lookup"><span data-stu-id="8df05-126">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0 and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="8df05-127">次の 5 つの出力列を、すべて文字列型 [DT_STR]、長さ 32 で作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-127">Create 5 output columns, all of type string [DT_STR] with a length of 32:</span></span>  
  
    -   <span data-ttu-id="8df05-128">FirstName</span><span class="sxs-lookup"><span data-stu-id="8df05-128">FirstName</span></span>  
  
    -   <span data-ttu-id="8df05-129">LastName</span><span class="sxs-lookup"><span data-stu-id="8df05-129">LastName</span></span>  
  
    -   <span data-ttu-id="8df05-130">タイトル</span><span class="sxs-lookup"><span data-stu-id="8df05-130">Title</span></span>  
  
    -   <span data-ttu-id="8df05-131">City</span><span class="sxs-lookup"><span data-stu-id="8df05-131">City</span></span>  
  
    -   <span data-ttu-id="8df05-132">StateProvince</span><span class="sxs-lookup"><span data-stu-id="8df05-132">StateProvince</span></span>  
  
13. <span data-ttu-id="8df05-133">[**スクリプト変換エディター**] の [**スクリプト**] ページで、[**スクリプトの編集**] をクリックし、例のクラスに示されているコードを入力し `ScriptMain` ます。</span><span class="sxs-lookup"><span data-stu-id="8df05-133">On the **Script** page of the **Script Transformation Editor**, click **Edit Script** and enter the code shown in the `ScriptMain` class of the example.</span></span> <span data-ttu-id="8df05-134">スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="8df05-134">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
14. <span data-ttu-id="8df05-135">SQL Server 変換先をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="8df05-135">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="8df05-136">OLE DB 接続マネージャーと RowDelimitedData テーブルを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-136">Configure it to use the OLE DB connection manager and the RowDelimitedData table.</span></span> <span data-ttu-id="8df05-137">スクリプト コンポーネントの出力をこの変換先に接続します。</span><span class="sxs-lookup"><span data-stu-id="8df05-137">Connect the output of the Script Component to this destination.</span></span>  
  
15. <span data-ttu-id="8df05-138">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="8df05-138">Run the package.</span></span> <span data-ttu-id="8df05-139">パッケージが完成したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先テーブル内のレコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="8df05-139">After the package has finished, examine the records in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination table.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Dim columnName As String  
    Dim columnValue As String  
  
    ' Check for an empty row.  
    If Row.Column0.Trim.Length > 0 Then  
        columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"))  
        ' Check for an empty value after the colon.  
        If Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd.Length > 1 Then  
            ' Extract the column value from after the colon and space.  
            columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2)  
            Select Case columnName  
                Case "FirstName"  
                    ' The FirstName value indicates a new record.  
                    Me.Output0Buffer.AddRow()  
                    Me.Output0Buffer.FirstName = columnValue  
                Case "LastName"  
                    Me.Output0Buffer.LastName = columnValue  
                Case "Title"  
                    Me.Output0Buffer.Title = columnValue  
                Case "City"  
                    Me.Output0Buffer.City = columnValue  
                Case "StateProvince"  
                    Me.Output0Buffer.StateProvince = columnValue  
            End Select  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
        string columnName;  
        string columnValue;  
  
        // Check for an empty row.  
        if (Row.Column0.Trim().Length > 0)  
        {  
            columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"));  
            // Check for an empty value after the colon.  
            if (Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd().Length > 1)  
            // Extract the column value from after the colon and space.  
            {  
                columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2);  
                switch (columnName)  
                {  
                    case "FirstName":  
                        // The FirstName value indicates a new record.  
                        this.Output0Buffer.AddRow();  
                        this.Output0Buffer.FirstName = columnValue;  
                        break;  
                    case "LastName":  
                        this.Output0Buffer.LastName = columnValue;  
                        break;  
                    case "Title":  
                        this.Output0Buffer.Title = columnValue;  
                        break;  
                    case "City":  
                        this.Output0Buffer.City = columnValue;  
                        break;  
                    case "StateProvince":  
                        this.Output0Buffer.StateProvince = columnValue;  
                        break;  
                }  
            }  
        }  
  
    }  
```  
  
##  <a name="example-2-splitting-parent-and-child-records"></a><a name="example2"></a> <span data-ttu-id="8df05-140">例 2: 親レコードと子レコードの分割</span><span class="sxs-lookup"><span data-stu-id="8df05-140">Example 2: Splitting Parent and Child Records</span></span>  
 <span data-ttu-id="8df05-141">この例では、親レコードの前に区切り行があり、親レコードの後に行数不定の子レコード行が続くテキスト ファイルを取得し、スクリプト コンポーネントを使用して解析し、適切に正規化された親変換先テーブルと子変換先テーブルに入れる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8df05-141">This example shows how to take a text file, in which a separator row precedes a parent record row that is followed by an indefinite number of child record rows, and parse it into properly normalized parent and child destination tables by using the Script component.</span></span> <span data-ttu-id="8df05-142">この簡単な例は、なんらかの方法で各レコードの先頭と末尾を識別できれば、各親レコードおよび子レコードで複数の行または列を使用するソース ファイルに容易に適用できます。</span><span class="sxs-lookup"><span data-stu-id="8df05-142">This simple example could easily be adapted for source files that use more than one row or column for each parent and child record, as long as there is some way to identify the beginning and end of each record.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8df05-143">このサンプルは、デモンストレーションのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="8df05-143">This sample is intended for demonstration purposes only.</span></span> <span data-ttu-id="8df05-144">サンプルを複数回実行すると、重複したキーの値が変換先テーブルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="8df05-144">If you run the sample more than once, it inserts duplicate key values into the destination table.</span></span>  
  
 <span data-ttu-id="8df05-145">データフローで変換として使用するスクリプトコンポーネントを構成する方法の詳細については、「[スクリプトコンポーネントによる同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)」および「[スクリプトコンポーネントによる非同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df05-145">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="8df05-146">このスクリプト コンポーネントの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="8df05-146">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="8df05-147">次のソース データを含む、**parentchilddata.txt** という名前のテキスト ファイルを作成して保存します。</span><span class="sxs-lookup"><span data-stu-id="8df05-147">Create and save a text file named **parentchilddata.txt** that contains the following source data:</span></span>  
  
    ```  
    **********  
    PARENT 1 DATA  
    child 1 data  
    child 2 data  
    child 3 data  
    child 4 data  
    **********  
    PARENT 2 DATA  
    child 5 data  
    child 6 data  
    child 7 data  
    child 8 data  
    **********  
  
    ```  
  
2.  <span data-ttu-id="8df05-148">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8df05-148">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="8df05-149">変換先データベースを選択し、新しいクエリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="8df05-149">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="8df05-150">クエリ ウィンドウで、次のスクリプトを実行して変換先テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-150">In the query window, execute the following script to create the destination tables:</span></span>  
  
    ```  
    CREATE TABLE [dbo].[Parents]([ParentID] [int] NOT NULL,  
    [ParentRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Parents] PRIMARY KEY CLUSTERED   
    ([ParentID] ASC))  
    GO  
    CREATE TABLE [dbo].[Children]([ChildID] [int] NOT NULL,  
    [ParentID] [int] NOT NULL,  
    [ChildRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Children] PRIMARY KEY CLUSTERED   
    ([ChildID] ASC))  
    GO  
    ALTER TABLE [dbo].[Children] ADD CONSTRAINT [FK_Children_Parents] FOREIGN KEY([ParentID])  
    REFERENCES [dbo].[Parents] ([ParentID])  
  
    ```  
  
4.  <span data-ttu-id="8df05-151">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を開き、SplitParentChild.dtsx という名前の新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-151">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named SplitParentChild.dtsx.</span></span>  
  
5.  <span data-ttu-id="8df05-152">フラット ファイル接続マネージャーをパッケージに追加し、ParentChildData という名前を付け、前の手順で作成した parentchilddata.txt ファイルに接続するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-152">Add a Flat File connection manager to the package, name it ParentChildData, and configure it to connect to the parentchilddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="8df05-153">OLE DB 接続マネージャーをパッケージに追加し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスと、変換先テーブルを作成したデータベースに接続するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-153">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination tables.</span></span>  
  
7.  <span data-ttu-id="8df05-154">データ フロー タスクをパッケージに追加し、SSIS デザイナーの **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8df05-154">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="8df05-155">フラット ファイル ソースをデータ フローに追加し、ParentChildData 接続マネージャーを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-155">Add a Flat File Source to the data flow and configure it to use the ParentChildData connection manager.</span></span> <span data-ttu-id="8df05-156">**[フラット ファイル ソース エディター]** の **[列]** ページで、単一の使用可能な外部列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8df05-156">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="8df05-157">スクリプト コンポーネントをデータ フローに追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-157">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="8df05-158">フラット ファイル ソースの出力をスクリプト コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="8df05-158">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="8df05-159">スクリプト コンポーネントをダブルクリックし、 **[スクリプト変換エディター]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="8df05-159">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="8df05-160">**[スクリプト変換エディター]** の **[入力列]** ページで、単一の使用可能な入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="8df05-160">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="8df05-161">[**スクリプト変換エディター**] の [**入力および出力**] ページで、出力0を選択し、parentrecords に名前を変更して、 `SynchronousInputID` を None に設定します。</span><span class="sxs-lookup"><span data-stu-id="8df05-161">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0, rename it to ParentRecords, and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="8df05-162">次の 2 つの出力列を作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-162">Create 2 output columns:</span></span>  
  
    -   <span data-ttu-id="8df05-163">ParentID (主キー)、4 バイト符号付き整数型 [DT_I4]</span><span class="sxs-lookup"><span data-stu-id="8df05-163">ParentID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="8df05-164">ParentRecord、文字列型 [DT_STR]、長さ 32</span><span class="sxs-lookup"><span data-stu-id="8df05-164">ParentRecord, of type string [DT_STR] with a length of 32.</span></span>  
  
13. <span data-ttu-id="8df05-165">2 つ目の出力を作成し、ChildRecords という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="8df05-165">Create a second output and name it ChildRecords.</span></span> <span data-ttu-id="8df05-166">新しい出力の `SynchronousInputID` は既に None に設定されています。</span><span class="sxs-lookup"><span data-stu-id="8df05-166">The `SynchronousInputID` of the new output is already set to None.</span></span> <span data-ttu-id="8df05-167">次の 3 つの出力列を作成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-167">Create 3 output columns:</span></span>  
  
    -   <span data-ttu-id="8df05-168">ChildID (主キー)、4 バイト符号付き整数型 [DT_I4]</span><span class="sxs-lookup"><span data-stu-id="8df05-168">ChildID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="8df05-169">ParentID (外部キー)、4 バイト符号付き整数型 [DT_I4]</span><span class="sxs-lookup"><span data-stu-id="8df05-169">ParentID (the foreign key), also of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="8df05-170">ChildRecord、文字列型 [DT_STR]、長さ 50</span><span class="sxs-lookup"><span data-stu-id="8df05-170">ChildRecord, of type string [DT_STR] with a length of 50</span></span>  
  
14. <span data-ttu-id="8df05-171">**[スクリプト変換エディター]** の **[スクリプト]** ページで、 **[スクリプトの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8df05-171">On the **Script** page of the **Script Transformation Editor**, click **Edit Script**.</span></span> <span data-ttu-id="8df05-172">`ScriptMain` クラスに、例に示すコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8df05-172">In the `ScriptMain` class, enter the code shown in the example.</span></span> <span data-ttu-id="8df05-173">スクリプト開発環境と **[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="8df05-173">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
15. <span data-ttu-id="8df05-174">SQL Server 変換先をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="8df05-174">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="8df05-175">スクリプト コンポーネントの ParentRecords 出力をこの変換先に接続します。OLE DB 接続マネージャーと Parents テーブルを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-175">Connect the ParentRecords output of the Script Component to this destination.Configure it to use the OLE DB connection manager and the Parents table.</span></span>  
  
16. <span data-ttu-id="8df05-176">別の SQL Server 変換先をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="8df05-176">Add another SQL Server Destination to the data flow.</span></span> <span data-ttu-id="8df05-177">スクリプト コンポーネントの ChildRecords 出力をこの変換先に接続します。</span><span class="sxs-lookup"><span data-stu-id="8df05-177">Connect the ChildRecords output of the Script Component to this destination.</span></span> <span data-ttu-id="8df05-178">OLE DB 接続マネージャーと Children テーブルを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="8df05-178">Configure it to use the OLE DB connection manager and the Children table.</span></span>  
  
17. <span data-ttu-id="8df05-179">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="8df05-179">Run the package.</span></span> <span data-ttu-id="8df05-180">パッケージが完成したら、2 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先テーブル内の親レコードと子レコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="8df05-180">After the package has finished, examine the parent and child records in the two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination tables.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Static nextRowIsParent As Boolean = False  
    Static parentCounter As Integer = 0  
    Static childCounter As Integer = 0  
  
    ' If current row starts with separator characters,  
    '  then following row contains new parent record.  
    If Row.Column0.StartsWith("***") Then  
        nextRowIsParent = True  
    Else  
        If nextRowIsParent Then  
            ' Current row contains parent record.  
            parentCounter += 1  
            Me.ParentRecordsBuffer.AddRow()  
            Me.ParentRecordsBuffer.ParentID = parentCounter  
            Me.ParentRecordsBuffer.ParentRecord = Row.Column0  
            nextRowIsParent = False  
        Else  
            ' Current row contains child record.  
            childCounter += 1  
            Me.ChildRecordsBuffer.AddRow()  
            Me.ChildRecordsBuffer.ChildID = childCounter  
            Me.ChildRecordsBuffer.ParentID = parentCounter  
            Me.ChildRecordsBuffer.ChildRecord = Row.Column0  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
    int static_Input0_ProcessInputRow_childCounter = 0;  
    int static_Input0_ProcessInputRow_parentCounter = 0;  
    bool static_Input0_ProcessInputRow_nextRowIsParent = false;  
  
        // If current row starts with separator characters,   
        // then following row contains new parent record.   
        if (Row.Column0.StartsWith("***"))  
        {  
            static_Input0_ProcessInputRow_nextRowIsParent = true;  
        }  
        else  
        {  
            if (static_Input0_ProcessInputRow_nextRowIsParent)  
            {  
                // Current row contains parent record.   
                static_Input0_ProcessInputRow_parentCounter += 1;  
                this.ParentRecordsBuffer.AddRow();  
                this.ParentRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ParentRecordsBuffer.ParentRecord = Row.Column0;  
                static_Input0_ProcessInputRow_nextRowIsParent = false;  
            }  
            else  
            {  
                // Current row contains child record.   
                static_Input0_ProcessInputRow_childCounter += 1;  
                this.ChildRecordsBuffer.AddRow();  
                this.ChildRecordsBuffer.ChildID = static_Input0_ProcessInputRow_childCounter;  
                this.ChildRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ChildRecordsBuffer.ChildRecord = Row.Column0;  
            }  
        }  
  
    }  
```  
  
<span data-ttu-id="8df05-181">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="8df05-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8df05-182">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df05-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8df05-183">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="8df05-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8df05-184">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="8df05-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df05-185">参照</span><span class="sxs-lookup"><span data-stu-id="8df05-185">See Also</span></span>  
 [<span data-ttu-id="8df05-186">スクリプト コンポーネントによる同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="8df05-186">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 [<span data-ttu-id="8df05-187">スクリプト コンポーネントによる非同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="8df05-187">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  
