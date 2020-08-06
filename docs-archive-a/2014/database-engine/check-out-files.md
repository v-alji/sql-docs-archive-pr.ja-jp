---
title: ファイルのチェックアウト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 151f554742bd6c381b27b58155d3f0e40e9eeb0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642327"
---
# <a name="check-out-files"></a><span data-ttu-id="d068a-102">ファイルのチェックアウト</span><span class="sxs-lookup"><span data-stu-id="d068a-102">Check Out Files</span></span>
  <span data-ttu-id="d068a-103">チェックインしたファイルの編集が許可されるように [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境を設定していない場合、チェックインしたファイルを変更するには、まずファイルをチェックアウトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d068a-103">Unless you have configured the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment to permit checked-in files to be edited, you must check out a file before you can modify it.</span></span> <span data-ttu-id="d068a-104">ファイルをチェックアウトすると、ファイルのバージョンのコピーがローカル ディスクにコピーされ、ファイルの読み取り専用の属性が解除されます。</span><span class="sxs-lookup"><span data-stu-id="d068a-104">When you check out a file, a copy of the file version is copied to your local disk, and the read-only attribute of the file is removed.</span></span>  
  
 <span data-ttu-id="d068a-105">ファイルのチェックアウトには、排他モードと共有モードがあります。</span><span class="sxs-lookup"><span data-stu-id="d068a-105">You can check files out either exclusively or in shared mode.</span></span> <span data-ttu-id="d068a-106">ファイルを排他モードでチェックアウトすると、チェックアウトしたユーザーがそのファイルを再びチェックインするまで、他のユーザーがそのファイルをチェックアウトすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d068a-106">When you check out a file exclusively, no other user can check out the file until you check it in.</span></span> <span data-ttu-id="d068a-107">共有モードでファイルをチェックアウトすると、他のユーザーもそのファイルをチェックアウトして変更できます。このファイルをチェックインする場合は、必要に応じて、チェックアウトしたバージョンと、他のユーザーが作成したバージョンをマージします。</span><span class="sxs-lookup"><span data-stu-id="d068a-107">When you check out a file in shared mode, other users can check out and modify the file, and when you check it in, you may need to merge the version you have checked out with the versions created by other users.</span></span>  
  
 <span data-ttu-id="d068a-108">ソース管理されたプロジェクトとファイルをチェックアウトするには、 **[チェックアウト]** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d068a-108">Use the **Check Out** command to check out source-controlled projects and files.</span></span> <span data-ttu-id="d068a-109">このコマンドを使用してソリューションまたはプロジェクトをチェックアウトすると、ソリューションまたはプロジェクト内のすべてのファイルもチェックアウトされます。ただし、個々のソースコードファイルをチェックアウトしても、そのファイルが属するプロジェクトまたはソリューションがチェックアウトされることはありません。</span><span class="sxs-lookup"><span data-stu-id="d068a-109">If you use this command to check out a solution or project, all the files in the solution or project are also checked out. However, checking out an individual source code file does not result in the check out of the project or solution to which it belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d068a-110">[!INCLUDE[msCoName](../includes/msconame-md.md)]プロジェクトの Visual SourceSafe データベースが複数のチェックアウトを許可するように構成されていて、ファイルを排他的にチェックアウトする場合は、ファイルをチェックアウトする前に、 **[チェックアウトオプションの詳細設定**] ダイアログボックスの [**複数のチェックアウトを許可**する] オプションをオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d068a-110">If the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database for your project is configured to allow multiple checkouts, and you want to check out a file exclusively, you must clear the **Allow multiple checkouts** option in the **Advanced Check Out Options** dialog box before checking out the file.</span></span> <span data-ttu-id="d068a-111">この設定を有効にするには、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d068a-111">You must restart the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for this setting to take effect.</span></span>  
  
### <a name="to-check-out-a-file"></a><span data-ttu-id="d068a-112">ファイルをチェックアウトするには</span><span class="sxs-lookup"><span data-stu-id="d068a-112">To check out a file</span></span>  
  
1.  <span data-ttu-id="d068a-113">ソリューション エクスプローラーで、プロジェクトまたはファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d068a-113">In Solution Explorer, select the project or file.</span></span>  
  
2.  <span data-ttu-id="d068a-114">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**編集用に**チェックアウト] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d068a-114">On the **File** menu, point to **Source Control**, and then click **Check Out for Edit**.</span></span>  
  
