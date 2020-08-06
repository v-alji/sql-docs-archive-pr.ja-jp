---
title: 通貨換算 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multiple currency conversions
- monetary data [SQL Server]
- currency [Analysis Services]
- converting currency
- one-to-many currency conversions
- many-to-many currency conversions [Analysis Services]
- many-to-one currency conversions [Analysis Services]
ms.assetid: e03f491c-7df8-46a0-ade9-f2e55b68db85
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4fee100dea2b3aff99516175bf688337a33592e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644247"
---
# <a name="currency-conversions-analysis-services"></a><span data-ttu-id="55b46-102">通貨換算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="55b46-102">Currency Conversions (Analysis Services)</span></span>
  <span data-ttu-id="55b46-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 多次元のみ</span><span class="sxs-lookup"><span data-stu-id="55b46-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="55b46-104">では、多次元式 (MDX) スクリプトによって実行される機能の組み合わせを使用して、複数の通貨をサポートしているキューブに通貨換算のサポートが提供されています。</span><span class="sxs-lookup"><span data-stu-id="55b46-104">uses a combination of features, guided by Multidimensional Expressions (MDX) scripts, to provide currency conversion support in cubes supporting multiple currencies.</span></span>  
  
## <a name="currency-conversion-terminology"></a><span data-ttu-id="55b46-105">通貨換算に関する用語</span><span class="sxs-lookup"><span data-stu-id="55b46-105">Currency Conversion Terminology</span></span>  
 <span data-ttu-id="55b46-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、通貨換算機能について説明するために次の用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="55b46-106">The following terminology is used in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to describe currency conversion functionality:</span></span>  
  
 <span data-ttu-id="55b46-107">ピボット通貨</span><span class="sxs-lookup"><span data-stu-id="55b46-107">Pivot currency</span></span>  
 <span data-ttu-id="55b46-108">レート メジャー グループで換算レートが入力される通貨です。</span><span class="sxs-lookup"><span data-stu-id="55b46-108">The currency against which exchange rates are entered in the rate measure group.</span></span>  
  
 <span data-ttu-id="55b46-109">現地の通貨</span><span class="sxs-lookup"><span data-stu-id="55b46-109">Local currency</span></span>  
 <span data-ttu-id="55b46-110">変換するメジャーの基となるトランザクションを格納するために使用する通貨です。</span><span class="sxs-lookup"><span data-stu-id="55b46-110">The currency used to store transactions on which measures to be converted are based.</span></span>  
  
 <span data-ttu-id="55b46-111">現地の通貨は次のどちらかで識別できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-111">The local currency can be identified by either:</span></span>  
  
-   <span data-ttu-id="55b46-112">トランザクションと共に格納されるファクト テーブル内の通貨識別子。これは、トランザクション自体がそのトランザクションに使用される通貨を識別する銀行取引アプリケーションなどで一般的です。</span><span class="sxs-lookup"><span data-stu-id="55b46-112">A currency identifier in the fact table stored with the transaction, as is commonly the case with banking applications where the transaction itself identifies the currency used for that transaction.</span></span>  
  
-   <span data-ttu-id="55b46-113">ディメンション テーブルの属性に関連付けられ、その後ファクト テーブルのトランザクションに関連付けられる通貨識別子。これは、場所や子会社などの他の識別子が、関連付けられているトランザクションに使用する通貨を識別する財務アプリケーションなどで一般的です。</span><span class="sxs-lookup"><span data-stu-id="55b46-113">A currency identifier associated with an attribute in a dimension table that is then associated with a transaction in the fact table, as is commonly the case in financial applications where a location or other identifier, such as a subsidiary, identifies the currency used for an associated transaction.</span></span>  
  
 <span data-ttu-id="55b46-114">レポートの通貨</span><span class="sxs-lookup"><span data-stu-id="55b46-114">Reporting currency</span></span>  
 <span data-ttu-id="55b46-115">ピボット通貨からトランザクションが変換される通貨です。</span><span class="sxs-lookup"><span data-stu-id="55b46-115">The currency to which transactions are converted from the pivot currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55b46-116">多対一の通貨換算では、ピボット通貨とレポートの通貨は同じになります。</span><span class="sxs-lookup"><span data-stu-id="55b46-116">For many-to-one currency conversions, the pivot currency and reporting currency are the same.</span></span>  
  
 <span data-ttu-id="55b46-117">通貨ディメンション</span><span class="sxs-lookup"><span data-stu-id="55b46-117">Currency dimension</span></span>  
 <span data-ttu-id="55b46-118">次の設定で定義されているデータベース ディメンションです。</span><span class="sxs-lookup"><span data-stu-id="55b46-118">A database dimension defined with the following settings:</span></span>  
  
