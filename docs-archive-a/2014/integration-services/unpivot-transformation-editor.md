---
title: ピボット解除変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c3b93370b34440b73b4c9c78dc7d19fa4095275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633198"
---
# <a name="unpivot-transformation-editor"></a><span data-ttu-id="305ec-102">[ピボット解除変換エディター]</span><span class="sxs-lookup"><span data-stu-id="305ec-102">Unpivot Transformation Editor</span></span>
  <span data-ttu-id="305ec-103">**[ピボット解除変換エディター]** ダイアログ ボックスを使用すると、行でピボットする列を選択したり、データ列および新しいピボット値出力列を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="305ec-103">Use the **Unpivot Transformation Editor** dialog box to select the columns to pivot into rows, and to specify the data column and the new pivot value output column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="305ec-104"> このトピックでは、「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) 」に示されているピボット解除の例に基づいて、オプションの使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="305ec-104">This topic relies on the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) to illustrate the use of the options.</span></span>  
  
 <span data-ttu-id="305ec-105">ピボット解除変換の詳細については、「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="305ec-105">To learn more about the Unpivot transformation, see [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="305ec-106">Options</span><span class="sxs-lookup"><span data-stu-id="305ec-106">Options</span></span>  
 <span data-ttu-id="305ec-107">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="305ec-107">**Available Input Columns**</span></span>  
 <span data-ttu-id="305ec-108">チェック ボックスを使用して、行でピボットする列を指定します。</span><span class="sxs-lookup"><span data-stu-id="305ec-108">Using the check boxes, specify the columns to pivot into rows.</span></span>  
  
 <span data-ttu-id="305ec-109">**名前**</span><span class="sxs-lookup"><span data-stu-id="305ec-109">**Name**</span></span>  
 <span data-ttu-id="305ec-110">使用できる入力列の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="305ec-110">View the name of the available input column.</span></span>  
  
 <span data-ttu-id="305ec-111">**[パススルー]**</span><span class="sxs-lookup"><span data-stu-id="305ec-111">**Pass Through**</span></span>  
 <span data-ttu-id="305ec-112">ピボット解除された出力に列を含めるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="305ec-112">Indicate whether to include the column in the unpivoted output.</span></span>  
  
 <span data-ttu-id="305ec-113">**入力列**</span><span class="sxs-lookup"><span data-stu-id="305ec-113">**Input Column**</span></span>  
 <span data-ttu-id="305ec-114">各行に対して使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="305ec-114">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="305ec-115">選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="305ec-115">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="305ec-116">「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、入力列として、 **Ham**, **Soda**, **Milk**, **Beer**、および **Chips** の各列があります。</span><span class="sxs-lookup"><span data-stu-id="305ec-116">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Input Columns are the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns.</span></span>  
  
 <span data-ttu-id="305ec-117">**変換先列**</span><span class="sxs-lookup"><span data-stu-id="305ec-117">**Destination Column**</span></span>  
 <span data-ttu-id="305ec-118">データ列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="305ec-118">Provide a name for the data column.</span></span>  
  
 <span data-ttu-id="305ec-119">「 [ピボット解除変換](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、変換先列は数量 (**Qty**) 列です。</span><span class="sxs-lookup"><span data-stu-id="305ec-119">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Destination Column is the quantity (**Qty**) column.</span></span>  
  
 <span data-ttu-id="305ec-120">**[ピボット キー値]**</span><span class="sxs-lookup"><span data-stu-id="305ec-120">**Pivot Key Value**</span></span>  
 <span data-ttu-id="305ec-121">ピボット値の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="305ec-121">Provide a name for the pivot value.</span></span> <span data-ttu-id="305ec-122">既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="305ec-122">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="305ec-123">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="305ec-123">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="305ec-124">「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、ピボット値は、 **[ピボット キー値の列名]** オプションで指定された新しい Product 列のテキスト値 **Ham**, **Soda**, **Milk**, **Beer**、および **Chips**として表示されます。</span><span class="sxs-lookup"><span data-stu-id="305ec-124">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Values will appear in the new Product column designated by the **Pivot Key Value Column Name** option, as the text values **Ham**, **Soda**, **Milk**, **Beer**, and **Chips**.</span></span>  
  
 <span data-ttu-id="305ec-125">**[ピボット キー値の列名]**</span><span class="sxs-lookup"><span data-stu-id="305ec-125">**Pivot Key Value Column Name**</span></span>  
 <span data-ttu-id="305ec-126">ピボット値列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="305ec-126">Provide a name for the pivot value column.</span></span> <span data-ttu-id="305ec-127">既定では [ピボット キー値] になりますが、わかりやすい一意な名前を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="305ec-127">The default is "Pivot Key Value"; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="305ec-128">「 [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md)」のピボット解除の例では、ピボット キー値列の名前は **Product** です。これは、 **Product** 、 **Product**, **Product**, **Product**, **Product**の列のピボット解除が行われる新しい **Product** 列を示しています。</span><span class="sxs-lookup"><span data-stu-id="305ec-128">In the Unpivot scenario described in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), the Pivot Key Value Column Name is **Product** and designates the new **Product** column into which the **Ham**, **Soda**, **Milk**, **Beer**, and **Chips** columns are unpivoted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305ec-129">参照</span><span class="sxs-lookup"><span data-stu-id="305ec-129">See Also</span></span>  
 <span data-ttu-id="305ec-130">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="305ec-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="305ec-131">ピボット変換</span><span class="sxs-lookup"><span data-stu-id="305ec-131">Pivot Transformation</span></span>](data-flow/transformations/pivot-transformation.md)  
  
  
