---
title: バックアップ タイムライン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.POINTINTIMERESTORE.F1
- sql12.swb.backuptimeline.f1
helpviewer_keywords:
- Backup Timeline
ms.assetid: ae3565f2-ddb2-4469-a992-7531d4f9ebb8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b075f8c9ec32cfe483c64e34e9f9b4e4b6e80e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645690"
---
# <a name="backup-timeline"></a><span data-ttu-id="0ae5d-102">バックアップ タイムライン</span><span class="sxs-lookup"><span data-stu-id="0ae5d-102">Backup Timeline</span></span>
  <span data-ttu-id="0ae5d-103">**[バックアップ タイムライン]** ダイアログ ボックスを使用して、特定の時点のデータベースを復元するためのバックアップを検索および指定します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-103">Use the **Backup Timeline** dialog box to locate and specify backups to restore a database to a point-in-time.</span></span> <span data-ttu-id="0ae5d-104">**[バックアップのタイムライン]** ダイアログ ボックスにアクセスするには、 **[データベースの復元] ([全般] ページ)** ペイン上の **[タイムライン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-104">The **Backup Timeline** dialog box is accessed by clicking **Timeline** on the **Restore Database (General Page)** pane.</span></span> <span data-ttu-id="0ae5d-105">このダイアログ ボックスで、データベースで実行される復元操作のタイムラインを表示できます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-105">This dialog box allows you to view a timeline of the restore operations performed on the database.</span></span>  
  
 <span data-ttu-id="0ae5d-106">データベース復旧アドバイザーによって、特定の時点に復元するために必要なバックアップだけが選択されます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-106">The Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected.</span></span> <span data-ttu-id="0ae5d-107">これらの選択されたバックアップは、復元操作用として推奨される復元プランを示しています。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-107">These selected backups make up the recommended restore plan for your restore operation.</span></span> <span data-ttu-id="0ae5d-108">選択されたバックアップのみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-108">You should use only the selected backups.</span></span> <span data-ttu-id="0ae5d-109">データベースの復旧アドバイザーの詳細については、「[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-109">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
## <a name="restore-to"></a><span data-ttu-id="0ae5d-110">[復元先]</span><span class="sxs-lookup"><span data-stu-id="0ae5d-110">Restore to</span></span>  
 <span data-ttu-id="0ae5d-111">既定では、 **[最後に作成されたバックアップ]** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-111">**Last backup taken** is selected by default.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="0ae5d-112">データベースを復元するための適切なバックアップを選択し、最後のバックアップの時点のデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-112">will select the appropriate backups to restore the database, and will restore the database to the point of the last backup.</span></span> <span data-ttu-id="0ae5d-113">**[特定の日付と時刻]** をクリックすると、手動で日時を設定できます (特定の時点を選択します)。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-113">Click **A specific date and time** to manually set the date and time (selecting a specific point in time).</span></span>  
  
 <span data-ttu-id="0ae5d-114">**[特定の日付と時刻]** では、選択した特定の日時で復元を停止できます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-114">**Specific date and time** permits you stop the restore at a specific date and time that you select.</span></span> <span data-ttu-id="0ae5d-115">タイムラインは、選択された日時の 24 時間の範囲で行われたバックアップ操作を表示します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-115">The timeline shows a representation of the backup operations performed in the 24 hours around the select date and time.</span></span>  
  
 <span data-ttu-id="0ae5d-116">**Date**</span><span class="sxs-lookup"><span data-stu-id="0ae5d-116">**Date**</span></span>  
 <span data-ttu-id="0ae5d-117">日付を入力するか、ボックスの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-117">Enter or select a date from the drop-down list.</span></span>  
  
 <span data-ttu-id="0ae5d-118">**Time**</span><span class="sxs-lookup"><span data-stu-id="0ae5d-118">**Time**</span></span>  
 <span data-ttu-id="0ae5d-119">復元を停止する特定の時点を指定する日付を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-119">Enter or select a date to designate the specific point-in-time for the restore to stop.</span></span>  
  
 <span data-ttu-id="0ae5d-120">**[タイムラインの間隔]**</span><span class="sxs-lookup"><span data-stu-id="0ae5d-120">**Timeline Interval**</span></span>  
 <span data-ttu-id="0ae5d-121">タイムラインに表示される間隔の種類のオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-121">Displays the options for the interval types viewable on the timeline.</span></span>  
  
## <a name="timeline-and-legend"></a><span data-ttu-id="0ae5d-122">[タイムラインと凡例]</span><span class="sxs-lookup"><span data-stu-id="0ae5d-122">Timeline and Legend</span></span>  
 <span data-ttu-id="0ae5d-123">タイムラインの下にあるスクロール バーを使用して、タイムラインに沿ってカーソルを前後に移動させます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-123">Use the scroll bar beneath the timeline to move the cursor forward and backward along the timeline.</span></span> <span data-ttu-id="0ae5d-124">バックアップをクリックすると、そのバックアップの末尾にスクロール バーが移動します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-124">Click on a backup to move the scroll bar to the end of that backup.</span></span> <span data-ttu-id="0ae5d-125">マウス ポインターをマーカーに重ねると、選択されたバックアップ セットの情報が画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-125">Hover the mouse over a marker to display a ScreenTip providing information about the selected backup set.</span></span> <span data-ttu-id="0ae5d-126">バックアップの情報は、以下のマーカーによってタイムラインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-126">Backup information is shown on the timeline by the following markers.</span></span>  
  
 <span data-ttu-id="0ae5d-127">大きい三角形</span><span class="sxs-lookup"><span data-stu-id="0ae5d-127">Larger triangle</span></span>  
 <span data-ttu-id="0ae5d-128">データベースで実行された完全バックアップを表します。これは各完全バックアップが実行された特定の時点を示します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-128">Represents the full backups performed on the database, denoting the specific point in time each full backup was performed.</span></span>  
  
 <span data-ttu-id="0ae5d-129">小さい三角形</span><span class="sxs-lookup"><span data-stu-id="0ae5d-129">Smaller triangle</span></span>  
 <span data-ttu-id="0ae5d-130">データベースで実行された差分バックアップを表します。これは各差分バックアップが実行された特定の時点を示します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-130">Represents the differential backups performed on the database, denoting the specific point in time that each differential backup was performed.</span></span>  
  
 <span data-ttu-id="0ae5d-131">緑の影の部分</span><span class="sxs-lookup"><span data-stu-id="0ae5d-131">Green shaded areas</span></span>  
 <span data-ttu-id="0ae5d-132">トランザクション ログ バックアップの適用範囲を表します。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-132">Represents the transaction log backup coverage.</span></span>  
  
 <span data-ttu-id="0ae5d-133">赤色の線</span><span class="sxs-lookup"><span data-stu-id="0ae5d-133">Red line</span></span>  
 <span data-ttu-id="0ae5d-134">復元が可能なタイムライン上にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-134">Can only be positioned along the timeline where the restore is possible.</span></span> <span data-ttu-id="0ae5d-135">タイムライン上で赤色の線を動かすと、 **[日付]** および **[時刻]** ボックスに表示される日付と時刻が調整されます。</span><span class="sxs-lookup"><span data-stu-id="0ae5d-135">Moving the red line along the timeline adjusts the date and time displayed in the **Date** and **Time** boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae5d-136">参照</span><span class="sxs-lookup"><span data-stu-id="0ae5d-136">See Also</span></span>  
 <span data-ttu-id="0ae5d-137">[[データベースの復元] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="0ae5d-137">[Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
  
