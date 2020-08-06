---
title: 勘定科目インテリジェンスの定義 (ディメンションウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90871e2299d1531db1b678b1f4b16ddd7f1db767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643015"
---
# <a name="define-account-intelligence-dimension-wizard"></a><span data-ttu-id="b694b-102">[勘定科目インテリジェンスの定義] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="b694b-102">Define Account Intelligence (Dimension Wizard)</span></span>
  <span data-ttu-id="b694b-103">**[勘定科目インテリジェンスの定義]** ページを使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで定義された勘定科目の種類を、ディメンションの **[勘定科目の種類]** の属性の種類に関連付けられた、ディメンションの属性で定義された勘定科目の種類にマップできます。</span><span class="sxs-lookup"><span data-stu-id="b694b-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined in the dimension attribute associated with the **Account Type** attribute type in the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b694b-104">**[ディメンションの種類の選択]** ページの **[標準ディメンション]** を選択した場合、およびディメンションの属性を **[ディメンションの種類を指定]** ページの **[勘定科目の種類]** にマップした場合のみ、このページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b694b-104">This page is displayed only if you selected **Standard dimension** on the **Select the Dimension Type** page and if you mapped a dimension attribute to the **Account Type** attribute type on the **Specify Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b694b-105">Options</span><span class="sxs-lookup"><span data-stu-id="b694b-105">Options</span></span>  
 <span data-ttu-id="b694b-106">**[基になるテーブルの勘定科目の種類]**</span><span class="sxs-lookup"><span data-stu-id="b694b-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="b694b-107">**[ディメンションのキーおよび種類を指定]** ページの **[勘定科目の種類]** の属性の種類に割り当てられた、ディメンションの属性に含まれる値を表示します。</span><span class="sxs-lookup"><span data-stu-id="b694b-107">Displays the values contained in the dimension attribute assigned to the **Account Type** attribute type in the **Specify Dimension Key and Type** page.</span></span>  
  
 <span data-ttu-id="b694b-108">**[ビルトイン勘定科目の種類]**</span><span class="sxs-lookup"><span data-stu-id="b694b-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="b694b-109">ソース テーブルの勘定科目の種類にマップされる、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで定義される勘定科目の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b694b-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="b694b-110">次の表は、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで定義される勘定科目の種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="b694b-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="b694b-111">値</span><span class="sxs-lookup"><span data-stu-id="b694b-111">Value</span></span>|<span data-ttu-id="b694b-112">説明</span><span class="sxs-lookup"><span data-stu-id="b694b-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b694b-113">**Asset**</span><span class="sxs-lookup"><span data-stu-id="b694b-113">**Asset**</span></span>|<span data-ttu-id="b694b-114">ある時点で所有している物の価値です。</span><span class="sxs-lookup"><span data-stu-id="b694b-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="b694b-115">**Balance**</span><span class="sxs-lookup"><span data-stu-id="b694b-115">**Balance**</span></span>|<span data-ttu-id="b694b-116">ある時点でのある物の数です。</span><span class="sxs-lookup"><span data-stu-id="b694b-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="b694b-117">**[Expense]**</span><span class="sxs-lookup"><span data-stu-id="b694b-117">**Expense**</span></span>|<span data-ttu-id="b694b-118">費やした物の価値です。</span><span class="sxs-lookup"><span data-stu-id="b694b-118">Value of things spent.</span></span>|  
|<span data-ttu-id="b694b-119">**Flow**</span><span class="sxs-lookup"><span data-stu-id="b694b-119">**Flow**</span></span>|<span data-ttu-id="b694b-120">物の増加数です。</span><span class="sxs-lookup"><span data-stu-id="b694b-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="b694b-121">**Income**</span><span class="sxs-lookup"><span data-stu-id="b694b-121">**Income**</span></span>|<span data-ttu-id="b694b-122">受け取った物の価値です。</span><span class="sxs-lookup"><span data-stu-id="b694b-122">Value of things received.</span></span>|  
|<span data-ttu-id="b694b-123">**[Liability]**</span><span class="sxs-lookup"><span data-stu-id="b694b-123">**Liability**</span></span>|<span data-ttu-id="b694b-124">ある時点で借りている物の価値です。</span><span class="sxs-lookup"><span data-stu-id="b694b-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="b694b-125">**統計**</span><span class="sxs-lookup"><span data-stu-id="b694b-125">**Statistical**</span></span>|<span data-ttu-id="b694b-126">ある物の計算された割合、または集計されない物の数です。</span><span class="sxs-lookup"><span data-stu-id="b694b-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b694b-127">参照</span><span class="sxs-lookup"><span data-stu-id="b694b-127">See Also</span></span>  
 <span data-ttu-id="b694b-128">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b694b-128">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="b694b-129">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b694b-129">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b694b-130">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="b694b-130">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
