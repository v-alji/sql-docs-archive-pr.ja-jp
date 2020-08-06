---
title: '[変換の種類の選択] (ビジネスインテリジェンスウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1f83fdf566b52a5fe79bea7a4a676274423d1091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633347"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a><span data-ttu-id="e54fa-102">[換算の種類の選択] (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e54fa-102">Select Conversion Type (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="e54fa-103">**[換算の種類の選択]** ページを使用すると、複数の通貨で保存されているトランザクションに関して、現地通貨とレポート用通貨の間のリレーションシップを定義できます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-103">Use the **Select Conversion Type** page to define the relationship between local currencies and reporting currencies for transactions stored in multiple currencies.</span></span> <span data-ttu-id="e54fa-104">現地通貨とは、 **[メジャーの選択]** ページで選択されたメジャーのトランザクションが保存される通貨です。</span><span class="sxs-lookup"><span data-stu-id="e54fa-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span> <span data-ttu-id="e54fa-105">レポート用通貨とは、 **[メジャーの選択]** ページで選択されたトランザクションが変換される通貨です。</span><span class="sxs-lookup"><span data-stu-id="e54fa-105">A reporting currency is the currency in which the transactions selected in the **Select Measures** page are translated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e54fa-106">ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="e54fa-106">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="e54fa-107">Options</span><span class="sxs-lookup"><span data-stu-id="e54fa-107">Options</span></span>  
 <span data-ttu-id="e54fa-108">**多対多**</span><span class="sxs-lookup"><span data-stu-id="e54fa-108">**Many-to-many**</span></span>  
 <span data-ttu-id="e54fa-109">現地通貨を使用してトランザクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="e54fa-109">Stores transactions using local currencies.</span></span> <span data-ttu-id="e54fa-110">この通貨換算機能は、このようなトランザクションを **[通貨換算オプションの設定]** ページで指定された、ピボット通貨に換算した後、1 つまたは複数の他のレポート用通貨に換算します。</span><span class="sxs-lookup"><span data-stu-id="e54fa-110">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
 <span data-ttu-id="e54fa-111">たとえば、ピボット通貨を米国ドル (USD) に設定し、トランザクションをユーロ (EUR)、豪ドル (AUD)、およびメキシコ ペソ (MXN) でファクト テーブルに格納するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-111">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="e54fa-112">このオプションを選択すると、これらのトランザクションは、指定された現地通貨からピボット通貨に換算されます。その後、換算されたトランザクションは、ピボット通貨から指定されたレポート用通貨に再び換算されます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-112">Selecting this option converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="e54fa-113">その結果、トランザクションを指定された現地通貨で格納して、指定のピボット通貨または **[レポート用通貨の指定]** ページで指定されたいずれかのレポート用通貨で表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e54fa-113">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
 <span data-ttu-id="e54fa-114">**多対一**</span><span class="sxs-lookup"><span data-stu-id="e54fa-114">**Many-to-one**</span></span>  
 <span data-ttu-id="e54fa-115">現地通貨を使用してトランザクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="e54fa-115">Stores transactions using local currencies.</span></span> <span data-ttu-id="e54fa-116">この通貨換算機能は、このようなトランザクションを **[通貨換算オプションの設定]** ページで指定された、ピボット通貨に換算します。</span><span class="sxs-lookup"><span data-stu-id="e54fa-116">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page.</span></span> <span data-ttu-id="e54fa-117">ピボット通貨は、指定された唯一のレポート用通貨としての役割を持ちます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-117">The pivot currency serves as the only specified reporting currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e54fa-118"> このオプションを選択した場合、 **[レポート用通貨の指定]** ページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="e54fa-118">If this option is selected, the **Specify Reporting Currencies** page does not appear.</span></span>  
  
 <span data-ttu-id="e54fa-119">たとえば、ピボット通貨を米国ドル (USD) に設定し、トランザクションをユーロ (EUR)、豪ドル (AUD)、およびメキシコ ペソ (MXN) でファクト テーブルに格納するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-119">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="e54fa-120">このオプションを選択すると、これらのトランザクションは、指定された現地通貨からピボット通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-120">Selecting this option converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="e54fa-121">その結果、トランザクションを指定された現地通貨で格納して、指定のピボット通貨で表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e54fa-121">The result is that transactions can be stored in the specified local currencies and viewed in the specified pivot currency.</span></span>  
  
 <span data-ttu-id="e54fa-122">**[一対多]**</span><span class="sxs-lookup"><span data-stu-id="e54fa-122">**One-to-many**</span></span>  
 <span data-ttu-id="e54fa-123">トランザクションを **[通貨換算オプションの設定]** ページで指定された、ピボット通貨を使用して格納した後、1 つまたは複数の他のレポート用通貨に換算します。</span><span class="sxs-lookup"><span data-stu-id="e54fa-123">Store transactions using the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e54fa-124"> このオプションを選択した場合、 **[現地の通貨参照の定義]** ページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="e54fa-124">If this option is selected, the **Define Local Currency Reference** page does not appear.</span></span>  
  
 <span data-ttu-id="e54fa-125">たとえば、ピボット通貨を米国ドル (USD) に設定し、トランザクションを USD でファクト テーブルに格納するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-125">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="e54fa-126">このオプションを選択すると、これらのトランザクションは、ピボット通貨から指定されたレポート用通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="e54fa-126">Selecting this option converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="e54fa-127">その結果、トランザクションを指定のピボット通貨で格納して、指定のピボット通貨または **[レポート用通貨の指定]** ページで指定されたいずれかのレポート用通貨で表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e54fa-127">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54fa-128">参照</span><span class="sxs-lookup"><span data-stu-id="e54fa-128">See Also</span></span>  
 <span data-ttu-id="e54fa-129">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e54fa-129">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="e54fa-130">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e54fa-130">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e54fa-131">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="e54fa-131">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
