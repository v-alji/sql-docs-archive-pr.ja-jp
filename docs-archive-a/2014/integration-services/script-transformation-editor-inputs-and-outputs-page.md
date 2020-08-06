---
title: '[スクリプト変換エディター] ([入力および出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.columnproperties.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 9659d2d2-5d73-4470-9768-e07b77142fc9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16adf74a1cd8f0c778bc18eaff84437b8fc13603
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712141"
---
# <a name="script-transformation-editor-inputs-and-outputs-page"></a><span data-ttu-id="e95f2-102">[スクリプト変換エディター] ([入力および出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="e95f2-102">Script Transformation Editor (Inputs and Outputs Page)</span></span>
  <span data-ttu-id="e95f2-103">**[スクリプト変換エディター]** ダイアログ ボックスの **[入力および出力]** ページを使用すると、スクリプト変換の入力および出力を追加、削除、構成できます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-103">Use the **Inputs and Outputs** page of the **Script Transformation Editor** dialog box to add, remove, and configure inputs and outputs for the Script Transformation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e95f2-104">基になるコンポーネントには出力はありますが、入力はありません。変換先のコンポーネントには入力はありますが、出力はありません。</span><span class="sxs-lookup"><span data-stu-id="e95f2-104">Source components have outputs and no inputs, while destination components have inputs but no outputs.</span></span> <span data-ttu-id="e95f2-105">変換には入力と出力の両方があります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-105">Transformations have both inputs and outputs.</span></span>  
  
 <span data-ttu-id="e95f2-106">スクリプト コンポーネントの詳細については、「 [Script Component](data-flow/transformations/script-component.md) 」および「 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95f2-106">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="e95f2-107">スクリプト コンポーネントのプログラミングの詳細については、「 [スクリプト コンポーネントによるデータ フローの拡張](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95f2-107">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e95f2-108">オプション</span><span class="sxs-lookup"><span data-stu-id="e95f2-108">Options</span></span>  
 <span data-ttu-id="e95f2-109">**Inputs and outputs**</span><span class="sxs-lookup"><span data-stu-id="e95f2-109">**Inputs and outputs**</span></span>  
 <span data-ttu-id="e95f2-110">左側で入力または出力を選択すると、右側の表にプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-110">Select an input or output on the left to view its properties in the table on the right.</span></span> <span data-ttu-id="e95f2-111">編集に使用できるプロパティは、選択内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-111">Properties available for editing vary according to the selection.</span></span> <span data-ttu-id="e95f2-112">表示されるプロパティの多くは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="e95f2-112">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="e95f2-113">各プロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95f2-113">For more information on the individual properties, see the following topics.</span></span>  
  
 [<span data-ttu-id="e95f2-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e95f2-114">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
 [<span data-ttu-id="e95f2-115">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="e95f2-115">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
 <span data-ttu-id="e95f2-116">**[出力の追加]**</span><span class="sxs-lookup"><span data-stu-id="e95f2-116">**Add Output**</span></span>  
 <span data-ttu-id="e95f2-117">追加の出力を一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-117">Add an additional output to the list.</span></span>  
  
 <span data-ttu-id="e95f2-118">**[列の追加]**</span><span class="sxs-lookup"><span data-stu-id="e95f2-118">**Add Column**</span></span>  
 <span data-ttu-id="e95f2-119">新しい出力列を格納するフォルダーを選択して **[列の追加]** をクリックすると、列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-119">Select a folder in which to place the new output column, and then add the column by clicking **Add Column**.</span></span>  
  
 <span data-ttu-id="e95f2-120">**[出力の削除]**</span><span class="sxs-lookup"><span data-stu-id="e95f2-120">**Remove Output**</span></span>  
 <span data-ttu-id="e95f2-121">出力を選択した後、 **[出力の削除]** をクリックするとその出力が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-121">Select an output, and then remove it by clicking **Remove Output**.</span></span>  
  
 <span data-ttu-id="e95f2-122">**[列の削除]**</span><span class="sxs-lookup"><span data-stu-id="e95f2-122">**Remove Column**</span></span>  
 <span data-ttu-id="e95f2-123">列を選択した後、 **[列の削除]** をクリックするとその列が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-123">Select a column, and then remove it by clicking **Remove Column**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95f2-124">参照</span><span class="sxs-lookup"><span data-stu-id="e95f2-124">See Also</span></span>  
 <span data-ttu-id="e95f2-125">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e95f2-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e95f2-126">[スクリプトコンポーネントの種類を選択](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="e95f2-126">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="e95f2-127">[[スクリプト変換エディター] &#40;[入力列] ページ&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e95f2-127">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="e95f2-128">[スクリプト変換エディター &#40;スクリプトページ&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="e95f2-128">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="e95f2-129">[[スクリプト変換エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="e95f2-129">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="e95f2-130">その他のスクリプト コンポーネントの例</span><span class="sxs-lookup"><span data-stu-id="e95f2-130">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
