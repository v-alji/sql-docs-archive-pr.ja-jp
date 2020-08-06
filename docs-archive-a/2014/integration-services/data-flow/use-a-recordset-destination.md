---
title: レコードセット変換先を使用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Recordset destination
ms.assetid: a7b143dc-8008-404f-83b0-b45ffbca6029
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34d1d5a7aa76876a9d8718b691b1d24a8835e2e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644037"
---
# <a name="use-a-recordset-destination"></a><span data-ttu-id="75421-102">レコードセット変換先を使用する</span><span class="sxs-lookup"><span data-stu-id="75421-102">Use a Recordset Destination</span></span>
  <span data-ttu-id="75421-103">レコードセット変換先では、データは外部データ ソースに保存されません。</span><span class="sxs-lookup"><span data-stu-id="75421-103">The Recordset destination does not save data to an external data source.</span></span> <span data-ttu-id="75421-104">代わりに、レコードセット変換先では、`Object` データ型の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ変数に格納されるレコードセットのメモリにデータが保存されます。</span><span class="sxs-lookup"><span data-stu-id="75421-104">Instead, the Recordset destination saves data in memory in a recordset that is stored in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package variable of the `Object` data type.</span></span> <span data-ttu-id="75421-105">レコードセット変換先でデータが保存されたら、通常、Foreach ループ コンテナーと Foreach ADO 列挙子を使用して、一度に 1 つのレコードセット行を処理します。</span><span class="sxs-lookup"><span data-stu-id="75421-105">After the Recordset destination saves the data, you typically use a Foreach Loop container with the Foreach ADO enumerator to process one row of the recordset at a time.</span></span> <span data-ttu-id="75421-106">Foreach ADO 列挙子によって、現在の行の各列の値が個別のパッケージ変数に保存されます。</span><span class="sxs-lookup"><span data-stu-id="75421-106">The Foreach ADO enumerator saves the value from each column of the current row into a separate package variable.</span></span> <span data-ttu-id="75421-107">その後、Foreach ループ コンテナー内で構成したタスクによって変数から値が読み取られ、その値を使用してアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="75421-107">Then, the tasks that you configure inside the Foreach Loop container read those values from the variables and perform some action with them.</span></span>  
  
 <span data-ttu-id="75421-108">レコードセット変換先は、さまざまなシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="75421-108">You can use the Recordset destination in many different scenarios.</span></span> <span data-ttu-id="75421-109">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="75421-109">Here are some examples:</span></span>  
  
