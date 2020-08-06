---
title: 複数の優先順位制約 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16fefbbf886818989131710876564fc9e147a56a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641059"
---
# <a name="multiple-precedence-constraints"></a><span data-ttu-id="e4041-102">複数の優先順位制約</span><span class="sxs-lookup"><span data-stu-id="e4041-102">Multiple Precedence Constraints</span></span>
  <span data-ttu-id="e4041-103">優先順位制約は、2 つのタスク、2 つのコンテナー、1 つのタスクと 1 つのコンテナーなど、2 つの実行可能ファイルを連結します。</span><span class="sxs-lookup"><span data-stu-id="e4041-103">A precedence constraint connects two executables: two tasks, two containers, or one of each.</span></span> <span data-ttu-id="e4041-104">これらは優先順位付き実行可能ファイル、および制約付き実行可能ファイルと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="e4041-104">They are known as the precedence executable and the constrained executable.</span></span> <span data-ttu-id="e4041-105">制約付き実行可能ファイルには、複数の優先順位制約を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e4041-105">A constrained executable can have multiple precedence constraints.</span></span> <span data-ttu-id="e4041-106">詳細については、「 [優先順位制約](control-flow/precedence-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4041-106">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="e4041-107">制約をグループ化して複雑な制約シナリオを組み立てると、複雑な制御フローをパッケージに実装できます。</span><span class="sxs-lookup"><span data-stu-id="e4041-107">Assembling complex constraint scenarios by grouping constraints enables you to implement complex control flow in packages.</span></span> <span data-ttu-id="e4041-108">たとえば、次の図で、タスク D は、`Success` 制約によってタスク A にリンクされ、`Failure` 制約によってタスク B にリンクされ、さらに `Success` 制約によってタスク C にリンクされています。</span><span class="sxs-lookup"><span data-stu-id="e4041-108">For example, in the following illustration, Task D is linked to Task A by a `Success` constraint, Task D is linked to Task B by a `Failure` constraint, and Task D is linked to Task C by a `Success` constraint.</span></span> <span data-ttu-id="e4041-109">タスク D とタスク A の間、タスク D とタスク B の間、およびタスク D とタスク C の間の優先順位制約は、論理 *AND* リレーションシップになります。</span><span class="sxs-lookup"><span data-stu-id="e4041-109">The precedence constraints between Task D and Task A, between Task D and Task B, and between Task D and Task C participate in a logical *and* relationship.</span></span> <span data-ttu-id="e4041-110">したがって、タスク D を実行するには、タスク A の実行が成功し、タスク B が失敗し、タスク C の実行が成功する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4041-110">Therefore, for Task D to run, Task A must run successfully, Task B must fail, and Task C must run successfully.</span></span>  
  
 <span data-ttu-id="e4041-111">![優先順位制約によってリンクされたタスク](media/precedenceconstraints.gif "優先順位制約によってリンクされたタスク")</span><span class="sxs-lookup"><span data-stu-id="e4041-111">![Tasks linked by precedence constraints](media/precedenceconstraints.gif "Tasks linked by precedence constraints")</span></span>  
  
## <a name="logicaland-property"></a><span data-ttu-id="e4041-112">LogicalAnd プロパティ</span><span class="sxs-lookup"><span data-stu-id="e4041-112">LogicalAnd Property</span></span>  
 <span data-ttu-id="e4041-113">タスクまたはコンテナーに複数の制約がある場合、`LogicalAnd` プロパティにより、優先順位制約を単独で評価するか、別の制約と組み合わせて評価するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4041-113">If a task or a container has multiple constraints, the `LogicalAnd` property specifies whether a precedence constraint is evaluated singly or in concert with other constraints.</span></span>  
  
 <span data-ttu-id="e4041-114">プロパティを設定するには、 `LogicalAnd` デザイナーの [**優先順位制約エディター** ] を使用するか、に用意されているプロパティウィンドウを使用し [!INCLUDE[ssIS](../includes/ssis-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e4041-114">You can set the `LogicalAnd` property using the **Precedence Constraint Editor** in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, or in the Properties window that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e4041-115">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e4041-115">Related Tasks</span></span>  
 [<span data-ttu-id="e4041-116">優先順位制約のプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="e4041-116">Set the Properties of a Precedence Constraint</span></span>](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
