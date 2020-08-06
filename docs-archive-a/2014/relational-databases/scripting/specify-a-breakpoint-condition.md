---
title: ブレークポイント条件の指定
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 659b6ca1149eb8f0412efbe2adbaf4c1ffce59d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717798"
---
# <a name="specify-a-breakpoint-condition"></a><span data-ttu-id="28cd3-102">ブレークポイント条件の指定</span><span class="sxs-lookup"><span data-stu-id="28cd3-102">Specify a Breakpoint Condition</span></span>
  <span data-ttu-id="28cd3-103">ブレークポイント条件は、ブレークポイントに達したときにデバッガーによって評価される [!INCLUDE[tsql](../../includes/tsql-md.md)] 式です。</span><span class="sxs-lookup"><span data-stu-id="28cd3-103">A breakpoint condition is a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that is evaluated by the debugger when the breakpoint is reached.</span></span> <span data-ttu-id="28cd3-104">指定したヒット カウントに達し、指定したブレークポイントの条件が満たされると、デバッガーはブレークポイントに指定されたアクションを実行するか、中断します。</span><span class="sxs-lookup"><span data-stu-id="28cd3-104">If the condition is satisfied and any specified hit count reached, the debugger either breaks or performs the action specified for the breakpoint.</span></span>  
  
## <a name="specifying-conditions"></a><span data-ttu-id="28cd3-105">条件の指定</span><span class="sxs-lookup"><span data-stu-id="28cd3-105">Specifying Conditions</span></span>  
 <span data-ttu-id="28cd3-106">指定する式は、ブール値に評価される有効な Transact-SQL 式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="28cd3-106">The expression specified must be a valid Transact-SQL expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="28cd3-107">詳細については、「[式 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28cd3-107">For more information, see [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).</span></span>  
  
 <span data-ttu-id="28cd3-108">無効な構文でブレークポイント条件を指定した場合は、警告メッセージがすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="28cd3-108">If you specify a breakpoint condition with invalid syntax, a warning message appears immediately.</span></span> <span data-ttu-id="28cd3-109">構文は有効でも無効なセマンティクスの条件を指定すると、最初にブレークポイントにヒットしたときに警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="28cd3-109">If you specify a condition with valid syntax but invalid semantics, a warning message is displayed the first time the breakpoint is hit.</span></span> <span data-ttu-id="28cd3-110">どちらの場合にも、無効なブレークポイントにヒットしたときにデバッガーの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="28cd3-110">In either case, the debugger breaks execution when the invalid breakpoint is hit.</span></span>  
  
#### <a name="to-specify-a-condition"></a><span data-ttu-id="28cd3-111">条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="28cd3-111">To Specify a Condition</span></span>  
  
1.  <span data-ttu-id="28cd3-112">エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28cd3-112">In the editor window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="28cd3-113">または</span><span class="sxs-lookup"><span data-stu-id="28cd3-113">-or-</span></span>  
  
     <span data-ttu-id="28cd3-114">**[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28cd3-114">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="28cd3-115">**[ブレークポイントの条件]** ダイアログ ボックスで、 **[条件]** ボックスに有効なブール式を入力します。</span><span class="sxs-lookup"><span data-stu-id="28cd3-115">In the **Breakpoint Condition** dialog box, enter a valid Boolean expression in the **Condition** box.</span></span>  
  
3.  <span data-ttu-id="28cd3-116">式がに評価されたときに中断する場合は [ **true** ] `true` 、式の値が変更されたときに中断する場合は [**変更済み**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="28cd3-116">Choose **Is true** if you want to break when the expression evaluates to `true`, or choose **Has changed** if you want to break when the value of the expression has changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="28cd3-117">デバッガーは、初めてブレークポイントに達するまでブール式を評価しません。</span><span class="sxs-lookup"><span data-stu-id="28cd3-117">The debugger does not evaluate the Boolean expression until the first time the breakpoint is reached.</span></span> <span data-ttu-id="28cd3-118">**[変更された場合]** を選択した場合、デバッガーは最初の評価を変更とは見なさないため、最初の評価でブレークすることはありません。</span><span class="sxs-lookup"><span data-stu-id="28cd3-118">If you choose **Has changed**, the debugger does not consider the first evaluation to be a change, so the debugger will not break on the first evaluation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cd3-119">参照</span><span class="sxs-lookup"><span data-stu-id="28cd3-119">See Also</span></span>  
 <span data-ttu-id="28cd3-120">[ヒットカウントの指定](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="28cd3-120">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="28cd3-121">ブレークポイント アクションの指定</span><span class="sxs-lookup"><span data-stu-id="28cd3-121">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
