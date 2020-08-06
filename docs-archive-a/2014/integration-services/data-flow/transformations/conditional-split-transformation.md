---
title: 条件分割変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittrans.f1
helpviewer_keywords:
- Conditional Split transformation
- route rows to different outputs [Integration Services]
ms.assetid: 3f8b5825-226f-413c-ba8f-0bb931ca3770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96ff4b177992c329908ebc93df8f6220168e634d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642205"
---
# <a name="conditional-split-transformation"></a><span data-ttu-id="57303-102">条件分割変換</span><span class="sxs-lookup"><span data-stu-id="57303-102">Conditional Split Transformation</span></span>
  <span data-ttu-id="57303-103">条件分割変換では、データ行をデータの内容に応じた別の出力にルートできます。</span><span class="sxs-lookup"><span data-stu-id="57303-103">The Conditional Split transformation can route data rows to different outputs depending on the content of the data.</span></span> <span data-ttu-id="57303-104">条件分割変換の実装は、プログラミング言語の CASE 決定構造と同様です。</span><span class="sxs-lookup"><span data-stu-id="57303-104">The implementation of the Conditional Split transformation is similar to a CASE decision structure in a programming language.</span></span> <span data-ttu-id="57303-105">この変換は式を評価し、その結果に基づいて、データ行を指定された出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="57303-105">The transformation evaluates expressions, and based on the results, directs the data row to the specified output.</span></span> <span data-ttu-id="57303-106">この変換には既定の出力も用意されているので、行が式に一致しない場合は既定の出力に送られます。</span><span class="sxs-lookup"><span data-stu-id="57303-106">This transformation also provides a default output, so that if a row matches no expression it is directed to the default output.</span></span>  
  
## <a name="configuration-of-the-conditional-split-transformation"></a><span data-ttu-id="57303-107">条件分割変換の構成</span><span class="sxs-lookup"><span data-stu-id="57303-107">Configuration of the Conditional Split Transformation</span></span>  
 <span data-ttu-id="57303-108">条件分割変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="57303-108">You can configure the Conditional Split transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="57303-109">変換をテストする各条件に対して、ブール型に評価される式を指定します。</span><span class="sxs-lookup"><span data-stu-id="57303-109">Provide an expression that evaluates to a Boolean for each condition you want the transformation to test.</span></span>  
  
-   <span data-ttu-id="57303-110">条件を評価する順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="57303-110">Specify the order in which the conditions are evaluated.</span></span> <span data-ttu-id="57303-111">行は、TRUE に評価される最初の条件に対応した出力へ送信されるため、順序の指定は重要です。</span><span class="sxs-lookup"><span data-stu-id="57303-111">Order is significant, because a row is sent to the output corresponding to the first condition that evaluates to true.</span></span>  
  
-   <span data-ttu-id="57303-112">変換に対する既定の出力を指定します。</span><span class="sxs-lookup"><span data-stu-id="57303-112">Specify the default output for the transformation.</span></span> <span data-ttu-id="57303-113">この変換では、既定の出力を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57303-113">The transformation requires that a default output be specified.</span></span>  
  
 <span data-ttu-id="57303-114">各入力行は、1 つの出力にのみ送信できます。この出力は、TRUE に評価される最初の条件に対する出力です。</span><span class="sxs-lookup"><span data-stu-id="57303-114">Each input row can be sent to only one output, that being the output for the first condition that evaluates to true.</span></span> <span data-ttu-id="57303-115">たとえば、次の条件は、 **FirstName** 列にある文字 *A* で始まる行を 1 つの出力に、文字 *B* で始まる行を別の 1 つの出力に、その他のすべての行を既定の出力に送信します。</span><span class="sxs-lookup"><span data-stu-id="57303-115">For example, the following conditions direct any rows in the **FirstName** column that begin with the letter *A* to one output, rows that begin with the letter *B* to a different output, and all other rows to the default output.</span></span>  
  
 <span data-ttu-id="57303-116">出力 1</span><span class="sxs-lookup"><span data-stu-id="57303-116">Output 1</span></span>  
  
 `SUBSTRING(FirstName,1,1) == "A"`  
  
 <span data-ttu-id="57303-117">出力 2</span><span class="sxs-lookup"><span data-stu-id="57303-117">Output 2</span></span>  
  
 `SUBSTRING(FirstName,1,1) == "B"`  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="57303-118">には、入力データを評価して出力データを出力する式を作成するために使用できる、関数と演算子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57303-118">includes functions and operators that you can use to create the expressions that evaluate input data and direct output data.</span></span> <span data-ttu-id="57303-119">詳細については、「 [Integration Services (SSIS) 式](../../expressions/integration-services-ssis-expressions.md)に評価されるまでそのワークフローを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="57303-119">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="57303-120">条件分割変換には、`FriendlyExpression` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="57303-120">The Conditional Split transformation includes the `FriendlyExpression` custom property.</span></span> <span data-ttu-id="57303-121">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="57303-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="57303-122">詳細については、「 [パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md) 」および「 [変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57303-122">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="57303-123">この変換は、1 つの入力、1 つ以上の出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="57303-123">This transformation has one input, one or more outputs, and one error output.</span></span>  
  
 <span data-ttu-id="57303-124">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="57303-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="57303-125">**[条件分割変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [[条件分割変換エディター]](../../conditional-split-transformation-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57303-125">For more information about the properties that you can set in the **Conditional Split Transformation Editor** dialog box, see [Conditional Split Transformation Editor](../../conditional-split-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="57303-126">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="57303-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="57303-127">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="57303-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="57303-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="57303-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="57303-129">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="57303-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="57303-130">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="57303-130">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="57303-131">条件分割変換を使用してデータセットを分割する</span><span class="sxs-lookup"><span data-stu-id="57303-131">Split a Dataset by Using the Conditional Split Transformation</span></span>](conditional-split-transformation.md)  
  
-   [<span data-ttu-id="57303-132">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="57303-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="57303-133">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="57303-133">Related Tasks</span></span>  
 [<span data-ttu-id="57303-134">条件分割変換を使用してデータセットを分割する</span><span class="sxs-lookup"><span data-stu-id="57303-134">Split a Dataset by Using the Conditional Split Transformation</span></span>](conditional-split-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="57303-135">参照</span><span class="sxs-lookup"><span data-stu-id="57303-135">See Also</span></span>  
 <span data-ttu-id="57303-136">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="57303-136">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="57303-137">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="57303-137">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
