---
title: '[全般] ([画像のプロパティ] ダイアログボックス) (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10051"
- sql12.rtp.rptdesigner.pictureproperties.general.f1
ms.assetid: c2218b93-f7fe-46ef-995f-d7dadf9752ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e599a437ae367a38483dbde99ffff79f64b957ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742990"
---
# <a name="image-properties-dialog-box-general-report-builder-and-ssrs"></a><span data-ttu-id="b4f47-102">[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b4f47-102">Image Properties Dialog Box, General (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b4f47-103">**[画像のプロパティ]** ダイアログ ボックスの **[全般]** を選択すると、画像の追加、画像の既定の名前の変更、およびツールヒントのテキストの追加を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b4f47-103">Select **General** on the **Image Properties** dialog box to add a picture, change the default name of the image, and add ToolTip text.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4f47-104">Options</span><span class="sxs-lookup"><span data-stu-id="b4f47-104">Options</span></span>  
 <span data-ttu-id="b4f47-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="b4f47-105">**Name**</span></span>  
 <span data-ttu-id="b4f47-106">アイテムの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-106">Type a name for the item.</span></span> <span data-ttu-id="b4f47-107">名前はレポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4f47-107">The name must be unique within the report.</span></span> <span data-ttu-id="b4f47-108">既定では、Image1 や Image2 などの一般的な名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b4f47-108">By default, a general name, such as Image1 or Image2, is assigned.</span></span>  
  
 <span data-ttu-id="b4f47-109">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="b4f47-109">**Tooltip**</span></span>  
 <span data-ttu-id="b4f47-110">テキスト、または結果がツールヒントになる式を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-110">Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="b4f47-111">式を編集するには、式 ([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4f47-111">Click the Expression (*fx*) button to edit the expression.</span></span> <span data-ttu-id="b4f47-112">**[ツールヒント]** は、ユーザーが HTML レポートのアイテムの上にポインターを置いたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4f47-112">The **Tooltip** appears when the user pauses the pointer over the item in an HTML report.</span></span>  
  
 <span data-ttu-id="b4f47-113">**[画像ソースの選択]**</span><span class="sxs-lookup"><span data-stu-id="b4f47-113">**Select the image source**</span></span>  
 <span data-ttu-id="b4f47-114">レポートを表示する際にレポート プロセッサで画像の取得元が認識されるように、画像が格納されている場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-114">Indicate where the image is stored so that when the report is rendered, the report processor will know where to get the image from.</span></span>  
  
-   <span data-ttu-id="b4f47-115">**[外部]** レポート サーバーおよび Web サーバー上のファイルとして画像を残す場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-115">**External** Choose this option when you want the image to continue to exist as a file on a report server or Web server.</span></span>  
  
-   <span data-ttu-id="b4f47-116">**[埋め込み]** レポートに画像を埋め込む場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-116">**Embedded** Choose this option when you want to embed the image into the report.</span></span>  
  
-   <span data-ttu-id="b4f47-117">**[データベース]** レポートに含める画像を表すデータベース フィールド名を追加する場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-117">**Database** Choose this option when you want to include a database field name that represents the images that you want to include in your report.</span></span>  
  
 <span data-ttu-id="b4f47-118">**[次の画像を使用]**</span><span class="sxs-lookup"><span data-stu-id="b4f47-118">**Use this image**</span></span>  
 <span data-ttu-id="b4f47-119">このオプションは、 **[埋め込み]** または **[外部]** を選択した場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4f47-119">This option appears when you select the **Embedded** or **External** option.</span></span>  
  
 <span data-ttu-id="b4f47-120">画像を埋め込む場合は、レポートに追加する画像をドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-120">If you are embedding the image, choose the image that you want to add to the report from the drop-down list.</span></span> <span data-ttu-id="b4f47-121">ドロップダウン リストに画像を追加するには、 **[インポート]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4f47-121">Click the **Import** button to add the image to the drop-down list.</span></span>  
  
 <span data-ttu-id="b4f47-122">**[外部]** オプションを選択した場合は、画像の URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-122">If you select the **External** option, type the URL of the image.</span></span> <span data-ttu-id="b4f47-123">ネイティブ モード用に構成されているレポート サーバーにレポートをパブリッシュする場合は、完全パスまたは相対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-123">For a report published to a report server configured for native mode, use a full or relative path.</span></span> <span data-ttu-id="b4f47-124">たとえば、http:// \<servername> /images/image1.jpg します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-124">For example, http://\<servername>/images/image1.jpg.</span></span> <span data-ttu-id="b4f47-125">SharePoint 統合モードで構成されているレポート サーバーにレポートをパブリッシュする場合は、完全修飾 URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-125">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL.</span></span> <span data-ttu-id="b4f47-126">たとえば、http:// \<*SharePointservername*> / \<*site*> /Documents/images/image1.jpg します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-126">For example, http://\<*SharePointservername*>/\<*site*>/Documents/images/image1.jpg.</span></span>  
  
 <span data-ttu-id="b4f47-127">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="b4f47-127">**Import**</span></span>  
 <span data-ttu-id="b4f47-128">**[次の画像を使用]** ボックスの一覧に画像を追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4f47-128">Click to add an image to the **Use this image** drop-down list.</span></span>  
  
 <span data-ttu-id="b4f47-129">**[次のフィールドを使用]**</span><span class="sxs-lookup"><span data-stu-id="b4f47-129">**Use this field**</span></span>  
 <span data-ttu-id="b4f47-130">このオプションは、 **[データベース]** オプションを選択した場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4f47-130">This option appears if you select the **Database** option.</span></span> <span data-ttu-id="b4f47-131">フィールド名を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4f47-131">Select the field name.</span></span>  
  
 <span data-ttu-id="b4f47-132">**[次の MIME の種類を使用]**</span><span class="sxs-lookup"><span data-stu-id="b4f47-132">**Use this MIME type**</span></span>  
 <span data-ttu-id="b4f47-133">データベース内に含まれている画像の適切な形式を選択します (.bmp、.jpeg、.gif、.png、.x-png など)。</span><span class="sxs-lookup"><span data-stu-id="b4f47-133">Choose the appropriate format of the images contained in the database, for example, .bmp, .jpeg, .gif, .png, and .x-png.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f47-134">参照</span><span class="sxs-lookup"><span data-stu-id="b4f47-134">See Also</span></span>  
 <span data-ttu-id="b4f47-135">[式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4f47-135">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b4f47-136">[&#40;レポートビルダーと SSRS&#41;の画像](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4f47-136">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b4f47-137">レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ</span><span class="sxs-lookup"><span data-stu-id="b4f47-137">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
