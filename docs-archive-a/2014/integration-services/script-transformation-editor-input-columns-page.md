---
title: '[スクリプト変換エディター] ([入力列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.inputcolumn.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: d6e4ce84-3335-48e6-82d3-1c359ed87f63
author: chugugrace
ms.author: chugu
ms.openlocfilehash: daffb52b62ad59ae4fe574d7fa27d4820b9cb5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712145"
---
# <a name="script-transformation-editor-input-columns-page"></a><span data-ttu-id="9e429-102">[スクリプト変換エディター] ([入力列] ページ)</span><span class="sxs-lookup"><span data-stu-id="9e429-102">Script Transformation Editor (Input Columns Page)</span></span>
  <span data-ttu-id="9e429-103">**[スクリプト変換エディター]** ダイアログ ボックスの **[入力列]** ページを使用すると、入力列のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="9e429-103">Use the **Input Columns** page of the **Script Transformation Editor** dialog box to set properties on input columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e429-104">ソース コンポーネントでは、出力はあっても入力はないため、 **[入力列]** ページはソース コンポーネントには表示されません。</span><span class="sxs-lookup"><span data-stu-id="9e429-104">The **Input Columns** page is not displayed for Source components, which have outputs but no inputs.</span></span>  
  
 <span data-ttu-id="9e429-105">スクリプト コンポーネントの詳細については、「 [Script Component](data-flow/transformations/script-component.md) 」および「 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e429-105">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="9e429-106">スクリプト コンポーネントのプログラミングの詳細については、「 [スクリプト コンポーネントによるデータ フローの拡張](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e429-106">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9e429-107">オプション</span><span class="sxs-lookup"><span data-stu-id="9e429-107">Options</span></span>  
 <span data-ttu-id="9e429-108">**[入力名]**</span><span class="sxs-lookup"><span data-stu-id="9e429-108">**Input name**</span></span>  
 <span data-ttu-id="9e429-109">使用できる入力の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="9e429-109">Select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="9e429-110">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="9e429-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="9e429-111">チェック ボックスを使用して、スクリプト変換に使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e429-111">Using the check boxes, specify the columns that the script transformation will use.</span></span>  
  
 <span data-ttu-id="9e429-112">**入力列**</span><span class="sxs-lookup"><span data-stu-id="9e429-112">**Input Column**</span></span>  
 <span data-ttu-id="9e429-113">各行に対して使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="9e429-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="9e429-114">選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="9e429-114">Your selections are reflected in the check box selections in the **Available Input Columns**table.</span></span>  
  
 <span data-ttu-id="9e429-115">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="9e429-115">**Output Alias**</span></span>  
 <span data-ttu-id="9e429-116">各出力列の別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9e429-116">Type an alias for each output column.</span></span> <span data-ttu-id="9e429-117">既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="9e429-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="9e429-118">**[使用法の種類]**</span><span class="sxs-lookup"><span data-stu-id="9e429-118">**Usage Type**</span></span>  
 <span data-ttu-id="9e429-119">スクリプト変換で各列を `ReadOnly` または `ReadWrite` として扱うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e429-119">Specify whether the Script Transformation will treat each column as `ReadOnly` or `ReadWrite`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e429-120">参照</span><span class="sxs-lookup"><span data-stu-id="9e429-120">See Also</span></span>  
 <span data-ttu-id="9e429-121">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9e429-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9e429-122">[スクリプトコンポーネントの種類を選択](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="9e429-122">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="9e429-123">[[スクリプト変換エディター] の [入力および出力] ページ &#40;&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="9e429-123">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="9e429-124">[スクリプト変換エディター &#40;スクリプトページ&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="9e429-124">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="9e429-125">[[スクリプト変換エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="9e429-125">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="9e429-126">その他のスクリプト コンポーネントの例</span><span class="sxs-lookup"><span data-stu-id="9e429-126">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
