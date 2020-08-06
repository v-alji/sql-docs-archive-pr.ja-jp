---
title: データ コレクターのプロパティの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05172c2c831ec649269512a625be069cdc67047a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718249"
---
# <a name="configure-properties-of-a-data-collector"></a><span data-ttu-id="9065f-102">データ コレクターのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="9065f-102">Configure Properties of a Data Collector</span></span>
  <span data-ttu-id="9065f-103">ここでは、データ コレクターのプロパティを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9065f-103">This topic discusses how you can configure the properties of a data collector.</span></span>  
  
## <a name="data-collection-properties-general-tab"></a><span data-ttu-id="9065f-104">[データ コレクションのプロパティ] ([全般] タブ)</span><span class="sxs-lookup"><span data-stu-id="9065f-104">Data Collection Properties (General Tab)</span></span>  
 <span data-ttu-id="9065f-105">このページを使用すると、管理データ ウェアハウスの設定を構成し、収集したデータをデータ ウェアハウスにアップロードするまで格納しておく場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9065f-105">Use this page to configure settings for the management data warehouse and specify where collected data should be stored before it is uploaded to the data warehouse.</span></span>  
  
 <span data-ttu-id="9065f-106">**[データ コレクションの有効化]**</span><span class="sxs-lookup"><span data-stu-id="9065f-106">**Enable Data Collection**</span></span>  
 <span data-ttu-id="9065f-107">データ コレクションを有効にする場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="9065f-107">Select to enable data collection.</span></span> <span data-ttu-id="9065f-108">これは、sp_syscollector_enable_collector ストアド プロシージャを実行するのと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="9065f-108">This has the same effect as running the sp_syscollector_enable_collector stored procedure.</span></span> <span data-ttu-id="9065f-109">このチェック ボックスをオフにすると、データ コレクションが無効になり、sp_syscollector_disable_collector ストアド プロシージャを実行した場合と同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="9065f-109">Clearing this check box disables data collection and has the same effect as running the sp_syscollector_disable_collector stored procedure.</span></span>  
  
 <span data-ttu-id="9065f-110">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="9065f-110">**Server**</span></span>  
 <span data-ttu-id="9065f-111">管理データ ウェアハウスをホストするサーバーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9065f-111">Displays the name of the server that will host the management data warehouse</span></span>  
  
 <span data-ttu-id="9065f-112">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="9065f-112">**Database name**</span></span>  
 <span data-ttu-id="9065f-113">管理データ ウェアハウスに使用されるリレーショナル データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9065f-113">Displays the name of the relational database that is used for the management data warehouse.</span></span>  
  
 <span data-ttu-id="9065f-114">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="9065f-114">**Test Connection**</span></span>  
 <span data-ttu-id="9065f-115">データ コレクションの構成時に指定した情報を使用して、 **[サーバー]** で指定したサーバーへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="9065f-115">Test the connection to the specified **Server** using information provided when data collection is configured.</span></span>  
  
 <span data-ttu-id="9065f-116">**[キャッシュ ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="9065f-116">**Cache directory**</span></span>  
 <span data-ttu-id="9065f-117">収集したデータを管理データ ウェアハウスにアップロードするまで格納しておく、データを収集したシステム上のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="9065f-117">Specifies the directory where collected data is stored on the system collecting the data before it is uploaded to the management data warehouse.</span></span> <span data-ttu-id="9065f-118">**キャッシュ ディレクトリ** が指定されていない場合、データ コレクターは %TEMP% 環境変数と %TMP% 環境変数を探し、これらの場所を一時ストレージの既定の場所として使用しようとします。</span><span class="sxs-lookup"><span data-stu-id="9065f-118">If **Cache directory** is not specified, the data collector attempts to locate the %TEMP% and %TMP% environment variables and use one these locations as the default location for temporary storage.</span></span> <span data-ttu-id="9065f-119">これらの環境変数が構成されていない場合はエラーが発生し、キャッシュ ディレクトリを作成するよう求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9065f-119">If these environment variables are not configured, an error occurs and you are prompted to create a cache directory.</span></span>  
  
## <a name="data-collection-properties-advanced-tab"></a><span data-ttu-id="9065f-120">[データ コレクションのプロパティ] ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="9065f-120">Data Collection Properties (Advanced Tab)</span></span>  
 <span data-ttu-id="9065f-121">このページを使用すると、管理データ ウェアハウスへの接続の再試行の設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="9065f-121">Use this page to configure the retry settings for the connection to the management data warehouse.</span></span>  
  
 <span data-ttu-id="9065f-122">**[アップロード失敗時の再試行回数]**</span><span class="sxs-lookup"><span data-stu-id="9065f-122">**Number of times to retry if upload fails**</span></span>  
 <span data-ttu-id="9065f-123">アップロードが失敗した場合に、管理データ ウェアハウスへのアップロードを再試行する回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9065f-123">Specifies the number of times to retry an upload to the management data warehouse if an upload fails.</span></span> <span data-ttu-id="9065f-124">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="9065f-124">The default is 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9065f-125">参照</span><span class="sxs-lookup"><span data-stu-id="9065f-125">See Also</span></span>  
 <span data-ttu-id="9065f-126">[データ コレクションの管理](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="9065f-126">[Manage Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="9065f-127">管理データ ウェアハウスの構成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9065f-127">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