-   <span data-ttu-id="55b46-119">ディメンションの `Type` プロパティが Currency に設定されている。</span><span class="sxs-lookup"><span data-stu-id="55b46-119">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="55b46-120">ディメンションの 1 つの属性の `Type` プロパティが CurrencyName に設定されている。</span><span class="sxs-lookup"><span data-stu-id="55b46-120">The `Type` property of one attribute for the dimension is set to CurrencyName.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="55b46-121">この属性値を、通貨識別子を含むすべての列で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-121">The values of this attribute must be used in all columns that should contain a currency identifier.</span></span>  
  
 <span data-ttu-id="55b46-122">レート メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="55b46-122">Rate measure group</span></span>  
 <span data-ttu-id="55b46-123">次の設定を使用して定義されている、キューブ内のメジャー グループです。</span><span class="sxs-lookup"><span data-stu-id="55b46-123">A measure group in a cube, defined with the following settings:</span></span>  
  
-   <span data-ttu-id="55b46-124">通貨ディメンションとレート メジャー グループ間に標準のディメンション リレーションシップが存在する。</span><span class="sxs-lookup"><span data-stu-id="55b46-124">A regular dimension relationship exists between a currency dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="55b46-125">時間ディメンションとレート メジャー グループ間に標準のディメンション リレーションシップが存在する。</span><span class="sxs-lookup"><span data-stu-id="55b46-125">A regular dimension relationship exists between a time dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="55b46-126">必要に応じて、`Type` プロパティが ExchangeRate に設定される。</span><span class="sxs-lookup"><span data-stu-id="55b46-126">Optionally, the `Type` property is set to ExchangeRate.</span></span> <span data-ttu-id="55b46-127">ビジネス インテリジェンス ウィザードでは通貨ディメンションおよび時間ディメンションとのリレーションシップを使用して、考えられるレート メジャー グループが識別されますが、`Type` プロパティを ExchangeRate に設定すると、クライアント アプリケーションでより簡単にレート メジャー グループを識別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="55b46-127">While the Business Intelligence Wizard uses the relationships with the currency and time dimensions to identify likely rate measure groups, setting the `Type` property to ExchangeRate allows client applications to more easily identify rate measure groups.</span></span>  
  
-   <span data-ttu-id="55b46-128">レート メジャー グループに含まれている換算レートを表す 1 つまたは複数のメジャー。</span><span class="sxs-lookup"><span data-stu-id="55b46-128">One or more measures, representing the exchange rates contained by the rate measure group.</span></span>  
  
 <span data-ttu-id="55b46-129">レポートの通貨ディメンション</span><span class="sxs-lookup"><span data-stu-id="55b46-129">Reporting currency dimension</span></span>  
 <span data-ttu-id="55b46-130">通貨換算の定義後にビジネス インテリジェンス ウィザードによって定義されるディメンションで、その通貨換算用のレポートの通貨を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="55b46-130">The dimension, defined by the Business Intelligence Wizard after a currency conversion is defined, that contains the reporting currencies for that currency conversion.</span></span> <span data-ttu-id="55b46-131">レポートの通貨ディメンションは、通貨ディメンションのディメンション メイン テーブルから名前付きクエリに基づいて作成され、レート メジャー グループに関連付けられている通貨ディメンションの基になっているデータ ソース ビューで定義されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-131">The reporting currency dimension is based on a named query, defined in the data source view on which the currency dimension associated with the rate measure group is based, from the dimension main table of the currency dimension.</span></span> <span data-ttu-id="55b46-132">ディメンションは、次の設定を使用して定義されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-132">The dimension is defined with the following settings:</span></span>  
  
