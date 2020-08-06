---
title: 可変グリッドのオプション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variableoptionswindow.f1
helpviewer_keywords:
- Choose Variable Columns dialog box
ms.assetid: 7cccc230-3b20-4074-804f-3448d9616a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b90e1a3c69e4eaf1f123603e0082ecb1eda4e893
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633195"
---
# <a name="variable-grid-options"></a><span data-ttu-id="919ff-102">可変グリッドのオプション</span><span class="sxs-lookup"><span data-stu-id="919ff-102">Variable Grid Options</span></span>
  <span data-ttu-id="919ff-103">**[可変グリッドのオプション]** ダイアログ ボックスを使用して、 **[変数]** ウィンドウに表示される列を選択したり、変数の一覧に適用するフィルターを選択したりします。</span><span class="sxs-lookup"><span data-stu-id="919ff-103">Use the **Variable Grid Options** dialog box to select the columns that will display in the **Variables** window and to select the filters to apply to the list of variables.</span></span> <span data-ttu-id="919ff-104">対応する変数のプロパティの詳細については、「 [Integration Services (SSIS) の変数](integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="919ff-104">For more information about the corresponding variable properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-filter"></a><span data-ttu-id="919ff-105">フィルターのオプション</span><span class="sxs-lookup"><span data-stu-id="919ff-105">Options for Filter</span></span>  
 <span data-ttu-id="919ff-106">**システム変数を表示する**</span><span class="sxs-lookup"><span data-stu-id="919ff-106">**Show system variables**</span></span>  
 <span data-ttu-id="919ff-107">選択すると、 **[変数]** ウィンドウにシステム変数が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="919ff-107">Select to list system variables in the **Variables** window.</span></span> <span data-ttu-id="919ff-108">システム変数は定義済みです。</span><span class="sxs-lookup"><span data-stu-id="919ff-108">System variables are predefined.</span></span> <span data-ttu-id="919ff-109">システム変数は追加も削除もできません。</span><span class="sxs-lookup"><span data-stu-id="919ff-109">You cannot add or delete system variables.</span></span> <span data-ttu-id="919ff-110">**RaiseChangedEvent** プロパティ設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="919ff-110">You can modify the **RaiseChangedEvent** property setting.</span></span>  
  
 <span data-ttu-id="919ff-111">この一覧は色分け表示されています。</span><span class="sxs-lookup"><span data-stu-id="919ff-111">This list is color coded.</span></span> <span data-ttu-id="919ff-112">システム変数は灰色で、ユーザー定義変数は黒です。</span><span class="sxs-lookup"><span data-stu-id="919ff-112">System variables are gray, and user-defined variables are black.</span></span>  
  
 <span data-ttu-id="919ff-113">**すべてのスコープの変数を表示する**</span><span class="sxs-lookup"><span data-stu-id="919ff-113">**Show variables of all scopes**</span></span>  
 <span data-ttu-id="919ff-114">選択すると、パッケージのスコープ内の変数、および、パッケージにあるコンテナー、タスク、およびイベント ハンドラーのスコープ内の変数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="919ff-114">Select to show variables within the scope the package, and within the scope of containers, tasks, and event handlers in the package.</span></span> <span data-ttu-id="919ff-115">このオプションをオフにすると、パッケージのスコープ内の変数、および、選択されたコンテナー、タスク、またはイベント ハンドラーのスコープ内の変数のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="919ff-115">Clear this option to show only variables within the scope of the package and within the scope of a selected container, task, or event handler.</span></span>  
  
 <span data-ttu-id="919ff-116">変数のスコープの詳細については、「 [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)領域の下にあります。</span><span class="sxs-lookup"><span data-stu-id="919ff-116">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-columns"></a><span data-ttu-id="919ff-117">列のオプション</span><span class="sxs-lookup"><span data-stu-id="919ff-117">Options for Columns</span></span>  
 <span data-ttu-id="919ff-118">**[変数]** ウィンドウに表示する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="919ff-118">Select the columns that you want to appear in the **Variables** window.</span></span>  
  
-   <span data-ttu-id="919ff-119">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="919ff-119">**Scope**</span></span>  
  
-   <span data-ttu-id="919ff-120">**データの種類**</span><span class="sxs-lookup"><span data-stu-id="919ff-120">**Data type**</span></span>  
  
-   <span data-ttu-id="919ff-121">**Value**</span><span class="sxs-lookup"><span data-stu-id="919ff-121">**Value**</span></span>  
  
-   <span data-ttu-id="919ff-122">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="919ff-122">**Namespace**</span></span>  
  
-   <span data-ttu-id="919ff-123">**[変数値の変化時にイベントを発生]**</span><span class="sxs-lookup"><span data-stu-id="919ff-123">**Raise event when variable value changes**</span></span>  
  
-   <span data-ttu-id="919ff-124">**説明**</span><span class="sxs-lookup"><span data-stu-id="919ff-124">**Description**</span></span>  
  
-   <span data-ttu-id="919ff-125">**[式]**</span><span class="sxs-lookup"><span data-stu-id="919ff-125">**Expression**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919ff-126">参照</span><span class="sxs-lookup"><span data-stu-id="919ff-126">See Also</span></span>  
 <span data-ttu-id="919ff-127">[変数ウィンドウ](../../2014/integration-services/variables-window.md) </span><span class="sxs-lookup"><span data-stu-id="919ff-127">[Variables Window](../../2014/integration-services/variables-window.md) </span></span>  
 <span data-ttu-id="919ff-128">[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="919ff-128">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="919ff-129">[パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="919ff-129">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="919ff-130">Integration Services &#40;SSIS&#41; のイベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="919ff-130">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
