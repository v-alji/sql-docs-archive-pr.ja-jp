---
title: '[新しいフォルダー] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9212fc68-f0a6-4f79-83c1-84baf4d1957e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27c6a82c4911ba42215d4ab7dcafd666ddce5d54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643203"
---
# <a name="new-folder-page-report-manager"></a><span data-ttu-id="e0851-102">[新しいフォルダー] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="e0851-102">New Folder Page (Report Manager)</span></span>
  <span data-ttu-id="e0851-103">[新しいフォルダー] ページでは、レポート サーバーのフォルダー階層に新しいフォルダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e0851-103">Use the New Folder page to create a new folder in the report server folder hierarchy.</span></span> <span data-ttu-id="e0851-104">作成するフォルダーは、レポート サーバー データベースに保存される仮想フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="e0851-104">The folder that you create is a virtual folder that is stored in a report server database.</span></span> <span data-ttu-id="e0851-105">このフォルダーは、コンピューターのファイル システムに作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e0851-105">The folder is not created in the file system of your computer.</span></span>  
  
 <span data-ttu-id="e0851-106">フォルダーは、現在選択されているフォルダーのサブフォルダーになるよう作成されます。</span><span class="sxs-lookup"><span data-stu-id="e0851-106">A folder is created in-place, as a subfolder of the folder that is currently selected.</span></span> <span data-ttu-id="e0851-107">フォルダーを作成する前に、フォルダーを作成する場所を参照しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0851-107">Before creating a folder, you should navigate to the location where you want to create the folder.</span></span>  
  
 <span data-ttu-id="e0851-108">フォルダーを作成した後も、そのフォルダーの [全般] プロパティ ページから名前および説明を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e0851-108">After you create a folder, you can modify its name and description through the General properties page of the folder.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="e0851-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="e0851-109">Navigation</span></span>  
 <span data-ttu-id="e0851-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e0851-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-folder-page"></a><span data-ttu-id="e0851-111">[新しいフォルダー] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="e0851-111">To open the New Folder page</span></span>  
  
1.  <span data-ttu-id="e0851-112">レポート マネージャーを開き、新しいフォルダーを作成するフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="e0851-112">Open Report Manager, and navigate to the folder in which you want to create a new folder.</span></span>  
  
2.  <span data-ttu-id="e0851-113">ツール バーの **[新しいフォルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0851-113">In the toolbar, click **New Folder**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0851-114">Options</span><span class="sxs-lookup"><span data-stu-id="e0851-114">Options</span></span>  
 <span data-ttu-id="e0851-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="e0851-115">**Name**</span></span>  
 <span data-ttu-id="e0851-116">フォルダー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e0851-116">Specify the name of the folder.</span></span> <span data-ttu-id="e0851-117">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0851-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="e0851-118">また、スペースおよび特定の記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e0851-118">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="e0851-119">名前を指定するときに、; ?</span><span class="sxs-lookup"><span data-stu-id="e0851-119">Do not use the characters ; ?</span></span> <span data-ttu-id="e0851-120">: \@ & = +、$/\* \< > |"またはの名前を指定する場合。</span><span class="sxs-lookup"><span data-stu-id="e0851-120">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="e0851-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="e0851-121">**Description**</span></span>  
 <span data-ttu-id="e0851-122">フォルダーの内容の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="e0851-122">Type a description of folder contents.</span></span> <span data-ttu-id="e0851-123">この説明は、フォルダーへの権限を持つユーザーの [コンテンツ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0851-123">This description appears in the Contents page to users who have permission to access the folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0851-124">参照</span><span class="sxs-lookup"><span data-stu-id="e0851-124">See Also</span></span>  
 <span data-ttu-id="e0851-125">[フォルダー &#40;レポートマネージャーの作成、削除、または変更&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e0851-125">[Create, Delete, or Modify a Folder &#40;Report Manager&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span></span>  
 <span data-ttu-id="e0851-126">[[全般] プロパティページ、フォルダー &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e0851-126">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="e0851-127">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e0851-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e0851-128">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e0851-128">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="e0851-129">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e0851-129">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="e0851-130">[[全般] プロパティページ、フォルダー &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="e0851-130">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md)</span></span>  
  
  
