---
title: 優先順位制約エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6853d1974f4276361d60e1d73b34c72a366a7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633883"
---
# <a name="precedence-constraint-editor"></a><span data-ttu-id="19534-102">優先順位制約エディター</span><span class="sxs-lookup"><span data-stu-id="19534-102">Precedence Constraint Editor</span></span>
  <span data-ttu-id="19534-103">**[優先順位制約エディター]** ダイアログ ボックスを使用すると、優先順位制約を構成できます。</span><span class="sxs-lookup"><span data-stu-id="19534-103">Use the **Precedence Constraint Editor** dialog box to configure precedence constraints.</span></span>  
  
## <a name="options"></a><span data-ttu-id="19534-104">Options</span><span class="sxs-lookup"><span data-stu-id="19534-104">Options</span></span>  
 <span data-ttu-id="19534-105">**[評価操作]**</span><span class="sxs-lookup"><span data-stu-id="19534-105">**Evaluation operation**</span></span>  
 <span data-ttu-id="19534-106">優先順位制約で使用する評価操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="19534-106">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="19534-107">操作は次のとおりです: **[制約]** 、 **[式]** 、 **[式と制約]** 、 **[式または制約]** 。</span><span class="sxs-lookup"><span data-stu-id="19534-107">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
 <span data-ttu-id="19534-108">**Value**</span><span class="sxs-lookup"><span data-stu-id="19534-108">**Value**</span></span>  
 <span data-ttu-id="19534-109">制約値として次の値を指定します: **[成功]** 、 **[失敗]** 、 **[完了]** 。</span><span class="sxs-lookup"><span data-stu-id="19534-109">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19534-110"> 優先順位制約を表す線は、 **[成功]** の場合は緑色、 **[失敗]** の場合は強調表示、 **[完了]** の場合は青色です。</span><span class="sxs-lookup"><span data-stu-id="19534-110">The precedence constraint line is green for **Success**, highlighted for **Failure**, and blue for **Completion**.</span></span>  
  
 <span data-ttu-id="19534-111">**[式]**</span><span class="sxs-lookup"><span data-stu-id="19534-111">**Expression**</span></span>  
 <span data-ttu-id="19534-112">操作として **[式]**、 **[式と制約]**、または **[式または制約]** を使用する場合は、式を入力するか、式ビルダーを起動して式を作成します。</span><span class="sxs-lookup"><span data-stu-id="19534-112">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression or launch the Expression Builder to create the expression.</span></span> <span data-ttu-id="19534-113">式はブール値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="19534-113">The expression must evaluate to a Boolean.</span></span>  
  
 <span data-ttu-id="19534-114">**テスト**</span><span class="sxs-lookup"><span data-stu-id="19534-114">**Test**</span></span>  
 <span data-ttu-id="19534-115">式を検証します。</span><span class="sxs-lookup"><span data-stu-id="19534-115">Validate the expression.</span></span>  
  
 <span data-ttu-id="19534-116">**論理積**</span><span class="sxs-lookup"><span data-stu-id="19534-116">**Logical AND**</span></span>  
 <span data-ttu-id="19534-117">同一の実行可能ファイルに対して、複数の優先順位制約を同時に評価することを指定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="19534-117">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="19534-118">すべての制約が `True` に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="19534-118">All constraints must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19534-119">この種類の優先順位制約は、緑色、強調表示、または青色の実線で示されます。</span><span class="sxs-lookup"><span data-stu-id="19534-119">This type of precedence constraint appears as a solid green, highlighted or blue line.</span></span>  
  
 <span data-ttu-id="19534-120">**論理和**</span><span class="sxs-lookup"><span data-stu-id="19534-120">**Logical OR**</span></span>  
 <span data-ttu-id="19534-121">同一の実行可能ファイルに対して、複数の優先順位制約を同時に評価することを指定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="19534-121">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="19534-122">少なくとも 1 つの制約が `True` に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="19534-122">At least one constraint must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19534-123">この種類の優先順位制約は、緑色、強調表示、または青色の点線で示されます。</span><span class="sxs-lookup"><span data-stu-id="19534-123">This type of precedence constraint appears as a dotted green, highlighted, or blue line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19534-124">参照</span><span class="sxs-lookup"><span data-stu-id="19534-124">See Also</span></span>  
 <span data-ttu-id="19534-125">[優先順位制約](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="19534-125">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="19534-126">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="19534-126">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="19534-127">[Integration Services コンテナー](control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="19534-127">[Integration Services Containers](control-flow/integration-services-containers.md) </span></span>  
 [<span data-ttu-id="19534-128">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="19534-128">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
