---
title: 優先順位制約で式を使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a997efa448a8381cc8251cd4cbf69dc59f8968e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716413"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a><span data-ttu-id="41815-102">優先順位制約で式を使用する</span><span class="sxs-lookup"><span data-stu-id="41815-102">Use an Expression in a Precedence Constraint</span></span>
  <span data-ttu-id="41815-103">この手順では、 **[優先順位制約エディター]** ダイアログ ボックスを使用して、優先順位制約に式を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41815-103">This procedure describes how to add an expression to a precedence constraint by using the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="41815-104">優先順位制約に式を追加する場合、タスクまたはコンテナーのいずれかである実行可能ファイルを 2 つ以上含め、それらが優先順位制約によって連結される必要があります。</span><span class="sxs-lookup"><span data-stu-id="41815-104">Before you can add an expression to a precedence constraint, the package must include at least two executables, either tasks or containers, and they must be connected by a precedence constraint.</span></span>  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a><span data-ttu-id="41815-105">優先順位制約に式を追加するには</span><span class="sxs-lookup"><span data-stu-id="41815-105">To add an expression to a precedence constraint</span></span>  
  
1.  <span data-ttu-id="41815-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="41815-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="41815-107">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="41815-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="41815-108">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="41815-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="41815-109">**[制御フロー]** タブのデザイン画面で、優先順位制約をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="41815-109">On the design surface of the **Control Flow** tab, double-click the precedence constraint.</span></span> <span data-ttu-id="41815-110">**[優先順位制約エディター]** が開きます。</span><span class="sxs-lookup"><span data-stu-id="41815-110">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="41815-111">**[評価操作]** の一覧で、 **[式]**、 **[式と制約]** 、または **[式または制約]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="41815-111">Select **Expression**, **Expression and Constraint**, or **Expression or Constraint** in the **Evaluation operation** list.</span></span>  
  
6.  <span data-ttu-id="41815-112">**[式]** ボックスに式を入力するか、式ビルダーを起動して式を作成します。</span><span class="sxs-lookup"><span data-stu-id="41815-112">Type an expression in the **Expression** text box or launch the Expression Builder to create an expression.</span></span>  
  
7.  <span data-ttu-id="41815-113">式の構文を検証するには、 **[テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41815-113">To validate the expression syntax, click **Test**.</span></span>  
  
8.  <span data-ttu-id="41815-114">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41815-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41815-115">参照</span><span class="sxs-lookup"><span data-stu-id="41815-115">See Also</span></span>  
 <span data-ttu-id="41815-116">[優先順位制約](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="41815-116">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="41815-117">[既定の優先順位制約を使用してタスクとコンテナーを連結する](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="41815-117">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="41815-118">[ショートカットメニューを使用して優先順位制約の値を設定する](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="41815-118">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="41815-119">[優先順位制約のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="41815-119">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="41815-120">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="41815-120">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
