---
title: データベースの圧縮タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 587777928e362e87e4b691e3c46167c1239984cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644091"
---
# <a name="shrink-database-task"></a><span data-ttu-id="5fe16-102">データベースの圧縮タスク</span><span class="sxs-lookup"><span data-stu-id="5fe16-102">Shrink Database Task</span></span>
  <span data-ttu-id="5fe16-103">データベースの圧縮タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータおよびログ ファイルのサイズを縮小します。</span><span class="sxs-lookup"><span data-stu-id="5fe16-103">The Shrink Database task reduces the size of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database data and log files.</span></span>  
  
 <span data-ttu-id="5fe16-104">データベースの圧縮タスクを使用すると、パッケージは単一データベースまたは複数データベースのファイルを圧縮できます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-104">By using the Shrink Database task, a package can shrink files for a single database or multiple databases.</span></span>  
  
 <span data-ttu-id="5fe16-105">ファイルの末尾にあるデータのページを、ファイルの先頭に近い占有されていない領域に移動することにより、データ ファイルが圧縮され、領域が回復されます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-105">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="5fe16-106">ファイル末尾に十分な空き領域が作成された場合は、ファイル末尾のデータ ページの割り当てを解除して、ファイル システムに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-106">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="5fe16-107">ファイルを圧縮するために移動されたデータは、ファイル内のあらゆる使用可能な場所に分散される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fe16-107">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="5fe16-108">これにより、インデックスの断片化が発生し、広範なインデックスを検索するクエリのパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fe16-108">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="5fe16-109">断片化を解消するには、圧縮後にファイルのインデックスを再構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5fe16-109">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="commands"></a><span data-ttu-id="5fe16-110">コマンド</span><span class="sxs-lookup"><span data-stu-id="5fe16-110">Commands</span></span>  
 <span data-ttu-id="5fe16-111">データベースの圧縮タスクは DBCC SHRINKDATABASE コマンドをカプセル化します。DBCC SHRINKDATABASE コマンドには、次の引数とオプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-111">The Shrink Database task encapsulates a DBCC SHRINKDATABASE command, including the following arguments and options:</span></span>  
  
-   <span data-ttu-id="5fe16-112">*database_name*</span><span class="sxs-lookup"><span data-stu-id="5fe16-112">*database_name*</span></span>  
  
-   <span data-ttu-id="5fe16-113">*target_percent*</span><span class="sxs-lookup"><span data-stu-id="5fe16-113">*target_percent*</span></span>  
  
-   <span data-ttu-id="5fe16-114">NOTRUNCATE または TRUNCATEONLY</span><span class="sxs-lookup"><span data-stu-id="5fe16-114">NOTRUNCATE or TRUNCATEONLY.</span></span>  
  
 <span data-ttu-id="5fe16-115">データベースの圧縮タスクで複数のデータベースを圧縮する場合、複数の SHRINKDATABASE コマンドが、1 つのデータベースにつき 1 回ずつ実行されます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-115">If the Shrink Database task shrinks multiple databases, the task runs multiple SHRINKDATABASE commands, one for each database.</span></span> <span data-ttu-id="5fe16-116">SHRINKDATABASE コマンドのすべてのインスタンスは、 *database_name* 引数以外の引数に同じ値を使用します。</span><span class="sxs-lookup"><span data-stu-id="5fe16-116">All instances of the SHRINKDATABASE command use the same argument values, except for the *database_name* argument.</span></span> <span data-ttu-id="5fe16-117">詳細については、「[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fe16-117">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span>  
  
## <a name="configuration-of-the-shrink-database-task"></a><span data-ttu-id="5fe16-118">データベースの圧縮タスクの構成</span><span class="sxs-lookup"><span data-stu-id="5fe16-118">Configuration of the Shrink Database Task</span></span>  
 <span data-ttu-id="5fe16-119">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="5fe16-120">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fe16-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="5fe16-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fe16-121">For more information about the properties that you can set in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="5fe16-122">[[データベースの圧縮タスク] &#40;メンテナンス プラン&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="5fe16-122">[Shrink Database Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)</span></span>  
  
 <span data-ttu-id="5fe16-123">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="5fe16-123">For more information about setting these properties in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="5fe16-124">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="5fe16-124">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
