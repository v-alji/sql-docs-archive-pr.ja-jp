---
title: パッケージ ワークフローでデータ プロファイル タスクを使用する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], using output in workflow
ms.assetid: 39a51586-6977-4c45-b80b-0157a54ad510
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd3544586ac99f66b961f7961e4f4af4d9e4a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639592"
---
# <a name="incorporate-a-data-profiling-task-in-package-workflow"></a><span data-ttu-id="beddf-102">パッケージ ワークフローでデータ プロファイル タスクを使用する</span><span class="sxs-lookup"><span data-stu-id="beddf-102">Incorporate a Data Profiling Task in Package Workflow</span></span>
  <span data-ttu-id="beddf-103">データ プロファイルとクリーンアップは、初期段階で自動化されるプロセスの対象にはなりません。</span><span class="sxs-lookup"><span data-stu-id="beddf-103">Data profiling and cleanup are not candidates for an automated process in their early stages.</span></span> <span data-ttu-id="beddf-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、データ プロファイル タスクを出力する場合、通常、視覚的な分析とユーザーの判断によって、報告された違反が意味のあるものか過剰であるかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the output of the Data Profiling task usually requires visual analysis and human judgment to determine whether reported violations are meaningful or excessive.</span></span> <span data-ttu-id="beddf-105">データ品質の問題を認識した後でも、クリーンアップに最適な方法に取り組む綿密な計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="beddf-105">Even after recognizing data quality problems, there still has to be a carefully thought-out plan that addresses the best approach for cleanup.</span></span>  
  
 <span data-ttu-id="beddf-106">ただし、データ品質の基準が確立された後に、データ ソースの定期的な分析とクリーンアップを自動化することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-106">However, after criteria for data quality have been established, you might want to automate a periodic analysis and cleanup of the data source.</span></span> <span data-ttu-id="beddf-107">次のシナリオを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="beddf-107">Consider these scenarios:</span></span>  
  
-   <span data-ttu-id="beddf-108">**増分読み込みの前にデータ品質を確認する**。</span><span class="sxs-lookup"><span data-stu-id="beddf-108">**Checking data quality before an incremental load**.</span></span> <span data-ttu-id="beddf-109">データ プロファイル タスクを使用して、Customers テーブルの CustomerName 列のために、新しいデータの列の NULL 比プロファイルを計算します。</span><span class="sxs-lookup"><span data-stu-id="beddf-109">Use the Data Profiling task to compute the Column Null Ratio Profile of new data intended for the CustomerName column in a Customers table.</span></span> <span data-ttu-id="beddf-110">NULL 値の比率が 20% を超える場合は、プロファイル出力を含む電子メールをオペレーターに送信します。</span><span class="sxs-lookup"><span data-stu-id="beddf-110">If the percentage of null values is greater than 20%, send an e-mail message that contains the profile output to the operator and end the package.</span></span> <span data-ttu-id="beddf-111">それ以外の場合は、増分読み込みを続行します。</span><span class="sxs-lookup"><span data-stu-id="beddf-111">Otherwise, continue the incremental load.</span></span>  
  
-   <span data-ttu-id="beddf-112">**指定した条件が満たされる場合にクリーンアップを自動化する**。</span><span class="sxs-lookup"><span data-stu-id="beddf-112">**Automating cleanup when the specified conditions are met**.</span></span> <span data-ttu-id="beddf-113">データ プロファイル タスクを使用し、州の参照テーブルに対して State 列、および郵便番号の参照テーブルに対して ZIP Code/Postal Code 列の値包含プロファイルを計算します。</span><span class="sxs-lookup"><span data-stu-id="beddf-113">Use the Data Profiling task to compute the Value Inclusion Profile of the State column against a lookup table of states, and of the ZIP Code/Postal Code column against a lookup table of zip codes.</span></span> <span data-ttu-id="beddf-114">州の値の包含の強さが 80% 未満でも、郵便番号の値の包含の強さが 99% を超える場合は、2 つのことを示しています。</span><span class="sxs-lookup"><span data-stu-id="beddf-114">If the inclusion strength of the state values is less than 80%, but the inclusion strength of the ZIP Code/Postal Code values is greater than 99%, this indicates two things.</span></span> <span data-ttu-id="beddf-115">1 つは州のデータが適切ではないこと、</span><span class="sxs-lookup"><span data-stu-id="beddf-115">First, the state data is bad.</span></span> <span data-ttu-id="beddf-116">もう 1 つは郵便番号のデータは適切であることです。</span><span class="sxs-lookup"><span data-stu-id="beddf-116">Second, the ZIP Code/Postal Code data is good.</span></span> <span data-ttu-id="beddf-117">現在の郵便番号の値から正しい州の値の参照を実行することで州のデータをクリーンアップするデータ フロー タスクを起動します。</span><span class="sxs-lookup"><span data-stu-id="beddf-117">Launch a Data Flow task that cleans up the state data by performing a lookup of the correct state value from the current Zip Code/Postal Code value.</span></span>  
  
 <span data-ttu-id="beddf-118">データ フロー タスクを組み込むことのできるワークフローを用意したら、このタスクを追加するために必要な手順を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-118">After you have a workflow into which you can incorporate the Data Flow task, you have to understand the steps that are required to add this task.</span></span> <span data-ttu-id="beddf-119">次のセクションでは、データ フロー タスクを組み込む一般的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="beddf-119">The next section describes the general process of incorporating the Data Flow task.</span></span> <span data-ttu-id="beddf-120">最後の 2 つのセクションでは、データ フロー タスクを直接データ ソースに接続する方法、またはデータ フローから変換されたデータに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="beddf-120">The final two sections describe how to connect the Data Flow task either directly to a data source or to transformed data from the Data Flow.</span></span>  
  
