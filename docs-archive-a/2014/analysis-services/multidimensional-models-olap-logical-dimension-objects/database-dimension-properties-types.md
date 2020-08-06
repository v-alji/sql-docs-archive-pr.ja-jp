---
title: ディメンションの種類 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5e0c16a57081aa1d9ed3cc6964d1f17fa7135986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645878"
---
# <a name="dimension-types"></a><span data-ttu-id="ca1e7-102">ディメンションの種類</span><span class="sxs-lookup"><span data-stu-id="ca1e7-102">Dimension Types</span></span>
  <span data-ttu-id="ca1e7-103">`Type` プロパティの設定は、ディメンションの内容に関する情報をサーバーおよびクライアント アプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-103">The `Type` property setting provides information about the contents of a dimension to server and client applications.</span></span> <span data-ttu-id="ca1e7-104">`Type` の設定がクライアント アプリケーションへのガイダンスの提供のみを目的としている場合は、この設定を省略できます。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-104">In some cases, the `Type` setting only provides guidance for client applications and is optional.</span></span> <span data-ttu-id="ca1e7-105">一方、`Accounts` ディメンションや `Time` ディメンションでは、ディメンションおよびその属性の `Type` プロパティの設定によって、サーバー ベースの具体的な動作が決まるため、キューブで特定の動作を実装する際に、この設定が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-105">In other cases, such as `Accounts` or `Time` dimensions, the `Type` property settings for the dimension and its attributes determine specific server-based behaviors and may be required to implement certain behaviors in the cube.</span></span> <span data-ttu-id="ca1e7-106">たとえば、ディメンションの `Type` プロパティを `Accounts` に設定すると、標準ディメンションに勘定科目属性が含まれていることがクライアント アプリケーションに示されます。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-106">For example, the `Type` property of a dimension can be set to `Accounts` to indicate to client applications that the standard dimension contains account attributes.</span></span> <span data-ttu-id="ca1e7-107">時間、勘定科目、通貨ディメンションの詳細については、「[日付型ディメンションの作成](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md)」、「[親子型ディメンションの財務アカウントの](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)作成」、および「[通貨型ディメンションの作成](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-107">For more information about time, account, and currency dimensions, see [Create a Date type Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Create a Finance Account of parent-child type Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), and [Create a Currency type Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="ca1e7-108">ディメンションの種類の既定の設定は `Regular` です。この設定では、ディメンションの内容に関して何も想定されません。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-108">The default setting for the dimension type is `Regular`, which makes no assumptions about the contents of the dimension.</span></span> <span data-ttu-id="ca1e7-109">ディメンション ウィザードを使用してディメンションを定義するときに `Time` を指定しない限り、初めてディメンションを定義する場合は、これがすべてのディメンションの既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-109">This is the default setting for all dimensions when you initially define a dimension unless you specify `Time` when defining the dimension using the Dimension Wizard.</span></span> <span data-ttu-id="ca1e7-110">また、ディメンション ウィザードの [ディメンションの種類] の一覧に適切な種類が表示されていない場合は、ディメンションの種類を `Regular` のままにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-110">You should also leave `Regular` as the dimension type if the Dimension Wizard does not list an appropriate type for Dimension type.</span></span>  
  
## <a name="available-dimension-types"></a><span data-ttu-id="ca1e7-111">使用可能なディメンションの種類</span><span class="sxs-lookup"><span data-stu-id="ca1e7-111">Available Dimension Types</span></span>  
 <span data-ttu-id="ca1e7-112">次の表では、で使用できるディメンションの種類について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-112">The following table describes the dimension types available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="ca1e7-113">[ディメンションの種類]</span><span class="sxs-lookup"><span data-stu-id="ca1e7-113">Dimension type</span></span>|<span data-ttu-id="ca1e7-114">説明</span><span class="sxs-lookup"><span data-stu-id="ca1e7-114">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ca1e7-115">Regular</span><span class="sxs-lookup"><span data-stu-id="ca1e7-115">Regular</span></span>|<span data-ttu-id="ca1e7-116">特定のディメンションの種類に設定されていない種類のディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-116">A dimension whose type has not been set to a special dimension type.</span></span>|  
|<span data-ttu-id="ca1e7-117">Time</span><span class="sxs-lookup"><span data-stu-id="ca1e7-117">Time</span></span>|<span data-ttu-id="ca1e7-118">属性が年、半期、四半期、月、日などの時間間隔を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-118">A dimension whose attributes represent time periods, such as years, semesters, quarters, months, and days.</span></span>|  
|<span data-ttu-id="ca1e7-119">Organization</span><span class="sxs-lookup"><span data-stu-id="ca1e7-119">Organization</span></span>|<span data-ttu-id="ca1e7-120">属性が従業員や子会社などの組織情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-120">A dimension whose attributes represent organizational information, such as employees or subsidiaries.</span></span>|  
|<span data-ttu-id="ca1e7-121">[地理的な場所]</span><span class="sxs-lookup"><span data-stu-id="ca1e7-121">Geography</span></span>|<span data-ttu-id="ca1e7-122">属性が市区町村や郵便番号などの地理情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-122">A dimension whose attributes represent geographic information, such as cities or postal codes.</span></span>|  
|<span data-ttu-id="ca1e7-123">BillOfMaterials</span><span class="sxs-lookup"><span data-stu-id="ca1e7-123">BillOfMaterials</span></span>|<span data-ttu-id="ca1e7-124">属性が製品の部品表などの在庫情報や製造情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-124">A dimension whose attributes represent inventory or manufacturing information, such as parts lists for products.</span></span>|  
|<span data-ttu-id="ca1e7-125">アカウント</span><span class="sxs-lookup"><span data-stu-id="ca1e7-125">Accounts</span></span>|<span data-ttu-id="ca1e7-126">財務報告用の勘定科目一覧表を表す属性を持つディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-126">A dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>|  
|<span data-ttu-id="ca1e7-127">顧客</span><span class="sxs-lookup"><span data-stu-id="ca1e7-127">Customers</span></span>|<span data-ttu-id="ca1e7-128">属性が顧客情報や連絡先情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-128">A dimension whose attributes represent customer or contact information.</span></span>|  
|<span data-ttu-id="ca1e7-129">製品</span><span class="sxs-lookup"><span data-stu-id="ca1e7-129">Products</span></span>|<span data-ttu-id="ca1e7-130">属性が製品情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-130">A dimension whose attributes represent product information.</span></span>|  
|<span data-ttu-id="ca1e7-131">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ca1e7-131">Scenario</span></span>|<span data-ttu-id="ca1e7-132">属性が計画的または戦略的な分析情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-132">A dimension whose attributes represent planning or strategic analysis information.</span></span>|  
|<span data-ttu-id="ca1e7-133">Quantitative</span><span class="sxs-lookup"><span data-stu-id="ca1e7-133">Quantitative</span></span>|<span data-ttu-id="ca1e7-134">属性が量的な情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-134">A dimension whose attributes represent quantitative information.</span></span>|  
|<span data-ttu-id="ca1e7-135">ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="ca1e7-135">Utility</span></span>|<span data-ttu-id="ca1e7-136">属性がその他の情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-136">A dimension whose attributes represent miscellaneous information.</span></span>|  
|<span data-ttu-id="ca1e7-137">Currency</span><span class="sxs-lookup"><span data-stu-id="ca1e7-137">Currency</span></span>|<span data-ttu-id="ca1e7-138">この種類のディメンションには、通貨のデータとメタデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-138">This type of dimension contains currency data and metadata.</span></span>|  
|<span data-ttu-id="ca1e7-139">Rates</span><span class="sxs-lookup"><span data-stu-id="ca1e7-139">Rates</span></span>|<span data-ttu-id="ca1e7-140">属性が通貨レート情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-140">A dimension whose attributes represent currency rate information.</span></span>|  
|<span data-ttu-id="ca1e7-141">チャネル</span><span class="sxs-lookup"><span data-stu-id="ca1e7-141">Channel</span></span>|<span data-ttu-id="ca1e7-142">属性がチャネル情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-142">A dimension whose attributes represent channel information.</span></span>|  
|<span data-ttu-id="ca1e7-143">Promotion</span><span class="sxs-lookup"><span data-stu-id="ca1e7-143">Promotion</span></span>|<span data-ttu-id="ca1e7-144">属性がマーケティング関連のプロモーション情報を表すディメンションです。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-144">A dimension whose attributes represent marketing promotion information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca1e7-145">参照</span><span class="sxs-lookup"><span data-stu-id="ca1e7-145">See Also</span></span>  
 <span data-ttu-id="ca1e7-146">[既存のテーブルを使用してディメンションを作成する](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="ca1e7-146">[Create a Dimension by Using an Existing Table](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="ca1e7-147">ディメンション &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="ca1e7-147">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
