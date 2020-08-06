---
title: データベースのバックアップ タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633962"
---
# <a name="back-up-database-task"></a><span data-ttu-id="377bd-102">データベースのバックアップ タスク</span><span class="sxs-lookup"><span data-stu-id="377bd-102">Back Up Database Task</span></span>
  <span data-ttu-id="377bd-103">データベースのバックアップ タスクは、さまざまな種類の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="377bd-103">The Back Up Database task performs different types of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database backups.</span></span> <span data-ttu-id="377bd-104">詳しくは、「[SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="377bd-104">For more information, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="377bd-105">データベースのバックアップ タスクを使用すると、パッケージは単一データベースまたは複数データベースをバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="377bd-105">By using the Back Up Database task, a package can back up a single database or multiple databases.</span></span> <span data-ttu-id="377bd-106">タスクにより単一データベースのみをバックアップする場合、バックアップ対象となるデータベース、ファイル、またはファイル グループなどのコンポーネントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="377bd-106">If the task backs up only a single database, you can choose the backup component: the database, or its files and filegroups.</span></span>  
  
## <a name="supported-recover-models-and-backup-types"></a><span data-ttu-id="377bd-107">サポートされている復旧モデルとバックアップの種類</span><span class="sxs-lookup"><span data-stu-id="377bd-107">Supported Recover Models and Backup Types</span></span>  
 <span data-ttu-id="377bd-108">次の表に、データベースのバックアップ タスクがサポートする復旧モデルとバックアップの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="377bd-108">The following table lists the recovery models and backup types that the Back Up Database task supports.</span></span>  
  
|<span data-ttu-id="377bd-109">復旧モデル</span><span class="sxs-lookup"><span data-stu-id="377bd-109">Recovery model</span></span>|<span data-ttu-id="377bd-110">データベース</span><span class="sxs-lookup"><span data-stu-id="377bd-110">Database</span></span>|<span data-ttu-id="377bd-111">データベースの差分</span><span class="sxs-lookup"><span data-stu-id="377bd-111">Database differential</span></span>|<span data-ttu-id="377bd-112">[トランザクション ログ]</span><span class="sxs-lookup"><span data-stu-id="377bd-112">Transaction log</span></span>|<span data-ttu-id="377bd-113">ファイルまたはファイルの差分</span><span class="sxs-lookup"><span data-stu-id="377bd-113">File or file differential</span></span>|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|<span data-ttu-id="377bd-114">シンプル</span><span class="sxs-lookup"><span data-stu-id="377bd-114">Simple</span></span>|<span data-ttu-id="377bd-115">必須</span><span class="sxs-lookup"><span data-stu-id="377bd-115">Required</span></span>|<span data-ttu-id="377bd-116">省略可能</span><span class="sxs-lookup"><span data-stu-id="377bd-116">Optional</span></span>|<span data-ttu-id="377bd-117">サポートされていません</span><span class="sxs-lookup"><span data-stu-id="377bd-117">Not supported</span></span>|<span data-ttu-id="377bd-118">サポートされていません</span><span class="sxs-lookup"><span data-stu-id="377bd-118">Not supported</span></span>|  
|<span data-ttu-id="377bd-119">[完全]</span><span class="sxs-lookup"><span data-stu-id="377bd-119">Full</span></span>|<span data-ttu-id="377bd-120">必須</span><span class="sxs-lookup"><span data-stu-id="377bd-120">Required</span></span>|<span data-ttu-id="377bd-121">省略可能</span><span class="sxs-lookup"><span data-stu-id="377bd-121">Optional</span></span>|<span data-ttu-id="377bd-122">必須</span><span class="sxs-lookup"><span data-stu-id="377bd-122">Required</span></span>|<span data-ttu-id="377bd-123">省略可能</span><span class="sxs-lookup"><span data-stu-id="377bd-123">Optional</span></span>|  
|<span data-ttu-id="377bd-124">一括ログ</span><span class="sxs-lookup"><span data-stu-id="377bd-124">Bulk-logged</span></span>|<span data-ttu-id="377bd-125">必須</span><span class="sxs-lookup"><span data-stu-id="377bd-125">Required</span></span>|<span data-ttu-id="377bd-126">省略可能</span><span class="sxs-lookup"><span data-stu-id="377bd-126">Optional</span></span>|<span data-ttu-id="377bd-127">必須</span><span class="sxs-lookup"><span data-stu-id="377bd-127">Required</span></span>|<span data-ttu-id="377bd-128">省略可能</span><span class="sxs-lookup"><span data-stu-id="377bd-128">Optional</span></span>|  
  
 <span data-ttu-id="377bd-129">データベースのバックアップ タスクは、Transact-SQL BACKUP ステートメントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="377bd-129">The Back Up Database task encapsulates a Transact-SQL BACKUP statement.</span></span> <span data-ttu-id="377bd-130">詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="377bd-130">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
## <a name="configuration-of-the-back-up-database-task"></a><span data-ttu-id="377bd-131">データベースのバックアップ タスクの構成</span><span class="sxs-lookup"><span data-stu-id="377bd-131">Configuration of the Back Up Database Task</span></span>  
 <span data-ttu-id="377bd-132">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="377bd-132">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="377bd-133">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="377bd-133">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="377bd-134">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="377bd-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="377bd-135">[[データベースのバックアップ タスク] &#40;メンテナンス プラン&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="377bd-135">[Back Up Database Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)</span></span>  
  
 <span data-ttu-id="377bd-136">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="377bd-136">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="377bd-137">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="377bd-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
