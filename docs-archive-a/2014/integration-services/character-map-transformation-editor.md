---
title: 文字マップ変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c6cdcdba448dafc6ccf03774d4f611dee704b823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633964"
---
# <a name="character-map-transformation-editor"></a><span data-ttu-id="c38be-102">文字マップ変換エディター</span><span class="sxs-lookup"><span data-stu-id="c38be-102">Character Map Transformation Editor</span></span>
  <span data-ttu-id="c38be-103">**[文字マップ変換エディター]** ダイアログ ボックスを使用すると、列のデータに適用する文字列関数を選択し、マッピングが埋め込み先の変更か新しい列として追加されるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c38be-103">Use the **Character Map Transformation Editor** dialog box to select the string functions to apply to column data and to specify whether mapping is an in-place change or added as a new column.</span></span>  
  
 <span data-ttu-id="c38be-104">文字マップ変換の詳細については、「 [Character Map Transformation](data-flow/transformations/character-map-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c38be-104">To learn more about the Character Map transformation, see [Character Map Transformation](data-flow/transformations/character-map-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c38be-105">Options</span><span class="sxs-lookup"><span data-stu-id="c38be-105">Options</span></span>  
 <span data-ttu-id="c38be-106">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="c38be-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="c38be-107">チェック ボックスを使用し、文字列関数を使用して変換する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c38be-107">Use the check boxes to select the columns to transform using string functions.</span></span> <span data-ttu-id="c38be-108">選択は下の表に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c38be-108">Your selections appear in the table below.</span></span>  
  
 <span data-ttu-id="c38be-109">**入力列**</span><span class="sxs-lookup"><span data-stu-id="c38be-109">**Input Column**</span></span>  
 <span data-ttu-id="c38be-110">上の表で選択された入力列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c38be-110">View input columns selected from the table above.</span></span> <span data-ttu-id="c38be-111">使用できる入力列の一覧を使用して、選択した列を変更したり、削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="c38be-111">You can also change or remove a selection by using the list of available input columns.</span></span>  
  
 <span data-ttu-id="c38be-112">**宛先**</span><span class="sxs-lookup"><span data-stu-id="c38be-112">**Destination**</span></span>  
 <span data-ttu-id="c38be-113">文字列処理の結果を、既定の列を使用して所定の場所に保存するか、変更されたデータを新しい列として保存するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c38be-113">Specify whether to save the results of the string operations in place, using the existing column, or to save the modified data as a new column.</span></span>  
  
|<span data-ttu-id="c38be-114">値</span><span class="sxs-lookup"><span data-stu-id="c38be-114">Value</span></span>|<span data-ttu-id="c38be-115">説明</span><span class="sxs-lookup"><span data-stu-id="c38be-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c38be-116">新しい列</span><span class="sxs-lookup"><span data-stu-id="c38be-116">New column</span></span>|<span data-ttu-id="c38be-117">データを新しい列に保存します。</span><span class="sxs-lookup"><span data-stu-id="c38be-117">Save the data in a new column.</span></span> <span data-ttu-id="c38be-118">**[出力の別名]** で、列名を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c38be-118">Assign the column name under **Output Alias**.</span></span>|  
|<span data-ttu-id="c38be-119">[埋め込み先変更]</span><span class="sxs-lookup"><span data-stu-id="c38be-119">In-place change</span></span>|<span data-ttu-id="c38be-120">変更されたデータを既存の列に保存します。</span><span class="sxs-lookup"><span data-stu-id="c38be-120">Save the modified data in the existing column.</span></span>|  
  
 <span data-ttu-id="c38be-121">**操作**</span><span class="sxs-lookup"><span data-stu-id="c38be-121">**Operation**</span></span>  
 <span data-ttu-id="c38be-122">列のデータに適用する文字列関数を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="c38be-122">Select from the list the string functions to apply to column data.</span></span>  
  
|<span data-ttu-id="c38be-123">値</span><span class="sxs-lookup"><span data-stu-id="c38be-123">Value</span></span>|<span data-ttu-id="c38be-124">説明</span><span class="sxs-lookup"><span data-stu-id="c38be-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c38be-125">小文字</span><span class="sxs-lookup"><span data-stu-id="c38be-125">Lowercase</span></span>|<span data-ttu-id="c38be-126">小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-126">Convert to lower case.</span></span>|  
|<span data-ttu-id="c38be-127">大文字</span><span class="sxs-lookup"><span data-stu-id="c38be-127">Uppercase</span></span>|<span data-ttu-id="c38be-128">大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-128">Convert to upper case.</span></span>|  
|<span data-ttu-id="c38be-129">バイトの反転</span><span class="sxs-lookup"><span data-stu-id="c38be-129">Byte reversal</span></span>|<span data-ttu-id="c38be-130">バイト順序を反転します。</span><span class="sxs-lookup"><span data-stu-id="c38be-130">Convert by reversing byte order.</span></span>|  
|<span data-ttu-id="c38be-131">ひらがな</span><span class="sxs-lookup"><span data-stu-id="c38be-131">Hiragana</span></span>|<span data-ttu-id="c38be-132">カタカナをひらがなに変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-132">Convert Japanese katakana characters to hiragana.</span></span>|  
|<span data-ttu-id="c38be-133">カタカナ</span><span class="sxs-lookup"><span data-stu-id="c38be-133">Katakana</span></span>|<span data-ttu-id="c38be-134">ひらがなをカタカナに変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-134">Convert Japanese hiragana characters to katakana.</span></span>|  
|<span data-ttu-id="c38be-135">半角</span><span class="sxs-lookup"><span data-stu-id="c38be-135">Half width</span></span>|<span data-ttu-id="c38be-136">全角文字を半角文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-136">Convert full-width characters to half width.</span></span>|  
|<span data-ttu-id="c38be-137">全角</span><span class="sxs-lookup"><span data-stu-id="c38be-137">Full width</span></span>|<span data-ttu-id="c38be-138">半角文字を全角文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-138">Convert half-width characters to full width.</span></span>|  
|<span data-ttu-id="c38be-139">言語の文字種</span><span class="sxs-lookup"><span data-stu-id="c38be-139">Linguistic casing</span></span>|<span data-ttu-id="c38be-140">システムのルールではなく、言語の文字種による規則 (チュルク語などのロケールにおける Unicode の文字種の単純な割り当て) を適用します。</span><span class="sxs-lookup"><span data-stu-id="c38be-140">Apply linguistic rules of casing (Unicode simple case mapping for Turkic and other locales) instead of the system rules.</span></span>|  
|<span data-ttu-id="c38be-141">簡体中国語</span><span class="sxs-lookup"><span data-stu-id="c38be-141">Simplified Chinese</span></span>|<span data-ttu-id="c38be-142">繁体中国語の文字を簡体中国語に変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-142">Convert traditional Chinese characters to simplified Chinese.</span></span>|  
|<span data-ttu-id="c38be-143">Traditional Chinese</span><span class="sxs-lookup"><span data-stu-id="c38be-143">Traditional Chinese</span></span>|<span data-ttu-id="c38be-144">簡体中国語の文字を繁体中国語に変換します。</span><span class="sxs-lookup"><span data-stu-id="c38be-144">Convert simplified Chinese characters to traditional Chinese.</span></span>|  
  
 <span data-ttu-id="c38be-145">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="c38be-145">**Output Alias**</span></span>  
 <span data-ttu-id="c38be-146">各出力列の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="c38be-146">Type an alias for each output column.</span></span> <span data-ttu-id="c38be-147">既定では、入力列の名前の後に " **のコピー** " が追加された別名になりますが、固有のわかりやすい名前を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="c38be-147">The default is **Copy of** followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="c38be-148">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="c38be-148">**Configure Error Output**</span></span>  
 <span data-ttu-id="c38be-149">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、この変換のエラー処理オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="c38be-149">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38be-150">参照</span><span class="sxs-lookup"><span data-stu-id="c38be-150">See Also</span></span>  
 [<span data-ttu-id="c38be-151">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="c38be-151">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
