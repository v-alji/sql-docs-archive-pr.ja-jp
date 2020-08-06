---
title: '[ディメンション処理変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 50ba42292c1f48c9b1cdf2ba00c709dacd2f9675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645193"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="c5b2f-102">[ディメンション処理変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="c5b2f-102">Dimension Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="c5b2f-103">**[ディメンション処理変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-103">Use the **Connection Manager** page of the **Dimension Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c5b2f-104">ディメンション処理変換先の詳細については、「 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c5b2f-105">Options</span><span class="sxs-lookup"><span data-stu-id="c5b2f-105">Options</span></span>  
 <span data-ttu-id="c5b2f-106">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-106">**Connection manager**</span></span>  
 <span data-ttu-id="c5b2f-107">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-107">Select an existing connection manager from the list, or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="c5b2f-108">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-108">**New**</span></span>  
 <span data-ttu-id="c5b2f-109">**[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-109">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="c5b2f-110">**利用可能なディメンションの一覧**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-110">**List of available dimensions**</span></span>  
 <span data-ttu-id="c5b2f-111">処理するディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-111">Select the dimension to process.</span></span>  
  
 <span data-ttu-id="c5b2f-112">**[処理方法]**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-112">**Processing method**</span></span>  
 <span data-ttu-id="c5b2f-113">一覧で選択したディメンションに適用する処理方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-113">Select the processing method to apply to the dimension selected in the list.</span></span> <span data-ttu-id="c5b2f-114">このオプションの既定値は **[完全]** です。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-114">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="c5b2f-115">値</span><span class="sxs-lookup"><span data-stu-id="c5b2f-115">Value</span></span>|<span data-ttu-id="c5b2f-116">説明</span><span class="sxs-lookup"><span data-stu-id="c5b2f-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5b2f-117">**[追加 (増分)]**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-117">**Add (incremental)**</span></span>|<span data-ttu-id="c5b2f-118">ディメンションの増分処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-118">Perform an incremental processing of the dimension.</span></span>|  
|<span data-ttu-id="c5b2f-119">**完全**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-119">**Full**</span></span>|<span data-ttu-id="c5b2f-120">ディメンションの完全処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-120">Perform full processing of the dimension.</span></span>|  
|<span data-ttu-id="c5b2f-121">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="c5b2f-121">**Update**</span></span>|<span data-ttu-id="c5b2f-122">ディメンションの更新処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5b2f-122">Perform an update processing of the dimension.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5b2f-123">参照</span><span class="sxs-lookup"><span data-stu-id="c5b2f-123">See Also</span></span>  
 <span data-ttu-id="c5b2f-124">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c5b2f-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c5b2f-125">[ディメンション処理変換先エディター &#40;マッピングページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="c5b2f-125">[Dimension Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="c5b2f-126">[ディメンション処理変換先エディター &#40;[詳細設定] ページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5b2f-126">[Dimension Processing Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)</span></span>  
  
  