3.  <span data-ttu-id="d068a-115">[**編集用に**チェックアウト] ダイアログボックスが表示された場合は、目的の項目を選択し、[**チェックアウト] をクリックし**ます。[チェックアウト] ダイアログボックスを表示しないように環境を構成した場合 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 、[ソリューションエクスプローラーで選択した項目とその子が**Check Out**直ちにチェックアウトされます。</span><span class="sxs-lookup"><span data-stu-id="d068a-115">If the **Check Out for Edit** dialog box is displayed, select the items you want, and click **Check Out**. If you have configured the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment not to display the **Check Out** dialog box, the items selected in Solution Explorer and any children they might have are checked out immediately.</span></span>  
  
     <span data-ttu-id="d068a-116">**チェックアウト**</span><span class="sxs-lookup"><span data-stu-id="d068a-116">**Check Out**</span></span>  
     <span data-ttu-id="d068a-117">選択されているすべての項目をチェックアウトします。</span><span class="sxs-lookup"><span data-stu-id="d068a-117">Check out all the selected items.</span></span>  
  
     <span data-ttu-id="d068a-118">**[列]**</span><span class="sxs-lookup"><span data-stu-id="d068a-118">**Columns**</span></span>  
     <span data-ttu-id="d068a-119">表示する列と、その表示順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="d068a-119">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="d068a-120">**コメント**</span><span class="sxs-lookup"><span data-stu-id="d068a-120">**Comments**</span></span>  
     <span data-ttu-id="d068a-121">チェックアウト操作に関連付けるコメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d068a-121">Specify a comment to associate with the checkout operation.</span></span>  
  
     <span data-ttu-id="d068a-122">**[項目のチェックアウト時に [チェックアウト] ダイアログ ボックスを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="d068a-122">**Don't Show Check Out dialog box when checking out items**</span></span>  
     <span data-ttu-id="d068a-123">チェックアウト処理時にダイアログ ボックスが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="d068a-123">Suppress the dialog box during checkout operations.</span></span>  
  
     <span data-ttu-id="d068a-124">**[平面表示]**</span><span class="sxs-lookup"><span data-stu-id="d068a-124">**Flat View**</span></span>  
     <span data-ttu-id="d068a-125">チェックアウトする項目をソース管理接続の下に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d068a-125">Display the items you are checking out as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="d068a-126">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="d068a-126">**Edit**</span></span>  
     <span data-ttu-id="d068a-127">チェックアウトせずに項目を変更します。[**編集**] ボタンは、チェックインした [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ファイルの編集をサポートするようにを構成した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="d068a-127">Modify an item without checking it out. The **Edit** button appears only if you have [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configured to support the editing of checked-in files.</span></span>  
  
     <span data-ttu-id="d068a-128">**名前**</span><span class="sxs-lookup"><span data-stu-id="d068a-128">**Name**</span></span>  
     <span data-ttu-id="d068a-129">チェックアウトできる項目の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="d068a-129">Displays the names of the items available for checkout.</span></span> <span data-ttu-id="d068a-130">選択されている項目の横にはチェック ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d068a-130">Items that are selected appear with check boxes next to them.</span></span> <span data-ttu-id="d068a-131">特定の項目をチェックアウトしない場合は、そのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d068a-131">If you do not want to check out a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="d068a-132">**Options**</span><span class="sxs-lookup"><span data-stu-id="d068a-132">**Options**</span></span>  
     <span data-ttu-id="d068a-133">ボタンの右側の矢印をクリックすると、ソース管理のプラグインに固有のチェックアウト オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d068a-133">Displays source control plug-in-specific checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="d068a-134">**Sort**</span><span class="sxs-lookup"><span data-stu-id="d068a-134">**Sort**</span></span>  
     <span data-ttu-id="d068a-135">表示する列の順序を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="d068a-135">Sort the order of the displayed columns.</span></span>  
  
     <span data-ttu-id="d068a-136">**ツリービュー**</span><span class="sxs-lookup"><span data-stu-id="d068a-136">**Tree View**</span></span>  
     <span data-ttu-id="d068a-137">チェックアウトする項目のフォルダーおよびファイル階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="d068a-137">Display the folder and file hierarchy for the item you are checking out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d068a-138">参照</span><span class="sxs-lookup"><span data-stu-id="d068a-138">See Also</span></span>  
 <span data-ttu-id="d068a-139">[チェックインしたファイルの編集](../../2014/database-engine/edit-checked-in-files.md) </span><span class="sxs-lookup"><span data-stu-id="d068a-139">[Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md) </span></span>  
 <span data-ttu-id="d068a-140">[編集時にファイルを自動的にチェックアウトする](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span><span class="sxs-lookup"><span data-stu-id="d068a-140">[Automatically Check Out Files Upon Edit](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span></span>  
 <span data-ttu-id="d068a-141">[チェックアウトを元に戻す](../../2014/database-engine/undo-checkouts.md) </span><span class="sxs-lookup"><span data-stu-id="d068a-141">[Undo Checkouts](../../2014/database-engine/undo-checkouts.md) </span></span>  
 [<span data-ttu-id="d068a-142">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="d068a-142">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
