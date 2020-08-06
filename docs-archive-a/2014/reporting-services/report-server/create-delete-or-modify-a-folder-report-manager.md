---
title: フォルダーの作成、削除、または変更 (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bd7d5ceebdb7b3a48ded66ed108bddda25d8a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642548"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a><span data-ttu-id="e829d-102">フォルダーの作成、削除、または変更 (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="e829d-102">Create, Delete, or Modify a Folder (Report Manager)</span></span>
  <span data-ttu-id="e829d-103">フォルダーを作成すると、レポート サーバーにパブリッシュするアイテムを整理して管理できます。</span><span class="sxs-lookup"><span data-stu-id="e829d-103">You can create folders to organize and manage the items you publish to a report server.</span></span> <span data-ttu-id="e829d-104">フォルダーを作成することには、関心のあるレポートをユーザーが見つけやすくなるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="e829d-104">Creating folders can help users find reports of interest to them.</span></span> <span data-ttu-id="e829d-105">コンテンツ マネージャーは、権限を適用するためのフレームワークとしてフォルダーを利用できます。</span><span class="sxs-lookup"><span data-stu-id="e829d-105">For content managers, folders provide a framework for applying permissions.</span></span> <span data-ttu-id="e829d-106">特定のフォルダーに対してロールの割り当てを作成することで、開発中のレポートや限定されたユーザーのみを対象としたレポートへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="e829d-106">You can create role assignments on specific folders to restrict access to reports that are in development or that should not be widely distributed.</span></span>  
  
### <a name="to-create-a-folder"></a><span data-ttu-id="e829d-107">フォルダーを作成するには</span><span class="sxs-lookup"><span data-stu-id="e829d-107">To create a folder</span></span>  
  
1.  <span data-ttu-id="e829d-108">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="e829d-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e829d-109">レポート マネージャーで、[ホーム] フォルダーを選択し、 **[新しいフォルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-109">In Report Manager, select the Home folder and click **New Folder**.</span></span> <span data-ttu-id="e829d-110">既存のフォルダーの下にフォルダーを作成する場合は、 **[コンテンツ]** ページでそのフォルダーに移動し、クリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="e829d-110">Or, to create a folder under an existing folder, navigate to that folder in the **Contents** page and click the folder to open it.</span></span> <span data-ttu-id="e829d-111">次に **[新しいフォルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-111">Then click **New Folder**.</span></span>  
  
     <span data-ttu-id="e829d-112">**[新しいフォルダー]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="e829d-112">The **New Folder** page opens.</span></span>  
  
3.  <span data-ttu-id="e829d-113">フォルダー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="e829d-113">Type a folder name.</span></span> <span data-ttu-id="e829d-114">フォルダー名にはスペースを使用できますが、URL エンコードに使用される予約文字 (; ? :など) は使用できません</span><span class="sxs-lookup"><span data-stu-id="e829d-114">A folder name can include spaces, but cannot include reserved characters that are used for URL encoding: ; ?</span></span> <span data-ttu-id="e829d-115">: \@ & = +、$/\* \< > |。</span><span class="sxs-lookup"><span data-stu-id="e829d-115">: \@ & = + , $ / \* \< > |.</span></span> <span data-ttu-id="e829d-116">フォルダー名を続けて入力して、同時に複数のフォルダーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e829d-116">You cannot type a series of folder names to create several folders at once.</span></span>  
  
4.  <span data-ttu-id="e829d-117">必要に応じて、説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="e829d-117">Optionally type a description.</span></span>  
  
5.  <span data-ttu-id="e829d-118">**[コンテンツ]** ページの既定の表示でフォルダーを非表示にする場合は、 **[リスト ビューで非表示にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="e829d-118">Select **Hide in list view** if you do not want to display the folder in the default view of the **Contents** page.</span></span> <span data-ttu-id="e829d-119">このフォルダーは、 **[コンテンツ]** ページの **[詳細の表示]** をクリックした場合にのみ表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e829d-119">The folder will be visible to users only when they click **Show Details** on the **Contents** page.</span></span>  
  
6.  <span data-ttu-id="e829d-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-120">Click **OK**.</span></span>  
  
### <a name="to-delete-a-folder"></a><span data-ttu-id="e829d-121">フォルダーを削除するには</span><span class="sxs-lookup"><span data-stu-id="e829d-121">To delete a folder</span></span>  
  
1.  <span data-ttu-id="e829d-122">レポート マネージャーで、 **[コンテンツ]** ページに移動し、変更するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="e829d-122">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="e829d-123">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-123">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="e829d-124">ドロップダウン メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-124">In the drop-down menu, click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a><span data-ttu-id="e829d-125">フォルダーを変更または削除するには</span><span class="sxs-lookup"><span data-stu-id="e829d-125">To modify or delete a folder</span></span>  
  
1.  <span data-ttu-id="e829d-126">レポート マネージャーで、 **[コンテンツ]** ページに移動し、変更するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="e829d-126">In Report Manager, navigate to the **Contents** page, and locate the item that you want to modify.</span></span>  
  
2.  <span data-ttu-id="e829d-127">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-127">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="e829d-128">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-128">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="e829d-129">[全般プロパティ] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="e829d-129">The General Properties page opens.</span></span>  
  
4.  <span data-ttu-id="e829d-130">フォルダーの場所を変更するには、 **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-130">To change the folder location, click **Move**.</span></span> <span data-ttu-id="e829d-131">移動先のフォルダーの場所を入力するか、ツリーから移動先のフォルダーを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-131">Type the location of the destination folder, or choose the destination folder from the tree, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e829d-132">または、以下の方法でフォルダーのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="e829d-132">Or, modify folder properties in the following ways:</span></span>  
  
    -   <span data-ttu-id="e829d-133">フォルダーについて表示するテキストを変更するには、名前または説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="e829d-133">To modify display text about the folder, type a name or description.</span></span>  
  
    -   <span data-ttu-id="e829d-134">**[コンテンツ]** ページの既定の表示でフォルダーを表示するには、 **[リスト ビューで非表示にする]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="e829d-134">To display the folder in the default view on the **Contents** page, clear **Hide in list view**.</span></span>  
  
6.  <span data-ttu-id="e829d-135">フォルダーとフォルダーの内容を削除するには、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e829d-135">Or, to remove the folder and its contents, click **Delete**.</span></span>  
  
7.  <span data-ttu-id="e829d-136">**[Apply (適用)]** をクリックして変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="e829d-136">Click **Apply** to save changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e829d-137">参照</span><span class="sxs-lookup"><span data-stu-id="e829d-137">See Also</span></span>  
 <span data-ttu-id="e829d-138">[[新しいフォルダー] ページ &#40;レポートマネージャー&#41;](../new-folder-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e829d-138">[New Folder Page &#40;Report Manager&#41;](../new-folder-page-report-manager.md) </span></span>  
 <span data-ttu-id="e829d-139">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e829d-139">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="e829d-140">レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e829d-140">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