## <a name="defining-a-general-workflow-for-the-data-flow-task"></a><span data-ttu-id="beddf-121">データ フロー タスクの一般的なワークフローの定義</span><span class="sxs-lookup"><span data-stu-id="beddf-121">Defining a General Workflow for the Data Flow Task</span></span>  
 <span data-ttu-id="beddf-122">パッケージのワークフローでデータ プロファイル タスクの出力を使用するための一般的な方法の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="beddf-122">The following procedure outlines the general approach for using the output of the Data Profiling task in the workflow of a package.</span></span>  
  
#### <a name="to-use-the-output-of-the-data-profiling-task-programmatically-in-a-package"></a><span data-ttu-id="beddf-123">データ プロファイル タスクの出力をパッケージ内でプログラムによって使用するには</span><span class="sxs-lookup"><span data-stu-id="beddf-123">To use the output of the Data Profiling task programmatically in a package</span></span>  
  
1.  <span data-ttu-id="beddf-124">パッケージにデータ プロファイル タスクを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-124">Add and configure the Data Profiling task in a package.</span></span>  
  
2.  <span data-ttu-id="beddf-125">プロファイルの結果から取得する値を保持するようにパッケージ変数を構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-125">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
3.  <span data-ttu-id="beddf-126">スクリプト タスクを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-126">Add and configure a Script task.</span></span> <span data-ttu-id="beddf-127">スクリプト タスクをデータ プロファイル タスクに接続します。</span><span class="sxs-lookup"><span data-stu-id="beddf-127">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="beddf-128">スクリプト タスクで、必要な値をデータ プロファイル タスクの出力ファイルから読み取り、パッケージ変数を設定するコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-128">In the Script task, write code that reads the desired values from the output file of the Data Profiling task and populates the package variables.</span></span>  
  
4.  <span data-ttu-id="beddf-129">スクリプト タスクをワークフロー内の下流の分岐に接続する優先順位制約では、変数の値を使用してワークフローを分ける式を作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-129">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
 <span data-ttu-id="beddf-130">データ プロファイル タスクをパッケージのワークフローに組み込む場合は、このタスクの次の 2 つの機能に注意してください。</span><span class="sxs-lookup"><span data-stu-id="beddf-130">When incorporating the Data Profiling task into the workflow of a package, keep these two features of the task in mind:</span></span>  
  
-   <span data-ttu-id="beddf-131">**タスクの出力**。</span><span class="sxs-lookup"><span data-stu-id="beddf-131">**Task output**.</span></span> <span data-ttu-id="beddf-132">データ プロファイル タスクは、DataProfile.xsd スキーマに従って、その出力をファイルまたはパッケージ変数に XML 形式で書き込みます。</span><span class="sxs-lookup"><span data-stu-id="beddf-132">The Data Profiling task writes its output to a file or a package variable in XML format according to the DataProfile.xsd schema.</span></span> <span data-ttu-id="beddf-133">そのため、パッケージの条件ワークフローでプロファイルの結果を使用する場合は、XML 出力に対してクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-133">Therefore, you have to query the XML output if you want to use the profile results in the conditional workflow of a package.</span></span> <span data-ttu-id="beddf-134">Xpath クエリ言語を使用すると、この XML 出力に対して簡単にクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="beddf-134">You can easily use the Xpath query language to query this XML output.</span></span> <span data-ttu-id="beddf-135">この XML 出力の構造を調べるために、サンプルの出力ファイル、またはスキーマ自体を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="beddf-135">To study the structure of this XML output, you can open a sample output file or the schema itself.</span></span> <span data-ttu-id="beddf-136">出力ファイルまたはスキーマを開くには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] やその他の XML エディター、またはメモ帳などのテキスト エディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="beddf-136">To open the output file or schema, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], another XML editor, or a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="beddf-137">Data Profile Viewer に表示されるプロファイルの結果には、出力で直接見つからない、計算された値もあります。</span><span class="sxs-lookup"><span data-stu-id="beddf-137">Some of the profile results that are displayed in the Data Profile Viewer are calculated values that are not directly found in the output.</span></span> <span data-ttu-id="beddf-138">たとえば、列の NULL 比プロファイルの出力には、行の総数と、NULL 値を含む行の総数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="beddf-138">For example, the output of the Column Null Ratio Profile contains the total number of rows and the number of rows that contain null values.</span></span> <span data-ttu-id="beddf-139">列の NULL 比を取得するには、この 2 つの値に対してクエリを実行してから、NULL 値を含む行の比率を計算します。</span><span class="sxs-lookup"><span data-stu-id="beddf-139">You have to query these two values, and then calculate the percentage of rows that contain null values, to obtain the column null ratio.</span></span>  
  
