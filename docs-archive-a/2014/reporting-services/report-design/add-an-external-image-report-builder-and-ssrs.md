---
title: 外部の画像の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8d0030c8f29b14b2c62048be306daa15948cd8d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712733"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a><span data-ttu-id="58363-102">外部の画像の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="58363-102">Add an External Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="58363-103">外部の画像は、ネイティブ モードまたは SharePoint 統合モードのレポート サーバー上にあるものも、他の Web サイトにあるものもあります。</span><span class="sxs-lookup"><span data-stu-id="58363-103">External images can be on a report server in native mode or SharePoint integrated mode, or on any other Web site.</span></span> <span data-ttu-id="58363-104">外部の画像をレポートに含める場合、その画像が存在すること、およびその画像にアクセスする権限をレポートのリーダーが持っていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58363-104">When you include external images in your report, you must verify that the image exists and that the report reader has permissions to access the image.</span></span> <span data-ttu-id="58363-105">詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](images-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58363-105">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a><span data-ttu-id="58363-106">外部の画像を追加するには</span><span class="sxs-lookup"><span data-stu-id="58363-106">To add an external image</span></span>  
  
1.  <span data-ttu-id="58363-107">レポート デザイン ビューの **[挿入]** タブで、 **[画像]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58363-107">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="58363-108">デザイン画面で、ボックスをクリックし、画像の目的のサイズにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="58363-108">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="58363-109">**[画像のプロパティ]** ダイアログ ボックスの **[全般]** タブにある **[名前]** ボックスに名前を入力するか、既定値を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="58363-109">On the **General** tab of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="58363-110">(省略可) **[ツールヒント]** ボックスに、HTML で表示されたレポートの画像の上にマウスを置いたときに表示されるテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="58363-110">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in a report rendered for HTML.</span></span>  
  
5.  <span data-ttu-id="58363-111">**[画像ソースの選択]** で、 **[外部]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="58363-111">In **Select the image source**, select **External**.</span></span>  
  
     <span data-ttu-id="58363-112">ネイティブ モードのレポート サーバーにある画像を指定する場合は、 **[次の画像を使用]** ボックスに画像の相対パスを入力します (例: ../images/image1.jpg)。</span><span class="sxs-lookup"><span data-stu-id="58363-112">For an image on a report server in native mode, type a relative path to the image in the **Use this image** box-for example, ../images/image1.jpg.</span></span>  
  
     <span data-ttu-id="58363-113">SharePoint 統合モードのレポートサーバーまたはその他の Web サイトの画像の場合は、[**次の画像を使用**] ボックスに画像の完全な URL を入力します (たとえば、http:// \<SharePointservername> / \<site> /Documents/images/image1.jpg)。</span><span class="sxs-lookup"><span data-stu-id="58363-113">For an image on a report server in SharePoint integrated mode, or any other Web site, type a full URL to the image in the **Use this image** box-for example, http://\<SharePointservername>/\<site>/Documents/images/image1.jpg.</span></span>  
  
     <span data-ttu-id="58363-114">詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58363-114">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="58363-115">(省略可) 画像レポート アイテムのその他のプロパティを設定するには、 **[サイズ]** 、 **[表示]** 、 **[アクション]** 、または **[罫線]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="58363-115">(Optional) Click **Size**, **Visibility**, **Action**, or **Border** to set additional properties for the image report item.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58363-116">参照</span><span class="sxs-lookup"><span data-stu-id="58363-116">See Also</span></span>  
 <span data-ttu-id="58363-117">[レポートへの画像の埋め込み &#40;レポート ビルダーおよび SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="58363-117">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="58363-118">[背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="58363-118">[Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="58363-119">[[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="58363-119">[Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
