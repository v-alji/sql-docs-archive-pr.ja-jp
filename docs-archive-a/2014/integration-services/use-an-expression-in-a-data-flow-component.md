---
title: データフローコンポーネント | で式を使用するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 653bf468d0af6d44c5abe7344fcc13f93f86b430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718428"
---
# <a name="use-an-expression-in-a-data-flow-component"></a><span data-ttu-id="a1277-102">データ フロー コンポーネントで式を使用する</span><span class="sxs-lookup"><span data-stu-id="a1277-102">Use an Expression in a Data Flow Component</span></span>
  <span data-ttu-id="a1277-103">この手順では、条件分割変換または派生列変換に式を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1277-103">This procedure describes how to add an expression to the Conditional Split transformation or to the Derived Column transformation.</span></span> <span data-ttu-id="a1277-104">条件分割変換では、式を使用して、変換出力にデータ行を出力する条件を定義します。また、派生列変換では、式を使用して、列に割り当てる値を定義します。</span><span class="sxs-lookup"><span data-stu-id="a1277-104">The Conditional Split transformation uses expressions to define the conditions that direct data rows to a transformation output, and the Derived Column transformation uses expressions to define values assigned to columns.</span></span>  
  
 <span data-ttu-id="a1277-105">変換に式を実装するには、あらかじめパッケージに少なくとも 1 つのデータ フロー タスクとソースが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1277-105">To implement an expression in a transformation, the package must already include at least one Data Flow task and a source.</span></span> <span data-ttu-id="a1277-106">パッケージにアイテムを追加する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1277-106">For information about adding items to packages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a1277-107">制御フローのタスクまたはコンテナーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="a1277-107">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [<span data-ttu-id="a1277-108">データ フローでコンポーネントを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="a1277-108">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [<span data-ttu-id="a1277-109">データ フロー内でコンポーネントを連結する</span><span class="sxs-lookup"><span data-stu-id="a1277-109">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a><span data-ttu-id="a1277-110">式を作成するには</span><span class="sxs-lookup"><span data-stu-id="a1277-110">To create an expression</span></span>  
  
1.  <span data-ttu-id="a1277-111">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a1277-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a1277-112">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a1277-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a1277-113">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[制御フロー]** タブをクリックし、式を実装するデータ フローを含むデータ フロー タスクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1277-113">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow** tab, and then click the Data Flow task that contains the data flow in which you want to implement an expression.</span></span>  
  
4.  <span data-ttu-id="a1277-114">**[データ フロー]** タブをクリックし、 **[ツールボックス]** からデザイン画面に条件分割変換または派生列変換のいずれかをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a1277-114">Click the **Data Flow** tab, and drag either a Conditional Split or Derived Column transformation from the **Toolbox** to the design surface.</span></span>  
  
5.  <span data-ttu-id="a1277-115">緑色のコネクタをソースまたは変換から条件分割変換または派生列変換にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a1277-115">Drag the green connector from the source or a transformation to the Conditional Split or Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="a1277-116">変換をダブルクリックして、変換のダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a1277-116">Double-click the transformation to open its dialog box.</span></span>  
  
7.  <span data-ttu-id="a1277-117">左側のペインで **[変数]** を展開し、システム変数およびユーザー定義変数を表示します。また、 **[列]** を展開して、変換の入力列を表示します。</span><span class="sxs-lookup"><span data-stu-id="a1277-117">In the left pane, expand **Variables** to display system and user-defined variables, and expand **Columns** to display the transformation input columns.</span></span>  
  
8.  <span data-ttu-id="a1277-118">右側のペインで **[数学関数]**、 **[文字列関数]**、 **[日付/時刻関数]**、 **[NULL 関数]**、 **[型キャスト]**、および **[演算子]** を展開して、式の文法で用意されている関数、キャスト、および演算子にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a1277-118">In the right pane, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators** to access the functions, the casts, and the operators that the expression grammar provides.</span></span>  
  
9. <span data-ttu-id="a1277-119">変換に応じて、次のいずれかの操作を実行し、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="a1277-119">Depending on the transformation, do one of the following to build an expression:</span></span>  
  
    -   <span data-ttu-id="a1277-120">**[条件分割変換エディター]** ダイアログ ボックスで、変数、列、関数、演算子、およびキャストを **[条件]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a1277-120">In the **Conditional Split Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Condition** column.</span></span> <span data-ttu-id="a1277-121">ドラッグする代わりに、 **[条件]** 列に式を直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="a1277-121">Alternatively, you can type an expression directly in the **Condition** column.</span></span>  
  
    -   <span data-ttu-id="a1277-122">**[派生列変換エディター]** ダイアログ ボックスで、変数、列、関数、演算子、およびキャストを **[式]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a1277-122">In the **Derived Column Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Expression** column.</span></span> <span data-ttu-id="a1277-123">ドラッグする代わりに、 **[式]** 列に式を直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="a1277-123">Alternatively, you can type an expression directly in the **Expression** column.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a1277-124">**[条件]** 列または **[式]** 列からフォーカスを外したときに、式テキストが強調表示された場合、式の文法が間違っていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a1277-124">When you remove the focus from the **Condition** column or the **Expression** column, the expression text might be highlighted to indicate that the expression syntax is incorrect.</span></span>  
  
10. <span data-ttu-id="a1277-125">[**OK**] をクリックして、ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="a1277-125">Click **OK** to exit the dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a1277-126">式が有効でない場合、式に文法エラーがあることを示す警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1277-126">If the expression is not valid, an alert appears describing the syntax errors in the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1277-127">参照</span><span class="sxs-lookup"><span data-stu-id="a1277-127">See Also</span></span>  
 <span data-ttu-id="a1277-128">[SSIS&#41; 式の Integration Services &#40;](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="a1277-128">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="a1277-129">[条件分割変換](data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a1277-129">[Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="a1277-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a1277-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span></span>  
 <span data-ttu-id="a1277-131">[データ フロー タスク](control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="a1277-131">[Data Flow Task](control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="a1277-132">データ フロー</span><span class="sxs-lookup"><span data-stu-id="a1277-132">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
