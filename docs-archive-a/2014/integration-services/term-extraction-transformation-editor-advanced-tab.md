---
title: '[用語抽出変換エディター] ([詳細設定] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718470"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a><span data-ttu-id="80243-102">[用語抽出変換エディター] ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="80243-102">Term Extraction Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="80243-103">**[用語抽出変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、頻度、長さ、語または句の抽出の有無など、抽出に関するプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="80243-103">Use the **Advanced** tab of the **Term Extraction Transformation Editor** dialog box to specify properties for the extraction such as frequency, length, and whether to extract words or phrases.</span></span>  
  
 <span data-ttu-id="80243-104">用語抽出変換の詳細については、「 [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80243-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="80243-105">オプション</span><span class="sxs-lookup"><span data-stu-id="80243-105">Options</span></span>  
 <span data-ttu-id="80243-106">**[名詞]**</span><span class="sxs-lookup"><span data-stu-id="80243-106">**Noun**</span></span>  
 <span data-ttu-id="80243-107">変換によって個別の名詞のみを抽出するように指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-107">Specify that the transformation extracts individual nouns only.</span></span>  
  
 <span data-ttu-id="80243-108">**[名詞句]**</span><span class="sxs-lookup"><span data-stu-id="80243-108">**Noun phrase**</span></span>  
 <span data-ttu-id="80243-109">変換によって個別の名詞句のみを抽出するように指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-109">Specify that the transformation extracts noun phrases only.</span></span>  
  
 <span data-ttu-id="80243-110">**[名詞と名詞句]**</span><span class="sxs-lookup"><span data-stu-id="80243-110">**Noun and noun phrase**</span></span>  
 <span data-ttu-id="80243-111">変換によって名詞と名詞句を両方とも抽出するように指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-111">Specify that the transformation extracts both nouns and noun phrases.</span></span>  
  
 <span data-ttu-id="80243-112">**頻度**</span><span class="sxs-lookup"><span data-stu-id="80243-112">**Frequency**</span></span>  
 <span data-ttu-id="80243-113">スコアが用語の頻度であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-113">Specify that the score is the frequency of the term.</span></span>  
  
 <span data-ttu-id="80243-114">**[TFIDF]**</span><span class="sxs-lookup"><span data-stu-id="80243-114">**TFIDF**</span></span>  
 <span data-ttu-id="80243-115">スコアが用語の TFIDF 値であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-115">Specify that the score is the TFIDF value of the term.</span></span> <span data-ttu-id="80243-116">TFIDF スコアは、Term Frequency と Inverse Document Frequency の積です。"用語 T の TFIDF = (T の頻度) \* log( (入力の行数) / (T を含む行数) )" として定義されます。</span><span class="sxs-lookup"><span data-stu-id="80243-116">The TFIDF score is the product of Term Frequency and Inverse Document Frequency, defined as: TFIDF of a Term T = (frequency of T) \* log( (#rows in Input) / (#rows having T) )</span></span>  
  
 <span data-ttu-id="80243-117">**[頻度のしきい値]**</span><span class="sxs-lookup"><span data-stu-id="80243-117">**Frequency threshold**</span></span>  
 <span data-ttu-id="80243-118">語または句を抽出する前の語または句の出現回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-118">Specify the number of times a word or phrase must occur before extracting it.</span></span> <span data-ttu-id="80243-119">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="80243-119">The default value is 2.</span></span>  
  
 <span data-ttu-id="80243-120">**[用語の最大長]**</span><span class="sxs-lookup"><span data-stu-id="80243-120">**Maximum length of term**</span></span>  
 <span data-ttu-id="80243-121">句の最大長を語数で指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-121">Specify the maximum length of a phrase in words.</span></span> <span data-ttu-id="80243-122">このオプションは、名詞句のみに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="80243-122">This option affects noun phrases only.</span></span> <span data-ttu-id="80243-123">既定値は 12 です。</span><span class="sxs-lookup"><span data-stu-id="80243-123">The default value is 12.</span></span>  
  
 <span data-ttu-id="80243-124">**[用語抽出で大文字と小文字を区別する]**</span><span class="sxs-lookup"><span data-stu-id="80243-124">**Use case-sensitive term extraction**</span></span>  
 <span data-ttu-id="80243-125">抽出で大文字と小文字を区別するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="80243-125">Specify whether to make the extraction case-sensitive.</span></span> <span data-ttu-id="80243-126">既定では、 `False`です。</span><span class="sxs-lookup"><span data-stu-id="80243-126">The default is `False`.</span></span>  
  
 <span data-ttu-id="80243-127">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="80243-127">**Configure Error Output**</span></span>  
 <span data-ttu-id="80243-128">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスは、エラーが発生した行に対するエラー処理を指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="80243-128">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80243-129">参照</span><span class="sxs-lookup"><span data-stu-id="80243-129">See Also</span></span>  
 <span data-ttu-id="80243-130">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="80243-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="80243-131">[[用語抽出変換エディター] &#40;[用語抽出] タブ&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="80243-131">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="80243-132">[[用語抽出変換エディター] &#40;[除外] タブ&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span><span class="sxs-lookup"><span data-stu-id="80243-132">[Term Extraction Transformation Editor &#40;Exclusion Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span></span>  
 [<span data-ttu-id="80243-133">用語参照変換</span><span class="sxs-lookup"><span data-stu-id="80243-133">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
