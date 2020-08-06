---
title: '[あいまい参照変換エディター] ([詳細設定] タブ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68f53eb2735dc07656fc8ff2b81c3259caa4847b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713310"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a><span data-ttu-id="ada9a-102">[あいまい参照変換エディター] ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="ada9a-102">Fuzzy Lookup Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="ada9a-103">**[あいまい参照変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、あいまい参照のパラメーターを設定できます。</span><span class="sxs-lookup"><span data-stu-id="ada9a-103">Use the **Advanced** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set parameters for the fuzzy lookup.</span></span>  
  
 <span data-ttu-id="ada9a-104">あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ada9a-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ada9a-105">Options</span><span class="sxs-lookup"><span data-stu-id="ada9a-105">Options</span></span>  
 <span data-ttu-id="ada9a-106">**[参照ごとの出力に対する最大一致数]**</span><span class="sxs-lookup"><span data-stu-id="ada9a-106">**Maximum number of matches to output per lookup**</span></span>  
 <span data-ttu-id="ada9a-107">変換で返される、各入力行の一致の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ada9a-107">Specify the maximum number of matches the transformation can return for each input row.</span></span> <span data-ttu-id="ada9a-108">既定値は **1**です。</span><span class="sxs-lookup"><span data-stu-id="ada9a-108">The default is **1**.</span></span>  
  
 <span data-ttu-id="ada9a-109">**[類似性のしきい値]**</span><span class="sxs-lookup"><span data-stu-id="ada9a-109">**Similarity threshold**</span></span>  
 <span data-ttu-id="ada9a-110">スライダーを使用して、コンポーネント レベルの類似性のしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ada9a-110">Set the similarity threshold at the component level by using the slider.</span></span> <span data-ttu-id="ada9a-111">値を 1 に近づけるほど、参照元の値と参照先の値との類似性が高くなければ一致しないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="ada9a-111">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="ada9a-112">しきい値を大きくすると、照合の対象となるレコードが少なくなるため、照合の速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="ada9a-112">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="ada9a-113">**[トークン区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="ada9a-113">**Token delimiters**</span></span>  
 <span data-ttu-id="ada9a-114">列の値をトークンにする際に使用される区切り記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="ada9a-114">Specify the delimiters that the transformation uses to tokenize column values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada9a-115">参照</span><span class="sxs-lookup"><span data-stu-id="ada9a-115">See Also</span></span>  
 <span data-ttu-id="ada9a-116">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ada9a-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ada9a-117">[[あいまい参照変換エディター] &#40;[参照テーブル] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ada9a-117">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 <span data-ttu-id="ada9a-118">[あいまい参照変換エディター ([列] タブ)](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)</span><span class="sxs-lookup"><span data-stu-id="ada9a-118">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)</span></span>  
  
  