-   <span data-ttu-id="55b46-133">ディメンションの `Type` プロパティが Currency に設定されている。</span><span class="sxs-lookup"><span data-stu-id="55b46-133">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="55b46-134">ディメンションのキー属性の `Type` プロパティが CurrencyName に設定されている。</span><span class="sxs-lookup"><span data-stu-id="55b46-134">The `Type` property of the key attribute for the dimension is set to CurrencyName.</span></span>  
  
-   <span data-ttu-id="55b46-135">ディメンション内の 1 つの属性の `Type` プロパティは CurrencyDestination に設定されており、属性にバインドされている列には、通貨換算用のレポートの通貨を表す通貨識別子が含まれている。</span><span class="sxs-lookup"><span data-stu-id="55b46-135">The `Type` property of one attribute within the dimension is set to CurrencyDestination, and the column bound to the attribute contains the currency identifiers that represent the reporting currencies for the currency conversion.</span></span>  
  
## <a name="defining-currency-conversions"></a><span data-ttu-id="55b46-136">通貨換算の定義</span><span class="sxs-lookup"><span data-stu-id="55b46-136">Defining Currency Conversions</span></span>  
 <span data-ttu-id="55b46-137">ビジネス インテリジェンス ウィザードを使用すると、キューブの通貨換算機能を定義できます。また、MDX スクリプトを使用して通貨換算を手動で定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="55b46-137">You can use the Business Intelligence Wizard to define currency conversion functionality for a cube, or you can manually define currency conversions using MDX scripts.</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="55b46-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="55b46-138">Prerequisites</span></span>  
 <span data-ttu-id="55b46-139">ビジネス インテリジェンス ウィザードを使用してキューブに通貨換算を定義するには、少なくとも 1 つの通貨ディメンション、少なくとも 1 つの時間ディメンション、および少なくとも 1 つのレート メジャー グループを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-139">Before you can define a currency conversion in a cube using the Business Intelligence Wizard, you must first define at least one currency dimension, at least one time dimension, and at least one rate measure group.</span></span> <span data-ttu-id="55b46-140">ビジネス インテリジェンス ウィザードでは、レポートの通貨ディメンションおよび MDX スクリプトの作成に使用するデータとメタデータをこれらのオブジェクトから取得し、通貨換算機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-140">From these objects, the Business Intelligence Wizard can retrieve the data and metadata used to construct the reporting currency dimension and MDX script needed to provide currency conversion functionality.</span></span>  
  
### <a name="decisions"></a><span data-ttu-id="55b46-141">決定事項</span><span class="sxs-lookup"><span data-stu-id="55b46-141">Decisions</span></span>  
 <span data-ttu-id="55b46-142">ビジネス インテリジェンス ウィザードでレポートの通貨ディメンションと MDX スクリプトを作成し、通貨換算機能を提供するには、次の項目を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-142">You need to make the following decisions before the Business Intelligence Wizard can construct the reporting currency dimension and MDX script needed to provide currency conversion functionality:</span></span>  
  
-   <span data-ttu-id="55b46-143">換算レートの方向</span><span class="sxs-lookup"><span data-stu-id="55b46-143">Exchange rate direction</span></span>  
  
-   <span data-ttu-id="55b46-144">換算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="55b46-144">Converted members</span></span>  
  
-   <span data-ttu-id="55b46-145">換算の種類</span><span class="sxs-lookup"><span data-stu-id="55b46-145">Conversion type</span></span>  
  
-   <span data-ttu-id="55b46-146">現地の通貨</span><span class="sxs-lookup"><span data-stu-id="55b46-146">Local currencies</span></span>  
  
-   <span data-ttu-id="55b46-147">[レポート用の通貨]</span><span class="sxs-lookup"><span data-stu-id="55b46-147">Reporting currencies</span></span>  
  
