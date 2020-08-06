---
title: 背景画像の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c777fefb-8695-44a7-b5cd-a18c587583f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7bc15e1b063a73c463cdb1e7e99075af2a3dce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739390"
---
# <a name="add-a-background-image-report-builder-and-ssrs"></a><span data-ttu-id="17b7e-102">背景画像の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="17b7e-102">Add a Background Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="17b7e-103">四角形、テキスト ボックス、一覧、マトリックス、テーブル、グラフの一部などのレポート アイテム、またはページ ヘッダー、ページ フッター、レポート本文などのレポート セクションに背景画像を追加できます。</span><span class="sxs-lookup"><span data-stu-id="17b7e-103">You can add a background image to a report item such as a rectangle, text box, list, matrix, table, and some parts of a chart, or a report section such as the page header, page footer, or report body.</span></span> <span data-ttu-id="17b7e-104">背景画像は、レポート デザイン画面で選択された任意のアイテムでプロパティ ペインに **[BackgroundImage]** が表示されるものに対して定義できます。</span><span class="sxs-lookup"><span data-stu-id="17b7e-104">You can define a background image for any selected item on the report design surface that displays **BackgroundImage** in the Properties pane.</span></span> <span data-ttu-id="17b7e-105">他の画像と同様に、背景画像は、レポート サーバー上の画像、データセット フィールドからの画像、またはレポート定義に埋め込まれた画像などへの URL である場合があります。</span><span class="sxs-lookup"><span data-stu-id="17b7e-105">Like other images, the background image can be a URL to an image on the report server, an image from a dataset field, or an image embedded in the report definition.</span></span> <span data-ttu-id="17b7e-106">レポートに埋め込まれた画像を使用するには、その画像をデザイン画面に追加する前に、それをレポート定義に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17b7e-106">To use an image embedded in the report, you must first add the image to the report definition before you can add the image to the design surface.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-the-report-definition"></a><span data-ttu-id="17b7e-107">レポート定義に画像を埋め込むには</span><span class="sxs-lookup"><span data-stu-id="17b7e-107">To embed an image in the report definition</span></span>  
  
