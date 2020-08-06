---
title: Analysis Services キャッシュをクリアする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6bf66fdd-6a03-4cea-b7e2-eb676ff276ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: e4890dd322406dcf48bc6b8eca89f292cfe132a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713642"
---
# <a name="clear-the-analysis-services-caches"></a><span data-ttu-id="f4140-102">Analysis Services キャッシュのクリア</span><span class="sxs-lookup"><span data-stu-id="f4140-102">Clear the Analysis Services Caches</span></span>
  <span data-ttu-id="f4140-103">Analysis Services は、クエリのパフォーマンス向上のためにデータをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="f4140-103">Analysis Services caches data to boost query performance.</span></span> <span data-ttu-id="f4140-104">このトピックでは、MDX クエリへの応答で作成されたキャッシュを、XMLA ClearCache コマンドを使用してクリアするための推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4140-104">This topic provides recommendations for using the XMLA ClearCache command to clear caches that were created in response to an MDX query.</span></span> <span data-ttu-id="f4140-105">ClearCache を実行した場合の効果は、テーブル モデルまたは多次元モデルのどちらを使用しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f4140-105">The effects of running ClearCache vary depending on whether you are using a tabular or multidimensional model.</span></span>  
  
 <span data-ttu-id="f4140-106">**多次元モデルのキャッシュをクリアする場合**</span><span class="sxs-lookup"><span data-stu-id="f4140-106">**When to clear the cache for multidimensional models**</span></span>  
  
 <span data-ttu-id="f4140-107">多次元データベースの場合、Analysis Services は、計算を評価する際、数式エンジン内にキャッシュを構築し、ディメンション クエリやメジャー グループ クエリの結果に対しては、ストレージ エンジン内にキャッシュを構築します。</span><span class="sxs-lookup"><span data-stu-id="f4140-107">For multidimensional databases, Analysis Services builds caches in the formula engine when evaluating a calculation, and in the storage engine for the results of dimension queries and measure group queries.</span></span> <span data-ttu-id="f4140-108">メジャー グループ クエリは、数式エンジンがセル座標またはサブキューブのデータを測定する必要がある場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="f4140-108">Measure group queries occur when the formula engine needs measure data for a cell coordinate or subcube.</span></span> <span data-ttu-id="f4140-109">ディメンション クエリは、不自然階層をクエリするときや、autoexists を適用するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="f4140-109">Dimension queries occur when querying unnatural hierarchies and when applying autoexists.</span></span>  
  
 <span data-ttu-id="f4140-110">パフォーマンス テストを実施する場合、キャッシュをクリアすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f4140-110">Clearing the cache is recommended when conducting performance testing.</span></span> <span data-ttu-id="f4140-111">次回のテスト実行までの間にキャッシュをクリアすることで、クエリ デザインの変更による影響を計測するテストの結果が、キャッシュによってゆがめられないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="f4140-111">By clearing the cache between test runs, you ensure that caching does not skew any test results that measure the impact of a query design change.</span></span>  
  
 <span data-ttu-id="f4140-112">**テーブル モデルのキャッシュをクリアする場合**</span><span class="sxs-lookup"><span data-stu-id="f4140-112">**When to clear the cache for tabular models**</span></span>  
  
 <span data-ttu-id="f4140-113">一般的にテーブル モデルはメモリに保存されます。クエリが実行されるとき、集計やその他の計算はメモリで実行されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-113">Tabular models are generally stored in memory, where aggregations and other calculations are performed at the time a query is executed.</span></span> <span data-ttu-id="f4140-114">そのため、ClearCache コマンドがテーブル モデルに与える影響は限定的です。</span><span class="sxs-lookup"><span data-stu-id="f4140-114">As such, the ClearCache command has a limited effect on tabular models.</span></span> <span data-ttu-id="f4140-115">テーブル モデルでは、MDX クエリが実行される場合、そのデータが Analysis Services キャッシュに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-115">For a tabular model, data may be added to the Analysis Services caches if MDX queries are run against it.</span></span> <span data-ttu-id="f4140-116">特に、MDX によって参照される DAX メジャーおよび autoexists 操作は、結果を数式キャッシュおよびディメンション キャッシュ内にそれぞれキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="f4140-116">In particular, DAX measures referenced by MDX and autoexists operations can cache results in the formula cache and dimension cache respectively.</span></span> <span data-ttu-id="f4140-117">ただし、不自然階層とメジャー グループ クエリは、ストレージ エンジン内にキャッシュしないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4140-117">Note however, that unnatural hierarchies and measure group queries do not cache results in the storage engine.</span></span> <span data-ttu-id="f4140-118">また、重要な点は、DAX クエリは、数式エンジンおよびストレージ エンジン内に結果をキャッシュしないことです。</span><span class="sxs-lookup"><span data-stu-id="f4140-118">Additionally, it is important to recognize that DAX queries do not cache results in the formula and storage engine.</span></span> <span data-ttu-id="f4140-119">MDX クエリの結果としてキャッシュが存在する限り、テーブル モードに対する ClearCache の実行は、システムからのすべてのキャッシュ データを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f4140-119">To the extent that caches exist as a result of MDX queries, running ClearCache against a tabular model will invalidate any cached data from the system.</span></span>  
  
 <span data-ttu-id="f4140-120">また、ClearCache を実行すると、xVelocity メモリ内分析エンジン (VertiPaq) のメモリ内キャッシュもクリアされます。</span><span class="sxs-lookup"><span data-stu-id="f4140-120">Running ClearCache will also clear in-memory caches in the xVelocity in-memory analytics engine (VertiPaq).</span></span> <span data-ttu-id="f4140-121">xVelocity エンジンは、キャッシュされた小さな結果セットを保持します。</span><span class="sxs-lookup"><span data-stu-id="f4140-121">The xVelocity engine maintains a small set of cached results.</span></span> <span data-ttu-id="f4140-122">ClearCache を実行すると、xVelocity エンジンのキャッシュも無効化されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-122">Running ClearCache will invalidate these caches in the xVelocity engine.</span></span>  
  
 <span data-ttu-id="f4140-123">最後に、ClearCache を実行すると、テーブル モデルが `DirectQuery` モード用に再構築されるときにメモリ内の残存データも削除されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-123">Finally, running ClearCache will also remove residual data that is left in memory when a tabular model is reconfigured for `DirectQuery` mode.</span></span> <span data-ttu-id="f4140-124">これは、厳密に管理される機密データがモデルに含まれる場合、特に重要です。</span><span class="sxs-lookup"><span data-stu-id="f4140-124">This is particularly important if the model contains sensitive data that is subject to tight controls.</span></span> <span data-ttu-id="f4140-125">この場合、ClearCache の実行は、機密データが想定した場所にのみ存在することを確実にするための予防的なアクションとなります。</span><span class="sxs-lookup"><span data-stu-id="f4140-125">In this case, running ClearCache is a precautionary action that you can take to ensure that sensitive data exists only where you expect it to be.</span></span> <span data-ttu-id="f4140-126">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用してモデルを配置し、クエリ モードを変更する場合、キャッシュは手動でクリアする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4140-126">Clearing the cache manually is necessary if you are using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to deploy the model and change the query mode.</span></span> <span data-ttu-id="f4140-127">一方、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用して、モデルに `DirectQuery` を指定した場合、そのクエリ モードを使用するようにモデルを切り替えると、パーティションが自動的にキャッシュをクリアします。</span><span class="sxs-lookup"><span data-stu-id="f4140-127">In contrast, using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to specify `DirectQuery` on the model and partitions will automatically clear the cache when you switch the model to use that query mode.</span></span>  
  
 <span data-ttu-id="f4140-128">多次元モデルのキャッシュをパフォーマンス テスト中にクリアするための推奨事項と比べると、テーブル モデルのキャッシュをクリアするための推奨事項はあまり多くありません。</span><span class="sxs-lookup"><span data-stu-id="f4140-128">Compared with recommendations for clearing multidimensional model caches during performance testing, there is no broad recommendation for clearing tabular model caches.</span></span> <span data-ttu-id="f4140-129">機密データを含むテーブル モデルの配置を管理していない場合は、キャッシュをクリアするために実施される特定の管理タスクはありません。</span><span class="sxs-lookup"><span data-stu-id="f4140-129">If you are not managing the deployment of a tabular model that contains sensitive data, there is no specific administrative task that calls for clearing the cache.</span></span>  
  