-   <span data-ttu-id="beddf-140">**タスクの入力**。</span><span class="sxs-lookup"><span data-stu-id="beddf-140">**Task input**.</span></span> <span data-ttu-id="beddf-141">データ プロファイル タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからその入力を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="beddf-141">The Data Profiling task reads its input from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="beddf-142">そのため、既にデータ フローに読み込まれて変換されたデータをプロファイルする場合は、メモリ内のデータをステージング テーブルに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-142">Therefore, you have to save data that is in memory to staging tables if you want to profile data that has already been loaded and transformed in the data flow.</span></span>  
  
 <span data-ttu-id="beddf-143">ここでは、外部データ ソースから直接送信されるデータ、またはデータ フロー タスクから変換されるデータのプロファイルを実行する、この一般的なワークフローを適用します。</span><span class="sxs-lookup"><span data-stu-id="beddf-143">The following sections apply this general workflow to profiling data that comes directly from an external data source or that comes transformed from the Data Flow task.</span></span> <span data-ttu-id="beddf-144">また、データ フロー タスクの入出力の要件を扱う方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="beddf-144">These sections also show how to handle the input and output requirements of the Data Flow task.</span></span>  
  
## <a name="connecting-the-data-profiling-task-directly-to-an-external-data-source"></a><span data-ttu-id="beddf-145">外部データ ソースへの直接的なデータ プロファイル タスクの接続</span><span class="sxs-lookup"><span data-stu-id="beddf-145">Connecting the Data Profiling Task Directly to an External Data Source</span></span>  
 <span data-ttu-id="beddf-146">データ プロファイル タスクでは、データ ソースから直接送信されるデータをプロファイルできます。</span><span class="sxs-lookup"><span data-stu-id="beddf-146">The Data Profiling task can profile data that comes directly from a data source.</span></span>  <span data-ttu-id="beddf-147">この機能を説明するために、次の例では、データ プロファイル タスクを使用して、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの Person.Address テーブルの列で列の NULL 比プロファイルを計算します。</span><span class="sxs-lookup"><span data-stu-id="beddf-147">To illustrate this capability, the following example uses the Data Profiling task to compute a Column Null Ratio Profile on the columns of the Person.Address table in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="beddf-148">その後、この例では、スクリプト タスクを使用して出力ファイルから結果を取得し、ワークフローを分けるために使用できるパッケージ変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="beddf-148">Then, this example uses a Script task to retrieve the results from the output file and populate package variables that can be used to direct workflow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="beddf-149">この簡単な例では、AddressLine2 列を選択しました。この列では NULL 値の比率が高くなっています。</span><span class="sxs-lookup"><span data-stu-id="beddf-149">The AddressLine2 column was selected for this simple example because this column contains a high percentage of null values.</span></span>  
  
 <span data-ttu-id="beddf-150">この例は、次の手順で構成されます。</span><span class="sxs-lookup"><span data-stu-id="beddf-150">This example consists of the following steps:</span></span>  
  
-   <span data-ttu-id="beddf-151">外部データ ソース、およびプロファイルの結果を格納する出力ファイルに接続する接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-151">Configuring the connection managers that connect to the external data source and to the output file that will contain the profile results.</span></span>  
  
-   <span data-ttu-id="beddf-152">データ プロファイル タスクで必要な値を保持するパッケージ変数を構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-152">Configuring the package variables that will hold the values needed by the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="beddf-153">列の NULL 比プロファイルを計算するようにデータ プロファイル タスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-153">Configuring the Data Profiling task to compute the Column Null Ratio Profile.</span></span>  
  
-   <span data-ttu-id="beddf-154">データ プロファイル タスクからの XML 出力を処理するスクリプト タスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-154">Configuring the Script task to work the XML output from the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="beddf-155">データ プロファイル タスクの結果に基づいて実行する、ワークフロー内の下流の分岐を制御する優先順位制約を構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-155">Configuring the precedence constraints that will control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
### <a name="configure-the-connection-managers"></a><span data-ttu-id="beddf-156">接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="beddf-156">Configure the Connection Managers</span></span>  
 <span data-ttu-id="beddf-157">この例では、次の 2 つの接続マネージャーがあります。</span><span class="sxs-lookup"><span data-stu-id="beddf-157">For this example, there are two connection managers:</span></span>  
  