1.  <span data-ttu-id="17b7e-108">レポート データ ペインで **[画像]** ノードを右クリックし、 **[画像の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17b7e-108">In the Report Data pane, right-click the **Images** node, and then click **Add Image**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="17b7e-109">レポート データ ペインが表示されていない場合は、 **[表示]** タブの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17b7e-109">If the Report Data pane is not visible, on the **View** tab, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="17b7e-110">レポート定義に埋め込む画像に移動し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17b7e-110">Navigate to the image you want to embed in your report definition, and then click **OK**.</span></span>  
  
### <a name="to-add-a-background-image"></a><span data-ttu-id="17b7e-111">背景画像を追加するには</span><span class="sxs-lookup"><span data-stu-id="17b7e-111">To add a background image</span></span>  
  
1.  <span data-ttu-id="17b7e-112">レポート デザイン ビューで、背景画像を追加するレポート アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-112">In report design view, select the report item to which you want to add a background image.</span></span>  
  
2.  <span data-ttu-id="17b7e-113">プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-113">If the Properties pane is not visible, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="17b7e-114">プロパティ ペインで、 **[BackgroundImage]** を展開し、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="17b7e-114">In the Properties pane, expand **BackgroundImage**, and then do the following:</span></span>  
  
    -   <span data-ttu-id="17b7e-115">埋め込まれた画像を追加する場合</span><span class="sxs-lookup"><span data-stu-id="17b7e-115">For an embedded image:</span></span>  
  
         <span data-ttu-id="17b7e-116">**[ソース]** を **[埋め込み]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-116">Set **Source** to **Embedded**.</span></span>  
  
         <span data-ttu-id="17b7e-117">**[値]** に、レポートに埋め込まれている画像の名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-117">Set **Value** to the name of an image that is embedded in the report.</span></span>  
  
    -   <span data-ttu-id="17b7e-118">外部の画像を追加する場合</span><span class="sxs-lookup"><span data-stu-id="17b7e-118">For an external image:</span></span>  
  
         <span data-ttu-id="17b7e-119">**[ソース]** を **[外部]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-119">Set **Source** to **External**.</span></span>  
  
         <span data-ttu-id="17b7e-120">**[値]** に画像への有効なパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-120">Set **Value** to a valid path to an image.</span></span> <span data-ttu-id="17b7e-121">これは、ネイティブ モードまたは SharePoint 統合モードのレポート サーバー上にあるものも、他の Web サイトにあるものもあります。</span><span class="sxs-lookup"><span data-stu-id="17b7e-121">This can be on a report server in native mode or SharePoint integrated mode, or it can be on any other Web site.</span></span> <span data-ttu-id="17b7e-122">詳細については、「[外部の画像の追加 (レポート ビルダーおよび SSRS)](add-an-external-image-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17b7e-122">For more information, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
    -   <span data-ttu-id="17b7e-123">レポート アイテムの接続先データベースのフィールドに格納されている画像を追加する場合</span><span class="sxs-lookup"><span data-stu-id="17b7e-123">For an image is that is contained in a field in the database to which the report item is connected:</span></span>  
  
         <span data-ttu-id="17b7e-124">**[ソース]** を **[データベース]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-124">Set **Source** to **Database**.</span></span>  
  
         <span data-ttu-id="17b7e-125">**[値]** に、レポート データセット内のフィールドの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-125">Set **Value** to the name of a field in the report dataset.</span></span> <span data-ttu-id="17b7e-126">詳細については、「[データバインド画像の追加 (レポート ビルダーおよび SSRS)](add-a-data-bound-image-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17b7e-126">For more information, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="17b7e-127">**[MIMEType]** 、またはファイル形式には、画像に適切な MIME の種類を選択します (bmp など)。</span><span class="sxs-lookup"><span data-stu-id="17b7e-127">For **MIMEType**, or file format, select the appropriate MIME type for the image-for example, .bmp.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="17b7e-128">**[Source]** プロパティが **[Database]** に設定されている場合にのみ、[MIMEType] が適用されます。</span><span class="sxs-lookup"><span data-stu-id="17b7e-128">MIMEType applies only if the **Source** property is set to **Database**.</span></span> <span data-ttu-id="17b7e-129">**[Source]** プロパティが **[External]** または **[Embedded]** に設定されている場合、 **[MIMEType]** の値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="17b7e-129">If the **Source** property is set to **External** or **Embedded**, the value of **MIMEType** is ignored.</span></span>  
  
    -   <span data-ttu-id="17b7e-130">**[BackgroundRepeat]** で、式、 **[Default]** 、 **[Repeat]** 、 **[RepeatX]** または **[RepeatY]** 、または **[Clip]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17b7e-130">For **BackgroundRepeat**, select an expression, **Default**, **Repeat**, **RepeatX**, or **RepeatY**, or **Clip**.</span></span>  
  
         <span data-ttu-id="17b7e-131">グラフ内の背景画像の場合は、 **[BackgroundRepeat]** を **[Default]** 、 **[Repeat]** 、 **[Fit]** 、および **[Clip]** に設定できますが、 **[RepeatX]** または **[RepeatY]** には設定できません。</span><span class="sxs-lookup"><span data-stu-id="17b7e-131">For background images in a chart, **BackgroundRepeat** can be set to **Default**, **Repeat**, **Fit**, and **Clip**, but not **RepeatX** or **RepeatY**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b7e-132">参照</span><span class="sxs-lookup"><span data-stu-id="17b7e-132">See Also</span></span>  
 <span data-ttu-id="17b7e-133">[画像 &#40;レポート ビルダーおよび SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="17b7e-133">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="17b7e-134">[[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="17b7e-134">[Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
