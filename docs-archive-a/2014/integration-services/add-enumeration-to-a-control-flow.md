---
title: 制御フローに列挙を追加する |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59b8569880fdf1a49f5f2ca1f6841841f9790af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640210"
---
# <a name="add-enumeration-to-a-control-flow"></a><span data-ttu-id="e2e58-102">制御フローに列挙を追加する</span><span class="sxs-lookup"><span data-stu-id="e2e58-102">Add Enumeration to a Control Flow</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e2e58-103">には、Foreach ループ コンテナーが含まれています。Foreach ループ コンテナーとは制御フローの要素で、これを使用すると、パッケージの制御フロー内のファイルおよびオブジェクトを列挙するループ構造を簡単に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e2e58-103">includes the Foreach Loop container, a control flow element that makes it simple to include a looping construct that enumerates files and objects in the control flow of a package.</span></span> <span data-ttu-id="e2e58-104">詳細については、「 [Foreach ループ コンテナー](control-flow/foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-104">For more information, see [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="e2e58-105">Foreach ループ コンテナーに機能は用意されていません。繰り返し可能な制御フローの構築、列挙子の型の指定、および列挙子の構成を行う構造を提供するだけです。</span><span class="sxs-lookup"><span data-stu-id="e2e58-105">The Foreach Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow, specify an enumerator type, and configure the enumerator.</span></span> <span data-ttu-id="e2e58-106">コンテナーに機能を設定するには、Foreach ループ コンテナーに少なくとも 1 つのタスクを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2e58-106">To provide container functionality, you must include at least one task in the Foreach Loop container.</span></span> <span data-ttu-id="e2e58-107">詳細については、「 [Integration Services のタスク](control-flow/integration-services-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-107">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="e2e58-108">Foreach ループ コンテナーには、複数のタスクを持つ制御フローおよび他のコンテナーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e2e58-108">The Foreach Loop container can include a control flow with multiple tasks and other containers.</span></span> <span data-ttu-id="e2e58-109">Foreach ループ コンテナーにタスクとコンテナーを追加する手順は、タスクとコンテナーをドラッグする先がパッケージではなく Foreach ループ コンテナーであること以外は、パッケージに追加する手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="e2e58-109">Adding tasks and containers to a Foreach Loop container is similar to adding them to a package, except you drag the tasks and containers to the Foreach Loop container instead of to the package.</span></span> <span data-ttu-id="e2e58-110">Foreach ループ コンテナーに複数のタスクまたはコンテナーが含まれる場合、パッケージで行う場合と同様に、優先順位制約を使用してそれらを連結できます。</span><span class="sxs-lookup"><span data-stu-id="e2e58-110">If the Foreach Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="e2e58-111">詳細については、「 [優先順位制約](control-flow/precedence-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-111">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a><span data-ttu-id="e2e58-112">Foreach ループ コンテナーを制御フローに実装するには</span><span class="sxs-lookup"><span data-stu-id="e2e58-112">To implement a Foreach Loop container in a control flow</span></span>  
  
1.  <span data-ttu-id="e2e58-113">Foreach ループ コンテナーをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="e2e58-113">Add the Foreach Loop container to the package.</span></span> <span data-ttu-id="e2e58-114">詳細については、「[制御フローでのタスクまたはコンテナーの追加または削除](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-114">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="e2e58-115">.</span><span class="sxs-lookup"><span data-stu-id="e2e58-115">.</span></span>  
  
2.  <span data-ttu-id="e2e58-116">タスクとコンテナーを Foreach ループ コンテナーに追加します。</span><span class="sxs-lookup"><span data-stu-id="e2e58-116">Add tasks and containers to the Foreach Loop container.</span></span> <span data-ttu-id="e2e58-117">詳細については、「[制御フローでのタスクまたはコンテナーの追加または削除](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-117">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="e2e58-118">.</span><span class="sxs-lookup"><span data-stu-id="e2e58-118">.</span></span>  
  
3.  <span data-ttu-id="e2e58-119">優先順位制約を使用して、Foreach ループ コンテナー内のタスクとコンテナーを連結します。</span><span class="sxs-lookup"><span data-stu-id="e2e58-119">Connect tasks and containers in the Foreach Loop container using precedence constraints.</span></span> <span data-ttu-id="e2e58-120">詳細については、「 [既定の優先順位制約を使用してタスクとコンテナーを連結する](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-120">For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).</span></span>  
  
4.  <span data-ttu-id="e2e58-121">Foreach ループ コンテナーを構成します。</span><span class="sxs-lookup"><span data-stu-id="e2e58-121">Configure the Foreach Loop container.</span></span> <span data-ttu-id="e2e58-122">詳細については、「 [Foreach ループ コンテナーを構成する](../../2014/integration-services/configure-a-foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e58-122">For more information, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e58-123">参照</span><span class="sxs-lookup"><span data-stu-id="e2e58-123">See Also</span></span>  
 <span data-ttu-id="e2e58-124">[制御フロー内のタスクまたはコンテナーを追加または削除する](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e2e58-124">[Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="e2e58-125">[コンポーネントのグループ化またはグループ解除](group-or-ungroup-components.md) </span><span class="sxs-lookup"><span data-stu-id="e2e58-125">[Group or Ungroup Components](group-or-ungroup-components.md) </span></span>  
 <span data-ttu-id="e2e58-126">[優先順位制約](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="e2e58-126">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="e2e58-127">[制御フローにイテレーションを追加する](add-iteration-to-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e2e58-127">[Add Iteration to a Control Flow](add-iteration-to-a-control-flow.md) </span></span>  
 [<span data-ttu-id="e2e58-128">制御フロー</span><span class="sxs-lookup"><span data-stu-id="e2e58-128">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
