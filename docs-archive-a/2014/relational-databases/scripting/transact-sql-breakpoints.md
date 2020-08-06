---
title: Transact-SQL ブレークポイント
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: rothja
ms.author: jroth
ms.openlocfilehash: c9595c9627ac3cc445b1193881c2d5b772e9b71d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643759"
---
# <a name="transact-sql-breakpoints"></a><span data-ttu-id="ced4e-102">Transact-SQL ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="ced4e-102">Transact-SQL Breakpoints</span></span>
  <span data-ttu-id="ced4e-103">ブレークポイントは、特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの実行の一時停止を指定し、その時点のコード要素の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ced4e-103">Breakpoints specify that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="ced4e-104">ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="ced4e-104">Breakpoints</span></span>  
 <span data-ttu-id="ced4e-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの実行時に、特定のステートメントでブレークポイントを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="ced4e-105">When running the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can toggle a breakpoint on specific statements.</span></span> <span data-ttu-id="ced4e-106">ブレークポイントが含まれているステートメントに到達すると、デバッガーの実行は一時停止され、変数やパラメーターに存在する値などの情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ced4e-106">When execution reaches a statement with a breakpoint, the debugger pauses execution so you can view debugging information, such as the values present in variables and parameters.</span></span>  
  
 <span data-ttu-id="ced4e-107">ブレークポイントの管理は、個別にエディター ウィンドウで、またはまとめて **[ブレークポイント]** ウィンドウで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ced4e-107">You can manage breakpoints individually in the editor window, or collectively by using the **Breakpoints** window.</span></span> <span data-ttu-id="ced4e-108">ブレークポイントを編集することにより、実行を一時停止する条件や、ブレークポイント実行時の動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ced4e-108">You can edit breakpoints to specify items such as specific conditions under which execution should pause, or the actions to be taken if the breakpoint is executed.</span></span>  
  
## <a name="breakpoint-tasks"></a><span data-ttu-id="ced4e-109">ブレークポイントのタスク</span><span class="sxs-lookup"><span data-stu-id="ced4e-109">Breakpoint Tasks</span></span>  
  
|<span data-ttu-id="ced4e-110">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="ced4e-110">Task Description</span></span>|<span data-ttu-id="ced4e-111">トピック</span><span class="sxs-lookup"><span data-stu-id="ced4e-111">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ced4e-112">デバッガーを一時停止する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-112">Describes how to specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement on which you want the debugger to pause.</span></span>|[<span data-ttu-id="ced4e-113">ブレークポイントの切り替え</span><span class="sxs-lookup"><span data-stu-id="ced4e-113">Toggle a Breakpoint</span></span>](../spatial/point.md)|  
|<span data-ttu-id="ced4e-114">ブレークポイントを一時的に非アクティブ化し、後で再アクティブ化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-114">Describes how to temporarily deactivate a breakpoint, and later reactivate it.</span></span> <span data-ttu-id="ced4e-115">ブレークポイントを削除する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-115">Also describes how to delete a breakpoint.</span></span>|[<span data-ttu-id="ced4e-116">ブレークポイントの有効化、無効化、削除</span><span class="sxs-lookup"><span data-stu-id="ced4e-116">Enable, Disable, and Delete Breakpoints</span></span>](enable-disable-and-delete-breakpoints.md)|  
|<span data-ttu-id="ced4e-117">指定した Transact-SQL 式の評価に基づいてブレークポイントがブレークするかどうかを決定する条件を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-117">Describes how to specify a condition, which defines whether breakpoint breaks based on the evaluation of a specified Transact-SQL expression.</span></span>|[<span data-ttu-id="ced4e-118">ブレークポイント条件の指定</span><span class="sxs-lookup"><span data-stu-id="ced4e-118">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)|  
|<span data-ttu-id="ced4e-119">ブレークポイントを含むステートメントが指定の回数実行されたときにのみ、ブレークポイントがブレークするように、ヒット カウントを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-119">Describes how to specify a hit count, which causes a breakpoint to break only when the statement containing the breakpoint has been executed a specified number of times.</span></span>|[<span data-ttu-id="ced4e-120">ヒット カウントの指定</span><span class="sxs-lookup"><span data-stu-id="ced4e-120">Specify a Hit Count</span></span>](specify-a-hit-count.md)|  
|<span data-ttu-id="ced4e-121">指定されたプロセスまたはスレッドでのみブレークポイントがブレークするように、フィルターを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-121">Describes how to specify a filter, which causes a breakpoint to break for only specified processes or threads.</span></span>|[<span data-ttu-id="ced4e-122">ブレークポイント フィルターの指定</span><span class="sxs-lookup"><span data-stu-id="ced4e-122">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)|  
|<span data-ttu-id="ced4e-123">ブレークポイント ステートメントが実行されるときに行われるカスタム操作である、 **ヒット時** アクションを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-123">Describes how to specify a **When Hit** action, which is a custom operation that is performed when the breakpoint statement is executed.</span></span> <span data-ttu-id="ced4e-124">例としては、メッセージの出力などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="ced4e-124">An example would be to print a message.</span></span>|[<span data-ttu-id="ced4e-125">ブレークポイント アクションの指定</span><span class="sxs-lookup"><span data-stu-id="ced4e-125">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)|  
|<span data-ttu-id="ced4e-126">ブレークポイントの場所を編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ced4e-126">Describes how to edit the location of a breakpoint.</span></span>|[<span data-ttu-id="ced4e-127">ブレークポイントの位置の編集</span><span class="sxs-lookup"><span data-stu-id="ced4e-127">Edit a Breakpoint Location</span></span>](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ced4e-128">参照</span><span class="sxs-lookup"><span data-stu-id="ced4e-128">See Also</span></span>  
 [<span data-ttu-id="ced4e-129">Transact-SQL デバッガー情報</span><span class="sxs-lookup"><span data-stu-id="ced4e-129">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
