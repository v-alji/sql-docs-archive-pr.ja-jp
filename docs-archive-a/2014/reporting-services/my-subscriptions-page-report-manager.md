---
title: '[個人用サブスクリプション] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 491a85a3-f323-4155-a0a8-de2779899995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 891796ec491b157f3c9bb5b4adfd15daedbc7c88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739517"
---
# <a name="my-subscriptions-page-report-manager"></a><span data-ttu-id="141be-102">[個人用サブスクリプション] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="141be-102">My Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="141be-103">[個人用サブスクリプション] ページでは、各自のサブスクリプションをすべて参照できます。</span><span class="sxs-lookup"><span data-stu-id="141be-103">Use the My Subscriptions page to view all of your subscriptions in one place.</span></span> <span data-ttu-id="141be-104">このページから所有している任意のサブスクリプションにアクセスし、サブスクリプションを変更または削除できます。</span><span class="sxs-lookup"><span data-stu-id="141be-104">From this page, you can access and modify or delete any subscription that you own.</span></span> <span data-ttu-id="141be-105">所有できるサブスクリプションは、自分で作成したサブスクリプションだけです。</span><span class="sxs-lookup"><span data-stu-id="141be-105">You own only the subscriptions that you create.</span></span> <span data-ttu-id="141be-106">他のユーザーのサブスクリプションにはアクセスできません。また、使用していても所有していないサブスクリプション (たとえば、他のユーザーが定義して、自分の名前が追加されている既存のサブスクリプション) にもアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="141be-106">You cannot access those of other users, nor can you access subscriptions that you use but do not own (for example, if your name has been added to an existing subscription defined by another user).</span></span> <span data-ttu-id="141be-107">また、このページからサブスクリプションを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="141be-107">You cannot create subscriptions from this page.</span></span> <span data-ttu-id="141be-108">サブスクリプションの作成の詳細については、[[新しいサブスクリプション] ページまたは [サブスクリプションの編集] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141be-108">For more information about creating subscriptions, see the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="141be-109">既定では、サブスクリプションはレポート名のアルファベット順に格納されます。</span><span class="sxs-lookup"><span data-stu-id="141be-109">By default, subscriptions are sorted in alphabetical order by report name.</span></span> <span data-ttu-id="141be-110">別の列見出しをクリックすると、サブスクリプションの格納方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="141be-110">Click a different column heading to change how subscriptions are sorted.</span></span> <span data-ttu-id="141be-111">サブスクリプションが存在しない場合、またはサブスクリプションを作成または管理する権限が無効の場合、このページにサブスクリプションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="141be-111">If you have no subscriptions or if permission to create or manage subscriptions is disabled, no subscriptions appear on the page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="141be-112">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="141be-112">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="141be-113">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="141be-113">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="141be-114">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="141be-114">Navigation</span></span>  
 <span data-ttu-id="141be-115">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="141be-115">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-my-subscriptions-page"></a><span data-ttu-id="141be-116">[個人用サブスクリプション] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="141be-116">To open the My Subscriptions page</span></span>  
  
1.  <span data-ttu-id="141be-117">レポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="141be-117">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="141be-118">ページの右上隅の [個人用サブスクリプション] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141be-118">At the top of the page, in the right-hand corner, click My Subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="141be-119">サブスクリプションを作成する権限がない場合でも、[個人用サブスクリプション] は常に有効です。</span><span class="sxs-lookup"><span data-stu-id="141be-119">My Subscriptions is always available, even if you lack permission to create subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="141be-120">Options</span><span class="sxs-lookup"><span data-stu-id="141be-120">Options</span></span>  
 <span data-ttu-id="141be-121">**削除**</span><span class="sxs-lookup"><span data-stu-id="141be-121">**Delete**</span></span>  
 <span data-ttu-id="141be-122">削除する各サブスクリプションの横にあるチェック ボックスをオンにして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141be-122">Select the check box next to each subscription that you want to delete and click **Delete**.</span></span>  
  
 <span data-ttu-id="141be-123">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="141be-123">**Edit**</span></span>  
 <span data-ttu-id="141be-124">説明を表示または編集する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="141be-124">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="141be-125">**Report**</span><span class="sxs-lookup"><span data-stu-id="141be-125">**Report**</span></span>  
 <span data-ttu-id="141be-126">サブスクリプションに指定されたレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="141be-126">Shows the report that is specified in the subscription.</span></span> <span data-ttu-id="141be-127">レポート名をクリックして、レポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="141be-127">Click the report name to view the report.</span></span>  
  
 <span data-ttu-id="141be-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="141be-128">**Description**</span></span>  
 <span data-ttu-id="141be-129">サブスクリプションの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="141be-129">Shows a description of the subscription.</span></span> <span data-ttu-id="141be-130">レポートのサブスクリプション情報を表示または編集するには、説明をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141be-130">Click the description to view or edit the subscription information for the report.</span></span>  
  
 <span data-ttu-id="141be-131">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="141be-131">**Folder**</span></span>  
 <span data-ttu-id="141be-132">サブスクリプションに指定されたレポートを含むフォルダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="141be-132">Shows the folder that contains the report that is specified in the subscription.</span></span> <span data-ttu-id="141be-133">フォルダーの内容を表示するには、フォルダー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="141be-133">Click the folder name to view the contents of the folder.</span></span>  
  
 <span data-ttu-id="141be-134">**トリガー**</span><span class="sxs-lookup"><span data-stu-id="141be-134">**Trigger**</span></span>  
 <span data-ttu-id="141be-135">サブスクリプションが実行される条件を表します。</span><span class="sxs-lookup"><span data-stu-id="141be-135">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="141be-136">**TimedSubscription** トリガーは、サブスクリプションを実行する日時を定義したスケジュールに基づいています。</span><span class="sxs-lookup"><span data-stu-id="141be-136">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="141be-137">**SnapshotUpdated** トリガーは、レポート スナップショットの更新に基づいています。</span><span class="sxs-lookup"><span data-stu-id="141be-137">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="141be-138">**[最終実行]**</span><span class="sxs-lookup"><span data-stu-id="141be-138">**Last Run**</span></span>  
 <span data-ttu-id="141be-139">サブスクリプションを処理した最終日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="141be-139">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="141be-140">**状態**</span><span class="sxs-lookup"><span data-stu-id="141be-140">**Status**</span></span>  
 <span data-ttu-id="141be-141">サブスクリプションの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="141be-141">Shows the status of the subscription.</span></span> <span data-ttu-id="141be-142">通常、状態値は "新規" か、サブスクリプションを最後に実行した日時です。</span><span class="sxs-lookup"><span data-stu-id="141be-142">Usually, the status value is either "New" or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="141be-143">"無効なデータ" の状態値は、既に無効となった暗号化された値 (つまり、レポートの実行に使用される保存された資格情報) へのポインターがサブスクリプションに含まれている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="141be-143">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="141be-144">データの暗号化および暗号化の解除に使用される対称キーがレポート サーバー上で再作成されると、既存の暗号化された値は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="141be-144">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="141be-145">サブスクリプションが非アクティブ化されている場合、そのサブスクリプションは処理できません。</span><span class="sxs-lookup"><span data-stu-id="141be-145">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="141be-146">サブスクリプションを更新し、操作可能な状態にするには、サブスクリプションを開いてから保存します。</span><span class="sxs-lookup"><span data-stu-id="141be-146">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141be-147">参照</span><span class="sxs-lookup"><span data-stu-id="141be-147">See Also</span></span>  
 <span data-ttu-id="141be-148">[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="141be-148">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="141be-149">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="141be-149">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
