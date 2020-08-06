---
title: オペレーターへの通知タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed5158a4ec5cfe8374fedbb2afbca1294b58f05e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741166"
---
# <a name="notify-operator-task"></a><span data-ttu-id="a4903-102">オペレーターへの通知タスク</span><span class="sxs-lookup"><span data-stu-id="a4903-102">Notify Operator Task</span></span>
  <span data-ttu-id="a4903-103">オペレーターへの通知タスクは、通知メッセージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント オペレーターに送信します。</span><span class="sxs-lookup"><span data-stu-id="a4903-103">The Notify Operator task sends notification messages to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span> <span data-ttu-id="a4903-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント オペレーターは、電子通知を受信できる人またはグループの別名です。</span><span class="sxs-lookup"><span data-stu-id="a4903-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator is an alias for a person or group that can receive electronic notifications.</span></span> <span data-ttu-id="a4903-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オペレーターの詳細については、「 [オペレーター](../../ssms/agent//operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4903-105">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operators, see [Operators](../../ssms/agent//operators.md).</span></span>  
  
 <span data-ttu-id="a4903-106">オペレーターへの通知タスクを使用すると、パッケージは電子メール、ポケットベル、または **Net Send**経由で、1 人以上のオペレーターに通知できます。</span><span class="sxs-lookup"><span data-stu-id="a4903-106">By using the Notify Operator task, a package can notify one or more operators via e-mail, pager, or **net send**.</span></span> <span data-ttu-id="a4903-107">通知方法は、オペレーターごとに変更できます。</span><span class="sxs-lookup"><span data-stu-id="a4903-107">Each operator can be notified by different methods.</span></span> <span data-ttu-id="a4903-108">たとえば、オペレーター A には電子メールとポケットベルで通知し、オペレーター B にはポケットベルと **Net Send**で通知します。</span><span class="sxs-lookup"><span data-stu-id="a4903-108">For example, OperatorA is notified by e-mail and pager, and OperatorB is notified by pager and **net send**.</span></span> <span data-ttu-id="a4903-109">オペレーターへの通知タスクから通知を受信するオペレーターは、このタスク上にある **OperatorNotify** コレクションのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4903-109">The operators who receive notifications from the task must be members of the **OperatorNotify** collection on the Notify Operator task.</span></span>  
  
 <span data-ttu-id="a4903-110">オペレーターへの通知タスクは、Transact-SQL ステートメントや DBCC コマンドをカプセル化しない、唯一のデータベース メンテナンス タスクです。</span><span class="sxs-lookup"><span data-stu-id="a4903-110">The Notify Operator task is the only database maintenance task that does not encapsulate a Transact-SQL statement or a DBCC command.</span></span>  
  
## <a name="configuration-of-the-notify-operator-task"></a><span data-ttu-id="a4903-111">オペレーターへの通知タスクの構成</span><span class="sxs-lookup"><span data-stu-id="a4903-111">Configuration of the Notify Operator Task</span></span>  
 <span data-ttu-id="a4903-112">プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="a4903-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="a4903-113">このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4903-113">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="a4903-114">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4903-114">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="a4903-115">[[オペレーターへの通知タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="a4903-115">[Notify Operator Task &#40;Maintenance Plan&#41;](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)</span></span>  
  
 <span data-ttu-id="a4903-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4903-116">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="a4903-117">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="a4903-117">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
