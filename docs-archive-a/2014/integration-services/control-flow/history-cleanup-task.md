---
title: 履歴クリーンアップ タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84bc697b7fb18269fc581cea51e111aebc82c15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631190"
---
# <a name="history-cleanup-task"></a><span data-ttu-id="ddac3-102">履歴クリーンアップ タスク</span><span class="sxs-lookup"><span data-stu-id="ddac3-102">History Cleanup Task</span></span>
  <span data-ttu-id="ddac3-103">履歴クリーンアップ タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb データベースの、次の履歴テーブル内のエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="ddac3-103">The History Cleanup task deletes entries in the following history tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
-   <span data-ttu-id="ddac3-104">backupfile</span><span class="sxs-lookup"><span data-stu-id="ddac3-104">backupfile</span></span>  
  
-   <span data-ttu-id="ddac3-105">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="ddac3-105">backupfilegroup</span></span>  
  
-   <span data-ttu-id="ddac3-106">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="ddac3-106">backupmediafamily</span></span>  
  
-   <span data-ttu-id="ddac3-107">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="ddac3-107">backupmediaset</span></span>  
  
-   <span data-ttu-id="ddac3-108">backupset</span><span class="sxs-lookup"><span data-stu-id="ddac3-108">backupset</span></span>  
  
-   <span data-ttu-id="ddac3-109">restorefile</span><span class="sxs-lookup"><span data-stu-id="ddac3-109">restorefile</span></span>  
  
-   <span data-ttu-id="ddac3-110">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="ddac3-110">restorefilegroup</span></span>  
  
-   <span data-ttu-id="ddac3-111">restorehistory</span><span class="sxs-lookup"><span data-stu-id="ddac3-111">restorehistory</span></span>  
  
 <span data-ttu-id="ddac3-112">履歴クリーンアップ タスクを使用すると、パッケージは、バックアップ操作と復元操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ、およびデータベース メンテナンス プランに関連する履歴データを削除できます。</span><span class="sxs-lookup"><span data-stu-id="ddac3-112">By using the History Cleanup task, a package can delete historical data related to backup and restore activities, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, and database maintenance plans.</span></span>  
  
 <span data-ttu-id="ddac3-113">このタスクは、sp_delete_backuphistory システム ストアド プロシージャをカプセル化し、指定した日付を引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="ddac3-113">This task encapsulates the sp_delete_backuphistory system stored procedure and passes the specified date to the procedure as an argument.</span></span> <span data-ttu-id="ddac3-114">詳細については、「[sp_delete_backuphistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddac3-114">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
## <a name="configuration-of-the-history-cleanup-task"></a><span data-ttu-id="ddac3-115">履歴クリーンアップ タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ddac3-115">Configuration of the History Cleanup Task</span></span>  
 <span data-ttu-id="ddac3-116">このタスクには、履歴テーブルに保持されるデータの、最も古い日付を指定するプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddac3-116">The task includes a property for specifying the oldest date of data retained in the history tables.</span></span> <span data-ttu-id="ddac3-117">日付は、現在の日付から起算して、日、週、月、または年数単位で指定できます。タスクは、その間隔を自動的に日付に変換します。</span><span class="sxs-lookup"><span data-stu-id="ddac3-117">You can indicate the date by number of days, weeks, months, or years from the current day, and the task automatically translates the interval to a date.</span></span>  
  
 <span data-ttu-id="ddac3-118">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="ddac3-118">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ddac3-119">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddac3-119">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="ddac3-120">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddac3-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ddac3-121">履歴クリーンアップ タスク (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="ddac3-121">History Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 <span data-ttu-id="ddac3-122">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddac3-122">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ddac3-123">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ddac3-123">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="ddac3-124">参照</span><span class="sxs-lookup"><span data-stu-id="ddac3-124">See Also</span></span>  
 <span data-ttu-id="ddac3-125">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="ddac3-125">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="ddac3-126">制御フロー</span><span class="sxs-lookup"><span data-stu-id="ddac3-126">Control Flow</span></span>](control-flow.md)  
  
  
