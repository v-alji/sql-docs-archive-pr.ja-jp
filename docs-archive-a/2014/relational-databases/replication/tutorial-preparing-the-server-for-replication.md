---
title: 'チュートリアル : レプリケーションに備えたサーバーの準備 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1f036ff2a111ee6b5f97655b9bebaf34391a436
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645494"
---
# <a name="tutorial-preparing-the-server-for-replication"></a><span data-ttu-id="ebd03-102">チュートリアル : レプリケーションに備えたサーバーの準備</span><span class="sxs-lookup"><span data-stu-id="ebd03-102">Tutorial: Preparing the Server for Replication</span></span>
  <span data-ttu-id="ebd03-103">レプリケーション トポロジを構成するには、事前にセキュリティ計画を立てることが重要です。</span><span class="sxs-lookup"><span data-stu-id="ebd03-103">It is important to plan for security before you configure your replication topology.</span></span> <span data-ttu-id="ebd03-104">このチュートリアルでは、レプリケーション トポロジのセキュリティを向上する方法と、データのレプリケートで最初のステップとなるディストリビューションの構成方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ebd03-104">This tutorial shows you how to better secure a replication topology as well as how to configure distribution, which is the first step in replicating data.</span></span> <span data-ttu-id="ebd03-105">他のチュートリアルを行う前に、まずこのチュートリアルを実行してください。</span><span class="sxs-lookup"><span data-stu-id="ebd03-105">You must complete this tutorial before any of the others.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebd03-106">サーバー間でデータを安全にレプリケートするには、「 [レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」の推奨事項をすべて実践してください。</span><span class="sxs-lookup"><span data-stu-id="ebd03-106">To replicate data securely between servers, you should implement all of the recommendations in [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="ebd03-107">学習する内容</span><span class="sxs-lookup"><span data-stu-id="ebd03-107">What You Will Learn</span></span>  
 <span data-ttu-id="ebd03-108">このチュートリアルでは、サーバーを準備し、レプリケーションを最小の特権で安全に実行できるようにする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ebd03-108">In this tutorial you will learn how to prepare a server so that replication can run securely with least privileges.</span></span> <span data-ttu-id="ebd03-109">最初のレッスンでは、レプリケーション エージェントの実行に使用する Windows サービス アカウントの作成方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ebd03-109">The first lesson shows how to create the Windows service accounts used to run replication agents.</span></span> <span data-ttu-id="ebd03-110">2 番目のレッスンでは、パブリケーション スナップショットの生成と保存に使用するフォルダーの構成方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ebd03-110">The second lesson shows how to configure the folder used to generate and store publication snapshots.</span></span> <span data-ttu-id="ebd03-111">3 番目のレッスンでは、ディストリビューションの構成方法と権限の設定方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ebd03-111">The third lesson shows how to configure distribution and set permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd03-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="ebd03-112">Requirements</span></span>  
 <span data-ttu-id="ebd03-113">このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="ebd03-113">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to replication.</span></span>  
  
 <span data-ttu-id="ebd03-114">このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebd03-114">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] <span data-ttu-id="ebd03-115">と [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース。</span><span class="sxs-lookup"><span data-stu-id="ebd03-115">with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="ebd03-116">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="ebd03-116">To enhance security, the sample databases are not installed by default.</span></span>  
  
 <span data-ttu-id="ebd03-117">**このチュートリアルの推定所要時間:30 分。**</span><span class="sxs-lookup"><span data-stu-id="ebd03-117">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="ebd03-118">このチュートリアルで行うレッスン</span><span class="sxs-lookup"><span data-stu-id="ebd03-118">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="ebd03-119">レッスン 1 : レプリケーション用の Windows アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="ebd03-119">Lesson 1: Creating Windows Accounts for Replication</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [<span data-ttu-id="ebd03-120">レッスン 2 : スナップショット フォルダーの準備</span><span class="sxs-lookup"><span data-stu-id="ebd03-120">Lesson 2: Preparing the Snapshot Folder</span></span>](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [<span data-ttu-id="ebd03-121">レッスン 3 : ディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="ebd03-121">Lesson 3: Configuring Distribution</span></span>](lesson-3-configuring-distribution.md)  
  
 [<span data-ttu-id="ebd03-122">チュートリアルを開始する</span><span class="sxs-lookup"><span data-stu-id="ebd03-122">Start the Tutorial</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="ebd03-123">参照</span><span class="sxs-lookup"><span data-stu-id="ebd03-123">See Also</span></span>  
 <span data-ttu-id="ebd03-124">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="ebd03-124">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="ebd03-125">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="ebd03-125">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