## <a name="clear-the-cache-for-analysis-services-models"></a><span data-ttu-id="f4140-130">Analysis Services モデルのキャッシュをクリアする</span><span class="sxs-lookup"><span data-stu-id="f4140-130">Clear the cache for Analysis Services models</span></span>  
 <span data-ttu-id="f4140-131">キャッシュをクリアするには、XMLA と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4140-131">To clear the cache, use XMLA and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f4140-132">データベース、キューブ、ディメンション、テーブルのキャッシュ、またはメジャー グループ レベルのキャッシュをクリアできます。</span><span class="sxs-lookup"><span data-stu-id="f4140-132">You can clear the cache at the database, cube, dimension or table, or measure group level.</span></span> <span data-ttu-id="f4140-133">次の手順は、データベース レベルでキャッシュをクリアするために、多次元モデルとテーブル モデルの両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-133">The following steps for clearing the cache at the database level apply to both multidimensional models and tabular models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4140-134">厳密なパフォーマンス テストを実施するには、より包括的なキャッシュをクリアする手法が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4140-134">Rigorous performance testing might require a more comprehensive approach to clearing the cache.</span></span> <span data-ttu-id="f4140-135">Analysis Services とファイル システム キャッシュをフラッシュする方法については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539)」のキャッシュのクリアに関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4140-135">For instructions on how to flush Analysis Services and file system caches, see the section on clearing caches in the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="f4140-136">多次元モードとテーブル モードの両方に対して、これらのキャッシュをクリアするには、ClearCache が実行された時点でキャッシュを無効にし、その後、次のクエリを受信したときに、そのキャッシュを空にするという 2 段階の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="f4140-136">For both multidimensional and tabular models, clearing some of these caches can be a two-step process that consists of invalidating the cache when ClearCache executes, followed by emptying the cache when the next query is received.</span></span> <span data-ttu-id="f4140-137">キャッシュが実際に空になると、メモリの消費量の削減が明らかになります。</span><span class="sxs-lookup"><span data-stu-id="f4140-137">A reduction in memory consumption will be evident only after the cache is actually emptied.</span></span>  
  
 <span data-ttu-id="f4140-138">キャッシュをクリアするには、XMLA クエリの `ClearCache` ステートメントに、オブジェクトの識別子を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4140-138">Clearing the cache requires that you provide an object identifier to the `ClearCache` statement in an XMLA query.</span></span> <span data-ttu-id="f4140-139">このトピックの最初のステップでは、オブジェクト識別子を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f4140-139">The first step in this topic explains how to get an object identifier.</span></span>  
  
