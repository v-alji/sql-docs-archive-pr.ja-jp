---
title: 現地の通貨参照の定義 (ビジネスインテリジェンスウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: bcd5c01839ecc7ae120089f17a1b909f18464e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718908"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a><span data-ttu-id="ce704-102">現地の通貨参照の定義 (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="ce704-102">Define Local Currency Reference (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="ce704-103">**[現地の通貨参照の定義]** ページを使用すると、 **[換算の種類の選択]** ページで指定された多対多または多対一の変換を実行する通貨の換算機能のための現地通貨を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ce704-103">Use the **Define Local Currency Reference** page to define the local currencies for currency conversion functionality that covers the many-to-many or many-to-one conversion types specified on the **Select Conversion Type** page.</span></span> <span data-ttu-id="ce704-104">現地通貨とは、 **[メジャーの選択]** ページで選択されたメジャーのトランザクションが保存される通貨です。</span><span class="sxs-lookup"><span data-stu-id="ce704-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce704-105">ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="ce704-105">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ce704-106">また、このページは、 **[換算の種類の選択]** ページで **[一対多]** を選択した場合にも表示されません。</span><span class="sxs-lookup"><span data-stu-id="ce704-106">This page also does not appear if **One-to-Many** was selected on the **Select Conversion Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ce704-107">Options</span><span class="sxs-lookup"><span data-stu-id="ce704-107">Options</span></span>  
 <span data-ttu-id="ce704-108">**[ファクト テーブルの識別子]**</span><span class="sxs-lookup"><span data-stu-id="ce704-108">**Identifiers in the fact table**</span></span>  
 <span data-ttu-id="ce704-109">選択すると、 **[メジャーの選択]** ページで選択されたメジャーを格納するファクト テーブルから参照される、通貨ディメンションの現地通貨の通貨識別子を表す属性を指定できます</span><span class="sxs-lookup"><span data-stu-id="ce704-109">Select to specify an attribute that provides currency identifiers for local currencies in a currency dimension referenced by the fact table that contains the measures selected on the **Select Measures** page.</span></span> <span data-ttu-id="ce704-110">( `Type` プロパティが*currency*に設定されている1つの通貨ディメンション)。</span><span class="sxs-lookup"><span data-stu-id="ce704-110">(A currency dimension in one whose `Type` property is set to *Currency*.)</span></span>  
  
 <span data-ttu-id="ce704-111">このオプションは、トランザクションでそのトランザクション自体の現地通貨を決定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ce704-111">Use this option when the transaction itself determines the local currency for that transaction.</span></span> <span data-ttu-id="ce704-112">たとえば、サンプルデータベースの場合、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Internet Sales メジャーグループには、通貨ディメンションに対する標準のディメンションリレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="ce704-112">For example, in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="ce704-113">このメジャー グループのファクト テーブルは、このディメンションのディメンション テーブル内の通貨識別子を参照する外部キー列を格納します。</span><span class="sxs-lookup"><span data-stu-id="ce704-113">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span>  
  
 <span data-ttu-id="ce704-114">**[ファクト データによって参照される通貨ディメンションと属性]**</span><span class="sxs-lookup"><span data-stu-id="ce704-114">**Currency dimension and attribute referenced by the fact data**</span></span>  
 <span data-ttu-id="ce704-115">通貨ディメンションのメンバーが現地通貨の通貨識別子を表す、その通貨ディメンション内の通貨属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="ce704-115">Select the currency attribute within a currency dimension whose members represent currency identifiers for local currencies.</span></span> <span data-ttu-id="ce704-116">通貨属性とは、 `Type` プロパティが*currency*に設定されている属性です。</span><span class="sxs-lookup"><span data-stu-id="ce704-116">(A currency attribute is one whose `Type` property is set to *Currency*.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce704-117">**[ファクト テーブルの識別子]** オプションが選択されていない場合は、このオプションを利用できません。</span><span class="sxs-lookup"><span data-stu-id="ce704-117">This option is not available if the **Identifiers in the fact table** option is not selected.</span></span>  
  
 <span data-ttu-id="ce704-118">**[ディメンション テーブルの属性]**</span><span class="sxs-lookup"><span data-stu-id="ce704-118">**Attributes in the dimension table**</span></span>  
 <span data-ttu-id="ce704-119">選択すると、現地通貨の通貨識別子を格納するメジャー グループに関連したディメンションから属性を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ce704-119">Select to specify an attribute from a dimension related to the measure group that contains currency identifiers for local currencies.</span></span>  
  
 <span data-ttu-id="ce704-120">このオプションは、トランザクションと他のビジネス エンティティ (たとえば場所) とのリレーションシップによって、そのトランザクションの現地通貨が決定される場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ce704-120">Use this option when the relationship between a transaction and another business entity, such as a location, determines the local currency for that transaction.</span></span> <span data-ttu-id="ce704-121">たとえば、サンプルデータベースの場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 財務報告のメジャーグループには、組織ディメンションを介して、通貨ディメンションに対する参照ディメンションリレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="ce704-121">For example, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="ce704-122">つまり、[Financial Reporting] メジャー グループのファクト テーブルには、組織ディメンションのディメンション テーブル内のメンバーを参照する外部キー列があります。</span><span class="sxs-lookup"><span data-stu-id="ce704-122">That is, the fact table for the Financial Reporting measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="ce704-123">さらに、組織ディメンションのディメンション テーブルには、通貨ディメンションのディメンション テーブル内の通貨識別子を参照する外部キー列があります。</span><span class="sxs-lookup"><span data-stu-id="ce704-123">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span>  
  
 <span data-ttu-id="ce704-124">**[通貨を参照するディメンションの属性]**</span><span class="sxs-lookup"><span data-stu-id="ce704-124">**Dimension attribute that references currency**</span></span>  
 <span data-ttu-id="ce704-125">ディメンションのメンバーが現地通貨の通貨識別子を参照する、そのディメンション内の属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="ce704-125">Select the attribute within a dimension whose members reference the currency identifiers for local currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce704-126">**[ディメンション テーブルの属性]** オプションが選択されていない場合は、このオプションを利用できません。</span><span class="sxs-lookup"><span data-stu-id="ce704-126">This option is not available if the **Attributes in the dimension table** option is not selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce704-127">参照</span><span class="sxs-lookup"><span data-stu-id="ce704-127">See Also</span></span>  
 <span data-ttu-id="ce704-128">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ce704-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="ce704-129">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ce704-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="ce704-130">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="ce704-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
