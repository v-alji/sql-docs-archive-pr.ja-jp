---
title: 条件分割変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 386a93eb7c3058c7c3e98f2b652199d115d841f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632629"
---
# <a name="conditional-split-transformation-editor"></a><span data-ttu-id="1aa13-102">条件分割変換エディター</span><span class="sxs-lookup"><span data-stu-id="1aa13-102">Conditional Split Transformation Editor</span></span>
  <span data-ttu-id="1aa13-103">**[条件分割変換エディター]** を使用すると、式の作成、式が評価される順序の設定、条件分割の出力の名前付けを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1aa13-103">Use the **Conditional Split Transformation Editor** dialog box to create expressions, set the order in which expressions are evaluated, and name the outputs of a conditional split.</span></span> <span data-ttu-id="1aa13-104">このダイアログ ボックスには、式の作成に使用する、数学関数、文字列関数、日付/時刻関数や演算子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1aa13-104">This dialog box includes mathematical, string, and date/time functions and operators that you can use to build expressions.</span></span> <span data-ttu-id="1aa13-105">True として評価される最初の条件は、行が送信される出力を決定します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-105">The first condition that evaluates as true determines the output to which a row is directed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1aa13-106">条件分割変換は、1 つの出力に対してのみ各入力行を送信します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-106">The Conditional Split transformation directs each input row to one output only.</span></span> <span data-ttu-id="1aa13-107">複数の条件を入力した場合、変換によって、条件が True である最初の出力に各行が送信され、その行に対して後続する条件は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1aa13-107">If you enter multiple conditions, the transformation sends each row to the first output for which the condition is true and disregards subsequent conditions for that row.</span></span> <span data-ttu-id="1aa13-108">複数の条件を継続して評価する必要がある場合、データ フローで複数の条件分割変換の連結が必要となることがあります。</span><span class="sxs-lookup"><span data-stu-id="1aa13-108">If you need to evaluate several conditions successively, you may need to concatenate multiple Conditional Split transformations in the data flow.</span></span>  
  
 <span data-ttu-id="1aa13-109">条件分割変換の詳細については、「 [条件分割変換](data-flow/transformations/conditional-split-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1aa13-109">To learn more about the Conditional Split transformation, see [Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1aa13-110">Options</span><span class="sxs-lookup"><span data-stu-id="1aa13-110">Options</span></span>  
 <span data-ttu-id="1aa13-111">**Order**</span><span class="sxs-lookup"><span data-stu-id="1aa13-111">**Order**</span></span>  
 <span data-ttu-id="1aa13-112">行を選択し、右側の矢印キーを使用して、式を評価する順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-112">Select a row and use the arrow keys at right to change the order in which to evaluate expressions.</span></span>  
  
 <span data-ttu-id="1aa13-113">**出力名**</span><span class="sxs-lookup"><span data-stu-id="1aa13-113">**Output Name**</span></span>  
 <span data-ttu-id="1aa13-114">出力名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-114">Provide an output name.</span></span> <span data-ttu-id="1aa13-115">既定は数字の付いた場合の一覧ですが、一意のわかりやすい名前を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="1aa13-115">The default is a numbered list of cases; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="1aa13-116">**Condition**</span><span class="sxs-lookup"><span data-stu-id="1aa13-116">**Condition**</span></span>  
 <span data-ttu-id="1aa13-117">式を入力するか、使用可能な列、変数、関数、および演算子の一覧からドラッグして式を作成します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-117">Type an expression or build one by dragging from the list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="1aa13-118">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="1aa13-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="1aa13-119">\*\*: \*\*  [Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)、[ &#40;SSIS 式&#41;](expressions/operators-ssis-expression.md)、および [ &#40;SSIS 式&#41;](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="1aa13-119">**Related topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="1aa13-120">**[既定の出力名]**</span><span class="sxs-lookup"><span data-stu-id="1aa13-120">**Default output name**</span></span>  
 <span data-ttu-id="1aa13-121">既定の出力の名前を入力するか、既定を使用します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-121">Type a name for the default output, or use the default.</span></span>  
  
 <span data-ttu-id="1aa13-122">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="1aa13-122">**Configure error output**</span></span>  
 <span data-ttu-id="1aa13-123">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="1aa13-123">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa13-124">参照</span><span class="sxs-lookup"><span data-stu-id="1aa13-124">See Also</span></span>  
 <span data-ttu-id="1aa13-125">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1aa13-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="1aa13-126">条件分割変換を使用してデータセットを分割する</span><span class="sxs-lookup"><span data-stu-id="1aa13-126">Split a Dataset by Using the Conditional Split Transformation</span></span>](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
