---
title: '[属性データの翻訳] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
author: minewiskan
ms.author: owend
ms.openlocfilehash: b61022ec2cb8726fc034e13a0d63e432df6ec151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633631"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="4cd23-102">[属性データの翻訳] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="4cd23-102">Attribute Data Translation Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4cd23-103">**[属性データの翻訳]** ダイアログ ボックスを使用すると、翻訳キャプション データを含んでいる列を設定でき、翻訳済みデータと共に使用する照合順序と並べ替え順も設定できます。</span><span class="sxs-lookup"><span data-stu-id="4cd23-103">Use the **Attribute Data Translation** dialog box to set the column that contains the translation caption data, as well as the collation and sort order to be used with the translated data.</span></span> <span data-ttu-id="4cd23-104">**[属性データの翻訳]** ダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4cd23-104">You can display the **Attribute Data Translation** dialog box by:</span></span>  
  
-   <span data-ttu-id="4cd23-105">**ディメンション デザイナー** の **[翻訳]** タブの **[ツール バー]** ペインで **[新しいキャプション列]** または **[キャプション列の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cd23-105">Clicking **New caption column** or **Edit caption column** from the **Toolbar** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="4cd23-106">**ディメンション デザイナー** の **[翻訳]** タブの翻訳の **詳細ペイン** を右クリックし、 **[新しいキャプション列]** または **[キャプション列の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4cd23-106">Right-clicking the **Translation Details** pane on the **Translations** tab of **Dimension Designer** and selecting **New caption column** or **Edit caption column**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4cd23-107">Options</span><span class="sxs-lookup"><span data-stu-id="4cd23-107">Options</span></span>  
 <span data-ttu-id="4cd23-108">**属性**</span><span class="sxs-lookup"><span data-stu-id="4cd23-108">**Attribute**</span></span>  
 <span data-ttu-id="4cd23-109">選択した属性を表示します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-109">Displays the selected attribute.</span></span>  
  
 <span data-ttu-id="4cd23-110">**Language**</span><span class="sxs-lookup"><span data-stu-id="4cd23-110">**Language**</span></span>  
 <span data-ttu-id="4cd23-111">選択した言語を表示します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-111">Displays the selected language.</span></span>  
  
 <span data-ttu-id="4cd23-112">**[キャプションの翻訳]**</span><span class="sxs-lookup"><span data-stu-id="4cd23-112">**Translated caption**</span></span>  
 <span data-ttu-id="4cd23-113">選択した属性の現在翻訳されているキャプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-113">Sets the current translated caption for the selected attribute.</span></span>  
  
 <span data-ttu-id="4cd23-114">**[翻訳列]**</span><span class="sxs-lookup"><span data-stu-id="4cd23-114">**Translation columns**</span></span>  
 <span data-ttu-id="4cd23-115">翻訳キャプション データが格納されている列を設定します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-115">Sets the column where the translation caption data is stored.</span></span> <span data-ttu-id="4cd23-116">1 つの列のみを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4cd23-116">Only one column can be selected.</span></span> <span data-ttu-id="4cd23-117">プライマリ ディメンション テーブルによって参照されるすべての関連するテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4cd23-117">All related tables that are referred to by the primary dimension table will be displayed.</span></span>  
  
 <span data-ttu-id="4cd23-118">**[照合順序指定子]**</span><span class="sxs-lookup"><span data-stu-id="4cd23-118">**Collation designator**</span></span>  
 <span data-ttu-id="4cd23-119">選択した属性の照合順序指定子を設定します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-119">Sets the collation designator for the selected attribute.</span></span> <span data-ttu-id="4cd23-120">既定では、現在の Windows 照合順序が選択されています。</span><span class="sxs-lookup"><span data-stu-id="4cd23-120">By default, the current Windows collation is selected.</span></span> <span data-ttu-id="4cd23-121">下矢印をクリックして、使用可能な照合順序から選択します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-121">Click the down arrow to select from the available collations.</span></span>  
  
 <span data-ttu-id="4cd23-122">**Binary**</span><span class="sxs-lookup"><span data-stu-id="4cd23-122">**Binary**</span></span>  
 <span data-ttu-id="4cd23-123">このオプションを選択すると、文字ごとに定義されたビット パターンに基づいてデータの並べ替えと比較を行います。</span><span class="sxs-lookup"><span data-stu-id="4cd23-123">Select this option to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="4cd23-124">バイナリの並べ替え順では大文字と小文字が区別されるため、小文字は大文字より前に配置されます。また、アクセントも区別されます。</span><span class="sxs-lookup"><span data-stu-id="4cd23-124">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="4cd23-125">これは、最速の並べ替え順です。</span><span class="sxs-lookup"><span data-stu-id="4cd23-125">This is the fastest sorting order.</span></span>  
  
 <span data-ttu-id="4cd23-126">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には関連する言語またはアルファベットの辞書で定義されている並べ替えおよび比較ルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4cd23-126">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd23-127">このオプションが選択されている場合、 **[大文字と小文字を区別する]**、 **[アクセントを区別する]**、 **[かなを区別する]**、および **[文字幅を区別する]** オプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="4cd23-127">If this option is selected, the **Case sensitive**, **Accent sensitive**, **Kana sensitive**, and **Width sensitive** options are disabled.</span></span>  
  
 <span data-ttu-id="4cd23-128">**大文字と小文字を区別する**</span><span class="sxs-lookup"><span data-stu-id="4cd23-128">**Case sensitive**</span></span>  
 <span data-ttu-id="4cd23-129">このオプションを選択すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、大文字と小文字による区別を行います。</span><span class="sxs-lookup"><span data-stu-id="4cd23-129">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
 <span data-ttu-id="4cd23-130">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="4cd23-130">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="4cd23-131">大文字と小文字を区別するかどうかは、大文字小文字を**区別**するかどうかを定義しません。</span><span class="sxs-lookup"><span data-stu-id="4cd23-131">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
 <span data-ttu-id="4cd23-132">**アクセントを区別する**</span><span class="sxs-lookup"><span data-stu-id="4cd23-132">**Accent sensitive**</span></span>  
 <span data-ttu-id="4cd23-133">このオプションを選択すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、アクセント符号が付いた文字と付いていない文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-133">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="4cd23-134">たとえば、'a' と '&#xE1;' は等しくありません。</span><span class="sxs-lookup"><span data-stu-id="4cd23-134">For example, 'a' is not equal to 'á'.</span></span>  
  
 <span data-ttu-id="4cd23-135">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はアクセント符号の付いた文字と付いていない文字を同じものと見なします。</span><span class="sxs-lookup"><span data-stu-id="4cd23-135">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
 <span data-ttu-id="4cd23-136">**[かなを区別する]**</span><span class="sxs-lookup"><span data-stu-id="4cd23-136">**Kana sensitive**</span></span>  
 <span data-ttu-id="4cd23-137">このオプションを選択して、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、ひらがなとカタカナという日本語の 2 種類のかな文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-137">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
 <span data-ttu-id="4cd23-138">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はひらがなとカタカナを同じものと見なします。</span><span class="sxs-lookup"><span data-stu-id="4cd23-138">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
 <span data-ttu-id="4cd23-139">**[文字幅を区別する]**</span><span class="sxs-lookup"><span data-stu-id="4cd23-139">**Width sensitive**</span></span>  
 <span data-ttu-id="4cd23-140">このオプションを選択すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、1 バイト文字 (半角文字) と同じ文字の 2 バイト表現 (全角文字) とを区別します。</span><span class="sxs-lookup"><span data-stu-id="4cd23-140">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
 <span data-ttu-id="4cd23-141">このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は同じ文字の 1 バイト表現と 2 バイト表現を同じものと見なします。</span><span class="sxs-lookup"><span data-stu-id="4cd23-141">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd23-142">参照</span><span class="sxs-lookup"><span data-stu-id="4cd23-142">See Also</span></span>  
 <span data-ttu-id="4cd23-143">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4cd23-143">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4cd23-144">[翻訳の詳細 &#40;翻訳] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="4cd23-144">[Translation Details &#40;Translations Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
