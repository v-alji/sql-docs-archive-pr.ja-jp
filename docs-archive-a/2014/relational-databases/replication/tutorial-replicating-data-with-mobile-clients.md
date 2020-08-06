---
title: 'チュートリアル: モバイル クライアントとの間のデータのレプリケーション | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdf8be7cb0da11f0aa1022ba656d50c10826ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645490"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a><span data-ttu-id="d6854-102">チュートリアル : モバイル クライアントとの間のデータのレプリケーション</span><span class="sxs-lookup"><span data-stu-id="d6854-102">Tutorial: Replicating Data with Mobile Clients</span></span>
  <span data-ttu-id="d6854-103">レプリケーションは、中央のサーバーと、常時接続でないモバイル クライアントの間でデータを移動する際の問題を解決する有効なソリューションです。</span><span class="sxs-lookup"><span data-stu-id="d6854-103">Replication is a good solution to the problem of moving data between a central server and mobile clients that are only occasionally connected.</span></span> <span data-ttu-id="d6854-104">レプリケーション ウィザードを使用すると、レプリケーション トポロジを簡単に設定し、管理できます。</span><span class="sxs-lookup"><span data-stu-id="d6854-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="d6854-105">このチュートリアルでは、モバイル クライアント用のレプリケーション トポロジを設定する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="d6854-105">This tutorial shows you how to configure a replication topology for mobile clients.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="d6854-106">学習する内容</span><span class="sxs-lookup"><span data-stu-id="d6854-106">What You Will Learn</span></span>  
 <span data-ttu-id="d6854-107">このチュートリアルでは、マージ レプリケーションを使用して中央のデータベースから 1 名以上のモバイル ユーザーにデータをパブリッシュし、各ユーザーが独自にフィルター選択されたデータ サブセットを取得するようにします。</span><span class="sxs-lookup"><span data-stu-id="d6854-107">In this tutorial you will use merge replication to publish data from a central database to one or more mobile users so that each user gets a uniquely filtered subset of the data.</span></span> <span data-ttu-id="d6854-108">最初のレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使ってパブリケーションを作成する方法を学習し、</span><span class="sxs-lookup"><span data-stu-id="d6854-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="d6854-109">後のレッスンではサブスクリプションを作成および同期する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="d6854-109">Later lessons show how to create and synchronize a subscription.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6854-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d6854-110">Requirements</span></span>  
 <span data-ttu-id="d6854-111">このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="d6854-111">This tutorial is intended for users familiar with fundamental database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="d6854-112">このチュートリアルを開始する前に、 [「チュートリアル: レプリケーションに備えたサーバーの準備」](tutorial-preparing-the-server-for-replication.md)を完了しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6854-112">Before you start this tutorial, you must complete [Tutorial: Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="d6854-113">このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6854-113">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   <span data-ttu-id="d6854-114">パブリッシャー サーバー側 (レプリケーション元) :</span><span class="sxs-lookup"><span data-stu-id="d6854-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="d6854-115">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の任意のエディション。ただし、Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) と [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。</span><span class="sxs-lookup"><span data-stu-id="d6854-115">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="d6854-116">レプリケーションのパブリッシャーとして使用できないため除きます。</span><span class="sxs-lookup"><span data-stu-id="d6854-116">These editions cannot be a replication Publisher.</span></span>  
  
    -   <span data-ttu-id="d6854-117">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="d6854-117">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="d6854-118">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="d6854-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="d6854-119">サブスクライバー サーバー側 (レプリケーション先) :</span><span class="sxs-lookup"><span data-stu-id="d6854-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="d6854-120">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の任意のエディション。ただし、 [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。</span><span class="sxs-lookup"><span data-stu-id="d6854-120">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="d6854-121">は、このチュートリアルで作成するパブリケーションで使用できません。</span><span class="sxs-lookup"><span data-stu-id="d6854-121">is not supported by the publication created in this tutorial.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6854-122">既定では、レプリケーションは [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]にインストールされません。</span><span class="sxs-lookup"><span data-stu-id="d6854-122">Replication is not installed by default on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6854-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、固定サーバー ロール sysadmin のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6854-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the sysadmin fixed server role.</span></span>  
  
 <span data-ttu-id="d6854-124">**このチュートリアルの推定所要時間:30 分。**</span><span class="sxs-lookup"><span data-stu-id="d6854-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="d6854-125">このチュートリアルで行うレッスン</span><span class="sxs-lookup"><span data-stu-id="d6854-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="d6854-126">レッスン 1 : マージ レプリケーションを使用したデータのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="d6854-126">Lesson 1: Publishing Data Using Merge Replication</span></span>](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [<span data-ttu-id="d6854-127">レッスン 2 : マージ パブリケーションへのサブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="d6854-127">Lesson 2: Creating a Subscription to the Merge Publication</span></span>](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [<span data-ttu-id="d6854-128">チュートリアルを開始する</span><span class="sxs-lookup"><span data-stu-id="d6854-128">Start the Tutorial</span></span>](merge/merge-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="d6854-129">参照</span><span class="sxs-lookup"><span data-stu-id="d6854-129">See Also</span></span>  
 [<span data-ttu-id="d6854-130">レプリケーションのプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="d6854-130">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
