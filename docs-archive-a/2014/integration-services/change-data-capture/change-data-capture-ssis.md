---
title: 変更データ キャプチャ (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental loads [SQL Server change data capture]
- change data capture [SQL Server], Integration Services and
ms.assetid: c4aaba1b-73e5-4187-a97b-61c10069cc5a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55293d4e2caa4c31cb004a2cdf1cda99769c77e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720319"
---
# <a name="change-data-capture-ssis"></a><span data-ttu-id="0ebcc-102">変更データ キャプチャ (SSIS)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-102">Change Data Capture (SSIS)</span></span>
  <span data-ttu-id="0ebcc-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、変更データ キャプチャによって、ソース テーブルからデータ マートおよびデータ ウェアハウスへの増分読み込みを効率的に実行するための効果的なソリューションが実現します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], change data capture offers an effective solution to the challenge of efficiently performing incremental loads from source tables to data marts and data warehouses.</span></span>

## <a name="what-is-change-data-capture"></a><span data-ttu-id="0ebcc-104">変更データ キャプチャとは</span><span class="sxs-lookup"><span data-stu-id="0ebcc-104">What is Change Data Capture?</span></span>
 <span data-ttu-id="0ebcc-105">ソース テーブルは、時間の経過と共に変化します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-105">Source tables change over time.</span></span> <span data-ttu-id="0ebcc-106">このようなテーブルに基づくデータ マートまたはデータ ウェアハウスは、その変化を反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-106">A data mart or data warehouse that is based on those tables needs to reflect these changes.</span></span> <span data-ttu-id="0ebcc-107">ただし、ソース全体のスナップショットを定期的にコピーする処理には、膨大な時間とリソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-107">However, a process that periodically copies a snapshot of the entire source consumes too much time and resources.</span></span> <span data-ttu-id="0ebcc-108">timestamp 列、トリガー、複雑なクエリなどの別の方法を使用すると、多くの場合、パフォーマンスが低下して処理が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-108">Alternate approaches that include timestamp columns, triggers, or complex queries often hurt performance and increase complexity.</span></span> <span data-ttu-id="0ebcc-109">ここで必要となるのは、対象となるデータ表現に対して簡単に適用できるように構成された変更データの確実なストリームです。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-109">What is needed is a reliable stream of change data that is structured so that it can easily be applied by consumers to target representations of the data.</span></span> <span data-ttu-id="0ebcc-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の変更データ キャプチャはこのソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-110">Change data capture in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides this solution.</span></span>

 <span data-ttu-id="0ebcc-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] の変更データ キャプチャ機能は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルに対して適用された挿入、更新、削除の各アクティビティをキャプチャし、変更の詳細を、利用しやすいリレーショナル形式で格納します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-111">The change data capture feature of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] captures insert, update, and delete activity applied to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables, and makes the details of the changes available in an easily-consumed, relational format.</span></span> <span data-ttu-id="0ebcc-112">変更データ キャプチャで使用される変更テーブルには、追跡されたソース テーブルの列構造をミラー化する列が、行われた変更を行ごとに理解するために必要なメタデータと共に含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-112">The change tables used by change data capture contain columns that mirror the column structure of the tracked source tables, along with the metadata needed to understand the changes that have occurred on a row by row basis.</span></span>

> [!NOTE]
>  <span data-ttu-id="0ebcc-113">変更データ キャプチャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-113">Change data capture is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ebcc-114">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>

