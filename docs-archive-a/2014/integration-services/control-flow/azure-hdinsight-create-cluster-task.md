---
title: Azure HDInsight Create Cluster Task | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4029e3a01cbcfe04be5f2879a9b60866bfc867a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713390"
---
# <a name="azure-hdinsight-create-cluster-task"></a><span data-ttu-id="a93a6-102">Azure HDInsight Create Cluster Task</span><span class="sxs-lookup"><span data-stu-id="a93a6-102">Azure HDInsight Create Cluster Task</span></span>
<span data-ttu-id="a93a6-103">**Azure HDInsight Create Cluster Task** を使用すると、指定された Azure サブスクリプションとリソース グループの Azure HDInsight クラスターを SSIS パッケージで作成できます。</span><span class="sxs-lookup"><span data-stu-id="a93a6-103">The **Azure HDInsight Create Cluster Task** enables an SSIS package to create an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]  
> - <span data-ttu-id="a93a6-104">新しい HDInsight クラスターの作成には 10 分から 20 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a93a6-104">Creating a new HDInsight cluster may take 10~20 minutes.</span></span>  
> - <span data-ttu-id="a93a6-105">Azure HDInsight クラスターの作成と実行には、料金がかかります。</span><span class="sxs-lookup"><span data-stu-id="a93a6-105">There is a cost associated with creating and running an Azure HDInsight cluster.</span></span> <span data-ttu-id="a93a6-106">詳細については、「[HDInsight の価格](https://azure.microsoft.com/pricing/details/hdinsight/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a93a6-106">See [HDInsight Pricing](https://azure.microsoft.com/pricing/details/hdinsight/) for details.</span></span>  
  
<span data-ttu-id="a93a6-107">**Azure HDInsight Create Cluster Task**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックします。すると、次の **[Azure HDInsight Create Cluster Task エディター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a93a6-107">To add an **Azure HDInsight Create Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Create Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="a93a6-108">次の表で、このダイアログ ボックスの各フィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-108">The following table provides a description of the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a93a6-109">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="a93a6-109">**Field**</span></span>|<span data-ttu-id="a93a6-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="a93a6-110">**Description**</span></span>|  
|<span data-ttu-id="a93a6-111">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="a93a6-111">AzureResourceManagerConnection</span></span>|<span data-ttu-id="a93a6-112">既存の Azure Resource Manager 接続マネージャーを選択するか、HDInsight クラスターを作成するために使用する新しいものを作成します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-112">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to create the HDInsight cluster.</span></span>|  
|<span data-ttu-id="a93a6-113">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="a93a6-113">AzureStorageConnection</span></span>|<span data-ttu-id="a93a6-114">既存の Azure ストレージ接続マネージャーを選ぶか、HDInsight クラスターに関連付けられている Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-114">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account that will be associated with the HDInsight cluster.</span></span>|
|<span data-ttu-id="a93a6-115">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="a93a6-115">SubscriptionId</span></span>|<span data-ttu-id="a93a6-116">HDInsight クラスターが作成されるサブスクリプションの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-116">Specify the ID of the subscription the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="a93a6-117">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="a93a6-117">ResourceGroup</span></span>|<span data-ttu-id="a93a6-118">HDInsight クラスターが作成される Azure リソース グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-118">Specify the Azure resource group the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="a93a6-119">場所</span><span class="sxs-lookup"><span data-stu-id="a93a6-119">Location</span></span>|<span data-ttu-id="a93a6-120">HDInsight クラスターの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-120">Specify the location of the HDInsight cluster.</span></span> <span data-ttu-id="a93a6-121">クラスターは、指定された Azure ストレージ アカウントと同じ場所に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a93a6-121">The cluster must be created in the same location as the Azure Storage Account specified.</span></span>|  
|<span data-ttu-id="a93a6-122">ClusterName</span><span class="sxs-lookup"><span data-stu-id="a93a6-122">ClusterName</span></span>|<span data-ttu-id="a93a6-123">作成する HDInsight クラスターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-123">Specify a name for the HDInsight cluster to be created.</span></span>|  
|<span data-ttu-id="a93a6-124">ClusterSize</span><span class="sxs-lookup"><span data-stu-id="a93a6-124">ClusterSize</span></span>|<span data-ttu-id="a93a6-125">クラスターに作成するノードの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-125">Specify the number of nodes to create in the cluster.</span></span>|  
|<span data-ttu-id="a93a6-126">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="a93a6-126">BlobContainer</span></span>|<span data-ttu-id="a93a6-127">HDInsight クラスターに関連付けられる既定のストレージ コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-127">Specify the name of the default storage container to be associated with the HDInsight cluster.</span></span>|  
|<span data-ttu-id="a93a6-128">UserName</span><span class="sxs-lookup"><span data-stu-id="a93a6-128">UserName</span></span>|<span data-ttu-id="a93a6-129">HDInsight クラスターに接続するために使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-129">Specify the user name to be used for connecting to the HDInsight cluster.</span></span>|  
|<span data-ttu-id="a93a6-130">Password</span><span class="sxs-lookup"><span data-stu-id="a93a6-130">Password</span></span>|<span data-ttu-id="a93a6-131">HDInsight クラスターに接続するために使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-131">Specify the password to be used for connecting to the HDInsight cluster.</span></span>|
|<span data-ttu-id="a93a6-132">SshUserName</span><span class="sxs-lookup"><span data-stu-id="a93a6-132">SshUserName</span></span>|<span data-ttu-id="a93a6-133">SSH を使用して HDInsight クラスターをリモートでアクセスするために使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-133">Specify the user name used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="a93a6-134">SshPassword</span><span class="sxs-lookup"><span data-stu-id="a93a6-134">SshPassword</span></span>|<span data-ttu-id="a93a6-135">SSH を使用して HDInsight クラスターをリモートでアクセスするために使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-135">Specify the password used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="a93a6-136">FailIfExists</span><span class="sxs-lookup"><span data-stu-id="a93a6-136">FailIfExists</span></span>|<span data-ttu-id="a93a6-137">クラスターが既に存在する場合に、タスクがエラーになるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a6-137">Specify whether the task should fail if the cluster already exists.</span></span>|  
  
> [!NOTE]  
> <span data-ttu-id="a93a6-138">HDInsight クラスターと Azure ストレージ アカウントの場所は同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a93a6-138">The locations of the HDInsight cluster and the Azure Storage Account must be the same.</span></span>
