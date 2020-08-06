---
title: ファイルのチェックイン |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 070c1dfa5dd057cf777980f7022752a97a4dc84c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642328"
---
# <a name="check-in-files"></a><span data-ttu-id="02f2b-102">ファイルのチェックイン</span><span class="sxs-lookup"><span data-stu-id="02f2b-102">Check In Files</span></span>
  <span data-ttu-id="02f2b-103">ファイルのソース管理を行っている場合、修正後のファイルを他のユーザーも利用できるようにするには、そのファイルをソース管理にチェックインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02f2b-103">To make source-controlled files that you have modified available to other users, you must check the files into source control.</span></span> <span data-ttu-id="02f2b-104">ファイルをチェックインすると、チェックインしたバージョンがソース管理プロバイダーに書き込まれ、そのファイルの最新バージョンになります。</span><span class="sxs-lookup"><span data-stu-id="02f2b-104">When you check in a file, the version you check in is written to the source control provider and becomes the latest version of the file.</span></span>  
  
 <span data-ttu-id="02f2b-105">[**チェックイン] コマンドを使用して**、ファイルをチェックインできます。</span><span class="sxs-lookup"><span data-stu-id="02f2b-105">You can use the **Check In** command to check in files.</span></span> <span data-ttu-id="02f2b-106">このコマンドを使用してソリューションまたはプロジェクトをチェックインした場合は、そのソリューションまたはプロジェクト内にあるファイルもすべてチェックインされます。</span><span class="sxs-lookup"><span data-stu-id="02f2b-106">If you use this command to check in a solution or project, all the files in the solution or project are also checked in.</span></span> <span data-ttu-id="02f2b-107">ただし、個々のソース コード ファイルをチェックインしても、そのファイルが属するプロジェクトやソリューションはチェックインされません。</span><span class="sxs-lookup"><span data-stu-id="02f2b-107">However, checking in an individual source code file does not result in the check-in of the project or solution to which it belongs.</span></span>  
  
### <a name="to-check-in-a-file"></a><span data-ttu-id="02f2b-108">ファイルをチェックインするには</span><span class="sxs-lookup"><span data-stu-id="02f2b-108">To check in a file</span></span>  
  
1.  <span data-ttu-id="02f2b-109">ソリューションエクスプローラーで、チェックインするファイルを右クリックし、[**チェックイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="02f2b-109">In Solution Explorer, right-click the file to check in, and then click **Check In**.</span></span>  
  
2.  <span data-ttu-id="02f2b-110">[**チェックイン**] ダイアログボックスが表示された場合は、適切なオプションを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="02f2b-110">If the **Check In** dialog box appears, select the appropriate options, and then click **OK**.</span></span>  
  
     <span data-ttu-id="02f2b-111">**チェックイン**</span><span class="sxs-lookup"><span data-stu-id="02f2b-111">**Check In**</span></span>  
     <span data-ttu-id="02f2b-112">選択されている項目をすべてチェックインします。</span><span class="sxs-lookup"><span data-stu-id="02f2b-112">Check in all the selected items.</span></span>  
  
     <span data-ttu-id="02f2b-113">**[列]**</span><span class="sxs-lookup"><span data-stu-id="02f2b-113">**Columns**</span></span>  
     <span data-ttu-id="02f2b-114">表示する列と、その表示順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="02f2b-114">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="02f2b-115">**コメント**</span><span class="sxs-lookup"><span data-stu-id="02f2b-115">**Comments**</span></span>  
     <span data-ttu-id="02f2b-116">チェックイン操作に関連付けるコメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="02f2b-116">Add a comment to associate with the check-in operation.</span></span>  
  
     <span data-ttu-id="02f2b-117">**[項目をチェックインするときにチェックイン ダイアログ ボックスを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="02f2b-117">**Don't show Check in dialog box when checking in items**</span></span>  
     <span data-ttu-id="02f2b-118">チェックインの処理中にダイアログ ボックスが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="02f2b-118">Suppress the dialog box during check-in operations.</span></span>  
  
     <span data-ttu-id="02f2b-119">**[平面表示]**</span><span class="sxs-lookup"><span data-stu-id="02f2b-119">**Flat View**</span></span>  
     <span data-ttu-id="02f2b-120">チェックインするファイルをソース管理接続の下に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="02f2b-120">Display the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="02f2b-121">**名前**</span><span class="sxs-lookup"><span data-stu-id="02f2b-121">**Name**</span></span>  
     <span data-ttu-id="02f2b-122">チェックインする項目の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="02f2b-122">Displays the names of the items to check in.</span></span> <span data-ttu-id="02f2b-123">選択した項目の横にチェックボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="02f2b-123">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="02f2b-124">特定の項目をチェックインしない場合は、そのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="02f2b-124">If you do not want to check in a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="02f2b-125">**Options**</span><span class="sxs-lookup"><span data-stu-id="02f2b-125">**Options**</span></span>  
     <span data-ttu-id="02f2b-126">ボタンの右側の矢印をクリックすると、ソース管理のプラグインに固有のチェックイン オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="02f2b-126">Displays source control plug-in-specific check-in options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="02f2b-127">**Sort**</span><span class="sxs-lookup"><span data-stu-id="02f2b-127">**Sort**</span></span>  
     <span data-ttu-id="02f2b-128">表示列の順序を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="02f2b-128">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="02f2b-129">**ツリービュー**</span><span class="sxs-lookup"><span data-stu-id="02f2b-129">**Tree View**</span></span>  
     <span data-ttu-id="02f2b-130">チェックインする項目のフォルダーおよびファイル階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="02f2b-130">Display the folder and file hierarchy for the items you are checking in.</span></span>  
  
 <span data-ttu-id="02f2b-131">チェックインしたファイルが共有チェックアウトの一部でない場合、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境ではそのファイルが直ちにチェックインされます。</span><span class="sxs-lookup"><span data-stu-id="02f2b-131">If the file you have checked in is not part of a shared checkout, the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment checks in the file immediately.</span></span> <span data-ttu-id="02f2b-132">あるいは、直ちにはチェックインされずに、他のユーザーが作成したバージョンとのマージを要求するダイアログが表示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="02f2b-132">Otherwise, it may prompt you to merge your version with versions created by other users.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f2b-133">参照</span><span class="sxs-lookup"><span data-stu-id="02f2b-133">See Also</span></span>  
 <span data-ttu-id="02f2b-134">[変更されたファイルの一覧を表示する](../../2014/database-engine/view-a-list-of-modified-files.md) </span><span class="sxs-lookup"><span data-stu-id="02f2b-134">[View a List of Modified Files](../../2014/database-engine/view-a-list-of-modified-files.md) </span></span>  
 [<span data-ttu-id="02f2b-135">チェックインの管理</span><span class="sxs-lookup"><span data-stu-id="02f2b-135">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)  
  
  
