---
title: データ ドリブン サブスクリプションの作成 (SSRS チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], tutorials
- walkthroughs [Reporting Services]
- data-driven subscriptions
ms.assetid: 79ab0572-43e9-4dc4-9b5a-cd8b627b8274
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53be7cf793d8fa38d177643c7f366115d4df8b7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719695"
---
# <a name="create-a-data-driven-subscription-ssrs-tutorial"></a><span data-ttu-id="66a9b-102">データ ドリブン サブスクリプションの作成 (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="66a9b-102">Create a Data-Driven Subscription (SSRS Tutorial)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="66a9b-103">が提供するデータ ドリブン サブスクリプションにより、動的なサブスクライバー データに基づいてレポートの配信をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="66a9b-103">provides data-driven subscriptions so that you can customize the distribution of a report based on dynamic subscriber data.</span></span> <span data-ttu-id="66a9b-104">データ ドリブン サブスクリプションには次のような用途があります。</span><span class="sxs-lookup"><span data-stu-id="66a9b-104">Data-driven subscriptions are intended for the following kinds of scenarios:</span></span>  
  
-   <span data-ttu-id="66a9b-105">配信するたびに宛先メンバーの構成が変更される多人数受信者プールへのレポート配信。</span><span class="sxs-lookup"><span data-stu-id="66a9b-105">Distributing reports to a large recipient pool whose membership may change from one distribution to the next.</span></span> <span data-ttu-id="66a9b-106">たとえば、月刊レポートを現在の全顧客に配信する場合など。</span><span class="sxs-lookup"><span data-stu-id="66a9b-106">For example, distribute a monthly report to all current customers.</span></span>  
  
