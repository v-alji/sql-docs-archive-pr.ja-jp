---
title: 'チュートリアル: 常時接続サーバー間でのデータのレプリケーション | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 415cac62112c1c1d2aa6c42ec189c2614ec03923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645492"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a><span data-ttu-id="2da0a-102">チュートリアル : 常時接続サーバー間でのデータのレプリケーション</span><span class="sxs-lookup"><span data-stu-id="2da0a-102">Tutorial: Replicating Data Between Continuously Connected Servers</span></span>
  <span data-ttu-id="2da0a-103">レプリケーションは、常時接続サーバー間でデータを移動する際の問題を解決する有効なソリューションです。</span><span class="sxs-lookup"><span data-stu-id="2da0a-103">Replication is a good solution to the problem of moving data between continuously connected servers.</span></span> <span data-ttu-id="2da0a-104">レプリケーション ウィザードを使用すると、レプリケーション トポロジを簡単に設定し、管理できます。</span><span class="sxs-lookup"><span data-stu-id="2da0a-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="2da0a-105">このチュートリアルでは、常時接続サーバー間にレプリケーション トポロジを設定する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="2da0a-105">This tutorial shows you how to configure a replication topology for continuously connected servers.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="2da0a-106">学習する内容</span><span class="sxs-lookup"><span data-stu-id="2da0a-106">What You Will Learn</span></span>  
 <span data-ttu-id="2da0a-107">このチュートリアルでは、トランザクション レプリケーションによって 1 つのデータベースから別のデータベースにデータをパブリッシュする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="2da0a-107">This tutorial will show you how to publish data from one database to another using transactional replication.</span></span> <span data-ttu-id="2da0a-108">最初のレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使ってパブリケーションを作成する方法を学習し、</span><span class="sxs-lookup"><span data-stu-id="2da0a-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="2da0a-109">後のレッスンでは、サブスクリプションを作成および検証する方法と、待機時間を計測する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="2da0a-109">Later lessons show how to create and validate a subscription and how to measure latency.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2da0a-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="2da0a-110">Requirements</span></span>  
 <span data-ttu-id="2da0a-111">このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="2da0a-111">This tutorial is intended for users who are familiar with basic database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="2da0a-112">このチュートリアルを学習するには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da0a-112">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="2da0a-113">このチュートリアルを使用するには、システムに次のコンポーネント必要です。</span><span class="sxs-lookup"><span data-stu-id="2da0a-113">To use this tutorial, your system must have the following components:</span></span>  
  
-   <span data-ttu-id="2da0a-114">パブリッシャー サーバー側 (レプリケーション元) :</span><span class="sxs-lookup"><span data-stu-id="2da0a-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="2da0a-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の任意のエディション。ただし、Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) と [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます</span><span class="sxs-lookup"><span data-stu-id="2da0a-115">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="2da0a-116">(これらのエディションはレプリケーションのパブリッシャーとして使用できません)。</span><span class="sxs-lookup"><span data-stu-id="2da0a-116">These editions cannot be replication Publishers.</span></span>  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] <span data-ttu-id="2da0a-117">サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="2da0a-117">sample database.</span></span> <span data-ttu-id="2da0a-118">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="2da0a-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="2da0a-119">サブスクライバー サーバー側 (レプリケーション先) :</span><span class="sxs-lookup"><span data-stu-id="2da0a-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="2da0a-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の任意のエディション。ただし、 [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。</span><span class="sxs-lookup"><span data-stu-id="2da0a-120">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="2da0a-121">は、トランザクション レプリケーションのサブスクライバーとして使用できません。</span><span class="sxs-lookup"><span data-stu-id="2da0a-121">cannot be a Subscriber in transactional replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2da0a-122">既定では、レプリケーションは [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] にインストールされません。</span><span class="sxs-lookup"><span data-stu-id="2da0a-122">Replication is not installed on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2da0a-123">で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、 **sysadmin**固定サーバーロールのメンバーであるログインを使用して、パブリッシャーおよびサブスクライバーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da0a-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="2da0a-124">**このチュートリアルの推定所要時間:30 分。**</span><span class="sxs-lookup"><span data-stu-id="2da0a-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="2da0a-125">このチュートリアルで行うレッスン</span><span class="sxs-lookup"><span data-stu-id="2da0a-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="2da0a-126">レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="2da0a-126">Lesson 1: Publishing Data Using Transactional Replication</span></span>](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [<span data-ttu-id="2da0a-127">レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="2da0a-127">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [<span data-ttu-id="2da0a-128">レッスン 3 : サブスクリプションの検証と待機時間の計測</span><span class="sxs-lookup"><span data-stu-id="2da0a-128">Lesson 3: Validating the Subscription and Measuring Latency</span></span>](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [<span data-ttu-id="2da0a-129">チュートリアルを開始する</span><span class="sxs-lookup"><span data-stu-id="2da0a-129">Start the Tutorial</span></span>](transactional/transactional-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="2da0a-130">参照</span><span class="sxs-lookup"><span data-stu-id="2da0a-130">See Also</span></span>  
 [<span data-ttu-id="2da0a-131">レプリケーションのプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="2da0a-131">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
