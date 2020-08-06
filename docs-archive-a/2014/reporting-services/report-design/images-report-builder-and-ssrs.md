---
title: 画像 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fcc2db5c-5c26-4607-ae2b-f65c80360536
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f0840a10cc1082ba8dc7912862f7cf34c64972d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713865"
---
# <a name="images-report-builder-and-ssrs"></a><span data-ttu-id="61ce9-102">画像 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="61ce9-102">Images (Report Builder and SSRS)</span></span>
  <span data-ttu-id="61ce9-103">画像は、レポート内に埋め込まれている画像、データベースに格納されている画像、レポート サーバー上に格納されている画像、または Web 上の他の場所に格納されている画像への参照を保持するレポート アイテムです。</span><span class="sxs-lookup"><span data-stu-id="61ce9-103">An image is a report item that contains a reference to an image that is embedded in the report, stored in a database, stored on the report server, or stored elsewhere on the Web.</span></span> <span data-ttu-id="61ce9-104">画像は、行データとして繰り返し使用されるピクチャである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="61ce9-104">An image can be a picture that is repeated with rows of data.</span></span> <span data-ttu-id="61ce9-105">画像は、任意のレポート アイテムの背景としても使用できます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-105">You can also use an image as a background for certain report items.</span></span>  
  
 <span data-ttu-id="61ce9-106">サーバーにロゴを保存すると、多くのレポートで同じロゴを使用できるので効果的です。</span><span class="sxs-lookup"><span data-stu-id="61ce9-106">Storing logos on a server is a good idea because you can use the same logo in many reports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="comparing-external-embedded-and-data-bound-images"></a><a name="ComparingImages"></a> <span data-ttu-id="61ce9-107">外部の画像、埋め込み画像、およびデータバインド画像の比較</span><span class="sxs-lookup"><span data-stu-id="61ce9-107">Comparing External, Embedded, and Data-Bound Images</span></span>  
 <span data-ttu-id="61ce9-108">サーバーベースの画像やその他の外部の画像をレポートで使用している場合は、この画像アイテムにはレポート サーバー上または Web 上の任意の場所にある画像を指すパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-108">When you use a server-based or other external image in a report, the image item contains a path that points to an image on the report server or wherever it exists on the Web.</span></span> <span data-ttu-id="61ce9-109">ただし、埋め込み画像を使用する場合は、画像データをレポート定義内に格納し、別ファイルとしては保持しません。</span><span class="sxs-lookup"><span data-stu-id="61ce9-109">When you use an embedded image, however, the image data is stored within the report definition and does not exist as a separate file.</span></span>  
  
 <span data-ttu-id="61ce9-110">サーバーベースの画像は、複数のレポートや Web ページで共有されるロゴや静的ピクチャに適しています。</span><span class="sxs-lookup"><span data-stu-id="61ce9-110">Server-based images work well for logos and static pictures that are shared among several reports or Web pages.</span></span> <span data-ttu-id="61ce9-111">埋め込み画像を使用した場合は、常に確実に画像がレポートで利用できるようになりますが、共有はできません。</span><span class="sxs-lookup"><span data-stu-id="61ce9-111">Embedded images ensure that the images are always available to the report, but they cannot be shared.</span></span> <span data-ttu-id="61ce9-112">外部の画像を使用しているレポート定義の方が、埋め込み画像を使用しているレポート定義よりもサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="61ce9-112">Report definitions with external images are smaller than definitions with embedded images.</span></span>  
  
 <span data-ttu-id="61ce9-113">また、データバインド画像は、データベースに格納されているバイナリ データからも表示できます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-113">Data-bound images can also be displayed from binary data stored in a database.</span></span> <span data-ttu-id="61ce9-114">たとえば、製品一覧で製品名と合わせて表示されるピクチャはデータベース画像です。</span><span class="sxs-lookup"><span data-stu-id="61ce9-114">For example, the pictures that appear alongside product names in a product list are database images.</span></span> <span data-ttu-id="61ce9-115">次の図では、自転車の画像はデータベースに保存され、各製品を図示するためにレポートで取得されます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-115">In the following picture, the images of bicycles are stored in a database and retrieved in the report to illustrate each product.</span></span>  
  
 <span data-ttu-id="61ce9-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span><span class="sxs-lookup"><span data-stu-id="61ce9-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span></span>  
  

  
##  <a name="images-as-report-parts"></a><a name="ImagesReportParts"></a> <span data-ttu-id="61ce9-117">レポート パーツとしての画像</span><span class="sxs-lookup"><span data-stu-id="61ce9-117">Images as Report Parts</span></span>  
 <span data-ttu-id="61ce9-118">画像は、レポート パーツとしてレポートとは別に保存できます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-118">You can save images separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 
  
