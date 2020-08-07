---
title: '[SQL Server のプロパティ] ([AlwaysOn 高可用性] タブ) |Microsoft Docs'
description: SQL Server 2014 で AlwaysOn 可用性グループ機能をオンまたはオフにする方法について説明します。 この機能のためにサーバーインスタンスが満たす必要のある前提条件を表示します。
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 3939b40a334746e9ee96441338e2e50791987103
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719275"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a><span data-ttu-id="334a6-104">SQL Server のプロパティ ([AlwaysOn 高可用性] タブ)</span><span class="sxs-lookup"><span data-stu-id="334a6-104">SQL Server Properties (AlwaysOn High Availability Tab)</span></span>
  <span data-ttu-id="334a6-105">**構成マネージャーの** [SQL Server のプロパティ] **ダイアログ ボックスの** [AlwaysOn 高可用性] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] タブを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の AlwaysOn 可用性グループを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="334a6-105">Use the **AlwaysOn High Availability** tab of the **SQL Server Properties** dialog box in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to enable or disable the AlwaysOn Availability Groups feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="334a6-106">AlwaysOn 可用性グループの有効化は、高可用性およびディザスター リカバリー ソリューションとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが可用性グループを使用するための前提条件です。</span><span class="sxs-lookup"><span data-stu-id="334a6-106">Enabling AlwaysOn Availability Groups is a prerequisite for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use availability groups as a high availability and disaster recovery solution.</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="334a6-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="334a6-107">Prerequisites</span></span>  
 <span data-ttu-id="334a6-108">AlwaysOn 可用性グループを有効にするには、サーバー インスタンスが以下の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="334a6-108">To be enabled for AlwaysOn Availability Groups, a server instance must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="334a6-109">このサーバー インスタンスは、Windows Server フェールオーバー クラスタリング (WSFC) ノードに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="334a6-109">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="334a6-110">同じ可用性グループのインスタンスはすべて、同じ WSFC クラスターに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="334a6-110">To be in the same availability group, instances must be in the same WSFC cluster.</span></span> <span data-ttu-id="334a6-111">可用性グループが複数の WSFC クラスターにまたがることはできません。</span><span class="sxs-lookup"><span data-stu-id="334a6-111">An availability group cannot span WSFC clusters.</span></span>  
  
-   <span data-ttu-id="334a6-112">サーバー インスタンスでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートする [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]エディションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="334a6-112">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
-   <span data-ttu-id="334a6-113">一度に 1 つのサーバー インスタンスでのみ AlwaysOn 可用性グループを有効にします。</span><span class="sxs-lookup"><span data-stu-id="334a6-113">Enable AlwaysOn Availability Groups for only one server instance at a time.</span></span> <span data-ttu-id="334a6-114">AlwaysOn 可用性グループを有効にした後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが再起動するまで待ってから、次のサーバー インスタンスを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="334a6-114">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has restarted before you enable the next server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="334a6-115">サポートされている機能の詳細、および [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]の追加の前提条件、制限、推奨設定については、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] オンライン ブックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="334a6-115">For information about feature support and for information about additional prerequisites, restrictions, and recommendations for [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
## <a name="dialog-options"></a><span data-ttu-id="334a6-116">ダイアログ オプション</span><span class="sxs-lookup"><span data-stu-id="334a6-116">Dialog Options</span></span>  
 <span data-ttu-id="334a6-117">**[Windows フェールオーバー クラスター名]**</span><span class="sxs-lookup"><span data-stu-id="334a6-117">**Windows failover cluster name**</span></span>  
 <span data-ttu-id="334a6-118">ローカル コンピューターのノードが含まれる WSFC クラスターの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="334a6-118">Displays the name of the WSFC cluster in which the local computer is a node.</span></span>  
  
 <span data-ttu-id="334a6-119">**AlwaysOn 可用性グループを有効にする**</span><span class="sxs-lookup"><span data-stu-id="334a6-119">**Enable AlwaysOn Availability Groups**</span></span>  
 <span data-ttu-id="334a6-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのインスタンスで AlwaysOn 可用性グループを有効または無効にするには、このチェック ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="334a6-120">Use this check box to enable or disable AlwaysOn Availability Groups on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as follows:</span></span>  
  
-   <span data-ttu-id="334a6-121">このチェック ボックスがオフの場合、AlwaysOn 可用性グループは現在無効になっています。</span><span class="sxs-lookup"><span data-stu-id="334a6-121">If this check box is empty, AlwaysOn Availability Groups is currently disabled.</span></span> <span data-ttu-id="334a6-122">AlwaysOn 可用性グループを有効にするには、このチェック ボックスをオンにして、 **[OK]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを手動で再起動します。</span><span class="sxs-lookup"><span data-stu-id="334a6-122">To enable AlwaysOn Availability Groups, select this check box, click **OK**, and manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="334a6-123">このチェック ボックスが既にオンに設定されている場合、AlwaysOn 可用性グループは現在有効になっています。</span><span class="sxs-lookup"><span data-stu-id="334a6-123">If this check box is already selected, AlwaysOn Availability Groups is currently enabled.</span></span> <span data-ttu-id="334a6-124">AlwaysOn 可用性グループを無効にするには、このチェック ボックスをオフにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="334a6-124">To disable AlwaysOn Availability Groups, uncheck the check box and click **OK**.</span></span> <span data-ttu-id="334a6-125">これにより、サーバー インスタンスが再起動します。</span><span class="sxs-lookup"><span data-stu-id="334a6-125">This causes the server instance to restart.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="334a6-126">AlwaysOn 可用性グループを無効にした後は、サーバー インスタンスからローカル可用性レプリカをすべて削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="334a6-126">After disabling AlwaysOn Availability Groups, you should remove any local availability replicas from the server instance.</span></span> <span data-ttu-id="334a6-127">各可用性グループの最後のレプリカを削除したら、グループも削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="334a6-127">If you remove the last replica of a given availability group, you should also remove the group.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="334a6-128">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="334a6-128">UI element list</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="334a6-129">AlwaysOn 可用性グループを無効にした後の設定と、可用性グループの作成および構成方法については、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="334a6-129">For more information about follow up after you disable AlwaysOn Availability Groups and for information about how to create and configure availability groups, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
