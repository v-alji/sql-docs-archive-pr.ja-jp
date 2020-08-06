---
title: Azure Feature Pack |Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bca2b4d3ce91f6010fbe01da836efd8a67ca6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712334"
---
# <a name="azure-feature-pack"></a><span data-ttu-id="ccbfd-102">Azure Feature Pack</span><span class="sxs-lookup"><span data-stu-id="ccbfd-102">Azure Feature Pack</span></span>
<span data-ttu-id="ccbfd-103">SQL Server Integration Services (SSIS) Feature Pack for Azure は、このページにリストされている SSIS のコンポーネントを提供して、Azure サービスへの接続、Azure とオンプレミスのデータ ソース間でのデータ転送、および Azure に格納されたデータの処理を行うための拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-103">SQL Server Integration Services (SSIS) Feature Pack for Azure is an extension that provides the components listed on this page for SSIS to connect to Azure services, transfer data between Azure and on-premises data sources, and process data stored in Azure.</span></span>

## <a name="components-in-the-feature-pack"></a><span data-ttu-id="ccbfd-104">Feature Pack のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="ccbfd-104">Components in the Feature Pack</span></span>
  
-   <span data-ttu-id="ccbfd-105">接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ccbfd-105">Connection Managers</span></span>  
  
    -   [<span data-ttu-id="ccbfd-106">Azure Storage 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ccbfd-106">Azure Storage Connection Manager</span></span>](connection-manager/azure-storage-connection-manager.md)  
  
    -   [<span data-ttu-id="ccbfd-107">Azure サブスクリプション接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ccbfd-107">Azure Subscription Connection Manager</span></span>](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [<span data-ttu-id="ccbfd-108">Azure Data Lake Store 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ccbfd-108">Azure Data Lake Store Connection Manager</span></span>](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [<span data-ttu-id="ccbfd-109">Azure Resource Manager の接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ccbfd-109">Azure Resource Manager Connection Manager</span></span>](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [<span data-ttu-id="ccbfd-110">Azure HDInsight 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ccbfd-110">Azure HDInsight Connection Manager</span></span>](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   <span data-ttu-id="ccbfd-111">タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-111">Tasks</span></span>  
  
    -   [<span data-ttu-id="ccbfd-112">Azure BLOB のアップロード タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-112">Azure Blob Upload Task</span></span>](control-flow/azure-blob-upload-task.md)  
  
    -   [<span data-ttu-id="ccbfd-113">Azure BLOB のダウンロード タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-113">Azure Blob Download Task</span></span>](control-flow/azure-blob-download-task.md)  
  
    -   [<span data-ttu-id="ccbfd-114">Azure HDInsight Hive タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-114">Azure HDInsight Hive Task</span></span>](control-flow/azure-hdinsight-hive-task.md)  
  
    -   <span data-ttu-id="ccbfd-115">[Azure HDInsight Pig タスク](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="ccbfd-115">[Azure HDInsight Pig Task](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span></span>
  
    -   [<span data-ttu-id="ccbfd-116">Azure HDInsight クラスターの作成タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-116">Azure HDInsight Create Cluster Task</span></span>](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [<span data-ttu-id="ccbfd-117">Azure HDInsight クラスターの削除タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-117">Azure HDInsight Delete Cluster Task</span></span>](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [<span data-ttu-id="ccbfd-118">Azure SQL DW のアップロード タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-118">Azure SQL DW Upload Task</span></span>](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [<span data-ttu-id="ccbfd-119">Azure Data Lake Store ファイル システム タスク</span><span class="sxs-lookup"><span data-stu-id="ccbfd-119">Azure Data Lake Store File System Task</span></span>](control-flow/file-system-task.md)    
  
-   <span data-ttu-id="ccbfd-120">データ フロー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ccbfd-120">Data Flow Components</span></span>  
  
    -   <span data-ttu-id="ccbfd-121">[Azure BLOB Source](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="ccbfd-121">[Azure Blob Source](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span></span>  
  
    -   [<span data-ttu-id="ccbfd-122">Azure Blob Destination</span><span class="sxs-lookup"><span data-stu-id="ccbfd-122">Azure Blob Destination</span></span>](data-flow/azure-blob-destination.md)  
    
    -   [<span data-ttu-id="ccbfd-123">Azure Data Lake Store Source</span><span class="sxs-lookup"><span data-stu-id="ccbfd-123">Azure Data Lake Store Source</span></span>](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [<span data-ttu-id="ccbfd-124">Azure Data Lake Store Destination</span><span class="sxs-lookup"><span data-stu-id="ccbfd-124">Azure Data Lake Store Destination</span></span>](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   <span data-ttu-id="ccbfd-125">Azure Blob 列挙子は、ADLS File 列挙子 & ます。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-125">Azure Blob Enumerator & ADLS File Enumerator.</span></span> <span data-ttu-id="ccbfd-126">「 [Foreach ループコンテナー](control-flow/foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-126">See [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 
## <a name="download-the-feature-pack"></a><span data-ttu-id="ccbfd-127">Feature Pack のダウンロード</span><span class="sxs-lookup"><span data-stu-id="ccbfd-127">Download the Feature Pack</span></span>  
<span data-ttu-id="ccbfd-128">SQL Server Integration Services (SSIS) Feature Pack for Azure をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-128">Download the SQL Server Integration Services (SSIS) Feature Pack for Azure.</span></span>  
  
-   [<span data-ttu-id="ccbfd-129">Microsoft SQL Server 2014 Integration Services Feature Pack for Azure</span><span class="sxs-lookup"><span data-stu-id="ccbfd-129">Microsoft SQL Server 2014 Integration Services Feature Pack for Azure</span></span>](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a><span data-ttu-id="ccbfd-130">前提条件</span><span class="sxs-lookup"><span data-stu-id="ccbfd-130">Prerequisites</span></span>  
<span data-ttu-id="ccbfd-131">この機能パックをインストールする前に、次の前提条件をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-131">You must install the following prerequisites before installing this feature pack.</span></span>  
  
-   <span data-ttu-id="ccbfd-132">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="ccbfd-132">SQL Server Integration Services</span></span>  
-   <span data-ttu-id="ccbfd-133">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ccbfd-133">.Net Framework 4.5</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="ccbfd-134">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ccbfd-134">Scenarios</span></span>  
  
### <a name="big-data-processing"></a><span data-ttu-id="ccbfd-135">ビッグ データ処理</span><span class="sxs-lookup"><span data-stu-id="ccbfd-135">Big Data Processing</span></span>  
 <span data-ttu-id="ccbfd-136">Azure コネクタを使用して、次のビッグ データの処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-136">Use Azure Connector to complete following big data processing work:</span></span>  
  
1.  <span data-ttu-id="ccbfd-137">Azure Blob Upload Task を使用して、入力データを Azure Blob ストレージにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-137">Use the Azure Blob Upload Task to upload input data to Azure Blob Storage.</span></span>  
  
2.  <span data-ttu-id="ccbfd-138">Azure HDInsight Create Cluster Task を使用して、Azure HDInsight のクラスターを作成します。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-138">Use the Azure HDInsight Create Cluster Task to create an Azure HDInsight cluster.</span></span> <span data-ttu-id="ccbfd-139">独自のクラスターを使用する場合は、この手順は省略できます。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-139">This step is optional if you want to use your own cluster.</span></span>  
  
3.  <span data-ttu-id="ccbfd-140">Azure HDInsight Hive Task か Azure HDInsight Pig Task を使用して、Azure HDInsight クラスターで Pig または Hive ジョブを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-140">Use the Azure HDInsight Hive Task or Azure HDInsight Pig Task to invoke a Pig or Hive job on the Azure HDInsight cluster.</span></span>  
  
4.  <span data-ttu-id="ccbfd-141">手順 2 でオンデマンドの HDInsight クラスターを作成した場合は、使用後の HDInsight クラスターを Azure HDInsight Delete Cluster Task で削除します。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-141">Use the Azure HDInsight Delete Cluster Task to delete the HDInsight Cluster after use if you have created an on-demand HDInsight cluster in step #2.</span></span>  
  
5.  <span data-ttu-id="ccbfd-142">Azure HDInsight Blob Download Task を使用して、Azure Blob ストレージから Pig/Hive の出力データをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-142">Use the Azure HDInsight Blob Download Task to download the Pig/Hive output data from the Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="ccbfd-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span><span class="sxs-lookup"><span data-stu-id="ccbfd-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span></span>  
  
### <a name="cloud-data-archiving"></a><span data-ttu-id="ccbfd-144">クラウド データのアーカイブ</span><span class="sxs-lookup"><span data-stu-id="ccbfd-144">Cloud Data Archiving</span></span>  
 <span data-ttu-id="ccbfd-145">SSIS パッケージ内の Azure Blob Destination を使用して、出力データを Azure Blob ストレージに書き込みむか、または Azure Blob Source を使用して、Azure Blob ストレージからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-145">Use the Azure Blob Destination in an SSIS package to write output data to an Azure Blob Storage, or use the Azure Blob Source to read data from an Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="ccbfd-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span><span class="sxs-lookup"><span data-stu-id="ccbfd-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span></span>  
  
 <span data-ttu-id="ccbfd-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span><span class="sxs-lookup"><span data-stu-id="ccbfd-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span></span>  
  
 <span data-ttu-id="ccbfd-148">また、Azure Blob 列挙子とともに Foreach ループ コンテナーを使用して、複数の bob ファイルのデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-148">And use the Foreach Loop Container with Azure Blob Enumerator to process data in multiple bob files.</span></span>  
  
 <span data-ttu-id="ccbfd-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span><span class="sxs-lookup"><span data-stu-id="ccbfd-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span></span>  
  
  
