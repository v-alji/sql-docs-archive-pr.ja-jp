---
title: データ ドリブン サブスクリプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b59d5cc447191bef526d4cf4399a841d68932886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634826"
---
# <a name="data-driven-subscriptions"></a><span data-ttu-id="5d882-102">データ ドリブン サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="5d882-102">Data-Driven Subscriptions</span></span>
  <span data-ttu-id="5d882-103">データ ドリブン サブスクリプションでは、実行時に外部データ ソースから取得した動的サブスクリプション データを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d882-103">A data-driven subscription provides a way to use dynamic subscription data that is retrieved from an external data source at run time.</span></span> <span data-ttu-id="5d882-104">サブスクリプションの定義時に指定した静的テキストや既定値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d882-104">A data-driven subscription can also use static text and default values that you specify when the subscription is defined.</span></span> <span data-ttu-id="5d882-105">データ ドリブン サブスクリプションを使用すると、次のようなことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="5d882-105">You can use data-driven subscriptions to do the following:</span></span>  
  
-   <span data-ttu-id="5d882-106">サブスクライバーの変動が頻繁に生じても、それに対応してレポートを配信する。</span><span class="sxs-lookup"><span data-stu-id="5d882-106">Distribute a report to a fluctuating list of subscribers.</span></span> <span data-ttu-id="5d882-107">たとえば、データ ドリブン サブスクリプションを使用して、サブスクライバーが毎月変わる大きな組織全体にレポートを配信したり、他の条件を使用して既存の一連のユーザーからグループのメンバーシップを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="5d882-107">For example, you can use data-driven subscriptions to distribute a report throughout a large organization where subscribers vary from one month to the next, or use other criteria that determines group membership from an existing set of users.</span></span>  
  
-   <span data-ttu-id="5d882-108">実行時に取得したレポート パラメーター値に基づいてレポート出力をフィルター選択する。</span><span class="sxs-lookup"><span data-stu-id="5d882-108">Filter the report output using report parameter values that are retrieved at run time.</span></span>  
  
-   <span data-ttu-id="5d882-109">レポートを配信するたびにレポートの出力形式や配信オプションを変化させる。</span><span class="sxs-lookup"><span data-stu-id="5d882-109">Vary report output formats and delivery options for each report delivery.</span></span>  
  
 <span data-ttu-id="5d882-110">データ ドリブン サブスクリプションは複数の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="5d882-110">A data-driven subscription is composed of multiple parts.</span></span> <span data-ttu-id="5d882-111">データ ドリブン サブスクリプションの固定的な要素は、サブスクリプションの作成時に定義され、次のような要素があります。</span><span class="sxs-lookup"><span data-stu-id="5d882-111">The fixed aspects of a data-driven subscription are defined when you create the subscription, and these include the following:</span></span>  
  
-   <span data-ttu-id="5d882-112">サブスクリプションを定義するレポート (サブスクリプションは常に単一のレポートと関連付けられます)。</span><span class="sxs-lookup"><span data-stu-id="5d882-112">The report for which the subscription is defined (a subscription is always associated with a single report).</span></span>  
  
-   <span data-ttu-id="5d882-113">レポートの配信に使用する配信拡張機能。</span><span class="sxs-lookup"><span data-stu-id="5d882-113">The delivery extension used to distribute the report.</span></span> <span data-ttu-id="5d882-114">レポート サーバーの電子メール配信、ファイル共有配信、キャッシュの事前読み込みに使用する NULL 配信プロバイダー、カスタム配信拡張機能などを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5d882-114">You can specify report server e-mail delivery, file share delivery, the null delivery provider used for preloading the cache, or a custom delivery extension.</span></span> <span data-ttu-id="5d882-115">単一のサブスクリプションに対して複数の配信拡張機能を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5d882-115">You cannot specify multiple delivery extensions within a single subscription.</span></span>  
  
-   <span data-ttu-id="5d882-116">サブスクライバー データ ソース。</span><span class="sxs-lookup"><span data-stu-id="5d882-116">The subscriber data source.</span></span> <span data-ttu-id="5d882-117">サブスクリプションを定義するとき、サブスクライバー データが格納されているデータ ソースへの接続文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d882-117">You must specify a connection string to the data source that contains subscriber data when you define the subscription.</span></span> <span data-ttu-id="5d882-118">サブスクライバー データ ソースを実行時に動的に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5d882-118">The subscriber data source cannot be specified dynamically at run time.</span></span>  
  
