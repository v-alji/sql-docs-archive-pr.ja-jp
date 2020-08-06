---
title: タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21e334faff95e63e59bbf9c40fdf7e479de949da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633223"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a><span data-ttu-id="872e6-102">タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする</span><span class="sxs-lookup"><span data-stu-id="872e6-102">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>
  <span data-ttu-id="872e6-103">この手順では、パッケージ、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーにブレークポイントを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="872e6-103">This procedure describes how to set breakpoints in a package, a task, a For Loop container, a Foreach Loop container, or a Sequence container.</span></span>  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a><span data-ttu-id="872e6-104">パッケージ、タスク、またはコンテナーにブレークポイントを設定するには</span><span class="sxs-lookup"><span data-stu-id="872e6-104">To set breakpoints in a package, a task, or a container</span></span>  
  
1.  <span data-ttu-id="872e6-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="872e6-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="872e6-106">ブレークポイントを設定するパッケージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="872e6-106">Double-click the package in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="872e6-107">SSIS デザイナーで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="872e6-107">In SSIS Designer, do the following:</span></span>  
  
    -   <span data-ttu-id="872e6-108">パッケージ オブジェクトにブレークポイントを設定するには、 **[制御フロー]** タブをクリックし、デザイン画面の背景の任意の場所にカーソルを置いて右クリックし、 **[ブレークポイントの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="872e6-108">To set breakpoints in the package object, click the **Control Flow** tab, place the cursor anywhere on the background of the design surface, right-click, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="872e6-109">パッケージ制御フローにブレークポイントを設定するには、 **[制御フロー]** タブをクリックし、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーを右クリックし、 **[ブレークポイントの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="872e6-109">To set breakpoints in a package control flow, click the **Control Flow** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="872e6-110">イベント ハンドラーにブレークポイントを設定するには、 **[イベント ハンドラー]** タブをクリックし、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーを右クリックし、 **[ブレークポイントの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="872e6-110">To set breakpoints in an event handler, click the **Event Handler** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
4.  <span data-ttu-id="872e6-111">**[ブレークポイント \<container name> の設定]** ダイアログ ボックスで、有効にするブレークポイントを選択します。</span><span class="sxs-lookup"><span data-stu-id="872e6-111">In the **Set Breakpoints \<container name>** dialog box, select the breakpoints to enable.</span></span>  
  
5.  <span data-ttu-id="872e6-112">必要に応じて、各ブレークポイントのヒット カウントの種類とヒット カウント数を変更します。</span><span class="sxs-lookup"><span data-stu-id="872e6-112">Optionally, modify the hit count type and the hit count number for each breakpoint.</span></span>  
  
6.  <span data-ttu-id="872e6-113">パッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="872e6-113">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872e6-114">参照</span><span class="sxs-lookup"><span data-stu-id="872e6-114">See Also</span></span>  
 <span data-ttu-id="872e6-115">[パッケージ開発のトラブルシューティング ツール](troubleshooting/troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="872e6-115">[Troubleshooting Tools for Package Development](troubleshooting/troubleshooting-tools-for-package-development.md) </span></span>  
 <span data-ttu-id="872e6-116">[スクリプトタスクとスクリプトコンポーネントにブレークポイントを設定してスクリプトをデバッグする](data-flow/transformations/script-component.md) </span><span class="sxs-lookup"><span data-stu-id="872e6-116">[Debug a Script by Setting Breakpoints in a Script Task and Script Component](data-flow/transformations/script-component.md) </span></span>  
 <span data-ttu-id="872e6-117">[スクリプトタスクのコーディングおよびデバッグ](control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="872e6-117">[Coding and Debugging the Script Task](control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="872e6-118">スクリプト コンポーネントのコーディングおよびデバッグ</span><span class="sxs-lookup"><span data-stu-id="872e6-118">Coding and Debugging the Script Component</span></span>](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
