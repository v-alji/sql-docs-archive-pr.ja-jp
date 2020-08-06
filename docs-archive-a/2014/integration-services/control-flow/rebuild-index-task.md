---
title: インデックスの再構築タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33bbe25bc8c47f4f749f95dbb7096c3a76c25297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642222"
---
# <a name="rebuild-index-task"></a><span data-ttu-id="073e8-102">インデックスの再構築タスク</span><span class="sxs-lookup"><span data-stu-id="073e8-102">Rebuild Index Task</span></span>
  <span data-ttu-id="073e8-103">インデックスの再構築タスクでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのテーブルおよびビュー内のインデックスを再構築します。</span><span class="sxs-lookup"><span data-stu-id="073e8-103">The Rebuild Index task rebuilds indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="073e8-104">インデックスの管理の詳細については、「 [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073e8-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="073e8-105">インデックスの再構築タスクを使用すると、パッケージは単一データベースまたは複数のデータベース内のインデックスを再構築できます。</span><span class="sxs-lookup"><span data-stu-id="073e8-105">By using the Rebuild Index task, a package can rebuild indexes in a single database or multiple databases.</span></span> <span data-ttu-id="073e8-106">このタスクにより単一データベース内のインデックスのみを再構築する場合、タスクによってインデックスを再構築するビューおよびテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="073e8-106">If the task rebuilds only the indexes in a single database, you can choose the views and tables whose indexes the task rebuilds.</span></span>  
  
 <span data-ttu-id="073e8-107">このタスクは、次のインデックス再構築オプションを付けて ALTER INDEX REBUILD ステートメントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="073e8-107">This task encapsulates an ALTER INDEX REBUILD statement with the following index rebuild options:</span></span>  
  
-   <span data-ttu-id="073e8-108">FILLFACTOR のパーセント値を指定するか、または FILLFACTOR の元の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="073e8-108">Specify a FILLFACTOR percentage or use the original FILLFACTOR amount.</span></span>  
  
-   <span data-ttu-id="073e8-109">PAD_INDEX = ON と設定すると、FILLFACTOR で指定された空き容量がインデックスの中間レベル ページに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="073e8-109">Set PAD_INDEX = ON to allocate the free space specified by FILLFACTOR to the intermediate-level pages of the index.</span></span>  
  
-   <span data-ttu-id="073e8-110">SORT_IN_TEMPDB = ON と設定すると、インデックスの作成に使用された並べ替えの途中結果が tempdb に格納されます。</span><span class="sxs-lookup"><span data-stu-id="073e8-110">Set SORT_IN_TEMPDB = ON to store the intermediate sort result used to rebuild the index in tempdb.</span></span> <span data-ttu-id="073e8-111">並べ替えの途中結果が OFF に設定されている場合、インデックスと同じデータベースに結果が保存されます。</span><span class="sxs-lookup"><span data-stu-id="073e8-111">When the intermediate sort result is set to OFF, the result is stored in the same database as the index.</span></span>  
  
-   <span data-ttu-id="073e8-112">IGNORE_DUP_KEY = ON と設定すると、UNIQUE 制約に違反するレコードを含む複数行の挿入操作を行う場合に、UNIQUE 制約に違反しないレコードを挿入できるようになります。</span><span class="sxs-lookup"><span data-stu-id="073e8-112">Set IGNORE_DUP_KEY = ON to allow a multirow insert operation that includes records that violate unique constraints to insert the records that do not violate the unique constraints.</span></span>  
  
-   <span data-ttu-id="073e8-113">ONLINE = ON と設定すると、テーブルをロックしたままにせず、インデックスの再構築中に基になるテーブルに対するクエリまたは更新を行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="073e8-113">Set ONLINE = ON to not hold table locks so that queries or updates to the underlying table can proceed during re-indexing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="073e8-114">オンラインでのインデックス操作は、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="073e8-114">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="073e8-115">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073e8-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="073e8-116">ALTER INDEX ステートメントおよびインデックスの再構築オプションの詳細については、「[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073e8-116">For more information about the ALTER INDEX statement and index rebuild options, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="073e8-117">実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを作成するためにタスクが費やす時間は、タスクが再構築するインデックス数に比例します。</span><span class="sxs-lookup"><span data-stu-id="073e8-117">The time the task takes to create the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that the task runs is proportionate to the number of indexes the task rebuilds.</span></span> <span data-ttu-id="073e8-118">多数のインデックスを含むデータベースのすべてのテーブルおよびビュー内のインデックスの再構築、または複数のデータベース内のインデックスの再構築を実行するようにタスクが構成されている場合、タスクが Transact-SQL ステートメントを生成するには非常に長い時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="073e8-118">If the task is configured to rebuild indexes in all the tables and views in a database with a large number of indexes, or to rebuild indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-rebuild-index-task"></a><span data-ttu-id="073e8-119">インデックスの再構築タスクの構成</span><span class="sxs-lookup"><span data-stu-id="073e8-119">Configuration of the Rebuild Index Task</span></span>  
 <span data-ttu-id="073e8-120">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="073e8-120">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="073e8-121">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="073e8-121">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="073e8-122">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="073e8-122">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
 <span data-ttu-id="073e8-123">[[インデックスの再構築タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="073e8-123">[Rebuild Index Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="073e8-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="073e8-124">Related Tasks</span></span>  
 <span data-ttu-id="073e8-125">これらのプロパティを [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073e8-125">For more about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073e8-126">参照</span><span class="sxs-lookup"><span data-stu-id="073e8-126">See Also</span></span>  
 <span data-ttu-id="073e8-127">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="073e8-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="073e8-128">制御フロー</span><span class="sxs-lookup"><span data-stu-id="073e8-128">Control Flow</span></span>](control-flow.md)  
  
  
