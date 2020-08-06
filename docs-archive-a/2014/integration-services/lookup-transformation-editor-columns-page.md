---
title: '[参照変換エディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b768076d8acbcaef8cbff21783a7697020e027eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641067"
---
# <a name="lookup-transformation-editor-columns-page"></a><span data-ttu-id="ad4f5-102">[参照変換エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="ad4f5-102">Lookup Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="ad4f5-103">**[参照変換エディター]** ダイアログ ボックスの **[列]** ページを使用すると、元のテーブルと参照テーブルの間に結合を指定したり、参照テーブルから参照列を選択したりできます。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-103">Use the **Columns** page of the **Lookup Transformation Editor** dialog box to specify the join between the source table and the reference table, and to select lookup columns from the reference table.</span></span>  
  
 <span data-ttu-id="ad4f5-104">参照変換の詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ad4f5-105">Options</span><span class="sxs-lookup"><span data-stu-id="ad4f5-105">Options</span></span>  
 <span data-ttu-id="ad4f5-106">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="ad4f5-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="ad4f5-107">使用できる入力列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-107">View the list of available input columns.</span></span> <span data-ttu-id="ad4f5-108">入力列とは、データ フロー内の接続されているソースからの列です。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-108">The input columns are the columns in the data flow from a connected source.</span></span> <span data-ttu-id="ad4f5-109">入力列と参照列のデータ型は一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-109">The input columns and lookup column must have matching data types.</span></span>  
  
 <span data-ttu-id="ad4f5-110">ドラッグ アンド ドロップ操作により、使用できる入力列を参照列にマップします。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-110">Use a drag-and-drop operation to map available input columns to lookup columns.</span></span>  
  
 <span data-ttu-id="ad4f5-111">キーボードを使用して、 **[使用できる入力列]** テーブル内の列を強調表示し、アプリケーション キーを押して、 **[マッピングの編集]** をクリックすることで、入力列を参照列にマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-111">You can also map input columns to lookup columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="ad4f5-112">**使用できる参照列**</span><span class="sxs-lookup"><span data-stu-id="ad4f5-112">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="ad4f5-113">参照列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-113">View the list of lookup columns.</span></span> <span data-ttu-id="ad4f5-114">参照列とは、入力列に一致する値の参照先の参照テーブルにある列です。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-114">The lookup columns are columns in the reference table in which you want to look up values that match the input columns.</span></span>  
  
 <span data-ttu-id="ad4f5-115">ドラッグ アンド ドロップ操作により、使用できる参照列を入力列にマップします。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-115">Use a drag-and-drop operation to map available lookup columns to input columns.</span></span>  
  
 <span data-ttu-id="ad4f5-116">チェック ボックスを使用して、参照操作を実行する参照テーブル内の参照列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-116">Use the check boxes to select lookup columns in the reference table on which to perform lookup operations.</span></span>  
  
 <span data-ttu-id="ad4f5-117">キーボードを使用して、 **[使用できる参照列]** テーブル内の列を強調表示し、アプリケーション キーを押して、 **[マッピングの編集]** をクリックすることで、参照列を入力列にマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-117">You can also map lookup columns to input columns using the keyboard, by highlighting a column in the **Available Lookup Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="ad4f5-118">**参照列**</span><span class="sxs-lookup"><span data-stu-id="ad4f5-118">**Lookup Column**</span></span>  
 <span data-ttu-id="ad4f5-119">選択した参照列を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-119">View the selected lookup columns.</span></span> <span data-ttu-id="ad4f5-120">選択内容は、 **[使用できる参照列]** テーブルのチェック ボックスの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-120">The selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span>  
  
 <span data-ttu-id="ad4f5-121">**[参照操作]**</span><span class="sxs-lookup"><span data-stu-id="ad4f5-121">**Lookup Operation**</span></span>  
 <span data-ttu-id="ad4f5-122">一覧から、参照列で実行する参照操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-122">Select a lookup operation from the list to perform on the lookup column.</span></span>  
  
 <span data-ttu-id="ad4f5-123">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="ad4f5-123">**Output Alias**</span></span>  
 <span data-ttu-id="ad4f5-124">各参照列の出力の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-124">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="ad4f5-125">既定では参照列の名前が使用されますが、一意なわかりやすい名前を自由に付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ad4f5-125">The default is the name of the lookup column; however, you can select any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad4f5-126">参照</span><span class="sxs-lookup"><span data-stu-id="ad4f5-126">See Also</span></span>  
 <span data-ttu-id="ad4f5-127">[[参照変換エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ad4f5-127">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="ad4f5-128">[[参照変換エディター] &#40;接続ページ&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad4f5-128">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="ad4f5-129">[[参照変換エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad4f5-129">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="ad4f5-130">[[参照変換エディター] &#40;エラー出力ページ&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad4f5-130">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="ad4f5-131">あいまい参照変換</span><span class="sxs-lookup"><span data-stu-id="ad4f5-131">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
