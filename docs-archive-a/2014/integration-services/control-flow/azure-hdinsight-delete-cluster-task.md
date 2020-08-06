---
title: Azure HDInsight クラスターの削除タスク | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: db0a15aaea37c6d18c1d3c2136e0fd0c94eb7506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644096"
---
# <a name="azure-hdinsight-delete-cluster-task"></a><span data-ttu-id="60090-102">Azure HDInsight クラスターの削除タスク</span><span class="sxs-lookup"><span data-stu-id="60090-102">Azure HDInsight Delete Cluster Task</span></span>
<span data-ttu-id="60090-103">**Azure HDInsight クラスターの削除タスク**を使用すると、指定された Azure サブスクリプションとリソース グループの Azure HDInsight クラスターを SSIS パッケージで削除できます。</span><span class="sxs-lookup"><span data-stu-id="60090-103">The **Azure HDInsight Delete Cluster Task** enables an SSIS package to delete an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]
> <span data-ttu-id="60090-104">HDInsight クラスターの削除には 10 分から 20 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="60090-104">Deleting an HDInsight cluster may take 10~20 minutes.</span></span>  
  
<span data-ttu-id="60090-105">**Azure HDInsight クラスターの削除タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure HDInsight クラスターの削除タスク エディター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="60090-105">To add an **Azure HDInsight Delete Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Delete Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="60090-106">次の表で、ダイアログ ボックスの各フィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="60090-106">The following table provides a description for the fields in the dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60090-107">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="60090-107">**Field**</span></span>|<span data-ttu-id="60090-108">**説明**</span><span class="sxs-lookup"><span data-stu-id="60090-108">**Description**</span></span>|  
|<span data-ttu-id="60090-109">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="60090-109">AzureResourceManagerConnection</span></span>|<span data-ttu-id="60090-110">既存の Azure Resource Manager 接続マネージャーを選択するか、HDInsight クラスターを削除するために使用する新しいものを作成します。</span><span class="sxs-lookup"><span data-stu-id="60090-110">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to delete the HDInsight cluster.</span></span>|
|<span data-ttu-id="60090-111">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="60090-111">SubscriptionId</span></span>|<span data-ttu-id="60090-112">HDInsight クラスターが存在するサブスクリプションの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="60090-112">Specify the ID of the subscription the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="60090-113">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="60090-113">ResourceGroup</span></span>|<span data-ttu-id="60090-114">HDInsight クラスターが存在する Azure リソース グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="60090-114">Specify the Azure resource group the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="60090-115">ClusterName</span><span class="sxs-lookup"><span data-stu-id="60090-115">ClusterName</span></span>|<span data-ttu-id="60090-116">削除するクラスターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="60090-116">Specify the name of the cluster to be deleted.</span></span>|  
|<span data-ttu-id="60090-117">FailIfNotExists</span><span class="sxs-lookup"><span data-stu-id="60090-117">FailIfNotExists</span></span>|<span data-ttu-id="60090-118">クラスターが存在しない場合に、タスクがエラーになるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="60090-118">Specify whether the task should fail if the cluster does not exist.</span></span>|
