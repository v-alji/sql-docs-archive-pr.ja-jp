---
title: メンテナンス クリーンアップ タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.maintenancecleanuptask.f1
helpviewer_keywords:
- deleting files
- removing files
- Maintenance Cleanup task
ms.assetid: 73ad3cd6-9a6d-44cf-905f-c56aa658bf42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4d39dd775402adadbe51eaadc530f4feb288ab9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639580"
---
# <a name="maintenance-cleanup-task"></a><span data-ttu-id="39705-102">メンテナンス クリーンアップ タスク</span><span class="sxs-lookup"><span data-stu-id="39705-102">Maintenance Cleanup Task</span></span>
  <span data-ttu-id="39705-103">メンテナンス クリーンアップ タスクでは、データベース バックアップ ファイルや、メンテナンス プランによって作成されたレポートなど、メンテナンス プランに関連するファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="39705-103">The Maintenance Cleanup task removes files related to maintenance plans, including database backup files and reports created by maintenance plans.</span></span> <span data-ttu-id="39705-104">詳細については、「 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md) 」および「 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39705-104">For more information, see [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md) and [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="39705-105">パッケージは、メンテナンス クリーンアップ タスクを使用して、指定したサーバー上のバックアップ ファイルやメンテナンス プランのレポートを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="39705-105">By using the Maintenance Cleanup task, a package can remove the backup files or maintenance plan reports on the specified server.</span></span> <span data-ttu-id="39705-106">メンテナンス クリーンアップ タスクには、特定のファイルを削除したり、1 つのフォルダー内のファイルのグループを削除するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="39705-106">The Maintenance Cleanup task includes an option to remove a specific file or remove a group of files in a folder.</span></span> <span data-ttu-id="39705-107">必要に応じて、削除するファイルの拡張子を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="39705-107">Optionally you can specify the extension of the files to delete.</span></span>  
  
 <span data-ttu-id="39705-108">メンテナンス クリーンアップ タスクを構成してバックアップ ファイルを削除する場合、既定のファイル名の拡張子は BAK です。</span><span class="sxs-lookup"><span data-stu-id="39705-108">When you configure the Maintenance Cleanup task to remove backup files, the default file name extension is BAK.</span></span> <span data-ttu-id="39705-109">レポート ファイルの場合、既定のファイル名の拡張子は TXT です。</span><span class="sxs-lookup"><span data-stu-id="39705-109">For report files, the default file name extension is TXT.</span></span> <span data-ttu-id="39705-110">必要に応じて拡張子を更新できます。この場合、唯一の制限事項として、拡張子を 256 文字未満にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39705-110">You can update the extensions to suit your needs; the only limitation is that extensions must be less than 256 characters long.</span></span>  
  
 <span data-ttu-id="39705-111">不要になった古いファイルは削除するのが普通です。メンテナンス クリーンアップ タスクは、指定した期限に達したファイルを削除するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="39705-111">Typically, you want to remove old files that are no longer needed, and the Maintenance Cleanup task can be configured to delete files that have reached a specified age.</span></span> <span data-ttu-id="39705-112">たとえば、4 週間を経過したファイルを削除するようにタスクを構成できます。</span><span class="sxs-lookup"><span data-stu-id="39705-112">For example, the task can be configured to delete files that are older than four weeks.</span></span> <span data-ttu-id="39705-113">削除するファイルの期限は、日、週、月、または年を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="39705-113">You can specify the age of files to delete by using days, weeks, months, or years.</span></span> <span data-ttu-id="39705-114">削除するファイルの最小経過期間を指定しないと、指定した種類のファイルがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="39705-114">If you do not specify the minimum age of files to delete, all files of the specified type are deleted.</span></span>  
  
 <span data-ttu-id="39705-115">以前のバージョンのメンテナンス クリーンアップ タスクとは対照的に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンのタスクでは、指定したディレクトリのサブディレクトリにあるファイルは自動的には削除されません。</span><span class="sxs-lookup"><span data-stu-id="39705-115">In contrast to earlier versions of the Maintenance Cleanup task, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version of the task does not automatically delete files in the subdirectories of the specified directory.</span></span> <span data-ttu-id="39705-116">この制約により、メンテナンス クリーンアップ タスクの機能を悪用して故意にファイルを削除するような外部からの攻撃を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="39705-116">This constraint reduces the surface area of any attack that could exploit the functionality of the Maintenance Cleanup task to delete files maliciously.</span></span> <span data-ttu-id="39705-117">直下のサブフォルダーを削除するには、 **[メンテナンス クリーンアップ タスク]** ダイアログ ボックスの **[直下のサブフォルダーを含める]** オプションをオンにして、明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39705-117">To delete the first-level subfolders, you must explicitly elect to do this by checking the **Include first-level subfolders** option in the **Maintenance Cleanup Task** dialog box.</span></span>  
  
## <a name="configuration-of-the-maintenance-cleanup-task"></a><span data-ttu-id="39705-118">メンテナンス クリーンアップ タスクの構成</span><span class="sxs-lookup"><span data-stu-id="39705-118">Configuration of the Maintenance Cleanup Task</span></span>  
 <span data-ttu-id="39705-119">プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="39705-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="39705-120">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="39705-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="39705-121">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39705-121">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="39705-122">[[メンテナンス クリーンアップ タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="39705-122">[Maintenance Cleanup Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="39705-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="39705-123">Related Tasks</span></span>  
 <span data-ttu-id="39705-124">これらのプロパティを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39705-124">For details about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39705-125">参照</span><span class="sxs-lookup"><span data-stu-id="39705-125">See Also</span></span>  
 <span data-ttu-id="39705-126">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="39705-126">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="39705-127">制御フロー</span><span class="sxs-lookup"><span data-stu-id="39705-127">Control Flow</span></span>](control-flow.md)  
  
  