## <a name="how-change-data-capture-works-in-integration-services"></a><span data-ttu-id="0ebcc-115">Integration Services における変更データ キャプチャのしくみ</span><span class="sxs-lookup"><span data-stu-id="0ebcc-115">How Change Data Capture Works in Integration Services</span></span>
 <span data-ttu-id="0ebcc-116">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内の変更データを簡単に取得でき、データ ウェアハウスへの増分読み込みを効率的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-116">An [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can easily harvest the change data in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases to perform efficient incremental loads to a data warehouse.</span></span> <span data-ttu-id="0ebcc-117">ただし、 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] を使用して変更データを読み込む前に、管理者は、変更をキャプチャするデータベースおよびテーブルで変更データ キャプチャを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-117">However, before you can use [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] to load change data, an administrator must enable change data capture on the database and the tables from which you want to capture changes.</span></span> <span data-ttu-id="0ebcc-118">データベースで変更データ キャプチャを構成する方法の詳細については、「[変更データ キャプチャの有効化と無効化 &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-118">For more information on how to configure change data capture on a database, see [Enable and Disable Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md).</span></span>

 <span data-ttu-id="0ebcc-119">データベースで変更データ キャプチャが有効になったら、変更データの増分読み込みを実行するパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-119">Once an administrator has enabled change data capture on the database, you can create a package that performs an incremental load of the change data.</span></span> <span data-ttu-id="0ebcc-120">次の図は、1 つのテーブルから増分読み込みを実行するパッケージの作成手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-120">The following diagram shows the steps for creating such a package that performs an incremental load from a single table:</span></span>

 <span data-ttu-id="0ebcc-121">![変更データ キャプチャ パッケージの作成手順](../media/cdc-package-creation.gif "変更データ キャプチャ パッケージの作成手順")</span><span class="sxs-lookup"><span data-stu-id="0ebcc-121">![Change Data Capture Package Creation Steps](../media/cdc-package-creation.gif "Change Data Capture Package Creation Steps")</span></span>

 <span data-ttu-id="0ebcc-122">上の図に示したように、変更データの増分読み込みを実行するパッケージを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-122">As shown in the previous diagram, creating a package that performs an incremental load of changed data involves the following steps:</span></span>

 <span data-ttu-id="0ebcc-123">**手順 1: 制御フローの設計**パッケージの制御フローでは、次のタスクを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-123">**Step 1: Designing the Control Flow** In the control flow in the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="0ebcc-124">取得するソース データに対する変更の間隔の開始と終了の `datetime` 値を計算します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-124">Calculate the starting and ending `datetime` values for the interval of changes to the source data that you want to retrieve.</span></span>

     <span data-ttu-id="0ebcc-125">これらの値を計算するには、`datetime` 関数を指定した SQL 実行タスクまたは [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-125">To calculate these values, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expressions with `datetime` functions.</span></span> <span data-ttu-id="0ebcc-126">その後、これらのエンドポイントをパッケージで後から使用するためにパッケージ変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-126">You then store these endpoints in package variables for use later in the package.</span></span>

     <span data-ttu-id="0ebcc-127">**詳細**  [変更データの間隔を指定する](specify-an-interval-of-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-127">**For more information:**  [Specify an Interval of Change Data](specify-an-interval-of-change-data.md)</span></span>

-   <span data-ttu-id="0ebcc-128">選択した間隔の変更データが準備できているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-128">Determine whether the change data for the selected interval is ready.</span></span> <span data-ttu-id="0ebcc-129">非同期キャプチャ プロセスが、選択したエンドポイントにまだ達していない可能性があるため、この手順が必要となります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-129">This step is necessary because the asynchronous capture process might not yet have reached the selected endpoint.</span></span>

     <span data-ttu-id="0ebcc-130">データが準備できているかどうかを判断するには、必要に応じて、選択した間隔の変更データが準備できるまで実行を遅延させる For ループ コンテナーをまず用意します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-130">To determine whether the data is ready, start with a For Loop container to delay execution, if necessary, until the change data for the selected interval is ready.</span></span> <span data-ttu-id="0ebcc-131">ループ コンテナー内で SQL 実行タスクを使用して、変更データ キャプチャによって管理される時間マッピング テーブルに対するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-131">Inside the loop container, use an Execute SQL task to query the time mapping tables maintained by change data capture.</span></span> <span data-ttu-id="0ebcc-132">その後、`Thread.Sleep` メソッドを呼び出すスクリプト タスク、または `WAITFOR` ステートメントを実行する別の SQL 実行タスクを使用して、必要に応じてパッケージの実行を一時的に遅延させます。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-132">Then, use a Script task that calls the `Thread.Sleep` method, or another Execute SQL task with a `WAITFOR` statement, to delay the execution of the package temporarily, if necessary.</span></span> <span data-ttu-id="0ebcc-133">必要に応じて、エラー状態またはタイムアウトをログに記録する別のスクリプト タスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-133">Optionally, use another Script task to log an error condition or a timeout.</span></span>

     <span data-ttu-id="0ebcc-134">**詳細**  [データの変更の準備ができているかどうかを判断する](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-134">**For more information:**  [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>

-   <span data-ttu-id="0ebcc-135">変更データのクエリに使用するクエリ文字列を準備します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-135">Prepare the query string that will be used to query for the change data.</span></span>

     <span data-ttu-id="0ebcc-136">スクリプト タスクまたは SQL 実行タスクを使用して、変更をクエリで確認するために使用する SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-136">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>

     <span data-ttu-id="0ebcc-137">**詳細**  [変更データのクエリを準備する](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-137">**For more information:**  [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>

 <span data-ttu-id="0ebcc-138">**手順 2: 変更データのクエリの設定**データのクエリを実行するテーブル値関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-138">**Step 2: Setting Up the Query for Change Data** Create the table-valued function that will query for the data.</span></span>

 <span data-ttu-id="0ebcc-139">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してクエリを作成および保存します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-139">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to develop and save the query.</span></span>

 <span data-ttu-id="0ebcc-140">**詳細**  [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-140">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

 <span data-ttu-id="0ebcc-141">**手順 3: データフローのデザイン**パッケージのデータフローでは、次のタスクを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-141">**Step 3: Designing the Data Flow** In the data flow of the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="0ebcc-142">変更テーブルから変更データを取得します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-142">Retrieve the change data from the change tables.</span></span>

     <span data-ttu-id="0ebcc-143">データを取得するには、変換元コンポーネントを使用して、選択した間隔内の変更のクエリを変更テーブルに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-143">To retrieve the data, use a source component to query the change tables for the changes that fall within the selected interval.</span></span> <span data-ttu-id="0ebcc-144">事前に作成しておく必要がある Transact-SQL テーブル値関数が変換元によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-144">The source calls a Transact-SQL table-valued function that you must have previously created.</span></span>

     <span data-ttu-id="0ebcc-145">**詳細**  [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-145">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

-   <span data-ttu-id="0ebcc-146">変更を処理用に挿入、更新、および削除に分割します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-146">Split the changes into inserts, updates, and deletes for processing.</span></span>

     <span data-ttu-id="0ebcc-147">変更を分割するには、条件分割変換を使用して、適切な処理のために挿入、更新、および削除を異なる出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-147">To split the changes, use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>

     <span data-ttu-id="0ebcc-148">**詳細**  [挿入、更新、および削除を処理する](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-148">**For more information:**  [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>

-   <span data-ttu-id="0ebcc-149">挿入、削除、および更新を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-149">Apply the inserts, deletes, and updates to the destination.</span></span>

     <span data-ttu-id="0ebcc-150">変更を変換先に適用するには、変換先コンポーネントを使用して、挿入を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-150">To apply the changes to the destination, use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="0ebcc-151">また、OLE DB コマンド変換とパラメーター化された UPDATE および DELETE ステートメントを使用して、更新と削除を変換先に適用します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-151">Also, use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span> <span data-ttu-id="0ebcc-152">更新と削除は、変換先コンポーネントを使用して一時テーブルに行を保存することによって適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-152">You can also apply updates and deletes by using destination components to save the rows to temporary tables.</span></span> <span data-ttu-id="0ebcc-153">次に、SQL 実行タスクを使用して、一時テーブルから変換先に対して一括更新および一括削除操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-153">Then, use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>

     <span data-ttu-id="0ebcc-154">**詳細**  [変換先に変更を適用する](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-154">**For more information:**  [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>

### <a name="change-data-from-multiple-tables"></a><span data-ttu-id="0ebcc-155">複数のテーブルの変更データ</span><span class="sxs-lookup"><span data-stu-id="0ebcc-155">Change Data from Multiple Tables</span></span>
 <span data-ttu-id="0ebcc-156">上の図と手順で説明したプロセスでは、1 つのテーブルから増分読み込みを実行しています。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-156">The process outlined in the previous diagram and steps involves an incremental load from a single table.</span></span> <span data-ttu-id="0ebcc-157">複数のテーブルから増分読み込みを実行する必要がある場合も、全体的に同じプロセスになります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-157">When having to perform an incremental load from multiple tables, the overall process is the same.</span></span> <span data-ttu-id="0ebcc-158">ただし、複数のテーブルの処理に対応できるようにパッケージのデザインを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-158">However, the design of the package needs to be changed to accommodate the processing of multiple tables.</span></span> <span data-ttu-id="0ebcc-159">複数のテーブルから増分読み込みを実行するパッケージの作成方法の詳細については、「 [複数のテーブルの増分読み込みを実行する](perform-an-incremental-load-of-multiple-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-159">For more information on how to create a package that performs an incremental load from multiples tables, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>

## <a name="samples-of-change-data-capture-packages"></a><span data-ttu-id="0ebcc-160">変更データ キャプチャ パッケージのサンプル</span><span class="sxs-lookup"><span data-stu-id="0ebcc-160">Samples of Change Data Capture Packages</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="0ebcc-161">には、パッケージで変更データ キャプチャを使用する方法を紹介したサンプルが 2 つ用意されています。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-161">provides two samples that demonstrate how to use change data capture in packages.</span></span> <span data-ttu-id="0ebcc-162">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ebcc-162">For more information, see the following topics:</span></span>

-   [<span data-ttu-id="0ebcc-163">Change Data Capture for Specified Interval パッケージ サンプルの Readme</span><span class="sxs-lookup"><span data-stu-id="0ebcc-163">Readme_Change Data Capture for Specified Interval Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133507)

-   [<span data-ttu-id="0ebcc-164">Change Data Capture since Last Request パッケージ サンプルの Readme</span><span class="sxs-lookup"><span data-stu-id="0ebcc-164">Readme_Change Data Capture since Last Request Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133508)

## <a name="related-tasks"></a><span data-ttu-id="0ebcc-165">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0ebcc-165">Related Tasks</span></span>

-   [<span data-ttu-id="0ebcc-166">変更データの間隔を指定する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-166">Specify an Interval of Change Data</span></span>](specify-an-interval-of-change-data.md)

-   [<span data-ttu-id="0ebcc-167">データの変更の準備ができているかどうかを判断する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-167">Determine Whether the Change Data Is Ready</span></span>](determine-whether-the-change-data-is-ready.md)

-   [<span data-ttu-id="0ebcc-168">変更データのクエリを準備する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-168">Prepare to Query for the Change Data</span></span>](prepare-to-query-for-the-change-data.md)

-   [<span data-ttu-id="0ebcc-169">変更データを取得する関数を作成する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-169">Create the Function to Retrieve the Change Data</span></span>](create-the-function-to-retrieve-the-change-data.md)

-   [<span data-ttu-id="0ebcc-170">変更データを取得および理解する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-170">Retrieve and Understand the Change Data</span></span>](retrieve-and-understand-the-change-data.md)

-   [<span data-ttu-id="0ebcc-171">挿入、更新、および削除を処理する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-171">Process Inserts, Updates, and Deletes</span></span>](process-inserts-updates-and-deletes.md)

-   [<span data-ttu-id="0ebcc-172">変換先に変更を適用する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-172">Apply the Changes to the Destination</span></span>](apply-the-changes-to-the-destination.md)

-   [<span data-ttu-id="0ebcc-173">複数のテーブルの増分読み込みを実行する</span><span class="sxs-lookup"><span data-stu-id="0ebcc-173">Perform an Incremental Load of Multiple Tables</span></span>](perform-an-incremental-load-of-multiple-tables.md)

## <a name="related-content"></a><span data-ttu-id="0ebcc-174">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0ebcc-174">Related Content</span></span>
 <span data-ttu-id="0ebcc-175">sqlblog.com のブログ投稿「[SSIS Design Pattern - Incremental Load](https://go.microsoft.com/fwlink/?LinkId=217679)」(SSIS のデザイン パターン - 増分読み込み)</span><span class="sxs-lookup"><span data-stu-id="0ebcc-175">Blog entry, [SSIS Design Pattern - Incremental Load](https://go.microsoft.com/fwlink/?LinkId=217679), on sqlblog.com</span></span>


