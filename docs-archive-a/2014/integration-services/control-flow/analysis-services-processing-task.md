---
title: Analysis Services 処理タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.f1
helpviewer_keywords:
- Analysis Services Processing task
- processing objects [Integration Services]
ms.assetid: e5748836-b4ce-4e17-ab6b-617a336f02f4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19ef8046c06c9131b3ea2eb8ffe267c026808dfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713397"
---
# <a name="analysis-services-processing-task"></a><span data-ttu-id="3e502-102">Analysis Services 処理タスク</span><span class="sxs-lookup"><span data-stu-id="3e502-102">Analysis Services Processing Task</span></span>
  <span data-ttu-id="3e502-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクは、テーブル モデル、キューブ、ディメンション、マイニング モデルなどの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="3e502-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task processes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects such as tabular models, cubes, dimensions, and mining models.</span></span>  
  
 <span data-ttu-id="3e502-104">テーブル モデルを処理する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3e502-104">When processing tabular models, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="3e502-105">テーブル モデルでは影響分析を実行できません。</span><span class="sxs-lookup"><span data-stu-id="3e502-105">You cannot perform impact analysis on tabular models.</span></span>  
  
-   <span data-ttu-id="3e502-106">テーブル モード用のいくつかの処理オプションが表示されません ([デフラグの処理] や [再計算の処理] など)。</span><span class="sxs-lookup"><span data-stu-id="3e502-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="3e502-107">これらの機能は DDL 実行タスクを使用すると実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e502-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
-   <span data-ttu-id="3e502-108">[インデックスの処理] オプションと [更新の処理] オプションはテーブル モデルには適していないので、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e502-108">The options Process Index and Process Update are not appropriate for tabular models and should not be used.</span></span>  
  
