---
title: '[処理の進行状況] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processprogress.f1
ms.assetid: f3bd5278-3a83-4fd9-9903-e81bdd4b6892
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e436eeab21a37ae174a5003c01e77c05240238b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741354"
---
# <a name="process-progress-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="23eaa-102">[処理の進行状況] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="23eaa-102">Process Progress Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="23eaa-103">**と** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [処理の進行状況] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]で処理を監視できます。</span><span class="sxs-lookup"><span data-stu-id="23eaa-103">Use the **Process Progress** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to monitor processing in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="23eaa-104">**[処理の進行状況]** ダイアログ ボックスは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクト上で処理が開始される場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="23eaa-104">The **Process Progress** dialog box appears when processing begins on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="23eaa-105">Options</span><span class="sxs-lookup"><span data-stu-id="23eaa-105">Options</span></span>  
 <span data-ttu-id="23eaa-106">**状態ツリー ビュー**</span><span class="sxs-lookup"><span data-stu-id="23eaa-106">**Status tree view**</span></span>  
 <span data-ttu-id="23eaa-107">開始時刻、停止時刻、および進行状況情報を含む、処理中のオブジェクトに関する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスからの状態メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="23eaa-107">Displays status messages from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance regarding the objects being processed, including start time, stop time, and progress information.</span></span> <span data-ttu-id="23eaa-108">アイテムを右クリックして **[コピー]** を選択し、状態メッセージの詳細をクリップボードにコピーするか、アイテムをダブルクリックして、**[詳細表示]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="23eaa-108">Right-click an item and select **Copy** to copy the details of a status message to the clipboard, or double-click an item to display the **View Details** dialog box.</span></span> <span data-ttu-id="23eaa-109">**[詳細表示]** ダイアログ ボックスの詳細については、「[[詳細表示] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eaa-109">For more information about the **View Details** dialog box, see [View Details Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="23eaa-110">**状態の説明**</span><span class="sxs-lookup"><span data-stu-id="23eaa-110">**Status description**</span></span>  
 <span data-ttu-id="23eaa-111">処理中の操作の現在の処理状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="23eaa-111">Displays the current status of the processing operation.</span></span>  
  
 <span data-ttu-id="23eaa-112">**Stop**</span><span class="sxs-lookup"><span data-stu-id="23eaa-112">**Stop**</span></span>  
 <span data-ttu-id="23eaa-113">処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="23eaa-113">Click to stop the processing operation.</span></span>  
  
 <span data-ttu-id="23eaa-114">**処理**</span><span class="sxs-lookup"><span data-stu-id="23eaa-114">**Reprocess**</span></span>  
 <span data-ttu-id="23eaa-115">**[処理の進行状況]** ダイアログ ボックスを表示した処理中の操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="23eaa-115">Click to repeat the processing operation that displayed the **Process Progress** dialog box.</span></span>  
  
 <span data-ttu-id="23eaa-116">**詳細の表示**</span><span class="sxs-lookup"><span data-stu-id="23eaa-116">**View Details**</span></span>  
 <span data-ttu-id="23eaa-117">**[詳細表示]** ダイアログ ボックスを表示して、**状態ツリー ビュー**で選択したアイテムに関する詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="23eaa-117">Click to open the **View Details** dialog box and display details regarding the item selected in **Status tree view**.</span></span> <span data-ttu-id="23eaa-118">**[詳細表示]** ダイアログ ボックスの詳細については、「[[詳細表示] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23eaa-118">For more information about the **View Details** dialog box, see [View Details Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](view-details-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23eaa-119">参照</span><span class="sxs-lookup"><span data-stu-id="23eaa-119">See Also</span></span>  
 <span data-ttu-id="23eaa-120">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="23eaa-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="23eaa-121">多次元モデルのオブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="23eaa-121">Multidimensional Model Object Processing</span></span>](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
