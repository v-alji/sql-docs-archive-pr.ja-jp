---
title: プロパティ式を追加または変更する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], creating
- expressions [Integration Services], property expressions
ms.assetid: cb5da499-065f-4fa6-9f6d-5bc5f385241e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d6d12fbe46930818af2b47b59620963d39616e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642940"
---
# <a name="add-or-change-a-property-expression"></a><span data-ttu-id="e4b58-102">プロパティ式を追加または変更する</span><span class="sxs-lookup"><span data-stu-id="e4b58-102">Add or Change a Property Expression</span></span>
  <span data-ttu-id="e4b58-103">パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、シーケンス コンテナー、イベント ハンドラー、パッケージおよびプロジェクト レベルの接続マネージャー、およびログ プロバイダーに対してプロパティ式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-103">You can create property expressions for packages, tasks, Foreach Loop containers, For Loop containers, Sequence containers, event handlers, package and project level connection managers, and log providers.</span></span>  
  
 <span data-ttu-id="e4b58-104">プロパティ式を作成または変更するには、 **[プロパティ式エディター]** か **[式ビルダー]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4b58-104">To create or change property expressions, you can use either the **Property Expressions Editor** or **Expression Builder**.</span></span> <span data-ttu-id="e4b58-105">**[プロパティ式エディター]** には、タスクおよびコンテナーで使用可能なカスタム エディターか、 **[プロパティ]** ウィンドウからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-105">The **Property Expressions Editor** can be accessed from either the custom editors that are available for tasks and containers, or from the **Properties** window.</span></span> <span data-ttu-id="e4b58-106">**[式ビルダー]** には、 **[プロパティ式エディター]** 内からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-106">**Expression Builder** can be accessed from inside the **Property Expressions Editor**.</span></span> <span data-ttu-id="e4b58-107">**[プロパティ式エディター]** または **[式ビルダー]** のいずれかで式を作成することができますが、 **[式ビルダー]** には、複雑な式の作成を容易にするグラフィカル ツール セットが備わっています。</span><span class="sxs-lookup"><span data-stu-id="e4b58-107">While you can write expressions in either the **Property Expressions Editor** or **Expression Builder**, **Expression Builder** provides a graphical set of tools that makes it simple to build complex expressions.</span></span>  
  
 <span data-ttu-id="e4b58-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が提供する構文、演算子、および関数の詳細については、「[ &#40;SSIS 式&#41;](operators-ssis-expression.md)」および「[ &#40;SSIS 式&#41;](functions-ssis-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4b58-108">To learn more about the syntax, operators, and functions that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides, see [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) and [Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md).</span></span> <span data-ttu-id="e4b58-109">各演算子または関数のトピックには、式で演算子や関数を使用する例が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-109">The topic for each operator or function includes examples of using that operator or function in an expression.</span></span> <span data-ttu-id="e4b58-110">複雑な式の例については、「 [パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4b58-110">For examples of more complex expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
### <a name="to-create-or-change-a-property-expression"></a><span data-ttu-id="e4b58-111">プロパティ式を作成または変更するには</span><span class="sxs-lookup"><span data-stu-id="e4b58-111">To create or change a property expression</span></span>  
  
1.  <span data-ttu-id="e4b58-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが含まれているプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="e4b58-113">ソリューション エクスプローラーで、パッケージをダブルクリックして開き、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e4b58-113">In Solution Explorer, double-click the package to open it, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="e4b58-114">アイテムがタスクまたはコンテナーの場合は、アイテムをダブルクリックし、エディターの **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b58-114">If the item is a task or a container, double-click the item, and then click **Expressions** in the editor.</span></span>  
  
    -   <span data-ttu-id="e4b58-115">アイテムを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b58-115">Right-click the item and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e4b58-116">**[式]** ボックス内でクリックし、省略記号 [...] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b58-116">Click in the **Expressions** box and then click the ellipsis (...).</span></span>  
  
4.  <span data-ttu-id="e4b58-117">**[プロパティ式エディター]** で、 **[プロパティ]** ボックスの一覧からプロパティを選択し、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e4b58-117">In the **Property Expressions Editor**, select a property in the **Property** list, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="e4b58-118">**[式]** 列で直接プロパティ式を入力するか変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b58-118">Type or change the property expression directly in the **Expression** column, and then click **OK**.</span></span>  
  
         <span data-ttu-id="e4b58-119">または</span><span class="sxs-lookup"><span data-stu-id="e4b58-119">-or-</span></span>  
  
    -   <span data-ttu-id="e4b58-120">プロパティの式の行の省略記号 [...] をクリックし、 **[式ビルダー]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-120">Click the ellipsis (...) in the expression row of the property to open the **Expression Builder**.</span></span>  
  
5.  <span data-ttu-id="e4b58-121">(省略可能) **[式ビルダー]** での次のタスクのいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="e4b58-121">(Optional) In the **Expression Builder**, do any of the following tasks:</span></span>  
  
    -   <span data-ttu-id="e4b58-122">システム変数およびユーザー定義変数にアクセスするには、 **[変数]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="e4b58-122">To access system and user-defined variables, expand **Variables**.</span></span>  
  
    -   <span data-ttu-id="e4b58-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 式言語で提供される関数、キャスト、および演算子にアクセスするには、 **[数学関数]** 、 **[文字列関数]** 、 **[日付/時刻関数]** 、 **[NULL 関数]** 、 **[型キャスト]** 、および **[演算子]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="e4b58-123">To access the functions, the casts, and the operators that the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression language provides, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators**.</span></span>  
  
    -   <span data-ttu-id="e4b58-124">**[式ビルダー]** で式を作成または変更するには、変数、列、関数、演算子、およびキャストを **[式]** ボックスにドラッグするか、または式をボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="e4b58-124">To build or change an expression in the **Expression Builder**, drag variables, columns, functions, operators, and casts to the **Expression** box, or type the expression in the box.</span></span>  
  
    -   <span data-ttu-id="e4b58-125">式の評価結果を表示するには、 **[式ビルダー]** の **[式の評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e4b58-125">To view the evaluation result of the expression, click **Evaluate Expression** in the **Expression Builder**.</span></span>  
  
         <span data-ttu-id="e4b58-126">式が有効でない場合は、式の構文エラーを示す警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="e4b58-126">If the expression is not valid, an alert appears that describes the syntax errors in the expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e4b58-127">式の評価を行っても、評価結果はプロパティに割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="e4b58-127">Evaluating an expression does not assign the evaluation result to the property.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e4b58-128">参照</span><span class="sxs-lookup"><span data-stu-id="e4b58-128">See Also</span></span>  
 <span data-ttu-id="e4b58-129">[Integration Services &#40;SSIS&#41; 式](integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-129">[Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="e4b58-130">[パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-130">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="e4b58-131">[Integration Services &#40;SSIS&#41; パッケージ](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-131">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="e4b58-132">[Integration Services コンテナー](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-132">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="e4b58-133">[Integration Services タスク](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-133">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="e4b58-134">[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-134">[Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="e4b58-135">[Integration Services &#40;SSIS&#41; の接続](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="e4b58-135">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="e4b58-136">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="e4b58-136">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)  
  
  
