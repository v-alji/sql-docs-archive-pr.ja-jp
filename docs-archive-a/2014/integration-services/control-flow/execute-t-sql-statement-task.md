---
title: T-SQL ステートメントの実行タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7ebc73ad843ac7fcf1dfbe7699ecd8ea53edcdad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713385"
---
# <a name="execute-t-sql-statement-task"></a><span data-ttu-id="78e82-102">T-SQL ステートメントの実行タスク</span><span class="sxs-lookup"><span data-stu-id="78e82-102">Execute T-SQL Statement Task</span></span>
  <span data-ttu-id="78e82-103">T-SQL ステートメントの実行タスクは、Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="78e82-103">The Execute T-SQL Statement task runs Transact-SQL statements.</span></span> <span data-ttu-id="78e82-104">詳細については、「[Transact-SQL リファレンス (データベース エンジン)](/sql/t-sql/language-reference)」および「[Integration Services (SSIS) のクエリ](../integration-services-ssis-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78e82-104">For more information, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference) and [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="78e82-105">このタスクは、SQL 実行タスクと同様です。</span><span class="sxs-lookup"><span data-stu-id="78e82-105">This task is similar to the Execute SQL task.</span></span> <span data-ttu-id="78e82-106">ただし、T-SQL ステートメントの実行タスクでは、SQL 言語の Transact-SQL バージョンのみがサポートされるため、このタスクを使用して、SQL 言語の他の仕様の言語によるステートメントをサーバーで実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="78e82-106">However, the Execute T-SQL Statement task supports only the Transact-SQL version of the SQL language and you cannot use this task to run statements on servers that use other dialects of the SQL language.</span></span> <span data-ttu-id="78e82-107">パラメーター化クエリの実行、クエリ結果の変数への保存、またはプロパティ式の使用が必要な場合は、T-SQL ステートメントの実行タスクではなく、SQL 実行タスクを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78e82-107">If you need to run parameterized queries, save the query results to variables, or use property expressions, you should use the Execute SQL task instead of the Execute T-SQL Statement task.</span></span> <span data-ttu-id="78e82-108">詳細については、「 [SQL 実行タスク](execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78e82-108">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="configuration-of-the-execute-t-sql-task"></a><span data-ttu-id="78e82-109">T-SQL 実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="78e82-109">Configuration of the Execute T-SQL Task</span></span>  
 <span data-ttu-id="78e82-110">プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="78e82-110">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="78e82-111">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="78e82-111">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="78e82-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78e82-112">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="78e82-113">[[T-SQL ステートメントの実行タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="78e82-113">[Execute T-SQL Statement Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)</span></span>  
  
 <span data-ttu-id="78e82-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78e82-114">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="78e82-115">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="78e82-115">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="78e82-116">参照</span><span class="sxs-lookup"><span data-stu-id="78e82-116">See Also</span></span>  
 <span data-ttu-id="78e82-117">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="78e82-117">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="78e82-118">[制御フロー](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="78e82-118">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="78e82-119">Integration Services パッケージで MERGE を実行する</span><span class="sxs-lookup"><span data-stu-id="78e82-119">MERGE in Integration Services Packages</span></span>](merge-in-integration-services-packages.md)  
  
  
