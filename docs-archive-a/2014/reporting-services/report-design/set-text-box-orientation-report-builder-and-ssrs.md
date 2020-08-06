---
title: テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d509f1df29203fa5def79b61b74ae9db8f40d204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631538"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a><span data-ttu-id="2812f-102">テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2812f-102">Set Text Box Orientation (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2812f-103">テキスト ボックスの方向には、水平、垂直 (テキストを上から下に配置)、または 270°回転 (テキストを下から上に配置) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2812f-103">A text box can be oriented in different directions: horizontally, vertically (text reading from top to bottom), or rotated by 270 degrees (text reading from bottom to top).</span></span> <span data-ttu-id="2812f-104">方向はテキストではなくテキスト ボックスに設定されるため、そのテキスト ボックス内のすべてのテキストにその方向が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2812f-104">Because orientation is set on the text box not the text, the orientation applies to all the text in the text box.</span></span> <span data-ttu-id="2812f-105">テキストの一部のみに異なる方向を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="2812f-105">You cannot specify different orientations for parts of the text.</span></span> <span data-ttu-id="2812f-106">回転したテキストに合わせて、列の幅と行の高さを手動で調整してください。</span><span class="sxs-lookup"><span data-stu-id="2812f-106">Size the column width and the row height manually to accommodate the rotated text.</span></span>  
  
 <span data-ttu-id="2812f-107">テキストの向きを指定するために使用する WritingMode プロパティは、[**テキストボックスのプロパティ**] ダイアログボックスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2812f-107">The WritingMode property, which you use to specify text orientation, is not available in the **Text Box Properties** dialog box.</span></span> <span data-ttu-id="2812f-108">この場合、プロパティ ペインを開き、そこでプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2812f-108">You need to open the Properties pane and set the property there.</span></span> <span data-ttu-id="2812f-109">WritingMode プロパティに使用できる値は、**水平**(左から右へのテキストの読み取り)、**縦**(テキストの上から下)、 **Rotate270** (テキストを下から上に読む) です。</span><span class="sxs-lookup"><span data-stu-id="2812f-109">The available values for the WritingMode property are **Horizontal** (text reading left to right), **Vertical** (text reading top to bottom), **Rotate270** (text reading bottom to top).</span></span> <span data-ttu-id="2812f-110">テキストに合わせて、列の幅と行の高さを手動で調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2812f-110">You must manually size the column width and the row height to accommodate the text.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a><span data-ttu-id="2812f-111">テキストの方向を指定する方法</span><span class="sxs-lookup"><span data-stu-id="2812f-111">To set text orientation</span></span>  
  
1.  <span data-ttu-id="2812f-112">レポートを新規作成するか、既存のレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2812f-112">Create a new report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="2812f-113">プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2812f-113">If the Properties pane is not open, click the **View** tab and select the **Properties** check box.</span></span>  
  
3.  <span data-ttu-id="2812f-114">変更を加えるテキスト ボックスをクリックし、テキスト ボックスの方向を変更します。</span><span class="sxs-lookup"><span data-stu-id="2812f-114">Click the text box for which you want to change text orientation.</span></span>  
  
4.  <span data-ttu-id="2812f-115">[プロパティ] ペインの [WritingMode] プロパティを見つけ、ドロップダウンリストで、テキストボックスに適用するテキストの方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="2812f-115">Locate the WritingMode property in the Properties pane and in the drop-down list select the text orientation to apply to the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2812f-116">プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、 **[ローカライズ]** カテゴリ内にあります。</span><span class="sxs-lookup"><span data-stu-id="2812f-116">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span>  
  
5.  <span data-ttu-id="2812f-117">リスト ボックスで **[横]**、 **[縦]**、 **[270 度回転]** のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="2812f-117">In the list box, select **Horizontal**, **Vertical**, or **Rotate270**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2812f-118">参照</span><span class="sxs-lookup"><span data-stu-id="2812f-118">See Also</span></span>  
 <span data-ttu-id="2812f-119">[テキストボックス &#40;レポートビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2812f-119">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2812f-120">チュートリアル: テキストの書式設定 &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="2812f-120">Tutorial: Format Text &#40;Report Builder&#41;</span></span>](../tutorial-format-text-report-builder.md)  
  
  
