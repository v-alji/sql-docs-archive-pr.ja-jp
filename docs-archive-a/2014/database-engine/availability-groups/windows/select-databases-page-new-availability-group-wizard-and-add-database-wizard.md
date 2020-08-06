---
title: '[データベースの選択] ページ (新しい可用性グループウィザード-データベース追加ウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c626b8f0953f18a6dd4661124a09b7f542caeb82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740476"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a><span data-ttu-id="56036-102">[データベースの選択] ページ (新しい可用性グループウィザード-データベース追加ウィザード)</span><span class="sxs-lookup"><span data-stu-id="56036-102">Select Databases Page (New Availability Group Wizard-Add Database Wizard)</span></span>
  <span data-ttu-id="56036-103"> このヘルプ トピックでは、**[データベースの指定]** ページのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="56036-103">This help topic describes the options of the **Specify Databases** page.</span></span> <span data-ttu-id="56036-104">このトピックの対象は、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] の [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] と [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="56036-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="select-databases-options"></a><a name="PageOptions"></a> <span data-ttu-id="56036-105">データベース オプションの選択</span><span class="sxs-lookup"><span data-stu-id="56036-105">Select Databases Options</span></span>  
 <span data-ttu-id="56036-106">**[この SQL Server のインスタンス上のユーザー データベース]** グリッドには、すべてのローカル ユーザー データベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56036-106">The **User databases on this instance of SQL Server** grid lists every local user database.</span></span> <span data-ttu-id="56036-107">次の列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="56036-107">The columns are as follows:</span></span>  
  
 <span data-ttu-id="56036-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="56036-108">**Name**</span></span>  
 <span data-ttu-id="56036-109">ローカル ユーザー データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56036-109">Displays the name of a local user database.</span></span>  
  
 <span data-ttu-id="56036-110">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="56036-110">**Size**</span></span>  
 <span data-ttu-id="56036-111">データベースのサイズが表示されます (サイズをウィザードで使用できる場合)。</span><span class="sxs-lookup"><span data-stu-id="56036-111">Displays the database size, if the size is available to the wizard.</span></span>  
  
 <span data-ttu-id="56036-112">**状態**</span><span class="sxs-lookup"><span data-stu-id="56036-112">**Status**</span></span>  
 <span data-ttu-id="56036-113">可用性グループに追加するための前提条件を特定のデータベースが満たしているかどうかを示すハイパーリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56036-113">Displays a hyperlink whose text that indicates whether a given database meets the prerequisites for being added to an availability group.</span></span> <span data-ttu-id="56036-114">状態が **[前提条件を満たしています]** の場合、データベースを可用性グループに追加できます。</span><span class="sxs-lookup"><span data-stu-id="56036-114">If the status is "**Meets prerequisites**" you can add the database to the availability group.</span></span> <span data-ttu-id="56036-115">データベースが一部の前提条件を満たしていない場合は、 **[状態]** ハイパーリンクにデータベースが不適格である理由が簡潔に示されます。</span><span class="sxs-lookup"><span data-stu-id="56036-115">If a database does not meet all of the prerequisites, the **Status** hyperlink provides a brief explanation of why the database is ineligible.</span></span> <span data-ttu-id="56036-116">詳細については、ハイパーリンクをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="56036-116">For more information, click the hyperlink.</span></span>  
  
 <span data-ttu-id="56036-117">前提条件を満たすためにデータベースを操作したままで、 **[データベースの選択]** ページでウィザードを終了できます。</span><span class="sxs-lookup"><span data-stu-id="56036-117">You can leave the wizard on the **Select Database** page while you take action on a database to meet a prerequisite.</span></span> <span data-ttu-id="56036-118">**[データベースの選択]** ページに戻ったら、 **[最新の情報に更新]** をクリックしてグリッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="56036-118">When you return to the **Select Databases** page, click **Refresh** to update the grid.</span></span>  
  
 <span data-ttu-id="56036-119">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="56036-119">**Refresh**</span></span>  
 <span data-ttu-id="56036-120">クリックしてグリッドを最新の情報に更新します。</span><span class="sxs-lookup"><span data-stu-id="56036-120">Click to refresh the grid.</span></span> <span data-ttu-id="56036-121">前提条件を満たすためにデータベースを操作した後で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="56036-121">This is useful after you take action on a database to meet a prerequisite.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="56036-122">関連タスク</span><span class="sxs-lookup"><span data-stu-id="56036-122">Related Tasks</span></span>  
  
-   <span data-ttu-id="56036-123">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="56036-123">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="56036-124">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="56036-124">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="56036-125">参照</span><span class="sxs-lookup"><span data-stu-id="56036-125">See Also</span></span>  
 <span data-ttu-id="56036-126">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56036-126">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="56036-127">AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;</span><span class="sxs-lookup"><span data-stu-id="56036-127">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