-   <span data-ttu-id="66a9b-107">定義済みの条件に基づく特定の受信者グループへのレポート配信。</span><span class="sxs-lookup"><span data-stu-id="66a9b-107">Distributing reports to a specific group of recipients based on predefined criteria.</span></span> <span data-ttu-id="66a9b-108">たとえば、社内の上位 10 名の営業責任者に販売実績レポートを送信する場合など。</span><span class="sxs-lookup"><span data-stu-id="66a9b-108">For example, send a sales performance report to the top ten sales managers in an organization.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="66a9b-109">学習する内容</span><span class="sxs-lookup"><span data-stu-id="66a9b-109">What You Will Learn</span></span>  
 <span data-ttu-id="66a9b-110">このチュートリアルでは、簡単な例で概念を確認しながら、データ ドリブン サブスクリプションの使用方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-110">This tutorial shows you how to use data-driven subscriptions using a simple example to illustrate the concepts.</span></span>  
  
 <span data-ttu-id="66a9b-111">このチュートリアルは、次の 3 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="66a9b-111">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="66a9b-112">レッスン 1:サンプル サブスクライバー データベースの作成</span><span class="sxs-lookup"><span data-stu-id="66a9b-112">Lesson 1: Creating a Sample Subscriber Database</span></span>](lesson-1-creating-a-sample-subscriber-database.md)  
 <span data-ttu-id="66a9b-113">このレッスンでは、サブスクライバー情報を格納するローカル [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースを作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-113">In this lesson you will learn how to create a local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains subscriber information.</span></span>  
  
 [<span data-ttu-id="66a9b-114">レッスン 2: レポート データ ソースのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="66a9b-114">Lesson 2: Modifying the Report Data Source Properties</span></span>](lesson-2-modifying-the-report-data-source-properties.md)  
 <span data-ttu-id="66a9b-115">このレッスンでは、レポート データ ソースのプロパティを変更し、レポートを自動実行できるようにする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-115">In this lesson, you will learn how to modify report data source properties so that the report can run unattended.</span></span> <span data-ttu-id="66a9b-116">自動処理では保存された資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="66a9b-116">Unattended processing requires stored credentials.</span></span> <span data-ttu-id="66a9b-117">また、レポートのデータセットを変更して、サブスクライバーのデータが提供するパラメーターを含めます。</span><span class="sxs-lookup"><span data-stu-id="66a9b-117">You will also modify the report dataset to include a parameter that is supplied by the subscriber data.</span></span>  
  
 [<span data-ttu-id="66a9b-118">レッスン 3:データ ドリブン サブスクリプションの定義</span><span class="sxs-lookup"><span data-stu-id="66a9b-118">Lesson 3: Defining a Data-Driven Subscription</span></span>](lesson-3-defining-a-data-driven-subscription.md)  
 <span data-ttu-id="66a9b-119">このレッスンでは、データ ドリブン サブスクリプションを定義する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-119">In this lesson you will learn how to define a data-driven subscription.</span></span> <span data-ttu-id="66a9b-120">ここでは、データ ドリブン サブスクリプション ウィザードを 1 ページずつ順に実行します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-120">This lesson guides you through each page in the Data-Driven Subscription Wizard.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a9b-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="66a9b-121">Requirements</span></span>  
 <span data-ttu-id="66a9b-122">通常、データ ドリブン サブスクリプションはレポート サーバー管理者が作成し、保守します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-122">Data-driven subscriptions are typically created and maintained by report server administrators.</span></span> <span data-ttu-id="66a9b-123">データ ドリブン サブスクリプションを作成するには、クエリ作成の専門知識、サブスクライバー データを持つデータ ソースに関する知識、およびレポート サーバーへの高度なアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="66a9b-123">The ability to create data-driven subscriptions requires expertise in building queries, knowledge of data sources that contain subscriber data, and elevated permissions on a report server.</span></span>  
  
 <span data-ttu-id="66a9b-124">このチュートリアルでは、チュートリアル「[基本的なテーブルレポートの作成](create-a-basic-table-report-ssrs-tutorial.md)」で作成したレポートを使用して、SSRS チュートリアル&#41;とデータを &#40;します。[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a9b-124">The tutorial will use the report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md) and data from [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span></span>  
  
 <span data-ttu-id="66a9b-125">このチュートリアルを使用するには、システムに以下のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="66a9b-125">Your system must have the following installed to use this tutorial:</span></span>  
  
-   <span data-ttu-id="66a9b-126">データ ドリブン サブスクリプションをサポートするエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="66a9b-126">An edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that supports data-driven subscriptions.</span></span> <span data-ttu-id="66a9b-127">詳細については、「 [SQL Server 2014 のエディションとコンポーネント](../sql-server/editions-and-components-of-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a9b-127">For more information, see [Editions and Components of SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
-   <span data-ttu-id="66a9b-128">レポート サーバー (ネイティブ モードで実行)。</span><span class="sxs-lookup"><span data-stu-id="66a9b-128">The report server must be running in native mode.</span></span> <span data-ttu-id="66a9b-129">このチュートリアルで説明するユーザー インターフェイスは、ネイティブ モードのレポート サーバーに基づいています。</span><span class="sxs-lookup"><span data-stu-id="66a9b-129">The user interface described in this tutorial is based on a native mode report server.</span></span> <span data-ttu-id="66a9b-130">サブスクリプションは SharePoint モードのレポート サーバーでサポートされていますが、ユーザー インターフェイスはこのチュートリアルで説明されているものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="66a9b-130">Subscriptions are supported on SharePoint mode report servers but the user interface will be different than what is described in this tutorial.</span></span>  
  
-   <span data-ttu-id="66a9b-131">SQL Server エージェント サービス (実行された状態)。</span><span class="sxs-lookup"><span data-stu-id="66a9b-131">SQL Server Agent service must be running.</span></span>  
  
-   <span data-ttu-id="66a9b-132">パラメーターを含むレポート。</span><span class="sxs-lookup"><span data-stu-id="66a9b-132">A report that includes parameters.</span></span> <span data-ttu-id="66a9b-133">このチュートリアルでは、チュートリアル「 `Sales Orders` 基本的なテーブル レポートの作成 (SSRS チュートリアル) [基本的なテーブル レポートの作成 (SSRS チュートリアル)](create-a-basic-table-report-ssrs-tutorial.md)のデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="66a9b-133">This tutorial assumes the sample report, `Sales Orders` you create using the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
-   <span data-ttu-id="66a9b-134">サンプル レポートにデータを提供する [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="66a9b-134">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database, which provides data to the sample report.</span></span>  
  
-   <span data-ttu-id="66a9b-135">サンプル レポートで、すべてのサブスクリプション タスクを管理するためのロールの割り当て。</span><span class="sxs-lookup"><span data-stu-id="66a9b-135">A role assignment that includes the Manage all subscriptions task on the sample report.</span></span> <span data-ttu-id="66a9b-136">データ ドリブン サブスクリプションを定義するには、この作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="66a9b-136">This task is required for defining a data-driven subscription.</span></span> <span data-ttu-id="66a9b-137">コンピューター管理者の場合は、ローカル管理者用の既定のロール割り当てで、データ ドリブン サブスクリプションの作成に必要な権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="66a9b-137">If you are an administrator on the computer, the default role assignment for local administrators provides the permissions necessary for creating data-driven subscriptions.</span></span> <span data-ttu-id="66a9b-138">詳細については、「 [ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a9b-138">For more information, see [Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md).</span></span>  
  
-   <span data-ttu-id="66a9b-139">書き込み権限のある共有フォルダー。</span><span class="sxs-lookup"><span data-stu-id="66a9b-139">A shared folder for which you have write permissions.</span></span> <span data-ttu-id="66a9b-140">共有フォルダーはネットワーク接続経由でアクセス可能になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="66a9b-140">The shared folder must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="66a9b-141">**このチュートリアルの推定所要時間:** 30 分。</span><span class="sxs-lookup"><span data-stu-id="66a9b-141">**Estimated time to complete the tutorial:** 30 minutes.</span></span> <span data-ttu-id="66a9b-142">基本的なレポートのチュートリアルを完了していない場合は追加で 30 分かかります。</span><span class="sxs-lookup"><span data-stu-id="66a9b-142">An additional 30 minutes if you have not completed the basic report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a9b-143">参照</span><span class="sxs-lookup"><span data-stu-id="66a9b-143">See Also</span></span>  
 <span data-ttu-id="66a9b-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="66a9b-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="66a9b-145">基本的なテーブル レポートの作成 (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="66a9b-145">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
