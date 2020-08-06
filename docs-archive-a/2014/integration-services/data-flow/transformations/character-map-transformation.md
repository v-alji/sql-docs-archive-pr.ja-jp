---
title: 文字マップ変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactertrans.f1
helpviewer_keywords:
- mutually exclusive mapping [Integration Services]
- mapping data [Integration Services]
- string functions
- Character Map transformation [Integration Services]
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5fc31e1a3500a7a7b023e43a968e70e5b438dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642207"
---
# <a name="character-map-transformation"></a><span data-ttu-id="04d5f-102">文字マップ変換</span><span class="sxs-lookup"><span data-stu-id="04d5f-102">Character Map Transformation</span></span>
  <span data-ttu-id="04d5f-103">文字マップ変換は、小文字から大文字への変換関数などの文字列関数を、文字データに適用します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-103">The Character Map transformation applies string functions, such as conversion from lowercase to uppercase, to character data.</span></span> <span data-ttu-id="04d5f-104">この変換は、文字列データ型の列データにのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-104">This transformation operates only on column data with a string data type.</span></span>  
  
 <span data-ttu-id="04d5f-105">文字マップ変換では、列データを適切に変換したり、変換出力に列を追加して、変換後のデータを新しい列に挿入したりできます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-105">The Character Map transformation can convert column data in place or add a column to the transformation output and put the converted data in the new column.</span></span> <span data-ttu-id="04d5f-106">また、さまざまなマップ操作のセットを同じ入力列に適用し、その結果を別の列に格納できます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-106">You can apply different sets of mapping operations to the same input column and put the results in different columns.</span></span> <span data-ttu-id="04d5f-107">たとえば、同じ列を大文字と小文字に変換し、その結果を 2 つの異なる列に格納できます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-107">For example, you can convert the same column to uppercase and lowercase and put the results in two different columns.</span></span>  
  
 <span data-ttu-id="04d5f-108">状況によっては、マップによってデータが切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="04d5f-108">Mapping can, under some circumstances, cause data to be truncated.</span></span> <span data-ttu-id="04d5f-109">たとえば、1 バイト文字をマルチバイトで表記される文字にマップした場合、切り捨てが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="04d5f-109">For example, truncation can occur when single-byte characters are mapped to characters with a multibyte representation.</span></span> <span data-ttu-id="04d5f-110">文字マップ変換には 1 つのエラー出力が含まれます。このエラー出力を使用すると、切り捨てられたデータを別の出力に送ることができます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-110">The Character Map transformation includes an error output, which can be used to direct truncated data to separate output.</span></span> <span data-ttu-id="04d5f-111">詳細については、「 [データのエラー処理](../error-handling-in-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04d5f-111">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="04d5f-112">この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="04d5f-112">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="mapping-operations"></a><span data-ttu-id="04d5f-113">マップ操作</span><span class="sxs-lookup"><span data-stu-id="04d5f-113">Mapping Operations</span></span>  
 <span data-ttu-id="04d5f-114">次の表では、文字マップ変換がサポートするマップ操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-114">The following table describes the mapping operations that the Character Map transformation supports.</span></span>  
  
|<span data-ttu-id="04d5f-115">操作</span><span class="sxs-lookup"><span data-stu-id="04d5f-115">Operation</span></span>|<span data-ttu-id="04d5f-116">説明</span><span class="sxs-lookup"><span data-stu-id="04d5f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04d5f-117">バイトの反転</span><span class="sxs-lookup"><span data-stu-id="04d5f-117">Byte reversal</span></span>|<span data-ttu-id="04d5f-118">バイト順を反転します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-118">Reverses byte order.</span></span>|  
|<span data-ttu-id="04d5f-119">全角</span><span class="sxs-lookup"><span data-stu-id="04d5f-119">Full width</span></span>|<span data-ttu-id="04d5f-120">半角文字を全角文字にマップします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-120">Maps half-width characters to full-width characters.</span></span>|  
|<span data-ttu-id="04d5f-121">半角</span><span class="sxs-lookup"><span data-stu-id="04d5f-121">Half width</span></span>|<span data-ttu-id="04d5f-122">全角文字を半角文字にマップします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-122">Maps full-width characters to half-width characters.</span></span>|  
|<span data-ttu-id="04d5f-123">ひらがな</span><span class="sxs-lookup"><span data-stu-id="04d5f-123">Hiragana</span></span>|<span data-ttu-id="04d5f-124">カタカナをひらがなにマップします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-124">Maps katakana characters to hiragana characters.</span></span>|  
|<span data-ttu-id="04d5f-125">カタカナ</span><span class="sxs-lookup"><span data-stu-id="04d5f-125">Katakana</span></span>|<span data-ttu-id="04d5f-126">ひらがなをカタカナにマップします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-126">Maps hiragana characters to katakana characters.</span></span>|  
|<span data-ttu-id="04d5f-127">言語の文字種</span><span class="sxs-lookup"><span data-stu-id="04d5f-127">Linguistic casing</span></span>|<span data-ttu-id="04d5f-128">システム規則ではなく言語の文字種を適用します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-128">Applies linguistic casing instead of the system rules.</span></span> <span data-ttu-id="04d5f-129">言語の文字種は、Win32 API が提供する、チュルク語や他のロケールの Unicode 単純文字種のマップに関する機能を基準とします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-129">Linguistic casing refers to functionality provided by the Win32 API for Unicode simple case mapping of Turkic and other locales.</span></span>|  
|<span data-ttu-id="04d5f-130">小文字</span><span class="sxs-lookup"><span data-stu-id="04d5f-130">Lowercase</span></span>|<span data-ttu-id="04d5f-131">文字を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-131">Converts characters to lowercase.</span></span>|  
|<span data-ttu-id="04d5f-132">簡体中国語</span><span class="sxs-lookup"><span data-stu-id="04d5f-132">Simplified Chinese</span></span>|<span data-ttu-id="04d5f-133">繁体中国語文字を簡体中国語文字にマップします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-133">Maps traditional Chinese characters to simplified Chinese characters.</span></span>|  
|<span data-ttu-id="04d5f-134">Traditional Chinese</span><span class="sxs-lookup"><span data-stu-id="04d5f-134">Traditional Chinese</span></span>|<span data-ttu-id="04d5f-135">簡体中国語文字を繁体中国語文字にマップします。</span><span class="sxs-lookup"><span data-stu-id="04d5f-135">Maps simplified Chinese characters to traditional Chinese characters.</span></span>|  
|<span data-ttu-id="04d5f-136">大文字</span><span class="sxs-lookup"><span data-stu-id="04d5f-136">Uppercase</span></span>|<span data-ttu-id="04d5f-137">文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-137">Converts characters to uppercase.</span></span>|  
  