### <a name="exchange-rate-directions"></a><span data-ttu-id="55b46-148">換算レートの方向</span><span class="sxs-lookup"><span data-stu-id="55b46-148">Exchange Rate Directions</span></span>  
 <span data-ttu-id="55b46-149">レート メジャー グループは、現地の通貨とピボット通貨 (通常は会社で使用する通貨と呼ばれます) 間の換算レートを表すメジャーを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="55b46-149">The rate measure group contains measures representing exchange rates between local currencies and the pivot currency (commonly referred to as the corporate currency).</span></span> <span data-ttu-id="55b46-150">ビジネス インテリジェント ウィザードで生成した MDX スクリプトによって換算されるメジャーに対する操作は、換算レートの方向と換算の種類の組み合わせによって決まります。</span><span class="sxs-lookup"><span data-stu-id="55b46-150">The combination of exchange rate direction and conversion type determines the operation performed on measures to be converted by the MDX script generated using the Business Intelligence Wizard.</span></span> <span data-ttu-id="55b46-151">次の表では、換算レートの方向と換算の種類に応じて実行される操作について説明します。これらの操作は、ビジネス インテリジェンス ウィザードで使用可能な換算レートの方向オプションと換算の方向に基づいています。</span><span class="sxs-lookup"><span data-stu-id="55b46-151">The following table describes the operations performed depending on the exchange rate direction and conversion type, based on the exchange rate direction options and conversion directions available in the Business Intelligence Wizard.</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="55b46-152">換算レートの方向</span><span class="sxs-lookup"><span data-stu-id="55b46-152">Exchange rate direction</span></span>|<span data-ttu-id="55b46-153">**多対一**</span><span class="sxs-lookup"><span data-stu-id="55b46-153">**Many-to-one**</span></span>|<span data-ttu-id="55b46-154">**[一対多]**</span><span class="sxs-lookup"><span data-stu-id="55b46-154">**One-to-many**</span></span>|<span data-ttu-id="55b46-155">**多対多**</span><span class="sxs-lookup"><span data-stu-id="55b46-155">**Many-to-many**</span></span>|  
