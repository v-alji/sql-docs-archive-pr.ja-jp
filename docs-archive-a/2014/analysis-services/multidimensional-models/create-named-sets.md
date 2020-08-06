---
title: 名前付きセットの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
ms.openlocfilehash: e92984102ceb8ad0ac049c15870e9f1efd6090fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712574"
---
# <a name="create-named-sets"></a><span data-ttu-id="40289-102">名前付きセットの作成</span><span class="sxs-lookup"><span data-stu-id="40289-102">Create Named Sets</span></span>
  <span data-ttu-id="40289-103">名前付きセットはディメンション メンバーのセットまたはセット式で、たとえば多次元式 (MDX) のクエリなどで再利用するために作成されます。</span><span class="sxs-lookup"><span data-stu-id="40289-103">A named set is a set of dimension members or a set expression that is created for reuse, for example in Multidimensional Expressions (MDX) queries.</span></span> <span data-ttu-id="40289-104">名前付きセットは、キューブ データ、算術演算子、数値、および関数を組み合わせることによって作成できます。</span><span class="sxs-lookup"><span data-stu-id="40289-104">You can create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="40289-105">たとえば、Top Ten Factories という名前付きセットを作成して、その中に Factories ディメンションのメンバーのうち Production メジャーの最高値を持つものを上から 10 個含めることができます。</span><span class="sxs-lookup"><span data-stu-id="40289-105">For example, you can create a named set called Top Ten Factories that contains the ten members of the Factories dimension that have the highest values for the Production measure.</span></span> <span data-ttu-id="40289-106">この結果、エンド ユーザーがクエリで Top Ten Factories を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40289-106">Top Ten Factories can then be used in queries by end users.</span></span> <span data-ttu-id="40289-107">たとえば、エンド ユーザーは Top Ten Factories を 1 つの軸に配置し、Production などの Measures ディメンションを別の軸に配置できます。</span><span class="sxs-lookup"><span data-stu-id="40289-107">For example, an end user can place Top Ten Factories on one axis and the Measures dimension, including Production, on another axis.</span></span> <span data-ttu-id="40289-108">詳細については、「[多次元モデルの計算](calculations-in-multidimensional-models.md)」および「[MDX での名前付きセットの作成 (MDX)](mdx/mdx-named-sets-building-named-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40289-108">For more information, see [Calculations in Multidimensional Models](calculations-in-multidimensional-models.md), and [Building Named Sets in MDX &#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="40289-109">名前付きセットを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい名前付きセット]** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="40289-109">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="40289-110">このコマンドは、 **[計算]** タブのツール バー上にある **[キューブ]** メニューから起動できます。</span><span class="sxs-lookup"><span data-stu-id="40289-110">This command can be invoked on the **Cube** menu on the **Calculations** tab toolbar.</span></span> <span data-ttu-id="40289-111">このコマンドでは、名前付きセットの次のオプションを指定するためのフォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="40289-111">This command displays a form to specify the following options for the named set:</span></span>  
  
 <span data-ttu-id="40289-112">**名前**</span><span class="sxs-lookup"><span data-stu-id="40289-112">**Name**</span></span>  
 <span data-ttu-id="40289-113">名前付きセットの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="40289-113">Select the name of the named set.</span></span> <span data-ttu-id="40289-114">この名前は、エンド ユーザーがキューブを参照したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="40289-114">This name appears to end users when they browse the cube.</span></span>  
  
 <span data-ttu-id="40289-115">**[式]**</span><span class="sxs-lookup"><span data-stu-id="40289-115">**Expression**</span></span>  
 <span data-ttu-id="40289-116">名前付きセットを作成する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="40289-116">Specify the expression that produces the named set.</span></span> <span data-ttu-id="40289-117">この式は、MDX で記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="40289-117">This expression can be written in MDX.</span></span> <span data-ttu-id="40289-118">式には、次の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="40289-118">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="40289-119">ディメンション、レベル、メジャーなど、キューブのコンポーネントを表すデータ式</span><span class="sxs-lookup"><span data-stu-id="40289-119">Data expressions that represent cube components such as dimensions, levels, measures, and so on.</span></span>  
  
-   <span data-ttu-id="40289-120">算術演算子</span><span class="sxs-lookup"><span data-stu-id="40289-120">Arithmetic operators.</span></span>  
  
-   <span data-ttu-id="40289-121">数値</span><span class="sxs-lookup"><span data-stu-id="40289-121">Numbers.</span></span>  
  
-   <span data-ttu-id="40289-122">関数</span><span class="sxs-lookup"><span data-stu-id="40289-122">Functions.</span></span>  
  
 <span data-ttu-id="40289-123">キューブ コンポーネントは、 **[計算ツール]** ペインの **[メタデータ]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="40289-123">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span> <span data-ttu-id="40289-124">関数は、 **[計算ツール]** ペインの **[関数]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="40289-124">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="40289-125">セット内のメンバーに明示的に名前を付けてセット式を作成する場合は、メンバーの一覧を中かっこ () で囲み {} ます。</span><span class="sxs-lookup"><span data-stu-id="40289-125">If you create the set expression by explicitly naming the members in the set, enclose the list of members in a pair of braces ({}).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40289-126">参照</span><span class="sxs-lookup"><span data-stu-id="40289-126">See Also</span></span>  
 [<span data-ttu-id="40289-127">多次元モデルの計算</span><span class="sxs-lookup"><span data-stu-id="40289-127">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
