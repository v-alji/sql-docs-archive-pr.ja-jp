---
title: 勘定科目インテリジェンスの定義 (ビジネスインテリジェンスウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.mapaccounttype.f1
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17b8136e79097cd502d6b239ba6867c4e678c70f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712641"
---
# <a name="define-account-intelligence-business-intelligence-wizard"></a><span data-ttu-id="bfcd1-102">[勘定科目インテリジェンスの定義] (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="bfcd1-102">Define Account Intelligence (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="bfcd1-103">**[勘定科目インテリジェンスの定義]** ページでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで定義された勘定科目の種類を、勘定科目ディメンションにデータを供給するデータ ソース内のソース テーブルによって定義される勘定科目の種類にマップできます。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined by a source table in the data source that supplies the data for the account dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bfcd1-104"> このページは、ディメンションの属性が、 **[ディメンションの属性の構成]** ページの **[勘定科目の種類]** の属性の型にマップされた場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-104">This page will appear if a dimension attribute was mapped to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bfcd1-105">Options</span><span class="sxs-lookup"><span data-stu-id="bfcd1-105">Options</span></span>  
 <span data-ttu-id="bfcd1-106">**[基になるテーブルの勘定科目の種類]**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="bfcd1-107">**[ディメンションの属性の構成]** ページの **[勘定科目の種類]** の属性の型に割り当てられた、ディメンション属性が持つ値を表示します。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-107">Displays the values that are contained in the dimension attribute assigned to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
 <span data-ttu-id="bfcd1-108">**[ビルトイン勘定科目の種類]**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="bfcd1-109">ソース テーブルの勘定科目の種類にマップされる、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで定義される勘定科目の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="bfcd1-110">次の表は、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで定義される勘定科目の種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="bfcd1-111">値</span><span class="sxs-lookup"><span data-stu-id="bfcd1-111">Value</span></span>|<span data-ttu-id="bfcd1-112">説明</span><span class="sxs-lookup"><span data-stu-id="bfcd1-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bfcd1-113">**Asset**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-113">**Asset**</span></span>|<span data-ttu-id="bfcd1-114">ある時点で所有している物の価値です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="bfcd1-115">**Balance**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-115">**Balance**</span></span>|<span data-ttu-id="bfcd1-116">ある時点でのある物の数です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="bfcd1-117">**[Expense]**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-117">**Expense**</span></span>|<span data-ttu-id="bfcd1-118">費やした物の価値です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-118">Value of things spent.</span></span>|  
|<span data-ttu-id="bfcd1-119">**Flow**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-119">**Flow**</span></span>|<span data-ttu-id="bfcd1-120">物の増加数です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="bfcd1-121">**Income**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-121">**Income**</span></span>|<span data-ttu-id="bfcd1-122">受け取った物の価値です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-122">Value of things received.</span></span>|  
|<span data-ttu-id="bfcd1-123">**[Liability]**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-123">**Liability**</span></span>|<span data-ttu-id="bfcd1-124">ある時点で借りている物の価値です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="bfcd1-125">**統計**</span><span class="sxs-lookup"><span data-stu-id="bfcd1-125">**Statistical**</span></span>|<span data-ttu-id="bfcd1-126">ある物の計算された割合、または集計されない物の数です。</span><span class="sxs-lookup"><span data-stu-id="bfcd1-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfcd1-127">参照</span><span class="sxs-lookup"><span data-stu-id="bfcd1-127">See Also</span></span>  
 <span data-ttu-id="bfcd1-128">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="bfcd1-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="bfcd1-129">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="bfcd1-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="bfcd1-130">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="bfcd1-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