-   <span data-ttu-id="beddf-158">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続する [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 接続マネージャー。</span><span class="sxs-lookup"><span data-stu-id="beddf-158">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
-   <span data-ttu-id="beddf-159">データ プロファイル タスクの結果を格納する出力ファイルを作成するファイル接続マネージャー。</span><span class="sxs-lookup"><span data-stu-id="beddf-159">A File connection manager that creates the output file that will hold the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="beddf-160">接続マネージャーを構成するには</span><span class="sxs-lookup"><span data-stu-id="beddf-160">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="beddf-161">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-161">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="beddf-162">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="beddf-162">Add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to the package.</span></span> <span data-ttu-id="beddf-163">この接続マネージャーを、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用して、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの使用可能なインスタンスに接続するように構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-163">Configure this connection manager to use the NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) and to connect to an available instance of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
     <span data-ttu-id="beddf-164">既定では、接続マネージャーの名前は \<server name>.AdventureWorks1 となります。</span><span class="sxs-lookup"><span data-stu-id="beddf-164">By default, the connection manager has the following name: \<server name>.AdventureWorks1.</span></span>  
  
3.  <span data-ttu-id="beddf-165">ファイル接続マネージャーをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="beddf-165">Add a File connection manager to the package.</span></span> <span data-ttu-id="beddf-166">この接続マネージャーを、データ プロファイル タスクの出力ファイルを作成するように構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-166">Configure this connection manager to create the output file for the Data Profiling task.</span></span>  
  
     <span data-ttu-id="beddf-167">この例では、ファイル名 DataProfile1.xml を使用します。</span><span class="sxs-lookup"><span data-stu-id="beddf-167">This example uses the file name, DataProfile1.xml.</span></span> <span data-ttu-id="beddf-168">既定では、接続マネージャーの名前はファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="beddf-168">By default, the connection manager has the same name as the file.</span></span>  
  
### <a name="configure-the-package-variables"></a><span data-ttu-id="beddf-169">パッケージ変数の構成</span><span class="sxs-lookup"><span data-stu-id="beddf-169">Configure the Package Variables</span></span>  
 <span data-ttu-id="beddf-170">この例では、2 つのパッケージ変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="beddf-170">This example uses two package variables:</span></span>  
  
-   <span data-ttu-id="beddf-171">ProfileConnectionName 変数は、ファイル接続マネージャーの名前をスクリプト タスクに渡します。</span><span class="sxs-lookup"><span data-stu-id="beddf-171">The ProfileConnectionName variable passes the name of the File connection manager to the Script task.</span></span>  
  
-   <span data-ttu-id="beddf-172">AddressLine2NullRatio 変数は、この列の計算された NULL 比をスクリプト タスクからパッケージに渡します。</span><span class="sxs-lookup"><span data-stu-id="beddf-172">The AddressLine2NullRatio variable passes the calculated null ratio for this column out of the Script task to the package.</span></span>  
  
##### <a name="to-configure-the-package-variables-that-will-hold-profile-results"></a><span data-ttu-id="beddf-173">プロファイルの結果を保持するパッケージ変数を構成するには</span><span class="sxs-lookup"><span data-stu-id="beddf-173">To configure the package variables that will hold profile results</span></span>  
  
-   <span data-ttu-id="beddf-174">**[変数]** ウィンドウで、次の 2 つのパッケージ変数を追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-174">In the **Variables** window, add and configure the following two package variables:</span></span>  
  
    -   <span data-ttu-id="beddf-175">変数の1つに名前として「」を入力 `ProfileConnectionName` し、この変数の型を**String**に設定します。</span><span class="sxs-lookup"><span data-stu-id="beddf-175">Enter the name, `ProfileConnectionName`, for one of the variables and set the type of this variable to **String**.</span></span>  
  
    -   <span data-ttu-id="beddf-176">他の変数の名前として「」を入力 `AddressLine2NullRatio` し、この変数の型を**Double**に設定します。</span><span class="sxs-lookup"><span data-stu-id="beddf-176">Enter the name, `AddressLine2NullRatio`, for the other variable and set the type of this variable to **Double**.</span></span>  
  
### <a name="configure-the-data-profiling-task"></a><span data-ttu-id="beddf-177">データ プロファイル タスクの構成</span><span class="sxs-lookup"><span data-stu-id="beddf-177">Configure the Data Profiling Task</span></span>  
 <span data-ttu-id="beddf-178">データ プロファイル タスクは、次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-178">The Data Profiling task has to be configured in the following way:</span></span>  
  
-   <span data-ttu-id="beddf-179">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーが提供するデータを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="beddf-179">To use the data that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager supplies as input.</span></span>  
  
