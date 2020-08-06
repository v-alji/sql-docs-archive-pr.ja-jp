---
title: レポートパーツのトラブルシューティング (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9fe1932-46e7-421b-a8a9-4c54d9576e94
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 798bb59fc2470dedd3bdc5c996b4da395e57bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715993"
---
# <a name="troubleshoot-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="6bc13-102">レポート パーツのトラブルシューティング (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="6bc13-102">Troubleshoot Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6bc13-103">レポート パーツを使用するために役立つヒントを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6bc13-103">These tips can help when working with report parts.</span></span>  
  
## <a name="why-do-my-co-worker-and-i-see-different-instances-of-the-same-report-part-when-we-search-for-it"></a><span data-ttu-id="6bc13-104">同僚と同じレポート パーツを検索したのに、表示されるインスタンスが異なる</span><span class="sxs-lookup"><span data-stu-id="6bc13-104">Why do my co-worker and I see different instances of the same report part when we search for it?</span></span>  
 <span data-ttu-id="6bc13-105">レポート サーバーまたはレポート サーバーに統合された SharePoint サイトには、1 つのレポート パーツに対して、すべて同じグローバル一意識別子 (GUID) を持つ複数のインスタンスが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-105">There can be multiple instances of a single report part on a report server or SharePoint site integrated with a report server, and all instances will have the same globally unique identifier (GUID).</span></span> <span data-ttu-id="6bc13-106">検索結果には、最新のインスタンスのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bc13-106">Only the most recent instance is displayed in the list of search results.</span></span> <span data-ttu-id="6bc13-107">1 つのレポート パーツに複数のインスタンスがある場合は、それぞれの権限が異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-107">In some situations, different instances of a single report part can have different permissions.</span></span> <span data-ttu-id="6bc13-108">サーバーに対する権限が同僚と異なる場合は、同じインスタンスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="6bc13-108">If your co-worker and you have different permissions on the server, you will not see the same instance.</span></span> <span data-ttu-id="6bc13-109">たとえば、すべて同じ GUID を持つレポート パーツの複数のコピーが SharePoint 統合モードのレポート サーバー上のそれぞれ異なるフォルダーに保存されているとします。</span><span class="sxs-lookup"><span data-stu-id="6bc13-109">For example, say that multiple copies of a report part, all with the same GUID, are saved in different folders on a report server in SharePoint integrated mode.</span></span> <span data-ttu-id="6bc13-110">フォルダーの権限が異なる場合、これらのフォルダーのレポート パーツもそれぞれ異なる権限を持つことになります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-110">If the folders have different permissions, then the report parts in those folders will also have different permissions.</span></span>  
  
 <span data-ttu-id="6bc13-111">自分の権限と同僚の権限を確認するには、レポート サーバー管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="6bc13-111">To see what permissions you and your co-worker have, ask your report server administrator.</span></span>  
  
## <a name="when-i-search-for-report-parts-that-i-uploaded-to-a-sharepoint-server-i-do-not-see-them-why-not"></a><span data-ttu-id="6bc13-112">SharePoint サーバーにアップロードしたレポート パーツを検索しても、</span><span class="sxs-lookup"><span data-stu-id="6bc13-112">When I search for report parts that I uploaded to a SharePoint server, I do not see them.</span></span> <span data-ttu-id="6bc13-113">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="6bc13-113">Why not?</span></span>  
 <span data-ttu-id="6bc13-114">レポート ビルダーを使用してパブリッシュする代わりに、SharePoint ドキュメント ライブラリに手動でアップロードしたレポート パーツは、レポート パーツ ギャラリーに表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-114">Report Parts that you have manually uploaded to a SharePoint document library, instead of published by using Report Builder, might not appear in the Report Part Gallery.</span></span> <span data-ttu-id="6bc13-115">ギャラリー検索に使用されるレポート サーバーは、SharePoint ドキュメント ライブラリのコンテンツと同期することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-115">The report server used for the gallery search might need to be synchronized with the contents of the SharePoint document library.</span></span> <span data-ttu-id="6bc13-116">詳細については、msdn.microsoft.com のオンラインブックの「SharePoint サーバーの[全体管理でレポートサーバー File Sync 機能をアクティブにする](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)」を参照してください [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="6bc13-116">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
## <a name="why-cant-others-see-the-image-in-their-reports"></a><span data-ttu-id="6bc13-117">他の人のレポートに画像が表示されない</span><span class="sxs-lookup"><span data-stu-id="6bc13-117">Why can't others see the image in their reports?</span></span>  
 <span data-ttu-id="6bc13-118">画像ファイルのリンクとなるレポート パーツをパブリッシュした場合、このレポート パーツは単なるリンクになります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-118">If you publish a report part that is a link to an image file, the report part is really just a link.</span></span> <span data-ttu-id="6bc13-119">他の人がレポートに画像レポート パーツを作成したときに画像が表示されない場合は、リンク先の画像に対する権限を持っていないことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="6bc13-119">If others cannot see the image when they add the image report part to their reports, they might not have permissions for the image that you are linking to.</span></span>  
  
 <span data-ttu-id="6bc13-120">この解決方法として、次のいくつかの手段が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="6bc13-120">There are a few possible solutions to this:</span></span>  
  
-   <span data-ttu-id="6bc13-121">画像ファイルへのリンクをレポート パーツとするのではなく、画像ファイルをレポート パーツにする。</span><span class="sxs-lookup"><span data-stu-id="6bc13-121">Make the image file a report part, instead of making the link to the image file the report part.</span></span>  
  
-   <span data-ttu-id="6bc13-122">他の人が権限を持つ場所に画像ファイルを移動する。</span><span class="sxs-lookup"><span data-stu-id="6bc13-122">Move the image file to a location for which others have permissions.</span></span>  
  
-   <span data-ttu-id="6bc13-123">レポート サーバー管理者に権限を変更してもらう。</span><span class="sxs-lookup"><span data-stu-id="6bc13-123">Ask the report server administrator to change permissions.</span></span>  
  
## <a name="why-do-i-get-a-circular-reference-error-message-when-i-try-to-publish-my-report-part"></a><span data-ttu-id="6bc13-124">レポート パーツをパブリッシュしようとすると、"循環参照" エラー メッセージが表示される</span><span class="sxs-lookup"><span data-stu-id="6bc13-124">Why do I get a "circular reference" error message when I try to publish my report part?</span></span>  
 <span data-ttu-id="6bc13-125">レポート アイテムに循環参照が含まれている場合、そのアイテムをレポート パーツとしてパブリッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6bc13-125">If report items have a circular reference, you won't be able to publish them as report parts.</span></span> <span data-ttu-id="6bc13-126">たとえば、レポート アイテムがデータセットを参照し、そのデータセットがパラメーターを参照するとします。</span><span class="sxs-lookup"><span data-stu-id="6bc13-126">For example, a report item points to a dataset, which in turn points to a parameter.</span></span> <span data-ttu-id="6bc13-127">また、そのパラメーターはデータセットを参照します。</span><span class="sxs-lookup"><span data-stu-id="6bc13-127">The parameter, in turn, points to the dataset¸ too.</span></span> <span data-ttu-id="6bc13-128">レポート パーツをパブリッシュするには、まずいずれかの参照を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bc13-128">You'll need to delete one of the references first before you can publish the report part.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc13-129">参照</span><span class="sxs-lookup"><span data-stu-id="6bc13-129">See Also</span></span>  
 [<span data-ttu-id="6bc13-130">レポート パーツ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6bc13-130">Report Parts &#40;Report Builder and SSRS&#41;</span></span>](report-parts-report-builder-and-ssrs.md)  
  
  