##  <a name="embedding-images"></a><a name="EmbedImages"></a> <span data-ttu-id="61ce9-119">埋め込み画像</span><span class="sxs-lookup"><span data-stu-id="61ce9-119">Embedding Images</span></span>  
 <span data-ttu-id="61ce9-120">レポートに画像を埋め込み、すべての画像データがレポート定義内に格納されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-120">You can embed images in a report so that all image data is stored within the report definition.</span></span> <span data-ttu-id="61ce9-121">画像を埋め込む場合は、画像が MIME でエンコードされ、テキストとしてレポート定義に格納されます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-121">When you embed an image, the image is MIME-encoded and stored as text in the report definition.</span></span> <span data-ttu-id="61ce9-122">埋め込み画像を使用すると、常に確実に画像がレポートで利用できるようになりますが、レポート定義のサイズが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="61ce9-122">Using an embedded image ensures that the image is always available to the report, but it also increases the size of the report definition.</span></span>  
  
 <span data-ttu-id="61ce9-123">画像の埋め込みの詳細については、「 [レポートへの画像の埋め込み &#40;レポート ビルダーおよび SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61ce9-123">For more information about embedding an image, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="external-images"></a><a name="ExternalImages"></a> <span data-ttu-id="61ce9-124">外部の画像</span><span class="sxs-lookup"><span data-stu-id="61ce9-124">External Images</span></span>  
 <span data-ttu-id="61ce9-125">画像に URL を指定することにより、レポートに格納された画像を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-125">You can include stored images in a report by specifying a URL to the image.</span></span> <span data-ttu-id="61ce9-126">レポートで外部の画像を使用する場合、画像ソースは `External` に設定され、この画像の値は画像の URL アドレスまたはパスになります。</span><span class="sxs-lookup"><span data-stu-id="61ce9-126">When you use an external image in a report, the image source is set to `External` and the value for the image is the URL address or path to the image.</span></span>  
  
 <span data-ttu-id="61ce9-127">詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61ce9-127">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="61ce9-128">レポート ビルダーまたはレポート デザイナーでレポートを実行すると、ユーザーの資格情報を使用して画像が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-128">When the report is run in Report Builder or Report Designer, preview uses the credentials of the user to display the image.</span></span> <span data-ttu-id="61ce9-129">レポート サーバーでレポートを実行する場合、画像にアクセスするための十分なサーバー資格情報がないとレポートの画像を表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="61ce9-129">When the report is run on the report server, the image in the report may not be displayed if the server credentials are not sufficient to access the image.</span></span> <span data-ttu-id="61ce9-130">その場合は、システム管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="61ce9-130">In that case, contact your system administrator.</span></span>  
  
 <span data-ttu-id="61ce9-131">外部の画像をレポートに追加する方法について詳しくは、「 [外部の画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61ce9-131">For more information about adding an external image to a report, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="background-images"></a><a name="BackgroundImages"></a> <span data-ttu-id="61ce9-132">背景画像</span><span class="sxs-lookup"><span data-stu-id="61ce9-132">Background Images</span></span>  
 <span data-ttu-id="61ce9-133">画像は、レポート本文や四角形、テキスト ボックス、一覧、マトリックス、テーブルの背景画像としても使用できます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-133">You can use an image as a background image in the body of the report or in a rectangle, text box, list, matrix, or table.</span></span> <span data-ttu-id="61ce9-134">背景画像と画像には、同じようなプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="61ce9-134">A background image and an image have similar properties.</span></span> <span data-ttu-id="61ce9-135">アイテムの背景を埋めるために、画像を繰り返す方法も指定できます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-135">You can also specify how the image is repeated to fill the background of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61ce9-136">HTML 表示拡張機能などのいくつかの表示拡張機能では、レポート本文用の背景画像が本文、ページ ヘッダー、ページ フッター内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-136">Some rendering extensions, like the HTML rendering extension, render the background image for the report body in the body, the page header, and the page footer.</span></span> <span data-ttu-id="61ce9-137">ページ ヘッダーおよびページ フッター用にそれぞれ別の背景画像を定義できますが、画像を定義しない場合は、本文の背景画像が使用されます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-137">You can define a separate background image for the page header and footer, but if no image is defined, the report uses the background image of the body.</span></span> <span data-ttu-id="61ce9-138">画像表示拡張機能などの他の表示拡張機能では、ページ ヘッダーおよびページ フッターに本文の背景画像は表示されません。</span><span class="sxs-lookup"><span data-stu-id="61ce9-138">Other rendering extensions, like the Image rendering extension, do not render the body background image in the page header and footer.</span></span>  
  
 <span data-ttu-id="61ce9-139">背景画像を追加する方法について詳しくは、「 [背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61ce9-139">For more information about adding a background image, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="data-bound-images"></a><a name="DataboundImages"></a> <span data-ttu-id="61ce9-140">データバインド画像</span><span class="sxs-lookup"><span data-stu-id="61ce9-140">Data-bound Images</span></span>  
 <span data-ttu-id="61ce9-141">データベースに格納されている画像をレポートに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="61ce9-141">You can add images that are stored in a database to your report.</span></span> <span data-ttu-id="61ce9-142">静的画像に使用したものと同じ画像レポート アイテムを使用しますが、画像がデータベースに格納されていることを示すプロパティ セットと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="61ce9-142">You use the same image report item as the one used for static images, but with a set of properties that indicate that the image is stored in a database.</span></span> <span data-ttu-id="61ce9-143">データバインド画像の処理については、「 [データバインド画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61ce9-143">To view instructions about working with data-bound images, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="61ce9-144">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="61ce9-144">How-to Topics</span></span>  
 [<span data-ttu-id="61ce9-145">外部の画像の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61ce9-145">Add an External Image &#40;Report Builder and SSRS&#41;</span></span>](add-an-external-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="61ce9-146">レポートへの画像の埋め込み &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61ce9-146">Embed an Image in a Report &#40;Report Builder and SSRS&#41;</span></span>](embed-an-image-in-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="61ce9-147">背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61ce9-147">Add a Background Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-background-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="61ce9-148">データバインド画像の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61ce9-148">Add a Data-Bound Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-data-bound-image-report-builder-and-ssrs.md)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="61ce9-149">参照</span><span class="sxs-lookup"><span data-stu-id="61ce9-149">See Also</span></span>  
 <span data-ttu-id="61ce9-150">[画像ファイルへのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="61ce9-150">[Exporting to an Image File &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="61ce9-151">レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61ce9-151">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
