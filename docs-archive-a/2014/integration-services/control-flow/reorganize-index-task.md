---
title: インデックスの再編成タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3f910391bd3a5a35770bb677bc17c91a00ace457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642220"
---
# <a name="reorganize-index-task"></a><span data-ttu-id="227f0-102">インデックスの再編成タスク</span><span class="sxs-lookup"><span data-stu-id="227f0-102">Reorganize Index Task</span></span>
  <span data-ttu-id="227f0-103">インデックスの再編成タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのテーブルおよびビューのインデックスを再編成します。</span><span class="sxs-lookup"><span data-stu-id="227f0-103">The Reorganize Index task reorganizes indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="227f0-104">インデックスの管理の詳細については、「 [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="227f0-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="227f0-105">インデックスの再編成タスクを使用すると、パッケージは単一データベースまたは複数データベースのインデックスを再編成できます。</span><span class="sxs-lookup"><span data-stu-id="227f0-105">By using the Reorganize Index task, a package can reorganize indexes in a single database or multiple databases.</span></span> <span data-ttu-id="227f0-106">タスクにより単一データベースのインデックスのみを再編成する場合、インデックスの再編成の対象となるビューまたはテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="227f0-106">If the task reorganizes only the indexes in a single database, you can choose the views or the tables whose indexes the task reorganizes.</span></span> <span data-ttu-id="227f0-107">また、インデックスの再編成タスクには、ラージ オブジェクト データを圧縮するオプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="227f0-107">The Reorganize Index task also includes an option to compact large object data.</span></span> <span data-ttu-id="227f0-108">ラージ オブジェクト データとは、`image`、`text`、`ntext`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)`、または `xml` データ型のデータのことです。</span><span class="sxs-lookup"><span data-stu-id="227f0-108">Large object data is data with the `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, or `xml` data type.</span></span> <span data-ttu-id="227f0-109">詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="227f0-109">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="227f0-110">インデックスの再編成タスクは、Transact-SQL ALTER INDEX ステートメントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="227f0-110">The Reorganize Index task encapsulates the Transact-SQL ALTER INDEX statement.</span></span> <span data-ttu-id="227f0-111">ラージ オブジェクト データの圧縮を選択した場合、Transact-SQL ALTER INDEX ステートメントは REORGANIZE WITH (LOB_COMPACTION = ON) 句を使用します。それ以外の場合は、LOB_COMPACTION が OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="227f0-111">If you choose to compact large object data, the statement uses the REORGANIZE WITH (LOB_COMPACTION = ON) clause, otherwise LOB_COMPACTION is set to OFF.</span></span> <span data-ttu-id="227f0-112">詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="227f0-112">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="227f0-113">実行する Transact-SQL ステートメントを作成するためにタスクが費やす時間は、タスクが再編成するインデックス数に比例します。</span><span class="sxs-lookup"><span data-stu-id="227f0-113">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of indexes the task reorganizes.</span></span> <span data-ttu-id="227f0-114">多数のインデックスを含むデータベースのすべてのテーブルおよびビュー内のインデックスの再編成、または複数のデータベース内のインデックスの再編成を実行するようにタスクが構成されている場合、タスクが Transact-SQL ステートメントを生成するには非常に長い時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="227f0-114">If the task is configured to reorganize indexes in all the tables and views in a database that holds a large number of indexes, or to reorganize indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-reorganize-index-task"></a><span data-ttu-id="227f0-115">インデックスの再構成タスクの構成</span><span class="sxs-lookup"><span data-stu-id="227f0-115">Configuration of the Reorganize Index Task</span></span>  
 <span data-ttu-id="227f0-116">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="227f0-116">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="227f0-117">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="227f0-117">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="227f0-118">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="227f0-118">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="227f0-119">[[インデックスの再構成タスク] &#40;メンテナンス プラン&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="227f0-119">[Reorganize Index Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="227f0-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="227f0-120">Related Tasks</span></span>  
 <span data-ttu-id="227f0-121">これらのプロパティを [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="227f0-121">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227f0-122">参照</span><span class="sxs-lookup"><span data-stu-id="227f0-122">See Also</span></span>  
 <span data-ttu-id="227f0-123">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="227f0-123">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="227f0-124">制御フロー</span><span class="sxs-lookup"><span data-stu-id="227f0-124">Control Flow</span></span>](control-flow.md)  
  
  
