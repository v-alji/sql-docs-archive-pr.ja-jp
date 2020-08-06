---
title: レポートへの HTML の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 605c84843d62fb664a8a665a3fc3b024f8f87186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737957"
---
# <a name="add-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="ab341-102">レポートへの HTML の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ab341-102">Add HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ab341-103">レポートでプレースホルダーを使用すると、データセットのフィールドから HTML をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="ab341-103">Using a placeholder, you can import HTML from a field in your dataset for use in the report.</span></span> <span data-ttu-id="ab341-104">既定のプレースホルダーはプレーン テキストを表すため、プレースホルダーのマークアップ タイプを HTML に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab341-104">By default, a placeholder represents plain text, so you will need to change the placeholder mark-up type to HTML.</span></span> <span data-ttu-id="ab341-105">詳細については、[「レポートへの HTML のインポート &#40;レポート ビルダーおよび SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab341-105">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-html-from-a-field-in-your-dataset-into-a-text-box"></a><span data-ttu-id="ab341-106">データセットのフィールドからテキスト ボックスに HTML を追加するには</span><span class="sxs-lookup"><span data-stu-id="ab341-106">To add HTML from a field in your dataset into a text box</span></span>  
  
1.  <span data-ttu-id="ab341-107">**[挿入]** タブの **[一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab341-107">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="ab341-108">デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ab341-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
     <span data-ttu-id="ab341-109">**[データセットのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab341-109">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="ab341-110">共有データセットまたはレポートに埋め込まれたデータセットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab341-110">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="ab341-111">詳細については、「[[クエリ] ([データセットのプロパティ] ダイアログ ボックス) &#40;レポート ビルダー&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md)」または「[[クエリ] ([データセットのプロパティ] ダイアログ ボックス)](../dataset-properties-dialog-box-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab341-111">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="ab341-112">**[挿入]** タブの **[テキスト ボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab341-112">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="ab341-113">一覧内をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ab341-113">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="ab341-114">データセットからテキスト ボックスに HTML フィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ab341-114">Drag an HTML field from your dataset into the text box.</span></span> <span data-ttu-id="ab341-115">フィールドに対してプレースホルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab341-115">A placeholder is created for your field.</span></span>  
  
4.  <span data-ttu-id="ab341-116">プレースホルダーを右クリックし、 **[プレースホルダーのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab341-116">Right-click the placeholder, and then click **Placeholder Properties**.</span></span>  
  
5.  <span data-ttu-id="ab341-117">**[全般]** タブの **[値]** ボックスに、手順 3 でドロップしたフィールドを評価する式が入力されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab341-117">On the **General** tab, verify that the **Value** box contains an expression that evaluates to the field you dropped in step 3.</span></span>  
  
6.  <span data-ttu-id="ab341-118">**[HTML - HTML タグをスタイルとして解釈]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab341-118">Click **HTML - Interpret HTML tags as styles**.</span></span> <span data-ttu-id="ab341-119">これで、フィールドが HTML として評価されます。</span><span class="sxs-lookup"><span data-stu-id="ab341-119">This causes the field to be evaluated as HTML.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab341-120">参照</span><span class="sxs-lookup"><span data-stu-id="ab341-120">See Also</span></span>  
 <span data-ttu-id="ab341-121">[数値と日付の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab341-121">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ab341-122">[線、色、および画像の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab341-122">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ab341-123">[[全般] ([プレースホルダーのプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="ab341-123">[Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)</span></span>  
  
  
