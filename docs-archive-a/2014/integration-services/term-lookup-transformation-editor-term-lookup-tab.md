---
title: '[用語参照変換エディター] ([用語参照] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bb8c0bd0477d9883640cc3e4d3cb25c2a3a8b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645171"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a><span data-ttu-id="39760-102">[用語参照変換エディター] ([用語参照] タブ)</span><span class="sxs-lookup"><span data-stu-id="39760-102">Term Lookup Transformation Editor (Term Lookup Tab)</span></span>
  <span data-ttu-id="39760-103">**[用語参照変換エディター]** ダイアログ ボックスの **[用語参照]** タブを使用すると、入力列を参照テーブルの参照列にマップし、各出力列の別名を提供できます。</span><span class="sxs-lookup"><span data-stu-id="39760-103">Use the **Term Lookup** tab of the **Term Lookup Transformation Editor** dialog box to map an input column to a lookup column in a reference table and to provide an alias for each output column.</span></span>  
  
 <span data-ttu-id="39760-104">用語参照変換の詳細については、「 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39760-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="39760-105">Options</span><span class="sxs-lookup"><span data-stu-id="39760-105">Options</span></span>  
 <span data-ttu-id="39760-106">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="39760-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="39760-107">チェック ボックスを使用して、出力にそのまま渡す入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="39760-107">Using the check boxes, select input columns to pass through to the output unchanged.</span></span> <span data-ttu-id="39760-108">**[使用できる参照列]** の一覧に入力列をドラッグして、入力列を参照テーブル内の参照列にマップします。</span><span class="sxs-lookup"><span data-stu-id="39760-108">Drag an input column to the **Available Reference Columns** list to map it to a lookup column in the reference table.</span></span> <span data-ttu-id="39760-109">入力列と参照列は、DT_NTEXT または DT_WSTR のサポートされるデータ型が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="39760-109">The input and lookup columns must have matching, supported data types, either DT_NTEXT or DT_WSTR.</span></span> <span data-ttu-id="39760-110">マッピングする行を選択して右クリックし、 [[リレーションシップの作成]](data-flow/transformations/create-relationships.md) ダイアログ ボックスでマッピングを編集します。</span><span class="sxs-lookup"><span data-stu-id="39760-110">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="39760-111">**[使用できる参照列]**</span><span class="sxs-lookup"><span data-stu-id="39760-111">**Available Reference Columns**</span></span>  
 <span data-ttu-id="39760-112">参照テーブル内の使用できる列を表示します。</span><span class="sxs-lookup"><span data-stu-id="39760-112">View the available columns in the reference table.</span></span> <span data-ttu-id="39760-113">一致させる用語の一覧を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="39760-113">Choose the column that contains the list of terms to match.</span></span>  
  
 <span data-ttu-id="39760-114">**[パススルー列]**</span><span class="sxs-lookup"><span data-stu-id="39760-114">**Pass-Through Column**</span></span>  
 <span data-ttu-id="39760-115">使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="39760-115">Select from the list of available input columns.</span></span> <span data-ttu-id="39760-116">選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="39760-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="39760-117">**[出力列の別名]**</span><span class="sxs-lookup"><span data-stu-id="39760-117">**Output Column Alias**</span></span>  
 <span data-ttu-id="39760-118">各出力列の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="39760-118">Type an alias for each output column.</span></span> <span data-ttu-id="39760-119">既定では列の名前が使用されますが、一意なわかりやすい名前を自由に付けることができます。</span><span class="sxs-lookup"><span data-stu-id="39760-119">The default is the name of the column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="39760-120">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="39760-120">**Configure Error Output**</span></span>  
 <span data-ttu-id="39760-121">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスは、エラーが発生した行に対するエラー処理オプションを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="39760-121">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39760-122">参照</span><span class="sxs-lookup"><span data-stu-id="39760-122">See Also</span></span>  
 <span data-ttu-id="39760-123">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="39760-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="39760-124">[[用語参照変換エディター] &#40;[参照テーブル] タブ&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="39760-124">[Term Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 <span data-ttu-id="39760-125">[[用語参照変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="39760-125">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="39760-126">用語抽出変換</span><span class="sxs-lookup"><span data-stu-id="39760-126">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
