---
title: 通貨の種類のディメンションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91123fb5fda898e90056057114295335fbd1d32c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714677"
---
# <a name="create-a-currency-type-dimension"></a><span data-ttu-id="34225-102">通貨ディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="34225-102">Create a Currency type Dimension</span></span>
  <span data-ttu-id="34225-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、通貨ディメンションとは、財務報告のために通貨の一覧を表す属性を持つディメンションです。</span><span class="sxs-lookup"><span data-stu-id="34225-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a currency type dimension is a dimension whose attributes represent a list of currencies for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="34225-104">通貨ディメンションによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のキューブに通貨換算機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="34225-104">A currency dimension lets you add currency conversion capabilities to a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="34225-105">キューブに通貨換算を追加するには、ビジネス インテリジェンス ウィザードを使用して、クライアント アプリケーションのロケールに対応する値に通貨メジャーを変換する多次元式 (MDX) スクリプト コマンドを定義します。</span><span class="sxs-lookup"><span data-stu-id="34225-105">To add currency conversion to a cube, you use the Business Intelligence Wizard define a Multidimensional Expressions (MDX) script command that converts currency measures to values that are appropriate for the locale of the client application.</span></span> <span data-ttu-id="34225-106">この MDX スクリプトを作成するには、ビジネス インテリジェンス ウィザードで次の情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34225-106">To create this MDX script, the Business Intelligence Wizard needs the following information:</span></span>  
  
-   <span data-ttu-id="34225-107">現地通貨を表す通貨ディメンション</span><span class="sxs-lookup"><span data-stu-id="34225-107">A currency dimension that represents source currencies.</span></span> <span data-ttu-id="34225-108">(このディメンションが換算元通貨ディメンションになります)。</span><span class="sxs-lookup"><span data-stu-id="34225-108">(This dimension is the source currency dimension.)</span></span>  
  
-   <span data-ttu-id="34225-109">使用する換算レートを表すメジャー グループ。</span><span class="sxs-lookup"><span data-stu-id="34225-109">A measure group that represents the exchange rates that will be used.</span></span>  
  
 <span data-ttu-id="34225-110">ビジネス インテリジェンス ウィザードは、これらの情報に基づいて、適切な換算先通貨ディメンション (換算先の通貨を表す通貨ディメンション) を指定する通貨換算プロセスをデザインします。</span><span class="sxs-lookup"><span data-stu-id="34225-110">From this information, the Business Intelligence Wizard will design a currency conversion process that identifies the appropriate destination currency dimension (the currency dimension that represents destination currencies).</span></span> <span data-ttu-id="34225-111">ビジネス インテリジェンス ウィザードでは、使用するビジネス インテリジェンス ソリューションに必要な通貨換算の数に応じて、複数の換算先通貨ディメンションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="34225-111">Depending on the number of currency conversions that your business intelligence solution requires, the Business Intelligence Wizard can define multiple destination currency dimensions.</span></span> <span data-ttu-id="34225-112">通貨換算の定義の詳細については、「[通貨換算 &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34225-112">For more information about defining currency conversions, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="34225-113">ディメンションを通貨ディメンションとして指定するには、ディメンションの `Type` プロパティを `Currency` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34225-113">To identify a dimension as a currency dimension, set the `Type` property of the dimension to `Currency`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="34225-114">[ディメンション構造]</span><span class="sxs-lookup"><span data-stu-id="34225-114">Dimension Structure</span></span>  
 <span data-ttu-id="34225-115">通貨ディメンションには、少なくとも、その通貨ディメンションのディメンション テーブル内で個々の通貨を識別するキー属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="34225-115">A currency dimension contains, at least, a key attribute identifying individual currencies in the dimension table for the currency dimension.</span></span> <span data-ttu-id="34225-116">キー属性の値は、換算元通貨ディメンションと換算先通貨ディメンションで異なります。</span><span class="sxs-lookup"><span data-stu-id="34225-116">The value of the key attribute is different in both source and destination currency dimensions:</span></span>  
  
-   <span data-ttu-id="34225-117">属性を換算元通貨ディメンションのキー属性として指定するには、属性の `Type` プロパティを `CurrencySource` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34225-117">To identify an attribute as the key attribute of a source currency dimension, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="34225-118">属性を換算先通貨ディメンションとして指定するには、属性の `Type` プロパティを `CurrencyDestination` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34225-118">To identify an attribute as the destination currency dimension, set the `Type` property of the attribute to `CurrencyDestination`.</span></span>  
  
 <span data-ttu-id="34225-119">必要に応じて次の属性を換算元通貨ディメンションと換算先通貨ディメンションに含めると、レポート作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="34225-119">For reporting purposes, both source and destination currency dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="34225-120">通貨名を表す属性</span><span class="sxs-lookup"><span data-stu-id="34225-120">A currency name attribute.</span></span>  
  
     <span data-ttu-id="34225-121">属性を通貨名属性として指定するには、属性の `Type` プロパティを `CurrencyName` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34225-121">To identify an attribute as a currency name attribute, set the `Type` property of the attribute to `CurrencyName`.</span></span>  
  
-   <span data-ttu-id="34225-122">換算元通貨を表す属性</span><span class="sxs-lookup"><span data-stu-id="34225-122">A currency source attribute.</span></span>  
  
     <span data-ttu-id="34225-123">属性を換算元通貨の属性として指定するには、属性の `Type` プロパティを `CurrencySource` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34225-123">To identify an attribute as a currency source attribute, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="34225-124">国際標準化機構 (ISO) 通貨コード</span><span class="sxs-lookup"><span data-stu-id="34225-124">A currency International Standards Organization (ISO) code.</span></span>  
  
     <span data-ttu-id="34225-125">属性を ISO 通貨コード属性として指定するには、属性の `Type` プロパティを `CurrencyIsoCode` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34225-125">To identify an attribute as a currency ISO code attribute, set the `Type` property of the attribute to `CurrencyIsoCode`.</span></span>  
  
 <span data-ttu-id="34225-126">属性の種類の詳細については、「 [属性の種類の構成](attribute-properties-configure-attribute-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34225-126">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="34225-127">ビジネス インテリジェンス ウィザードを使用した勘定科目インテリジェンスの定義</span><span class="sxs-lookup"><span data-stu-id="34225-127">Defining Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="34225-128">勘定科目ディメンションを定義し、定義したディメンションをキューブに追加したら、ビジネス インテリジェンス ウィザードを使用して、勘定科目の種類の特定とマップなどの勘定科目インテリジェンス機能をディメンションに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="34225-128">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to add account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="34225-129">詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34225-129">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34225-130">参照</span><span class="sxs-lookup"><span data-stu-id="34225-130">See Also</span></span>  
 <span data-ttu-id="34225-131">[属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="34225-131">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="34225-132">[ビジネスインテリジェンスウィザードの F1 ヘルプ](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="34225-132">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="34225-133">ディメンションの種類</span><span class="sxs-lookup"><span data-stu-id="34225-133">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
