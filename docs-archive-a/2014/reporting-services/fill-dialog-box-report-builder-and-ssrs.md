---
title: '[塗りつぶし] ダイアログボックス (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae7f2b05d4d108c77f1dcae9ce7fefe5073e2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641470"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="50768-102">[塗りつぶし] ダイアログ ボックス (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="50768-102">Fill Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="50768-103">**[塗りつぶし]** タブでは、データ領域やテキスト ボックスにある 1 つまたは複数のセルの背景色のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="50768-103">On the **Fill** tab, you can specify color options for the background of a single cell or multiple cells within a data region or a text box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50768-104">Options</span><span class="sxs-lookup"><span data-stu-id="50768-104">Options</span></span>  
 <span data-ttu-id="50768-105">**塗りつぶしの色**</span><span class="sxs-lookup"><span data-stu-id="50768-105">**Fill Color**</span></span>  
 <span data-ttu-id="50768-106">色のボタンをクリックして、四角形の塗りつぶしの色を選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-106">Click the color button to select a fill color for the rectangle.</span></span> <span data-ttu-id="50768-107">式を編集するには、 **[式]**_(fx)_ ボタンをクリックします。この式には、RGB 色を表す 16 進値、または **[式]** ダイアログ ボックスに用意されている定義済みの色の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="50768-107">Click the **Expression**_(fx)_ button to edit the expression, which can be a hexadecimal value for the RGB color or one of the predefined color names that are provided in the **Expression** dialog box.</span></span> <span data-ttu-id="50768-108">定義済みの色の一覧を表示するには、 **[アイテム]** ペインの **[Web]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-108">To see a list of predefined colors, in the **Item** pane, select **Web**.</span></span> <span data-ttu-id="50768-109">**[タイトル]** ペインに表示されている色の名前は、[式] ペインに入力できます。</span><span class="sxs-lookup"><span data-stu-id="50768-109">The color names listed in the **Title** pane can be typed into the expression text pane.</span></span> <span data-ttu-id="50768-110">色の名前を入力する場合は、等号 (=) または引用符 ("") を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="50768-110">Do not use an equal sign (=) or quotation marks ("") when typing the color name.</span></span>  
  
 <span data-ttu-id="50768-111">**[画像ソースの選択]**</span><span class="sxs-lookup"><span data-stu-id="50768-111">**Select the image source**</span></span>  
 <span data-ttu-id="50768-112">レポートを表示する際にレポート プロセッサで表示できるように、画像が格納されている場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="50768-112">Indicate where the image is stored so that when the report is rendered, the report processor can display it.</span></span>  
  
-   <span data-ttu-id="50768-113">**[外部]** レポート サーバーおよび Web サーバー上のファイルとして画像を残す場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-113">**External** Choose this option when you want the image to continue to exist as a file on a report server or Web server.</span></span>  
  
-   <span data-ttu-id="50768-114">**[埋め込み]** レポートに画像を埋め込む場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-114">**Embedded** Choose this option when you want to embed the image into the report.</span></span>  
  
-   <span data-ttu-id="50768-115">**[データベース]** レポートに含める画像を表すデータベース フィールド名を追加する場合にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-115">**Database** Choose this option when you want to include a database field name that represents the images that you want to include in your report.</span></span>  
  
 <span data-ttu-id="50768-116">**[次の画像を使用]**</span><span class="sxs-lookup"><span data-stu-id="50768-116">**Use this image**</span></span>  
 <span data-ttu-id="50768-117">このオプションは、 **[埋め込み]** または **[外部]** を選択した場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="50768-117">This option appears when you select the **Embedded** or **External** option.</span></span>  
  
 <span data-ttu-id="50768-118">画像を埋め込む場合は、レポートに追加する画像をドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-118">If you are embedding the image, choose the picture that you want to add to the report from the drop-down list.</span></span> <span data-ttu-id="50768-119">ドロップダウン リストに画像を追加するには、 **[インポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50768-119">Click **Import** to add the image to the drop-down list.</span></span> <span data-ttu-id="50768-120">画像を **[データ]** ペインに追加した場合は、 **[埋め込み]** をクリックし、ドロップダウン リストから画像を選択すると、追加した画像を選択できます。</span><span class="sxs-lookup"><span data-stu-id="50768-120">If you added an image to the **Data** pane, you can select that image by choosing **Embedded** and then selecting the image from the drop-down list.</span></span>  
  
 <span data-ttu-id="50768-121">**[外部]** オプションを選択した場合は、画像の URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="50768-121">If you select the **External** option, type the URL of the image.</span></span> <span data-ttu-id="50768-122">ネイティブモード用に構成されているレポートサーバーにレポートをパブリッシュする場合は、完全パスまたは相対パス (たとえば、http:// *\<servername>* /images/image1.jpg) を使用します。</span><span class="sxs-lookup"><span data-stu-id="50768-122">For a report published to a report server configured for native mode, use a full or relative path (for example, http://*\<servername>*/images/image1.jpg).</span></span> <span data-ttu-id="50768-123">SharePoint 統合モードで構成されているレポートサーバーにレポートをパブリッシュする場合は、完全修飾 URL (たとえば、http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg) を使用します。</span><span class="sxs-lookup"><span data-stu-id="50768-123">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
 <span data-ttu-id="50768-124">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="50768-124">**Import**</span></span>  
 <span data-ttu-id="50768-125">**[埋め込み]** を選択すると使用できます。</span><span class="sxs-lookup"><span data-stu-id="50768-125">Available when you select **Embedded**.</span></span> <span data-ttu-id="50768-126">**[次の画像を使用]** ボックスの一覧に画像を追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="50768-126">Click to add an image to the **Use this image** drop-down list.</span></span>  
  
 <span data-ttu-id="50768-127">**[次のフィールドを使用]**</span><span class="sxs-lookup"><span data-stu-id="50768-127">**Use this field**</span></span>  
 <span data-ttu-id="50768-128">**[データベース]** を選択すると使用できます。</span><span class="sxs-lookup"><span data-stu-id="50768-128">Available when you select **Database**.</span></span> <span data-ttu-id="50768-129">フィールド名を選択します。</span><span class="sxs-lookup"><span data-stu-id="50768-129">Select the field name.</span></span>  
  
 <span data-ttu-id="50768-130">**[次の MIME の種類を使用]**</span><span class="sxs-lookup"><span data-stu-id="50768-130">**Use this MIME type**</span></span>  
 <span data-ttu-id="50768-131">データベース内に含まれている画像の適切な形式を選択します (たとえば、.bmp、.jpeg、.gif、.png、.x-png など)。</span><span class="sxs-lookup"><span data-stu-id="50768-131">Choose the appropriate format of the pictures contained in the database (for example, .bmp, .jpeg, .gif, .png, or .x-png).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50768-132">参照</span><span class="sxs-lookup"><span data-stu-id="50768-132">See Also</span></span>  
 <span data-ttu-id="50768-133">[レポートアイテムの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50768-133">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="50768-134">[レポートビルダーおよび SSRS&#41;&#40;のテキストとプレースホルダーの書式設定](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50768-134">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="50768-135">画像 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="50768-135">Images &#40;Report Builder and SSRS&#41;</span></span>](report-design/images-report-builder-and-ssrs.md)  
  
  