## <a name="mutually-exclusive-mapping-operations"></a><span data-ttu-id="04d5f-138">相互に排他的なマップ操作</span><span class="sxs-lookup"><span data-stu-id="04d5f-138">Mutually Exclusive Mapping Operations</span></span>  
 <span data-ttu-id="04d5f-139">変換では、複数の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-139">More than one operation can be performed in a transformation.</span></span> <span data-ttu-id="04d5f-140">ただし、一部のマップ操作は相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="04d5f-140">However, some mapping operations are mutually exclusive.</span></span> <span data-ttu-id="04d5f-141">次の表に、同じ行に対して複数の操作を行う場合に適用される制限の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-141">The following table lists restrictions that apply when you use multiple operations on the same column.</span></span> <span data-ttu-id="04d5f-142">操作 A 列と操作 B 列の操作は、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="04d5f-142">Operations in the columns Operation A and Operation B are mutually exclusive.</span></span>  
  
|<span data-ttu-id="04d5f-143">操作 A</span><span class="sxs-lookup"><span data-stu-id="04d5f-143">Operation A</span></span>|<span data-ttu-id="04d5f-144">操作 B</span><span class="sxs-lookup"><span data-stu-id="04d5f-144">Operation B</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="04d5f-145">小文字</span><span class="sxs-lookup"><span data-stu-id="04d5f-145">Lowercase</span></span>|<span data-ttu-id="04d5f-146">大文字</span><span class="sxs-lookup"><span data-stu-id="04d5f-146">Uppercase</span></span>|  
|<span data-ttu-id="04d5f-147">ひらがな</span><span class="sxs-lookup"><span data-stu-id="04d5f-147">Hiragana</span></span>|<span data-ttu-id="04d5f-148">カタカナ</span><span class="sxs-lookup"><span data-stu-id="04d5f-148">Katakana</span></span>|  
|<span data-ttu-id="04d5f-149">半角</span><span class="sxs-lookup"><span data-stu-id="04d5f-149">Half width</span></span>|<span data-ttu-id="04d5f-150">全角</span><span class="sxs-lookup"><span data-stu-id="04d5f-150">Full width</span></span>|  
|<span data-ttu-id="04d5f-151">Traditional Chinese</span><span class="sxs-lookup"><span data-stu-id="04d5f-151">Traditional Chinese</span></span>|<span data-ttu-id="04d5f-152">簡体中国語</span><span class="sxs-lookup"><span data-stu-id="04d5f-152">Simplified Chinese</span></span>|  
|<span data-ttu-id="04d5f-153">小文字</span><span class="sxs-lookup"><span data-stu-id="04d5f-153">Lowercase</span></span>|<span data-ttu-id="04d5f-154">ひらがな、カタカナ、半角、全角</span><span class="sxs-lookup"><span data-stu-id="04d5f-154">Hiragana, katakana, half width, full width</span></span>|  
|<span data-ttu-id="04d5f-155">大文字</span><span class="sxs-lookup"><span data-stu-id="04d5f-155">Uppercase</span></span>|<span data-ttu-id="04d5f-156">ひらがな、カタカナ、半角、全角</span><span class="sxs-lookup"><span data-stu-id="04d5f-156">Hiragana, katakana, half width, full width</span></span>|  
  
## <a name="configuration-of-the-character-map-transformation"></a><span data-ttu-id="04d5f-157">文字マップ変換の構成</span><span class="sxs-lookup"><span data-stu-id="04d5f-157">Configuration of the Character Map Transformation</span></span>  
 <span data-ttu-id="04d5f-158">文字マップ変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-158">You configure the Character Map transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="04d5f-159">変換する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-159">Specify the columns to convert.</span></span>  
  
-   <span data-ttu-id="04d5f-160">各列に適用する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-160">Specify the operations to apply to each column.</span></span>  
  
 <span data-ttu-id="04d5f-161">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="04d5f-161">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="04d5f-162">**[文字マップ変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [文字マップ変換エディター](../../character-map-transformation-editor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="04d5f-162">For more information about the properties that you can set in the **Character Map Transformation Editor** dialog box, see [Character Map Transformation Editor](../../character-map-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="04d5f-163">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="04d5f-163">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="04d5f-164">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04d5f-164">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="04d5f-165">Common Properties</span><span class="sxs-lookup"><span data-stu-id="04d5f-165">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="04d5f-166">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="04d5f-166">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="04d5f-167">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04d5f-167">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="04d5f-168">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="04d5f-168">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="04d5f-169">マージ変換およびマージ結合変換用にデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="04d5f-169">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  
