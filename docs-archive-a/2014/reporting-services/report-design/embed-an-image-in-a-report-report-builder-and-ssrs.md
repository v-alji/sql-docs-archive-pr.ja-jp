---
title: レポートへの画像の埋め込み (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.embeddedimages.f1
- "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6599092e0ef37dd9bbc15f4815c0315c77e7943b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711725"
---
# <a name="embed-an-image-in-a-report-report-builder-and-ssrs"></a><span data-ttu-id="80778-102">レポートへの画像の埋め込み (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="80778-102">Embed an Image in a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="80778-103">レポートには、画像を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="80778-103">A report can include an embedded image.</span></span> <span data-ttu-id="80778-104">画像の埋め込みには、レポートの画像を常に利用可能な状態にできるというメリットはありますが、レポート定義 (レポートを定義するファイル) のサイズは大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80778-104">Embedding an image ensures that the image is always available to a report, but can affect the size of the report definition, the file that defines the report.</span></span> <span data-ttu-id="80778-105">レポートに埋め込まれた画像は、レポート データ ペインに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="80778-105">The images embedded in a report are listed in the Report Data pane.</span></span>  
  
 <span data-ttu-id="80778-106">デザイン画面に画像を追加する前にレポート定義に画像を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="80778-106">You might want to embed an image in the report definition before adding the image to the design surface.</span></span> <span data-ttu-id="80778-107">詳細については、「[背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80778-107">For more information, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-a-report"></a><span data-ttu-id="80778-108">レポートに画像を埋め込むには</span><span class="sxs-lookup"><span data-stu-id="80778-108">To embed an image in a report</span></span>  
  
1.  <span data-ttu-id="80778-109">レポート デザイン ビューの **[挿入]** タブで、 **[画像]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80778-109">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="80778-110">デザイン画面で、ボックスをクリックし、画像の目的のサイズにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="80778-110">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="80778-111">**[画像のプロパティ]** ダイアログ ボックスの **[全般]** ページにある **[名前]** ボックスに名前を入力するか、既定値を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="80778-111">In the **General** page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="80778-112">(省略化) **[ツールヒント]** ボックスで、ユーザーが表示レポートの画像の上にマウスを置いたときに表示されるテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="80778-112">(Optional) In the **ToolTip** text box, type the text that you want to appear when the user hovers over the image in the rendered report.</span></span>  
  
5.  <span data-ttu-id="80778-113">**[画像ソースの選択]** で、 **[埋め込み]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="80778-113">In **Select the image source**, select **Embedded**.</span></span>  
  
6.  <span data-ttu-id="80778-114">**[次の画像を使用]** ボックスの横にある **[インポート]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80778-114">Click the **Import** button next to the **Use this image** text box</span></span>  
  
7.  <span data-ttu-id="80778-115">**[ファイルの種類]** で画像ファイルの種類を選択し、ファイルに移動し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80778-115">In **Files of type**, select the image file type, navigate to the file, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="80778-116">**[画像のプロパティ]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80778-116">In the **Image Properties** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="80778-117">デザイン画面に描画したボックス内に画像が表示され、レポート データ ペインの [画像] フォルダー内にファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80778-117">The image is displayed in the box you drew on the design surface, and the file is displayed under the Images folder in the Report Data pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80778-118">また、MIME の種類 (例 : bmp) は、画像がインポートされるときに自動的に取得されます。</span><span class="sxs-lookup"><span data-stu-id="80778-118">The MIME type (for example, bmp) is derived automatically when the image is imported.</span></span> <span data-ttu-id="80778-119">MIME の種類を変更するには、次の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80778-119">To change the MIME type, see the next procedure.</span></span>  
  
### <a name="optional-to-change-the-mime-type-of-an-imported-image"></a><span data-ttu-id="80778-120">(省略可) インポートされた画像の MIME の種類を変更するには</span><span class="sxs-lookup"><span data-stu-id="80778-120">(optional) To change the MIME type of an imported image</span></span>  
  
1.  <span data-ttu-id="80778-121">[デザイン] ビューでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="80778-121">Open the report in Design view.</span></span>  
  
2.  <span data-ttu-id="80778-122">デザイン画面で画像を選択します。</span><span class="sxs-lookup"><span data-stu-id="80778-122">Select the image on the design surface.</span></span> <span data-ttu-id="80778-123">**プロパティ** ペインに画像のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="80778-123">The **Properties** pane displays the image properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80778-124">プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80778-124">If the Properties pane is not visible, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="80778-125">**[MIMEType]** プロパティの横にあるボックス内をクリックし、ボックスの一覧から新しい MIME の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="80778-125">Click in the text box next to the **MIMEType** property and select a new MIME type from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80778-126">参照</span><span class="sxs-lookup"><span data-stu-id="80778-126">See Also</span></span>  
 <span data-ttu-id="80778-127">[画像 &#40;レポート ビルダーおよび SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80778-127">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="80778-128">[データバインド画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80778-128">[Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="80778-129">[[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="80778-129">[Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