-   <span data-ttu-id="beddf-180">入力データに対して列の NULL 比プロファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="beddf-180">To perform a Column Null Ratio profile on the input data.</span></span>  
  
-   <span data-ttu-id="beddf-181">ファイル接続マネージャーに関連付けられているファイルにプロファイルの結果を保存します。</span><span class="sxs-lookup"><span data-stu-id="beddf-181">To save the profile results to the file that is associated with the File connection manager.</span></span>  
  
##### <a name="to-configure-the-data-profiling-task"></a><span data-ttu-id="beddf-182">データ プロファイル タスクを構成するには</span><span class="sxs-lookup"><span data-stu-id="beddf-182">To configure the Data Profiling task</span></span>  
  
1.  <span data-ttu-id="beddf-183">制御フローにデータ プロファイル タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="beddf-183">To the Control Flow, add a Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="beddf-184">**[データ プロファイル タスク エディター]** を開き、タスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-184">Open the **Data Profiling Task Editor** to configure the task.</span></span>  
  
3.  <span data-ttu-id="beddf-185">エディターの **[全般]** ページの **[変換先]** で、既に構成済みのファイル接続マネージャーの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="beddf-185">On the **General** page of the editor, for **Destination**, select the name of the File connection manager that you have previously configured.</span></span>  
  
4.  <span data-ttu-id="beddf-186">エディターの **[プロファイル要求]** ページで、列の NULL 比プロファイルを新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-186">On the **Profile Requests** page of the editor, create a new Column Null Ratio Profile.</span></span>  
  
