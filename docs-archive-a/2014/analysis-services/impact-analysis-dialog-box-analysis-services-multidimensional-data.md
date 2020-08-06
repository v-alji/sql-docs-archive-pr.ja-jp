---
title: '[影響分析] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e47ab806b9bd10afc812113b69fe0849437068b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712609"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="375fd-102">[影響分析] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="375fd-102">Impact Analysis Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="375fd-103">**および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [影響分析] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 **[処理]** ダイアログ ボックスに一覧表示されているオブジェクトが処理された場合に影響を受ける依存オブジェクトを特定し、必要に応じて処理できます。</span><span class="sxs-lookup"><span data-stu-id="375fd-103">Use the **Impact Analysis** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to identify and optionally process dependent objects that are affected if the objects listed in the **Process** dialog box are processed.</span></span> <span data-ttu-id="375fd-104">**[影響分析]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスの **[影響分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="375fd-104">You can display the **Impact Analysis** dialog box by clicking **Impact Analysis** from the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="375fd-105">オブジェクトが複数回にわたって影響を受ける場合は、そのオブジェクトが複数回表示されます。</span><span class="sxs-lookup"><span data-stu-id="375fd-105">An object appears more than once if it is affected in more than one way.</span></span>  
  
## <a name="options"></a><span data-ttu-id="375fd-106">Options</span><span class="sxs-lookup"><span data-stu-id="375fd-106">Options</span></span>  
 <span data-ttu-id="375fd-107">**オブジェクトの一覧**</span><span class="sxs-lookup"><span data-stu-id="375fd-107">**Object list**</span></span>  
 <span data-ttu-id="375fd-108">依存オブジェクトの一覧をグリッドに表示します。</span><span class="sxs-lookup"><span data-stu-id="375fd-108">Displays a list of dependent objects in a grid.</span></span> <span data-ttu-id="375fd-109">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="375fd-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="375fd-110">**[オブジェクト名]**</span><span class="sxs-lookup"><span data-stu-id="375fd-110">**Object Name**</span></span>  
 <span data-ttu-id="375fd-111">処理する必要がある可能性がある依存オブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="375fd-111">Displays the name of the dependent object that may need to be processed.</span></span> <span data-ttu-id="375fd-112">名前の左にあるアイコンはオブジェクトの種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="375fd-112">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="375fd-113">**Type**</span><span class="sxs-lookup"><span data-stu-id="375fd-113">**Type**</span></span>  
 <span data-ttu-id="375fd-114">処理する必要がある可能性がある依存オブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="375fd-114">Displays the type of dependent object that may need to be processed.</span></span>  
  
 <span data-ttu-id="375fd-115">**[影響の種類]**</span><span class="sxs-lookup"><span data-stu-id="375fd-115">**Impact Type**</span></span>  
 <span data-ttu-id="375fd-116">**[処理]** ダイアログ ボックスに表示されているオブジェクトを処理することによって依存オブジェクトに与える影響を表示します。</span><span class="sxs-lookup"><span data-stu-id="375fd-116">Displays the effect that processing the objects in the **Process** dialog box has on the dependent object.</span></span> <span data-ttu-id="375fd-117">次の表に、処理の影響と、その結果として警告またはエラーのどちらが生成されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="375fd-117">The following table lists the possible effects of processing and notes whether each one results in a warning or an error.</span></span>  
  
|<span data-ttu-id="375fd-118">影響</span><span class="sxs-lookup"><span data-stu-id="375fd-118">Impact</span></span>|<span data-ttu-id="375fd-119">Message</span><span class="sxs-lookup"><span data-stu-id="375fd-119">Message</span></span>|  
|------------|-------------|  
|<span data-ttu-id="375fd-120">オブジェクトがクリアされます (処理されません)。</span><span class="sxs-lookup"><span data-stu-id="375fd-120">Object will be cleared (unprocessed)</span></span>|<span data-ttu-id="375fd-121">警告</span><span class="sxs-lookup"><span data-stu-id="375fd-121">Warning</span></span>|  
|<span data-ttu-id="375fd-122">オブジェクトが無効になります。</span><span class="sxs-lookup"><span data-stu-id="375fd-122">Object would be invalid</span></span>|<span data-ttu-id="375fd-123">エラー</span><span class="sxs-lookup"><span data-stu-id="375fd-123">Error</span></span>|  
|<span data-ttu-id="375fd-124">集計が削除されます。</span><span class="sxs-lookup"><span data-stu-id="375fd-124">Aggregation would be dropped</span></span>|<span data-ttu-id="375fd-125">警告</span><span class="sxs-lookup"><span data-stu-id="375fd-125">Warning</span></span>|  
|<span data-ttu-id="375fd-126">柔軟な集計が削除されます。</span><span class="sxs-lookup"><span data-stu-id="375fd-126">Flexible aggregation would be dropped</span></span>|<span data-ttu-id="375fd-127">警告</span><span class="sxs-lookup"><span data-stu-id="375fd-127">Warning</span></span>|  
|<span data-ttu-id="375fd-128">インデックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="375fd-128">Indexes will be dropped</span></span>|<span data-ttu-id="375fd-129">警告</span><span class="sxs-lookup"><span data-stu-id="375fd-129">Warning</span></span>|  
|<span data-ttu-id="375fd-130">子オブジェクトでないオブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="375fd-130">Non-child object will be processed</span></span>|<span data-ttu-id="375fd-131">警告</span><span class="sxs-lookup"><span data-stu-id="375fd-131">Warning</span></span>|  
  
 <span data-ttu-id="375fd-132">**[オブジェクトの処理]**</span><span class="sxs-lookup"><span data-stu-id="375fd-132">**Process Object**</span></span>  
 <span data-ttu-id="375fd-133">処理操作の対象となる依存オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="375fd-133">Select the dependent objects that you want to process with the processing operation.</span></span> <span data-ttu-id="375fd-134">選択されていない依存オブジェクトは、処理操作が完了した後に処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="375fd-134">Dependent objects that are not selected must be processed after the processing operation is finished.</span></span> <span data-ttu-id="375fd-135">処理しないと、それらのオブジェクトは使用できません。</span><span class="sxs-lookup"><span data-stu-id="375fd-135">Otherwise, they cannot be used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375fd-136">参照</span><span class="sxs-lookup"><span data-stu-id="375fd-136">See Also</span></span>  
 <span data-ttu-id="375fd-137">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="375fd-137">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="375fd-138">[[処理] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="375fd-138">[Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](process-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
