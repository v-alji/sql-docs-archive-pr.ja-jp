---
title: タスク ホスト コンテナー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4429d564cea0f08d5c2408199a8f1837b38389b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644085"
---
# <a name="task-host-container"></a><span data-ttu-id="dcf8d-102">タスク ホスト コンテナー</span><span class="sxs-lookup"><span data-stu-id="dcf8d-102">Task Host Container</span></span>
  <span data-ttu-id="dcf8d-103">タスク ホスト コンテナーは、1 つのタスクをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-103">The task host container encapsulates a single task.</span></span> <span data-ttu-id="dcf8d-104">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは、タスク ホストは個別には構成されず、カプセル化するタスクのプロパティを設定する際に構成されます。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-104">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the task host is not configured separately; instead, it is configured when you set the properties of the task it encapsulates.</span></span> <span data-ttu-id="dcf8d-105">タスク ホスト コンテナーがカプセル化するタスクの詳細については、「 [Integration Services タスク](integration-services-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-105">For more information about the tasks that the task host containers encapsulate, see [Integration Services Tasks](integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="dcf8d-106">タスク ホスト コンテナーは、変数とイベント ハンドラーの使用を、タスク レベルに拡張します。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-106">This container extends the use of variables and event handlers to the task level.</span></span> <span data-ttu-id="dcf8d-107">詳細については、「[Integration Services (SSIS) のイベント ハンドラー](../integration-services-ssis-event-handlers.md)」および「[Integration Services (SSIS) の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-107">For more information, see [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="configuration-of-the-task-host"></a><span data-ttu-id="dcf8d-108">タスク ホストの構成</span><span class="sxs-lookup"><span data-stu-id="dcf8d-108">Configuration of the Task Host</span></span>  
 <span data-ttu-id="dcf8d-109">プロパティを設定するには、 **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ウィンドウで行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-109">You can set properties in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="dcf8d-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でのこれらのプロパティの設定については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-110">For information about setting these properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="dcf8d-111">プログラムによってこれらのプロパティを設定する方法については、 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcf8d-111">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="dcf8d-112">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="dcf8d-112">Related Tasks</span></span>  
  
-   [<span data-ttu-id="dcf8d-113">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="dcf8d-113">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="dcf8d-114">参照</span><span class="sxs-lookup"><span data-stu-id="dcf8d-114">See Also</span></span>  
 [<span data-ttu-id="dcf8d-115">Integration Services コンテナー</span><span class="sxs-lookup"><span data-stu-id="dcf8d-115">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
