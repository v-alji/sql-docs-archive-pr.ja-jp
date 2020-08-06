---
title: シーケンス コンテナー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b972f923e2134363ba1b378beebebbeb1e5d6bb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642214"
---
# <a name="sequence-container"></a><span data-ttu-id="c4471-102">シーケンス コンテナー</span><span class="sxs-lookup"><span data-stu-id="c4471-102">Sequence Container</span></span>
  <span data-ttu-id="c4471-103">シーケンス コンテナーは、パッケージ制御フローのサブセットである制御フローを定義します。</span><span class="sxs-lookup"><span data-stu-id="c4471-103">The Sequence container defines a control flow that is a subset of the package control flow.</span></span> <span data-ttu-id="c4471-104">シーケンス コンテナーは、パッケージを複数の個別の制御フローにグループ化します。各制御フローには、パッケージ制御フロー全体の中で実行される、1 つ以上のタスクおよびコンテナーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c4471-104">Sequence containers group the package into multiple separate control flows, each containing one or more tasks and containers that run within the overall package control flow.</span></span>  
  
 <span data-ttu-id="c4471-105">シーケンス コンテナーには、他のコンテナーの他に、複数のタスクを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c4471-105">The Sequence container can include multiple tasks in addition to other containers.</span></span> <span data-ttu-id="c4471-106">シーケンス コンテナーにタスクとコンテナーを追加する手順は、タスクとコンテナーをドラッグする先がパッケージ コンテナーではなくシーケンス コンテナーであること以外は、パッケージに追加する手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="c4471-106">Adding tasks and containers to a Sequence container is similar to adding them to a package, except you drag the tasks and containers to the Sequence container instead of to the package container.</span></span> <span data-ttu-id="c4471-107">シーケンス コンテナーに複数のタスクまたはコンテナーが含まれる場合、パッケージの場合と同様に、優先順位制約を使用してそれらを連結できます。</span><span class="sxs-lookup"><span data-stu-id="c4471-107">If the Sequence container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="c4471-108">詳細については、「 [優先順位制約](precedence-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4471-108">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="c4471-109">シーケンス コンテナーを使用すると、次のような多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="c4471-109">There are many benefits of using a Sequence container:</span></span>  
  
-   <span data-ttu-id="c4471-110">タスクのグループを無効にして、パッケージ制御フローの 1 つのサブセットに集中してパッケージをデバッグできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c4471-110">Disabling groups of tasks to focus package debugging on one subset of the package control flow.</span></span>  
  
-   <span data-ttu-id="c4471-111">個別のタスクではなくシーケンス コンテナー上でプロパティを設定することにより、複数タスクのプロパティを 1 か所で管理します。</span><span class="sxs-lookup"><span data-stu-id="c4471-111">Managing properties on multiple tasks in one location by setting properties on a Sequence container instead of on the individual tasks.</span></span>  
  
     <span data-ttu-id="c4471-112">たとえば、シーケンス コンテナーの `Disable` プロパティを `True` に設定すると、シーケンス コンテナーのすべてのタスクとコンテナーを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="c4471-112">For example, you can set the `Disable` property of the Sequence container to `True` to disable all the tasks and containers in the Sequence container.</span></span>  
  
-   <span data-ttu-id="c4471-113">関連タスクおよびコンテナーのグループが使用する、変数の範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4471-113">Providing scope for variables that a group of related tasks and containers use.</span></span>  
  
-   <span data-ttu-id="c4471-114">多数のタスクをグループ化すると、シーケンス コンテナーの折りたたみおよび展開によってタスクを簡単に管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c4471-114">Grouping many tasks so you can more easily managed them by collapsing and expanding the Sequence container.</span></span>  
  
     <span data-ttu-id="c4471-115">また、タスク グループを作成すると、 **[グループ]** ボックスで展開および折りたたみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c4471-115">You can also create task groups, which expand and collapse using the **Group** box.</span></span> <span data-ttu-id="c4471-116">ただし、 **[グループ]** ボックスはデザイン時の機能であり、プロパティがなく、実行時には動作しません。</span><span class="sxs-lookup"><span data-stu-id="c4471-116">However, the **Group** box is a design-time feature that has no properties or run-time behavior.</span></span> <span data-ttu-id="c4471-117">詳細については、「 [コンポーネントのグループ化とグループの解除](../group-or-ungroup-components.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4471-117">For more information, see [Group or Ungroup Components](../group-or-ungroup-components.md)</span></span>  
  
-   <span data-ttu-id="c4471-118">シーケンス コンテナー上でトランザクションの属性を設定し、パッケージ制御フローのサブセットのトランザクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="c4471-118">Set a transaction attribute on the Sequence container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="c4471-119">この方法により、より細かなレベルでトランザクションを管理できます。</span><span class="sxs-lookup"><span data-stu-id="c4471-119">In this way, you can manage transactions at a more granular level.</span></span>  
  
     <span data-ttu-id="c4471-120">たとえば、シーケンス コンテナーに 2 つの関連タスクが含まれ、1 つはテーブル内のデータを削除するタスクで、もう 1 つはテーブルにデータを挿入するタスクの場合、挿入アクションが失敗した場合に削除アクションをロールバックするようにトランザクションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c4471-120">For example, if a Sequence container includes two related tasks, one task that deletes data in a table and another task that inserts data into a table, you can configure a transaction to ensure that the delete action is rolled back if the insert action fails.</span></span> <span data-ttu-id="c4471-121">詳細については、「 [Integration Services のトランザクション](../integration-services-transactions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4471-121">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-sequence-container"></a><span data-ttu-id="c4471-122">シーケンス コンテナーの構成</span><span class="sxs-lookup"><span data-stu-id="c4471-122">Configuration of the Sequence Container</span></span>  
 <span data-ttu-id="c4471-123">シーケンス コンテナーにはカスタム ユーザー インターフェイスはなく、 **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ウィンドウ、またはプログラムによってのみ構成できます。</span><span class="sxs-lookup"><span data-stu-id="c4471-123">The Sequence container has no custom user interface and you can configure it only in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="c4471-124">プログラムによってこれらのプロパティを設定する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.Sequence** クラスのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4471-124">For information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.Sequence** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c4471-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c4471-125">Related Tasks</span></span>  
 <span data-ttu-id="c4471-126">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でコンポーネントのプロパティを設定する方法については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4471-126">For information about how to set properties of the component in the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4471-127">参照</span><span class="sxs-lookup"><span data-stu-id="c4471-127">See Also</span></span>  
 <span data-ttu-id="c4471-128">[制御フローのタスクまたはコンテナーを追加または削除する](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="c4471-128">[Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="c4471-129">[既定の優先順位制約を使用してタスクとコンテナーを連結する](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="c4471-129">[Connect Tasks and Containers by Using a Default Precedence Constraint](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="c4471-130">Integration Services コンテナー</span><span class="sxs-lookup"><span data-stu-id="c4471-130">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
