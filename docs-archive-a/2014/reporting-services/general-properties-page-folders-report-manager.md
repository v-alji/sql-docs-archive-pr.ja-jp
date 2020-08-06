---
title: '[全般] プロパティページ、フォルダー (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 31d99d9b-2303-4bae-9466-fb67b97cf11a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1c3fbf2e9020ac5d1fe5ebbd1e9ed48b45adb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644855"
---
# <a name="general-properties-page-folders-report-manager"></a><span data-ttu-id="ddf8c-102">[全般] プロパティ ページ、フォルダー (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="ddf8c-102">General Properties Page, Folders (Report Manager)</span></span>
  <span data-ttu-id="ddf8c-103">フォルダーの [全般] プロパティ ページでは、作成するフォルダーのプロパティを表示または設定できます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-103">Use the General properties page for folders to view and set properties for the folders that you create.</span></span> <span data-ttu-id="ddf8c-104">フォルダーを作成または変更したユーザーおよびフォルダーの変更日時に関する情報が、[全般] プロパティ ページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-104">Information about who created or modified the folder and when the folder was modified appear at the top of the General properties page.</span></span>  
  
 <span data-ttu-id="ddf8c-105">フォルダーのプロパティには、セキュリティ設定も含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-105">Folder properties also include security settings.</span></span> <span data-ttu-id="ddf8c-106">フォルダーのセキュリティの詳細については、「[セキュリティで保護されたフォルダー](security/secure-folders.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-106">For more information about folder security, see [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="ddf8c-107">[ホーム] フォルダー、[個人用レポート] フォルダー、[Users] フォルダーなどの特別な用途に使用されるフォルダーは、名前を変更したり、レポート サーバーの名前空間内で移動できません。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-107">Special-purpose folders such as Home, My Reports, and Users folders cannot be renamed or moved within the report server namespace.</span></span> <span data-ttu-id="ddf8c-108">これらのフォルダーの [全般] プロパティ ページはありません。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-108">The General properties page is not available for these folders.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ddf8c-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="ddf8c-109">Navigation</span></span>  
 <span data-ttu-id="ddf8c-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-folder"></a><span data-ttu-id="ddf8c-111">フォルダーの [全般] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="ddf8c-111">To open the General properties page for a folder</span></span>  
  
1.  <span data-ttu-id="ddf8c-112">レポート マネージャーを開き、プロパティを表示または構成するフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-112">Open Report Manager, and open the folder for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="ddf8c-113">フォルダー バナーの下のツール バーの **[フォルダー設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-113">Under the folder banner, in the toolbar, click **Folder Settings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ddf8c-114">Options</span><span class="sxs-lookup"><span data-stu-id="ddf8c-114">Options</span></span>  
 <span data-ttu-id="ddf8c-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="ddf8c-115">**Name**</span></span>  
 <span data-ttu-id="ddf8c-116">フォルダーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-116">Specify a name for the folder.</span></span> <span data-ttu-id="ddf8c-117">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="ddf8c-118">また、スペースおよびいくつかの記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-118">It can also include spaces and some symbols.</span></span> <span data-ttu-id="ddf8c-119">名前を指定するときに、; ?</span><span class="sxs-lookup"><span data-stu-id="ddf8c-119">Do not use the characters ; ?</span></span> <span data-ttu-id="ddf8c-120">: \@ & = +、$ \* \< > |"またはの名前を指定する場合。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-120">: \@ & = + , $ \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="ddf8c-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="ddf8c-121">**Description**</span></span>  
 <span data-ttu-id="ddf8c-122">フォルダーの内容の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-122">Type a description of the folder contents.</span></span> <span data-ttu-id="ddf8c-123">ユーザーがフォルダーへのアクセス権を持っている場合、この説明が [コンテンツ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-123">This description appears on the Contents page for users who have permission to access the folder.</span></span>  
  
 <span data-ttu-id="ddf8c-124">**[リスト ビューで非表示にする]**</span><span class="sxs-lookup"><span data-stu-id="ddf8c-124">**Hide in list view**</span></span>  
 <span data-ttu-id="ddf8c-125">このオプションをオンにすると、レポート マネージャーでリスト ビュー モードを使用しているユーザーにフォルダーを表示しません。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-125">Select this option to hide the folder from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="ddf8c-126">リスト ビュー モードは、レポート サーバー フォルダー階層を参照するときの既定のビュー形式です。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-126">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="ddf8c-127">リスト ビューでは、アイテム名および説明がページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-127">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="ddf8c-128">別の形式として詳細ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-128">The alternate format is details view.</span></span> <span data-ttu-id="ddf8c-129">詳細ビューでは説明が省略されますが、そのアイテムに関するその他の情報は含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-129">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="ddf8c-130">リスト ビューのアイテムは非表示にできますが、詳細ビューのアイテムは非表示にできません。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-130">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="ddf8c-131">アイテムへのアクセスを制限する場合は、ロールの割り当てを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-131">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="ddf8c-132">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="ddf8c-132">**Apply**</span></span>  
 <span data-ttu-id="ddf8c-133">変更を保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-133">Click to save your changes.</span></span>  
  
 <span data-ttu-id="ddf8c-134">**削除**</span><span class="sxs-lookup"><span data-stu-id="ddf8c-134">**Delete**</span></span>  
 <span data-ttu-id="ddf8c-135">フォルダーとフォルダーの内容を削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-135">Click to remove the folder and its contents.</span></span>  
  
 <span data-ttu-id="ddf8c-136">**移動**</span><span class="sxs-lookup"><span data-stu-id="ddf8c-136">**Move**</span></span>  
 <span data-ttu-id="ddf8c-137">レポート サーバー名前空間内のレポートまたはフォルダーを再配置する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-137">Click to relocate a report or folder within the report server namespace.</span></span> <span data-ttu-id="ddf8c-138">このボタンをクリックすると、[カタログ アイテムの移動] ページが表示され、新しいフォルダーの場所でフォルダーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ddf8c-138">Clicking this button opens the Move Items page that allows you to browse folders for a new folder location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf8c-139">参照</span><span class="sxs-lookup"><span data-stu-id="ddf8c-139">See Also</span></span>  
 <span data-ttu-id="ddf8c-140">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ddf8c-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="ddf8c-141">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="ddf8c-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
