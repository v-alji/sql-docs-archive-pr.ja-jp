---
title: データバインド画像の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea85bdcd6eab04ff51c879a9e790b6e12f73a771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631560"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a><span data-ttu-id="e403e-102">データバインド画像の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e403e-102">Add a Data-Bound Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e403e-103">レポートには、データベースに保存されている画像への参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e403e-103">A report can include a reference to an image that is stored in a database.</span></span> <span data-ttu-id="e403e-104">このような画像を *データバインド画像*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="e403e-104">Such an image is known as a *data-bound image*.</span></span> <span data-ttu-id="e403e-105">たとえば、製品一覧で製品名と合わせて表示される画像はデータバインド画像です。</span><span class="sxs-lookup"><span data-stu-id="e403e-105">The pictures that appear alongside product names in a product list are examples of data-bound images.</span></span>  
  
 <span data-ttu-id="e403e-106">データバインド画像をページ ヘッダーまたはページ フッターに追加するには、別の手順が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e403e-106">Adding a data-bound image to a page header or page footer requires additional steps.</span></span> <span data-ttu-id="e403e-107">詳細については、「[ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e403e-107">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a><span data-ttu-id="e403e-108">データバインド画像を追加するには</span><span class="sxs-lookup"><span data-stu-id="e403e-108">To add a data-bound image</span></span>  
  
1.  <span data-ttu-id="e403e-109">レポート デザイン ビューで、データ ソース接続のあるテーブル、および画像のバイナリ データを含むフィールドのあるデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="e403e-109">In report design view, create a table with a data source connection and a dataset with a field that contains binary image data.</span></span> <span data-ttu-id="e403e-110">詳細については、「[テーブル &#40;レポート ビルダーおよび SSRS& #41;](tables-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e403e-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="e403e-111">テーブルに列を挿入します。</span><span class="sxs-lookup"><span data-stu-id="e403e-111">Insert a column in your table.</span></span> <span data-ttu-id="e403e-112">詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e403e-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="e403e-113">**[挿入]** メニューで **[画像]** をクリックし、新しい列のデータ行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e403e-113">On the **Insert** menu, click **Image**, and then click in the data row of the new column.</span></span>  
  
4.  <span data-ttu-id="e403e-114">**[画像のプロパティ]** ダイアログ ボックスの [全般] ページにある **[名前]** ボックスに名前を入力するか、既定値を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="e403e-114">On the General page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
5.  <span data-ttu-id="e403e-115">(省略可) **[ツールヒント]** ボックスに、HTML で表示されたレポートの画像の上にマウスを置いたときに表示されるテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="e403e-115">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in the report rendered for HTML.</span></span>  
  
6.  <span data-ttu-id="e403e-116">**[画像ソースの選択]** で、 **[データベース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e403e-116">In **Select the image source**, select **Database**.</span></span>  
  
7.  <span data-ttu-id="e403e-117">**[次のフィールドを使用]** で、レポート内の画像を含むフィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="e403e-117">In **Use this Field**, select the field that contains images in your report.</span></span>  
  
8.  <span data-ttu-id="e403e-118">**[次の MIME の種類を使用]** で、画像の MIME の種類またはファイル形式を選択します (bmp など)。</span><span class="sxs-lookup"><span data-stu-id="e403e-118">In **Use this MIME type**, select the MIME type, or file format, of the image-for example, bmp.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="e403e-119">画像のプレースホルダーがレポート デザイン画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e403e-119">An image placeholder appears on the report design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e403e-120">参照</span><span class="sxs-lookup"><span data-stu-id="e403e-120">See Also</span></span>  
 <span data-ttu-id="e403e-121">[画像 &#40;レポート ビルダーおよび SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e403e-121">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e403e-122">[レポートへの画像の埋め込み &#40;レポート ビルダーおよび SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e403e-122">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e403e-123">[外部の画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e403e-123">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e403e-124">[[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="e403e-124">[Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
