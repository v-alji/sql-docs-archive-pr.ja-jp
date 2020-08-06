---
title: '[参照変換エディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cd78f40a0072f7f0c5c923cdd51431873402f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641063"
---
# <a name="lookup-transformation-editor-error-output-page"></a><span data-ttu-id="fa2c6-102">[参照変換エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="fa2c6-102">Lookup Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="fa2c6-103">**[参照変換エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-103">Use the **Error Output** page of the **Lookup Transformation Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="fa2c6-104">参照変換の詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa2c6-105">Options</span><span class="sxs-lookup"><span data-stu-id="fa2c6-105">Options</span></span>  
 <span data-ttu-id="fa2c6-106">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-106">**Input/Output**</span></span>  
 <span data-ttu-id="fa2c6-107">入力の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-107">View the name of the input.</span></span>  
  
 <span data-ttu-id="fa2c6-108">**列**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-108">**Column**</span></span>  
 <span data-ttu-id="fa2c6-109">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-109">Not used.</span></span>  
  
 <span data-ttu-id="fa2c6-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-110">**Error**</span></span>  
 <span data-ttu-id="fa2c6-111">参照データセットに一致するエントリがない行を処理したときに発生させるエラーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-111">Specify what type of error should occur when handling rows without matching entries in the reference dataset:</span></span>  
  
-   <span data-ttu-id="fa2c6-112">エラーを無視し、行を出力にダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-112">Ignore the failure and direct the rows to an output.</span></span>  
  
-   <span data-ttu-id="fa2c6-113">行をエラー出力にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-113">Redirect the rows to an error output.</span></span>  
  
-   <span data-ttu-id="fa2c6-114">コンポーネントを失敗させます。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-114">Fail the component.</span></span>  
  
 <span data-ttu-id="fa2c6-115">このオプションは、 **[エントリが一致しない行の処理方法を指定する]** ボックスの一覧で **[一致なしの出力に行をリダイレクトする]** を選択した場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-115">This option is not available when you select **Redirect rows to no match output** in the **Specify how to handle rows with no matching entries** list.</span></span> <span data-ttu-id="fa2c6-116">この一覧は、 **[参照変換エディター]** ダイアログ ボックスの **[全般]** ページにあります。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-116">This list is on the **General** page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="fa2c6-117">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c6-117">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="fa2c6-118">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-118">**Truncation**</span></span>  
 <span data-ttu-id="fa2c6-119">データの切り捨てが発生したときの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-119">Specify what should happen when data truncation occurs:</span></span>  
  
-   <span data-ttu-id="fa2c6-120">エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-120">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="fa2c6-121">行をリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-121">Redirect the row.</span></span>  
  
-   <span data-ttu-id="fa2c6-122">コンポーネントを失敗させます。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-122">Fail the component.</span></span>  
  
 <span data-ttu-id="fa2c6-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-123">**Description**</span></span>  
 <span data-ttu-id="fa2c6-124">操作の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-124">View the description of the operation.</span></span>  
  
 <span data-ttu-id="fa2c6-125">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-125">**Set selected cells to this value**</span></span>  
 <span data-ttu-id="fa2c6-126">エラーまたは切り捨てが発生したときのすべての選択済みセルの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-126">Specify what should happen to all the selected cells when an error or truncation occurs:</span></span>  
  
-   <span data-ttu-id="fa2c6-127">エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-127">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="fa2c6-128">行をリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-128">Redirect the row.</span></span>  
  
-   <span data-ttu-id="fa2c6-129">コンポーネントを失敗させます。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-129">Fail the component.</span></span>  
  
 <span data-ttu-id="fa2c6-130">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="fa2c6-130">**Apply**</span></span>  
 <span data-ttu-id="fa2c6-131">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="fa2c6-131">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa2c6-132">参照</span><span class="sxs-lookup"><span data-stu-id="fa2c6-132">See Also</span></span>  
 [<span data-ttu-id="fa2c6-133">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="fa2c6-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
