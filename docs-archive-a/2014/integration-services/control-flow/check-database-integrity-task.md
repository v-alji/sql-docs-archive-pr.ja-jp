---
title: データベースの整合性確認タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 99a2620a6f3f6a9a73c27fe6bb1abd34af73707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640201"
---
# <a name="check-database-integrity-task"></a><span data-ttu-id="8f364-102">データベースの整合性確認タスク</span><span class="sxs-lookup"><span data-stu-id="8f364-102">Check Database Integrity Task</span></span>
  <span data-ttu-id="8f364-103">データベースの整合性確認タスクは、指定されたデータベース内のすべてのオブジェクトの割り当てと構造上の整合性をチェックします。</span><span class="sxs-lookup"><span data-stu-id="8f364-103">The Check Database Integrity task checks the allocation and structural integrity of all the objects in the specified database.</span></span> <span data-ttu-id="8f364-104">このタスクは、単一のデータベースまたは複数のデータベースをチェックできます。また、データベースのインデックスもチェックするかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8f364-104">The task can check a single database or multiple databases, and you can choose whether to also check the database indexes.</span></span>  
  
 <span data-ttu-id="8f364-105">データベースの整合性確認タスクは、DBCC CHECKDB ステートメントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="8f364-105">The Check Database Integrity task encapsulates the DBCC CHECKDB statement.</span></span> <span data-ttu-id="8f364-106">詳細については、「[DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f364-106">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql).</span></span>  
  
## <a name="configuration-of-the-check-database-integrity-task"></a><span data-ttu-id="8f364-107">データベースの整合性確認タスクの構成</span><span class="sxs-lookup"><span data-stu-id="8f364-107">Configuration of the Check Database Integrity Task</span></span>  
 <span data-ttu-id="8f364-108">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="8f364-108">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="8f364-109">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f364-109">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="8f364-110">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f364-110">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="8f364-111">[[データベースの整合性確認タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="8f364-111">[Check Database Integrity Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)</span></span>  
  
 <span data-ttu-id="8f364-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f364-112">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="8f364-113">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="8f364-113">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
