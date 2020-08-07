---
title: '[サブスクリプション] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c67895babe99c92b7c09afd8cb75ca88d5cd7553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719430"
---
# <a name="subscriptions-page-report-manager"></a><span data-ttu-id="f05d7-102">[サブスクリプション] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="f05d7-102">Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="f05d7-103">[サブスクリプション] ページは、現在のレポートまたは共有データ ソースのサブスクリプションをすべて表示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-103">Use the Subscriptions page to list all of the subscriptions for the current report or shared data source.</span></span> <span data-ttu-id="f05d7-104">[すべてのサブスクリプションを管理] での指定により十分な権限を持っている場合、すべてのユーザーのサブスクリプションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-104">If you have sufficient permission (as conveyed by the "Manage all subscriptions" task), you can view the subscriptions of all users.</span></span> <span data-ttu-id="f05d7-105">それ以外の場合、このページには自分のサブスクリプションのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-105">Otherwise, this page shows only the subscriptions that you own.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f05d7-106">その他のページにもサブスクリプション情報は含まれています。</span><span class="sxs-lookup"><span data-stu-id="f05d7-106">Other pages also contain subscription information.</span></span> <span data-ttu-id="f05d7-107">詳細については、「 [[個人用サブスクリプション] ページ](../../2014/reporting-services/my-subscriptions-page-report-manager.md)」を参照して &#40;レポートマネージャー&#41;ですべてのサブスクリプションにアクセスするか、[[新しいサブスクリプション] ページまたは [サブスクリプションの編集] ページ &#40;レポートマネージャー](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)&#41;を使用してサブスクリプションを作成または編集します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-107">For more information, see [My Subscriptions Page &#40;Report Manager&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md) to access all your subscriptions in one place or the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) to create or edit a subscription.</span></span>  
  
 <span data-ttu-id="f05d7-108">一部のオプションは、既存のサブスクリプションを操作しているときにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-108">Some options are visible only if there are existing subscriptions to work with.</span></span> <span data-ttu-id="f05d7-109">サブスクリプションが定義されていない場合に、レポートからこのページを表示すると、 **[新しいサブスクリプション]** および **[新しいデータ ドリブン サブスクリプション]** 以外のオプションはこのページに表示されません。</span><span class="sxs-lookup"><span data-stu-id="f05d7-109">If no subscriptions are defined and you are accessing this page from a report, the **New Subscription** and **New Data-Driven Subscription** are the only options on the page.</span></span>  
  
 <span data-ttu-id="f05d7-110">新しいサブスクリプションを作成するには、保存されている資格情報がレポートのデータ ソースで使用されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-110">Before you can create a new subscription, you must verify that the report data source uses stored credentials.</span></span> <span data-ttu-id="f05d7-111">資格情報を保存するには [データ ソース] プロパティ ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-111">Use the Data Sources properties page to store credentials.</span></span> <span data-ttu-id="f05d7-112">詳細については、「[[データソース] プロパティページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f05d7-112">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f05d7-113">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f05d7-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f05d7-114">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f05d7-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="f05d7-115">［ナビゲーション］</span><span class="sxs-lookup"><span data-stu-id="f05d7-115">Navigation</span></span>  
 <span data-ttu-id="f05d7-116">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f05d7-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-subscriptions-page-for-report"></a><span data-ttu-id="f05d7-117">レポートの [サブスクリプション] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="f05d7-117">To open the Subscriptions page for report</span></span>  
  
1.  <span data-ttu-id="f05d7-118">レポート マネージャーを開き、サブスクリプションを表示または構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-118">Open Report Manager, and locate the report for which you want to view or configure a subscription.</span></span>  
  
2.  <span data-ttu-id="f05d7-119">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="f05d7-120">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-120">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="f05d7-121">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-121">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="f05d7-122">**[サブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-122">Select the **Subscriptions** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f05d7-123">オプション</span><span class="sxs-lookup"><span data-stu-id="f05d7-123">Options</span></span>  
 <span data-ttu-id="f05d7-124">**削除**</span><span class="sxs-lookup"><span data-stu-id="f05d7-124">**Delete**</span></span>  
 <span data-ttu-id="f05d7-125">サブスクリプションを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-125">Click to delete a subscription.</span></span> <span data-ttu-id="f05d7-126">削除する各サブスクリプションの隣のチェック ボックスをオンにしてから、サブスクリプションを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-126">Before you can delete a subscription, select the check box next to each subscription that you want to delete.</span></span>  
  
 <span data-ttu-id="f05d7-127">**新しいサブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="f05d7-127">**New Subscription**</span></span>  
 <span data-ttu-id="f05d7-128">現在のレポートの新しいサブスクリプションを作成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-128">Click to create a new subscription to the current report.</span></span> <span data-ttu-id="f05d7-129">保存されている資格情報がレポートで使用される場合または資格情報が使用されない場合に、このボタンは有効になります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-129">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="f05d7-130">共有データ ソースの [サブスクリプション] ページを開いた場合、このボタンは無効になります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-130">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="f05d7-131">**[新しいデータ ドリブン サブスクリプション]**</span><span class="sxs-lookup"><span data-stu-id="f05d7-131">**New Data-Driven Subscription**</span></span>  
 <span data-ttu-id="f05d7-132">情報を含むデータ ストアに対するコマンドやクエリから、サブスクライバーの一覧と配信オプションを生成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-132">Click to generate a subscriber list and delivery options from a command or query against a data store that contains this information.</span></span> <span data-ttu-id="f05d7-133">保存されている資格情報がレポートで使用される場合または資格情報が使用されない場合に、このボタンは有効になります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-133">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="f05d7-134">共有データ ソースの [サブスクリプション] ページを開いた場合、このボタンは無効になります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-134">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="f05d7-135">**編集**</span><span class="sxs-lookup"><span data-stu-id="f05d7-135">**Edit**</span></span>  
 <span data-ttu-id="f05d7-136">説明を表示または編集する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f05d7-136">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="f05d7-137">**Report**</span><span class="sxs-lookup"><span data-stu-id="f05d7-137">**Report**</span></span>  
 <span data-ttu-id="f05d7-138">共有データ ソースからこのページを開くと、この列でサブスクリプションが定義されているレポートが識別されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-138">When you open this page from a shared data source, this column identifies the report for which the subscription is defined.</span></span> <span data-ttu-id="f05d7-139">**[フォルダー]** 列ではレポートの場所が識別されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-139">The **Folder** column identifies the location of the report.</span></span>  
  
 <span data-ttu-id="f05d7-140">**説明**</span><span class="sxs-lookup"><span data-stu-id="f05d7-140">**Description**</span></span>  
 <span data-ttu-id="f05d7-141">サブスクリプションの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-141">Shows a description of the subscription.</span></span>  
  
 <span data-ttu-id="f05d7-142">**トリガー**</span><span class="sxs-lookup"><span data-stu-id="f05d7-142">**Trigger**</span></span>  
 <span data-ttu-id="f05d7-143">サブスクリプションが実行される条件を表します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-143">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="f05d7-144">**TimedSubscription** トリガーは、サブスクリプションを実行する日時を定義したスケジュールに基づいています。</span><span class="sxs-lookup"><span data-stu-id="f05d7-144">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="f05d7-145">**SnapshotUpdated** トリガーは、レポート スナップショットの更新に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f05d7-145">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="f05d7-146">**所有者**</span><span class="sxs-lookup"><span data-stu-id="f05d7-146">**Owner**</span></span>  
 <span data-ttu-id="f05d7-147">サブスクリプションを作成したユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-147">Shows the name of the user who created the subscription.</span></span>  
  
 <span data-ttu-id="f05d7-148">**[最終実行]**</span><span class="sxs-lookup"><span data-stu-id="f05d7-148">**Last Run**</span></span>  
 <span data-ttu-id="f05d7-149">サブスクリプションを処理した最終日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-149">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="f05d7-150">**状態**</span><span class="sxs-lookup"><span data-stu-id="f05d7-150">**Status**</span></span>  
 <span data-ttu-id="f05d7-151">サブスクリプションの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f05d7-151">Shows the status of the subscription.</span></span> <span data-ttu-id="f05d7-152">通常、状態値は "新規" またはサブスクリプションが最後に実行された日時のいずれかとなります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-152">Usually, the status value is either New or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="f05d7-153">"無効なデータ" の状態値は、既に無効となった暗号化された値 (つまり、レポートの実行に使用される保存された資格情報) へのポインターがサブスクリプションに含まれている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-153">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="f05d7-154">データの暗号化および暗号化の解除に使用される対称キーがレポート サーバー上で再作成されると、既存の暗号化された値は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f05d7-154">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="f05d7-155">サブスクリプションが非アクティブ化されている場合、そのサブスクリプションは処理できません。</span><span class="sxs-lookup"><span data-stu-id="f05d7-155">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="f05d7-156">サブスクリプションを更新し、操作可能な状態にするには、サブスクリプションを開いてから保存します。</span><span class="sxs-lookup"><span data-stu-id="f05d7-156">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05d7-157">参照</span><span class="sxs-lookup"><span data-stu-id="f05d7-157">See Also</span></span>  
 <span data-ttu-id="f05d7-158">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f05d7-158">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f05d7-159">[ネイティブモードで Reporting Services &#40;標準のサブスクリプションを作成、変更、および削除&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="f05d7-159">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="f05d7-160">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="f05d7-160">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="f05d7-161">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="f05d7-161">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
