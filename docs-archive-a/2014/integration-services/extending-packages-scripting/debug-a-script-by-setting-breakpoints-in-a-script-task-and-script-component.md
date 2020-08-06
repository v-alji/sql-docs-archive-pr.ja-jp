---
title: スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45e7ffc6680c33e3b17b9b39fba0aabd8fa4028c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633907"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a><span data-ttu-id="0739c-102">スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする</span><span class="sxs-lookup"><span data-stu-id="0739c-102">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>
  <span data-ttu-id="0739c-103">この手順では、スクリプト タスクとスクリプト コンポーネントで使用するスクリプトに、ブレークポイントを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0739c-103">This procedure describes how to set breakpoints in the scripts that are used in the Script task and Script component.</span></span>  
  
 <span data-ttu-id="0739c-104">スクリプトにブレークポイントを設定すると、 **[ブレークポイントの設定 - \<object name>]** ダイアログ ボックスに、組み込みブレークポイントと共に、設定したブレークポイントの一覧が表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="0739c-104">After you set breakpoints in the script, the **Set Breakpoints - \<object name>** dialog box lists the breakpoints, along with the built-in breakpoints.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0739c-105">状況によっては、スクリプト タスクおよびスクリプト コンポーネント内のブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="0739c-105">Under certain circumstances, breakpoints in the Script task and Script component are ignored.</span></span> <span data-ttu-id="0739c-106">詳細については、「スクリプト[タスクのコーディングおよびデバッグ](../control-flow/script-task.md)」の「**スクリプトタスクのデバッグ**」および「スクリプトコンポーネントのコーディングと**デバッグ」 (** ../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="0739c-106">For more information, see the **Debugging the Script Task** section in [Coding and Debugging the Script Task](../control-flow/script-task.md) and the **Debugging the Script Component** section in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.</span></span>  
  
### <a name="to-set-a-breakpoint-in-script"></a><span data-ttu-id="0739c-107">スクリプトにブレークポイントを設定するには</span><span class="sxs-lookup"><span data-stu-id="0739c-107">To set a breakpoint in script</span></span>  
  
1.  <span data-ttu-id="0739c-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0739c-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="0739c-109">ブレークポイントを設定するスクリプトを含むパッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-109">Double-click the package that contains the script in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="0739c-110">スクリプト タスクを開くには、 **[制御フロー]** タブをクリックして、スクリプト タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-110">To open the Script task, click the **Control Flow** tab, and then double-click the Script task.</span></span>  
  
4.  <span data-ttu-id="0739c-111">スクリプト コンポーネントを開くには、 **[データ フロー]** タブをクリックして、スクリプト コンポーネントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-111">To open the Script component, click the **Data Flow** tab, and then double-click the Script component.</span></span>  
  
5.  <span data-ttu-id="0739c-112">**[スクリプト]** をクリックし、 **[スクリプトの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-112">Click **Script** and then click **Edit Script**.</span></span>  
  
6.  <span data-ttu-id="0739c-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) で、ブレークポイントを設定するスクリプト行を探して右クリックします。 **[ブレークポイント]** をポイントし、 **[ブレークポイントの挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-113">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA), locate the line of script on which you want to set a breakpoint, right-click that line, point to **Breakpoint**, and then click **Insert Breakpoint**.</span></span>  
  
     <span data-ttu-id="0739c-114">ブレークポイントを表すアイコンがコード行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0739c-114">The breakpoint icon appears on the line of code.</span></span>  
  
7.  <span data-ttu-id="0739c-115">**[ファイル]** メニューの **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-115">On the **File** menu, click **Exit**.</span></span>  
  
8.  <span data-ttu-id="0739c-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-116">Click **OK**.</span></span>  
  
9. <span data-ttu-id="0739c-117">パッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0739c-117">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
  
