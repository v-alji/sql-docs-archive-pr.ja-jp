---
title: データマイニングソリューションを以前のバージョンの SQL Server | に配置します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f09a37c078cf58f24db9a08e3ddcb68cb2638717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644229"
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a><span data-ttu-id="99021-102">SQL Server の以前のバージョンへのデータ マイニング ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="99021-102">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>
  <span data-ttu-id="99021-103">ここでは、 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] のインスタンスで作成されたデータ マイニング モデルまたはデータ マイニング構造を、SQL Server 2005 Analysis Services を使用するデータベースに配置しようとする際、または SQL Server 2005 で作成されたモデルを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスに配置する際に発生する可能性のある、互換性に関する既知の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="99021-103">This section describes known compatibility issues that may arise when you attempt to deploy a data mining model or data mining structure that was created in an instance of [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to a database that uses SQL Server 2005 Analysis Services, or when you deploy models created in SQL Server 2005 to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="99021-104">SQL Server 2000 Analysis Services のインスタンスへの配置はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="99021-104">Deployment to an instance of SQL Server 2000 Analysis Services is not supported.</span></span>  
  
 [<span data-ttu-id="99021-105">タイム シリーズ モデルの配置</span><span class="sxs-lookup"><span data-stu-id="99021-105">Deploying Time Series Models</span></span>](#bkmk_TimeSeries)  
  
 [<span data-ttu-id="99021-106">提示されるモデルのデプロイ</span><span class="sxs-lookup"><span data-stu-id="99021-106">Deploying Models with Holdout</span></span>](#bkmk_Holdout)  
  
 [<span data-ttu-id="99021-107">フィルターを使用したモデルの配置</span><span class="sxs-lookup"><span data-stu-id="99021-107">Deploying Models with Filters</span></span>](#bkmk_Filter)  
  
 [<span data-ttu-id="99021-108">データベース バックアップからの復元</span><span class="sxs-lookup"><span data-stu-id="99021-108">Restoring from Database Backups</span></span>](#bkmk_Backup)  
  
 [<span data-ttu-id="99021-109">データベースの同期の使用</span><span class="sxs-lookup"><span data-stu-id="99021-109">Using Database Synchronization</span></span>](#bkmk_Synch)  
  
##  <a name="deploying-times-series-models"></a><a name="bkmk_TimeSeries"></a><span data-ttu-id="99021-110">時系列モデルの配置</span><span class="sxs-lookup"><span data-stu-id="99021-110">Deploying Times Series Models</span></span>  
 <span data-ttu-id="99021-111">Microsoft Time Series アルゴリズムは、SQL Server 2008 で補完的なアルゴリズムの ARIMA が追加され、機能が拡張されています。</span><span class="sxs-lookup"><span data-stu-id="99021-111">The Microsoft Time Series algorithm was enhanced in SQL Server 2008 by the addition of a second, complementary algorithm, ARIMA.</span></span> <span data-ttu-id="99021-112">タイム シリーズ アルゴリズムの変更に関する詳細については、「 [Microsoft Time Series アルゴリズム](microsoft-time-series-algorithm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99021-112">For more information about the changes in the time series algorithm, see [Microsoft Time Series Algorithm](microsoft-time-series-algorithm.md).</span></span>  
  
 <span data-ttu-id="99021-113">したがって、新しい ARIMA アルゴリズムを使用するタイム シリーズ マイニング モデルを SQL Server 2005 Analysis Services のインスタンスに配置すると、動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="99021-113">Therefore, time series mining models that use the new ARIMA algorithm may behave differently when deployed to an instance of SQL Server 2005 Analysis Services.</span></span>  
  
 <span data-ttu-id="99021-114">ARTXP モデルと ARIMA モデルを組み合わせた予測を制御するパラメーター PREDICTION_SMOOTHING を明示的に設定している場合に、このモデルを SQL Server 2005 のインスタンスに配置すると、パラメーターが無効であるというエラーが Analysis Services で発生します。</span><span class="sxs-lookup"><span data-stu-id="99021-114">If you have explicitly set the parameter PREDICTION_SMOOTHING to control the mixture of ARTXP and ARIMA models in prediction, when you deploy this model to an instance of SQL Server 2005, Analysis Services will raise an error stating that the parameter is not valid.</span></span> <span data-ttu-id="99021-115">このエラーを防ぐには、PREDICTION_SMOOTHING パラメーターを削除し、モデルを純粋な ARTXP モデルに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99021-115">To prevent this error, you must delete the PREDICTION_SMOOTHING parameter and convert the models to a pure ARTXP model.</span></span>  
  
 <span data-ttu-id="99021-116">反対に、SQL Server 2005 Analysis Services を使用して作成されたタイム シリーズ モデルを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスに配置する場合、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でマイニング モデルを開くと、最初に定義ファイルが新しい形式に変換され、既定では、2 つの新しいパラメーターがすべてのタイム シリーズ モデルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="99021-116">Conversely, if you deploy a time series model that was created using SQL Server 2005 Analysis Services to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], when you open the mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the definition files are first converted to the new format, and two new parameters are added by default to all time series models.</span></span> <span data-ttu-id="99021-117">パラメーター FORECAST_METHOD が既定値 MIXED で追加され、パラメーター PREDICTION_SMOOTHING が既定値 0.5 で追加されます。</span><span class="sxs-lookup"><span data-stu-id="99021-117">The parameter FORECAST_METHOD is added with the default value of MIXED, and the parameter PREDICTION_SMOOTHING is added with the default value of 0.5.</span></span> <span data-ttu-id="99021-118">ただし、モデルを再処理するまで、モデルは引き続き ARTXP のみを予測に使用します。</span><span class="sxs-lookup"><span data-stu-id="99021-118">However, the model will continue to use only ARTXP for forecasting until you reprocess the model.</span></span> <span data-ttu-id="99021-119">モデルの再処理が終わるとすぐ、予測に ARIMA と ARTXP の両方が使用されます。</span><span class="sxs-lookup"><span data-stu-id="99021-119">As soon as you reprocess the model, prediction changes to use both ARIMA and ARTXP.</span></span>  
  
 <span data-ttu-id="99021-120">したがって、モデルが変更されないようにするには、モデルを参照するだけにして、決して処理を行わないようにします。</span><span class="sxs-lookup"><span data-stu-id="99021-120">Therefore, if you wish to avoid changing the model, you should only browse the model and never process it.</span></span> <span data-ttu-id="99021-121">あるいは、FORECAST_METHOD パラメーターまたは PREDICTION_SMOOTHING パラメーターを明示的に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="99021-121">Alternatively, you could explicitly set the FORECAST_METHOD or PREDICTION_SMOOTHING parameters.</span></span>  
  
 <span data-ttu-id="99021-122">混合モデルを設定する方法については、「 [Microsoft Time Series アルゴリズム テクニカル リファレンス](microsoft-time-series-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99021-122">For detailed information about configuring mixed models, see [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="99021-123">モデルのデータ ソースに使用されるプロバイダーが SQL Client Data Provider 10 の場合、データ ソース定義も変更して、SQL Server Native Client の前のバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99021-123">If the provider that is used for the model's data source is SQL Client Data Provider 10, you must also modify the data source definition to specify the previous version of the SQL Server Native Client.</span></span> <span data-ttu-id="99021-124">そうしないと、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で、プロバイダーが登録されていないことを示すエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="99021-124">Otherwise, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] generates an error stating that the provider is not registered.</span></span>  
  
##  <a name="deploying-models-with-holdout"></a><a name="bkmk_Holdout"></a> <span data-ttu-id="99021-125">提示されたパーティションを使用するモデルの配置</span><span class="sxs-lookup"><span data-stu-id="99021-125">Deploying Models with Holdout</span></span>  
 <span data-ttu-id="99021-126">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] で、データ マイニング モデルのテストに使用する提示されたパーティションを含むマイニング構造を作成する場合、マイニング構造を SQL Server 2005 インスタンスに配置できますが、パーティションの情報は失われます。</span><span class="sxs-lookup"><span data-stu-id="99021-126">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to create a mining structure that contains a holdout partition used for testing data mining models, the mining structure can be deployed to an instance of SQL Server 2005, but the partition information will be lost.</span></span>  
  
 <span data-ttu-id="99021-127">SQL Server 2005 Analysis Services でマイニング構造を開くと、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でエラーが発生し、提示されたパーティションを削除するためにそのマイニング構造が再生成されます。</span><span class="sxs-lookup"><span data-stu-id="99021-127">When you open the mining structure in SQL Server 2005 Analysis Services, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] raises an error, and then regenerates the structure to remove the holdout partition.</span></span>  
  
 <span data-ttu-id="99021-128">構造が再構築されると、提示されたパーティションのサイズがプロパティウィンドウで使用できなくなります。ただし、値 \<ddl100_100:HoldoutMaxPercent> 30 \</ddl100_100:HoldoutMaxPercent> ) が assl スクリプトファイルに存在していてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="99021-128">After the structure has been rebuilt, the size of the holdout partition is no longer available in the Properties window; however, the value \<ddl100_100:HoldoutMaxPercent>30\</ddl100_100:HoldoutMaxPercent>) may still be present in the ASSL script file.</span></span>  
  
##  <a name="deploying-models-with-filters"></a><a name="bkmk_Filter"></a> <span data-ttu-id="99021-129">フィルターを使用するモデルの配置</span><span class="sxs-lookup"><span data-stu-id="99021-129">Deploying Models with Filters</span></span>  
 <span data-ttu-id="99021-130">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] で、マイニング モデルにフィルターを適用する場合、モデルを SQL Server 2005 インスタンスに配置できますが、フィルターは適用されません。</span><span class="sxs-lookup"><span data-stu-id="99021-130">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to apply a filter to a mining model, the model can be deployed to an instance of SQL Server 2005, but the filter will not be applied.</span></span>  
  
 <span data-ttu-id="99021-131">マイニング モデルを開くと、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でエラーが発生し、フィルターを削除するためにモデルが再生成されます。</span><span class="sxs-lookup"><span data-stu-id="99021-131">When you open the mining model, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] raises an error, and then regenerates the model to remove the filter.</span></span>  
  
##  <a name="restoring-from-database-backups"></a><a name="bkmk_Backup"></a><span data-ttu-id="99021-132">データベースバックアップからの復元</span><span class="sxs-lookup"><span data-stu-id="99021-132">Restoring from Database Backups</span></span>  
 <span data-ttu-id="99021-133">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で作成されたデータベース バックアップを SQL Server 2005 のインスタンスに復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="99021-133">You cannot restore a database backup that was created in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to an instance of SQL Server 2005.</span></span> <span data-ttu-id="99021-134">復元を実行すると、SQL Server Management Studio でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="99021-134">If you do so, SQL Server Management Studio generates an error.</span></span>  
  
 <span data-ttu-id="99021-135">SQL Server 2005 Analysis Services データベースのバックアップを作成して [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンス上に復元する場合、前のセクションで示したようにすべてのタイム シリーズ モデルが変更されます。</span><span class="sxs-lookup"><span data-stu-id="99021-135">If you create a backup of a SQL Server 2005 Analysis Services database and restore this backup on an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], all time series models are modified as described in the previous section.</span></span>  
  
##  <a name="using-database-synchronization"></a><a name="bkmk_Synch"></a><span data-ttu-id="99021-136">データベースの同期の使用</span><span class="sxs-lookup"><span data-stu-id="99021-136">Using Database Synchronization</span></span>  
 <span data-ttu-id="99021-137">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] から SQL Server 2005 へのデータベースの同期はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="99021-137">Database synchronization is not supported from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to SQL Server 2005.</span></span>  
  
 <span data-ttu-id="99021-138">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] データベースの同期を試みると、サーバーはエラーを返し、データベースの同期は失敗します。</span><span class="sxs-lookup"><span data-stu-id="99021-138">If you attempt to synchronize a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, the server returns an error and database synchronization fails.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99021-139">参照</span><span class="sxs-lookup"><span data-stu-id="99021-139">See Also</span></span>  
 [<span data-ttu-id="99021-140">Analysis Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="99021-140">Analysis Services Backward Compatibility</span></span>](../analysis-services-backward-compatibility.md)  
  
  
