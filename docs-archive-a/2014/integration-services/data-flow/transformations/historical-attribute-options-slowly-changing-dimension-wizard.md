---
title: 履歴属性オプション (緩やかに変化するディメンション ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad005d6b8f80973abeb47dd881ef02b669d7b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644071"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="96117-102">[履歴属性オプション] (緩やかに変化するディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="96117-102">Historical Attribute Options (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="96117-103">**[履歴属性オプション]** ダイアログ ボックスを使用すると、開始日や終了日によって履歴属性を表示したり、専用に作成された列に履歴属性を記録したりできます。</span><span class="sxs-lookup"><span data-stu-id="96117-103">Use the **Historical Attributes Options** dialog box to show historical attributes by start and end dates, or to record historical attributes in a column specially created for this purpose.</span></span>  
  
 <span data-ttu-id="96117-104">このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96117-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="96117-105">オプション</span><span class="sxs-lookup"><span data-stu-id="96117-105">Options</span></span>  
 <span data-ttu-id="96117-106">**[現在のレコードと有効期限が切れたレコードを 1 列で表示する]**</span><span class="sxs-lookup"><span data-stu-id="96117-106">**Use a single column to show current and expired records**</span></span>  
 <span data-ttu-id="96117-107">1 列を使用して履歴属性のステータスを記録する場合は、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="96117-107">If you choose to use a single column to record the status of historical attributes, the following options are available:</span></span>  
  
|<span data-ttu-id="96117-108">オプション</span><span class="sxs-lookup"><span data-stu-id="96117-108">Option</span></span>|<span data-ttu-id="96117-109">説明</span><span class="sxs-lookup"><span data-stu-id="96117-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="96117-110">**[現在のレコードを示す列]**</span><span class="sxs-lookup"><span data-stu-id="96117-110">**Column to indicate current record**</span></span>|<span data-ttu-id="96117-111">現在のレコードを示す列を選択します。</span><span class="sxs-lookup"><span data-stu-id="96117-111">Select a column in which to indicate the current record.</span></span>|  
|<span data-ttu-id="96117-112">**[現時点での値]**</span><span class="sxs-lookup"><span data-stu-id="96117-112">**Value when current**</span></span>|<span data-ttu-id="96117-113">**[True]** または **[Current]** を使用してレコードが現在のレコードであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="96117-113">Use either **True** or **Current** to show whether the record is current.</span></span>|  
|<span data-ttu-id="96117-114">**[有効期限切れの値]**</span><span class="sxs-lookup"><span data-stu-id="96117-114">**Expiration value**</span></span>|<span data-ttu-id="96117-115">**[False]** または **[Expired]** を使用してレコードが履歴の値であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="96117-115">Use either **False** or **Expired** to show whether the record is a historical value.</span></span>|  
  
 <span data-ttu-id="96117-116">**[開始日と終了日を使用して現在のレコードと有効期限が切れたレコードを識別する]**</span><span class="sxs-lookup"><span data-stu-id="96117-116">**Use start and end dates to identify current and expired records**</span></span>  
 <span data-ttu-id="96117-117">このオプションのディメンション テーブルには、日付列を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="96117-117">The dimension table for this option must include a date column.</span></span> <span data-ttu-id="96117-118">履歴属性を開始日および終了日を使用して示す場合は、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="96117-118">If you choose to show historical attributes by start and end dates, the following options are available:</span></span>  
  
|<span data-ttu-id="96117-119">オプション</span><span class="sxs-lookup"><span data-stu-id="96117-119">Option</span></span>|<span data-ttu-id="96117-120">説明</span><span class="sxs-lookup"><span data-stu-id="96117-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="96117-121">**[開始日の列]**</span><span class="sxs-lookup"><span data-stu-id="96117-121">**Start date column**</span></span>|<span data-ttu-id="96117-122">ディメンション テーブルで開始日を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="96117-122">Select the column in the dimension table to contain the start date.</span></span>|  
|<span data-ttu-id="96117-123">**[終了日の列]**</span><span class="sxs-lookup"><span data-stu-id="96117-123">**End date column**</span></span>|<span data-ttu-id="96117-124">ディメンション テーブルで終了日を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="96117-124">Select the column in the dimension table to contain the end date.</span></span>|  
|<span data-ttu-id="96117-125">**[日付の値を設定する変数]**</span><span class="sxs-lookup"><span data-stu-id="96117-125">**Variable to set date values**</span></span>|<span data-ttu-id="96117-126">日付の変数を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="96117-126">Select a date variable from the list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96117-127">参照</span><span class="sxs-lookup"><span data-stu-id="96117-127">See Also</span></span>  
 [<span data-ttu-id="96117-128">緩やかに変化するディメンション ウィザードを使用して出力を構成する</span><span class="sxs-lookup"><span data-stu-id="96117-128">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
