---
title: For ループエディター |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainer.f1
ms.assetid: c4db9df6-d2f4-44da-9f4d-628893e86956
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b610805808e0f392e675ad79f16d2d39886c7f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632594"
---
# <a name="for-loop-editor"></a><span data-ttu-id="c73b9-102">[For ループ エディター]</span><span class="sxs-lookup"><span data-stu-id="c73b9-102">For Loop Editor</span></span>
  <span data-ttu-id="c73b9-103">**[For ループ エディター]** ダイアログ ボックスの **[For ループ]** ページを使用すると、指定した条件が false と評価されるまでワークフローを繰り返すループを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c73b9-103">Use the **For Loop** page of the **For Loop Editor** dialog box to configure a loop that repeats a workflow until a specified condition evaluates to false.</span></span>  
  
 <span data-ttu-id="c73b9-104">For ループ コンテナーの概要とパッケージ内で For ループ コンテナーを使用する方法の詳細については、「 [For Loop Container](control-flow/for-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c73b9-104">To learn about the For Loop container and how to use it in packages, see [For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c73b9-105">Options</span><span class="sxs-lookup"><span data-stu-id="c73b9-105">Options</span></span>  
 <span data-ttu-id="c73b9-106">**[InitExpression]**</span><span class="sxs-lookup"><span data-stu-id="c73b9-106">**InitExpression**</span></span>  
 <span data-ttu-id="c73b9-107">必要に応じて、ループが使用する値を初期化する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c73b9-107">Optionally, provide an expression that initializes values used by the loop.</span></span>  
  
 <span data-ttu-id="c73b9-108">**[EvalExpression]**</span><span class="sxs-lookup"><span data-stu-id="c73b9-108">**EvalExpression**</span></span>  
 <span data-ttu-id="c73b9-109">ループが停止するか続行するかを評価する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c73b9-109">Provide an expression to evaluate whether the loop should stop or continue.</span></span>  
  
 <span data-ttu-id="c73b9-110">**[AssignExpression]**</span><span class="sxs-lookup"><span data-stu-id="c73b9-110">**AssignExpression**</span></span>  
 <span data-ttu-id="c73b9-111">必要に応じて、ループの繰り返しごとに条件を変更する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c73b9-111">Optionally, provide an expression that changes a condition each time that the loop repeats.</span></span>  
  
 <span data-ttu-id="c73b9-112">**名前**</span><span class="sxs-lookup"><span data-stu-id="c73b9-112">**Name**</span></span>  
 <span data-ttu-id="c73b9-113">For ループ コンテナーに一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c73b9-113">Provide a unique name for the For Loop container.</span></span> <span data-ttu-id="c73b9-114">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c73b9-114">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c73b9-115">オブジェクト名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73b9-115">Object names must be unique within a package.</span></span>  
  
 <span data-ttu-id="c73b9-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="c73b9-116">**Description**</span></span>  
 <span data-ttu-id="c73b9-117">For ループ コンテナーの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="c73b9-117">Provide a description of the For Loop container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73b9-118">参照</span><span class="sxs-lookup"><span data-stu-id="c73b9-118">See Also</span></span>  
 <span data-ttu-id="c73b9-119">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c73b9-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c73b9-120">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="c73b9-120">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="c73b9-121">[Foreach ループコンテナー](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="c73b9-121">[Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="c73b9-122">For ループ コンテナーを構成する</span><span class="sxs-lookup"><span data-stu-id="c73b9-122">Configure a For Loop Container</span></span>](../../2014/integration-services/configure-a-for-loop-container.md)  
  
  
