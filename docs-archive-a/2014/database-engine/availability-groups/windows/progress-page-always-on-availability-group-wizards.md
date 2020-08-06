---
title: '[進行状況] ページ (AlwaysOn 可用性グループウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.progress.f1
- sql12.swb.newagwizard.progress.f1
- sql11.swb.failoverwizard.progress.f1
- sql11.swb.adddatabasewizard.progress.f1
- sql11.swb.addreplicawizard.progress.f1
- sql11.swb.newagwizard.progress.f1
- sql12.swb.adddatabasewizard.progress.f1
- sql12.swb.failoverwixard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7de8df6906d930215d71a0adc562bd7cef961ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740494"
---
# <a name="progress-page-alwayson-availability-group-wizards"></a><span data-ttu-id="b84de-102">[進行状況] ページ (AlwaysOn 可用性グループ ウィザード)</span><span class="sxs-lookup"><span data-stu-id="b84de-102">Progress Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="b84de-103">このダイアログ ボックスを使用すると、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で実行中の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]ウィザードの進行状況を表示できます。</span><span class="sxs-lookup"><span data-stu-id="b84de-103">Use this dialog box to view the progress of a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard that you are running in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b84de-104">進行状況バーには、ウィザードが実行している手順の相対的な進行状況が示されます。</span><span class="sxs-lookup"><span data-stu-id="b84de-104">The progress bar indicates the relative progress of the steps that the wizard is performing.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b84de-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="b84de-105">UI element list</span></span>  
 <span data-ttu-id="b84de-106">**[詳細]**</span><span class="sxs-lookup"><span data-stu-id="b84de-106">**More details**</span></span>  
 <span data-ttu-id="b84de-107">下矢印をクリックすると、完了した手順を順に示す一覧と現在進行中の操作が進行状況グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b84de-107">Click the down arrow to display a progress grid that lists any completed steps, in order, followed by the current in-progress operation.</span></span> <span data-ttu-id="b84de-108">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b84de-108">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="b84de-109">**名前**</span><span class="sxs-lookup"><span data-stu-id="b84de-109">**Name**</span></span>  
 <span data-ttu-id="b84de-110">各手順についての説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b84de-110">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="b84de-111">**状態**</span><span class="sxs-lookup"><span data-stu-id="b84de-111">**Status**</span></span>  
 <span data-ttu-id="b84de-112">完了した手順の結果と、現在の手順の完了の割合を次のように示します。</span><span class="sxs-lookup"><span data-stu-id="b84de-112">Indicates the outcome of completed steps and the percentage of completion of the current step, as follows:</span></span>  
  
|<span data-ttu-id="b84de-113">結果</span><span class="sxs-lookup"><span data-stu-id="b84de-113">Result</span></span>|<span data-ttu-id="b84de-114">説明</span><span class="sxs-lookup"><span data-stu-id="b84de-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b84de-115">**Error**</span><span class="sxs-lookup"><span data-stu-id="b84de-115">**Error**</span></span>|<span data-ttu-id="b84de-116">この手順の操作がエラーになったことを示します。</span><span class="sxs-lookup"><span data-stu-id="b84de-116">Indicates the operation for this step experienced an error.</span></span> <span data-ttu-id="b84de-117">リンクをクリックすると、エラーを説明するメッセージ ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b84de-117">Click the link to display a message dialog box that describes the error.</span></span>|  
|<span data-ttu-id="b84de-118">**実行中 (** "*完了率*" **)**</span><span class="sxs-lookup"><span data-stu-id="b84de-118">**In Progress (** *percentage-completed* **)**</span></span>|<span data-ttu-id="b84de-119">操作が現在実行中であることを示し、この手順の進行状況をパーセンテージで示します。</span><span class="sxs-lookup"><span data-stu-id="b84de-119">Indicates that the operation is occurring now and estimates the percentage of this step that has completed.</span></span>|  
|<span data-ttu-id="b84de-120">**Success**</span><span class="sxs-lookup"><span data-stu-id="b84de-120">**Success**</span></span>|<span data-ttu-id="b84de-121">この手順の操作が正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="b84de-121">Indicates the operation for this step completed successfully.</span></span>|  
  
 <span data-ttu-id="b84de-122">**[詳細の非表示]**</span><span class="sxs-lookup"><span data-stu-id="b84de-122">**Fewer Details**</span></span>  
 <span data-ttu-id="b84de-123">進行状況グリッドを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="b84de-123">Click to hide the progress grid.</span></span>  
  
 <span data-ttu-id="b84de-124">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="b84de-124">**Cancel**</span></span>  
 <span data-ttu-id="b84de-125">残りのすべての操作をスキップして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="b84de-125">Click to skip any remaining operations and then exit the wizard.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b84de-126">関連タスク</span><span class="sxs-lookup"><span data-stu-id="b84de-126">Related Tasks</span></span>  
  
-   <span data-ttu-id="b84de-127">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="b84de-127">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="b84de-128">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b84de-128">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="b84de-129">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b84de-129">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="b84de-130">可用性グループのフェールオーバー ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b84de-130">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="b84de-131">参照</span><span class="sxs-lookup"><span data-stu-id="b84de-131">See Also</span></span>  
 [<span data-ttu-id="b84de-132">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="b84de-132">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
