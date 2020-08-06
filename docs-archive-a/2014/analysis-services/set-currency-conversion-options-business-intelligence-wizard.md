---
title: 通貨換算オプションの設定 (ビジネスインテリジェンスウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.calculationsettings.f1
ms.assetid: a49d4e1f-bdda-4a83-ab4f-ce8c500e1d6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61877deb0bc422d65f977e3fc9de3e678f7d8477
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736907"
---
# <a name="set-currency-conversion-options-business-intelligence-wizard"></a><span data-ttu-id="3f6fe-102">[通貨換算オプションの設定] (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="3f6fe-102">Set Currency Conversion Options (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="3f6fe-103">**[通貨換算オプションの設定]** ページを使用すると、換算レートを含むメジャー グループに対して通貨換算の計算を定義できます。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-103">Use the **Set Currency Conversion** page to define currency conversion calculations for a measure group that contains exchange rates.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f6fe-104">ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f6fe-105">Options</span><span class="sxs-lookup"><span data-stu-id="3f6fe-105">Options</span></span>  
 <span data-ttu-id="3f6fe-106">**[換算レートを含むメジャー グループを選択]**</span><span class="sxs-lookup"><span data-stu-id="3f6fe-106">**Select the measure group that contains exchange rates**</span></span>  
 <span data-ttu-id="3f6fe-107">通貨換算の計算が参照する換算レートを含むメジャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-107">Select the measure group that contains the exchange rates that the currency conversion calculations should reference.</span></span>  
  
 <span data-ttu-id="3f6fe-108">**[ピボット通貨の指定]**</span><span class="sxs-lookup"><span data-stu-id="3f6fe-108">**Specify the pivot currency**</span></span>  
 <span data-ttu-id="3f6fe-109">メジャー グループのピボット通貨としての役割を果たすメンバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-109">Select the member that serves as the pivot currency for the measure group.</span></span>  
  
 <span data-ttu-id="3f6fe-110">**[入力した換算レート (サンプル通貨を選択します)]**</span><span class="sxs-lookup"><span data-stu-id="3f6fe-110">**Select how you entered your exchange rates (select a sample currency)**</span></span>  
 <span data-ttu-id="3f6fe-111">通貨ディメンションからサンプル通貨を表すメンバーを選択して、換算レートの動向をよりわかりやすく表示するため、[1 つのサンプル通貨につき X のピボット通貨] オプションと [1 つのピボット通貨につき X のサンプル通貨] オプションのテキストを変更します。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-111">Select a member representing a sample currency from the currency dimension to change the text for the X pivot currency per 1 sample currency and X sample currency per 1 pivot currency options to better display the exchange rate direction.</span></span>  
  
 <span data-ttu-id="3f6fe-112">**[1 つのサンプル通貨につき X のピボット通貨]**</span><span class="sxs-lookup"><span data-stu-id="3f6fe-112">**X pivot currency per 1 sample currency**</span></span>  
 <span data-ttu-id="3f6fe-113">レート メジャー グループ内の換算レートが、指定のピボット通貨に対する乗数を表すことを示します。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-113">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified pivot currency.</span></span>  
  
 <span data-ttu-id="3f6fe-114">**[1 つのピボット通貨につき X のサンプル通貨]**</span><span class="sxs-lookup"><span data-stu-id="3f6fe-114">**X sample currency per 1 pivot currency**</span></span>  
 <span data-ttu-id="3f6fe-115">レート メジャー グループ内の換算レートが、指定されたサンプル通貨に対する乗数を表すことを示します。</span><span class="sxs-lookup"><span data-stu-id="3f6fe-115">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified sample currency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6fe-116">参照</span><span class="sxs-lookup"><span data-stu-id="3f6fe-116">See Also</span></span>  
 <span data-ttu-id="3f6fe-117">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3f6fe-117">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="3f6fe-118">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3f6fe-118">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="3f6fe-119">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="3f6fe-119">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
