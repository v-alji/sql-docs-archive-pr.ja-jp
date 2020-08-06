---
title: '[スケジュール] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ef19d96e-9f00-4434-950e-152dda9c1ced
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e31bc25473aad23ecd2654f74ee3e837e65b65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634837"
---
# <a name="schedules-page-report-manager"></a><span data-ttu-id="92cb5-102">[スケジュール] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="92cb5-102">Schedules Page (Report Manager)</span></span>
  <span data-ttu-id="92cb5-103">[スケジュール] ページでは、共有スケジュールを作成、変更、削除、一時停止、または再開できます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-103">Use the Schedules page to create, modify, delete, pause, or resume shared schedules.</span></span> <span data-ttu-id="92cb5-104">共有スケジュールとは、レポート、サブスクリプション、およびスケジュール情報を利用するその他のプロセスとは別に作成および管理できる名前付きのスケジュールです。</span><span class="sxs-lookup"><span data-stu-id="92cb5-104">A shared schedule is a named schedule that you can create and manage separately from reports, subscriptions, and other processes that consume schedule information.</span></span> <span data-ttu-id="92cb5-105">追加した共有スケジュールは、全ユーザーが選択できます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-105">Users can select shared schedules that you provide.</span></span>  
  
 <span data-ttu-id="92cb5-106">共有スケジュールを削除、一時停止、または再開するには、該当する共有スケジュールの横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-106">To delete, pause, or resume a shared schedule, select the check box next to the shared schedule that you want to modify.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92cb5-107">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="92cb5-107">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="92cb5-108">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92cb5-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="92cb5-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="92cb5-109">Navigation</span></span>  
 <span data-ttu-id="92cb5-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="92cb5-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-schedules-page"></a><span data-ttu-id="92cb5-111">[スケジュール] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="92cb5-111">To open the Schedules page</span></span>  
  
1.  <span data-ttu-id="92cb5-112">レポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-112">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="92cb5-113">ページの右上隅の **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-113">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="92cb5-114">この操作により、サイトの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-114">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="92cb5-115">**[スケジュール]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-115">Select the **Schedules** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="92cb5-116">Options</span><span class="sxs-lookup"><span data-stu-id="92cb5-116">Options</span></span>  
 <span data-ttu-id="92cb5-117">**新しいスケジュール**</span><span class="sxs-lookup"><span data-stu-id="92cb5-117">**New Schedule**</span></span>  
 <span data-ttu-id="92cb5-118">クリックすると、[スケジュール] ページが開きます。このページは、頻度に関する情報の指定に使用します。</span><span class="sxs-lookup"><span data-stu-id="92cb5-118">Click to open the Scheduling page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="92cb5-119">**削除**</span><span class="sxs-lookup"><span data-stu-id="92cb5-119">**Delete**</span></span>  
 <span data-ttu-id="92cb5-120">共有スケジュールを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-120">Click to remove a shared schedule.</span></span>  
  
 <span data-ttu-id="92cb5-121">**一時停止**</span><span class="sxs-lookup"><span data-stu-id="92cb5-121">**Pause**</span></span>  
 <span data-ttu-id="92cb5-122">共有スケジュールの実行を一時的に停止する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-122">Click to stop a shared schedule from running temporarily.</span></span> <span data-ttu-id="92cb5-123">スケジュールを一時停止することで、サブスクリプションおよびスケジュール設定されているその他の処理が実行されなくなります。</span><span class="sxs-lookup"><span data-stu-id="92cb5-123">Pausing a schedule prevents subscriptions and other scheduled processes from running.</span></span>  
  
 <span data-ttu-id="92cb5-124">**再開**</span><span class="sxs-lookup"><span data-stu-id="92cb5-124">**Resume**</span></span>  
 <span data-ttu-id="92cb5-125">共有スケジュールを再度設定する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-125">Click to reinstate a shared schedule.</span></span> <span data-ttu-id="92cb5-126">スケジュールを一時停止している間に実行される予定だった無効になった処理は、破棄されます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-126">Lapsed processes that were scheduled to run while the schedule was paused are not made up.</span></span>  
  
 <span data-ttu-id="92cb5-127">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="92cb5-127">**Schedule**</span></span>  
 <span data-ttu-id="92cb5-128">現在定義されている共有スケジュールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-128">Shows the shared schedules that are currently defined.</span></span> <span data-ttu-id="92cb5-129">頻度に関する情報を表示または編集するには、共有スケジュールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="92cb5-129">Click a shared schedule to view or edit frequency information.</span></span>  
  
 <span data-ttu-id="92cb5-130">**Creator**</span><span class="sxs-lookup"><span data-stu-id="92cb5-130">**Creator**</span></span>  
 <span data-ttu-id="92cb5-131">共有スケジュールを作成したユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-131">Shows the name of the user who created the shared schedule.</span></span>  
  
 <span data-ttu-id="92cb5-132">**[最終実行]、[次の実行]**</span><span class="sxs-lookup"><span data-stu-id="92cb5-132">**Last Run, Next Run**</span></span>  
 <span data-ttu-id="92cb5-133">共有スケジュールが最後に実行された日時と、次に実行される日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-133">Shows when the shared schedule was last run and when it will run next.</span></span>  
  
 <span data-ttu-id="92cb5-134">**状態**</span><span class="sxs-lookup"><span data-stu-id="92cb5-134">**Status**</span></span>  
 <span data-ttu-id="92cb5-135">共有スケジュールが一時停止されているか、稼動中かが表示されます。</span><span class="sxs-lookup"><span data-stu-id="92cb5-135">Shows whether a shared schedule is paused or active.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cb5-136">参照</span><span class="sxs-lookup"><span data-stu-id="92cb5-136">See Also</span></span>  
 <span data-ttu-id="92cb5-137">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="92cb5-137">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="92cb5-138">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="92cb5-138">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