|<span data-ttu-id="55b46-156">**n 個のピボット通貨対 1 つのサンプル通貨**</span><span class="sxs-lookup"><span data-stu-id="55b46-156">**n pivot currency to 1 sample currency**</span></span>|<span data-ttu-id="55b46-157">メジャーをピボット通貨に換算するには、換算するメジャーを現地の通貨の換算レート メジャーと掛け合わせます。</span><span class="sxs-lookup"><span data-stu-id="55b46-157">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="55b46-158">メジャーをレポートの通貨に換算するには、換算するメジャーをレポートの通貨の換算レート メジャーで割ります。</span><span class="sxs-lookup"><span data-stu-id="55b46-158">Divide the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="55b46-159">メジャーをピボット通貨に換算するには、換算するメジャーを現地の通貨の換算レート メジャーと掛け合わせ、メジャーをレポートの通貨に換算するには、換算するメジャーをレポートの通貨の換算レート メジャーで割ります。</span><span class="sxs-lookup"><span data-stu-id="55b46-159">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then divide the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
|<span data-ttu-id="55b46-160">**n 個のサンプル通貨対 1 つのピボット通貨**</span><span class="sxs-lookup"><span data-stu-id="55b46-160">**n sample currency to 1 pivot currency**</span></span>|<span data-ttu-id="55b46-161">メジャーをピボット通貨に換算するには、換算するメジャーを現地の通貨の換算レート メジャーで割ります。</span><span class="sxs-lookup"><span data-stu-id="55b46-161">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="55b46-162">メジャーをレポートの通貨に換算するには、換算するメジャーをレポートの通貨の換算レート メジャーと掛け合わせます。</span><span class="sxs-lookup"><span data-stu-id="55b46-162">Multiply the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="55b46-163">メジャーをピボット通貨に換算するには、換算するメジャーを現地の通貨の換算レート メジャーで割り、メジャーをレポートの通貨に換算するには、換算するメジャーをレポートの通貨の換算レート メジャーと掛け合わせます。</span><span class="sxs-lookup"><span data-stu-id="55b46-163">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then multiply the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
  
 <span data-ttu-id="55b46-164">換算レートの方向は、ビジネス インテリジェンス ウィザードの **[通貨換算オプションの設定]** ページで選択します。</span><span class="sxs-lookup"><span data-stu-id="55b46-164">You choose the exchange rate direction on the **Set currency conversion options** page of the Business Intelligence Wizard.</span></span> <span data-ttu-id="55b46-165">換算方向の設定の詳細については、「[通貨換算オプションの設定 &#40;ビジネス インテリジェンス ウィザード&#41;](set-currency-conversion-options-business-intelligence-wizard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="55b46-165">For more information about setting conversion direction, see [Set Currency Conversion Options &#40;Business Intelligence Wizard&#41;](set-currency-conversion-options-business-intelligence-wizard.md).</span></span>  
  
### <a name="converted-members"></a><span data-ttu-id="55b46-166">換算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="55b46-166">Converted Members</span></span>  
 <span data-ttu-id="55b46-167">ビジネス インテリジェンス ウィザードを使用すると、値の換算にレート メジャー グループのどのメジャーを使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-167">You can use the Business Intelligence Wizard to specify which measures from the rate measure group are used to convert values for:</span></span>  
  
-   <span data-ttu-id="55b46-168">他のメジャー グループのメジャー</span><span class="sxs-lookup"><span data-stu-id="55b46-168">Measures in other measure groups.</span></span>  
  
-   <span data-ttu-id="55b46-169">データベース ディメンションの勘定科目属性用の属性階層のメンバー</span><span class="sxs-lookup"><span data-stu-id="55b46-169">Members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
-   <span data-ttu-id="55b46-170">データベース ディメンションの勘定科目属性用の属性階層のメンバーが使用する勘定科目の種類</span><span class="sxs-lookup"><span data-stu-id="55b46-170">Account types, used by members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
 <span data-ttu-id="55b46-171">ビジネス インテリジェンス ウィザードでは、ウィザードが生成した MDX スクリプト内でこの情報を使用して、通貨換算の計算の範囲を決定します。</span><span class="sxs-lookup"><span data-stu-id="55b46-171">The Business Intelligence Wizard uses this information within the MDX script generated by the wizard to determine the scope of the currency conversion calculation.</span></span> <span data-ttu-id="55b46-172">通貨換算のメンバーを指定する方法の詳細については、「[メンバーの選択 &#40;ビジネス インテリジェンス ウィザード&#41;](select-members-business-intelligence-wizard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="55b46-172">For more information about specifying members for currency conversion, see [Select Members &#40;Business Intelligence Wizard&#41;](select-members-business-intelligence-wizard.md).</span></span>  
  
### <a name="conversion-types"></a><span data-ttu-id="55b46-173">換算の種類</span><span class="sxs-lookup"><span data-stu-id="55b46-173">Conversion Types</span></span>  
 <span data-ttu-id="55b46-174">ビジネス インテリジェンス ウィザードでは、次の 3 種類の通貨換算がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="55b46-174">The Business Intelligence Wizard supports three different types of currency conversion:</span></span>  
  
-   <span data-ttu-id="55b46-175">**[一対多]**</span><span class="sxs-lookup"><span data-stu-id="55b46-175">**One-to-many**</span></span>  
  
     <span data-ttu-id="55b46-176">トランザクションはピボット通貨のファクト テーブルに格納され、1 つまたは複数の他のレポートの通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-176">Transactions are stored in the fact table in the pivot currency, and then converted to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="55b46-177">たとえば、ピボット通貨を米国ドル (USD) に設定し、トランザクションを USD でファクト テーブルに格納するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-177">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="55b46-178">この種類の換算では、これらのトランザクションが、ピボット通貨から指定のレポートの通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-178">This conversion type converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="55b46-179">その結果、トランザクションは、指定のピボット通貨で格納でき、ピボット通貨、または通貨換算用に定義されているレポートの通貨ディメンションに指定されているレポートの通貨のいずれかで表示できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-179">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any of the reporting currencies specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="55b46-180">**多対一**</span><span class="sxs-lookup"><span data-stu-id="55b46-180">**Many-to-one**</span></span>  
  
     <span data-ttu-id="55b46-181">トランザクションは、現地の通貨でファクト テーブルに格納され、ピボット通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-181">Transactions are stored in the fact table in local currencies, and then converted into the pivot currency.</span></span> <span data-ttu-id="55b46-182">ピボット通貨は、レポートの通貨ディメンションに指定されている唯一のレポートの通貨として機能します。</span><span class="sxs-lookup"><span data-stu-id="55b46-182">The pivot currency serves as the only specified reporting currency in the reporting currency dimension.</span></span>  
  
     <span data-ttu-id="55b46-183">たとえば、ピボット通貨を米国ドル (USD) に設定し、トランザクションをユーロ (EUR)、豪ドル (AUD)、およびメキシコ ペソ (MXN) でファクト テーブルに格納するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-183">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="55b46-184">この種類の換算では、これらのトランザクションは、指定されている現地の通貨から、ピボット通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-184">This conversion type converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="55b46-185">その結果、トランザクションは、指定されている現地の通貨で格納でき、通貨換算用に定義されているレポートの通貨ディメンションに指定されている、ピボット通貨で表示できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-185">The result is that transactions can be stored in the specified local currencies and viewed in the pivot currency, which is specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="55b46-186">**多対多**</span><span class="sxs-lookup"><span data-stu-id="55b46-186">**Many-to-many**</span></span>  
  
     <span data-ttu-id="55b46-187">トランザクションは現地の通貨でファクト テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-187">Transactions are stored in the fact table in local currencies.</span></span> <span data-ttu-id="55b46-188">このようなトランザクションは、通貨換算機能によって、ピボット通貨に換算され、その後 1 つまたは複数の他のレポートの通貨に換算されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-188">The currency conversion functionality converts such transactions into the pivot currency, and then to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="55b46-189">たとえば、ピボット通貨を米国ドル (USD) に設定し、トランザクションをユーロ (EUR)、豪ドル (AUD)、およびメキシコ ペソ (MXN) でファクト テーブルに格納するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-189">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="55b46-190">この種類の換算では、これらのトランザクションは、指定されている現地の通貨から、ピボット通貨に換算され、換算されたトランザクションは、ピボット通貨から、指定されているレポートの通貨に再び換算されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-190">This conversion type converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="55b46-191">その結果、トランザクションは、指定されている現地の通貨で格納でき、指定のピボット通貨、または通貨換算用に定義されているレポートの通貨ディメンションに指定されているレポートの通貨のいずれかで表示できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-191">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any of the reporting currencies that are specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
 <span data-ttu-id="55b46-192">変換の種類を指定すると、ビジネス インテリジェンス ウィザードでは、レポートの通貨ディメンションの名前付きクエリおよびディメンション構造に加えて、通貨換算用に定義する MDX スクリプトの構造を定義できるようになります。</span><span class="sxs-lookup"><span data-stu-id="55b46-192">Specifying the conversion type allows the Business Intelligence Wizard to define the named query and dimension structure of the reporting currency dimension, as well as the structure of the MDX script defined for the currency conversion.</span></span>  
  
### <a name="local-currencies"></a><span data-ttu-id="55b46-193">現地の通貨</span><span class="sxs-lookup"><span data-stu-id="55b46-193">Local Currencies</span></span>  
 <span data-ttu-id="55b46-194">通貨換算に多対多または多対一の種類の換算を選択する場合は、ビジネス インテリジェンス ウィザードで生成した MDX スクリプトが通貨換算の計算を実行するときの現地の通貨を識別する方法を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-194">If you choose a many-to-many or many-to-one conversion type for your currency conversion, you need to specify how to identify the local currencies from which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="55b46-195">ファクト テーブル内のトランザクションの現地の通貨は、次の 2 種類の方法のどちらかで識別できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-195">The local currency for a transaction in a fact table can be identified in one of two ways:</span></span>  
  
-   <span data-ttu-id="55b46-196">メジャー グループには、通貨ディメンションに対する標準のディメンション リレーションシップが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55b46-196">The measure group contains a regular dimension relationship to the currency dimension.</span></span> <span data-ttu-id="55b46-197">たとえば、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースでは、"インターネット販売" メジャー グループに "通貨" ディメンションに対する通常のディメンション リレーションシップが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55b46-197">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="55b46-198">このメジャー グループのファクト テーブルは、このディメンションのディメンション テーブル内の通貨識別子を参照する外部キー列を格納します。</span><span class="sxs-lookup"><span data-stu-id="55b46-198">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span> <span data-ttu-id="55b46-199">この場合は、メジャー グループによって参照されている通貨ディメンションから属性を選択し、そのメジャー グループのファクト テーブル内のトランザクションの現地の通貨を識別できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-199">In this case, you can select the attribute from the currency dimension that is referenced by the measure group to identify the local currency for transactions in the fact table for that measure group.</span></span> <span data-ttu-id="55b46-200">この状況は、トランザクション自体がトランザクションで使用される通貨を判断する銀行取引アプリケーションなどで最もよく発生します。</span><span class="sxs-lookup"><span data-stu-id="55b46-200">This situation most often occurs in banking applications, where the transaction itself determines the currency used within the transaction.</span></span>  
  
-   <span data-ttu-id="55b46-201">メジャー グループには、通貨ディメンションを直接参照する別のディメンションを介して、通貨ディメンションに対する参照ディメンション リレーションシップが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55b46-201">The measure group contains a referenced dimension relationship to the currency dimension, through another dimension that directly references the currency dimension.</span></span> <span data-ttu-id="55b46-202">たとえば、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースにおいて、[Financial Reporting] メジャー グループは、組織ディメンションを介して、通貨ディメンションに対する参照ディメンション リレーションシップを持ちます。</span><span class="sxs-lookup"><span data-stu-id="55b46-202">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="55b46-203">そのメジャー グループのファクト テーブルには外部キー列が含まれており、この列は "組織" ディメンションのディメンション テーブル内のメンバーを参照します。</span><span class="sxs-lookup"><span data-stu-id="55b46-203">The fact table for that measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="55b46-204">さらに、組織ディメンションのディメンション テーブルには、通貨ディメンションのディメンション テーブル内の通貨識別子を参照する外部キー列があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-204">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span> <span data-ttu-id="55b46-205">この状況は、トランザクションの場所または支社によってトランザクションの通貨が決定される財務報告アプリケーションなどで最もよく発生します。</span><span class="sxs-lookup"><span data-stu-id="55b46-205">This situation most often occurs in financial reporting applications, where the location or subsidiary for a transaction determines the currency for the transaction.</span></span> <span data-ttu-id="55b46-206">この場合は、通貨ディメンションを参照する属性をビジネス エンティティ用ディメンションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-206">In this case, you can select the attribute that references the currency dimension from the dimension for the business entity.</span></span>  
  
### <a name="reporting-currencies"></a><span data-ttu-id="55b46-207">[レポート用の通貨]</span><span class="sxs-lookup"><span data-stu-id="55b46-207">Reporting Currencies</span></span>  
 <span data-ttu-id="55b46-208">通貨変換に多対多または一対多の種類の換算を選択する場合は、ビジネス インテリジェンス ウィザードが生成した MDX スクリプトが通貨換算の計算を実行するときのレポートの通貨を識別する方法を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-208">If you choose a many-to-many or one-to-many conversion type for your currency conversion, you need to specify the reporting currencies for which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="55b46-209">レート メジャー グループに関連する通貨ディメンションのメンバーをすべて指定することも、ディメンションから個別のメンバーを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="55b46-209">You can either specify all the members of the currency dimension related to the rate measure group, or select individual members from the dimension.</span></span>  
  
 <span data-ttu-id="55b46-210">ビジネス インテリジェンス ウィザードでは、選択されているレポートの通貨を使用して通貨ディメンション用のディメンション テーブルから作成された名前付きクエリに基づいて、レポートの通貨ディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="55b46-210">The Business Intelligence Wizard creates a reporting currency dimension, based on a named query constructed from the dimension table for the currency dimension using the selected reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55b46-211">一対多の種類の換算を選択した場合は、レポートの通貨ディメンションも作成されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-211">If you select the one-to-many conversion type, a reporting currency dimension is also created.</span></span> <span data-ttu-id="55b46-212">ディメンションにはピボット通貨を表す 1 つのみのメンバーが含まれます。ピボット通貨は、一対多の通貨換算用のレポートの通貨としても使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="55b46-212">The dimension contains only one member representing the pivot currency, because the pivot currency is also used as the reporting currency for a one-to-many currency conversion.</span></span>  
  
 <span data-ttu-id="55b46-213">キューブに定義されている各通貨換算には、個別のレポートの通貨ディメンションが定義されます。</span><span class="sxs-lookup"><span data-stu-id="55b46-213">A separate reporting currency dimension is defined for each currency conversion defined in a cube.</span></span> <span data-ttu-id="55b46-214">レポートの通貨ディメンションの名前は作成後に変更できますが、変更する場合は、その通貨換算用に生成する MDX スクリプトも更新して、レポートの通貨ディメンションを参照する際にスクリプト コマンドが正しい名前を使用するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b46-214">You can change the name of the reporting currency dimensions after creation, but if you do so you must also update the MDX script generated for that currency conversion to ensure that the correct name is used by the script command when referencing the reporting currency dimension.</span></span>  
  
## <a name="defining-multiple-currency-conversions"></a><span data-ttu-id="55b46-215">複数の通貨換算の定義</span><span class="sxs-lookup"><span data-stu-id="55b46-215">Defining Multiple Currency Conversions</span></span>  
 <span data-ttu-id="55b46-216">ビジネス インテリジェンス ウィザードを使用すると、ビジネス インテリジェンス ソリューションに必要な数の通貨換算をいくつでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-216">Using the Business Intelligence Wizard, you can define as many currency conversions as needed for your business intelligence solution.</span></span> <span data-ttu-id="55b46-217">既存の通貨換算を上書きすることも、新しい通貨換算をキューブ用の MDX スクリプトに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="55b46-217">You can either overwrite an existing currency conversion or append a new currency conversion to the MDX script for a cube.</span></span> <span data-ttu-id="55b46-218">1 つのキューブに定義されている複数の通貨換算は、国際的な報告に関する複数の個別の換算要件をサポートしている財務報告アプリケーションなどの、複雑な報告要件を持つビジネス インテリジェンス アプリケーションに柔軟性をもたらします。</span><span class="sxs-lookup"><span data-stu-id="55b46-218">Multiple currency conversions defined in a single cube provide flexibility in business intelligence applications that have complex reporting requirements, such as financial reporting applications that support multiple, separate conversion requirements for international reporting.</span></span>  
  
### <a name="identifying-currency-conversions"></a><span data-ttu-id="55b46-219">通貨換算の識別</span><span class="sxs-lookup"><span data-stu-id="55b46-219">Identifying Currency Conversions</span></span>  
 <span data-ttu-id="55b46-220">ビジネス インテリジェンス ウィザードでは、通貨換算用のスクリプト コマンドを次のコメントに含めることで、各通貨換算を識別します。</span><span class="sxs-lookup"><span data-stu-id="55b46-220">The Business Intelligence Wizard identifies each currency conversion by framing the script commands for the currency conversion in the following comments:</span></span>  
  
 `//<Currency conversion>`  
  
 `...`  
  
 `[MDX statements for the currency conversion]`  
  
 `...`  
  
 `//</Currency conversion>`  
  
 <span data-ttu-id="55b46-221">これらのコメントを変更または削除すると、ビジネス インテリジェンス ウィザードでは通貨換算を検出できなくなるので、これらのコメントは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="55b46-221">If you change or remove these comments, the Business Intelligence Wizard is unable to detect the currency conversion, so you should not change these comments.</span></span>  
  
 <span data-ttu-id="55b46-222">また、ウィザードではこれらのコメントに、作成日時、ユーザー、換算の種類などのメタデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="55b46-222">The wizard also stores metadata in comments within these comments, including the creation date and time, the user, and the conversion type.</span></span> <span data-ttu-id="55b46-223">これらのコメントも、変更しないでください。ビジネス インテリジェンス ウィザードでは既存の通貨換算を表示する際に、このメタデータを使用するためです。</span><span class="sxs-lookup"><span data-stu-id="55b46-223">These comments should also not be changed because the Business Intelligence Wizard uses this metadata when displaying existing currency conversions.</span></span>  
  
 <span data-ttu-id="55b46-224">通貨換算に含まれているスクリプト コマンドは、必要に応じて変更できます。</span><span class="sxs-lookup"><span data-stu-id="55b46-224">You can change the script commands contained in a currency conversion as needed.</span></span> <span data-ttu-id="55b46-225">ただし、通貨換算を上書きした場合、変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="55b46-225">If you overwrite the currency conversion, however, your changes will be lost.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b46-226">参照</span><span class="sxs-lookup"><span data-stu-id="55b46-226">See Also</span></span>  
 [<span data-ttu-id="55b46-227">Analysis Services 多次元のグローバル化のシナリオ</span><span class="sxs-lookup"><span data-stu-id="55b46-227">Globalization scenarios for Analysis Services Multiidimensional</span></span>](globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
  