#### <a name="step-1-get-the-object-identifier"></a><span data-ttu-id="f4140-140">手順 1: オブジェクトの識別子を取得する</span><span class="sxs-lookup"><span data-stu-id="f4140-140">Step 1: Get the object identifier</span></span>  
  
1.  <span data-ttu-id="f4140-141">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でオブジェクトを右クリックし、 **[プロパティ]** を選択して、 **[プロパティ]** ペインの ID プロパティの値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f4140-141">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click an object, select **Properties**, and copy the value from the ID property in the **Properties** pane.</span></span> <span data-ttu-id="f4140-142">この方法は、データベース、キューブ、ディメンション、またはテーブルに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4140-142">This approach works for the database, cube, dimension, or table.</span></span>  
  
2.  <span data-ttu-id="f4140-143">メジャー グループの ID を取得するには、メジャー グループを右クリックし、 **[メジャー グループをスクリプト化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4140-143">To get the measure group ID, right-click the measure group and select **Script Measure Group As**.</span></span> <span data-ttu-id="f4140-144">**[作成]** または **[変更]** のいずれかを選択し、クエリをウィンドウに送信します。</span><span class="sxs-lookup"><span data-stu-id="f4140-144">Choose either **Create** or **Alter**, and send the query to a window.</span></span> <span data-ttu-id="f4140-145">メジャー グループの ID は、オブジェクト定義に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-145">The ID of the measure group will be visible in the object definition.</span></span> <span data-ttu-id="f4140-146">オブジェクト定義の ID をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f4140-146">Copy the ID of the object definition.</span></span>  
  
#### <a name="step-2-run-the-query"></a><span data-ttu-id="f4140-147">手順 2: クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="f4140-147">Step 2: Run the query</span></span>  
  
1.  <span data-ttu-id="f4140-148">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でデータベースを右クリックし、 **[新しいクエリ]** をポイントして、 **[XMLA]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4140-148">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a database, point to **New Query**, and select **XMLA**.</span></span>  
  
2.  <span data-ttu-id="f4140-149">XMLA クエリ ウィンドウに次のコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f4140-149">Copy the following code example into the XMLA query window.</span></span> <span data-ttu-id="f4140-150">`DatabaseID` を現在の接続のデータベース ID に変更します。</span><span class="sxs-lookup"><span data-stu-id="f4140-150">Change `DatabaseID` to the ID of the database on the current connection.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
      </Object>  
    </ClearCache>  
  
    ```  
  
     <span data-ttu-id="f4140-151">または、メジャー グループなどの子オブジェクトのパスを指定して、そのオブジェクトのキャッシュだけをクリアすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f4140-151">Alternatively, you can specify a path of a child object, such as a measure group, to clear the cache for just that object.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
            <CubeID>Adventure Works</CubeID>  
            <MeasureGroupID>Fact Currency Rate</MeasureGroupID>  
      </Object>  
    </ClearCache>  
    ```  
  
3.  <span data-ttu-id="f4140-152">F5 キーを押してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f4140-152">Press F5 to execute the query.</span></span> <span data-ttu-id="f4140-153">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4140-153">You should see the following result:</span></span>  
  
    ```  
    <return xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty" />  
    </return>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f4140-154">参照</span><span class="sxs-lookup"><span data-stu-id="f4140-154">See Also</span></span>  
 <span data-ttu-id="f4140-155">[Analysis Services での管理タスクのスクリプト作成](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f4140-155">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="f4140-156">Analysis Services インスタンスの監視</span><span class="sxs-lookup"><span data-stu-id="f4140-156">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