-   <span data-ttu-id="75421-110">メール送信タスクと [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式言語を使用して、レコードセットの行ごとにカスタマイズされた電子メール メッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="75421-110">You can use a Send Mail task and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language to send a customized e-mail message for each row in the recordset.</span></span>  
  
-   <span data-ttu-id="75421-111">データ フロー タスク内で変換元として構成されたスクリプト コンポーネントを使用して、列値をデータ フローの列に読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="75421-111">You can use a Script component configured as a source, inside a Data Flow task, to read the column values into the columns of the data flow.</span></span> <span data-ttu-id="75421-112">その後、変換や変換先を使用して、行を変換および保存できます。</span><span class="sxs-lookup"><span data-stu-id="75421-112">Then, you can use transformations and destinations to transform and save the row.</span></span> <span data-ttu-id="75421-113">この例では、データ フロー タスクが行ごとに 1 回実行されます。</span><span class="sxs-lookup"><span data-stu-id="75421-113">In this example, the Data Flow task runs once for each row.</span></span>  
  
 <span data-ttu-id="75421-114">ここでは、まずレコードセット変換先を使用する一般的な手順について説明し、次に変換先の使用方法の具体的な例を示します。</span><span class="sxs-lookup"><span data-stu-id="75421-114">The following sections first describe the general process of using the Recordset destination and then show a specific example of how to use the destination.</span></span>  
  
## <a name="general-steps-to-using-a-recordset-destination"></a><span data-ttu-id="75421-115">レコードセット変換先を使用する一般的な手順</span><span class="sxs-lookup"><span data-stu-id="75421-115">General Steps to Using a Recordset Destination</span></span>  
 <span data-ttu-id="75421-116">次の手順は、レコードセット変換先にデータを保存し、Foreach ループ コンテナーを使用して各行を処理するために必要な手順をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="75421-116">The following procedure summarizes the steps that are required to save data to a Recordset destination, and then use the Foreach Loop container to process each row.</span></span>  
  
#### <a name="to-save-data-to-a-recordset-destination-and-process-each-row-by-using-the-foreach-loop-container"></a><span data-ttu-id="75421-117">レコードセット変換先にデータを保存し、Foreach ループ コンテナーを使用して各行を処理するには</span><span class="sxs-lookup"><span data-stu-id="75421-117">To save data to a Recordset destination and process each row by using the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="75421-118">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="75421-118">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="75421-119">レコードセット変換先でメモリに保存されたレコードセットを格納する変数を作成し、変数の型を `Object` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75421-119">Create a variable that will contain the recordset saved into memory by the Recordset destination, and set the variable's type to `Object`.</span></span>  
  
3.  <span data-ttu-id="75421-120">使用するレコードセットの各列の値を格納するために、適切な型の追加の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="75421-120">Create additional variables of the appropriate types to contain the values of each column in the recordset that you want to use.</span></span>  
  
4.  <span data-ttu-id="75421-121">データ フローで使用するデータ ソースに必要な接続マネージャーを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-121">Add and configure the connection manager required by the data source that you plan to use in your data flow.</span></span>  
  
5.  <span data-ttu-id="75421-122">データ フロー タスクをパッケージに追加し、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [データ フロー] タブで、データの読み込みおよび変換を行うための変換元および変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-122">Add a Data Flow task to the package, and on the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, configure sources and transformations to load and transform the data.</span></span>  
  
6.  <span data-ttu-id="75421-123">レコードセット変換先をデータ フローに追加し、変換に接続します。</span><span class="sxs-lookup"><span data-stu-id="75421-123">Add a Recordset destination to the data flow and connect it to the transformations.</span></span> <span data-ttu-id="75421-124">レコードセット変換先の `VariableName` プロパティに、レコードセットを格納するために作成した変数の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="75421-124">For the `VariableName` property of the Recordset destination, enter the name of the variable that you created to hold the recordset.</span></span>  
  
7.  <span data-ttu-id="75421-125">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [制御フロー] タブで、Foreach ループ コンテナーを追加し、このコンテナーをデータ フロー タスクの後に連結します。</span><span class="sxs-lookup"><span data-stu-id="75421-125">On the Control Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container and connect this container after the Data Flow task.</span></span> <span data-ttu-id="75421-126">**[Foreach ループ エディター]** を開いて、次の設定を使用してコンテナーを構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-126">Then, open the **Foreach Loop Editor** to configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="75421-127">**[コレクション]** ページで、[Foreach ADO 列挙子] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75421-127">On the **Collection** page, select the Foreach ADO Enumerator.</span></span> <span data-ttu-id="75421-128">次に、 **[ADO オブジェクト ソース変数]** で、レコードセットが含まれる変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="75421-128">Then, for **ADO object source variable**, select the variable that contains the recordset.</span></span>  
  
    2.  <span data-ttu-id="75421-129">**[変数のマッピング]** ページで、使用する各列の 0 から始まるインデックスを適切な変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="75421-129">On the **Variable Mappings** page, map the zero-based index of each column that you want to use to the appropriate variable.</span></span>  
  
         <span data-ttu-id="75421-130">ループの各反復処理で、列挙子によってこれらの変数に現在の行の列値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="75421-130">On each iteration of the loop, the enumerator populates these variables with the column values from the current row.</span></span>  
  
8.  <span data-ttu-id="75421-131">Foreach ループ コンテナー内にタスクを追加し、変数から値を読み取って一度に 1 つのレコードセット行を処理するように構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-131">Inside the Foreach Loop container, add and configure tasks to process one row of the recordset at a time by reading the values from the variables.</span></span>  
  
## <a name="example-of-using-the-recordset-destination"></a><span data-ttu-id="75421-132">レコードセット変換先の使用例</span><span class="sxs-lookup"><span data-stu-id="75421-132">Example of Using the Recordset Destination</span></span>  
 <span data-ttu-id="75421-133">次の例では、データ フロー タスクが [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] の従業員に関する情報を Sales.SalesPerson テーブルからレコードセット変換先に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="75421-133">In the following example, the Data Flow task loads information about [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] employees from the Sales.SalesPerson table into a Recordset destination.</span></span> <span data-ttu-id="75421-134">次に、Foreach ループ コンテナーが一度に 1 つのデータ行を読み取って、メール送信タスクを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="75421-134">Then, a Foreach Loop container reads one row of data at a time, and calls a Send Mail task.</span></span> <span data-ttu-id="75421-135">メール送信タスクは、式を使用して、ボーナス額に関するカスタマイズされた電子メール メッセージを各販売員に送信します。</span><span class="sxs-lookup"><span data-stu-id="75421-135">The Send Mail task uses expressions to send a customized e-mail message to each salesperson about the amount of his or her bonus.</span></span>  
  
#### <a name="to-create-the-project-and-configure-the-variables"></a><span data-ttu-id="75421-136">プロジェクトを作成して変数を構成するには</span><span class="sxs-lookup"><span data-stu-id="75421-136">To create the project and configure the variables</span></span>  
  
1.  <span data-ttu-id="75421-137">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="75421-137">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="75421-138">**[SSIS]** メニューの **[変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75421-138">On the **SSIS** menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="75421-139">**[変数]** ウィンドウで、レコードセットと現在の行の列値を格納する変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="75421-139">In the **Variables** window, create the variables that will hold the recordset and the column values from the current row:</span></span>  
  
    1.  <span data-ttu-id="75421-140">`BonusRecordset` という名前の変数を作成し、その型を `Object` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75421-140">Create a variable named, `BonusRecordset`, and set its type to `Object`.</span></span>  
  
         <span data-ttu-id="75421-141">`BonusRecordset` 変数にはレコードセットが格納されます。</span><span class="sxs-lookup"><span data-stu-id="75421-141">The `BonusRecordset` variable holds the recordset.</span></span>  
  
    2.  <span data-ttu-id="75421-142">`EmailAddress` という名前の変数を作成し、その型を `String` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75421-142">Create a variable named, `EmailAddress`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="75421-143">`EmailAddress` 変数には販売員の電子メール アドレスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="75421-143">The `EmailAddress` variable holds the salesperson's e-mail address.</span></span>  
  
    3.  <span data-ttu-id="75421-144">`FirstName` という名前の変数を作成し、その型を `String` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75421-144">Create a variable named, `FirstName`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="75421-145">`FirstName` 変数には販売員の名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="75421-145">The `FirstName` variable holds the salesperson's first name.</span></span>  
  
    4.  <span data-ttu-id="75421-146">`Bonus` という名前の変数を作成し、その型を `Double` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75421-146">Create a variable named, `Bonus`, and set its type to `Double`.</span></span>  
  
         <span data-ttu-id="75421-147">`Bonus` 変数には販売員のボーナス額が格納されます。</span><span class="sxs-lookup"><span data-stu-id="75421-147">The `Bonus` variable holds the amount of the salesperson's bonus.</span></span>  
  
#### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="75421-148">接続マネージャーを構成するには</span><span class="sxs-lookup"><span data-stu-id="75421-148">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="75421-149">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [接続マネージャー] 領域で、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベースに接続する新しい OLE DB 接続マネージャーを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-149">In the Connection Managers area of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add and configure a new OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>  
  
     <span data-ttu-id="75421-150">この接続マネージャーは、データ フロー タスクの OLE DB ソースがデータを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="75421-150">The OLE DB source in the Data Flow task will use this connection manager to retrieve data.</span></span>  
  
2.  <span data-ttu-id="75421-151">[接続マネージャー] 領域で、使用可能な SMTP サーバーに接続する新しい SMTP 接続マネージャーを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-151">In the Connection Managers area, add and configure a new SMTP connection manager that connects to an available SMTP server.</span></span>  
  
     <span data-ttu-id="75421-152">この接続マネージャーは、Foreach ループ コンテナー内のメール送信タスクが電子メールを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="75421-152">The Send Mail task inside the Foreach Loop container will use this connection manager to send emails.</span></span>  
  
#### <a name="to-configure-the-data-flow-and-the-recordset-destination"></a><span data-ttu-id="75421-153">データ フローとレコードセット変換先を構成するには</span><span class="sxs-lookup"><span data-stu-id="75421-153">To configure the data flow and the Recordset Destination</span></span>  
  
1.  <span data-ttu-id="75421-154">**デザイナーの** [制御フロー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブで、データ フロー タスクをデザイン画面に追加します。</span><span class="sxs-lookup"><span data-stu-id="75421-154">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Data Flow task to the design surface.</span></span>  
  
2.  <span data-ttu-id="75421-155">**[データ フロー]** tab, add an OLE DB source to the [データ フロー] task, and then open the **[OLE DB ソース エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="75421-155">On the **Data Flow** tab, add an OLE DB source to the Data Flow task, and then open the **OLE DB Source Editor.**</span></span>  
  
3.  <span data-ttu-id="75421-156">エディターの **[接続マネージャー]** ページで、次の設定を使用してソースを構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-156">On the **Connection Manager** page of the editor, configure the source with the following settings:</span></span>  
  
    1.  <span data-ttu-id="75421-157">**[OLE DB 接続マネージャー]** で、前もって作成した OLE DB 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="75421-157">For **OLE DB connection manager**, select the OLE DB connection manager that you previously created.</span></span>  
  
    2.  <span data-ttu-id="75421-158">**[データ アクセス モード]** で、 **[SQL コマンド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="75421-158">For **Data access mode**, select **SQL command**.</span></span>  
  
    3.  <span data-ttu-id="75421-159">**[SQL コマンド テキスト]** で、次のクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="75421-159">For **SQL command text**, enter the following query:</span></span>  
  
        ```  
        SELECT     Person.Contact.EmailAddress, Person.Contact.FirstName, CONVERT(float, Sales.SalesPerson.Bonus) AS Bonus  
        FROM         Sales.SalesPerson INNER JOIN  
                              Person.Contact ON Sales.SalesPerson.SalesPersonID = Person.Contact.ContactID  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="75421-160">Bonus 列の `currency` 値を `float` 型のパッケージ変数に読み込む前に、その値を `Double` に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75421-160">You have to convert the `currency` value in the Bonus column to a `float` before you can load that value into a package variable whose type is `Double`.</span></span>  
  
4.  <span data-ttu-id="75421-161">**[データ フロー]** タブで、レコードセット変換先を追加し、この変換先を OLE DB ソースの後に連結します。</span><span class="sxs-lookup"><span data-stu-id="75421-161">On the **Data Flow** tab, add a Recordset destination, and connect the destination after the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="75421-162">**[レコードセット変換先エディター]** を開いて、次の設定を使用して変換先を構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-162">Open the **Recordset Destination Editor**, and configure the destination with the following settings:</span></span>  
  
    1.  <span data-ttu-id="75421-163">[**コンポーネントのプロパティ**] タブの [プロパティ] で、 `VariableName` [] を選択し `User::BonusRecordset` ます。</span><span class="sxs-lookup"><span data-stu-id="75421-163">On the **Component Properties** tab, for `VariableName` property, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="75421-164">**[入力列]** タブで、使用可能な 3 つすべての列を選択します。</span><span class="sxs-lookup"><span data-stu-id="75421-164">On the **Input Columns** tab, select all three of the available columns.</span></span>  
  
#### <a name="to-configure-the-foreach-loop-container-and-run-the-package"></a><span data-ttu-id="75421-165">Foreach ループ コンテナーを構成してパッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="75421-165">To configure the Foreach Loop container and run the package</span></span>  
  
1.  <span data-ttu-id="75421-166">**デザイナーの** [制御フロー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブで、Foreach ループ コンテナーを追加し、このコンテナーをデータ フロー タスクの後に連結します。</span><span class="sxs-lookup"><span data-stu-id="75421-166">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container, and connect the container after the Data Flow task.</span></span>  
  
2.  <span data-ttu-id="75421-167">**[Foreach ループ エディター]** を開いて、次の設定を使用してコンテナーを構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-167">Open the **Foreach Loop Editor**, and configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="75421-168">[**コレクション**] ページの [**列挙子**] で [ **Foreach ado Enumerator**] を選択し、[ **ADO オブジェクトソース変数**] でを選択し `User::BonusRecordset` ます。</span><span class="sxs-lookup"><span data-stu-id="75421-168">On the **Collection** page, for **Enumerator**, select **Foreach ADO Enumerator**, and for **ADO object source variable**, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="75421-169">[**変数のマッピング**] ページで、インデックス `User::EmailAddress` 0、 `User::FirstName` インデックス1、インデックス2にマップし `User::Bonus` ます。</span><span class="sxs-lookup"><span data-stu-id="75421-169">On the **Variable Mappings** page, map `User::EmailAddress` to index 0, `User::FirstName` to index 1, and `User::Bonus` to index 2.</span></span>  
  
3.  <span data-ttu-id="75421-170">**[制御フロー]** タブで、Foreach ループ コンテナー内にメール送信タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="75421-170">On the **Control Flow** tab, inside the Foreach Loop container, add a Send Mail task.</span></span>  
  
4.  <span data-ttu-id="75421-171">**[メール送信タスク エディター]** を開いて、 **[メール]** ページで次の設定を使用してタスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="75421-171">Open the **Send Mail Task Editor**, and then on the **Mail** page, configure the task with the following settings:</span></span>  
  
    1.  <span data-ttu-id="75421-172">**[SmtpConnection]** で、前もって構成した SMTP 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="75421-172">For **SmtpConnection**, select the SMTP connection manager that was configured previously.</span></span>  
  
    2.  <span data-ttu-id="75421-173">**[差出人]** に、適切な電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="75421-173">For **From**, enter an appropriate e-mail address.</span></span>  
  
         <span data-ttu-id="75421-174">自分の電子メール アドレスを使用すると、パッケージが正常に実行されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="75421-174">If you use your own e-mail address, you will be able to confirm that the package runs successfully.</span></span> <span data-ttu-id="75421-175">メール送信タスクによって [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]に存在しない販売員にメッセージが送信されると、配信できなかったことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="75421-175">You will receive undeliverable receipts for the messages sent by the Send Mail task to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
    3.  <span data-ttu-id="75421-176">**[宛先]** に、既定の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="75421-176">For **To**, enter a default e-mail address.</span></span>  
  
         <span data-ttu-id="75421-177">この値は使用されませんが、実行時に各販売員の電子メール アドレスに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="75421-177">This value will not be used, but will be replaced at run time by the e-mail address of each salesperson.</span></span>  
  
    4.  <span data-ttu-id="75421-178">**[件名]** に、「Your annual bonus」と入力します。</span><span class="sxs-lookup"><span data-stu-id="75421-178">For **Subject**, enter "Your annual bonus".</span></span>  
  
    5.  <span data-ttu-id="75421-179">**[MessageSourceType]** に対して **[直接入力]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="75421-179">For **MessageSourceType**, select **Direct Input**.</span></span>  
  
5.  <span data-ttu-id="75421-180">**[メール送信タスク エディター]** の **[式]** ページで、参照ボタン ( **[...]** ) をクリックして **[プロパティ式エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="75421-180">On the **Expressions** page of the **Send Mail Task Editor**, click the ellipsis button (**...**) to open the **Property Expressions Editor**.</span></span>  
  
6.  <span data-ttu-id="75421-181">**[プロパティ式エディター]** で、次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="75421-181">In the **Property Expressions Editor**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="75421-182">**[ToLine]** に、次の式を追加します。</span><span class="sxs-lookup"><span data-stu-id="75421-182">For **ToLine**, add the following expression:</span></span>  
  
        ```  
        @[User::EmailAddress]  
        ```  
  
    2.  <span data-ttu-id="75421-183">**MessageSource** プロパティに、次の式を追加します。</span><span class="sxs-lookup"><span data-stu-id="75421-183">For the **MessageSource** property, add the following expression:</span></span>  
  
        ```  
        "Dear " +  @[User::FirstName] + ": The amount of your bonus for this year is $" +  (DT_WSTR, 12) @[User::Bonus] + ". Thank you!"  
        ```  
  
7.  <span data-ttu-id="75421-184">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="75421-184">Run the package.</span></span>  
  
     <span data-ttu-id="75421-185">有効な SMTP サーバーと自分の電子メール アドレスを指定すると、メール送信タスクによって [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]に存在しない販売員にメッセージが送信され、配信できなかったことが通知されます。</span><span class="sxs-lookup"><span data-stu-id="75421-185">If you have specified a valid SMTP server and provided your own e-mail address, you will receive undeliverable receipts for the messages that the Send Mail task sends to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
  