-   <span data-ttu-id="5d882-119">サブスクライバー データの選択に使用するクエリ。サブスクリプションの定義時に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d882-119">The query that you use to select subscriber data must be specified when you define the subscription.</span></span> <span data-ttu-id="5d882-120">クエリを実行時に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="5d882-120">You cannot change the query at run time.</span></span>  
  
 <span data-ttu-id="5d882-121">データ ドリブン サブスクリプションに使用される動的な値は、サブスクリプションの処理時に取得されます。</span><span class="sxs-lookup"><span data-stu-id="5d882-121">Dynamic values used in a data-driven subscription are obtained when the subscription is processed.</span></span> <span data-ttu-id="5d882-122">サブスクリプションで使用される変数データには、サブスクライバー名、電子メール アドレス、使用するレポート出力形式のほか、各種レポート パラメーターの値があります。</span><span class="sxs-lookup"><span data-stu-id="5d882-122">Examples of variable data that you might use in a subscription include the subscriber name, e-mail address, preferred report output format, or any value that is valid for a report parameter.</span></span> <span data-ttu-id="5d882-123">データ ドリブン サブスクリプションで動的な値を使用するには、クエリから返されるフィールドを、特定の配信オプションおよびレポート パラメーターに対応付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d882-123">To use dynamic values in a data-driven subscription, you define a mapping between the fields that are returned in the query to specific delivery options and to report parameters.</span></span> <span data-ttu-id="5d882-124">変数データは、サブスクリプションを処理するごとに、サブスクライバー データ ソースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="5d882-124">Variable data is retrieved from a subscriber data source each time the subscription is processed.</span></span>  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a><span data-ttu-id="5d882-125">データ ドリブン サブスクリプションを使用する場合の要件</span><span class="sxs-lookup"><span data-stu-id="5d882-125">Requirements for using Data-Driven Subscriptions</span></span>  
 <span data-ttu-id="5d882-126">データ ドリブン サブスクリプション機能は、すべてのエディションで利用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5d882-126">Data-driven subscription functionality is not available in all editions.</span></span> <span data-ttu-id="5d882-127">また、データ ソースの種類によっては、実行時にサブスクリプション データを取得できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5d882-127">There are also limitations on the kinds of data sources that you can use to retrieve subscription data at run time.</span></span> <span data-ttu-id="5d882-128">詳細な要件については、以下の情報を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="5d882-128">The following list provides more information about the requirements:</span></span>  
  
-   <span data-ttu-id="5d882-129">データドリブンサブスクリプション機能をサポートするのエディションの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="5d882-129">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Data-driven subscription functionality, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="5d882-130">サブスクリプション データについては、スキーマ情報をレポート サーバーに提供できるデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="5d882-130">For subscription data, choose a data source that can provide schema information to the report server.</span></span> <span data-ttu-id="5d882-131">サポートされているデータ ソースの種類としては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データ、Oracle、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ データ、ODBC データ ソース、OLE DB データ ソースなどがあります。</span><span class="sxs-lookup"><span data-stu-id="5d882-131">Examples of supported data source types include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational data, Oracle, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package data, ODBC data sources, and OLE DB data sources.</span></span> <span data-ttu-id="5d882-132">サブスクライバー データ ソース要件の詳細については、「 [サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d882-132">For more information about subscriber data source requirements, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
## <a name="working-with-data-driven-subscriptions"></a><span data-ttu-id="5d882-133">データ ドリブン サブスクリプションの処理</span><span class="sxs-lookup"><span data-stu-id="5d882-133">Working with Data-Driven Subscriptions</span></span>  
 <span data-ttu-id="5d882-134">以下のトピックでは、データ ドリブン サブスクリプションの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d882-134">The following topics provide more information about data-driven subscriptions.</span></span>  
  
|<span data-ttu-id="5d882-135">トピック</span><span class="sxs-lookup"><span data-stu-id="5d882-135">Topics</span></span>|<span data-ttu-id="5d882-136">説明</span><span class="sxs-lookup"><span data-stu-id="5d882-136">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d882-137">データ ドリブン サブスクリプションを作成、変更、および削除する</span><span class="sxs-lookup"><span data-stu-id="5d882-137">Create, Modify, and Delete a Data-Driven Subscription</span></span>](data-driven-subscriptions.md)|<span data-ttu-id="5d882-138">データ ドリブン サブスクリプションの作成、変更、および削除方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d882-138">Explains how to create, modify, or delete a data-driven subscription.</span></span>|  
|[<span data-ttu-id="5d882-139">サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;</span><span class="sxs-lookup"><span data-stu-id="5d882-139">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|<span data-ttu-id="5d882-140">データ ドリブン サブスクリプションに使用できるデータ ソースに関する情報を記載しています。</span><span class="sxs-lookup"><span data-stu-id="5d882-140">Provides information about the data sources that you can use for a data-driven subscription.</span></span>|  
|[<span data-ttu-id="5d882-141">データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="5d882-141">Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;</span></span>](../create-a-data-driven-subscription-ssrs-tutorial.md)|<span data-ttu-id="5d882-142">データ ドリブン サブスクリプションの作成方法について理解するための手順を記載しています。</span><span class="sxs-lookup"><span data-stu-id="5d882-142">Provides step-by-step instruction for learning how to create a data-driven subscription.</span></span>|  
|[<span data-ttu-id="5d882-143">レポートのキャッシュ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5d882-143">Caching Reports &#40;SSRS&#41;</span></span>](../report-server/caching-reports-ssrs.md)|<span data-ttu-id="5d882-144">データ ドリブン サブスクリプションと NULL 配信プロバイダーを使用して、キャッシュを事前に読み込む方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="5d882-144">Describes how to use the Null Delivery Provider with a data-driven subscription to preload the cache.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d882-145">参照</span><span class="sxs-lookup"><span data-stu-id="5d882-145">See Also</span></span>  
 <span data-ttu-id="5d882-146">[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="5d882-146">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="5d882-147">[[データドリブンサブスクリプションの作成] ページ &#40;レポートマネージャー&#41;](../create-data-driven-subscription-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5d882-147">[Create Data-driven Subscription Page &#40;Report Manager&#41;](../create-data-driven-subscription-page-report-manager.md) </span></span>  
 [<span data-ttu-id="5d882-148">キャッシュの事前読み込み &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="5d882-148">Preload the Cache &#40;Report Manager&#41;</span></span>](../report-server/preload-the-cache-report-manager.md)  
  
  