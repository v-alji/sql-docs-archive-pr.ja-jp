---
title: 統計の更新タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.updatestatisticstask.f1
helpviewer_keywords:
- updating statistics
- Update Statistics task [Integration Services]
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1507ada1e4fa087901383930fce4996c191fb553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631169"
---
# <a name="update-statistics-task"></a><span data-ttu-id="df296-102">統計の更新タスク</span><span class="sxs-lookup"><span data-stu-id="df296-102">Update Statistics Task</span></span>
  <span data-ttu-id="df296-103">統計の更新タスクは、指定されたテーブルまたはインデックス付きビュー内の 1 つ以上の統計グループ (コレクション) についてキー値の分布に関する情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="df296-103">The Update Statistics task updates information about the distribution of key values for one or more statistics groups (collections) in the specified table or indexed view.</span></span> <span data-ttu-id="df296-104">詳細については、[統計](../../relational-databases/statistics/statistics.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df296-104">For more information, see [Statistics](../../relational-databases/statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="df296-105">統計の更新タスクを使用すると、パッケージは単一データベースまたは複数のデータベース内の統計を更新できます。</span><span class="sxs-lookup"><span data-stu-id="df296-105">By using the Update Statistics task, a package can update statistics for a single database or multiple databases.</span></span> <span data-ttu-id="df296-106">このタスクにより単一データベース内の統計のみを更新する場合、タスクによって統計を更新するビューおよびテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="df296-106">If the task updates only the statistics in a single database, you can choose the views or the tables whose statistics the task updates.</span></span> <span data-ttu-id="df296-107">更新は、すべての統計、列統計のみ、またはインデックス統計のみを対象とするように構成できます。</span><span class="sxs-lookup"><span data-stu-id="df296-107">You can configure the update to update all statistics, column statistics only, or index statistics only.</span></span>  
  
 <span data-ttu-id="df296-108">このタスクは、次の引数および句を含めて UPDATE STATISTICS ステートメントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="df296-108">This task encapsulates an UPDATE STATISTICS statement, including the following arguments and clauses:</span></span>  
  
-   <span data-ttu-id="df296-109">*table_name* または *view_name* 引数。</span><span class="sxs-lookup"><span data-stu-id="df296-109">The *table_name* or *view_name* argument.</span></span>  
  
-   <span data-ttu-id="df296-110">すべての統計に更新が適用される場合、暗黙的に WITH ALL 句が含められます。</span><span class="sxs-lookup"><span data-stu-id="df296-110">If the update applies to all statistics, the WITH ALL clause is implied.</span></span>  
  
-   <span data-ttu-id="df296-111">列統計にのみ更新が適用される場合、WITH COLUMN 句が含められます。</span><span class="sxs-lookup"><span data-stu-id="df296-111">If the update applies only to columns, the WITH COLUMN clause is included.</span></span>  
  
-   <span data-ttu-id="df296-112">インデックス統計にのみ更新が適用される場合、WITH INDEX 句が含められます。</span><span class="sxs-lookup"><span data-stu-id="df296-112">If the update applies only to indexes, the WITH INDEX clause is included.</span></span>  
  
 <span data-ttu-id="df296-113">統計の更新タスクにより複数データベース内の統計を更新する場合、タスクは複数の UPDATE STATISTICS ステートメントを各テーブルまたはビューに対して 1 つずつ実行します。</span><span class="sxs-lookup"><span data-stu-id="df296-113">If the Update Statistics task updates statistics in multiple databases, the task runs multiple UPDATE STATISTICS statements, one for each table or view.</span></span> <span data-ttu-id="df296-114">UPDATE STATISTICS の全インスタンスで同じ句が使用されますが、 *table_name* または *view_name* の値が異なります。</span><span class="sxs-lookup"><span data-stu-id="df296-114">All instances of UPDATE STATISTICS use the same clause, but different *table_name* or *view_name* values.</span></span> <span data-ttu-id="df296-115">詳細については、「[CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql)」および「[UPDATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df296-115">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) and [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="df296-116">実行する Transact-SQL ステートメントを作成するためにタスクが費やす時間は、タスクが更新する統計数に比例します。</span><span class="sxs-lookup"><span data-stu-id="df296-116">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of statistics the task updates.</span></span> <span data-ttu-id="df296-117">多数のインデックスを含むデータベースのすべてのテーブルおよびビュー内の統計の更新、または複数のデータベース内の統計の更新を実行するようにタスクが構成されている場合、タスクが Transact-SQL ステートメントを生成するには非常に長い時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="df296-117">If the task is configured to update statistics in all the tables and views in a database with a large number of indexes, or to update statistics in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-update-statistics-task"></a><span data-ttu-id="df296-118">統計の更新タスクの構成</span><span class="sxs-lookup"><span data-stu-id="df296-118">Configuration of the Update Statistics Task</span></span>  
 <span data-ttu-id="df296-119">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="df296-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="df296-120">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="df296-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="df296-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df296-121">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="df296-122">[[統計の更新タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="df296-122">[Update Statistics Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="df296-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="df296-123">Related Tasks</span></span>  
 <span data-ttu-id="df296-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df296-124">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="df296-125">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="df296-125">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="df296-126">参照</span><span class="sxs-lookup"><span data-stu-id="df296-126">See Also</span></span>  
 <span data-ttu-id="df296-127">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="df296-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="df296-128">制御フロー</span><span class="sxs-lookup"><span data-stu-id="df296-128">Control Flow</span></span>](control-flow.md)  
  
  
