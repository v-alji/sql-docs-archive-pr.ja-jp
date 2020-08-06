---
title: 既定の優先順位制約を使用してタスクとコンテナーを連結する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 00207172babdb41b1030e77e71a2c8bc3b99799d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738611"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a><span data-ttu-id="67b3b-102">既定の優先順位制約を使用してタスクとコンテナーを連結する</span><span class="sxs-lookup"><span data-stu-id="67b3b-102">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>
  <span data-ttu-id="67b3b-103">優先順位制約は、2 つの実行可能ファイルを連結します。</span><span class="sxs-lookup"><span data-stu-id="67b3b-103">Precedence constraints connect two executables.</span></span> <span data-ttu-id="67b3b-104">実行可能ファイルには、任意のタスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="67b3b-104">An executable can be any task or a For Loop, Foreach Loop, or Sequence container.</span></span> <span data-ttu-id="67b3b-105">この手順では、優先順位制約の既定の動作を設定する方法と、既定の優先順位制約を使用して実行可能ファイルを連結する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="67b3b-105">This procedure describes how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints.</span></span>  
  
## <a name="creating-default-precedence-constraints"></a><span data-ttu-id="67b3b-106">既定の優先順位制約の作成</span><span class="sxs-lookup"><span data-stu-id="67b3b-106">Creating Default Precedence Constraints</span></span>  
 <span data-ttu-id="67b3b-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを初めて使用する場合、優先順位制約の既定値は `Success` です。</span><span class="sxs-lookup"><span data-stu-id="67b3b-107">When you first use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the default value of a precedence constraint is `Success`.</span></span> <span data-ttu-id="67b3b-108">別の既定値を使用するように [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを構成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="67b3b-108">Follow these steps to configure [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to use a different default value for precedence constraints.</span></span>  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a><span data-ttu-id="67b3b-109">優先順位制約の既定値を設定するには</span><span class="sxs-lookup"><span data-stu-id="67b3b-109">To set the default value for precedence constraints</span></span>  
  
1.  <span data-ttu-id="67b3b-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="67b3b-110">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="67b3b-111">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67b3b-111">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="67b3b-112">**[オプション]** ダイアログ ボックスで **[ビジネス インテリジェンス デザイナー]** を展開し、次に **[Integration Services デザイナー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="67b3b-112">In the **Options** dialog box, expand **Business Intelligence Designers,** and then expand **Integration Services Designers**.</span></span>  
  
4.  <span data-ttu-id="67b3b-113">**[制御フローの自動接続]** をクリックし、 **[選択した図形に新しい図形を既定で接続する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="67b3b-113">Click **Control Flow Auto Connect** and select **Connect a new shape to the selected shape by default**.</span></span>  
  
5.  <span data-ttu-id="67b3b-114">ドロップダウン リストで、 **[新しい図形に失敗制約を使用]** または **[新しい図形に完了制約を使用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="67b3b-114">In the drop-down list, choose either **Use a Failure constraint for the new shape** or **Use a Completion constraint for the new shape**.</span></span>  
  
6.  <span data-ttu-id="67b3b-115">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67b3b-115">Click **OK**.</span></span>  
  
#### <a name="to-create-a-default-precedence-constraint"></a><span data-ttu-id="67b3b-116">既定の優先順位制約を作成するには</span><span class="sxs-lookup"><span data-stu-id="67b3b-116">To create a default precedence constraint</span></span>  
  
1.  <span data-ttu-id="67b3b-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="67b3b-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="67b3b-118">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="67b3b-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="67b3b-119">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="67b3b-119">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="67b3b-120">**[制御フロー]** タブのデザイン画面で、タスクまたはコンテナーをクリックし、そのコネクタを、優先順位制約を適用する実行可能ファイルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67b3b-120">On the design surface of the **Control Flow** tab, click the task or container and drag its connector to the executable to which you want the precedence constraint to apply.</span></span>  
  
5.  <span data-ttu-id="67b3b-121">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67b3b-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b3b-122">参照</span><span class="sxs-lookup"><span data-stu-id="67b3b-122">See Also</span></span>  
 <span data-ttu-id="67b3b-123">[優先順位制約](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="67b3b-123">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="67b3b-124">[ショートカットメニューを使用して優先順位制約の値を設定する](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="67b3b-124">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="67b3b-125">[優先順位制約のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="67b3b-125">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="67b3b-126">優先順位制約で式を使用する</span><span class="sxs-lookup"><span data-stu-id="67b3b-126">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
