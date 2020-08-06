---
title: 変更されたファイルの一覧を表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckinWindow
helpviewer_keywords:
- listing modified files
- modified files list [SQL Server]
- checking in files
ms.assetid: 1b053719-8500-4300-a169-fffca5801dd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2899ab9889908089d17b3c929e7bf4b2dfe2185
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643467"
---
# <a name="view-a-list-of-modified-files"></a><span data-ttu-id="9d4d9-102">変更されたファイルの一覧表示</span><span class="sxs-lookup"><span data-stu-id="9d4d9-102">View a List of Modified Files</span></span>
  <span data-ttu-id="9d4d9-103">[**保留中のチェックイン**] ウィンドウを使用すると、現在のソリューションでチェックアウトされているファイルの一覧を常に表示したり、1回のボタンクリックでこれらのファイルをチェックインしたりできます。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-103">You can use the **Pending Checkins** window to display at all times a list of the checked-out files in the current solution, and to check in these files with a single button click.</span></span>  
  
### <a name="to-view-a-list-of-modified-files"></a><span data-ttu-id="9d4d9-104">変更されたファイルの一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="9d4d9-104">To view a list of modified files</span></span>  
  
1.  <span data-ttu-id="9d4d9-105">[**表示**] メニューの [**保留中のチェックイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-105">On the **View** menu, click **Pending Checkins**.</span></span>  
  
2.  <span data-ttu-id="9d4d9-106">選択したファイルをチェックインするには、[**チェックイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-106">To check in the selected files, click **Check In**.</span></span> <span data-ttu-id="9d4d9-107">または、[**保留中のチェックイン**] ウィンドウを環境の右側にドッキングして、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 作業が終了したときにファイルをチェックインできるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-107">Alternatively, you can dock the **Pending Checkins** window on the right side of the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment so that you can check in the files when you are finished working.</span></span>  
  
     <span data-ttu-id="9d4d9-108">**チェックイン**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-108">**Check In**</span></span>  
     <span data-ttu-id="9d4d9-109">ソリューションにチェックインします。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-109">Checks in the solution.</span></span>  
  
     <span data-ttu-id="9d4d9-110">**コメント**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-110">**Comments**</span></span>  
     <span data-ttu-id="9d4d9-111">プレーンテキスト コメントを保留中のチェックインに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-111">Associates a plain text comment with the pending check in.</span></span> <span data-ttu-id="9d4d9-112">コメントが作成され、プロジェクトの各バージョンに関連付けられ、ソース管理データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-112">A comment is created and associated with each version of a project, and stored in the source control database.</span></span>  
  
     <span data-ttu-id="9d4d9-113">**Options**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-113">**Options**</span></span>  
     <span data-ttu-id="9d4d9-114">[**チェックイン**] ボタンをクリックしたときにソース管理で実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-114">Specifies the actions that source control should take when you click the **Check In** button.</span></span>  
  
    -   <span data-ttu-id="9d4d9-115">**[すべてのチェックアウト状態を保持]**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-115">**Keep All Checked Out**</span></span>  
  
         <span data-ttu-id="9d4d9-116">ファイルをチェックアウトした状態のままで、変更がソース管理プロバイダーに書き込まれるように指定します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-116">Specifies that your changes should be written to the source control provider but that the files should remain checked out.</span></span>  
  
     <span data-ttu-id="9d4d9-117">**Sort**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-117">**Sort**</span></span>  
     <span data-ttu-id="9d4d9-118">アイテムの一覧に表示された列の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-118">Specifies the sort order for the columns displayed in the Items list.</span></span>  
  
     <span data-ttu-id="9d4d9-119">**[列]**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-119">**Columns**</span></span>  
     <span data-ttu-id="9d4d9-120">ウィンドウのアイテムの一覧に追加できる列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-120">Displays a list of the columns you can add to the window's Items list.</span></span>  
  
     <span data-ttu-id="9d4d9-121">**ツリービュー**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-121">**Tree View**</span></span>  
     <span data-ttu-id="9d4d9-122">チェックインするソリューションまたはプロジェクトのフォルダーおよびファイルの階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-122">Displays the folder and file hierarchy for the solution or project you are checking in.</span></span>  
  
     <span data-ttu-id="9d4d9-123">**[平面表示]**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-123">**Flat View**</span></span>  
     <span data-ttu-id="9d4d9-124">ソース管理接続の下にあるフラットリストとしてチェックインしているファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-124">Displays the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="9d4d9-125">**[バージョンの比較]**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-125">**Compare Versions**</span></span>  
     <span data-ttu-id="9d4d9-126">[Visual SourceSafe の**相違点のオプション**] ダイアログボックスを開きます。このダイアログボックスでは、開発環境プロジェクト内の選択したファイルを選択した他のファイルと比較し、相違がある場合はその相違点を表示します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-126">Opens the Visual SourceSafe **Difference Options** dialog box, which compares a selected file in your development environment project to any other selected file and shows you the differences, if any.</span></span>  
  
     <span data-ttu-id="9d4d9-127">**チェックアウトを元に戻す**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-127">**Undo checkout**</span></span>  
     <span data-ttu-id="9d4d9-128">[**保留中のチェックイン**] ウィンドウで選択したすべての項目のチェックアウトを元に戻します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-128">Reverses the checkout of all items selected in the **Pending Checkins** window.</span></span>  
  
     <span data-ttu-id="9d4d9-129">**名前**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-129">**Name**</span></span>  
     <span data-ttu-id="9d4d9-130">チェックインに利用可能なアイテムの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-130">Displays a list of the items available for check in.</span></span> <span data-ttu-id="9d4d9-131">項目の横に、オン状態のチェック ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-131">Items appear with the check box next to them selected.</span></span> <span data-ttu-id="9d4d9-132">チェックインしないアイテムがある場合は、対象アイテムの横のチェック ボックスをオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="9d4d9-132">If you do not want to check in a particular item, clear the check box next to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4d9-133">参照</span><span class="sxs-lookup"><span data-stu-id="9d4d9-133">See Also</span></span>  
 <span data-ttu-id="9d4d9-134">[チェックインの管理](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="9d4d9-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="9d4d9-135">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="9d4d9-135">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