5.  <span data-ttu-id="beddf-187">**[要求プロパティ]** ペインの **[接続マネージャー]** で、既に構成済みの [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="beddf-187">In the **Request properties** pane, for **ConnectionManager**, select the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that you have previously configured.</span></span> <span data-ttu-id="beddf-188">次に、 **[TableOrView]** で Person.Address を選択します。</span><span class="sxs-lookup"><span data-stu-id="beddf-188">Then, for **TableOrView**, select Person.Address.</span></span>  
  
6.  <span data-ttu-id="beddf-189">データ プロファイル タスク エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="beddf-189">Close the Data Profiling Task Editor.</span></span>  
  
### <a name="configure-the-script-task"></a><span data-ttu-id="beddf-190">スクリプト タスクの構成</span><span class="sxs-lookup"><span data-stu-id="beddf-190">Configure the Script Task</span></span>  
 <span data-ttu-id="beddf-191">スクリプト タスクは、出力ファイルから結果を取得し、既に構成済みのパッケージ変数を設定するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-191">The Script task has to be configured to retrieve the results from the output file and populate the package variables that were previously configured.</span></span>  
  
##### <a name="to-configure-the-script-task"></a><span data-ttu-id="beddf-192">スクリプト タスクを構成するには</span><span class="sxs-lookup"><span data-stu-id="beddf-192">To configure the Script task</span></span>  
  
1.  <span data-ttu-id="beddf-193">制御フローにスクリプト タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="beddf-193">To the Control Flow, add a Script task.</span></span>  
  
2.  <span data-ttu-id="beddf-194">スクリプト タスクをデータ プロファイル タスクに接続します。</span><span class="sxs-lookup"><span data-stu-id="beddf-194">Connect the Script task to the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="beddf-195">**スクリプト タスク エディター** を開いて、タスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-195">Open the **Script Task Editor** to configure the task.</span></span>  
  
4.  <span data-ttu-id="beddf-196">**[スクリプト]** ページで、使用するプログラミング言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="beddf-196">On the **Script** page, select your preferred programming language.</span></span> <span data-ttu-id="beddf-197">次に、2 つのパッケージ変数をスクリプトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="beddf-197">Then, make the two package variables available to the script:</span></span>  
  
    1.  <span data-ttu-id="beddf-198">`ReadOnlyVariables`では、を選択し `ProfileConnectionName` ます。</span><span class="sxs-lookup"><span data-stu-id="beddf-198">For `ReadOnlyVariables`, select `ProfileConnectionName`.</span></span>  
  
    2.  <span data-ttu-id="beddf-199">**ReadWriteVariables**の場合は、を選択し `AddressLine2NullRatio` ます。</span><span class="sxs-lookup"><span data-stu-id="beddf-199">For **ReadWriteVariables**, select `AddressLine2NullRatio`.</span></span>  
  
5.  <span data-ttu-id="beddf-200">**[スクリプトの編集]** を選択して、スクリプト開発環境を開きます。</span><span class="sxs-lookup"><span data-stu-id="beddf-200">Select **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="beddf-201">System.Xml 名前空間への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="beddf-201">Add a reference to the System.Xml namespace.</span></span>  
  
7.  <span data-ttu-id="beddf-202">プログラミング言語に対応するサンプル コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="beddf-202">Enter the sample code that corresponds to your programming language:</span></span>  
  
    ```vb  
    Imports System  
    Imports Microsoft.SqlServer.Dts.Runtime  
    Imports System.Xml  
  
    Public Class ScriptMain  
  
      Private FILENAME As String = "C:\ TEMP\DataProfile1.xml"  
      Private PROFILE_NAMESPACE_URI As String = "https://schemas.microsoft.com/DataDebugger/"  
      Private NULLCOUNT_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()"  
      Private TABLE_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table"  
  
      Public Sub Main()  
  
        Dim profileConnectionName As String  
        Dim profilePath As String  
        Dim profileOutput As New XmlDocument  
        Dim profileNSM As XmlNamespaceManager  
        Dim nullCountNode As XmlNode  
        Dim nullCount As Integer  
        Dim tableNode As XmlNode  
        Dim rowCount As Integer  
        Dim nullRatio As Double  
  
        ' Open output file.  
        profileConnectionName = Dts.Variables("ProfileConnectionName").Value.ToString()  
        profilePath = Dts.Connections(profileConnectionName).ConnectionString  
        profileOutput.Load(profilePath)  
        profileNSM = New XmlNamespaceManager(profileOutput.NameTable)  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI)  
  
        ' Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM)  
        nullCount = CType(nullCountNode.Value, Integer)  
  
        ' Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM)  
        rowCount = CType(tableNode.Attributes("RowCount").Value, Integer)  
  
        ' Compute and return null ratio.  
        nullRatio = nullCount / rowCount  
        Dts.Variables("AddressLine2NullRatio").Value = nullRatio  
  
        Dts.TaskResult = Dts.Results.Success  
  
      End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SqlServer.Dts.Runtime;  
    using System.Xml;  
  
    public class ScriptMain  
    {  
  
      private string FILENAME = "C:\\ TEMP\\DataProfile1.xml";  
      private string PROFILE_NAMESPACE_URI = "https://schemas.microsoft.com/DataDebugger/";  
      private string NULLCOUNT_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()";  
      private string TABLE_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table";  
  
      public void Main()  
      {  
  
        string profileConnectionName;  
        string profilePath;  
        XmlDocument profileOutput = new XmlDocument();  
        XmlNamespaceManager profileNSM;  
        XmlNode nullCountNode;  
        int nullCount;  
        XmlNode tableNode;  
        int rowCount;  
        double nullRatio;  
  
        // Open output file.  
        profileConnectionName = Dts.Variables["ProfileConnectionName"].Value.ToString();  
        profilePath = Dts.Connections[profileConnectionName].ConnectionString;  
        profileOutput.Load(profilePath);  
        profileNSM = new XmlNamespaceManager(profileOutput.NameTable);  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI);  
  
        // Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM);  
        nullCount = (int)nullCountNode.Value;  
  
        // Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM);  
        rowCount = (int)tableNode.Attributes["RowCount"].Value;  
  
        // Compute and return null ratio.  
        nullRatio = nullCount / rowCount;  
        Dts.Variables["AddressLine2NullRatio"].Value = nullRatio;  
  
        Dts.TaskResult = Dts.Results.Success;  
  
      }  
  
    }  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="beddf-203">この手順で示すサンプル コードでは、データ プロファイル タスクの出力をファイルから読み込む方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="beddf-203">The sample code shown in this procedure demonstrates how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="beddf-204">パッケージ変数からデータ プロファイル タスクの出力を読み込むには、この手順の後に示す他のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="beddf-204">To load the output of the Data Profiling task from a package variable instead, see the alternative sample code that follows this procedure.</span></span>  
  
8.  <span data-ttu-id="beddf-205">スクリプト開発環境を閉じてから、スクリプト タスク エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="beddf-205">Close the script development environment, and then close the Script Task Editor.</span></span>  
  
#### <a name="alternative-code-reading-the-profile-output-from-a-variable"></a><span data-ttu-id="beddf-206">変数からプロファイル出力を読み込むコード</span><span class="sxs-lookup"><span data-stu-id="beddf-206">Alternative Code-Reading the Profile Output from a Variable</span></span>  
 <span data-ttu-id="beddf-207">上記の手順は、データ プロファイル タスクの出力をファイルから読み込む方法を示していますが、</span><span class="sxs-lookup"><span data-stu-id="beddf-207">The previous procedure shows how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="beddf-208">この出力をパッケージ変数から読み込む方法もあります。</span><span class="sxs-lookup"><span data-stu-id="beddf-208">However, an alternative method would be to load this output from a package variable.</span></span> <span data-ttu-id="beddf-209">出力を変数から読み込むには、サンプル コードを次のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-209">To load the output from a variable, you have to make the following changes to the sample code:</span></span>  
  
-   <span data-ttu-id="beddf-210">`LoadXml` メソッドではなく、`XmlDocument` クラスの `Load` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="beddf-210">Call the `LoadXml` method of the `XmlDocument` class instead of the `Load` method.</span></span>  
  
-   <span data-ttu-id="beddf-211">スクリプト タスク エディターで、プロファイル出力を格納するパッケージ変数の名前を、タスクの `ReadOnlyVariables` リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="beddf-211">In the Script Task Editor, add the name of the package variable that contains the profile output to the task's `ReadOnlyVariables` list.</span></span>  
  
-   <span data-ttu-id="beddf-212">次のコード例で示すように、変数の文字列値を `LoadXML` メソッドに渡します </span><span class="sxs-lookup"><span data-stu-id="beddf-212">Pass the string value of the variable to the `LoadXML` method, as shown in the following code example.</span></span> <span data-ttu-id="beddf-213">(この例では、プロファイル出力を格納するパッケージ変数の名前として "ProfileOutput" を使用しています)。</span><span class="sxs-lookup"><span data-stu-id="beddf-213">(This example uses "ProfileOutput" as the name of the package variable that contains the profile output.)</span></span>  
  
    ```vb  
    Dim outputString As String  
    outputString = Dts.Variables("ProfileOutput").Value.ToString()  
    ...  
    profileOutput.LoadXml(outputString)  
    ```  
  
    ```csharp  
    string outputString;  
    outputString = Dts.Variables["ProfileOutput"].Value.ToString();  
    ...  
    profileOutput.LoadXml(outputString);  
    ```  
  
### <a name="configure-the-precedence-constraints"></a><span data-ttu-id="beddf-214">優先順位制約の構成</span><span class="sxs-lookup"><span data-stu-id="beddf-214">Configure the Precedence Constraints</span></span>  
 <span data-ttu-id="beddf-215">優先順位制約は、データ プロファイル タスクの結果に基づいて実行する、ワークフロー内の下流の分岐を制御するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-215">The precedence constraints have to be configured to control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-precedence-constraints"></a><span data-ttu-id="beddf-216">優先順位制約を構成するには</span><span class="sxs-lookup"><span data-stu-id="beddf-216">To configure the precedence constraints</span></span>  
  
-   <span data-ttu-id="beddf-217">スクリプト タスクをワークフロー内の下流の分岐に接続する優先順位制約では、変数の値を使用してワークフローを分ける式を作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-217">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
     <span data-ttu-id="beddf-218">たとえば、 **[式と制約]** で、優先順位制約の **[評価操作]** を設定するとします。</span><span class="sxs-lookup"><span data-stu-id="beddf-218">For example, you might set the **Evaluation operation** of the precedence constraint to **Expression and Constraint**.</span></span> <span data-ttu-id="beddf-219">次に、式の値として `@AddressLine2NullRatio < .90` を使用します。</span><span class="sxs-lookup"><span data-stu-id="beddf-219">Then, you might use `@AddressLine2NullRatio < .90` as the value of the expression.</span></span> <span data-ttu-id="beddf-220">これにより、ワークフローは、直前のタスクが成功した場合、および選択した列の NULL 値の比率が 90% 未満の場合に、選択したパスに沿って進みます。</span><span class="sxs-lookup"><span data-stu-id="beddf-220">This causes the workflow to follow the selected path when the previous tasks succeed, and when the percentage of null values in the selected column is less than 90%.</span></span>  
  
## <a name="connecting-the-data-profiling-task-to-transformed-data-from-the-data-flow"></a><span data-ttu-id="beddf-221">データ フローから変換されたデータへのデータ プロファイル タスクの接続</span><span class="sxs-lookup"><span data-stu-id="beddf-221">Connecting the Data Profiling Task to Transformed Data from the Data Flow</span></span>  
 <span data-ttu-id="beddf-222">データ ソースから直接データをプロファイルするのではなく、既にデータ フローに読み込まれて変換されたデータをプロファイルできます。</span><span class="sxs-lookup"><span data-stu-id="beddf-222">Instead of profiling data directly from a data source, you can profile data that has already been loaded and transformed in the data flow.</span></span> <span data-ttu-id="beddf-223">ただし、データ プロファイル タスクは、メモリ内のデータではなく、持続データに対してしか動作しません。</span><span class="sxs-lookup"><span data-stu-id="beddf-223">However, the Data Profiling task works only against persisted data, not against in-memory data.</span></span> <span data-ttu-id="beddf-224">したがって、変換されたデータをステージング テーブルに保存するには、最初に、変換先コンポーネントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-224">Therefore, you must first use a destination component to save the transformed data to a staging table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="beddf-225">データ プロファイル タスクを構成する場合は、既存のテーブルと列を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-225">When you configure the Data Profiling task, you have to select existing tables and columns.</span></span> <span data-ttu-id="beddf-226">そのため、タスクを構成するには、デザイン時にステージング テーブルを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="beddf-226">Therefore, you must create the staging table at design time before you can configure the task.</span></span> <span data-ttu-id="beddf-227">つまり、このシナリオでは、実行時に作成した一時テーブルを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="beddf-227">In other words, this scenario does not allow you to use a temporary table that is created at run time.</span></span>  
  
 <span data-ttu-id="beddf-228">データをステージング テーブルに保存すると、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="beddf-228">After saving the data to a staging table, you can do the following actions:</span></span>  
  
-   <span data-ttu-id="beddf-229">データ プロファイル タスクを使用してデータをプロファイルする。</span><span class="sxs-lookup"><span data-stu-id="beddf-229">Use the Data Profiling task to profile the data.</span></span>  
  
-   <span data-ttu-id="beddf-230">このトピックの前半で説明したように、スクリプト タスクを使用して結果を読み込む。</span><span class="sxs-lookup"><span data-stu-id="beddf-230">Use a Script task to read the results as described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="beddf-231">この結果を使用してパッケージの後続のワークフローを進む。</span><span class="sxs-lookup"><span data-stu-id="beddf-231">Use those results to direct the subsequent workflow of the package.</span></span>  
  
 <span data-ttu-id="beddf-232">次の手順では、データ プロファイル タスクの出力を使用して、データ フローによって変換されたデータをプロファイルするための一般的な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="beddf-232">The following procedure provides the general approach for using the Data Profiling task to profile data that has been transformed by the data flow.</span></span> <span data-ttu-id="beddf-233">この手順の多くは、外部データ ソースから直接送信されるデータをプロファイルするための既に説明した手順と似ています。</span><span class="sxs-lookup"><span data-stu-id="beddf-233">Many of these steps are similar to the ones described earlier for profiling data that comes directly from an external data source.</span></span> <span data-ttu-id="beddf-234">さまざまなコンポーネントを構成する方法の詳細については、上記の手順を確認してください。</span><span class="sxs-lookup"><span data-stu-id="beddf-234">You might want to review those earlier steps for more information about how to configure the various components.</span></span>  
  
#### <a name="to-use-the-data-profiling-task-in-the-data-flow"></a><span data-ttu-id="beddf-235">データ フローでデータ プロファイル タスクを使用するには</span><span class="sxs-lookup"><span data-stu-id="beddf-235">To use the Data Profiling task in the data flow</span></span>  
  
1.  <span data-ttu-id="beddf-236">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-236">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a package.</span></span>  
  
2.  <span data-ttu-id="beddf-237">データ フローで、適切な変換元と変換を追加、構成、および接続します。</span><span class="sxs-lookup"><span data-stu-id="beddf-237">In the Data Flow, add, configure, and connect the appropriate sources and transformations.</span></span>  
  
3.  <span data-ttu-id="beddf-238">データ フローで、変換したデータをステージング テーブルに保存する変換先コンポーネントを追加、構成、および接続します。</span><span class="sxs-lookup"><span data-stu-id="beddf-238">In the Data Flow, add, configure, and connect a destination component that saves the transformed data to a staging table.</span></span>  
  
4.  <span data-ttu-id="beddf-239">制御フローで、ステージング テーブル内の変換したデータに対して必要なプロファイルを計算するデータ プロファイル タスクを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-239">In the Control Flow, add and configure a Data Profiling task that computes the desired profiles against the transformed data in the staging table.</span></span> <span data-ttu-id="beddf-240">データ プロファイル タスクをデータ フロー タスクに接続します。</span><span class="sxs-lookup"><span data-stu-id="beddf-240">Connect the Data Profiling task to the Data Flow task.</span></span>  
  
5.  <span data-ttu-id="beddf-241">プロファイルの結果から取得する値を保持するようにパッケージ変数を構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-241">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
6.  <span data-ttu-id="beddf-242">スクリプト タスクを追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-242">Add and configure a Script task.</span></span> <span data-ttu-id="beddf-243">スクリプト タスクをデータ プロファイル タスクに接続します。</span><span class="sxs-lookup"><span data-stu-id="beddf-243">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="beddf-244">スクリプト タスクで、必要な値をデータ プロファイル タスクの出力から読み取り、パッケージ変数を設定するコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-244">In the Script task, write code that reads the desired values from the output of the Data Profiling task and populates the package variables.</span></span>  
  
7.  <span data-ttu-id="beddf-245">スクリプト タスクをワークフロー内の下流の分岐に接続する優先順位制約では、変数の値を使用してワークフローを分ける式を作成します。</span><span class="sxs-lookup"><span data-stu-id="beddf-245">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beddf-246">参照</span><span class="sxs-lookup"><span data-stu-id="beddf-246">See Also</span></span>  
 <span data-ttu-id="beddf-247">[データ プロファイル タスクのセットアップ](data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="beddf-247">[Setup of the Data Profiling Task](data-profiling-task.md) </span></span>  
 [<span data-ttu-id="beddf-248">Data Profile Viewer</span><span class="sxs-lookup"><span data-stu-id="beddf-248">Data Profile Viewer</span></span>](data-profile-viewer.md)  
  
  
