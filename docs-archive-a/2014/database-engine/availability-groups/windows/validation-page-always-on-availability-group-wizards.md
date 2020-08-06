---
title: '[検証] ページ (AlwaysOn 可用性グループウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2010074a357932f8af7358a05ee6ed16f5c0881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632120"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a><span data-ttu-id="88a97-102">[検証] ページ (AlwaysOn 可用性グループ ウィザード)</span><span class="sxs-lookup"><span data-stu-id="88a97-102">Validation Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="88a97-103">このヘルプ トピックでは、 **[検証]** ページのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="88a97-103">This help topic describes the options of the **Validation** page.</span></span> <span data-ttu-id="88a97-104">このトピックの対象は、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]の [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]、 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 、および [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="88a97-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="88a97-105">このページでは、ウィザードのこれまでのページで選択したすべての構成が、使用している環境でサポートされているかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="88a97-105">Use this page to validate that your environment supports all the configuration choices you made on previous pages of the wizard.</span></span>  
  
##  <a name="validation-page-options"></a><a name="PageOptions"></a><span data-ttu-id="88a97-106">[検証] ページのオプション</span><span class="sxs-lookup"><span data-stu-id="88a97-106">Validation Page Options</span></span>  
 <span data-ttu-id="88a97-107">**[可用性グループの検証の結果。]**</span><span class="sxs-lookup"><span data-stu-id="88a97-107">**Results of availability group validation.**</span></span>  
 <span data-ttu-id="88a97-108">このグリッドでは、完了した検証手順ごとの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="88a97-108">This grid displays the results of each completed validation step.</span></span> <span data-ttu-id="88a97-109">グリッドの列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="88a97-109">The grid columns are as follows:</span></span>  
  
 <span data-ttu-id="88a97-110">**名前**</span><span class="sxs-lookup"><span data-stu-id="88a97-110">**Name**</span></span>  
 <span data-ttu-id="88a97-111">各手順についての説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="88a97-111">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="88a97-112">**結果**</span><span class="sxs-lookup"><span data-stu-id="88a97-112">**Result**</span></span>  
 <span data-ttu-id="88a97-113">以下のハイパーリンク テキストのいずれかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="88a97-113">Displays one of the following hyperlink texts.</span></span> <span data-ttu-id="88a97-114">特定の検証手順の結果の詳細については、ハイパーリンクをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="88a97-114">For more information about the result of given validation step, click the hyperlink.</span></span>  
  
|<span data-ttu-id="88a97-115">結果</span><span class="sxs-lookup"><span data-stu-id="88a97-115">Result</span></span>|<span data-ttu-id="88a97-116">説明</span><span class="sxs-lookup"><span data-stu-id="88a97-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="88a97-117">**エラー**</span><span class="sxs-lookup"><span data-stu-id="88a97-117">**Error**</span></span>|<span data-ttu-id="88a97-118">検証手順が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88a97-118">Indicates that the validation step failed.</span></span> <span data-ttu-id="88a97-119">エラー メッセージを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="88a97-119">Click the link to view the error message.</span></span>|  
|<span data-ttu-id="88a97-120">**Skipped**</span><span class="sxs-lookup"><span data-stu-id="88a97-120">**Skipped**</span></span>|<span data-ttu-id="88a97-121">不要と指定されていたため、検証手順がスキップされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="88a97-121">Indicates that the validation step was skipped because it is not required by your selections.</span></span> <span data-ttu-id="88a97-122">手順がスキップされた理由を表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="88a97-122">Click the link to view the reason that a step was skipped.</span></span>|  
|<span data-ttu-id="88a97-123">**Success**</span><span class="sxs-lookup"><span data-stu-id="88a97-123">**Success**</span></span>|<span data-ttu-id="88a97-124">検証手順が正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88a97-124">Indicates that the validation step completed successfully</span></span>|  
|<span data-ttu-id="88a97-125">**警告**</span><span class="sxs-lookup"><span data-stu-id="88a97-125">**Warning**</span></span>|<span data-ttu-id="88a97-126">可用性グループの構成に関する潜在的な問題を示します。</span><span class="sxs-lookup"><span data-stu-id="88a97-126">Indicates a potential issue with the availability group configuration.</span></span>  <span data-ttu-id="88a97-127">警告メッセージを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="88a97-127">Click the link to view the warning message.</span></span>|  
  
 <span data-ttu-id="88a97-128">**[検証の再実行]**</span><span class="sxs-lookup"><span data-stu-id="88a97-128">**Re-run Validation**</span></span>  
 <span data-ttu-id="88a97-129">検証エラーに対応して、ウィザードの外部で変更を行った場合に、検証手順を繰り返すときにクリックします。</span><span class="sxs-lookup"><span data-stu-id="88a97-129">Click to repeat the validation steps if you make a change outside of the wizard in response to a validation error.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="88a97-130">関連タスク</span><span class="sxs-lookup"><span data-stu-id="88a97-130">Related Tasks</span></span>  
  
-   <span data-ttu-id="88a97-131">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="88a97-131">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="88a97-132">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="88a97-132">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="88a97-133">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="88a97-133">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="88a97-134">参照</span><span class="sxs-lookup"><span data-stu-id="88a97-134">See Also</span></span>  
 [<span data-ttu-id="88a97-135">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="88a97-135">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
