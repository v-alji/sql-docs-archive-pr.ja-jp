---
title: レポートまたはデータフィードへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connreportdatafeed.f1
ms.assetid: e0ccfb0b-e646-4de8-b7da-f88c986c96e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76dd51c32d13e64b0368267ba7ac66aa6d76a784
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633470"
---
# <a name="connect-to-a-report-or-data-feed-ssas"></a><span data-ttu-id="128e1-102">[レポートまたはデータ フィードへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="128e1-102">Connect to a Report or Data Feed (SSAS)</span></span>
  <span data-ttu-id="128e1-103">**テーブルのインポート ウィザード** のこのページを使用すると、データ フィードに接続できます。</span><span class="sxs-lookup"><span data-stu-id="128e1-103">This page of the **Table Import Wizard** enables you to connect to a data feed.</span></span> <span data-ttu-id="128e1-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="128e1-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="from-a-report"></a><span data-ttu-id="128e1-105">レポートから</span><span class="sxs-lookup"><span data-stu-id="128e1-105">From a Report</span></span>  
 <span data-ttu-id="128e1-106">**接続の表示名**</span><span class="sxs-lookup"><span data-stu-id="128e1-106">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="128e1-107">データ フィード接続の表示名を入力します。</span><span class="sxs-lookup"><span data-stu-id="128e1-107">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="128e1-108">**[レポートのパス]**</span><span class="sxs-lookup"><span data-stu-id="128e1-108">**Report Path**</span></span>  
 <span data-ttu-id="128e1-109">データ フィードを生成する SQL Server Reporting Services レポートの URL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="128e1-109">Lists the URL for a SQL Server Reporting Services report that generates data feeds.</span></span> <span data-ttu-id="128e1-110">**[参照]** をクリックして、レポートの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="128e1-110">Click **Browse** to specify the URL for the report.</span></span>  
  
 <span data-ttu-id="128e1-111">**[レポートの表示]** をクリックしてレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="128e1-111">Click **View Report** to display the report.</span></span>  
  
 <span data-ttu-id="128e1-112">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="128e1-112">**Browse**</span></span>  
 <span data-ttu-id="128e1-113">使用可能なレポートがある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="128e1-113">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="128e1-114">**詳細**</span><span class="sxs-lookup"><span data-stu-id="128e1-114">**Advanced**</span></span>  
 <span data-ttu-id="128e1-115">**[詳細プロパティの設定**] ダイアログボックスを使用して、追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="128e1-115">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="128e1-116">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="128e1-116">**Test Connection**</span></span>  
 <span data-ttu-id="128e1-117">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="128e1-117">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="128e1-118">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128e1-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-an-azure-datamarket-dataset"></a><span data-ttu-id="128e1-119">Azure DataMarket データセットから</span><span class="sxs-lookup"><span data-stu-id="128e1-119">From an Azure DataMarket Dataset</span></span>  
 <span data-ttu-id="128e1-120">**接続の表示名**</span><span class="sxs-lookup"><span data-stu-id="128e1-120">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="128e1-121">データ フィード接続の表示名を入力します。</span><span class="sxs-lookup"><span data-stu-id="128e1-121">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="128e1-122">**[データ フィード URL]**</span><span class="sxs-lookup"><span data-stu-id="128e1-122">**Data Feed URL**</span></span>  
 <span data-ttu-id="128e1-123">Atom サービス ドキュメント (.atomsvc、.atom) への完全なパス、または単一のデータ フィードの URL を入力するか、 **[参照]** をクリックして Atom サービス ドキュメントを選択します。</span><span class="sxs-lookup"><span data-stu-id="128e1-123">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="128e1-124">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="128e1-124">**Browse**</span></span>  
 <span data-ttu-id="128e1-125">使用可能なレポートがある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="128e1-125">Navigate to a location where a report is available.</span></span>  
  
 <span data-ttu-id="128e1-126">使用可能なデータセットを表示するには、 **[使用可能な Azure DataMarket データセットの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="128e1-126">Click **View available Azure DataMarket datasets** to display available datasets.</span></span>  
  
 <span data-ttu-id="128e1-127">**アカウント キー**</span><span class="sxs-lookup"><span data-stu-id="128e1-127">**Account key**</span></span>  
 <span data-ttu-id="128e1-128">Azure Marketplace データセットサブスクリプションへのアクセスに使用するアカウントキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="128e1-128">Specify the account key used to access your Azure Marketplace dataset subscriptions.</span></span>  
  
 <span data-ttu-id="128e1-129">**探す**</span><span class="sxs-lookup"><span data-stu-id="128e1-129">**Find**</span></span>  
 <span data-ttu-id="128e1-130">Windows Live アカウントに関連付けられたアカウント キーを検索します。</span><span class="sxs-lookup"><span data-stu-id="128e1-130">Locate an account key associated with a Windows Live account.</span></span>  
  
 <span data-ttu-id="128e1-131">**[アカウント キーを保存する]**</span><span class="sxs-lookup"><span data-stu-id="128e1-131">**Save my account key**</span></span>  
 <span data-ttu-id="128e1-132">暗号化されたアカウント キーをデータ接続と共に保存します。</span><span class="sxs-lookup"><span data-stu-id="128e1-132">Saves the account key (encrypted) with the data connection.</span></span>  
  
 <span data-ttu-id="128e1-133">**詳細**</span><span class="sxs-lookup"><span data-stu-id="128e1-133">**Advanced**</span></span>  
 <span data-ttu-id="128e1-134">**[詳細プロパティの設定**] ダイアログボックスを使用して、追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="128e1-134">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="128e1-135">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="128e1-135">**Test Connection**</span></span>  
 <span data-ttu-id="128e1-136">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="128e1-136">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="128e1-137">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128e1-137">A message is displayed indicating whether the connection is successful.</span></span>  
  
## <a name="from-other-feeds"></a><span data-ttu-id="128e1-138">その他のフィードから</span><span class="sxs-lookup"><span data-stu-id="128e1-138">From Other Feeds</span></span>  
 <span data-ttu-id="128e1-139">**接続の表示名**</span><span class="sxs-lookup"><span data-stu-id="128e1-139">**Friendly Connection Name**</span></span>  
 <span data-ttu-id="128e1-140">データ フィード接続の表示名を入力します。</span><span class="sxs-lookup"><span data-stu-id="128e1-140">Type a friendly name for the data feed connection.</span></span>  
  
 <span data-ttu-id="128e1-141">**[データ フィード URL]**</span><span class="sxs-lookup"><span data-stu-id="128e1-141">**Data Feed URL**</span></span>  
 <span data-ttu-id="128e1-142">Atom サービス ドキュメント (.atomsvc、.atom) への完全なパス、または単一のデータ フィードの URL を入力するか、 **[参照]** をクリックして Atom サービス ドキュメントを選択します。</span><span class="sxs-lookup"><span data-stu-id="128e1-142">Type the full path to an Atom service document (.atomsvc, .atom) or the URL for a single data feed, or click **Browse** to select an Atom service document.</span></span>  
  
 <span data-ttu-id="128e1-143">**[すべてのフィード列を含める]** をクリックして、すべてのデータ フィード列をインポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="128e1-143">Click **Include all feed columns** to specify whether all the data feed columns are imported.</span></span>  
  
 <span data-ttu-id="128e1-144">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="128e1-144">**Browse**</span></span>  
 <span data-ttu-id="128e1-145">使用可能なデータ フィードがある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="128e1-145">Navigate to a location where a data feed is available.</span></span>  
  
 <span data-ttu-id="128e1-146">**詳細**</span><span class="sxs-lookup"><span data-stu-id="128e1-146">**Advanced**</span></span>  
 <span data-ttu-id="128e1-147">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="128e1-147">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="128e1-148">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="128e1-148">**Test Connection**</span></span>  
 <span data-ttu-id="128e1-149">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="128e1-149">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="128e1-150">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="128e1-150">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