-   <span data-ttu-id="3e502-109">テーブル モデルでは、バッチ設定が無視されます。</span><span class="sxs-lookup"><span data-stu-id="3e502-109">Batch settings are ignored for tabular models.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="3e502-110">には、データ定義言語 (DDL) ステートメントやデータ マイニング予測クエリの実行など、ビジネス インテリジェンス操作を実行する多数のタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3e502-110">includes a number of tasks that perform business intelligence operations, such as running Data Definition Language (DDL) statements and data mining prediction queries.</span></span> <span data-ttu-id="3e502-111">関連するビジネス インテリジェンス タスクの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e502-111">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3e502-112">Analysis Services DDL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="3e502-112">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="3e502-113">データ マイニング クエリ タスク</span><span class="sxs-lookup"><span data-stu-id="3e502-113">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="object-processing"></a><span data-ttu-id="3e502-114">オブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="3e502-114">Object Processing</span></span>  
 <span data-ttu-id="3e502-115">複数のオブジェクトを同時に処理できます。</span><span class="sxs-lookup"><span data-stu-id="3e502-115">Multiple objects can be processed at the same time.</span></span> <span data-ttu-id="3e502-116">複数のオブジェクトを処理する場合は、バッチ内のすべてのオブジェクトの処理に適用する設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="3e502-116">When processing multiple objects, you define settings that apply to the processing of all the objects in the batch.</span></span>  
  
 <span data-ttu-id="3e502-117">バッチ内のオブジェクトは順に処理することも、並列処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e502-117">Objects in a batch can be processed in sequence or in parallel.</span></span> <span data-ttu-id="3e502-118">順に処理することが重要なオブジェクトがバッチに含まれていない場合、並列処理を行うと処理速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="3e502-118">If the batch does not contain objects for which processing sequence is important, parallel processing can speed up processing.</span></span> <span data-ttu-id="3e502-119">バッチ内のオブジェクトを並列処理する場合、タスクを構成して並列処理するオブジェクト数を決定することも、同時に処理するオブジェクト数を手動で指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e502-119">If objects in the batch are processed in parallel, you can configure the task to let it determine how many objects to process in parallel, or you can manually specify the number of objects to process at the same time.</span></span> <span data-ttu-id="3e502-120">オブジェクトを順に処理する場合、1 つのトランザクションにすべてのオブジェクトを含めるか、バッチ内のオブジェクトごとに異なるトランザクションを使用して、バッチのトランザクションの属性を設定できます。</span><span class="sxs-lookup"><span data-stu-id="3e502-120">If objects are processed sequentially, you can set a transaction attribute on the batch either by enlisting all objects in one transaction or by using a separate transaction for each object in the batch.</span></span>  
  
 <span data-ttu-id="3e502-121">分析オブジェクトを処理する場合、その分析オブジェクトに依存するオブジェクトも処理できます。</span><span class="sxs-lookup"><span data-stu-id="3e502-121">When you process analytic objects, you might also want to process the objects that depend on them.</span></span> <span data-ttu-id="3e502-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクには、選択したオブジェクトの他に、任意の依存オブジェクトを処理するオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3e502-122">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task includes an option to process any dependent objects in addition to the selected objects.</span></span>  
  
 <span data-ttu-id="3e502-123">通常は、ファクト テーブルを処理する前にディメンション テーブルを処理します。</span><span class="sxs-lookup"><span data-stu-id="3e502-123">Typically, you process dimension tables before processing fact tables.</span></span> <span data-ttu-id="3e502-124">ディメンション テーブルを処理する前にファクト テーブルを処理しようとすると、エラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e502-124">You may encounter errors if you try to process fact tables before processing the dimension tables.</span></span>  
  
 <span data-ttu-id="3e502-125">さらに、このタスクでは、ディメンション キーによるエラー処理を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e502-125">This task also lets you configure the handling of errors in dimension keys.</span></span> <span data-ttu-id="3e502-126">たとえば、エラーを無視したり、指定したエラー数が発生した後に停止するようにタスクを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3e502-126">For example, the task can ignore errors or stop after a specified number of errors occur.</span></span> <span data-ttu-id="3e502-127">この場合、タスクで既定のエラー構成を使用することも、カスタム エラー構成を構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e502-127">The task can use the default error configuration, or you can construct a custom error configuration.</span></span> <span data-ttu-id="3e502-128">カスタム エラー構成では、タスクによるエラー処理方法とエラー条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="3e502-128">In the custom error configuration, you specify how the task handles errors and the error conditions.</span></span> <span data-ttu-id="3e502-129">たとえば、4 番目のエラーが発生したときにタスクが実行を停止するように指定できます。また、 **NULL** キー値をタスクが処理する方法を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e502-129">For example, you can specify that the task should stop running when the fourth error occurs, or specify how the task should handle **Null** key values.</span></span> <span data-ttu-id="3e502-130">カスタム エラー構成には、エラー ログのパスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="3e502-130">The custom error configuration can also include the path of an error log.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e502-131">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクで処理できるのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ツールを使用して作成された分析オブジェクトのみです。</span><span class="sxs-lookup"><span data-stu-id="3e502-131">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task can process only analytic objects created by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools.</span></span>  
  
 <span data-ttu-id="3e502-132">このタスクは、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに読み込む一括挿入タスク、またはデータをテーブルに読み込むデータ フローを実装するデータ フロー タスクと組み合わせて使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="3e502-132">This task is frequently used in combination with a Bulk Insert task that loads data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, or a Data Flow task that implements a data flow that loads data into a table.</span></span> <span data-ttu-id="3e502-133">たとえば、オンライン トランザクション処理 (OLTP) データベースからデータを抽出して、データ ウェアハウス内のファクト テーブルに読み込むデータ フローがデータ フロー タスク内にあり、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクがこのタスクの処理後に呼び出され、データ ウェアハウスに構築されたキューブを処理する例などがあります。</span><span class="sxs-lookup"><span data-stu-id="3e502-133">For example, the Data Flow task might have a data flow that extracts data from an online transactional database (OLTP) database and loads it into a fact table in a data warehouse, after which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task is called to process the cube built on the data warehouse.</span></span>  
  
 <span data-ttu-id="3e502-134">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3e502-134">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3e502-135">詳しくは、「 [Analysis Services 接続マネージャー](../connection-manager/analysis-services-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3e502-135">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="3e502-136">エラー処理</span><span class="sxs-lookup"><span data-stu-id="3e502-136">Error Handling</span></span>  
  
## <a name="configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="3e502-137">Analysis Services 処理タスクの構成</span><span class="sxs-lookup"><span data-stu-id="3e502-137">Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="3e502-138">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="3e502-138">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3e502-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e502-139">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="3e502-140">[[Analysis Services 処理タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="3e502-140">[Analysis Services Processing Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="3e502-141">[[Analysis Services 処理タスク エディター] &#40;[Analysis Services] ページ&#41;](../analysis-services-processing-task-editor-analysis-services-page.md)</span><span class="sxs-lookup"><span data-stu-id="3e502-141">[Analysis Services Processing Task Editor &#40;Analysis Services Page&#41;](../analysis-services-processing-task-editor-analysis-services-page.md)</span></span>  
  
-   <span data-ttu-id="3e502-142">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="3e502-142">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="3e502-143">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="3e502-143">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="3e502-144">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="3e502-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="3e502-145">プログラムによる Analysis Services 処理タスクの構成</span><span class="sxs-lookup"><span data-stu-id="3e502-145">Programmatic Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="3e502-146">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e502-146">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.DTSProcessingTask>  
  
  
